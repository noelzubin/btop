Arguments are parsed manually without a libary.
`btop_shared.hpp` Global: stores global configuration. 

`btop_tools.cpp` contains
* The TUI term implementation 
* Bunch of utility functions.
`Fx` contains text formatting tools
`Mv` contains escape codes for cursor manipulation
`Term` contains escpa codes for Terminal manipulation

There seems to be a lot of RAII patterns used everywhere, especially with locks.

`btop_config.cpp` contains all the configurations. There are maps storing the
descriptions, and another set of maps storing the default values. Config dir is
by default set to `$HOME/.config/btop`


`src/linux/btop_collect.cpp` Contains the code to get the info for all the
stats. The information is mostly gathered from the `/proc` filesystem files.
Some of the information is also gathered from the `sys` filesystem.  

The main thread processes the events and then calls `Input::process(key)`. Which
looks like then kills the current runner and recreates a new runner. which then
draws the things again.

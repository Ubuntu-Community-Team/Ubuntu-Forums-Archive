---
title: "Conky background transparency"
date: 2019-03-18
forum: Ubuntu/Debian BASED
---

### Post by roweder on 2019-03-18
Using Elementary OS Juno which is basically ubuntu 18.04 with the pantheon desktop and some other tweaks (the elementary OS forums are silent).  

When I use a default elementary OS background, conky has a nice transparency:

[ATTACH=CONFIG]282814[/ATTACH]

But when I change the background to a custom photo the conky background changes to this:

[ATTACH=CONFIG]282815[/ATTACH]

I have copied the parted magic conky config:

```
-- vim: ts=4 sw=4 noet ai cindent syntax=lua--[[
Conky, a system monitor, based on torsmo


Any original torsmo code is licensed under the BSD license


All code written since the fork of torsmo is licensed under the GPL


Please see COPYING for details


Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
Copyright (c) 2005-2012 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
All rights reserved.


This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.


This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
]]


conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
	default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 5,
    gap_y = 60,
    minimum_height = 5,
	minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false
}


conky.text = [[
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
]]
```

I have found a few different answers to this but most don't work and some I didn't try because I was not sure how to implement them into this config.

---

### Post by #&amp;thj^% on 2019-03-18
Some of my configs inclued this
```
# Window specifications
############################
own_window yes
own_window_class Conky
own_window_type normal
**own_window_transparent yes**
#own_window_colour black
own_window_argb_visual yes
own_window_argb_value 0# volume - 0 or 250
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```
I do use a compositor though. (Compiz)
I'm not familiar with pantheon desktop though.

---

### Post by again? on 2019-03-18
The config you posted is the default config included with conky and looks like this...
[ATTACH=CONFIG]282819[/ATTACH]
...which doesn't look like your screenshot.

Not familiar with Elementary OS but if they have included a conky config
you will most likely find it at **~/.conkyrc**, a hidden file in your home directory.

In terminal run...
```
ps aux | awk '/[c]onky/'
```

If you just see "conky", the config will be at **~/.conkyrc** which is the default location for a user config.
If you see "conky -c" it will show the path to the config.

eg 
I run 2 conky instances.
One using the the ~/.conkyrc config, the other specifying a config (-c).
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ps aux | awk '/[c]onky/'**
glen     17619  3.0  0.5 390180 23556 pts/0    Sl+  10:45   0:00 **conky**
glen     17562  0.9  0.5 727820 23952 pts/1    Sl+  10:45   0:00 **conky -c /home/glen/conky/configs/tint2.conkyrc**

```      

Please post the correct config to have a look at.

As a quick test, when conky doesn't display properly try reloading with...
```
killall -SIGUSR1 conky
```

---


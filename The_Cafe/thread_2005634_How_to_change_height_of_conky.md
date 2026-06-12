---
title: "How to change height of conky"
date: 2012-06-17
forum: The Cafe
---

### Post by ryanvade on 2012-06-17
Hello, 
         I've got everything perfect for my conky script, except that it is to tall... Apparently the base code I'm using is for a resolution of 1980X1080 , My resolution is 1440X900. I tried to add a max_height 100  but it dosent change anything. heres my code:

```
#==============================================================================
#                                  conkyrc_4
#
#  author  : CAYMUS
#  version : v20120420-03
#  license : Distributed under the terms of GNU GPL version 2 or later
#
#==============================================================================

background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius

double_buffer yes
no_buffers yes
text_buffer_size 100

alignment bottom_middle
gap_x 250
gap_y 30
minimum_size 100 5
maximum_width 1070
Maximum_height 10
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment tl

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color 1B1B1B
color1 000000
color2 333333
color3 333333
color4 333333

lua_load ~/.conky/conky_4.lua
lua_draw_hook_post main

TEXT

${voffset 20}
${goto 50}${font Ubuntu:size=12,weight:bold}${color}CPU ${goto 250}${font Ubuntu:size=12,weight:bold}${color}MEM ${goto 455}${font Ubuntu:size=12,weight:bold}${color}DISKS ${goto 655}${font Ubuntu:size=12,weight:bold}${color}NET ${goto 810}${font Ubuntu:size=7,weight:bold}${color}open ports: ${color1}${tcp_portmon 1 65535 count}
${goto 50}${font Ubuntu:size=7,weight:normal}${color2}${top name 1}${goto 130}${top cpu 1}% ${goto 250}${font Ubuntu:size=7,weight:normal}${color2}${top_mem name 1}${goto 330}${top_mem mem 1}% ${goto 455}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /home} /home ${goto 655}${color1}${font Ubuntu:size=7,weight:bold}eth0 ${addr eth0} ${goto 810}${font Ubuntu:size=7,weight:bold}${color}${offset 10}URL${goto 950}PORT
${goto 50}${font Ubuntu:size=7,weight:normal}${color}${top name 2}${goto 130}${top cpu 2}% ${goto 250}${font Ubuntu:size=7,weight:normal}${color}${top_mem name 2}${goto 330}${top_mem mem 2}% ${goto 455}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /} / ${goto 655}${color}${font Ubuntu:size=7,weight:normal}D: ${downspeed eth1} ${goto 715}U: ${upspeed eth0} ${goto 810}${font Ubuntu:size=7,weight:normal}${color}${tcp_portmon 1 65535 rhost 0} ${goto 950} ${tcp_portmon 1 65535 rport 0}
${goto 50}${font Ubuntu:size=7,weight:normal}${color}${top name 3}${goto 130}${top cpu 3}% ${goto 250}${font Ubuntu:size=7,weight:normal}${color}${top_mem name 3}${goto 330}${top_mem mem 3}% ${goto 455}${diskiograph 10,100 AAAAAA AAAAAA} ${goto 655}TD: ${totaldown eth0} ${goto 715}TU: ${totalup eth0} ${goto 810}${font Ubuntu:size=7,weight:normal}${color}${tcp_portmon 1 65535 rhost 1} ${goto 950} ${tcp_portmon 1 65535 rport 1}
${goto 50}${cpugraph 10,100 AAAAAA AAAAAA} ${goto 655}${color1}${font Ubuntu:size=7,weight:bold}wifi ${addr eth0} ${goto 810}${font Ubuntu:size=7,weight:normal}${color}${tcp_portmon 1 65535 rhost 2} ${goto 950} ${tcp_portmon 1 65535 rport 2}
${goto 50}${font Ubuntu:size=7,weight:normal}${color}${threads} process ${goto 655}${color}${font Ubuntu:size=7,weight:normal}AP: ${wireless_essid eth0} ${goto 715}Speed: ${wireless_bitrate eth0} ${goto 810}${font Ubuntu:size=7,weight:normal}${color}${tcp_portmon 1 65535 rhost 3} ${goto 950} ${tcp_portmon 1 65535 rport 3}
${goto 655}Quality: ${wireless_link_qual_perc eth0}% ${goto 715}Mode: ${wireless_mode eth0} ${goto 810}${font Ubuntu:size=7,weight:normal}${color}${tcp_portmon 1 65535 rhost 4} ${goto 950} ${tcp_portmon 1 65535 rport 4}
${goto 655}D: ${downspeed eth0} ${goto 715}U: ${upspeed eth0} ${goto 810}${font Ubuntu:size=7,weight:normal}${color}${tcp_portmon 1 65535 rhost 5} ${goto 950} ${tcp_portmon 1 65535 rport 5}
${goto 655}TD: ${totaldown eth0} ${goto 715}TU: ${totalup eth0} ${goto 810}${font Digital Readout Thick Upright:size=60}${time %k}:${time %M}



#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  0}${goto 950}${tcp_portmon 1 65535 rport  0}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  1}${goto 950}${tcp_portmon 1 65535 rport  1}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  2}${goto 950}${tcp_portmon 1 65535 rport  2}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  3}${goto 950}${tcp_portmon 1 65535 rport  3}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  4}${goto 950}${tcp_portmon 1 65535 rport  4}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  5}${goto 950}${tcp_portmon 1 65535 rport  5}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  6}${goto 950}${tcp_portmon 1 65535 rport  6}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  7}${goto 950}${tcp_portmon 1 65535 rport  7}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  8}${goto 950}${tcp_portmon 1 65535 rport  8}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  9}${goto 950}${tcp_portmon 1 65535 rport  9}


#${goto 810}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rhost 5} ${goto 950} ${tcp_portmon 1 65535 rport 5}
#${goto 810}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rhost 6} ${goto 950} ${tcp_portmon 1 65535 rport 6}
#${goto 810}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rhost 7} ${goto 950} ${tcp_portmon 1 65535 rport 7}
#${goto 810}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rhost 8} ${goto 950} ${tcp_portmon 1 65535 rport 8}
#${goto 50}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rhost 9} ${goto 950} ${tcp_portmon 1 65535 rport 9}
```

What am I missing?

---

### Post by Bandit on 2012-06-18
Conky gets its height from multiple things. One being "minimum_size" which does just what it says, another from border_width, border_inner_margin and border_outer_margin; in which is best left at 0 until you finally done and then used to tweak the appearance. But mostly the height is controlled by the amount of text you have. Also NOTE that any WHITE SPACE you have below your final line of text will add to its height. Now also take into account any other White Space within your text body. I highly recommend keeping that to one line becuase if you have code for something in one place then a few line of white space then use an voffset -xx then the white lines will push the bottom of your conky border down. Making it possibly too tall.

Hope this helps.

-Joe

---

### Post by ryanvade on 2012-06-18
so how would I change that in my script? specifically?

---


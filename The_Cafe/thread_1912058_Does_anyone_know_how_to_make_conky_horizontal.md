---
title: "Does anyone know how to make conky horizontal"
date: 2012-01-19
forum: The Cafe
---

### Post by BrewerFR on 2012-01-19
Does anyone have any config files that are horizontal and either at the top OR the bottom of their desktop? If not, does anyone know of any resources i can look at that will help me do this? 

I'm using Kubuntu and have multiple desktops; having my conky at either the right or left of each desktop covers the wallpaper, and just by tinkering around with conky its now COMPLETELY broken. Ive also been googling 'horizontal, conky, conky config, how to make conky horizontal, etc' for the last 3 and a half hours and have still found nothing

---

### Post by mips on 2012-01-20
Browse through [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

First one I noticed was in post#45




.

---

### Post by forrestcupp on 2012-01-20
> **mips said:**
> Browse through [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

First one I noticed was in post#48




.

The original post with the code is post#45. Good find.

---

### Post by mips on 2012-01-20
> **forrestcupp said:**
> The original post with the code is post#45. Good find.

Thanks for the correction. Would not call it a good find, the thread is there staring everybody in the face :D

---

### Post by forrestcupp on 2012-01-20
> **mips said:**
> Thanks for the correction. Would not call it a good find, the thread is there staring everybody in the face :D

It's such a huge thread, though, that that one post was a good find. ;)

---

### Post by Sector11 on 2012-01-21
Simply put all the code on one line or break the line with a "\" so you can read it easier in your text editor.

A sample (requires a composite manager and the back ground LUA) for the bottom of the screen:

```
# To use #! in a conky use: ${exec echo '#!'}
# by Sector11 - 14 Aug 2011
# killall conky && conky -c ~/Conky/OB_1-liner-bot &
# WARNING: Change name and passwords on e-mail code if posting!!

###  Begin Window Settings  ##################################################
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# own_window_colour brown
own_window_class Conky
own_window_title OneLine under Tint2

# Use the Xdbe extension? (eliminates flicker)
# It is highly recommended to use own window with this one
# so double buffer won't be so big.
double_buffer yes

### ARGB can be used for real transparency
### NOTE that a composite manager is required for real transparency.
### This option will not work as desired (in most cases) in conjunction with
### 'own_window_type override'
own_window_argb_visual yes

### When ARGB visuals are enabled, this use this to modify the alpha value
### Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
# # own_window_argb_value 0

minimum_size 1013 14     ## width, height
maximum_width 1013       ## width, usually a good idea to equal minimum width

gap_x 5 # left-right
gap_y 3 # up-down

alignment bottom_left
###################################################  End Window Settings  ###
###  Font Settings  ##########################################################
# Use Xft (anti-aliased font and stuff)
use_xft yes
# xftfont dejavu sans mono:size=8
# xftfont ProggySmallTT:size=12
# xftfont ProggyCleanTT:size=12
# xftfont ProggySquareTT:size=12
# xftfont Unispace Regular:size=8
xftfont Anonymous Pro:size=9

# Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 0
# Force UTF8? requires XFT ###
override_utf8_locale yes

draw_shades no
default_shade_color black

draw_outline no # amplifies text if yes
default_outline_color black

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
default_shade_color grey
default_outline_color black

default_color DCDCDC #Gainsboro
color0 DAA520 #Goldenrod  FFFFF0 #Ivory
color1 778899 #LightSlateGrey
color2 FF8C00 #Darkorange
color3 7FFF00 #Chartreuse
color4 FFA07A #LightSalmon
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
color7 00FFFF #Cyan 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red
#####################################################  End Color Settings  ###
###  Borders Section  ########################################################
draw_borders no
# Stippled borders?
stippled_borders 0
# border margins
border_inner_margin 0
border_outer_margin 0
# border width
border_width 0
# graph borders
draw_graph_borders no
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################

# Boolean value, if true, Conky will be forked to background when started.
background no

# Adds spaces around certain objects to stop them from moving other things
# around, this only helps if you are using a mono font
# Options: right, left or none
use_spacer none

# Default and Minimum size is 256 - needs more for single commands that
# "call" a lot of text IE: bash scripts
text_buffer_size 1028

# Subtract (file system) buffers from used memory?
no_buffers yes

# change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2

##############################################  End Miscellaneous Section  ###
###  LUA Settings  ###########################################################
## Above and After TEXT - requires a composite manager or blinks.
##
## lua_load ~/Conky/LUA/draw_bg.lua
## TEXT
## ${lua conky_draw_bg 10 0 0 0 0 0x000000 0.4}
## ${lua conky_draw_bg corner_radius x_position y_position width height color alpha}
##
##
## OR Both above TEXT (No composite manager required - no blinking!)
lua_load ~/Conky/LUA/draw_bg.lua
lua_draw_hook_pre draw_bg 5 0 0 0 0 0x000000 0.5
##
#######################################################  End LUA Settings  ###

# The all important - How often conky refreshes.
# If you have a "Crey" try: 0.2 - smokin' - but watch the CPU useage go UP!
update_interval 1

TEXT
 ${color7}${desktop_name}${color}\
 CPU ${color7}${if_match ${cpu cpu0} < 10}00${cpu cpu0}${color}\
${else}${color7}${if_match ${cpu cpu0} < 100}0${cpu cpu0}${color}\
${else}${color9}${cpu cpu0}${color}\
${endif}${endif}\
 Mem ${color7}${if_match ${memperc} < 10}00${memperc}${color}\
${else}${color7}${if_match ${memperc} < 100}0${memperc}${color}\
${else}${color9}${memperc}${color}\
${endif}${endif}\
 Root ${color7}${if_match ${fs_used_perc /} < 10}00${fs_used_perc /}${color}\
${else}${color7}${if_match ${fs_used_perc /} < 100}0${fs_used_perc /}${color}\
${else}${color9}${fs_used_perc /}${color}\
${endif}${endif}\
 CPU ${color7}${hwmon 1 temp 1}°${color}\
 Fan ${color7}${hwmon 2 fan 1}${color}rpm\
 T2 ${color7}${hwmon 2 temp 1}°${color}\
 T3 ${color7}${hwmon 2 temp 2}°${color}\
 SDA ${color7}${execpi 15 hddtemp -n /dev/sda | xargs ~/Conky/scripts/ColorTempHDD.sh}°${color}\
 GPU ${color7}${nvidia temp}°${color}\
 ${color5}Freq${color} GPU ${color7}${nvidia gpufreq}${color}\
 MEM ${color7}${nvidia memfreq}${color}\
 DN ${downspeedgraph eth0 10,40 FFFF00 FF0000}\
 UP ${upspeedgraph eth0 10,40 FF0000 FFFF00}&#322;\
${goto 933}|  ${color}${uptime_short}${voffset -8}
```

Change:
```
alignment bottom_left
```
to
```
alignment top_left
```
to put it on the top.

---

### Post by Tibuda on 2012-01-21
just remove the line breaks

---

### Post by Sector11 on 2012-01-21
> **Tibuda said:**
> just remove the line breaks

why? Removing those makes a vertical conky.

He asked about a horizontal conky

---

### Post by Tibuda on 2012-01-22
> **Sector11 said:**
> why? Removing those makes a vertical conky.

He asked about a horizontal conky
I mean CR/LF not \

---

### Post by Sector11 on 2012-01-22
> **Tibuda said:**
> I mean CR/LF not \

One could do it all on one line and I did for years:
```
TEXT
 ${color7}${desktop_name}${color} CPU ${color7}${if_match ${cpu cpu0} < 10}00${cpu cpu0}${color}${else}${color7}${if_match ${cpu cpu0} < 100}0${cpu cpu0}${color}${else}${color9}${cpu cpu0}${color}${endif}${endif} Mem ${color7}${if_match ${memperc} < 10}00${memperc}${color}${else}${color7}${if_match ${memperc} < 100}0${memperc}${color}${else}${color9}${memperc}${color}${endif}${endif} Root ${color7}${if_match ${fs_used_perc /} < 10}00${fs_used_perc /}${color}${else}${color7}${if_match ${fs_used_perc /} < 100}0${fs_used_perc /}${color}${else}${color9}${fs_used_perc /}${color}${endif}${endif} CPU ${color7}${hwmon 1 temp 1}°${color} Fan ${color7}${hwmon 2 fan 1}${color}rpm T2 ${color7}${hwmon 2 temp 1}°${color} T3 ${color7}${hwmon 2 temp 2}°${color} SDA ${color7}${execpi 15 hddtemp -n /dev/sda | xargs ~/Conky/scripts/ColorTempHDD.sh}°${color} GPU ${color7}${nvidia temp}°${color} ${color5}Freq${color} GPU ${color7}${nvidia gpufreq}${color} MEM ${color7}${nvidia memfreq}${color} DN ${downspeedgraph eth0 10,40 FFFF00 FF0000} UP ${upspeedgraph eth0 10,40 FF0000 FFFF00}${goto 933}|  ${color}${uptime_short}${voffset -8}
```

but the **[COLOR="Blue"]\[/COLOR]** simply tells conky to **ignore** the "CR/LF" making a horizontal conky a lot easier to work with.

Other than those I have no idea how to remove the "CR/LF" and {opinion} not sure I'd want to, I like the idea of having the sections readily readable.

---


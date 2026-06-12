---
title: "rhythmbox+conky album art"
date: 2011-02-27
forum: The Cafe
---

### Post by sdlynx on 2011-02-27
Now, a quick google finds a nice script to set up conky to show the album art for the song you're listening to (odds are you would come upon this [http://crunchbanglinux.org/forums/topic/3728/images-in-conky-specifically-rhythmbox-album-art/](http://crunchbanglinux.org/forums/topic/3728/images-in-conky-specifically-rhythmbox-album-art/)).

However, after using that script I realized it was a bit system intensive (it copies the album art over and over again), and so I tried to improve it a bit.  I just wanted to share what I've come up with.  Basically, it stores the current album artwork location, and only changes the displayed artwork if rhythmbox says that the current album artwork location has changed.  This keeps my system from rewriting ~/.album over and over again.

.conkyrc
```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no #Transparent background.

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval .5

# Draw shades?
draw_shades no

# Draw borders around graphs
draw_graph_borders no

# Text stuff
draw_outline no
draw_borders no
override_utf8_locale no
xftfont HandelGotDLig:size=10
xftalpha 0.8
#font arial
uppercase no # set to yes if you want all text to be in uppercase
lowercase yes

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
#default_color 666666
default_color 1E201D
color1 1A6C91
color2 D0D0D0
color3 00AFFF
default_outline_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 30
gap_y 30

# Minimum size of text area
minimum_size 240 5

uppercase no
imlib_cache_size 0

# stuff after 'TEXT' will be formatted on screen

lua_load conkyluabg.lua
lua_draw_hook_pre draw_bg

TEXT
${font HandelGotDLig:size=12}${color2}System   ${hr}${font}
${color1}$uptime${alignr}Battery: $battery_percent%
#Up ${uptime}${alignr} cpu0: ${cpu cpu1}% cpu1: ${cpu cpu2}%
${top name 1}${alignr}${top cpu 1}%
${color3}RAM:${color1}$alignr${membar 4,200}
${color2}I/O ${color3}Write:${color1} ${diskio_write}${goto 150}${color3}Read:${color1} ${diskio_read}
#
${if_running rhythmbox}
${font HandelGotDLig:size=12}${color2}Tunes   ${hr}${font}
${offset 69}$color1${font HandelGotDLig:size=9} ${exec rhythmbox-client --no-start --print-playing-format "%te / %td"}
${offset 69}$color1${font HandelGotDLig:size=9} ${exec rhythmbox-client --no-start --print-playing-format %tt}
${offset 69}$color2${font HandelGotDLig:size=11} ${exec rhythmbox-client --print-playing-format %at}
${offset 69}$color3${font HandelGotDLig:size=12} ${exec rhythmbox-client --print-playing-format %aa}${font}
${exec sh .conkyart.sh}${image /home/sdlynx/.drop -s 64x64 -p 5,135}${image /home/sdlynx/.album -s 64x64 -p 0,130}$endif
#
${font HandelGotDLig:size=12}${color2}Networking   ${hr}${font}
eth0${goto 60}${color1}${font DTPDingbats:size=10}${color3}E${color1}${font} ${downspeed eth0}/s${goto 150}${font DTPDingbats:size=10}${color3}B${color1} ${font}${upspeed eth0}/s
${goto 60}${color1}${font DTPDingbats:size=10}${color3}E${color1}${font} ${totaldown eth0}${goto 150}${font DTPDingbats:size=10}${color3}B${color1} ${font}${totalup eth0}${if_up wlan0}
${color2}wlan0${goto 60}${color1}${font DTPDingbats:size=10}${color3}E${color1}${font} ${downspeed wlan0}/s${goto 150}${font DTPDingbats:size=10}${color3}B${color1} ${font}${upspeed wlan0}/s
${goto 60}${color1}${font DTPDingbats:size=10}${color3}E${color1}${font} ${totaldown wlan0}${goto 150}${font DTPDingbats:size=10}${color3}B${color1} ${font}${totalup wlan0}${endif}

${color2}${font ITC Avant Garde Gothic Std:size=15}${time %l:%M:%S %p}
  ${color3}${font ITC Avant Garde Gothic Std:size=10}${time %B %e, %G}

```

The essential parts are:
```

imlib_cache_size 0

TEXT
${offset 69}$color1${font HandelGotDLig:size=9} ${exec rhythmbox-client --no-start --print-playing-format "%te / %td"}
${offset 69}$color1${font HandelGotDLig:size=9} ${exec rhythmbox-client --no-start --print-playing-format %tt}
${offset 69}$color2${font HandelGotDLig:size=11} ${exec rhythmbox-client --print-playing-format %at}
${offset 69}$color3${font HandelGotDLig:size=12} ${exec rhythmbox-client --print-playing-format %aa}${font}
${exec sh .conkyart.sh}${image /home/sdlynx/.drop -s 64x64 -p 5,135}${image /home/sdlynx/.album -s 64x64 -p 0,130}

```

and .conkyart.sh
```

#!/bin/sh
DERP=`conkyRhythmbox --datatype=CA`
if [ `cat .current_album`" " != $DERP" " ]
	then
		if [ -f "`conkyRhythmbox --datatype=CA | sed 's/%20/ /g' | sed "s/%27/\\\'/g" | sed "s/%26/\&/g" | sed 's/%3A/:/g' | sed 's/%21/\!/g' | sed "s/%28/\(/g" | sed "s/%29/\)/g" | sed "s/%24/\$/g"`" ]
			then
				cp "`conkyRhythmbox --datatype=CA | sed 's/%20/ /g' | sed "s/%27/\'/g" | sed "s/%26/\&/g" | sed 's/%3A/:/g' | sed 's/%21/\!/g' | sed "s/%28/\(/g" | sed "s/%29/\)/g" | sed "s/%24/\$/g"`" /home/sdlynx/.album
			else
				cp /home/sdlynx/.noalbum /home/sdlynx/.album
		fi
		conkyRhythmbox --datatype=CA > .current_album
fi

```

.drop is a 64x64 drop shadow image, and you'll also need an image for if there's no album art (saved as ~/.noalbum).  I'm hoping this is helpful for someone, haha.

[img]http://img155.imageshack.us/img155/8237/screenshot1rqa.png[/img]

---


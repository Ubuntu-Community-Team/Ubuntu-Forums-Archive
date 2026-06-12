---
title: "Conky Manager"
date: 2017-01-17
forum: Ubuntu, Linux and OS Chat
---

### Post by g33zr on 2017-01-17
Is there a reason why Conky Manager isn't in the Ubuntu repository? Most other Linux distros I've run offer it. There is a workaround to install it in Ubuntu 16.04, but it doesn't work for 16.10. :confused:

---

### Post by #&amp;thj^% on 2017-01-17
If you don't mind adding his PPA you can install it this way:
His PPA is here: [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa)


> You can update your system with unsupported packages from this untrusted PPA by adding ppa:teejee2008/ppa to your system's Software Sources. (Read about installing)

```
sudo add-apt-repository ppa:teejee2008/ppa
sudo apt update
sudo apt install conky-manager
```
I have used this method for a few years now.:)

---

### Post by vasa1 on 2017-01-17
I don't know what OP means about the method that worked in 16.04 but doesn't work in 16.10, but teejee's ppa doesn't seem to have conky manager for 16.10: [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa?field.series_filter=yakkety](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa?field.series_filter=yakkety)

---

### Post by #&amp;thj^% on 2017-01-17
I have it installed on 16.10...please explain?

---

### Post by Frogs Hair on 2017-01-17
Conky Manager themes for conky Version 1.10 were not available the last time I installed CM though some  themes may work with the old syntax.

---

### Post by #&amp;thj^% on 2017-01-17
> **Frogs Hair said:**
> Conky Manager themes for conky Version 1.10 were not available the last time I installed CM though some  themes may work with the old syntax.

Ok this is good information for me.
I run all my own themes and scripts...so i would have never taken that to consideration.
Thanks for that.

---

### Post by g33zr on 2017-01-17
You can install and run Conky Manager in Ubuntu 16.04. It works, but you're correct, teejee's ppa doesn't seem to have Conky Manager for 16.10. However, my original question remains: Why doesn't Ubuntu include Conky Manager in its ppa, when most other distros I've used does?

---

### Post by deadflowr on 2017-01-17
It's not in Debian, from what I see. And Ubuntu pulls a large majority of packages from Debian.
So if something is not in Debian it doesn't get pulled into Ubuntu.

And if it doesn't get pulled from Debian into Ubuntu, then someone from Ubuntu would have to deal with it.

You can ask the Ubuntu-developers if someone would like to build it. (and deal with it's maintenance) 
Or ask someone at Debian to build and maintain it. Then Ubuntu and other Debian derivatives will pull it in with the rest of the packages, like normal.

Or maybe see if teejee (or someone else) is willing to build a snap package for it.

Or ask teejee about the state of the ppa  and it's relation to 16.10.

---

### Post by g33zr on 2017-01-17
Thanks, deadflower, for the info and suggestions. I think I'll contact teejee first

---

### Post by vasa1 on 2017-01-17
> **1fallen said:**
> I have it installed on 16.10...please explain?
The link I posted didn't list conky manager as being available for YY (16.10). Whereas if you use the filter for XX (16.04), it is listed. That's about all I got.

I've never used CM. My Conky is tiny, just text: day, date, month, time (local & UTC), CPU temp, CPU%, RAM% and a couple of curls to monitor my e-mail :)

---

### Post by SantaFe on 2017-01-18
This is the link I use when installing Conky Manager after a reinstall: [http://www.teejeetech.in/p/conky-manager.html](http://www.teejeetech.in/p/conky-manager.html)

I know the latest CM on the PPA page is listed as 16.04, but it does install & work fine in Ubuntu-MATE 16.10. ;)

---

### Post by g33zr on 2017-01-19
Thanks for link. Yes, it installs and works. When I initially tried to configure (both gui and text config file) /Gotham/Gotham anywhere at the top, it stays at the corresponding left, right, or middle/middle position. However, after rebooting the PC, Conky Manager worked just fine. :D

---

### Post by lovespock on 2017-07-02
Hey, one short question of me. For month my Conky worked well, I had create new widgets and download some nice. Now I wanted to add a new calender, but he is not list in my Conky Manager. I write some on my own and download some, but nothing happens, they are not shown in my Conky Manager. If I take a file that is shown in Conky and copy it, it is also not more shown (in my Conky Manger list with all files). Can I do something, maybe import them manually in Conky? Why they do not work whatever I try? Thanks for help (and of course, sorry for my english ;) ), lovespock

---

### Post by #&amp;thj^% on 2017-07-02
Post your file here, and we can take a look to see if we can help you!
Mine is just basic:
```
###Settings###
background yes
cpu_avg_samples 1
default_bar_size 100 8
default_graph_size 200 100
diskio_avg_samples 10
double_buffer yes
extra_newline no
if_up_strictness address
net_avg_samples 1
no_buffers yes
temperature_unit celsius
text_buffer_size 2048
short_units yes
update_interval 90
###End Settings###

###Position###
alignment top_right
gap_x 20
gap_y 42
minimum_size 300 740
maximum_width 300
###End Position###

###Borders###
border_inner_margin 0
border_outer_margin 10
border_width 0
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
###End Borders###

###Window###
own_window yes
own_window_argb_value 0
own_window_argb_visual yes

#own_window_class systemConky
own_window_color 3D3D3D
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
#all options for own_window_type are normal, desktop, dock, panel or override
#best for Linux Mint 17.1 Cinnamon
#own_window_type dock
#best for Ubuntu 14.10 Utopic
own_window_type dock
#own_window_transparent yes
#own_window_title system_conky
###End Window###


use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create 'own_window' type. Makes Conky behave like other panels.
#
own_window yes
own_window_transparent yes
# own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type dock
####
## Some distros require the following lines for true transparency.
## BOTH of these lines need to be Commented/Uncommented in tandem.
#
# own_window_argb_visual yes
# own_window_argb_value 255

####
## Force images to redraw when they change.
#
imlib_cache_size 1

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
#draw_shades yes
default_shade_color 330

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
# alignment top_right
alignment top_left
# alignment br

####
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
#minimum_size 245 1394
# minimum_size 245 1894
# minimum_size 300 1080
minimum_size 245 1080
maximum_width 1200


###End Font###

###Defining Colors###
default_color FFFFFF
default_outline_color 000000
default_shade_color 000000
#Shades of Gray#
color1 DDDDDD
color2 AAAAAA
color3 888888
#Orange#
color4 EF5A29
#Green#
color5 77B753
#Light Orange#
color6 FFA300
###End Color###

TEXT
${alignr}${font ConkyColors:size=14,weight:normal}n  ${font}
${voffset -10}${offset 55}${voffset 20}${color1}${font Ubuntu mono:size=14,weight:bold}${execpi 80000 cal |sed '/\(20[0-9][0-9]\)/!s/^.*$/ ${offset 40}${color} &/;/\(20[0-9][0-9]\)/!s/.\{8\}$/${color3}&/;s/${color3} '"`date +%_d`"' /${color4} '"`date +%_d`"'${color3} /;/color1/!s/ '"`date +%_d`"'$c/${color1} '"`date +%_d`"'$c/;/color1/!s/ '"`date +%_d`"' /${color4} '"`date +%_d`"'${color2} /'}
```
EDIT: And just in case naming the file is important for Conky Manager to see it.
IE: (.my_calendarrc)
And these scirpts must be the .conky directory in your home.

---


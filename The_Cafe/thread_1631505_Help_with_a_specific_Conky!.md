---
title: "Help with a specific Conky!"
date: 2010-11-26
forum: The Cafe
---

### Post by Sector11 on 2010-11-26
I need people to test a conky on a **desktop** with various Distros, Desktop Managers and Window Managers.

**What's it all about?**

Some people say that using a CPU bar for a CPU you don't have causes conky to "crash" as you see I don't even get an error message with #! Statler regarding the CPU bar on the bottom.  I do see errors in the terminal regarding the battery bar I'm using but it's not crashing the conky!
The LARGE box you see is created by the second last line in the conky:
```
${voffset -850}${battery_bar 870,240}
```
I have NO battery!

The little box on the bottom, is created by the last line:
```
${cpubar cpu6 10,240}
```
I have an AMD64 single core - no 6 cores here!

Feedback should include:
[list=*]
[*]OS:  Debian x86_64 - #! Statler
[*]Kernel:  2.6.32-5-amd64
[*]Resolution:  1280x1024
[*]DE:  Not Present
[*]WM:  OpenBox,
[*]Conky Version:  1.8.0
[*]Does "right-click" work over the conky: Yes, and
[*]A screenshot with the terminal open
[/list]

[[img]http://thumbnails26.imagebam.com/10834/44077e108330187.jpg[/img]](http://www.imagebam.com/image/44077e108330187)

The conky: all-text

```
alignment tl
background no
border_inner_margin 0
border_width 0
default_color FFFFFF
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 10 # left-right
gap_y 20 # up-down
minimum_size 250 0
no_buffers yes
override_utf8_locale yes

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints below,skip_taskbar,skip_pager
own_window_title alltext
own_window_class alltext

pad_percents 2
short_units yes
stippled_borders 0
top_name_width 5
update_interval 1
uppercase no
use_spacer right
use_xft yes
xftalpha 1.0 #0.2
xftfont Sans Mono:size=8

TEXT
${voffset 25}${goto 15}${nodename}
${goto 15}|
${goto 12}+----System
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- OS${goto 125}${sysname}
${goto 15}|${goto 38}+-- Kernel ${goto 125}${kernel}
${goto 15}|${goto 38}+-- Machine${goto 125}${machine}
${goto 15}|
${goto 12}+----Memory
${goto 15}|${goto 38}+-- Total${goto 125}${memmax}
${goto 15}|${goto 38}+-- In Use${goto 125}${mem} (${memperc}%)
${goto 15}|${goto 38}+-- Free${goto 125}${memfree}
${goto 15}|${goto 38}+-- Up to${goto 125}${memeasyfree} freed easily
${goto 15}|${goto 38}+-- Swap
${goto 15}|${goto 60}+-- Total${goto 125}${swapmax}
${goto 15}|${goto 60}+-- Used${goto 125}${swap} - ${swapperc}%
${goto 15}|${goto 60}+-- Free${goto 125}${swapfree}
${goto 15}|
${goto 12}+----Status
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- CPU${goto 125}${cpu cpu0}% - ${freq_g}GHz
${goto 15}|${goto 38}+-- Ram${goto 125}${memperc}%
${goto 15}|${goto 38}+-- LoadAvg${goto 125}${loadavg}
${goto 15}|${goto 38}+-- Disk${goto 125}${fs_used_perc /}% Used
${goto 15}|${goto 38}+-- Diskio ${goto 125}${diskio}
${goto 15}|${goto 60}+-- Read${goto 125}${diskio_read}
${goto 15}|${goto 60}+-- Write${goto 125}${diskio_write}
${goto 15}|
${goto 12}+----Storage
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- /ROOT${goto 125}${fs_free /} / ${fs_size /}
${goto 15}|${goto 38}+-- /HOME${goto 125}${fs_free /home} / ${fs_size /home}
${goto 15}|
${goto 12}+----Processes
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- Total${goto 125}${processes}
${goto 15}|${goto 38}+-- Running${goto 125}${running_processes}
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- CPU
${goto 15}|${goto 40}|${goto 60}+-- ${top name 1}${goto 125}${top cpu 1}${top mem 1}
${goto 15}|${goto 40}|${goto 60}+-- ${top name 2}${goto 125}${top cpu 2}${top mem 2}
${goto 15}|${goto 40}|${goto 60}+-- ${top name 3}${goto 125}${top cpu 3}${top mem 3}
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- MEM
${goto 15}|${goto 60}+-- ${top_mem name 1}${goto 125}${top_mem cpu 1}${top_mem mem 1}
${goto 15}|${goto 60}+-- ${top_mem name 2}${goto 125}${top_mem cpu 2}${top_mem mem 2}
${goto 15}|${goto 60}+-- ${top_mem name 3}${goto 125}${top_mem cpu 3}${top_mem mem 3}
${goto 15}|
${goto 12}+----Net
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- eth0${goto 125}${addr eth0}
${goto 15}|${goto 38}+-- Up
${goto 15}|${goto 40}|${goto 60}+-- Speed${goto 125}${upspeedf eth0}KiB
${goto 15}|${goto 40}|${goto 60}+-- Total${goto 125}${totalup eth0}KiB
${goto 15}|${goto 40}|
${goto 15}|${goto 38}+-- Down
${goto 15}|${goto 60}+-- Speed${goto 125}${downspeedf eth0}KiB
${goto 15}|${goto 60}+-- Total${goto 125}${totaldown eth0}KiB
${goto 15}|
${goto 12}+----Time / Date Calcs
${goto 40}|
${goto 38}+-- Time${goto 125}${time %R:%S}
${goto 38}+-- Date${goto 125}${time %a, %d %b %y}
${goto 38}+-- Uptime${goto 125}${uptime}
${voffset -850}${battery_bar 870,240}
${cpubar cpu6 10,240}
```

It's all generic conky commands, nothing that should stop this from working on any computer - well, unless the CPU and Battery bars cause problems, but that is what I'm testing.

Thanks.
----------------------
Check this out ... new method: [images]("http://ubuntuforums.org/showthread.php?p=10170879#post10170879")

---

### Post by cariboo on 2010-11-26
I just tested your script on Natty using the Ubuntu Classic Desktop, the script seems to work OK here

OS: Natty 11.04 
Kernel:  2.6.37-6-generic #17-
Resolution: 1280X1024
Desktop: Ubuntu Classic Desktop
Right Click : No
Conky version: 1.8.0

I didn't try Unity, but it doesn't work in gnome-shell

---

### Post by Sector11 on 2010-11-26
> **cariboo907 said:**
> I just tested your script on Natty using the Ubuntu Classic Desktop, the script seems to work OK here

OS: Natty 11.04 
Kernel:  2.6.37-6-generic #17-
Resolution: 1280X1024
Desktop: Ubuntu Classic Desktop
Right Click : No

I didn't try Unity, but it doesn't work in gnome-shell

Thanks I forgot to add: What version of conky?

---

### Post by 42dorian on 2010-11-26
OS: Maverick 10.10
Kernel: 2.6.35-23-generic on i686
Resolution: 1280X1024
Desktop: Xubuntu with GT4 Black GTK Theme
Processor: Intel P4 Model 530 3.00Ghz, Hyperthreading 2 Processors
Conky Version: 1.8.1

Tried to do(In Script, Run From Prompt):

```
${color2}CPU2:${goto 55}${freq_g 2}Ghz ${color FFFF00}${cpubar cpu2 5,120}:${cpu cpu2}%${goto 290}Used
```

Result(Crash):

```
Conky: attempting to use more CPUs than you have!
```

---

### Post by ddnev45 on 2010-11-26
No crashes on two computers:

OS - Debian Testing x86_64 on desktop, Aptosid i686 on laptop
Kernel - Debian Testing = 2.6.32-5-amd64; Aptosid = 2.6.30-0.slh.6-aptosid-686
Resolutions - Desktop 1600x900; laptop 1024x768
DE - none
WM - Desktop = Fluxbox; laptop = Openbox
Conky - Desktop 1.8.0; laptop 1.8.1
Right Click - Works on both
Both are AMD processors, single core.

---

### Post by VastOne on 2010-11-27
> **cariboo907 said:**
> I just tested your script on Natty using the Ubuntu Classic Desktop, the script seems to work OK here

OS: Natty 11.04 
Kernel:  2.6.37-6-generic #17-
Resolution: 1280X1024
Desktop: Ubuntu Classic Desktop
Right Click : No
Conky version: 1.8.0

I didn't try Unity, but it doesn't work in gnome-shell

Exact same results as this except using Maverick and a resolution of 1900x1200
Kernel:  2.6.37-6-generic #17-
Gnome
Right click Yes
1.8.0

---

### Post by kaivalagi on 2010-11-27
OS: Arch Linux 64 bit (2.6.35-ARCH)
Kernel:  2.6.35.8-1
Resolution: 3120X1050
Desktop: Gnome + Compiz + AWN + Conky
Right Click : Yes
Conky version: 1.8.1

```
Conky: desktop window (1a0002a) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x5c00001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

```

---

### Post by Sector11 on 2010-11-27
**Thank you,** cariboo907, 42dorian, ddnev45, VastOne & kaivalagi

Interesting 42dorian didn't say if right-click worked or not but from other issues, I'd suspect it didn't.

Other than that it looks like the "DE" are blocking the right-click, and along comes kaivalagi and "poof" that goes up in smoke.

I hope this goes for a bit more.

---

### Post by kaivalagi on 2010-11-27
Just upgraded my kernel to version 2.6.36.1-3 but kept everything else the same and I am getting the same results, I've attached proof of right click operation (I am assuming that is what you are referring to?)

You know you want to make the switch to Arch, tinkering galore to be had :)

---

### Post by Sector11 on 2010-11-27
> **kaivalagi said:**
> Just upgraded my kernel to version 2.6.36.1-3 but kept everything else the same and I am getting the same results, I've attached proof of right click operation (I am assuming that is what you are referring to?)

You know you want to make the switch to Arch, tinkering galore to be had :)

Hey, thanks mate ... I'm actually looking at three things.

1. It started with this [-- text here --]("http://conky-pitstop.wikidot.com/howto-s#toc15") and some people saying it didn't work because of and error: "Your trying to use a CPU you don't have" and conky would "crash" (read - not start).

2. Then came a trick by "arpinux" to run [Conkys in windows]("http://conky-pitstop.wikidot.com/tips-tricks#toc1") that can be opened closed like programs.  I modified that to be a borderless and found that it had a side affect: I could right-click on the conky!

3. I decided to toss in a battery bar that I don't have - and while it produces an error in the terminal it doesn't seem to cause conky to crash.

So this is good news for the most part.
**Thanks for the feedback.**

---

### Post by kaivalagi on 2010-11-27
Now that images are available in conky why not use them to draw a series of broken lines...you could use an image of fixed width and height and position/resize it to suit what the requirements are

Just a thought...

---

### Post by Sector11 on 2010-11-27
> **kaivalagi said:**
> Now that images are available in conky why not use them to draw a series of broken lines...you could use an image of fixed width and height and position/resize it to suit what the requirements are

Just a thought...

See, now that's why you earn the big bucks/pounds/euros (whatever). Brains!! :D

Or even a a square/rectangular box transparent in the middle... YEA!

I'm on it!

make a white one - a black one and people can change them if they want something different.

Back soon!

---

### Post by Sector11 on 2010-11-27
**@ K - you are a genius**

Some notes:
[LIST]
[*]I created 2 images, one black, one white, 1x1 pixel each
[*]I used: *minimum_size 202 # Width Height*
[*]I never use an image command on a line by itself, it creates a "screen dispaly line" if you do.
[/LIST]

The test conky!
```
# To use #! in a conky use: ${exec echo '#!'}
# OB_timeup

alignment tl
background yes
cpu_avg_samples 2
default_outline_color d9d7d6
default_shade_color 000000
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 100
gap_y 100
imlib_cache_size 0
no_buffers yes
override_utf8_locale no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints below,skip_taskbar,skip_pager
own_window_title timeup
own_window_class timeup
total_run_times 0
uppercase no
use_xft yes
xftalpha 0.2
xftfont DejaVu Sans Mono:size=9
imlib_cache_size 0

# Colors
default_color DCDCDC #Gainsboro
color0 FFFFF0 #Ivory
color1 FFA07A #LightSalmon
color2 FF8C00 #Darkorange
color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red
#maximum_width 1160 # Ummm, Width only here
minimum_size 202 # Width Height

update_interval 1
TEXT
${voffset 10}${goto 15}stuff${image ~/Conky/images/white-1.png -p 0,0 -s 1x215}
${goto 15}stuff${image ~/Conky/images/black-1.png -p 0,0 -s 200x1}
${goto 15}stuff${image ~/Conky/images/white-1.png -p 200,0 -s 1x215}
${goto 15}stuff${image ~/Conky/images/black-1.png -p 0,215 -s 200x1}
${goto 15}stuff
${goto 15}stuff
${goto 15}next is System heading
${voffset 20}${alignc 2}System${image ~/Conky/images/white-1.png -p 0,143 -s 70x1}${image ~/Conky/images/white-1.png -p 130,143 -s 70x1}
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
```

Which means BAR text BAR wworks well again!

```
TEXT
${voffset 10}${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
${goto 15}next is System heading
${voffset 20}${alignc 2}System${image ~/Conky/images/white-1.png -p 0,142 -s 70x3}${image ~/Conky/images/white-1.png -p 130,142 -s 70x3}
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
${goto 15}stuff
```

---

### Post by kaivalagi on 2010-11-28
Good stuff, glad my suggestion works okay, fingers crossed the image caching means the IO load is minimal

---

### Post by Sector11 on 2010-11-28
> **kaivalagi said:**
> Good stuff, glad my suggestion works okay, fingers crossed the image caching means the IO load is minimal

Well when ypou think about it a few 1px/sq images stretched to make a line is a lot less than the images for a conkyForecast template   :)

And while I don't need to use the images as the "cbubar" for a CPU I don't have works just fine for me I thought I'd try the lines ...

My latest "vnstat" conky using three lines - 2 white and one red:

[[IMG]http://thumbnails30.imagebam.com/10859/798769108588786.jpg[/IMG]](http://www.imagebam.com/image/798769108588786)

I have white, black, red, green and yellow "dot" images.

Thanks again for the heads up.

---


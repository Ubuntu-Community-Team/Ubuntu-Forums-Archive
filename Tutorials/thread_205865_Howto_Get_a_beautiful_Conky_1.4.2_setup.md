---
title: "Howto: Get a beautiful Conky 1.4.2 setup"
date: 2006-06-29
forum: Tutorials
---

### Post by seldon77 on 2006-06-29
[SIZE="5"][SIZE="5"][COLOR=Red]**Note: this thread is for setting up Conky on older versions of Ubuntu (EDGY, DAPPER and BREEZY). For current Ubuntu versions (Hardy and Ibex, etc), go to: [see this How-to instead]("http://ubuntuforums.org/showthread.php?p=6365702")**[/COLOR][/SIZE][/SIZE]
 
 
FOR EDGY, DAPPER, and BREEZY. NOTE: conky in current versions of Ubuntu is now fixed and up to date, and can be installed from the standard repo. afaik, you only need to install, insert a .conkyrc file similar to the one below, and afaik there is no longer a place in xorg.conf to load the 'dbe' module. Read later discussion for more info or if someone can update me at [EMAIL="conky@pengo.us"]conky@pengo.us[/EMAIL] on the latest instructions for later versions I'll put them up, as a lot of people seem to use this thread.
 
Conky is an powerful desktop app that posts system monitoring info onto the root window. It is hard to set up properly (has unlisted dependencies, special command line compile options, and requires a mod to xorg.conf to stop it from flickering, and the apt-get version doesnt work properly). Most people can't get it working right, but its an AWESOME app if it can be set up right done!
 
With Version 1.4.2 there is no longer a need to load devilspie to hide the taskbar window.
 
Screenshot:
[CENTER][IMG]http://www.pengo.us/conky.jpg[/IMG][/CENTER]
 
1. Install required dependencies (make sure the universe repo is enabled)
Edgy/Breezy/Dapper:
```

    sudo apt-get --assume-yes install wmctrl

```If you want to build from scratch, also install libxext-dev build-essential checkinstall
 
2. Edgy: Install 'conky' from universe repo. ie:
```

    sudo apt-get --assume-yes install conky

```Dapper / Breezy: Download [http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb](http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb) PLEASE DON'T LINK TO THIS FILE, as it's only on very limited bandwidth! ie:
```
cd
wget http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb
sudo dpkg -i conky_1.4.2-0ubuntu1_i386.deb

```This is a .deb file for Conky 1.4.2 now that works on Breezy/Dapper Ubuntu (the standard Debian 1.4.2 .deb doesn't work). Note that at the time of writing this how-to, the conky in the dapper ubuntu universe repository is very old and, in ways, broken.[INDENT]*[COLOR=dimgray]Note that at the time of writing, version 1.4.2 is the latest version. If a later version has been released since the writing of this guide, you can build your own conky .deb file as follows. First, go to [http://conky.sourceforge.net/](http://conky.sourceforge.net/) to download the latest version.[/COLOR]*
 
*[COLOR=dimgray]```
wget http://umn.dl.sourceforge.net/sourceforge/conky/conky-1.4.2.tar.gz
```[/COLOR]*```

*[COLOR=dimgray]        tar xvzf conky-1.4.2.tar.gz[/COLOR]*
*[COLOR=dimgray]        rm conky-1.4.2.tar.gz[/COLOR]*
*[COLOR=dimgray]        cd ~/conky-1.4.2[/COLOR]*
*[COLOR=dimgray]        ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe[/COLOR]*
*[COLOR=dimgray]        make[/COLOR]*
*[COLOR=dimgray]        sudo checkinstall[/COLOR]*

```*[COLOR=dimgray]Then answer the relevant questions that checkinstall gives. But, as stated above, you may only need to download the source and make it if this guide has become outdated and versions after 1.4.2 have been released.[/COLOR]*
[/INDENT]3. Make a configuration file in your home directory (ie. /home/bob)
```

gedit /home/bob/.conkyrc

```4. Paste the following code into the file and save / exit. If you know what you are doing, you can edit this file, or download other example configuration file on the net (but this one is probably the best!).
```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```If the network connections graph does not work, you will have to change all "eth0" references to "ppp0" (for modem) or "ath0" (for some other devices). 
 
5. Add dbe module to /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```find the section titled Section "Module", and add
```

        Load    "dbe"

```6. Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot![INDENT]*[COLOR=dimgray]NOTE: **Kubuntu users ONLY** make the following changes:[/COLOR]*
*[COLOR=dimgray]Open .conkyrc and comment out the lines[/COLOR]*
*[COLOR=dimgray]```
own_window yes
```[/COLOR]*```

*[COLOR=dimgray]own_window_hints undecorated,below,skip_taskbar[/COLOR]*
*[COLOR=dimgray]background yes[/COLOR]*
```*[COLOR=dimgray]Since we don't use nautilus in Kubuntu, we don't need it.[/COLOR]*
 
*[COLOR=dimgray]Also, to get Conky to autostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to [/COLOR]*
*[COLOR=dimgray]```
~/.kde/Autostart
```[/COLOR]*
*[COLOR=dimgray]**For XFCE ONLY** make the following changes to .conkyrc[/COLOR]*
*[COLOR=dimgray]```
own_window yes
```[/COLOR]*```

*[COLOR=dimgray]own_window_type override[/COLOR]*
*[COLOR=dimgray]own_window_transparent yes[/COLOR]*

```*[COLOR=dimgray]For **Compiz / AIGLX users ONLY** please make these changes:[/COLOR]*
*[COLOR=dimgray]In .conkyrc[/COLOR]*
*[COLOR=dimgray]```
own_window yes
```[/COLOR]*```

*[COLOR=dimgray]own_window_type override[/COLOR]*
*[COLOR=dimgray]own_window_transparent yes[/COLOR]*
*[COLOR=dimgray]own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager[/COLOR]*

```*[COLOR=dimgray]Then (Compiz users) place a startup script called .conky_start.sh in your home directory:[/COLOR]*
*[COLOR=dimgray]```
#!/bin/bash
```[/COLOR]*```

*[COLOR=dimgray]sleep 60 && conky;[/COLOR]*
```*[COLOR=dimgray]This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs). [/COLOR]*
[/INDENT]

---

### Post by mikl on 2006-06-29
Using ```
sudo make install
``` is a rather bad idea. It's much better to use the debian package system to keep track of such files, so instead of running ```
sudo make install
```, just run ```
sudo checkinstall
``` and enter your way through all the questions (the default options are just fine) and make sure you install the .deb file checkinstall generates.

Now you won't have unmanaged files cluttering your system and Conky can be easily removed using apt-get and even redistrbuted :)

---

### Post by ciscosurfer on 2006-06-29
I've followed the instructions...what am I missing?  I keep getting this error:
```
magic@frisky:~/conky-1.4.2$ ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking build system type... Invalid configuration `i686-pc-linux-oldld': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux-oldld failed
``` Any thoughts anyone? ](*,)

Also, can someone please give me a run-down on <sudo checkinstall> vs <sudo make install>.  Thanx!

---

### Post by markmark on 2006-06-29
[QUOTE=ciscosurfer]Also, can someone please give me a run-down on <sudo checkinstall> vs <sudo make install>.  Thanx![/QUOTE]Basically "make install" just installs the program by copying all the files to the appropriate places, you can then uninstall later on by doing a "make uninstall" in the source directory (which you need to keep around). "checkinstall" makes a deb file and installs it with apt-get, which means you can use apt to uninstall, plus if you set the version numbers right it will automatically get upgraded if a newer version appears in the repos (for example if you build 1.4.2, and then in a few months 1.5 appeared in the ubuntu repos, it would get updated).

---

### Post by ciscosurfer on 2006-06-29
[quote=markmark]Basically "make install" just installs the program by copying all the files to the appropriate places, you can then uninstall later on by doing a "make uninstall" in the source directory (which you need to keep around). "checkinstall" makes a deb file and installs it with apt-get, which means you can use apt to uninstall, plus if you set the version numbers right it will automatically get upgraded if a newer version appears in the repos (for example if you build 1.4.2, and then in a few months 1.5 appeared in the ubuntu repos, it would get updated).[/quote] Thanks for the info, I appreciate it.  :grin:

---

### Post by beerorkid on 2006-06-30
woorked good for me.
 
took me a little bit to get it up in the right hand corner.

Just read the docs on the main site, or man conky

Kind of neat.  Seems a bummer it is not up to date in the repo's.

thanks

---

### Post by seldon77 on 2006-06-30
if anyone has a lot of trouble compiling, i've got a .deb file for 1.4.2 now that works on ubuntu (the standard debian 1.4.2 deb doesn't work).

but, please don't link to this file, as it's only on very limited bandwidth!
[http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb](http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb)

---

### Post by Kashirigi on 2006-06-30
I'm trying to compile conky, and when I do ./configure --whatever,  I get this:
.......
checking for X... no
checking for XdbeQueryExtension in -lXext... no
configure: error: something went wrong when checking for Xdbe (double buffer extension)

Clearly something is wrong, but I have no idea where to start looking.

Thanks for any help you can provide.

---

### Post by seldon77 on 2006-06-30
[QUOTE=Kashirigi]I'm trying to compile conky, and when I do ./configure --whatever,  I get this:
.......
checking for X... no
checking for XdbeQueryExtension in -lXext... no
configure: error: something went wrong when checking for Xdbe (double buffer extension)

Clearly something is wrong, but I have no idea where to start looking.

Thanks for any help you can provide.[/QUOTE]

I think you skipped step 1? Installing the required dependancies?
do the:
sudo apt-get --assume-yes install libxext-dev lm-sensors
before continuing.

if thats not the problem, let me know!

---

### Post by Greeface on 2006-07-01
It is still all flickery for me, even after I added that part to my xorg.conf file. What gives?

---

### Post by seldon77 on 2006-07-01
[QUOTE=Greeface]It is still all flickery for me, even after I added that part to my xorg.conf file. What gives?[/QUOTE]

have you rebooted yet??

if you have, ensure that the xorg.conf is editted correctly and you are using the .conkyrc file supplied (a wrongly configured .conkyrc script will flicker, ie. if it doesn't ask for the double buffer)

---

### Post by Stormboy on 2006-07-02
[QUOTE=seldon77]if anyone has a lot of trouble compiling, i've got a .deb file for 1.4.2 now that works on ubuntu (the standard debian 1.4.2 deb doesn't work).

but, please don't link to this file, as it's only on very limited bandwidth!
[http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb](http://www.pengo.us/conky_1.4.2-0ubuntu1_i386.deb)[/QUOTE]
thanks for the link saved me lot of time! \\:D/

---

### Post by Stormboy on 2006-07-02
How do I get the original content of the .conkyrc file?
I nuffed mine!
Thanks!

---

### Post by bulldog on 2006-07-02
[QUOTE=Stormboy]How do I get the original content of the .conkyrc file?
I nuffed mine!
Thanks![/QUOTE]

Look at the first page of this HowTo:D 

Works very well indeed,thanks for this HowTo.
One question though,it keeps track of hda1 but I use sda1 and I changed hda1 into sda1,but that doesn't seem to work.
Is there a way to change this?

---

### Post by blacknyx on 2006-07-02
Is there way to add it to your desktop perminately without gnome.  I'm running Xubuntu.  
Thanks

---

### Post by Stormboy on 2006-07-02
[QUOTE=bulldog]Look at the first page of this HowTo:D 

Works very well indeed,thanks for this HowTo.
One question though,it keeps track of hda1 but I use sda1 and I changed hda1 into sda1,but that doesn't seem to work.
Is there a way to change this?[/QUOTE]
:oops: 
Thanks!

---

### Post by saax on 2006-07-02
I installed Conky succesly but I cant figure out why my conky doesn't stop to flicker.

I change "double_buffer no" instead of "double_buffer yes"

and set time interval to half a second instead of one second.

Im using this script
[http://conky.sourceforge.net/conkyrc-vert]("http://conky.sourceforge.net/conkyrc-vert")

I would also like to use it on right top corner ,but dont now how


Please help me

---

### Post by R3linquish3r on 2006-07-02
I personally like the configs that offer multi-colors on the status bars. Heres a shot of my flux desktop with my conky conifg:

[IMG]http://www.pascam.net/teamm/edstuff/screenshot.jpg[/IMG]

---

### Post by Mr.X on 2006-07-02
Wow, thanks this really is a great desktop, *using* :D.

---

### Post by kpkeerthi on 2006-07-03
It worked great... but it could not load the font 'arial'... 
```

Conky: can't load font 'arial'

```

I have mstcorefonts but it won't load. I tried replacing the font with system default (Sans) and still won't work. I also tried the -f option and no luck too... Would highly appreciate your help.

---

### Post by maddbaron on 2006-07-03
this worked great for me but it is still flickering for me. how do i double buffer via command line? also i have it at the bottom left of the screen how do i move it to the top right?
and what way to change the visual style of it?

thanks in advance.

---

### Post by maddbaron on 2006-07-03
and now after i rebooted again it doesnt show up at all.....what can i do? even sudo conky doesny work in terminal

---

### Post by n00b@linux on 2006-07-03
[quote=ciscosurfer]I've followed the instructions...what am I missing?  I keep getting this error:
```
magic@frisky:~/conky-1.4.2$ ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking build system type... Invalid configuration `i686-pc-linux-oldld': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux-oldld failed
``` Any thoughts anyone? ](*,)

Also, can someone please give me a run-down on <sudo checkinstall> vs <sudo make install>.  Thanx![/quote] 
I get exactly the same thing.  Was it ever resolved?  What do I do?

EDIT:  I decided to download the .deb file instead.  Once I downloaded it, I opened up the file browser and navigated my way to it.  Then I right-clicked on it and selected "Open with GDebi Package Installer".  That did the trick.  Then I just followed seldon77's post from where I left it, ie. I restarted again at point 4.  Et voila!  It's excellent.  Thanks for all the work seldon77! :)
[[IMG]http://img89.imageshack.us/img89/8652/screenshot42or.th.png[/IMG]](http://img89.imageshack.us/my.php?image=screenshot42or.png)

---

### Post by ciscosurfer on 2006-07-04
Realizing that I didn't have the proper compiler installed to build from source, I went ahead and installed 'build-essential' via apt-get (you can use aptitude as well, or the more friendly GUIs, Synaptic or Adept):
```
sudo apt-get install build-essential
```This will grab and install the necessary files for you: the GNU C compiler (gcc), make, g++, and a bevy of other progs you will need to compile from source.  Hope this helps others. \\:D/

---

### Post by seldon77 on 2006-07-04
[QUOTE=kpkeerthi]It worked great... but it could not load the font 'arial'... 
```

Conky: can't load font 'arial'

```

I have mstcorefonts but it won't load. I tried replacing the font with system default (Sans) and still won't work. I also tried the -f option and no luck too... Would highly appreciate your help.[/QUOTE]

yeah. it's to do with the compile options in making conky.

for some reason, compiling with xbe doesn't work wel, and thus the error.

you could try downloading the .deb file I mention on page 1 (?), instead of compiling by hand.

---

### Post by honeysucker on 2006-07-12
> **maddbaron said:**
> and now after i rebooted again it doesnt show up at all.....what can i do? even sudo conky doesny work in terminal

i've got the same prob. i work with openbox and xgl, can that be a problem?

---

### Post by Johan! on 2006-07-13
It works!
Thanks for the how-to =D> 

Screenshot:
[[IMG]http://img228.imageshack.us/img228/6577/screenshot55wd.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshot55wd.png)

But as you can see, there are still some errors in the output...
This is my .conkyrc file:

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
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
CPU: ${freq}MHz   Load: ${loadavg}   Temp: ${execi 30 sensors |grep "CPU" |cut -d " " -f6}
$cpubar
${cpugraph}$color

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:        $memperc%       ${membar 6}$color
Swap:       $swapperc%       ${swapbar 6}$color

Root:       ${fs_free_perc /}%        ${fs_bar 6 /}$color 
Winblows:   ${fs_free_perc /media/windows}%         ${fs_bar 6 /media/windows}$color 
WD:         ${fs_free_perc /media/wd}%         ${fs_bar 6 /media/wd}$color
Server:     ${fs_free_perc /media/server}%        ${fs_bar 6 /media/server}$color
$color$stippled_hr
IP: ${addr eth0} Total: ${totaldown eth0} Down ${totalup eth0} Up

Down: ${downspeed eth0} k/s ${offset 110}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 32,200} ${upspeedgraph eth0 32,200}

${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
$color$stippled_hr
SYSTEM LOG TAIL
${execi 30 tail -n3 /var/log/messages | fold -w67}
$color$stippled_hr
Xmms: ${execi 5 cat /tmp/xmms-info | grep Status: | cut -d ":" -f2}
Artist: ${execi 5 cat /tmp/xmms-info |grep Title: | cut -d "-" -f1}
Title :${execi 5 cat /tmp/xmms-info |grep Title: | cut -d "-" -f2}
Time : ${execi 5  cat /tmp/xmms-info |grep -w Position | cut -d " " -f2} (${execi 5 cat /tmp/xmms-info |grep -w Time |cut -d " " -f2})
List  : ${execi 5 cat /tmp/xmms-info |grep Currently |cut -d ":" -f2} /${execi 5 cat /tmp/xmms-info | grep Tunes | cut -d ":" -f2}
${execi 10 /home/johan/xmmsbar.sh}
$color$stippled_hr
${execi 300 fortune -s | fold -w67}
```

I used the .conkyrc file from the first post, and modified it a little:p 
I changed the temperature output from acpitemp to sensors, because acpitemp always shows 40 degrees, not the actual temperature. There is only a small problem in the conky output.

The real problem is the XMMS output... see the next screenshot:

[[IMG]http://img204.imageshack.us/img204/4041/screenshot69zr.png[/IMG]](http://imageshack.us)
Sometimes, the XMMS information appears multiple times. I use xmms-infopipe to create the data.

Who can help me fix these small problems?

---

### Post by seldon77 on 2006-07-14
> **honeysucker said:**
> i've got the same prob. i work with openbox and xgl, can that be a problem?

could be. gnome users dont seem to have a problem.

just ensure that 'conky' is run by default when the window manager starts up.

---

### Post by hype on 2006-07-15
Following your How-to i finally removed the "flickering effect" i had previously with conky.
 Your config is really good tho.
Only thing: How can i modify the length of the CPU and up/down bars?

Edit: i ve been able to make smaller "version":
```
TEXT
$color$stippled_hr
$nodename 
$sysname $kernel on $machine

CPU: ${freq}MHz     Temp: ${acpitemp}
${cpubar 16,180}
$color$stippled_hr
NAME            CPU%      MEM%

${top name 1}${top cpu 1}    ${top mem 1}
${top name 2}${top cpu 2}    ${top mem 2}
${top name 3}${top cpu 3}    ${top mem 3}
${top name 4}${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:   $memperc%  ${membar 4,100}$color
Swap:  $swapperc%  ${swapbar 4,100}$color

Root:  ${fs_free_perc /}%   ${fs_bar 4,100 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 4,100 /media/hda1}$color 
$color$stippled_hr
Total: ${totaldown eth0} Down ${totalup eth0} Up

Down: $color${downspeed eth0}     Up: ${upspeed eth0}
${downspeedgraph eth0 16,87.5} ${upspeedgraph eth0 16,87.5}
$color$stippled_hr

```

By the way, how to had color into conky ? I tried $color (color) command but it doesnt seem to work ( iwanted to color "Down" in green: i added $color green in front of "Down", but it just displayed "green Down" :p)

---

### Post by Neo40 on 2006-07-15
Hello,

It working fine here on my Xubuntu system (I'm using xfce4) but conky appears only in one desktop. How can I configure to be able to see it on my 4 desktops?
Thanks

---

### Post by Rexbron! on 2006-07-16
Once again, thank you for writing this great tutorial.

My problem is this, the network traffic monitor does not monitor anything and it never changes. I have had this problem with other system montitors (for karamba). Is there a package that I need to install before this will work?

And for those who are installing the package, make sure to update .conkyrc with the one given here.

We should see if we can get this to replace the old corky package in the repository. Any volunteers for emailing the MOTU's?

---

### Post by hype on 2006-07-16
I noticed while booting, i have a service that fails to start:
"Setting Sensors Limit"  Failed 
 It didnt appear before i installed conky from your How-to.
Its doesnt seem to bother conky ; it seems to wrok fine

---

### Post by Rexbron! on 2006-07-16
I have this problem as well, I think is has something to do with ls-sensors package not being the right one for your mobo/laptop (in my case acer aspire 3624)

---

### Post by ScoobyDan on 2006-07-16
Thanks for this How-To - it worked great!

The only problem I am having, is I can't get transparency to work - the background is always black. I read on the Conky FAQ ([http://conky.sourceforge.net/faq.html)](http://conky.sourceforge.net/faq.html)), that I need to use a program called "qiv", but I can't see how. Any ideas?

Daniel

PS: I am running Kubuntu 6.06, and the graphics card is a VIA Unichrome on-board jobby (if that's of any help).

---

### Post by Rexbron! on 2006-07-16
> **ScoobyDan said:**
> Thanks for this How-To - it worked great!

The only problem I am having, is I can't get transparency to work - the background is always black. I read on the Conky FAQ ([http://conky.sourceforge.net/faq.html)](http://conky.sourceforge.net/faq.html)), that I need to use a program called "qiv", but I can't see how. Any ideas?

Daniel

PS: I am running Kubuntu 6.06, and the graphics card is a VIA Unichrome on-board jobby (if that's of any help).

Open .conkyrc and comment out the lines
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
```

Since we don't use nautilus, we don't need it. If the original writer of this guide is around, he (or she) might want to add that to the original post.

Also, to get Conky to atostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 
```
~/.kde/Autostart
```.

---

### Post by mtpadilla on 2006-07-16
Hello. I love conky so far...great app. Thank you seldon77 for the nice how to.

So I followed the Howto exactly, compling from scratch without any problems, changing /etc/X11/xorg.config, and only slightly modifying the .conkyrc file to more appropriate partitions to monitor the size of. Things for the most part are fine...(oh, and no flicker problem).

HOWEVER, I have three problems:
1) I get the errors
Conky: /home/mtp/.conkyrc: 15: no such configuration: 'own_window_hints'
Conky: can't load font 'arial'
2) It looks kind of crappy, with thick black lines around every character.
3) It only shows up on one of my four desktops.

Does anyone happen to know how to solve this to make the errors go away and make it look reasonably well on the desktop?

Thank you very much in advance!!:p 

SCREENSHOT:
[IMG]http://www.stanford.edu/~mtp/papers/Screenshot.png[/IMG]

EDIT: Added problem #3 after realizing it.

---

### Post by hype on 2006-07-16
> **Rexbron! said:**
> I have this problem as well, I think is has something to do with ls-sensors package not being the right one for your mobo/laptop (in my case acer aspire 3624)

 As i dont have a LapTop, it may be the origin of the problem. :p

Anyway, i can see my cpu temperature, so some sensor must be working ^^
ANd actually the error message at boot time is something like:
 "Setting sensors limit" FAILED 
It doesn mean that sensors dont work, right?

---

### Post by arrizaba on 2006-07-17
I've got the "dbe" module but conky still flickers a bit. I changed the refresh time to 1 min not to make it so annoying. 
Can the flickering be completely eliminated? 
Btw, I use Compiz as window manager.

I got (I think) a nice config for my conky. Here's a sceenshot:

[IMG]http://www.nikhef.nl/~arrizaba/pub/Screenshot.png[/IMG]

---

### Post by ScoobyDan on 2006-07-17
> **Rexbron! said:**
> Open .conkyrc and comment out the lines
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
```

Since we don't use nautilus, we don't need it. If the original writer of this guide is around, he (or she) might want to add that to the original post.

Also, to get Conky to atostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 
```
~/.kde/Autostart
```.

Rexbron,

Many thanks for that - my conky is now nice and transparent!

Regarding the autostart, I just saved my session with conky running, and now it starts every time. I might look into the link route, if that is more elegant...

Thanks again,

Daniel

---

### Post by seldon77 on 2006-07-18
wow.. nice screenshot. can you share your .conkyrc file? also, which gdesklet are you using there for the temperature?

---

### Post by seldon77 on 2006-07-18
> **mtpadilla said:**
> Hello. I love conky so far...great app. Thank you seldon77 for the nice how to.

I have three problems:
1) I get the errors
Conky: /home/mtp/.conkyrc: 15: no such configuration: 'own_window_hints'
Conky: can't load font 'arial'
2) It looks kind of crappy, with thick black lines around every character.
3) It only shows up on one of my four desktops.


1) hmm... are you compiling the latest conky version? the cant find arial problem is known. you can take that line out of the .conkyrc file but then the text goes a bit funny.

2) put
```
draw_outline no
```
into the .conkyrc file

3) This has to do with the own_window_hints settings. see the conky man page for more options and to put on all desktops.

---

### Post by seldon77 on 2006-07-18
> **Rexbron! said:**
> Open .conkyrc and comment out the lines
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
```

Since we don't use nautilus, we don't need it. If the original writer of this guide is around, he (or she) might want to add that to the original post.

Also, to get Conky to atostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 
```
~/.kde/Autostart
```.

Done - thanks!

---

### Post by mtpadilla on 2006-07-18
> **seldon77 said:**
> 1) hmm... are you compiling the latest conky version? the cant find arial problem is known. you can take that line out of the .conkyrc file but then the text goes a bit funny.

2) put
```
draw_outline no
```
into the .conkyrc file

3) This has to do with the own_window_hints settings. see the conky man page for more options and to put on all desktops.


Thank you for your help.

1) Yep, I compiled using the latest version off the conky website (& followed the how-to exactly except for changing which partitions to monitor the size of).
2) Worked well...thanks.
3) Yep, I needed to add "sticky" it seems. Now it's appearing on all the desktops. 

Cheers...I'm going to be using this now. Still a lot of cuter customizations to do, but I'll get to it later.

BTW...yes, if arizzaba wouldn't mind sharing their .conkyrc, that would be killer.

---

### Post by mtpadilla on 2006-07-18
Hello. I've noticed one odd problem that I haven't seen anyone else mention in this thread...everything's pretty smooth now by following the Howto and seldon77's advice.

However, sometimes the background of conky momentarily (say for a second or so) changes to some other image that appeared at some recent time (like the past 5 minutes). This can be another part of the desktop itself (such as another part of my desktop background with the icons on top), part of some webpage I just viewed in Firefox, etc. I don't know how to envoke the behavior as I haven't noticed any clear cause/effect pattern.

SCREENSHOTS:
w/ the problem: [http://www.stanford.edu/~mtp/papers/Screenshot2.png](http://www.stanford.edu/~mtp/papers/Screenshot2.png)
w/o the problem: [http://www.stanford.edu/~mtp/papers/Screenshot3.png](http://www.stanford.edu/~mtp/papers/Screenshot3.png)

Unfortunately I haven't the knowledge yet (i.e. newbie) to diagnose and solve it...any ideas? Thank you very much.

p.s. I'm using Gnome (the standard ubuntu 6.06 install)

EDIT: Added the links to screenshots.

---

### Post by sirlancelot on 2006-07-19
Thanks so much for this!

I've been looking for something like this since I switched to linux, (windows version: [samurize]("http://www.samurize.com")).

I look forward to this app's progress! \\:D/

---

### Post by dmitriyr333 on 2006-07-19
Has anybody got **conky** working with transparency **AND** in its own window in KUBUNTU??? If so, please, please, please post a solution. 
	Thank you.
Dmitriy

---

### Post by GarethEvans on 2006-07-21
Great tutorial, worked perfectly for me (chose to compile from source with xfce)

---

### Post by 5-HT on 2006-07-21
> **Neo40 said:**
> Hello,

It working fine here on my Xubuntu system (I'm using xfce4) but conky appears only in one desktop. How can I configure to be able to see it on my 4 desktops?
Thanks

Add *sticky* to your *own_window_hints* line in ~/.conkyrc

> **hype said:**
> 
By the way, how to had color into conky ? I tried $color (color) command but it doesnt seem to work ( iwanted to color "Down" in green: i added $color green in front of "Down", but it just displayed "green Down" :p)

${color <color>} text to be displayed in defined colour

e.g., 
${color red} this text will be displayed in red
${color FF0D00} this text will be displayed in ~reddish

---

### Post by Rexbron! on 2006-07-22
Maybe everybody already knows this but I was unable to get the ipgraph to display any of my traffic. Note that I am on a laptop: today I decided to plugin my laptop to my wired network and bam the graph was working. 

So I checked in the .conkyrc file under the ip/graph heading changed all instances of eth0 to ath0 (if you have a broadcom chip change it to whatever networkconnections lists your device as) and now the graphs are working.

If you want both your wireless card and you wired card to graph, just copy the relevant section and then change as above.

---

### Post by seldon77 on 2006-07-23
> **Rexbron! said:**
> Maybe everybody already knows this but I was unable to get the ipgraph to display any of my traffic. Note that I am on a laptop: today I decided to plugin my laptop to my wired network and bam the graph was working. 

So I checked in the .conkyrc file under the ip/graph heading changed all instances of eth0 to ath0 (if you have a broadcom chip change it to whatever networkconnections lists your device as) and now the graphs are working.

If you want both your wireless card and you wired card to graph, just copy the relevant section and then change as above.

Thanks! I put your advice into the how-to. I am updating the how-to as advice and comments come in.

---

### Post by btlotfinia on 2006-07-25
Typing the following,

```
sudo dpkg -i conky_1.4.2-0ubuntu1_i386.deb
```

results in this:

```
dpkg-deb: `conky_1.4.2-0ubuntu1_i386.deb' is not a debian format archive
dpkg: error processing conky_1.4.2-0ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 conky_1.4.2-0ubuntu1_i386.deb
```

Any thoughts would be appreciated.

---

### Post by BoomAM on 2006-07-25
I followed that guide word for word and it doesnt work.
If i run the conky icon from the app menu i briefly get a window popping up, then it disappears again without doing anything.

Ideas?

---

### Post by nwgray on 2006-07-25
I compiled everything and when my session starts up, I can see it but then it disappears. I'm running gnome. I can't seem to figure out how to find it again after startup.

Thx

---

### Post by 5-HT on 2006-07-25
> **nwgray said:**
> I compiled everything and when my session starts up, I can see it but then it disappears. I'm running gnome. I can't seem to figure out how to find it again after startup.

Thx

Is conky drawing to its own window?
If not, nautilus might be gobbling conky up when it draws the desktop.
If this is the case then you can either call conky with the -o option or add 'own_window yes' in your conkyrc.

HTH

---

### Post by Rexbron! on 2006-07-25
> **btlotfinia said:**
> Typing the following,

```
sudo dpkg -i conky_1.4.2-0ubuntu1_i386.deb
```

results in this:

```
dpkg-deb: `conky_1.4.2-0ubuntu1_i386.deb' is not a debian format archive
dpkg: error processing conky_1.4.2-0ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 conky_1.4.2-0ubuntu1_i386.deb
```

Any thoughts would be appreciated.

Try compiling Conky from source and use checkinstall instead of make install.

---

### Post by ephman on 2006-07-26
hi,

has anybody noticed that conky sometimes pauses?  also, it'll vanish a little later.  i don't know if the two are related.  i read the above posting about the vanishing problem somebody else noticed, but is there a way i can fix this?

thanks,
ephman

btw thanks for the howto it's great, i was looking for something like that so i didn't have to use gdesklets...

---

### Post by btlotfinia on 2006-07-26
I had tried compiling directly before, but without luck. Double checked what I had installed, and saw that I lacked "checkinstall." It compiled and installed quickly. Now I'm just having issues with the actual program. ;)

---

### Post by BIGtrouble77 on 2006-07-27
I compiled an AMD64 version if anyone wants it.

EDIT: my package was broken so I removed it.

When I compiled I had to change it from an x86_64 arch to amd64 for it to properly compile.  Make sure you remove conky if you already have it installed before installing this version.

---

### Post by ubuntuuser on 2006-07-27
The link to the deb-file seems to be dead, at least I couldn't access the file. I compiled it from source and created my own deb. You can get it [here.]("http://rapidshare.de/files/27253981/conky-1.4.2_1.4.2-1_i386.deb.html")

---

### Post by Rexbron! on 2006-07-29
Care to elaborate on your problems Btlotfinia?

---

### Post by FlyingCheese on 2006-07-29
I'm running Ubuntu on a Pentium 2 laptop, how does this app fare on low resource computers? I would hate to try to install this program only to find it brings the computer down to a crawl. Thanks.

Looks like a great HowTo.

---

### Post by Rexbron! on 2006-07-29
> **FlyingCheese said:**
> I'm running Ubuntu on a Pentium 2 laptop, how does this app fare on low resource computers? I would hate to try to install this program only to find it brings the computer down to a crawl. Thanks.

Looks like a great HowTo.

It is a text based program, and you can set the polling intervals. There should be absoultly no problem interms of hardware. (I also recomend using Xubuntu for older hardware).

---

### Post by 5-HT on 2006-07-29
> **FlyingCheese said:**
> I'm running Ubuntu on a Pentium 2 laptop, how does this app fare on low resource computers? I would hate to try to install this program only to find it brings the computer down to a crawl. Thanks.

Looks like a great HowTo.

> **Rexbron! said:**
> It is a text based program, and you can set the polling intervals. There should be absoultly no problem interms of hardware. (I also recomend using Xubuntu for older hardware).

Just to add to Rexbron's post: While conky is a pretty light system monitor, the graph, tail, font ($font, not the overal font conky is set for), and top objects are fairly resource intensive as compared to the rest of the application.

If you don't use any graphs, mix fonts around, or use the tail or top options conky will be really good on resources.

---

### Post by FlyingCheese on 2006-07-30
Thanks, I'll install this when I get back home in about a week.

---

### Post by loserboy on 2006-07-31
```
loser@loser-desktop:~/Desktop$ sudo dpkg -i conky-1.4.2_1.4.2-1_amd64.deb
(Reading database ... 122239 files and directories currently installed.)
Unpacking conky-1.4.2 (from conky-1.4.2_1.4.2-1_amd64.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing conky-1.4.2_1.4.2-1_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/conky-1.4.2/README')

```



someone here had a similar prob and they were told to "Try compiling Conky from source and use checkinstall instead of make install."

...how do I go about doin that, or is that what im suppose to do

Edit: I think there maybe something wrong with the deb

---

### Post by BIGtrouble77 on 2006-08-01
> **loserboy said:**
> 
Edit: I think there maybe something wrong with the deb
That's the version I compiled.  I removed conky from my system and tried it again and am also having issues.  I apologize, I'm gonna edit my other post.  It's actually very easy to compile to i'd just do that for now.

---

### Post by Zottan on 2006-08-01
for amd64 that i compiled i you get error use "dpkg --force-architecture -i .deb"
[http://rapidshare.de/files/27769327/conky-1.4.2_1.4.2-1_x86_64.deb.html](http://rapidshare.de/files/27769327/conky-1.4.2_1.4.2-1_x86_64.deb.html)

is compiled for amd only that the deb give this error , using make install from the source works fine...

---

### Post by Gehaktbal on 2006-08-01
I just installed conky with the deb in the first post. But Al my other icons in gnome disappear. When i go over them with my mouse (where they are supposed to be) they appear again only to vanish after a few seconds. How can i change this?

->

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
on_bottom yes

---

### Post by kerry_s on 2006-08-01
hmmm, i just installed the one from the repo's and added the line in xorg.conf(Load "dbe"). i launch it with a script so it starts on top of the background.
conky start script->
```
#!/bin/sh

sleep 10
conky


```

my .conkyrc->
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
on_bottom no

# Xft font when Xft is enabled
xftfont Sans:size=12

# Text alpha when using Xft
xftalpha 1.0

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
               Conky
${color white}CPU:${color white} ${freq} ${color white}mhz / Temp:${color white}$acpitemp ${color white}C 
${color white}Disk I/O:${color white} ${diskio}    ${color white}Uptime:${color white} $uptime 
${color white}Processes:${color white} $processes  ${color white}Running:${color white} $running_processes
${color white}CPU Usage:${color white} $cpu% ${color white}${cpugraph  20, 125 ffffff 0000ff}
${color white}RAM Usage:${color white} $mem/$memmax ${color white}- ${color white}$memperc% ${color white}${membar}
${color white}Swap Usage:${color white} $swap/$swapmax ${color white}- ${color white}$swapperc% ${color white}${swapbar}
${color white}File systems: / ${color white}${fs_used /}/${fs_size /} ${color white}${fs_bar /}

${color}Name              PID     CPU%   MEM%
${color green} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color green} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color green} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color green} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color green} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}

${color white}Networking:
 Down:${color white} ${downspeed eth0} k/s${color white} ${offset 80}Up:${color white} ${upspeed eth0} k/s
${color white}${downspeedgraph eth0 20,150 ff0000 0000ff} ${color white}${upspeedgraph eth0 20,150 0000ff ff0000}

${color white}Netstat
${color green}${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
${color white}Remote Address ${alignr} Local Service/Port
${color green} ${tcp_portmon 1 65535 rhost 0} ${alignr} ${tcp_portmon 1 65535 lservice 0}
${color green} ${tcp_portmon 1 65535 rhost 1} ${alignr} ${tcp_portmon 1 65535 lservice 1}
${color green} ${tcp_portmon 1 65535 rhost 2} ${alignr} ${tcp_portmon 1 65535 lservice 2}
${color green} ${tcp_portmon 1 65535 rhost 3} ${alignr} ${tcp_portmon 1 65535 lservice 3}
${color green} ${tcp_portmon 1 65535 rhost 4} ${alignr} ${tcp_portmon 1 65535 lservice 4}
${color green} ${tcp_portmon 1 65535 rhost 5} ${alignr} ${tcp_portmon 1 65535 lservice 5}
${color green} ${tcp_portmon 1 65535 rhost 6} ${alignr} ${tcp_portmon 1 65535 lservice 6}
${color green} ${tcp_portmon 1 65535 rhost 7} ${alignr} ${tcp_portmon 1 65535 lservice 7}
${color green} ${tcp_portmon 1 65535 rhost 8} ${alignr} ${tcp_portmon 1 65535 lservice 8}
${color green} ${tcp_portmon 1 65535 rhost 9} ${alignr} ${tcp_portmon 1 65535 lservice 9}
${color green} ${tcp_portmon 1 65535 rhost 10} ${alignr} ${tcp_portmon 1 65535 lservice 10}



```

i also made a on/off switch for when i want to try different looks/colors/settings/position->
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky


```

---

### Post by loserboy on 2006-08-01
> t's actually very easy to compile to i'd just do that for now.

I'd love to learn how to compile, how do i do that?

---

### Post by spiral777 on 2006-08-01
I finally got it set up to work just the way I want it, except for 1 small problem. I use it in a window, because my backgrounds are crazy and I couldn't find a nice text color to use. 

Is it possible to set it up to automatically open in workspace 4 in ubuntu?

---

### Post by Catsworth on 2006-08-01
Hi Guys,

I've got conky up and running nicely, I've even managed to strip out some of the stuff that I don't want (haven't thought about 'adding' anything yet!).

I'm having a small problem though.....

When I open an application in Ubuntu (Firefox for example) I get a 'tab' (for want of a better word) in the panel at the bottom of my desktop, clicking on this brings that application to the fore.  I have a 'tab' for conky - ideally I just want conky to sit on my desktop and not have a 'tab' on the panel, is that possible?  Thanks.

---

### Post by 5-HT on 2006-08-01
> **loserboy said:**
> I'd love to learn how to compile, how do i do that?

Steps 1 & 3 in this HowTo document how to download required depencies and compile conky (lm-sensors is optional). 

If you're having dependency issues, the following thread may be of help:
[http://www.ubuntuforums.org/showthread.php?t=139262](http://www.ubuntuforums.org/showthread.php?t=139262)

---

### Post by loserboy on 2006-08-02
> 
Steps 1 & 3 in this HowTo document how to download required depencies and compile conky (lm-sensors is optional).


that doesnt seem to work for amd64 though. 
and someone has posted one for 64 but the deb doesnt work for me

---

### Post by 5-HT on 2006-08-02
> **loserboy said:**
> that doesnt seem to work for amd64 though. 
and someone has posted one for 64 but the deb doesnt work for me

Sorry, I missed the earlier post you made. I'm not running a 64-bit system so I can't be of much help.
Posting the the compile errors you're getting may help someone track down what the problem is.

HTH

---

### Post by kpkeerthi on 2006-08-03
Thanks for the How To. This is my first build-from-source in linux ever. Conky rocks!

---

### Post by John.Michael.Kane on 2006-08-03
Is there a version/howto: for 64bit users?

---

### Post by ConstableRoark on 2006-08-03
Is there any way to prevent conky from starting again when one logs out of one session and into another?  In that scenario, the conky from the first is not killed (but is asleep), while the second conky heavily uses the CPU.  I regularly switch from Xorg to XGL and vice versa and this problem is really starting to bug me (having to kill it manually, that is).  I don't recall this happening with previous versions of conky.

---

### Post by seldon77 on 2006-08-04
> **ConstableRoark said:**
> Is there any way to prevent conky from starting again when one logs out of one session and into another?  In that scenario, the conky from the first is not killed (but is asleep), while the second conky heavily uses the CPU.  I regularly switch from Xorg to XGL and vice versa and this problem is really starting to bug me (having to kill it manually, that is).  I don't recall this happening with previous versions of conky.

Just thinking laterally... i wonder if you could put in your startup scripts:
```

killall conky
conky

```

or something like that... i dunno...

As for the guy earlier who had the 'tab' appear in the workspace - if you use the .conkyrc I provided you wont get the 'tab'

---

### Post by BigBastard on 2006-08-04
i also made a on/off switch for when i want to try different looks/colors/settings/position->

Code:

#!/bin/sh 
# click to start, click to stop 
if pidof conky | grep [0-9] > /dev/null 
then exec killall conky 
else 
exec conky 
fi

I tried this and while it successfully "kills" conky, it doesn't successfully start it again.
But if I use conky at the command line it starts.....

Hints?

BB

---

### Post by kerry_s on 2006-08-04
That's my code but that one's screwed. It should be this->
```
#!/bin/sh

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky


```

---

### Post by ConstableRoark on 2006-08-04
Thanks for the reply guys and gals.

---

### Post by John.Michael.Kane on 2006-08-05
Has anyone got this to work under dapper64? it seems all these post here are from 32bit users.

---

### Post by greenbmw530i on 2006-08-06
Great HOWTO! I've always wanted to get Conky setup properly, but never could. Thanks to your HOWTO, I've got a great lookin' Conky on my desktop. 

However, I have one question...I use XGL/Compiz and use the "fade" plugin with it. The fade plugin for XGL/Compiz darkens a window that is not selected to put it out of focus and put it in the background. The problem is that it darkens Conky when a window is selected, which makes it seem as if it's not blended with my wallpaper...which is ugly. Is there some way I can exempt Conky from fading in XGL/Compiz? I've attatched screenshots to show you what it looks like when it's faded and what it looks like when it's not.

---

### Post by simplyw00x on 2006-08-07
> **Johan! said:**
> I

The real problem is the XMMS output... see the next screenshot:

Sometimes, the XMMS information appears multiple times. I use xmms-infopipe to create the data.

Who can help me fix these small problems?
?Well I can't fix it, but I can tell you it's infopipe's problem. If you 'watch -n 1 cat /tmp/whatevertheinfopipeiscalled' you'll see it sometimes screws up and puts more than one copy of the info in that file. There isn't really a workaround and I'd suggest not using infopipe or not using xmms.

> **mtpadilla said:**
> 
HOWEVER, I have three problems:
1) I get the errors
Conky: /home/mtp/.conkyrc: 15: no such configuration: 'own_window_hints'
Conky: can't load font 'arial'
2) It looks kind of crappy, with thick black lines around every character.
3) It only shows up on one of my four desktops.

1) Are you using the latest conky? Only the newest version has the own_window_hints property. As to the arial problem, make sure that arial is actually on your system.

2) draw_outline no

---

### Post by Rexbron! on 2006-08-07
> **greenbmw530i said:**
> Great HOWTO! I've always wanted to get Conky setup properly, but never could. Thanks to your HOWTO, I've got a great lookin' Conky on my desktop. 

However, I have one question...I use XGL/Compiz and use the "fade" plugin with it. The fade plugin for XGL/Compiz darkens a window that is not selected to put it out of focus and put it in the background. The problem is that it darkens Conky when a window is selected, which makes it seem as if it's not blended with my wallpaper...which is ugly. Is there some way I can exempt Conky from fading in XGL/Compiz? I've attatched screenshots to show you what it looks like when it's faded and what it looks like when it's not.

Maybe someone can correct me, but my best sugestion is to file a bug report in malone and upstream in conky and xgl and see if a dev will try and solve your problem.

But if any one else can solve it, by all means post!

---

### Post by greenbmw530i on 2006-08-07
Thanks for the reply, Rexbron! I'm not so sure that it's a bug, since the effect is just the result of XGL doing it's job. I was just wondering if there was some sort of way to exempt Conky from the XGL fade effect.

---

### Post by Rexbron! on 2006-08-07
I do not use xgl or compiz myself but a quick google search turned up a ubuntu thread with someone having a problem with gdesklets. Turns out that there is an exclude feature for compiz for precisely this problem.

From: [http://www.ubuntuforums.org/archive/index.php/t-148351-p-2.html](http://www.ubuntuforums.org/archive/index.php/t-148351-p-2.html)

> hi, i have gdesklets in ubuntu with xgl/compiz but its really irritating to have them have a shadow like when they are not in focus. is it possible to disable this shadowing of windows in compiz?

thanx
You can disable the Trailfocus plugin, from what I can see, and that would take off the "shadowing" effect entirely.

Alternatively, if you wish to keep trailfocus on but disable the effect on certain windows, read this page (and Especially pay attention to the Trailfocus section): [https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29](https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz?highlight=%28compiz%29)

It should help tell you how to setup the "exclude" field to prevent certain programs from being affected (I.E., I have my video players in the exclude list).


I did a quick look at the fade plugin, you probably want to disable "desktop" under the window_types.

This maybe another thing to add to the guide.

UPDATE: Looked a little bit closer at the wiki document, turns out that desktop is not  enabled by default, so still check for it but maybe you should take out "unknown" as well, seeing as I do not know how conky is classifed.

Also, would you mind sharing your .conkyrc file?

---

### Post by greenbmw530i on 2006-08-07
I already have "desktop" and "unknown" de-selected in the XGL fade plugin. Oh well, it's not a biggie -- I can live with it. As for my .conkyrc file...I tried to attatch it here but it told me it was an invalid file :-k  So I'll just paste it in here:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 60
gap_y 40

# stuff after 'TEXT' will be formatted on screen

TEXT
${color CC0D00}SYSTEM OVERVIEW
${color CC0D00}${hr}
${color FFFF00}Host: ${color white}$nodename
${color FFFF00}Kernel: ${color white}$kernel ${machine} (Ubuntu Dapper)
${color FFFF00}Uptime: ${color white}$uptime
${color FFFF00}Load: ${color white}$loadavg
${color FFFF00}Battery: ${color white}${battery}

${color CC0D00}CPU USAGE
${color CC0D00}${hr}
${color FFFF00}CPU Usage: ${color white}${cpu}% $cpubar
${cpugraph}
${color FFFF00}RAM Usage: ${color white}$mem/$memmax - $memperc% $membar
${color FFFF00}Swap Usage: ${color white}$swap/$swapmax - $swapperc% $swapbar
${color FFFF00}Processes: ${color white}$processes ${color FFFF00}Running: ${color white} $running_processes

${color CC0D00}NETWORKING
${color CC0D00}${hr}
${color FFFF00}Down: ${color white}${downspeed ath0} k/s ${offset 110}${color FFFF00}Up: ${color white}${upspeed ath0} k/s
${downspeedgraph ath0 32,200} ${upspeedgraph ath0 32,200}
${color FFFF00}Signal: ${color white}${linkstatus ath0}

${color CC0D00}FILESYSTEMS
${color CC0D00}${hr}
${color FFFF00}Root:        ${color white}${fs_used /}/${fs_size /}        ${fs_bar 6 /} 
${color FFFF00}WinXP:       ${color white}${fs_used /media/hda1}/${fs_size /media/hda1}        ${fs_bar 6 /media/hda1}

```

---

### Post by OffHand on 2006-08-08
Well, it was a pain in the *** to get a working configuration.
It was worth it though. It's awesome. 
Here is a pic of my conky. (That sounds just weird haha)

---

### Post by lime4x4 on 2006-08-08
can't get the on-off kill switch to work

this is what i get when i try to run it

Details: Failed to execute child process "/home/john/conky" (No such file or directory)

I have the file saved in /home/john/conky on-off

and that is where i have the launcher pointed to

---

### Post by lime4x4 on 2006-08-08
also how do u get the graphs to show in different colors

---

### Post by greenbmw530i on 2006-08-08
> **lime4x4 said:**
> also how do u get the graphs to show in different colors

Just add the color 'tag' in front of the graph in your .conkyrc. Refer to my .conkyrc on page 9 to see exactly how to do it.

---

### Post by loserboy on 2006-08-09
i'm having problems with my sensors,  

temp is showing 40 and never changes
during boot it fails "setting sensor limits"

is it a problem with lm-sensors? i followed the howto

Edit: ok I fixed the failed "setting sensor limits", but i still can't get my temp readout to change

---

### Post by simplyw00x on 2006-08-09
A replacement for this very involved kill script you all seems to be using:
killall -SIGUSR1 conky
(from `man conky`)

---

### Post by kerry_s on 2006-08-09
> **lime4x4 said:**
> can't get the on-off kill switch to work

this is what i get when i try to run it

Details: Failed to execute child process "/home/john/conky" (No such file or directory)

I have the file saved in /home/john/conky on-off

and that is where i have the launcher pointed to

You can't have no space in the name(conky on-off) other wise it's just looking for conky, change it to> conky-on-off or your launchline to> /home/john/conky\ on-off < if you want to keep the space. Make sure you have set it executable(right click it> properties>permissions> check execute. Also you can make it a hidden file by adding "." to the front (example: .conky-on-off)

Also take out the "fi" at the bootom it throws up a xserver error.
Here's what i run know->
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky
```

---

### Post by lime4x4 on 2006-08-09
ok did what u said and changed my file to match yours but now when i click on the icon on my desktop for it nothing happens

---

### Post by ephman on 2006-08-09
> **loserboy said:**
> i'm having problems with my sensors,  

temp is showing 40 and never changes
during boot it fails "setting sensor limits"

is it a problem with lm-sensors? i followed the howto

Edit: ok I fixed the failed "setting sensor limits", but i still can't get my temp readout to change

i think the "setting sensor limits" deals with lmsensors.  can you give some system specs?  if you have a name brand the model, or if you put it together yourself your motherboard.  that'll help.

i know that if ya have a dell the i8k drivers will work with conky, just need to modify the conkyrc file to:

Temp: ${i8k_cpu_temp}   Fan: ${i8k_right_fan_status}

if you read the [variables page]("http://conky.sourceforge.net/variables.html") you can get a whole bunch of options.

thanks for the bandwidth,
ephman

---

### Post by loserboy on 2006-08-10
> if you have a name brand the model

AMD athlon64
asus mobo - A8NE

one thing i noticed is under "Temp: ${Temp: ${acpitemp}"
should I change that to adt746xcpu or something...just from glancing at that link

---

### Post by kerry_s on 2006-08-10
> **lime4x4 said:**
> ok did what u said and changed my file to match yours but now when i click on the icon on my desktop for it nothing happens

Are you sure you made it executable? Is your launcher pointing to it? When you click on the file you created does it launch/kill conky?

---

### Post by LordMau on 2006-08-10
> **greenbmw530i said:**
> Great HOWTO! I've always wanted to get Conky setup properly, but never could. Thanks to your HOWTO, I've got a great lookin' Conky on my desktop. 

However, I have one question...I use XGL/Compiz and use the "fade" plugin with it. The fade plugin for XGL/Compiz darkens a window that is not selected to put it out of focus and put it in the background. The problem is that it darkens Conky when a window is selected, which makes it seem as if it's not blended with my wallpaper...which is ugly. Is there some way I can exempt Conky from fading in XGL/Compiz? I've attatched screenshots to show you what it looks like when it's faded and what it looks like when it's not.

Try to play around with the ```
own_window_type
``` setting. You can set it to **desktop** to make it sticky across all workspace and compiz ignores the window from effects, such as fade and wobble. Still it still seems quirky on my xgl/compiz system, as conky sometimes justs disappears. YMMV and may be more consistent on your setup.

---

### Post by kerry_s on 2006-08-10
My bag, somethings changed during the updates. Here is the code that is working for me and not throwing any errors in the .xsession-errors file.

```
#!/bin/sh
if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky
 fi
```

Sorry about that i only just realized it had stopped working.

---

### Post by ephman on 2006-08-10
> **loserboy said:**
> AMD athlon64
asus mobo - A8NE

one thing i noticed is under "Temp: ${Temp: ${acpitemp}"
should I change that to adt746xcpu or something...just from glancing at that link

sure give it a shot.  are you 100% that the 40 degrees is not accurate.  my machine is pretty stable.  you can test it by running a stress test and maxin g out the cpu, if it doesn't budge after a few minutes then you'll you have a temp issue.

thanks,
ephman

---

### Post by loserboy on 2006-08-10
> sure give it a shot. are you 100% that the 40 degrees is not accurate.

ya know it might be i guess, its just that even before i configured lm-sensors it was showing 40

I haven't setup a kill switch for conky yet so i have to restart everytime i change stuff...guess i better get that out of the way 1st

---

### Post by Mandor on 2006-08-10
It would be nice if ubuntu maintainers of that package finally update it. Any idea how such request can be addressed?

---

### Post by simplyw00x on 2006-08-10
> I haven't setup a kill switch for conky yet so i have to restart everytime i change stuff...guess i better get that out of the way 1st
killall -SIGUSR1 conky

*sigh*

---

### Post by simplyw00x on 2006-08-10
> It would be nice if ubuntu maintainers of that package finally update it. Any idea how such request can be addressed?
[https://wiki.ubuntu.com/MOTU/Packages/Candidates](https://wiki.ubuntu.com/MOTU/Packages/Candidates)

- suggest conky there.

---

### Post by loserboy on 2006-08-10
> killall -SIGUSR1 conky

*sigh*

:) sorry i don't know very much about this, can i just make a new launcher with that command

or do i make an empty file then make it executable?

reason i ask is cuz im at work and can't test it till i get home

---

### Post by Kuraboy on 2006-08-10
Hi!

nice how-to, thnx :)

I have a simpel conky ;) just what I need, but I dont understand something...

it shows a different usage of ram than what Ubuntu shows, why?

conky  - 97%
ubuntu - 42,8 %

I heared somewhere that it calculates in a different matter? so how dose it works and how can I make it show the same usage as Ubuntu dose?

thnx

EDIT:
I have another problem, and it seems that many have it too, when ever I click the button show desktop, conky minimizez and I must type wmctrl -a conky to show it again, isnt there another and better solution?

---

### Post by simplyw00x on 2006-08-10
>  sorry i don't know very much about this, can i just make a new launcher with that command
Either way will do.

---

### Post by Kuraboy on 2006-08-12
no one knows how I can solve the ram usage thing? :(

---

### Post by Kashirigi on 2006-08-14
I can't answer the RAM usage thing, but I can solve a problem that was plaguing me for a long time in XFCE.

In XFCE, conky wouldn't write to the root window correctly. Setting it to be its own window worked, but if you had the composite manager showing shadows, it would be ugly, and against the spirit of conky.

After peering through the man pages, for XFCE, make sure you this in your .conkyrc

own_window yes
own_window_type override
own_window_transparent yes


the key is the override.

Goodbye adesklets.

---

### Post by spockrock on 2006-08-14
hey I have a question I would like to add a couple of temperatures from my configured lm-sensors to conky but I am not sure how.

when I enter sensors in terminal I get this
```

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.33 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +1.17 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +6.56 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.95 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +11.71 V  (min = +11.39 V, max = +12.61 V)
-12V:     -13.74 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -1.24 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +4.97 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.10 V
fan1:     1110 RPM  (min =    0 RPM, div = 8)
fan2:     2008 RPM  (min = 3013 RPM, div = 8)          ALARM
fan3:     4115 RPM  (min = 3013 RPM, div = 8)
CPU Temp:    +33°C  (low  =   +15°C, high =   +40°C)   sensor = diode
PWMIC Temp:
             +36°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Nforce 4 Temp:
             +48°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor

ds1621-i2c-1-4e
Adapter: SMBus nForce2 adapter at 1c40
temp:      +0.00°C  (low  =  +0.0°C, high =  +0.0°C)


```

The two Temps I would like to add are pwmic temp and the nforce 4 temp but I have no idea what variables to call I am going throught the man pages but I cant seem to find it.

---

### Post by spockrock on 2006-08-14
never mind I figured it out.

and thanks for the great guide.

---

### Post by ophanim on 2006-08-14
> Great HOWTO! I've always wanted to get Conky setup properly, but never could. Thanks to your HOWTO, I've got a great lookin' Conky on my desktop.

However, I have one question...I use XGL/Compiz and use the "fade" plugin with it. The fade plugin for XGL/Compiz darkens a window that is not selected to put it out of focus and put it in the background. The problem is that it darkens Conky when a window is selected, which makes it seem as if it's not blended with my wallpaper...which is ugly. Is there some way I can exempt Conky from fading in XGL/Compiz? I've attatched screenshots to show you what it looks like when it's faded and what it looks like when it's not.

Try:

```
own_window yes
own_window_type normal
own_window_hints undecorated,below,sticky
```

---

### Post by Ahriman on 2006-08-15
> **Kuraboy said:**
> no one knows how I can solve the ram usage thing? :(

Can you post or attach your .conkyrc for us to look at? It could be as simple as a slight spelling error or referencing the wrong function in the RAM section.

---

### Post by kurup on 2006-08-16
> **arrizaba said:**
> I've got the "dbe" module but conky still flickers a bit. I changed the refresh time to 1 min not to make it so annoying. 
Can the flickering be completely eliminated? 
Btw, I use Compiz as window manager.

I got (I think) a nice config for my conky.

Thats a brilliant looking conky config! Can you please share the .conkyrc file?

---

### Post by Kuraboy on 2006-08-16
> **Ahriman said:**
> Can you post or attach your .conkyrc for us to look at? It could be as simple as a slight spelling error or referencing the wrong function in the RAM section.

here is my .conkyrc, I have looked at others and it seems okay.

```

# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 5
border_margin 4
border_width 1
default_color grey
default_shade_color black
default_outline_color black
alignment bottom_left
gap_x 1
gap_y 1
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer no

TEXT
${color white}$alignc$sysname $kernel @ ${freq_g}GHz
${color white}$alignc${exec whoami} @ $nodename
$color$stippled_hr
${color}Date: ${color white}${time %A,%d %B}
${color}Uptime: ${color white}$uptime
$color$stippled_hr
${color}CPU:        ${color white} ${cpu cpu1}% ${cpubar cpu1}
${color}RAM:        ${color white} $memperc% ${membar}
${color}Swap:       ${color white} $swapperc% ${swapbar}
$color$stippled_hr
${color}Root:       ${color white} ${fs_free /}   ${fs_bar /}
${color}Lin2:       ${color white} ${fs_free /media/hda2}   ${fs_bar /media/hda2}
${color}WinXP:      ${color white} ${fs_free /media/hda1}   ${fs_bar /media/hda1}
${color}WinLin:     ${color white} ${fs_free /media/hda5}   ${fs_bar /media/hda5}
${color}BigStorage: ${color white} ${fs_free /media/hdb1}  ${fs_bar /media/hdb1}
${color}TheHeart:   ${color white} ${fs_free /media/hdd1}   ${fs_bar /media/hdd1}

```

---

### Post by seldon77 on 2006-08-18
Thanks everyone for the further followup questions and suggestions.

I've made some updates to the how-to page to add everyones ideas. In particular, i've added the instructions for XFCE.

Also, I've added
```
${execi 60 wmctrl -a conky}
```
to .conkyrc

As people have said, conky has a bug where in some circumstances, like after a screensaver has come on or if you have hit the 'show desktop' button that conky will disappear. I think that code will ensure that conky will make sure that it is on the root desktop every 60 seconds. I've tried it for a while, and it seems to work, but i'll listen to feedback on it.

Note you will need the 'wmctrl' program, which I have now also put into the dependencies, will need to be installed from universe.

---

### Post by seldon77 on 2006-08-18
hey is there a solution to the XGL/Compiz issue?

if there is, i'll add it to the how-to

---

### Post by jason.b.c on 2006-08-18
Got a problem...!!!    This package dosen't exist for me....

> jason@Hp-Vectra-VL:~$ sudo apt-get --assume-yes install libxext-dev lm-sensors build-essential checkinstall wmctrl
Password:
Reading package lists... Done
Building dependency tree... Done
Package libxext-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package libxext-dev has no installation candidate
jason@Hp-Vectra-VL:~$


How do i get it otherwise..??](*,)

---

### Post by notjohn101 on 2006-08-18
cant get it to double buffer

boys@linux:~$ conky
Conky: /home/boys/.conkyrc: 43: no such configuration: 'borders'
Conky: forked to background, pid is 5294
boys@linux:~$ 
Conky: desktop window (1200089) is subwindow of root window (44)
Conky: window type - normal
Conky: hint - undecorated
Conky: hint - skip_taskbar
Conky: drawing to created window (2a00002)
Conky: failed to set up double buffer
Conky: drawing to single buffer

---

### Post by OffHand on 2006-08-18
> **notjohn101 said:**
> cant get it to double buffer

boys@linux:~$ conky
Conky: /home/boys/.conkyrc: 43: no such configuration: 'borders'
Conky: forked to background, pid is 5294
boys@linux:~$ 
Conky: desktop window (1200089) is subwindow of root window (44)
Conky: window type - normal
Conky: hint - undecorated
Conky: hint - skip_taskbar
Conky: drawing to created window (2a00002)
Conky: failed to set up double buffer
Conky: drawing to single buffer

Did you do step 7 of this faq?

[http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)

---

### Post by notjohn101 on 2006-08-18
thx that did the trick...must of missed it

---

### Post by jason.b.c on 2006-08-18
> **jason.b.c said:**
> Got a problem...!!!    This package dosen't exist for me....



How do i get it otherwise..??](*,)

So could someone give me some advise on my problem..?:D

---

### Post by jason.b.c on 2006-08-19
Why can't i get this package..??  , I just ran sudo update...I don't understand what i'm missing..

> jason@Hp-Vectra-VL:~$ sudo apt-get --assume-yes install libxext-dev lm-sensors build-essential checkinstall wmctrl
Password:
Reading package lists... Done
Building dependency tree... Done
Package libxext-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package libxext-dev has no installation candidate
jason@Hp-Vectra-VL:~$

](*,)

---

### Post by Rexbron! on 2006-08-19
First try 
```
sudo apt-get update 
```


If that does not work, make sure that the universe repositories are uncommented in you sources.list file.

EDIT: What version of Ubuntu are you using? (Your profile says 5.10)

---

### Post by jason.b.c on 2006-08-19
> **Rexbron! said:**
> First try 
```
sudo apt-get update 
```
I've done that several times...

> If that does not work, make sure that the universe repositories are uncommented in you sources.list file.
They are...As far as i know everything is enabled..

> EDIT: What version of Ubuntu are you using? (Your profile says 5.10)

Breezy..! , v5.10   Does that matter..??

---

### Post by kencoe on 2006-08-19
Great Post!!!

Finally have a nice looking script setup, but...

For some reason Conky will switch me to the workspace that it was started in ever thirty seconds, no matter what I am doing. don't think it is refresh as conky is refreshing in five second intervals. Any ideas would be helpful. 

This one is kinda buggin me. It's never good to suddenly be typing into the wrong app or term window.

Any clues would be helpful. Config listed below.

...
${execi 30 wmctrl -a conky}
...

Edit:
Just re-read the man for wmctrl, and realized the problem. Had .conky open in gedit in WS-3 and conky Website in WS-1. wmctrl was finding Conky windows everywhere. Is the maybe a way to select in wmctrl by process ID or name instead of window name? Here's a screenshot of mine in case you want to look...

---

### Post by seldon77 on 2006-08-20
> **kencoe said:**
> Great Post!!!
${color #7f8ed3}${execi 30 tail -n3 /var/log/messages | fold -w48}
${color #436EEE}$stippled_hr
${execi 30 wmctrl -a conky}

Just re-read the man for wmctrl, and realized the problem. Had .conky open in gedit in WS-3 and conky Website in WS-1. wmctrl was finding Conky windows everywhere. Maybe there is a way to do it by process?

Yeah... its the ${execi 30 wmctrl -a conky} code... that will run every 60 seconds and make sure conky is on the root window.

hmmm... its a catch 22... if that code isn't there then sometimes conky disappears (ie. after screensaver runs, etc sometimes). but you say it causes trouble if you use a few different workspaces? hmmm....

I don't know enough about the wmctrl code. could this be fixed by making conky sticky across all workspaces? its the windows_hint code in .conkyrc.

I don't have enough time to look at it now - does anyone have any ideas? if it causes problems remove the wmctrl code from .conkyrc - but I'm hoping theres some way to keep it in.

---

### Post by jason.b.c on 2006-08-21
> **jason.b.c said:**
> Why can't i get this package..??  , I just ran sudo update...I don't understand what i'm missing..

](*,)

Well i guess i'll never have Conky , I just can't figure it out , How can everybody else get that package but i can't..???

---

### Post by Neo40 on 2006-08-21
Hi,

I have conky working fine but there is a small problem. In my ~.conkyrc I have this part:

```
${color}Name                CPU%     MEM%
${color green} ${top  name 1}   ${top cpu 1}   ${top mem 1}
${color green} ${top  name 2}   ${top cpu 2}   ${top mem 2}
${color green} ${top  name 3}   ${top cpu 3}   ${top mem 3}
${color green} ${top  name 4}   ${top cpu 4}   ${top mem 4}
${color green} ${top  name 5}   ${top cpu 5}   ${top mem 5}

```
The problem is the text is not always align. Here is an example what I mean:

```

Name        CPU%       MEM%
bittorent   47.12        23.55
Xorg      17.44        10.15
conky       0.33         0.49
xfce4-panel  0.33         2.47
xchat       1.67         2.44
```

So, how can I align columns correctly? 
Thanks!

---

### Post by kencoe on 2006-08-21
jason.b.c,
Stop bangin your head already! You're makin ME hurt...

Try two things for me, man. 

try comparing your sources.list to the one at this thread [http://www.ubuntuforums.org/showthread.php?t=92672]("http://www.ubuntuforums.org/showthread.php?t=92672")


then run-- sudo apt-get update
and 
then run-- sudo apt-get install xlibs

........
See if that helps

---

### Post by kencoe on 2006-08-21
> **Neo40 said:**
> So, how can I align columns correctly?

Do You have the string "use_spacer yes" in your .conkyrc ?

---

### Post by Neo40 on 2006-08-21
> **kencoe said:**
> Do You have the string "use_spacer yes" in your .conkyrc ?

Yes, I have "use_spacer yes" and it doesnt help much.

---

### Post by jason.b.c on 2006-08-21
> **kencoe said:**
> jason.b.c,
Stop bangin your head already! You're makin ME hurt...

Try two things for me, man. 

try comparing your sources.list to the one at this thread [http://www.ubuntuforums.org/showthread.php?t=92672]("http://www.ubuntuforums.org/showthread.php?t=92672")


then run-- sudo apt-get update
and 
then run-- sudo apt-get install xlibs

........
See if that helps


Great , Now it's even worse..

> jason@Hp-Vectra-VL:~$ sudo apt-get update
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Get:5 [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [767kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [116kB]
99% [6 Packages gzip 0] [Query] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Sub-process gzip returned an error code (1)
99% [7 Packages gzip 0] [Query] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Hit [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Get:8 [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages
Hit [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages
Fetched 195B in 7s (27B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
jason@Hp-Vectra-VL:~$



> jason@Hp-Vectra-VL:~$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package xlibs
jason@Hp-Vectra-VL:~$


And here's the list i have now..
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
#
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## plf mirror. use if primary repo is offline
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

##
## Use the following repos ONLY if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## official wine apt repository
##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main


## opera web browser
## deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## skype
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

](*,) ](*,)

---

### Post by seldon77 on 2006-08-22
> **jason.b.c said:**
> Well i guess i'll never have Conky , I just can't figure it out , How can everybody else get that package but i can't..???

You probably don't need that program. I included that one in the apt-get mostly for people who want to compile conky themselves.

just try skipping that particular file and going on from there.

---

### Post by calvinthomas on 2006-08-22
This looks great except for I have a dark background which I really want to keep, how can I brighten conky up? (or perhaps make the text bolder!)

Calv

---

### Post by calvinthomas on 2006-08-22
Ok, i've fixed the colour issue but cannot at all find a way to get it into the top right corner (having align set as in the original post puts it slightly left of centre and a little bit too low.)

I think the reason is that i'm in XGL with compiz, can anyone tell me how I can set it into the right hand corner as in the instructions?

My resolution is 1280 x 800 if that makes any difference.

Calv

---

### Post by calvinthomas on 2006-08-22
So sorry for the triple post in a row, I have found an odd quirk, if I open it up from a terminal, it opens in the correct place. It seems to be a problem with the startup, is there a way to get it to open in a terminal on startup (and then close the terminal down?)

Calv

---

### Post by Camino on 2006-08-23
Hi,
thanks for this nice tutorial...never thought that such a cool monitor exists :)

Just got one small problem. The memory usage is not correctly shown (have a look at the attached screenshot)

Anybody else noticed this too or is just me ?

Bye

---

### Post by 0okami on 2006-09-01
i must be doing something wrong... Its still flickering and double buffer fails to load. 

xorg.conf: 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load 	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	# these lines were added by ookami to implement a second monitor
	Option          "TwinView" "on"
	#Option         "MetaModes" "1280x1024,1280x1024"
	#Option "MetaModes" "1024x768 +0+0, 1024x768 +1024+0;"
	Option 		"MetaModes" "1280x1024,1280x1024,1280x1024"
	Option          "SecondMonitorHorizSync" "30-81"
	Option          "SecondMonitorVertRefresh" "56-75"
	Option          "TwinViewOrientation" "RightOf"   
	Option		"NoLogo" "true"
	#end dual monitor
EndSection


########adding 2nd vid card
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:10:0"   
EndSection
############ end 2nd vid card


Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

################ added monitor
Section "Monitor"
	Identifier	"3rd_monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection
###############end added



Section "Screen"
	Identifier	"screen1"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200 Ultra]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection



######### added  screen specs
Section "Screen"
	Identifier	"screen2"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"3rd_monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
######## end added



Section "ServerLayout"
	Identifier	"Layout0"
	Screen		"screen1"
	Screen		"screen2" RightOf "screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama""true"
EndSection


Section "DRI"
	Mode	0666
EndSection

```


.conky_raidmax
(on Conky 1.4.2 compiled Jun 12 2006)
```
# # # # # # # # # # # # # # # # # # # #
# Conky Script
# Edited by 0okami 2006-08-31
# # # # # # # # # # # # # # # # # # # #

# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft no

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=6


# Create own window instead of using desktop (required in nautilus)
own_window yes

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_colour black



# Text alpha when using Xft
xftalpha 0.8

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 280 5
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 10

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#minimum_size 10 10
gap_x 13
gap_y 13
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
#${font Luxi Mono:size=10}justo como este texto que o google traduz fÃªz o portuguÃªs
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}
#
# # # # # beyond this point (TEXT) will be on screen # # # # #


TEXT
$nodename: $sysname $kernel
System Uptime:$color $uptime 

System/CPU: $machine (1.8Ghz)
${cpugraph 70,290 000000 aa0000} 
${voffset -67}   Current CPU Freq. ${freq_dyn_g}Ghz. (${color ffaaaa}${cpu}%$color) 
   Temp:  ${acpitemp}c /  ${acpitempf}F
   Load:$color $loadavg
   Processes: $processes  Running: $running_processes


${color orange}Name              PID     CPU%   MEM%
${color #ffffff} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #bbbbbb} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #aaaaaa} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #888888} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}$color

RAM Usage: $color $mem of $memmax ${color orange}$memperc%$color ${membar 8,22}

${color orange}Name              PID     CPU%   MEM%
${color #ffffff} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #bbbbbb} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #aaaaaa} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color #888888} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
${color #666666} ${top_mem name 5} ${top_mem pid 5} ${top_mem cpu 5} ${top_mem mem 5}$color


Disk Drive: hda (ext3 Linux)
${color 222222}${fs_bar 16,300 /}$color$color
 ${voffset -20}${color white}${fs_size /} $color| ${color #ff0000}${fs_used /} $color| ${color #00ff00}${fs_free /} ${color}| I/O: ${diskio /}  

Disk Drive: hda5 (fat32 os-share)
${color 222222}${fs_bar 16,300 /home/ookami/os-share}$color
 ${voffset -20}${color white}${fs_size /home/ookami/os-share} $color| ${color #ff0000}${fs_used /home/ookami/os-share} $color| ${color #00ff00}${fs_free /home/ookami/os-share} ${color}| I/O: ${diskio /home/ookami/os-share}  

Disk Drive: sda (Cruzer Micro)
${color 222222}${fs_bar 16,300 /media/usbdisk}$color
 ${voffset -20}${color white}${fs_size /media/usbdisk} $color| ${color #ff0000}${fs_used /media/usbdisk} $color| ${color #00ff00}${fs_free /media/usbdisk} ${color}| I/O: ${diskio /media/usbdisk}  

Disk Drive: sda (XSDRIVE)
${color 222222}${fs_bar 16,300 /media/XSDRIVE}$color
 ${voffset -20}${color white}${fs_size /media/XSDRIVE} $color| ${color #ff0000}${fs_used /media/XSDRIVE} $color| ${color #00ff00}${fs_free /media/XSDRIVE} ${color}| I/O: ${diskio /media/XSDRIVE}  


Swap: $swap | $swapmax | - $swapperc% ${swapbar 8,100}


${color #BBBBBB} Wired (IP ${addr eth1})  
${downspeedgraph eth1 45,140 ff0000 0000ff}	  ${upspeedgraph eth1 45,140 0000ff ff0000}
${voffset -40}  Down: ${downspeedf eth1} k/s	Up: ${upspeedf eth1} k/s
  Total: ${totaldown eth1}		Total: ${totalup eth1}

${color #BBBBBB} WiFi (IP ${addr wlan0})  
${downspeedgraph ath0 45,140 ff0000 0000ff}	  ${upspeedgraph ath0 45,140 0000ff ff0000}
${voffset -40}  Down: ${downspeedf ath0} k/s	Up: ${upspeedf ath0} k/s
  Total: ${totaldown ath0}		Total: ${totalup ath0}


```

terminal output: 
```
ookami@navi-001:~$ conky -c .conky_raidmax
Conky: desktop window (e00054) is subwindow of root window (20e)
Conky: window type - normal
Conky: hint - undecorated
Conky: hint - below
Conky: hint - sticky
Conky: hint - skip_taskbar
Conky: hint - skip_pager
Conky: drawing to created window (2600002)
Conky: failed to set up double buffer
Conky: drawing to single buffer

```

This returns nothing:
```

ookami@navi-001:~$ xdpyinfo|grep DOUBLE
ookami@navi-001:~$
ookami@navi-001:~$

```

Looking at my Xorg.0.log (pertaining to double buffer...: 
```

(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER

```

^ looks ok... there are no errors

Not sure what im missing. Ive set this up on other machines easly... but for some reason, today its not going to well... Im probably over looking something simple as i've been up for 18 hours so far... so, if you see it, point it out please. 

zzzzZZZ

---

### Post by Anonii on 2006-09-01
Some questions:

I usually reach the Desktop by using the "Hide All Windows" button, and that probably hides the Conky window too => I cant see it :P
How can I stop it from minimizing or something?

Also, does it support other players too? Like Banshee?

---

### Post by seldon77 on 2006-09-02
yes you are right

a few weeks ago i included some code in the last line of .conkyrc that will make sure conky is on the root window every 30 seconds or so (wmctl). Just wait a few seconds and conky should  reappear.

.... yep ... just tried it - it works.





> **Anonii said:**
> Some questions:

I usually reach the Desktop by using the "Hide All Windows" button, and that probably hides the Conky window too => I cant see it :P
How can I stop it from minimizing or something?

Also, does it support other players too? Like Banshee?

---

### Post by Bigga on 2006-09-02
Hi evryone! Great tute there pal.

I've got one question though. I'm running xubuntu on a server install and I was wondering if there was anyway to get conky running as a screensaver? or sending it's output to one?

I ask because I don't sit in front of the server but it would be nice to be able to see all the info from across the room. Any ideas?

---

### Post by one_stinky_bum on 2006-09-16
> **calvinthomas said:**
> can anyone tell me how I can set it into the right hand corner as in the instructions?


I use "alignment top_right" and it works on aiglx+compiz. Maybe this would help.

I have some questions of my own: can I enable alpha blending for the graphs + can I make them such that they don't fill the area under the curve? How do I make it appear on all workspaces? It would be nice to exclude compiz shadows from the conky window.
Thanks.

---

### Post by k9brand on 2006-09-16
Mine still flickers as well :(

Also, everytime conky updates itself, my screen loses focus...

---

### Post by hikaricore on 2006-09-16
> **one_stinky_bum said:**
> I use "alignment top_right" and it works on aiglx+compiz. Maybe this would help.

I have some questions of my own: can I enable alpha blending for the graphs + can I make them such that they don't fill the area under the curve? How do I make it appear on all workspaces? It would be nice to exclude compiz shadows from the conky window.
Thanks.

if you have devilspie make a file in the .devilspie directory inside your home dir called conky.ds and copy paste:

```
(if
    (matches (application_name) "conky")
    (begin
        (pin)
    )
)
```

then save.

if you're already using devilspie you'll have it set to autostart so just enjoy the on all desktops feature :)

if not you'll need to do:

```
sudo apt-get install devilspie
```

and proceed with the above mentioned instructions after placing devilspie in your startup settings then starting it manually :)


sorry if there are any typos in this message i'm currently fighting with a text color problem whic stops me from being able to see when posting in odd colored forms :P

--aaron

---

### Post by jpyanowski on 2006-09-16
I really want to thank you for this bit of informative software. I thought I had everything done but had left the upstream and downstream expressions referring to eth0 and not wlan0. Now it's looking gooooood!!!!!

---

### Post by one_stinky_bum on 2006-09-16
Thanks for the tip hikaricore. Turns out I was using an older version of conky! I got the latest deb from the first page and now I can do "own_window_type override" and I'm all set. The last thing that baffles me is the poor correlation between the network upspeed value and the graph generated by "upspeedgraph". It seems to me that the upspeedgraph mimics the downspeed graph.

---

### Post by hikaricore on 2006-09-17
> **one_stinky_bum said:**
> Thanks for the tip hikaricore. Turns out I was using an older version of conky! I got the latest deb from the first page and now I can do "own_window_type override" and I'm all set. The last thing that baffles me is the poor correlation between the network upspeed value and the graph generated by "upspeedgraph". It seems to me that the upspeedgraph mimics the downspeed graph.

yea tried the own_window_type override on my system but if i clicked on my gnome desktop conky it would disappear under it O.o  worked fine if i clicked on conky for the desktop menu and such tho, didn't feel like figuring it out so for those of us with my issue, devilspie pwns :)

---

### Post by harryc on 2006-09-17
> **spockrock said:**
> never mind I figured it out.

and thanks for the great guide.What did you do to fix this missing cpu temperature sensor? Here is my sensors readout. I want to display 'CPU Temp' and 'temp3' in Conky. Anyone?

w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.09 V  (min =  +1.94 V, max =  +1.94 V)       ALARM
+12V:     +12.65 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.20 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +5.04 V  (min =  +4.75 V, max =  +5.25 V)
-12V:     -12.20 V  (min = -10.80 V, max = -13.18 V)       ALARM
V5SB:      +5.03 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +2.72 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 168750 RPM, div = 8)              ALARM
CPU Fan:     0 RPM  (min = 1318 RPM, div = 8)              ALARM
fan3:        0 RPM  (min = 30681 RPM, div = 2)              ALARM
M/B Temp:     +5°C  (high =   +22°C, hyst =   -96°C)   sensor = thermistor 
CPU Temp:  +29.5°C  (high =   +80°C, hyst =   +75°C)   sensor = diode
temp3:     +31.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
vid:      +0.000 V  (VRM Version 9.0)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm enabled

---

### Post by hikaricore on 2006-09-17
> **harryc said:**
> What did you do to fix this missing cpu temperature sensor? Here is my sensors readout. I want to display 'CPU Temp' and 'temp3' in Conky. Anyone?

if you can't find your answer here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) it probably can't be done :)  good luck


also for anyone who needs it, the config manual page as well can be useful:

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by harryc on 2006-09-17
> **hikaricore said:**
> if you can't find your answer here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) it probably can't be done :)  good luck


also for anyone who needs it, the config manual page as well can be useful:

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)I figured it out. Here's what I used in .conkyrc instead of acpitemp, which did not work on my machine;

Case Temp: ${i2c 9191-0290 temp 2}  CPU Temp: ${i2c 9191-0290 temp 3}

---

### Post by one_stinky_bum on 2006-09-18
here's my "no nonsense" conky setup... just need the basics: ram, swap, disk free, wireless strength, disk IO, downloads, uploads and top so that I know which processes to nuke. I wish conky could make graphs out of numbers returned from it's own variables. I want to take the output of the wireless strength signal ${linkstatus eth1} and make it a horizontal bar graph (like the ram indicator), but conky isn't too happy with that.
Here's my .conkyrc config file incase it's of help. I found other posted conkyrc's useful.

Lastly, to make sure the window override works, I wrote a simple script to start conky: 
```
#!/bin/bash
sleep 30 && conky;

```
The problem was that conky started before compiz started drawing windows, so I just had to make conky wait a bit.


.conkyrc:
```
# Conky configuration
background yes
use_xft yes
xftfont Bitstream Vera Sans Mono:size=7
xftalpha 0.2
out_to_console no
update_interval 1
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,skip_taskbar
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline yes
draw_borders no
draw_graph_borders yes
stippled_borders 5
border_margin 4
border_width 1
default_color grey
default_shade_color black
default_outline_color black
alignment top_right 
gap_x 10
gap_y 30
no_buffers yes
pad_percents 0
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer no
######### a few things I tried that didn't work ###########
#${color #ffffff}${downspeedgraph eth1 upspeedgraph eth1}
#${color}Bat: $apm_battery_time  ${apm_battery_life}% 
#${color}${pb_battery percent}
#${color}${downspeedgraph eth1 ddaa00 888888 100-upspeedgraph eth1 33ff00 ffffff}

TEXT
${color}${cpugraph cpu1 25}
${color}Ram: ${color 888888}$memperc ${membar}
${color}Swp: ${color 888888}$swapperc  ${swapbar}
${color}Dsk: ${color white} ${alignc}${fs_free /} ${alignr}${fs_free_perc /}%
${color}Wrl: ${alignr}${color white}${linkstatus eth1}%
${color white}${voffset 12}IO: ${color white}$diskio${alignr}${voffset -12}${color 888888}${diskiograph 20,100 0}
${color white}${voffset 12}D: ${color white}${downspeedf eth1}k/s ${alignr}${voffset -12}${color 888888}${downspeedgraph eth1 20,100 888888 888888 100}
${color white}${voffset 9}U: ${color white}${upspeedf eth1}k/s ${alignr}${voffset -9}${color 888888}${upspeedgraph eth1 20,100 888888 888888 100}
${color #ddaa00}${top name 1} ${alignc}${top cpu 1} ${alignr}${top mem 1}
${color #888888}${top name 2} ${alignc}${top cpu 2} ${alignr}${top mem 2}

```
screenie attached. The config file layout is pretty straight forward, I wish I could write a gui for it, like samurize for windows.

---

### Post by OffHand on 2006-09-18
Time to show off my updated conky. A screenshot and the .conkyrc file...

# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 60
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
${color #0077ff}$nodename - $sysname $kernel on $machine

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}
${color #0077ff}Proces:${color lightgrey} $processes  ${color #0077ff}Run:${color lightgrey} $running_processes ${color #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color #0077ff}HD IO: ${color lightgrey}${diskio}
${color #0077ff}${diskiograph 000000 0077ff}

${color #0077ff}Hard Disks:
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
${color #0077ff} Data ${color lightgrey}${fs_used /media/data}/${fs_size /media/data}${alignr}${color #0077ff}${fs_bar 5,120 /media/data}

${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}Networking: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s
${color #0077ff}${downspeedgraph eth0 27,120 000000 0077ff} $alignr${color #0077ff}${upspeedgraph eth0 27,120 000000 0077ff}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #0077ff}Port(s)${alignr}#Connections
${color #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${color #0077ff}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}

---

### Post by Odinist on 2006-09-19
worked gorgeously!

[screenshot]("http://cyberpirate23.googlepages.com/Screenshot-1.png")

---

### Post by Odinist on 2006-09-19
Ah, except using the "Show Desktop" launcher does indeed make Conky go away... I added another launcher right next to it with the command "wmctrl -a conky" to bring it back, but that's a sloppy fix... any other ideas on how to keep it from happening in the first place?

---

### Post by harryc on 2006-09-20
Thanks for the tips.

[Screenshot]("http://mysite.verizon.net/hjc56/snapshots/screenshot3.jpg")

---

### Post by Zhen-Xlogic on 2006-09-20
This script is to show in Conky Inbound & Outbound Connections!

```
${color lightgrey}Internet/Networking Status (${addr eth0}):
${offset 10}Down:${color #59687B} ${downspeed eth0} k/s${color lightgrey} ${alignr}Up:${color #59687B} ${upspeed eth0} k/s
${offset 10}${color #59687B}${downspeedgraph eth0 25,100 59687B 94506C} ${alignr}${color #59687B}${upspeedgraph eth0 25,100 59687B 94506C}
${offset 10}${color lightgrey}Total: ${color #59687B}${totaldown eth0} ${alignr}${color lightgrey}Total: ${color #59687B}${totalup eth0}

${color lightgrey}Port(s)${alignr}#Connections
${color lightgrey}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count} ${color lightgrey}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color lightgrey}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${color lightgrey}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}
${color lightgrey}Outbound Connection ${alignr} Local Service/Port${color lightgrey}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 lservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 lservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 lservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 lservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 lservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 lservice 5}
${tcp_portmon 32768 61000 rhost 6} ${alignr} ${tcp_portmon 32768 61000 lservice 6}

```

Thanks ;)

---

### Post by TLE on 2006-09-22
I don't know if this info has already been added, (I didn't borther reading the last two pages of the thread). But in GNOME to ensure that it opens on all desktops and that it doesn't show in the program pager just replace
```
own_window yes
own_window_hints undecorated,below,skip_taskbar
```
with
```
own_window yes
own_window_type desktop

```
That own_window_type line replaces the functionality of the own_window_hints line and ensures that conky is shown on all desktops

---

### Post by Nectron on 2006-09-23
Thanks for the great thread..

I've downloaded the .deb file of conky, edited the config files and conky starts at linux startup..

I only have one problem, conky can't figure out what my IP address is, therefore all network data on conky is not shown..

What's could be the problem ?

---

### Post by TLE on 2006-09-23
> **Nectron said:**
> 
I only have one problem, conky can't figure out what my IP address is, therefore all network data on conky is not shown..

What's could be the problem ?
It probably because it's the wrong network interface that's described in the configfile. What I think will work is this, first figure out what internet interface you are using, at a terminal type
```
ifconfig
```
In this output find the one that has a IP adress and that's your interface, like say on my computer it is eth0 (written in the left collumn). Then when you find this open your conky config
```
gedit ~/.conkyrc
```
and replace all the places where it says eth0 with the values you found

---

### Post by K.Mandla on 2006-09-23
Thanks for this. I put together a nifty onscreen summary for my ultralight Openbox machine.

[[IMG]http://img208.imageshack.us/img208/8267/screenshotox7.th.jpg[/IMG]](http://img208.imageshack.us/my.php?image=screenshotox7.jpg)

Nothing fancy, no graphs or process lists. Just the basics. Maybe later I'll go back to a big panel and so forth.

In case anyone is interested. ...

```
background yes
use_xft yes
xftfont Bitstream Vera Sans:size=12
xftalpha 0.8
update_interval 2
own_window no
double_buffer yes
draw_shades yes
draw_outline no
stippled_borders no
border_margin 0
border_width 1
default_color white
default_shade_color black
alignment bottom_left
gap_x 9
gap_y 9
use_spacer no
no_buffers yes
uppercase no

TEXT
${color white}Ubuntu $sysname $kernel ${color darkgrey}on ${color white}$nodename ${color darkgrey}[${color white}${freq_dyn}Mhz ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}${color darkgrey}]
${color white}$uptime_short ${color darkgrey}uptime at ${color white}$cpu% ${color darkgrey}cpu load with ${color white}${mem}b${color darkgrey} of ${color white}${memmax}b${color darkgrey} (${color white}$memperc%${color darkgrey}) used by ${color white}$processes ${color darkgrey}processes
${color white}${fs_used /}b${color darkgrey} of ${color white}${fs_size /}b${color darkgrey} root partition used, ${color white}${fs_used /home}b${color darkgrey} of ${color white}${fs_size /home}b${color darkgrey} home partition used
${color white}${downspeed eth0} kbps${color darkgrey} down (${color white}${totaldown eth0}b${color darkgrey} total), ${color white}${upspeed eth0} kbps${color darkgrey} up (${color white}${totalup eth0}b${color darkgrey} total) on ${color white}${addr eth0}
```
That's the result of an hour's trial-and-error, so there might be some redundancies in there. (Edit: I cleaned it up a bit, and added some things. ;) )

---

### Post by Dinerty on 2006-09-24
Great howto, however I notice I have flickering and have did all the things mentioned in this threa to resolve it, however it is still there.

Any ideas?

---

### Post by foureight84 on 2006-09-29
> **one_stinky_bum said:**
> 
The problem was that conky started before compiz started drawing windows, so I just had to make conky wait a bit.


how do i make a delay load for conky? i think this is why conky doesn't show up when compiz loads. i have "own_window no" set in the script. i was having problems with it appearing when i active compiz resize.

---

### Post by OffHand on 2006-09-29
You can always make a toggle button for conky. Use the following script and point a launcher to this script:

#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky

fi

8)

---

### Post by TLE on 2006-09-29
Or a script that waits a little while before launching

```
#!/bin/sh

sleep 10
# Waits 10 seconds

exec conky
```

---

### Post by seldon77 on 2006-09-29
i've updated the .conkyrc file, to tidy up the network interfaces section (reusing some great code someone posted above), and including a little bit of colour into the graphs.

can someone please check the new .conkyrc file in their setup to make sure it's working fine?

---

### Post by foureight84 on 2006-09-29
okay, here's the problem i am having. here is my current settings:

```

own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
double_buffer yes

```

with this, when i active fade in compiz, conky is selected with other windows. however, when i change own_window to no and add own_window_type to desktop that problem goes away. however, my desktop icons disappear. the cause of that is double_buffer. but when i turn off double buffer, conky flickers. is there any fix to make my icons reappear and not have conky flicker?

---

### Post by seldon77 on 2006-09-29
i dont know anything about compiz....

i thought someone posted a workaround several pages back, but i dont know if it works. if someone can confirm code to make compiz work, can you please post it here so i can update the how-to

---

### Post by foureight84 on 2006-09-30
the workarounds don't work. i got it be excluded from fader, but you would have to turn off own_window and leave double_buffer on. but you will have disappearing desktop icons. you can turn off double_buffer but it will flicker. there's no work around for now. i think the only way is to somehow get compiz to exclude conky from the fade effect.

---

### Post by one_stinky_bum on 2006-09-30
Hmm... I'm using compiz + AIGLX, and this works for me:
```
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```
I also have a startup script that I called .conky_start.sh in my home directory:
```
#!/bin/bash
sleep 60 && conky;
```
This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs). 

I don't have any trouble with conky and compiz... conky is essentially seen as part of my wallpaper and I don't have any flickering icons (i915 graphics here).

This is real basic stuff. Hope it helps.

---

### Post by foureight84 on 2006-09-30
i'd kiss you, but you're a stinky bum. dude, thanks so much for the fix works really well.

---

### Post by seldon77 on 2006-10-01
Thanks - I'll add your tips to the How-to

> **one_stinky_bum said:**
> Hmm... I'm using compiz + AIGLX, and this works for me:
```
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```
I also have a startup script that I called .conky_start.sh in my home directory:
```
#!/bin/bash
sleep 60 && conky;
```
This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs). 

I don't have any trouble with conky and compiz... conky is essentially seen as part of my wallpaper and I don't have any flickering icons (i915 graphics here).

This is real basic stuff. Hope it helps.

---

### Post by handband2 on 2006-10-04
Here is what I did...

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
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

maximum_width 280

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$sysname $kernel | Uptime: ${uptime}
$color$stippled_hr
CPU: ${freq}MHz   Load: ${loadavg}
CPU Usage:  $cpu%   $cpubar
${cpugraph 000000 ffffff}
${color #ddaa00}NAME             PID        CPU%       MEM%$color
${top name 1} ${top pid 1} |  ${top cpu 1} |   ${top mem 1}
${top name 2} ${top pid 2} |  ${top cpu 2} |   ${top mem 2}
${top name 3} ${top pid 3} |  ${top cpu 3} |   ${top mem 3}
${top name 4} ${top pid 4} |  ${top cpu 4} |   ${top mem 4}
${top name 5} ${top pid 5} |  ${top cpu 5} |   ${top mem 5}
${top name 6} ${top pid 6} |  ${top cpu 6} |   ${top mem 6}
$color$stippled_hr
RAM:        $memperc%     $mem/$memmax    ${membar 6}$color
Swap:       $swapperc%       $swap/$swapmax      ${swapbar 6}$color

Root:       ${fs_free_perc /}%      $color${fs_used /}/${fs_size /}    ${fs_bar 6 /}$color 
Home:       ${fs_free_perc /home}%     $color${fs_used /home}/${fs_size /home}   ${fs_bar 6 /home}$color
$color$stippled_hr
Internet/Networking Status (${addr eth0}):
Down: ${downspeedf eth0} k/s ${alignr}Up: ${upspeedf eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$stippled_hr
Internet/Networking Status (${addr eth1}):
Down: ${downspeedf eth1} k/s ${alignr}Up: ${upspeedf eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$stippled_hr
${color #ddaa00}Port(s)${alignr}#Connections
$color ALL:     ${alignr}$color ${tcp_portmon 1 65535 count}
${color #ddaa00}Remote Address ${alignr} Local Service/Port$color
 ${tcp_portmon 1 65535 rhost 0} ${alignr} ${tcp_portmon 1 65535 lservice 0}
 ${tcp_portmon 1 65535 rhost 1} ${alignr} ${tcp_portmon 1 65535 lservice 1}
 ${tcp_portmon 1 65535 rhost 2} ${alignr} ${tcp_portmon 1 65535 lservice 2}
 ${tcp_portmon 1 65535 rhost 3} ${alignr} ${tcp_portmon 1 65535 lservice 3}
 ${tcp_portmon 1 65535 rhost 4} ${alignr} ${tcp_portmon 1 65535 lservice 4}
$color$stippled_hr
SYSTEM LOG TAIL
${execi 30 tail -n3 /var/log/messages | fold -w67}
$color$stippled_hr

```

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16899&stc=1&d=1160006643[/IMG]

---

### Post by VCSkier on 2006-10-05
i just wanted to say this works great on my dapper setup.  i had always wanted something to display live statistics, that used very little resources, and still looked cool.  this is it!  i haven't tried it yet on my edgy setup w/ beryl, but i'll let you know how it goes when i do.  thanks!

---

### Post by Frédéric Perrin on 2006-10-07
How do you specify a scale for graphs ?
For example, if I barely use my connection, the top of the graph will be, say 3ko/s ; if I use it it extensively, it will be 120ko/s or so. Such a variation make the graph close to useless.
The doc says that you may use as arguments to 
downspeedgraph the following : « net (height),(width) (gradient colour 1) (gradient colour 2) (scale) ». I couldn't find other information about how to use graphs.
I tried as values to scale numbers ranging from 0.1 to a million, without it changing anything. How are you supposed to use it ?

---

### Post by one_stinky_bum on 2006-10-07
This is what I did:
```
${color white}U:${upspeedf eth1}k/s ${upspeedgraph eth1 20,100 888888 888888 [COLOR="Red"]100[/COLOR]}
```
The last 100 (in red) means that the graph tops out at 100kb/s. I figured if I'm downloading anything that fast I needn't worry about speed. Adjust that number to suit your needs.

---

### Post by sktfeelsdapper on 2006-10-08
A little late in the game here, but I had a question.

Is there any reason my conky seems so big? I mean GIGANTIC.

Here's a shot.

---

### Post by OffHand on 2006-10-08
> **sktfeelsdapper said:**
> A little late in the game here, but I had a question.

Is there any reason my conky seems so big? I mean GIGANTIC.

Here's a shot.

This is the reason:

# Minimum size of text area
minimum_size 260 5
maximum_width 250

Adjust the max width  :D

---

### Post by sktfeelsdapper on 2006-10-08
> **OffHand said:**
> This is the reason:

# Minimum size of text area
minimum_size 260 5
maximum_width 250

Adjust the max width  :D

Yah, I guess I deserve a big collective "duh" on that one.
I couldn't seem to change it before, but this did the trick.
Thanks.

---

### Post by handy on 2006-10-09
Thanks **Seldon77** for this great how-to, & to all concerned for feeding it!

I am happy with my conky setup, except for the ubiquitous *one last thing* :) 

I have a Gigabyte GA-K8NS Ultra 939, running the nForce-3 chipset.  I would like to be able to monitor my CPU temp'. The graphics card would be a bonus, as would any fan speeds.

I don't know what the command is for sensor's in bash either.

Any help very much appreciated.

Thanks again all, you make all this stuff fun...

---

### Post by OffHand on 2006-10-09
> **handy said:**
> Thanks **Seldon77** for this great how-to, & to all concerned for feeding it!

I am happy with my conky setup, except for the ubiquitous *one last thing* :) 

I have a Gigabyte GA-K8NS Ultra 939, running the nForce-3 chipset.  I would like to be able to monitor my CPU temp'. The graphics card would be a bonus, as would any fan speeds.

I don't know what the command is for sensor's in bash either.

Any help very much appreciated.

Thanks again all, you make all this stuff fun...

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)


CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C


Try if that one works.

---

### Post by handy on 2006-10-09
> **OffHand said:**
> [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)


CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C


Try if that one works.

Thanks for your reply, but that line of code stops Conky from starting on my box :-k 

I've looked at the **Conky Variables** before, & exhausted the possibilities. ***[Edit:] re: Monitoring  heat & fan speeds that is...***

Perhaps I will have to live with the fact that all m/boards are not supported, & mines one of them...

---

### Post by Aberrix on 2006-10-11
it appears my swap space isnt being displayed properly? it looks like some other people had the same problem... anyone know how to fix it?

---

### Post by Aberrix on 2006-10-11
here is my conky:

```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour black
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
#default_color white
#default_shade_color white
#default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 60
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
# Variable Arguments Description
# acpiacadapter ACPI ac adapter state.
# acpifan ACPI fan state
# acpitemp ACPI temperature.
# adt746xcpu CPU temperature from therm_adt746x
# adt746xfan Fan speed from therm_adt746x
# battery (num) Remaining capasity in ACPI or APM
# battery. ACPI battery number can be
# given as argument (default is BAT0).
# buffers Amount of memory buffered
# cached Amount of memory cached
# color (color) Change drawing color to color
# cpu CPU usage in percents
# cpubar (height) Bar that shows CPU usage, height is
# bar's height in pixels
# downspeed net Download speed in kilobytes
# downspeedf net Download speed in kilobytes with one
# decimal
# exec shell command Executes a shell command and displays
# the output in torsmo. warning: this
# takes a lot more resources than other
# variables. I'd recommend coding wanted
# behaviour in C and posting a patch .
# execi interval, shell Same as exec but with specific interval.
# command Interval can't be less than
# update_interval in configuration.
# fs_bar (height), (fs) Bar that shows how much space is used on
# a file system. height is the height in
# pixels. fs is any file on that file
# system.
# fs_free (fs) Free space on a file system available
# for users.
# fs_free_perc (fs) Free percentage of space on a file
# system available for users.
# fs_size (fs) File system size
# fs_used (fs) File system used space
# hr (height) Horizontal line, height is the height in
# pixels
# i2c (dev), type, n I2C sensor from sysfs (Linux 2.6). dev
# may be omitted if you have only one I2C
# device. type is either in (or vol)
# meaning voltage, fan meaning fan or temp
# meaning temperature. n is number of the
# sensor. See /sys/bus/i2c/devices/ on
# your local computer.
# kernel Kernel version
# loadavg (1), (2), (3) System load average, 1 is for past 1
# minute, 2 for past 5 minutes and 3 for
# past 15 minutes.
# machine Machine, i686 for example
# mails Mail count in mail spool. You can use
# program like fetchmail to get mails from
# some server using your favourite
# protocol. See also new_mails.
# mem Amount of memory in use
# membar (height) Bar that shows amount of memory in use
# memmax Total amount of memory
# memperc Percentage of memory in use
# new_mails Unread mail count in mail spool.
# nodename Hostname
# outlinecolor (color) Change outline color
# pre_exec shell command Executes a shell command one time before
# torsmo displays anything and puts output
# as text.
# processes Total processes (sleeping and running)
# running_processes Running processes (not sleeping),
# requires Linux 2.6
# shadecolor (color) Change shading color
# stippled_hr (space), Stippled (dashed) horizontal line
# (height)
# swapbar (height) Bar that shows amount of swap in use
# swap Amount of swap in use
# swapmax Total amount of swap
# swapperc Percentage of swap in use
# sysname System name, Linux for example
# time (format) Local time, see man strftime to get more
# information about format
# totaldown net Total download, overflows at 4 GB on
# Linux with 32-bit arch and there doesn't
# seem to be a way to know how many times
# it has already done that before torsmo
# has started.
# totalup net Total upload, this one too, may overflow
# updates Number of updates (for debugging)
# upspeed net Upload speed in kilobytes
# upspeedf net Upload speed in kilobytes with one
# decimal
# uptime Uptime
# uptime_short Uptime in a shorter format
#
# seti_prog Seti@home current progress
# seti_progbar (height) Seti@home current progress bar
# seti_credit Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Boldixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a %b %d}${alignr -25}${time %k:%M}

TEXT
${color #000000}$nodename
${color #000000}$sysname ${color #000000}$kernel
${color #000000}$stippled_hr
${color #000000}uptime: $uptime
${color #000000}load: $loadavg
${color #000000}$stippled_hr
${color #000000}AMD Athlon(tm) 64 X2 3800+ 
${color #000000}Usage:${color #000000} ${cpu}% ${color #000000}${cpubar}
${color #000000}${cpugraph 000000 000000}
${color #000000}proces: $processes ${color #000000}run: $running_processes
${color #000000}$stippled_hr
memory:
${color #000000} ram: ${alignr}$mem/$memmax ${color #000000}${membar 5,140}
${color #000000} swp: ${alignr}$swap/$swapmax ${color #000000}${swapbar 5,140}
${color #000000}$stippled_hr
${color #000000}hard disks:
${color #000000} / ${alignr}${fs_used /}/${fs_size /} ${color #000000}${fs_bar 5,100 /}
${color #000000} storage ${alignr}${fs_used /media/storage}/${fs_size /media/storage} ${color #000000}${fs_bar 5,100 /media/storage}
${color #000000}$stippled_hr
${color #000000}cpu usage         PID     CPU%   MEM%
 ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #000000} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #000000} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

${color #000000}mem usage
 ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #000000} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #000000} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color #000000}$stippled_hr
${color #000000}eht0: ${addr eth0}

${color #000000}down: ${downspeed eth0} k/s $alignr${color #000000} up: ${upspeed eth0} k/s
${color #000000}${downspeedgraph eth0 27,120 000000 000000} $alignr${color #000000}${upspeedgraph eth0 27,120 000000 000000}
${totaldown eth0} $alignr${totalup eth0}
${color #000000}$stippled_hr
${color #000000}port(s)${alignr}#connections
${color #000000}inbound: ${tcp_portmon 1 32767 count} ${color #000000}outbound: ${tcp_portmon 32768 61000 count}${alignr}${color #000000}total: ${tcp_portmon 1 65535 count}

${color #000000}inbound connection ${alignr} local service/port
${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}
```

---

### Post by nwgray on 2006-10-13
My icons are disappearing when I run conky even though I'm not running compiz /xgl. Here's the .conkyrc (copied from a poster's own file in this thread - thx):

background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
on_bottom no

# Xft font when Xft is enabled
xftfont Sans:size=12

# Text alpha when using Xft
xftalpha 1.0

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
               Conky
${color white}CPU:${color white} ${freq} ${color white}mhz / Temp:${color white}$acpitemp ${color white}C 
${color white}Disk I/O:${color white} ${diskio}    ${color white}Uptime:${color white} $uptime 
${color white}Processes:${color white} $processes  ${color white}Running:${color white} $running_processes
${color white}CPU Usage:${color white} $cpu% ${color white}${cpugraph  20, 125 ffffff 0000ff}
${color white}RAM Usage:${color white} $mem/$memmax ${color white}- ${color white}$memperc% ${color white}${membar}
${color white}Swap Usage:${color white} $swap/$swapmax ${color white}- ${color white}$swapperc% ${color white}${swapbar}
${color white}File systems: / ${color white}${fs_used /}/${fs_size /} ${color white}${fs_bar /}

${color}Name              PID     CPU%   MEM%
${color green} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color green} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color green} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color green} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color green} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}

${color white}Networking:
 Down:${color white} ${downspeed eth0} k/s${color white} ${offset 80}Up:${color white} ${upspeed eth0} k/s
${color white}${downspeedgraph eth0 20,150 ff0000 0000ff} ${color white}${upspeedgraph eth0 20,150 0000ff ff0000}

${color white}Netstat
${color green}${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
${color white}Remote Address ${alignr} Local Service/Port
${color green} ${tcp_portmon 1 65535 rhost 0} ${alignr} ${tcp_portmon 1 65535 lservice 0}
${color green} ${tcp_portmon 1 65535 rhost 1} ${alignr} ${tcp_portmon 1 65535 lservice 1}
${color green} ${tcp_portmon 1 65535 rhost 2} ${alignr} ${tcp_portmon 1 65535 lservice 2}
${color green} ${tcp_portmon 1 65535 rhost 3} ${alignr} ${tcp_portmon 1 65535 lservice 3}
${color green} ${tcp_portmon 1 65535 rhost 4} ${alignr} ${tcp_portmon 1 65535 lservice 4}
${color green} ${tcp_portmon 1 65535 rhost 5} ${alignr} ${tcp_portmon 1 65535 lservice 5}
${color green} ${tcp_portmon 1 65535 rhost 6} ${alignr} ${tcp_portmon 1 65535 lservice 6}
${color green} ${tcp_portmon 1 65535 rhost 7} ${alignr} ${tcp_portmon 1 65535 lservice 7}
${color green} ${tcp_portmon 1 65535 rhost 8} ${alignr} ${tcp_portmon 1 65535 lservice 8}
${color green} ${tcp_portmon 1 65535 rhost 9} ${alignr} ${tcp_portmon 1 65535 lservice 9}
${color green} ${tcp_portmon 1 65535 rhost 10} ${alignr} ${tcp_portmon 1 65535 lservice 10}


thoughts?

/thx

---

### Post by OffHand on 2006-10-13
> **Aberrix said:**
> here is my conky:

```

memory:
${color #000000} ram: ${alignr}$mem/$memmax ${color #000000}${membar 5,140}
${color #000000} swp: ${alignr}$swap/$swapmax ${color #000000}${swapbar 5,140}
```
Strange, mine looks the same and works. You might want to ask in Conky's IRC channel. They really do know a lot and are very helpful.

---

### Post by OffHand on 2006-10-13
> **nwgray said:**
> My icons are disappearing when I run conky even though I'm not running compiz /xgl. Here's the .conkyrc (copied from a poster's own file in this thread - thx):


# Create own window instead of using desktop (required in nautilus)
own_window no

# Use pseudo transparency with own_window?
own_window_transparent yes

Try this instead
```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

```

---

### Post by handy on 2006-10-13
Conky disappears if I LMB click on the desktop?  It is still running, I have to kill it before I can start it again...

---

### Post by forger on 2006-10-14
for fortune cookies you'll need (and probably like) these:
```

sudo apt-get install fortunes fortunes-debian-hints

```

now, my version, with external ip and a bit of different approach on $machine and processor identification.
you'll need curl:
```

sudo apt-get install curl

```

[[IMG]http://static.flickr.com/80/269120466_ca76488cc3_m.jpg[/IMG]]("http://static.flickr.com/80/269120466_ca76488cc3_o.png")

```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 10.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
${color yellow}$nodename $sysname ${exec uname -r | cut -d - -f 1-2} on ${exec uname -r | cut -d - -f 3} ${exec cat /proc/cpuinfo | grep "model name" | sed -e 's/model name\t: //' -e 's/\s\s\s/ /'}
${color white}$stippled_hr
${color yellow}Uptime: ${color lightgrey}$uptime_short ${color yellow}CPU: ${color lightgrey}${freq}${color white}MHz ${color yellow}Load: ${color lightgrey}${loadavg}
${color white}$cpubar
${cpugraph}${color yellow}
NAME             PID       CPU%      MEM%${color lightgrey}
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${color white}$stippled_hr
${color white}RAM:        ${color lightgrey}$memperc%       ${membar 6}
${color white}Swap:       ${color lightgrey}$swapperc%       ${swapbar 6}

${color white}Root:       ${color lightgrey}${fs_free_perc /}%        ${fs_bar 6 /} 
${color white}sda1:       ${color lightgrey}${fs_free_perc /home}%        ${fs_bar 6 /home} 
${color white}$stippled_hr
${color yellow}IP: ${color lightgrey}${addr eth0} ${execi 600 curl 'http://www.whatismyip.org'} ${color yellow}Total: ${color lightgrey}${totaldown eth0} ${color white}Down ${color lightgrey}${totalup eth0} ${color white}Up

${color yellow}Down: ${color lightgrey}${downspeedf eth0} ${color white}kB/s ${offset 110} ${color yellow}Up: ${color lightgrey}${upspeedf eth0} ${color white}kB/s
${color lightgrey}${downspeedgraph eth0 32,200} ${upspeedgraph eth0 32,200}

${color lightgrey}${execi 30 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
${color white}$stippled_hr
${color yellow}SYSTEM LOG TAIL
${color lightgrey}${execi 60 tail -n3 /var/log/messages | fold -w67}
${color white}$stippled_hr
${color white}${execi 120 fortune | fold -w67}
${color lightgrey}${execi 120 wmctrl -a conky}

```

---

### Post by nwgray on 2006-10-16
Offhand
   I had to comment out - own_window_hints undecorated,below,skip_taskbar

but now it's working fine. 

Thx!

---

### Post by Aberrix on 2006-10-16
> **OffHand said:**
> Strange, mine looks the same and works. You might want to ask in Conky's IRC channel. They really do know a lot and are very helpful.

I copied yours to start with, hope you don't mind... I liked yours the best. I just tweaked it for my use/taste.

---

### Post by OffHand on 2006-10-16
You're welcome guys. And I do not mind people using my Conky, knock yourself out  ;)

---

### Post by nwgray on 2006-10-16
Has anyone tried to get curl working as an rss grabber? I found this on the sourceforge page in one of the conkyrc files:

${color #5b6dad}Fox News Latest Headlines:
${color #7f8ed3}${execi 300 /home/hellfire/scripts/conky-rss.sh}

I have changed the conky-rss.sh script and changed the info to point to my directory. Here's the info from the conky-rss.sh file:

#!/bin/bash
# RSS Feed Display Script by Hellf[i]re v0.1
#
# This script is designed for most any RSS Feed.  As some feeds may not be
# completely compliant, it may need a bit of tweaking
#
# This script depends on curl.
# Gentoo: emerge -av net-misc/curl
# Debian: apt-get install curl
# Homepage: [http://curl.haxx.se/](http://curl.haxx.se/)
#
# Usage:
# .conkyrc:	${execi [time] /path/to/script/conky-rss.sh}
#
# Usage Example		
#		${execi 300 /home/youruser/scripts/conky-rss.sh}


#RSS Setup
URI=http://www.foxnews.com/xmlfeed/rss/0,4313,1,00.rss	#URI of RSS Feed
LINES=4							#Number of headlines

#Environment Setup
EXEC="/usr/bin/curl -s"				#Path to curl

#Work Start
$EXEC $URI | grep title |\
sed -e :a  -e 's/<[^>]*>//g;/</N' |\
sed -e 's/[ \t]*//' |\
sed -e 's/\(.*\)/ \1/' |\
sed -e 's/\.//' |\
sed -e 's/\"//' |\
sed -e 's/\"//' |\
head -n $(($LINES + 2)) |\
tail -n $(($LINES))


When I run it, I have no info shows up in my Fox News section (see screenshot). If I manually run the command curl -s [http://www.foxnews.com/xmlfeed/rss/0,4313,1,00.rss](http://www.foxnews.com/xmlfeed/rss/0,4313,1,00.rss) then I get this in my terminal window:

<?xml version="1.0" encoding="iso-8859-1" ?>
<rss version="2.0">
<channel>


         
                  

          
                    
        <title>FOXNews.com</title>
        <description>FOX News Channel - We Report. You Decide.</description>
        <link>http://www.foxnews.com/</link>
        <copyright>Copyright 2006 FOX News Channel</copyright>
        <language>en-us</language>
        <lastBuildDate>Mon, 16 Oct 2006 11:37:40 EST</lastBuildDate>
        <managingEditor>foxnewsonline@foxnews.com</managingEditor>
        <webMaster>foxnewsonline@foxnews.com</webMaster>
        <image>
                <url>http://www.foxnews.com/images/headers/fnc_logo.gif</url>
                <title>FOXNews.com Live Bookmark</title>
                <link>http://www.foxnews.com/</link>
        </image>



                        <item>
                                <title>Moussaoui Juror Falls Ill; Deliberations to Resume Friday</title>
                                <link>http://www.foxnews.com/story/0,2933,193329,00.html</link>
                                <description>Jurors in the Zacarias Moussaoui case headed into a fourth day of deliberations Thursday but talks halted when one juror fell ill; deliberations to resume Friday</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Thu, 27 Apr 2006 05:35:04 EST</pubDate>
                        </item>

                        <item>
                                <title>Iran Test-Fires Another 'Top Secret' Missile</title>
                                <link>http://www.foxnews.com/story/0,2933,190696,00.html</link>
                                <description>Iran's state-run television says it successfully test-fired a "top secret" missile, the third in a week.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 02:55:22 EST</pubDate>
                        </item>

                        <item>
                                <title>Duke Lacrosse Coach Resigns Amid Rape Flap</title>
                                <link>http://www.foxnews.com/story/0,2933,190749,00.html</link>
                                <description>University cancels remainder of season after allegations that three players raped an exotic dancer at a party.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Thu, 06 Apr 2006 03:16:47 EST</pubDate>
                        </item>

                        <item>
                                <title>100 Homes Threatened by Weakened Dam in Northern California</title>
                                <link>http://www.foxnews.com/story/0,2933,190674,00.html</link>
                                <description>About 100 homes were being evacuated Wednesday morning as a small earthen dam in Calaveras County in northern California weakened by an overnight thunderstorm threatened to break.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Thu, 06 Apr 2006 08:03:31 EST</pubDate>
                        </item>

                        <item>
                                <title>Video Claims to Show Insurgents Dragging Burning Body of U.S</title>
                                <link>http://www.foxnews.com/story/0,2933,190646,00.html</link>
                                <description>A poor-quality video posted on the Internet Wednesday in the name of an extremist group claimed to show Iraqi insurgents dragging the burning body of a U.S. pilot on the ground after the crash of an Apache helicopter.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 05:53:26 EST</pubDate>
                        </item>

                        <item>
                                <title>DHS Press Secretary Arrested on Child Seduction Charges</title>
                                <link>http://www.foxnews.com/story/0,2933,190604,00.html</link>
                                <description>The deputy press secretary for the U.S. Department of Homeland Security was arrested Tuesday for using the Internet to seduce what he thought was a teenage girl, authorities said.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 11:17:47 EST</pubDate>
                        </item>

                        <item>
                                <title>Saddam Dodges Questions From Prosecutors </title>
                                <link>http://www.foxnews.com/story/0,2933,190621,00.html</link>
                                <description>Former Iraqi dictator is cross-examined for the first time in the trial for the killings of Shiites in 1982.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 01:36:25 EST</pubDate>
                        </item>

                        <item>
                                <title>Kidnapped Brothers Killed in Venezuela </title>
                                <link>http://www.foxnews.com/story/0,2933,190721,00.html</link>
                                <description>Venezuelan authorities found the bullet-ridden bodies of three Canadian boys who had been kidnapped more than a month ago in the South American country, the justice minister said. </description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 03:28:22 EST</pubDate>
                        </item>

                        <item>
                                <title>French Unions: Repeal Labor Law in 10 Days, or Else</title>
                                <link>http://www.foxnews.com/story/0,2933,190623,00.html</link>
                                <description>France's biggest trade unions set a 10-day deadline Wednesday for the government to revoke a divisive jobs law, threatening more protests and strikes that have spiraled into a national crisis.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 03:51:20 EST</pubDate>
                        </item>

                        <item>
                                <title>Three Arrested, Man Shot in 'Baby Shower Gone Bad'</title>
                                <link>http://www.foxnews.com/story/0,2933,190700,00.html</link>
                                <description>A baby shower erupted into a fight among guests in which one man was shot and several other people, including the seven-months-pregnant guest of honor, were beaten with a stick, police say.</description>
                                <author>foxnewsonline@foxnews.com</author>
                                <pubDate>Wed, 05 Apr 2006 01:17:01 EST</pubDate>
                        </item>
                  </channel>


so it would appear, at least to me, that the command is correct. What should I tweak to get this working from within conky?

Thx

---

### Post by nwgray on 2006-10-16
I found the problem - file permissions. I changed the script to R/W and made it executable. 

Later all!

---

### Post by Aberrix on 2006-10-17
Does conky support being able to monitor both cores on a dual core processor?

---

### Post by OffHand on 2006-10-17
> **Aberrix said:**
> Does conky support being able to monitor both cores on a dual core processor?

Yes it does. Try this:
```

${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}

```

---

### Post by Aberrix on 2006-10-17
Thank you, I'll try it when I get home ;)

---

### Post by m.musashi on 2006-10-17
> **OffHand said:**
> Yes it does. Try this:
```

${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}

```

Cool. I've been looking for a way to do this. One question, I have the following line in my conky config
```
CPU0: ${freq cpu0}MHz   Load: ${loadavg}   Temp: ${acpitemp}
```
that gives a text readout of the mhz the cpu is currently running at as well as load info. Do you know how to modify this to add the second core. I've tried a few things but it only reports dual info for one core.

Thanks.

---

### Post by OffHand on 2006-10-17
> **m.musashi said:**
> Cool. I've been looking for a way to do this. One question, I have the following line in my conky config
```
CPU0: ${freq cpu0}MHz   Load: ${loadavg}   Temp: ${acpitemp}
```
that gives a text readout of the mhz the cpu is currently running at as well as load info. Do you know how to modify this to add the second core. I've tried a few things but it only reports dual info for one core.

Thanks.

Did you try:
```
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${freq cpu1}MHz   Load: ${loadavg}   Temp: ${acpitemp}${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${freq cpu2}MHz   Load: ${loadavg}   Temp: ${acpitemp}${cpubar cpu2}
```

---

### Post by m.musashi on 2006-10-17
> **OffHand said:**
> Did you try:
```
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${freq cpu1}MHz   Load: ${loadavg}   Temp: ${acpitemp}${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${freq cpu2}MHz   Load: ${loadavg}   Temp: ${acpitemp}${cpubar cpu2}
```
Yes, that is more what I was looking for. However, it seems to be reporting the data from only one core. The graphs look different but the load and MHz are exactly the same. Using cpuburn, if one core goes to 100% the frequency changes for both even though the graph and other monitors show only one scaling up. I know for the cpu monitor that you can add to the panel, the cores are numbered 0 and 1. Here they are named 1 and 2. Is conky different? I'll change it and see. Otherwise, any ideas?

Thanks.

---

### Post by OffHand on 2006-10-18
> **m.musashi said:**
> Yes, that is more what I was looking for. However, it seems to be reporting the data from only one core. The graphs look different but the load and MHz are exactly the same. Using cpuburn, if one core goes to 100% the frequency changes for both even though the graph and other monitors show only one scaling up. I know for the cpu monitor that you can add to the panel, the cores are numbered 0 and 1. Here they are named 1 and 2. Is conky different? I'll change it and see. Otherwise, any ideas?

Thanks.

Go to the Conky IRC channel on Freenode and ask there. I'm out of ideas.

---

### Post by Aberrix on 2006-10-18
> **m.musashi said:**
> Yes, that is more what I was looking for. However, it seems to be reporting the data from only one core. The graphs look different but the load and MHz are exactly the same. Using cpuburn, if one core goes to 100% the frequency changes for both even though the graph and other monitors show only one scaling up. I know for the cpu monitor that you can add to the panel, the cores are numbered 0 and 1. Here they are named 1 and 2. Is conky different? I'll change it and see. Otherwise, any ideas?

Thanks.

what kernel are you using? what CPU do you have? are you using 32bit or 64bit Ubuntu?

---

### Post by bennyj on 2006-10-18
> **harryc said:**
> I figured it out. Here's what I used in .conkyrc instead of acpitemp, which did not work on my machine;

Case Temp: ${i2c 9191-0290 temp 2}  CPU Temp: ${i2c 9191-0290 temp 3}

Thanks for this harryc!worked out great for me.

---

### Post by m.musashi on 2006-10-18
> **Aberrix said:**
> what kernel are you using? what CPU do you have? are you using 32bit or 64bit Ubuntu?

I upgraded to the 686 kernel when I installed Beryl (but not the smp as I have a single core Athlon 64 3700) I have the 32 bit Ubuntu (or does using the 686 kernel mean I have the 64 bit version?). In any case, I installed the 32 bit Dapper.

---

### Post by Aberrix on 2006-10-18
> **m.musashi said:**
> However, it seems to be reporting the data from only one core. The graphs look different but the load and MHz are exactly the same. Using cpuburn, if one core goes to 100% the frequency changes for both even though the graph and other monitors show only one scaling up. I know for the cpu monitor that you can add to the panel, the cores are numbered 0 and 1. Here they are named 1 and 2.


> **m.musashi said:**
> I upgraded to the 686 kernel when I installed Beryl (but not the smp as I have a single core Athlon 64 3700) I have the 32 bit Ubuntu. 

so you first said you have a dual-core processor, but now you just said you have a single core processor?

---

### Post by m.musashi on 2006-10-18
> **Aberrix said:**
> so you first said you have a dual-core processor, but now you just said you have a single core processor?

Oops. I have conky on my dual core laptop and my single core desktop. I forgot which computer I was trying to fix. Both have minor issues. Sorry about that.

The truth is the laptop has a core duo processor and is running the 686-smp kernel. I also installed the 32 bit Ubuntu.

---

### Post by Aberrix on 2006-10-18
> **m.musashi said:**
> Oops. I have conky on my dual core laptop and my single core desktop. I forgot which computer I was trying to fix. Both have minor issues. Sorry about that.

The truth is the laptop has a core duo processor and is running the 686-smp kernel. I also installed the 32 bit Ubuntu.

ahh, makes sense.

So I installed the linux-k7-smp on my machine (32bit Ubuntu, AMD x2 3800+ CPU)

```
sudo apt-get install linux-k7-smp
```

and restarted with that kernel, then I played around with conky, adding the 'cpu1' or 'cpu2' variables to my config and it seems to be working properly as far as I can tell.

from what I can tell/have read unless you run the k7-smp kernel you are not actually utilizing both cores. Again am not 100% sure because I am still learning all this also, but like I said from what I've read you must use the k7-smp kernel to utilize both of those cores on the AMD CPU machine. I think once you do that, conky should start working as it should.

The 686-smp kernel is for modern Pentium 2+ kernel for dual processors, dual cores, or hyperthreading. So that's probably why it see's both cores, but since its more geared torwards intel chips it's not working properly. From my guess.

try thr k7-smp kernel since you have an AMD chip and give it a go.

**EDIT:** err... wait? I think I have it all backwards... I am guessing your desktop is a single core AMD and your laptop is a dual core Intel chip? If so, then disregard my post as I had it backwards... :P

---

### Post by m.musashi on 2006-10-18
> **Aberrix said:**
> **EDIT:** err... wait? I think I have it all backwards... I am guessing your desktop is a single core AMD and your laptop is a dual core Intel chip? If so, then disregard my post as I had it backwards... :P

Yes, I think I created a bit of confusion. Sorry. The laptop in question has the Intel Core Duo processor. I have the 686-smp kernel. It seems to be using both cores. When I run cpuburn I can see the graph on the two cores move around. One takes most of it but from time to time the other core scales up. I also added the little cpu monitors to the panel and I can see them both scale up and down idependently. In conky I can see it too on the bar graphs but the frequency only responds to what one core is doing but shows it for both.

---

### Post by Aberrix on 2006-10-18
> **m.musashi said:**
> In conky I can see it too on the bar graphs but the frequency only responds to what one core is doing but shows it for both.

Taking a look at the [conky variables]("http://conky.sourceforge.net/variables.html"), it looks like the **freq** variable doesn't have a argument to depict cpu1 or cpu2, or any arguments for that matter. So my quess is its just a current limitation in Conky.

---

### Post by m.musashi on 2006-10-18
> **OffHand said:**
> Go to the Conky IRC channel on Freenode and ask there. I'm out of ideas.

That's okay. I'm alomost there. Thanks for the help.

---

### Post by m.musashi on 2006-10-18
> **Aberrix said:**
> Taking a look at the [conky variables]("http://conky.sourceforge.net/variables.html"), it looks like the **freq** variable doesn't have a argument to depict cpu1 or cpu2, or any arguments for that matter. So my quess is its just a current limitation in Conky.
I see that now. There are arguments for cpubar and such but not freq. The cpu variable talks about smp-machines but that's it. I suppose you might be right about the limitations in conky.

Earlier you mentioned the k7 kernel. I have seem reference to i8k for dell laptops but I can't find much info on it. It seems to be a utility rather than a kernel. Is that correct?

---

### Post by OffHand on 2006-10-18
> **bennyj said:**
> Thanks for this harryc!worked out great for me.

> Yes, that is more what I was looking for. However, it seems to be reporting the data from only one core. The graphs look different but the load and MHz are exactly the same. Using cpuburn, if one core goes to 100% the frequency changes for both even though the graph and other monitors show only one scaling up. I know for the cpu monitor that you can add to the panel, the cores are numbered 0 and 1. Here they are named 1 and 2. Is conky different? I'll change it and see. Otherwise, any ideas?
> 
<drphibes> use the cpu lines form /proc/cpuinfo
<drphibes> those labels should work
<drphibes> 0 is the summary label
<OffHand>  so 0 = both average?
<drphibes> yes
<drphibes> it's all in the linux docs
<drphibes> /usr/src/linux/Documentation
<drphibes> i think thats right
<drphibes> but the general idea is that there is a total/summary line
<drphibes> followed by the individual cpu's

I couldn't find the file drphibes was talking about.
> 
<drphibes> cpuinfo certainly is a file on linux if ur runnign proc
<OffHand> hmm its empty
<drphibes> thats a kernel config
<drphibes> turn it on
<drphibes> CONFIG_PROC_FS=y


EDIT: Actually you can get the info about your cpu(s) by using this command in the terminal

```
cat /proc/cpuinfo
```

---

### Post by TheMono on 2006-10-19
On another note, you can find a .deb package for conky at [www.getdeb.net](www.getdeb.net) - it has just been added.

---

### Post by th3gh05t on 2006-10-19
Hi, 

I followed your How-To and everything is setup great!

How do I make it appear on all of my desktops? In the same location..

---

### Post by th3gh05t on 2006-10-20
> **th3gh05t said:**
> Hi, 

I followed your How-To and everything is setup great!

How do I make it appear on all of my desktops? In the same location..

Does anyone know how to do this?

---

### Post by OffHand on 2006-10-20
> **th3gh05t said:**
> Does anyone know how to do this?

Just copy my conkyrc file and start from there. It will appear on all desktops, but I do not know which settings are responsible for this behavior.

---

### Post by NPALeech on 2006-10-20
I don't think this issue's been addressed yet. (This is a really long thread so I skimmed a lot, so I apologize if this has been resolved.)

The modification to the xorg.conf did indeed fix the flickering of conky issue, but now my entire desktop is flickering. i.e. all my desktop icons flicker in and out. Anyone had this problem?

---

### Post by OffHand on 2006-10-21
> **NPALeech said:**
> I don't think this issue's been addressed yet. (This is a really long thread so I skimmed a lot, so I apologize if this has been resolved.)

The modification to the xorg.conf did indeed fix the flickering of conky issue, but now my entire desktop is flickering. i.e. all my desktop icons flicker in and out. Anyone had this problem?

Can you post your xorg.conf here?

---

### Post by NPALeech on 2006-10-21
Sure can.

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the<iframe style="position: relative; z-index: 10000;" marginwidth="0" marginheight="0" hspace="0" vspace="0" src="http://deBR.myspace.com/html.ng/site=myspace&amp;position=banner&amp;page=13000000&amp;rand=5287125800&amp;category=23&amp;acnt=1" frameborder="0" height="60" scrolling="no" width="468"></iframe> last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe" 

EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by OffHand on 2006-10-22
> **NPALeech said:**
> Sure can.

That looks good and should work if you have rebooted X after making the changes. Therefor I think it has something to do with settings in your conkyrc file. You might wanna try to experiment a bit with them.

---

### Post by NPALeech on 2006-10-22
Yes, I have restarted x, and the conckyrc file I'm using is the exact one given on the front page of this thread.

---

### Post by handy on 2006-10-22
> **th3gh05t said:**
> Hi, 

I followed your How-To and everything is setup great!

How do I make it appear on all of my desktops? In the same location..

There is a previous post, sorry I don't remember which one, that shows a way for conky to be on all workspaces simultaneously.  It did not work well for me, whenever I LMB click on the desktop conky becomes invisible?

I have to kill conky then start again if I want to see it... :rolleyes:

Obviously Conky is not that important to me, or I would have undone that command, I guess I'll get to it sooner or later. :)

---

### Post by handy on 2006-10-23
Well I've just upgraded (?) to Edgy (RC1?) & now Conky won't start, I'm not going to read the entire thread again, so if someone could give me the word, will Conky work on Edgy, & if so... How do you do that?

Thanks in advance.

**[Edit:]** *I just had a quick scan back a couple of pages & **Aberix** is using Edgy so it is a goer?*

---

### Post by OffHand on 2006-10-23
> **handy said:**
> Well I've just upgraded (?) to Edgy (RC1?) & now Conky won't start, I'm not going to read the entire thread again, so if someone could give me the word, will Conky work on Edgy, & if so... How do you do that?

Thanks in advance.

**[Edit:]** *I just had a quick scan back a couple of pages & **Aberix** is using Edgy so it is a goer?*

It does. Mine worked out of the box (I didn't need to change anything after doing a dist-upgrade).

---

### Post by Aberrix on 2006-10-23
> **handy said:**
> Well I've just upgraded (?) to Edgy (RC1?) & now Conky won't start, I'm not going to read the entire thread again, so if someone could give me the word, will Conky work on Edgy, & if so... How do you do that?

Thanks in advance.

**[Edit:]** *I just had a quick scan back a couple of pages & **Aberix** is using Edgy so it is a goer?*

I actually just* upgraded Saturday morning and haven't installed conky yet. It's on my agenda for tonight... so we'll see *crosses fingers*

---

### Post by Anonii on 2006-10-23
I replaced my conkyrc, with my upgrade to Edgy RC. I changed it to:

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
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

```

But I noticed that conky terminates itself many times, without a reason. I just minimise all programs and conky isnt there. I dont know why. I tried waiting in case it appears, but nothing.
Any ideas?

---

### Post by OffHand on 2006-10-23
> **Anonii said:**
> I replaced my conkyrc, with my upgrade to Edgy RC. I changed it to:

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
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

```

But I noticed that conky terminates itself many times, without a reason. I just minimise all programs and conky isnt there. I dont know why. I tried waiting in case it appears, but nothing.
Any ideas?

Try to add "own_window_type override" or "own_window_type normal" under: 

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

---

### Post by Aberrix on 2006-10-23
Okay I got everything working just fine on Edgy tonight, the biggest problem I ran into is when I tried to simply use the same config as I did on dapper. I found out there there "isn't" a k7-smp kernel for Edgy and that using the "generic" one actually supports k7-smp. So it wasn't seeing both cores at first and telling me I had the wrong number of CPU's (I was using the i386 kernel at first). So I booted into the "generic" kernel and sure enough everything worked just fine and it appears to be using both my cores as it should. I had to play around with the windows to make it show up properly in Beryl. Here is my latest config;

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
#own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
#default_color white
#default_shade_color white
#default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 60
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
none

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
# Variable Arguments Description
# acpiacadapter ACPI ac adapter state.
# acpifan ACPI fan state
# acpitemp ACPI temperature.
# adt746xcpu CPU temperature from therm_adt746x
# adt746xfan Fan speed from therm_adt746x
# battery (num) Remaining capasity in ACPI or APM
# battery. ACPI battery number can be
# given as argument (default is BAT0).
# buffers Amount of memory buffered
# cached Amount of memory cached
# color (color) Change drawing color to color
# cpu CPU usage in percents
# cpubar (height) Bar that shows CPU usage, height is
# bar's height in pixels
# downspeed net Download speed in kilobytes
# downspeedf net Download speed in kilobytes with one
# decimal
# exec shell command Executes a shell command and displays
# the output in torsmo. warning: this
# takes a lot more resources than other
# variables. I'd recommend coding wanted
# behaviour in C and posting a patch .
# execi interval, shell Same as exec but with specific interval.
# command Interval can't be less than
# update_interval in configuration.
# fs_bar (height), (fs) Bar that shows how much space is used on
# a file system. height is the height in
# pixels. fs is any file on that file
# system.
# fs_free (fs) Free space on a file system available
# for users.
# fs_free_perc (fs) Free percentage of space on a file
# system available for users.
# fs_size (fs) File system size
# fs_used (fs) File system used space
# hr (height) Horizontal line, height is the height in
# pixels
# i2c (dev), type, n I2C sensor from sysfs (Linux 2.6). dev
# may be omitted if you have only one I2C
# device. type is either in (or vol)
# meaning voltage, fan meaning fan or temp
# meaning temperature. n is number of the
# sensor. See /sys/bus/i2c/devices/ on
# your local computer.
# kernel Kernel version
# loadavg (1), (2), (3) System load average, 1 is for past 1
# minute, 2 for past 5 minutes and 3 for
# past 15 minutes.
# machine Machine, i686 for example
# mails Mail count in mail spool. You can use
# program like fetchmail to get mails from
# some server using your favourite
# protocol. See also new_mails.
# mem Amount of memory in use
# membar (height) Bar that shows amount of memory in use
# memmax Total amount of memory
# memperc Percentage of memory in use
# new_mails Unread mail count in mail spool.
# nodename Hostname
# outlinecolor (color) Change outline color
# pre_exec shell command Executes a shell command one time before
# torsmo displays anything and puts output
# as text.
# processes Total processes (sleeping and running)
# running_processes Running processes (not sleeping),
# requires Linux 2.6
# shadecolor (color) Change shading color
# stippled_hr (space), Stippled (dashed) horizontal line
# (height)
# swapbar (height) Bar that shows amount of swap in use
# swap Amount of swap in use
# swapmax Total amount of swap
# swapperc Percentage of swap in use
# sysname System name, Linux for example
# time (format) Local time, see man strftime to get more
# information about format
# totaldown net Total download, overflows at 4 GB on
# Linux with 32-bit arch and there doesn't
# seem to be a way to know how many times
# it has already done that before torsmo
# has started.
# totalup net Total upload, this one too, may overflow
# updates Number of updates (for debugging)
# upspeed net Upload speed in kilobytes
# upspeedf net Upload speed in kilobytes with one
# decimal
# uptime Uptime
# uptime_short Uptime in a shorter format
#
# seti_prog Seti@home current progress
# seti_progbar (height) Seti@home current progress bar
# seti_credit Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Boldixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a %b %d}${alignr -25}${time %k:%M}

TEXT
${color #000000}
$nodename
$kernel
$stippled_hr
$time
$stippled_hr
load: $loadavg
$stippled_hr
AMD Athlon(tm) 64 X2 3800+ 
Core 1: ${cpu cpu1}% ${cpubar cpu1}
${cpugraph cpu1 000000 000000}
Core 2: ${cpu cpu2}% ${cpubar cpu2}
${cpugraph cpu2 000000 000000}
proces: $processes run: $running_processes
$stippled_hr
memory:
 ram: ${alignr}$mem / $memmax ${membar 5,120}
 swp: ${alignr}$swap / $swapmax ${swapbar 5,120}
$stippled_hr
hard disks:
 / ${alignr}${fs_used /} / ${fs_size /} ${color #000000}${fs_bar 5,95 /}
 home ${alignr}${fs_used /home} / ${fs_size /home} ${fs_bar 5,95 /home}
 storage ${alignr}${fs_used /mnt/storage} / ${fs_size /mnt/storage} ${fs_bar 5,95 /mnt/storage}
$stippled_hr
cpu usage         PID     CPU%   MEM%
 ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
 ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
 ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

mem usage
 ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
 ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
 ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$stippled_hr
eht0: ${addr eth0}

down: ${downspeed eth0} k/s $alignr up: ${upspeed eth0} k/s
${downspeedgraph eth0 27,120 000000 000000} $alignr${upspeedgraph eth0 27,120 000000 000000}
${totaldown eth0} $alignr${totalup eth0}
$stippled_hr
port(s)${alignr}#connections
inbound: ${tcp_portmon 1 32767 count} outbound: ${tcp_portmon 32768 61000 count}${alignr}total: ${tcp_portmon 1 65535 count}

inbound connection ${alignr} local service/port
${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}

```

---

### Post by NPALeech on 2006-10-23
Just thought I'd update: After installing the latest NVIDIA driver, my issue with the entire desktop flickering has stopped.

Edit: Well conky just started flickering now... *Sigh* It is better than having everything else flicker though.

---

### Post by OffHand on 2006-10-23
> **NPALeech said:**
> Just thought I'd update: After installing the latest NVIDIA driver, my issue with the entire desktop flickering has stopped.

Edit: Well conky just started flickering now... *Sigh* It is better than having everything else flicker though.

Do you have this line in your conkyrc file?

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

---

### Post by NPALeech on 2006-10-23
Yeah that's in there. Here's my conkyrc anyways:

> # UBUNTU-CONKY
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
#own_window yes
#own_window_hints undecorated,below,skip_taskbar
#background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
CPU: ${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:        $memperc%       ${membar 6}$color
Swap:       $swapperc%       ${swapbar 6}$color

Root:       ${fs_free_perc /}%        ${fs_bar 6 /}$color 
hda1:       ${fs_free_perc /media/hda1}%        ${fs_bar 6 /media/hda1}$color 
$color$stippled_hr
Internet/Networking Status (${addr eth0}):
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,190 000000 ff0000} ${alignr}${upspeedgraph eth0 25,190 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$color$stippled_hr
SYSTEM LOG TAIL
${execi 30 tail -n3 /var/log/messages | fold -w67}
$color$stippled_hr
${execi 120 fortune -s | fold -w67}
${execi 15 wmctrl -R " - conky"}

Any problems? I was told already that my xorg.conf was fine, so hopefully there's something I over-looked here.

---

### Post by tturrisi on 2006-10-24
Thought I'd add to this guide..

Hard Drive Temperature in Conky:
[http://ubuntuforums.org/showthread.php?t=282353&highlight=conky](http://ubuntuforums.org/showthread.php?t=282353&highlight=conky)

---

### Post by FreakinSyco on 2006-10-31
> **Camino said:**
> Hi,
thanks for this nice tutorial...never thought that such a cool monitor exists :)

Just got one small problem. The memory usage is not correctly shown (have a look at the attached screenshot)

Anybody else noticed this too or is just me ?

Bye

Did anyone ever figure this out? I have the exact same problem. Conky shows mem usage as about 98% while system monitor shows it to be roughly 30%.

---

### Post by TLE on 2006-11-02
> **FreakinSyco said:**
> Did anyone ever figure this out? I have the exact same problem. Conky shows mem usage as about 98% while system monitor shows it to be roughly 30%.

Well one of you will have to post your concyrc, it's not realy possible to help you without it.

---

### Post by sibrand on 2006-11-03
Hello there,

My first post on this board. :p 

I've now got a nice conky-config, but how on earth can you format those Name-PID-CPU%-MEM% things I see here ? I just can't get all the PID's, CPU, MEM%'s start from the same width. :mad: 

Many thanks in advance ! ;)

---

### Post by OffHand on 2006-11-03
> **sibrand said:**
> Hello there,

My first post on this board. :p 

I've now got a nice conky-config, but how on earth can you format those Name-PID-CPU%-MEM% things I see here ? I just can't get all the PID's, CPU, MEM%'s start from the same width. :mad: 

Many thanks in advance ! ;)

Hi Sibrand and welcome on the forums. 
Could you please post a screenshot and your conkyrc file.

---

### Post by DanielSmith604 on 2006-11-03
> **seldon77 said:**
> 6. Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot!

Is there a way I can do that in the Terminal? I'm using nUbuntu and I don't get the GNOME menu system that you get :)

And since we're posting out conky setups:

[[IMG]http://img53.imageshack.us/img53/4857/desktopzj7.th.png[/IMG]](http://img53.imageshack.us/my.php?image=desktopzj7.png)

---

### Post by OffHand on 2006-11-03
> **DanielSmith604 said:**
> Is there a way I can do that in the Terminal? I'm using nUbuntu and I don't get the GNOME menu system that you get :)

And since we're posting out conky setups:

[[IMG]http://img53.imageshack.us/img53/4857/desktopzj7.th.png[/IMG]](http://img53.imageshack.us/my.php?image=desktopzj7.png)

You could use this script (put it in /home for instance) and make a shortcut to it. It's not automatically but you can easily toggle conky on/off with it.
```

#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky

fi

```

---

### Post by sibrand on 2006-11-03
> **OffHand said:**
> Hi Sibrand and welcome on the forums. 
Could you please post a screenshot and your conkyrc file.
A screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=18820&stc=1&d=1162600130[/IMG]


The piece of code I need to change to have it shown properly:
```
${color #888888}cpu usage
${color #CCCCCC} name            pid     cpu%   mem%
${color #ddaa00} ${top name 1} ${color #888888}${top pid 1} ${top cpu 1} ${top mem 1}
${color #888888} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #888888} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #888888}mem usage
${color #ddaa00} ${top_mem name 1} ${color #888888}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #888888} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #888888} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
```
I want to have it shown like the config of DanielSmith604 (just above me), name/pid/cpu%/mem% starting at the same point, for every process.

---

### Post by OffHand on 2006-11-04
> **sibrand said:**
> A screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=18820&stc=1&d=1162600130[/IMG]


The piece of code I need to change to have it shown properly:
```
${color #888888}cpu usage
${color #CCCCCC} name            pid     cpu%   mem%
${color #ddaa00} ${top name 1} ${color #888888}${top pid 1} ${top cpu 1} ${top mem 1}
${color #888888} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #888888} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #888888}mem usage
${color #ddaa00} ${top_mem name 1} ${color #888888}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #888888} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #888888} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
```
I want to have it shown like the config of DanielSmith604 (just above me), name/pid/cpu%/mem% starting at the same point, for every process.
```

${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
```

Try that one. Adjust the color codes to yours.

---

### Post by sibrand on 2006-11-04
Thanks for your reply, but as you can see below, it doesn't make any difference. 
I've tried several things with the Tab-key, but that also didn't give the result I was hoping for.

[[IMG]http://img98.imageshack.us/img98/6598/screenshotph2.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=screenshotph2.jpg)

---

### Post by OffHand on 2006-11-04
> **sibrand said:**
> Thanks for your reply, but as you can see below, it doesn't make any difference. 
I've tried several things with the Tab-key, but that also didn't give the result I was hoping for.

[[IMG]http://img98.imageshack.us/img98/6598/screenshotph2.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=screenshotph2.jpg)

Just make a bit more or less space (with space bar) where it's out of line.

---

### Post by aristotlewilde on 2006-11-04
I found this quite helpful in my setup...

[http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")

---

### Post by sibrand on 2006-11-04
> **OffHand said:**
> Just make a bit more or less space (with space bar) where it's out of line.Sounds very obvious, but different names don't have the same length. :neutral:

---

### Post by OffHand on 2006-11-04
> **sibrand said:**
> Sounds very obvious, but different names don't have the same length. :neutral:

True, that's why you need more space after the process so everything will fit.

---

### Post by ~LoKe on 2006-11-04
Does anyone have a good configuration for Dual Core systems with temp monitoring?

---

### Post by OffHand on 2006-11-04
> **~LoKe said:**
> Does anyone have a good configuration for Dual Core systems with temp monitoring?

Start reading from post #199 and up on this page:

[http://www.ubuntuforums.org/showthread.php?t=205865&page=20&highlight=conky](http://www.ubuntuforums.org/showthread.php?t=205865&page=20&highlight=conky)

This is all I could find out about dual core.

---

### Post by ~LoKe on 2006-11-04
> **OffHand said:**
> Start reading from post #199 and up on this page:

[http://www.ubuntuforums.org/showthread.php?t=205865&page=20&highlight=conky](http://www.ubuntuforums.org/showthread.php?t=205865&page=20&highlight=conky)

This is all I could find out about dual core.

I've got one going for Dual Core, was just wondering what others had come up with.  Thanks. =]

---

### Post by Linuturk on 2006-11-05
I'm running Edgy Eft, and I noticed that the repos have the 1.42-1 version. Should I use this one instead?

---

### Post by OffHand on 2006-11-05
> **Linuturk said:**
> I'm running Edgy Eft, and I noticed that the repos have the 1.42-1 version. Should I use this one instead?

If it works I wouldn't change it. A new release should come soon but I do not have an eta.

---

### Post by lammer on 2006-11-05
Does anyone know how to get this perl script work?

[http://conky.sourceforge.net/gmail.pl](http://conky.sourceforge.net/gmail.pl)

It shows your current **gmail inbox into conky**, and I think it should be lighter than the "gmail updater" that I'm running right now...

---

### Post by DanielSmith604 on 2006-11-05
> **OffHand said:**
> You could use this script (put it in /home for instance) and make a shortcut to it. It's not automatically but you can easily toggle conky on/off with it.
```

#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky

fi

```

Thanks for the help but I'm looking for this type of activity:

'conky' starts 30 seconds after 'startx' initiates. Also end 'conky' when you stop x

:-D

---

### Post by hikaricore on 2006-11-05
> **lammer said:**
> Does anyone know how to get this perl script work?

[http://conky.sourceforge.net/gmail.pl](http://conky.sourceforge.net/gmail.pl)

It shows your current **gmail inbox into conky**, and I think it should be lighter than the "gmail updater" that I'm running right now...

[http://gentoo-wiki.com/TIP_conky](http://gentoo-wiki.com/TIP_conky)

has some info on using grep and cat to parse perl scripts and use them in conky, sorry I don't have alot of time to test it out for ya just thought I'd point you in the right direction.  the info they have is used for the xmms info script but with a little tinkering i'm sure it can be adapted for your use :)

---

### Post by adam.tropics on 2006-11-11
Cheers. Excellent!

---

### Post by adam.tropics on 2006-11-12
Using this to check a pop mail account, it is meant to check apparently every 5 mins by default. If it finds mail, it registers it and displays as expected, but then doesn't update it again, any ideas?

```
Yahoo Email: $alignr${pop3_unseen pop.mail.yahoo.com.au **username** **password**} new messages
```

---

### Post by Don_DiZzLe on 2006-11-20
Im trying to compile conky 1.4.4 with the following

./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-own-window --enable-proc-uptime --enable-hddtemp --enable-mpd --enable-imlib2 --enable-portmon --enable-double-buffer --enable-xdamage --enable-x11

However the last 2 lines read:

checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage

How do I fix this?

Edit: I fixed it! I had to install libxdamage-dev to make it work.

---

### Post by m.musashi on 2006-11-21
I'm having some trouble with conky and kde (also beryl running but the problem exists even without beryl running). As you can see in the attached image, I can't get rid of the black background. I've also included my .conkyrc.

I thought this part might be the problem ```
# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes
```
but commenting out didn't change anything.

Any ideas? Thanks.
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
#own_window yes
#own_window_hints undecorated,below,skip_taskbar
#background yes

## options for beryl
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen
# move below to bottom to add system log data
##SYSTEM LOG TAIL
##${execi 30 tail -n3 /var/log/messages | fold -w67}
##$color$stippled_hr
##${execi 120 fortune -s | fold -w67}
##${execi 15 wmctrl -R " - conky"}

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
Uptime: $uptime
CPU Usage: ${cpu}%   CPU: ${freq}MHz   Load: ${loadavg}   Temp: ${i2c temp 2}
${cpugraph 000000 ffffff}
CPU Fan: ${i2c fan 2} rpm   Case Fan: ${i2c fan 1} rpm

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:   $memperc%       ${membar 6}$color
Swap:  $swapperc%       ${swapbar 6}$color

Root:  ${fs_used} / ${fs_size}: ${fs_free_perc /}% free     ${fs_bar 6 /}$color 
Home:  ${fs_used /home} / ${fs_size /home}: ${fs_free_perc /home}% free    ${fs_bar 6 /home}$color 
$color$stippled_hr
Internet/Networking Status (${addr eth0}):
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,190 000000 0000ff} ${alignr}${upspeedgraph eth0 25,190 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$color$stippled_hr
```

---

### Post by adam.tropics on 2006-11-22
well on mine,

```

# Create own window instead of using desktop (required in nautilus)
#own_window yes
#own_window_hints undecorated,below,skip_taskbar
#background yes
```

are **not** commented, and I have transparent borderless window.

---

### Post by m.musashi on 2006-11-22
> **adam.tropics said:**
> well on mine,

```

# Create own window instead of using desktop (required in nautilus)
#own_window yes
#own_window_hints undecorated,below,skip_taskbar
#background yes
```

are **not** commented, and I have transparent borderless window.

Are you using gnome or kde? I had that first but according to the guide I am supposed to comment those out with kde. I've tried both but I get the black background either way.

---

### Post by adam.tropics on 2006-11-22
Ok, so I had a look into kde with relation to Conky, and I can't see how it should make any difference. With Beryl, it is suggested to start Conky after Beryl has started to prevent shadows etc being drawn. Anyway, the first half of my conkrc, all the config bit is below. See if you can see any other major differences. That's about all I can think of really! Sorry!

```
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont arial:size=9
update_interval 1.0
minimum_size 250 5
draw_shades yes
draw_outline no
draw_borders no
uppercase no
stippled_borders 3
border_margin 9
border_width 10
default_color FFFFFF
own_window_colour brown
own_window_transparent yes
alignment top_right
gap_x 15
gap_y 15
```

---

### Post by m.musashi on 2006-11-22
Thanks for the help. You have a few different setting so I tried them but no luck. I am starting conky after beryl but in all cases I continue to get the black background. If I start gnome I don't have any problems (I first have to uncomment the 3 lines for natilus) so something must be odd between my conky and kde. I'll keep looking.

---

### Post by CoolHand on 2006-11-22
> **DanielSmith604 said:**
> Thanks for the help but I'm looking for this type of activity:

'conky' starts 30 seconds after 'startx' initiates. Also end 'conky' when you stop x

:-D

I use XFCE but I think Gnome and Kde both offer a tool to run commands at startup.  I just write a simple bash script and call it from that startup tool.  By calling a script instead of the individual programs I have total control over what it does.  Below is my script as an example.  You will notice I delay the start of a few programs to allow network-manager time to set up my wifi connection and also I run a check to see if I am plugged in on ethernet or on wifi and adjust things accordingly.  Just FYI I have sudo set up to allow the firestarter widget to run without a password or this wouldn't work.  I also have two different conky rc files for the different network setups.  I hope this helps.

```
#!/bin/sh
#
# Startup script for XFCE4
# This way I can control better the timing 
# and behavior of auto started applications

# Start the drop down terminal
# ... oops tilda has a bug that leaves orphaned
# lock files.  We have just started the desktop
# so lets delete all lock files for tilda
/bin/rm -rf /home/myuser/.tilda/locks
/usr/bin/tilda &

# Detect network interface and adjust
# firewall and desktop monitor
ifconfig eth0 | grep -q "inet addr"
if [ $? = 0 ]
then
    sudo sed -i 's/wlan0/\eth0/' /etc/firestarter/configuration
    CONKY="/home/myuser/.conkyrc-eth0"
else
    sudo sed -i 's/eth0/\wlan0/' /etc/firestarter/configuration
    CONKY="/home/myuser/.conkyrc"
fi

# Start conky with slight delay
# to allow for network association
sleep 30
/usr/bin/conky -c $CONKY

# Start the firewall after a delay
sleep 10
/usr/bin/xhost + local:root
sudo /usr/sbin/firestarter --start-hidden &

```

---

### Post by ~LoKe on 2006-11-22
CoolHand, could I by chance get your **entire** config?

---

### Post by CoolHand on 2006-11-23
> **~LoKe said:**
> CoolHand, could I by chance get your **entire** config?

Sure.  I attached my full config (both actually) and all the support files.  There are several scripts I have gotten from others and modified for my own use for gathering rss feeds and the weather.  I have left credits in the headers where I used others code.  You have to have curl and xsltproc installed for it all to work.  Both are available with apt-get.  I also added a better updated screenshot from my notebook PC which is the one I use most.  I don't mind sharing.  I put alot of time into my setup to get it just the way I like.  Hope you find it useful.

---

### Post by ~LoKe on 2006-11-23
After a little bit of hacking and slashing, it works!  It's perfect.  Thanks a lot. ;)

---

### Post by m.musashi on 2006-11-24
> **m.musashi said:**
> I'm having some trouble with conky and kde (also beryl running but the problem exists even without beryl running). As you can see in the attached image, I can't get rid of the black background. I've also included my .conkyrc.

I'm replying to myself so anyone interested can view the original post easily. Hope that is okay.

I played around with this some more. I started with a fresh copy of the .conkyrc from the how-to and commented out the parts not needed for kubuntu. Now I get one big black screen with only the conky text that is not black visible. After some playing around with the settings, I noticed that turning off the double buffer option fixed the display but now conky "flickers".

Anyone know a solution to this (besides not using kde:))?

Thanks.

---

### Post by Don_DiZzLe on 2006-11-26
> Sure. I attached my full config (both actually) and all the support files. There are several scripts I have gotten from others and modified for my own use for gathering rss feeds and the weather. I have left credits in the headers where I used others code. You have to have curl and xsltproc installed for it all to work. Both are available with apt-get. I also added a better updated screenshot from my notebook PC which is the one I use most. I don't mind sharing. I put alot of time into my setup to get it just the way I like. Hope you find it useful.

Thnx alot for posting your files here, but I do have one question, I know that the configuration file .conkyrc goes in my homefolder but what about u'r files, where do I put them?

---

### Post by tturrisi on 2006-11-26
> **m.musashi said:**
> I'm replying to myself so anyone interested can view the original post easily. Hope that is okay.

I played around with this some more. I started with a fresh copy of the .conkyrc from the how-to and commented out the parts not needed for kubuntu. Now I get one big black screen with only the conky text that is not black visible. After some playing around with the settings, I noticed that turning off the double buffer option fixed the display but now conky "flickers".

Anyone know a solution to this (besides not using kde:))?

Thanks.
re conky flickers:
add this to your /etc/x11/xorg.conf
```
Section "Module"
	Load	"dbe"
```
& restart X (ctrl-alt-backspace).

from the Conky FAQs: [http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)
[i]#
3. Q: Conky won't stop flickering

A: Conky is designed to draw to the root desktop window. However, there are several other applications which like drawing to the root desktop window. Because of this, Conky has two options available to get around this problem:

    * You can try enabling double-buffer. Conky's double-buffer option uses the X double-buffer extension to provide a flicker-free Conky.
    * Conky can run in windowed mode, meaning that instead of drawing the the root window it draws to it's own window. You can move this window around and resize it by right-clicking or left-clicking on the window while holding down the Alt key.[/i]

---

### Post by CoolHand on 2006-11-26
> **Don_DiZzLe said:**
> Thnx alot for posting your files here, but I do have one question, I know that the configuration file .conkyrc goes in my homefolder but what about u'r files, where do I put them?

What I do is put them all in the same location and then create a link using ln -s in my home dir.  That way I can keep it all nice and clean.  As for where to put them it doesn't really matter.  Wherever you prefer.  Just after you decide you will need to edit the .conkyrc file and the weather script to adjust the paths to the scripts.

---

### Post by Don_DiZzLe on 2006-11-26
I see that the weather is only available if u live in the USA, what about other countries (NL) ?

---

### Post by m.musashi on 2006-11-26
@tturrisi

Thanks for the help. I do have the "dbe" part in my xorg.conf but without the double buffer option it doesn't seem to help. It all works fine in gnome but in kde I get the black background, the whole screen black or missing desktop icons. There doesn't seem to be an option that works well in kde (at least for me).

I'll try some of the other option you suggest. Thanks.

---

### Post by adam.tropics on 2006-11-27
> **Don_DiZzLe said:**
> I see that the weather is only available if u live in the USA, what about other countries (NL) ?


No mate, you can use it from pretty much anywhere. I do, and I am in Cairns Australia....hardly a major city!

Anyway, to get location id, from a terminal, do (Example for Amsterdam!)

```
wget http://xoap.weather.com/search/search?where=Amsterdam
```This will create a small text file in your home directory, part of which will be

```
<loc id="NLXX0002" type="1">Amsterdam, Netherlands</loc>
```...and Bob's your Uncle!

---

### Post by ~LoKe on 2006-11-27
I found my location...
> <loc id="CAXX0255" type="1">London, Canada</loc>
But I don't know where to put "CAXX0255" or if I'm only supposed to use "0255".  I googled around and read that I'm supposed to change a line in .conkyrc, so I found it:
```
${color #e9c703}Local Weather:
$color${execi 1800 /usr/bin/conky2/weather.gov.sh 0520}
```
so I changed "0520" to "0255" and then conky complained about not being able to find the page.  Any ideas?

---

### Post by adam.tropics on 2006-11-27
> **~LoKe said:**
> I found my location...

But I don't know where to put "CAXX0255" or if I'm only supposed to use "0255".  I googled around and read that I'm supposed to change a line in .conkyrc, so I found it:
```
${color #e9c703}Local Weather:
$color${execi 1800 /usr/bin/conky2/weather.gov.sh 0520}
```so I changed "0520" to "0255" and then conky complained about not being able to find the page.  Any ideas?

You can test by just running the script from a terminal before you edit conky itself. The output, with your **FULL** location id is below.

```
adamtropics@adam-laptop:~/weather$ ./weather.sh CAXX0520
Location: Saint-Hubert, Canada:
Temperature: 5C
Feels Like: 3C
Humidity: 93%
Conditions: Cloudy
Wind: 8km/h (5mph) (N)
Tomorrow: 1C to 7C, Few Showers
```...and  might I say...that's damned cold! (8) currently at 32C !)

So in .conkyrc you want
```

${color #e9c703}Local Weather:
$color${execi 1800 /usr/bin/conky2/weather.gov.sh CAXX0255}
```

..and so long as your script location is correct, you should be set.

---

### Post by ~LoKe on 2006-11-27
I get a page not found error when I run that.  I must have screwed something up when I was tinkering with it earlier.  Thanks, at least I know I'm going in the right direction. ;)

---

### Post by adam.tropics on 2006-11-27
> **~LoKe said:**
> I get a page not found error when I run that.  I must have screwed something up when I was tinkering with it earlier.  Thanks, at least I know I'm going in the right direction. ;)

Well I have attached my weather stuff. If you try it, and even if you don't, make sure with your script that the run directory is actually where it, and the xslt file are. The main difference is that mine uses the weather.com server rather than the weather.gov....other than that, not much, they are based off the same work. Oh, and make sure you have curl installed.

---

### Post by ~LoKe on 2006-11-27
Those scripts fixed the problem.  Weather.gov is not available for Canada, but .com is.

Thanks!

---

### Post by CoolHand on 2006-11-27
> **~LoKe said:**
> Those scripts fixed the problem.  Weather.gov is not available for Canada, but .com is.

Thanks!

Sorry I didn't reply sooner.  Glad you figured it out.  I would have told you that the original script was for weather.com.  I prefer the noaa weather service here in the US so I changed the script to point to them and toyed with the output format for what information I wanted to see.

---

### Post by ice60 on 2006-11-29
how do you get it to tail /var/log/messages? is it suppose to run as root?

---

### Post by ~LoKe on 2006-11-29
> **ice60 said:**
> how do you get it to tail /var/log/messages? is it suppose to run as root?

Runs as regular user just fine for me.

---

### Post by ice60 on 2006-11-29
> **~LoKe said:**
> Runs as regular user just fine for me.
thanks, i had a feeling someone would say that :rolleyes: i'm actually running suse, i compiled it myself too, but i put the blame on suse, not my compilation :mrgreen:

---

### Post by HeSh on 2006-11-29
Is it safe to use conky 1.4.2-1 from repository? In conky guide on EdgyCust pages author said "Note that at the time of writing this how-to, the conky in the ubuntu universe repository is very old and, in ways, broken." Is he refering to this version?

---

### Post by OffHand on 2006-11-29
> **HeSh said:**
> Is it safe to use conky 1.4.2-1 from repository? In conky guide on EdgyCust pages author said "Note that at the time of writing this how-to, the conky in the ubuntu universe repository is very old and, in ways, broken." Is he refering to this version?

He was referring to another (older) version. The latest version is  Conky 1.4.4. The one you have in the repositories is ok to use.

---

### Post by damnhappy on 2006-11-29
I have conky up and running and even managed to customize it a little. A great thing. Thanks for a great tutorial. I was wondering if there was a way to get the conky so it runs from the notification area instead of the bottom panel. You know, the way gaim does.  

Thanks again!

---

### Post by OffHand on 2006-11-30
> **damnhappy said:**
> I have conky up and running and even managed to customize it a little. A great thing. Thanks for a great tutorial. I was wondering if there was a way to get the conky so it runs from the notification area instead of the bottom panel. You know, the way gaim does.  

Thanks again!

That is not possible. You can make a toggle button though. See this post: [http://www.ubuntuforums.org/showpost.php?p=1710345&postcount=241](http://www.ubuntuforums.org/showpost.php?p=1710345&postcount=241)

Btw: Conky shouldn't show in your panel. It should merge with your desktop.

---

### Post by damnhappy on 2006-11-30
Ok, I don't need it in the task tray; just a thought. What I really want is for the button on my bottom panel to go away. Here is a screenshot to make clear my vague descriptions.
Thanks ! :mrgreen:
[IMG]http://innerphaze.homelinux.com/images/Screenshot.png[/IMG]

---

### Post by OffHand on 2006-11-30
I need to see your conkyrc file. Can you post it?

---

### Post by damnhappy on 2006-11-30
Sure: 
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
# -- Pengo (conky@)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_type desktop

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda2:  ${fs_free_perc /media/hda2}%   ${fs_bar 6 /media/hda2}$color
hda5:  ${fs_free_perc /media/hda5}%   ${fs_bar 6 /media/hda5}

${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color red}To Do ${hr 2}$color
${execi 30 tail -n3 /home/dan/to_do | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

```

---

### Post by OffHand on 2006-11-30
It's going wrong somewhere here:

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_type desktop

You have two types of own_window_type. You gotta pick one.

This is my setup. You could try to backup your conkyrc and then replace the part above with mine. Sometimes it takes a bit of tweaking. Not all machines react the same.


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

---

### Post by CoolHand on 2006-11-30
> **ice60 said:**
> how do you get it to tail /var/log/messages? is it suppose to run as root?

If you are using a different distro or have your permissions set up different you have two options if you want to run it as a user.  Add yourself to a group that has read permissions on the messages file or add read permission for everyone.  The group option is much safer but it is your choice as you know how your machine is used.

---

### Post by damnhappy on 2006-11-30
Ok, this is my latest attempt.
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints skip_taskbar
own_window_type desktop

```
I tried it with ```
own_window override
``` and ```
own_window_hints undecorated,below,skip_taskbar 
```

Nothing has worked yet. I am open for other suggestions. 

Thanks for helpin.

---

### Post by m.musashi on 2006-11-30
Is the panel button (or whaterver they are called) from conky? I suppose that might be a dumb question but having never seen that before I'm wondering it it could be say from the terminal or other app.

What happens if you comment out or remove this line -> own_window_type desktop? Or is that what you already tried?

By the way, that looks like a pretty nice desktop from what I can see. What is the theme?

---

### Post by baalthazar on 2006-12-01
greeting people!
there is something weird when i installed conky... 
it shows 88% of root and it doesnt detect my Sata drive... 
could some1 help me fix this?

---

### Post by ice60 on 2006-12-01
> **CoolHand said:**
> If you are using a different distro or have your permissions set up different you have two options if you want to run it as a user.  Add yourself to a group that has read permissions on the messages file or add read permission for everyone.  The group option is much safer but it is your choice as you know how your machine is used.
thanks, i screwed up with sudoers :rolleyes: but, then put it back to normal because i wanted some rss feeds instead. (i didn't have enough space)

i still need to fix the temp though :|

i got the rss feeds and weather from here -
[http://www.suseforums.net/index.php?showtopic=24669&pid=144272&st=0&#entry144272](http://www.suseforums.net/index.php?showtopic=24669&pid=144272&st=0&#entry144272)

i added a netstat command too from the suse link. you can see it in my screenshot where it says irssi :cool: 

baalthazar,  i suppose i have the same problem, i'd forgotten.

---

### Post by damnhappy on 2006-12-01
m.musashi, the button is from conky. I tried removing the line own_window_type desktop and it didn't help.
My desktop I got from [URL="http://www.gnome-look.org/content/show.php?content=43054"]http://www.gnome-look.org/content/show.php?content=43054
[/URL]
It's called LiNsta (linux is not vista) Conky was the cherry on top. 
Here is my desktop. ice60, yours is awesome too. I dig the dragon. 

Sorry can't help with thte SATA issue. My hard drive thingy wasn't working because I forgot to change to default drive letters, but it showed as all full. Like the rss too!

---

### Post by OffHand on 2006-12-01
> **damnhappy said:**
> m.musashi, the button is from conky. I tried removing the line own_window_type desktop and it didn't help.
Dont' remove it. Change desktop for normal or override. Did you try to copy that whole part I posted earlier?

---

### Post by damnhappy on 2006-12-01
Hi Offhand, 
I put the line back, because I figured it wasn't good to get rid of it. I tried your code. That is what I have now.

---

### Post by damnhappy on 2006-12-01
Hi again, I just closed Cronky, then retarted it from the terminal and the terminal said this: 
```
Conky: /home/dan/.conkyrc: 16: no such configuration: 'own_window_hints'
Conky: /home/dan/.conkyrc: 17: no such configuration: 'own_window_type'
Conky: can't load font 'arial'
Conky: failed to set up double buffer
Conky: drawing to single buffer

```
Don't know if that helps.

---

### Post by OffHand on 2006-12-01
> **damnhappy said:**
> Hi again, I just closed Cronky, then retarted it from the terminal and the terminal said this: 
```
Conky: /home/dan/.conkyrc: 16: no such configuration: 'own_window_hints'
Conky: /home/dan/.conkyrc: 17: no such configuration: 'own_window_type'
Conky: can't load font 'arial'
Conky: failed to set up double buffer
Conky: drawing to single buffer

```
Don't know if that helps.

I don't know if you know how to use IRC, but if you login on the freenode server and /join #conky I am sure they can help you.

---

### Post by damnhappy on 2006-12-01
Ok, I will check there.

---

### Post by m.musashi on 2006-12-01
> **OffHand said:**
> Dont' remove it. Change desktop for normal or override. Did you try to copy that whole part I posted earlier?

Sorry, I meant to say that I didn't have that option (desktop) but didn't catch that is should have been "override" (at least that is what I have) and not removed.

EDIT: Actually, this is what I was referring to:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_type desktop
```
own_window_type appears twice. Comment out or remove one of them. I don't think the option should be there twice.

---

### Post by ice60 on 2006-12-01
hi, i fixed everything now, apart from the columns aren't straight ](*,) does anyone know how to fix it? these - PID CPU% MEM%

---

### Post by ice60 on 2006-12-01
> **baalthazar said:**
> greeting people!
there is something weird when i installed conky... 
it shows 88% of root and it doesnt detect my Sata drive... 
could some1 help me fix this?

i used these instead for the SATA drives, nothing else worked - sda sda2 sdb etc lol - 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color

---

### Post by ice60 on 2006-12-01
> **damnhappy said:**
> Hi again, I just closed Cronky, then retarted it from the terminal and the terminal said this: 
```

Conky: can't load font 'arial'

```
Don't know if that helps.
i fixed the arial problem by deleting the whole arial font line and adding these instead -
```
# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont "dejavu sans mono":size=9

# Text alpha when using Xft
xftalpha 1.0
```
you can pick whichever font you like, even arial.
MAKE A BACKUP FIRST :|

---

### Post by m.musashi on 2006-12-02
> **ice60 said:**
> hi, i fixed everything now, apart from the columns aren't straight ](*,) does anyone know how to fix it? these - PID CPU% MEM%

I'm not sure but I think it's because you are not using a mono-spaced font. Mine says it's using Ariel and I didn't think that was mono-spaced but on screen it looks like it is. From your screen shot, it looks like your font is not mono-spaced.

---

### Post by OffHand on 2006-12-02
> **ice60 said:**
> hi, i fixed everything now, apart from the columns aren't straight ](*,) does anyone know how to fix it? these - PID CPU% MEM%

Start reading here: [http://www.ubuntuforums.org/showthread.php?t=205865&page=25](http://www.ubuntuforums.org/showthread.php?t=205865&page=25)

---

### Post by baalthazar on 2006-12-02
hello ppl!
i was playing with my conky setup and blew it, dont know where i messed it but im pretty sure its a comment i put in and now it looks like a big black box. i also wanted to get the temp of the cpy, but its not showing... could some1 help me fix it.

btw, i wanted to add the graph with the gradient effect and now i have 4 graphs, i tried to comment them but they dont dissapear.

and also, when ppl are happy with their setup of conky shoul put the source too..

heres my source too see if some1 could help me with the lil probs i have...

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
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color black

own_window_colour black
own_window_trans

parent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
CPU: AMD64 Turion 3200 @ ${freq}MHz   Load: ${loadavg}   Temp: ${execi 30 sensors |grep "CPU" |cut -d " " -f6}
$cpubar
${cpugraph}$color

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:        $memperc%       ${membar 6}$color
Swap:       $swapperc%       ${swapbar 6}$color

Root:       ${fs_free_perc /}%        ${fs_bar 6 /}$color 
Frispace!:  ${fs_free_perc /media/hda1}%        ${fs_bar 6 /media/sda1}$color 
$color$stippled_hr
Internet/Networking Status (${addr eth0}) Total: ${totaldown eth0} Down ${totalup eth0} Up
Down: ${downspeedf eth0} k/s ${alignr}Up: ${upspeedf eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$stippled_hr

#Down: #${downspeed eth0} k/s ${offset 110}Up: #${upspeed eth0} 1k/s
#${downspeedgraph eth0 32,200} ${upspeedgraph eth0 32,200}
#${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
$color$stippled_hr
SYSTEM LOG TAIL
${execi 30 tail -n3 /var/log/messages | fold -w67}
$color$stippled_hr
${execi 300 fortune -s | fold -w67}
${execi 60 wmctrl -a conky}

```

---

### Post by tturrisi on 2006-12-02
re if Conky showing up on the taskbar, use these hints:

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

re weather:

pymetar still works w/ conky, thus no need for weather.com, get the weather data directly.
apt-get install python-pymetar
add to conkyrc
${execi 60 /usr/bin/pymetar KIAD}  #where KIAD = the station you want to grab weather data
get your station here:
[http://www.nws.noaa.gov/tg/siteloc.shtml](http://www.nws.noaa.gov/tg/siteloc.shtml)

tweak the pymetar output by editing the file called pymetar in /usr/bin as root

---

### Post by ice60 on 2006-12-02
> **m.musashi]I'm not sure but I think it's because you are not using a mono-spaced font.[/QUOTE]yeap, it was the fonts lol, thanks.

[QUOTE=OffHand said:**
> Start reading here: [http://www.ubuntuforums.org/showthread.php?t=205865&page=25](http://www.ubuntuforums.org/showthread.php?t=205865&page=25)
thanks, but it turned out to be the xftfonts :rolleyes: i shouldn't have changed it in the first place lol.

i decided to go with the font error as i like the look of it best :biggrin:

---

### Post by Omnios on 2006-12-02
Hi hi, this rates :KS:KS:KS:KS:KS. Conky is very light weight and works well. Thank you for the config file as it makes setting it up easier than before though I had to change the text color and the orange to red.

---

### Post by ice60 on 2006-12-02
this might stop the text from moving about if you use the xftfonts
```
# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
```
i've spent too much time monkeying about with conky the last day or so to try it atm, i'll try it tomorrow :|

here's my latest effort looooooool does anyone know how to make the text disappear off the screen rather than conky? ](*,)

---

### Post by Junk_head on 2006-12-02
Would Conky be able to make a setup like this [[IMG]http://img120.imageshack.us/img120/6856/extv8.th.png[/IMG]](http://img120.imageshack.us/my.php?image=extv8.png)
Samurize is the only thing i miss in windows and I just dig a formal text status display

---

### Post by tturrisi on 2006-12-02
> **Junk_head said:**
> Would Conky be able to make a setup like this [[IMG]http://img120.imageshack.us/img120/6856/extv8.th.png[/IMG]](http://img120.imageshack.us/my.php?image=extv8.png)
Samurize is the only thing i miss in windows and I just dig a formal text status display
yes

---

### Post by damnhappy on 2006-12-02
Hi everyone, 
I got no response from the folks at IRC, they must have been away from the computer and I was too tired to wait up. But happilly, this morning Ubuntu's automatic update had an update for conky and it seemed to solve my problem. The button on the bottom panel is gone! yes! Thanks for all your help. Now I have to get an RSS feed in there. 
:D 
Thanks!

---

### Post by halitech on 2006-12-03
thank you for this, started playing with conky about 2 hours ago and now have it setup the way I want it.

---

### Post by RichJacot on 2006-12-03
Hello,

When I add the weather, via the folling in my .conkyrc file.  

```
${execi 60 /usr/bin/pymetar KDFW}
```

Conky goes very wide.  Is there a way to get the weather to wrap so its not so wide?

Thanks

---

### Post by ice60 on 2006-12-03
here's mine now :| i still need to find out how to stop conky disappearing when there's too much text in a RSS feed :-k

you see where it mentions beep-media-player? that's read from this line 
```
${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
```
what does the cut bit do? and can someone help me apply it to my RSS feeds if it stops the writting going off the screen (like in my last screenshot a few posts ago) i'd like the whole of beep-media-player there too instead of that bit missing :D

---

### Post by tturrisi on 2006-12-04
> **RichJacot said:**
> Hello,

When I add the weather, via the folling in my .conkyrc file.  

```
${execi 60 /usr/bin/pymetar KDFW}
```

Conky goes very wide.  Is there a way to get the weather to wrap so its not so wide?

Thanks
You have to edit your /usr/bin/pymetar file and add or remove sections that are unwanted.  See the files in /usr/share/doc/python-pymetar
Here's mine:
```
#!/usr/bin/python -tt
# -*- coding: iso-8859-15 -*-

__version__="1.0"

import pymetar
import sys

#print "pymet v%s using pymetar lib v%s"%(__version__,pymetar.__version__)

if len(sys.argv)<2 or sys.argv[1]=="--help":
    sys.stderr.write("Usage: %s <station id>\n"% sys.argv[0])
    sys.stderr.write("Station IDs can be found at: http://www.nws.noaa.gov/tg/siteloc.shtml\n")
    sys.exit(1)
elif (sys.argv[1] == "--version"):
    print "pmw v%s using pymetar lib v%s"%(__version__,pymetar.__version__)
    sys.exit(0)
else:
    station=sys.argv[1]

try:
    rf=pymetar.ReportFetcher(station)
    rep=rf.FetchReport()
except Exception, e:
    sys.stderr.write("Something went wrong when fetching the report.\n")
    sys.stderr.write("These usually are transient problems if the station ")
    sys.stderr.write("ID is valid. \nThe error encountered was:\n")
    sys.stderr.write(str(e)+"\n")
    sys.exit(1)

rp=pymetar.ReportParser()
pr=rp.ParseReport(rep)

#print "Weather report for %s (%s) as of %s" %\
#    (pr.getStationName(), station, pr.getISOTime())
#print "Values of \"None\" indicate that the value is missing from the report."
print "Temperature: %s C / %s F" %\
    (pr.getTemperatureCelsius(), pr.getTemperatureFahrenheit())
print "Rel. Humidity: %s%%" % (pr.getHumidity())
if pr.getWindSpeed() is not None:
    print "Wind speed: %0.2f m/s" % (pr.getWindSpeed())
else:
    print "Wind speed: None"
    
print "Wind direction: %s deg (%s)" %\
    (pr.getWindDirection(), pr.getWindCompass())
#if pr.getPressure() is not None:
#    print "Pressure: %s hPa" % (int(pr.getPressure()))
#else:
#    print "Pressure: None"

#print "Dew Point: %s C / %s F" %\
#    (pr.getDewPointCelsius(), pr.getDewPointFahrenheit())
print "Weather:",pr.getWeather()
print "Sky Conditions:",pr.getSkyConditions()
```

---

### Post by RichJacot on 2006-12-04
Worked Great!  Thank you!

---

### Post by CoolHand on 2006-12-04
> **ice60 said:**
> here's mine now :| i still need to find out how to stop conky disappearing when there's too much text in a RSS feed :-k

you see where it mentions beep-media-player? that's read from this line 
```
${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
```
what does the cut bit do? and can someone help me apply it to my RSS feeds if it stops the writting going off the screen (like in my last screenshot a few posts ago) i'd like the whole of beep-media-player there too instead of that bit missing :D

From the man page:
> CUT(1)                           User Commands                          CUT(1)

NAME
       cut - remove sections from each line of files

SYNOPSIS
       cut [OPTION]... [FILE]...

DESCRIPTION
       Print selected parts of lines from each FILE to standard output.
Just do a "man cut" to get the full list of options and how it works.  It is a standard unix command.  In my config I use it to remove the leading charachters from my log files such as system name etc.  That way I see more important info without all the repeating stuff.

---

### Post by CoolHand on 2006-12-04
> **ice60 said:**
> hi, i fixed everything now, apart from the columns aren't straight ](*,) does anyone know how to fix it? these - PID CPU% MEM%

I don't know of any way to auto adjust the spacing.  The problem is the changing values for each text field.  What I found that sort of works is to center justify, ${alignc}, the bar graphs.  That way they all start even at least.

---

### Post by tturrisi on 2006-12-04
> **CoolHand said:**
> I don't know of any way to auto adjust the spacing.  The problem is the changing values for each text field.  What I found that sort of works is to center justify, ${alignc}, the bar graphs.  That way they all start even at least.

Tabs instead of spaces should keep the columns separated.

---

### Post by CoolHand on 2006-12-06
> **tturrisi said:**
> Tabs instead of spaces should keep the columns separated.

I thought I tried that but that may have been on an older version.  I'll have to give it another shot.  Thanks for the tip.

---

### Post by marx2k on 2006-12-12
I have installed all dependencies and am still getting;

checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage


Any suggestions on this?  Trying to install 1.4.4 on Edgy

---

### Post by kret on 2006-12-12
Hello :)

I think I'm having the same problem as m.musashi..I'm using Kubuntu (so KDE) 6.06 and conky 1.4.4..and I'm having problems of course..my desktop either gets all black without icons, either I get black conky window (with own_window yes) or finally I get nice and transparent desktop and conky, but if there is any icon on the desktop it dissapears..and I get this kind of behaviour

[[IMG]http://img134.imageshack.us/img134/1629/conkygr7.th.png[/IMG]](http://img134.imageshack.us/my.php?image=conkygr7.png)

yes, I have enables dbe in my xorg.conf and yes, I have rebooted the computer ;) my .conkyrc file was taken from the first post of this thread and tweaked to suit my taste and needs..though various changes and commenting/uncommenting of own_window and all options mentioned many times above does not give any result..

my thoughts..when I got black conky window and normal desktop (after commenting own_window_transparency yes) the flicker of icons dissapeared..so my conclusion? its something with the fake transparency of the window..

so..how will you help me? :]

oh..yes..and this is my .conkyrc :)
```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# Subtract file system buffers from used memory?
no_buffers yes

# Create own window instead of using desktop (required in nautilus)
own_window_type override
own_window_transparent yes
own_window_hints sticky,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer no

# Use Xft?
use_xft yes
xftfont Clean

# Update interval in seconds
update_interval 3

# Minimum size of text area
# minimum_size 250 5
maximum_width 240

# Draw shades?
draw_shades no

# Text stuff
draw_outline no
draw_borders no
uppercase yes

# Stippled borders?
stippled_borders 10

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 30

# stuff after 'TEXT' will be formatted on screen

TEXT
${color white}kret kubuntu $sysname $kernel on $machine$color
...........................................
date: ${color white}${time %e %B %G} ${alignr}${time %H:%M}$color
uptime: ${color white}${uptime}$color
...........................................
cpu usage: ${color white}$cpu% $cpubar
${cpugraph 25,240 000000 ffffff}  $color
...........................................
RAM USAGE:   ${color white}$mem/$memmax - ${alignr}$memperc% ${membar 6,40}$color
Swap usage:  ${color white}$swap/$swapmax - ${alignr}$swapperc% ${swapbar 6,40}$color
...........................................
processes:
NAME             ${alignr}PID    CPU%   MEM%  
${color white}${top name 1} ${alignr}${top pid 1}${top cpu 1} ${top mem 1}$color
${color white}${top name 2} ${alignr}${top pid 2}${top cpu 2} ${top mem 2}$color
${color white}${top name 3} ${alignr}${top pid 3}${top cpu 3} ${top mem 3}$color
total: ${color white}$processes$color${alignr}running: ${color white}$running_processes$color
...........................................
NETWORK (${addr eth0})
Down: ${color white}${downspeed eth0} k/s$color ${alignr}Up: ${color white}${upspeed eth0} k/s$color
${color white}${downspeedgraph eth0 25,115 000000 ff0000} ${upspeedgraph eth0 25,115 000000 00ff00}$color
Total: ${color white}${totaldown eth0}$color ${alignr}Total: ${color white}${totalup eth0}$color
Inbound: ${color white}${tcp_portmon 1 32767 count}$color     Outbound: ${color white}${tcp_portmon 32768 61000 count}$color${alignr}Total: ${color white}${tcp_portmon 1 65535 count}$color
```

---

### Post by OffHand on 2006-12-12
> **kret said:**
> 
# Create own window instead of using desktop (required in nautilus)
own_window_type override
own_window_transparent yes
own_window_hints sticky,skip_pager

Try: own_window_hints undecorated,below,skip_taskbar

---

### Post by kret on 2006-12-12
nope..same :) tried it before already :) but thanks for the effort..

---

### Post by CoolHand on 2006-12-13
> **kret said:**
> nope..same :) tried it before already :) but thanks for the effort..
I don't use KDE but I used to.  This may be a long shot but in the KDE control center have you enabled the feature to allow applications to draw to the root window?  I don't know that it would fix it but it's worth a try.

---

### Post by kret on 2006-12-13
I dunno if it's the thing you talk about but the only thing I've found involving window transparency was under System Settings -> Desktop -> Windows -> Transparency Tab

and it didn't help.. ;)

---

### Post by m.musashi on 2006-12-15
I found this [http://briancarper.net/2006/08/25/transparent-conky-in-kde-part-2/](http://briancarper.net/2006/08/25/transparent-conky-in-kde-part-2/)

Maybe it will help the conky - kde problem. I'm at work and can't try right now. The trick seems to be to use [feh](http://linuxbrit.co.uk/feh/) or similar to set the root wallpaper to be something other than black.

Anyone know why kde has two desktops (if that's a correct way to put it)?

---

### Post by CoolHand on 2006-12-15
> **m.musashi said:**
> 
Anyone know why kde has two desktops (if that's a correct way to put it)?

Yes, most of the desktops now do that.  They build a "desktop window"  on top of the root window.  I believe the purpose is that it allows them much more control to draw icons and control window placement and such.  While all of that is possible in the real root window I don't know the logistics of doing it.  Take that for what it's worth though as I am no expert on desktop design or anything.

---

### Post by m.musashi on 2006-12-15
Thanks for the info. I'm no expert either (I'm barely a noob). But there seems to be a fundamental difference between gnome and kde here as gnome doesn't have the problems that kde does - with respect to conky and transparency at least.

EDIT: Well, I don't exactly know how or why, but I managed to get conky to work in kde. I right clicked the desktop and chose configure desktop and then under behavior unchecked and checked show desktop icons and allow programs in desktop window and then restarted conky and it works. I can see my desktop icons and conky is transparent.

---

### Post by brohan on 2006-12-16
Might as well post my setup, conky has been my toy for playing around with tiny little ruby scripts to get cool stuff like changing the color of my gmail or bloglines thing when there's new messages.

This thread has been a start, but I hope that my .conkyrc will show some people some aid.

(Should of seriously tar'd this)

Was a good place to learn to use sed and grep :)
(I use a slightly modified version of pymetar, I just edited the file to not put anything in Fahrenheit.

.conkyrc
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft no
update_interval 1.0
draw_shades no 
draw_borders no 
draw_graph_borders no
draw_outline no
uppercase no
stippled_borders 3
border_margin 9
border_width 10
default_color 676f9d
default_shade_color grey
alignment top_left
#gap_y 25 
use_spacer no
TEXT
$nodename	       	${time %Y-%m-%e %r}
$color$stippled_hr
${color #C2C3F3}Load: $color${loadavg}
${color #C2C3F3}CPU: $color${freq}MHz ${color #C2C3F3}Temp: $color${acpitemp}
${color #C2C3F3}Battery: $color${battery}
$cpubar
${cpugraph ffffff 676f9d}
$color$stippled_hr
Processes:$color $processes  Running: $running_processes

Name              PID     CPU%   MEM%
${color #C2C3F3}${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
$color${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

Mem usage
${color #C2C3F3}${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
$color${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #C2C3F3}RAM:   $color$memperc% ${membar 6}
${color #C2C3F3}Swap:  $color$swapperc% ${swapbar 6}

${color #C2C3F3}RAM: $color$mem ${color #C2C3F3}Swap: $color$swap
$color$stippled_hr
${color #C2C3F3}hda1:  $color${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
$color$stippled_hr
eth1
  ${color #C2C3F3}ip: $color${addr eth1}
  ${color #C2C3F3}essid: $color${exec iwconfig eth1 | sed 's/  /\n/g' | grep ESSID | sed 's/ESSID:"//'| sed 's/"//'}
  ${color #C2C3F3}link status: $color${exec iwconfig eth1 | sed 's/  /\n/g' | grep Quality | sed 's/Link Quality://' | sed 's/Link Quality=//' | sed 's/ //g' } ${color #C2C3F3}s: $color${exec iwconfig eth1 | sed 's/  /\n/g' | grep Signal | sed 's/Signal level=//' | sed 's/Signal level://' } 
$color$stippled_hr
${texeci 500 pymetar CYUL > /tmp/.weather}${color #C2C3F3}Temperature:$color${exec grep Temp /tmp/.weather | sed 's/Temperature://'| sed 's/.0 C/ C/'}  ${color #C2C3F3}Wind:$color${exec grep speed /tmp/.weather | sed 's/Wind speed://' }
${color #C2C3F3}Weather: $color${exec grep Weather /tmp/.weather | sed s/'Weather: //' | sed 1d | ~/dev/wordwrap -w 30 | tr [:upper:] [:lower:]}
$color$stippled_hr
${texeci 60 python ~/.gmail.py | /home/brohan/dev/conkyhelper.rb}${color #C2C3F3}Mail Messages: $color${if_existing /tmp/.gmailnew}${color #FF2222}$endif${exec cat /tmp/.gmailcount}
${texeci 60 ~/dev/conkyblog}${color #C2C3F3}Bloglines: $color${if_existing /tmp/.blognew}${color #FF2222}$endif${exec cat /tmp/.blogcount}
$color$stippled_hr
${texeci 5 cat ~/todo | ~/dev/wordwrap -w 40}
$color$stippled_hr
${texeci 120 curl http://brohan.ca/random.php|sed 's/<br>/\n/g'|sed 's/&lt;/</g'|sed 's/&gt;/>/g'|~/dev/wordwrap -w 40 > /tmp/.quote;cat /tmp/.quote}

```

~/dev/wordwrap
```
:
##########################################################################
# Shellscript:	wordwrap - wrap lines on word boundaries
# Author     :	Heiner Steven <heiner.steven@odn.de>
# Date       :	2001-12-10
# Requires   :	
# Category   :	Text Utilities
# SCCS-Id.   :	@(#) wordwrap	1.4 04/09/24
##########################################################################
# Description
#	A very simple text formatting program. The input is read
#	word by word.  All words are joined using a space (ASCII
#	32) character. If "-j" was specified, each line is
#	filled up to the maximum line length, or the next empty
#	line before it is printed. Each continued line can be
#	offset by a number of blanks.
#
# Note
#    o	Leading whitespace is ignored
#    o	An AWK program actually formats the input. It is written in
#	a way to be portable to a wide range of AWK dialects.
#    o  thanks for Samus-Aran for suggesting the "-l" option
#
# Caveats
#    o	Should have an option for keeping whitespace inbetween words
##########################################################################

PN=`basename "$0"`			# Program name
VER='1.4'

# Uncomment the following line to disable the search for the fastest AWK
#: ${AWK:=awk}

DEFWIDTH=72				# Default line length
DEFOFFSET=0				# Default continued line offset
DEFMARGIN=0				# Default left margin

Usage () {
    echo >&2 "$PN - wrap lines on word boundaries, $VER
usage: $PN [-j] [-w width] [-o offset] [-l margin] [file ...]
    -j  join multiple lines up to the maximum line length
    -l  left margin (default $DEFMARGIN)
    -o  offset of continued lines (default $DEFOFFSET)
    -w  max. line width (default is $DEFWIDTH characters)"
    exit 1
}

Msg () {
    for MsgLine
    do echo "$PN: $MsgLine" >&2
    done
}

Fatal () { Msg "$@"; exit 1; }

##########################################################################
# searchprog - search program using search PATH
# usage: searchprog program
##########################################################################

searchprog () {
    _search=$1; shift

    for _dir in `echo "$PATH" | sed "s/^:/.:/;s/:\$/:./;s/::/:.:/g;s/:/ /g"`
    do
        [ -x "$_dir/$_search" ] || continue
        echo "$_dir/$_search"
        return 0
    done

    return 1
}

# isint - is argument a valid integer number?
isint () {
    case "$1" in
    	*[!0-9]*)   return 1;;
	*)	    return 0;;
    esac
}

set -- `getopt :hjl:o:w: "$@"` || Usage
[ $# -lt 1 ] && Usage			# "getopt" detected an error

# Search for an AWK implementation, prefer the fastest one
: ${AWK:=`searchprog mawk || searchprog gawk || searchprog nawk || echo awk`}

LineWidth=
JoinLines=false
LeftMargin=
while [ $# -gt 0 ]
do
    case "$1" in
	-j)	JoinLines=true;;
	-l)	isint "$2" || Fatal "invalid margin: $2"
		LeftMargin=$2; shift;;
	-o)	isint "$2" || Fatal "invalid offset: $2"
		LineOffset=$2; shift;;
	-w)	isint "$2" || Fatal "invalid line width: $2"
		LineWidth=$2; shift;;
	--)	shift; break;;
	-h)	Usage;;
	-*)	Usage;;
	*)	break;;			# First file name
    esac
    shift
done

: ${LineWidth:=$DEFWIDTH}
: ${LineOffset:=$DEFOFFSET}
: ${LeftMargin:=$DEFMARGIN}

$AWK '
    BEGIN {
	WORDSEP = " "
	WORDSEPLEN = length (WORDSEP)
	maxwidth = '"$LineWidth"'
	if ( "'"$JoinLines"'" == "true" ) joinlines = 1; else joinlines = 0;
	line = ""
	offset = '"$LineOffset"'
	margin = '"$LeftMargin"'
	if ( offset >= 1 ) indent = sprintf ("%*s", offset, " ")
	if ( margin >= 1 ) leftmargin = sprintf ("%*s", margin, "")
    }
    {
    	# Special handling: preserve leading whitespace characters
	if ( line == "" ) {
	    for ( i=1; i<length($0); ++i ) {
		c = substr ($0, i, 1)
		if ( c != " " && c != "	" ) break
	    }
	    if ( i > 1 ) line = substr ($0, 1, i-1)
	}

	for ( i=1; i<=NF; ++i ) {
	    newlen = length (line) + length ($i)
	    if ( line != "" ) newlen += WORDSEPLEN
	    if ( newlen > maxwidth ) {
	        print leftmargin line
		line = indent $i
	    } else {
		if ( line != "" ) line = line WORDSEP
		line = line $i
	    }
	}

	# No joining of lines: print the current line immediately

	if ( !joinlines || NF == 0 ) {
	    print leftmargin line
	    if ( line != "" && NF == 0 ) print ""	# preserve empty line
	    line = ""
	}
    }
    END {
	if ( line != "" ) {
	    print leftmargin line
	}
    }
' "$@"


```

gmail.py
```
import feedparser
from sys import stdout
d=feedparser.parse("https://username:password@gmail.google.com/gmail/feed/atom")
stdout.write(str(len(d['entries'])))


```
~/dev/conkyhelper.rb
```
#!/usr/bin/ruby
require 'fileutils'
num = STDIN.read.to_i
if num > 0
	outfile = File.new("/tmp/.gmailnew", "w")
	outfile.puts(num)
	outfile.close
else
	FileUtils.rm_f('/tmp/.gmailnew')
end
countfile = File.new("/tmp/.gmailcount", "w")
countfile.puts(num)
countfile.close


```

~/dev/conkyblog
```
#!/bin/bash
curl 'http://rpc.bloglines.com/update?user=EMAIL_ADDRESS&ver=1' | sed 's/|//g' | ~/dev/conkybloglines.rb

```

~/dev/conkybloglines.rb
```
#!/usr/bin/ruby
require 'fileutils'
num = STDIN.read.to_i
if num > 0
        outfile = File.new("/tmp/.blognew", "w")
        outfile.puts(num)
        outfile.close
else
        FileUtils.rm_f('/tmp/.blognew')
end
countfile = File.new("/tmp/.blogcount", "w")
countfile.puts(num)
countfile.close


```

---

### Post by CoolHand on 2006-12-17
> **m.musashi said:**
> Thanks for the info. I'm no expert either (I'm barely a noob). But there seems to be a fundamental difference between gnome and kde here as gnome doesn't have the problems that kde does - with respect to conky and transparency at least.

EDIT: Well, I don't exactly know how or why, but I managed to get conky to work in kde. I right clicked the desktop and chose configure desktop and then under behavior unchecked and checked show desktop icons and allow programs in desktop window and then restarted conky and it works. I can see my desktop icons and conky is transparent.

The important part there is that you checked "allow programs in desktop window".  I have heard that is key to getting it to work as KDE is more restrictive about drawing to that window.

---

### Post by frenchbuntu on 2006-12-17
Hi

Do you think I could get an eBay module for conky?

Thanks

---

### Post by bugz0r on 2006-12-17
How can I get conky to look like this, except for Miejsce(whatever that is). Font and all please.

---

### Post by m.musashi on 2006-12-17
> **CoolHand said:**
> The important part there is that you checked "allow programs in desktop window".  I have heard that is key to getting it to work as KDE is more restrictive about drawing to that window.
It seems the trick is to uncheck apply and recheck apply and then start conky. This has to be done each time I reboot. Kind of a pain really. The link I gave above had some tips on getting this to work more permanently by setting a root desktop background. However, I suspect that if you change your wallpaper frequently you would have to change it twice each time. Also kind of a pain. If anyone knows a better fix to this I'd appreciate hearing it.

Thanks.

---

### Post by CoolHand on 2006-12-18
> **frenchbuntu said:**
> Hi

Do you think I could get an eBay module for conky?

Thanks

I don't know about a module but you can script just about anything.  It depends on what you want it to do.  Do a few searches and see if someone else has already done it and if you are good with scripting you can do it yourself.  If not maybe you can talk someone else into helping you build a script.

---

### Post by blonder on 2006-12-18
Every Conky that i set have a ugly black background but i want transparency,how is it possible on ubuntu edgy beryl/aiglx ?

---

### Post by OffHand on 2006-12-18
> **blonder said:**
> Every Conky that i set have a ugly black background but i want transparency,how is it possible on ubuntu edgy beryl/aiglx ?

You will have to play with the settings listed below. You might as well start with copying/pasting it into your conkyrc to see if it works on your machine.

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

---

### Post by marx2k on 2006-12-18
Im going to have to re-post my problem here...
New Conky is out 1.4.5... trying to compile it (happens with 1.4.4 as well), I run ./configure and get:

checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage

and it craps out after that.

I *do* have all dependencies installed from the beginning of this thread, so no dice there.

Also, the man page states 
       For  users  compiling from source, make sure you have the X development
       libraries installed.  This should be  a  package  along  the  lines  of
       "libx11-dev or xorg-x11-dev".

Which is done...

Anyone have any hints as to how this can be accomplished?

---

### Post by viuks on 2006-12-19
For me conky works fone, BUT I can not put it in startup programs, becouse when Gnome is starting, conky pops up and then just dissapier. So I have to start it manually. Where can be problem?

---

### Post by ChronoStriker1 on 2006-12-19
I am having the same problem and cant figure it out ether.  It runs fine when started normally just not when set at startup.

---

### Post by n3Cre0 on 2006-12-19
Works awesome here.

Tweaked my whole conkyrc :)

Then I saw [this]("http://ubuntuforums.org/showthread.php?t=281865&page=1").

And now tweaking it even more :)

---

### Post by OffHand on 2006-12-19
For those that are having difficulties with starting conky when booting read this post: [http://www.ubuntuforums.org/showpost.php?p=1562209&postcount=173](http://www.ubuntuforums.org/showpost.php?p=1562209&postcount=173)

---

### Post by CoolHand on 2006-12-19
> **viuks said:**
> For me conky works fone, BUT I can not put it in startup programs, becouse when Gnome is starting, conky pops up and then just dissapier. So I have to start it manually. Where can be problem?

My first guess is that you do not have it set to fork to the background.  In the .conkyrc file you should see this:

# set to yes if you want Conky to be forked in the background
background yes

If that is not the problem then you may need to follow the post with the link to the other thread but since it works when started from a terminal or the run dialog I would be this is it.
Also if you have some other porblem you can always try calling a script instead of the actual program and in the script call conky like this: conky &
That will also start it in the background.  Good luck.

---

### Post by viuks on 2006-12-20
> **CoolHand said:**
> My first guess is that you do not have it set to fork to the background.  In the .conkyrc file you should see this:

# set to yes if you want Conky to be forked in the background
background yes

If that is not the problem then you may need to follow the post with the link to the other thread but since it works when started from a terminal or the run dialog I would be this is it.
Also if you have some other porblem you can always try calling a script instead of the actual program and in the script call conky like this: conky &
That will also start it in the background.  Good luck.
Background yes did not helped, but startupscript made conky run. Thank you!

---

### Post by raul_ on 2006-12-20
How can i keep the values in for example NAME PID MEM aligned?

rephrasing: how can i keep the text aligned?

---

### Post by raul_ on 2006-12-20
- bump - ?

---

### Post by m.musashi on 2006-12-20
Does anyone know how to upgrade conky? I have version 1.4.2 and version 1.4.5 is out. It doesn't seem to be in the repos though as apt-get install conky just tells me I have the latest version (unless I need to do that differently).

I can follow the instructions at the beginning to install from source if I have to, but do I first need to remove 1.4.2 or will that happen automatically?

Thanks.

---

### Post by m.musashi on 2006-12-20
> **raul_ said:**
> How can i keep the values in for example NAME PID MEM aligned?

rephrasing: how can i keep the text aligned?

If I understand your question, you need to make sure you are using a monospaced font. If there is a way to do it without a monospaced font I don't know how. If everything is lined up in the .conkyrc after text then it should line up on the screen. Using tabs rather than spaces to line everything up might help if you are not using a monospaced font.

If that doesn't help, post your .conkyrc file and I'm sure someone can help.

---

### Post by raul_ on 2006-12-20
i posted my screenshot and file here

[http://ubuntuforums.org/showthread.php?p=1912365#post1912365]("http://ubuntuforums.org/showthread.php?p=1912365#post1912365")

It seems that if i disable xft fonts they auto-align , but i don't want to disable them =\

---

### Post by m.musashi on 2006-12-20
> **raul_ said:**
> i posted my screenshot and file here

[http://ubuntuforums.org/showthread.php?p=1912365#post1912365]("http://ubuntuforums.org/showthread.php?p=1912365#post1912365")

It seems that if i disable xft fonts they auto-align , but i don't want to disable them =\

Since they are not aligned in your .conkyrc I don't think they are going to align on the screen. Try using tabs to align them in the file and see what that does. If that doesn't work then I'm out of ideas.

---

### Post by raul_ on 2006-12-20
They're aligned, They just get messed up in the paste. The problem is that the NAME field "pushes" the other fiels to the right...Is there a way to limit the characters in a process name? For example, is the max characters number is 3 then  "conky" would appear "con"

---

### Post by tturrisi on 2006-12-20
See "tab" here:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
see the examples here:
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by raul_ on 2006-12-20
yeah i went to the irc channel and got some support there :) i could use the tabs but i just changed my font to a uglier but monospaces one. thanks anyway..appreciated

---

### Post by balloons on 2006-12-20
nice.. thanks.. for better copy and pasting code, use this

gedit $HOME/.conkyrc

instead of /home/bob.. that way it will automagically use the path var and get the user's home path

---

### Post by brohan on 2006-12-21
> **raul_ said:**
> yeah i went to the irc channel and got some support there :) i could use the tabs but i just changed my font to a uglier but monospaces one. thanks anyway..appreciated
You could use the $font thing to change the font to monospace temporarily

Or you could do
```
${top name 1}$alignr${top cpu 1}
```
like I've done, but that gets rif of the PID/memory usage too.

---

### Post by v8YKxgHe on 2006-12-22
Hey,

I have setup Conky just now with this guide, but even though I have added "conky &" to the session on startup, it just appears then disappears. Why is this?

---

### Post by raul_ on 2006-12-22
I don't know why it disappears but you don't need the "&"...try removing it and see if it works. Before you do that, press Alt+F2 and then type "conky" and see if it stays...if it does, then just add "conky" (without &) to the startup programs and it should work.

---

### Post by engineering.concepts on 2006-12-22
Please help!](*,) 
I am using Xubuntu and set up Conky - everything works fine, but every once and a while I lose my transparancy in conky and the background turns grey. If I change the .conkyrc file and have a visible window around the conky this will never happen, any ideas on how to fix this?
My .conkyrc file is posted below:

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

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer no
use_xft no

# Update interval in seconds
update_interval 2.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font xftfonts
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda3:  ${fs_free_perc /media/hda3}%   ${fs_bar 6 /media/hda3}

${color orange}NETWORK (${addr ath0}) ${hr 2}$color
Down: $color${downspeed ath0} k/s ${alignr}Up: ${upspeed ath0} k/s
${downspeedgraph ath0 25,140 000000 ff0000} ${alignr}${upspeedgraph ath0 
25,140 000000 00ff00}$color
Total: ${totaldown ath0} ${alignr}Total: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

--------------

thanks in advance for your help :)

---

### Post by raul_ on 2006-12-22
try adding this line after "own_window_transparent yes"
```

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

PS: you have  "own_window_transparent yes" twice

---

### Post by viuks on 2006-12-23
> **raul_ said:**
> I don't know why it disappears but you don't need the "&"...try removing it and see if it works. Before you do that, press Alt+F2 and then type "conky" and see if it stays...if it does, then just add "conky" (without &) to the startup programs and it should work.
I dont know why, byt it was also for me. You have to make startup script. Follow this post [http://www.ubuntuforums.org/showpost.php?p=1562209&postcount=173](http://www.ubuntuforums.org/showpost.php?p=1562209&postcount=173)

---

### Post by engineering.concepts on 2006-12-23
> **raul_ said:**
> try adding this line after "own_window_transparent yes"
```

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

PS: you have  "own_window_transparent yes" twice

I have changed my .conkyrc to add
```

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

and #out the 2nd "own_window_transparent yes"

but it still goes grey after I click my desktop a few times or open a file explorer.:-k

---

### Post by raul_ on 2006-12-23
Since Xubuntu doesn't use Nautilus, try putting the "own_window" value to "no" and see what happens

---

### Post by engineering.concepts on 2006-12-23
> **raul_ said:**
> Since Xubuntu doesn't use Nautilus, try putting the "own_window" value to "no" and see what happens

that makes my entire desktop turn grey and I lose my wallpaper. Conky is still in the corner, but everthing else on the desktop is grey.

---

### Post by raul_ on 2006-12-23
I'm out if ideas then. If u have a irc client installed join #conky at irc.freenode.net 

I'm sure they can handle that :) they rule in matter of conky

---

### Post by aristotlewilde on 2006-12-23
My conky keeps disappearing as well.  My .conkyrc is below.  Can anyone see a reason for it??

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${freq_dyn}Mhz

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
ppp0 $alignr ${addr ppp0}

Inbound $alignr ${downspeed ppp0} kb/s
${downspeedgraph ppp0}
Outbound $alignr ${upspeed ppp0} kb/s
${upspeedgraph ppp0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

---

### Post by OffHand on 2006-12-23
> **aristotlewilde said:**
> My conky keeps disappearing as well.  My .conkyrc is below.  Can anyone see a reason for it??

own_window_type normal


Try to replace normal with desktop or override.

---

### Post by engineering.concepts on 2006-12-23
> **raul_ said:**
> I'm out if ideas then. If u have a irc client installed join #conky at irc.freenode.net 

I'm sure they can handle that :) they rule in matter of conky

I'll give them a try at the irc channel.
Thanks for trying:)

---

### Post by hq4ever on 2006-12-24
> **marx2k said:**
> Im going to have to re-post my problem here...
New Conky is out 1.4.5... trying to compile it (happens with 1.4.4 as well), I run ./configure and get:

checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage

and it craps out after that.

I *do* have all dependencies installed from the beginning of this thread, so no dice there.

Also, the man page states 
       For  users  compiling from source, make sure you have the X development
       libraries installed.  This should be  a  package  along  the  lines  of
       "libx11-dev or xorg-x11-dev".

Which is done...

Anyone have any hints as to how this can be accomplished?

Any news on the above?
I'm having the exact same problem here with edgy...

I'd be glad if someone could shade some light on this issue, do we need to build a new version of X for this to work?

---

### Post by aristotlewilde on 2006-12-24
Still have the amazing disappearing CONKY.  

.conkyrc is below, followed by terminal output.

Anyone have ideas?  I am determined to use conky for some odd reason...

--------------------------------------

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${freq_dyn}Mhz

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
ppp0 $alignr ${addr ppp0}

Inbound $alignr ${downspeed ppp0} kb/s
${downspeedgraph ppp0}
Outbound $alignr ${upspeed ppp0} kb/s
${upspeedgraph ppp0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}



------------------------

scott@blackbox:~$ conky
Conky: forked to background, pid is 5472
scott@blackbox:~$ 
Conky: desktop window (100005b) is subwindow of root window (45)
Conky: window type - desktop
Conky: hint - undecorated
Conky: hint - below
Conky: hint - sticky
Conky: hint - skip_taskbar
Conky: hint - skip_pager
Conky: drawing to created window (2e00002)
Conky: drawing to double buffer

---

### Post by Atreus12 on 2006-12-24
Thanks for the guide, I got conky set up and looking good, but I was wondering how to get CPU temperature to work. I played around with it for a while, and it only says 0 degrees.I have a dell 8400 desktop, and when I type (at the terminal):
acpi -V
I get the following output:
No support for device type: thermal

Whats going on?

---

### Post by NeoLithium on 2006-12-25
> **aristotlewilde said:**
> Still have the amazing disappearing CONKY.  

.conkyrc is below, followed by terminal output.

Anyone have ideas?  I am determined to use conky for some odd reason...

--------------------------------------

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${freq_dyn}Mhz

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
ppp0 $alignr ${addr ppp0}

Inbound $alignr ${downspeed ppp0} kb/s
${downspeedgraph ppp0}
Outbound $alignr ${upspeed ppp0} kb/s
${upspeedgraph ppp0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}



------------------------

scott@blackbox:~$ conky
Conky: forked to background, pid is 5472
scott@blackbox:~$ 
Conky: desktop window (100005b) is subwindow of root window (45)
Conky: window type - desktop
Conky: hint - undecorated
Conky: hint - below
Conky: hint - sticky
Conky: hint - skip_taskbar
Conky: hint - skip_pager
Conky: drawing to created window (2e00002)
Conky: drawing to double buffer

While I don't use GNOME, have you tried setting the own_window_type to override?

---

### Post by aristotlewilde on 2006-12-25
> **NeoLithium said:**
> While I don't use GNOME, have you tried setting the own_window_type to override?

Override did the same thing.  I am at a loss...

+++++edit++++

Thought I edited this yesterday.  Override actually got it to work, however, conky "conks" out when my wallpaper comes in at startup.  If I start conky once my computer is running, it stays indefinitely.

---

### Post by blonder on 2006-12-26
How can i change the output Color from white to red ?

```
# Conky configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# The additions to this config require curl and xsltproc be installed

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# set to yes if you want Conky to be forked in the background
#background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
#own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Max window size
maximum_width 300

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player none

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color #246eb5}SYSTEM ${hr 2}$color
${time %e %B %G}                   ${alignr}${time %H:%M}
${color #246eb5}Core:$color   ${execi 1000 cat /proc/cpuinfo | grep 'model name' | cut -c 21-31} 2800+ 1.6GHz
${color #246eb5}Host:$color   $nodename 
${color #246eb5}Kernel:$color $kernel 
${color #246eb5}Uptime:$color $uptime
${color #246eb5}POWER ${hr 2}$color
${color #246eb5}Adapter Stat:$color  ${acpiacadapter}	${color #246eb5}${alignr}Battery Info:$color ${battery}
${color #246eb5}CPU ${hr 2}$color
${color #246eb5}Speed:$color ${freq}MHz  ${color #246eb5}Load:$color ${loadavg} ${color #246eb5}${alignr}CPU Temp:$color ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
${color #246eb5}NAME             PID       CPU%      MEM%$color
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color #246eb5}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
       $mem of $memmax
Swap:  $swapperc%   ${swapbar 6}$color
       $swap of $swapmax
HDA:   ${fs_free_perc /}%   ${fs_bar 6 /}$color 
${color #246eb5}Total:$color ${fs_used /}   ${color #246eb5}${alignc}Free:$color ${fs_free /}   ${color #246eb5}${alignr}Used:$color ${fs_used /}
${color #246eb5}NETWORK (${addr ppp0}) ${hr 2}$color
${downspeedgraph ppp0 25,140 000000 ff0000} ${alignr}${upspeedgraph ppp0 
25,140 000000 00ff00}$color
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${color #246eb5}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${color #246eb5}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color #246eb5}SYSTEM LOGS ${hr 2}$color
${color #246eb5}Messages:$color
${execi 10 /usr/bin/tail -n 4 /var/log/messages | cut -c 27-}
${color #246eb5}Security:$color
${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 27-}
```

---

### Post by NeoLithium on 2006-12-26
> **blonder said:**
> How can i change the output Color from white to red ?


Just replace all instances of white with red, as well as any #246eb5 to red as well.

---

### Post by blonder on 2006-12-26
#246eb5 is blue

Is this the place where I can change the output colour ?

> 
# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white


thats my Problem :

---

### Post by eXisor on 2006-12-26
[quote="hq4ever"]DamageQueryExtension in -lXdamage[/quote]

The error message means you do not have libxdamage installed.

See my post in the thread below for the additional libraries you will need.

[http://ubuntuforums.org/showpost.php?p=1923799&postcount=6](http://ubuntuforums.org/showpost.php?p=1923799&postcount=6)

---

### Post by NeoLithium on 2006-12-27
> **blonder said:**
> #246eb5 is blue

Is this the place where I can change the output colour ?




thats my Problem :

Yep, that's where you change the default color output when none of the lines in the TEXT Field have ${color WHATEVER}

---

### Post by harrisony on 2006-12-27
> **marx2k said:**
> Im going to have to re-post my problem here...
New Conky is out 1.4.5... trying to compile it (happens with 1.4.4 as well), I run ./configure and get:

checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage

and it craps out after that.

I *do* have all dependencies installed from the beginning of this thread, so no dice there.

Also, the man page states 
       For  users  compiling from source, make sure you have the X development
       libraries installed.  This should be  a  package  along  the  lines  of
       "libx11-dev or xorg-x11-dev".

Which is done...

Anyone have any hints as to how this can be accomplished?
if you still need it
```
sudo aptitude install xorg-dev
```
worked for me
EDIT:hahahah i didnt read opps

---

### Post by dragnazz5.0 on 2006-12-28
well i just installed this and its working but any time i happen to drag a window over top of it or click on it the thing kind of freezes and goes white for a second.  am i missing something or is it just the way it is.  also, the only way i can run it is if i go to "run program" and type it in.  im using xubuntu right now because i cant figure out how in the world to get it to work on regular ubuntu

---

### Post by Gumper on 2006-12-30
I apologize if this has been already mentioned but I couldn't find anything when searching. I installed Conky and I'm happy with the results. I have xmms showing up and my system temps, fan speeds, etc. But the only thing that doesn't seem to work is when I add  Conky to the "start up programs" in session it will start when ubuntu starts but it will then disappear from the screen. 

Any idea on how to correct this?

Thanks,

Gumper

---

### Post by raul_ on 2006-12-30
```

sudo gedit <filenameyouwant>.sh

```

then place these lines in there
```

sleep 10 && conky;

```

replace 10 with whatever time you want, save it, and add that script to the startup programs..that should do it

---

### Post by Gumper on 2006-12-30
Thanks. I'll give it a try.

---

### Post by raul_ on 2006-12-30
Let me know if it worked

---

### Post by Gumper on 2006-12-30
i tried it but it didn't seem to do anything. In your ex. does "10" represent 10 sec. or minutes?

---

### Post by Gumper on 2006-12-30
I'm trying it again. I made a typo.

---

### Post by raul_ on 2006-12-30
seconds. But what do you mean with nothing? Conky doesn't start or it starts and it stays behind the background?

---

### Post by Gumper on 2006-12-30
it doesnt start. when i add the script to my sessions i hit add and then pointed it to my script location. Is this correct?

/home/gumper/conkdel.sh

---

### Post by raul_ on 2006-12-30
I'm assuming you logged out and in again. Can you do post the results of this command:

```

ps aux | grep conky

```

---

### Post by Gumper on 2006-12-30
Yes i did reboot. 

5037  0.0  0.0   3900   800 pts/0    R+   10:52   0:00 grep conky

---

### Post by raul_ on 2006-12-30
You don't need to reboot. In the very max you just have to restart X with ctrl+alt+backspace . Reboot is for windows (kidding) So good news! conky isn't starting so it's a problem with the script or with the way you start it. here is my script

```

raul@raul:~$ cat .conky_start.sh 
#!/bin/bash
sleep 20 && conky;

```

it's pretty much the same, so try adding it again. Step by step, System->Preferences->Sessions->Startup Programs->Add and browse for the script

DAMN!! i forgot...my bad. Make the script executable.

```

chmod +x ~/conkdel.sh

```

~ is the user's home folder btw

---

### Post by Gumper on 2006-12-30
i tried to make it exe but i get "changing permissions of `/home/gumper/conkydel.sh': Operation not permitted"

---

### Post by raul_ on 2006-12-30
sudo chmod blablabla

---

### Post by Gumper on 2006-12-30
got it! thanks for all the help!

---

### Post by helpdeskdan on 2007-01-03
My desktop picture covers conky!  It comes up, it changes color, desktop image shows up, conky disappears.  But, it's still running:

dan@dan-desktop:~$ ps ax | grep conky
27190 ?        Ss     0:00 conky
27455 pts/0    S+     0:00 grep conky

If I kill it and relaunch, I can see it fine.  Certainly somebody else is having this problem, but I can't find the answer. 

Thanks, 
-Dan

---

### Post by raul_ on 2007-01-03
Try using the script solution posted in this thread (some posts behind)

---

### Post by v8YKxgHe on 2007-01-04
yep! Im having the same problem. It's annoying,

edit: didn't see raul_'s comment, I'll try that now. ( sleep && conky )

---

### Post by raul_ on 2007-01-04
sleep <timeinseconds> && conky;

---

### Post by helpdeskdan on 2007-01-04
Great, thanks!

---

### Post by diskotek on 2007-01-07
are there any codes that conky can display what i'm listening on "exaile" media player?

---

### Post by oyvindaa on 2007-01-08
Thanks for a great howto.

It works great my end, apart from one little detail. 

When I reboot it doesn't re-appear on my desktop. The only way to get it back is to log out and log back in. 

Anyone ever experienced this problem?

---

### Post by m.musashi on 2007-01-08
> **oyvindaa said:**
> Thanks for a great howto.

It works great my end, apart from one little detail. 

When I reboot it doesn't re-appear on my desktop. The only way to get it back is to log out and log back in. 

Anyone ever experienced this problem?

How do you have it set to start? If It's added to your session I think it will cause a problem as it loads before the desktop. Perhaps logging in and out is a work around because by the time you log in again the desktop is already loaded. Just a guess though. Somewhere in here is a short bash script that will start conky 60 seconds after your session starts and thus avoid that problem. It's probably a little less elegant but I just start it manually. I have a custom launcher on the top panel for conky so I just click it if I want conky to load. I use beryl a lot so I want to be sure I start beryl first as well.

If you are using the delayed start then I'm afraid I don't know.

---

### Post by raul_ on 2007-01-09
> **m.musashi said:**
> How do you have it set to start? If It's added to your session I think it will cause a problem as it loads before the desktop. Perhaps logging in and out is a work around because by the time you log in again the desktop is already loaded. Just a guess though. Somewhere in here is a short bash script that will start conky 60 seconds after your session starts and thus avoid that problem. It's probably a little less elegant but I just start it manually. I have a custom launcher on the top panel for conky so I just click it if I want conky to load. I use beryl a lot so I want to be sure I start beryl first as well.

If you are using the delayed start then I'm afraid I don't know.

I use beryl and the script with a 2s sleep works fine with me ;)

---

### Post by m.musashi on 2007-01-09
> **raul_ said:**
> I use beryl and the script with a 2s sleep works fine with me ;)

I didn't try such a short sleep but I decided I didn't really want it or beryl to auto load - especially beryl. Sometime I don't really need or want it so I'd rather decided at login what to use. Afterall, with a custom launcher it's only a single click to load.

---

### Post by oyvindaa on 2007-01-09
> **m.musashi said:**
> How do you have it set to start? If It's added to your session I think it will cause a problem as it loads before the desktop. Perhaps logging in and out is a work around because by the time you log in again the desktop is already loaded. Just a guess though. Somewhere in here is a short bash script that will start conky 60 seconds after your session starts and thus avoid that problem. It's probably a little less elegant but I just start it manually. I have a custom launcher on the top panel for conky so I just click it if I want conky to load. I use beryl a lot so I want to be sure I start beryl first as well.

If you are using the delayed start then I'm afraid I don't know.

Yeah, it's added to my sessions. Thanks, I'll try that script :)

EDIT: That script worked a treat. Everything's fine now.

```

#!/bin/bash
sleep 10 && conky;

```

It's not just a conky-related problem though, because this was happening when I was using adesklets as well. Oh well, sorted now :)

---

### Post by truthfatal on 2007-01-09
Great HOWTO :)

I had a few problems at first. For some reason my ~/.config was read-only and owned by root. that prevented me from adding startup programs from the sessions menu. I also had the problem where the background was hiding the conky display. but that little "sleep 10" script fixed that right up :)

---

### Post by oyvindaa on 2007-01-10
I found out that the hd part was wrong in my setup.

However, when I change it to /dev/hda1 , which is my hd, it shows up as 99% in conky, and that's wrong. First it was /media/hda1, but I've got nothing there.

The hd is a 60gb one with 38gb free space at the moment. That makes the 99% part very wrong. 

Any suggestions?

---

### Post by NeoLithium on 2007-01-10
> **oyvindaa said:**
> I found out that the hd part was wrong in my setup.

However, when I change it to /dev/hda1 , which is my hd, it shows up as 99% in conky, and that's wrong. First it was /media/hda1, but I've got nothing there.

The hd is a 60gb one with 38gb free space at the moment. That makes the 99% part very wrong. 

Any suggestions?

Try using the mount points instead, for my conky, I have to list them as / and /home in the conkyrc file.

---

### Post by marx2k on 2007-01-11
Attempts at compiling conky 1.4.5 ... This is the same error I get in 1.4.2 through 1.4.5

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.17.2... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for GLIB... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: ./config.rpath: No such file or directory
done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for X11... yes
checking for XEXT... yes
checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage
marx2k@Commodore-64:~/source/conky-1.4.5$

```

Anyone? Anyone?

EDIT: SOLVED:  Had to install via Synaptic- X11 damaged region extension library (development headers)

---

### Post by marx2k on 2007-01-11
Looking good now!
```

marx2k@Commodore-64:~/source/conky-1.4.5$ conky -v
Conky 1.4.5 compiled Thu Jan 11 02:26:28 CST 2007 for Linux 2.6.17-10-generic (i686)

Compiled in features:

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * hddtemp
  * portmon

```

The only thing is that it installs to /usr/local/bin but that can be changed with ./configure options.

---

### Post by function1 on 2007-01-12
Works great except for one minor annoyance:
If I click on conky it seems to create a selection box starting from the left side of the screen and going under conky. It also seems counterintuitive that when dragging a desktop icon over conky, the icon ends up below conky. Perhaps there is no way around this given that conky is its "own_window" or whatever.
I used the exact same .conkyrc provided by the HOWTO.

---

### Post by seelk on 2007-01-14
I get a black background under Kubuntu using conky 1.4.5.  Does anyone have any ideas what could be causing this.

[conkyrc]("http://paste.ubuntu-nl.org/1599/")

---

### Post by oyvindaa on 2007-01-14
> **NeoLithium said:**
> Try using the mount points instead, for my conky, I have to list them as / and /home in the conkyrc file.

Alright, that worked a treat. Thanks.

I've got another problem now though (typical isn't it).

I changed my .conkyrc to this:

```

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 12
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth1 $alignr ${addr eth1}

Inbound $alignr ${downspeed eth1} kb/s
${downspeedgraph eth1}
Outbound $alignr ${upspeed eth1} kb/s
${upspeedgraph eth1}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

${execi 60 wmctrl -a conky}

```

Whenever I log off or reboot/shutdown I get the following message ("Warning"):

```

These windows do not support
"save current setup" and will have
to be restarted manually next time
you log in.

TITLE               |       CLASS
aassveen -conky        conky

```

So, what's the problem here?

EDIT: Problem solved. I had another look at the .conkyrc and noticed it was running inside a window. I removed that and the warning disappeared as well.

---

### Post by lime4x4 on 2007-01-14
I'm running he latest version of conky on ubuntu-edgy. The only problem i'm having is i also have the weather in my conky file which works great for the most part except when there is a special weather announcement.Then my conky windows becomes real big how can i add word wrap or something so that it stays the same size all the time? I don't mind if it increases it's size verticaly just not horizontaly. I also included a copy of my file the weather part is at the bottom. and i also added a copy of my weather script as well

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
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color green

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
CPU: ${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
${color green}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color purple}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${cpugraph 000000 ffffff}

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hdb1:  ${fs_free_perc /dev/hdb1}%   ${fs_bar 6 /dev/hdb1}$color
${color #0077ff}/home      $color${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
$color$stippled_hr
sda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
sdb1:  ${fs_free_perc /media/sdb1}%   ${fs_bar 6 /media/sdb1}$color
$color$stippled_hr
Internet/Networking Status (${addr eth0}):
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
$color$stippled_hr
SYSTEM LOG TAIL
${execi 30 tail -n3 /var/log/messages | fold -w50}
$color$stippled_hr
${execi 15 wmctrl -R " - conky"}
$color$stippled_hr
${execi 1800 /home/john/scripts/weather.sh 18071}


and here is my weather script

#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# The orignal script and xslt can be downloaded from [http://pondol.com/weather.tar.gz](http://pondol.com/weather.tar.gz)

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/harryc/downloads/weather/weather.sh USNY1175}

# your Location ID: use [http://xoap.weather.com/search/search?where=](http://xoap.weather.com/search/search?where=)[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=$1

# s=standard units, m=metric units
UNITS=s

# where this script and the XSLT lives
RUNDIR=/home/john/scripts 

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at [http://curl.haxx.se/](http://curl.haxx.se/)
CURLCMD=/usr/bin/curl

# get it at [http://xmlsoft.org/XSLT/](http://xmlsoft.org/XSLT/)
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS&dayf=2"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt 

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"

---

### Post by m.musashi on 2007-01-14
> **seelk said:**
> I get a black background under Kubuntu using conky 1.4.5.  Does anyone have any ideas what could be causing this.

[conkyrc]("http://paste.ubuntu-nl.org/1599/")

I been fighting this battle for a while. I'm still using 1.4.2 but it seems that conky uses the root desktop for fake transparency. However, in kde the root desktop is not the one you see. Someone posted a link to a solution some pages back. It involved setting a root background that is the same as the desktop. Another work around involved opening the desktop configuration and deselecting the draw icons on desktop or something like that (I'm not using kde at the moment and can't remember exactly) and then applying and the reselecting it and applying. It only works for the one session so it's not a fix. Afaik, there is no fix yet unless 1.4.5 somehow addressed it.

---

### Post by bloodfilledwater on 2007-01-25
When I start conky before beryl, it doesn't use my .conkyrc that's in my home directory. Where it the other config file or how can I get it to use it?

---

### Post by Andifferous on 2007-01-28
lime4x4

the word wrap problem that you have with your weather, I've been having with xmms 
say I want to listen to: the glorious liberation of vinnland by the combined forces of the united territories of europa by type o negative. It bumps half of my conky off the leftside of my screen until the song is over. I'm new to conky, but from looking at the code, and the man pages for something like word wrap... I haven't found it.

---

### Post by OffHand on 2007-01-28
> **Andifferous said:**
> lime4x4

the word wrap problem that you have with your weather, I've been having with xmms 
say I want to listen to: the glorious liberation of vinnland by the combined forces of the united territories of europa by type o negative. It bumps half of my conky off the leftside of my screen until the song is over. I'm new to conky, but from looking at the code, and the man pages for something like word wrap... I haven't found it.

# Minimum size of text area
minimum_size 260 5
maximum_width 260

---

### Post by phssthpok on 2007-01-29
I was wondering if anyone has had this issue with $tcp_portmon and showing outbound connections. When I navigate away from a webpage in firefox, the connections made for that website seem to be "kept open" and occupy the first positions in the connection list; thus, newer connections are never shown. I've tried flushing cookies but the only thing that works is to actually restart firefox. Then the connections are refreshed but the first website I visit will fill up all the slots again.

---

### Post by Athanasius on 2007-02-01
Two questions.

First, when I click on the "show desktop" icon conky goes away.  Is there a way to always make it stay on top?

Second, how do I get the weather in conky?  I have seen some examples in people's scripts but they don't work for me.  Is there something I am supposed to install first?

---

### Post by raul_ on 2007-02-02
You have to install a program called "pymetar" that is available in the repositories. Then you can tweak the programs file to edit the output

---

### Post by BLTicklemonster on 2007-02-02
Nice!

---

### Post by Athanasius on 2007-02-02
Raul,

Could you perhaps show a script that uses pymetar?

---

### Post by raul_ on 2007-02-02
```
${execi 60 /usr/bin/pymetar LPPT}
```

replace LPPT with your location's code. i think you can get it from weather.com or something like that

---

### Post by tturrisi on 2007-02-02
> **raul_ said:**
> ```
${execi 60 /usr/bin/pymetar LPPT}
```

replace LPPT with your location's code. i think you can get it from weather.com or something like that
(KIAD = Dulles Intl. Airport)
${execi 60 /usr/bin/pymetar KIAD}

Full list of stations:
[http://www.nws.noaa.gov/tg/siteloc.shtml](http://www.nws.noaa.gov/tg/siteloc.shtml)

---

### Post by Athanasius on 2007-02-02
Ah!  Thank you!

---

### Post by foormea on 2007-03-03
hi

i've got two problems:

1) when using a if_running or if_exist or stuff, if the whatever-i'm-checking exists/runs, then it works fine. however, if it doesn't exist, conky will print a blank line. pretty ugly. any way to prevent it?
> ${if_mounted /media/usbdisk-1}usb:  ${color lightblue}${fs_used_perc /media/usbdisk-1} ${color}% ${color lightblue}${fs_used /media/usbdisk-1}${color}/${fs_size /media/usbdisk-1} ${fs_bar /media/usbdisk-1}${endif}

2) here's the part of my .conkyrc relevant with fonts:
> use_xft yes 
xftfont Bitstream Vera Sans Mono:size=9

whatever size i put, it'll be the same size on screen
i don't understand how fonts, either regular or xft, work
for example, i know they're in /usr/share/fonts
but if i go in /usr/share/fonts/truetype/ttf-dejavu. there're a few files in that directory, but let's consider only one file, randomly, DejaVuSans-BoldOblique.ttf. should i put spaces, like Deja Vu Sans ....? how do i know the actual name of the font? how do i know if it's an xft font or regular font?

i've also heard i could put fonts in ~/.fonts
would i have to add that path to my xorg.conf ?
i've also noticed that i have to refresh font path after installing new fonts or stuff? how does all that work? i'm somewhat confused! :confused: :confused:

edit: currently reading some howto about fonts :)

---

### Post by BOBSONATOR on 2007-03-05
> **diskotek said:**
> are there any codes that conky can display what i'm listening on "exaile" media player?

Im looking for this too.

Thanks for the great tut!

---

### Post by Frenzy-br on 2007-03-18
took me a while to get it running below everythign because every time i ran it it would go over every other screen, now i can only see it when i move the beryl cube ... other than that its invisible...

---

### Post by DoorGunner on 2007-03-22
I am curious has anyone been able to get amarok to  work with conky?

---

### Post by aeiah on 2007-03-28
> **DoorGunner said:**
> I am curious has anyone been able to get amarok to  work with conky?

yea there's a script on the conky homepage for amarok, in the screenshot section

---

### Post by Muppeteer on 2007-04-25
Here's mine...Only started it yesterday, haven't really changed much, just tweaked the default one for now :) 

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

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font padmaa
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour green
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 110

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color 0e5075}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color 0e5075}MEMORY${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

${color 0e5075}DISK ${hr 2}$color
Root:     ${fs_used_perc /}%   ${fs_bar 6 /}$color 
Windows:  ${fs_used_perc /media/HDD1}%   ${fs_bar 6 /media/Windows}$color
linux:    ${fs_used_perc /media/HDD2}%   ${fs_bar 6 /media/linux}
Games:    ${fs_used_perc /media/HDD3}%   ${fs_bar 6 /media/Games}
Downloads:${fs_used_perc /media/HDD4}%   ${fs_bar 6 /media/Downloads}
Maritas:  ${fs_used_perc /media/HDD5}%   ${fs_bar 6 /media/Maritas}

${color 0e5075}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color 0e5075}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color 0e5075}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

[[IMG]http://img176.imageshack.us/img176/7964/screenshotjb8.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshotjb8.png)

---

### Post by satellite360 on 2007-04-30
Hi all

I'm running Conky 1.4.5 and all is working well except I can't figure out how to display MB etc in abbreviated form.  Currently I am Conky is displaying something like 343MiB/1.98GiB when all I really want to display is 343M/1.98G.

This isn't a setting which can be changed in the conkyrc file as far as I can see.

Grateful if anyone can point me in the right direction.

Thanks

---

### Post by chm0d on 2007-04-30
I must be a complete idiot because I have not yet been able to get amarok to work with conky.  I have the script from sourceforge.  I have put the script in /home/usr/.conky but still I cannot get anything out of it.  Only thing that displays is Now Playing and it refreshes every 10 secs.  I will post my conkyrc.  Any help would be greatly appreciated.  

chm0d

---

### Post by m.musashi on 2007-04-30
I think this might be an issue with how it's compiled - there are a lot of options you can enable. I found this:
> Compiling

For users compiling from source, make sure you have the X development libraries installed. This should be a package along the lines of "libx11-dev or xorg-x11-dev".

Gentoo users -- Conky is in Gentoo's Portage... simply use "emerge app-admin/conky" for installation. There is also usually an up-to-date ebuild within Conky's package or in Svn.

Debian,etc. users -- Conky will be in Debian's repositories soon (by mid-September, hopefully), and then Ubuntu shortly thereafter. Until then, "dpkg -i" the .deb package to install.

Example to compile and run Conky with all optional components (note that some configure options may differ for your system):

sh autogen.sh # Only required if building from Svn
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-own-window --enable-proc-uptime --enable-audacious --enable-bmpx --enable-hddtemp --enable-mpd --enable-xmms2 --enable-imlib2 --enable-portmon --enable-debug --enable-double-buffer --enable-xdamage --enable-x11

It was posted in another conky thread by a user who found it in the gentoo forums.

---

### Post by m.musashi on 2007-04-30
Oops. That was double posted for some reason. Sorry

---

### Post by r0nin on 2007-05-14
In "nvidia-settings" I can see how hot my GPU gets. Is there anyway I could put that into my Conky setup?

---

### Post by justleen on 2007-05-21
> **seldon77 said:**
> 

5. Add dbe module to /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```
find the section titled Section "Module", and add
```

        Load    "dbe"

```



I found there was already a line  ** Load    "vbe" ** in my xorg. I had to change this to "dbe" in order for conky to work correctly with double buffering./

---

### Post by Thore on 2007-05-30
> **r0nin said:**
> In "nvidia-settings" I can see how hot my GPU gets. Is there anyway I could put that into my Conky setup?

> 
${color black}Nvidia: ${color white}${exec /usr/bin/nvidia-settings -q gpus | cut -c 29-43 | tail -n2}
${color black}GPU Core Temp: ${color white}${exec /usr/bin/nvidia-settings -q gpucoretemp |grep Attribute |cut -c 44-45}'C

[IMG]http://www.thore.org/nvidiatemp.png[/IMG]


My NVIDIA Driver version is 9631
Hope this helps you on your way :)

Thore

---

### Post by r0nin on 2007-05-30
Cheers mate. Works nicely!

---

### Post by RichJacot on 2007-05-31
> **chm0d said:**
> I must be a complete idiot because I have not yet been able to get amarok to work with conky.  I have the script from sourceforge.  I have put the script in /home/usr/.conky but still I cannot get anything out of it.  Only thing that displays is Now Playing and it refreshes every 10 secs.  I will post my conkyrc.  Any help would be greatly appreciated.  

chm0d



Is your amarok collection in mysql?

I just copied the last lines out of your conkyrc (changed paths), converted my amarok from sqlite to mysql, downloaded the script form conky's screenshot page and it appears to be working fine.

---

### Post by qchi on 2007-06-06
Hi all!

I just wanted to share my conky config files!

I've written a script to show weather information from yahoo in conky, but it is still using too many resources, so i will try to optimize it in the future.

ENJOY!

---

### Post by nightfire117 on 2007-06-20
Sorry if this post is a bit off-topic. (Great topic by the way, it's been quite helpful.) Erm, is there a way to center everything in my conky config into the top center of my screen?

Erm, thanks - hopefully this isn't the wrong place to ask.

~Nightfire

---

### Post by OffHand on 2007-06-20
> **nightfire117 said:**
> Sorry if this post is a bit off-topic. (Great topic by the way, it's been quite helpful.) Erm, is there a way to center everything in my conky config into the top center of my screen?

Erm, thanks - hopefully this isn't the wrong place to ask.

~Nightfire

Play with these settings (or add them to) in your .conkyrc file
gap_x and gap_y are measured in pixels.

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 85
alignment top_right
#alignment bottom_left
#alignment bottom_right

---

### Post by nightfire117 on 2007-06-20
> **OffHand said:**
> Play with these settings (or add them to) in your .conkyrc file
gap_x and gap_y are measured in pixels.

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 85
alignment top_right
#alignment bottom_left
#alignment bottom_right

Thanks, tweaking those settings work well.

~Nightfire

**[EDIT]:** Erm, what about laptop battery? Thanks.... XD

~Nightfire

---

### Post by OffHand on 2007-06-20
> **nightfire117 said:**
> Thanks, tweaking those settings work well.

~Nightfire

**[EDIT]:** Erm, what about laptop battery? Thanks.... XD

~Nightfire

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

;)

---

### Post by nightfire117 on 2007-06-20
> **OffHand said:**
> [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

;)

Heh, thanks. Not exactly sure how to implement these variables though, since I started using Conky about... erm, a couple days ago. I guess I should put the line ```
$battery
``` somewhere in my Conky under the "TEXT" section, or do I have to define something in the file before "TEXT?" I'll give it a shot for now anyways. Thanks. XD

~Nightfire

---

### Post by raul_ on 2007-06-20
battery BAT0/BAT1/whatever fits you

and 

battery_time BAT0/BAT1/.......

after "TEXT"

---

### Post by nightfire117 on 2007-06-20
Yeah, I checked and I have BAT1 and BAT2 (actually I only have one battery in my laptop, I dunno where the BAT2 came from - Windows, when I had it on this laptop, reported 2 batteries as well, the second one not being present - hmm). So I put ${execi 200 SCRIPT HERE} to report the battery, and it works. (Seems to have quite a large empty space though but I'm fine with that.) Actually, I think I'll try your method too.

Thanks.

~Nightfire

**[EDIT]:** And it works, even better.

~Nightfire

---

### Post by Megatog615 on 2007-06-21
Anyone know how to get Conky to use the CPU temperature output from the "sensors" command? My Athlon64's sensors only work through the module "k8temp" and the sensors command is the only way to get correct temperatures.

Here's an example output of "sensors":
```
$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +31°C
```

How can I get that temperature to display in Conky? Neither i2c or acpitemp work.

---

### Post by Megatog615 on 2007-06-21
I got it to work. Here's the command to replace ${acpitemp} with:
```
${execi 4 sensors | grep ° | cut -c 15-16 ;}C
```

For those who have the same situation as I.

---

### Post by nightfire117 on 2007-06-21
> **Megatog615 said:**
> I got it to work. Here's the command to replace ${acpitemp} with:
```
${execi 4 sensors | grep ° | cut -c 15-16 ;}C
```

For those who have the same situation as I.

Nice job. I got the {acpitemp} but if I run into problems with another comp I'll keep this in my mind.

Anyways, I've got another question.

I configured my Conky just the way I like it, and it even has weather. Which is the problem. When I put this computer to sleep/hibernate/standby (it's a notebook - Function+F4 puts it into standby), after I wake it up the portion displaying the weather is missing. I have to reload Conky manually in order to get it to reload that weather part. Here's the code for my Conky:

```
# stuff after 'TEXT' will be formatted on screen
TEXT
@kr-note - ${color}CPU: $cpu% - ${color}${freq_dyn}MHz${color} ${color}${acpitemp}C - ${color}$mem/$memmax ${color}- ${battery BAT1} - ${color}${execi 100 ~/.conky/weather.sh JAXX0055}               
```

So I guess the refresh is just too slow? I don't want Conky to keep refreshing and updating - if it did so frequently, would it pose a threat to overall system performance? What exactly does "100" mean? I turned it down from "500" in hopes that it would refresh more quickly, but I'm not even sure what kind of time this is measured in. Milliseconds is what I thought but I figured if I put it to sleep, 100 milliseconds after I woke it up shouldn't it have refreshed that part of the Conky config? Should I just put something somewhere to refresh either that part or the whole config, and would such a refresh be visible, i.e. disappear and reappear? (Have 512 MB RAM, P4-M 2.0 GHz.) Anyways, thanks in advance.

~Nightfire

---

### Post by raul_ on 2007-06-21
I think it's seconds

---

### Post by nightfire117 on 2007-06-22
> **raul_ said:**
> I think it's seconds

Hmm, alright. Thanks for the info. :-D

~Nightfire

---

### Post by RichJacot on 2007-06-27
Does anyone know if there is a way to have the $cpubar ignore or not show nice processes?

Basically I like the cpu bar but when I have a process that I nice because it takes 100% of the CPU for a day or two, I don't notice or can't quickly see if something else is hogging the CPU that I haven't niced.

---

### Post by JMO707 on 2007-06-27
I have a problem: conky seems to "shrink" and "expand" his width all the time.

My conkyrc is: 

>  # UBUNTU-CONKY
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

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
xftfont nu:size=10
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors, #7e7e9790 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y 0

# stuff after 'TEXT' will be formatted on screen

TEXT
$color

${color #7e7e97}SYSTEM ${hr 2}$color
Computer Name: $nodename 
Kernel: $kernel 
Uptime: ${uptime}

${color #7e7e97}CPU ${hr 2}$color
AthlonXP Barton ${freq}MHz   
Load: ${loadavg}   Temp: ${acpitemp}
Processes: ${processes}   Running: ${running_processes}

CPU: ${cpu 0}%   ${cpubar 6}
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color #7e7e97}MEMORY ${hr 2}$color
RAM:   $memperc%  ${membar 6}$color
       ${mem} / ${memmax}

${color #7e7e97}DISK ${hr 2}$color
Root:  ${fs_used_perc /}%   ${fs_bar 6 /}$color 
       ${fs_used /} / ${fs_size /}

Musik:  ${fs_used_perc /musik}%   ${fs_bar 6 /musik}$color
       ${fs_used /musik} / ${fs_size /musik}

Datos:  ${fs_used_perc /datos}%   ${fs_bar 6 /datos}$color
       ${fs_used /datos} / ${fs_size /datos}

${color #7e7e97}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color #7e7e97}MPD: ${alignc}$mpd_artist - $mpd_title
${color #7e7e97}$mpd_bar
${color #7e7e97}${alignc}$mpd_status

---

### Post by raul_ on 2007-06-27
You have to use monospace fonts

---

### Post by Rudy246 on 2007-06-28
Hello. I seem to be having a bit of trouble around step 2.

My problems begin at:
```
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe

```

After returning many successful lines, it returns this:

```

checking for GLIB... configure: error: Package requirements (glib-2.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've been looking around for solutions, but thus far haven't found anything. Any help is greatly appreciated.

Also, I'm fairly new to Ubuntu, I've only been using it for about two weeks, so forgive the possibly newbish question.
-Rudy

---

### Post by linuks on 2007-06-28
checking for GLIB... configure: error: Package requirements (glib-2.0) were not met:

No package 'glib-2.0' found

Install 'glib-2.0' and run the .configure again. Search for the package first by doing sudo apt-cache search glib and then install it with sudo apt-get install `packagename` (remove `).

GLuck

---

### Post by Rudy246 on 2007-06-28
Thanks for the advice, but I'm not sure which package to download.

It gave me a lengthy list of packages after I entered the search command.

I picked "libglib2.0-0" since it seemed to be the most accurate.

When I installed it, it said that it was already installed.

```
rudy@rudy-laptop:~$ sudo apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree... Done
libglib2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any idea what the name of the package is that I need to install?
-Rudy

---

### Post by johnc4510 on 2007-06-30
Anyone know the trick to getting conky on all desktops in comp-fusion? I would appreciated it 

because right now it only shows on the first desktop. Thanks

---

### Post by johnc4510 on 2007-06-30
OK, solved this by changing conky start delay from 10 seconds to 15. Now it runs on all desktops.

---

### Post by Rudy246 on 2007-07-01
[edit]
Nevermind, this problem is unrelated to Conky.

---

### Post by OffHand on 2007-07-02
> **Rudy246 said:**
> Hello. I seem to be having a bit of trouble around step 2.

My problems begin at:
```
./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe

```

After returning many successful lines, it returns this:

```

checking for GLIB... configure: error: Package requirements (glib-2.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've been looking around for solutions, but thus far haven't found anything. Any help is greatly appreciated.

Also, I'm fairly new to Ubuntu, I've only been using it for about two weeks, so forgive the possibly newbish question.
-Rudy

I f you want to compile you will need the dev versions... glib-2.0-dev or something like that. You will need the package build-essential as well to compile stuff.

---

### Post by FNDII on 2007-07-12
I dont see conky in the sessions window. This is the first time even clicking on sessions window

---

### Post by Nekiruhs on 2007-07-12
> **FNDII said:**
> I dont see conky in the sessions window. This is the first time even clicking on sessions window
You have to add it. Go to system > preferences > Sessions,  and add it there.

---

### Post by FNDII on 2007-07-12
system > preferences > Sessions 

> New > "command line"  > ok   ?

like that?

---

### Post by FNDII on 2007-07-12
Problem is that I don't see conky in my sessions menu and or don't know where to look for the command line

---

### Post by FNDII on 2007-07-13
I did a file search for conky. found a couple clicked on one and it started up no problem. figure that one is the executable.  Next I

system > preferences > Sessions > startup programs

> New > name = conky > command = /usr/X11R6/bin/conky  > Ok

But that wont load it on startup, i have to click the file to start it after boot.

---

### Post by stalker145 on 2007-07-13
> **FNDII said:**
> I did a file search for conky. found a couple clicked on one and it started up no problem. figure that one is the executable.  Next I

system > preferences > Sessions > startup programs

> New > name = conky > command = /usr/X11R6/bin/conky  > Ok

But that wont load it on startup, i have to click the file to start it after boot.

in place of ```
command = /usr/X11R6/bin/conky 
```all i put was ```
conky
``` in the appropriate spot and it worked out for me.

---

### Post by FNDII on 2007-07-13
well I just put conky in the command line. when i restart it looks like cony loads but it soon disappear. I'll have to go and start it up manualy again. Unless its already there and i  just cant see it for some reason.

---

### Post by miceagol on 2007-07-19
> **FNDII said:**
> well I just put conky in the command line. when i restart it looks like cony loads but it soon disappear. I'll have to go and start it up manualy again. Unless its already there and i  just cant see it for some reason.

It might help to issue the command
```

kdeinit

```
and then restart conky. If conky won't start at every boot, add kdeinit to sessions.

---

### Post by boob11 on 2007-07-22
Thanx man

---

### Post by prkfriryce on 2007-07-25
My conky refresh or update frequency is every 10 or more seconds. For the first 8 seconds it is visible on the desktop, but then disappears before it re-populates around the 10 second mark.  I installed lm-sensors, but even if I remove the 'i2c' variables from my config, the problem still persists.

As you can see, my update_interval is 1:

```

# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 300

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 70
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

TEXT
${color #0077ff}$sysname $kernel $machine - $nodename 

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}
${color #0077ff}MB:${color lightgrey}${i2c 9191-0290 temp 1}C${alignr}${color #0077ff}CPU:${i2c 9191-0290 temp 2}C



${color #0077ff}Hard Disks:
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
${color #0077ff} Muzik ${color lightgrey}${fs_used /home/muzik}/${fs_size /home/muzik}${alignr}${color #0077ff}${fs_bar 5,120 /home/muzik}
${color #0077ff} Video ${color lightgrey}${fs_used /home/video}/${fs_size /home/video}${alignr}${color #0077ff}${fs_bar 5,120 /home/video}


${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}Network: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s
${color #0077ff}${downspeedgraph eth0 27,120 000000 0077ff 180} $alignr${color #0077ff}${upspeedgraph eth0 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #0077ff}Network: ${color lightgrey}${addr eth1}

${color #0077ff}Down:${color lightgrey} ${downspeed eth1} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth1} k/s
${color #0077ff}${downspeedgraph eth1 27,120 000000 0077ff 180} $alignr${color #0077ff}${upspeedgraph eth1 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth1}           $alignr${color lightgrey}${totalup eth1}

${color #0077ff}Port(s)${alignr}#Connections
${color #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${color #0077ff}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}  


```

Any ideas why it is not updating every second?  thanks

---

### Post by wnelson on 2007-07-25
${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
execi is the line causing updates to be slow modify that line.

Walt

---

### Post by prkfriryce on 2007-07-25
> **wnelson said:**
> ${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
execi is the line causing updates to be slow modify that line.

Walt

The script is only executing every 1000 seconds. Should It be closer to the interval of 1 second?

---

### Post by OffHand on 2007-07-25
> **prkfriryce said:**
> The script is only executing every 1000 seconds. Should It be closer to the interval of 1 second?

I think it is ms

---

### Post by raul_ on 2007-07-25
It's in seconds

---

### Post by prkfriryce on 2007-07-25
> **OffHand said:**
> I think it is ms


thanks guys, updated to '1000000' ( 1000s ) and it's updating fine now

:)

---

### Post by prkfriryce on 2007-07-26
> **prkfriryce said:**
> thanks guys, updated to '1000000' ( 1000s ) and it's updating fine now

:)

well, after about 20 hours, it is back to updating every 10 seconds or so again. the only two processes that are using any CPU are

```
 5180 root      15   0  321m  42m  10m S    0  4.2  10:30.44 Xorg                                   
    1 root      15   0  2912 1848  524 S    0  0.2   0:01.71 init  
```

anyone else experiencing this?

---

### Post by limaunion on 2007-07-29
Hi! I've just  finished switching from gkrellm to conky and am really impressed!

I'm having two issues, maybe someone can help me:

1) I want to add the calendar output (/usr/bin/cal) aligned to the right margin of conky, but I'm just getting the first line aligned in this way (month/year), the rest is on the left margin. Any idea how to fix this ?

2) How can I divide by two the speed displayed by my CPU Fan sensor in order to have it correcly displayed ? 
Thanks for any info!
JC

---

### Post by Cryptic1911 on 2007-07-29
Hi, just wondering if anyone here has tried getting core temps from a quad core cpu yet.. I have conky all setup and working great except for the temps that i'm after. My problem is that I can't figure out what to put in conky for it to display the cpu core temps.. I can get other temps to show (mb chips)but those are "i2c temp1, 2 , 3". The ones I'm after are listed from sensors as coretemp-isa0000 , 0001 , 0002 and 0003.

here's sensors full output:


it8718-isa-0290
Adapter: ISA adapter
in0:       +1.12 V  (min =  +0.00 V, max =  +4.08 V)   
in1:       +2.02 V  (min =  +0.00 V, max =  +4.08 V)   
in2:       +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in3:       +2.85 V  (min =  +0.00 V, max =  +4.08 V)   
in4:       +0.30 V  (min =  +0.00 V, max =  +4.08 V)   
in5:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +0.83 V  (min =  +0.00 V, max =  +4.08 V)   
in7:       +3.09 V  (min =  +0.00 V, max =  +4.08 V)   
in8:       +3.07 V
fan1:     1102 RPM  (min =    0 RPM)                   
fan2:        0 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +52°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp2:       +40°C  (low  =  +127°C, high =  +127°C)   sensor = diode   
temp3:        -2°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
vid:      +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
temp1:       +62°C  (high =  +100°C)                     

coretemp-isa-0001
Adapter: ISA adapter
temp1:       +63°C  (high =  +100°C)                     

coretemp-isa-0002
Adapter: ISA adapter
temp1:       +58°C  (high =  +100°C)                     

coretemp-isa-0003
Adapter: ISA adapter
temp1:       +57°C  (high =  +100°C)

---

### Post by logos34 on 2007-08-05
nice tutorial.  I just used the conky deb straight from the Feisty repos though, and it works fine.  I installed wmctrl, added 'dbe' module to xorg.conf, and added the bottom part of your conyrc.conf stuff (after 'TEXT') to my own conky file (plus a few other tweaks of my own).  Here is what works for me:
> # Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft no

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors
default_color white

own_window_colour grey
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 10

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hda5:  ${fs_free_perc /media/hda5}%   ${fs_bar 6 /media/hda5}$color
hda8:  ${fs_free_perc /media/hda8}%   ${fs_bar 6 /media/hda8}$color

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

---

### Post by HarshReality on 2007-08-07
Anybody been able to get battery_bar to work? As I understand it uses height, width & number BAT0 being default...

I have status and time remaining working but the bar wont go for anything

---

### Post by fwojciec on 2007-08-07
Here is my conky setup, maybe someone will find it useful.

[[img]http://img339.imageshack.us/img339/3714/screenaugust07aa5.th.png[/img]](http://img339.imageshack.us/my.php?image=screenaugust07aa5.png)

Conky (very minimal) is in upper right corner.  Other apps on the screenshot are pypanel (top left) and tint (bottom left).  The WM is Openbox.

> # conky configuration

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1
#font -artwiz-snap-normal-r-normal-*-10-100-75-75-*-*-*-*
#font -*-terminus-medium-*-*-*-12-*-*-*-*-*-*-*
#font *nu*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Sans:size=8
xftfont nu


# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?

# out_to_console no

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)

own_window yes
own_window_transparent yes
own_window_type desktop
#own_window_type override
own_window_hints below,undecorated,skip_taskbar

#own_window_type desktop

#own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area

#minimum_size 190
minimum_size 400
#maximum_width 500

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width

border_width 1

# Default colors and also border colors

#default_color A29F84
default_color ffffff

default_shade_color black

default_outline_color black


# Text alignment, other possible values are commented

#alignment top_left

alignment top_right

#alignment bottom_left

#alignment bottom_right


# Gap between borders of screen and text

# same thing as passing -x at command line
gap_x 7
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average

# set to 1 to disable averaging
cpu_avg_samples 2

# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT

override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no
TEXT
$alignr${color #6FA637}CPU: ${color }$cpu% / ${color }${freq_g} GHz    ${color #6FA637}Bat: ${color }${execi 45 /home/filip/Scripts/readbattery.sh}    ${color #6FA637}RAM: ${color }$mem/$memmax


I also need a little script to read the battery charge:

> #!/bin/sh
acpi -b | awk '{print $3, $4}' | sed -e s/,//2


This is a very useful thread, btw!

---

### Post by HarshReality on 2007-08-07
Why do you need a script? Granted my system is using ACPI but... 

Battery Status: ${battery BAT1} $alignr ${battery_time BAT1}

Screenshot is here:
[http://harrea.100webspace.net/Shot-3.png](http://harrea.100webspace.net/Shot-3.png)

incidentally, the powers that be indicated the battery_bar only works in current SVN for conky.

---

### Post by fwojciec on 2007-08-07
> **HarshReality said:**
> Why do you need a script? Granted my system is using ACPI but... 

Battery Status: ${battery BAT1} $alignr ${battery_time BAT1}

Screenshot is here:
[http://harrea.100webspace.net/Shot-3.png](http://harrea.100webspace.net/Shot-3.png)

incidentally, the powers that be indicated the battery_bar only works in current SVN for conky.

Silly me - no need for the script anymore ;)  Thanks.

Edit: I spoke too soon...  I knew there was a reason why I had to use this script.  The battery variable, I was just reminded, works correctly only with the AC cord plugged in; when the laptop is on battery power $battery returns "full" all the time (which is pretty useless, naturally).  It's probably a hardware/bios issue - ACPI on my laptop is pretty sketchy...

---

### Post by pt123 on 2007-08-11
Is it possible for Conky to read a text file and output the text file over the desktop with the rest of the CPU load etc.

---

### Post by HarshReality on 2007-08-11
example of usage please?

---

### Post by pt123 on 2007-08-11
> **HarshReality said:**
> example of usage please?

I want to try and get a text file with my todo list on my desktop.

---

### Post by HarshReality on 2007-08-12
So, your wanting a list of sorts.. perhaps using the calander might be of more acceptable use?

---

### Post by a5benwillis on 2007-08-13
> **qchi said:**
> Hi all!

I just wanted to share my conky config files!

I've written a script to show weather information from yahoo in conky, but it is still using too many resources, so i will try to optimize it in the future.

ENJOY!



Has anyone gotten this weather script to work?

---

### Post by Nessa on 2007-08-13
Can conky show the internet speed?

---

### Post by OffHand on 2007-08-13
> **Nessa said:**
> Can conky show the internet speed?

Yes, it can.

---

### Post by Nessa on 2007-08-14
Can anyone share the how?

---

### Post by 5-HT on 2007-08-14
> **Cryptic1911 said:**
> Hi, just wondering if anyone here has tried getting core temps from a quad core cpu yet.. I have conky all setup and working great except for the temps that i'm after. My problem is that I can't figure out what to put in conky for it to display the cpu core temps.
Here's what I'm using:
```
$alignc${color red} CPU Temps(C): $color ${execi 6 /usr/bin/sensors | grep Core | paste -s | cut -c15-16,19-20,71-72}
```You'll need to play around with the parameters (replacing 'Core' for 'temp' would the the first thing, and then the cut parameters. I prefer piping through pasts to get everything on one line, but that's a preference thing.
Please refer to the manual pages for cut, paste, and grep if necessary.
Cheers,

---

### Post by RichJacot on 2007-08-14
I don't know if this is what your looking for or not, but try adding the following to your .conkyrc file for your interface to the internet.

```
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}

```

---

### Post by boob11 on 2007-08-15
Thanx!

---

### Post by legatek on 2007-08-16
I am having trouble getting the output of a log file to wrap long lines in conky. It appears that the fold command doesn't work when you tail log files, is that correct? How can I get long lines to wrap instead of simply disappearing when they run out of room? Here is the relevant line:

```
${tail /var/log/messages 3 | fold -w35}
```

---

### Post by boob11 on 2007-08-17
thnx

---

### Post by lixx on 2007-08-20
hey guys, how do i fix my battery status?

the status is currently located at /proc/acpi/battery/C16D
but if i use ${battery_time} it doesn't display the info

---

### Post by yodaky on 2007-08-21
I have been playing with various settings and I have finally gotten one that I like however now it would seem that the "space" taken up by what would be the window is roughly double what it should be.  Does anyone know how to "push" the box further to the right?

---

### Post by markonhismobile on 2007-08-21
Just a quick one here, I've dabbled with Conky before but could never get quite the right initial setup. I have now used the one from this guide and it provides all the details I need and I will tweak these so I'd like to say a big thank you for an excellent howto!

Now onto my question! I have installed the latest .deb from sourceforge (0.46.1 i think!) and it runs great, I have added conky to the startup items under Sessions and it does seem to load as Gnome is coming up but once my wallpaper is applied it seems to disappear! I can then launch it from a terminal or the Alt+F2 and it shows up fine!

I'm not using any 3D effects or anything like Compiz/Beryl etc. as this is on an old Tecra laptop! Would creating a script like the one shown for the 3D windows managers to avoid the shadows being drawn help at all by delaying it's launch until the wallpaper is displayed?

---

### Post by Nicram on 2007-08-21
Hi,
Is it possible to have conky visible all the time?
The problem is, when you maximize a window, conky is covered up. How to keep it visible like a panel in Gnome, Kde for example or at least as a docking option in gkrellm?
There's a hack for this using this file: _[COLOR=Blue][space_dapp.c]("http://www.tenr.de/junk/space_dapp.c.html")[/COLOR]_ but it's for flubox.
         I have been playing with various settings, but with no result.

Any ideas

This is my conkyrc by the way:

---

### Post by kevdog on 2007-08-22
Can someone post a snippet from their conkyrc file to show me how to used a fixed font?  Although this is a can of worms how do I find a list of fixed fonts to use -- Im looking for a nice one!!

---

### Post by litemotiv on 2007-08-23
> **kevdog said:**
> Can someone post a snippet from their conkyrc file to show me how to used a fixed font?  Although this is a can of worms how do I find a list of fixed fonts to use -- Im looking for a nice one!!

use_xft yes
xftfont Bitstream Vera Sans Mono:size=8

---

### Post by kevdog on 2007-08-26
This script still doesnt work for me:

#!/bin/bash
sleep 10 && conky;

I did exactly the above, changed permissions to 755, added the script to the Sessions menu.

Now when I reboot I get nothing coming up.
sudo ps -ef | grep conky
doesnt show any process running.

Before with just conky in the sessions menu, I would at least get conky up for a brief second before being replaced by the background.

Any other suggestions?

---

### Post by EinA on 2007-08-26
> **a5benwillis said:**
> Has anyone gotten this weather script to work?

Hi,
Can't see your script. Maybe the following script(tweather.sh) will help.
It was originally used in Torsmo but works fine in my Conky.  (Thanks to the Puppy Linux forum)
P.S I don't know much about how it works :-)

[COLOR="Blue"]#!/bin/bash

# This script receives two parameters
# LOCATION : is the LOCATION name in weather.yahoo.com without the .html
# SCALE: can be "C" or "F" the default is "F"

LOCATION="$1" 
SCALE="$2"
WEATHER_FILE=/tmp/weather${LOCATION}.txt

if [ ! -e $WEATHER_FILE ] ; then
  ELAPSED_TIME=601
else
  # Only execute the script every 10 minutes
  CURRENT_TIME=`date -u +%s`
  PREV_TIME=`date -r $WEATHER_FILE +%s`
  ELAPSED_TIME=`expr $CURRENT_TIME - $PREV_TIME`
fi


if [ $ELAPSED_TIME -gt 600 ] ; then
  if [ "${SCALE}" == "C" ] ; then
    wget http://weather.yahoo.com/forecast/${LOCATION}_c.html?force_units=1 \
        -O $WEATHER_FILE
  else
    SCALE="F"
    wget http://weather.yahoo.com/forecast/${LOCATION}.html?force_units=1 \
        -O $WEATHER_FILE
  fi
fi

awk '/<div id="forecast-temperature">/,/&deg;</' $WEATHER_FILE | \
grep "&deg" | \
sed -e 's/.\+>\([0-9]\+\)&deg.\+/\1/' > /tmp/tmp$$

echo `cat /tmp/tmp$$` " ${SCALE}"

rm /tmp/tmp$$

#These are to extract more
#awk '/More Current/,/Local/' $WEATHER_FILE | tr -d "\n" > tmp.txt
# cat tmp.txt | cut -d">" -f17
# cat tmp.txt | cut -d">" -f20
# cat tmp.txt | cut -d">" -f27
# cat tmp.txt | cut -d">" -f32
######################################################## end of script
[/COLOR]
and this is the line from my .conkyrc

[COLOR="Blue"]${color}Maidenhead: ${color green}${execi 1800 /root/tweather.sh UKXX0090 C }
[/COLOR]
to find your towns code go to [http://weather.yahoo.com](http://weather.yahoo.com)  find your town and then look in the url and you will see its code. Swap that for mine. (UKXX0090)

and some other chaps bring in stocks and share prices.

hope this helps
EinA

---

### Post by legatek on 2007-08-27
> **kevdog said:**
> This script still doesnt work for me:

Before with just conky in the sessions menu, I would at least get conky up for a brief second before being replaced by the background.

Any other suggestions?

I had to specify the entire path in the sessions menu (ie. /home/.../.conky_start.sh) to get the script to work. Now conky sits on top of everything until I kill it and restart it, but at least it shows up!

---

### Post by raul_ on 2007-08-27
> **kevdog said:**
> This script still doesnt work for me:

#!/bin/bash
sleep 10 && conky;

I did exactly the above, changed permissions to 755, added the script to the Sessions menu.

Now when I reboot I get nothing coming up.
sudo ps -ef | grep conky
doesnt show any process running.

Before with just conky in the sessions menu, I would at least get conky up for a brief second before being replaced by the background.

Any other suggestions?

try a "sudo chmod a+x script" instead

and then try to run it yourself

---

### Post by waldorsockbat on 2007-08-28
Ok guy's I need a little help here if you will be so kind.I can't get video card temp to work not sure what info besides what in the conky.

 Also I can't get the weather from a couple posts up to work either.  I copied and pasted the script ,chmod a+x weather.sh. I then changed the location in the conky line.

Here's my conky config

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

#Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
${color orange}$nodename $sysname $kernel on $machine
${color #C0C8CD}UpTime: ${uptime}   Load: ${loadavg}
${color orange}$stippled_hr
CPU:Pentium D940 ${freq}mhz ${alignr} Temp: ${execi 1 sensors | grep "CPU Temp:" | cut -c12-16 ;}C
${color orange} CPU0: ${cpu cpu1}% 
${color #C0C8CD}${cpubar cpu1} 
${color orange} CPU1: ${cpu cpu2}% 
${color #C0C8CD}${cpubar cpu2}
${color orange}Processes:${color #C0C8CD} $processes  ${color orange}  Running:${color #C0C8CD} $running_processes

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Hard Drive Temp: WD1600JB ${execi 1 nc localhost 7634 | cut -c31-32 ;}C
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color black}Nvidia: ${color white}${exec /usr/bin/nvidia-settings -q gpus | cut -c 29-43 | tail -n2}
${color black}GPU Core Temp: ${color white}${exec /usr/bin/nvidia-settings -q gpucoretemp |grep Attribute |cut -c 44-45}'C
${color}Maidenhead: ${color orange}${execi 1800 /root/tweather.sh USAL0162 C }

---

### Post by Plasma_NZ on 2007-08-29
re-post #509 by Nicram

> Hi,
Is it possible to have conky visible all the time?
The problem is, when you maximize a window, conky is covered up. How to keep it visible like a panel in Gnome, Kde for example or at least as a docking option in gkrellm?
There's a hack for this using this file: space_dapp.c but it's for flubox.
I have been playing with various settings, but with no result.

Any ideas


Anyone able to help...?  Wouldnt mind a solution myself as im lookin for the same solution..

---

### Post by codedmin on 2007-08-30
Hy there it's possible click in some place of conky and then run one script?

Like shortcut?

Thanks in advance

---

### Post by OffHand on 2007-08-30
> **codedmin said:**
> Hy there it's possible click in some place of conky and then run one script?

Like shortcut?

Thanks in advance

You cannot make conky clickable if that is what you mean.

---

### Post by Yes on 2007-08-30
For anyone who needs help loading Conky after Copiz or Beryl, someone gave me this script and it works perfectly:

```
#!/bin/bash

sleep 15 &&
conky &
exit
```

Make sure you make it executable:

```
chmod a+x /path/to/file.sh
```

---

### Post by codedmin on 2007-08-31
> **OffHand said:**
> You cannot make conky clickable if that is what you mean.

It's a shame :(

Thanks

---

### Post by stalker145 on 2007-09-04
Decided to tune up my Conky and can't seem to figure this one out.

I looked up the variables and found ```
${wireless_essid ath1}
```should allow me to view the name of the wireless AP that I'm hooked to. Doesn't quite seem to work - it just prints the code to screen.

I've already found that the code for the wireless quality is incorrect as read from the [sourceforge page]("http://conky.sourceforge.net/variables.html"), so I'm sure this is the case here. I found how to do this by culling the [Post Your Conky Files]("http://ubuntuforums.org/showthread.php?p=3307374#post3307374") thread, but I couldn't find the above needed correction.

Thanks to all, in advance.

---

### Post by foureight84 on 2007-09-04
> **stalker145 said:**
> Decided to tune up my Conky and can't seem to figure this one out.

I looked up the variables and found ```
${wireless_essid ath1}
```should allow me to view the name of the wireless AP that I'm hooked to. Doesn't quite seem to work - it just prints the code to screen.

I've already found that the code for the wireless quality is incorrect as read from the [sourceforge page]("http://conky.sourceforge.net/variables.html"), so I'm sure this is the case here. I found how to do this by culling the [Post Your Conky Files]("http://ubuntuforums.org/showthread.php?p=3307374#post3307374") thread, but I couldn't find the above needed correction.

Thanks to all, in advance.


if you want conky to display your wireless essid, then you can just do 
```
${exec iwconfig eth1 | grep "ESSID" | cut -c 25-50}
```

the cut command depends on your output. but that's the general idea.

---

### Post by stalker145 on 2007-09-04
> **foureight84 said:**
> if you want conky to display your wireless essid, then you can just do 
```
${exec iwconfig eth1 | grep "ESSID" | cut -c 25-50}
```

the cut command depends on your output. but that's the general idea.

Most excellent. With a little finagling of the cut numbers it worked perfectly. I thank you much.

---

### Post by foureight84 on 2007-09-05
> **stalker145 said:**
> Most excellent. With a little finagling of the cut numbers it worked perfectly. I thank you much.

no problem =D

---

### Post by Matt Jones on 2007-09-09
Can anybody help me.. I have conky set to load on start-up - it loads, then goes off again and I have to manually start it from the terminal.

any suggestions?

---

### Post by kevdog on 2007-09-11
Im trying to conky 1.47 from source. I think Ive installed all the required dependencies (there are more that what are actually listed on the sourceforge conky website).  Anyway at the end of the configure process I get the following:

```
 * x11:
  x11 support:      yes
  xdamage support:  yes
  xdbe support:     yes
  xft support:      yes

 * music detection:
  audacious:        no
  bmpx:             no
  mpd:              yes
  xmms2:            no

 * general:
  hddtemp:          yes
  portmon:          yes
  RSS:              no
  wireless:         no

```

Does anyone know how I can make some of those no statements become yes??  Specifically wireless and RSS.  Ive looked for the configure options available (such as --enable-wireless), but I couldnt find any available options.  Any suggestions??  

I guess on the same note I tried to compile the svn sources, but also keep getting errors in the configure process

```
checking for BASE_DEPENDENCIES... configure: error: Package requirements (cairo >= 0.9.2.
                                              libsvg-cairo >= 0.1.6) were not met:

No package 'libsvg-cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Im stumped on this error, b/c obviously this is pointing to a mssing package dependency but I dont know what this is!!

---

### Post by kevdog on 2007-09-12
Ive managed to get a little farther and found these were the options to compile the conky-1.47 version:

./configure --enable-wlan --enable-rss -enable-audacious --enable-bmpx

The xmms2 package is not available in the repositories.

The configure process completes however this is what Im finding during the make process:

make
make: *** No rule to make target `configure.ac', needed by `Makefile.in'.  Stop.
 

Help???

---

### Post by mikawber on 2007-09-18
I love this application, however I have a major question. I have an Intel Core 2 Quad Q6600 processor. Is there anyway to get a temp for every core?

---

### Post by dcast on 2007-09-23
Hey I followed the instructions exactly, however Conky only shows up as gnome is starting and before my wallpaper appears then it disappears. It also shows up as I am shutting down. How can I fix this?

---

### Post by aristotlewilde on 2007-10-06
AAAAAArgh!

I am having an issue that I had before.  I have not used conky ina long time and have since lost my original .conkyrc file (due to a full drive reformat).

My conky disappears when I click on the desktop.  Or, if I start it thru terminal, when I close the terminal window, it disappears.

I am frustrated because I had this fixed before.

I am using nvidia graphics in Feisty Fawn...

Anyone have thoughts?

Sorry for asking the same question I asked 12 months ago.  I can't find the proper responses.


***EDIT

I screwed around with my startup script (sleep for 12) and set desktop to override.  All good in the hood now!!!!!!!!!!1

---

### Post by victorbrca on 2007-10-21
Is there anyway I can setup conky to open on a specific viewport when using Gutsy with Compiz?

I added "title=conky" and "X viewport position = 5 and Y viewpoprt position = 0" but it does not work. It always open the desktop where it's called.


Thanks,

Vic.

---

### Post by tturrisi on 2007-10-22
> **kevdog said:**
> Im trying to conky 1.47 from source. I think Ive installed all the required dependencies (there are more that what are actually listed on the sourceforge conky website).  Anyway at the end of the configure process I get the following:

```
 * x11:
  x11 support:      yes
  xdamage support:  yes
  xdbe support:     yes
  xft support:      yes

 * music detection:
  audacious:        no
  bmpx:             no
  mpd:              yes
  xmms2:            no

 * general:
  hddtemp:          yes
  portmon:          yes
  RSS:              no
  wireless:         no

```

Does anyone know how I can make some of those no statements become yes??  Specifically wireless and RSS.  Ive looked for the configure options available (such as --enable-wireless), but I couldnt find any available options.  Any suggestions??  

I guess on the same note I tried to compile the svn sources, but also keep getting errors in the configure process

```
checking for BASE_DEPENDENCIES... configure: error: Package requirements (cairo >= 0.9.2.
                                              libsvg-cairo >= 0.1.6) were not met:

No package 'libsvg-cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Im stumped on this error, b/c obviously this is pointing to a mssing package dependency but I dont know what this is!!
You have to compile conky with the new wlan variables enabled.   See my Conky and Cairo writeups here:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)
and a HowTo Conky wifi at this foruum:
[http://ubuntuforums.org/showthread.php?t=563401](http://ubuntuforums.org/showthread.php?t=563401)
To get RSS configure with --enable-rss

---

### Post by cdiem on 2007-10-26
I have the following problem; I have a dual core processor, and would like to setup conky to show the temperature at the ACPI Thermal Zone of each of the cores (i.e., the ACPI temperature of each processor - something that [Kima]("http://www.kde-apps.org/content/show.php/Kima+-+kicker+monitoring+applet?content=33257") shows). How can I make it? Is it possible at all?

---

### Post by hikeb on 2007-10-27
First of all I want to thank every one for helping out and contributing to this and other topics.

Now let me tell you about my problem. When I go into X for the first time this is what happens when conky is loaded (please look at sswp.png problem highlighted in yellow) notice that conky is loaded on top of my top panel. But if I reload conky every thing loads just fine (please look at sswop.png)

I also included a screenshot of my sessions window.

I'm also posting my config file for conky.

Hope that someone can help me out with this.

---

### Post by mgbdeftones on 2007-10-27
> **hikeb said:**
> First of all I want to thank every one for helping out and contributing to this and other topics.

Now let me tell you about my problem. When I go into X for the first time this is what happens when conky is loaded (please look at sswp.png problem highlighted in yellow) notice that conky is loaded on top of my top panel. But if I reload conky every thing loads just fine (please look at sswop.png)

I also included a screenshot of my sessions window.

I'm also posting my config file for conky.

Hope that someone can help me out with this.

What you need to do is create a script so that conky will load after gnome/compiz has fully loaded, say 15 seconds after bootup

To do so:
1. Create a "file.sh" (name it whatever, without quotes)
2. In "file.sh" put:
                            #!/bin/bash
                            sleep 15 &&
                            conky &
                            exit
3. chmod a+x /path/to/file.sh (/path/to being the location that the file is stored, which can be anywhere)
4. Go back to session manager and instead of loading "conky", select the path to this file

Should fix it, good luck

---

### Post by hikeb on 2007-10-29
> **mgbdeftones said:**
> What you need to do is create a script so that conky will load after gnome/compiz has fully loaded, say 15 seconds after bootup

To do so:
1. Create a "file.sh" (name it whatever, without quotes)
2. In "file.sh" put:
                            #!/bin/bash
                            sleep 15 &&
                            conky &
                            exit
3. chmod a+x /path/to/file.sh (/path/to being the location that the file is stored, which can be anywhere)
4. Go back to session manager and instead of loading "conky", select the path to this file

Should fix it, good luck
mgbdeftones thanx a lot that did exactly what I need it to do. Now I can enjoy conky at start up.

---

### Post by pt123 on 2007-11-04
Anyone able to get Google Calendar working with this

[http://code.google.com/p/gcalcli/](http://code.google.com/p/gcalcli/)

I was trying to follow this how to 
[http://blog.wired.com/monkeybites/20...-embed-go.html](http://blog.wired.com/monkeybites/20...-embed-go.html)

but i am having problems installing the dependencies

---

### Post by zyg0t3 on 2007-11-08
Correct me if i'm wrong but dual core is utilizing 2 different cores within or inside of the same chip therefore i would expect the temperature results to be the same.

Pictures of the app in your link show temps for_ C_pu and _G_pu. 

> **cdiem said:**
> I have the following problem; I have a dual core processor, and would like to setup conky to show the temperature at the ACPI Thermal Zone of each of the cores (i.e., the ACPI temperature of each processor - something that [Kima]("http://www.kde-apps.org/content/show.php/Kima+-+kicker+monitoring+applet?content=33257") shows). How can I make it? Is it possible at all?

---

### Post by MicroChris on 2007-11-09
Anyone know if there's sensor support for Mobile Athlon XP's?

I have a 2500+M that I bought purely due to the fact that it's a sick overclocker, but it comes up as "Unknown CPU Type" in Linux and Windows.

---

### Post by arbulus on 2007-11-11
I use openbox, and I don't use a panel.  I just use Tint for a task manager.  but I don't have a clock, and I've seen people with clock's in their Conkys.  So, I'm curious: how would I need to setup my conkyrc to display just a small 12-hour clock in the bottom right corner of my screen?

---

### Post by lpb331 on 2007-11-11
Just make sure the line "alignment bottom_right" is not commented out and add the line "${time %I:%M:%S %p}" at the end of your .conkyrc file. If you want the rest of your conky somewhere else you can run multiple instances, where each conky runs its own config file.

---

### Post by arbulus on 2007-11-11
> **lpb331 said:**
> Just make sure the line "alignment bottom_right" is not commented out and add the line "${time %I:%M:%S %p}" at the end of your .conkyrc file. If you want the rest of your conky somewhere else you can run multiple instances, where each conky runs its own config file.


Awesome!  Thank you!

---

### Post by elcasey on 2007-11-11
I'm sure this has been covered before, but I can't find it (these conky threads are huge). I've almost completely reworked my .conkyrc today and am very happy that audacious variables are included in 1.4.8.

But....I can't figure out how to get a line to wrap. Every song title displayed by *$audacious_title* is wider than the 250px I've set to be conky's maximum width. I know I saw someone asking about this re: XMMS awhile back, but I cannot find the post again.

These are the audacious lines in my .conkyrc:
```
${color orange}MUSIC (Audacious) ${hr 2}$color
${audacious_title}
${audacious_bar 8,180} $alignr ${audacious_position} / ${audacious_length}
```

Attached is how it looks on-screen.

Any ideas? :confused:

---

### Post by cdiem on 2007-11-14
> **zyg0t3 said:**
> Correct me if i'm wrong but dual core is utilizing 2 different cores within or inside of the same chip therefore i would expect the temperature results to be the same.

Pictures of the app in your link show temps for_ C_pu and _G_pu.

I don't get this very well; the Preferences menu in Kima says, that these temperatures come from the "Linux Acpi Thermal Zone Driver"; but as I said, I don't understand this very much. 

Issuing
"cat /proc/acpi/thermal_zone/TZS0/temperature " gives me (at the moment):
temperature:             39 C
and "cat /proc/acpi/thermal_zone/TZS1/temperature" gives me (at the moment):
temperature:             49 C

What I was looking for was a command to put this in conky (something like "acpitemp", but for each of the cores, probably). 

Edit: -----------------> I think I'll stick with the normal way of putting this in, I mean, something like:   
${execi 5 cat /proc/acpi/thermal_zone/TZS1/temperature |cut -c26-27 } 
${execi 5 cat /proc/acpi/thermal_zone/TZS0/temperature |cut -c26-27 }

Thanks for help, anyway

---

### Post by BlackMotion on 2007-11-14
Hi all,

I don't know if this question is asked before but i have a problem
but when i press "show desktop"
*( i don't know if it's called "show desktop", i have the Dutch version...)*
than Conky disappears as well...
I've deleted the line: "own_window_type override" from the .conkyrc file because otherwise it' stay on top always... 

can anyone help me please,
i'm sorry if this question is asked before...:KS

---

### Post by BlackMotion on 2007-11-14
i have the same issue...

**My conky disappears when I click on the desktop.  Or, if I start it thru terminal, when I close the terminal window, it disappears.**

---

### Post by CanonKen on 2007-11-29
Any ideas why I'm getting this 

> ken@ubuntu:~$ conky
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: desktop window (16000b5) is subwindow of root window (187)
Conky: window type - override
Conky: drawing to created window (4200003)
Conky: drawing to double buffer
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory


---

### Post by stalker145 on 2007-11-29
> **CanonKen said:**
> Any ideas why I'm getting this

If you could post the output of ```
sudo fdisk -l
``` we can get to looking. I think the reason, though, is that if you're trying to get Conky to read your installed hard disks, you're putting in the wrong directory. Instead of ```
/media/hda1
```and so forth, it should be ```
/dev/hda1
```

---

### Post by mmac on 2007-12-01
Nevermind, I figured it out.   I'll post mine once I finish it.

---

### Post by anthonie on 2007-12-07
Hi there,

Two questions:

1. Installed latest conky without trouble. One thing annoys me though, and that is that Conky is always 'on top', so it always takes up space at my right side of the screen. I'd prefer for Conky to just be available when I go to my desktop. I looked at the config file but can't find where to change the settings.

2. I normally don't work within a Gnome surrounding but rather with E17. Anyone knows why it does not want to work under E17 or what to do to make it work?

First problem somehow solved itself without me doing anything else than a couple of reboots. The second remains though

---

### Post by subs on 2007-12-07
worked gr8!!!

amazing.... much better than the gdesklets i used to work with!!

---

### Post by Mud.Knee.Havoc on 2007-12-07
> **BlackMotion said:**
> i have the same issue...

**My conky disappears when I click on the desktop.  Or, if I start it thru terminal, when I close the terminal window, it disappears.**

Any program you run in a terminal will disappear when you close the terminal unless you add a & sign to the end of the command and properly exit the terminal.  EDIT: Actually, the & sign at the end of the command just lets you continue using the terminal... handy if you don't want 10 terminals open and useless just to run 10 different processes!  But you'll need to follow these steps to do what you're after.

For example, don't run
```
conky
```

Run
```
conky &
```

When you want to close the terminal, the best way to do it is type ```
exit
``` instead of clicking on the window's X.  This way, the process will remain running in the background.

This is very handy... you can add the & to any command to launch a program. :)

An alternative is to install a program like gmrun (I think there's also fbrun which does the same) - it will open a tiny window that lets you input a command (like "conky" or "pidgin") and then disappear, launching the program.

---

### Post by deviouschild on 2007-12-08
Hey i have it up and working now, only issue is after the install my desktop icons dissappear when conky refresh's???

---

### Post by phenolholic on 2007-12-12
my conky(ies) on my touchscreen laptop. envy.

---

### Post by HDave on 2007-12-12
I have a laptop with a wifi card (wlan0), a built in ethernet connection (eth0), a PC Express Card gigE (eth1), and a Verizon wireless card (ppp0).

Anybody out there have a way that I get conky to show the network traffic for the one connection I am using at any given moment in time.....thanks!!

Scriptless...if possible! :)

---

### Post by pt123 on 2007-12-13
> **phenolholic said:**
> my conky(ies) on my touchscreen laptop. envy.

can you post you .conkyrc file?how did you get the data into two different areas of the screen?

---

### Post by lpb331 on 2007-12-13
I've compiled conky 1.4.9 with audacious and wireless support. It's running fine but for some reason it takes around 8 seconds for ${audacious_position} to refresh even though the update interval is set to 1 second. I don't have a music_player_interval variable in my config, so it's not that. Any ideas on why this is happening?

---

### Post by anthonie on 2007-12-14
Hi all,

I have a question about text positioning. I have been playing around with conky for a while, all to much joy. However, I have a couple of graph-bars for my hdd's, and I'd like the text to sit on top of it, in order to preserve space. To achieve that I use negative margins, but that only solves the horizontal dimension. 

Anyone knows how to get the text lined up to the graph-bars?

---

### Post by victorbrca on 2007-12-14
Any one knows how to remove the border of a cpu and memory graph??

[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/misc/cpu-mem-graph.png[/IMG]


Thanks,


Vic.

---

### Post by anthonie on 2007-12-14
> **victorbrca said:**
> Any one knows how to remove the border of a cpu and memory graph??

In my conky version, 1.4.7, it's

draw_graph_borders no

---

### Post by victorbrca on 2007-12-14
> **anthonie said:**
> In my conky version, 1.4.7, it's

draw_graph_borders no

Thanks a lot man!!!  ;)



Vic.

---

### Post by Mikebert on 2007-12-15
> **Mud.Knee.Havoc said:**
> Any program you run in a terminal will disappear when you close the terminal unless you add a & sign to the end of the command and properly exit the terminal.  EDIT: Actually, the & sign at the end of the command just lets you continue using the terminal... handy if you don't want 10 terminals open and useless just to run 10 different processes!  But you'll need to follow these steps to do what you're after.

Actually, prepend 'nohup' to a command if you want to run no matter what happens to the window that called it.

```
mike@desktop> nohup conky &
```

= a conky that runs in the background and won't quit until explicitly killed.

EDIT:  nohup [command] & is a still a great way to run a process as described, but for conky, you can go into .conkyrc and set 'background yes' and conky will run the same way.  Just found that out after a lot of tinkering.

---

### Post by MachineBucket on 2007-12-20
Is it possible to enable all the variables at once by using apt-get? I installed conky 1.4.7 through synaptic, but it doesn't have audacious variable support.

```
machinebucket@notebook:~$ conky -v
Conky 1.4.7 compiled Thu Sep  6 13:03:21 GMT 2007 for Linux 2.6.15.7 (x86_64)

Compiled in features:

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * hddtemp
  * portmon
  * rss
  * wireless

```

I was also wondering if it matters what version of Audacious I have. I've got version 1.3.2.

---

### Post by CoolHand on 2007-12-20
I haven't posted to this thread in a long time.  Amazing how long it is.  I thought I would share a screencap of conky on my freshly installed 7.10 system.  It was great when I upgraded.  Just used apt-get to grab conky, copied over my old config added curl for grabbing web stuff and I was in buisness.  Looks good to me even on the default background.

---

### Post by Phurious on 2007-12-21
> **anthonie said:**
> Hi all,

I have a question about text positioning. I have been playing around with conky for a while, all to much joy. However, I have a couple of graph-bars for my hdd's, and I'd like the text to sit on top of it, in order to preserve space. To achieve that I use negative margins, but that only solves the horizontal dimension. 

Anyone knows how to get the text lined up to the graph-bars?

To move your text up or down you are going to have to play with offsets.  I had to modify *A LOT* of offsets in my .conkyrc, and it can get confusing.  The command you are looking for is ${voffset <AMOUNT>}.

```
background yes
update_interval 1.0
total_run_times 0

own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 300

#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

gap_x 40
gap_y 60

use_xft yes
xftfont Candara:size=6
xftalpha 0.8
uppercase no
override_utf8_locale yes
use_spacer no

#default_color dedede
default_color d2d2d2
default_shade_color 404040
#default_outline_color 404040
default_outline_color 597DB2

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

stippled_borders 2
border_margin 4
border_width 1

mpd_host localhost
mpd_port 6600

mail_spool $MAIL
no_buffers yes
cpu_avg_samples 2
net_avg_samples 2

#${offset 15}${color B26B59}${execi 3600 curl 'http://www.whatismyip.org'}$color

TEXT
${font bold:size=26}${color ffffff}${shadecolor 202020}${time %I:%M %p}$shadecolor$color$font
${font bold:size=8}${color ffffff}${shadecolor 202020}${time %A %B, %d %Y}$shadecolor$color$font
${color B28F59}$hr${color}
${font size=8}${color ffffff}${shadecolor 202020}$nodename$shadecolor$color$font - $sysname $kernel on $machine$font
${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}STATUS :$shadecolor$color
${color B28F59}${voffset -6}$hr${color}
Uptime: $uptime - Load: $loadavg
Processes:
	Running: $processes
	Active: $running_processes
Processes Detail:        ${alignr}${offset -4}PID    ${offset 4}CPU%   MEM%
	${color #B26B59}${offset 17}${top name 1}${alignr}${offset -3}${top pid 1}    ${top cpu 1}    ${top mem 1}$color
	${offset 17}${top name 2}${alignr}${top pid 2}    ${top cpu 2}    ${top mem 2} 
	${offset 17}${top name 3}${alignr}${top pid 3}    ${top cpu 3}    ${top mem 3}
	${offset 17}${top name 4}${alignr}${top pid 4}    ${top cpu 4}    ${top mem 4}
	${offset 17}${top name 5}${alignr}${top pid 5}    ${top cpu 5}    ${top mem 5}

${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}PROCESSOR :$shadecolor$color
${color B28F59}${voffset -6}$hr${color}
${cpugraph cpu0 60,299 070F1C 3073AA}
${voffset -68}AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
        Core 1: ${freq 1} MHz
        ${cpu cpu1}% ${color 597DB2}${cpubar cpu1}$color
        Core 2: ${freq 2} MHz
        ${cpu cpu2}% ${color 597DB2}${cpubar cpu2}$color


${voffset -12}${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}MEMORY :$shadecolor$color
${color B28F59}${voffset -6}$hr${color}
2GiB Corsair TWINX Pro:
        $mem / $memmax
        $memperc% ${color 597DB2}${membar}$color
${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}STORAGE :$shadecolor$color
${color B28F59}${voffset -6}$hr${color}
File systems:
        System: ${fs_used /} / ${fs_size /}
        ${color 597DB2}${fs_bar /}${color}
        RAID: ${fs_used /mnt/RAID} / ${fs_size /mnt/RAID}
        ${color 597DB2}${fs_bar /mnt/RAID}${color}

${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}NETWORK :$shadecolor$color
${color B28F59}${voffset -6}$hr$color
${voffset -5}${downspeedgraph eth0 64,149 495831 91B359}${upspeedgraph eth0 64,149 5C232D B05B6A}
${voffset -67}Ethernet:
	Public IP: ${offset 15}${execi 3600 curl 'http://www.whatismyip.org'}
	Local IP: ${offset 20}${addr eth0}
	Down: ${offset 20}${downspeed eth0} Kb/s${offset 80}Up: ${upspeed eth0}$color Kb/s

        
${voffset -4}${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}REMOVEABLE MEDIA :$shadecolor$color
${color B28F59}${voffset -6}$hr${color}
${if_mounted /media/USB-Thumbdrive}USB-Thumbdrive: ${fs_used /media/USB-Thumbdrive} / ${fs_size /media/USB-Thumbdrive}
${color 597DB2}${fs_bar /media/USB-Thumbdrive}${endif}${color}

${voffset -4}${color B28F59}$hr${color}
${voffset -2}${color B28F59}${shadecolor 202020}WEATHER :$shadecolor$color
${color B28F59}${voffset -6}$hr${color}
Weather report for Dallas, Texas:
${color 597DB2}${execi 60 /usr/bin/pymetar KDFW}$color
```

A screencap of my conky:

[http://i.pbase.com/o4/37/531737/1/90627352.JcW8fpDD.Conky.png]("http://i.pbase.com/o4/37/531737/1/90627352.JcW8fpDD.Conky.png")

---

### Post by pt123 on 2007-12-24
Can someone explain to me what the 10 & 20 mean
```

${tail /home/username/file.txt 10 20}

```because when I looked at the man page for tail, you specify the number of lines by using -n. When I enter the above command in the terminal I get these errors:
```

tail: cannot open `12' for reading: No such file or directory
tail: cannot open `20' for reading: No such file or directory

```
The lines ${tail /home/username/file.txt 10 20} is limiting me to 10 lines from the file, even when I change it to 12 20 I am only getting 10 lines.

Edit:

Once I changed this all is fine:
# Maximum size of buffer for user text, i.e. below TEXT line.default is 16384 bytes
max_user_text 32768

---

### Post by CanonKen on 2007-12-25
Whats the PID stand for where you have PID CPU% and MEM%

Edit - Googled it, Prog ID

---

### Post by shareMenaPeace on 2007-12-25
Is there a way to have deskto disabled and see conky?

I use 4 diffrent cube wallpapers thats why... and its configured to be in right corner, but appears left bottom.
Have also screenlets and AWN ...


Thanx

---

### Post by AirOnSkin on 2007-12-26
Hey there...

I just would like  to share my conky config. I was searching a lot for examples and did not found the one that fit my desires. So this is my conky-setup. Maybe it helps some of you.

[[img]http://img4.myimg.de/conky0ee9c_thumb.jpg[/img]](http://www.myimg.de/?img=conky0ee9c.jpg)

---

### Post by ronbrooks on 2007-12-27
I am trying to use conky 1.4.9 and when I try to compile it I get that X11 can't be found.  Dose anyone know how to fix this.  Here is I out put when I try and compile. 

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for X... no
configure: error: Can't locate your X11 installation


Maybe I will have to go back to 1.4.2

---

### Post by rjmdomingo2003 on 2008-01-02
Is it possible to have conky scroll horizontally (left to right) instead of just being stationary?

---

### Post by era506 on 2008-01-02
Hi!! I just discovered conky and I love it! Just have some questions:

- How can I display my CPU temp? The acpitemp variable doesn't seem to work
- How about the hard disk temp? The hdtemp variable doesn't work either -- Nevermind, I had to install hddtemp.
I have lmsensors installed and working with screenlets.
- How can I display the current song I'm listening with Exaile, I've read that you can with amarok but couldn't find how to do it.
- My desktop icons have dissapeared and they come back when I hover my mouse over them, this happens since conky was installed, how do I fix it?

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
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Xft font when Xft is enabled
xftfont AquaBase:size=8
#xftalpha 0.5

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes



# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font -*-purisa-*-*-*-*-11-*-*-*-*-*-*-*
#font -*-comic sans ms-*-*-*-*-11-*-*-*-*-*-*-*
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 35



# stuff after 'TEXT' will be formatted on screen

TEXT
${color 469bdc}$nodename  ${hr}
${color }Today is: $alignr${color }${time %A, }${time %e %B %G}
${color }The time is: $alignr${color }${time %I:%M %p}
${color }UpTime: $alignr${color }$uptime 
${color }Architecture: $alignr${color }$machine
${color }Kernel:$alignr${color }$kernel

${color 469bdc}AMD(R) Athlon64(TM)X2 CPU     4200+ @ 2.2GHz ${hr 2}$color
${color }CPU0: ${cpu cpu1}% ${cpugraph cpu1}
${color }CPU1: ${cpu cpu2}% ${cpugraph cpu2}
${color }CPU Temp: ${acpitemp}.C

${color 469bdc}Memory / Disk ${hr}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
Mint:	${fs_free_perc /} %    ${fs_bar 6 /}$color 
EdRA:	${fs_free_perc /media/sda6} %    ${fs_bar 6 /media/sda6}$color
WinXP:	${fs_free_perc /media/sda1} %    ${fs_bar 6 /media/sda1}$color
HDD Temp: ${hddtemp /dev/sda localhost 7634}

${color 469bdc}Internet Conetion ${hr}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count}      Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color 469bdc}Gmail ${hr}
${color }${execi 300 python /home/era506/.conky/gmail.py}

${color #469bdc}Weather ${hr}
${color }${execi 1800 /home/era506/.conky/weather/weather.sh CSXX0008}
```

Thanks in advance!

---

### Post by lvleph on 2008-01-02
[Amarok and Conky](http://ubuntuforums.org/showpost.php?p=4017279&postcount=570) Which by the way was only 2 posts before yours.

You already have the CPU Temp in you conkyrc. For the HD temp look around [this thread](http://ubuntuforums.org/showthread.php?t=281865).

---

### Post by era506 on 2008-01-02
Thanks!! The HD temp is working but the CPU doesn't, I think I have to use something different than "acpitemp" but I don't know what. Solved icons issue, it was because of the conkyrc I was using.

---

### Post by dannyboy79 on 2008-01-04
can anyone tell me how to edit my session startup apps without using X. meaning, what file can I edit through ssh to remove conky from my session startup windows and instead make it run .conkylaunch.

.conkylaunch is the bash script I created with this in it per another thread I read

#!/bin/bash
sleep 30 &&
conky &
exit

I can just wait until I get home and change it through X while sitting at my desk but I'd like to learn how to add and remove startup apps from the command line. I did a search for conky and found this:
~/.config/autostart/conky.desktop

it had this in it:
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_US]=conky
Exec=conky
X-GNOME-Autostart-enabled=true

Would I just change that to be this?:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_US]=conky
Exec=~/.conkylaunch
X-GNOME-Autostart-enabled=true

hopefully that would work. ANy thoughts on this?

---

### Post by John.Michael.Kane on 2008-01-04
> **era506 said:**
> Thanks!! The HD temp is working but the CPU doesn't, I think I have to use something different than "acpitemp" but I don't know what. Solved icons issue, it was because of the conkyrc I was using.

Since passing the acpitemp option is not working.You might want to try the method below.

1) Using lmsensors. I included the lines from my conky file. You will have to adjust the cut numbers eg: -c13-16 to fit your cpu's
```
Core 0: ${freq_g core 0}Ghz ${execi 8 sensors | grep -A 1 'Core 0' | cut -c13-16 | sed '/^$/d'}°C
        ${cpu core 0}% ${cpubar core 0}
```
```
        Core 1: ${freq_g core 1}Ghz ${execi 8 sensors | grep -A 1 'Core 1' | cut -c13-16 | sed '/^$/d'}°C
        ${cpu core 1}% ${cpubar core 1}
```
To set up lmsensors read the thread below.
[HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors")

---

### Post by era506 on 2008-01-04
> **John.Michael.Kane said:**
> Since passing the acpitemp option is not working.You might want to try the method below.

1) Using lmsensors. I included the lines from my conky file. You will have to adjust the cut numbers eg: -c13-16 to fit your cpu's
```
Core 0: ${freq_g core 0}Ghz ${execi 8 sensors | grep -A 1 'Core 0' | cut -c13-16 | sed '/^$/d'}°C
        ${cpu core 0}% ${cpubar core 0}
```
```
        Core 1: ${freq_g core 1}Ghz ${execi 8 sensors | grep -A 1 'Core 1' | cut -c13-16 | sed '/^$/d'}°C
        ${cpu core 1}% ${cpubar core 1}
```
To set up lmsensors read the thread below.
[HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors")

Thank you for the answer!!! I have lmsensors working with screenlets and the panel applet but with those lines didn't work in conky, I think I have to change the numbers c13-16 as you say but don't know how and  the howto you linked doesn't mention anything about them. What do those numbers mean?

---

### Post by John.Michael.Kane on 2008-01-04
> **era506 said:**
> Thank you for the answer!!! I have lmsensors working with screenlets and the panel applet but with those lines didn't work in conky, I think I have to change the numbers c13-16 as you say but don't know how and  the howto you linked doesn't mention anything about them. What do those numbers mean?

Passing the cut command allows the user to cut out selected columns or fields from one or more files.

Example:
```
Core 0: ${freq_g core 0}Ghz ${execi 8 sensors | grep -A 1 'Core 0' | cut -c13-16 | sed '/^$/d'}°C
        ${cpu core 0}% ${cpubar core 0}
```

The above line is passing the cut command with the -c option. Which specifies character positions, and in this case it would pass characters 13-16.

In order for you to pass the cut command correctly you need to adjust the amount of characters passed by the -c option, As everyones -c option will be different.

On the system you are running the characters might be longer or shorter. You would simply count the characters up to the point you want.

Taking your cpu for example. You would run sensors | grep -A 1 'Core0' from your terminal, and count the number of characters including any spaces/gaps until you reach the numbered amount you want cut pass.

You can also try using the version below. " you might still need to adjust the cut numbers"
```
Core0..:: ${freq_dyn_g cpu0}Ghz ::: Usage: ${cpu cpu0}% ${cpubar cpu0 8,50} ${execi 8 sensors | grep -A 1 'Core0' | cut -c13-16 | sed '/^$/d'}C
```
```
Core1..:: ${freq_dyn_g cpu1}Ghz ::: Usage: ${cpu cpu1}% ${cpubar cpu1 8,50} ${execi 8 sensors | grep -A 1 'Core1' | cut -c13-16 | sed '/^$/d'}C
```

---

### Post by era506 on 2008-01-04
This is what appears:
```
Core0 Temp:
             +40°C

```

That will be 26 characters?

---

### Post by dannyboy79 on 2008-01-04
> **dannyboy79 said:**
> can anyone tell me how to edit my session startup apps without using X. meaning, what file can I edit through ssh to remove conky from my session startup windows and instead make it run .conkylaunch.

.conkylaunch is the bash script I created with this in it per another thread I read

#!/bin/bash
sleep 30 &&
conky &
exit

I can just wait until I get home and change it through X while sitting at my desk but I'd like to learn how to add and remove startup apps from the command line. I did a search for conky and found this:
~/.config/autostart/conky.desktop

it had this in it:
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_US]=conky
Exec=conky
X-GNOME-Autostart-enabled=true

Would I just change that to be this?:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_US]=conky
Exec=~/.conkylaunch
X-GNOME-Autostart-enabled=true

hopefully that would work. ANy thoughts on this?

can anyone answer this question please? I would really appreciate it.

---

### Post by era506 on 2008-01-04
Got it!!! Thanks for everything!!

```
${color0}CPU1 Temp: ${color}${execi 8 sensors | grep -A 1 'Core0' | cut -c15-19 | sed '/^$/d'}
${color0}CPU2 Temp: ${color}${execi 8 sensors | grep -A 1 'Core1' | cut -c15-19 | sed '/^$/d'}
```

---

### Post by John.Michael.Kane on 2008-01-04
> **era506 said:**
> Got it!!! Thanks for everything!!

```
${color0}CPU1 Temp: ${color}${execi 8 sensors | grep -A 1 'Core0' | cut -c15-19 | sed '/^$/d'}
${color0}CPU2 Temp: ${color}${execi 8 sensors | grep -A 1 'Core1' | cut -c15-19 | sed '/^$/d'}
```

Glad it worked out.

---

### Post by funnypanks on 2008-01-04
hi i have a very strange problem. conky runs perfect when i launch it from alt+f2 but when i put it in sessions to boot with the computer it floats for some reason. to it stays above all windows. any help?

---

### Post by Bruce M. on 2008-01-04
> **funnypanks said:**
> hi i have a very strange problem. conky runs perfect when i launch it from alt+f2 but when i put it in sessions to boot with the computer it floats for some reason. to it stays above all windows. any help?

What do you mean by "floats" ?

Sounds like it could be the same problem I had.
When I set up conky to run at bootup, it came up before my desktop then was hidden when the destop came online.

If that's your problem try this.
Modify this to fit your situation.

```

#!/bin/bash
sleep 30 &&
conky -c ~/.startconky/conkymain &
sleep 2 &&
conky -c ~/.startconky/conkyweather &

```


A 30 second pause before conky starts, and another 2 second for the second instance of conky.

Hope this helps.
Bruce

---

### Post by John.Michael.Kane on 2008-01-04
> **funnypanks said:**
> hi i have a very strange problem. conky runs perfect when i launch it from alt+f2 but when i put it in sessions to boot with the computer it floats for some reason. to it stays above all windows. any help?

After installing conky via synaptic run
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

Next run
```
gedit ~/.conkyrc
```

Find the following lines below, and edited them.
# set to yes if you want Conky to be forked in the background
background no <---- change this from no to yes

# If own_window is yes, these window manager hints may be used
Remove this from in front of the line-->#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

---

### Post by funnypanks on 2008-01-04
thanks bruce and mike but shortly after posting i found this
[http://ubuntuforums.org/showthread.php?t=424670&highlight=conky+start](http://ubuntuforums.org/showthread.php?t=424670&highlight=conky+start)

very similar i think to bruce's post. ubuntu has the best support ever!

---

### Post by dannyboy79 on 2008-01-05
> **dannyboy79 said:**
> can anyone answer this question please? I would really appreciate it.

that was it if anyone else is interested in knowing how to edit session startup apps from the cli. BUT it worked when I removed the tilde and put the whole path like this:

Exec=/home/daniel/.conkylaunch

---

### Post by RavUn on 2008-01-05
I have my conky set to load at startup and it does but then it goes away... it seems like it may load before the desktop...?  Isn't there a way to make conky wait before  starting?  I had it setup like that on my other desktop but I forget how.

System>preferences>sessions Add... something like sleep 10 && conky but that didn't work...

---

### Post by Bruce M. on 2008-01-05
> **RavUn said:**
> I have my conky set to load at startup and it does but then it goes away... it seems like it may load before the desktop...?  Isn't there a way to make conky wait before  starting?  I had it setup like that on my other desktop but I forget how.

System>preferences>sessions Add... something like sleep 10 && conky but that didn't work...

As you can see a few posts earlier than this one, I use 30 seconds, just to make sure.  Works like a champ.

Bruce

---

### Post by RavUn on 2008-01-05
```

#!/bin/bash
sleep 30 &&
conky -c ~/.startconky/conkymain &
sleep 2 &&
conky -c ~/.startconky/conkyweather &

```

Yeah, I saw your post but I don't see how to add it to startup sessions... do you add it just like that in that one command line?  I don't have conkymain or conkyweather... so I figured I'd just use "sleep 30 && conky" but that does not work in the startup sessions.. it works when I put it in the terminal, though.  Would you know what I should put in the startup sessions to just make conky wait 30 seconds?

---

### Post by Bruce M. on 2008-01-07
> **RavUn said:**
> ```

#!/bin/bash
sleep 30 &&
conky -c ~/.startconky/conkymain &
sleep 2 &&
conky -c ~/.startconky/conkyweather &

```

Yeah, I saw your post but I don't see how to add it to startup sessions... do you add it just like that in that one command line?  I don't have conkymain or conkyweather... so I figured I'd just use "sleep 30 && conky" but that does not work in the startup sessions.. it works when I put it in the terminal, though.  Would you know what I should put in the startup sessions to just make conky wait 30 seconds?

Hi RavUn
OK, I see your dilemma now. Do this:
```

$ gedit ~/.startconky

```

Creates a hidden file in your home folder called startconky ( the . means it's hidden) in that file put this:.

```

#!/bin/bash
sleep 30 &&
conky

```

Now in you can start it with the terminal command:

```

$ ./.startconky

``` 

or for auto startup:
System>Preferences>Sessions>New
Name: Conky
Command: /home/{your foldername}/.startconky

Click on the [OK] buttom and make sure Conky is checked for startup.

Now if you ever want to add a second conky you only need to create it and change:
```

#!/bin/bash
sleep 30 &&
conky

```
to something like this:
```

#!/bin/bash
sleep 30 &&
conky -c ~/.startconky/conkymain &
sleep 2 &&
conky -c ~/.startconky/conkyweather &

```

BTW: You can stop conky with:

```

$ killall conky

```

Bruce

---

### Post by b4d on 2008-01-17
Hi is there a way to hide eth1 data if I am not connected to wireless? or maybe somehow that conky himself finds out what an i connected to pppoe, eth0, eth1? ty

---

### Post by erwall on 2008-01-17
> **b4d said:**
> Hi is there a way to hide eth1 data if I am not connected to wireless? or maybe somehow that conky himself finds out what an i connected to pppoe, eth0, eth1? ty
[http://ubuntuforums.org/showthread.php?t=644463&highlight=conky](http://ubuntuforums.org/showthread.php?t=644463&highlight=conky)

---

### Post by torgrot on 2008-01-21
Well I installed the version in the repositories 1.4.7  and copied the conkyrc file to my home directory.  I created the script to start it at login.  So far so good.  Conky displays as by default in the bottom left position.  I don't like it there so I modified conkyrc this way ```

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

```
Which I though would move it to the bottom right of the desktop, but it still shows up at the bottom left of the desktop.  :confused:  What am I doing wrong?  If I kill conky and start it from a terminal with the -a bottom_right it starts where I want it.

torgrot

---

### Post by Bruce M. on 2008-01-21
> **torgrot said:**
> Well I installed the version in the repositories 1.4.7  and copied the conkyrc file to my home directory.  I created the script to start it at login.  So far so good.  Conky displays as by default in the bottom left position.  I don't like it there so I modified conkyrc this way ```

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

```
Which I though would move it to the bottom right of the desktop, but it still shows up at the bottom left of the desktop.  :confused:  What am I doing wrong?  If I kill conky and start it from a terminal with the -a bottom_right it starts where I want it.

torgrot

Post your startup script please.
Bruce

---

### Post by torgrot on 2008-01-21
```

#!/bin/bash
sleep 30;
exec conky -d
exit

```

It starts just not in the correct locataion.  Here is the resource file
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
background yes
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 20

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```


torgrot

---

### Post by Bruce M. on 2008-01-22
I take it this is your "autostart" for conky?
And you are using the regular concyrc file.

> **torgrot said:**
> ```

#!/bin/bash
sleep 30;
exec conky -d
exit

```

If so try this one:

```

#!/bin/bash
sleep 30 &
conky &

```

> **torgrot said:**
> It starts just not in the correct locataion.  Here is the resource file

torgrot

```

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
```

Looks ok, you do want it on the bottom right, right?

---

### Post by torgrot on 2008-01-22
I'll try your startup script.  Yes I do want it to start on the bottom right.  It is just the default script with the alignment changed.  I figured I needed to start somewhere first.

torgrot::oops:  

I feel so stupid right now.  When I copied the default .conkyrc, I mistyped the name.  Sorry for bothering you.

torgrot

---

### Post by brainkilla on 2008-02-03
Given that my knowledge of sed is virtually non-existent, I would like to ask for something my config sorely lacks: I copied someone's .conkyrc and managed to delete lines I don't need, yet I cannot succeed in removing the part of sed output which displays processor model name - I have dual core Athlon 64, therefore processor name is displayed twice. How can I make output from /proc/cpuinfo more discriminatory, i.e. make it display processor name only once? Thanx...

---

### Post by rustutzman on 2008-02-05
Since that's not a piece of info that changes why not just type it in? That's what I ended up doing for my quad core.

Russ

TEXT
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey} - Load:$color $loadavg
Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.4 GHz
${color #ddaa00}Core 1: $color${freq 1} MHz $alignc${color lightgrey}${cpubar 5, 100 cpu1}$color  ${cpu cpu1}%
${color #ddaa00}Core 2: $color${freq 2} MHz $alignc${color lightgrey}${cpubar 5, 100 cpu2}$color  ${cpu cpu2}%
${color #ddaa00}Core 3: $color${freq 3} MHz $alignc${color lightgrey}${cpubar 5, 100 cpu3}$color  ${cpu cpu3}%
${color #ddaa00}Core 4: $color${freq 4} MHz $alignc${color lightgrey}${cpubar 5, 100 cpu4}$color  ${cpu cpu4}%
${color #ddaa00}CPU 1 ${exec sensors | grep -A 2 '^coretemp-isa-0000' | cut -c15-18 | grep '\u00b0'} CPU 2 ${exec sensors | grep -A 2 '^coretemp-isa-0001' | cut -c15-18 | grep '\u00b0'} CPU 3 ${exec sensors | grep -A 2 '^coretemp-isa-0002' | cut -c15-18 | grep '\u00b0'} CPU 4 ${exec sensors | grep -A 2 '^coretemp-isa-0003' | cut -c15-18 | grep '\u00b0'}

---

### Post by ikt on 2008-02-10
Bit of a problem, I have read parts of this thread and done a bit of a search but does not appear to immediately stand out to me the answer.

I have followed the instructions on the first page as best I can, and when I am in terminal and type 'conky' it comes up and looks good, however if I close the terminal window, conky goes with it.

when I start the pc however nothing comes up initially even though i have added it to the startup programs :/

Here is a picture of what it looks like when i start it in terminal:

[http://adam.com.au/totalss/conky.png](http://adam.com.au/totalss/conky.png)

but otherwise it doesn't start up properly, does anyone know what it might be?

---

### Post by RichJacot on 2008-02-10
Try this thread for your start up issue:
[http://ubuntuforums.org/showthread.php?t=424670&highlight=conky+start]("http://ubuntuforums.org/showthread.php?t=424670&highlight=conky+start")

It also appears your config can't see your drives.  Do a df -h in a terminal window, look for your drives an put those devices inplace of the /media ones you have in your config.

---

### Post by ikt on 2008-02-19
> **RichJacot said:**
> Try this thread for your start up issue:
[http://ubuntuforums.org/showthread.php?t=424670&highlight=conky+start]("http://ubuntuforums.org/showthread.php?t=424670&highlight=conky+start")

It also appears your config can't see your drives.  Do a df -h in a terminal window, look for your drives an put those devices inplace of the /media ones you have in your config.

thanks, that worked great.

---

### Post by coljohnhannibalsmith on 2008-02-28
I have an Acer 5102 WLMi Laptop with 2x AMD TL50 64 bit processors. I have "ATI Radeon Xpress 1100" graphics. I'm running the Ubuntu 7.10 "Gutsy Gibbon" AMD64 Alternate Install distribution. I'm using XGL/Compiz for 3D effects and am using "Nautilus" as a window manager. I also have conky 1.4.7, which I downloaded with:
 
"sudo apt-get install conky"
 
I have all the libraries and I believe I have satisfied all the dependencies by running:
 
"sudo apt-get update"
"sudo apt-get install"
 
I'm running conky with the following startup script which I'm launching at startup with "Session Manager:'
 
#! /bin/sh
 
sleep 30
 
/usr/bin/conky
 
The above mentioned script attempts to launch conky after 30 seconds. The desktop is almost always completely stable by then.
 
What happens intermittantly is that a small black square, about the size of a thumbnail will appear in the upper right hand corner on the desktop, then just go away. Other times conky will load just fine. When I try to run conky from "Terminal" and it fails, I get "segmenation faults."
 
I have my .conkyrc setup to " own use window" and "double buffering." I also have the window type set to "override."
 
I have edited my "xorg.conf" file to include the following line:
 
Load "dbe"
 
I have also compiled the current 1.4.9 version by hand successfully; but when I replace v1.4.7 with v1.4.9 the problem persists.
 
I suspect the problem could be caused by any of the following:
 
*Basic incompatibility with "Nautilus."
*conky being incompatible with the AMD64 platform.
*An improperly configured xorg.config file.
*Incompatible Desktop effects set.
*Incorrect settings in "gconf-editor."
 
I've read many of the previous posts and it doesn't appear anyone has solved this:confused:
 
**Does anyone have a reasonable idea what might be causing the problem? Should I just change my Window Manager to "Thunar" or something else that conky will get along with?
 
Any well thought out suggestions will be greatly appreciated.
 
 
 
Thanks, John

---

### Post by WernerBrandt on 2008-03-01
worked 1st attempt on fresh Kubuntu install

Great ' howto' 

Thank you!

---

### Post by koleoptero on 2008-03-05
Thank you for this great guide. Needed to do some tweaking, but I managed it. :KS

---

### Post by johnny9794 on 2008-03-05
Heya, I'm having a bit of little trouble from my end, I'd like conky to read my hdd temp, I have installed hddtemp and configured it correctly from my point of stand. for .conkyryc i might be doing something wrong for it to not show hddtemp. could someone help me out?

Here are my configs for hddtemp and conkyryc and a screenshot with gparted to show hdd info.

I am running one entire hdd with multi partitions.

---

### Post by Kerry_W on 2008-03-12
> **johnny9794 said:**
> Heya, I'm having a bit of little trouble from my end, I'd like conky to read my hdd temp, I have installed hddtemp and configured it correctly from my point of stand. for .conkyryc i might be doing something wrong for it to not show hddtemp. could someone help me out?

Here are my configs for hddtemp and conkyryc and a screenshot with gparted to show hdd info.

I am running one entire hdd with multi partitions.

to get my hd temps i just used the following in my conky script
${color lightgrey}Sata 1: ${color orange}${hddtemp /dev/sda} 
check my screenshot for the output.

Hope this helps.
Kerry

---

### Post by andybleaden on 2008-03-20
Well despite my worse fears and a few glitches I had a play around with this and got it running just perfectly for me. 

Changed the layout and did a few changes with me using wireless etc but looks fine and dandy.

I attach the txt file if you want to adapt it feel free :)

You will need to save it as a file called .conkyrc in your home folder though.

Feel free to ask any questions

---

### Post by arbulus on 2008-03-20
I have a question.  I recently got a new computer, and in the shuffle I lost my old conky script.  I was my favourite conky, just a clock and date. I had copied it from someone in the forums here, but I can't remember who it was, but I think I got it maybe six months ago.

Anyway, I've attached a screenshot of what it looks like.  Is anyone using this script or something very similar that could share with me?

[[IMG]http://img177.imageshack.us/img177/346/cleandesktopmk5.th.jpg[/IMG]](http://img177.imageshack.us/my.php?image=cleandesktopmk5.jpg)

---

### Post by banewman on 2008-03-22
> I have a question. I recently got a new computer, and in the shuffle I lost my old conky script. I was my favourite conky, just a clock and date. I had copied it from someone in the forums here, but I can't remember who it was, but I think I got it maybe six months ago.

Anyway, I've attached a screenshot of what it looks like. Is anyone using this script or something very similar that could share with me?

I just knocked up a quick one that is similar
```
alignment bottom_right
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes
double_buffer yes
use_spacer yes
use_xft yes
update_interval 1
maximum_width 200
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
xftfont Bitstream Vera Sans Mono:size=8
uppercase no 
stippled_borders 0
border_margin 10
border_width 1
default_color white
own_window_colour black
own_window_transparent yes
gap_x 25
gap_y 50

TEXT
${color white}${time %A %e} ${alignr}
${font size=1}${time %I:%M} ${time %p}
```
Hope it is close enough :)

---

### Post by arbulus on 2008-03-22
> **banewman said:**
> I just knocked up a quick one that is similar
```
alignment bottom_right
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes
double_buffer yes
use_spacer yes
use_xft yes
update_interval 1
maximum_width 200
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
xftfont Bitstream Vera Sans Mono:size=8
uppercase no 
stippled_borders 0
border_margin 10
border_width 1
default_color white
own_window_colour black
own_window_transparent yes
gap_x 25
gap_y 50

TEXT
${color white}${time %A %e} ${alignr}
${font size=1}${time %I:%M} ${time %p}
```
Hope it is close enough :)


Thank you so much!

---

### Post by zmjjmz on 2008-03-27
I'm running on an old Fluxbuntu box here, and whenever I turn on conky, it reserves this grey area in the screen instead of being transparent.  I commented out the own_window stuff, and then the rest of the desktop went grey.  Can anyone help?
Also, when I add conky to the startup file (I did use conky &) it didn't start...

---

### Post by SkonesMickLoud on 2008-03-30
Got my conky all set up the way I like it today, but when I hit my "Show Desktop" button conky disappears.  This doesn't happen when I manually minimize all windows open.

Any way to disable this?

---

### Post by andybleaden on 2008-04-01
Now then...having had a few weeks to play with this and there is one thing I cannot seem to sort which is to get the conky screen to be transparent ie the same background as the desktop. I have had a play around with this but wither end up with no display or all black....any ideas where I am going wrong?

I attach a txt  of the conky script

---

### Post by andybleaden on 2008-04-01
Sorted the above with the help of the conky irc channel and used a srcipt called feh 

which I found about through this 

[http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)

[http://linuxbrit.co.uk/feh/wiki](http://linuxbrit.co.uk/feh/wiki)

Which helped the settings and I now have a transparent backgroud ...yippe another in the eye for those nasty windows things!

---

### Post by SkonesMickLoud on 2008-04-01
> **andybleaden said:**
> Now then...having had a few weeks to play with this and there is one thing I cannot seem to sort which is to get the conky screen to be transparent ie the same background as the desktop. I have had a play around with this but wither end up with no display or all black....any ideas where I am going wrong?

```
#own_window yes
#own_window_transparent no
```

Uncomment these and change "no" to "yes".

---

### Post by andybleaden on 2008-04-03
Well after many different changes I have more success. Still struggling to get an amarok script that works but here is what I have now and a screen print for the first time

---

### Post by zmjjmz on 2008-04-03
Does anyone know of a good way to get Audacious to display statistics in conky? I fixed the other problem; by installing antiX, but I want an Audacious script...

---

### Post by Chame_Wizard on 2008-04-03
search and you will find it  :lolflag:

---

### Post by dccrens on 2008-04-06
Does anyone have the color variables working? From reading the docs and various posts it looks like you should be able to predefine color variable "color0 - color9" so you can change colors easily throughout the rc file. You can set "default_color" and then use "color" to ref it. 

I assume you would put for example:
color2 #42AE4A

and then later in the rc you would be able to say something like:
${color2}CPU0 ${cpu cpu1}% ${color #5000a0}${cpubar 6 cpu1}${color}

But this doesn't appear to work.

If I say:
${color #42AE4A}CPU0 ${cpu cpu1}% ${color #5000a0}${cpubar 6 cpu1}${color}

Then it works fine. 

But I would then have to go through and manually change every line that refs the color #42AE4A if I want to change it. Whereas, if I can define "color2" as "#42AE4A" in one spot then I could just change it in one place. 

Any help is appreciated.

---

### Post by dccrens on 2008-04-06
After experimenting more you can set the color0-color9 variable to "standard" color names such as red, blue, cyan, etc. But not the hex codes. Anyone have a list of the acceptable colors? Things like "cornflower blue" do not work.

---

### Post by Hobbes87 on 2008-04-06
If I want a word to appear in **bold** in conky, for example: System. How do I get this done?

---

### Post by ian320 on 2008-04-10
> **dccrens said:**
> After experimenting more you can set the color0-color9 variable to "standard" color names such as red, blue, cyan, etc. But not the hex codes. Anyone have a list of the acceptable colors? Things like "cornflower blue" do not work.

Try entering the hex values without the pound '#' sign. That works fine for me.

---

### Post by tone77 on 2008-04-14
Has anyone tried this on Hardy yet?  
Is it still a bunch of work to get it working on Hardy?

---

### Post by zmjjmz on 2008-04-14
I'd imagine it'd be quite the same.

---

### Post by Voorhees1979 on 2008-04-14
1.5.1 is available for Hardy just use Synaptic to install it. Have it working here fine. There was a bug reported but its not needed you change just change a setting in the conf file. Read here on how to do it:

[https://bugs.launchpad.net/ubuntu/+source/conky/+bug/195022](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/195022)

"own_window no" working fine here in overlay mode with no window. Just need to see how to make it a little bit bigger.

---

### Post by shanepardue on 2008-04-15
How do we prevent the flicker in Hardy? The modules section doesn't exist in my xorg.conf anymore. Thanks!

---

### Post by ashley1987 on 2008-04-18
hi... im new to ubuntu... so im looking for such an obvious fix that i will say durrr lol

im running gutsy, i followed the instructions on the how-to until i tried to save the *.conkyrc file. it says:

Could not save the file /home/bob/.conkyrc. Unexpected error: File not found.

What am i doing wrong?

Thanks everyone.

---

### Post by zmjjmz on 2008-04-18
It should be saved as .conkyrc, not *.conkyrc.

---

### Post by zka on 2008-04-26
I created a new thread before finding this one but since noone replied to it i guess its okay to paste it here ... 

My conky stopped being transparent as soon as I disabled nautilus option show deskop through configuration editor in order to have different wallpapers on each workspace. Instead the background of conky shows the part of the old wallpaper(default background on hardy).

Googled around and the problem seems to be that conky uses the default background of nautilus instead of being a "real" transperant. One solution was to use feh but the only guide on how to do it was for kde and it didn't work for me..

How do I fix this ? :(

PS: Only started using ubuntu few weeks ago so be easy on an eventual answer so that i can apply it myself =)

Thanks
 
My conky cfg taken from gnomelooks i think...

```
background no
font Zekton:size=7
xftfont Zekton:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment middle_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer left

TEXT
${font Zekton:style=Bold:pixelsize=42}${alignc}${time %H:%M:%S}${font Zekton:size=7}
SYSTEM ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
Battery    ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}
CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}

NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,107} ${alignr}${upspeedgraph wlan0 25,107}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}
```


Tried reading 30 pages of this thread before i died :( .. so if the problem was already addressed pls redirect me to what page...

---

### Post by waldorsockbat on 2008-04-27
I have a question about getting conky to display local tv listings with selected stations and times for the program.I have been searching for a few days now and all I have found is this how to in the link below but not exactly what I am looking for.

[http://howto.wikia.com/wiki/Howto_add_an_RSS_feed_to_Conky]("http://howto.wikia.com/wiki/Howto_add_an_RSS_feed_to_Conky")

Any ideas on how to take this script and tweak it or if you know where a guide is that will help I would very much appreciate your input.

---

### Post by Th3Professor on 2008-05-06
I originally used gkrellm, it was okay... then tried torsmo, really liked it... just discovered conky, and it's looking pretty cool. I just took the the generic config from the original post of this thread and made a couple adjustments to fit it to my computer and it's working great. :)

EDIT:
I've gotta dual core... how do I get both to show?

---

### Post by shadowtroopers on 2008-05-07
ok, how to enable autostart conky every time we boot? i'm not sure what to put on the "add start-up proggramme" details (name field,command field and comment field)

---

### Post by Th3Professor on 2008-05-07
> **shadowtroopers said:**
> ok, how to enable autostart conky every time we boot? i'm not sure what to put on the "add start-up proggramme" details (name field,command field and comment field)

Here's a real quick step-by-step...

1. Create a conky start-up script like ~/.conky_start.sh
Put this in the file:
```
#!/bin/bash
sleep 60 && conky;

```2. chmod 755 ~/.conky_start.sh
3. If you're in GNOME, go to System>Preferences>Sessions.
4. In the "Startup Programs" tab, click on "Add".
5. Click the "Browse..." button, find your new file and add it, name it, comment, etc.

That should do it.

---

### Post by gonio5 on 2008-05-13
Hey guys! that's my first post in the forum. I am running Linux ubuntu 8.04 right now, i m a noob basically so excuse my questions i m sure they ll be a bit silly.

Anyway, I installed CONKY following the instructions of this thread : [http://ubuntuforums.org/showthread.php?t=205865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

But, I had several problems while trying to make it work properly.
1: It was only running when I was logged in as *root*
2: I managed to make it work (Through TERMINAL) while logged in as my username but it gives me this:
```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: desktop window (10000b4) is subwindow of root window (5d)
Conky: window type - override
Conky: drawing to created window (3c00003)
Conky: drawing to double buffer
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory

```
Plus it is not aligned correctly, half of it is out of the screen site :(
I did change the conky script with others I found while researching in the forum (eg. [http://ubuntuforums.org/showthread.php?t=281865&highlight=install+conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=install+conky") )

3: I made the executable script mentiond in other posts above and in other threads : ```
#!/bin/bash
sleep 60 && conky;
```

But still no luck.....
And finally today when I logged in i realised my compiz is not working, as in the cube rotation and the extra effects I had on.
I know is really hard to tell what's going on and my post will be quite a pain, but please if someone knows post here, i really want this to work, i ve been trying 3 days now to make it work :(

ps. If my question is answered somewhere in the forum please direct me, I tried reading as much as i could before posting, but didnt find anything relevant.


Cheers :):):):)

---

### Post by zmjjmz on 2008-05-13
Check the permissions on your .conkyrc
try ```
sudo chmod 777 ~/.conkyrc
```

---

### Post by gonio5 on 2008-05-13
> **zmjjmz said:**
> Check the permissions on your .conkyrc
try ```
sudo chmod 777 ~/.conkyrc
```

Ok I did that, it asked for my password then nothing. it basically looked like this: 
```
gonio5@ozzy:~$ sudo chmod 777 ~/.conkyrc
[sudo] password for gonio5: 
gonio5@ozzy:~$ 
```

I restarted still no change, It doesnt show on startup, the compiz is not working and if i started from the terminal it's not alligned correctly and it gives me this again:

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: desktop window (e000b5) is subwindow of root window (5d)
Conky: window type - override
Conky: drawing to created window (3200003)
Conky: drawing to double buffer
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory

```
 :(

---

### Post by Th3Professor on 2008-05-15
"find the section titled Section "Module", and add
 	Code:
 	        Load    "dbe" 
"

Okay... I went into xorg.conf and didn't see "Module"... I'm assuming that's for the old xorg config files. My new xorg.conf (Ubuntu 8.04) is really short and to the point:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

That's ommitting the keyboard and mouse stuff.

So can I just add the Load "dbe" line within the "Monitor" section or maybe the "Screen" section?

My conky is not flickering every second or every single time it refreshes something within its "window", like the CPU bar or the DL/UL graphs... but rather, every few minutes the entire conky flickers - even when behind other windows, causing a flicker within other applications (on top of it).

Would the "dbe" line even stop that flicker?

---

### Post by SkonesMickLoud on 2008-05-15
@ gonoi5:

Try changing "hda#" to "sda#".

---

### Post by TWeerts on 2008-05-18
i have conky installed, and it runs in standard configuration. when i go to make a config file, it says: 

bash: gedit/home/ted/.conkyrc: No such file or directory

---

### Post by anticapitalista on 2008-05-18
Leave a space between gedit and the /
so it is like this.
gedit /home/ted/.conkyrc

---

### Post by Th3Professor on 2008-05-19
questions in my quote...

> **Th3Professor said:**
> "find the section titled Section "Module", and add
     Code:
             Load    "dbe" 
"

Okay... I went into xorg.conf and didn't see "Module"... I'm assuming that's for the old xorg config files. My new xorg.conf (Ubuntu 8.04) is really short and to the point:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```That's ommitting the keyboard and mouse stuff.

So can I just add the Load "dbe" line within the "Monitor" section or maybe the "Screen" section?

My conky is not flickering every second or every single time it refreshes something within its "window", like the CPU bar or the DL/UL graphs... but rather, every few minutes the entire conky flickers - even when behind other windows, causing a flicker within other applications (on top of it).

Would the "dbe" line even stop that flicker?

---

### Post by signseeker on 2008-05-19
I've got a dual monitor setup (2 separate screens driven by 2 graphics cards)

How would I go about getting conky to appear on the 2nd screen?

---

### Post by eberndl on 2008-05-19
Hi, I'm having some slight problems, I've been following the instructions for this tutorial (but slightly out of order).

Everything seems to be good, but when I did that big ./configure, I think it didn't do everything it was supposed to...

The last lines are:

checking for XDamageQueryExtension in -lXdamage... no
configure: error: Could not find XDamageQueryExtension in -lXdamage

and then when I went to the "make" line... I got

lizz@lizz-desktop:~$ gedit /home/lizz/.conkyrc
lizz@lizz-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.

I realise it's a n00bie question, but can anyone help with either of these??

Thanks!!!

---

### Post by zmjjmz on 2008-05-20
I believe conky is in the repos, no need to compile it.
```
sudo apt-get install conky
```

---

### Post by signseeker on 2008-05-20
> **signseeker said:**
> I've got a dual monitor setup (2 separate screens driven by 2 graphics cards)

How would I go about getting conky to appear on the 2nd screen?

Found this on the web, and it works like a charm,



Thriving with two monitors

If there are particular programs you want to start automatically when you log in, do the following:

   1. Create a start-up script:
         1. Create a file called startup.sh in your home directory.
         2.

            In startup.sh, set the first display and type in the applications you want to start there. Then, set the second display and type in the applications you want to start on that monitor. You may want to put the "intrusive" applications (email, IRC) on the secondary monitor.

            Here is an example start-up script for a dual-independent display (that is, on in which you specify either DISPLAY=:0.0 or DISPLAY=:0.1):

            # Applications on the left monitor
            export DISPLAY=:0.1
            evolution&
            xchat&

            # Applications on the right monitor
            export DISPLAY=:0.0
            firefox&
            gnome-terminal&
            gaim&

         3. Make startup.sh executable:

---

### Post by eberndl on 2008-05-20
zmjjmz, thanks.  I thought that I'd tried that before I did the self-compile, but I must have done something wrong the first time.

---

### Post by Th3Professor on 2008-05-21
> **Th3Professor said:**
> "find the section titled Section "Module", and add
     Code:
             Load    "dbe" 
"

Okay... I went into xorg.conf and didn't see "Module"... I'm assuming that's for the old xorg config files. My new xorg.conf (Ubuntu 8.04) is really short and to the point:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```That's ommitting the keyboard and mouse stuff.

So can I just add the Load "dbe" line within the "Monitor" section or maybe the "Screen" section?

My conky is not flickering every second or every single time it refreshes something within its "window", like the CPU bar or the DL/UL graphs... but rather, every few minutes the entire conky flickers - even when behind other windows, causing a flicker within other applications (on top of it).

Would the "dbe" line even stop that flicker?
?

---

### Post by citakis on 2008-05-22
thank you very much for the help. The article was amazing. Very good work

---

### Post by jharkn on 2008-05-25
Great howto :)

One problem though, I don't seem to be able to get conky to run on startup, I have to run it from the terminal each time.  Any idea why this is?  I followed the instructions here but it still doesn't work...

---

### Post by Fenris_rising on 2008-05-25
great tut lovely implementation on the desktop. but i have one problem!
cpu temp doesnt work with the acpitemp argument. i have read almost every page of this post and tried all the variations of the cpu temp text but to no avail. my M/B does use temp probes as under xp i had the ASUS monitoring software displaying the info. currently i have on my top bar the desktop all 3 HDD temps (this uses HDDTEMP) and the cpu core temp which uses the (kernel i2c sensors (hwmon). can anyone give me the nudge in the right direction. ive managed to add a few lines myself and adjust the code for my HDD id codes and my wireless lan so im not entirely stupid.........i think.

---

### Post by hufferd on 2008-05-25
I had this some place else but moved it here in hope that I may get help 

 Conky Help
Im not sure if this is posted in the right place

But I installed Conky .. using this tutorial here

Everything is working but ......

the conky window even though it appears to be on the desk top it covers up everything

ie I can see the desk top surface but not any open windows behind it


any
ideas?

---

### Post by Old Marcus on 2008-05-25
Hmm, it loads up when I log in, then when my desktop background appears, it disappears.

I try and run it in the terminal and get this:
```
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: desktop window (12000bc) is subwindow of root window (1a5)
Conky: window type - override
Conky: drawing to created window (3a00003)
Conky: drawing to double buffer
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory

```
Did I do something wrong here? could it be that this guide isn't compatible with gutsy? I used the OP guide so...

EDIT: No matter, it seems to be running fine now. Any idea how the change the text colour though? it's a bit invisible against my background...

---

### Post by signseeker on 2008-05-25
> **jharkn said:**
> Great howto :)

One problem though, I don't seem to be able to get conky to run on startup, I have to run it from the terminal each time.  Any idea why this is?  I followed the instructions here but it still doesn't work...

What desktop environment are you running?

---

### Post by signseeker on 2008-05-25
> **Old Marcus said:**
> Hmm, it loads up when I log in, then when my desktop background appears, it disappears.

I try and run it in the terminal and get this:
```
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: desktop window (12000bc) is subwindow of root window (1a5)
Conky: window type - override
Conky: drawing to created window (3a00003)
Conky: drawing to double buffer
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory

```
Did I do something wrong here? could it be that this guide isn't compatible with gutsy? I used the OP guide so...

EDIT: No matter, it seems to be running fine now. Any idea how the change the text colour though? it's a bit invisible against my background...


The text colour needs to be put in after 'TEXT'

for example - 

TEXT

${color #00ff00}${time %A, %d %B}${alignr}${alignr}${time %T}

${color #00ff00}System:
${color #00ff00}$nodename   ${alignr}linux-$kernel

${color #00ff00} Uptime:${color #7f8ed3} $uptime ${color #00ff00}- Load:${color #7f8ed3} $loadavg
${color #00ff00} CPU Frequency:${color #7f8ed3} $freq_dyn_g ${color #00ff00} Maximum:${color #7f8ed3} $freq_g

So basically, pick a colour you like, and start playing :)

---

### Post by jharkn on 2008-05-26
> **signseeker said:**
> What desktop environment are you running?

Gnome (with compiz-fusion if that has any effect, the conky process isn't in the system monitor though so I don't think that it's just been hidden by some special effect or other).

---

### Post by Fenris_rising on 2008-05-26
hi all

well it seems that half my problem was lm_sensors wasnt installed. so i have downloaded the tar file and installed it.........what do i do now. ive been trawling thru my file system trying to find anything that will give me a clue, same with the interweb. trouble is im not fluant in program language. i have a vague idea what certain things mean but not a clue how to implement it. in terminal the output of 'sensors' is;

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +53.0°C 

other than that its abject failure. can anyone instruct me in the dark art of getting the cpu temp going.

ive just managed to run the lm sensor detect program and its says i have w83627ehf sensor and k8temp sensor other than that im still going round in circles.

---

### Post by Th3Professor on 2008-05-26
Questions below...
> **Th3Professor said:**
> "find the section titled Section "Module", and add
     Code:
             Load    "dbe" 
"

Okay... I went into xorg.conf and didn't see "Module"... I'm assuming that's for the old xorg config files. My new xorg.conf (Ubuntu 8.04) is really short and to the point:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```That's ommitting the keyboard and mouse stuff.

So can I just add the Load "dbe" line within the "Monitor" section or maybe the "Screen" section?

My conky is not flickering every second or every single time it refreshes something within its "window", like the CPU bar or the DL/UL graphs... but rather, every few minutes the entire conky flickers - even when behind other windows, causing a flicker within other applications (on top of it).

Would the "dbe" line even stop that flicker?

---

### Post by Green_Star on 2008-05-26
> **jharkn said:**
> Gnome (with compiz-fusion if that has any effect, the conky process isn't in the system monitor though so I don't think that it's just been hidden by some special effect or other).

If you are running conky using startup, trying running it after 10-15 seconds. Like

sleep 20;conky

I am not sure about above syntax in startup but what I did is a created a shell program with two commands first one is sleep and second one is to run conky. If still not running then try catching conky log by doing something like "conky > /home/user/conkylog.log" and check the log after you logged in.

---

### Post by Fenris_rising on 2008-05-26
hi all
well ive got my conky showing the temp at last. big thanks to the poster who guided me. now my next question is really going to show me up as a noob. but here goes. the auto start string, i understand (starts conky at boot but with a delay so its drwn ontop of the background). ok i get that its very simple. my problem is i have no idea how to start. what app do i need to open up to type the code into. :oops: any one do an idiots guide please, ive been at this all day and ive also fixed a mates PC and installed 7.10 on it. so i have transferred my conkyrc file over to it and id like to just add the icing to the cake.

---

### Post by tigersrock on 2008-05-26
i have the "show desktop" option disabled in nautilus (i can't see icons on desktop) to be able to use different wallpapers on each side of the cube using compiz fusion. 

Conky works fine but the background of its window remains the same on each side and i really don't know much about this so....is there a way to get conky with different window background in each side?. I'm on ubuntu hardy.

---

### Post by Th3Professor on 2008-05-26
> **tigersrock said:**
> i have the "show desktop" option disabled in nautilus (i can't see icons on desktop) to be able to use different wallpapers on each side of the cube using compiz fusion. 

Conky works fine but the background of its window remains the same on each side and i really don't know much about this so....is there a way to get conky with different window background in each side?. I'm on ubuntu hardy.

You mean the background (wallpaper) image? A different image on each workspace?

I second that, I'm curious to know how to get a different background on each workspace too. :)

EDIT:
Correction - I'm referring to backgrounds, in general, not specifically the background behind conky.

---

### Post by Fenris_rising on 2008-05-27
ok im ](*,) ive tried every variation of the conky start file and i cant get it to start automatically. im running Hrdy Heron 8.04. this is what im doing.

sudo gedit ~/.conky_start.sh...........to create the file in home or
sudo gedit /home/fenris/.conky_start.sh......a variation of the above.

in the resulting file i put 

#!/bin/bash
sleep 60 && conky;


save it and then do this

chmod a+x .conky_start.sh.....to grant permission and allow as an exe or
chmod 755 ~/.conky_start.sh.... a variation of the above.

then i do this

go to System>Preferences>Sessions. and add 

./conky_start.sh

so far its failed. what am i doing wrong? and i have checked that the file is set to run.

heeeeeeeeeeeeelp! :confused:

---

### Post by RichJacot on 2008-05-27
Does it start properly or as expected if you just type conky at the command line?  If so, try adding the path to it in your start script.

---

### Post by Fenris_rising on 2008-05-27
hi there

yes in terminal 'conky' starts it know problem. at your suggestion i have no done this;
#!/bin/bash
sleep 60 && 
/home/fenris/.conky_start.sh

just going to try it, fingers crossed

---

### Post by Fenris_rising on 2008-05-27
failed!!!!!!!!!! blast!!!!!! it must be me

---

### Post by RichJacot on 2008-05-27
If that doesn't help I'll walk through how I have mine configured.

---

### Post by Fenris_rising on 2008-05-27
please do. its a small thing to want but it will all help with the learning curve.

---

### Post by RichJacot on 2008-05-27
Okay here we go....

My startup script looks like: (which may be overkill, but it works)

```

#!/bin/sh

# conky startup script
sleep 10
if pidof conky | grep [0-9] > /dev/null
then
exec killall conky
else
exec conky

fi

```

Notice the 10 second sleep.


In my sessions I have a conky startup that has this in the command section:

/usr/local/bin/conky.sh

which is where my startup is located (not in my home dir.).

I have nothing other than this on a fresh 64bit install of 8.04.  Let me know if this helps.

Rich

---

### Post by jjgomera on 2008-05-27
> **Fenris_rising said:**
> 

#!/bin/bash
sleep 60 && conky;


maybe that semicolon, remove it and retry

---

### Post by Fenris_rising on 2008-05-27
lololol this is so frustrating. every one else can do it except me!!!!!
didnt work on both counts. can you run me through the actual procedure of opening whatever it is you write the bash script in, right through to implementing it from session. i must be doing something wrong somewhere. i know its been written about extensively but not for a thick b$%^&*( like me.

---

### Post by RichJacot on 2008-05-27
Lets try something else first.

At the end of your session startup command line add:  > /tmp/conky.out 2>&1

So your session startup command should look like this:

/home/fenris/.conky_start.sh > /tmp/conky.out 2>&1

Lets see what output that gives you.  Once you log back in cat /tmp/conky.out and let me know what you get.

BTW: your just doing a ctrl backspace and not rebooting to test this, right? ;-)

---

### Post by Fenris_rising on 2008-05-27
gentlemen i am a fish of the first order! the tmp/ string produced a no such file or directory..............so i went back to the session string to check id added it properly which i had...........however when you notice that .sh has been typed in asssss..................ch oh god im such a pratt!!!! your thanks icons have been ticked and im now going to remove my worthless carcus to the back garden and have myself shot through the lungs.
thankyou for all you time and effort in helping me get this sorted.

---

### Post by RichJacot on 2008-05-27
Okay.  In a terminal window in your home dir.  

```

rm .conky_start.sh
vi .conky_start.sh

```

Copy and past my conky.sh from my other post into that vi session (don't forget to 'esc i' for insert mode before pasting). You can really use any editor you like here though. Then:

```


chmod 777 .conky_start.sh


```

Yes, 777 for now can can turn it back later.

Now in System -> Preferences -> Sessions

remove your current startup and then add a new one with the command:

```


/home/fenris/.conky_start.sh


```

The name and comment fields can be whatever you'd like.

Ctrl-backspace and log back in and it "should" work.

Good Luck!

---

### Post by RichJacot on 2008-05-28
Hello,

After a fresh install of 64bit 8.04 with my same .conkyrc file my calendar is cut off.

[http://www.flickr.com/photos/39672899@N00/2531248800/]("http://www.flickr.com/photos/39672899@N00/2531248800/")

Here's the end of my .conkyrc file and my calendar.sh.

```

.conkyrc:

$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 /usr/local/bin/amarok_conky.sh artist}
${alignc}${execi 10 /usr/local/bin/amarok_conky.sh title}
${execibar 2 /usr/local/bin/amarok_conky.sh progress}
${alignc}"${execi 10 /usr/local/bin/amarok_conky.sh album}"
${alignc}${execi 10 /usr/local/bin/amarok_conky.sh year} - ${color white}${alignc}${execi 10 /usr/local/bin/amarok_conky.sh genre}
$endif
${color #0774FC}CALENDAR ${hr 2}$color
${color #FFFFFF}${execi 300 /usr/local/bin/calendar.sh}


calendar.sh:

cal | awk 'NR>1' | sed -e 's/   /    /g' -e 's/[^ ] /& /g' -e 's/..*/  & /' -e 's/ \('`date | awk '{print $3}'`'\) /\['`date | awk '{print $3}'`'\]/'


```

Here is what I get when I run calendar.sh via cmd line.

```

borg:/usr/local/bin$ ./calendar.sh 
  Su  Mo  Tu  We  Th  Fr  Sa 
                   1   2   3 
   4   5   6   7   8   9  10 
  11  12  13  14  15  16  17 
  18  19  20  21  22  23  24 
  25  26  27 [28] 29  30  31 
                             

```

Any ideas why the end of my calendar is being cut off now?

---

### Post by jjgomera on 2008-05-28
if you count the character of calendar in conky, you will see conky show around 128, you must add this line at the beginning of conkyrc to modify that:

text_buffer_size=256

---

### Post by RichJacot on 2008-05-28
Thank you!  Minus the = sign it worked great.

It appears that this was changed on 3/19 according to the change log.

Thanks again!

---

### Post by Old Marcus on 2008-05-28
Odd, when compiz isn't running, the conky interface is hidden, but when compiz is running, conky appears over everything I open, including the top panel. Any help?

If needed, I can provide a screenshot.

---

### Post by dccrens on 2008-05-29
Has anyone used the "short_units" setting to get G vice GiB (Gigabytes) output? I have tried it but it doesn't seem to work. I tried "short_units on" but no joy...

---

### Post by Nessa on 2008-05-29
Any idea why conly says I have zero swap? I know for a fact that I have 1 gig. Just upgraded to 8.04.

```
swap $alignc $swap / $swapmax $alignr $swapperc% 
${swapbar}
```

---

### Post by jjgomera on 2008-05-29
go to gnome-system-monitor and check your real swap

---

### Post by Fenris_rising on 2008-06-01
hi all
heres my conky script again. i seem to have been able to select an alternate text however it know causes the PID, CPU, and MEM lists to wave in reaction to the name processors no longer remaining contracted, i assume this is just down to the larger font. ive tried to just space out the code but i assume im missing something basic. any one know how to cure this.

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

# Use double buffering (reduces flicker, may not work for everyone) 
double_buffer yes 

# fiddle with window 
use_spacer yes 
use_xft yes 

# Update interval in seconds 
update_interval 3.0 

# Minimum size of text area 
minimum_size 300 5 

# Draw shades? 
draw_shades no 

# Text stuff 
draw_outline no # amplifies text if yes 
draw_borders no 
# Xft font when Xft is enabled
xftfont Sans:size=9

uppercase no # set to yes if you want all text to be in uppercase 

# Stippled borders? 
stippled_borders 3 

# border margins 
border_margin 9 

# border width 
border_width 10 

# Default colors and also border colors, purple 
default_color purple 

own_window_colour brown 
own_window_transparent yes 

# Text alignment, other possible values are commented 
#alignment top_left 
alignment top_right 
#alignment bottom_left 
#alignment bottom_right 

# Gap between borders of screen and text 
gap_x 10 
gap_y 10 

# stuff after 'TEXT' will be formatted on screen 

TEXT 
$color 
${color red}SYSTEM ${hr 1}$color 
$nodename $sysname $kernel on $machine 

${color red}Time: ${color purple}${time %k:%M:%S} 
${color red}Date: ${color purple}${time %A, %d %B} 

${color red}CPU ${hr 1}$color 
${color purple}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} 
${freq}MHz   Load: ${loadavg}   Temp: ${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2} C 
${cpubar 7}$color 
${cpugraph C11B17 571B7e} 
ATI Driver Version:$alignr${execi 3600 fglrxinfo | tail -n2 | tail -c19} 

NAME		PID	  CPU%      MEM% 
${top name 1}${top pid 1}   ${top cpu 1}    ${top mem 1} 
${top name 2}${top pid 2}   ${top cpu 2}    ${top mem 2} 
${top name 3}${top pid 3}   ${top cpu 3}    ${top mem 3} 
${top name 4}${top pid 4}   ${top cpu 4}    ${top mem 4} 
${top name 5}${top pid 5}   ${top cpu 5}    ${top mem 5} 
${top name 6}${top pid 5}   ${top cpu 6}    ${top mem 6} 
${top name 7}${top pid 5}   ${top cpu 7}    ${top mem 7} 

${color red}MEMORY / DISK ${hr 1}$color 
RAM:   $memperc%   ${membar 7}$color 
Swap:  $swapperc%   ${swapbar 7}$color 

Root:  ${fs_free_perc /}%   ${fs_bar 7 /}$color 
sdb1:  ${fs_free_perc /media/sdb1}%   ${fs_bar 7 /media/sdb1}$color 
sdc1:  ${fs_free_perc /media/sdc1}%   ${fs_bar 7 /media/sdc1} 

${color red}NET ${hr 1}$color 
${color red}Total:${color purple} ${totaldown wlan0}${color red} Down${color purple} ${totalup wlan0}${color red} Up 

${color red}Wireless ${hr 1}$color 
${color red}Down:${color purple} ${downspeedgraph wlan0 20,100 C11B17 571B7e}${color red} Up:${color purple} ${upspeedgraph wlan0 20,100 C11B17 571B7e}  ${wireless_bitrate wlan0} 
${color red}ESSID:${color red} ${wireless_essid wlan0} 

${color red}Ethernet ${hr 1}$color 
${color red}Down:${color purple} ${downspeedgraph eth1 20,100 C11B17 571B7e}${color red} Up:${color purple} ${upspeedgraph eth1 20,100 C11B17 571B7e} 100Mb/s 

${color red}AMAROK ${hr 1}$color 
${if_running amarokapp} 

${voffset -3}${color red}Artist:$alignc${if_empty execi 10 dcop amarok player artist}$alignc${color purple}Music Stopped $else${color purple}${execi 10 dcop amarok player artist}$endif 

${voffset -3}${color red}Title:$alignc${color purple}${execi 10 dcop amarok player title} 

${voffset -3}${color red}Time:$alignc${color purple}${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime} 
 
${voffset -3}${color red}Album:$alignc${color purple}${execi 10 dcop amarok player album}$endif${font }
```

---

### Post by jjgomera on 2008-06-01
you can prove with:

${top name 1}${alignr}${top pid 1}   ${top cpu 1}    ${top mem 1} 
${top name 2}${alignr}${top pid 2}   ${top cpu 2}    ${top mem 2} 
${top name 3}${alignr}${top pid 3}   ${top cpu 3}    ${top mem 3} 
${top name 4}${alignr}${top pid 4}   ${top cpu 4}    ${top mem 4} 
${top name 5}${alignr}${top pid 5}   ${top cpu 5}    ${top mem 5} 
${top name 6}${alignr}${top pid 5}   ${top cpu 6}    ${top mem 6} 
${top name 7}${alignr}${top pid 5}   ${top cpu 7}    ${top mem 7}

---

### Post by Fenris_rising on 2008-06-01
ah that crossed my mind lol. thanks very much

---

### Post by h33tman on 2008-06-03
I'm sure this was probably covered already, I was searching through the pages, and it seems everyone but me knows how to do this.

How do I make the script executable? I'm running compiz on hardy, but I am not sure how to make that script executable for the boot.

---

### Post by Fenris_rising on 2008-06-03
in terminal type:

sudo gedit /home/yourname/.conky_start.sh to create a document notice the full stop at the front of conky! add the following code and save it.

```
#!/bin/bash

sleep 20 && conky;
```   20 is the time in seconds from the login to conky being drawn. dont go any less than 10.

in terminal type:

chmod a+x .conky_start.sh to make it executable.

go to sessions under system > preferences > session and 'add' then;

name: conky
command: /home/yourname/.conky_start.sh (notice the fullstop @ front of conky!)

and close. itll boot next time you restart.

---

### Post by h33tman on 2008-06-03
Thanks! I'll definitely give it a go when I get home. I kept struggling on the making executable last night. Thanks for the help

---

### Post by Fenris_rising on 2008-06-03
sorry dont forget to sudo the line:

**sudo** chmod a+x .conky_start.sh to make it executable

@jj i did the {alignr} but the string length of the {top name} seems to be causing the ripple in the columns which are well to the right as they should be. it seems the longer the output of the name string the following info in the same lines is pulled and pushed to the string names in reaction to the lengths.

---

### Post by cl0ckwork on 2008-06-03
another great conky thread!
sadly i have "borrowed" a few lines of code again :lolflag:

Fenris_rising, im borrowing from you mostly, ive been looking for a delayed start and im hoping this will work.

heres my code and screenshot for everyone else

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Kochi Gothic:size=8

# Text alpha when using Xft
xftalpha .8

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Update interval in seconds
update_interval 3

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 230 5
maximum_width 230

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 40

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#  Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}



# blue color ${color 246eb5}

# stuff after 'TEXT' will be formatted on screen

TEXT
${color goldenrod}SYSTEM ${hr 2}$color
Ubuntu  (7.10)  Gutsy Gibbeon
${time %B%e, %G} ${alignr}Uptime: $uptime
${color goldenrod}POWER ${hr 2}$color
Adapter Stat: ${acpiacadapter}	
Battery Info: ${battery}
${color goldenrod}NETWORK ${hr 2}$color
Down: ${downspeedf wlan0} Kb/s ${alignr}${downspeedgraph wlan0 15,130}
Up:   ${upspeedf wlan0} Kb/s ${alignr}${upspeedgraph wlan0 15,130}
Bitrate: ${wireless_bitrate wlan0} ${alignr}Wireless: ${wireless_essid wlan0}
${color goldenrod}CORE ${hr 2}$color
${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
CPU1: ${cpu cpu0}% ${freq} MHz$color  ${alignr}CPU2: ${cpu cpu1}% ${freq} MHz$color
${cpubar cpu0 5,110} ${alignr}${cpubar cpu1 5,110}
RAM: $memperc%  ${mem} / ${memmax}$color
${membar 5,110}  ${alignr}Temp:$color ${acpitempf} F
${color goldenrod}MEMORY ${hr 2}$color
Root/ ${alignr}${fs_used /}/${fs_size /}
${fs_bar 5,120 /}
Windows ${alignr}${fs_used /media/Windows}/${fs_size /media/Windows}
${fs_bar 5,120 /media/Windows}
Data  ${alignr}${fs_used /media/sdb1}/${fs_size /media/sdb1}
${fs_bar 5,120 /media/sdb1}
${if_running amarokapp}
${color goldenrod}AMAROK ${hr 2}$color

${voffset -3}${color goldenrod}Artist:$alignc${if_empty execi 10 dcop amarok player artist}$alignc${color wheat1}Music Stopped $else${color wheat1}${execi 10 dcop amarok player artist}$endif

${voffset -3}${color goldenrod}Title:$alignc${color wheat1}${execi 10 dcop amarok player title}

${voffset -3}${color goldenrod}Time:$alignc${color wheat1}${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime} 
 
${voffset -3}${color goldenrod}Album:$alignc${color wheat1}${execi 10 dcop amarok player album}$endif${font }
${color goldenrod}${hr 2}$color
```

---

### Post by Fenris_rising on 2008-06-03
:lolflag::lolflag: i think everyone starts by nicking code, thats the beauty of conky. im currently trying to tweak it on my laptop as that has dapper drake on it and amarok 1.3.......the Amarok code needs tweaking somehow to suit conky 1.4.2. unless i can get conky 1.5.1 to compile..........and thats a struggle. still my PC looks bloody great hehehe
dont ya just love ubuntu!

---

### Post by TWeerts on 2008-06-03
i have a great layout, but i cant seem to cange the fonts. how do you cange the fonts? font size?

---

### Post by Fenris_rising on 2008-06-03
make sure you change:
'use_xft no' to
'use_xft yes'

replace 'font arial' with:
xftfont Sans:size=9

i look in the font dropdown list of open office currently im using:

xftfont Purisa:size=8............i would like to try the bold, underline and italic's to if thats possible.

---

### Post by TWeerts on 2008-06-05
for some reason, my graphix driver was turned off. i turned it back on, and restarted. now, when i run conky , it takes a good 45 seconds for it to appear, and refreshes after another 45 seconds. any help?

i tried another restart as well

---

### Post by HpZ on 2008-06-07
i installed it but how do I get it to stay to the desktop and not on top of other windows?

---

### Post by cl0ckwork on 2008-06-07
> **HpZ said:**
> i installed it but how do I get it to stay to the desktop and not on top of other windows?

what does your code look like?

did u include
```
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override
```

also what worked for me is setting up a bash script for conky to start after x amount of seconds

```
#!/bin/bash

sleep 20 && conky;
```

save it as something like .conky_startup, make it executable, and add it to your startup programs in system->pref->sessions

---

### Post by Th3Professor on 2008-06-08
.> **Th3Professor said:**
> "find the section titled Section "Module", and add
     Code:
             Load    "dbe" 
"

Okay... I went into xorg.conf and didn't see "Module"... I'm assuming that's for the old xorg config files. My new xorg.conf (Ubuntu 8.04) is really short and to the point:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```That's ommitting the keyboard and mouse stuff.

So can I just add the Load "dbe" line within the "Monitor" section or maybe the "Screen" section?

My conky is not flickering every second or every single time it refreshes something within its "window", like the CPU bar or the DL/UL graphs... but rather, every few minutes the entire conky flickers - even when behind other windows, causing a flicker within other applications (on top of it).

Would the "dbe" line even stop that flicker?

How do I stop the flickering?

The flickering occurs every minute or couple/few minutes.

---

### Post by Raistlin82 on 2008-06-08
> **cl0ckwork said:**
> another great conky thread!
sadly i have "borrowed" a few lines of code again :lolflag:

Fenris_rising, im borrowing from you mostly, ive been looking for a delayed start and im hoping this will work.

heres my code and screenshot for everyone else

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Kochi Gothic:size=8

# Text alpha when using Xft
xftalpha .8

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Update interval in seconds
update_interval 3

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 230 5
maximum_width 230

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 40

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#  Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}



# blue color ${color 246eb5}

# stuff after 'TEXT' will be formatted on screen

TEXT
${color goldenrod}SYSTEM ${hr 2}$color
Ubuntu  (7.10)  Gutsy Gibbeon
${time %B%e, %G} ${alignr}Uptime: $uptime
${color goldenrod}POWER ${hr 2}$color
Adapter Stat: ${acpiacadapter}	
Battery Info: ${battery}
${color goldenrod}NETWORK ${hr 2}$color
Down: ${downspeedf wlan0} Kb/s ${alignr}${downspeedgraph wlan0 15,130}
Up:   ${upspeedf wlan0} Kb/s ${alignr}${upspeedgraph wlan0 15,130}
Bitrate: ${wireless_bitrate wlan0} ${alignr}Wireless: ${wireless_essid wlan0}
${color goldenrod}CORE ${hr 2}$color
${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
CPU1: ${cpu cpu0}% ${freq} MHz$color  ${alignr}CPU2: ${cpu cpu1}% ${freq} MHz$color
${cpubar cpu0 5,110} ${alignr}${cpubar cpu1 5,110}
RAM: $memperc%  ${mem} / ${memmax}$color
${membar 5,110}  ${alignr}Temp:$color ${acpitempf} F
${color goldenrod}MEMORY ${hr 2}$color
Root/ ${alignr}${fs_used /}/${fs_size /}
${fs_bar 5,120 /}
Windows ${alignr}${fs_used /media/Windows}/${fs_size /media/Windows}
${fs_bar 5,120 /media/Windows}
Data  ${alignr}${fs_used /media/sdb1}/${fs_size /media/sdb1}
${fs_bar 5,120 /media/sdb1}
${if_running amarokapp}
${color goldenrod}AMAROK ${hr 2}$color

${voffset -3}${color goldenrod}Artist:$alignc${if_empty execi 10 dcop amarok player artist}$alignc${color wheat1}Music Stopped $else${color wheat1}${execi 10 dcop amarok player artist}$endif

${voffset -3}${color goldenrod}Title:$alignc${color wheat1}${execi 10 dcop amarok player title}

${voffset -3}${color goldenrod}Time:$alignc${color wheat1}${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime} 
 
${voffset -3}${color goldenrod}Album:$alignc${color wheat1}${execi 10 dcop amarok player album}$endif${font }
${color goldenrod}${hr 2}$color
```



Hi all,  just been looking at the above and tried it out, I like it, been playing around with Conky trying to see what I like and don't, on that note can anyone tell me how I can change the temp measurement from Fahrenheit to Celsius? Cos i have no idea about degrees f, was always brought up to know degrees c:)

---

### Post by Raistlin82 on 2008-06-08
Figured it out, was easier than I thought it would be and I feel a bit stupid now, still i'm only learning!!!  All I had to do was insert ${acpitemp} Celsius rather than ${acpitempf} F

---

### Post by cl0ckwork on 2008-06-08
> **Raistlin82 said:**
> Figured it out, was easier than I thought it would be and I feel a bit stupid now, still i'm only learning!!!  All I had to do was insert ${acpitemp} Celsius rather than ${acpitempf} F

:)
everyones gotta start somewhere
also check these links for reference
the first one is for the settings before TEXT, second one is for everything after
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by davethomas691 on 2008-06-09
Hey all, I've had a look around to see if anyone else has had this problem and I haven't found anything like it yet.  When I run Conky, the pseudo transparency is off.  It appears as though it took the background from a few pixels off in each direction and set that as the Conky background.  Check out the screenshot.  The problem is easiest to see at the top near the System and CPU sections

Here is my .conkyrc

```

background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.3
total_run_times 0
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 0
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT




${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/storage} / ${fs_size /media/storage}
${fs_bar 4 /media/storage}

NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 24,128} ${alignr}${upspeedgraph eth0 24,128}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

WEATHER${hr 1}${color}

${color}Location: ${color ffffff}Orlando, FL$color

${color #B3B3B3}${execi 3600 python /home/davidthomas/.scripts/conkyForecast.py --location=32816 --imperial --template=/home/davidthomas/.scripts/conkyForecast2.template}
${alignr}${voffset -130}${offset -70}${font weather:size=45}${color}${execi 3600 python ~/.scripts/conkyForecast.py --location=32816 --startday=0 --datatype=WF}$font$color
${alignr}${voffset 5}${offset -70}${font weather:size=45}${color}${execi 3600 python ~/.scripts/conkyForecast.py --location=32816 --startday=0 -n --datatype=WF}$font$color


${voffset 7}${color}3 day forecast
${voffset 7}${color}${offset 12}${execi 3600 python ~/.scripts/conkyForecast.py -w --location=32816 --startday=1 --endday=3 --datatype=DW --spaces=27}
${font weather:size=44}${color}${offset 12}${execi 3600 python ~/.scripts/conkyForecast.py --location=32816 --startday=1 --endday=3 --datatype=WF} $font$color
${color e0e0e0}${execi 3600 python /home/davidthomas/.scripts/conkyForecast.py --location=32816 --imperial --spaces=27 --template=/home/davidthomas/.scripts/conkyForecast.template}
```

Any help would be greatly appreciated.

---

### Post by Sealbhach on 2008-06-10
OK, I have a reasonably good conky now....



.

---

### Post by Green_Star on 2008-06-10
> **davethomas691 said:**
> Hey all, I've had a look around to see if anyone else has had this problem and I haven't found anything like it yet.  When I run Conky, the pseudo transparency is off.  It appears as though it took the background from a few pixels .................

Can I see your templates, please. I mean

/home/davidthomas/.scripts/conkyForecast.template
/home/davidthomas/.scripts/conkyForecast2.template

---

### Post by cl0ckwork on 2008-06-10
> **Sealbhach said:**
> Hi,

I copied in the config from the first page and it looks nice but...

 It stays on top, even when I'm in Firefox, it's on top, blocking my view.

EDIT:

I think I missed the script to start Conky after Compix starts



in

.conky_start.sh 


Would that be the reason?


.

thats what happened with mine. it doesnt have to be 60 seconds though. 20 worked fine for me but nothing less than 10

---

### Post by Camuso21 on 2008-06-16
Hey I'm new to this whole Linux dance, and I really want to get conky working and am currently stuck at steps three and four, this is the results I get in terminal when I try to run steps three and four, its probably a really simple mistake but I'm making it anyway.

```
:~$ gedit /home/bob/.conkyrc
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

** (gedit:24734): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

```

---

### Post by raul_ on 2008-06-16
Well, there's something wrong with your ~/.fonts file, but that shouldn't compromise this guide. Just proceed as if it was nothing.

---

### Post by Camuso21 on 2008-06-16
Wow, I'm so depressed at how miserable of a mistake that was, anyways I figured it out.

---

### Post by Camuso21 on 2008-06-16
New problems, conky doesnt appear to be transparent, when I start a new session it appears to be above all of the windows. My other problems are probably easy, the first is that I can't find the module section of the /etc/X11/xorg.conf file. And finally could someone go into a little detail about creating a startup script (the last step).

---

### Post by davethomas691 on 2008-06-16
> **Green_Star said:**
> Can I see your templates, please. I mean

/home/davidthomas/.scripts/conkyForecast.template
/home/davidthomas/.scripts/conkyForecast2.template

A couple of restarts and a new script to start conky fixed things up for me.  Thanks for being willing to help.

---

### Post by cl0ckwork on 2008-06-16
> **Camuso21 said:**
> New problems, conky doesnt appear to be transparent, when I start a new session it appears to be above all of the windows. My other problems are probably easy, the first is that I can't find the module section of the /etc/X11/xorg.conf file. And finally could someone go into a little detail about creating a startup script (the last step).
```

#!/bin/bash
sleep 20 && conky
```

save that as .startconky,sh or something then run 

```
chmod u+x ~/.startconky
```

to make it exectutable

then add the .startconky.sh to your sessions menu and you are all set
the sleep 20 section should also sove the problem of having it on top of other windows

---

### Post by jokermatt999 on 2008-06-19
I'm kind of a linux newbie here, but I like my Conky rc file. I know a few of the scripts I use with it could be cleaned up, but they work for now.

I was wondering, however, if there was a way to set the scale of the upspeed graph to the downspeed. I couldn't find a way to pass the downspeed variable through conky, and I searched in vain for an easy way to find it through shell scripting, so I was wondering if anyone here could show me a solution.

Anyway, screenshot, conkyrc, and scripts below.

[http://i32.tinypic.com/157q60.png](http://i32.tinypic.com/157q60.png)

Edit: img tags + fullscreenshot = bad idea

---

### Post by cl0ckwork on 2008-06-19
> **jokermatt999 said:**
> I'm kind of a linux newbie here, but I like my Conky rc file. I know a few of the scripts I use with it could be cleaned up, but they work for now.

I was wondering, however, if there was a way to set the scale of the upspeed graph to the downspeed. I couldn't find a way to pass the downspeed variable through conky, and I searched in vain for an easy way to find it through shell scripting, so I was wondering if anyone here could show me a solution.

how do you mean scale it? you can change the size of the graphs and bar sizes my adding variables after it 
ex: ${downspeedgraph wlan0 15,130} or ${fs_bar 5,120 /}
where the first number is the height and second number is the length.

any other Q's feel free to ask

---

### Post by Th3Professor on 2008-06-19
> **jokermatt999 said:**
> I'm kind of a linux newbie here, but I like my Conky rc file. I know a few of the scripts I use with it could be cleaned up, but they work for now.

I was wondering, however, if there was a way to set the scale of the upspeed graph to the downspeed. I couldn't find a way to pass the downspeed variable through conky, and I searched in vain for an easy way to find it through shell scripting, so I was wondering if anyone here could show me a solution.

Anyway, screenshot, conkyrc, and scripts below.

[http://i32.tinypic.com/157q60.png](http://i32.tinypic.com/157q60.png)

Edit: img tags + fullscreenshot = bad idea

Where'd ya get that pretty clock? :)

---

### Post by jokermatt999 on 2008-06-19
Oh, I already know how to set the size of a graph, what I wanted was the *scale* parameter. It makes the graph treat the number passed to it as the maximum. So if the scale for the downspeed_graph was 30, the graph would reach the top when it was 30kps or above. I want to set the scale of the upspeed to the downspeed, so the graphs will be proportional.

As for the clock, I believe I got it from the screenlets app. It's definitely my favorite clock app I've seen.

---

### Post by cl0ckwork on 2008-06-19
> **jokermatt999 said:**
> Oh, I already know how to set the size of a graph, what I wanted was the *scale* parameter. It makes the graph treat the number passed to it as the maximum. So if the scale for the downspeed_graph was 30, the graph would reach the top when it was 30kps or above. I want to set the scale of the upspeed to the downspeed, so the graphs will be proportional.

As for the clock, I believe I got it from the screenlets app. It's definitely my favorite clock app I've seen.

ah :oops: i was looking into that a while ago.
but then i jsut gave up the graph all together :)

---

### Post by jokermatt999 on 2008-06-19
In the end, I just said screw it, and set the scale to both bars as 80. It doesn't have quite the effect I wanted, but I do like how I combined both bars into one.
I improved on the song bar code as well; it no longer gives an error when switching songs.

new graph code below:

${color black}${downspeedgraph wlan0 0000FF 0000FF 80}
${voffset -35}${color black}${upspeedgraph wlan0 FF0000 FF0000 80}

[http://tinypic.com/view.php?pic=1zlrr6b&s=3](http://tinypic.com/view.php?pic=1zlrr6b&s=3)

Edit: I've now made a script that uses Amarok's similarArtist function, checks if the suggestion is in my collection already (or a text file), and if not, adds them to a text file. Basically, its a music suggestions mine. :D

---

### Post by geezerone on 2008-06-24
> **Rexbron! said:**
> Once again, thank you for writing this great tutorial.

My problem is this, the network traffic monitor does not monitor anything and it never changes. I have had this problem with other system montitors (for karamba). Is there a package that I need to install before this will work?...

Nice program but same for me. Also transparancy doesn't work too.

---

### Post by Th3Professor on 2008-06-24
i still get a flicker when conky does the refresh (every minute or couple minutes or something). . . i tried previous steps in removing the flicker but they don't work. so i removed conky. well, not deinstall... just stopped using it. bummer really, it's a pretty neat app. i wonder if torsmo works on this distro, tried it once before but had no luck with it.

---

### Post by cl0ckwork on 2008-06-24
> **geezerone said:**
> Nice program but same for me. Also transparancy doesn't work too.

are you using KDE?

---

### Post by geezerone on 2008-06-24
Using Gnome.

---

### Post by kaivalagi on 2008-06-24
Hi All,

I thought this was a good place to make mention my post, and get some feedback.

I have created a Google Calendar python script specifically for Conky, which uses the gdata api rather than the cli app talked about here. I've done this on the premise that it should be much more customizable than would otherwise be possible.

You can find the post here: [http://ubuntuforums.org/showthread.php?t=837385](http://ubuntuforums.org/showthread.php?t=837385)

I would appreciate some feedback on the script and any suggestions for further functionality are welcome.

Key feature are:
[LIST]
[*]Utilises the Google Calendar API.
[*]Supports the use of a template to define the layout of each event output
[*]Supports regional datetime formats, by way of system locales
[*]Optional event limit so you can reduce the total output in Conky if you have lot's of events, events should be returned earliest first (needs testing)
[/LIST]

I have already created a weather forecasting script for Conky in much the same manner, which has gone down well, and I hope the same can be the case for this one.

Cheers

---

### Post by Nullack on 2008-06-24
Ive realised a strange issue. While compiling a program my cpu utilusation expectedly hit 100%, but my cpu top only showed a fraction in conky. Curiously so did top in the command line.

None of the processes add up to 100%, and its not by a little, but by a huge amount.

Whats going on here??? :confused:

---

### Post by kaivalagi on 2008-06-24
> **Nullack said:**
> Ive realised a strange issue. While compiling a program my cpu utilusation expectedly hit 100%, but my cpu top only showed a fraction in conky. Curiously so did top in the command line.

None of the processes add up to 100%, and its not by a little, but by a huge amount.

Whats going on here??? :confused:

Could it be an averaging thing? I know Conky can average out the CPU utilisation calculation, so if you have peaks and troughs, you'll see a lower %....

Just a guess....quite strange

---

### Post by Nullack on 2008-06-25
Ive attached an archived screenshot showing the problem. Also my conkyrc. This is truly bizzare!

---

### Post by kaivalagi on 2008-06-25
> **Nullack said:**
> Ive attached an archived screenshot showing the problem. Also my conkyrc. This is truly bizzare!

Your conkyrc does include the cpu averaging option. The option is describde in the conky documentation as "cpu_avg_samples - The number of samples to average for CPU monitoring"

Try adding the following to see if things change:

```
# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

```

---

### Post by Nullack on 2008-06-25
There is something seriously wrong here. Ive now moved into top to better diagnose this problem as Conky behaves the same as top.

Simple test, compile something that takes awhile and see the user cpu load hit say 93% and the system cpu load ar 7%. In this condition I only see top show user processes of about 30% not 93%!

This is a default top run with no command line switches. I even confirmed that top is doing the default of sorting by cpu % - sort option K.

:confused::confused::confused::confused:

---

### Post by jjgomera on 2008-06-25
> Simple test, compile something that takes awhile and see the user cpu load hit say 93% and the system cpu load ar 7%. In this condition I only see top show user processes of about 30% not 93%!maybe this is the reason, can you trace while you are compiling top in a terminal and sudo top in another terminal?

i think conky only show user process, maybe compiling is root process

---

### Post by Nullack on 2008-06-25
I launched make from my account not root though????

---

### Post by cl0ckwork on 2008-06-25
heres my setup as of now, i will probably change it by next week

sys. info. (bottom left)
```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 250 5
maximum_width

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black
color1 white #00FF00
color2 white #EEAA00
color3 white #9933FF

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 40

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
none

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#  Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               



# blue color ${color 246eb5}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font zekton:size=14} ${time %I:%M:%S}${font} ${goto 120}${font zekton:size=8}${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59} ${goto 360}CPU Temp: ${color orange}${acpitempf}°F${color}${font} ${goto 480} Quality: ${color 78e6e4}$alignr${wireless_link_qual_perc wlan0} %${color}
${time %B %e, %G} ${goto 120}${color1}CPU1: ${cpu cpu1}% ${freq_g} GHz ${goto 240}${color2}CPU2: ${cpu cpu2}% ${freq_g} GHz ${goto 360}${color3}RAM: $memperc%  ${mem} ${color}${goto 480} Down:${color green}$alignr${downspeedf wlan0} Kb/s$color
Uptime: $uptime   ${goto 120}${color1}${cpubar cpu1 5,110} ${goto 240}${color2}${cpubar cpu2 5,110} ${goto 360}${color3}${membar 5,110} ${color}${goto 480} Up:   ${color red}$alignr${upspeedf wlan0} Kb/s$color
${voffset 3}
${exec feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```

amarok, top right
```
TEXT
${color3}Artist: ${color}$alignr${if_empty execi 10 dcop amarok player artist}$alignc Music Stopped $else${execi 10 dcop amarok player artist}$endif
${voffset 3}${color3}Title: ${color}$alignr${execi 10 dcop amarok player title}
${voffset 3}${color3}Time: ${color}$alignr${execi 1 dcop amarok player currentTime} / ${execi 10 dcop amarok player totalTime} 
${voffset 3}${color3}Album: ${color}$alignr${execi 10 dcop amarok player album}$endif${font }
${color3}${hr 2}$color
```

---

### Post by geezerone on 2008-07-01
> **davethomas691 said:**
> Hey all, I've had a look around to see if anyone else has had this problem and I haven't found anything like it yet.  When I run Conky, the pseudo transparency is off.  It appears as though it took the background from a few pixels off in each direction and set that as the Conky background.  Check out the screenshot.  The problem is easiest to see at the top near the System and CPU sections

Here is my .conkyrc

```

background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.3
total_run_times 0
own_window yes
own_window_type desktop
own_window_transparent yes
**own_window_type override**
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 0
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT




${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/storage} / ${fs_size /media/storage}
${fs_bar 4 /media/storage}

NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 24,128} ${alignr}${upspeedgraph eth0 24,128}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

WEATHER${hr 1}${color}

${color}Location: ${color ffffff}Orlando, FL$color

${color #B3B3B3}${execi 3600 python /home/davidthomas/.scripts/conkyForecast.py --location=32816 --imperial --template=/home/davidthomas/.scripts/conkyForecast2.template}
${alignr}${voffset -130}${offset -70}${font weather:size=45}${color}${execi 3600 python ~/.scripts/conkyForecast.py --location=32816 --startday=0 --datatype=WF}$font$color
${alignr}${voffset 5}${offset -70}${font weather:size=45}${color}${execi 3600 python ~/.scripts/conkyForecast.py --location=32816 --startday=0 -n --datatype=WF}$font$color


${voffset 7}${color}3 day forecast
${voffset 7}${color}${offset 12}${execi 3600 python ~/.scripts/conkyForecast.py -w --location=32816 --startday=1 --endday=3 --datatype=DW --spaces=27}
${font weather:size=44}${color}${offset 12}${execi 3600 python ~/.scripts/conkyForecast.py --location=32816 --startday=1 --endday=3 --datatype=WF} $font$color
${color e0e0e0}${execi 3600 python /home/davidthomas/.scripts/conkyForecast.py --location=32816 --imperial --spaces=27 --template=/home/davidthomas/.scripts/conkyForecast.template}
```Any help would be greatly appreciated.

good config.

I tried this but when I click on it or the desktop background the_ conky data vanishes_ and keep having to restart conky. this also happens if other windows max and min over it?? Any ideas why?

Fixed: **own_window_type override**

---

### Post by Th3Professor on 2008-07-01
so... how do you get rid of the flicker?
every minute or couple/few minutes there's a flicker.
this occurs even when a video is playing at fullscreen.

---

### Post by cl0ckwork on 2008-07-01
> **Th3Professor said:**
> so... how do you get rid of the flicker?
every minute or couple/few minutes there's a flicker.
this occurs even when a video is playing at fullscreen.

what ive seen with mine, even after enabling double_buffer and what not, is when the size of the drawn conky window changes.

for example, if you have a variable that changes from single digit to double digit (5 to 10) and it forces conky to get wider depending on your set up

that is when i have noticed it flickers for me. i have added some spaces and offsets now so that my setup is wide enough that it doesnt push the edges any further.

its kind of confusing, if you need any clarity just ask

---

### Post by Th3Professor on 2008-07-01
> **cl0ckwork said:**
> what ive seen with mine, even after enabling double_buffer and what not, is when the size of the drawn conky window changes.

for example, if you have a variable that changes from single digit to double digit (5 to 10) and it forces conky to get wider depending on your set up

that is when i have noticed it flickers for me. i have added some spaces and offsets now so that my setup is wide enough that it doesnt push the edges any further.

its kind of confusing, if you need any clarity just ask

Could you please? Also a reminder on the double_buffer would be great... I just got rid of conky due to the flicker, so I'll need to start from scratch with the config. I used the double_buffer before, though it didn't help - I'd like to still use it this time around. Otherwise, the variables changed from 1-digit to 2-digits, some clarification on that might help. Thanks! :)

---

### Post by jjgomera on 2008-07-01
> **cl0ckwork said:**
> what ive seen with mine, even after enabling double_buffer and what not, is when the size of the drawn conky window changes.

for example, if you have a variable that changes from single digit to double digit (5 to 10) and it forces conky to get wider depending on your set up

that is when i have noticed it flickers for me. i have added some spaces and offsets now so that my setup is wide enough that it doesnt push the edges any further.

its kind of confusing, if you need any clarity just ask

You can use ${tab} or ${goto} to adjust this dont fix spaces, for example:

```
cpu: ${cpugraph 11,40 738A88 738A88} ${offset -25}${color FCFCFC}${cpu}${color}${tab}${tab}${tab}ram: ${memgraph 11,40 738A88 738A88} ${offset -25}${color FCFCFC}${memperc}${color}${tab}${tab}${tab}io: ${diskiograph 11,40 738A88 738A88}${tab}${tab}${tab}${tab}${color}${font Arrows:size=8}N$font ${color FCFCFC}${downspeed eth0}${color}${offset -5}kb/s ${downspeedgraph eth0 11,50 738A88 738A88 300}${tab}${tab}${color}${font Arrows:size=8}S$font ${color FCFCFC}${upspeed eth0}${color}${offset -5}kb/s ${upspeedgraph eth0 11,50 738A88 738A88 30}${tab}${tab}${tab}${color FCFCFC}${font Trebuchet MS:size=8}${time %a, %d de %b %H:%M}
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75970&d=1214945399[/IMG]

All spaces are fix, it dont depend the number of number :guitar:

About double buffer, it must add to xorg.conf too this line in
Section "Module":
	Load		"dbe"

---

### Post by cl0ckwork on 2008-07-01
> **Th3Professor said:**
> Could you please? Also a reminder on the double_buffer would be great... I just got rid of conky due to the flicker, so I'll need to start from scratch with the config. I used the double_buffer before, though it didn't help - I'd like to still use it this time around. Otherwise, the variables changed from 1-digit to 2-digits, some clarification on that might help. Thanks! :)

for the options in the beginning set,
double_buffer yes

own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

that should solve a few or your problems but theres more system specific stuff to figure out also

ok. on with the reason of the post.
say you have a setting for a music player and song1 is playing.
the minimum width for conky is set at 200 pixels wide and the title "song1" fits without making the embeded window of conky and wider.
now say the next song is called "really really long title" and because teh title is so long, it makes conky wider that the previous 200 pixels, and thats when it flickers.
now if it is set up with something that updates frequently (instead of a song) and changes size, the flicker is very noticeable.

i have been fiddling with my setup and arranged it so that it wont push the edges any further when something changes size and that solved my flicker problem.
once you get your code working, if you need help setting it up so it wont move at all i would be happy to help

---

### Post by MantinoX on 2008-07-03
.

---

### Post by chepioq on 2008-07-07
Hello
First excuse my bad English...
I test kde-4 and I have problem with transparency.
With kde.3 I make a scrip with:
"feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`"
And that work, but with kde.4 that don't work.
I think that in kde.4 dcop is replaced by dbus, and also kdesktop by plasma...
Any ideas?...
Thank.

---

### Post by chepioq on 2008-07-11
hello...
With Crinos512 we have solution...
See this post: 
[http://ubuntuforums.org/showthread.php?t=228731&page=5]("http://ubuntuforums.org/showthread.php?t=228731&page=5")

---

### Post by M4rotku on 2008-07-14
Hello all,

Since I'm running Hardy and it seemed like this guide was written for older versions, I downloaded the newest 1.5.1 version.  When I ran the code that was specified:

> joey@joey-laptop:~/conky-1.5.1$ ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe


I got the following error near the end:

> checking for X... no
configure: error: Can't locate your X11 installation


How would I go about fixing this and is it still possible to use the older version if the newer version is what is causing the problem?

---

### Post by imjscn on 2008-07-14
> **seldon77 said:**
> 

5. Add dbe module to /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```
find the section titled Section "Module", and add
```

        Load    "dbe"

```

6. Go to System, Preferences, Sessions, Startup Programs and add 'conky' to the list of start up progams. Reboot. Conky will be active after your next reboot!


Need some help:
in my xorg.conf, there isn't a section "Module", what to do?
in my Application/System, there isn't a "Preferences" , what to do?

I'm in Xubuntu8.04

Thanks!

---

### Post by cl0ckwork on 2008-07-15
> **M4rotku said:**
> Hello all,

Since I'm running Hardy and it seemed like this guide was written for older versions, I downloaded the newest 1.5.1 version.  When I ran the code that was specified:



I got the following error near the end:



How would I go about fixing this and is it still possible to use the older version if the newer version is what is causing the problem?

im guessing you installed and compiled the package yourself.
try using the repositories and installing that way.

---

### Post by jjgomera on 2008-07-15
> **imjscn said:**
> Need some help:
in my xorg.conf, there isn't a section "Module", what to do?
in my Application/System, there isn't a "Preferences" , what to do?

I'm in Xubuntu8.04

Thanks!

if module section isnt it, add it:

```
Section "Module"
	Load		"dbe"
EndSection
```

About Application/System/Preferences, is about gnome (ubuntu), you must do it with xfce, look [here]("http://gentoo-wiki.com/HOWTO_Autostart_Programs#Xfce4")

---

### Post by imjscn on 2008-07-15
jjgomera, thanks for helping. Another question:
Should I do both Add module and Add Autostart for most apps that I want to run at start, or it's just Conky need both?

---

### Post by jjgomera on 2008-07-16
no, to modify xorg.conf **only** for conky, to autostart each apps, it only necesary add in Xfce4 menu > Settings > Xfce 4 Autostarted Applications.

---

### Post by imjscn on 2008-07-16
Thanks a lot, I'm on the fly :)

---

### Post by gardara on 2008-07-22
My conky currently shows cpu load, ram load, hdd space, etc. but is there any way of letting it show hdd load? Not how much space I'm using but how much strain is on the hdd?

---

### Post by Bruce M. on 2008-07-22
Hi Folks,

In most of the conky threads there are instructions for people trying to setup conky for the first time. Bu the time it's answered it's spaced out over a few pages and the simplicity of it seems to be lost.

So with that in mind I've started a new thread:

[HOW TO: A Beginners Guide to Setting up Conky]("http://ubuntuforums.org/showthread.php?p=5436679#post5436679")

And like I said there, I'm really hoping it stays a "1 post" thread, it doesn't talk about configuring the internal workings of conky. Simply a way to get it up and running. Leave configuring tips and tricks and screenshots here where there is lots of help.

Take a look.

Have a nice day
Bruce

---

### Post by Jean__ on 2008-08-27
Hi folks,

I have conky running on two machines, an old machine running hardy server with a bare xfce and a newer running hardy kubuntu.

On the faster machine though, the calls to tcp_portmon for *outbound* connections make conky very slow in updating.

As soon as I add only 1 outbound connection like:

${tcp_portmon 32768 61000 rhost 0} 

conky only comes up after 5 seconds and can only update once in 5 seconds, though the polling interval is set to 1.

It's only the call to tcp_portmon with rhost which slows it down, the call to  ${tcp_portmon 32768 61000 rservice 0} is working well.
Replacing rhost with rip works well too, so it seems the problem is in the dns lookup.

Any idea's?

Thanks.

---

### Post by m_l17 on 2008-09-24
Here is my .conkyrc with colors to match Linux Mint:

```
### my conky setup for t21 ###

# LINUX MINT - CONKY
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

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
#minimum_size 250 5

# Maximum Width
maximum_width 295

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font sans
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 5

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 15

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color A2E062}Linux Mint ${hr 2}$color
$nodename $sysname $kernel on $machine

${color A2E062}Uptime ${hr 2}$color 
${uptime}

${color A2E062}Intel Mobile Pentium III ${hr 2}$color
${freq}MHz $alignr ${cpu cpu1}%  Load ${loadavg}   Temp ${acpitemp}
${cpubar cpu0}
${cpugraph 000000 A2E062}
Processes $processes
Running $running_processes

NAME             PID      CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color A2E062}Memory ${hr 2}$color
Mem $alignc $memperc%    $mem / $memmax
${membar 6}$color
Swap $alignc   $swapperc%    $swap / $swapmax  
${swapbar 6}$color

${color A2E062}Hdd ${hr 2}$color
/ $alignc ${fs_free_perc /}%    ${fs_used /}/ ${fs_size /}
${fs_bar 6 /}$color
/home $alignc ${fs_free_perc /home}%    ${fs_used /home}/ ${fs_size /home}
${fs_bar 6 /home}$color

${color A2E062}Network ${hr 2}$color
eth0's IP  ${addr eth0}$color

Public IP  ${execi 3600 wget -O - http://whatismyip.org/ | tail}$color

Down $color${downspeed eth0}k/s            Up ${upspeed eth0}k/s
${downspeedgraph eth0 25,140 000000 A2E062}$color ${alignr}${upspeedgraph eth0 
25,140 000000 A2E062}$color
Total ${totaldown eth0}          Total ${totalup eth0}
${color A2E062}${hr 2}$color
```

Thanks to this thread and [http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/")

---

### Post by dustint83 on 2008-10-09
heres my conky setup, quite nice i must say!

---

### Post by reg4c on 2008-10-15
> **seldon77 said:**
> 
Then (Compiz users) place a startup script called .conky_start.sh in your home directory:
```
#!/bin/bash
sleep 60 && conky;
```
This would start conky after 60 seconds of your login. That way, compiz doesn't draw shadows around conky. Make sure the script is executable: ```
chmod a+x .conky_start.sh
``` and add it to your startup programs (menu: system->preferences->session->startup programs). 


Urm, you don't need a script for this.
You can just add "conky" to the session and then go to CCSM > Decorations
and then in the Shadow windows box add !(iclass=conky)

I found that on Compiz forums but I cannot find the link now O_o
Cheers

---

### Post by Green_Star on 2008-10-20
Hello,

My conky setup is working well except one thing. It supposed to be placed left-bottom of my screen but it is almost middle of left side, I guess there is an empty space at the end of my screen, i am not sure how to get rid of that, my script looks fine. I you guys can point me what I need to change that would be great, I love to have conky at my left-bottom of the screen. 

```
# UBUNTU-CONKY.
text_buffer_size 256
# Update interval in seconds
update_interval 3.0
font freesans:size=12
xftfont freesans:size=12
use_xft yes
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override #try also 'normal' or 'desktop' 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 492 8
maximum_width 492

draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0.9
xftfont Candera:size=6
uppercase no
override_utf8_locale yes
use_spacer no

stippled_borders 3
border_margin 9
border_width 10

# Gap between borders of screen and text
gap_x 10
gap_y 0

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color1 orange

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# stuff after 'TEXT' will be formatted on screen
#${cpugraph 000000 ffffff}${color blue}   ${execi 60 python /home/suma/.scripts/recordingdevices.py;}
#${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
color1 blue
color2 white
color3 red
color4
TEXT
${color 2e2e2e}${cpugraph 110,320}
${voffset -128}

${font Zekton:style=Bold:pixelsize=12}
${color3}SUMA EMPIRE $alignr$sysname $kernel on $machine

${color1}CPU Temparature ${color3}${execi 4 sensors | grep ° | cut -c 15-16 ;}C $alignr${color1}Uptime: ${color1}$uptime
${freq}MHz ${color1} $alignr Load: ${color1}${loadavg}
${color1}$cpubar

Processes: ${color1}$processes  Running: $running_processes $alignr Mythtv: ${color red}${execi 60 python /home/suma/.scripts/recordingdevices.py;}${color1}

${top name 1}$alignr${offset -155}${top cpu 1} ${color grey}| 
${color blue}${voffset -15}${offset 165}${top_mem name 1}$alignr${top_mem mem 1}
${top name 2}$alignr${offset -155}${top cpu 2} ${color grey}| 
${color blue}${voffset -15}${offset 165}${top_mem name 2}$alignr${top_mem mem 2}
${top name 3}$alignr${offset -155}${top cpu 3} ${color grey}| 
${color blue}${voffset -15}${offset 165}${top_mem name 3}$alignr${top_mem mem 3}
${top name 4}$alignr${offset -155}${top cpu 4} ${color grey}| 
${color blue}${voffset -15}${offset 165}${top_mem name 4}$alignr${top_mem mem 4}
${top name 5}$alignr${offset -155}${top cpu 5} ${color grey}| 
${color blue}${voffset -15}${offset 165}${top_mem name 5}$alignr${top_mem mem 5}
${top name 6}$alignr${offset -155}${top cpu 6} ${color grey}| 
${color blue}${voffset -15}${offset 165}${top_mem name 6}$alignr${top_mem mem 6}

ram $alignr${offset -253}:
${voffset -15}$alignr${offset -215}$memperc% ${membar 6}
swap $alignr${offset -253}:
${voffset -15}$alignr${offset -215}$swapperc% ${swapbar 6}

root $alignr${offset -253}:
${voffset -15}$alignr${offset -215}${fs_free_perc /}% ${fs_bar 6 /}
main $alignr${offset -253}:
${voffset -15}$alignr${offset -215}${fs_free_perc /storage/main}% ${fs_bar 6 /storage/main}
backup $alignr${offset -253}:
${voffset -15}$alignr${offset -215}${fs_free_perc /storage/backup}% ${fs_bar 6 /storage/backup}
extra $alignr${offset -253}:
${voffset -15}$alignr${offset -215}${fs_free_perc /storage/extra}% ${fs_bar 6 /storage/extra}

Down : ${color green}${downspeed eth0}${color blue} k/s ${alignr}Up: ${color green}${upspeed eth0}${color blue} k/s
Total  :${color red} ${totaldown eth0} ${alignr}${color blue}Total: ${color red}${totalup eth0}${color blue}
In / Out bound: ${color green}${tcp_portmon 1 32767 count} / ${tcp_portmon 32768 61000 count}${alignr}${color blue}Total: ${tcp_portmon 1 65535 count}
${color red}${voffset -30}${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}
```

---

### Post by Bruce M. on 2008-10-20
> **Green_Star said:**
> Hello,

My conky setup is working well except one thing. It supposed to be placed left-bottom of my screen but it is almost middle of left side, I guess there is an empty space at the end of my screen, i am not sure how to get rid of that, my script looks fine. I you guys can point me what I need to change that would be great, I love to have conky at my left-bottom of the screen.

You'll need to play with the **gap_y** command:

```
gap_x 10
gap_y -200 # a negative value brings conky DOWN, positive UP

```

Hope that helps.
Bruce

---

### Post by Bruce M. on 2008-10-20
And once again I changed mine.  I decided I didn't really need other's weather, so I made changes to my weather and where my conky's are located.

[CENTER][[IMG]http://img528.imageshack.us/img528/392/20oct08et8.th.gif[/IMG]](http://img528.imageshack.us/my.php?image=20oct08et8.gif)[/CENTER]

Will be posting the code in [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showpost.php?p=6001621&postcount=692")

Chimo!
Bruce

---

### Post by Green_Star on 2008-10-21
That worked well, thank you so much. By the way can I see your calender conky script?

> **Bruce M. said:**
> You'll need to play with the **gap_y** command:

```
gap_x 10
gap_y -200 # a negative value brings conky DOWN, positive UP

```

Hope that helps.
Bruce

---

### Post by Bruce M. on 2008-10-21
> **Green_Star said:**
> That worked well, thank you so much. By the way can I see your calender conky script?

Sure no problem:
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 2.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 yellow
color8 lightblue
color9 red
alignment tr  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y 35
text_buffer_size 512 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2
# Timezone information found in: /usr/share/zoneinfo


TEXT
${font Zekton:bold:size=12}${color4}${alignc}UTC:$color ${utime %H:%M}
${font Zekton:bold:size=9}${color8}Man: $color${tztime Canada/Central %H:%M}${alignr 2}${color8}Ont: $color${tztime Canada/Eastern %H:%M}$font
${color0}${hr}
${goto 70}${font Zekton:bold:size=9}${color1}Buenos Aires, Argentina$color
${goto 70}${color4}34°20' S            58°30' W$color$font
${font Zekton:size=55}${time %H:%M}$font
${voffset -63}${font Zekton:size=20}${color1}${alignr 5}${time %b}$color$font
${font Zekton:size=20}${color1}${alignr 5}${time %y}$color$font
${color0}${hr 1}$color
${font LCDMono:size=19}${color2}${execi 60 ~/Conky/scripts/calendario.sh semana}
${color 888888}${execi 60 ~/Conky/scripts/calendario.sh pasado}${color red}${execi 60 ~/Conky/scripts/calendario.sh hoy}${color 888888}${execi 60 ~/Conky/scripts/calendario.sh futuro}$font

${color4}${font Bitstream Vera Sans Mono:size=7}${pre_exec cal -3 | cut -c23-44 --complement}
```
**calendario.sh**
```
#! /bin/sh
# written by: jjgomera

#str=`echo '\033[01;32m29'`

# replace the 4 "cal |" with "cal -m |" to have the week start on Monday

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
mes)
cal | head -n1
;;
semana)
cal | head -n2 | tail -n1
;;
pasado)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
hoy)
echo $DATE;
;;
futuro)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac
```
Enjoy!

Chimo!
Bruce

---

### Post by Green_Star on 2008-10-22
Thanks for your help, by the way when I tried the calender part the first two lines of dates are not aliened properly, please check my screenshot, can you suggest anything in this? By the way how do you get that ubuntu logo on the top of your conky display?


> **Bruce M. said:**
> Sure no problem:
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 2.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 yellow
color8 lightblue
color9 red
alignment tr  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y 35
text_buffer_size 512 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2
# Timezone information found in: /usr/share/zoneinfo


TEXT
${font Zekton:bold:size=12}${color4}${alignc}UTC:$color ${utime %H:%M}
${font Zekton:bold:size=9}${color8}Man: $color${tztime Canada/Central %H:%M}${alignr 2}${color8}Ont: $color${tztime Canada/Eastern %H:%M}$font
${color0}${hr}
${goto 70}${font Zekton:bold:size=9}${color1}Buenos Aires, Argentina$color
${goto 70}${color4}34°20' S            58°30' W$color$font
${font Zekton:size=55}${time %H:%M}$font
${voffset -63}${font Zekton:size=20}${color1}${alignr 5}${time %b}$color$font
${font Zekton:size=20}${color1}${alignr 5}${time %y}$color$font
${color0}${hr 1}$color
${font LCDMono:size=19}${color2}${execi 60 ~/Conky/scripts/calendario.sh semana}
${color 888888}${execi 60 ~/Conky/scripts/calendario.sh pasado}${color red}${execi 60 ~/Conky/scripts/calendario.sh hoy}${color 888888}${execi 60 ~/Conky/scripts/calendario.sh futuro}$font

${color4}${font Bitstream Vera Sans Mono:size=7}${pre_exec cal -3 | cut -c23-44 --complement}
```
**calendario.sh**
```
#! /bin/sh
# written by: jjgomera

#str=`echo '\033[01;32m29'`

# replace the 4 "cal |" with "cal -m |" to have the week start on Monday

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
mes)
cal | head -n1
;;
semana)
cal | head -n2 | tail -n1
;;
pasado)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
hoy)
echo $DATE;
;;
futuro)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac
```
Enjoy!

Chimo!
Bruce

---

### Post by Bruce M. on 2008-10-22
> **Green_Star said:**
> Thanks for your help, by the way when I tried the calender part the first two lines of dates are not aliened properly, please check my screenshot, can you suggest anything in this? By the way how do you get that ubuntu logo on the top of your conky display?

The calendar ***_"requires"_*** a *mono font*

Ubuntu = the letter "v" from the [OpenLogos font]("http://www.dafont.com/search.php?psize=m&q=OpenLogos")
```
${voffset -45}${color1}${font OpenLogos:size=150}v$font$color
```

---

### Post by Green_Star on 2008-10-22
Got it, so its all because of the font. And printing the logos using font is new thing to me. Thanks.

---

### Post by Bruce M. on 2008-10-22
> **Green_Star said:**
> Got it, so its all because of the font. And printing the logos using font is new thing to me. Thanks.

Remember:

1. if spacing is critical - try mono fonts
2. images are not allowed: however, pop a cloud, sun, moon, logo or what ever into a font and that's a different story.  :)

Have a good day.
Bruce

---

### Post by Farmer of Bricks on 2008-10-25
I'm running KDE 4.1.1, Conky from the repos, and a 5.0 second refresh time. The Conky blinks frequently, and occasionally disappears in its entirety.

[INDENT]#own_window yes
own_window_type override
own_window_transparent yes
#own_window_colour 000000
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer no[/INDENT]

I'm also having problems with pymetar, which is configured correctly, but the text gets cut off in Conky. 

Does anyone have any suggestions? My ~.conkyrc is below:

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
#own_window yes
own_window_type override
own_window_transparent yes
#own_window_colour 000000
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# fiddle with window
use_spacer none
use_xft no

# Update interval in seconds
update_interval 5.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Outline Text?
draw_outline no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen


# Stuff removed from after 'TEXT'
# ${color orange}LOGGING ${hr 2}$color
# ${execi 30 tail -n3 /var/log/messages | fold -w50}

# $sysname $kernel on $machine
# $color$stippled_hr

TEXT
${color orange}SYSTEM ${hr 2}$color
 $nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
 ${color white}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}$color
 ${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
 ${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
 ${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 ${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}

${color orange}MEMORY / DISK ${hr 2}$color
 RAM:   $memperc%   ${membar 6}$color
 Swap:  $swapperc%   ${swapbar 6}$color

 Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
 home:  ${fs_free_perc /home/}%   ${fs_bar 6 /home}$color


${color orange}NETWORK (${addr wlan0}) ${hr 2}$color
 Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
 ${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
 25,140 000000 00ff00}$color
 Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
 Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}FORTUNE ${hr 2}$color
 ${execi 360 fortune -s | fold -w50}

${color orange}WEATHER ${hr 2}$color
 ${execi 60 /usr/bin/pymetar KIAD | fold -w50} 
```

---

### Post by cl0ckwork on 2008-10-25
> **Farmer of Bricks said:**
> I'm running KDE 4.1.1, Conky from the repos, and a 5.0 second refresh time. The Conky blinks frequently, and occasionally disappears in its entirety.

[INDENT]#own_window yes
own_window_type override
own_window_transparent yes
#own_window_colour 000000
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer no[/INDENT]

I'm also having problems with pymetar, which is configured correctly, but the text gets cut off in Conky. 

Does anyone have any suggestions? My ~.conkyrc is below:

the flicker is probably from different variables changing the sapcing in conky.

try setting a maximum_width variable in the top half to about 200 for starters

---

### Post by Farmer of Bricks on 2008-10-25
> **cl0ckwork said:**
> the flicker is probably from different variables changing the sapcing in conky.

try setting a maximum_width variable in the top half to about 200 for starters

The flicker is still there, but less pronounced, and pymetar is still cut off. 

Thanks anyways

---

### Post by Bruce M. on 2008-10-26
> **Farmer of Bricks said:**
> The flicker is still there, but less pronounced, and pymetar is still cut off. 

Thanks anyways

Try this it worked for me:

For every ${alignr} you have change it to ${alignr 2}

Chimo!
Bruce

---

### Post by RayVad on 2008-10-26
Is there someone who got all his voltage sensor working in Conky?

This is what i have:

VCore1: ${alignr}${hwmon 0 in 0} V
VCore2: ${alignr}${hwmon 0 in 1} V
+3.3V: ${alignr}${hwmon 0 in 2} V
+5V: ${alignr}${hwmon 0 in 3} V
+12V: ${alignr}${hwmon 0 in 4} V

But only the first 3 are giving the right value.
The +5 and +12 are giving only the value 3.0 V. Although these sensors are giving correct outputs in Gkrellm.

My sensors are in: /sys/class/hwmon/hwmon0/device

cpu0_vid    fan3_input  in2_input  in5_input  pwm1            temp3_input
driver      fan3_min    in2_max    in5_max    pwm1_enable     temp3_max
fan1_div    hwmon       in2_min    in5_min    subsystem       temp3_max_hyst
fan1_input  in0_input   in3_input  in6_input  temp1_input     temp4_input
fan1_min    in0_max     in3_max    in6_max    temp1_max       temp4_max
fan2_div    in0_min     in3_min    in6_min    temp1_max_hyst  temp4_max_hyst
fan2_input  in1_input   in4_input  modalias   temp2_input     uevent
fan2_min    in1_max     in4_max    name       temp2_max       vrm


asb100-i2c-0-2d
Adapter: SMBus I801 adapter at e800
VCore 1:          +1.58 V  (min =  +1.20 V, max =  +1.81 V)
+3.3V:            +3.26 V  (min =  +2.96 V, max =  +3.63 V)
+5V:              +5.00 V  (min =  +4.49 V, max =  +5.51 V)
+12V:            +11.31 V  (min =  +9.55 V, max = +14.41 V)
-12V (reserved): -11.81 V  (min =  -0.00 V, max =  -0.00 V)
-5V (reserved):   -4.96 V  (min =  -0.00 V, max =  -0.00 V)
CPU Fan:         2518 RPM  (min = 2481 RPM, div = 4)
Chassis Fan:        0 RPM  (min = 4963 RPM, div = 2)
Power Fan:          0 RPM  (min =   -1 RPM, div = 8)
M/B Temp:         +28.0°C  (high = +80.0°C, hyst = +75.0°C)  
CPU Temp (Intel): +43.0°C  (high = +100.0°C, hyst = +90.0°C)  
Power Temp:        -0.5°C  (high = +60.0°C, hyst = +50.0°C)  
CPU Temp (AMD):   +25.0°C  (high = +80.0°C, hyst = +75.0°C)  
cpu0_vid:        +1.425 V



Any ideas how to get the right values?

---

### Post by Farmer of Bricks on 2008-10-29
I fixed the pymetar cutoff with the following:
```
# Minimum size of text area
# minimum_size 250 5
text_buffer_size 600

```
However, the blink is still very annnnoying, and I don't wnat to have to make the refresh rate any longer than 5 secs. Any help for KDE4?

Thanks.

---

### Post by cl0ckwork on 2008-10-29
> **Farmer of Bricks said:**
> I fixed the pymetar cutoff with the following:
```
# Minimum size of text area
# minimum_size 250 5
text_buffer_size 600

```
However, the blink is still very annnnoying, and I don't wnat to have to make the refresh rate any longer than 5 secs. Any help for KDE4?

Thanks.
try adding this at the end

```
${texeci 1000 feh --bg-scale "`grep 'wallpaper=' ~/.kde/share/config/plasma-appletsrc | tail --bytes=+11`"}
```

---

### Post by Farmer of Bricks on 2008-10-30
> **cl0ckwork said:**
> try adding this at the end

```
${texeci 1000 feh --bg-scale "`grep 'wallpaper=' ~/.kde/share/config/plasma-appletsrc | tail --bytes=+11`"}
```

I did, returned a 'conky: feh not found', installed feh, re-ran it and got :
```

grep: /home/blk/.kde/share/config/plasma-appletsrc: No such file or directory
feh WARNING:  - File does not exist
feh ERROR: Couldn't load image in order to set bg

```

I don't know anything about feh or what it's supposed to do, so please help. Thank you.

---

### Post by Despot Despondency on 2008-11-01
OK, so I've got my conky set up as I want it but I have just one problem. When I click one of the launchers on my desktop then my conky disappears. How do I get it so that this doesn't happen? Here's my conky file

```

# Set update interval
update_interval 1
# Set it to run in the background
background yes
# Double buffering to reduce flicker
double_buffer yes
# CPU separation?
top_cpu_separate true
# Window specs
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# Use fonts
use_xft yes
# Font specs
xftfont Vibrocentric:size=12
default_color white
uppercase no
# Parameters 
maximum_width 300
alignment top_right
gap_x 5
gap_y 5
# Begin variables
TEXT
${goto 72}${color #00bfff}${font augie:size=15}${time %a, %d of %b}$font$color
${voffset -3}${alignc}${font LCDDisplayCapsSSi:size=8}${time %H:%M:%S}$font${voffset -6}

${font LCDMono:size=21}${color #00bfff}${execi 60 ~/Conky/calender.sh semana}
${color 888888}${execi 60 ~/Conky/calender.sh pasado}${color red}${execi 60 ~/Conky/calender.sh hoy}${color 888888}${execi 60 ~/Conky/calender.sh futuro}$font
${color #00bfff}${hr 1}$color

${color #00bfff}Processor & Memory${color blue}${hr 0}$color
${color gray}CPU Max:${color} $freq_dyn_g ${alignr}${color gray}CPU:$color $cpu%
$cpubar
${color gray}RAM Usage:$color $mem/$memmax -${alignr}$memperc%
$membar
${color gray}Swap Usage:$color $swap/$swapmax -${alignr}$swapperc%
$swapbar
${color gray}Root:$color ${fs_used /}/${fs_size /} - ${alignr}${fs_free_perc /}% Free
${color gray}home:$color ${fs_used /home}/${fs_size /home} - ${alignr}${fs_free_perc /home}% Free

${color 00bfff}Active Processes${color blue}${hr 0}$color
${color gray}Name  	    ${alignr}CPU  	     ${alignr}RAM$color
${top_mem name 1}     ${alignr}${top_mem cpu 1}      ${alignr}${top_mem mem 1}
${top_mem name 2}     ${alignr}${top_mem cpu 2}      ${alignr}${top_mem mem 2}
${top_mem name 3}     ${alignr}${top_mem cpu 3}      ${alignr}${top_mem mem 3}
${top_mem name 4}     ${alignr}${top_mem cpu 4}      ${alignr}${top_mem mem 4}
${top_mem name 5}     ${alignr}${top_mem cpu 5}      ${alignr}${top_mem mem 5}

${offset 0}${color 00bfff}Internet${color blue}${hr 0}$color
LAN IP $alignr ${addr eth0}
${offset 0}${color}Up: ${color }${upspeed eth0} k/s
${offset 0}${upspeedgraph eth0 20,130 000000 FF0000}
${offset 0}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 0}${downspeedgraph eth0 20,130 000000 15317E}

```

Thanks in advance

---

### Post by steveydoteu on 2008-11-01
Replace everything in your #Window Specs section with the following:

```
own_window yes
own_window_type override
own_window_transparent yes

```

---

### Post by Despot Despondency on 2008-11-01
Hi, thanks for your response. I've tried those settings before but I end up with the conky appearing above all other applications, like firefox for example. I don't want that I just want the conky on the desktop where it doesn't disappear when I click on the desktop. Any ideas?

---

### Post by steveydoteu on 2008-11-01
Those are the exact same settings I use to achieve what you are asking in my Conky setup.

---

### Post by Despot Despondency on 2008-11-01
That's what I thought. I had those settings on previous install of ubuntu and everything worked fine. Don't understand why it's acting like this now. Oh well, sure I'll get there in the end. :confused:

---

### Post by Bruce M. on 2008-11-01
> **Despot Despondency said:**
> That's what I thought. I had those settings on previous install of ubuntu and everything worked fine. Don't understand why it's acting like this now. Oh well, sure I'll get there in the end. :confused:

How about these:
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour blue
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
```
That's how all my conkys start.

CHIMO!
Bruce

---

### Post by steveydoteu on 2008-11-01
This line:

```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```Is not needed as it does nothing if window type is set to override.

```
If own_window is yes, you may use these window manager hints to affect the way Conky displays.             Notes: Use own_window_type desktop as another way to implement many of these hints implicitly.             If you use own_window_type override, window manager hints have no meaning and are ignored
```

---

### Post by Despot Despondency on 2008-11-02
I got rid of the own_window_hints line that I had in my conky and it seems to be working as it should. Cheers for the tips.

---

### Post by slinkey1981 on 2008-11-04
I am having some problems getting my conky to display my GPU clock speed and vram clock speed. 

I am using an nvidia geforce 6800 pci card.

Also, my "MediaShare" under "Storage Info" feads like a 500MiB drive, when it's a 150GiB drive, any clue as to why it's acting funky?

My conky.conf file is as follows. (I know I cheated on some of the things and just added text instead of it getting the info from my pc)

I know that the TEMPS listed have a F beside them, I have changed it to C to match the readings.

> 
alignment top_left
maximum_width 300
background yes
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
gap_x 5
gap_y 35
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer left
alignment top_right
double_buffer yes

TEXT
$alignc ${color red}Ubuntu 8.04 Hardy Heron
$alignc ${color orange}$sysname $kernel 
$alignc ${color yellow}Shifty${color yellow}@${color yellow}$nodename
${color grey}$hr
${alignc}${color orange}Hardware Info:
${color gray}$stippled_hr
${color white}CPU:$alignr ${color gray}Intel Celeron
${color grey}Frequency:$alignr ${color white}$freq
${color white}CPU: ${color #999999}${cpu}%
${color white}${cpubar 7,300}
${color #ffffff}RAM: ${color #999999}$memperc% ${color #cccccc}
${color white}${membar 7,300}
${color grey}GPU Temp:$alignr ${color white} +${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}°C
${color grey}Video RAM:$alignr ${color white} ${exec nvidia-settings -q VideoRam | grep Attribute | cut -d ' ' -f 6 | cut -c 1-6}KiB
${color grey}NVidia Driver Version:$alignr ${color white} ${exec nvidia-settings -q NvidiaDriverVersion | grep Attribute | cut -d ' ' -f 6}
${color grey}GPU Clock:$alignr ${color white} ${exec nvidia-settings -q GPUPerfModes | grep perf=0 | cut -d ' ' -f 7 | cut -c 9-11}MHz
${color grey}Video RAM Clock:$alignr ${color white} ${exec nvidia-settings -q GPUPerfModes | grep perf=0 | cut -d ' ' -f 8 | cut -c 10-12}MHz
${color grey}M/B Temperature: $alignr${color white}$acpitemp°C
${color grey}$hr
${alignc}${color orange}Storage Info:
${color grey}Home $alignr ${color white}${fs_free /}/${fs_size /} ${fs_bar 6,75 /}
${color grey}MediaShare $alignr ${color white}${fs_free /dev/sdb1}/${fs_size /dev/sdb1} ${fs_bar 6,75 /dev/sdb1}
${color grey}$hr
${alignc}${color orange}Network Info:${color grey}
${alignc}Internet IP:${color white}${exec wget -O - [http://ip.tupeux.com](http://ip.tupeux.com) | tail}
${alignc}${color gray}Local IP:${color white}${addr eth0}
${color grey}Down:${color white}${downspeed eth0}Kbps${color grey}${alignr}Up:${color white}${upspeed eth0}Kbps${color grey}
${downspeedgraph eth0 25,145 white green} ${upspeedgraph eth0 25,145 white red} ${alignr}
${color grey}$hr
${color grey}Uptime:$alignr ${color white} $uptime

${color white}Process          ${alignr -10}      ProcID ${alignr -5}         CPU%        $alignr MEM%
${color grey} ${top name 1} ${alignr 30} ${top pid 1} ${alignr 10} ${top cpu 1}   $alignr ${top mem 1} 
${color grey} ${top name 2} ${alignr 30} ${top pid 2} ${alignr 10} ${top cpu 2}   $alignr ${top mem 2} 
${color grey} ${top name 3} ${alignr 30} ${top pid 3} ${alignr 10} ${top cpu 3}   $alignr ${top mem 3} 
${color grey} ${top name 4} ${alignr 30} ${top pid 4} ${alignr 10} ${top cpu 4}   $alignr ${top mem 4} 
${color grey} ${top name 5} ${alignr 30} ${top pid 5} ${alignr 10} ${top cpu 5}   $alignr ${top mem 5} 
${color grey}$hr
${alignc}${color white}Date and Time:
${alignc}${color white}${exec /sbin/hwclock | cut -c 1-31}


Edit: I got the MediaShare drive info working by changing it from /dev/sdb1 to /mnt/MediaShare.... My mistake.

And if anyone knows of a better way to retrieve and display your REAL ip address, please share, cause mine just keeps on banging away.

---

### Post by kaivalagi on 2008-11-04
> **slinkey1981 said:**
> And if anyone knows of a better way to retrieve and display your REAL ip address, please share, cause mine just keeps on banging away.

Replace:

```
${exec wget -O - http://ip.tupeux.com | tail}
```

with:

```
${pre_exec wget -O - http://ip.tupeux.com | tail}
```

It will only be called the first time the conkyrc is processed

Hope that helps

---

### Post by slinkey1981 on 2008-11-04
> **kaivalagi said:**
> Replace:

```
${exec wget -O - http://ip.tupeux.com | tail}
```

with:

```
${pre_exec wget -O - http://ip.tupeux.com | tail}
```

It will only be called the first time the conkyrc is processed

Hope that helps

Worked perfectly, thank you!

So, without trying to sound completely obvious, the 'pre_' prefix will make the 'exec' execute only on conky startup for any command?

---

### Post by kaivalagi on 2008-11-04
> **slinkey1981 said:**
> Worked perfectly, thank you!

So, without trying to sound completely obvious, the 'pre_' prefix will make the 'exec' execute only on conky startup for any command?

Yep, that's right

Take a look at the doc pages here: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Under the variables page pre_exec is described as:

```
pre_exec 	shell command 	 Executes a shell command one time before conky displays anything and puts output as text.
```

You might want to look at the other exec options in there in case there is something else that might help you.

Chimo

---

### Post by Emily the strange on 2008-11-05
> **seldon77 said:**
> 
5. Add dbe module to /etc/X11/xorg.conf to reduce flickering.
```

sudo gedit /etc/X11/xorg.conf

```
find the section titled Section "Module", and add
```

        Load    "dbe"

```


There is no Section Module in my case. And this is the paste from file:

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"CoreKeyboard"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"si"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	InputDevice	"Generic Keyboard"
# commented out by update-manager, HAL is now used
#	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#	InputDevice	"Synaptics Touchpad"
EndSection

```

Any ideas?

Ps: I have ubuntu 8.10

---

### Post by Bruce M. on 2008-11-05
> **Emily the strange said:**
> Any ideas?

Ps: I have ubuntu 8.10

Sure .... **[COLOR="Red"]make a backup[/COLOR]** of the original **/etc/X11/xorg.conf** and add the section at the end:
```
Section "Module"
        Load    "dbe"
EndSection
```

Hope that helps.

Have a nice day.
Bruce

---

### Post by Emily the strange on 2008-11-05
I didn't make backup but I changed my xorg.conf file and it works now =]

thank you

---

### Post by Bruce M. on 2008-11-05
> **Emily the strange said:**
> I didn't make backup but I changed my xorg.conf file and it works now =]

thank you

More than welcome.

Have a nice day.
Bruce

---

### Post by Th3Professor on 2008-12-05
I'd like to display/monitor the following info with conky. Does anybody have a nice clean config that would work well with this?

Freq/temp of 4 core CPU
Freq/temp of GPU
Fan speeds of CPU, GPU, and case fans
RAM info/use
HDD info/use (4x hard drives: 1x= OS+apps, 3x= RAID+LVM set-up)
Internet DL/UL speeds and totals
top (processes/tasks, either by CPU or MEM usage, main 4 or 5 jobs)

I've seen some config files, though they don't seem to work; there's a plethora of pages in this thread, I was wondering if anybody has a config file that would work well with the above. I figure I'll have to tweak it a little bit, though am hoping there's a config that's pretty close.

Thanks. :)

EDIT:
If I could also embed a command line somewhere, that would be sweet.

---

### Post by steveydoteu on 2008-12-06
I would suggest looking through [this]("http://ubuntuforums.org/showthread.php?t=281865") and also try and learn a bit yourself rather than essentially asking someone to do all of it for you.

---

### Post by derklempner on 2008-12-07
Many thanks to the OP (can't find the thank button on the web page!), as I was able to get Conky up and running in no time flat.  The only changes I had to make were changing the font color, adding a font outline, and adding a system uptime line, all of which were simple to find in the script seldon77 provided or on the Conky website.

---

### Post by The_Real_Bacon on 2008-12-09
> **steveydoteu said:**
> I would suggest looking through [this]("http://ubuntuforums.org/showthread.php?t=281865") and also try and learn a bit yourself rather than essentially asking someone to do all of it for you.

Been looking through that and there is nothing of use. 

```
nvidia-settings -q GPUCurrentClockFreqs
```
shows current frequencies. How would I grep out the clocks?
 
*edit- I spent a while learning to grep and cut last night. I figured I'd post this now.

```
Core: ${execi 30 nvidia-settings -q GPUCurrentClockFreqs |grep [0-9] | cut -c 49-51}
Memory: ${execi 30 nvidia-settings -q GPUCurrentClockFreqs |grep [0-9] | cut -c 53-55}
```

---

### Post by Th3Professor on 2008-12-09
I agree... and reading 80 pages? lol ;)

---

### Post by Bruce M. on 2008-12-10
> **Th3Professor said:**
> I agree... and reading 80 pages? lol ;)

80 is better than 497 pages found -> [here]("http://ubuntuforums.org/showthread.php?t=281865").  :)

Have a nice day reading.
Bruce

---

### Post by Th3Professor on 2008-12-10
> **Bruce M. said:**
> 80 is better than 497 pages found -> [here]("http://ubuntuforums.org/showthread.php?t=281865").

1 is better than 80, and there doesn't appear to be one (tutorial, howto, etc.) that covers the grounds within page 1.

---

### Post by Bruce M. on 2008-12-10
> **Th3Professor said:**
> 1 is better than 80, and there doesn't appear to be one (tutorial, howto, etc.) that covers the grounds within page 1.

Well, considering that you are basing this on your [post #768]("http://ubuntuforums.org/showpost.php?p=6316071&postcount=786") I'd have to say that it would be almost impossible for someone to do a conky for your machine.

However if you are willing to do a little work to get things started check out the little Beginner's Guide I created in my sig.

Now just to get you started, here's my **conkymain**
```
background no
own_window yes
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_colour lightblue
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=9
xftfont Zekton:size=9
xftalpha 2.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 blue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment bl  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y -200 # -200 for br & 35 for tm
text_buffer_size 512 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

# -------- help ---------------
# Timezone information found in: /usr/share/zoneinfo
# UTC ${utime %H:%M}
# BC: ${tztime Canada/Pacific %H:%M}
# Man: ${tztime Canada/Central %H:%M}
# Ont: ${tztime Canada/Eastern %H:%M}
# Nfld: ${tztime Canada/Newfoundland %H:%M}
# Beijing: ${tztime Asia/Shanghai %H:%M}

#-----------------
# with vnstat first you must create database:
# sudo vnstat -u -i eth0 (change eth0 for your network interface)

# to use hddtemp
# sudo chmod u+s /usr/sbin/hddtemp

# -------- end help ------------

TEXT
${voffset -45}${color7}${font OpenLogos:size=150}v$font$color
${voffset -65}${font Zekton:size=15}${color2}Up time:$color${alignr 2}$uptime_short
${color0}${hr 1}$color
${color2}AMD64:$color${alignc}${font DejaVu Sans Mono:size=9}${freq_dyn_g cpu0} GHz$font
${alignc}${color7}<= ${color8}Temperataures ${color9}=>$color
${color4}CPU: ${color5}${execpi 8 sensors | grep 'CPU Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCPU.sh}°$color${goto 108}${color4}Core: ${execpi 8 sensors | grep 'Core0' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCore.sh}°$color${alignr 2}${color4}M/B: ${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempMB.sh}°$color
${voffset 10}${font DejaVu Sans Mono:size=9}${color2}Process:$color${alignr 2}${color 888888}${cpubar cpu0 14,140}$color
${color4}${voffset -16}${goto 140}$running_processes /$processes${alignr 5}$cpu%$color
${voffset -14}${alignr 2}${color yellow}${cpubar cpu2 14,140}$color
${voffset 5}${color7}Load:		${goto 70}${color3}${loadavg 1}	${goto 140}${loadavg 2}${alignr 5}${loadavg 3}$color
${voffset 5}${color2}RAM:$color${alignr 2}${color 888888}${membar 14,140}$color
${color4}${voffset -16}${goto 140}$mem${alignr 5}$memperc%$color
${voffset -14}${alignr 2}${color yellow}${cpubar cpu3 14,140}$color
${voffset 5}${color7}Buffered:${color3}	${goto 70}${buffers}${alignr 2}${color7}Cached:${color3} ${cached}
${voffset 5}${color2}SWAP:$color${alignr 2}${color 888888}${swapbar 14,140}$color
${color4}${voffset -16}${goto 140}$swap${alignr 5}$swapperc%$font
${voffset -16}${alignr 2}${color yellow}${cpubar cpu4 14,140}$color
${color0}${hr 1}$color
${voffset 5}${color2}HD Info${color7} -$color Free${color7} - Used$color
${voffset 5}${color2}sda: ${color7}<= ${color8}Temp: ${color9}=> ${execpi 8 hddtemp /dev/sda | cut --characters 27-28 | xargs ~/Conky/scripts/ColorTempHDD.sh}°$color
${font DejaVu Sans Mono:size=9}		${goto 25}${color7}Root:$color	${goto 90}${fs_free_perc /}%	${goto 135}${fs_free /}${color2}${alignr 2}${color7}${fs_used /}$color$font
${goto 25}${font DejaVu Sans Mono:size=9}${color7}Home:$color	${goto 90}${fs_free_perc /home/bruloo}%	${goto 135}${fs_free /home/bruloo}${alignr 2}${color7}${fs_used /home/bruloo}$color$font
${voffset 5}${color2}sdb: ${color7}<= ${color8}Temp: ${color9}=> ${execpi 8 hddtemp /dev/sdb | cut --characters 31-32 | xargs ~/Conky/scripts/ColorTempHDD.sh}°$color
${goto 25}${font DejaVu Sans Mono:size=9}${color7}Data:$color	${goto 90}${fs_free_perc /media/Data}%	${goto 135}${fs_free /media/Data}${alignr 2}${color7}${fs_used /media/Data}$color$font
${color0}${hr}$color
${voffset 5}${alignc 2}${color2}IP:  $color${addr eth0}
${color8}Dn:$color${downspeed eth0} k/s ${totaldown eth0}${alignr 2}${color7}Up:$color${upspeed eth0} k/s ${totalup eth0}
${color2}In:  $color${tcp_portmon 1 32767 count}${alignc}${color2}Out:  $color${tcp_portmon 32768 61000 count}${alignr 2}${color2}Total:  $color${tcp_portmon 1 65535 count}

${color8}Today:$color${goto 60}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 150}${color7}Today:$color${goto 210}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
${color8}Week:$color${goto 60}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 150}${color7}Week:$color${goto 210}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
${color8}Month:$color${goto 60}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150}${color7}Month:$color${goto 210}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${color0}${hr}$color
${goto 60}${color9}${font Zekton:size=12}${execi 60 du -sh ~/.local/share/Trash/files/ | awk '{print $1}' | sed '/^4.0K/ d'  | sed 's/$/ of TRASH /'}$font$color
```
If you have more question, just ask.

Have a nice day.
Bruce

---

### Post by Luk_Deisler on 2008-12-13
> **Bruce M. said:**
> ...
If you have more question, just ask.

Have a nice day.
Bruce

Hi I've got a problem, when i setup tr(top right), there is no Uptime etc it's cut. [[IMG]http://img185.imageshack.us/img185/6348/screenshotwq1.th.png[/IMG]](http://img185.imageshack.us/my.php?image=screenshotwq1.png)
How to setup conky, that it is top right but everythink visible?
What exactly do you've got in these scripts(~/Conky/scripts)? Can you upload them as well? 

Cheers

---

### Post by richaoj on 2008-12-13
I have googled and haven't scene anyone that's had this problem.  Conky works great, looks beautiful etc, except at login (whenever it starts automatically at the beginning of a session, it looks like a raised transparent window with borders.  I have to kill it and restart it to get it to look the way I want it to.  I have attached my .conkyrc, and a screenshot of how it messed up.

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers no
uppercase no
color1 F8DF58
update_interval 1.0
minimum_size 230 5
maximum_width 230


TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 conkyForecast --location=USMS0175 --datatype=WF --imperial}${color}${font}${voffset -25}  ${execi 600 conkyForecast --location=USMS0175 --datatype=HT --imperial} / ${execi 600 conkyForecast --location=USMS0175 --datatype=LT --imperial}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}
   ${font StyleBats:size=16}A${font}  CPU2: ${cpu cpu2}% ${cpubar cpu2}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 ~/scripts/gmail.pl e}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

```[ATTACH]96226[/ATTACH]

---

### Post by kaivalagi on 2008-12-13
> **richaoj said:**
> I have googled and haven't scene anyone that's had this problem.  Conky works great, looks beautiful etc, except at login (whenever it starts automatically at the beginning of a session, it looks like a raised transparent window with borders.  I have to kill it and restart it to get it to look the way I want it to.  I have attached my .conkyrc, and a screenshot of how it messed up.

Have a read of the beginners guide, link in my sig. Step 2 mentions using a sleep command so compiz etc has time to get up and running before conky starts....

---

### Post by Bruce M. on 2008-12-13
> **Luk_Deisler said:**
> Hi I've got a problem, when i setup tr(top right), there is no Uptime etc it's cut. 

How to setup conky, that it is top right but everythink visible?
What exactly do you've got in these scripts(~/Conky/scripts)? Can you upload them as well? 

Cheers

OK, take a look at the line:
```
gap_y -200 # -200 for br & 35 for tm
```
change it to:
```
gap_y 35 # -200 for br & 35 for tm
```
because you are using it at the **top** of the screen not the **bottom**. That will allow you to see conky complete.

As to your other request, I'll post a complete setup tomorrow. I was away today and have been having connection problems for the last little while and only saw your request now.

Until Sunday, have a nice evening.
Bruce

---

### Post by Bruce M. on 2008-12-14
> **Luk_Deisler said:**
> How to setup conky, that it is top right but everythink visible?
What exactly do you've got in these scripts(~/Conky/scripts)? Can you upload them as well? 

Cheers

Hi Luk

OK, to start off with You don't need everything I have in my ~/Conky/scripts directory ... I've got test files and sub-directories with other complete working configurations for a total of over 200 different working conkys (I save everything).

However lets get this working for you. You will need to some work on your own.

The "layout" of any conky is dependant on a quite a few things, for example: the font you are using **and** the size of the fonts used.

The ${offset}, ${voffset} and ${goto} commands play a big part as well as settings commands: **gap_x** and **gap_y** settings, as you see from my previous post.

```
gap_x 	 Gap, in pixels, between right or left border of screen, same as passing -x at command line, e.g. gap_x 10
gap_y 	 Gap, in pixels, between top or bottom border of screen, same as passing -y at command line, e.g. gap_y 10.
```

So lets get started so you can have this running.

For my **conkymain** you are asking about:
Extra programs needed: **curl, lm-sensors, hddtemp** and **vnstat**, they are all in the repos.

Check out: [HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780"), it's an old post but worked for me.

With the **hddtemp** and **vnstat** programs there is help section built into my conkymain just above the TEXT line.

Fonts needed: **Zekton, OpenLogos, DejaVu Sans Mono**
[COLOR="Blue"]**Mono fonts are highly recommended when "spacing" is the critical factor!**[/COLOR]

You will also need to look at the lines that have:
```
/home/bruloo
/dev/sdb
/media/Data
etc.
```
as I'm sure your ~/home/username is not /bruloo and you probably don't have a second drive with a mount point /media/Data

As for what is in my /Conky/scripts that you need these are what I see:
**ColorTempCPU.sh**
**ColorTempCore.sh**
**ColorTempMB.sh**
**ColorTempHDD.sh**
They are set to use:
```
color7 lightblue
color8 yellow
color9 red
```
so you know if the temps are **cool (lightblue) normal (yellow) or in the danger zone (red)**

The scripts:
**ColorTempCPU.sh**
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
**ColorTempCore.sh**
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
**ColorTempMB.sh**
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
**ColorTempHDD.sh**
```
#!/bin/bash
# colorize.sh

COOL=40
WARM=50

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```

**NOTES:**
[LIST=1]
[*]the temps of *COOL=60 & WARM=70* are the same in three files as I am still researching my hardware to find the critical temps.
[*]make sure the ColorTempxxxx.sh files are executable.
[/LIST]

OK, that should do it, if you have further questions, just ask.

Have a nice day.
Bruce

---

### Post by Luk_Deisler on 2008-12-15
Thanks Bruce, thanks a lot :p it's superb

---

### Post by richaoj on 2008-12-16
Ok, thanks for the earlier help, i am just now having one inconsistent and minor problem . . . the time at the end of my display gets one digit cut off sometimes. 

I have tried increasing max_user_text and text_buffer to no avail . .. 

The conkyrc is the same as in my earlier post (on page 80)

---

### Post by Bruce M. on 2008-12-16
> **Luk_Deisler said:**
> Thanks Bruce, thanks a lot :p it's superb

No problem.  Everything I know about conky I learned here in the forums. So I'm just passing on others work.  :)

Try playing with some of [Kaivalagi's Python Scripts]("http://ubuntuforums.org/showthread.php?p=6097476"). That will improved things even more.

Like:

[LIST]
[*]conkyDeluge
[*]conkyEmail
[*]conkyExaile
[*]conkyForecast
[*]conkyGoogleCalendar
[*]conkyPidgin
[*]conkyRhythmbox
[/LIST]

Enjoy.
Bruce

---

### Post by Bruce M. on 2008-12-16
> **richaoj said:**
> Ok, thanks for the earlier help, i am just now having one inconsistent and minor problem . . . the time at the end of my display gets one digit cut off sometimes. 

I have tried increasing max_user_text and text_buffer to no avail . .. 

The conkyrc is the same as in my earlier post (on page 80)

Hi richaoj,

Ok, so your code ends like this:

```

 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}
```
1. try this:
```

${font Radio Space:size=14}${time %A %d %Y}
${font Radio Space:size=55}${time %H:%M}
```
and see if the minutes stay at 2 digits.

If they do you can also try centring the final two lines:
```

${alignc}${font Radio Space:size=14}${time %A %d %Y}
${alignc}${font Radio Space:size=55}${time %H:%M}
```
It looks like when there is a number wider than 1 (0, 2-9) it gets lost as you have pushed it to the right with those spaces.

If none of this works (I'm confident it will) come back with more questions.

Have a nice day.
Bruce

---

### Post by haneya on 2008-12-19
Hi , thnaks great post , I have a problem with conky , I installed and add it to startup session it ase starting with ubuntu start with no problem until today I tried to restart my computer and then conky started (system monitor) but i cant see it on my desktop , ihave to start it manually , I didnt change any setting at all . 

thanks

---

### Post by Bruce M. on 2008-12-19
> **haneya said:**
> Hi , thnaks great post , I have a problem with conky , I installed and add it to startup session it ase starting with ubuntu start with no problem until today I tried to restart my computer and then conky started (system monitor) but i cant see it on my desktop , ihave to start it manually , I didnt change any setting at all . 

thanks

How do you start it automatically?
Use a script?  Please show it.

Have a nice day
Bruce

---

### Post by haneya on 2008-12-19
...

---

### Post by haneya on 2008-12-19
Hi Bruce , thanks for replying ..

well ,to start conky automaticlly am used to add it startup programs am not using any script it the usual way i guess 
[[IMG]http://img171.imageshack.us/img171/4457/anastz8.th.png[/IMG]](http://img171.imageshack.us/my.php?image=anastz8.png)

thanks , have a nice  day too ):P

---

### Post by Xenophobia on 2008-12-19
Hi, im sorry.

Im installed conky for KDE 4.1

How to start conky for KDE4?

---

### Post by Bruce M. on 2008-12-19
> **Xenophobia said:**
> Hi, im sorry.

Im installed conky for KDE 4.1

How to start conky for KDE4?

See my little guide in my sig ... it's old but still works apparently (I'm an Xubuntu user).

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-12-19
> **haneya said:**
> Hi Bruce , thanks for replying ..

well ,to start conky automaticlly am used to add it startup programs am not using any script it the usual way i guess 

thanks , have a nice  day too ):P

May I suggest a nice little start up script I call SSC.sh (Star/Stop Conky)
```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
# Uncomment sleep lines if necessary
#sleep 30
conky -c ~/Conky/conkymain &
#sleep 30
conky -c ~/Conky/conkyforecast &
#sleep 30
conky -c ~/Conky/conkyemail &
 exit
fi
```
Pop that in, make it executable, uncomment the sleep lines if using Gnome or a heavy desktop manager to allow it to start up **before** conky starts, that way conky will stay on your screen.

Change the lines necessary to point to your conky files and put that in your startup.

At this time you can "Add New Item" to your panel, give it an Icon and use that manually as well. If conky is running it will stop it, if it's not running it will start it.  :D

Hope this helps.

Have a nice day.
Bruce

---

### Post by haneya on 2008-12-19
Well, thanks am going to use this script, but it didnt solve me problem. Before i had to add it to start up programs , and every time ubuntu starts conky start with it but today I restarted me ubuntu and conky doesnt appears on my desktop but its actually running but I cant see it thats what am wondering about .. 

Thanks again ;)

---

### Post by Bruce M. on 2008-12-19
> **haneya said:**
> Well, thanks am going to use this script, but it didnt solve me problem. Before i had to add it to start up programs , and every time ubuntu starts conky start with it but today I restarted me ubuntu and conky doesnt appears on my desktop but its actually running but I cant see it thats what am wondering about .. 

Thanks again ;)

Did you comment out the sleep lines?

From this:
```
#sleep 30
```
To this:
```
sleep 30
```

Try increasing the sleep time ....

Another thought here. Are you using compiz?
If so there are some other issues, let me know and I'll get Hippy here to help.  :D

Have a nice day.
Bruce

---

### Post by haneya on 2008-12-20
Well , Thanks its really working (comment out the sleep statement ) you are the best :p

---

### Post by Bruce M. on 2008-12-20
> **haneya said:**
> Well , Thanks its really working (comment out the sleep statement ) you are the best :p

The best? No, I don't think so.  :D

Just passing on stuff I learned here because a lot of people helped me.

But I'm happy it is working for you.

Here's another thing you can do.

Create an "alias" in your **~/.bashrc** file, I call this one "conke", the "e" is for **e**dit:
```
alias conke='(gedit ~/Conky/scripts/ssc.sh ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/calendar ~/Conky/conkyemail ~/Conky/conkygcal ~/Conky/todo ~/Conky/scripts/myweather.template ~/Conky/scripts/conkyGoogleCalendar.template ~/.conkyForecast.config &)'
```
What this does is simple. Open a terminal type: **conke** and gedit will open everything you have concerning "conky".  You'll have to change the file names and locations to suit your setup, but it is very handy when you want to edit something concerning your conky.

Have a nice day.
Bruce

---

### Post by Fenris_rising on 2009-01-20
Hi all

this is the conky file for my eeepc 904HD.  It includes 3 entries for the displaying of my usb mem sticks and SD media cards. Now I have a question as regards the code as regards the displaying of the info. Can i make it so that the visual info only shows up when a mem stick or the SD card is plugged in rather than as is at the moment where all the bars are displayed regardless of the sticks being present. Also as it stands each line is specific to each by the last word of each ie. disk, disk-1, UDISK.
can these lines also be amended to work 'non-specifically' as in any card or stick plugged in will display without having a specific tag.

regards

Fenris




```

# UBUNTU-CONKY 
# A comprehensive conky script, configublack for use on 
# Ubuntu / Debian Gnome, without the need for any external scripts. 
# 
# Based on conky-jc and the default .conkyrc. 
# INCLUDES: 
# - tail of /var/log/messages 
# - netstat connections to your computer 
# 
# -- Pengo (conky@pengo.us) 
# 

# Create own window instead of using desktop (requiblack in nautilus) 
own_window yes 
own_window_type override 
own_window_transparent yes 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager 

# Use double buffering (blackuces flicker, may not work for everyone) 
double_buffer yes 

# fiddle with window 
use_spacer left 
use_xft yes 

# Update interval in seconds 
update_interval 3.0 

# Minimum size of text area 
minimum_size 200 5 

# Draw shades? 
draw_shades no 

# Text stuff 
draw_outline no # amplifies text if yes 
draw_borders no 
# Xft font when Xft is enabled
xftfont Purisa:size=7

uppercase no # set to yes if you want all text to be in uppercase 

# Stippled borders? 
stippled_borders 3 

# border margins 
border_margin 9 

# border width 
border_width 10 

# Default colors and also border colors, 413839 
default_color 413839 

own_window_colour brown 
own_window_transparent yes 

# Text alignment, other possible values are commented 
#alignment top_left 
alignment top_right 
#alignment bottom_left 
#alignment bottom_right 

# Gap between borders of screen and text 
gap_x 10 
gap_y 10 

# stuff after 'TEXT' will be formatted on screen 

TEXT 
$color 
${color black}SYSTEM ${hr 1}$color 
$nodename $sysname $kernel on $machine 

${color black}Time: ${color 413839}${time %k:%M:%S} 
${color black}Date: ${color 413839}${time %A, %d %B} 

${color black}CPU ${hr 1}$color 
${color 413839}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} 
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp} C
${cpugraph 736F6E FF0000} 

NAME	    ${alignr}PID    CPU%    MEM% 
${top name 1}${alignr 5}${top pid 1} 	${top cpu 1}   ${top mem 1} 
${top name 2}${alignr 5}${top pid 2} 	${top cpu 2}   ${top mem 2} 
${top name 3}${alignr 5}${top pid 3} 	${top cpu 3}   ${top mem 3} 
${top name 4}${alignr 5}${top pid 4} 	${top cpu 4}   ${top mem 4} 
${top name 5}${alignr 5}${top pid 5} 	${top cpu 5}   ${top mem 5} 
${top name 6}${alignr 5}${top pid 5} 	${top cpu 6}   ${top mem 6} 
${top name 7}${alignr 5}${top pid 5} 	${top cpu 7}   ${top mem 7} 

${color black}MEMORY / DISK ${hr 1}$color 
RAM:   $memperc%   ${membar 6}$color 
Swap:  $swapperc%   ${swapbar 6}$color 

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
sdb1:  ${fs_free_perc /media/disk}%   ${fs_bar 6 /media/disk}$color 
sdc1:  ${fs_free_perc /media/disk-1}%   ${fs_bar 6 /media/disk-1}
sdd1:  ${fs_free_perc /media/UDISK}%   ${fs_bar 6 /media/UDISK}

${color black}NET ${hr 1}$color 
${color black}Total:${color 413839} ${totaldown ath0}${color black} Down${color 413839} ${totalup ath0}${color black} Up 
${color black}Wireless ${hr 1}$color 
${color black}Down:${color 413839} ${downspeedgraph ath0 15,75 736F6E FF0000}${color black} Up:${color 413839} ${upspeedgraph ath0 15,75 736F6E FF0000}  ${wireless_bitrate ath0} 

${color black}ESSID:${color black} ${wireless_essid ath0} 
```

---

### Post by dccrens on 2009-01-20
use the following for the device;

${if_mounted /media/DEVICENAMEHERE} "insert you other details about what you want displayed" ${endif}

for example  my "C" drive 

${if_mounted /media/C} ${color4}C Drive: ${color5}${fs_used /media/C} ${endif}

---

### Post by Fenris_rising on 2009-01-20
Hi there

Thanks for that I have been trying the if_mount for hours but with little success. I was close it seems but defo no cigar! Other than the config information that simply lists the options and vagually hints at the string is there any other more detailed information on setting up the strings correctly. Thanks again it's all working fine now. :D

regards

Fenris

---

### Post by dccrens on 2009-01-20
Fenris,
All of the variables and settings are listed at the sourceforge site.
conky.sourceforge.net/config_settings.html 

conky.sourceforge.net/variables.html

other than that I just google a lot :)

---

### Post by Sil3nt Pr0digy on 2009-05-27
Sorry Guys, I just recently started messing with conky, and i cannot seem to get conky to start at the top right, even though i spawn it with the code "conky -a top_right" any suggestions guys? or do i need to edit my .conkyrc file again to incorporate some other piece of code that I am missing?

---

### Post by Bruce M. on 2009-05-27
> **Sil3nt Pr0digy said:**
> Sorry Guys, I just recently started messing with conky, and i cannot seem to get conky to start at the top right, even though i spawn it with the code "conky -a top_right" any suggestions guys? or do i need to edit my .conkyrc file again to incorporate some other piece of code that I am missing?

1. The [conky setting]("http://conky.sourceforge.net/config_settings.html") tell you to put
```
alignment tr
```
above TEXT in your conky file.

Visit us at: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Bruce

---

### Post by The Thug on 2009-08-13
I'm a new Ubuntu user and from what i've seen would like to use Conky as a monitoring tool for my broadband connection (ppp0).

I have seen a couple of scripts that show both the upload and download speed but what I'm looking for is a script that will give me the total daily and monthly upload & download in Mb. Is this possible ?

---

### Post by Bruce M. on 2009-08-13
> **The Thug said:**
> I'm a new Ubuntu user and from what i've seen would like to use Conky as a monitoring tool for my broadband connection (ppp0).

I have seen a couple of scripts that show both the upload and download speed but what I'm looking for is a script that will give me the total daily and monthly upload & download in Mb. Is this possible ?

Yes, a program called "vnstat" it's in the repos...

More info here: [Conky Hardcore! - vnstat]("http://conky.linux-hardcore.com/?page_id=1104")

Have a nice day.
Bruce

---

### Post by The Thug on 2009-08-13
Thanks Bruce, will have a look at it and play around.

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for the info, I appreciate it.

---

### Post by categ0re on 2009-12-30
Hi.

I'd like to post a small HowTo.

Maybe some of you guys are using an overlay network like TOR or i2p to surf the web.
If you do, maybe you´d like to have BOTH IP's displayed in conky.

So well, here we go:

First, you need the ip.sh script.

Create a directory in your home called .scripts
cd into the new directory and create a new blank file with an editor you like to use. I prefer nano.

so well:

**[SIZE=3]Displaying the "normal" IP Adress:[/SIZE]**

**nano ip.sh**

paste the following content:

**#!/bin/bash**
[B]wget --no-proxy [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -q -O - |
grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>'[/B]

(NOTE: --no-proxy option will be explained later. IT HAS TO BE THERE.)

save the file

**chmod +x ip.sh**

--------------------------------------------------------------------------

[SIZE=3]Displaying the i2p-Adress:[/SIZE]

stay in /home/foo/.scripts

**nano i2p.sh**

paste the following content:

**#!/bin/bash**
[B]wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -q -O - |
grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>'[/B]

save the file

[B]chmod +x i2p.sh

[/B]--------------------------------------------------------------------------

Now, we have to configure wget to use our TOR/i2p-server as proxy.

**sudo nano /etc/wgetrc**

search for:
**#http_proxy = [http://proxy:8080](http://proxy:8080)**

uncomment and change to:
**http_proxy = [http://I2P_PROXY_IP:8080/]("http://I2P_PROXY_IP:????/")**
NOTE: The proxy IP can be localhost if you are running TOR/i2p on your machine. Otherwise, enter the IP of your I2P-Server. Change the port to the one you defined, or leave it default.

uncomment
**use_proxy = on**

save the file

--------------------------------------------------------------------------

[SIZE=3]Configuring your .conkyrc[/SIZE]

open .conkyrc with the editor of your choice. I stay with nano here.

**nano /home/foo/.conkyrc**

paste the following lines to your .conkyrc

[B]Regular IP: ${alignr}${execi 1~/.scripts/ip.sh}
i2p IP: ${alignr}${execi 300~/.scripts/i2p.sh}[/B]

The "300" is important. Otherweise your i2p-server is gonna start to reject tunnels because of a high message delay.
Remember? We saved these two files in .scripts , the directory in your home folder.
Reload conky.

Feel free to add some colours or custom fonts to these lines. Example:

**${font Sans:size=7:weight=bold}${color red}i2p IP: ${alignr}${execi 1~/.scripts/i2p.sh}**

--------------------------------------------------------------------------

Keep in mind: **If you are gonna use wget in the future, you have to use the --no-proxy option.** Well, maybe you want wget to download files via encrypted networks. It's your choice.

regards, categ0re

---

### Post by jerryhannah on 2010-10-03
Im so sorry im a linux "noob" i see all this talk about creating this config file when i copied your code in the terminal to paste you conky config and tried to save it said could not find....does any1 have the heart to walk a dummy through step by step

---

### Post by kaivalagi on 2010-10-03
> **jerryhannah said:**
> Im so sorry im a linux "noob" i see all this talk about creating this config file when i copied your code in the terminal to paste you conky config and tried to save it said could not find....does any1 have the heart to walk a dummy through step by step

The last post on this thread was back in December 2009! Try asking for help in the conkyrc thread here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
Better still have a look at the conky pitstop site linked in my sig, or the documentation for conky here: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

HTH

---

### Post by valtam on 2012-09-04
Just finished my LCars Star Trek Conky, took just over a day of coding. This is for the right side screen of a dual monitor setup.

[IMG]http://i.imgur.com/zFvCI.png

---

### Post by RichJacot on 2012-09-05
That's AWESOME!!!!!!!!

---


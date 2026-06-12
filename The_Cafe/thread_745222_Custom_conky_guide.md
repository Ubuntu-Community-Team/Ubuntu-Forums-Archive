---
title: "Custom conky guide"
date: 2008-04-04
forum: The Cafe
---

### Post by billgoldberg on 2008-04-04
I just wrote a guide to create a custom conky setup on my blog.

The point was to make it as simple as possible.

If anyone here can give any pointers on how to make it easier, please do.

link:

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/](http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/)

---

### Post by Ebuntor on 2008-04-04
Looks great, thank you. I've been struggling with conky for quite some time now, couldn't find a easy howto anywhere. I'll read it entirely tomorrow and see if I can give you some pointers.

---

### Post by HangukMiguk on 2008-04-04
Problems:

here's my config file

```
# THIS CONFIG RELIES ON 2 SCRIPTS, CPUSPEED AND CPUTEMP
# YOUR SYSTEM MAY NOT REQUIRE THEM, REPLACE AS DESIRED

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want tormo to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
xftfont Rocky Mountain Spotted Fever-10
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 4.0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 320 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #000000}$nodename$color      ${color #000000}$sysname $kernel on $machine$color
${color #000000}Uptime:$color    $uptime

${color #000000}PROCESSING$color
   ${color #000000}CPU:$color   $cpu% 
   ${color #000000}$cpubar

${color #000000}DATA$color
   ${color #000000}RAM:$color     $memperc%          
${color #000000}Upload:$color  ${upspeed eth0}kb/s${color #000000}	Download:$color       ${downspeed eth0}kb/s

${color #000000}E-MAIL$color
   ${color #000000}GMail:$color You have ${color #000000}${texeci 100 python ~/.scripts/gmail.py}${color} email(s).

${color #000000}MUSIC$color
   ${color #000000}Now Playing:$color ${exec rhythmbox-client –print-playing –no-start}
```

the GMail notifier shows: "You have  email(s)

The music script just shows Now Playing:

But it does launch rhythmbox.........constantly.

I saw variables on the conky website that apparently work with Audacious (which I switched to so I could get my track shown in conky), but don't.

---

### Post by billgoldberg on 2008-04-05
> **HangukMiguk said:**
> Problems:

here's my config file

```
# THIS CONFIG RELIES ON 2 SCRIPTS, CPUSPEED AND CPUTEMP
# YOUR SYSTEM MAY NOT REQUIRE THEM, REPLACE AS DESIRED

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want tormo to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
xftfont Rocky Mountain Spotted Fever-10
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 4.0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 320 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #000000}$nodename$color      ${color #000000}$sysname $kernel on $machine$color
${color #000000}Uptime:$color    $uptime

${color #000000}PROCESSING$color
   ${color #000000}CPU:$color   $cpu% 
   ${color #000000}$cpubar

${color #000000}DATA$color
   ${color #000000}RAM:$color     $memperc%          
${color #000000}Upload:$color  ${upspeed eth0}kb/s${color #000000}	Download:$color       ${downspeed eth0}kb/s

${color #000000}E-MAIL$color
   ${color #000000}GMail:$color You have ${color #000000}${texeci 100 python ~/.scripts/gmail.py}${color} email(s).

${color #000000}MUSIC$color
   ${color #000000}Now Playing:$color ${exec rhythmbox-client –print-playing –no-start}
```

the GMail notifier shows: "You have  email(s)

The music script just shows Now Playing:

But it does launch rhythmbox.........constantly.

I saw variables on the conky website that apparently work with Audacious (which I switched to so I could get my track shown in conky), but don't.

${color #000000}MUSIC$color
   ${color #000000}Now Playing:$color ${exec rhythmbox-client –print-playing –no-start}[/CODE]

It should be -- (- -, without the space) instead of –

Wordpress insists on doing that. I'll going to adjust it.

---

### Post by Scruffynerf on 2008-04-05
We've already a huge conky thread here at [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Should this be merged in?

---

### Post by billgoldberg on 2008-04-05
> **Scruffynerf said:**
> We've already a huge conky thread here at [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Should this be merged in?

I hope not.

That thread is to way big.

If people need conky help, this will show up in the search results.

---

### Post by HangukMiguk on 2008-04-05
> **billgoldberg said:**
> ${color #000000}MUSIC$color
   ${color #000000}Now Playing:$color ${exec rhythmbox-client –print-playing –no-start}[/CODE]

It should be -- (- -, without the space) instead of –

Wordpress insists on doing that. I'll going to adjust it.
Yeah, after looking at a few other pages, I figured that out, and it did fix the problem.  :)

Also, I think I figured out why the gmail script did not work in your howto, you forgot the step to make it executable:

```
sudo chmod a+x ~/scripts/gmail.py
```

I looked at other scripts for GMail, these in perl, and every one mentioned this, so I tried, and voila.

---

### Post by billgoldberg on 2008-04-05
> **HangukMiguk said:**
> Yeah, after looking at a few other pages, I figured that out, and it did fix the problem.  :)

Also, I think I figured out why the gmail script did not work in your howto, you forgot the step to make it executable:

```
sudo chmod a+x ~/scripts/gmail.py
```

I looked at other scripts for GMail, these in perl, and every one mentioned this, so I tried, and voila.

Thanks, it must have slipped my mind.

---

### Post by TWeerts on 2008-05-23
i am trying to have the conky app say the music now playing. it says the "music" and "now playing" but there is no info on the song that is playing. here is my .conkyrc:

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
${offset 240}${cpugraph 20,130 000000 0033ff}
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
${offset 240}${memgraph eth0 20,130 000000 ffccff}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}

${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 cc0033}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 00ff00}

${offset 240}${color slate grey}MUSIC$color
${offset 240}${color #ffffff}Now Playing:$color ${exec rhythmbox-client –print-playing –no-start}

```
attached is what comes up

---

### Post by TheBigBakedBean on 2008-06-20
> **HangukMiguk said:**
> The music script just shows Now Playing:

But it does launch rhythmbox.........constantly.


I found this thread:[http://ubuntuforums.org/showthread.php?t=658067](http://ubuntuforums.org/showthread.php?t=658067) but I don't speak Spanish, so I took it for what it was worth and this is what I came up with:

[IMG]http://www.jimlerza.com/images/rhythmbox_conky.png[/IMG]

I ran into the same problem - where Rhythmbox was constantly launching after I closed it.  I came up with a fix, but I'm sure it's probably not the ideal solution.

It turns out that the ${if_running} var by itself is not refreshed at each conky interval, so running the command rhythmbox-client is actually launching rhythmbox.  I wrote a script that first checks running processes (ps aux) before checking for running rhythmbox-client.

Please let me know if you find ways to make this better!

I know - the progress meter is a little excessive, but I've broken the code that drives it out so you don't have to use it if you don't want to. [-( 

The first script, nowplaying.sh, handles pulling the artist information when Rhythmbox is running.  Feel free to edit the conky formatting to your tastes.  
> nano ~/bin/nowplaying.sh

Paste in the following:
```
#!/bin/bash

isrunning=$(ps aux | grep [r]hythmbox | cut -c66-74)

if [ "$isrunning" != "" ]
then
   artist=$(rhythmbox-client --print-playing-format '%aa')
   album=$(rhythmbox-client --print-playing-format '%at')
   title=$(rhythmbox-client --print-playing-format '%tt')
   year=$(rhythmbox-client --print-playing-format '%ay')

   if [ "$year" != "Not playing" ]
   then
      echo '${color orange}Now Playing ${hr 2}${color}'
      echo '${alignc}${font}'$title' ${font URW Chancery L:size=7}by  ${voffset -1}${font}'$artist
      if [ "$year" -lt 1900 ]
      then
         echo '${alignc}${font URW Chancery L:size=7}from  ${font}'$album
      else 
         echo '${alignc}${font URW Chancery L:size=7}from  ${font}'$album'${voffset -1}${font URW Chancery L:size=7} ('$year')${font}'
      fi
   else
      echo '${voffset -21}'
   fi
fi
```

The ${vosffset -21} in that last else statement is to correct the empty linebreaks that are created when rhythmbox is running but has reached the end of a playlist.  You may want to change this to match whatever font rendering you use.  Once you're finished with your edits, press CTRL+X then Y to save the file.

Then make it executable:
> chmod a+x ~/bin/nowplaying.sh

If you want the progress meter, you'll need to make another file.
> nano ~/bin/progress.sh

Paste this in:
```
#!/bin/bash

isrunning=$(ps aux | grep [r]hythmbox | cut -c66-74)

if [ "$isrunning" != "" ]
then
   elapsed=$(rhythmbox-client --print-playing-format '%te')
   duration=$(rhythmbox-client --print-playing-format '%td')
   if [ "$elapsed" != "Not playing" ]
   then
      ethirdchar=$(echo $elapsed | cut -c3)
      dthirdchar=$(echo $duration | cut -c3)
      efifthchar=$(echo $elapsed | cut -c5)
      dfifthchar=$(echo $duration | cut -c5)

      if [ "$efifthchar" == ":" ]
      then
         ehour=$(echo $elapsed | cut -c1)
         emin=$(echo $elapsed | cut -c3-4)
         esec=$(echo $elapsed | cut -c6-7)
      else
         if [ "$ethirdchar" == ":" ]
         then
            emin=$(echo $elapsed | cut -c1-2)
            esec=$(echo $elapsed | cut -c4-5)
         else
            emin=$(echo $elapsed | cut -c1)
            esec=$(echo $elapsed | cut -c3-4)
         fi
      fi

      if [ "$dfifthchar" == ":" ]
      then
         dhour=$(echo $duration | cut -c1)
         dmin=$(echo $duration | cut -c3-4)
         dsec=$(echo $duration | cut -c6-7)
      else
         if [ $dthirdchar == ":" ]
         then
            dmin=$(echo $duration | cut -c1-2)
            dsec=$(echo $duration | cut -c4-5)
         else
            dmin=$(echo $duration | cut -c1)
            dsec=$(echo $duration | cut -c3-4)
         fi
      fi

      if [ "$ehour" != "" ]
      then
         ehrtosec=$(qalc -t $ehour*3600)
         emintosec=$(qalc -t $emin*60)
         esecs=$(qalc -t $ehrtosec+$emintosec+$esec)
      else
         emintosec=$(qalc -t $emin*60)
         esecs=$(qalc -t $emintosec+$esec)
      fi

      if [ "$dhour" != "" ]
      then
         dhrtosec=$(qalc -t $dhour*3600)
         dmintosec=$(qalc -t $dmin*60)
         dsecs=$(qalc -t $dhrtosec+$dmintosec+$dsec)
      else
         dmintosec=$(qalc -t $dmin*60)
         dsecs=$(qalc -t $dmintosec+$dsec)
      fi

      ratio=$(qalc -t $esecs/$dsecs | cut -c3-6)
      percent=$(qalc -t $ratio/100)

      echo $percent
   fi
fi
```

Save the file by pressing CTRL+X then Y, and then make it executable:
> chmod a+x ~/bin/progress.sh

This script requires qalc, a command line calculator, to perform the calculations.  

Run this to install qalc:
> sudo apt-get install qalc

Then you have to run qalc once and type "yes" to download the conversion equations:
> qalc

Almost there...now you just need to edit .conkyrc:
> nano ~/.conkyrc

If you want the progress bar, paste this snippet wherever you want the Rhythmbox information to be displayed:
```
${if_running /usr/bin/rhythmbox}${execp ~/bin/nowplaying.sh}${if_empty ${exec ~/bin/progress.sh}}${else}
${alignc}${exec rhythmbox-client --print-playing-format '%te'} / ${exec rhythmbox-client --print-playing-format '%td'} ${alignr}${exec ~/bin/progress.sh}%
${execibar 2 ~/bin/progress.sh}${endif}

${endif}
```

Or if you don't want the progress bar, paste this snippet into .conkyrc instead:
```
${if_running /usr/bin/rhythmbox}${execp ~/bin/nowplaying.sh}${endif}
```

Once you've pasted the appropriate snippet, save and close with CTRL+X then Y.

In case you're curious, here's my complete .conkyrc:
```
background yes
use_xft yes
xftfont Sans:size=7
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 240 5
maximum_width 240
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 38
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
${color orange}$sysname $kernel on $nodename ${hr 2}$color
${font StyleBats:size=12}P${font} Uptime $alignr $uptime
${font StyleBats:size=12}X${font} Load $alignr $loadavg
${font StyleBats:size=12}O${font} Local IP $alignr ${addr eth0}
${font StyleBats:size=12}V${font} Public IP $alignr ${color}${execi 14400 wget -O - http://whatismyip.org/ | tail}${color}

${color orange}System ${hr 2}$color
${font StyleBats:size=12}T${font} $processes processes ($running_processes running)

${font PizzaDude Bullets:size=11}N${font} Highest CPU ${goto 130}${voffset -4}${font PizzaDude Bullets:size=11}O${font} Highest MEM
${voffset 4}${goto 10}${top name 1} ${goto 90}${top cpu 1} ${goto 134}${top_mem name 1}${alignr}${top_mem mem 1}
${goto 10}${top name 2} ${goto 90}${top cpu 2} ${goto 134}${top_mem name 2}${alignr}${top_mem mem 2}
${goto 10}${top name 3} ${goto 90}${top cpu 3} ${goto 134}${top_mem name 3}${alignr}${top_mem mem 3}
${goto 10}${top name 4} ${goto 90}${top cpu 4} ${goto 134}${top_mem name 4}${alignr}${top_mem mem 4}
${goto 10}${top name 5} ${goto 90}${top cpu 5} ${goto 134}${top_mem name 5}${alignr}${top_mem mem 5}

${font StyleBats:size=12}A${font} CPU $alignr ${cpu cpu0}%
${cpugraph cpu0 14,240}
${font PizzaDude Bullets:size=12}J${font} MEM $alignc $mem / $memmax $alignr $memperc%
$membar
${font StyleBats:size=12}B${font} swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}
${font StyleBats:size=12}F${font} /root $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
${font StyleBats:size=12}G${font} /home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_used_perc /home}%
${fs_bar /home}
${voffset 5}${goto 7}${font weather:size=18}y${font} ${voffset -5}${goto 24}CPU Temp $alignr ${i2c 1-002d temp 2} C
${voffset 8}${font xspiralmental:size=11}j${font} ${voffset -1}${goto 24}CPU Fan Speed $alignr ${i2c 1-002d fan 1} C
${voffset 5}${goto 7}${font weather:size=18}y${font} ${voffset -5}${goto 24}MB Temp $alignr ${i2c 1-002d temp 1} C
${voffset 5}${goto 7}${font weather:size=18}y${font} ${voffset -5}${goto 24}GPU Temp $alignr ${execi 300 nvclock -T | grep GPU | cut -c21-22 ;} C
${voffset 5}${goto 7}${font weather:size=18}y${font} ${voffset -5}${goto 24}HDD Temp $alignr ${execi 300 nc localhost 7634 | cut -c26-27 ;} C

${color orange}Networking ${hr 2}$color
${font PizzaDude Bullets:size=12}r${font} Down: $alignr ${downspeed eth0} k/s
${downspeedgraph eth0 14,240}
${font PizzaDude Bullets:size=12}v${font} Up: $alignr ${upspeed eth0} k/s
${upspeedgraph eth0 14,240}
${font FnT_BasicShapes1:size=12}\${font} Inbound (${tcp_portmon 1 32767 count}) ${alignr} Local Service/Port
${goto 10}${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${goto 10}${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${font FnT_BasicShapes1:size=12}^${font} Outbound (${tcp_portmon 32768 61000 count}) ${alignr} Remote Service/Port
${goto 10}${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${goto 10}${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}

${if_running /usr/bin/rhythmbox}${execp ~/bin/nowplaying.sh}${if_empty ${exec ~/bin/progress.sh}}${else}
${alignc}${exec rhythmbox-client --print-playing-format '%te'} / ${exec rhythmbox-client --print-playing-format '%td'} ${alignr}${exec ~/bin/progress.sh}%
${execibar 2 ~/bin/progress.sh}${endif}

${endif}${color orange}E-Mail ${hr 2}$color
${font Dingbat:size=18})${font} ${voffset -5}EMAIL ONE $alignr ${execi 300 python ~/bin/gmail.py}
${font Dingbat:size=18})${font} ${voffset -5}EMAIL TWO $alignr ${execi 300 ~/bin/fetchmail.sh}

${color orange}Current Weather Conditions ${hr 2}$color
${execp ~/bin/nwsweather.sh}
```

And here's a screenshot:

---

### Post by SomeGuyDude on 2008-06-20
That's helpful, but not really a "custom guide". It tells you how to play with a config file someone else made and add some stuff, but at the end of it the person isn't going to have a complete understanding of the elements. What I'd like to see is a guide that tells you how to build one from scratch.

---

### Post by TheBigBakedBean on 2008-06-20
> **SomeGuyDude said:**
> That's helpful, but not really a "custom guide". It tells you how to play with a config file someone else made and add some stuff, but at the end of it the person isn't going to have a complete understanding of the elements. What I'd like to see is a guide that tells you how to build one from scratch.

I found "man conky" entry to be very informative.  All of the options that you can configure before the TEXT portion of .conkyrc are explained.  I recommend going through and setting each option, and then tweaking them to your liking.

Following those explanations, all of the variables you can use are explained.  See the [Conky Variables](http://conky.sourceforge.net/variables.html) page for usage examples.

If you have any further questions that the man page doesn't explain, I'm sure someone around here can shed some light.

---

### Post by tensecor on 2008-08-06
That is great?
But if I use fetchmail download mails to my computer,how to set up cony is this case.
Thanks!

---

### Post by geezerone on 2008-09-30
I *used* to have the SWAP size displayed but since resizing (with GParted CD) my HOME partition and moving the SWAP partition I get the message of **No swap %**

My conky script to display the 'SWAP' partition is:

```
${color slate grey}SWAP: ${color }$swapperc%$alignr$swap/$swapmax
${swapbar 3,230}
```Any ideas?

(The Swap is shown in partition editor).

Solution found due to moving Swap partiton and thus the UUID changed. Had to copy new UUID discover by typing  *sudo blkid* to get new UUID value. Copied this to fstab file and rebooted.

---

### Post by fedex1993 on 2008-09-30
Is there a way that i could use a email other than gmail for conky?

---

### Post by easybake on 2008-09-30
> **fedex1993 said:**
> Is there a way that i could use a email other than gmail for conky?

Check out this [thread]("http://ubuntuforums.org/showthread.php?t=869771")

---

### Post by BlackLLama on 2008-09-30
nice simple guide

---

### Post by crimesaucer on 2008-09-30
I bookmarked it just in case I want to add gmail.


You might want to add a tutorial/discussion about showing temperatures of GPU and hdd.


I had to search around a lot of conky threads to learn how to show my nvidia GPU temp, and I never felt like doing all the work to get my hddtemp to actually show (running it with root privileges).

---

### Post by djsroknrol on 2008-09-30
> **billgoldberg said:**
> I just wrote a guide to create a custom conky setup on my blog.

The point was to make it as simple as possible.

If anyone here can give any pointers on how to make it easier, please do.

link:

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/](http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/)

Very nice guide billgoldberg, but how would one change Celsius output to Fahrenheit?

---

### Post by grayfox3214 on 2009-07-10
i'm trying to get an script to work, only conky pickes an diffrent script folder.

I thought the default folder for that was .conkyrc

But that doesn't work....

Is there an root folder for conkyrc?

---

### Post by dogbert176 on 2009-07-11
also nice to check:
[http://conky.linux-hardcore.com/]("http://conky.linux-hardcore.com/")

---

### Post by rajadain on 2010-05-07
I use the following:
```
rhythmbox-client --no-start --no-present --print-playing-format "%ta"
```
I find that having separate calls to rhythmbox-client for Artist, Title, Album and other info every second keeps my processor running. I think we can reduce this usage if we make a single call, like
```
rhythmbox-client --no-start --no-present --print-playing-format "%ta %tt %at %te %td"
```
and then capture these values and use them in variables. Can anybody tell me how to do that?

---


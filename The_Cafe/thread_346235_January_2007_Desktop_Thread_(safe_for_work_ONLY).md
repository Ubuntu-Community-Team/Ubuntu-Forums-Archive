---
title: "January 2007 Desktop Thread (safe for work ONLY)"
date: 2006-12-31
forum: The Cafe
---

### Post by John.Michael.Kane on 2006-12-31
[B]Here are the 'rules':

Posts made to a screen shot area need to follow forum rules at all times.
No explicit or suggestive images (they must be safe for your kids and/or boss to see).
No political or religious attacks.
No racist or other attacks against a group of people.
Please post links to screen shots with thumbnails. Actual screen shot width take up excessive bandwidth.

[COLOR="DarkOrange"]Please include the following[/COLOR]

Name of theme/icons being used.
Link to wallpaper used.
Conky.rc file if used.
[/B]

---

### Post by s6dalane on 2006-12-31
There's very little snow in Estonia, but look at my desktop!

---

### Post by slimdog360 on 2006-12-31
I took the wallpaper from deviant art and modded it a little.
[[IMG]http://img73.imageshack.us/img73/3842/snapshot5kd9.th.jpg[/IMG]]("http://img73.imageshack.us/img73/3842/snapshot5kd9.jpg")

---

### Post by testube_babies on 2006-12-31
A fresh year, a fresh install of Ubuntu + XP.

[[IMG]http://img357.imageshack.us/img357/8126/ubuntushotuy9.th.jpg[/IMG]](http://img357.imageshack.us/my.php?image=ubuntushotuy9.jpg) [[IMG]http://img517.imageshack.us/img517/6835/cubean8.th.jpg[/IMG]](http://img517.imageshack.us/my.php?image=cubean8.jpg) [[IMG]http://img357.imageshack.us/img357/4042/xpshotqk8.th.jpg[/IMG]](http://img357.imageshack.us/my.php?image=xpshotqk8.jpg)

---

### Post by ~LoKe on 2006-12-31
[[IMG]http://img354.imageshack.us/img354/8739/1231061su8.th.jpg[/IMG]](http://img354.imageshack.us/my.php?image=1231061su8.jpg)

---

### Post by PatrickMay16 on 2006-12-31
Ha! Ha! Oh man. I'm pretty happy right now.
In this screenshot, I have one window showing; it is gedit, showing my weekly backup script.


[http://img509.imageshack.us/img509/6276/freebenisjb3.jpg](http://img509.imageshack.us/img509/6276/freebenisjb3.jpg)

Theme used: PenOSmaster, which is a theme I made myself

The background image is something that some guy posted on 4chan.org's photography board.

---

### Post by justinlb on 2006-12-31
Just a nice picture I found and the Gnome environment slightly modded.

[[IMG]http://img293.imageshack.us/img293/320/screenshotnb0.th.png[/IMG]](http://img293.imageshack.us/my.php?image=screenshotnb0.png)

---

### Post by SAGEv4.5 on 2006-12-31
[http://i127.photobucket.com/albums/p160/ddbann/Screenshot.png](http://i127.photobucket.com/albums/p160/ddbann/Screenshot.png)

found it at [http://www.linuxwallpapers.org/linux/linux-wallpaper30.html](http://www.linuxwallpapers.org/linux/linux-wallpaper30.html)

---

### Post by fuscia on 2007-01-01
nothing new, except the window decoration is 'milk noir light gray' for dekorator.

---

### Post by TheRingmaster on 2007-01-01
I love my "[watching the heavens fall]("http://www.deviantart.com/deviation/34452503/")" background. I got it from here: [StudioTwentyEight : giving your computer a new look]("http://www.studiotwentyeight.com/index2.htm")

nothing else did I change except top panel (and beryl of course)

---

### Post by fuscia on 2007-01-01
hey, ringmaster, have you considered changing the level of your wallpaper? if you get it to the right level (so that the left edge and right edge are at exactly the same height), the landscape on your cube will have the appearance of going all the way around.

---

### Post by RAV TUX on 2007-01-01
Sabayon Linux 3.2

---

### Post by crimesaucer on 2007-01-01
These are some screenshots of my most recent desktop. The graffiti art is from an artist named Dalek. The space invader guy is from a tag piece called "Game-Bombing", and I think the artist's name was Don Carlos E.

I used the Dalek piece because it has the shadow of a "fawn" or a baby deer behind the mouse, so it will be my xubuntu Feisty Fawn desktop as soon as the release candidates come out. It also matched my Pimpzilla leopard fur.

The borders are leopard fur, gold and diamonds that I cropped from the PimpZilla theme to go with my favorite Firefox theme. The Beryl splash and logo are from the Beryl wiki page and I modified it a bit with GIMP. The bubble.png is from the Beryl 1.5-svn and I used the GIMP to create the bubbled space invaders. The xubuntu logo is from the xubuntu art page, I added the space invaders to it with GIMP. The fonts are Judas and Ubuntu-title.

This is Conky 1.4.5 and the .conkyrc is at the bottom.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-15-3.png[/IMG]

[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8-2.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8-2.png)

[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-1.png)

[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-15-2.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-15-2.png)

[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-12-3.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-12-3.png)

[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-16-2.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-16-2.png)


```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - battery stats, cached memory, uptime, date/time, file system stats
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
#own_window_type normal
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
# I think the "use spacer" option only works with mono fonts.
use_spacer yes
use_xft yes

# Xft font when Xft is enabled
xftfont Judas:size=9

# Update interval in seconds
update_interval 3.0

# Minimum size of text area

minimum_size 666 10

maximum_width 249


# Text stuff
# amplifies text if yes was no
draw_outline yes 
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase


# border margins
#border_margin 0

# border width
#border_width 0

# Default colors and also border colors
#default_shade_color a7d9a3
default_outline_color 2c2c2c
default_color fffcf7 



# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 23
gap_y 66
	

# Text alpha when using Xft
xftalpha 1


# drawn 1 pixel border around graphs 
draw_graph_borders no

# stuff after 'TEXT' will be formatted on screen


TEXT
xubuntu 6.10/Beryl AiGLX
blah@${nodename}
${kernel} on ${machine} 
IP eth0:    ${addr eth0}
wifi eth1:  ${linkstatus eth1}%
${time} 
*  Uptime:  ${uptime}
*  Battery: ${battery}
*  B. time: ${battery_time}
Thunar File System:${alignr 24}${fs_size}
${alignr 24}used = ${fs_used}
${alignr 24}free = ${fs_free} 
Root File:${alignr 24}${fs_free_perc /}% used  
Win Xp:${alignr 24}${fs_free_perc /media/hda1}% used
Swap File:${alignr 24}${swapperc}% of ${swapmax}
RAM:${alignr 24}${memperc}% of ${memmax}
Cache Mem:${alignr 24}${cached}
  
  1.)  ${top_mem name 1}
mem %${offset 18}${top_mem mem 1}${offset 31}${alignc}cpu %${alignr 24}${top_mem cpu 1}

  2.)  ${top_mem name 2}
mem %${offset 18}${top_mem mem 2}${offset 31}${alignc}cpu %${alignr 24}${top_mem cpu 2}

  3.)  ${top_mem name 3}
mem %${offset 18}${top_mem mem 3}${offset 31}${alignc}cpu %${alignr 24}${top_mem cpu 3}

Up: ${upspeedf eth0}k/s${alignr 24}Down: ${downspeedf eth0}k/s
Up: ${totalup eth0}${alignr 24}Down: ${totaldown eth0}
${upspeedgraph eth0 34,100 6f706b 2b2c27}${offset 28}${downspeedgraph eth0 34,100 6f706b 2b2c27}

*  Temp:    ${acpitemp}.c
*  Load:    ${loadavg}
*  CPU:     ${freq}MHz
*  Clocked: ${freq_dyn}MHz
${cpugraph 34,228 6f706b 2b2c27}  
  1.)  ${top name 1}
cpu %${offset 18}${top cpu 1}${offset 31}${alignc}mem %${alignr 24}${top mem 1}
  
  2.)  ${top name 2}
cpu %${offset 18}${top cpu 2}${offset 31}${alignc}mem %${alignr 24}${top mem 2}

  3.)  ${top name 3}
cpu %${offset 18}${top cpu 3}${offset 31}${alignc}mem %${alignr 24}${top mem 3}

. . . . . crimesaucer--->


```

---

### Post by matthew on 2007-01-01
It's not nearly as cool as some, but I like my current background...it's Grand Canyon in Arizona. Click for full size.
[[IMG]http://ubuntuforums.org/gallery/data/500/thumbs/20070101.jpg[/IMG]]("http://ubuntuforums.org/gallery/data/500/20070101.jpg")

---

### Post by ayoli on 2007-01-01
Nothing much new on my desktop, just a way to wish an happy new year to everybody, using beryl's annotation plugin :)
[[IMG]http://img472.imageshack.us/img472/9753/captureyx7.th.png[/IMG]](http://img472.imageshack.us/my.php?image=captureyx7.png)

---

### Post by stalker145 on 2007-01-01
Happy New Year!!

Theme is Emerald's Scaled_Black_Mod with LiNsta-GTK2 controls and Crux icons.

The background is one I found in the December thread. I LOVE IT!!

I just got the maximized windows fixed this morning. They were giving me a white title bar and the whole Beryl thing was running a bit slow. Works now :) 

Nice thing is, even the snow works now :D

Now, though, to remember how to change it from 10 faces on the cube back to the normal 6.

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
update_interval 1.0

# Minimum size of text area
minimum_size 50 5

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
gap_x 2
gap_y 3

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont TSCu_Times:size=11
xftalpha 0.8

TEXT
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }   $kernel
${offset 240}${color slate grey}CPU:${color }    $cpu% 
${offset 240}${cpugraph 20,130 1a1aaf ff0000 }
${offset 240}${color slate grey}Processes: ${color }$processes  ${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 242}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 242}${color lightgrey} ${top name 2}${top cpu 2}
${offset 242}${color lightgrey} ${top name 3}${top cpu 3}

${offset 240}${color slate grey}Highest MEM:
${offset 242}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 242}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 242}${color lightgrey} ${top_mem name 3}${top_mem mem 3}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}Root:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}Thumb:  ${color }${fs_free /media/usbdisk}/${fs_size /media/usbdisk}
${offset 240}${fs_bar 3,100 /media/usbdisk}

${offset 240}${color slate grey}NET: 
${offset 240}ath0:    ${addr ath0}
${offset 240}Signal:  ${linkstatus  ath0}%
${offset 240}${color}Up: ${color}${upspeed ath0}    ${color}Down: ${color}${downspeed ath0}
${offset 240}${upspeedgraph ath0 20,60 1a1aaf ff0000}  ${color}${downspeedgraph ath0 20,60 1a1aaf ff0000}
${offset 240}${color #ddaa00}Port(s)    #Connections   
${offset 240}$color Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}    
${offset 240}    ALL: ${tcp_portmon 1 65535 count}
${offset 240}${color #ddaa00}Outbound ${color #ffffff}
${offset 240} ${tcp_portmon 32768 61000 rhost 0}
${offset 240} ${tcp_portmon 32768 61000 rhost 1}
${offset 240} ${tcp_portmon 32768 61000 rhost 2}
${offset 240} ${tcp_portmon 32768 61000 rhost 3}
${offset 240} ${tcp_portmon 32768 61000 rhost 4}
${offset 240} ${tcp_portmon 32768 61000 rhost 5}

```

---

### Post by TheRingmaster on 2007-01-01
> **fuscia said:**
> hey, ringmaster, have you considered changing the level of your wallpaper? if you get it to the right level (so that the left edge and right edge are at exactly the same height), the landscape on your cube will have the appearance of going all the way around.

actually no, but it would be nice to know. If you or someone would tell me.

---

### Post by linuxgeekery on 2007-01-01
Fuscia: KDE can be quite beautiful sometimes, but I'm a gnome guy :)

Anyways, here are my screenshots for this month.  I really like my current desktop, but I might get a new wallpaper sometime. 
The little media controller thing at the bottom is just a gnome panel with media controller icons from the Innocent suite (find it on gnome-look.org).  I just chose the controller icons as the icon and used command line switches for banshee to operate the controls.

---

### Post by fuscia on 2007-01-01
> **TheRingmaster said:**
> actually no, but it would be nice to know. If you or someone would tell me.

you mean tell you how? open the wallpaper in gimp and select *tools>transform tools>rotate*. you'll have a guide on the left hand side which will show you the level of wherever you're pointing the cursor. after rotating the image, you will have to trim it back to a retangle (*crop&resize* is also under *transform tools*).

edit: after looking at the wallpaper again, you may not be able to match up all the edges, but you could certainly line up the horizon line. another possibility would be to cut the image in half, take the better half and match it to a mirror image. that way, all the lines would match up around the cube.

edit 2: here are some samples of what i mean. i took part of the first sample, copied it, flipped the copy and matched the two up in one pic. as both sides of the resultant picture are the same, they will match up exactly all around the cube.

---

### Post by m.musashi on 2007-01-01
@fusica

That's pretty cool. Is there a way to have two sides of the beryl cube each use half of that image so that the point were the roads converge is the edge of the cube? I guess it would only work on one one edge but it would look cool.

---

### Post by fuscia on 2007-01-01
> **m.musashi said:**
> @fusica

That's pretty cool. Is there a way to have two sides of the beryl cube each use half of that image so that the point were the roads converge is the edge of the cube? I guess it would only work on one one edge but it would look cool.

the only way i could see that happening is to use kde with beryl, but i think i recall multiple wallpapers not working with beryl and kde.

edit: yup, you can't do it.

---

### Post by Albi on 2007-01-01
> **ayoli said:**
> Nothing much new on my desktop, just a way to wish an happy new year to everybody, using beryl's annotation plugin :)
[[IMG]http://img472.imageshack.us/img472/9753/captureyx7.th.png[/IMG]](http://img472.imageshack.us/my.php?image=captureyx7.png)

What dock is that?

---

### Post by fuscia on 2007-01-01
here's kind of a rush job of what i was talking about earlier (meh)...

---

### Post by ayoli on 2007-01-01
> **Albi said:**
> What dock is that?

kxdocker (it's a kde app but i prefer it to gnomedock or kiba beacause it's more functional)

---

### Post by m.musashi on 2007-01-01
> **fuscia said:**
> the only way i could see that happening is to use kde with beryl, but i think i recall multiple wallpapers not working with beryl and kde.

edit: yup, you can't do it.

That's kind of what I thought. Your solution above is cool though. You could probably do some pretty neat effects with symmetrical images - a face split in half for example. I'm not much good with gimp but I'll have to play around and see what I can come up with.

EDIT: Here is my quick hack job. I'm listening to hendrix so that's where I got the idea. I guess I could have cropped closer to the middle so the halves would line up better but I didn't want to lose too much of the face since I don't look at the cube that often.

---

### Post by tigerpants on 2007-01-01
Here's my current gnome set up. Beryl + Emerald running nice and smooth now. :)

---

### Post by fuscia on 2007-01-01
love the idea of the faces, musashi. gave me an idea. second one hasn't worked the way i want it, yet.

(busts by franz messerschmidt)

---

### Post by tigerpants on 2007-01-01
How come you guys all have skydome working in beryl? I can't get it to work at all ](*,)

Fuscia, dude, that is giving me nightmares ;)

---

### Post by Crooksey on 2007-01-01
[[img]http://tn3-1.deviantart.com/fs15/300W/f/2007/001/8/1/Openbox___Arch_Jan_07_by_crooksey.jpg[/img]](http://ic1.deviantart.com/fs15/f/2007/001/8/1/Openbox___Arch_Jan_07_by_crooksey.jpg)

---

### Post by m.musashi on 2007-01-01
I modified my hack job wallpaper to give it some color and then set a more apropriate skydome. You can't really see the skydome but it's the cover from "first rays of the new rising sun"

---

### Post by urukrama on 2007-01-01
> **tigerpants said:**
> Here's my current gnome set up.

Nice.

---

### Post by RAV TUX on 2007-01-01
> **fuscia said:**
> the only way i could see that happening is to use kde with beryl, but i think i recall multiple wallpapers not working with beryl and kde.

edit: yup, you can't do it.

correction...multiple wallpaper do work with Beryl & KDE...I am almost certain I have done this before.

---

### Post by ~LoKe on 2007-01-01
> **RAV TUX said:**
> correction...multiple wallpaper do work with Beryl & KDE

The SVN release of beryl has a plugin to do just that.  Haven't played with it yet and am not sure if it even works.

---

### Post by BOBSONATOR on 2007-01-01
Love it!

---

### Post by raul_ on 2007-01-01
Pretty simple actually...i don't remember where i got the background. Here is my .conkyrc:

```

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want tormo to be forked in the background
#background yes

use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-7
#xftfont Clean-7
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 0.8
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 230 5
maximum_width 250

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
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


${color #ffcb48}$nodename$color      ${color #ffcb48}$sysname $kernel on $machine$color
${color #ffffff}Sky is the limit                                      Uptime:$uptime$color
__________________________________________________________________________

${color #ffcb48}PROCESSING$color
${color #98c2c7}CPU:$color     $cpu% 
${color #98c2c7}$cpubar
${color #98c2c7}${cpugraph 78af78 a3a3a3}

${color #98c2c7}NAME             PID       CPU%      MEM%
${color #e5e5e5}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${color #c4c4c4}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${color #a3a3a3}${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${color #828282}${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color #ffcb48}DATA$color
${color #98c2c7}RAM:$color$memperc% ${color #98c2c7}${membar 6}${color #828282}
${color #98c2c7}SWAP:$color$swapperc% ${color #98c2c7}${swapbar 6}${color #828282}

${color #ffcb48}FILESYSTEM
${color #98c2c7}root /:$color${fs_free_perc /}% $fs_free ${color #98c2c7}${fs_bar 6 /}$color

${color #98c2c7}Upload:${color red}${upspeed eth0}kb/s${color #98c2c7} 
Download:${color green}${downspeed eth0}kb/s${color #98c2c7}
__________________________________________________________________________

${execi 60 /usr/bin/pymetar LPPT}

```

I actually feel bad posting it, some guys have awesome desktops :rolleyes:

---

### Post by illu45 on 2007-01-01
My current desktop

[Wallpaper Link]("http://www.photonav.dk/images/deepseahuntingNy21680.png")

---

### Post by Skidpad on 2007-01-01
> **ayoli said:**
> Nothing much new on my desktop, just a way to wish an happy new year to everybody, using beryl's annotation plugin :)
[[IMG]http://img472.imageshack.us/img472/9753/captureyx7.th.png[/IMG]](http://img472.imageshack.us/my.php?image=captureyx7.png)
I'm a n00b user, so pardon my ignorance, but what system monitor is that?  (Great desktop by the way!)

---

### Post by Crooksey on 2007-01-01
Gkrellm?

---

### Post by Tiede on 2007-01-01
Well, I just changed mine about half an hour ago... I think I like it so far... Hope you guys do too!

[[IMG]http://img523.imageshack.us/img523/1386/capture1et7.th.png[/IMG]](http://img523.imageshack.us/my.php?image=capture1et7.png)

Any thoughts? :)
I forgot to say kudos to ryzst from the caedes.net gallery for his fabulous [Second Earth](http://www.caedes.net/Zephir.cgi?lib=Caedes::Infopage&image=ryzst-1156927835.jpg) image I am using as my background.

---

### Post by ~LoKe on 2007-01-01
Back to the one I had in December.

**January 1st, 2007**
[[img]http://img216.imageshack.us/img216/192/27decyb3.th.png[/img]](http://img216.imageshack.us/img216/192/27decyb3.png)

---

### Post by Kingsley on 2007-01-01
evil!!! i'll post my linux desktop later :P.

---

### Post by c.dric on 2007-01-01
Compiz with Nvidia on XFCE
Most wallpapers are from [here]("http://interfacelift.com/wallpaper/index.php?sort=ratings&w=1680&h=1050").

[Capture 1]("http://c.dric.be/gium/misc/Compiz-cube1.jpg")
[Capture 2]("http://c.dric.be/gium/misc/Compiz-cube2.jpg")

---

### Post by kevinf311 on 2007-01-01
> **Kingsley said:**
> evil!!! i'll post my linux desktop later :P.

Maybe, but nice Win mod! Very slick looking. I'll post my Ubuntu desktop when I get back to Atlanta next week.

---

### Post by darkhatter on 2007-01-02
> **ayoli said:**
> Nothing much new on my desktop, just a way to wish an happy new year to everybody, using beryl's annotation plugin :)
[[IMG]http://img472.imageshack.us/img472/9753/captureyx7.th.png[/IMG]](http://img472.imageshack.us/my.php?image=captureyx7.png)

can you tell me what docker your using?

---

### Post by ayoli on 2007-01-02
> **darkhatter said:**
> can you tell me what docker your using?

[http://www.ubuntuforums.org/showthread.php?t=328915&page=3#24](http://www.ubuntuforums.org/showthread.php?t=328915&page=3#24) :)

---

### Post by queen_yoshi on 2007-01-02
Here is my nice shiny new desktop after a fresh install after playing around with and singing the praises of Kubuntu....I still went back to Ubuntu and Gnome, seems to feel the MOST right lol

[http://www.f-monkey.com/gallery/main.php?g2_itemId=206](http://www.f-monkey.com/gallery/main.php?g2_itemId=206)

---

### Post by happy-and-lost on 2007-01-02
I still haven't changed the default layout of the Gnome panels... but that's 'cos I love them as they are :D

Wallpaper is [here]("http://www.deviantart.com/deviation/45484415/"), I flipped it over so that my conky could stay where it is.

My .conkyrc is enclosed below

Using the MurrinaCandyDuo theme with good old Tango icons.

---

### Post by fuscia on 2007-01-02
> **RAV TUX said:**
> correction...multiple wallpaper do work with Beryl & KDE...I am almost certain I have done this before.

[quote=Loke]The SVN release of beryl has a plugin to do just that. Haven't played with it yet and am not sure if it even works.[/quote]

this *is* exciting news!

---

### Post by BOBSONATOR on 2007-01-02
> **queen_yoshi said:**
> Here is my nice shiny new desktop after a fresh install after playing around with and singing the praises of Kubuntu....I still went back to Ubuntu and Gnome, seems to feel the MOST right  lol



What theme/metacity/icon is that?

i love it!

---

### Post by happy-and-lost on 2007-01-02
> **BOBSONATOR said:**
> What theme/metacity/icon is that?

i love it!

I second that, which font is that also?

---

### Post by urukrama on 2007-01-02
> **queen_yoshi said:**
> Here is my nice shiny new desktop after a fresh install after playing around with and singing the praises of Kubuntu....I still went back to Ubuntu and Gnome, seems to feel the MOST right  lol

What Icon theme is that?

---

### Post by raul_ on 2007-01-02
Got bored and changed my desktop. Theme is Elegance both in metacity and in beryl. Background from zenwalk artwork (resized) and the conky file is still the same.
I'm still working in the dock though. gnome-dock gives me a floating point exception and kxdock says i don't have the headers installed. That way i could get rid of those launchers in the panel

---

### Post by fuscia on 2007-01-02
more silly crap with messerschmidt...

---

### Post by Quillz on 2007-01-02
I call it... Windows Classic ;)

---

### Post by raul_ on 2007-01-02
> **Quillz said:**
> I call it... Windows Classic ;)

A little off-topic, but the icons definition in linux is so much better than in windows. I can see the pixels in windows

---

### Post by Quillz on 2007-01-02
> **raul_ said:**
> A little off-topic, but the icons definition in linux is so much better than in windows. I can see the pixels in windows
I agree. Even in Windows Vista, you are limited to 96x96 .ico files. But with Linux, there is no limit, and you can use any file format. On my current desktop, I'm using stretched, high quality .png icons.

---

### Post by Quillz on 2007-01-02
> **raul_ said:**
> Got bored and changed my desktop. Theme is Elegance both in metacity and in beryl. Background from zenwalk artwork (resized) and the conky file is still the same.
I'm still working in the dock though. gnome-dock gives me a floating point exception and kxdock says i don't have the headers installed. That way i could get rid of those launchers in the panel
Does Elegance refer to the desktop icons? What style are those?

---

### Post by raul_ on 2007-01-02
the icons are called Dropline neu! and i found them in gnome-look . Forgot to mention that :)

---

### Post by raul_ on 2007-01-02
Does anybody know how to add text to the "menu bar" icon in the panel? I could use that

---

### Post by Quillz on 2007-01-02
> **raul_ said:**
> the icons are called Dropline neu! and i found them in gnome-look . Forgot to mention that :)
Thanks. I'm gonna go look for them now.

---

### Post by red_Marvin on 2007-01-02
[URL="http://ubuntuforums.org/gallery/data/4/screenshot208.png"][img]http://ubuntuforums.org/gallery/data/4/thumbs/screenshot208.png[/img]
http://ubuntuforums.org/gallery/data/4/screenshot208.png
[/URL]
Background: "simply_captured", found on deviantart
OB Theme: "p0ng", found on boxwhore, although the screenshot there looks different...

---

### Post by ffi on 2007-01-02
Beryl/Emerald with my own window borders ( a mix of compiz-gilouche and t-ish)
Icons: SnowIsh
and qt-curve style

---

### Post by finferflu on 2007-01-02
I've been tweaking with IceWM for a couple of weeks now.. I'm quite satisfied; adesklets are very handy! (and yea, it's raining in Manchester :P).

---

### Post by mysticrider92 on 2007-01-02
Here is my desktop. Not much has changed from last month, but I did change the skydome in Beryl. 
[[IMG]http://imagecloset.net/uthumbs/bwy1167790966q.png[/IMG]](http://imagecloset.net/viewer.php?id=bwy1167790966q.png) [[IMG]http://imagecloset.net/uthumbs/cqs1167791063r.png[/IMG]](http://imagecloset.net/viewer.php?id=cqs1167791063r.png) [[IMG]http://imagecloset.net/uthumbs/viu1167791107e.png[/IMG]](http://imagecloset.net/viewer.php?id=viu1167791107e.png)

---

### Post by fuscia on 2007-01-02
> **red_Marvin said:**
> [URL="http://ubuntuforums.org/gallery/data/4/screenshot208.png"][img]http://ubuntuforums.org/gallery/data/4/thumbs/screenshot208.png[/img]
http://ubuntuforums.org/gallery/data/4/screenshot208.png
[/URL]
Background: "simply_captured", found on deviantart
OB Theme: "p0ng", found on boxwhore, although the screenshot there looks different...

that's very nice. openbox can be quite lovely.

---

### Post by ice60 on 2007-01-02
here's mine running glxgears too. should xglgears be taking up all my CPU cycles?

[[IMG]http://img131.imageshack.us/img131/7666/screenshot0301200703200kw2.th.png[/IMG]](http://img131.imageshack.us/my.php?image=screenshot0301200703200kw2.png)

---

### Post by BWF89 on 2007-01-02
Mac OS 10.4.8
[http://img172.imageshack.us/img172/6514/bwfosxdesktopjan2007ur8.png](http://img172.imageshack.us/img172/6514/bwfosxdesktopjan2007ur8.png)
Wallpaper from [http://homepage2.nifty.com/hsuzuki/wallpaper/e_04_winter_01.htm](http://homepage2.nifty.com/hsuzuki/wallpaper/e_04_winter_01.htm)

Kubuntu 6.10
[http://img49.imageshack.us/img49/8371/bwfkubuntudesktopjan200nr7.jpg](http://img49.imageshack.us/img49/8371/bwfkubuntudesktopjan200nr7.jpg)
Wallpaper included with installation

---

### Post by ice60 on 2007-01-02
> **Quillz said:**
> I agree. Even in Windows Vista, you are limited to 96x96 .ico files. But with Linux, there is no limit, and you can use any file format. On my current desktop, I'm using stretched, high quality .png icons.
hi, i've never used vista and i'm not planning to either, but i thought they had made big improvments with alot windows GUI stuff. unless i'm misunderstanding something somewhere :confused: :)
[http://www.axialis.com/tutorials/tutorial-vistaicons.html](http://www.axialis.com/tutorials/tutorial-vistaicons.html)

> Vista introduces a new standard for Windows icon size: 256x256 pixels.

---

### Post by queen_yoshi on 2007-01-02
> **BOBSONATOR said:**
> What theme/metacity/icon is that?

i love it!

I am using Murrine Angellic Green from Gnome-Look for Metacity/GTK2 and the nuoveXT 1.6 icons also from Gnome Art :mrgreen:

---

### Post by queen_yoshi on 2007-01-02
> **happy-and-lost said:**
> I second that, which font is that also?

Font is URW Gothic :-D

---

### Post by m.musashi on 2007-01-02
> **ice60 said:**
> here's mine running glxgears too. should xglgears be taking up all my CPU cycles?

[[IMG]http://img131.imageshack.us/img131/7666/screenshot0301200703200kw2.th.png[/IMG]](http://img131.imageshack.us/my.php?image=screenshot0301200703200kw2.png)

I don't know why, but glxgears runs the cpu at 100%. Perhaps that is intentional as it's kind of (but not really :)) a benchmark. In any case, that seems to be a normal outcome of running it.

---

### Post by ice60 on 2007-01-02
> **m.musashi said:**
> I don't know why, but glxgears runs the cpu at 100%. Perhaps that is intentional as it's kind of (but not really :)) a benchmark. In any case, that seems to be a normal outcome of running it.
OK, thanks for the help, musashi :) 

i might as well add this while i'm here -

[[IMG]http://img132.imageshack.us/img132/1851/mydesktopfv5.th.png[/IMG]](http://img132.imageshack.us/my.php?image=mydesktopfv5.png)

---

### Post by m.musashi on 2007-01-03
I spend way too much time playing around with look of my screen. My wife calls it an addiction but the drugstore didn't have little patches. Oh well. Here is my latest attempt. Not much different than last month but with a new wall and some changes to conky. The wallpaper and skydome came from [http://www.caedes.net](http://www.caedes.net) I think. Sorry I don't have the exact link but there are a lot of pages there.

---

### Post by Scabby_al on 2007-01-03
Here is a few shots of my desktop and the wallpaper I found. I don't have a link but PM me and I'll email the hi-res version to you.

---

### Post by Tiede on 2007-01-03
Never  mind...
Move along. nothing to see here...

---

### Post by tigerpants on 2007-01-03
Wish I could get the skydome working in Beryl:(

Ice60 - can you post your conky file please, its fab

---

### Post by supertux on 2007-01-03
> **Scabby_al said:**
> Here is a few shots of my desktop and the wallpaper I found. I don't have a link but PM me and I'll email the hi-res version to you.

Nice wallpaper!! tx

---

### Post by renzokuken on 2007-01-03
> **Scabby_al said:**
> Here is a few shots of my desktop and the wallpaper I found. I don't have a link but PM me and I'll email the hi-res version to you.

i took almost that exact photo in the Heineken Experience factory/museum in Amsterdam. Quality place. Three free beers during the tour.

They have the bottles lined up like that behind one of the bars.

---

### Post by darkhatter on 2007-01-03
> **Quillz said:**
> I call it... Windows Classic ;)

those icons are kind of small, can you make them bigger :rolleyes:

---

### Post by BLTicklemonster on 2007-01-03
Here's what my desktop looks like

---

### Post by TheRingmaster on 2007-01-03
> **BLTicklemonster said:**
> Here's what my desktop looks like

your gonna get a splinter if you aren't careful! :)

---

### Post by r0nin on 2007-01-03
Voilà:

---

### Post by raublekick on 2007-01-03
[[IMG]http://entropy.good-evil.net/images/beryl1-thumb.png[/IMG]]("http://entropy.good-evil.net/images/beryl1.png")

[[IMG]http://entropy.good-evil.net/images/beryl2-thumb.png[/IMG]]("http://entropy.good-evil.net/images/beryl2.png")

---

### Post by finferflu on 2007-01-03
I feel alone... I'm the only one who can't install Beryl, since I've got an ATI (unsupported) card, and XGL would make my wacom tablet useless :(

---

### Post by raul_ on 2007-01-03
Have you tried AIGLX?

---

### Post by finferflu on 2007-01-03
> **raul_ said:**
> Have you tried AIGLX?

Yes, but the driver doesn't support direct rendering for my graphics card...

---

### Post by ice60 on 2007-01-03
> **tigerpants said:**
> Ice60 - can you post your conky file please, its fab hi :) i've uploaded my .conkyrc file along with the scripts (which work with everything from the weather downward).

i keep all the scripts in a directory called ~/scripts. you'll have to edit the paths, at the bottom of .conkyrc, so your username replaces mine. make the scripts executable too. if you have any problems you can PM me if you want :)


[Conky_setup_files.Tar.Gz](http://www.bigupload.com/d=42CB563A)
i don't know anything about the upload site i've used so here's the md5 
```
b24c2b3f7ef2b03d7c71d5c130073b7d  conky_setup_files.tar.gz
```

you can check you have the same sum by typing this into your terminal -
```
md5sum conky_setup_files.tar.gz
``` just make sure your terminal is working in the directory you saved conky_setup_files.tar.gz too.

make sure you allow javascript to run at the download site it won't work otherwise.

[color=blue]EDIT[/color] i just noticed i saved the scripts in a directory called scripts_backup_no.2, you'll have to rename scripts_backup_no.2 to scripts.

---

### Post by cmmike1 on 2007-01-04
here's mine. Some custom icons and beryl.

---

### Post by tbroderick on 2007-01-04
> **finferflu said:**
> I feel alone... I'm the only one who can't install Beryl, since I've got an ATI (unsupported) card, and XGL would make my wacom tablet useless :(

I can but I don't want to. Try WMII for a change.

---

### Post by fuscia on 2007-01-04
my first post-hose reinstall screeny. i feel, as they say, 'so fresh and so clean'.

samui theme, AER-OS-XK icons (with a few extras, like 'dead girl' for xkill) and one of my favorite wallpapers ('olympie' from interfacelift).

---

### Post by katana2k on 2007-01-04
> **ayoli said:**
> Nothing much new on my desktop, just a way to wish an happy new year to everybody, using beryl's annotation plugin :)
[[IMG]http://img472.imageshack.us/img472/9753/captureyx7.th.png[/IMG]](http://img472.imageshack.us/my.php?image=captureyx7.png)

nice desktop! i notice your weather desklet and ive been trying to get that same one for like a year now and i cant find the gdesklet anywhere :( could you tell me how you got it/send it to me?

---

### Post by finferflu on 2007-01-04
> **tbroderick said:**
> I can but I don't want to. Try WMII for a change.

I've tryed WMII, but I'm not quite satisfied. I think it's very usable, but I need something for my eyes as well (I'm an artist you know :P). I couldn't find any theme or anything like that whatsoever. Windows are only plain squares, no desktop, no toolbars. Yet, I think its concept is very fascinating.

---

### Post by fuscia on 2007-01-04
'victrola' gtk and 'floth' metacity themes, a mix of icons (AER-OS-XK, j3cons and a few others(that irish looking thing, that suse looking thing, swiftfox and 'dead girl') and some real looking wallpaper...

---

### Post by theturtlemoves on 2007-01-04
This is the first time I've got something worth showing.

---

### Post by BOBSONATOR on 2007-01-04
Nice ones guys, and fuscia, dont you want to change that font?

mine right now...

---

### Post by fuscia on 2007-01-04
> **BOBSONATOR said:**
> Nice ones guys, and fuscia, dont you want to change that font?

why didn't *i* think of that???](*,)

---

### Post by plb on 2007-01-04
Mine

---

### Post by hoagie on 2007-01-04
New January desky.
[http://www.flickr.com/photo_zoom.gne?id=345801615&size=o](http://www.flickr.com/photo_zoom.gne?id=345801615&size=o)

---

### Post by ayoli on 2007-01-04
> **katana2k said:**
> nice desktop! i notice your weather desklet and ive been trying to get that same one for like a year now and i cant find the gdesklet anywhere :( could you tell me how you got it/send it to me?
thanks :)
for the desklet, have a look [**here**]("http://www.ubuntuforums.org/showthread.php?t=215769&highlight=gdesklets+weather#8")

---

### Post by Theimon on 2007-01-04
Does anyone know which font is used in the this screenie? [http://www.gnome-look.org/content/pre1/42755-1.jpg](http://www.gnome-look.org/content/pre1/42755-1.jpg)

---

### Post by zekopeko on 2007-01-04
ubuntu default icons and theme, using gdesklets and conky.

wallpaper is from [http://interfacelift.com/](http://interfacelift.com/). they have some great and BIG RES wallpapers.

[[IMG]http://img465.imageshack.us/img465/4968/cloudsrc6.th.jpg[/IMG]](http://img465.imageshack.us/my.php?image=cloudsrc6.jpg)

---

### Post by tigerpants on 2007-01-04
> **ice60 said:**
> hi :) i've uploaded my .conkyrc file along with the scripts (which work with everything from the weather downward).


You're a :KS

---

### Post by ayoli on 2007-01-04
ok, new year implies some changes (even few), so here is my 2007 desktop, i really like cube transparency :)
[[IMG]http://img398.imageshack.us/img398/4250/200701042249021024x768sdx3.th.png[/IMG]](http://img398.imageshack.us/my.php?image=200701042249021024x768sdx3.png)
beryl theme is a customized t-ish, gtk theme is a customized murrina style, icons are from slafd pack (avalaible on [www.gnome-look.org](www.gnome-look.org)) dock is kxdocker, monitor is gkrellm with invisibleXT theme (also avalaible on [www.gnome-look.org](www.gnome-look.org))

---

### Post by Interestedinthepenguin on 2007-01-04
I created the blue background in the GIMP.

The Kingdom Hearts transparent PNG is from [http://www.khextreme.co.uk/](http://www.khextreme.co.uk/)

Conky file: 

```

# Create own window instead of using desktop (required in nautilus)

own_window yes

own_window_hints undecorated,below,skip_taskbar

background no

# Use double buffering (reduces flicker, may not work for everyone)

double_buffer yes

# fiddle with window

use_spacer no

use_xft yes

# Update interval in seconds

update_interval 3.0

# Minimum size of text area

minimum_size 400 5

# Draw shades? no causes blue text to be invisible

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

own_window_colour slategrey

own_window_transparent yes

# Text alignment, other possible values are commented

#alignment top_left

alignment top_right

#alignment bottom_left

#alignment bottom_right

# Gap between borders of screen and text

gap_x 1

gap_y 1

# stuff after 'TEXT' will be formatted on screen 

override_utf8_locale 
no
xftfont 
Terminus:size=8

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


${offset 240}${color slate grey}Battery: $color${battery}


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

```

---

### Post by Quillz on 2007-01-04
> **ayoli said:**
> Nothing much new on my desktop, just a way to wish an happy new year to everybody, using beryl's annotation plugin :)
[[IMG]http://img472.imageshack.us/img472/9753/captureyx7.th.png[/IMG]](http://img472.imageshack.us/my.php?image=captureyx7.png)
That's a very nice desktop.

---

### Post by ayoli on 2007-01-04
> **Quillz said:**
> That's a very nice desktop.

thanx :)

---

### Post by tigerpants on 2007-01-04
My latest. The wife is getting sick of me changing things. :)  As long as I leave the gdesklets launcher in the same place, she's fine.

---

### Post by BOBSONATOR on 2007-01-04
> **Theimon said:**
> Does anyone know which font is used in the this screenie? [http://www.gnome-look.org/content/pre1/42755-1.jpg](http://www.gnome-look.org/content/pre1/42755-1.jpg)


Yes that is luxi sans, search it on the forum and someone has a guide to installing it.

---

### Post by Theimon on 2007-01-04
> **BOBSONATOR said:**
> Yes that is luxi sans, search it on the forum and someone has a guide to installing it.

Brilliant :) Thank you!

Edit: should anyone be interested: these fonts can be found in the repos. Look for ttf-xfree86-nonfree or t1-xfree86-nonfree.

---

### Post by fuscia on 2007-01-04
'red underwear'

openbox, victrola theme, laser star 4000 theme for beep and, of course, astron boy font.

---

### Post by m.musashi on 2007-01-04
fuscia...I think you change your desktop as often as I change underware...probably more often :).

---

### Post by electricshoes on 2007-01-04
you have a link to that wallpaper ~LoKe?

---

### Post by fuscia on 2007-01-04
> **m.musashi said:**
> fuscia...I think you change your desktop as often as I change underware...probably more often :).

i like to stay fresh.

---

### Post by ~LoKe on 2007-01-04
> **electricshoes said:**
> you have a link to that wallpaper ~LoKe?

[This](http://img363.imageshack.us/img363/7806/blackwallwallpapers1361oy8.jpg) one?

---

### Post by rkakkar on 2007-01-04
> **raublekick said:**
> [[IMG]http://entropy.good-evil.net/images/beryl1-thumb.png[/IMG]]("http://entropy.good-evil.net/images/beryl1.png")

[[IMG]http://entropy.good-evil.net/images/beryl2-thumb.png[/IMG]]("http://entropy.good-evil.net/images/beryl2.png")


tell me everything i need to know to get my desktop looking like that :D. including font and all!

---

### Post by electricshoes on 2007-01-05
> **~LoKe said:**
> [This](http://img363.imageshack.us/img363/7806/blackwallwallpapers1361oy8.jpg) one?

Rejoice!!

---

### Post by Quillz on 2007-01-05
Here's my new desktop, featuring a widescreen resolution, Beryl and Kiba-Dock.
[URL="http://www.quillz.net/random/desktop/desktop_010407.png"]
[IMG]http://img507.imageshack.us/img507/1786/desktop010407ib8.png[/IMG][/URL]

---

### Post by kvonb on 2007-01-05
> **tigerpants said:**
> My latest. The wife is getting sick of me changing things. :)  As long as I leave the gdesklets launcher in the same place, she's fine.

You could always create an account just for her, then you could become another Fuscia and customise till your eyes wear out!

---

### Post by tigerpants on 2007-01-05
> **kvonb said:**
> You could always create an account just for her, then you could become another Fuscia and customise till your eyes wear out!

I did offer, but her reply was, "why don't you just stop ****** about with it instead?" :-D 

[-(

---

### Post by escape on 2007-01-05
[[IMG]http://img526.imageshack.us/img526/4095/screenshotla0.th.png[/IMG]](http://img526.imageshack.us/my.php?image=screenshotla0.png)
[[IMG]http://img504.imageshack.us/img504/7650/screenshotpc6.th.png[/IMG]](http://img504.imageshack.us/my.php?image=screenshotpc6.png)

Using Beryl with Emerald theme called "Truth" (@gnome-look.org) with some tweaks; gtk theme is Glossy P with some tweaks and color changes. Get it from art.gnome.org; icon theme is OS X from gnome-look.org using alternate folder colors; background is [here](http://img507.imageshack.us/img507/1361/metamerismti1.jpg); panel is [here](http://img506.imageshack.us/img506/9792/panel142gy7.png); using alltray and deviant art icon forThunderbird, with alltray and OS X icon for gaim and swiftfox for the deviant art-ish firefox icon; rhythmbox icon thread [here](http://ubuntuforums.org/showthread.php?t=259176&highlight=custom+rhythmbox+icons);  firefox theme is iFox Graphite with tweaks.

---

### Post by cmmike1 on 2007-01-05
I changed up my desktop a lot since the other day. now i have kiba-dock running the way i want it to and i removed the one panel. beryl and some custom icons but i'm using the  glass icon set. enjoy.

---

### Post by fuscia on 2007-01-05
'blueish'

crystal diamond icons and some pic from interfacelift.

---

### Post by ayoli on 2007-01-05
> **m.musashi said:**
> fuscia...I think you change your desktop as often as I change underware...probably more often :).

LOL, i second that :D

---

### Post by xoai on 2007-01-05
My desktop

[[IMG]http://img525.imageshack.us/img525/5654/screenshotthumbnailog9.png[/IMG]](http://img506.imageshack.us/img506/8817/screenshotvl2.png)

---

### Post by slimdog360 on 2007-01-05
I shot that wallpaper myself and cropped it to 1440x900. Its getting good results in the 1024x768 section on kdelook so far.

[[IMG]http://img441.imageshack.us/img441/3760/snapshot6bq0.th.jpg[/IMG]]("http://img441.imageshack.us/img441/3760/snapshot6bq0.jpg")

for anyone who wants the wallpaper [http://www.kde-look.org/content/show.php?content=51133]("http://www.kde-look.org/content/show.php?content=51133")

---

### Post by m.musashi on 2007-01-06
^nice avatar.

Well, I didn't change my underwear today but I did come up with a new desktop. It's pretty similar to before but I changed my conky colors to kind of match the wallpaper (had to keep some orange though) and a new skydome.

BTW, if anyone is looking for a nice tool for screen shots, try scrot. It is very simple and allows saving in different file formats (I used png and jpg), delay shots and more. I bet someone could make a simple script and attach it to a key or launch icon too. I installed it with apt-get.

---

### Post by fuscia on 2007-01-06
the *seasons* change more often than you guys change your underwear. anyway...

openbox with a modified version of obMurrina and a very important message in the terminal (xfce4-terminal and that's kaffeine in there too). the gun is a mini-uzi.

---

### Post by flapane on 2007-01-06
my sister box w/dapper i386 and xp-m 2ghz.
I used to format her pc with windows xp 1time a month for viruses, now I'll be happier, and she's happier too (she prefers even amarok and amsn)

[[IMG]http://img220.imageshack.us/img220/4559/schermata2dq0.th.jpg[/IMG]](http://img220.imageshack.us/img220/4559/schermata2dq0.jpg)
[[IMG]http://img220.imageshack.us/img220/3271/schermata3mp4.th.jpg[/IMG]](http://img220.imageshack.us/img220/3271/schermata3mp4.jpg)

---

### Post by gosh on 2007-01-06
beryl theme euh
icons tangerine
wallpaper from [www.webstrings.com](www.webstrings.com)

.conkyrc:

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
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color beige
default_shade_color red
default_outline_color green
alignment bottom_left
gap_x 12
gap_y 48
double_buffer yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$nodename $sysname $kernel on $machine
Uptime $alignr $uptime
eth1 $alignr ${addr eth1}
Signal $alignr${linkstatus  eth1}%
In  ${downspeed eth1} kb/s ${downspeedgraph eth1}
Out ${upspeed eth1} kb/s ${upspeedgraph eth1}
CPU ${freq}Mhz $alignr ${cpu cpu0}%
${cpubar cpu0}
MEM $alignc $mem / $memmax $alignr $memperc%
$membar
/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
XP $alignc ${fs_used /media/XP} / ${fs_size /media/XP} $alignr ${fs_free_perc /media/XP}%
${fs_bar /media/XP}
Music $alignc ${fs_used /media/USB DISK} / ${fs_size /media/USB DISK} $alignr ${fs_free_perc /media/USB DISK}%
${fs_bar /media/USB DISK}
Movies $alignc ${fs_used /media/Movies} / ${fs_size /media/Movies} $alignr ${fs_free_perc /media/Movies}%
${fs_bar /media/Movies}
iPod $alignc ${fs_used /media/ipod} / ${fs_size /media/ipod} $alignr ${fs_free_perc /media/ipod}%
${fs_bar /media/ipod}
2Gb $alignc ${fs_used /media/2GB} / ${fs_size /media/2GB} $alignr ${fs_free_perc /media/2GB}%
${fs_bar /media/2GB}

```

---

### Post by happy-and-lost on 2007-01-06
Here's my go at a Mac rip off. I *really* _hate_ the shinyness of OSX, but I had a point to prove to a friend ;)

> **zekopeko said:**
> ubuntu default icons and theme, using gdesklets and conky.

wallpaper is from [http://interfacelift.com/](http://interfacelift.com/). they have some great and BIG RES wallpapers.


Do my eyes deceive me, or have you got RCT2 working under Wine... how?!

(The attatched image is the OSX panel background I made, I couldn't find any 24px ones on the net)

PS... does anyone have a clue how to get rid of those fugly handles either side of my dock?

---

### Post by chronusdark on 2007-01-06
My Current Desktop

---

### Post by m.musashi on 2007-01-06
> **chronusdark said:**
> My Current Desktop

How did you do this different walls on different desktops? I've heard tell of way in beryl but I haven't investigated yet. I know kde offers this but it looks like you have gnome to me.

---

### Post by fuscia on 2007-01-06
> **m.musashi said:**
> How did you do this different walls on different desktops? 

the one on the left looks more like a maximized image file than a wallpaper (note the lack of panels).

---

### Post by viciouslime on 2007-01-06
> **m.musashi said:**
> How did you do this different walls on different desktops? I've heard tell of way in beryl but I haven't investigated yet. I know kde offers this but it looks like you have gnome to me.

I don't think that is different wallpapers, look carefully and i think it is probably a video running in full screen mode on that desktop. There are no panels, nor icons visible...

EDIT: Lol damn it, someone beat me to it :p Though I think video is more likely than full-screen image personally :p

---

### Post by m.musashi on 2007-01-06
^nice detective work you two.

I was just jumping to conclusions and seeing what I wanted to see. Still, didn't someone say something like that was possible - different walls that is.

---

### Post by zerhacke on 2007-01-06
My Enlightenment desktop I've worked on for a few hours now.  This is a work in progress.  I'd like to see more Enlightenment folks on here!

---

### Post by tcrroadie on 2007-01-06
zerhacke, wish granted.

Here is a screenshot of my Enlightenment E17 desktop running on Edgy.

E17 Theme - cthulhain
GTK2 Theme - Silicon
Wallpaper - Divianopoly [http://www.deviantart.com/deviation/2967044/?&q=devianopoly&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5]("http://www.deviantart.com/deviation/2967044/?&q=devianopoly&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5")

[IMG]http://ubuntuforums.org/gallery/data/4/medium/e17-listen2.png[/IMG]

---

### Post by Quillz on 2007-01-06
[[IMG]http://img352.imageshack.us/img352/2751/desktop010607ne4.png[/IMG]]("http://www.quillz.net/random/desktop/desktop_010607.png")

---

### Post by fuscia on 2007-01-06
nice A (if you know what i mean...) -

---

### Post by RAV TUX on 2007-01-06
sensual but safe fine art.

---

### Post by toorima on 2007-01-07
> **RAV TUX said:**
> sensual but safe fine art.

What is that world time map thing on your panel? I would love to have it animated as desktopbackground but it works in the panel too

---

### Post by maniacmusician on 2007-01-07
> **Quillz said:**
> [[IMG]http://img352.imageshack.us/img352/2751/desktop010607ne4.png[/IMG]]("http://www.quillz.net/random/desktop/desktop_010607.png")
excuse my ignorance, but what are you using for those icons on the bottom right corner? looks intriguing.

edit: nevermind, it looks to be kiba dock...

---

### Post by Quillz on 2007-01-07
> **maniacmusician said:**
> excuse my ignorance, but what are you using for those icons on the bottom right corner? looks intriguing.

edit: nevermind, it looks to be kiba dock...
Yes, it's Kiba-Dock. The icons themselves are a combination of the Dropline_neu! icon set and others found on DeviantArt.

---

### Post by kvonb on 2007-01-07
>  PS... does anyone have a clue how to get rid of those fugly handles either side of my dock?

Yes, switch to KDE!  Honestly the Gnome devs have been sweeping this under the mat for years!  I've searched and emailed till my fingers were raw, best to forget it and think of something much more pleasing :)

---

### Post by urukrama on 2007-01-07
> **zerhacke said:**
> I'd like to see more Enlightenment folks on here!

I tried enlightenment once, but it made absolutely no sense to me. :D Just a blank space with some odd buttons that didn't seem to do anything and no right click menu. I didn't even know how to log back out. 

I'm sure there is something to it, but I didn't have the time and energy to try and find out.

---

### Post by zerhacke on 2007-01-07
> **tcrroadie said:**
> zerhacke, wish granted.

Here is a screenshot of my Enlightenment E17 desktop running on Edgy.

I'll see your E17 and raise you an E17 I just whipped together real quick.... with XMMS playing Hendrix!

---

### Post by gamma on 2007-01-07
Recently came back to Ubuntu after using OpenSuse for some time now. Things are definitely more responsive on Ubuntu. Multimedia support is a breeze to set up too! Using a Viva Pinata screenshot for a background. Great game and no it's not too kiddish :P.

[[img]http://home.cfl.rr.com/gamma/images/ss-t.png[/img]](http://home.cfl.rr.com/gamma/images/ss.png)

---

### Post by bvc on 2007-01-07
> **happy-and-lost said:**
> 
PS... does anyone have a clue how to get rid of those fugly handles either side of my dock?

Put about a 10x10px transparent .png in your home dir and this in .gtkrc-2.0
```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

Here's my simple [screenie]("http://gnomethemes.org/pre/screenshots/Zen.png")

---

### Post by tcrroadie on 2007-01-07
> **zerhacke said:**
> I'll see your E17 and raise you an E17 I just whipped together real quick.... with XMMS playing Hendrix!

Battle of the E17 desktops 'ey.  Changed my desktop up a little this morning.  Check this out.  Kachow.

---

### Post by finferflu on 2007-01-07
Enlightenment looks really cool! I've just installed, but I've still no clue about how it works... I need a bit of reading, and then I'll be back... I just wonder why it's not as popular as KDE and Gnome...

---

### Post by kriwil on 2007-01-07
my desktop: 

**Ubuntu 6.10 Edgy Eft**
Innocent emerald theme
Innocent gtk2 theme
nuoveXT-1.6 icon theme
[PixelBabies Devil Desktop]("http://www.pixelgirlpresents.com/images/desktops/pixelgirl/devil_1024.jpg") wallpaper
[078MKSDMediumCondensed]("http://aldi.kriwil.com/file_download/3") font
conky system monitor ([conkyrc]("http://aldi.kriwil.com/file_download/4"))

---

### Post by zerhacke on 2007-01-07
> **tcrroadie said:**
> Battle of the E17 desktops 'ey.  Changed my desktop up a little this morning.  Check this out.  Kachow.

Are those epplets in the top left and right corner?  How did you do that?  While I have E17 I really don't know much about it other than where to put the Theme files (~/.e/e/themes).

I know e16 had lots of epplets, but I can't find anything about them on E17.  How DID you do that?

---

### Post by finferflu on 2007-01-07
> **tcrroadie said:**
> Battle of the E17 desktops 'ey.  Changed my desktop up a little this morning.  Check this out.  Kachow.

Actually, where did you get that control panel??

---

### Post by _simon_ on 2007-01-07
Been a Gnome user for well over a year but installed KDE-core today and kbfx.

Had a little bit of a play:

[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_snapshot7.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/snapshot7.jpg)

---

### Post by _simon_ on 2007-01-07
> **finferflu said:**
> Actually, where did you get that control panel??

That's the normal E17 control panel.

---

### Post by Polygon on 2007-01-07
[[IMG]http://img440.imageshack.us/img440/5086/screenshotrt4.th.png[/IMG]](http://img440.imageshack.us/my.php?image=screenshotrt4.png)

---

### Post by finferflu on 2007-01-07
> **_simon_ said:**
> That's the normal E17 control panel.

well... ok.. how do you get it out! :D
Sorry, I feel a bit lost... If I right click on the desktop, I get a lot of configuration options, but no control panel...

---

### Post by _simon_ on 2007-01-07
I can't remember to be honest.

It's in either the right click or left click menu on the desktop.

---

### Post by finferflu on 2007-01-07
Right click doesn't work for me, it doesn't do anything....

EDIT: Ok, found the problem... I'm using E16... that's what I've found in the repositories...

---

### Post by killkoy on 2007-01-07
[[IMG]http://img384.imageshack.us/img384/2174/screenshotfc7.th.png[/IMG]](http://img384.imageshack.us/my.php?image=screenshotfc7.png)[[IMG]http://img247.imageshack.us/img247/4945/desktoppg5.th.png[/IMG]](http://img247.imageshack.us/my.php?image=desktoppg5.png)

---

### Post by fuscia on 2007-01-07
> **killkoy said:**
> [[IMG]http://img384.imageshack.us/img384/2174/screenshotfc7.th.png[/IMG]](http://img384.imageshack.us/my.php?image=screenshotfc7.png)[[IMG]http://img247.imageshack.us/img247/4945/desktoppg5.th.png[/IMG]](http://img247.imageshack.us/my.php?image=desktoppg5.png)

ooooooooooooooooh! nice wallpaper!

link?

---

### Post by Quillz on 2007-01-07
> **Polygon said:**
> [[IMG]http://img440.imageshack.us/img440/5086/screenshotrt4.th.png[/IMG]](http://img440.imageshack.us/my.php?image=screenshotrt4.png)
What dock is that?

---

### Post by BLTicklemonster on 2007-01-07
> **bvc said:**
> Put about a 10x10px transparent .png in your home dir and this in .gtkrc-2.0
```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

Here's my simple [screenie]("http://gnomethemes.org/pre/screenshots/Zen.png")


I have no gtkrc-2.0 so what do I do? I figured it was something easy like that, but wasn't sure where to look to find what to edit. I think if I could get rid of them love handles, the wimmin would find me sexier. :mrgreen:

I do have a .gtkrc-1.2-gnome2 but it says do not edit and has nothing configuration-like in it.

> # Autowritten by gnome-settings-daemon. Do not edit

include "/home/bill/.themes/Yattacier3/gtk/gtkrc"

include "/home/bill/.gtkrc.mine"

... and theres' no .gtkrc.mine in my /home/bill/ directory...

---

### Post by killkoy on 2007-01-07
> **fuscia said:**
> ooooooooooooooooh! nice wallpaper!

link?

[http://gnome-look.org/content/files/50434-autumn_fog.jpg](http://gnome-look.org/content/files/50434-autumn_fog.jpg)

[quote=Quillz]What dock is that?[/quote]
looks like gnome panel with icons on it

---

### Post by fuscia on 2007-01-07
> **killkoy said:**
> [http://gnome-look.org/content/files/50434-autumn_fog.jpg](http://gnome-look.org/content/files/50434-autumn_fog.jpg)


thank you.

---

### Post by tcrroadie on 2007-01-07
> **zerhacke said:**
> Are those epplets in the top left and right corner?  How did you do that?  While I have E17 I really don't know much about it other than where to put the Theme files (~/.e/e/themes).

I know e16 had lots of epplets, but I can't find anything about them on E17.  How DID you do that?

Everything you see on my desktop is standard issue E17 gadgets.  In the upper left hand corner is the pager, upper right is E17's clock of course, and at the bottom of the screen is E17's ibar.  E17 uses shelves to manage gadgets (pager, clock, ibar, ibox, and the start menu).

I am simply using 2 shelves.  One placed at the top and another shelf at the bottom.  If you right click on your shelf a menu will appear with options such as shelf configuration, shelf item movement and so forth.  Just play around with the options that are available in the menu and you'll figure it out in no time.  Your options are all most endless.  You can even place shelves and their contents on the sides of your desktop.  

I am using what I believe is the current release of E17 from CVS (I could be wrong).  Installing themes and additional wallpapers is dead simple now.  The current release of E17 now has tools for adding themes and wallpapers were in earlier releases you needed to add themes and wallpapers manually as you have stated.  Using Enlightenments configuration panel as shown in my last screen capture allows easy installation and selection of themes and wallpapers.  

Thanks for the feedback zerhacke.  This has been a lot of fun and I hope our screen captures of E17 will help other Ubuntu users give Enlightenment E17 a try.

---

### Post by ~LoKe on 2007-01-07
> **fuscia said:**
> the one on the left looks more like a maximized image file than a wallpaper (note the lack of panels).

That's the movie "A Scanner Darkly" in full screen.

---

### Post by fuscia on 2007-01-07
'kill B L'

---

### Post by m.musashi on 2007-01-08
> **tcrroadie said:**
> Thanks for the feedback zerhacke.  This has been a lot of fun and I hope our screen captures of E17 will help other Ubuntu users give Enlightenment E17 a try.

It has. I just installed E17. It's really cool but it will take some getting used to. I don't care for the file browser so much and the menu seems to bury stuff a bit deeper than gnome but I suspect a lot of this is configurable. It is very shiny with some neat effects. After 10 minutes I can't say whether or not it will be my new de but I'll keep playing. Thanks for the encouragement. I've been wanting to try this for some time. It always seemed a bit hard since it wasn't in the repos (only e16) but I found [this](http://www.ubuntuforums.org/showthread.php?t=319336&highlight=install+e17) thread and it couldn't have been easier.

---

### Post by kvonb on 2007-01-08
> **urukrama said:**
> I tried enlightenment once, but it made absolutely no sense to me. :D Just a blank space with some odd buttons that didn't seem to do anything and no right click menu. I didn't even know how to log back out. 

I'm sure there is something to it, but I didn't have the time and energy to try and find out.

Here here! Enlightenment always was weird, looks good, but weird :-k.

---

### Post by bvc on 2007-01-08
> **BLTicklemonster said:**
> I have no gtkrc-2.0 so what do I do? I figured it was something easy like that, but wasn't sure where to look to find what to edit. I think if I could get rid of them love handles, the wimmin would find me sexier. :mrgreen:

I do have a .gtkrc-1.2-gnome2 but it says do not edit and has nothing configuration-like in it.

... and theres' no .gtkrc.mine in my /home/bill/ directory...just create it. It's just a simple text file like the others. In fact you can open .gtkrc-1.2-gnome2 with a text editor, save it as .gtkrc-2.0, remove what's in it and put the handle code there.

You can control other aspects of the panel too.
```
#style "handle"
#{
#engine "pixmap"
#  {
#    image
#    {
#      function			= HANDLE
#      file              		= "pixel.png"
#      border            		= { 0, 0, 0, 0 }
#      stretch           		= TRUE
#      orientation			= VERTICAL
#    }
#    image
#    {
#      function			= HANDLE
#      file              		= "pixel.png"
#      border            		= { 0, 0, 0, 0 }
#      stretch           		= TRUE
#      orientation			= HORIZONTAL
#    }
#  }
#}
#class "PanelAppletFrame" style "handle"

#style "handle"
#{
#  bg[NORMAL]				= "#E9E864"
#}
#class "PanelAppletFrame" style "handle"

#style "panel-clock"
#{
#  fg[NORMAL] = "#FF0000"
#}
#widget "*.clock-applet-button.*" style "panel-clock"

#style "pager" {
#fg[NORMAL] = "#222222" # inactive workspaces
#fg[PRELIGHT] = "#880000" # mouseover
#fg[ACTIVE] = "#550000" # active workspace window background
#fg[SELECTED] = "#ffffff" # active workspace window wireframe
#bg[NORMAL] = "#101010" # background workspaces
#bg[PRELIGHT] = "#880000" # mouseover
#bg[SELECTED] = "#880000" # workspace active
#}
#widget "*WnckPager" style "pager"
```

---

### Post by RAV TUX on 2007-01-08
[[IMG]http://img180.imageshack.us/img180/6203/snapshot3cl2.th.png[/IMG]](http://img180.imageshack.us/my.php?image=snapshot3cl2.png).

---

### Post by kvonb on 2007-01-08
>  					Originally Posted by **BLTicklemonster: **if I could get rid of them love handles, the wimmin would find me sexier. :mrgreen:

You look scary  BL, but you certainly make me smile :D

---

### Post by BLTicklemonster on 2007-01-08
Mine right now

---

### Post by mcduck on 2007-01-08
> **bvc said:**
> just create it. It's just a simple text file like the others. In fact you can open .gtkrc-1.2-gnome2 with a text editor, save it as .gtkrc-2.0, remove what's in it and put the handle code there.

You can control other aspects of the panel too.
```
#style "handle"
#{
#engine "pixmap"
#  {
#    image
#    {
#      function			= HANDLE
#      file              		= "pixel.png"
#      border            		= { 0, 0, 0, 0 }
#      stretch           		= TRUE
#      orientation			= VERTICAL
#    }
#    image
#    {
#      function			= HANDLE
#      file              		= "pixel.png"
#      border            		= { 0, 0, 0, 0 }
#      stretch           		= TRUE
#      orientation			= HORIZONTAL
#    }
#  }
#}
#class "PanelAppletFrame" style "handle"

#style "handle"
#{
#  bg[NORMAL]				= "#E9E864"
#}
#class "PanelAppletFrame" style "handle"

#style "panel-clock"
#{
#  fg[NORMAL] = "#FF0000"
#}
#widget "*.clock-applet-button.*" style "panel-clock"

#style "pager" {
#fg[NORMAL] = "#222222" # inactive workspaces
#fg[PRELIGHT] = "#880000" # mouseover
#fg[ACTIVE] = "#550000" # active workspace window background
#fg[SELECTED] = "#ffffff" # active workspace window wireframe
#bg[NORMAL] = "#101010" # background workspaces
#bg[PRELIGHT] = "#880000" # mouseover
#bg[SELECTED] = "#880000" # workspace active
#}
#widget "*WnckPager" style "pager"
```

That's very nice, but would you happen to know how to get rid of the bars at the ends of the panel (when it's not expanded)? With Murrine themes the spacers aren't that ugly but the end bars are annoying with every GTK theme..

---

### Post by RAV TUX on 2007-01-08
[[IMG]http://img150.imageshack.us/img150/5683/snapshot5uy7.th.png[/IMG]](http://img150.imageshack.us/my.php?image=snapshot5uy7.png);)

---

### Post by yabbadabbadont on 2007-01-08
> **RAV TUX said:**
> [[IMG]http://img150.imageshack.us/img150/5683/snapshot5uy7.th.png[/IMG]](http://img150.imageshack.us/my.php?image=snapshot5uy7.png);)

What?!?  No bunnies?  ;) 

Do you actually have that game, or did you just download the image?  If you have the game, how do you like it?  I've seen it in the $9.99 bin a few times and have been tempted to get it.

---

### Post by _simon_ on 2007-01-08
> **finferflu said:**
> Right click doesn't work for me, it doesn't do anything....

EDIT: Ok, found the problem... I'm using E16... that's what I've found in the repositories...

HOWTO install E17

[http://www.ubuntuforums.org/showthread.php?t=319336&highlight=E17](http://www.ubuntuforums.org/showthread.php?t=319336&highlight=E17)

---

### Post by urukrama on 2007-01-08
> **killkoy said:**
> [[IMG]http://img384.imageshack.us/img384/2174/screenshotfc7.th.png[/IMG]](http://img384.imageshack.us/my.php?image=screenshotfc7.png)[[IMG]http://img247.imageshack.us/img247/4945/desktoppg5.th.png[/IMG]](http://img247.imageshack.us/my.php?image=desktoppg5.png)

Nice desktop picture. Do you have a link?

---

### Post by _simon_ on 2007-01-08
Loving title wave!

[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_January8.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/January8.jpg)

---

### Post by killkoy on 2007-01-08
> **urukrama]Nice desktop picture. Do you have a link?[/quote]
[QUOTE=killkoy said:**
> [http://gnome-look.org/content/files/50434-autumn_fog.jpg](http://gnome-look.org/content/files/50434-autumn_fog.jpg)
:p

---

### Post by ice60 on 2007-01-08
this is irssi running on xfce :cool: 

[[IMG]http://img394.imageshack.us/img394/3470/screenshotofirssirunninsr1.th.jpg[/IMG]](http://img394.imageshack.us/my.php?image=screenshotofirssirunninsr1.jpg)

---

### Post by ayoli on 2007-01-08
irssi fight ! :D
[[IMG]http://img465.imageshack.us/img465/4372/captureyz8.th.png[/IMG]](http://img465.imageshack.us/my.php?image=captureyz8.png)

---

### Post by kimara on 2007-01-08
Fvwm..

---

### Post by TheRingmaster on 2007-01-08
> **kimara said:**
> Fvwm..

Nice wallpaper

---

### Post by doobit on 2007-01-08
Ubuntu should make Conky standard in the next releases.

---

### Post by oyvindaa on 2007-01-08
This is my current desktop.

Theme: GTK Clearlooks
Icons: Human Azul2
Menu: USP

[Wallpaper](http://www.gnome-look.org/content/show.php?content=34251)

I used [this](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky) conky-setup, but removed the logging part and changed some of the colours.

---

### Post by serlex on 2007-01-08
[attach]22556[/attach]

any comments would be appreciated

---

### Post by BLTicklemonster on 2007-01-08
Getting in to making my own wallpapers. 

This is the one I posted earlier, but I added some family pictures. Hard to get the pics to stay sharp when you try moving them around in perspective trying to get them to fit, but still, it's kinda nice.

(serlex, that's one great looking set up)

---

### Post by m.musashi on 2007-01-08
> **serlex said:**
> [attach]22556[/attach]

any comments would be appreciated

Well, since you ask... Actually, it looks quite nice but personally I would think a theme that matched the green wallpaper a bit better would look nice. I don't know of any off the top of my head but you can probably find something nice on gnome-look. If you like the human icons (I think that's what you have, right?) you might look at the dropline icons ([http://www.gnome-look.org/content/show.php?content=38835)](http://www.gnome-look.org/content/show.php?content=38835)). They look pretty nice. Finally, I have removed my bottom panel and added a window selector to the top (and of course beryl makes a nice window switcher too if you can run it). I kind of like not having a bottom panel.

Of course, most of my desktops look kind of crummy so I wouldn't put too much stock in what I think :).

> **oyvindaa said:**
> This is my current desktop.

Theme: GTK Clearlooks
Icons: Human Azul2
Menu: USP

[Wallpaper](http://www.gnome-look.org/content/show.php?content=34251)

I used [this](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky) conky-setup, but removed the logging part and changed some of the colours.
Those are some pretty full hard drives (or are they empty?).

---

### Post by doobit on 2007-01-08
> **serlex said:**
> [attach]22556[/attach]

any comments would be appreciated

I really like green. Green is the color your brain is most sensitive to. It really makes one feel comfortable.

---

### Post by liquid boy on 2007-01-08
heres mine
the background is from [www.thatcloudgame.com](www.thatcloudgame.com)

---

### Post by fuscia on 2007-01-08
...

---

### Post by heathen on 2007-01-08
I just posted this in the fluxbox thread... but I figured I could post it here too...

[IMG]http://i19.photobucket.com/albums/b164/solenberg/january8.png[/IMG]

---

### Post by tbroderick on 2007-01-08
> **doobit said:**
> Ubuntu should make Conky standard in the next releases.

No.

---

### Post by doobit on 2007-01-08
> **tbroderick said:**
> No.
Come on!  Tell us how you really feel!
[IMG]http://www.louddata.com/dancsrn.jpg[/IMG]

---

### Post by Interestedinthepenguin on 2007-01-08
> **tbroderick said:**
> No.

I just curious, tbroderick.  Why not?

---

### Post by BOBSONATOR on 2007-01-08
Like it matters Penguin, all it takes is sudo apt-get install conky once you have enabled the multiverse packages.

---

### Post by bvc on 2007-01-08
> **mcduck said:**
> That's very nice, but would you happen to know how to get rid of the bars at the ends of the panel (when it's not expanded)? With Murrine themes the spacers aren't that ugly but the end bars are annoying with every GTK theme..No. It most likely can be done but a developer has not told us little themers howto yet. I only know how to exand the panel and use an image to make it look like it is not expanded. Like this
[http://gnomethemes.org/pre/screenshots/Gentle-Panel.png](http://gnomethemes.org/pre/screenshots/Gentle-Panel.png)
I haven't done this in a while but...hey....the crappy color is gone from the trans image! Cool! Wonder what upgrade fixed that?

---

### Post by Interestedinthepenguin on 2007-01-08
@BOBSONATOR

I know it doesn't matter. :neutral: 

 Like I said, in my last post, I was just curious.  

...and not all Ubuntu users have the net.

---

### Post by ~LoKe on 2007-01-08
> **heathen said:**
> I just posted this in the fluxbox thread... but I figured I could post it here too...

[[http://i19.photobucket.com/albums/b164/solenberg/january8.png](http://i19.photobucket.com/albums/b164/solenberg/january8.png)

Great!  Just a question; would something like Beryl even work in with Fluxbox?  I'd like to have all the effects, but I want the menus and whatnot that Fluxbox has. =[

---

### Post by heathen on 2007-01-08
dunno, last time i tried using beryl in gnome it locked up my computer....  I just figured I'd stick with what I know works...  My computer isnt old, but beryl and the i 915 graphics card in my laptop have not been known to get along well...

---

### Post by raul_ on 2007-01-08
No because Fluxbox IS a window manager..you can't use a window manager with another window manager. Gnome/KDE is a Desktop Environment with separate window managers (Gnome has metacity for example) whereas Fluxbox is a Desktop Environment/Window Manager

---

### Post by ~LoKe on 2007-01-08
**January 8, 2007**
[[IMG]http://img368.imageshack.us/img368/5540/0108071nz2.th.jpg[/IMG]](http://img368.imageshack.us/img368/5540/0108071nz2.jpg)

[img]http://img215.imageshack.us/img215/671/hpim0457cn1.jpg[/img]

---

### Post by m.musashi on 2007-01-08
> **raul_ said:**
> No because Fluxbox IS a window manager..you can't use a window manager with another window manager. Gnome/KDE is a Desktop Environment with separate window managers (Gnome has metacity for example) whereas Fluxbox is a Desktop Environment/Window Manager

I didn't know that. Learn something new... Is that the same with enlightenment? I just started playing with that but kind of would like to keep using beryl too. If not, are gnome and kde the only DEs that can use beryl or are there others?

---

### Post by raul_ on 2007-01-09
> **m.musashi said:**
> I didn't know that. Learn something new... Is that the same with enlightenment? I just started playing with that but kind of would like to keep using beryl too. If not, are gnome and kde the only DEs that can use beryl or are there others?

> Enlightenment, also known simply as E, is an open source window manager for the X Window System which can be used alone or in conjunction with a desktop environment such as GNOME or KDE.

Wikipedia ;)

---

### Post by crimesaucer on 2007-01-09
This is my new Desktop using Beryl 1.5-svn, Conky 1.4.5, and xubuntu 6.10. Artwork is Dozer Green. 

The .conkyrc is on page 2 from an earlier post: [http://www.ubuntuforums.org/showthread.php?t=328915&page=2](http://www.ubuntuforums.org/showthread.php?t=328915&page=2)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-16-4.png[/IMG]

this is a 10 picture slide show of my desktop theme: [http://s144.photobucket.com/albums/r161/crimesaucer/?action=view&current=1168342548.pbw](http://s144.photobucket.com/albums/r161/crimesaucer/?action=view&current=1168342548.pbw)

---

### Post by m.musashi on 2007-01-09
> **raul_ said:**
> Wikipedia ;)

Thanks for the tip. I read the wikipedia article but now I'm more confused. I thought E was analogous to gnome or kde since I can create an E session or gnome or kde. However, I cannot, as far as I know, have only a metacity session. According to the article though, E is more like metacity in that it can run with gnome or kde. Is that correct? If so, does that mean you can use gnome but have E be your window manager instead of metacity or beryl? Sorry, but the more I learn the more I find out what I don't know.

---

### Post by tbroderick on 2007-01-09
> **Interestedinthepenguin said:**
> I just curious, tbroderick.  Why not?

 Cause it's purely optional and should remain that way, IMO. I think Ubuntu should  focus on the core desktop and needed programs. Unless of course, Ubuntu releases a DVD edition.

---

### Post by yabbadabbadont on 2007-01-09
> **m.musashi said:**
> Thanks for the tip. I read the wikipedia article but now I'm more confused. I thought E was analogous to gnome or kde since I can create an E session or gnome or kde. However, I cannot, as far as I know, have only a metacity session. According to the article though, E is more like metacity in that it can run with gnome or kde. Is that correct? If so, does that mean you can use gnome but have E be your window manager instead of metacity or beryl? Sorry, but the more I learn the more I find out what I don't know.

Yes, you can replace either metacity or kwin with E if you wish.  I'm sure I've seen threads about it.  Of course, I might have seen them in the Gentoo forums as there is a massive collection of posts about E17 there.  (search for "E17 is coming part")  I know I've seen screenshots there of both Gnome and KDE using E17 as the window manager.

---

### Post by Tiede on 2007-01-09
I agree with you a hundred percent tbroderick. In the spirit of keeping ubuntu's install process clean and simple, it is way better to leave conky as an option then including it because it looks cool. One could argue about a lot of other gnome programs and their non-inclusion in ubuntu by default. All I am saying is, let ubuntu be simple, and we can all mod it to add what we feel suits us better - a typical user doesn't think about using conky that much any ways...

Bottom line, since ubuntu's philosophy (last time I heard it) was one task, one program, no need for conky because it looks better when you have the system monitor, the network applet always available, and other such nifty apps.

My 1.99 cents. And just to appease my conscience about this lengthy post, an updated screenie of my desktop follows as attachment.
The fish is from the egg Alt+F2 => free the fish
The wallpaper is Second Earth from Caedes.net
The icons are Glass-icons found on Gnome-look.org
GTK: Polycarbonate Dark
Metacity: Ater
Sliders on the side are just gnome-panels I've set hidden. (Anyone knows how to make them autohide with (as opposed to against) their orientation by the way - since they current won't autohide because their "opposite" side is not set at one of the screen's edges.
Finally, here is my .conkyrc:
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

# Xft font when Xft is enabled
#xftfont Sans:size=8
xftfont ubuntu-title:size=8

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 50 5

maximum_width 200

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font ubuntu-title
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
gap_y 20

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color white}SYSTEME ${hr 2}$color
$nodename running ${color FAC961}Ubuntu Edgy Eft$color
$sysname $kernel ($machine)
Temps de marche: ${uptime}
Batterie: ${battery BAT1}

${color white}CPU ${hr 2}$color
AMD Sempron ${freq}MHz   Temp: ${acpitemp}C
$cpubar
${cpugraph 00ff00 ffff00}
${color}Processus:$color $processes  ${color}Actifs:$color $running_processes
NOM               CPU%    MEM%
${top name 1}   ${top cpu 1}  ${top mem 1}
${top name 2}   ${top cpu 2}  ${top mem 2}
${top name 3}   ${top cpu 3}  ${top mem 3}
${top name 4}   ${top cpu 4}  ${top mem 4}

${color white}MEMOIRE / USAGE DES DISQUES ${hr 2}$color
RAM: ${mem}o/$memperc% Swap: ${swap}o/$swapperc%$color
${membar 6}$color
/linux:  ${fs_free /}o/${fs_size /}o
${fs_bar 6 /}$color 
/windows:  ${fs_free /media/hda2}o/${fs_size /home}o
${fs_bar 6 /media/hda2}$color

${color white}RESEAU (${addr eth1}) ${hr 2}$color
${color red}Entrant: ${downspeed eth1}k/s$color${alignr}${color green}Sortant: ${upspeed eth1}k/s$color
${downspeedgraph eth1 25,99 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,99 000000 00ff00}$color
Totaux des Telechargements:
Entres:${totaldown eth1}o ${alignr}Sortis:${totalup eth1}o

WiFi: ${linkstatus eth1}%

```

---

### Post by oyvindaa on 2007-01-09
> **m.musashi said:**
> 

Those are some pretty full hard drives (or are they empty?).
It's empty ;)

---

### Post by mcduck on 2007-01-09
> **bvc said:**
> No. It most likely can be done but a developer has not told us little themers howto yet. I only know how to exand the panel and use an image to make it look like it is not expanded. Like this
[http://gnomethemes.org/pre/screenshots/Gentle-Panel.png](http://gnomethemes.org/pre/screenshots/Gentle-Panel.png)
I haven't done this in a while but...hey....the crappy color is gone from the trans image! Cool! Wonder what upgrade fixed that?

That's what I was afraid of :(

It's about the only issue I have with Gnome that I haven't found a way to change.
I already know about the expanded panel with short background, it works very nice as long as long as your windows don't have drop shadows..

Btw, the color bug in panels disappeared when I moved from Dapper to Edgy, so I suppose it just was fixed in new Gnome.

---

### Post by doobit on 2007-01-09
> **Tiede said:**
> I agree with you a hundred percent tbroderick. In the spirit of keeping ubuntu's install process clean and simple, it is way better to leave conky as an option then including it because it looks cool. One could argue about a lot of other gnome programs and their non-inclusion in ubuntu by default. All I am saying is, let ubuntu be simple, and we can all mod it to add what we feel suits us better - a typical user doesn't think about using conky that much any ways...

Bottom line, since ubuntu's philosophy (last time I heard it) was one task, one program, no need for conky because it looks better when you have the system monitor, the network applet always available, and other such nifty apps.



Well, my original comment was only meant as an emotional outburst of positive sentiment toward the beautiful addition that Conky is to most of the coolest desktops being displayed here. FYAI, one of the smallest distros - DamnSmall Linux - uses Conky's parent (torsmo) as a standard include, along with two Window managers, and the whole distro is only 50 MB.

---

### Post by fuscia on 2007-01-09
what can i say? i'm a sucker for eye candy.

---

### Post by raul_ on 2007-01-09
> **fuscia said:**
> what can i say? i'm a sucker for eye candy.

Staying true to the fonts i see

---

### Post by finferflu on 2007-01-09
Ok, I'm now enlightened. E17 is just gorgeous.

---

### Post by fuscia on 2007-01-09
> **raul_ said:**
> Staying true to the fonts i see

first me, then, the world!

---

### Post by zerhacke on 2007-01-09
> **finferflu said:**
> Ok, I'm now enlightened. E17 is just gorgeous.

Ooh, the Milk theme.  I'm using that right now too.

---

### Post by tigerpants on 2007-01-09
E17 install on my laptop. I love enlightenmet :)

---

### Post by wildkarde on 2007-01-09
Nothing fancy...

---

### Post by INMCM on 2007-01-09
It's Clango-tastic:
[http://ewh.ieee.org/sb/louisville/ul/pics/Screenshot.png](http://ewh.ieee.org/sb/louisville/ul/pics/Screenshot.png)

---

### Post by tcrroadie on 2007-01-09
> **tigerpants said:**
> E17 install on my laptop. I love enlightenmet :)

Awsome tigerpants.  Question for ya.  How did you get window management tabs to display on your shelf like that?  Must be an option I have missed in the shelf config menu.  Starting to get the shakes and going through withdrawls.  Haven't played with E17 since Sunday morning. Been busy. Must play tonight.  I need my E.

---

### Post by tcrroadie on 2007-01-09
> **finferflu said:**
> Ok, I'm now enlightened. E17 is just gorgeous.

Sweet fingerflu.  Keep em comming.  

I'll try to post some more of mine tonight.

---

### Post by finferflu on 2007-01-09
> **tcrroadie said:**
> Awsome tigerpants.  Question for ya.  How did you get window management tabs to display on your shelf like that?  Must be an option I have missed in the shelf config menu.  Starting to get the shakes and going through withdrawls.  Haven't played with E17 since Sunday morning. Been busy. Must play tonight.  I need my E.

I'll answer in his/her behalf, just because I'm quicker :P
You have to enable that module from the modules menu, before it appears in the shelf contents configuration menu. Right-click on the desktop, Configuration > Configuration Panel > Extensions > Modules, and select Taskbar from the list and enable it. Then go in the shelf contents configuration and you'll find it in the list of items.

> **tcrroadie said:**
> Sweet fingerflu.  Keep em comming.  

I'll try to post some more of mine tonight.

Thanks! I didn't put so much effort in it, it's just my first experiment on how to configure things and testing an animated wallpaper (very classy!).

---

### Post by fuscia on 2007-01-09
...

---

### Post by Jaygo333 on 2007-01-09
> **testube_babies said:**
> A fresh year, a fresh install of Ubuntu + XP.

[[IMG]http://img357.imageshack.us/img357/8126/ubuntushotuy9.th.jpg[/IMG]](http://img357.imageshack.us/my.php?image=ubuntushotuy9.jpg) [[IMG]http://img517.imageshack.us/img517/6835/cubean8.th.jpg[/IMG]](http://img517.imageshack.us/my.php?image=cubean8.jpg) [[IMG]http://img357.imageshack.us/img357/4042/xpshotqk8.th.jpg[/IMG]](http://img357.imageshack.us/my.php?image=xpshotqk8.jpg)

How did you manage to have your Linux Partition show up in Windows.
Teach... been trying for two years now with partial success.

---

### Post by tcrroadie on 2007-01-09
> **finferflu said:**
> I'll answer in his/her behalf, just because I'm quicker :P
You have to enable that module from the modules menu, before it appears in the shelf contents configuration menu. Right-click on the desktop, Configuration > Configuration Panel > Extensions > Modules, and select Taskbar from the list and enable it. Then go in the shelf contents configuration and you'll find it in the list of items.

Thanks fingerflu.  I'll give it a try after work this evening, and see if I prefer the taskbar tabs over the application icons when windows are minimized.  I don't even remember seeing it in the modules menu.  I disabled most of the modules after I installed E17 nearly a month ago and have'nt looked at the menu since.

---

### Post by BLTicklemonster on 2007-01-09
> **Jaygo333 said:**
> How did you manage to have your Linux Partition show up in Windows.
Teach... been trying for two years now with partial success.

Indeed. All I can find is on ext2 or 3, but I'm running rieser fs and want to see it in xp.

---

### Post by manmower on 2007-01-09
> **Jaygo333 said:**
> How did you manage to have your Linux Partition show up in Windows.
Teach... been trying for two years now with partial success.

I think he/she's just got the Ubuntu CD in a CD/DVD drive.
EDIT: never mind I see what you mean, I guess Ext2IFS.

---

### Post by m.musashi on 2007-01-09
> **Jaygo333 said:**
> How did you manage to have your Linux Partition show up in Windows.
Teach... been trying for two years now with partial success.

It's also possible that it's a fat32 drive that he uses to share files rather than an actual linux formated drive. Of course it could be so we'll just have to wait for the official explanation.

---

### Post by TheRingmaster on 2007-01-09
for the clown inside all of us

---

### Post by tigerpants on 2007-01-09
> **finferflu said:**
> I'll answer in his/her behalf, just because I'm quicker :P
You have to enable that module from the modules menu, before it appears in the shelf contents configuration menu. Right-click on the desktop, Configuration > Configuration Panel > Extensions > Modules, and select Taskbar from the list and enable it. Then go in the shelf contents configuration and you'll find it in the list of items.



Thanks! I didn't put so much effort in it, it's just my first experiment on how to configure things and testing an animated wallpaper (very classy!).

Well fielded :) 

Hmm.... E17....

---

### Post by zerhacke on 2007-01-09
> **Jaygo333 said:**
> How did you manage to have your Linux Partition show up in Windows.
Teach... been trying for two years now with partial success.

There's some software on Sourceforge that will let you mount an ext2/3 partition in Windows.

Ext2FSD I think it's called.

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

---

### Post by raul_ on 2007-01-09
What about FS-drivers for windows?

---

### Post by SmiLey497 on 2007-01-09
mine, ubuntu firebox wallpaper, beryl dreamtiger emerald theme

---

### Post by finferflu on 2007-01-09
Ah, by the way, I think that E17 is a very good replacement for Beryl for me, since I can't install it anyway... I can't believe I'm ok also without wobbling windows!

---

### Post by ComplexNumber on 2007-01-09
here's my latest. i quite fancied a nice green this week/month.

Gtk: Murrina-Olive
Metacity: Murrine
Icons: JiniYellowishGreen
Wallpaper: wethetrees

---

### Post by crimesaucer on 2007-01-09
Hey, if you like the green window themes, you might like these Emerald themes I made:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-10-4.png[/IMG]

---

### Post by ComplexNumber on 2007-01-09
**crimesaucer**
what are they called?
 to tell you the truth, i'm not really into beryl/compiz or any of that sort of thing. a plain old attractive 2D desktop with no effects does me just fine.

---

### Post by bvc on 2007-01-09
> **mcduck said:**
> 
Btw, the color bug in panels disappeared when I moved from Dapper to Edgy, so I suppose it just was fixed in new Gnome.I'm still dapper

---

### Post by doobit on 2007-01-09
> **ComplexNumber said:**
> here's my latest. i quite fancied a nice green this week/month.

Gtk: Murrina-Olive
Metacity: Murrine
Icons: JiniYellowishGreen
Wallpaper: wethetrees

I like that! I am also into green right now. Must be the winter month's wish.

---

### Post by BLTicklemonster on 2007-01-09
for reiserfs in windows, if anyone wants to know:

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=nFg&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=access+reiserfs+partitions+from+windows&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=nFg&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=access+reiserfs+partitions+from+windows&spell=1)

now let me know which one works, mk?

---

### Post by ComplexNumber on 2007-01-09
> **doobit said:**
> I like that! I am also into green right now. Must be the winter month's wish.
cheers. i like it too, and its a compliment to cimi's themes(eg murrina etc). i think he makes the colours nice and the widgets attractive with the the help of his murrina theme engine.
its very dull, windy, ,rainy,and grey here in the UK at the moment, so maybe the green is a manifestation of some subconscious longing for the spring and to see some green on the trees.

i'm thinking of writing some sort of theming guide at some point (whether i do or not is a different matter) entitled something along the lines of "ComplexNumber's guide on theming, harmony, and colour balance". i have lots of themes and lots of wallpapers, and its just a guide to find the most attractive combination for various types of wallpaper(eg black & wite wp, hightly colourful wp, monocolour wp, and minimalistic wp, etc) and themes. its just my take on it as there are no right and wrong ways.

---

### Post by darkhatter on 2007-01-09
[[IMG]http://img478.imageshack.us/img478/5874/snapshot1xk2.th.png[/IMG]](http://img478.imageshack.us/my.php?image=snapshot1xk2.png)

kde
beryl (+xglsnow)

nothing special, I'm trying to keep it clean

---

### Post by ComplexNumber on 2007-01-09
> **darkhatter said:**
> [[IMG]http://img478.imageshack.us/img478/5874/snapshot1xk2.th.png[/IMG]]("http://img478.imageshack.us/my.php?image=snapshot1xk2.png")

kde
beryl (+xglsnow)

nothing special, I'm trying to keep it clean
is that that snow plugin thing for beryl? personally, i can't see the point of it all.

---

### Post by darkhatter on 2007-01-09
> **ComplexNumber said:**
> is that that snow plugin thing for beryl? personally, i can't see the point of it all.

there is no point, really really really useless. I got no snow on Christmas so this plugin is about as close as I'm going to get :-D

---

### Post by crimesaucer on 2007-01-09
@ComplexNumber

The theme was originally called "scaled black", it came with Emerald themes. I changed everything from colors to shape, roundness, button placement, added a "set above" button and icon, changed all of the sizes of all four sides, and changed font/size/colors.

If you want to know how to set the blends, curves, contrasts, notches, glows, and outlines, let me know. I also can give you the stats for shadows and all the other settings.

The colors are just from my desktop, the numbers are the opacity. Blue 73/White 92/Blue 73 and White73 /Green 92/White 73

green=7BAC0D
blue=1566FA
white=000000

And also, the snow plug in is pretty cool to customize, I usually run it with the settings low because it sort of bugs out my Thunderbird. This is how I customized mine:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-3.png[/IMG]

That also is my customized splash plug-in for Beryl. The splash background is available on the Beryl wiki, and the black gem was from the wiki and deviant art. I cropped the gem, added the same space-invader I use with my snow/bubble plug-in, and added it to the white splash background from the wiki page. I thought the new 1.5-svn looked sort of ugly with the burning gem.

And to everybody, I'm sorry about the size of my Photobucket images, I probably should use imageshack for this.

---

### Post by cstudent on 2007-01-09
I haven't posted one for awhile. I'm currently using the Peace theme on my desktop.

[[IMG]http://img293.imageshack.us/img293/1014/jan2007zb4.th.png[/IMG]](http://img293.imageshack.us/my.php?image=jan2007zb4.png)

---

### Post by ComplexNumber on 2007-01-09
> **darkhatter said:**
> there is no point, really really really useless. I got no snow on Christmas so this plugin is about as close as I'm going to get :-D
i had a nice snowy christmasy wallpaper for the chrismas period instead :D.



**crimesaucer**
are you a kde user by any chance? :D. the amount of configuration options possible seems a tad overwhelming to me. i don't think i'd know where to start.
i haven't seen your theme around (gnome-look etc). there is a nice lime coloured emerald them called ghost edge lime (i think)

---

### Post by urukrama on 2007-01-10
> **ComplexNumber said:**
> 
Metacity: Murrine

Where did you get that Metacity theme? I couldn't find it.

---

### Post by ComplexNumber on 2007-01-10
> **urukrama said:**
> Where did you get that Metacity theme? I couldn't find it.
just type "murrine" into gnome-look. [here]("http://gnomethemes.org/?p=52")'s a direct link.

---

### Post by fuscia on 2007-01-10
openbox, pypanel and beep with the EVO skin (i think i got it from winamp). i just spent the morning purging DE/wms i don't want. how pleasant and simple.

---

### Post by doobit on 2007-01-10
This thread convinced me tro try Enlightnement on my old AMD machine. It works great, and I love it! I also customized my old Xfce desktop radically.

---

### Post by finferflu on 2007-01-10
> **fuscia said:**
> openbox, pypanel and beep with the EVO skin (i think i got it from winamp). i just spent the morning purging DE/wms i don't want. how pleasant and simple.

I love your customization, apart from the blue you chose for the font in the taskbar (I guess it's called pypanel)...

> **doobit said:**
> This thread convinced me tro try Enlightnement on my old AMD machine. It works great, and I love it! I also customized my old Xfce desktop radically.
Send us screenshots!! :D

---

### Post by tigerpants on 2007-01-10
> **doobit said:**
> This thread convinced me tro try Enlightnement on my old AMD machine. It works great, and I love it! I also customized my old Xfce desktop radically.

Enlightenment is aptly named. I'll certainly won't be using Gnome or KDE again, although I still love Fluxbox.

---

### Post by BLTicklemonster on 2007-01-10
I ran conky with gnome, icewm, fluxbox, E17, and others, and I was amazed that of all of them, E17 ran with the least amount of ram usage, cpu load, and processes. 


but I do so love fluxbox...

---

### Post by doobit on 2007-01-10
> **finferflu said:**
> 

Send us screenshots!! :D

OK!
[IMG]http://www.louddata.com/danscrn3.jpg[/IMG]

---

### Post by finferflu on 2007-01-10
> **BLTicklemonster said:**
> I ran conky with gnome, icewm, fluxbox, E17, and others, and I was amazed that of all of them, E17 ran with the least amount of ram usage, cpu load, and processes. 


but I do so love fluxbox...

I haven't tested them like you did, but I've tried all of them, and I have noticed that E17 is incredibly fast despite its amazing eyecandy. I've just learnt that it's based on FVWM, and I understand why, now. I think that FVWM is great, but it's just too much work to customize it. 

Anyway, thanks for the stats :)

---

### Post by crimesaucer on 2007-01-10
@ ComplexNumber- No, I use xfce4 with xubuntu 6.10/ Beryl AiGlX 1.5-svn/ Emerald 1.5-svn/ and Conky 1.4.5

The window theme is originally called "scaled black" and came with the Emerald themes with the install for Beryl 1.1 and Emerald 1.1. Then I modified and customized everything. You can create any window theme you want with a choice of 5 engines. I chose to use scaled black because of the cool pixmap buttons and the easy to use vrunner engine. Then everything else is my creation.
 
The vrunner engine and tru-glass are my favorites, vrunner allows a three color horizontal fade, where as tru-glass is a vertical fade with a glow in the middle. I'm still perfecting the shadows in tru-glass so I mostly use vrunner.

As for customization, I just recently started to actually use Beryl, when I installed 1.1, I just had a regular cube, and no animations or visual effects. Now I have all the plug-ins that I like working for 1.5-svn and it hasn't slowed my computer down at all. It barely uses cpu and mem, and after messing around with some of the settings in the Beryl Manager, I now have all of my colors and animation speeds to exactly where I want them (at least I think so, I'm still learning Beryl's settings a bit).

---

### Post by m.musashi on 2007-01-10
> **BLTicklemonster said:**
> I ran conky with gnome, icewm, fluxbox, E17, and others, and I was amazed that of all of them, E17 ran with the least amount of ram usage, cpu load, and processes. 


but I do so love fluxbox...

You managed to get conky to run with e17? Did you have to change anything? I installed e17 the other day and tried to run conky but nothing happened. I thought maybe it wasn't supported.

---

### Post by BLTicklemonster on 2007-01-10
> **finferflu said:**
> I haven't tested them like you did, but I've tried all of them, and I have noticed that E17 is incredibly fast despite its amazing eyecandy. I've just learnt that it's based on FVWM, and I understand why, now. I think that FVWM is great, but it's just too much work to customize it. 

Anyway, thanks for the stats :)

I took screenshots, but I'm too lazy to put them up. For each instance, I ran xmms on a shoutcast station, logged into the same 4 pages here in firefox, and ran conky of course.

But I was amazed. I really wasn't going to even check E17, but I remember someone telling me that it was supposed to be amazingly fast.

They were right.

---

### Post by BLTicklemonster on 2007-01-10
Bah, I'm over my laziness. 

here they are


Beryl in gnome, of course
[[IMG]http://img356.imageshack.us/img356/5989/conkyberylcs2.th.png[/IMG]](http://img356.imageshack.us/my.php?image=conkyberylcs2.png)

FluxBox
[[IMG]http://img90.imageshack.us/img90/7056/conkyfluxfi5.th.png[/IMG]](http://img90.imageshack.us/my.php?image=conkyfluxfi5.png)

FVWM
[[IMG]http://img90.imageshack.us/img90/6199/conkyfvwmou3.th.png[/IMG]](http://img90.imageshack.us/my.php?image=conkyfvwmou3.png)

FVWMCrystal
[[IMG]http://img166.imageshack.us/img166/9199/conkyfvwmcrystaluz7.th.png[/IMG]](http://img166.imageshack.us/my.php?image=conkyfvwmcrystaluz7.png)

Gnome
[[IMG]http://img368.imageshack.us/img368/1694/conkygnomevu2.th.png[/IMG]](http://img368.imageshack.us/my.php?image=conkygnomevu2.png)

Sorry if this is a hijack! The other five I tested are in a following post.

---

### Post by BLTicklemonster on 2007-01-10
Icewm
[[IMG]http://img412.imageshack.us/img412/7169/conkyicewmcv5.th.png[/IMG]](http://img412.imageshack.us/my.php?image=conkyicewmcv5.png)

Kubuntu Desktop
[[IMG]http://img487.imageshack.us/img487/8598/conkykdeyw2.th.png[/IMG]](http://img487.imageshack.us/my.php?image=conkykdeyw2.png)

WindowMaker
[[IMG]http://img379.imageshack.us/img379/9858/conkywindowmakerwe2.th.png[/IMG]](http://img379.imageshack.us/my.php?image=conkywindowmakerwe2.png)

XFCE4
[[IMG]http://img379.imageshack.us/img379/4997/conkyxfce4pz3.th.png[/IMG]](http://img379.imageshack.us/my.php?image=conkyxfce4pz3.png)

And E17
[[IMG]http://img373.imageshack.us/img373/8831/conkye17ih0.th.png[/IMG]](http://img373.imageshack.us/my.php?image=conkye17ih0.png)

Sorry again.

---

### Post by ComplexNumber on 2007-01-10
**BLTicklemonster**
no offence or anything, but do you actually find those screenshots attractive, or are they just to demonstrate those monitors?  those meters are not even slightly readable or practical.

---

### Post by BLTicklemonster on 2007-01-10
lmao, they aren't meant to show off my desktop. I was just showing conky info for ten different window managers.

(you do know you can click then and view them full screen, right?)

---

### Post by m.musashi on 2007-01-10
> **m.musashi said:**
> You managed to get conky to run with e17? Did you have to change anything? I installed e17 the other day and tried to run conky but nothing happened. I thought maybe it wasn't supported.

Okay, I manged to get conky to run by using own_window yes but that puts it in a rather ugly window. Does anyone know if know if it can be done ala gnome (no window, transparent, etc)?

It looks like it's also in a window in BLTicklemonster's screenshot.

---

### Post by tenjin1 on 2007-01-10
This is my desktop on Breezy 5.10 w/ wallpaper from gnome-look.org, gdesklets and buuf/misc. icons:
[[IMG]http://img404.imageshack.us/img404/8017/new2uv8.th.png[/IMG]](http://img404.imageshack.us/my.php?image=new2uv8.png)

This is the same desktop running DixX-toDVD, Xmms and Nautilus:
[[IMG]http://img90.imageshack.us/img90/7011/new3pm5.th.png[/IMG]](http://img90.imageshack.us/my.php?image=new3pm5.png)

Here is an older screenie...IE on M$.com trying to update Win:
[[IMG]http://img145.imageshack.us/img145/8653/ieinlinux2fc0.th.png[/IMG]](http://img145.imageshack.us/my.php?image=ieinlinux2fc0.png)

---

### Post by ComplexNumber on 2007-01-10
> **BLTicklemonster said:**
> lmao, they aren't meant to show off my desktop. I was just showing conky info for ten different window managers.

(you do know you can click then and view them full screen, right?)
yeah, sure. i was just wondering thats all. i would find them quite a strain on the eyes

---

### Post by fuscia on 2007-01-10
openbox, pypanel, modified europa theme and a wallpaper from interfacelift...

---

### Post by BLTicklemonster on 2007-01-11
> **ComplexNumber said:**
> yeah, sure. i was just wondering thats all. i would find them quite a strain on the eyes
Oh, okay. I don't leave conky sitting on my desktop. It's a total annoyance no matter how it looks. But it's a great tool.

---

### Post by BLTicklemonster on 2007-01-11
> **m.musashi said:**
> You managed to get conky to run with e17? Did you have to change anything? I installed e17 the other day and tried to run conky but nothing happened. I thought maybe it wasn't supported.
OH, sorry, just saw this. I didn't do anything different. Just typed conky in the terminal.

---

### Post by kvonb on 2007-01-11
> **tenjin1 said:**
> This is my desktop on Breezy 5.10 w/ wallpaper from gnome-look.org, gdesklets and buuf/misc. icons:
[[IMG]http://img404.imageshack.us/img404/8017/new2uv8.th.png[/IMG]]("http://img404.imageshack.us/my.php?image=new2uv8.png")

Very nice layout :).

I searched through 64 pages of wallpapers on gnome-look and couldn't find the wallpaper, can you either make it available for d/l or give the exact name so that I can grab it?

Thanks, Kev :)

---

### Post by kvonb on 2007-01-11
> **fuscia said:**
> openbox, pypanel, modified europa theme and a wallpaper from interfacelift...

Fuscia, I am now thoroughly convinced that you are an alien!  Welcome to our humble planet.....hahaha :).

---

### Post by fuscia on 2007-01-11
> **kvonb said:**
> Fuscia, I am now thoroughly convinced that you are an alien!  Welcome to our humble planet.....hahaha :).

gosh, thanks!

---

### Post by finferflu on 2007-01-11
> **tenjin1 said:**
> This is my desktop on Breezy 5.10 w/ wallpaper from gnome-look.org, gdesklets and buuf/misc. icons:


I'm just curious, why do you still use Breezy? You're not the only one actually, and since I've seen many people still on older versions, I'm just curious about the reason...

---

### Post by tenjin1 on 2007-01-11
Hey, thx Kev for the comment!

> Very nice layout .

I searched through 64 pages of wallpapers on gnome-look and couldn't find the wallpaper, can you either make it available for d/l or give the exact name so that I can grab it?

Thanks, Kev 

yes the wallpaper is on gnome-look.org but is kinda hidden...anyway you can grab it here:
[http://www.bergamasterz.com/ubuntu/ubuntu_wire.jpg]("http://www.bergamasterz.com/ubuntu/ubuntu_wire.jpg")

> I'm just curious, why do you still use Breezy? You're not the only one actually, and since I've seen many people still on older versions, I'm just curious about the reason...

This is one of my pc's which is kinda my primary one (I use it alot), but my other pc is running Dapper, which I hope to upgrade to Edgy soon! As for the reason why still running Breezy.... it's just that there is so much custumization done to it that I'm just lazy to go back and custumize it after an clean install (usually don't upgrade since have had problems). But 5.10 seems to be running fine and no problems really, except for the fact some apps are only made for Dapper and Edgy (Automatix2 for example)

---

### Post by finferflu on 2007-01-11
> **tenjin1 said:**
> 
This is one of my pc's which is kinda my primary one (I use it alot), but my other pc is running Dapper, which I hope to upgrade to Edgy soon! As for the reason why still running Breezy.... it's just that there is so much custumization done to it that I'm just lazy to go back and custumize it after an clean install (usually don't upgrade since have had problems). But 5.10 seems to be running fine and no problems really, except for the fact some apps are only made for Dapper and Edgy (Automatix2 for example)

Thank you :)

---

### Post by ComplexNumber on 2007-01-11
> **kvonb said:**
> Fuscia, I am now thoroughly convinced that you are an alien!  Welcome to our humble planet.....hahaha :).
what? you've only just found out? fuscia is from The Land of the Longleaf Pine, way away in the constellation known as Plaideas. 
although they are generally open minded, their race have a tendency to be fickle. whats more, it has been proven scientifically that all members of their planet have an innate preference for openbox.

---

### Post by fuscia on 2007-01-11
this should probably be another thread, but seriously, don't you ever wonder why aliens don't stay here? i think singing drives them away. think about it: if your primary means of communication is telepathy, what are you really going to make out of singing?

---

### Post by ComplexNumber on 2007-01-11
> **fuscia said:**
> this should probably be another thread, but seriously, don't you ever wonder why aliens don't stay here? i think singing drives them away. think about it: if your primary means of communication is telepathy, what are you really going to make out of singing?
well, thats understandable when britney spears sings here.



just to keep this thread on topic, i'm going to have a blue theme soon that i'm going to post. this accurately reflects the whether here at the moment.

---

### Post by der_joachim on 2007-01-11
[Clicky]("http://members.home.nl/der-joachim/shot_20070111.jpg").

The background is mine. I shot it last September near Badwater, Death Valley, USA. The icon theme is NuoveXT (in universe IIRC). My .conkyrc is pretty standard and honestly not very interesting.

---

### Post by aionea on 2007-01-11
[Clean]("http://mbnet.fi/chap/clean.png")
[Busy]("http://mbnet.fi/chap/busy.png")

KDE: Polyester
Beryl: modified kind_of_dull_orange
Icons: crystal diamond

---

### Post by kevinf311 on 2007-01-11
As promised (pages ago :rolleyes: ) [here]("http://i126.photobucket.com/albums/p114/kevinf311/moo.jpg?t=1168540954") is my desktop. It's nothing super special, but it works for me. I added a joke folder to show more of the icon set I use (amaranth I think).

Next month I should have a Beryl/Edgy desktop to show off :D

---

### Post by crimesaucer on 2007-01-11
@ aionea- That's a cool theme color. The desktop is pretty crazy too.

---

### Post by fuscia on 2007-01-11
almost made it a whole day without posting a screenshot. this is my lame imitation of dreamlinux...

---

### Post by hoagie on 2007-01-11
> **aionea said:**
> [Clean]("http://mbnet.fi/chap/clean.png")
[Busy]("http://mbnet.fi/chap/busy.png")

KDE: Polyester
Beryl: modified kind_of_dull_orange
Icons: crystal diamond

Cab you link your wallpaper please?

---

### Post by truthfatal on 2007-01-11
Yay for screenshots.

[url=http://www.truthfatal.org/scrot/2007-01-11-040412_1600x1200_scrot.png][IMG]http://www.truthfatal.org/scrot/thumb/2007-01-11-040412_192x144_scrot-thumb.png[/IMG]
1600x1200[/url]

---

### Post by tenjin1 on 2007-01-11
> **kevinf311 said:**
> As promised (pages ago :rolleyes: ) [here]("http://i126.photobucket.com/albums/p114/kevinf311/moo.jpg?t=1168540954") is my desktop. It's nothing super special, but it works for me. I added a joke folder to show more of the icon set I use (amaranth I think).

Next month I should have a Beryl/Edgy desktop to show off :D

Haha..I like that apt-get moo...I've seen that before somewhere under "easter eggs in ubuntu" (or something like that)

---

### Post by yabbadabbadont on 2007-01-11
> **tenjin1 said:**
> Haha..I like that apt-get moo...I've seen that before somewhere under "easter eggs in ubuntu" (or something like that)

"emerge moo" does the same thing in Gentoo.  :)

---

### Post by Cirdan7 on 2007-01-11
Here is mine:

[Desktop](http://www.christiangaming.org/graphics/users/stormtrooper/desktop.png)
[Desktop Cube](http://www.christiangaming.org/graphics/users/stormtrooper/cube.png)

---

### Post by m.musashi on 2007-01-11
Well, here is something I've been working on for a while. It's nothing fancy theme-wise, but it's my 100% ubuntu lappy. I haven't the courage to do this my main desktop yet but baby steps should count for something. *insert applause here*

The other is a screen of my e17 install on the same lappy. I think it looks wonderful but I haven't adapted to it enough to find it very useful for me. Oh well, I'll just keep playing

EDIT: oh, no beryl here. It has an ati card and I haven't been able to get it to work. boo hoo

---

### Post by DrClaw27 on 2007-01-11
You sould give the artist credit that you took it from.

---

### Post by fuscia on 2007-01-11
flwm, with the only wallpaper i would ever use for it, and mp3blaster...

---

### Post by hk_2999 on 2007-01-12
A bit dark...

[[IMG]http://img02.picoodle.com/img/img02/7/1/12/t_Screenshi_913am_003f0ed5.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/7/1/12/f_Screenshi_913am_003f0ed5.png)

---

### Post by NeoChaosX on 2007-01-12
[January desktop for me](http://ubuntuforums.org/gallery/showphoto.php/photo/4699).

I'm gaining more of an appreciation for simple, cleaner background images now.

---

### Post by aionea on 2007-01-12
> **hoagie said:**
> Cab you link your wallpaper please?

[http://www.deviantart.com/deviation/31330067/](http://www.deviantart.com/deviation/31330067/)

---

### Post by tonyisntcreative on 2007-01-12
Clean
[[IMG]http://img142.imageshack.us/img142/9264/screenshotxi6.th.png[/IMG]](http://img142.imageshack.us/my.php?image=screenshotxi6.png)

What I'm workin' with
[[IMG]http://img142.imageshack.us/img142/7729/screenshot1dp3.th.png[/IMG]](http://img142.imageshack.us/my.php?image=screenshot1dp3.png)

---

### Post by GarethMB on 2007-01-12
Tinkering with E17 lately. It looks beautiful and it does what it does very nicely but there's a lot it doesn't do.

---

### Post by fuscia on 2007-01-12
> **GarethMB said:**
> Tinkering with E17 lately. It looks beautiful and it does what it does very nicely but there's a lot it doesn't do.

it's pretty fast, too, but i find it awkward to use.

---

### Post by m.musashi on 2007-01-12
> **fuscia said:**
> it's pretty fast, too, but i find it awkward to use.

Ditto on both of those.

---

### Post by RoLanRok on 2007-01-12
Still working on the theme, but right now it's the default human theme with eXperience icons from Gnome Art.
Wallpaper is the third one in this list [http://www.telltalegames.com/samandmax/avatars](http://www.telltalegames.com/samandmax/avatars)
The graphics on the panel are changed to XP like ones.

[[IMG]http://img225.imageshack.us/img225/7892/ubdesktopsmjj8.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=ubdesktopsmjj8.jpg)

[[IMG]http://img84.imageshack.us/img84/1350/ubscvv5.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=ubscvv5.jpg)

---

### Post by JoeC21 on 2007-01-12
My current setup...

[[img]http://joec21.googlepages.com/thumb-011107.png[/img]](http://joec21.googlepages.com/011107.jpg)

---

### Post by m.musashi on 2007-01-12
> **RoLanRok said:**
> Still working on the theme, but right now it's the default human theme with eXperience icons from Gnome Art.
Wallpaper is the third one in this list [http://www.telltalegames.com/samandmax/avatars](http://www.telltalegames.com/samandmax/avatars)
The graphics on the panel are changed to XP like ones.

[[IMG]http://img225.imageshack.us/img225/7892/ubdesktopsmjj8.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=ubdesktopsmjj8.jpg)

[[IMG]http://img84.imageshack.us/img84/1350/ubscvv5.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=ubscvv5.jpg)

How did you get the xp-like task bar? I bet I could install Ubuntu for some reluctant users and with that they would never know the difference. Devious.

---

### Post by raul_ on 2007-01-12
> **RoLanRok said:**
> Still working on the theme, but right now it's the default human theme with eXperience icons from Gnome Art.
Wallpaper is the third one in this list [http://www.telltalegames.com/samandmax/avatars](http://www.telltalegames.com/samandmax/avatars)
The graphics on the panel are changed to XP like ones.

[[IMG]http://img225.imageshack.us/img225/7892/ubdesktopsmjj8.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=ubdesktopsmjj8.jpg)

[[IMG]http://img84.imageshack.us/img84/1350/ubscvv5.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=ubscvv5.jpg)

I'm playing The secret of monkey island 2 right now!! :D

---

### Post by GarethMB on 2007-01-12
> **fuscia said:**
> it's pretty fast, too, but i find it awkward to use.

It's amazingly quick, considering how bling it really is. Personally I think the things native to E are very nice. Ie. Engage. The file browser's pretty sweet too (but it needs a close all option) but there's so much that it doesn't do which means using gtk or qt apps which are never going to have the same level of graphical integration, which removes the main reason for using E. The other day someone came to print something and I was logged into E instead of KDE needless to say it was more complicated than it should be because E doesn't handle USB devices itself. That meant I had to find Konqueror, from somewhere in the most poorly structured menu ever. So that's E beautiful to look at, flawed to use.

---

### Post by ComplexNumber on 2007-01-12
> **GarethMB said:**
> It's amazingly quick, considering how bling it really is. Personally I think the things native to E are very nice. Ie. Engage. The file browser's pretty sweet too (but it needs a close all option) but there's so much that it doesn't do which means using gtk or qt apps which are never going to have the same level of graphical integration, which removes the main reason for using E. The other day someone came to print something and I was logged into E instead of KDE needless to say it was more complicated than it should be because E doesn't handle USB devices itself. That meant I had to find Konqueror, from somewhere in the most poorly structured menu ever. So that's E beautiful to look at, flawed to use.
i get the same impression. i think that the only reasons to use E are exactly the same as those for using beryl/compiz. using E and beryl bring very little practicality to the table, and are for short term use only.

---

### Post by RoLanRok on 2007-01-12
> **m.musashi said:**
> How did you get the xp-like task bar? I bet I could install Ubuntu for some reluctant users and with that they would never know the difference. Devious.

I'm assuming you mean the start button.
I'll try to make this as brief as possible.
Well, for the start button I added a main menu item from "add to panel" in the right-click menu. 
Then I opened up the terminal and typed "gconf-editor" (no quotes), do not use the sudo command while doing this, and don't use a root terminal.
In the application that appears, expand "apps" then scroll down and expand "panels" then "objects".
Highlight each object till you see "menu-object" as the "object type" in the right column.
Go to "custom_icon" edit it and type the path to the image file you want it to display instead. 
Now make sure that "Use_custom_icon" is ticked and it should display that instead of the default, this will be your start button. If you want, you can also apply a background to the panel to go along with it.

It does seem a bit much for that little difference though.

I've provided the images, If you want them. The Start button is in gimp format, so that you can change the color of the button layer to your liking.

---

### Post by truthfatal on 2007-01-12
Playing with Fluxbox.... I think some of the posts in this thread influenced that...

---

### Post by kanpachi on 2007-01-12
> **JoeC21 said:**
> My current setup...

[[img]http://joec21.googlepages.com/thumb-011107.png[/img]](http://joec21.googlepages.com/011107.jpg)

please share this wallpaper

---

### Post by m.musashi on 2007-01-12
> **RoLanRok said:**
> I'm assuming you mean the start button.
I'll try to make this as brief as possible.
Well, for the start button I added a main menu item from "add to panel" in the right-click menu. 
Then I opened up the terminal and typed "gconf-editor" (no quotes), do not use the sudo command while doing this, and don't use a root terminal.
In the application that appears, expand "apps" then scroll down and expand "panels" then "objects".
Highlight each object till you see "menu-object" as the "object type" in the right column.
Go to "custom_icon" edit it and type the path to the image file you want it to display instead. 
Now make sure that "Use_custom_icon" is ticked and it should display that instead of the default, this will be your start button. If you want, you can also apply a background to the panel to go along with it.

It does seem a bit much for that little difference though.

I've provided the images, If you want them. The Start button is in gimp format, so that you can change the color of the button layer to your liking.

Thanks. I'll have to try this. When I first looked at the screenshot and saw the start button and quick launch toolbar I thought it was some sort of app like kiba but made to look like xp. It's very well integrated. It was only after I took a second look and your directions did I see it was a modified gnome panel. Yeah, I didn't scrutinize well but I but your average windows user wouldn't know the diff.

---

### Post by tcrroadie on 2007-01-12
A screen capture of Fluxbox on my system.

---

### Post by Cirdan7 on 2007-01-13
> **JoeC21 said:**
> My current setup...

[[img]http://joec21.googlepages.com/thumb-011107.png[/img]](http://joec21.googlepages.com/011107.jpg)

Yellow card rocks!

---

### Post by eriqk on 2007-01-13
> **tcrroadie said:**
> A screen capture of Fluxbox on my system.

Very nice theme! What theme is that?

Groet, Erik

---

### Post by slimdog360 on 2007-01-13
Im back on gnome with my laptop after a long stint with kde.

[[IMG]http://img155.imageshack.us/img155/9206/screenshotwe2.th.jpg[/IMG]]("http://img155.imageshack.us/img155/9206/screenshotwe2.jpg")

---

### Post by Tiede on 2007-01-13
OK! I'm following along... I'm getting enlighten*ed*!
Here's my fist screenshot in E17 -and I'm likin' it: Burning Plasma Fire, Dripping Rain and all:D!!!
C'mon everyone! Jump in!

---

### Post by raul_ on 2007-01-13
> **Tiede said:**
> OK! I'm following along... I'm getting enlighten*ed*!
Here's my fist screenshot in E17 -and I'm likin' it: Burning Plasma Fire, Dripping Rain and all:D!!!
C'mon everyone! Jump in!

Are you using Beryl?

---

### Post by bvc on 2007-01-13
[Good and Evil]("http://gnomethemes.org/pre/screenshots/Good-and-Evil.png")

---

### Post by m.musashi on 2007-01-13
> **bvc said:**
> [Good and Evil]("http://gnomethemes.org/pre/screenshots/Good-and-Evil.png")

That's very attractive. I've been working without a bottom panel for a while myself and I like it. Two always seemed kind of cluttered to me. I'd go to kde for a while but I always end up back on gnome.

Btw, where did you find that wall paper?

---

### Post by fuscia on 2007-01-13
looks like i've rejoined the fruitcake club...

---

### Post by raul_ on 2007-01-13
I did some (minor) modifications to my desktop. Panels are now transparent and using the USP. Still looking for a good Beryl theme that goes with the rest. Everything else is the same
I would like some feedback :)

EDIT: The 4th screenshot is using Humanistic borderless Beryl theme. It's smoother, a little bit too orange though :( i guess i'm just picky :lol:

---

### Post by bvc on 2007-01-13
> **m.musashi said:**
> That's very attractive. I've been working without a bottom panel for a while myself and I like it. Two always seemed kind of cluttered to me. I'd go to kde for a while but I always end up back on gnome.

Btw, where did you find that wall paper?Thx!

I made the wallpaper in the gimp from a pic I took of the cover of [this book]("http://shop.nogreaterjoy.org/product_info.php/cPath/9_12/products_id/153"). [=comic&tx_ttnews[tt_news]=231&tx_ttnews[backPid]=118&cHash=ed6c519fb5"]Details here]("http://www.nogreaterjoy.org/index.php?id=85&tx_ttnews[swords). So the art is not mine. It was done by an retired Marvel comic book artist. I'll send ya a pm. If anyone else is interested in the wallpaper pm me.

---

### Post by Tiede on 2007-01-13
> **raul_ said:**
> Are you using Beryl?
I'm not using beryl. My hardware doesn't support 3d Acceleration and direct rendering... Just Enlightenement and the rain and fire epplets!!!

---

### Post by raul_ on 2007-01-13
well, i did it :D obvious rip-off from sabayon but i just wanted to show that Ubuntu (gnome) can be beautiful too. Notice that the selected windows button is now transparent. I just copied transparent images and replaced the ones in the "panel" folder. This may cause some confusion to you guys who want to know what window is selected but i really don't need that feature because i know with what i'm working at the moment. Here are the screenshots

PS: Seems like i'm battling with fuscia for the one with most desktop changes this month :P a lot of them i didn't post  though :(

---

### Post by m.musashi on 2007-01-13
> **raul_ said:**
> well, i did it :D obvious rip-off from sabayon but i just wanted to show that Ubuntu (gnome) can be beautiful too. Notice that the selected windows button is now transparent. I just copied transparent images and replaced the ones in the "panel" folder. This may cause some confusion to you guys who want to know what window is selected but i really don't need that feature because i know with what i'm working at the moment. Here are the screenshots

PS: Seems like i'm battling with fuscia for the one with most desktop changes this month :P a lot of them i didn't post  though :(

Agreed, gnome/ubuntu can look great. Nice job. Here is mine. New wall, new emerald (slightly modified onux-orange), new conky colors. Anyone know how to change the color of the home folder text? That would look better if it matched conky or theme colors.

I wish I could come up with a better theme for the icons though. They seem just a mish-mash. I did away with the window list altogether since, as you say, I know what I'm working on. Of course if it's minimized it can be a pain to get back but that is where beryl comes in handy. I also added a window selector (little icon next to trash) that allows be to pick a window should beryl crash or if I don't launch it for some reason.

PS notice our balmy temps. That's Fahrenheit y'all

EDIT if I count right, fuscia has 33 posts so far this month. That 10% of the total so far!

---

### Post by kvonb on 2007-01-14
I haven't been doing any theme-ing lately, I've weaned myself from that particular drug!

I go around in circles, finally arriving where I started.  I'm really happy with the default Ubuntu settings with just a hint of modification so here are my latest desktops:

snapshot50.jpg:
menu background:    menubar-04.png
desktop background:    ubuntu_orb_grey_1600x1200.jpg
Emerald theme:        48348-T-ish slightly modified
Gnome theme - controls:    Clearlooks
Gnome theme - icons:    OSX

snapshot51.jpg:
menu background:    menu-bar-top-white.png
desktop background:    ubuntu-wallemblem.jpg
Emerald theme:        human-ubuntulooks
Gnome theme - controls:    Human
Gnome theme - icons:    Human

All wallpapers and menu-bar backgrounds are available from my server as usual (see my sig) in the edgy/themes/ folder.

Regards, KEv :)

---

### Post by SmiLey497 on 2007-01-14
new wallpaper, plus a pic showing my theme

---

### Post by bernied on 2007-01-14
This is all pretty standard kubuntu 6.10. I find it very aesthetic.
It's the vmware Windows install that is imprisoned on the desktop that tickles me.

The wallpaper image may be a copyright violation - I feel bad, but I still do it.
[[IMG]http://img177.imageshack.us/img177/1876/snapshot2se5.th.png[/IMG]](http://img177.imageshack.us/my.php?image=snapshot2se5.png)

---

### Post by kimara on 2007-01-14
Blue gnome =) on arch..

---

### Post by fuscia on 2007-01-14
> **m.musashi said:**
> EDIT if I count right, fuscia has 33 posts so far this month. That 10% of the total so far!

yikes! i've got some catching up to do.

---

### Post by GarethMB on 2007-01-14
Always end up back here.

---

### Post by AlexR1 on 2007-01-14
This is my current desktop setup,i have this for a while now.
Comments,ideas are welcome.

Click here to see -> [http://www.gnome-look.org/content/show.php?content=51564](http://www.gnome-look.org/content/show.php?content=51564)

---

### Post by truthfatal on 2007-01-14
So I decided to try Beryl today (Thank you Automatix2Bleeder creators :) )

Background is from [here](http://gnome-look.org/content/show.php?content=22730)
Window decorations came with Beryl

---

### Post by flapane on 2007-01-14
which beryl plugin do you use to have unfocused items under transparent windows?

---

### Post by truthfatal on 2007-01-14
I think it must be the Visual Effects -> Blur Effects plugin, because other than some minor tweaks to already activated plugins, that's the only new plugin I checked.

---

### Post by flapane on 2007-01-14
done
thank you

---

### Post by m.musashi on 2007-01-14
> **AlexR1 said:**
> This is my current desktop setup,i have this for a while now.
Comments,ideas are welcome.

Click here to see -> [http://www.gnome-look.org/content/show.php?content=51564](http://www.gnome-look.org/content/show.php?content=51564)

That's very nice. I really love organish themes. Those icons are beautiful. I saw that they were from [www.wincustomize.com](www.wincustomize.com) but you wouldn't know the name so I could search for them would you? A link to the wallpaper would be nice too.

Thanks.

---

### Post by AlexR1 on 2007-01-14
> **m.musashi said:**
> That's very nice. I really love organish themes. Those icons are beautiful. I saw that they were from [www.wincustomize.com](www.wincustomize.com) but you wouldn't know the name so I could search for them would you? A link to the wallpaper would be nice too.

Thanks.

Wallpaper is called red Dragon and here is the link for it 
[http://www.wincustomize.com/Skins.aspx?LibID=8&view=1&sortby=4&sortdir=DESC&p=1&advanced=0&searchtxt=Red%20Dragon](http://www.wincustomize.com/Skins.aspx?LibID=8&view=1&sortby=4&sortdir=DESC&p=1&advanced=0&searchtxt=Red%20Dragon)

and here is the link for icons  name is System Force Japan Icon Pack. on the bottom of the page
[http://www.wincustomize.com/Skins.aspx?LibID=2&view=1&sortby=4&sortdir=DESC&p=6&advanced=0](http://www.wincustomize.com/Skins.aspx?LibID=2&view=1&sortby=4&sortdir=DESC&p=6&advanced=0)

---

### Post by ice60 on 2007-01-14
i just started using compiz. i didn't like it when it first came out, but this time i have disabled a couple of things and just configured it so it's abit more subtle. and, i totally love it, i can't believe how good it is :cool: :cool: 

[[IMG]http://img164.imageshack.us/img164/1292/screenshotst4.th.png[/IMG]](http://img164.imageshack.us/my.php?image=screenshotst4.png)

i'll have to keep an eye on that beagle-helper server. it's taking up alot of CPU in the screenshot, i haven't used gnome for awhile, i normally use xfce or fluxbox :)

---

### Post by ice60 on 2007-01-14
> **truthfatal said:**
> So I decided to try Beryl today (Thank you Automatix2Bleeder creators :) )

Background is from [here](http://gnome-look.org/content/show.php?content=22730)
Window decorations came with Beryl
i really like your conky fonts :D can you show me which font and red that is you use, please?

---

### Post by Tyche on 2007-01-14
I have many graphics that I use.  This is the latest one.  It's a desert:  specifically, Red Rocks, Sedona, Arizona, taken from the passenger seat of the Jeep I was driving.  Original size is 1280 X 1024, but I scale up and down (and crop) as necessary using Gimp.

The full size graphic may be obtained at [http://www.kde-look.org/]("http://www.kde-look.org/content/show.php?content=50804")

---

### Post by truthfatal on 2007-01-14
> **ice60 said:**
> i really like your conky fonts :D can you show me which font and red that is you use, please?

No problem :)

${color red}SYSTEM ${hr 2} <-- Easy red 

And for the fonts:

use_xft yes
xftfont Hemi head 426:size=9
xftalpha 0.5

My full .conkyrc is [here](http://www.ubuntuforums.org/showpost.php?p=2010511&postcount=79) just a different default_color setting to suit my background at the time.

---

### Post by ice60 on 2007-01-14
> **truthfatal said:**
> No problem :)

${color red}SYSTEM ${hr 2} <-- Easy red 

And for the fonts:

use_xft yes
xftfont Hemi head 426:size=9
xftalpha 0.5

My full .conkyrc is [here](http://www.ubuntuforums.org/showpost.php?p=2010511&postcount=79) just a different default_color setting to suit my background at the time.
great, thanks. i thought it might just be red. i also noticed after i posted that i think those fonts make the columns not line up. if you don't use xft fonts then columns do line up correctly. you know? the columns with PID, CPU and MEM. and i don't know how to fix that :(

---

### Post by truthfatal on 2007-01-14
> **ice60 said:**
> great, thanks. i thought it might just be red. i also noticed after i posted that i think those fonts make the columns not line up. if you don't use xft fonts then columns do line up correctly. you know? the columns with PID, CPU and MEM. and i don't know how to fix that :(

I'm making a bit of progress with:

~/conkytop.sh
```
#!/bin/bash

top -n1 | head -n 12 | tail -n 6 | cut -c 7-75 | less > .conkytop

```
(because conky doesn't like to directly run top, needs to cut the first 7 to get rid of any binary characters from `top`)

${execi 5 /home/truthfatal/conkytop.sh}
${execi 5 cat /home/truthfatal/.conkytop}

I'm still having problems getting it to run *properly* It works fine when I type "conky" in the terminal but for some reason 'conky' in the "run Program" dialog (Alt-f2) the trick doesn't work :(
*edit
Bah! still doesn't stay aligned either!

(I should be posting this in a more "conky" related thread...Oops!)

---

### Post by oblivion on 2007-01-14
[[IMG]http://img442.imageshack.us/img442/347/screenshot27rn5.th.jpg[/IMG]](http://img442.imageshack.us/my.php?image=screenshot27rn5.jpg)

Wallpaper "River of Light" from mandolux.com

---

### Post by ComplexNumber on 2007-01-14
time for a change. i really liked my last (green-themed) desktop, but its time for a change. this time, i have gone with a light-ish blue. this one is not as harmonious as the green one (for a start, the gdeskcal looks slightly out of place), but it will do for the time being.

gtk theme: Murrina-Kent
metacity theme: Murrine
Icons: Human Effects Light Blue
wallpaper: woman

---

### Post by Zwei on 2007-01-14
This has been my desktop image for a few months now.. got it from graphate . com somewhere.

---

### Post by fuscia on 2007-01-14
i like this transparent cube stuff...

---

### Post by rabid9797 on 2007-01-14
i used to have xgl/beryl but then i had to reformat and didn't feel like going through the arduous task of setting it all back up again, plus i like the space dual monitors gives me so i opted for Twinview.:)

---

### Post by MkfIbK7a on 2007-01-14
heres my desktop
i use icewm 
and the leaf theme really apealed to me

---

### Post by rabid9797 on 2007-01-14
> **wert613 said:**
> heres my desktop

8-[

---

### Post by MkfIbK7a on 2007-01-14
im sorry i pressed post instead of advanced

but i edited it you should be able to see it now

---

### Post by Kateikyoushi on 2007-01-15
> **AlexR1 said:**
> This is my current desktop setup,i have this for a while now.
Comments,ideas are welcome.

Click here to see -> [http://www.gnome-look.org/content/show.php?content=51564](http://www.gnome-look.org/content/show.php?content=51564)

I like it, actually I bookmarked it the first time you posted that screenshot few months ago and been waiting since when you finish the theme. Looks nice.

---

### Post by fuscia on 2007-01-15
OSDark-K icons, milknoirlightgrey dekorator window dec., apple setup, kaffeine...

---

### Post by ayoli on 2007-01-15
ok here's my apple setup, [gtk mac menu bar hack]("http://www.ubuntuforums.org/showthread.php?t=241868"), slafd icons, murine gray gtk style, and kxdocker.
[[IMG]http://img299.imageshack.us/img299/1701/capturehr4.th.png[/IMG]](http://img299.imageshack.us/my.php?image=capturehr4.png)

---

### Post by NeoLithium on 2007-01-15
Ok, I've just finished my desktop that I'll keep for a while, so I thought I'd put it up on the thread, the Firefox 2.0.01 window is creatively placed to make it less suggestive; but I HAD to include this wallpaper, since it's one of my favourites by that artist, and she did a phenominal job.  I've included the links for the stuff you basically see. 

[LIST]
[*]Window manager is fluxbox 1.0RC2, downloadable [[COLOR="Blue"]here[/COLOR]]("http://www.fluxbox.org").
[*]Icon set is [[COLOR="Blue"]Nuove XT 1.6[/COLOR]]("http://www.gnome-look.org/content/show.php?content=26448") from [[COLOR="Blue"]gnome-look.org[/COLOR]]("http://www.gnome-look.org")
[*]Wallpaper courtesy of [[COLOR="Blue"]deviantart.com[/COLOR]]("http://www.deviantart.com"), and is [[COLOR="Blue"]Raverpaper by kuroitora[/COLOR].]("http://www.deviantart.com/deviation/22949045/?qo=6&q=raver&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5").
[*][[COLOR="Blue"]bbdock[/COLOR]]("http://bbdock.nethence.com/") is on the left top corner.
[*][[COLOR="Blue"]conky[/COLOR] ]("http://conky.sourceforge.net")up on the right, my .conkyrc is included below.
[/LIST]

Finally, my conkyrc:
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
font purisa medium
uppercase no # set to yes if you want all text to be in uppercase

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=
#xftfont  Purisa:size=6.5

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
gap_y 1
#gap for gnome: gap_y 10

# Max window size
maximum_width 300

# stuff after 'TEXT' will be formatted on screen
#
# ALTERNATE STUFF TO PUT IN:
# ${time %a %e %B %G}                   ${alignr}${time %H:%M:%S}
# ALTERNATE COLORS
# blue: #000000

TEXT
$color
${color #000000}SYSTEM ${hr 2}$color
${color #000000}Core:$color   ${execi 1000 cat /proc/cpuinfo | grep 'model name' | cut -c 21-31} 2800+ ${alignc}${color #000000}Uptime:$color $uptime
${color #000000}Kernel:$color $kernel ${alignc}${color #000000}    Host:$color $nodename 

${color #000000}POWER ${hr 2}$color
${color #000000}Adapter Stat:$color  ${acpiacadapter}	${color #000000}${alignr}Battery Info:$color ${battery}

${color #000000}CPU ${hr 2}$color
${color #000000}Speed:$color ${freq}MHz  ${color #000000}Load:$color ${loadavg} ${color #000000}${alignr}CPU Temp:$color ${acpitemp}
${cpugraph 000000 ffffff}
${color #000000}NAME             PID       CPU%      MEM%$color
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color #000000}MEMORY ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
       $mem of $memmax
Swap:  $swapperc%   ${swapbar 6}$color
       $swap of $swapmax

${color #000000}HD PARTITIONS ${hr 2}$color
Root:	${fs_used /} / ${fs_size /}  ${alignc}${fs_bar 6 /}$color 
Home:	${fs_used /home} / ${fs_size /home}  ${alignc}${fs_bar 6 /home}$color
Data:	${fs_used /data} / ${fs_size /data}  ${alignc}${fs_bar 6 /data}$color

${color #000000}NETWORK (${addr ppp0}) ${hr 2}$color
${downspeedgraph ppp0 12,140 000000 ff0000} ${alignr}${upspeedgraph ppp0 
12,140 000000 00ff00}$color
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color #000000}SYSTEM SECURITY LOGS ${hr 2}$color
${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 17-}

${color #000000}WEATHER ${hr 2}$color
${execi 1800 /home/neo/weather/weather.sh}

```

---

### Post by raul_ on 2007-01-15
Very good, specially because it only uses 170mb with Firefox :) I love minimalistic desktops, but i feel kinda bad setting them up because i have 1gb of RAM =\

PS: -23C ??

---

### Post by NeoLithium on 2007-01-15
> **raul_ said:**
> Very good, specially because it only uses 170mb with Firefox :) I love minimalistic desktops, but i feel kinda bad setting them up because i have 1gb of RAM =\

PS: -23C ??

Actually, I even had gimp, and a few other things open in the other workspaces, I'm pleasantly surprised at the RAM usage :)  And yeah; -23 before the wind chill. Winnipeg isn't nice this winter ;)

---

### Post by Polygon on 2007-01-15
[[IMG]http://img440.imageshack.us/img440/1470/screenshot11507jy1.th.png[/IMG]](http://img440.imageshack.us/my.php?image=screenshot11507jy1.png)

see post: [http://ubuntuforums.org/showpost.php?p=2019143&postcount=362](http://ubuntuforums.org/showpost.php?p=2019143&postcount=362)

for a more updated picture

---

### Post by ComplexNumber on 2007-01-15
> **Polygon said:**
> [[IMG]http://img440.imageshack.us/img440/1470/screenshot11507jy1.th.png[/IMG]]("http://img440.imageshack.us/my.php?image=screenshot11507jy1.png")
i like the colours and the harmony in that. i think everything blends well. the metacity theme(ie alphacube, if i'm not mistaken) tends to go well with grey/silver themes. the only thing that stands out is the Tango icon theme. try Tango OldPlainGrey or Tango Noir.

---

### Post by timpino on 2007-01-15
> **NeoLithium said:**
> Actually, I even had gimp, and a few other things open in the other workspaces, I'm pleasantly surprised at the RAM usage :)  And yeah; -23 before the wind chill. Winnipeg isn't nice this winter ;)

HOLY MOSES, how would you be able to squeeze Edgy down to that? i mean for me 300+ is normal using gnome...

And might I say, hefty fine fluxbox config you got there

EDIT: YAY, me first post

---

### Post by Polygon on 2007-01-15
> **ComplexNumber said:**
> i like the colours and the harmony in that. i think everything blends well. the metacity theme(ie alphacube, if i'm not mistaken) tends to go well with grey/silver themes. the only thing that stands out is the Tango icon theme. try Tango OldPlainGrey or Tango Noir.

thanks, i was just thinking that the blue folders were clashing a bit =P

thanks again for the suggestion, looks much better

[[IMG]http://img443.imageshack.us/img443/387/screenshot115072ub8.th.png[/IMG]](http://img443.imageshack.us/my.php?image=screenshot115072ub8.png)

Controls: MurinnaLoveGrey
Icons: Tango-OldPlainGrey
Window Border: Alphacube 1.0 Metacity Color
Wallpaper: Natural Grey Ubuntu ([http://www.gnome-look.org/content/show.php?content=22730](http://www.gnome-look.org/content/show.php?content=22730))

---

### Post by PhrankDaChickenGeek on 2007-01-15
Using Industrial controls and nuoveXT-1.6 icon set

with this wallpaper: [http://ubuntu.online02.com/node/87](http://ubuntu.online02.com/node/87)


[http://ubuntu.online02.com/node/79](http://ubuntu.online02.com/node/79)
[IMG]http://ubuntu.online02.com/files/active/0/79_thumb.jpg[/IMG]

---

### Post by ComplexNumber on 2007-01-15
<please ignore> accidental double post.

---

### Post by ComplexNumber on 2007-01-15
> **Polygon said:**
> thanks, i was just thinking that the blue folders were clashing a bit =P
i think some of the following icon sets would look nice with that theme and wallpaper: SnowIsh([click]("http://gnome-look.org/content/show.php?content=32599")), Samurai(its an OS X type silver theme) ([clic]("http://gnome-look.org/content/show.php?content=41263")k), or Tango-oldplaingrey([click]("http://gnome-look.org/content/show.php?content=46564")). theres also Human-grey.

a word of warning - if you use snowish, i find them to be quite resource hungry, so they make opening windows etc slow down a bit. 


EDIT: damn! you edited your post before i posted mine :D. i was going to do you a screenshot of how it would all look.

---

### Post by bvc on 2007-01-15
edited the wallpaper, added panel-bg, changed theme
seems to fit together better

[Good and Evil]("http://gnomethemes.org/pre/screenshots/Good-and-Evil.png")

---

### Post by NeoLithium on 2007-01-15
> **timpino said:**
> HOLY MOSES, how would you be able to squeeze Edgy down to that? i mean for me 300+ is normal using gnome...

And might I say, hefty fine fluxbox config you got there

EDIT: YAY, me first post

Just went with bare bones stuff; and not a lot of fancy things, conky helps for using very little RAM; and even when I had gnome, I was lucky, rarely went above 200MB for the ram usage :)

---

### Post by m.musashi on 2007-01-15
> **raul_ said:**
> Very good, specially because it only uses 170mb with Firefox :) I love minimalistic desktops, but i feel kinda bad setting them up because i have 1gb of RAM =\

PS: -23C ??

Just curious. I've never paid a lot of attention to RAM usage as it hasn't seemed an issue. However, I was wondering if gnome is really all that bad. According to conky, my usage is at 30% at the moment and with 1GB that's about 300MB. Certainly higher than the 170MB but I also have firefox and beryl running. When I opened up gimp to edit the screenshot it only went to 32%. Am I reading that right? Is that bad?

I've tried several DEs and window managers (still not clear on all that) but I keep coming back to gnome. It's very functional and I'm comfortable with it.

---

### Post by NeoLithium on 2007-01-15
I also don't have a great video card though, it's only a 32MB built in on my laptop, so that makes a difference too; no Beryl, just had straight gnome back then.  There's a few things that make the difference; but I mean, if you don't slow down, there's not a worry, really, is there? :)

---

### Post by m.musashi on 2007-01-15
> **bvc said:**
> edited the wallpaper, added panel-bg, changed theme
seems to fit together better

[Good and Evil]("http://gnomethemes.org/pre/screenshots/Good-and-Evil.png")

Very nice as usual. One question though. I notice that there is a tiny bit of black behind the rounded panel corners. I have the same problem but on the top part of windows if I round them (using beryl, emerald). Is there a way to fix that? I know is pretty nit-picky but for some reason it draws my eye and bugs me. Usually I just keep square corners but I like rounded better.

Sorry about the poor quality on the screenshot but I think you can see what I'm referring to.

---

### Post by ComplexNumber on 2007-01-15
> **bvc said:**
> edited the wallpaper, added panel-bg, changed theme
seems to fit together better

[Good and Evil]("http://gnomethemes.org/pre/screenshots/Good-and-Evil.png")
ay up, bvc! although i'm not interested in the actual wallpaper content, i am more interested in the 'scan-lines' type effect. if you altered the wallpaper yourslf, how did you get the effect because i'm interesting in using it myself?


btw the whole desktop looks good and harmonious.

---

### Post by ~LoKe on 2007-01-15
> **ComplexNumber said:**
> ay up, bvc! although i'm not interested in the actual wallpaper content, i am more interested in the 'scan-lines' type effect. if you altered the wallpaper yourslf, how did you get the effect because i'm interesting in using it myself?


btw the whole desktop looks good and harmonious.

Just make a 2px image and fill the top pixel with black, bottom with white.  Then use it as a pattern and fill a semi-transparent layer.

---

### Post by bvc on 2007-01-15
> **ComplexNumber said:**
> ay up, bvc! although i'm not interested in the actual wallpaper content, i am more interested in the 'scan-lines' type effect. if you altered the wallpaper yourslf, how did you get the effect because i'm interesting in using it myself?


btw the whole desktop looks good and harmonious.Hiya! in the gimp add a layer of whatever color you want the lines to be,Script-Fu>Alchemy>Erase every other row

---

### Post by bvc on 2007-01-15
> **m.musashi said:**
> Very nice as usual. One question though. I notice that there is a tiny bit of black behind the rounded panel corners. I have the same problem but on the top part of windows if I round them (using beryl, emerald). Is there a way to fix that? I know is pretty nit-picky but for some reason it draws my eye and bugs me. Usually I just keep square corners but I like rounded better.

Sorry about the poor quality on the screenshot but I think you can see what I'm referring to.in the case of my panel I put that black there. In the case of beryl in your screenie it's either just beryl bugs (engine only) or sometimes the theme is not made right (pixmap). If it is an image it may be wider than the border setting etc....make sure everything is equal.

---

### Post by ComplexNumber on 2007-01-15
> **~LoKe said:**
> Just make a 2px image and fill the top pixel with black, bottom with white. Then use it as a pattern and fill a semi-transparent layer.
cheers. i'm not too sure if i understood that exactly, though ;)

> **bvc said:**
> Hiya! in the gimp add a layer of whatever color you want the lines to be,Script-Fu>Alchemy>Erase every other row
thanks. i'm in the gimp now trying to achieve that  effect. after some brief research, i thought it may be perl-fu -> neon scanlines, but i can't seem to have much luck with getting the correct values. 
just tried script-fu -> alchemy -> erase every other row. thats spot on - just what i as looking for. thanks again :). i can't seem to get that silvery look, though. not yet anyway.

---

### Post by tigerpants on 2007-01-16
My latest fluxbox install on my laptop. Torn between E17 and Flux!

---

### Post by Vord on 2007-01-16
Here's my wonderfully minimalistic desktop (By my standards, at least). Which I spent far too much time on (Notice that out of 22 dock icons, only 10 are stock, I actually sought out individual icons for over half the programs there)

Let me know what you think, please.

---

### Post by ComplexNumber on 2007-01-16
> **Vord said:**
> Here's my wonderfully minimalistic desktop (By my standards, at least). Which I spent far too much time on (Notice that out of 22 dock icons, only 10 are stock, I actually sought out individual icons for over half the programs there)

Let me know what you think, please.
minimalistic wallpapers are good because, when selected correctly, they can blend with with theme and applications, rather than being a distraction from them.

---

### Post by SlCKB0Y on 2007-01-16
boring ol desktop

---

### Post by ComplexNumber on 2007-01-16
**SlCKB0Y**
what icon theme are you using?

---

### Post by GarethMB on 2007-01-16
Really happy with this now. Had to change two to JPEGs. Sorry if there's a discernible loss of quality.

---

### Post by kanpachi on 2007-01-16
> **SlCKB0Y said:**
> boring ol desktop

not boring at all in my eyes!
can you please share some details about it?
wallpaper icons and theme?

---

### Post by Theimon on 2007-01-16
> **Vord said:**
> Here's my wonderfully minimalistic desktop (By my standards, at least). Which I spent far too much time on (Notice that out of 22 dock icons, only 10 are stock, I actually sought out individual icons for over half the programs there)

Let me know what you think, please.

Could you tell us what theme and wallpaper those are? And perhaps where to get them? ;) I'm a sucker for dark themes, although I'm looking at a very bright one at the moment. (burn my eyes!! :evil:)

---

### Post by mustang on 2007-01-16
> **Polygon said:**
> thanks, i was just thinking that the blue folders were clashing a bit =P

thanks again for the suggestion, looks much better

[[IMG]http://img443.imageshack.us/img443/387/screenshot115072ub8.th.png[/IMG]](http://img443.imageshack.us/my.php?image=screenshot115072ub8.png)

Controls: MurinnaLoveGrey
Icons: Tango-OldPlainGrey
Window Border: Alphacube 1.0 Metacity Color
Wallpaper: Natural Grey Ubuntu ([http://www.gnome-look.org/content/show.php?content=22730](http://www.gnome-look.org/content/show.php?content=22730))

Very slick. Might have to steal your settings :p

---

### Post by BLTicklemonster on 2007-01-16
> **NeoLithium said:**
> Ok, I've just finished my desktop that I'll keep for a while, 

Do you mind me asking, what is the weather app you use at the end of your conky script?

---

### Post by tr4nce on 2007-01-16
Simple 
[[IMG]http://content.imagesocket.com/thumbs/Screenshotd79.png[/IMG]](http://imagesocket.com/view/Screenshotd79.png)

---

### Post by raul_ on 2007-01-16
> **tr4nce said:**
> Simple 
[[IMG]http://content.imagesocket.com/thumbs/Screenshotd79.png[/IMG]](http://imagesocket.com/view/Screenshotd79.png)

If you're using Gnome take a look at Exaile

---

### Post by Vord on 2007-01-16
> **Theimon said:**
> Could you tell us what theme and wallpaper those are? And perhaps where to get them? ;) I'm a sucker for dark themes, although I'm looking at a very bright one at the moment. (burn my eyes!! :evil:)

Well, just about everything on there has been tweaked, the base theme I used was Khali (I believe, no access to gnome-look.org right now) and the icon theme is a pretty customized version of GnomeCorsair2-All Black. The background is just a debian background I grabbed also off of Gnome-look, and edited out the "GNU/Linux Debian" at the bottom, because it looked tacky as hell. Window border is just one of the packaged Beryl Emerald themes.

I'd be happy to upload the wallpaper to you when I get out of class, if you'd like.

---

### Post by PatrickMay16 on 2007-01-17
Nobody cares to see it but I'm posting it anyway

---

### Post by MkfIbK7a on 2007-01-17
> **PatrickMay16 said:**
> Nobody cares to see it but I'm posting it anyway

gluck:-s 
a little dark....

---

### Post by slimdog360 on 2007-01-17
Mac look-a-likes FTW
[[IMG]http://img219.imageshack.us/img219/6594/200701172114231440x900sso0.th.png[/IMG]]("http://img219.imageshack.us/img219/6594/200701172114231440x900sso0.png")
Ive got beryl with a Mac theme, Mac icons, Mac wallpaper and gdesklets with the bar thingy down the bottom.

---

### Post by Vord on 2007-01-17
Hehe, not saying it doesn't look good, but I've always had to wonder why people try to make their desktops look like another OS. Linux has the potential to be absolutely gorgeous while still looking like Linux. Just like windows does while still looking like windows. I mean, sure, Macs look wonderful, but just because they look great out of the box doesn't mean that you shouldn't take pride in making your Linux box look like a damn nice Linux box.

Anyway, /rant.

I do like the desktop though, slimdog, nice and simplistic, easy on the eyes.

---

### Post by BLTicklemonster on 2007-01-17
It's not ubuntu, it's XP, and it's here at work, but a fella has to brag every now and then.

Me on the left, my son in law, his wife - my daughter, and on the right are my son and my other daughter.

What's that "his wife - my daughter" is holding?


Why it's my brand new (1st) grandchild, of course last Thursday night Jan 11th!!! 

:cigars all around:

---

### Post by ice60 on 2007-01-17
lol mine looks abit like a mac atm, i just started using gnome again after using fluxbox and xfce for quite awhile.

[[IMG]http://img72.imageshack.us/img72/5264/screenshot1fu4.th.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot1fu4.png)

---

### Post by ice60 on 2007-01-17
> **BLTicklemonster said:**
> 
Why it's my brand new (1st) grandchild, of course last Thursday night Jan 11th!!! 

:cigars all around:

congratulations, i don't even have one child lol

---

### Post by tcrroadie on 2007-01-17
More Enlightenment E17.  Showing Eclair media player and E17's main menu.

---

### Post by iPower on 2007-01-17
my desktop today

---

### Post by raul_ on 2007-01-17
> **BLTicklemonster said:**
> 

Why it's my brand new (1st) grandchild, of course last Thursday night Jan 11th!!! 

:cigars all around:

Congratulations :D

---

### Post by rsambuca on 2007-01-17
Would someone that lives in the Land of the Long Leaf Pine please go check in on fuscia?  I am starting to get worried as we haven't seen a new desktop in almost a day.:(

---

### Post by aristotlewilde on 2007-01-17
> **GarethMB said:**
> Tinkering with E17 lately. It looks beautiful and it does what it does very nicely but there's a lot it doesn't do.
I feel the same way.  Feels very experimental and unfinished.  

Of course, my brain might just need some re-training...

---

### Post by fuscia on 2007-01-17
> **rsambuca said:**
> Would someone that lives in the Land of the Long Leaf Pine please go check in on fuscia?  I am starting to get worried as we haven't seen a new desktop in almost a day.:(

believe it, or not, i've been using the same one for a couple of days. i'm deeply moved by your concern. 'sniff'

---

### Post by urukrama on 2007-01-17
> **GarethMB said:**
> Really happy with this now. Had to change two to JPEGs. Sorry if there's a discernible loss of quality.

Is that 'open' dialog of OpenOffice standard in KDE? It looks really nice. I use Gnome and Xfce, but the dialog looks differently there. Just curious.

---

### Post by Theimon on 2007-01-17
> **Vord said:**
> Well, just about everything on there has been tweaked, the base theme I used was Khali (I believe, no access to gnome-look.org right now) and the icon theme is a pretty customized version of GnomeCorsair2-All Black. The background is just a debian background I grabbed also off of Gnome-look, and edited out the "GNU/Linux Debian" at the bottom, because it looked tacky as hell. Window border is just one of the packaged Beryl Emerald themes.

I'd be happy to upload the wallpaper to you when I get out of class, if you'd like.

Found the Khali themes (GTK and Emerald), looks great. :) About the wallpaper: I'd like that yes :D

---

### Post by urukrama on 2007-01-17
> **BLTicklemonster said:**
> 
Why it's my brand new (1st) grandchild, of course last Thursday night Jan 11th!!! 

:cigars all around:

Congratulations to you and the parents! :KS

---

### Post by _simon_ on 2007-01-17
> **tcrroadie said:**
> More Enlightenment E17.  Showing Eclair media player and E17's main menu.

I like that a lot, makes me want to try E17 again.

What car is that btw? it looks stunning!

---

### Post by mcduck on 2007-01-17
> **_simon_ said:**
> I like that a lot, makes me want to try E17 again.

What car is that btw? it looks stunning!

Looks like Saleen S7 with some extra parts (like the rear wing).

After Vector M12 I think that's the best looking new car built in USA.

---

### Post by GarethMB on 2007-01-17
> **urukrama said:**
> Is that 'open' dialog of OpenOffice standard in KDE? It looks really nice. I use Gnome and Xfce, but the dialog looks differently there. Just curious.
Yep, I'm using the KDE package. It's picking up on my KDE widgets theme and I've told it to show icons and previews.

---

### Post by SunnyRabbiera on 2007-01-17
My screen this month:
[[IMG]http://img64.imageshack.us/img64/9617/screenshotxava9.th.png[/IMG]](http://img64.imageshack.us/my.php?image=screenshotxava9.png)
I got myself a mac like setup now

---

### Post by darkhatter on 2007-01-17
> **SunnyRabbiera said:**
> My screen this month:
[[IMG]http://img64.imageshack.us/img64/9617/screenshotxava9.th.png[/IMG]](http://img64.imageshack.us/my.php?image=screenshotxava9.png)
I got myself a mac like setup now

I love the show :D 

right click your desktop and select **"configure desktop.."**, goto** "position"** and select **"scale and crop"**. this will automatically scale and crop your wallpaper to fit your desktop size

and is it possible to get a link to the wallpaper plz

---

### Post by ~LoKe on 2007-01-17
> **darkhatter said:**
> I love the show :D 

right click your desktop and select **"configure desktop.."**, goto** "position"** and select **"scale and crop"**. this will automatically scale and crop your wallpaper to fit your desktop size

and is it possible to get a link to the wallpaper plz

Personally I don't have that option. o_O

---

### Post by darkhatter on 2007-01-17
> **~LoKe said:**
> Personally I don't have that option. o_O

I'm running KDE now, but I thought Gnome had that feature too.....

---

### Post by mcduck on 2007-01-17
> **~LoKe said:**
> Personally I don't have that option. o_O

In Gnome this option is called 'zoom'.

---

### Post by ComplexNumber on 2007-01-17
i'm going grey.......



gtk: MurrinaLoveGrey
metacity: Murrine
icons: Tango-oldplaingrey
wallpaper: Vallila_winter

---

### Post by darkhatter on 2007-01-17
I think I was the first to post a desktop screenshot of the new KVM module. This is going to be in the new 2.6 .20 kernel whenever it comes out

[[IMG]http://img180.imageshack.us/img180/4821/kvmdesktoplh3.th.jpg[/IMG]](http://img180.imageshack.us/my.php?image=kvmdesktoplh3.jpg)

stock edgy kernel, and theme
stock windows xp

---

### Post by finferflu on 2007-01-17
Ok, new E17 configuration... I felt a bit darker :P

---

### Post by MkfIbK7a on 2007-01-17
nice background!

---

### Post by ~LoKe on 2007-01-17
> **darkhatter said:**
> I think I was the first to post a desktop screenshot of the new KVM module. This is going to be in the new 2.6 .20 kernel whenever it comes out

[[IMG]http://img180.imageshack.us/img180/4821/kvmdesktoplh3.th.jpg[/IMG]](http://img180.imageshack.us/my.php?image=kvmdesktoplh3.jpg)

stock edgy kernel, and theme
stock windows xp
Would you by chance have a link to some instructions on how to get this going?  I've got 2.6.20.

---

### Post by darkhatter on 2007-01-17
> **~LoKe said:**
> Would you by chance have a link to some instructions on how to get this going?  I've got 2.6.20.

does you cpu support it?

[http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386](http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386) I followed this link and got everything working.

---

### Post by SlCKB0Y on 2007-01-17
> **ice60 said:**
> lol mine looks abit like a mac atm, i just started using gnome again after using fluxbox and xfce for quite awhile.

[[IMG]http://img72.imageshack.us/img72/5264/screenshot1fu4.th.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot1fu4.png)

What gnome theme is that?

---

### Post by SlCKB0Y on 2007-01-17
> **ComplexNumber said:**
> **SlCKB0Y**
what icon theme are you using?

Buuf

---

### Post by ComplexNumber on 2007-01-17
> **SlCKB0Y said:**
> Buuf
cheers ;). i've got that theme installed, but i've never used it....so thats probably why i didn't immediately recognise it.

---

### Post by ~LoKe on 2007-01-17
> **darkhatter said:**
> does you cpu support it?

[http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386](http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386) I followed this link and got everything working.

Flawless installation.  Thanks!

---

### Post by darkhatter on 2007-01-17
> **~LoKe said:**
> Flawless installation.  Thanks!```

```

no prob, I wonder how long its going to take someone to find a way to install OS X on this

---

### Post by PapaWiskas on 2007-01-17
Feeling melancholy lately...still using Xubuntu for now.

---

### Post by CCBalla10 on 2007-01-17
Here is my beautiful Ubuntu Box!  I love this wallpaper.  Looks even better all lit up by my laptops' screen!  Tell me what you think!

[[IMG]http://img405.imageshack.us/img405/1343/screenshotcv1.th.png[/IMG]](http://img405.imageshack.us/my.php?image=screenshotcv1.png)

---

### Post by raul_ on 2007-01-17
> **CCBalla10 said:**
> Tell me what you think!

[[IMG]http://img405.imageshack.us/img405/1343/screenshotcv1.th.png[/IMG]](http://img405.imageshack.us/my.php?image=screenshotcv1.png)

/me likes it

---

### Post by CCBalla10 on 2007-01-17
> **raul_ said:**
> /me likes it

Thank you my man!

---

### Post by MkfIbK7a on 2007-01-17
> **CCBalla10 said:**
> Here is my beautiful Ubuntu Box!  I love this wallpaper.  Looks even better all lit up by my laptops' screen!  Tell me what you think!

[[IMG]http://img405.imageshack.us/img405/1343/screenshotcv1.th.png[/IMG]](http://img405.imageshack.us/my.php?image=screenshotcv1.png)

very nice!
and wet

---

### Post by crimesaucer on 2007-01-18
I changed my gtkrc file to match my desktop.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64.png[/IMG]

---

### Post by MkfIbK7a on 2007-01-18
> **crimesaucer said:**
> I changed my gtkrc file to match my desktop.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64.png[/IMG]

woah awesome:D :D

---

### Post by _simon_ on 2007-01-18
> **crimesaucer said:**
> I changed my gtkrc file to match my desktop.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64.png[/IMG]

Looks pretty amazing!

What emerald theme is that?

---

### Post by ice60 on 2007-01-18
> **SlCKB0Y said:**
> What gnome theme is that?

here it is -
[http://www.gnome-look.org/content/show.php?content=46153](http://www.gnome-look.org/content/show.php?content=46153)

---

### Post by ice60 on 2007-01-18
is there a big difference between compiz and beryl? (or whatever that diamond one is) i'm still using compiz, i just like the way the windows open and close :|

---

### Post by crimesaucer on 2007-01-18
Thanks _simon_ and wert, the theme is a modification of "scaled black". I used my own colors, changed the size of everything, changed the the titlebar settings, added a "set above" button and an icon, changed the curve, notch, and blends. Basically, I changed everything except the pix map buttons which are some of my favorite I've seen so far.

If you would like, I can give you the exact stats and you can use your own colors.

---

### Post by raul_ on 2007-01-18
> **ice60 said:**
> is there a big difference between compiz and beryl? (or whatever that diamond one is) i'm still using compiz, i just like the way the windows open and close :|

Not really. Compiz feels really smooth but you just have to play with Beryl settings to get it smooth too. I've used compiz bue some things bugged me. I was already used to Beryl, Compiz doesn't support themes (only metacity themes, and that didn't work with my desktop) the cube was transparent and i couldn't spin the cube very smoothly. But i remember the first time i minimized a window in Compiz i was like "wow" :cool:

---

### Post by ice60 on 2007-01-18
> **raul_ said:**
> Not really. Compiz feels really smooth but you just have to play with Beryl settings to get it smooth too. I've used compiz bue some things bugged me. I was already used to Beryl, Compiz doesn't support themes (only metacity themes, and that didn't work with my desktop) the cube was transparent and i couldn't spin the cube very smoothly. But i remember the first time i minimized a window in Compiz i was like "wow" :cool:
thanks, Raul. i don't feel so left out now :D

---

### Post by fuscia on 2007-01-18
'kind o'green'

somehow, i managed to end up with a combination of the pharago and crux gtk themes (win.dec. is 'esco'). using the gnome theme manager and gtk-chtheme, at the same time, will do that sort of thing. a mix of icons and just a plain gradient wallpaper.

---

### Post by ComplexNumber on 2007-01-18
> **fuscia said:**
> 'kind o'green'

somehow, i managed to end up with a combination of the pharago and crux gtk themes (win.dec. is 'esco'). using the gnome theme manager and gtk-chtheme, at the same time, will do that sort of thing. a mix of icons and just a plain gradient wallpaper.
although you mention what theme you're using, it would be better to open a simple application so that people can see the theme 'in action' IMO.

---

### Post by fuscia on 2007-01-18
> **ComplexNumber said:**
> although you mention what theme you're using, it would be better to open a simple application so that people can see the theme 'in action' IMO.

oh yeah! i totally forgot to do that. DOH!1

---

### Post by ComplexNumber on 2007-01-18
nice. me personally, i wouldn't use an all-green wallpaper when the icons are green and the theme contains green elements. i think i would use a wallpaper that is extremly light grey, but with something in it thats green such as the wallpaper in my green theme a few posts back.. but thats just me.

---

### Post by fuscia on 2007-01-18
> **ComplexNumber said:**
> nice. me personally, i wouldn't use an all-green wallpaper when the icons are green and the theme contains green elements. i think i would use a wallpaper that is extremly light grey, but with something in it thats green such as the wallpaper in my green theme a few posts back.. but thats just me.

i'm gearing up for st. patrick's day (i've already started drinking).;)

---

### Post by ComplexNumber on 2007-01-18
> **fuscia said:**
> i'm gearing up for st. patrick's day (i've already started drinking).;)
of course. its quite big here in england too (beleive it or not). its big in america because theres a large population of  irish ancestry  there (partly because of the slave trade when the irish were used as slaves. when they dried up, they started using africans instead).
st paddys day is usually one big knees up.

---

### Post by _simon_ on 2007-01-18
> **crimesaucer said:**
> Thanks _simon_ and wert, the theme is a modification of "scaled black". I used my own colors, changed the size of everything, changed the the titlebar settings, added a "set above" button and an icon, changed the curve, notch, and blends. Basically, I changed everything except the pix map buttons which are some of my favorite I've seen so far.

If you would like, I can give you the exact stats and you can use your own colors.

Could you export it? Might be easier than giving out the settings. In fact you should release it!

---

### Post by crimesaucer on 2007-01-18
@fuscia- Where could I find (or make) icons like those, the mint-green human look?

Nice Miles Davis wallpaper too.

---

### Post by crimesaucer on 2007-01-18
@_simon_- Yeah, I could do that, I have never shared a file/theme before, what do I do, just export it to a location when I'm in Emerald? If you give me directions, I'll upload them today.

I actually have about 10 different custom Emerald themes that are similar to that one with different color combos, buttons, and sizes, as well as curve/shadow effects. Most are vrunner, but a couple are tru-glass.

---

### Post by fuscia on 2007-01-18
> **crimesaucer said:**
> @fuscia- Where could I find (or make) icons like those, the mint-green human look?

are you sure you mean the icons? they're all from various themes (dreamlinux's default set, kde's black+white, human ultra green). only the icon on the far left and 'dead girl' are not. the one on the far left is someone's icon (i forget whose) from these forums. the theme, which accounts for the green, is pharago, which i got from gnome-look.org.

> Nice Miles Davis wallpaper too.

thanks.

________

well, that (gnome) didn't last long. back to flwm (with kicker, klipper and beep)...

---

### Post by aristotlewilde on 2007-01-18
> **CCBalla10 said:**
> Here is my beautiful Ubuntu Box!  I love this wallpaper.  Looks even better all lit up by my laptops' screen!  Tell me what you think!

[[IMG]http://img405.imageshack.us/img405/1343/screenshotcv1.th.png[/IMG]](http://img405.imageshack.us/my.php?image=screenshotcv1.png)

Looks great.  Interesting choice of films you have there.

---

### Post by crimesaucer on 2007-01-18
You know what, I meant the folder theme (the human one). I was just thinking of the apllication icons like the trash can, desktop, home folder...my bad.

So where do I find the "human ultra green"?

***Edit- I found theme on gnome looks. They all look really cool.

---

### Post by fuscia on 2007-01-18
> **crimesaucer said:**
> You know what, I meant the folder theme (the human one). I was just thinking of the apllication icons like the trash can, desktop, home folder...my bad.

So where do I find the "human ultra green"?

there's a whole bunch of colors - [http://www.gnome-look.org/content/show.php?content=46010](http://www.gnome-look.org/content/show.php?content=46010)

---

### Post by _simon_ on 2007-01-18
> **crimesaucer said:**
> @_simon_- Yeah, I could do that, I have never shared a file/theme before, what do I do, just export it to a location when I'm in Emerald? If you give me directions, I'll upload them today.

I actually have about 10 different custom Emerald themes that are similar to that one with different color combos, buttons, and sizes, as well as curve/shadow effects. Most are vrunner, but a couple are tru-glass.

It's really easy to do, thankfully!

Open Emerald Theme Manager
Make sure the theme you want to export is selected
Choose the "Edit Themes" tab
At the bottom it allows you to add/edit the theme name and you will see 2 buttons - save and export.
Just click Export and choose where to e.g. Desktop

Then all you need to do is host it.

Ubuntu forum doesn't allow .emerald I don't think so I'd just stick it inside an archive, so right click on your exported theme and choose create archive then select .tar.gz or something and add it as an attachment to a post :)

---

### Post by tbeld on 2007-01-18
Here's my Eye-candy with a dual-head setup!

Font= Aqua ([http://grsites.com/exec/public/fontview.cgi?dir=a&fn=AQUA](http://grsites.com/exec/public/fontview.cgi?dir=a&fn=AQUA))
Wallpaper=vladstudio_ornamental2_1600x1200.jpg ([www.gnome-look.org](www.gnome-look.org))
Emerald Theme=51237-VistaQ2 ([www.gnome-look.org](www.gnome-look.org))

[[IMG]http://www.uccs.edu/~langtech/thumb.Screenshot.png[/IMG]](http://www.uccs.edu/~langtech/Screenshot.png)
([http://img166.imageshack.us/img166/8469/screenshotxp7.png](http://img166.imageshack.us/img166/8469/screenshotxp7.png))
[[IMG]http://www.uccs.edu/~langtech/thumb.Screenshot-1.png[/IMG]](http://www.uccs.edu/~langtech/Screenshot-1.png)
([http://img444.imageshack.us/img444/8199/screenshot1nx8.png](http://img444.imageshack.us/img444/8199/screenshot1nx8.png))

---

### Post by ahaslam on 2007-01-18
Standard Feisty Herd 2:

[ATTACH]23377[/ATTACH]

Is it me or does it seem a bit like openSUSE? I was half expecting to see the SLAB! I don't know whether this is good or bad, only time will tell :-k 

Though I must say that it passed the long lest & is only showing a few minor niggles, this will be a good release ;)

Tony.

---

### Post by bugz0r on 2007-01-18
[LINK](http://www.deviantart.com/deviation/46874963/)

---

### Post by rabid9797 on 2007-01-18
> **tbeld said:**
> Here's my Eye-candy with a dual-head setup!


personally i enjoy the dual cubes view than an all-in-one encompassing cube, looks too blah:-k

---

### Post by JetMars on 2007-01-18
Here is my desktop after messing around for a while, Really liking Gnome now, 

Anyone know how to get rid of the white side bit's off my dock?

---

### Post by MkfIbK7a on 2007-01-18
> **JetMars said:**
> Here is my desktop after messing around for a while, Really liking Gnome now, 

Anyone know how to get rid of the white side bit's off my dock?

yeah i think youu right click on it go properties and check something like 
show hide button

hope this helps!

---

### Post by BLTicklemonster on 2007-01-18
I think he means the side things that are left after you get rid of the hide buttons. I'd like to know how to get rid of them, too. Someone posted about it once before, but I lost track of the post. Probably in here, actually.

---

### Post by fuscia on 2007-01-18
i think you can right-click on those, as well, an choose 'remove from whatever'. i could be wrong, though.

edit: btw, i hate stupid little crap like that. the brand of teeshirts i buy are great, except this stupid little banner on them. it takes me nearly forever to get rid of them. can't anyone just make 'plain'? do i have to turn amish?

---

### Post by MkfIbK7a on 2007-01-18
> Show hide buttons determines whether there are hide buttons on the panel, which you can click to make the panel appear or disappear.

from 
apearance
 in customizing a gnome panel wiki

---

### Post by pissedoffdude on 2007-01-18
[[IMG]http://img452.imageshack.us/img452/4892/screenshotwd4.th.png[/IMG]](http://img452.imageshack.us/my.php?image=screenshotwd4.png)

---

### Post by cmmike1 on 2007-01-18
> **tbeld said:**
> Here's my Eye-candy with a dual-head setup!

Font= Aqua ([http://grsites.com/exec/public/fontview.cgi?dir=a&fn=AQUA](http://grsites.com/exec/public/fontview.cgi?dir=a&fn=AQUA))
Wallpaper=vladstudio_ornamental2_1600x1200.jpg ([www.gnome-look.org](www.gnome-look.org))
Emerald Theme=51237-VistaQ2 ([www.gnome-look.org](www.gnome-look.org))

[[IMG]http://www.uccs.edu/~langtech/thumb.Screenshot.png[/IMG]](http://www.uccs.edu/~langtech/Screenshot.png)
([http://img166.imageshack.us/img166/8469/screenshotxp7.png](http://img166.imageshack.us/img166/8469/screenshotxp7.png))
[[IMG]http://www.uccs.edu/~langtech/thumb.Screenshot-1.png[/IMG]](http://www.uccs.edu/~langtech/Screenshot-1.png)
([http://img444.imageshack.us/img444/8199/screenshot1nx8.png](http://img444.imageshack.us/img444/8199/screenshot1nx8.png))

how did you get your panel on each screen display different windows. this is probably simple to do but i couldn't figure out how to. i'm using twinview so maybe that has something to do with it.

---

### Post by kvonb on 2007-01-18
> **JetMars said:**
> Here is my desktop after messing around for a while, Really liking Gnome now, 

Anyone know how to get rid of the white side bit's off my dock?

No, you are stuck with the bloody things!  A method was suggested earlier in this thread, but I tried it and it didn't work.

They REALLY ruin a good desktop setup, it's like leaving the masking tape on after a beautiful paint job on a car :rolleyes:.

---

### Post by rabid9797 on 2007-01-18
my cube caps 8) 

[img]http://xs511.xs.to/xs511/07035/lolz.jpg[/img]

sry for the full size thing but you really need to be able to see what it is to know why its funny

---

### Post by Gen2ly on 2007-01-19
Ubuntu Standard / Webilder pic from flickr

[IMG]http://ia331337.us.archive.org/2/items/ToddPartridgeMacBook_Ubuntu_Screenshot/MacBook_Ubuntu_Screenshot.png[/IMG]

---

### Post by _simon_ on 2007-01-19
> **JetMars said:**
> Here is my desktop after messing around for a while, Really liking Gnome now, 

Anyone know how to get rid of the white side bit's off my dock?

Think those are panel handles.

I can help you with changing their colour but not with making them transparent.

Your best bet would be to use a proper dock.

I have a HOWTO on colour coding Gnome panel handles on my site along with links to 3x HOWTO's - one for Kiba-Dock, Gnome-Dock & Engage. [http://www.violet-rain.info/](http://www.violet-rain.info/)

---

### Post by urukrama on 2007-01-19
> **fuscia said:**
> 'kind o'green'

somehow, i managed to end up with a combination of the pharago and crux gtk themes (win.dec. is 'esco'). using the gnome theme manager and gtk-chtheme, at the same time, will do that sort of thing. a mix of icons and just a plain gradient wallpaper.


I quite liked that. 

How do you get Miles Davis like that  (washed out/outline/whatever) on the desktop picture? Can you do that with the Gimp?

---

### Post by der_joachim on 2007-01-19
> **rabid9797 said:**
> my cube caps 8) 

sry for the full size thing but you really need to be able to see what it is to know why its funny

Hmm... I once had the BSOD screen saver at work. My colleagues thought that my windows had crashed (I had a dual boot) and they gave my computer a hard reset. ](*,)

---

### Post by fuscia on 2007-01-19
> **urukrama said:**
> I quite liked that. 

How do you get Miles Davis like that  (washed out/outline/whatwmaker ever) on the desktop picture? Can you do that with the Gimp?

thanks. i did that in gimp taking the photo below and turning it into a transparency. then, i just pasted it onto another layer containing a gradient, adjusting the opacity of the pic until it looked the way i wanted.

---

### Post by urukrama on 2007-01-19
> **fuscia said:**
> thanks. i did that in gimp taking the photo below and turning it into a transparency. then, i just pasted it onto another layer containing a gradient, adjusting the opacity of the pic until it looked the way i wanted.

Thanks. I'll give that a try when I get home.

---

### Post by crimesaucer on 2007-01-19
I just redid my collage of Dozer Green, and created a new Emerald window theme to go with it. I also installed the Firefox and Thunderbird themes called Cylence to match my new gtkrc theme.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-33-3.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-2.png[/IMG]

---

### Post by Mr.Auer on 2007-01-19
Heres Januarys theme of mine...I like dark and blue as evident :)

---

### Post by _simon_ on 2007-01-19
As usual - click to enlarge.

[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_Friday19thJan.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/Friday19thJan.jpg) [[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_friday19thjan2.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/friday19thjan2.jpg)

---

### Post by fuscia on 2007-01-19
qvwm

---

### Post by IYY on 2007-01-19
A bit of a Fallout theme on XFCE:

[[IMG]http://img169.imageshack.us/img169/5215/screenshothl1.th.jpg[/IMG]](http://img169.imageshack.us/my.php?image=screenshothl1.jpg)

(I have two monitors with different resolutions)

---

### Post by Choad on 2007-01-19
my desktops a little cluttered right now, but whatever

[[IMG]http://img254.imageshack.us/img254/1820/screenshotir4.th.png[/IMG]](http://img254.imageshack.us/my.php?image=screenshotir4.png)

[[IMG]http://img442.imageshack.us/img442/3091/screenshot1yy1.th.png[/IMG]](http://img442.imageshack.us/my.php?image=screenshot1yy1.png)

---

### Post by Phixion on 2007-01-19
Hope you like:

[[IMG]http://img256.imageshack.us/img256/8397/200701200210001280x1024dw8.th.png[/IMG]](http://img256.imageshack.us/my.php?image=200701200210001280x1024dw8.png)

---

### Post by Kateikyoushi on 2007-01-19
Nice, any details on the used comonents ?

---

### Post by tbeld on 2007-01-19
> **cmmike1 said:**
> how did you get your panel on each screen display different windows. this is probably simple to do but i couldn't figure out how to. i'm using twinview so maybe that has something to do with it.

I'm not using either Xinerama or Twinview now. With the ATI drivers you just do:
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```
and boom you have a working dual-head setup.

Xinerama has worked for me in the past though. I don't know about Twinview, I've never used it.

---

### Post by tbeld on 2007-01-19
> **rabid9797 said:**
> personally i enjoy the dual cubes view than an all-in-one encompassing cube, looks too blah:-k

Hey, I gave that a try today. I like it better now too... Thanks!

---

### Post by timpino on 2007-01-19
> **Choad said:**
> my desktops a little cluttered right now, but whatever

[[IMG]http://img254.imageshack.us/img254/1820/screenshotir4.th.png[/IMG]](http://img254.imageshack.us/my.php?image=screenshotir4.png)

[[IMG]http://img442.imageshack.us/img442/3091/screenshot1yy1.th.png[/IMG]](http://img442.imageshack.us/my.php?image=screenshot1yy1.png)


Now that is a mighty fine gal, happen to know her name?

---

### Post by slimdog360 on 2007-01-20
> **timpino said:**
> Now that is a mighty fine gal, happen to know her name?

looks like that chick from scrubs.
 [http://en.wikipedia.org/wiki/Sarah_Chalke]("http://en.wikipedia.org/wiki/Sarah_Chalke")

---

### Post by Tiede on 2007-01-20
hmm... I think it might just be [Barbara Alyn Woods](http://www.tv.com/barbara-alyn-woods/person/6067/summary.html). Am I wrong?

---

### Post by timpino on 2007-01-20
> **Tiede said:**
> hmm... I think it might just be [Barbara Alyn Woods](http://www.tv.com/barbara-alyn-woods/person/6067/summary.html). Am I wrong?

Oh please don't let it be her... I hate deb in One Tree Hill... :)

---

### Post by DarkN00b on 2007-01-20
I'm running edgy with Beryl 0.1.99. My theme is a modified Wombat_Black theme for Emerald that I call Wombat_Blue. My menus burn away with a color-matched blue fire and my clock text was a matched blue as well, but it was kinda hard to see. The skydome is a seamless nebula pic I got from NASA's Hubble telescope site.

Here's the (offsite) pics:

[IMG]http://img.photobucket.com/albums/v191/DarkN00b/Caps/desktop.png[/IMG]
[IMG]http://img.photobucket.com/albums/v191/DarkN00b/Caps/CubeShot.png[/IMG]
[IMG]http://img.photobucket.com/albums/v191/DarkN00b/Caps/3D.png[/IMG]

---

### Post by WetWired on 2007-01-20
Here's mine.

[http://www.packet-surge.com/newflux.jpeg](http://www.packet-surge.com/newflux.jpeg)

---

### Post by Choad on 2007-01-20
> **timpino said:**
> Now that is a mighty fine gal, happen to know her name?
sarah chalke aka elliot from scrubs

---

### Post by kairu0 on 2007-01-20
My desktop is always cleanest in January :-P

---

### Post by crimesaucer on 2007-01-20
Is that somewhere in Yosemite?

---

### Post by bvc on 2007-01-20
> **crimesaucer said:**
> Is that somewhere in Yosemite?
I don't know but I would like a link to it!

---

### Post by fuscia on 2007-01-20
i think i saw that yosemite pic on interfacelift.

---

### Post by darkhatter on 2007-01-20
I really need to clean that desktop.....

[[IMG]http://img260.imageshack.us/img260/3969/messywindows3ug.th.jpg[/IMG]](http://img260.imageshack.us/my.php?image=messywindows3ug.jpg)

---

### Post by bvc on 2007-01-20
> **fuscia said:**
> i think i saw that yosemite pic on interfacelift.Thank you!
[http://interfacelift.com/wallpaper/details.php?id=1097](http://interfacelift.com/wallpaper/details.php?id=1097)

---

### Post by Falcorian on 2007-01-20
Here's mine, with conky.

---

### Post by bonzodog on 2007-01-20
This is my Clean Openbox Desktop on Zenwalk.

[[img]http://xs211.xs.to/xs211/07035/openzen.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs211&d=07035&f=openzen.png)

Uses Rezlooks-Graphite for the gtk theme, and that is a wm dockapp in the corner with peksystray for gaim.

---

### Post by FastZ on 2007-01-20
My desktop

[[IMG]http://ubuntuforums.org/gallery/data/540/thumbs/20Jan07-3.png[/IMG]]("http://ubuntuforums.org/gallery/data/540/20Jan07-3.png")

---

### Post by FastZ on 2007-01-20
My laptop

[[IMG]http://ubuntuforums.org/gallery/data/540/thumbs/20Jan07-Laptop.png[/IMG]]("http://ubuntuforums.org/gallery/data/540/20Jan07-Laptop.png")

---

### Post by kairu0 on 2007-01-20
> **fuscia said:**
> i think i saw that yosemite pic on interfacelift.

Bravo! Yes, it is from InterfaceLift!

---

### Post by Quillz on 2007-01-20
[[IMG]http://img370.imageshack.us/img370/1736/desktop0120073ya.png[/IMG]]("http://www.quillz.net/random/desktop/desktop_012007.png")

It's actually openSUSE 10.2 on my notebook computer, but the theme itself can easily be replicated on Kubuntu 6.10.

---

### Post by bvc on 2007-01-20
> **Quillz said:**
> 
It's actually openSUSE 10.2 on my notebook computer, but the theme itself can easily be replicated on Kubuntu 6.10.got a link to that wallpaper?

---

### Post by featherking on 2007-01-20
Wallpaper was made in inkscape, i found it on art.gnome.org and it was really bright blue, so i dulled it down it gimp. I made the panels black with white text and just a little transparent, also the gnome-terminal is transparent black. Using beryl with emerald and the scaled black mod theme.

Generally i dont use black themes, but i have definately stumbled on something i like...

---

### Post by fuscia on 2007-01-21
just finished setting up a dual boot with sabayon (at least, i *think* it's a dual boot. i haven't looked to see if ubuntu is still there, yet). here's my first screeny from it.

the icons are the kde crystal diamond set and the wallpaper is a homade collage...kind of...

---

### Post by Quillz on 2007-01-21
> **bvc said:**
> got a link to that wallpaper?
I found it on KDE-Look.org, where it's known as "Night."

[Download it from here.]("http://www.quillz.net/random/wallpaper/Night.jpg")

---

### Post by Phatfiddler on 2007-01-21
My desktop:
[IMG]http://cutlersoftware.com/images/Screenshot2.png[/IMG]

---

### Post by mrWoot on 2007-01-21
I like going for the minimalistic way.

---

### Post by riven0 on 2007-01-21
Well, guess it's time to share my desktop! :p

---

### Post by viper on 2007-01-21
> **fuscia said:**
> just finished setting up a dual boot with sabayon (at least, i *think* it's a dual boot. i haven't looked to see if ubuntu is still there, yet). here's my first screeny from it.

the icons are the kde crystal diamond set and the wallpaper is a homade collage...kind of...

Cool wallpaper.....

---

### Post by viper on 2007-01-21
My current desktop, comments welcome..........
[http://ubuntuforums.org/gallery/showphoto.php/photo/4800](http://ubuntuforums.org/gallery/showphoto.php/photo/4800)

---

### Post by MkfIbK7a on 2007-01-21
whooooo boy awesome new fvwm-crystal desktop!

it looks better at the original 1400x1280 but you know it was too big:biggrin:

---

### Post by Tmi on 2007-01-21
This is how mine looks like at the moment.

If anyone wants the wallpaper it can be found [here]("http://interfacelift.com/wallpaper/details.php?id=859").

---

### Post by mostwanted on 2007-01-21
Here's mine. I'm using the latest SVN version of Beryl...

---

### Post by Hieronymus on 2007-01-21
This is my Edgy Eft @ 1280x800

I got the wp from [deviantART.]("http://www.deviantart.com/deviation/16677420/")
The gkrellm theme is [niumx.]("http://www.muhri.net/gkrellm/niumx.tar.gz")
The emerald theme is adonis_mod @ vrunner engine.
And the WM is clearly Gnome with Beryl running.

Jeroen

---

### Post by graabein on 2007-01-21
I'm going for a [darker look]("http://ubuntuforums.org/gallery/showphoto.php/photo/4802") in January...

---

### Post by fuscia on 2007-01-21
> **viper said:**
> Cool wallpaper.....

thanks, dude.

---

### Post by BLTicklemonster on 2007-01-21
Seeing's how Linux is all about freedom and all, here's my desktop right this second for now until I go changing it again*.

[[IMG]http://img441.imageshack.us/img441/8734/jan21dt0zv.th.png[/IMG]](http://img441.imageshack.us/my.php?image=jan21dt0zv.png)

From a picture I took last spring on a trip to Nyark.






*cuz I'm free to do so, of course :)


(and yeah, I got to redo that a bit, I did the logo then on a whim decided to put it on the brickwork. I'll redo it one day and post back the results and see if it's any better)

---

### Post by bvc on 2007-01-21
> **Quillz said:**
> I found it on KDE-Look.org, where it's known as "Night."

[Download it from here.]("http://www.quillz.net/random/wallpaper/Night.jpg")Thank you!

---

### Post by crimesaucer on 2007-01-21
@fuscia- Hey fuscia, I've been having troubles with the download and extraction of the "Human Ultra" icon theme pack from gnome-looks.

Is there anyway I could get that icon pack from you. I would love to have those folders but I keep getting the same error in archiver, and the same empty folder in /tmp.

---

### Post by Wight_Rhino on 2007-01-21
My xfce screen. Conky, Thunar, Xfmedia, Orage, Xfce-term, gcalc. Murrina engine.

[[IMG]http://img266.imageshack.us/img266/760/screenshot19pq.th.png[/IMG]](http://img266.imageshack.us/my.php?image=screenshot19pq.png)

---

### Post by EdThaSlayer on 2007-01-21
I use a customized version of Amaranth theme.
-
Controls-Amaranth
Window Border-Chiro
Icon-Amaranth

Clean view:
[[IMG]http://img19.imageshack.us/img19/4535/mycurrentdesktop6rz.th.jpg[/IMG]](http://img19.imageshack.us/my.php?image=mycurrentdesktop6rz.jpg)

View with window open:
[[IMG]http://img201.imageshack.us/img201/6748/screenshot16gz.th.jpg[/IMG]](http://img201.imageshack.us/my.php?image=screenshot16gz.jpg)

---

### Post by fuscia on 2007-01-21
> **crimesaucer said:**
> @fuscia- Hey fuscia, I've been having troubles with the download and extraction of the "Human Ultra" icon theme pack from gnome-looks.

Is there anyway I could get that icon pack from you. I would love to have those folders but I keep getting the same error in archiver, and the same empty folder in /tmp.

ouch! i don't think i have them anymore (just installed sabayon, a kde centric distro). they are a pain in the butt to get and install. so, you succeeded in getting the tarball? if you did, you can just untar it and you'll find little tarballs for each color, inside. in the meantime, i'll look and see if i saved them somewhere.

---

### Post by anon32 on 2007-01-21
Ubuntu 6.10 w/ Beryl 0.2.0-beta2 (ATi Radeon X300SE on radeon drivers)

[http://img460.imageshack.us/img460/450/screenshot9yx.png](http://img460.imageshack.us/img460/450/screenshot9yx.png)

The wallpaper is "Alpha and Omega 3" by Shirosynth ( [http://shirosynth.deviantart.com/](http://shirosynth.deviantart.com/) ).
On the viewport 1 (left) is firefox and x-chat, on viewport 2 (center) is Bleach ep 59 in mplayer, and on viewport 3 (right) is uTorrent in wine.

---

### Post by MkfIbK7a on 2007-01-21
slightly new theme
the terminal is completely tranparent:biggrin:

---

### Post by tigerpants on 2007-01-21
Wert, that is a sweet desktop.

Here's my latest Gnome effort. I'm currently cycling between E17, Flux and Gnome, which I have a love hate relationship with.

I've come to the conclusion that I hate docks, so I got rid of gdesklets, and conky is really cool but annoying when its blinged up and covering half your desktop, so I cut it down abit.

---

### Post by MkfIbK7a on 2007-01-21
lol nice but whats with the rabbit or whatever that is for synaptic?

---

### Post by tigerpants on 2007-01-21
> **wert613 said:**
> lol nice but whats with the rabbit or whatever that is for synaptic?

I have no idea where i got that from, i just found it in my home folder so I used it :D

---

### Post by bvc on 2007-01-21
[MurrinaBreathe screenie]("http://gnomethemes.org/pre/screenshots/MurrinaBreathe.jpg")

[Murrine Theme]("http://gnomethemes.org/?p=81")

---

### Post by MkfIbK7a on 2007-01-21
> **tigerpants said:**
> I have no idea where i got that from, i just found it in my home folder so I used it :D

lol good enough for me:biggrin: :biggrin:

---

### Post by crimesaucer on 2007-01-21
Thank you fuscia, my xarchiver was having problems unpacking such a large file, and I had been writing the wrong tar options in terminal, but I figured it out and got it working and it made my whole desktop theme complete. Thank you.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-40-2.png[/IMG]

---

### Post by ComplexNumber on 2007-01-21
i wanted a more earthy desktop this time. i like this wallpaper because its easy on the eye and has has laid back colours. the overall theme of wallpaper + gtk theme + icons focuses on browns and greys.

gtk: clearlooks-gp-Human
metacity: clearlooks
icons: tango-oldplaingrey
wallpaper: Spring Fog

---

### Post by finferflu on 2007-01-21
I basically changed the shelf arrangement and the wallpaper... still, I love it!

---

### Post by Choad on 2007-01-21
pretty lush theme there. :)

---

### Post by fuscia on 2007-01-21
> **crimesaucer said:**
> Thank you fuscia, my xarchiver was having problems unpacking such a large file, and I had been writing the wrong tar options in terminal, but I figured it out and got it working and it made my whole desktop theme complete. Thank you.


that looks good, dude. i love the mix of different qualities of a color.

---

### Post by crimesaucer on 2007-01-21
Thanks, and now with all of those different choices of icons I can always have a folder theme to go with whatever way I theme my gtkrc, Emerald, and desktop wallpaper.

Thanks again, I usually visit xfce-looks, and they don't have that icon theme pack on there, so I didn't even know it existed.

---

### Post by fuscia on 2007-01-21
> **crimesaucer said:**
> Thanks, and now with all of those different choices of icons I can always have a folder theme to go with whatever way I theme my gtkrc, Emerald, and desktop wallpaper.

Thanks again, I usually visit xfce-looks, and they don't have that icon theme pack on there, so I didn't even know it existed.

i've used kde icons in xfce. check out the black+white icon theme. also, you can get the dreamlinux icons if you have some kind of usb drive. i use those all the time.

---

### Post by crimesaucer on 2007-01-21
Cool, I'll check that out.

---

### Post by bvc on 2007-01-21
> **ComplexNumber said:**
> i wanted a more earthy desktop this time. i like this wallpaper because its easy on the eye and has has laid back colours. the overall theme of wallpaper + gtk theme + icons focuses on browns and greys.

gtk: clearlooks-gp-Human
metacity: clearlooks
icons: tango-oldplaingrey
wallpaper: Spring FogNice combo! I forgot about Clearlooks-gp-Human2. I might need to make that into a CL_Cairo theme.

---

### Post by SendDerek on 2007-01-21
My Humble January Screenshot and Splash Screen:

---

### Post by gamma on 2007-01-21
My latest.. nothing great, kind of minimalist. :P I like the default gnome look.

[[img]http://home.cfl.rr.com/gamma/images/ss-t.png[/img]](http://home.cfl.rr.com/gamma/images/ss.png)

---

### Post by aristotlewilde on 2007-01-22
I am brand new to Beryl.  How do you get your windows to lay like they do in your bottom picture?  


> **crimesaucer said:**
> I just redid my collage of Dozer Green, and created a new Emerald window theme to go with it. I also installed the Firefox and Thunderbird themes called Cylence to match my new gtkrc theme.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-33-3.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-2.png[/IMG]

---

### Post by plb on 2007-01-22
new one.

---

### Post by ahaslam on 2007-01-22
My Zenwalk partition:

[ATTACH]23656[/ATTACH]

Tony ;)

---

### Post by linuxuser28 on 2007-01-22
My desktop at work.

---

### Post by klato on 2007-01-22
Cool.  How did you get your fonts to look so nice and smooth?  What font/size/settings is it?

---

### Post by mostwanted on 2007-01-22
> **linuxuser28 said:**
> My desktop at work.

Mind if I ask: what is your occupation since you get to use a nice Gnome desktop as your workstation?

---

### Post by linuxuser28 on 2007-01-22
Computer recycling. That is how I get to try Ubuntu on so many different machines. :D
                                       Since dropping Microsoft Access for our inventory system, I'm able to use Ubuntu for everything here now.

---

### Post by PatrickMay16 on 2007-01-22
> **linuxuser28 said:**
> My desktop at work.

Hey, that's good. Also, my sister really likes Van Morrison.

---

### Post by _simon_ on 2007-01-22
[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_DeadFish.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/DeadFish.jpg)

---

### Post by xabbott on 2007-01-22
Who needs X? Terminal shot. :P
[[img]http://xs511.xs.to/xs511/07042/here.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs511&d=07042&f=here.png)

---

### Post by finferflu on 2007-01-22
> **plb said:**
> new one.
What messenger are you using there? I'm curious :P

> **xabbott said:**
> Who needs X? Terminal shot. :P
[[img]http://xs511.xs.to/xs511/07042/here.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs511&d=07042&f=here.png)

You need X in order to view screenshots, or am I wrong? Or perhaps you don't need to view screenshots? :biggrin: just joking!

---

### Post by Quillz on 2007-01-22
Here's my new desktop. Been playing around with the panels a bit, especially since Kiba-Dock doesn't work for me on the desktop. It's a shame you can't make the panel border button transparent.

[[IMG]http://img375.imageshack.us/img375/298/desktop0122079ez.png[/IMG]]("http://www.quillz.net/random/desktop/desktop_012207.png")

---

### Post by yabbadabbadont on 2007-01-22
> **finferflu said:**
> What messenger are you using there? I'm curious :P



You need X in order to view screenshots, or am I wrong? Or perhaps you don't need to view screenshots? :biggrin: just joking!

As long as you have SDL or are using the framebuffer, you can view graphics without X.  Search Synaptic for "fbi".  (frame buffer imageviewer)  :D

---

### Post by murlosad on 2007-01-22
First time I've posted an Ubuntu desktop.  It's alphacube gtk with glass icons, and just green emerald theme. Also using adesklets Calendar, weatherForcaster, and SystemMonitor

[[IMG]http://static.zooomr.com/images/669796_c422c4011f_m.jpg[/IMG]]("http://static.zooomr.com/images/669796_c422c4011f_b.jpg")

---

### Post by Choad on 2007-01-22
> **linuxuser28 said:**
> My desktop at work.
whats that music thing in the corner? pretty slick!

---

### Post by fuscia on 2007-01-22
> **_simon_ said:**
> [[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_DeadFish.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/DeadFish.jpg)

now ***that*** is a fine wallpaper!

---

### Post by Bachstelze on 2007-01-22
Had to change my usual style(which is rather like my avatar's) to meet the "safe for work" requirement but there :

[[IMG]http://img253.imageshack.us/img253/2597/desktop200701234vp.th.jpg[/IMG]](http://img253.imageshack.us/img253/2597/desktop200701234vp.jpg)

The metalheads among you will have recognized the artwork from Rhapsody's *Power Of The Dragonflame*. As you can see, it'a KDE 3.5.5 desktop running in FreeBSD 6.2-STABLE with the [BioHazard Monitor](http://www.kde-look.org/content/show.php?content=25363) SuperKaramba applets and a nice Konsole window with a kernel compilation in progress. For those who would like the "clean" wallpaper, it's [there](http://www.rhapsodyoffire.com/pics/downloads/wallpaper/large/dragonfull1024x768.jpg).

---

### Post by ComplexNumber on 2007-01-22
> **bvc said:**
> Nice combo! I forgot about Clearlooks-gp-Human2. I might need to make that into a CL_Cairo theme.
thanks. clearlooks-gp-human2 is a nice theme. what is the typical difference between the cairo version and the ordinary one? 


---------------------------


my new desktop. 
gtk: tactile
metacity: tactile
icons: Gflat SVG
wallpaper: new life

---

### Post by m.musashi on 2007-01-22
> **murlosad said:**
> First time I've posted an Ubuntu desktop.  It's alphacube gtk with glass icons, and just green emerald theme. Also using adesklets Calendar, weatherForcaster, and SystemMonitor

[[IMG]http://static.zooomr.com/images/669796_c422c4011f_m.jpg[/IMG]]("http://static.zooomr.com/images/669796_c422c4011f_b.jpg")

Is that system monitor from gdesklet or something else? It looks nice. Rather hot cpu you have though. Is that accurate?

---

### Post by yabbadabbadont on 2007-01-23
> **m.musashi said:**
> Is that system monitor from gdesklet or something else? It looks nice. Rather hot cpu you have though. Is that accurate?

> Also using adesklets Calendar, weatherForcaster, and SystemMonitor
It is an adesklet.  They are similar to gdesklets, but are python apps using the adesklets framework.

---

### Post by m.musashi on 2007-01-23
> **yabbadabbadont said:**
> It is an adesklet.  They are similar to gdesklets, but are python apps using the adesklets framework.

Thanks. I'm checking them out right now.

---

### Post by kimara on 2007-01-23
Haiku under qemu

---

### Post by _simon_ on 2007-01-23
> **fuscia said:**
> now ***that*** is a fine wallpaper!

Here if you want it :)

[http://www.caedes.net/Zephir.cgi?lib=Caedes::Infopage&image=monkeypuzzle-1070596347.jpg](http://www.caedes.net/Zephir.cgi?lib=Caedes::Infopage&image=monkeypuzzle-1070596347.jpg)

I did modify mine slightly - the black background has artifacts so I got rid of those.

---

### Post by crimesaucer on 2007-01-23
@ aristotlewild- The way those windows look like that is to go to your Beryl Settings Manager-->--General Options-->--Main, and then in "Main" look for "Horizontal Virtual Size" that is set at 4, and change it to 3 to make your cube a triangle. 

Then go to Beryl Settings Manager-->--Desktop-->--Desktop Cube-->--Caps-->-- and then uncheck the "draw caps" box to just show the three sides of your triangle and no cap (since a cube cap won't show correctly anyway).

---

### Post by aristotlewilde on 2007-01-23
> **crimesaucer said:**
> @ aristotlewild- The way those windows look like that is to go to your Beryl Settings Manager-->--General Options-->--Main, and then in "Main" look for "Horizontal Virtual Size" that is set at 4, and change it to 3 to make your cube a triangle. 

Then go to Beryl Settings Manager-->--Desktop-->--Desktop Cube-->--Caps-->-- and then uncheck the "draw caps" box to just show the three sides of your triangle and no cap (since a cube cap won't show correctly anyway).

Thanks!

---

### Post by fuscia on 2007-01-23
> **_simon_ said:**
> Here if you want it :)

[http://www.caedes.net/Zephir.cgi?lib=Caedes::Infopage&image=monkeypuzzle-1070596347.jpg](http://www.caedes.net/Zephir.cgi?lib=Caedes::Infopage&image=monkeypuzzle-1070596347.jpg)

I did modify mine slightly - the black background has artifacts so I got rid of those.

thank you.

---

### Post by grovsnus22 on 2007-01-23
Here´s my current setup:

[[IMG]http://img260.imageshack.us/img260/1529/0701237pv.th.png[/IMG]](http://img260.imageshack.us/my.php?image=0701237pv.png)

---

### Post by murlosad on 2007-01-23
yup, adesklets it is, it's less cpu intensive, and as far as I can tell accurate.  I've got a new cpu heatsink and fan on order, the bearing is dying a slow death on my current fan.

---

### Post by kimara on 2007-01-23
> **grovsnus22 said:**
> Here´s my current setup:

[[IMG]http://img260.imageshack.us/img260/1529/0701237pv.th.png[/IMG]](http://img260.imageshack.us/my.php?image=0701237pv.png)

What icons you are using and where to get it, thanks..

---

### Post by grovsnus22 on 2007-01-23
> **kimara said:**
> What icons you are using and where to get it, thanks..

They´re called Snowish, here you go:
[http://www.gnome-look.org/content/show.php?content=32599](http://www.gnome-look.org/content/show.php?content=32599)

---

### Post by Quillz on 2007-01-23
> **grovsnus22 said:**
> Here´s my current setup:

[[IMG]http://img260.imageshack.us/img260/1529/0701237pv.th.png[/IMG]](http://img260.imageshack.us/my.php?image=0701237pv.png)
That's a nice icon pack. Thanks for posting the download link.

---

### Post by MkfIbK7a on 2007-01-23
here are just a few of the extremely easy to set up fvwm-crystal themes

the first is the default look the second is like windows and the third is like mac

sorry about the bad quality my resolution is 1400x1280 so i had to compress the files

---

### Post by truthfatal on 2007-01-23
Some minor tweaks from my last post here.

Changed the emerald theme to something lighter and grabbed skydome from [This guy](http://forum.beryl-project.org/viewtopic.php?f=55&t=1071) (thanks btw :) )

---

### Post by TheRingmaster on 2007-01-23
is anyone using superkaramba for their widgets? (one question: Is superkaramba dependant on kde libs?)

---

### Post by ComplexNumber on 2007-01-23
> **TheRingmaster said:**
> (one question: Is superkaramba dependant on kde libs?)
yes.

---

### Post by aristotlewilde on 2007-01-23
Have been playing around with Beryl.  Still don't know how to take a screenshot during Beryl animations, but here is my new desktop...

---

### Post by TheRingmaster on 2007-01-23
> **aristotlewilde said:**
> Have been playing around with Beryl.  Still don't know how to take a screenshot during Beryl animations, but here is my new desktop...


if my memory serves me correctly. You just hold down the alt key (may be ctrl key. I am not sure) and then click and drag your mouse over the portion you want to be in the screenshot.

---

### Post by Polygon on 2007-01-23
> **HymnToLife said:**
> Had to change my usual style(which is rather like my avatar's) to meet the "safe for work" requirement but there :

[[IMG]http://img253.imageshack.us/img253/2597/desktop200701234vp.th.jpg[/IMG]](http://img253.imageshack.us/img253/2597/desktop200701234vp.jpg)

The metalheads among you will have recognized the artwork from Rhapsody's *Power Of The Dragonflame*. As you can see, it'a KDE 3.5.5 desktop running in FreeBSD 6.2-STABLE with the [BioHazard Monitor](http://www.kde-look.org/content/show.php?content=25363) SuperKaramba applets and a nice Konsole window with a kernel compilation in progress. For those who would like the "clean" wallpaper, it's [there](http://www.rhapsodyoffire.com/pics/downloads/wallpaper/large/dragonfull1024x768.jpg).

yeah, im a metal head. I looked at your wallpaper and i was like "i recognize that dragon from somewhere..." and then remembered its from the power of the dragon flame cover art. Nice =P

and your url for the wallpaper is wrong (typo), so here is the correct one: [http://www.rhapsodyoffire.com/pics/downloads/wallpaper/large/dragonfull1024x768.jpg](http://www.rhapsodyoffire.com/pics/downloads/wallpaper/large/dragonfull1024x768.jpg)

---

### Post by Quillz on 2007-01-23
> **TheRingmaster said:**
> if my memory serves me correctly. You just hold down the alt key (may be ctrl key. I am not sure) and then click and drag your mouse over the portion you want to be in the screenshot.
Hmm... This isn't working for me.

---

### Post by TheRingmaster on 2007-01-23
> **Quillz said:**
> Hmm... This isn't working for me.

I don't have beryl right now. But it could be super+click and drag mouse

ps. you may want to check your beryl setting manager to get the correct key bindings.
):P

---

### Post by Quillz on 2007-01-23
> **TheRingmaster said:**
> I don't have beryl right now. But it could be super+click and drag mouse

ps. you may want to check your beryl setting manager to get the correct key bindings.
):P
Got it working. I just press the Prnt Scrn button and it worked.

---

### Post by ~LoKe on 2007-01-23
Print screen will screenshot your entire screen.  Alt+pritn screen will screenshot the focused window.  If you have beryl, holding the super key (windows! key) and drag your mouse, the part in your selection will be screenshotted.

---

### Post by m.musashi on 2007-01-24
laptop with beryl. The current svn, however, won't let me open up beryl-settings. I hope that will be fixed soon as there are few settings I'd like to change. Emerald is stock theme. I need to download the onyx themes on this machine but until I do this is fine. Notice the cool icons for the drives. I found them on gnome-look. I think they are called human strange or something.

---

### Post by ~LoKe on 2007-01-24
Install beryl-settings-bindings.

---

### Post by TheRingmaster on 2007-01-24
> **~LoKe said:**
> Print screen will screenshot your entire screen.  Alt+pritn screen will screenshot the focused window.  If you have beryl, holding the super key (windows! key) and drag your mouse, the part in your selection will be screenshotted.

that's what i said.:guitar:

---

### Post by Quillz on 2007-01-24
This isn't working for me.

---

### Post by fuscia on 2007-01-24
i'm not sure i even like this one...

---

### Post by ComplexNumber on 2007-01-24
> **fuscia said:**
> i'm not sure i even like this one...
the effect would have been much better if you got rid of that relatively intense green in the bottom right of the picture. i assume you did the effects yourself.

---

### Post by fuscia on 2007-01-24
> **ComplexNumber said:**
> the effect would have been much better if you got rid of that relatively intense green in the bottom right of the picture. i assume you did the effects yourself.

it took me hours to get that intense green just right.:mad:

---

### Post by ComplexNumber on 2007-01-24
> **fuscia said:**
> it took me hours to get that intense green just right.:mad:

get rid of it man! it looks awful :p. seriously, i don't think it blends with the rest of the picture at all. sometimes, a picture suits having something highlighted to draw the viewers eye to it, but its highlighting something that seems to mean nothing, so it looks like its a mistake.

---

### Post by fuscia on 2007-01-24
> **ComplexNumber said:**
> get rid of it man! it looks awful :p. seriously, i don't think it blends with the rest of the picture at all. sometimes, a picture suits having something highlighted to draw the viewers eye to it, but its highlighting something that seems to mean nothing, so it looks like its a mistake.

i've got it!!!

---

### Post by ComplexNumber on 2007-01-24
very intense, but a bit better.

---

### Post by fuscia on 2007-01-24
> **ComplexNumber said:**
> very intense, but a bit better.

are you serious? i was joking. i've switched it to something else (which i'm also displeased with).

---

### Post by ComplexNumber on 2007-01-24
> **fuscia said:**
> are you serious? i was joking. i've switched it to something else (which i'm also displeased with).
yup, i were serious.

---

### Post by Choad on 2007-01-24
> **TheRingmaster said:**
> I don't have beryl right now. But it could be super+click and drag mouse

ps. you may want to check your beryl setting manager to get the correct key bindings.
):P
genius! i always envied that feature form osX

not any more :)

---

### Post by fuscia on 2007-01-24
> **ComplexNumber said:**
> yup, i were serious.

that's funny. i will often look in the galleries and see the same screen with a rating of 1.0 from one person and a 10.0 from the next. you can never really tell what people are going to like.

---

### Post by ComplexNumber on 2007-01-24
> **fuscia said:**
> that's funny. i will often look in the galleries and see the same screen with a rating of 1.0 from one person and a 10.0 from the next. you can never really tell what people are going to like.
different people's aesthetic sense varies remarkably.

---

### Post by TheRingmaster on 2007-01-24
> **Quillz said:**
> This isn't working for me.

what version of beryl do you have??

---

### Post by Quillz on 2007-01-24
0.2.0 beta2

The super key does nothing for me, nor does alt or control keys. But it's not big deal, since Prnt Scrn seems to take a screenshot nonetheless.

---

### Post by TheRingmaster on 2007-01-24
> **Quillz said:**
> 0.2.0 beta2

The super key does nothing for me, nor does alt or control keys. But it's not big deal, since Prnt Scrn seems to take a screenshot nonetheless.

last I used beryl (0.1.4) the super + grab and drag mouse did work.

---

### Post by fuscia on 2007-01-24
openbox, on sabayon, with pypanel. this might be *too* fast.

---

### Post by TheRingmaster on 2007-01-24
> **fuscia said:**
> openbox, on sabayon, with pypanel. this might be *too* fast.


Is that burnt rubber I smell?

---

### Post by ~LoKe on 2007-01-24
Got tired of trying to find some 2560x1024 wallpapers that weren't mountains and skies.

[[IMG]http://img460.imageshack.us/img460/104/desktop9nw.th.png[/IMG]](http://img460.imageshack.us/img460/104/desktop9nw.png)

---

### Post by MkfIbK7a on 2007-01-24
what music player is that?

---

### Post by ~LoKe on 2007-01-24
MPD, with the ncmpc front-end.

---

### Post by MkfIbK7a on 2007-01-24
> **~LoKe said:**
> MPD, with the ncmpc front-end.

thx:D

---

### Post by xpod on 2007-01-24
[ATTACH]23789[/ATTACH]

Had a bit of white snow in London today but i prefer the blue variety:D

---

### Post by helloyo on 2007-01-24
heres my desktop, i find it very comfy to use:

---

### Post by SmiLey497 on 2007-01-24
:d

---

### Post by m.musashi on 2007-01-24
> **fuscia said:**
> i've got it!!!
This one is pretty cool if you ask me. You have some interesting tastes (interesting in a good sense) but I don't know how you can actually work with most of your setups. I think you should run some sort of computer art gallery. Each display can be some messed up piece of a computer with some weird linux distro and your theme art. I'd pay 10 bucks to tour such a gallery (if I were in the neighborhood of the long leaf pine.

> **fuscia said:**
> openbox, on sabayon, with pypanel. this might be *too* fast.

Are these all the same box or do you have like 20 computers running in various rooms? (or are they in your gallery?)

> **~LoKe said:**
> Got tired of trying to find some 2560x1024 wallpapers that weren't mountains and skies.

[[IMG]http://img460.imageshack.us/img460/104/desktop9nw.th.png[/IMG]](http://img460.imageshack.us/img460/104/desktop9nw.png)

What, that's not a mid winter sky?

> **SmiLey497 said:**
> :d
That is one of the best walls I've ever seen. However, it should be a vista box as I think it will be even more deserving of a flush.

(I wonder how much longer I can make this post...)

---

### Post by fuscia on 2007-01-24
> **TheRingmaster said:**
> Is that burnt rubber I smell?

no, that's burnt lambskin, my friend. pass the mint jelly.

[quote=m.musashi]This one is pretty cool if you ask me. You have some interesting tastes (interesting in a good sense) but I don't know how you can actually work with most of your setups. I think you should run some sort of computer art gallery. Each display can be some messed up piece of a computer with some weird linux distro and your theme art. I'd pay 10 bucks to tour such a gallery (if I were in the neighborhood of the long leaf pine.[/quote]

there's an idea. i bet there's lots of 'sucker' grant money for something like that. too bad i got screwed in the initiative department.

all on the same box, btw. if i had a bunch of boxes, i'd be wanting to switch one setup to another box, constantly.

---

### Post by testube_babies on 2007-01-24
I made some wallpapers based on [Babaorum]("http://gnome-look.org/content/show.php?content=48742"), then I couldn't decide whether to make my desktop look too much like OS X or Vista.

[[IMG]http://img318.imageshack.us/img318/5417/vistashot6xc.th.jpg[/IMG]](http://img318.imageshack.us/my.php?image=vistashot6xc.jpg) [[IMG]http://img318.imageshack.us/img318/5725/osxshot0ii.th.jpg[/IMG]](http://img318.imageshack.us/my.php?image=osxshot0ii.jpg)

---

### Post by fuscia on 2007-01-24
shut me off. i've had enough...

---

### Post by m.musashi on 2007-01-24
> **~LoKe said:**
> Install beryl-settings-bindings.

Thanks for the tip but it didn't seem to fix the problem. Not sure what is going on.

---

### Post by kuja on 2007-01-25
Well, i t has been a few months since I changed themes, so I did. I think I like the way it turned out.

---

### Post by kriwil on 2007-01-25
> **SmiLey497 said:**
> :d

nice wallpaper :D
could you share the link?

---

### Post by ice60 on 2007-01-25
here's mine -

[[img]http://xs411.xs.to/xs411/07044/Screenshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs411&d=07044&f=Screenshot.png)

---

### Post by Tweedicus on 2007-01-25
Hi,

The pictures on the sticky January 2007 Desktop Thread were truly great.

However, some of us grad students are poor so run five year old machines (Thinkpad T23 in my case) with 8 mb graphics cards. 

And we run these machines because they're ultra reliable and run Edgy tres fast.

BUT they will not run Compiz or Beryl. And some of us don't have the technical ability to do complext desktops.

All we want is something which is simple but looks real nice. Perhaps a special icon, window, and wallpaper theme, and maybe some minor special effects.

Perhaps some of you with older machines could post Desktop pictures with details so we could get inspired to change our own tired Desktops.

Here's mine: some Mac rip-off wall-paper and window borders, with crystal icon theme, and transparent panels.

Cheers,

Tweed

---

### Post by SmiLey497 on 2007-01-25
[http://www.kde-look.org/content/show.php?content=32716]("http://www.kde-look.org/content/show.php?content=32716")

---

### Post by ComplexNumber on 2007-01-25
don't see your reasoning at all. just because some of our computers can run beryl and all the silly effects, doesn't mean to say that those who can, will.
one doesn't need all those silly effects to make a desktop look nice. the only requirements are some themes, icons, and some creativity with a good eye for colour and balance. 
beryl/compiz is just a cheap 2 minute frill.

---

### Post by Tweedicus on 2007-01-25
Perhaps I wasn't clear.

The point was a lot of the great desktops displayed are not possible for us to do on the older machines.

So it would be nice to see some simple, easy to do, Desktops which would run on older machines. Especially for newer users

No controversy.

---

### Post by mcduck on 2007-01-25
> **fuscia said:**
> shut me off. i've had enough...

I love the wallpaper.. Can I have it? Please?

---

### Post by ComplexNumber on 2007-01-25
>  The point was a lot of the great desktops displayed are not possible for us to do on the older machines.so what? doesn't make those using frilly effects any better or more aesthetic.

---

### Post by Tweedicus on 2007-01-25
Er... I don't think I said it did.

I said that the desktops looked nice, which in my opinion they do, but we can't do them on older machines.

Therefore, it would be nice to see some simpler desktops which would run on older machines and which newer users could implement.

The line of reasoning really isn't that hard to follow, and it's really not argumentative either.

As the sticky thread has 600+ posts and as a lot of them are either too difficult to do for newer users, or they wouldn't know how to do them, or they wouldn't run on older machines, it would be nice to see some simpler Desktops which we could run.

It's really not an *issue*

---

### Post by SmiLey497 on 2007-01-25
my KDE desktop, nothing fancy

---

### Post by Brunellus on 2007-01-25
Threads are merged.  The monthly screenshot thread was begun as a means of managing this sort of screenshot thread unraveling.  We used to have multiple parallel screenshot threads.

Nothing in the thread title says "you may only post if you're 1337 and/or have HUGE system specs."  Perfectly humble screenshots are acceptable and indeed encouraged.

---

### Post by ComplexNumber on 2007-01-25
[quote=tweedicus]  I said that the desktops looked nice, which in my opinion they do, but we can't do them on older machines.

Therefore, it would be nice to see some simpler desktops which would run on older machines and which newer users could implement.[/quote]
don't make the assumption that just because some people need a 2 storey fridge to cool their graphics chip that people are going to use every single CPU cycle in desktop effects. a screenshot is not to show off effects, but more to show off people's creativity and how nice they can make their desktop look. like i said, beryl and silly effects are definitely  not a prerequisite for that  purpose.  in other words, you're missing the point of a screenshot thread.

---

### Post by doobit on 2007-01-25
Enlightenment can really look beautiful and works great on older machines. I was impressed on how well it works with my AMD Athlon 800 machine with an old Nvidia DDR card.
I use Xubuntu as well and can get a nice looking, functional desktop with that.

---

### Post by Sunflower1970 on 2007-01-25
> **doobit said:**
> Enlightenment can really look beautiful and works great on older machines. I was impressed on how well it works with my AMD Athlon 800 machine with an old Nvidia DDR card.
I use Xubuntu as well and can get a nice looking, functional desktop with that.

I'm impressed with Enlightenment. I downloaded the Elive CD just to see what that was all about..although I haven't installed it yet (I'm waiting on some hardware to arrive for this particular computer...) it runs pretty quickly on a PII 400 Mhz 384 MB Ram computer. Faster than Xubuntu, Kubuntu (obviously lol), or Ubuntu

---

### Post by Tweedicus on 2007-01-25
Thanks for the useful and polite reply. I'll try Enlightenment.

---

### Post by ~LoKe on 2007-01-25
This thread is in much need of a sticky.

---

### Post by m.musashi on 2007-01-25
> **Tweedicus said:**
> Er... I don't think I said it did.

I said that the desktops looked nice, which in my opinion they do, but we can't do them on older machines.

Therefore, it would be nice to see some simpler desktops which would run on older machines and which newer users could implement.

The line of reasoning really isn't that hard to follow, and it's really not argumentative either.

As the sticky thread has 600+ posts and as a lot of them are either too difficult to do for newer users, or they wouldn't know how to do them, or they wouldn't run on older machines, it would be nice to see some simpler Desktops which we could run.

It's really not an *issue*

> **Brunellus said:**
> Threads are merged.  The monthly screenshot thread was begun as a means of managing this sort of screenshot thread unraveling.  We used to have multiple parallel screenshot threads.

Nothing in the thread title says "you may only post if you're 1337 and/or have HUGE system specs."  Perfectly humble screenshots are acceptable and indeed encouraged.

I can see his point, though. If you are looking for an attractive and simple desktop idea, wading through 600+ posts to find the few that you can actually emulate could be frustrating.

However, even a desktop using beryl can be mostly duplicated on any machine. You wouldn't have the emerald theme but icons and and window controls still use the standard themes (right?). So, just about any desktop you see here could be recreated on an older machine just not necessarily exactly the same.

---

### Post by Brunellus on 2007-01-25
thread has been re-stickied and re-titiled.  sorry guys.

---

### Post by Mateo on 2007-01-25
i've still been sticking with both panels on the bottom.  it feels like extra work to drag the mouse up AND down, instead of just down.  trying to break the habit and go with a standard gnome look.

---

### Post by Brunellus on 2007-01-25
> **Mateo said:**
> i've still been sticking with both panels on the bottom.  it feels like extra work to drag the mouse up AND down, instead of just down.  trying to break the habit and go with a standard gnome look.
I do the opposite in Windows, moving windows' panel to the top of my screen.

---

### Post by Mateo on 2007-01-25
what i don't get about enlightenment and DEs like that is that you have to right click on the desktop to load an application.  what if you have your browser maximized?  do you have to minimize it just to load gimp or whatever?  seems like a lot of work.  also, programs are buried under menus.  gnome has gotten me spoiled.  I used to hate in XP having to press start, then all programs, then accessories (most of the time).

---

### Post by Mateo on 2007-01-25
> **Brunellus said:**
> I do the opposite in Windows, moving windows' panel to the top of my screen.

yeah, but that's only 1 panel.  my point what not that I like it better on the bottom, but that I don't like have the 2 panels split, because then I have to drag the cursor to the top to do one thing, and then to the bottom to do another.

but it's less attractive having 2 panels together, and more buggy.  stuff like the drawer doesn't work well with 2 panels lined up.

---

### Post by fuscia on 2007-01-25
> **mcduck said:**
> I love the wallpaper.. Can I have it? Please?

here you go. had to convert it to a jpg in order to attach. let me know if it came out stupid looking.

---

### Post by flapane on 2007-01-25
kde3.5.6
beryl0.2
[[IMG]http://img262.imageshack.us/img262/825/screen5ja.th.jpg[/IMG]](http://img262.imageshack.us/img262/825/screen5ja.jpg)

---

### Post by Rui Pais on 2007-01-25
> **Mateo said:**
> what i don't get about enlightenment and DEs like that is that you have to right click on the desktop to load an application.  what if you have your browser maximized?  do you have to minimize it just to load gimp or whatever?  seems like a lot of work.  also, programs are buried under menus.  gnome has gotten me spoiled.  I used to hate in XP having to press start, then all programs, then accessories (most of the time).

Enlightment use "objects" called shelves to act as panels (in gnome). They cannot be set to autohide, but can be set to stay above all windows (transparent or not) or stay above windows but not allowed to be covered when maximized (e then make the larger as possible not covering those).


Here mine:
[ATTACH]23864[/ATTACH][ATTACH]23865[/ATTACH]
and my browser maximized (covering only those modules a don't mid to be covered)
[ATTACH]23868[/ATTACH]

---

### Post by spinflick on 2007-01-25
My latest

---

### Post by raublekick on 2007-01-25
[[IMG]http://entropy.good-evil.net/gnomesaturnthumb.png[/IMG]]("http://entropy.good-evil.net/gnomesaturn.png")

nothing too spectacular

MurrinaGraphite GTK (looking for something darker, but not completely black, tried MurrinaY, loved the roundness, too dark though (maybe i should just edit the theme myself...(maybe i should get back to the post)))
Silicon Metacity (looking for something better, haven't really looked hard though)
Tango icons (need to get some darker ones)

background is from the [Cassini]("http://news.com.com/2300-11397_3-6152878-1.html?part=rss&tag=6152878&subj=news") contest

---

### Post by aristotlewilde on 2007-01-25
> **SmiLey497 said:**
> :d

I must have this wallpaper!

---

### Post by finferflu on 2007-01-25
> **Mateo said:**
> what i don't get about enlightenment and DEs like that is that you have to right click on the desktop to load an application.  what if you have your browser maximized?  do you have to minimize it just to load gimp or whatever?  seems like a lot of work.  also, programs are buried under menus.  gnome has gotten me spoiled.  I used to hate in XP having to press start, then all programs, then accessories (most of the time).

On E17 you actually got an "E" button for the shelf, which has the same menu as the one you get when you right click on the desktop :wink:

---

### Post by BoyOfDestiny on 2007-01-25
I decided to make an old school dark theme... So far so good. :)

[http://ubuntuforums.org/showthread.php?t=346457](http://ubuntuforums.org/showthread.php?t=346457)

Screenshots:

---

### Post by finferflu on 2007-01-25
> **BoyOfDestiny said:**
> I decided to make an old school dark theme... So far so good. :)

[http://ubuntuforums.org/showthread.php?t=346457](http://ubuntuforums.org/showthread.php?t=346457)

Screenshots:

Ancient remote memories from Amiga... more or less... that's pretty much old school.. Even though I've never used such colors in my old Commodore machines... I was too young anyways to even care about changing windows colors :P

---

### Post by BoyOfDestiny on 2007-01-25
> **finferflu said:**
> Ancient remote memories from Amiga... more or less... that's pretty much old school.. Even though I've never used such colors in my old Commodore machines... I was too young anyways to even care about changing windows colors :P

Yeah, looked more like this? (screencap below :) )

Anyway, I used c64's during elementary and middle school. For some reason the command to change the background and border stuck with me... 
poke 53281,colorcode
poke 53280,colorcode

Pretty geeky for me to know... but whatever. Computer Scientist :)

---

### Post by Phatfiddler on 2007-01-25
KDE 3.5
Debian Etch (testing)
Shameless wallpaper:)


    Click Picture for Larger Image
[[IMG]http://cutlersoftware.com/images/screenshot1.png[/IMG]]("http://cutlersoftware.com/images/screenshot.png")

---

### Post by m.musashi on 2007-01-25
Please excuse my bragging. This is my homage to amd. I just upgraded myself to an x2 4800 (from a single core 3700). I know it's nothing special now (which is why I got it so cheap:)). Still, since I have a 939 board it was an easy way to get a nice dual core set up. Notice my conky. I'm running cpu burn and only one core is maxed. I still have an entire core to work with. Even with it running I don't notice any slowdown at all. Yes, I know this is old news too and nothing special (thanks intel) but I'm having fun. It will wear off in a day or two.

---

### Post by fuscia on 2007-01-25
> **m.musashi said:**
> ) but I'm having fun.

meaning, of course, that nothing else matters.

---

### Post by m.musashi on 2007-01-26
> **fuscia said:**
> meaning, of course, that nothing else matters.

Exactamundo, mon ami.

---

### Post by Kateikyoushi on 2007-01-26
> **Brunellus said:**
> I do the opposite in Windows, moving windows' panel to the top of my screen.

I do the same  with every OSin case I have panel, it is less disturbing on top.

---

### Post by kvonb on 2007-01-26
This is my ULTIMATE desktop :)

I've just managed to get the "blue glass" sliders and menu backgrounds working thanks to a chap called "aidanr" on the forums!

Also upgraded to Beryl 0.2.0 Beta 2 last night, I was reluctant after reading all the problems people were having, but it works perfectly.

I really like the virtual desktop size thing, it looks fabulous when set to "2", as in the screenshot provided.

I also got info on how to temporarily disable Beryl when gaming, so that makes things just rosy.  I did touch up snapshot59 because the gamma messes up the desktop when in windowed mode, just incase anyone wants to get picky :rolleyes:.

Now if only I could get the bleedin' bin and kill-app icons to change :confused:.

---

### Post by PatrickMay16 on 2007-01-26
> **BoyOfDestiny said:**
> I decided to make an old school dark theme... So far so good. :)

[http://ubuntuforums.org/showthread.php?t=346457](http://ubuntuforums.org/showthread.php?t=346457)

Screenshots:

Nice. As for me, I also use a dark theme which I made myself. However, it causes a problem; I can't find an icon set that looks good with such a theme. This looks to be a problem with yours too; that "personal data" CD-R icon sticks out like a thorn.

---

### Post by crimesaucer on 2007-01-26
New theme with art from the same artist, Doze Green. The gtk theme is my own.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-19-4.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-4.png[/IMG]

---

### Post by mcduck on 2007-01-26
> **fuscia said:**
> here you go. had to convert it to a jpg in order to attach. let me know if it came out stupid looking.
Thanks. It looks great. Now I only need a GTK and Beryl or xfwm theme to go with it..

---

### Post by slimdog360 on 2007-01-26
> **crimesaucer said:**
> New theme with art from the same artist, Doze Green. The gtk theme is my own.
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-4.png[/IMG]

that wallpaper is way cool

---

### Post by fuscia on 2007-01-26
> **mcduck said:**
> Thanks. It looks great. Now I only need a GTK and Beryl or xfwm theme to go with it..

samui might do it.

---

### Post by brottman on 2007-01-26
Just a clean desktop. I've seen enough cube's for the month.

---

### Post by ComplexNumber on 2007-01-26
i made myself some colour mods for the theme called Bloodline. now there is Bloodline-blue, Bloodline-green, etc. i usually don't find dark themes as easy to work with as  lighter coloured themes, but i selected Bloodline because the background isn't completely black, but a  dark shade of grey.
i think the icons should be dark grey, though, so i may change them to Human_Ultra_Grey.

gtk: Bloodline-red (colour mod of Bloodline)
metacity: office
icons: Human_Ultra_Red2
wallpaper: To_Build.jpg

---

### Post by Mateo on 2007-01-26
not bad, and i usually don't like dark themes.  what is the weather app on your desktop?

---

### Post by bonzodog on 2007-01-26
> **BoyOfDestiny said:**
> I decided to make an old school dark theme... So far so good. :)

[http://ubuntuforums.org/showthread.php?t=346457](http://ubuntuforums.org/showthread.php?t=346457)

Screenshots:

Heh..i have an xfce desktop shot from Xubuntu Dapper, where I modified the xfwm tgc theme (I still have the modded tarball here), and I combined it with a modded darkening gtk theme.

[IMG]http://ubuntuforums.org/gallery/data/2/medium/screenshot-17.png[/IMG]

I then switched to Openbox, and modified the blat theme to make it green, and got the eMacs-green gtk theme, and made the widgets use green text instead of black.

[IMG]http://ubuntuforums.org/gallery/data/518/medium/openbox1.png[/IMG]

Both of these shots are in the gallery, under my photo albums.

---

### Post by darkhatter on 2007-01-26
the force is strong with this one....

[[IMG]http://img329.imageshack.us/img329/638/forcebewithyouky6.th.jpg[/IMG]](http://img329.imageshack.us/my.php?image=forcebewithyouky6.jpg)

---

### Post by ComplexNumber on 2007-01-26
> **Mateo said:**
> not bad, and i usually don't like dark themes.  what is the weather app on your desktop?
thats gdeklets. the actual weather app is called GoodWeather

---

### Post by ~LoKe on 2007-01-26
**January 26, 2007**
[[IMG]http://img168.imageshack.us/img168/4655/jan262007vc2.th.png[/IMG]](http://img168.imageshack.us/img168/4655/jan262007vc2.png)

---

### Post by flapane on 2007-01-26
> **flapane said:**
> kde3.5.6
beryl0.2
[[IMG]http://img262.imageshack.us/img262/825/screen5ja.th.jpg[/IMG]](http://img262.imageshack.us/img262/825/screen5ja.jpg)

sorry fixed up the thumbnail

---

### Post by fuscia on 2007-01-26
> **ComplexNumber said:**
> i made myself some colour mods for the theme called Bloodline. now there is Bloodline-blue, Bloodline-green, etc. i usually don't find dark themes as easy to work with as  lighter coloured themes, but i selected Bloodline because the background isn't completely black, but a  dark shade of grey.
i think the icons should be dark grey, though, so i may change them to Human_Ultra_Grey.

gtk: Bloodline-red (colour mod of Bloodline)
metacity: office
icons: Human_Ultra_Red2
wallpaper: To_Build.jpg

except for the goofy weather thing, that's most sharp looking desktop.

---

### Post by chavo on 2007-01-26
KDE 3.5.5 and beryl svn.
[[IMG]http://img256.imageshack.us/img256/7160/12607lv9.th.jpg[/IMG]](http://img256.imageshack.us/my.php?image=12607lv9.jpg)

---

### Post by CGW on 2007-01-26
Simple.  NuoveXT-1.6 Icons.  Random wallpaper downloaded from the Kubuntu control panel.

---

### Post by ComplexNumber on 2007-01-26
> **fuscia said:**
> except for the goofy weather thing, that's most sharp looking desktop.
sharp looking?

---

### Post by fuscia on 2007-01-26
> **ComplexNumber said:**
> sharp looking?

uh...looks really good.

---

### Post by BLTicklemonster on 2007-01-26
> **Tweedicus said:**
> Hi,

The pictures on the sticky January 2007 Desktop Thread were truly great.

However, some of us grad students are poor so run five year old machines (Thinkpad T23 in my case) with 8 mb graphics cards. 

And we run these machines because they're ultra reliable and run Edgy tres fast.

BUT they will not run Compiz or Beryl. And some of us don't have the technical ability to do complext desktops.

All we want is something which is simple but looks real nice. Perhaps a special icon, window, and wallpaper theme, and maybe some minor special effects.

Perhaps some of you with older machines could post Desktop pictures with details so we could get inspired to change our own tired Desktops.

Here's mine: some Mac rip-off wall-paper and window borders, with crystal icon theme, and transparent panels.

Cheers,

Tweed

How in the world anyone can find reason to argue with you is beyond comprehension. I agree, it would be nice if some folks with some older machines came in and showed just how great they can make their systems look.

I run a machine that will handle beryl just fine, but prefer to run fluxbox on it =).

---

### Post by terrien on 2007-01-26
Default theme and whatnot, I'm in the mood for something simple.

Wallpaper's from deviantArt, I needed something bright and sunny to try to ignore all the damn snow we've been having here in Colorado. ;)

---

### Post by ComplexNumber on 2007-01-26
> **fuscia said:**
> uh...looks really good.
ahhh right. cheers, fella! ;). i've done some further mods on all the Bloodline range so that the background to the themes are slightly lighter, and all previous text that was once white is now a very light grey. the latter change was necessary because  the white text was not showing up on white backgrounds in applications such as firefox (see second screenshot after the change to very light grey. the previous text highlighted in red was white, so it was barely visible. this is always a problem with dark themes :()

---

### Post by zeeR on 2007-01-26
[All info on deviantART!]("http://www.deviantart.com/deviation/47448417/")

[[IMG]http://img256.imageshack.us/img256/1788/screenshotcq3.th.png[/IMG]]("http://www.deviantart.com/deviation/47448417/")

---

### Post by John.Michael.Kane on 2007-01-26
zeeR where did you find those icons?

---

### Post by ~LoKe on 2007-01-26
Yeah, those icons kick ***.

---

### Post by BOBSONATOR on 2007-01-26
same here!^^^

---

### Post by cmmike1 on 2007-01-26
It's been a little while since I last posted a screen. Anyway I got Twinview to work again with beryl so I decided to post. My only complaint is that I can't get the window list to span across 2 panels or I can't make the panel span across the 2 screens. Anyway for any rap fans my background is of J Dilla. enjoy.

[[IMG]http://img409.imageshack.us/img409/8641/screenshotdillaxd0.th.png[/IMG]](http://img409.imageshack.us/my.php?image=screenshotdillaxd0.png)
[[IMG]http://img409.imageshack.us/img409/937/screenshotdilla2nn5.th.png[/IMG]](http://img409.imageshack.us/my.php?image=screenshotdilla2nn5.png)

---

### Post by highneko on 2007-01-26
> **~LoKe said:**
> **January 26, 2007**
[[IMG]http://img168.imageshack.us/img168/4655/jan262007vc2.th.png[/IMG]](http://img168.imageshack.us/img168/4655/jan262007vc2.png)

Is that conky? How do you display the core usage stuff? Where can I get that wallpaper? That's a great theme too. Where can we get all that?!

---

### Post by m.musashi on 2007-01-26
> **terrien said:**
> Default theme and whatnot, I'm in the mood for something simple.

Wallpaper's from deviantArt, I needed something bright and sunny to try to ignore all the damn snow we've been having here in Colorado. ;)

You know, snow in Colorado isn't supposed to be a novel idea. Back in the olden days we used to have lots of it - whole mountains covered with it.

Sorry. couldn't resist. You're right though. I've got about 100lbs of ice in my gutter that I'd really like to see melt.

---

### Post by ~LoKe on 2007-01-27
> **highneko said:**
> Is that conky? How do you display the core usage stuff? Where can I get that wallpaper? That's a great theme too. Where can we get all that?!

**Wallpaper: [Massive Momentum](http://www.dualscreenwallpaper.com/wallpapers/abstract/Massive_Momentum.jpg)**
**Theme: [Murrina BluRay](http://gnome-look.org/content/show.php?content=51073) ** (will need **[murrine engine](http://www.gnome-look.org/content/show.php?content=42755)**)
**Conky:**
> ${color #e9c703}Core 1 Usage:$color ${alignc} ${cpu cpu1}% ${color #888888}${cpubar cpu1}
${color #888888}${cpugraph cpu1 888888 e9c703}
${color #e9c703}Core 2 Usage:$color ${alignc} ${cpu cpu2}% ${color #888888}${cpubar cpu2}
${color #888888}${cpugraph cpu2 888888 e9c703}

---

### Post by doggie on 2007-01-27
It was my First try!

---

### Post by fuscia on 2007-01-27
it's funny how beckmann's self portraits always looked better than he did.

---

### Post by tcrroadie on 2007-01-27
Enlightenment E17 showing XMMS, transparency in Eterm and E17 main menu. 

Wallpaper can be found here. 

[http://www.deviantart.com/deviation/3791283/](http://www.deviantart.com/deviation/3791283/)

---

### Post by hoagie on 2007-01-27
> **tcrroadie said:**
> Enlightenment E17 showing XMMS, transparency in Eterm and E17 main menu. 

Wallpaper can be found here. 

[http://www.deviantart.com/deviation/3791283/](http://www.deviantart.com/deviation/3791283/)

What theme are using for xmms?

---

### Post by tcrroadie on 2007-01-27
> **hoagie said:**
> What theme are using for xmms?

The XMMS skin I am using can be found here.

[http://www.gnome-look.org/content/show.php?content=41102](http://www.gnome-look.org/content/show.php?content=41102)

---

### Post by finferflu on 2007-01-27
> **tcrroadie said:**
> The XMMS skin I am using can be found here.

[http://www.gnome-look.org/content/show.php?content=41102](http://www.gnome-look.org/content/show.php?content=41102)

Nice one! It works on Audacious as well :KS 

Did you use Esetroot for transparency? I guess there is no much choice... The only thing that annoys me is that I have to execute it every time I log back in... I need to find something that does it automatically...

---

### Post by bvc on 2007-01-27
[my current]("http://gnomethemes.org/pre/screenshots/Royale.png")

---

### Post by tcrroadie on 2007-01-27
> **finferflu said:**
> Nice one! It works on Audacious as well :KS 

Did you use Esetroot for transparency? I guess there is no much choice... The only thing that annoys me is that I have to execute it every time I log back in... I need to find something that does it automatically...

Ya, I did use Esetroot to set my background image for Eterm.  It does seem to work well even though it is cheating a little.  I know Esetroot can be added to xsessions or xinitrc so it can start in the background when Enlightenment is started, I'm just not sure where to look.  I poked around /etc/X11 some this morning but gave it a rest because my brain just is not working today.  A little sleep deprived.  I stayed up to late last night.  

I know if I had a separate xinitrc file (/home/user/.xinitrc) to launch Enlightenment from command line log-in with startx, it would be easy to do, but I am using GDM at the moment.  Ubuntu has xsession files everywhere.

Talk later, and thanks for helping out on my E17 thread. :D

---

### Post by Gadren on 2007-01-27
> **ice60 said:**
> here's mine -

[[img]http://xs411.xs.to/xs411/07044/Screenshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs411&d=07044&f=Screenshot.png)

Beautiful!  Do you have a link to the wallpaper itself? :)

---

### Post by ComplexNumber on 2007-01-27
> **Gadren said:**
> Beautiful!  Do you have a link to the wallpaper itself? :)
her yer go

---

### Post by spinflick on 2007-01-28
My last for the month ;)

---

### Post by Gadren on 2007-01-28
> **ComplexNumber said:**
> her yer go

Thanks! :)

---

### Post by %hMa@?b&lt;C on 2007-01-28
my real "themed" desktop... if you cant tell it is red:(
[[IMG]http://img294.imageshack.us/img294/7672/desktopshot1eh6.th.png[/IMG]](http://img294.imageshack.us/my.php?image=desktopshot1eh6.png)

---

### Post by Rab22 on 2007-01-28
My current desktop....

[http://www.rab22.ws/images/desktops/linux/LT_1.png](http://www.rab22.ws/images/desktops/linux/LT_1.png)

[http://www.rab22.ws/images/desktops/linux/LT_2.png](http://www.rab22.ws/images/desktops/linux/LT_2.png)

---

### Post by ahaslam on 2007-01-28
> **ComplexNumber said:**
> her yer go

Spot the difference :-k

---

### Post by boomklever on 2007-01-28
Running Gnome 2.16 on Edgy. Icon Theme is Noia. The Background picture I made myself. You can download it from there:
[[IMG]http://img253.imageshack.us/img253/3865/sartrewolfwc2.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=sartrewolfwc2.jpg)

---

### Post by ComplexNumber on 2007-01-28
> **Anthony Haslam said:**
> Spot the difference :-k
what?

---

### Post by ahaslam on 2007-01-28
> **ComplexNumber said:**
> what?
Yours is cropped ;)

---

### Post by ComplexNumber on 2007-01-28
> **Anthony Haslam said:**
> Yours is cropped ;)
oh, i see! yes, i thought that kink in the land at the bottom of the wallpaper looked a bit 'unnatural'. so because the wallpaper was originally 1600x1200 and the resolution that i use is 1024x768, i decided to crop that kink at the bottom of the wallpaper, together with the appropriate amount off the sides so that it keeps the 1:1.3333 ratio.

---

### Post by fuscia on 2007-01-28
no icons, no panels...

---

### Post by yabbadabbadont on 2007-01-28
> **BoyOfDestiny said:**
> I decided to make an old school dark theme... So far so good. :)

[http://ubuntuforums.org/showthread.php?t=346457](http://ubuntuforums.org/showthread.php?t=346457)

Screenshots:

Reminds me of working on the old IBM 3270 terminals.  Those things had keyboards that sounded like old manual typewriters.  (at least the earlier ones did, the later ones had a switch to turn off the clickity-clacks)

---

### Post by darkhatter on 2007-01-28
> **fuscia said:**
> no icons, no panels...

:confused:......I knew all that desktop changing was going to have negative effects in the long run....

---

### Post by fuscia on 2007-01-28
> **darkhatter said:**
> :confused:......I knew all that desktop changing was going to have negative effects in the long run....

negative??? you'd take desktop icons over gong li?!? oy...:confused:

---

### Post by MkfIbK7a on 2007-01-29
> **yabbadabbadont said:**
> Reminds me of working on the old IBM 3270 terminals.  Those things had keyboards that sounded like old manual typewriters.  (at least the earlier ones did, the later ones had a switch to turn off the clickity-clacks)

my dell keyboard still sounds like that...

---

### Post by Brunellus on 2007-01-29
> **wert613 said:**
> my dell keyboard still sounds like that...
the clickety-clacks came from their microswitches, which were operated by real steel springs.  They had probably the best tactile response of any keyboard ever--more like piano keys and less like mush (most modern, "quiet," rubber-dome keyboards).  

The click came as the spring buckled twice--once on the keypress itself, and again on the rebound.  If you type fast enough on these old Model M clickys, you sound like a machinegun.

There was no way to turn off that racket, though, short of removing the springs themselves.

---

### Post by flapane on 2007-01-29
[[IMG]http://img261.imageshack.us/img261/7823/sk34uo6.th.jpg[/IMG]](http://img261.imageshack.us/img261/7823/sk34uo6.jpg)
[[IMG]http://img258.imageshack.us/img258/4692/screennj8.th.jpg[/IMG]](http://img258.imageshack.us/img258/4692/screennj8.jpg)

---

### Post by kanpachi on 2007-01-29
> **Rab22 said:**
> My current desktop....

[http://www.rab22.ws/images/desktops/linux/LT_1.png](http://www.rab22.ws/images/desktops/linux/LT_1.png)

[http://www.rab22.ws/images/desktops/linux/LT_2.png](http://www.rab22.ws/images/desktops/linux/LT_2.png)

can you please PLEASE share the wallpaper icons theme and that nautilus bg color?

---

### Post by fuscia on 2007-01-29
two e17 shots. second one has *exhibit*, an awesome image viewer.

---

### Post by BOBSONATOR on 2007-01-29
[IMG]http://i37.photobucket.com/albums/e76/GOATSLAY3R/newscreen.png[/IMG]

---

### Post by Mateo on 2007-01-29
please tell us where you got your desktop icons... they are great.

---

### Post by Mateo on 2007-01-29
actually your entire desktop is one of the prettiest I've seen... very nice.

---

### Post by darkhatter on 2007-01-29
those icons look a lot like the oxygen ones, are they based on them?

---

### Post by BOBSONATOR on 2007-01-29
> **Mateo said:**
> actually your entire desktop is one of the prettiest I've seen... very nice.

Thank you.

The icons where sent to me by a nice member named zeeR (pm him)

the theme is murrina kent, the wallpaper can be found @ deviantart, in the minimal section, sorry i cant find the link right now.

and my normal icons are [NuvoXT]("http://gnome-look.org/content/show.php?content=26448")

Thanks again!

---

### Post by crimesaucer on 2007-01-29
@_simon_ from 17 pages back:

I know it's been a while since you asked me to export my Emerald theme, well, I finally did, it's on the Beryl pages themes in "All" and "Light". I call my new variation of it "moonglow". It's a double post because I couldn't erase the one with the wrong picture.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/moonglow.png[/IMG]

[http://themes.beryl-project.org/themes.php?cat=8](http://themes.beryl-project.org/themes.php?cat=8) 

If you want those colors I had in those old pictures I can give you the hex codes, and you can mess with it to perfect it.

---

### Post by justaguynpc on 2007-01-29
**_Very Sharp_**

 and I 'm not usually a "red-kinda-guy".

(In response to Post 692)

---

### Post by BLTicklemonster on 2007-01-30
Redmond toxic theme....

[[IMG]http://img179.imageshack.us/img179/3004/viralscourgelu5.th.png[/IMG]](http://img179.imageshack.us/my.php?image=viralscourgelu5.png)

Here's a real pretty desktop from windows for you all to look at. I'm waiting for it to finish healing so I can tell if it's still going to work (prolly not) so I tell my bud from work whether to just charge him a quarter a virus, or if I need to tack on a reinstall of windows. :D 

So who wants a beer? I'm buying!!! lol :guitar: 


sheesh, what a mess.

---

### Post by featherking on 2007-01-30
For anyone interested in changing many different colors in gnome without editing a .gtkrc-2.0 file, there is a thread [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=293342") (with a deb, doesnt work with dapper) that has a program called gnome-color-chooser, and its great for easily changing tons of colors.

The deb is on the first page along with a link to the src.. Just thought some might enjoy it..

---

### Post by crimesaucer on 2007-01-30
***Edit-updated and finished.

This is my newest gtkrc and Emerald, I'm calling it "rusted", and it should be on the Beryl Themes in a few days.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-37-1.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-38-1.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/rusted.png[/IMG]

-(Also, I just realized I almost ended up with close to the same colors of the Human theme, just with a bit more brown, orange and red. It was totally an accident since I have never used the Human theme in xubuntu xfce. But what's funny is that I must have tried 100 different shade of white/orange/red/silver for my bg [normal] #color, and I finally ended up with #efebe7 because it was the most mellowest browser color I had found, plus it was my Birthdays abbreviation Feb.07,1973. After comparing the two I think it's close to the Ubuntu Human theme's colors, but instead of the grayish tones, there is more of a light brown/red and dark orange to it.)

---

### Post by _simon_ on 2007-01-30
[[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_Tue30Jan.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/Tue30Jan.jpg) [[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_Tue32Jan3.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/Tue32Jan3.jpg) [[IMG]http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/th_Tue31Jan2.jpg[/IMG]](http://i31.photobucket.com/albums/c358/Beowulf1976/SIMON/Screenshots/Tue31Jan2.jpg)

---

### Post by ma1kel on 2007-01-30
> **crimesaucer said:**
> This is my newest gtkrc and Emerald, I'm calling it "rusted", and it should be on the Beryl Themes in a few days.


You win, sir.

---

### Post by fuscia on 2007-01-30
sarah vaughan. check out her version of *over the rainbow*. [http://www.youtube.com/watch?v=yNehKft3xEU&mode=related&search=](http://www.youtube.com/watch?v=yNehKft3xEU&mode=related&search=)

---

### Post by rsambuca on 2007-01-30
Thought I should get mine in before it is February.

---

### Post by m.musashi on 2007-01-30
> **BLTicklemonster said:**
> Redmond toxic theme....

[[IMG]http://img179.imageshack.us/img179/3004/viralscourgelu5.th.png[/IMG]](http://img179.imageshack.us/my.php?image=viralscourgelu5.png)

Here's a real pretty desktop from windows for you all to look at. I'm waiting for it to finish healing so I can tell if it's still going to work (prolly not) so I tell my bud from work whether to just charge him a quarter a virus, or if I need to tack on a reinstall of windows. :D 

So who wants a beer? I'm buying!!! lol :guitar: 


sheesh, what a mess.

Is that a joke? How can someone have 25000 infected files. That's one install that should be scrapped rather than fixed.

Anyway, here is mine for the end of the month. I suppose it's almost Feb somewhere in the world but oh well.

I have no idea what that wall is supposed to be. I'm just in a dark green mood lately and found this. Emerald theme is wii black and icons are called graphite-dark (although there really aren't any to see in the screenshot).

---

### Post by BLTicklemonster on 2007-01-30
It's for real, I'm afraid. I'm still nurturing it. Prolly have to dump it and start over, but I'm determined to give it a try.

---

### Post by crimesaucer on 2007-01-31
I just re-did my whole desktop theme. I made a new gtkrc, Emerald theme, Skydome, Desktop Wallpaper, and Cube Cap. All the art is Doze Green, and everything else is my custom Emerald and xfce gtkrc. I used the Gimp for everything.

these are more screenshots at Beryl: [http://forum.beryl-project.org/viewtopic.php?f=51&t=2893](http://forum.beryl-project.org/viewtopic.php?f=51&t=2893)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-40-3.png[/IMG]

---

### Post by Kateikyoushi on 2007-01-31
> **BLTicklemonster said:**
> It's for real, I'm afraid. I'm still nurturing it. Prolly have to dump it and start over, but I'm determined to give it a try.

Was he collecting them ? :D

---

### Post by BLTicklemonster on 2007-01-31
lmao looked like it!

Get this, I went to uninstall norton, now it won't boot. It's missing msconfig of all things. I can get past that, though. 

I forgot how challenging windows could be! (but I bet I get it networked in a jiffy)

---

### Post by fuscia on 2007-01-31
jwm and she hulk...

---

### Post by finferflu on 2007-01-31
> **fuscia said:**
> jwm and she hulk...

Gosh! you've got the weirdest wallpapers I've ever seen, and you keep posting them! That's amazing :D

---

### Post by fuscia on 2007-01-31
> **finferflu said:**
> Gosh! you've got the weirdest wallpapers I've ever seen, and you keep posting them! That's amazing :D

you'd think i'd learn after a while.

---

### Post by finferflu on 2007-01-31
> **fuscia said:**
> you'd think i'd learn after a while.

No, is that you've got a very very very wide collection of them :D

---

### Post by fuscia on 2007-01-31
> **finferflu said:**
> No, is that you've got a very very very wide collection of them :D

the oyster is infinite.:guitar:

---

### Post by m.musashi on 2007-01-31
> **crimesaucer said:**
> I just re-did my whole desktop theme. I made a new gtkrc, Emerald theme, Skydome, Desktop Wallpaper, and Cube Cap. All the art is Doze Green, and everything else is my custom Emerald and xfce gtkrc. I used the Gimp for everything.

these are more screenshots at Beryl: [http://forum.beryl-project.org/viewtopic.php?f=51&t=2893](http://forum.beryl-project.org/viewtopic.php?f=51&t=2893)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-40-3.png[/IMG]

Very nice looking. Any plans to post the .emerald and such on gnome-look or similar? I think this could entice me away from my current green mood.

---

### Post by linuxuser28 on 2007-01-31
My desktop when I'm using Xubuntu.

---

### Post by ~LoKe on 2007-01-31
**January 31, 2007**
[[IMG]http://img518.imageshack.us/img518/369/screenshotbb6.th.png[/IMG]](http://img518.imageshack.us/img518/369/screenshotbb6.png)

---

### Post by crimesaucer on 2007-01-31
@ m.musashi- Thank You, and yes, I plan to post the Emerald theme on Beryl Themes, all though, it is basically the exact same as the theme I posted on there called "moonglow", I just changed most of the colors, and the title glow a bit (and the content outline). If you download "moonglow" and use the color picker, you can match your desktop with the exact colors of whatever mood your in.

---

### Post by Catsworth on 2007-01-31
Never posted a desktop before, but I'm starting to get Ubuntu looking the way I want it to so here goes :)

Constructive critiques gratefully received.

---

### Post by rsambuca on 2007-01-31
Here fuscia, so you can match your desktop

---


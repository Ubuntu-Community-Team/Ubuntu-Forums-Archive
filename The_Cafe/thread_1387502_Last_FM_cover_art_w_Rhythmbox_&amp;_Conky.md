---
title: "Last FM cover art w/ Rhythmbox &amp; Conky"
date: 2010-01-21
forum: The Cafe
---

### Post by hhh on 2010-01-21
Almost all of my music listening at home now is through Last FM via Rhythmbox, and I'd love to have Conky display the cover art on my desktop. What I have so far is this script...
```
#!/bin/bash
artist=`rhythmbox-client --print-playing-format %aa`
album=`rhythmbox-client --print-playing-format %at`
str="`echo "$artist $album" | sed -e s/\\ /+/g`"
wget `wget "http://www.albumart.org/index.php?srchkey=$str&itempage=1&newsearch=1&searchindex=Music" -q -O - |
grep "http://www.albumart.org/images/zoom-icon.jpg" -m 1 |
sed -e 's/" border="0" class="image_border.*//' |
sed -e 's/.*img src="//'` -q -O /home/hhh/.album
```
...with this .conkyrc...
```
# maintain spacing between certain elements
use_spacer yes

# set to yes if you want conky to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-9
xftfont DejaVu Sans-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 4.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type desktop

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 250 5
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
gap_y 42

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${font DejaVu Sans:size=10}${color #a8d82c}${if_running rhythmbox}${exec rhythmbox-client --no-start --print-playing-format %tt}${color #da6e14} by ${color #a8d82c}${exec rhythmbox-client --no-start --print-playing-format %aa}
${execi 4 albumart}${image /home/hhh/.album -p 0,25 -s 190x190 -n}
${voffset 190}${font DejaVu Sans:size=8}${color #da6e14}from ${color #a8d82c}${exec rhythmbox-client --no-start --print-playing-format %at}
${color #da6e14}${exec rhythmbox-client --no-start --print-playing-format %te} / ${exec rhythmbox-client --no-start --print-playing-format %td}$endif
```

conkyRhythmbox has to be installed for this to work. The script is named "albumart" and is placed in /bin, I created a blank file in /home/hhh named .album to hold the image, which gives me this...

[[IMG]http://img638.imageshack.us/img638/6461/screenshot1v.th.png[/IMG]](http://img638.imageshack.us/img638/6461/screenshot1v.png)

Not bad, right? But there are problems...

1) I'm pulling images from albumart.org, I want to pull the images from Last FM.
2) I'm fairly consistently getting "wget missing url" errors displayed in Conky, they go away after the next Conky update (4 seconds, in my case).
3) If there is no cover art available, the last cover art stays there.

I'm not a programmer, so everything I've managed so far has been from this forum and the CrunchBang! forums (I'm running Openbox standalone/tint2 in Karmic).

Is anyone else interested in this? Can you help?

Thanks.

---

### Post by hhh on 2010-01-23
Bump, and linking to other resources...
[http://ubuntuforums.org/showthread.php?t=928168](http://ubuntuforums.org/showthread.php?t=928168)
[http://crunchbanglinux.org/forums/topic/3728/images-in-conky-specifically-rhythmbox-album-art/](http://crunchbanglinux.org/forums/topic/3728/images-in-conky-specifically-rhythmbox-album-art/)

---

### Post by hhh on 2010-01-26
bump

---

### Post by Garnett on 2010-02-19
hhh - did you ever have any joy with this? I love the idea - very cool.

---

### Post by hhh on 2010-02-19
No. I'm not a programmer, so this was above my head and I couldn't find any interest in it. I don't mind that the album art doesn't always match what Last FM uses, but the error messaqes are unacceptable to me.

---

### Post by Mahngiel on 2010-02-19
i've copied your script and will let you know what i can pull out of it for you.

---

### Post by hhh on 2010-02-19
Thanks!

---

### Post by Mahngiel on 2010-02-24
The only thing I've found wrong with your script is it's very primal.  You are mandating the url it searches for and in theory, it works perfectly, given a few circumstances:

You know or have spelled correctly the artist's name &
You know or have spelled correctly the album name

I was watching running this out of the terminal and flipping through songs, when I started getting URL issues with the wget command on songs where the album was unknown or I played a song pulled off a mix cd without proper names.  

So my theory is that when you see issues of album art not showing up, check your artist and album info.

---


---
title: "Date on Dekstop"
date: 2008-12-23
forum: The Cafe
---

### Post by Valok on 2008-12-23
I saw a desktop screenshot the other day that had a very nice and simple date right on the dekstop.  It just said the date, and the time.

I'd really like to get this on my desktop, but I have no idea how to, if anyone knows how to do this I'd love to hear about it!

---

### Post by smartboyathome on 2008-12-23
What window manager or desktop environment do you use?

---

### Post by Valok on 2008-12-23
Sorry, I use Gnome

---

### Post by billgoldberg on 2008-12-23
That's most likely Conky.

I have a guide on my blog (see signature).

---

### Post by Valok on 2008-12-23
Awesome, so second question, anyone have a conky file that will just show the date on the bottom left corner of the desktop?

---

### Post by billgoldberg on 2008-12-23
> **Valok said:**
> Awesome, so second question, anyone have a conky file that will just show the date on the bottom left corner of the desktop?

I'll just whipped one up for you.

> background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color gray
default_shade_color red
default_outline_color green
alignment bottom_right
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes
text_buffer_size 256

TEXT

${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
$endif

---

### Post by Valok on 2008-12-23
Thanks a ton!

---

### Post by Valok on 2008-12-23
On your guide, I'm having trouble making the conkyrc file.  Whenever I paste that code it just tells me that no such file or directory exists, any pointers?

---

### Post by Valok on 2008-12-23
One last question, how do I change the font to URW Gothic L Book?

---

### Post by glotz on 2008-12-23
[QUOTE=billgoldberg]I'll just whipped one up for you.

.
.
.
> **$endif**[/QUOTE]Isn't that bit unneeded?

[quote=valok]Whenever I paste that code it just tells me that no such file or directory exists, any pointers? ; One last question, how do I change the font to URW Gothic L Book? [/quote]How are you exactly pasting and where? ; Just put the font name after the xftfont instead of 123

---

### Post by kevin11951 on 2008-12-23
i have been following along, an have hit a minor snag, whenever i hit the "show desktop" button on the taskbar, it gets rid of conky, can i make conky ignore that button?

---

### Post by Valok on 2008-12-23
I got all that figured out now, its up and running, thanks!  I just need to figure out how to change the font.

---

### Post by glotz on 2008-12-23
Kevin, you might want to try experimenting with own_window no. That's how I have mine set up.

Besides conky, there's e.g. [screenlets](http://www.screenlets.org/index.php/Screenshots), [gdesklets](http://www.gdesklets.de/?q=desklet/browse/alphabetical), [google gadgets](http://code.google.com/p/google-gadgets-for-linux/) and probably quite a few more options.

---


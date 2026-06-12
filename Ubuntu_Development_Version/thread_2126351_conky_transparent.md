---
title: "conky transparent"
date: 2013-03-16
forum: Ubuntu Development Version
---

### Post by Kajover on 2013-03-16
hi. I am struggling to get conky transparent. It works sometimes but sometimes it does not :P any ideas?

```

background yes
use_xft yes
xftfont Liberation Sans:size=9
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_argb_visual no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 240
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color 656667
default_shade_color 000000
default_outline_color 828282
alignment top_right
gap_x 12
gap_y 42
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
Uptime:$alignr$uptime
RAM:$alignr$mem/$memmax
Swap usage:$alignr$swap/$swapmax
Disk usage:$alignr${fs_used /}/${fs_size /}
CPU usage:$alignr${cpu cpu0}%
#Signal Strength:$alignr${wireless_link_qual_perc wlan0}%
Download:$alignr${downspeed wlan0}
Upload:$alignr${upspeed wlan0}
```

---

### Post by VinDSL on 2013-03-16
'own_window_type' is the biggie!  Use 'normal', not 'override'.

Here's what I use, in that section...

```
####
## Create 'own_window' type. Makes Conky behave like other panels.
#
own_window yes
own_window_transparent yes
**[COLOR="#0000CD"]own_window_type normal[/COLOR]**
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros require the following lines for true transparency.
## BOTH of these lines need to be Commented/Uncommented in tandem.
#
**[COLOR="#0000CD"]own_window_argb_visual yes[/COLOR]**
**[COLOR="#0000CD"]own_window_argb_value 255[/COLOR]**
```


[INDENT]**[COLOR="#A52A2A"]GNOME 3 Staging || Liquorix 3.7.0-10 Kernel || nVidia 304.84 || Plank || ACYL || ConkyWX 0.7.9[/COLOR]**[/INDENT]

[[IMG]http://vindsl.com/images/vindsl-desktop-16-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-mar-2013-1.png")


Works in GS & Unity...  ;)

---

### Post by Kajover on 2013-03-16
sir, thank you very much! this fixed my problem

```
own_window_type normal
own_window_argb_visual yes
own_window_argb_value 255
```

---

### Post by VinDSL on 2013-03-16
> **Kajover said:**
> sir, thank you very much! this fixed my problem [...]
Welcome!

Be careful using Conky.  It's very addictive!  :D

---

### Post by Kajover on 2013-03-16
oh well, almost perfect.

Whenever I open a window/app e.g. Nautilus and then close it, the bar has no shadow. I have to click on the desktop in order for the shadow to appear.

---

### Post by stinkeye on 2013-03-16
Enable the window rules plugin in ccsm and add
```
class=Conky
```
in the **no focus** box at the bottom.

Restart conky.

---

### Post by Kajover on 2013-03-16
Thank you guys a lot! worked after a system reboot :)

---

### Post by VinDSL on 2013-03-16
Heh!  I was just going to suggest that, but...

I was afraid it would sound too rudimentary.  :)

That said, I always do a...

```
killall conky
```

...after making major changes.

And, I do a system restart, after adding fonts, or changing their location(s).

Simply saving your .conkyrc file, lua scripts, et cetera after editing them, usually works for minor changes, but to play it safe, it's best to do a more radical reset. ;)

---


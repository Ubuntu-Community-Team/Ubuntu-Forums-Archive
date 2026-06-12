---
title: "Xubuntu Precise + conky: how this is possible?"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dentaku65 on 2012-04-22
Hi,
I've configured conky in the session start up application via bash script called /usr/bin/start-conky
```
#!/bin/bash
sleep 20  && conky
exit
```
But when I log to the system I have conky runs at least twice or more:
```
ps -A |grep conky
 1503 ?        00:00:00 start-conky
 1521 ?        00:00:08 conky
 1524 ?        00:00:08 conky
 2078 ?        00:00:08 conky

```
How this is possible?

TIA

---

### Post by hakermania on 2012-04-22
Hello [dentaku65]("http://ubuntuforums.org/member.php?u=48938") !

Can you please check, if you remove from the startup applications the /usr/bin/start-conky script, will the conky application be launched (in order to see if other process starts conky aside from your script)?
Also, your script could simply be:
```

#!/bin/bash
sleep 20
conky&
exit

```

---

### Post by dentaku65 on 2012-04-22
> **hakermania said:**
> Hello [dentaku65]("http://ubuntuforums.org/member.php?u=48938") !

Can you please check, if you remove from the startup applications the /usr/bin/start-conky script, will the conky application be launched (in order to see if other process starts conky aside from your script)?
Also, your script could simply be:
```

#!/bin/bash
sleep 20
conky&
exit

```

Hi hackermania,
changing the script in your way I've got the same issue (multiple conky process).
I've already try to uncheck the script from the session menu, but conky have a really herratic behaviour: it starts anyway, in this scenario if I do:
```
killall -9 conky
```
on the next reboot conky will not start.

I'm using [conkycolors]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328"), but the configuration file resides under ~/.conkyrc 

If I run start-conky script manually (not in the session autostart) it works correctly.

:confused:

---

### Post by hakermania on 2012-04-22
It's ha**k**ermania; anyway, as I understood, the conky starts itself anyway. So, why don't you see what causes conky to autostart? Has this to do with the configuration file?

---

### Post by dentaku65 on 2012-04-22
> **hakermania said:**
> It's ha**k**ermania; anyway, as I understood, the conky starts itself anyway. So, why don't you see what causes conky to autostart? Has this to do with the configuration file?

sorry ha**k**ermania :-)

I did 
```
sudo updatedb
```
Then
```
locate conky |grep desktop
```
The only autostart script is the one that I've created

I've the suspect that conky starts inside nested in some saved sessions... this is because my box is a version upgrade from Lucid to Precise.

---

### Post by hakermania on 2012-04-22
```
locate conky |grep desktop
```
will locate all .desktop files that may cause this, but as you understand, conky can be launched in many other ways.

I don't really  know from where else an application can be launched (maybe a cron job? I really don't know).

If you disbale your script, does conky launch itself twice?

---

### Post by dentaku65 on 2012-04-22
> **hakermania said:**
> ```
locate conky |grep desktop
```
will locate all .desktop files that may cause this, but as you understand, conky can be launched in many other ways.

I don't really  know from where else an application can be launched (maybe a cron job? I really don't know).

If you disbale your script, does conky launch itself twice?


mmm. I think on Xfce the app autostart can be lauched only via .desktop snippet, of course I don't have conky configured in any cron job, or in /etc/rc.local or whatever.

And yes, with the script disabled it starts anyway (!?!?) in multiple process, but in the session if I do:
```
killall -9 conky
```
on the next reboot conky do not start

---

### Post by pbrane on 2012-04-22
Have you checked your ***~/.config/autostart*** directory? Also you could run **conky -d** to run it in the background instead of **conky &**.

---

### Post by dentaku65 on 2012-04-22
> **pbrane said:**
> Have you checked your ***~/.config/autostart*** directory? Also you could run **conky -d** to run it in the background instead of **conky &**.

Yes, conky.desktop is in ***~/.config/autostart***
I'll try -d option

---

### Post by dentaku65 on 2012-04-25
Hi,

even with conky -d in the autostart script the issue is still there!
Multiple conky processes :confused:

The only workaroud that I found is to 
```
killall -9 conky
```
before to reboot

:mad:

---

### Post by Quackers on 2012-04-25
Do you have multiple .conkyrc files?
If not please post your .conkyrc file in code tags.

---

### Post by dentaku65 on 2012-04-25
> **Quackers said:**
> Do you have multiple .conkyrc files?
If not please post your .conkyrc file in code tags.

No.
As I said on #1, multiple processes of conky
```
ps -A |grep conky
 1503 ?        00:00:00 start-conky
 1521 ?        00:00:08 conky
 1524 ?        00:00:08 conky
 2078 ?        00:00:08 conky
```

Now it happens randomly... I really getting mad!

---

### Post by Quackers on 2012-04-25
Please post the contents of your .conkyrc file in code tags.

---

### Post by Toz on 2012-04-25
It might be the result of xfce's session-saving feature. When you logout of xubuntu/xfce, there is a checkbox option to save the session. If this is selected, all currently running programs will be restarted on re-login. If then, you also add a conky autostart, you'll be starting another instance of it.

To reset the saved sessions cache:
```
rm -rf ~/.cache/sessions
```
...and try again. It is best to do this after you've logged out and from TTY1 (ie. Ctrl+Alt+F1). If you do it from within xfce/xubuntu, make sure that the option to save the session is unchecked on logout.

Then you can decide whether to use xfce's session-saving to start conky or to use autostart.

---

### Post by dentaku65 on 2012-04-25
> **Quackers said:**
> Please post the contents of your .conkyrc file in code tags.

Here you go
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window yes
own_window_class Conky
#own_window_type override
own_window_type root
own_window_transparent yes
own_window_argb_visual yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes


alignment top_right
gap_x 25
gap_y 40
minimum_size 182 600
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color E7E7E7

color0 D2E5EA
color1 FFFF15
color2 EFCE0E

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}uptime: ${alignr}${color2}${uptime}${color}
${goto 32}version: ${alignr}${color2}${pre_exec cat /etc/issue.net}${color}
# |--CPU
${offset 2}${color0}${font Poky:size=16}P${color}${font}${voffset -4}${goto 32}CPU: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 E07A1F CE5C00}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 126}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 126}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 126}${top cpu 3}${alignr }${top mem 3}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--eth1
${else}${if_up eth1}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth1}${color}${font} ${alignr}${color2}${upspeedgraph eth1 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth1}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth1}${color}${font} ${alignr}${color2}${downspeedgraph eth1 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth1}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth1}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 30 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
####################
# - WEATHER - #
####################
# http://weather.yahoo.com/
${voffset -8}${font Droid Sans:style=Bold:size=8}WEATHER $stippled_hr${font}
${goto 12}${voffset 8}${color0}${font Weather:size=28}y${font}${color}
${voffset -29}${goto 32}${font Droid Sans:style=Bold:size=10}°: ${font Droid Sans:style=Bold:size=12}${color1}${execi 30 /home/sava/.conkycolors/bin/conkyYahooWeather cur ITXX0090 c}°C${color}${font}
${goto 32}${voffset 5}${color0}${font VariShapes Solid:size=10}Q${font}${color}${font Droid Sans:style=Bold:size=10}${color1}${execi 30 /home/sava/.conkycolors/bin/conkyYahooWeather min ITXX0090 c}°C${color}${font}  ${voffset -5}${color0}${font VariShapes Solid:size=10}q${font}${color}${voffset -2}${font Droid Sans:style=Bold:size=10}${color1}${execi 30 /home/sava/.conkycolors/bin/conkyYahooWeather max ITXX0090 c}°C${color}${font}
#############
# - PHOTO - #
#############
# For a working photo widget you need to specify a file or directory in conkyPhoto or conkyPhotoRandom script in  /home/sava/.conkycolors/bin /usr/share/conkycolors/bin folders
${voffset 10}${font Droid Sans:style=Bold:size=8}PHOTO $stippled_hr${font}
${execi 120 /home/sava/.conkycolors/bin/conkyPhotoRandom}${image /tmp/conkyPhoto.png -s 174x110 -p 4,400}${voffset 104}
```

---

### Post by dentaku65 on 2012-04-25
> **Toz said:**
> It might be the result of xfce's session-saving feature. When you logout of xubuntu/xfce, there is a checkbox option to save the session. If this is selected, all currently running programs will be restarted on re-login. If then, you also add a conky autostart, you'll be starting another instance of it.

To reset the saved sessions cache:
```
rm -rf ~/.cache/sessions
```
...and try again. It is best to do this after you've logged out and from TTY1 (ie. Ctrl+Alt+F1). If you do it from within xfce/xubuntu, make sure that the option to save the session is unchecked on logout.

Then you can decide whether to use xfce's session-saving to start conky or to use autostart.

Ok. 
Seems that clearing the saved sessions plus uncheck the save session on exit option of Xfce "fix" my issue.

I'll try to put back the saved session option in order to check if the problem will be permanent fixed or not.

Thx!

---

### Post by dentaku65 on 2012-04-25
:mad:
Check save session option on Xfce cause multiple conky processes
:mad:

---

### Post by Toz on 2012-04-25
The Save Session option will save the current session. If you have one instance of conky running, it will save one instance. If one the other hand, you started a second instance (for example through autostart) and saved the session, you would then have 2 saved conky instances.

If you want to use the saved session functionality, don't add a conky autostart item. Instead, manually start (only one) instance of conky (Alt-F2) and save the session. The session can be saved by logging out with "Save session" option checked, or immediately through Settings Manager->Session and Startup->Session tab. In fact, I believe you can manage your sessions from this location.

---


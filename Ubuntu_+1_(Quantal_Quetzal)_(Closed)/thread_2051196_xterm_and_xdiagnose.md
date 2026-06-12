---
title: "xterm and xdiagnose"
date: 2012-09-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thotz on 2012-09-01
Sorry for this question, but why is xterm and xdiagnose shipped with the Ubuntu desktop.

I think they don't "fit" in the system. The logos are also very ugly.

Or are they really needed? 

Thanks for your help!

Thomas

---

### Post by jerrylamos on 2012-09-01
Don't know.

On Unity install I'll do a Ctrl-Alt-t to get a terminal then lock it to the launcher for later use.

This is Ubuntu install with sudo apt-get install lxde 
which has an accessory lxterminal which I add to the bottom panel, set the colors to what I want with edit preferences.

Ubuntu removed 2D so I use lxde desktop except for a quick check if Unity 3D has a bug on any of my tower, notebook, netbook test setups.

---

### Post by itcotbtoemik on 2012-09-01
> **thotz said:**
> Sorry for this question, but why is xterm and xdiagnose shipped with the Ubuntu desktop.

I think they don't "fit" in the system. The logos are also very ugly.


xterm is shipped because the alternative terminal is not suitable for "safe" startup.  For what it's worth, Ubuntu exists in a sort of time-delayed mode (a year or two) from current development.  xterm's icons were improved a while ago, providing higher-resolutions - see [http://invisible-island.net/xterm/xterm.html](http://invisible-island.net/xterm/xterm.html) for example.

---

### Post by cariboo on 2012-09-01
> **thotz said:**
> Sorry for this question, but why is xterm and xdiagnose shipped with the Ubuntu desktop.

I think they don't "fit" in the system. The logos are also very ugly.

Or are they really needed? 

Thanks for your help!

Thomas

Xterm and xdiagnose are parts of the default gnome installation that Ubuntu uses as a base for the distribution. As usual you aren't forced to use them, as you can add packages that *fit* better.

---

### Post by kuvanito on 2012-09-01
> **thotz said:**
> Sorry for this question, but why is xterm and xdiagnose shipped with the Ubuntu desktop.

I think they don't "fit" in the system. The logos are also very ugly.

Or are they really needed? 

Thanks for your help!

Thomas

you're good,you only mentioned 2 xterm and xdiagnose,take a look at what i think is crap:

sudo apt-get remove brasero* contacts* empathy* aisleriot* gnome-games-data* gwibber* libreoffice* onboard* deja-dup* gnome-orca* synaptic* remmina* rhythmbox* shotwell* usb-creator* software-center* ubuntuone* xdiagnose* xterm* 
sudo apt-get purge brasero* contacts* empathy* aisleriot* gnome-games-data* gwibber* libreoffice* onboard* deja-dup* gnome-orca* synaptic * remmina* rhythmbox* shotwell* usb-creator* software-center* ubuntuone* xdiagnose* xterm* 
sudo apt-get autoremove
sudo apt-get autoclean

this is what my house looks like.
then again the terminal is my best friend!

---

### Post by cariboo on 2012-09-01
> **kuvanito said:**
> you're good,you only mentioned 2 xterm and xdiagnose,take a look at what i think is crap:

sudo apt-get remove brasero* contacts* empathy* aisleriot* gnome-games-data* gwibber* libreoffice* onboard* deja-dup* gnome-orca* synaptic* remmina* rhythmbox* shotwell* usb-creator* software-center* ubuntuone* xdiagnose* xterm* 
sudo apt-get purge brasero* contacts* empathy* aisleriot* gnome-games-data* gwibber* libreoffice* onboard* deja-dup* gnome-orca* synaptic * remmina* rhythmbox* shotwell* usb-creator* software-center* ubuntuone* xdiagnose* xterm* 
sudo apt-get autoremove
sudo apt-get autoclean

this is what my house looks like.
then again the terminal is my best friend!

If you are going to all that trouble, why not just do a Debian/Ubuntu netinst?

---

### Post by kuvanito on 2012-09-01
> **cariboo907 said:**
> If you are going to all that trouble, why not just do a Debian/Ubuntu netinst?

nah,i like to play with sh|t
i enjoy doing all kinds of stuff like this,i got all the time on the world to play with linux or ubuntu or you name it,i've done it!

as you can see my pc has hot swap bay and i got bunch of hd laying around and all kinds of usb fd so for me installing one system or the other or testing this or that or changing things they way i like or what ever it's just a matter of minutes.this moment my puter is 12.10 unity the next minute is 12.10 gnome or pear os5 or windows xp or man,i can change my puter like i change my undies :lolflag:

---

### Post by cariboo on 2012-09-01
> **kuvanito said:**
> nah,i like to play with sh|t
i enjoy doing all kinds of stuff like this,i got all the time on the world to play with linux or ubuntu or you name it,i've done it!

as you can see my pc has hot swap bay and i got bunch of hd laying around and all kinds of usb fd so for me installing one system or the other or testing this or that or changing things they way i like or what ever it's just a matter of minutes.this moment my puter is 12.10 unity the next minute is 12.10 gnome or pear os5 or windows xp or man,i can change my puter like i change my undies :lolflag:

I used to do the same thing, when I was learning to use a Linux distribution, I guess I've gotten lazy since, :), although I still do something similar using vbox, these days.

---

### Post by jbicha on 2012-09-01
xterm has been included in Ubuntu for a long time. I tried objecting to the recent visibility of xterm, but that hasn't been successful yet. [http://pad.lv/129041](http://pad.lv/129041)

---


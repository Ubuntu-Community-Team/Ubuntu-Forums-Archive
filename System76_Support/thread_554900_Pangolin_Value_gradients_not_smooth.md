---
title: "Pangolin Value gradients not smooth"
date: 2007-09-19
forum: System76 Support
---

### Post by Zxaos on 2007-09-19
Hey all...

I just bought a new Pangolin Value a little under a month ago and I'm mostly very impressed.

One issue that I can't seem to figure out, though, is that gradients are showing up as banded for me.  As far as I can tell, X is running in 24-bit mode, though.  Any thoughts or suggestions? (It's not a compiz problem, as it happens with compiz both on and off)

---

### Post by thomasaaron on 2007-09-19
Yeah, I get that on our shop pangolin too. I've tried a number of ideas to smooth it out, but I've not been able to figure anything out yet.

It is definitely not related to the actual desktop image. It seems to be the same across applications.

---

### Post by Zxaos on 2007-09-19
maybe a driver issue?

I'm honestly not far from bumping the quality down to 16 and letting the true dithering handle it - a couple of related posts on the rest of the forum seem to say that because the 16-bit drive does real dithering, it actually looks better.

The other posts mentioned something about the amount of video memory being configured as too little, but I wasn't really able to follow them.

---

### Post by thomasaaron on 2007-09-19
I just lowered the color depth to 16 and it looks much better.

To do that:

1. Back up your xorg.conf file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

2. Run the xserver utility:
sudo dpkg-reconfigure xserver-xorg
WARNINGS:
a. Do not autodetect hardware. This option is given twice in the utility.
b. Choose "intel" for the driver
c. Everything else should be the default settings.

3. sudo reboot

The very last choice of the utility lets you set your color depth. Choose 16.

Best,
Tom

---

### Post by kungfoofairy on 2007-09-19
A quicker way to fix it would be to just change the config file manually using any text editor.

An example:
Open a terminal window
gksudo gedit /etc/X11/xorg.conf
Ctrl+F (Find) DefaultDepth
Edit this line from ```
DefaultDepth    24
``` to ```
DefaultDepth    16
```
Ctrl+S (Save)

This way you also don't risk borking something else during the setup.

---

### Post by Zxaos on 2007-09-19
Yeah, that's a bit better for many gradients, although I still noticed it on some.  I'd still appreciate a true fix if someone can figure it out. Thanks for the instructions.

---

### Post by kungfoofairy on 2007-09-20
Supposedly this is fixed in Gutsy (7.10), but someone [_backported_]("http://ubuntuforums.org/showthread.php?t=494943&highlight=intel+x3100") it to feisty .

 I installed it and it works great (to remove the banding and improve colors in general at least). I don't use much eyecandy in GDM so I don't know whether or not this would fix any of your compiz problems.

---

### Post by Zxaos on 2007-09-21
Looking at the thread, I'd be a bit concerned about introducing bugs since I'm running compiz currently, and people there seem to be having mixed results with it causing compiz instability.

However, I'll give it a shot, probably next week (too many things due this week to risk mucking up my school computer)

---

### Post by thomasaaron on 2007-09-21
I've had nothing but trouble with compiz under Feisty.
Under Gutsy, though, it's not too bad.

---

### Post by Zxaos on 2007-09-22
I actually haven't run into any problems with it apart from maximized windows not always updating their content ( and an un-maximize re-maximize usually fixes that).

I'm running the version that shipped with feisty, and I've even installed and activated some of the extra plugins too.

Weird.

---

### Post by thomasaaron on 2007-09-24
Well, the biggest problem I had under Feisty with Compiz was that it always hosed my desktop switcher, which I depend upon heavily to stay organized. For me, it was a deal-breaker.

---

### Post by Zxaos on 2007-09-24
In that it reduces the number of desktops to one?

It's a bug with how they turn on the desktop cube effect.  Run this:

```
#! /bin/bash
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --typd int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

It'll give you back the four workspaces on the bottom right and make  the cube work.

Of course, if it's a different problem completely, ignore me.

---

### Post by thomasaaron on 2007-09-24
Well, that's not exactly the problem I had. But I'll check it out to see if it fixes my problem too.

With mine, if I had gnome configured for, say, six desktops, it would delete that configuration completely so that when I rebooted (even without desktop effects) I would only have two, and there would be no names within them.

---


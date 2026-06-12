---
title: "Distro for a very old computer?"
date: 2009-12-17
forum: The Cafe
---

### Post by forsaken_pariah on 2009-12-17
Hi all... My in-laws' computer stopped working about a week ago, so they asked me to take a look at it. After playing around with it I determined the problem was a bad motherboard. Unfortunately, with all their Christmas shopping done, they don't have the money to buy a new one, so I decided I'm gonna build them a new one for Christmas. However, I would at least like to give them something to connect to the internet with for now, so I had to salvage some spare parts I found between my house and theirs to make a functional box. The computer definitely won't run XP, and I don't have 98 SE lying around anymore, so I have to use Linux. But the computer doesn't have enough RAM to install Xubuntu from the alternate install disc, so I have to use another distro...

The system has a Cyrix 6x86 MII processor @ 250 MHz with 64 MB RAM. The users have never used any OS other than Windows, except for one of the boys playing around in Ubuntu on my laptop for a couple hours while I was there looking at their computer, so it needs to kinda user friendly. Any ideas of the best distro to use?

---

### Post by Sef on 2009-12-17
Look at [DamnSmallLinux]("http://damnsmalllinux.org/"), [Puppy Linux]("http://damnsmalllinux.org/"), and [DeliLinux]("http://delilinux.org/").

---

### Post by HappinessNow on 2009-12-17
> **forsaken_pariah said:**
> Hi all... My in-laws' computer stopped working about a week ago, so they asked me to take a look at it. After playing around with it I determined the problem was a bad motherboard. Unfortunately, with all their Christmas shopping done, they don't have the money to buy a new one, so I decided I'm gonna build them a new one for Christmas. However, I would at least like to give them something to connect to the internet with for now, so I had to salvage some spare parts I found between my house and theirs to make a functional box. The computer definitely won't run XP, and I don't have 98 SE lying around anymore, so I have to use Linux. But the computer doesn't have enough RAM to install Xubuntu from the alternate install disc, so I have to use another distro...

The system has a Cyrix 6x86 MII processor @ 250 MHz with 64 MB RAM. The users have never used any OS other than Windows, except for one of the boys playing around in Ubuntu on my laptop for a couple hours while I was there looking at their computer, so it needs to kinda user friendly. Any ideas of the best distro to use?
Macpup Opera or Foxy...or any Puppy derivative.

Their is even a Puppy/Ubuntu hybrid out called Upup.

---

### Post by lostinxlation on 2009-12-17
"Light" version of vector linux is made for old computers. There are some reports that installations fail allegedly due to processing power, but you could try.
I'm running Vector Linux Light(6.0) on thinkpad 570(300MHz celeron, 128MB) and it is pretty quick for that poor processing power.
I'm also running puppy linux on Thinkpad 240(300MHz celeron, 128MB) and accessing the internet is not lightning fats, but is OK. 
 
If s/he has never used OS other than Windows, I believe puppy linux is better choice since it seems to be designed more for gui than command line interface.

---

### Post by Cam42 on 2009-12-17
tinycore?

---

### Post by ~sHyLoCk~ on 2009-12-17
AntiX ?

---

### Post by GeneralSpecific on 2009-12-18
DSL would probably run the _fastest_...but it's not the most user friendly.

[COLOR="Blue"]Puppy would be my suggestion as well. [/COLOR] 

If you have trouble with speed, or _compatibility with old hardware _don't be afraid to try an older version, with an older kernel.  That has helped me get older hardware working in the past.

Or...if you want to do it the hard way: (I have a computer-laptop with similar specs) I installed Debian 'Lenny'- command line only, added X11, ROX-filer,etc and then JWM as the window manager.  It ran great, but took some time to set up.  You can even theme JWM to look just like XP! (for familiarity)

Let us know how it goes!

-Ryan

---

### Post by starcannon on 2009-12-18
> **sef said:**
> look at [damnsmalllinux]("http://damnsmalllinux.org/"), [puppy linux]("http://damnsmalllinux.org/"), and [delilinux]("http://delilinux.org/").
+1

---

### Post by forsaken_pariah on 2009-12-18
Thanks for the help, guys. After looking around and wasting a few CD's I decided that I'm using Vector Lite. It seems to be the right balance of fast and lightweight and user-friendly. I just really wish they could use GNOME. :( Oh well. It'll be on the big computer....

> **GeneralSpecific said:**
> Or...if you want to do it the hard way: (I have a computer-laptop with similar specs) I installed Debian 'Lenny'- command line only, added X11, ROX-filer,etc and then JWM as the window manager.  It ran great, but took some time to set up.  You can even theme JWM to look just like XP! (for familiarity)

I actually almost wish they were gonna be keeping this one. I would totally do that. I had a very similar setup on an old computer of mine running Debian Etch with Xvesa/Fluxbox.

Actually I might try to get it back from them when I give them the new one....:)

---

### Post by smo0th on 2009-12-18
[vectorlinux]("http://vectorlinux.com/")

---

### Post by smo0th on 2009-12-18
oh, already there, good choice! =)

---

### Post by forsaken_pariah on 2009-12-18
Well, after doing some excavating in my old storage building, I found some upgrades, and this computer now has a 366 MHz processor w/ 256 MB ram. I'm working on installing Xubuntu as I type. Once again Linux has successfully breathed life back into a computer that has long been dead and gone in the eyes of Macrohard...

And the youngest son just called to ask when he was gonna get to play with "the Unbunto" again. :)

---

### Post by smo0th on 2009-12-21
bwahahaha that's nice :) when I got children I'll also make them linux lovers =)

---

### Post by Grifulkin on 2009-12-21
[Tiny Core](www.tinycorelinux.com)

---

### Post by Glenn nl on 2009-12-21
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Install the Minimal, then install these packages for a user friendly, super-fast system:

xorg
gdm
xfce4
gdebi
epiphany-browser
thunderbird
xfce4-terminal
synaptic
gpaint
abiword
gnumeric
xubuntu-default-settings
xubuntu-restricted-extras
xfce4-taskmanager
xfce4-screenshooter
dmz-cursor-theme
file-roller
pidgin
mousepad
ristretto
xfburn
xfce4-notifyd
xfmedia

A minimal system like this runs in about 60 mb of ram.

---


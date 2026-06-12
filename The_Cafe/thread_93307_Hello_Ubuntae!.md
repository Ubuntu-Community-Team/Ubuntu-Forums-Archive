---
title: "Hello Ubuntae!"
date: 2005-11-21
forum: The Cafe
---

### Post by T0PS30 on 2005-11-21
Before I'll post about my problems, I thought I'd better say hi first, just to be nice. So.. Hi!

Mini-Bio: I ran Ubuntu successfully for 2 weeks as my #1 desktop OS until I decided to try and update my Nvidia drivers... The ones out of the box only allowed 60Hz refresh rates which started to annoy me. 

New drivers means no more Ubuntu for me, can't even boot via recovery mode... So I'll be off to the right forum now. 

Am I the first to come here due to problems? :razz:

---

### Post by poofyhairguy on 2005-11-21
Hello and welcome.

---

### Post by sapo on 2005-11-21
Hi, be welcome, make yourself at home :)

And my post count love this kind of topic ^^

---

### Post by BoyOfDestiny on 2005-11-21
[QUOTE=T0PS30]Before I'll post about my problems, I thought I'd better say hi first, just to be nice. So.. Hi!

Mini-Bio: I ran Ubuntu successfully for 2 weeks as my #1 desktop OS until I decided to try and update my Nvidia drivers... The ones out of the box only allowed 60Hz refresh rates which started to annoy me. 

New drivers means no more Ubuntu for me, can't even boot via recovery mode... So I'll be off to the right forum now. 

Am I the first to come here due to problems? :razz:[/QUOTE]

Hi and welcome, actually I think your problem isn't related to the video drivers. It's that ubuntu chooses safe settings for your monitor. You need to put values new values for vertical and horizontal sync.

Google (or find) your monitors values for horizontal vertical sync.

Then, sudo gedit /etc/X11/xorg.conf

(case sensitive)

scroll down to some section that looks like this:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-110 #for higher refresh rate
	VertRefresh	50-160 #for higher refresh rate
EndSection

Replace with your listed values (unless you have a p220f from viewsonic...then you can use my settings :) )

EDIT: For clarity I mean the initial problem, the refresh rate. Mine defaulted at 60hz, when I changed the values it gave me 85hz (1600x1200)

---

### Post by T0PS30 on 2005-11-21
Yeah I just found a post about this 60hz thing and the monitor settings. But I can;t get into Ubuntu anymore so what am I supposed to do?!

---

### Post by BoyOfDestiny on 2005-11-21
[QUOTE=T0PS30]Yeah I just found a post about this 60hz thing and the monitor settings. But I can;t get into Ubuntu anymore so what am I supposed to do?![/QUOTE]

I know it's bad to recommend a re-install... 
Hear me out though. 

If during the install you manually partition (let's say 10 gig root, the rest /home), you will have all your settings and personal stuff seperate from root... 

What this means is you can install Ubuntu again (either new version or same, clean install) and have all that data intact. 

I recently did this on both my machines, and I can say within 10-15min (if you have good net access) you can have your machine up and running the way you like it...

Anyway barring that... I guess try to login under recovery mode, and change your xorg.conf back to the original driver option?

EDIT: specifically: dpkg-reconfigure xserver-xorg

---

### Post by T0PS30 on 2005-11-21
Don't quite fancy a re-install just yet. I wouldn't loose much but it feels sort of like giving up. 

I posted a real thread on thie issue here [http://ubuntuforums.org/showthread.php?t=93312](http://ubuntuforums.org/showthread.php?t=93312) it also shows my problems re logging on and getting command line access... Thanks for helping out!

---


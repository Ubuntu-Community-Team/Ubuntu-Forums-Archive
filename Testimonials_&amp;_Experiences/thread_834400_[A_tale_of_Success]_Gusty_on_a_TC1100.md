---
title: "[A tale of Success] Gusty on a TC1100"
date: 2008-06-19
forum: Testimonials &amp; Experiences
---

### Post by stormbolter on 2008-06-19
Cautionary note: Some of the procedures noted here are not for the faint of heart. Without the invaluable help of some UbuntuForums users as well as some LQWiki ones, this procedure would not been possible, and my default system on this laptop would be Windows XP.

After my tale of resounding failure with Heron on my desktop, I wanted to add a "user satisfied" tale, altough with Gutsy.

It all began when, because installing windows XP and its patches on this laptop requires a very careful order of installation, I botched again and ended up with a slow-as-a-dead-snail installation. What caused the slowness I'm not sure, perhaps I instaled the Tablet MUI before Windows MUI or reverse, or perhaps I should install SP2 before both MUIs. I don't wanna know. I was fed up with windows. And, as I did with my desktop, flipped the switch and installed Ubuntu.

Now, If some of you have a TC1100, know although most linux distros by default support the most common components and will result with a functional laptop, some others (tablet, wifi, side buttons) are not very well supported or... not at all.

Fortunately there are a group of very brave users (most of the ones I think reside here in UbuntuForums) that have dedicated a lot of their free time to make every component of this little but very complete laptop work as fine as in windows, or in some cases, even better.

Here are the steps necessary to configure everything in the TC1100.
[LIST]
[*]Install Ubuntu Gutsy
[*]Update (you'll want to enable the restricted repositories)
[*]Get Nvidia Drivers. The video card is quite capable and one of the best assets of this laptop.
[*]Get Modem Drivers. I don't really use a lot the modem, but damned I be if I get caught in a wifi-less town without a modem!
[*]Modprobe wmi-tc1100. It enables the deactivation of the wifi and bluetooth and the brightness control.
[*]This was the easy part. Now we have to create a special version of the wacom driver if we want FULL support (if you're happy without the tablet buttons, skip the two next steps)
[*]Get build-essentials,xorg-dev and download the 0.7.8-3 version of the wacom drivers from the [main webpage]("http://linuxwacom.sourceforge.net/").
[*]Now we have to patch the wacom version. I followed step by step the [LQWiki Section]("http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons"), and I unpacked the files on /usr/src, applied the patch and ./configure, make, make install. And prayed.
[*]Now we just have to edit the xorg.conf and enable the wacom cursors (just need to uncomment some lines -[this ubuntuforums thread explains it quite well]("http://ubuntuforums.org/showthread.php?t=563736")), restart X...
[*]Phew! It worked first time! Now we need to enable the rotation of the screen. Although it seems to disable some acceleration (GLXGears seems much slower now), this tablet is made to be held upright, specially when reading ebooks or comics.
[*]To enable rotation, we need NVIDIA binary driver. Also, the wacom-tools package, or the stylus won't work correctly if we rotate the screen (*note that some stylus sensitive apps like xournal don't like to be "rotated" when active. You probably will need to restart the application after rotation*).
[*]You will need to modify the xorg.conf again. Yes, i could do it before, but I forgot to, so I ended editing the xorg.conf twice.  Just add the line [FONT="Courier New"]Option "RandRRotation" "true"[/FONT]in your device entry and you'll be fine.
[*]Now we need a script to make the rotation work automagically. I made a version from the two previous sources (LQWiki and UbuntuForums Thread) that seemed to work well.
[*]To make it respond to the tablet buttons, we need an application called xbindkeys. You can configure it [following these instructions]("http://wiki.linuxquestions.org/wiki/Tc1100#Bindings_for_the_Stylus_Buttons").
[*]Following the advice on the same section I installed xournal and xvkbd
[*]I also installed Cellwriter to have something similar to HWR
[*]For the Q menu I used [Tabatha]("http://groundstate.ca/tabatha"), which was written with this function in mind.
[/LIST]

It took me part of my sanity, a great deal of faith and about four hours of work to get it to the actual state. Everything except the dualhead works perfectly, and I only fire the windows part to play mahjongg and to chat through Live MSN (with HWR support).

It was worth it? Sure! Getting the windows installation to the same point took me 12 hours. Yeah, most of the time I spent was installing software wich is a lot easier than configuring the laptop. But looking back it was not that hard, now that there are great tutorials here and there.

Note for people thinking to upgrade to Hardy on the TC1100:
The linux kernel of the 8.04 version does not incorporate the WMI patch, which was officially included in the next kernel version. It is advised to wait until the 8.10 (that uses this kernel) is released to upgrade the distro. Also I tried to follow the same instructions and I did not have a lot of success, so I went back to Gutsy.

---

### Post by hyper_ch on 2008-06-20
cool that it works .)

---


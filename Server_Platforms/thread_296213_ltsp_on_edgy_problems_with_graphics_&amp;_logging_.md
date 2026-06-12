---
title: "ltsp on edgy: problems with graphics &amp; logging out"
date: 2006-11-09
forum: Server Platforms
---

### Post by Juxi on 2006-11-09
Hi!

I installed LTSP on a Edgy server and everything works quite okay, except for the graphics, I do sometimes have blocks of gray that just appear on the client screen. Also when browsing the web, some pictures just do not appear in the right place or get stuck on screen when I swith to another tab or window.

Another problem is that when I try to log out from a thin client all the programs are closed but the the system seems to hang with jsut the wallpaper on the screen... waiting does not solve the problem ;(

any suggestions on these probs?

---

### Post by Kalif on 2006-11-13
Hi Juxi,

regarding your graphics problem it is probably either
something wrong with your x.org configuration or a
bug in the graphics driver for your particular hardware.

Regarding the login problem it may be some Gnome setting
that is "stuck" in the wrong place. Try to create a
new user account and try using that for logging on.
If you still is deprived of the delightful Ubuntu
desktop it is not that problem.

Best luck,
K.

---

### Post by fnjordy on 2006-11-16
I'm seeing a grey bar on the right hand side of the login screen, and the terminal hangs instead of powering off.  Going to install Dapper again and try to compare the differences as it used to work.

:(

---

### Post by fnjordy on 2006-11-18
My thin client is using the AMD Geode chipset and it appears the NSC (National Semiconductor) driver is being used.  It appears a bit out of date, VESA works better but without acceleration.  In Xorg 7.2 there's a new AMD driver based on a Geode driver from AMD used in the OLPC laptop, I've just seen there is a GIT version in Edgy that will be worth a try:

[http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-amd](http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-amd)

---


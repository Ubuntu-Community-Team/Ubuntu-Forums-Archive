---
title: "Get the Gunze touchscreens working"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by Megatog615 on 2007-10-19
It looks like nobody has gotten the Gunze touchscreens to work on Ubuntu at all. I have an old Panasonic Toughbook CF-M34 with a Gunze serial touchscreen (/dev/ttyS3). Of course, it doesn't work since the driver hasn't been updated in years.

---

### Post by Zdravko on 2007-10-19
What is that? I've never heard of it before. Is it a smart device?

---

### Post by Megatog615 on 2007-10-20
Certain old monitors(not sure if they're still around) had a touchscreen by the vendor of "Gunze." There is a Linux driver for them, but it is for XFree86 and will not build for Xorg. Hence, it doesn't work in Ubuntu.

I have a Panasonic Toughbook CF-M34 which has one. A quick search here shows that a few people have had problems with them(the touchscreens) but with no solution.

---

### Post by Zdravko on 2007-10-20
Aha. Thanks for the explanation.

---

### Post by Megatog615 on 2007-10-20
Hopefully given that the driver's source is available, someone could design a driver for modern Xorg installations?

---

### Post by Zdravko on 2007-10-21
Then we need a volunteer to do that. Maybe someone dev from Cannonical?

---

### Post by Skerit on 2007-10-22
I'm currently looking into turning some old laptops into regular audio players (for the bathroom and stuff) and want a touch screen, but it's too stupid to buy completely new screens for them ..

I've been looking for an external device to make my old screens touchscreen-ready ...

* Never mind .. never be so naïve to trust a tutorial which says touchscreen films only cost 5 dollars at radioshack ...

---

### Post by ScrappyLaptop on 2007-11-11
Actually, ever since I updated to Gutsy two days ago, the Gunze touchscreen on my Itronix IX-250 is reporting as follows:

output from:
'cat /proc/bus/input/devices'

I: Bus=0003 Vendor=0637 Product=0001 Version=0122
N: Name="GUNZE GUNZE Touch Panel"
P: Phys=/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse2 event4 
B: EV=b
B: KEY=400 0 0 0 0 0 0 0 0 0 0
B: ABS=3

this would seem to indicate that evdev is recognizing it, and indeed the cursor moves to a point relative to where I touch the screen.  Calibration is way off and the Y-axis is inverted, but it is a start.

Oddly, there does not appear to be an Input section in xorg.conf that matches, but it is showing up as  "/dev/input/mouse2", in that when I touch the screen, the contents of ../mouse2 changes

I should have prefaced this with noting that I don't know if this will work with a stock install of Gutsy, as this laptop started out with Breezy 5.10 upgraded to Dapper and then Gutsy.  Along the way, I downloaded, modified and compiled the only driver I could find for the Gunze, but since it was for XFree86, it of course never worked at all.

I should have kept notes but this has been a multi year on-again-off-again process.  Best I can do at this point is first see if anyone else on a fresh Gutsy gets anything from ''cat /proc/bus/input/devices' -it looks like another user on this forum (different thread) also has a similar functionality from the device, but it looks like they have not compiled the older drivers, etc., nor checked for anything in /dev/input nor /proc/bus/input/devices, so I'm hoping that the latest install handles the basics and just detail work remains...

The point is, the Gunze does work with Gutsy; let's start comparing this working example with yours and document it!  I don't frequent this forum all that often so please email me using my forum handle as the username and yahoo.com as the domain.

---

### Post by Megatog615 on 2007-11-13
Lucky me, my CF-M43's screen has crapped out and is now useless(backlighting seems to be the problem; flickers/etc).

---


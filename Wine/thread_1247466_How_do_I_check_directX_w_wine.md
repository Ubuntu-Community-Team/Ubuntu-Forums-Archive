---
title: "How do I check directX w/ wine?"
date: 2009-08-23
forum: Wine
---

### Post by mbuehl on 2009-08-23
New linux user, long time computer guy, I don't know how to check directx, usually i'd just type dxdiag in a run prompt and see what was up, but I have no idea how to do this in wine.

Anyway, a lot of my games wont start up because there are no 3d acceleration modes available. I also realize this might be an issue with my graphics card being improperly installed or having the wrong driver, but I am 100% certain my card is functioning as it was working in windows flawlessly before I gave windows the boot. How do I check to make sure it's configured properly? It's an nvidia 9600GT I believe.

---

### Post by mbuehl on 2009-08-23
I really need to get better at posting when people might actually be awake... :D

---

### Post by qamelian on 2009-08-23
You should start by going to System > Administration > Hardware Drivers to see if a restricted driver is listed as available for your card. If you either haven't done this or haven't installed the proprietary Nvidia drivers by some other means, you will still be using the open-source drivers which may not perform as well depending on what graphical task needs doing.

---

### Post by andrea000 on 2009-08-23
if your drivers are installed correctly you may
use [winetricks]("http://wiki.winehq.org/winetricks") to install direct x make sure your
drivers are installed correctly first.

---

### Post by jacksaff on 2009-08-23
Wine doesn't use directX. It's an interface for the hardware and linux doesn't have support for it. What wine does is translate directx calls into opengl ones that linux can deal with.

There are many drivers for video cards in ubuntu and not all of them support 3D. In particular, the open source drivers which ubuntu can ship without any legal repercussions don't do 3D so you want to make sure you have the restricted drivers installed.

grep -i "x driver" /var/log/Xorg.0.log

should tell you what video driver you have. If it says nv and not NVIDIA then you need to install the restricted driver - see post above.

---

### Post by andrea000 on 2009-08-23
I'm sorry jacksaff is right wine does not
use direct x but winetricks does have the
d3dx9 and dinput9 directx9 user redistributable
in it.I think it's just the runtime .dll but i'm
not sure sorry about that i should have told you
that in my first post.But they may help

---

### Post by mbuehl on 2009-08-23
When i type your CLI line, i get this:
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009

Hardware drivers says I am using... 
NVIDIA accelerated graphics driver (version 180) [Recommended]

However I don't recall having to do anything like click "okay I know I might be breaking some laws", or agreeing to anything,

Can someone direct me to the best nVidia driver I can use? I have a geforce 9600 GT, xfx branded

---


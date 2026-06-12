---
title: "wine question"
date: 2009-03-02
forum: Wine
---

### Post by rusty83 on 2009-03-02
So Ive come a long way with learning linux ubuntu 8.10 over the past 48 hours. Ive got my wireless working, graphics drives installed, and even got the cube dekstop and wobbly windows to work with compiz fusion.

now I am at the point where I need to install some windows programs (namely microsoft office 97, and world of warcraft). I have wine installed properly (i think, installed through add/remove programs) but the problem is when I either run winefile in the terminal or try to run configure wine from the applications drop down, i cant read anything. To elaborate, the wine config comes up completely blank, all the tabs are there but no words at all. when I run winefile the program comes up that looks like windows file manager, i can see all the folders but not any of the names. I heard theres a problem with nvidia graphics cards and wine, is this the problem? anyone know what I can do to fix this? I would really appreciate it. Sorry for the long post!

---

### Post by handy on 2009-03-03
There is at least one huge thread on WoW in the Wine sub-forum.

If you do a search for wow you will find plenty of info' as far as installation & setting up is concerned.

You should also find the other help you need has already been posted, but I'll ask the mod's to move this thread into the Wine sub-forum.  Whether they do or not seems to depend on which mod takes the request. :lolflag:

---

### Post by cogadh on 2009-03-03
If you have a GeForce 2 through 6 video card, then it is actually a problem with the legacy Nvidia drivers. It can be fixed by altering a reg entry in Wine:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/300476/comments/17](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/300476/comments/17)

---


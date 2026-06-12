---
title: "I can't get to a console in virtualbox - OpenSUSE guest on Ubuntu host"
date: 2010-04-14
forum: Virtualisation
---

### Post by dgw on 2010-04-14
I installed OpenSUSE in virtualbox to try it. My mouse worked during the installation, but now that it's installed, I boot into OpenSUSE, see a nice desktop with a mouse pointer... but I can't move the mouse.  It's capturing my mouse, but it just doesn't work. I've been searching for a way to fix this and found that I need to exit xorg.conf. That's fine, if I can somehow magically get to my xorg.conf to edit it. For the life of me I can't seem to get a console. I've tried ctrl+alt+f1 while my mouse is captured, but it just takes me to the console in Ubuntu (the host OS). I found a relevant thread about this ([http://www.linuxquestions.org/questions/linux-general-1/switching-virtual-terminals-within-virtualbox-662935/#post3248551](http://www.linuxquestions.org/questions/linux-general-1/switching-virtual-terminals-within-virtualbox-662935/#post3248551)) and it hasn't helped. I think I've tried pretty much every combo of ctrl, host key, alt, super key, and f1. No console. I also can't seem to find a way to get a console while OpenSUSE is booting.

Help please. :P

edit: I booted with an Ubuntu live CD and edited /etc/inittab so that it would boot with runlevel 3, and now it's booting to console for me. Now I guess fixing the mouse issue is the hard part.

---

### Post by dgw on 2010-04-14
The title of this thread is totally inaccurate now, but I'm still having problems with this. The fix that I'm finding from googling for info on the mouse issue is:

```
sed "s/vboxmouse/mouse/" -i /etc/X11/xorg.conf 
```The problem now is that I don't have a xorg.conf. I tried sudo Xorg -configure, but when I tried the resulting xorg.conf, it gave me a black screen. I also tried a xorg.conf that I found on the internet that someone said would work with virtualbox, and that gave me a black screen as well. I've tried fiddling with those xorg.confs, and writing my own xorg.conf...I'd love to see something other than a black screen while using a xorg.conf. I don't even know if the mouse issue is an X problem anyway, or if I'm just wasting my time fiddling with xorg.confs.

Edit: If someone tells me the name of a distro that is:
1. awesome
2. works in virtualbox without lots of fiddling
Then I'll probably just wipe the OpenSUSE install and try it instead. Fiddling with xorg.conf files has made this not fun, and the whole point here was to try a new distro recreationally.

---

### Post by dgw on 2010-04-16
> **cuinan128 said:**
> Wow! I’ve never heard of this before and I think they’re awesome!
You think what's awesome? :-s

edit: I reinstalled OpenSUSE, this time using the defaults offered during the install (last time I did manual partitioning, no office software, and gnome rather than KDE). Everything seems to work fine this time. :D :D :D

Edit again: Oh fun, the post by the guy who responded is gone now. I guess he was a bot or something, but now I look like I'm talking to myself or shamlessly bumping. :roll:

---


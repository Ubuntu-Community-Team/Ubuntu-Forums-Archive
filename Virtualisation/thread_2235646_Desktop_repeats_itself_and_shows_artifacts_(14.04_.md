---
title: "Desktop repeats itself and shows artifacts (14.04 on VmWare)"
date: 2014-07-22
forum: Virtualisation
---

### Post by johnnyk2 on 2014-07-22
I'm running 14.04 as a guest on a Win8.1 host. A few days ago, after changing the size of the VmWare window, my desktop is basically cut off but repeats itself. 
[Here's a screenshot]("http://i.imgur.com/dDnL7B9.png")

[Another one with nautilus - notice the artifacts]("http://i.imgur.com/QoOaNof.png")

I've tried different environments (Unity, Gnome, lxde), changing resolutions, resetting to default - no dice.

Anyone got any idea what I could try?

```
jars@jars-desktop:~$  lspci | grep VGA
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
jars@jars-desktop:~$  glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: VMware, Inc.
```

This might be better suited for the hardware forum - sorry if it is.

---

### Post by slickymaster on 2014-07-22
Hi johnnyk2, welcome to the forums.

I've moved your thread to the **Virtualisation** sub-forum.

Please see this as it refers to a similar issue: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1686](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1686)

---

### Post by johnnyk2 on 2014-07-22
Sorry for picking the wrong forum & thanks for the pointer; I tried this before but gave it another go, but vmware-tools no longer include x-drivers, so this kb is outdated (at least for VMWare Player 6.0.3) and had no effect. Reinstalling xserver-xorg-video-vmware unfortunately also did not help.

---

### Post by slickymaster on 2014-07-22
What kernel are you running?

My first guess would be an incompatibility between the kernel and the vmware video driver packaged with Ubuntu 14.04.

---

### Post by johnnyk2 on 2014-07-22
Ubuntu 3.13.0-32.57-generic 3.13.11.4

How could I un/reinstall that driver?

---

### Post by slickymaster on 2014-07-22
Not sure exactly how because I don't use VMWare.

Anyway there's a LP bug already filled on this: [VMware guest video broken by the 3.2.0.64 kernel update]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vmware/+bug/1328898")

---

### Post by JohnnyK on 2014-07-22
OP here - thanks for the pointer, I will try this tomorrow and report back.

EDIT: Updated kernel to 3.14.1 and all is well again. Thanks so much for the help.

Can someone mark this as solved please?

---

### Post by slickymaster on 2014-07-23
You're welcome. I'm glad you're got it fixed.

It's you who have to mark the thread as SOLVED, since you were the one who started it. To do it just scroll to the top of the thread and look for the Thread Tools menu item on the right of the toolbar then click on this menu item to produce a dropdown menu and click "Mark this thread as solved". This will mark your thread as solved.

---

### Post by JohnnyK on 2014-07-27
> **slickymaster said:**
> It's you who have to mark the thread as SOLVED, since you were the one who started it. 
I know but I can't as I recovered my old account and the account I started the thread with is now inactive.

---

### Post by Iowan on 2014-07-27
> **JohnnyK said:**
> Can someone mark this as solved please?Done. :)

---


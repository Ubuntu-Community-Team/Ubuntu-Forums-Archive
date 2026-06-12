---
title: "What is on what partition?"
date: 2009-04-23
forum: System76 Support
---

### Post by jpoRS on 2009-04-23
Hola,

So in order to (hopefully) fix a few self-inflicted problems, I am planning on doing a fresh install of Jaunty.  Is there some way I can tell which partition I have something on so I know what I need to backup?

I am sure this is a very simple question, I just seem to be completely incompetent at partitions, every time I try to figure something out about them I just seem to get more confused.

Thanks in advance,
jim

---

### Post by utnubuuser on 2009-04-23
Gparted on the liveCD will tell you how much of a partition is in use, and how much of it is free-space.
I think Gparted will usually also list the mount-points, - like /home /root, swap, etc.
Usually the only one you need to concern yourself with is the home partition.  That's where all your documents music etc are kept.
When I install,  I do a root ( / ) partition (approx 4gigs), a swap partition (1.5x amount of installed ram), and a /home partition(give home most of the disk space).

That way, if you need to re-install, you can use the existing /home partition so you don't have to re-do all your configuration settings (like email accounts, browser preferences, screen-saver etc).

---

### Post by jpoRS on 2009-04-23
That seems like exactly what I needed to know.  Gracias!

jim

---

### Post by PGScooter on 2009-04-24
In order to see what is on what partition, use the following two commands:
```

sudo fdisk -l
sudo mount

```
Actually I don't know if sudo is needed on the second command. The first command displays your partition information, and the second command shows you where each partition is mounted to. You could also check out the files /etc/mtab /etc/fstab

---


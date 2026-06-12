---
title: "Gnome showing blank screen, 9.04"
date: 2009-07-21
forum: System76 Support
---

### Post by andrewdied on 2009-07-21
My serval performance (serp4, I think) has gone into a bad state.  I shut it down poorly and the ext2 (3?) partition got bad.  An fsck or two later I was up and running, but it had some quirks like when I'd login, bash would tell me: "/home/andrew/.profile: Stale NFS file handle.", I suspect because the inode was corrupted.

So, after pulling back some things like .profile and .bashrc from a backup, when I log into gnome all I get is a mouse pointer and a blank screen.  I had gotten notices that the gnome power daemon wasn't configured properly, so I forced a reinstall of that and the error went away.  Fortunately I'd installed XFCE, and that works fine.

Is there a way I can do the same thing with gnome and not do a complete reinstall of 9.04?  I'm not sure what packages to select.  Thanks for the help.

---

### Post by thomasaaron on 2009-07-22
Well, you can reinstall gnome with...

sudo apt-get --reinstall install ubuntu-desktop

However, I'm worried that you have one of these two bugs...
[B]
1. A Tracker Bug[/B]
> It's recently come to my attention that this problem is actually a Tracker bug. It occurs either when upgrading directly from Intrepid to Jaunty or when doing a fresh install from some older Jaunty disk images.

We have an ongoing forum post going on it. Please see...
[http://ubuntuforums.org/showthread.php?p=7225556#post7225556](http://ubuntuforums.org/showthread.php?p=7225556#post7225556)

Running these commands should fix it...
sudo apt-get install tracker-utils
tracker-processes -r 

After running these commands, try to run fsck on your partitions from a live CD. If that doesn't repair your filesystem, you may need to re-image. 

If fe-imaging becomes necessary, you should download the latest Ubuntu image (i.e. don't use an older disk image, as it may install the problematic software).


**2. SATA Driver Bug (and this one really stinks)**
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)

---

### Post by andrewdied on 2009-07-22
> **thomasaaron said:**
> Well, you can reinstall gnome with...

sudo apt-get --reinstall install ubuntu-desktop

However, I'm worried that you have one of these two bugs...


Yeah, I'm worried about that SATA bug.  I've never used tracker before, but I tried that just in case.  I also tried reinstalling ubuntu-desktop with your instructions, but it just reinstalled the one small program, under 100k.  

I'm really concerned I'll wind up with another weird bug down the line that exists now, but I haven't run into yet.   While I'd like to avoid the pain of a fresh install, I don't know if I can avoid it.  (I had upgraded from 8.10 to 9.04, by the way.)

If you have a way to force a reinstall of all the gnome pieces I'll give that a try.

---

### Post by thomasaaron on 2009-07-23
I'm not sure how you would do that.

That bug, according to the report I posted, doesn't exist before Intrepid's *-9 kernel or in Karmic Koala. It seems to be hitting the kernels in between.

---

### Post by andrewdied on 2009-07-23
> **thomasaaron said:**
> I'm not sure how you would do that.

That bug, according to the report I posted, doesn't exist before Intrepid's *-9 kernel or in Karmic Koala. It seems to be hitting the kernels in between.

Oh, I meant run into another key file that got corrupted / destroyed earlier.  For example, I haven't been using postgreSQL in the last month, so maybe it's broken.

If you meant "how do you reinstall of of gnome" unless you know a way I'll have to reinstall 9.04 entirely.

Question: what's Karmic Koala?

Question: The kernel I'm using right now is 2.6.28-13.  Is that a known good or a known bad kernel?

---

### Post by wojox on 2009-07-23
Try and reset the terminal

```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

---

### Post by andrewdied on 2009-07-23
> **wojox said:**
> Try and reset the terminal

```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

No joy.  I ran that in a regular terminal, logged out of XFCE (the only window manager currently working), and tried logging in with the gnome default session.  I got the login sound and a black screen with a pointer.

Earlier I'd made a second user to try and get a fresh profile from the default.  Same result -- black screen on login.

I think my install has wandered into the badlands.

---

### Post by thomasaaron on 2009-07-23
Karmic Koala is the next version of Ubuntu (9.10). 

According to that bug report, the *-13 kernel is one of the problematic kernels.

---

### Post by andrewdied on 2009-07-23
> **thomasaaron said:**
> Karmic Koala is the next version of Ubuntu (9.10). 

According to that bug report, the *-13 kernel is one of the problematic kernels.

Oh, ok (version).  So, what's the recommendation on recovering my gnome desktop?  I can go and install all of the gnome package, and hope that it kick starts the rest of the desktop / window manager / etc enough so that I can use gnome again.  Otherwise I'm not sure what else to do besides a fresh install.

Then I just have to keep hoping my partition doesn't break again.  I did run that tracker fix, just in case.

---

### Post by thomasaaron on 2009-07-24
At this point, it's probably just simpler to re-install than to try and figure out all the things that are probably hosed.

---

### Post by andrewdied on 2009-07-28
I've re-installed Ubuntu 9.04, and gnome is working again.  The only question I have left is it installs 2.6.28-11 as the kernel.  Of course, it's nagging me to install 2.6.28-13.  I have no opinion about kernel releases.  Do you think I'm better off keeping the default kernel, or upgrading to the latest?  I still don't know if it was tracker or the kernel that got me.

Aside: it'd be really nice if the system76 driver installed compiz config tools and put in some common settings.  Compiz has some neat eye candy, some it it useful, but it's hard as all get out to decide what each of the conflicting optinos do.

---

### Post by thomasaaron on 2009-07-29
Well, if memory serves, that bug runs from the -9 kernel and isn't reported as fixed until Karmic Koala's kernels. So, whether you're on the -11 or the -13 kernel probably doesn't make any difference. The SerP4 does seem to be one of the affected computers, too.

From what I'm able to gather, large file transfers exacerbate the problem.

---

### Post by andrewdied on 2009-07-29
> **thomasaaron said:**
> Well, if memory serves, that bug runs from the -9 kernel and isn't reported as fixed until Karmic Koala's kernels. So, whether you're on the -11 or the -13 kernel probably doesn't make any difference. The SerP4 does seem to be one of the affected computers, too.

From what I'm able to gather, large file transfers exacerbate the problem.

Ah, well.  I'll update the kernel then, so at least it stops bugging me about it.  Hopefully they'll backport the dang fix!

---

### Post by gila_monster on 2009-07-29
> **andrewdied said:**
> Ah, well.  I'll update the kernel then, so at least it stops bugging me about it.  Hopefully they'll backport the dang fix!

Hope springs eternal. Meantime...to which kernel will you update? I installed 2.6.29 directly, seems to work pretty well.

---

### Post by andrewdied on 2009-07-29
> **gila_monster said:**
> Hope springs eternal. Meantime...to which kernel will you update? I installed 2.6.29 directly, seems to work pretty well.

I'd be happy to, but 2.6.28-13 is the one that's appearing in my 9.04 update list.  Is that one available somewhere else?

---

### Post by gila_monster on 2009-07-29
> **andrewdied said:**
> I'd be happy to, but 2.6.28-13 is the one that's appearing in my 9.04 update list.  Is that one available somewhere else?

Ooops, sorry, wasn't clear. I installed the 2.6.29 kernel from deb files I pulled from the Ubuntu site. I'm at work, so I don't remember where. I will look it up and home and post the information. 

Someone mentioned the backports repositories, but I don't think the newer kernel is in there yet.

---

### Post by gila_monster on 2009-07-30
I think the packages listed here are not the very latest, so check the site first. The instructions themselves still apply.

[http://ubuntuforums.org/archive/index.php/t-1108281.html]("http://ubuntuforums.org/archive/index.php/t-1108281.html")

---


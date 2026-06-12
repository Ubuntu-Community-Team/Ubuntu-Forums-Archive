---
title: "upgrading to edgy (for syst?em76 customers)"
date: 2006-10-26
forum: System76 Support
---

### Post by fuscia on 2006-10-26
are there specific directions for system76 owners for upgrading to edgy?

note to moderators: i started the other thread in this forum for a reason (i believe the tags for the other thread specified system76). please don't move this thread too. thanks.

---

### Post by PriceChild on 2006-10-26
Sorry...

---

### Post by fuscia on 2006-10-26
> **PriceChild said:**
> Sorry...

i forgive you. (don't anyone ever say i'm not divine.)

---

### Post by newlinux on 2006-10-26
[http://www.ubuntuforums.org/showthread.php?t=276104](http://www.ubuntuforums.org/showthread.php?t=276104)

[http://www.ubuntuforums.org/showthread.php?t=280557](http://www.ubuntuforums.org/showthread.php?t=280557) (for XGL issues)

---

### Post by crichell on 2006-10-26
The standard upgrade command:
```
gksu "update-manager -c -d"
```

Has worked brilliantly - nothing special to do.  newlinux pointed out the previous post.  Refer to that if you have installed XGL and are having problems.

After the upgrade run the system76 driver:

System > Administration > System76 Driver Installer

We have one known bug we're working on - Edgy has borked Suspend on the Gazelle and Serval Series.  Not a deal breaker so we're moving ahead and expect we'll have it fixed within a couple of days.

---

### Post by fuscia on 2006-10-26
"about 22 hours and 16 minutes remaining"??? lol!

---

### Post by crichell on 2006-10-26
oh man, that's tough.  we're downloading iso's and it's crawling as well :)

---

### Post by lord trousers on 2006-10-27
The only weird thing I had happen was my Pangolin mistaking my USB mouse for a keyboard (at least, I think that's what happened), making my real keyboard slightly unresponsive and repeating keys for no good reason sometimes. That made it very hard to log in. :D

I unplugged the mouse and plugged it back in, and it's all good now. I'm *fairly* sure this was Logitech's problem.

Having AIGLX integrated into Xorg is nice.

---

### Post by crichell on 2006-10-27
The AIGLX integration is nice - Fonts are smooter and much easier on the eyes.

---

### Post by underdog512 on 2006-10-30
I just want to know how upgrades are going for everyone.  I have a ratel desktop with the nvidia graphics card.  I am debateing upgrading to edgy.  I don't want to break my machine which is running brilliantly!!

---

### Post by crichell on 2006-10-30
We have had very few problems upgrading - I've give it a go and if you have any problems we'll be here to help.

---

### Post by newlinux on 2006-11-02
After waiting about 5 or 6 hours through the upgrade, I run into a couple snags. First, X won't start - I get an error, can't load i810 module. Which module should I now being trying to load? I tried reconfiger xserver-xorg but still couldn't get it to work. Can someone shoot me a working xorg.conf for the 12" gazelle value?

Second weird thing is that the kernel doesn't seem to be upgraded. When I upgraded to edgy on my desktop I (after having to manually reconfigure menu.lst) was running 2.6.17-10-generic. That kernel doesn't even exit in my /boot directory on my laptop (I think it's still running 2.6.15 something - I'll have to run into the other room and check. Did the update completely fail? it didn't give me any error messages. Any help would be greatly appreciated as I use my laptop a ton everyday.

---

### Post by newlinux on 2006-11-02
just for added info, I removed all the compiz/xgl stuff (downgraded the packages in some cases) before upgrading. Perhaps that screwed something up.

---

### Post by newlinux on 2006-11-02
Okay. I manually installed xserver-xorg-intel (I hope that was the right thing to do) and got X running. Then I manually installed the newer kernel. So I think I'm okay now, except that now I need to redo all of my splash screens, and some of my desktop settings are quite off now. I wonder what happened with X not being installed right, and the kernel not updating...

---


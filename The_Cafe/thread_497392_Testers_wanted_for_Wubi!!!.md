---
title: "Testers wanted for Wubi!!!"
date: 2007-07-10
forum: The Cafe
---

### Post by ago on 2007-07-10
Hi all,

We are closing in on our final [Wubi](http://wubi-installer.org) release, so testing and feedback on these latest builds would be highly appreciated. Please use the version below (I will update the link if I change something).

Latest build: [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php)

Please use the [dedicated forum](http://ubuntuforums.org/forumdisplay.php?f=234) to report any issue (edubuntu does not work yet).

Thanks in advance.

---

### Post by Polygon on 2007-07-10
ill see if i can check it out, i dont have any extra hard drives to install anything on however..

---

### Post by Warpnow on 2007-07-10
Wubi would save Ubuntu bandwith if I could install from an already downloaded .iso

---

### Post by ago on 2007-07-10
> **Polygon said:**
> ill see if i can check it out, i dont have any extra hard drives to install anything on however..

you do not need an extra drive, you need enough free space (5GB) inside of the windows partition

---

### Post by ago on 2007-07-10
> **Warpnow said:**
> Wubi would save Ubuntu bandwith if I could install from an already downloaded .iso

You can, but it has to be an alternate ISO. You just have to place it in the same folder where you have wubi.exe

---

### Post by ago on 2007-07-10
I have uploaded rc2 (7.04.02). If all goes well this will be the final.

---

### Post by codydh on 2007-07-10
What do you mean it has to be an "Alternate ISO?"

Thanks!

---

### Post by stepan2 on 2007-07-10
alternate iso's are the ones that don't have a livecd mode.

---

### Post by FuturePilot on 2007-07-10
> **ago said:**
> you do not need an extra drive, you need enough free space (5GB) inside of the windows partition

So it installs itself inside the Windows partition?

---

### Post by ago on 2007-07-11
> **codydh said:**
> What do you mean it has to be an "Alternate ISO?"

Thanks!

In the ubuntu website select to see all download options, you will see several types of ISOs, some are called alternate. Wubi will download one for you if you do not have one already. The issue with that is that the algorithm to select the mirror is a bit dumb, and sometimes you get a slow mirror...

---

### Post by ago on 2007-07-11
> **FuturePilot said:**
> So it installs itself inside the Windows partition?

Yep, that is the full point. Wubi alleviates the pain associated with ISO burning and partitioning. It installs as any other windows application, but it still gives you a proper dual boot. And on top of that, it can be uninstalled as any other windows application... That will hopefully help addressing bug #1. 

Anyway we need feedback, so try it out!

---


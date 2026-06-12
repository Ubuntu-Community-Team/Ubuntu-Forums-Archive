---
title: "Package lubuntu-desktop removed in my last update."
date: 2018-03-08
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2018-03-08
I have an installation of Lubuntu-18.04 as a VM in VirtualBox and in an update yesterday, the first time I've updated for several days, I noted that the lubuntu-desktop package was removed for some reason.

A search has given no information or reason for this and I wonder if others have seen the same, and if anyone knows why.

I realise that the OS runs fine without this meta-package, but in the past it has always been something that would be removed only if one of the default packages of Lubuntu was manually removed as it was no longer wanted.  It will otherwise be of use only if upgrading in the future from 18.04 to either 18.10 or eventually to 20.04.

Perhaps it will come back in a few days; perhaps I will see what happens if I try to reinstall it.
Watch this space!

---

### Post by TheFu on 2018-03-08
Did you do a "minimal install?"

---

### Post by VMC on 2018-03-08
I forget what I removed, but that meta package was also removed. Maybe 'snap'. I think that was it. Not sure.

---

### Post by ajgreeny on 2018-03-09
No, it was not a minimal install but using the normal ISO soon after it was available; I'll look for the date when I am on that machine and report back.
Incidentally, it has been running very well for as long as I have had it running.
I did try out Lubuntu-Next with the LXqt desktop as well for a while but that was completely useless and did not boot to a GUI.

EDIT:
I have booted my Lubuntu VM and can see that I installed it 28 Nov 2017 and it has been kept fully updated since then.
I also just re-installed lubuntu-desktop package to see what would happen; this is what was then removed and installed as shown from synaptic ->File ->History
> Removed the following packages:
libcurl3

Installed the following packages:
libcurl4 (7.58.0-2ubuntu2)
lubuntu-desktop (0.92)
lubuntu-gtk-desktop (0.92)
whoopsie (0.2.59build1)
Time will tell if the upgrade from libcurl3 to libcurl4 will make any problems but I suspect not.

---


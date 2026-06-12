---
title: "Problem after converting from Parallels to VMWare"
date: 2013-06-28
forum: Virtualisation
---

### Post by chazmuzz on 2013-06-28
Hi,

I had the trial version of Parallels Desktop 8, running on my Macbook Pro OSX 10.8.3.  I am running Ubuntu 12.04.

When the trial ran out, I converted my VM to VMware Fusion. It is running great with one exception; whenever I start it, I get an error message stating "An error occurred while trying to mount /media/psf".  I can skip past this error and everything works fine.  But it's annoying, and I am unable to run the VM in nogui mode.

I understand that /media/psf is something to do with Parallel Tools.  How do I remove them?  Or at least prevent Ubuntu trying to mount them at startup?

Many thanks,

---

### Post by chazmuzz on 2013-06-28
Solved this by removing the entry in /etc/fstab

---


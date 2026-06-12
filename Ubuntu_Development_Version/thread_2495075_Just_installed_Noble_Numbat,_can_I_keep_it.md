---
title: "Just installed Noble Numbat, can I keep it?"
date: 2024-02-06
forum: Ubuntu Development Version
---

### Post by hrsetrdr on 2024-02-06
I just installed Noble Numbat, used the ISO available on Thu 18 Jan 2024 . Is it possible to just update / upgrade like a rolling release, rather than doing a whole fresh install ?

---

### Post by #&amp;thj^% on 2024-02-06
Yes sir, but still a good idea for a good back-up strategy.

---

### Post by oldfred on 2024-02-06
You can.

But it will get a lot of updates and changes. Occasionally updates get out of sync & something breaks.
And because of the many updates, you get larger log files.

I keep current LTS as main working install. But like to install each release even before final just to see changes, so change from one LTS to another is not as different.
I would make good backups and plan new install, just to houseclean the built up cruft.

---

### Post by hrsetrdr on 2024-02-06
Thanks. Yes, I am obsessive about backups.

---

### Post by #&amp;thj^% on 2024-02-06
oldfred is right about the accumulation of cruft as  Noble comes closer to release.

If your a Gnome and Snap user it can amount to a lot!
I just cleaned and removed a ton of left overs, just form snaps:
```
snap list
No snaps are installed yet. Try 'snap install hello-world'.

```

---

### Post by ajgreeny on 2024-02-06
The alternative method i choose is to install regularly using a virtual machine install in KVM, and updating the iso file I currently have using zsync, meaning a very quick download of very few Mb compared to the complete iso file.
It is quick and easy to install using KVM and it's very easy now to share data files between host and guest to check how well everything is working.

If one of my VMs is badly broken or corrupted or simply won't boot I will fairly quickly delete it in virt-manager rather than spend a lot of time trying to put things right, and then install again using a new iso from the dailys archive at [https://cdimage.ubuntu.com](https://cdimage.ubuntu.com)

Select which DE version you want and then go from there as there is little point in installing the iso from 4 weeks ago when changes happen so quickly at this stage of development.

And don't ever forget about those **BACKUPS**!

PS:
By the way, snaps are something I remove totally from my machines so no extra cruft and space lost to them for me.
My machines are mostly 10 years old so pretty slow compared to newer ones and snaps, eg firefox take about 40 -60 seconds to appear the first time in a session; far to long for me so snap,and all its Infrastructure goes from my computers straight after installing any distro.

---

### Post by guiverc on 2024-02-06
I'm using my primary box right now, which is running Ubuntu *noble* (I'm logged into my Lubuntu/LXQt session as I normally am, but I also have Xubuntu/Xfce, Ubuntu/GNOME installed too; ie. my box has multiple desktop/flavors installed).

I'll suggest using `apt full-upgrade` over just `upgrade` due to the use of a *development* release.

Also note if you're using *'noble*' in your sources; your system will switch to *stable* when RC is reached and remain that way when *noble* becomes 24.04, ie. that isn't like a rolling system.

You can also use *devel *too (see [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) etc), but personally I prefer using the *codename* thus am on *noble* now, and manuallydoing an upgrade after the current *development* release (ie. *noble*) reaches *stable* AFTER I've examined the system & done a clean up (*which I'm doing every six months**; a few days to a seek post-release date*).

My prior box was an *artful* install (*late beta actually; artful became 17.10*), and it survived ~until *kinetic* or 22.10 when the PSU failed & I decided I needed to replace the box... ie. that's numerous years sitting on the *development* release which eventually needed to be replaced because the hardware itself failed.  I won't say I didn't have problems (*eg. when Lubuntu after 18.04 switched from LXDE to LXQt; or change of desktops*) but that is pretty good for my *primary* system in my opinion.

This replacement box was installed during *lunar *(23.04) cycle, and I actually opted to *non-destructively re-install *it 30-Aug-2023 due to an issue in the *mantic* (23.10) cycle, so be aware issues can always occur if you remain on the *development* cycle, but **you'll want to have a *secondary* box available for when those issues do occur.**

eg. if I want to use specific apps I use on occasion (*and have been needing to of late too!*) there can be problems, eg. [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844)  ... backups aren't always a fix for *development* release issues; using 23.10 or a *stable* release is a better option for some cases..

---

### Post by corradoventu on 2024-02-07
I am writing from Noble installed from the 10th Jan ISO and although I have also installed the 6.8.0-060800rc2 and 6.8.0-060800rc3 kernels my log is only 529.0 MB.

---


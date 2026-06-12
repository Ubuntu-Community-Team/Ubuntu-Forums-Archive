---
title: "What options are available on the alternate CD?"
date: 2008-10-21
forum: The Cafe
---

### Post by etnlIcarus on 2008-10-21
I've done a bit of googling and even searched these forums but can't seem to find any details on what options are available during the alternate CD installation process.

Basically, I was planning to download an ubuntu minimal CD, allowing me to manually install my desktop of choice (Xfce4.x) and keep the system largely clean.

However, there aren't any ubuntu minimal CDs out for 8.10 beta and I was hoping to get this installation done before the official release and the subsequent repo downtime in the immediate aftermath.

So instead, I was thinking of downloading the alt CD to see if that allows for deep selective package installation. Does anyone know of any walkthroughs or screenshot tours which show all the options available on the alt CD?

Cheers.

---

### Post by Ozor Mox on 2008-10-21
When you boot the alternate CD you can select 'command-line installation' by pressing one of the F keys (can't remember which). It will install a very basic system which then lets you choose exactly what packages to install on top of it. Essentially it is the same as the mini ISO, except you have to download the whole ~600 MB CD instead of the ~10 MB mini ISO. The bonus though is that apt will use the packages from the CD instead of downloading them if you install them afterwards, making it quicker. This is what you want isn't it?

---

### Post by WorldTripping on 2008-10-21
There are a couple of advantages.

1. The alternate CD can be run with a lower amount of RAM

2. When installing the OS, you can set up a completely encrypted system (encrypted LVM).

Reason 2 is why I've just used the alternate CD to install 8.10 (Intrepid Ibex) Beta.

(And it just recognised my USB GSM dongle..)

:)

---

### Post by etnlIcarus on 2008-10-21
Thanks, folks. Might download it tonight.

---

### Post by Archmage on 2008-10-21
On alternative would be to install **X**ubuntu. This is Ubuntu with XFCE instead of Gnome.

---

### Post by etnlIcarus on 2008-10-21
Yeah I'm running the full Xubuntu desktop right now but there appear to be quite a few Gnome components running and I can't identify half the stuff being started with X. It's a struggle to keep Xubuntu < 100mb or RAM right after logging in. Supposedly, pure Xfce4 without all that stuff installed by default uses a fair bit less memory.

---


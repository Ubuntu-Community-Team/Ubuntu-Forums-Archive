---
title: "virtualization question"
date: 2009-02-18
forum: Virtualisation
---

### Post by acfreema on 2009-02-18
perhaps this has already been covered, but i'm unsure how to search for it without many inaccurate threads being drawn into the search.

i'm curious if it is possible to run a current installation of xp (it is installed on a separate partition) with a virtual machine in ubuntu 64?  right now, i'm running 64bit 8.1.

thanks in advance

---

### Post by bettlebrox on 2009-02-18
I haven't done this in years, but I used to be able to point VMWare to my pre-existing Win95 install and run within VMWare on Linux. This probably won't work with XP and later as they've anti-copying feature built in that will complain as it won't be running on the same hardware (it'll be running on the virtualised hardware which will appear different). And this might cause you Windows install not to boot at all.

The best way to go is to to start with a fresh install. Or create a disk image, mount it over the loopback device, and copy the files from your existing Windows install and then see if you can get it to boot. If it does't boot due to Window's anti-copying features, your existing Windows install should be safe (and unbroken). Also, you might be breaking MS's licensing terms if you run your Windows instance in a VM. :(

---

### Post by acfreema on 2009-02-18
if i were more awake, i would have laughed very hard at your mention of ms's terms.  regardless, that made my day.

i didn't see any way to organize a virtual machine from a current installation, so i'll try installing in virtualbox to see what i can find and post more questions when i have them.  yes sir, that iron-shackle drm is definitely making me buy more xp licenses :rolleyes:.  i paid my tax on one new laptop and got xp home and bought pro for school a few years ago.

---


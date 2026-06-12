---
title: "[SOLVED] Partition in Virtual Box .vdi?"
date: 2008-07-07
forum: Virtualisation
---

### Post by Rytron on 2008-07-07
Hi,
Is it possible to make a partitioned .vdi hard drive in virtual box?
I wanted to test if a backup I made of my vista os(which came with no dvd) worked in Virtual box. When I put in the dvd backup, fired up Virtual Box; everything looked to be going fine but then I got a message saying that I have no partition.
Any ideas?
Thanks.

---

### Post by Shazaam on 2008-07-07
Either use the Ubuntu livecd or the gparted livecd to partition the vm first. Make sure the vm is the same size as the original partition (less problems)....
50 gig os partition compressed and backed up to dvd= 50 gig virtual partition.
Depending on the type of backup it may need the original Vista to be there. If you made a "snapshot" (full copy) you should be fine.

---

### Post by Rytron on 2008-10-05
I tried gparted but it wont work under my computer - not sure why(it does work under another computer - I think its something to do with the graphics card). 
I don't have the Ubuntu live cd - only the alternative cd.
What other partition tool will work? I tried Ultimate Boot cd and many of their tools wont work under VirtualBox.

Please help.

---

### Post by Shazaam on 2008-10-05
Start VBox. Highlight the vm, go to Settings>General>Advanced. In the boot order box make CD/DVD-ROM first in the list. Then go to CD/DVD-ROM and make sure "Mount CD/DVD Drive" and "Host CD/DVD drive" is checked (and it recognised your drive)- hit ok.
Pop the gparted livecd in; start the vm. When you get to the video choices screen choose "VESA". The gparted livecd should boot and allow you to partition the vm.

---

### Post by Jordanwb on 2008-10-06
I'm not sure if Vista would work in the Virtual Machine because the Virtual Machine has different hardware than your host PC.

---

### Post by Rytron on 2008-10-06
> **Jordanwb said:**
> I'm not sure if Vista would work in the Virtual Machine because the Virtual Machine has different hardware than your host PC.

The funny thing is that GParted worked (the screen was very dull but it still worked) when I used the VESA setting when booting up my pc. When I tried the same VESA setting when using GParted in VirtualBox - no luck. I tried all the other GParted settings in VirtualBox and none worked.

I eventually got partitions set up by using one of the partition tools on the Ultimate Boot Cd. However when I installed Vista, it said restart but then just hung at boot up with a blank screen. So frustrating.

You could be right about the different hardware!

---


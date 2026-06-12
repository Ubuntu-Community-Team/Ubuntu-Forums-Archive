---
title: "Using a virtual machine to access host machines filesystem"
date: 2009-03-17
forum: Virtualisation
---

### Post by Nocturnal_son on 2009-03-17
hey, im a linux newbie. ive been looking at the linux ubuntu CE and Knoppix live cd's. Im running my Knoppix live cd through virtual pc and id like to know if its possible to access my host operating systems' files with my virtual machine.. so far ive tried the "machine additions" option on virtual pc to try and enable file sharing, but it didnt work, instead it unmounted my virtual cd drive(which has the Knoppix image mounted onto it), and i end up not been able to access any of the programs on the live cd. i tried to use my virtual machine with my linux ubuntu CE and it simply doesnt work, it boots and after that, nothing happens.. any kind of help would be much appreciated! thanx:D

---

### Post by LegendofTom on 2009-03-17
I assume you have a windows host, so you can share your harddrive on the network and access it from the guest.

---

### Post by bodhi.zazen on 2009-03-17
Moved to virtualization.

I advise you use a network protocol such as samba or ssh (scp, sshfs).

Other options include ftp and https.

---


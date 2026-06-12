---
title: "Why So Fast?"
date: 2011-10-23
forum: Virtualisation
---

### Post by Quarkrad on 2011-10-23
Sorry if this the wrong type of question for this thread.  I've just installed winXP on my 10.10 system within Virtualbox 4.  Why is the installation and 'windows updating' so fast in Virtualbox than it is if done natively on the same PC?  Is this a function of VBox, Ubuntu, or both?  I am amazed how fast it is compared to a standard winXP install.

---

### Post by northd_tech on 2011-10-23
Just as a guess- because things happen much faster in RAM than they do on [nearly?] ANY physical hard disk that needs to spin up, track sectors, move read/write heads, etc.  Also your 64-bit MoBo is a pretty wide 'pipe' to move data and operations back and forth between the CPU(s) and RAM.

I think you will eventually find that some things are painfully slow running virtualization (or maybe it's just my 64-bit machine running the old Windows 98 or my setup or ??).  I have wondered if VirtualBox had frozen up several times, but eventually it came back to life.  

I recently had to reinstall Ubuntu over the top of the previous version (no format) due to a Windows rootkit infection taking over the LightScribe software and mangling GRUB2 (and possibly some other things or else my hard disk is dying), so maybe I've got a conflict with the default kvm and kvmamd modules that my Ubuntu distro sets up by default.  Maybe I'd better look into that sometime soon.

---

### Post by xaronic on 2011-10-23
The hyper visor that runs between the "host" OS and the "guest" OS does lots of things to optimise the operation. As other users have said also because more data is run from within RAM than from disk so it is much much quicker.

---


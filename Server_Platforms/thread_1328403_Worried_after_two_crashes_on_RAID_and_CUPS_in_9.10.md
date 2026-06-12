---
title: "Worried after two crashes on RAID and CUPS in 9.10"
date: 2009-11-16
forum: Server Platforms
---

### Post by Macchi on 2009-11-16
Sorry, but I have to mention a not so positive experience with printing and storage services on 9.10                                      :

We have been forced to roll back two machines from 9.10 to 8.04 LTS after two test servers crashed independently upon simple experiments with RAID and CUPS. We have only used software from the standard repositories and were testing simple functionality related to printing, file sharing, and safe storage with LVM on soft RAID1. Contrary to most recommendations we had Gnome installed to facilitate administration. Shall I blame the graphic environment?

We lost complete contact on the console(s) & ssh. The partial solution was a reboot! 
Unfortunately I do not have time to investigate the true cause of the problems, but hope for better stability in the future since I really would like to use Ubuntu in our IT environment. 

PS: the new login environment and screens are described as confusing by a few users, the earlier artwork and functionality was better in my humble opinion.

/Signed by a stressed IT manager that ultimately loves Open Source

---

### Post by dca on 2009-11-16
I've had similar experiences running VMware on an Ubuntu 9.10 server install that had the 'ubuntu-desktop' package installed on top of it for using Gnome.  I know this doesn't help but had to do the same thing.  I wiped it, installed Ubuntu Server 8.04LTS, set up everything and then installed 'ubuntu-desktop' package... So far, so good.  Again this is the only box that had gnome on it because the rest are headless boxes...

---


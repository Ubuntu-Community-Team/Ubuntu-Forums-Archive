---
title: "Vmware can't see computer"
date: 2008-07-13
forum: Virtualisation
---

### Post by Stolea on 2008-07-13
I have installed VMWare server and got it up and running after a few initial hickups. For some reason I can see and access the drives an my network (WinXp machines) but only the VMWare drive and nothing else on the host machine. My /windows partition is set up as shared and can be seen by the network XP machine.
Any ideas?

---

### Post by Stolea on 2008-07-14
Anyone??? Please. :)

---

### Post by bodhi.zazen on 2008-07-15
Your description of the problem is vague.

What does vmware have to do with sharing from the host machine ?

---

### Post by Stolea on 2008-07-15
I installed Vmware mainly to run Quickbooks Premier and Photoshop CS2. The first because I have not found anything even remotely comparable as a native Linux program and the second because I have spent a lot of time and effort to set it up just the way I like/need Photoshop to function.
My machine is set up as a dual boot with winXp and Ubuntu. The datafiles for Quickbooks unfortunately have for the time being to reside on the winXp system which is /windows in Ubuntu.
At this point VMware-Winxp can see and access NTFS drives on my main network computer, but not the /windows(NTFS) folder/directory on my system. And the datafile resides on the /windows partition so that other WinXp network computers can access it.
I am sure that it is some little setting that I have not found (I hope)

---

### Post by bodhi.zazen on 2008-07-15
Ah ...

You need to either set up vmware to use shared directories on the host hard driver (this involves installing vmware toools onto the guest) or install samba server on the hosts and share the /windows directory.

See this thread (or similar) :

[http://ubuntuforums.org/showthread.php?t=437903](http://ubuntuforums.org/showthread.php?t=437903)

and :

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

[uwiki]ComprehensiveSambaGuide[/uwiki]

[uhelp]community/SettingUpSamba[/uhelp]

---

### Post by fjgaude on 2008-07-15
> **Stolea said:**
> I have installed VMWare server and got it up and running after a few initial hickups. For some reason I can see and access the drives an my network (WinXp machines) but only the VMWare drive and nothing else on the host machine. My /windows partition is set up as shared and can be seen by the network XP machine.
Any ideas?

After vmware is installed and loaded, you have to use your Windows install disk to plave it within vmware as a VM. Then you need to load your applications into this Windows install.

Have you followed the Sticky How-To at the top of this forum?

---


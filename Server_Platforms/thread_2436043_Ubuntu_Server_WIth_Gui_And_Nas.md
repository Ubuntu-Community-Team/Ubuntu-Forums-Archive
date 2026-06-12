---
title: "Ubuntu Server WIth Gui And Nas"
date: 2020-01-30
forum: Server Platforms
---

### Post by dreico332 on 2020-01-30
Hellow,
  
I am kind of new on Linux and i would like to share with you my  thoughts. I want to install NAS on Ubuntu. I am with Debian and OMV but i dont  quite get it. So i would like to give a chance to Ubuntu. So my  questions go like this:

  
[LIST=1]
[*]I Want to Install  Nas on Ubuntu, so which NAS Server-App can run on Ubuntu?


[*]Which Ubuntu Version should i Install. If the answer is Ubuntu  Server i would like to have a GUI so that i can run other Apps Also.  (Ddrescue-GUI) for example and other very useful apps.
[/LIST]
  
So my whole idea is to NAS On Ubuntu (Server-GUI Or Desktop) mostly  for Samba - File Server-Sharing and to have also a GUI on Ubuntu so that  i can run other apps also. *My system HW Is like this: Intel Core 2 Quad 2.66 Ghz. 2*2gb Drr2 800Mhz Ati Radeon 5450 512 MB  HDD WD 250 GB for the Ubuntu and  2X 2TB WD RED for the NAS.

  .
Thank you very Much for your time, I am looking forward for your responses .

  
Constantine.

---

### Post by SeijiSensei on 2020-01-30
Running Samba is all you need though I'd recommend also supporting NFS to share files with *nix clients.  I run both on the server in my office.

You can simply install a desktop version of Ubuntu, add Samba and nfs-kernel-server, and configure it appropriately.

Since you have two 2TB drives for storage you should consider setting up RAID1 so that the two drives mirror each other.  Not a substitute for backups, though. There are a number of HOWTOs on the Internet about using mdadm to set up a RAID array.  mdadm, like nfs-kernel-server, needs to be installed separately if you're using a desktop distribution.

---

### Post by TheFu on 2020-01-30
I've never used and "NAS" specific software.  As SeijiSensei wrote, just install **samba** for Windows clients, NFS for Unix-like clients and I'd add **openssh-server** with **fail2ban** and **sshfs** for secure file access use over the internet using ssh-keys for authentication.  ssh-keys are both more convenient AND more secure.  That never happens. Never.

I wouldn't use any GUI to configure samba or NFS - actually, I don't think there is an GUI for that.  Both are pretty easy to get working for trivial setups.  People have more trouble mounting disks than they do setting NFS. In Unix-like OSes, mounts usually don't happen automatically and if they do, we really want to use a manual mount for NAS purposes for a number of reasons.  I specifically avoid mounting storage under /mnt/ or /media/.

It doesn't matter too much which variant of Ubuntu you install, though a server, without any GUI, will use much less resources. On the machine you have, I'd install Ubuntu-Mate 18.04 today and move to the 20.04 version in June-July.

For home media, I wouldn't use RAID. I would have good backups, however. RAID is for 2 purposes and in my world, media isn't sufficient for RAID and the hassles that often come in using it.  To each their own.  I use RAID for running VMs, things that can't go down without data corruption highly likely.

---


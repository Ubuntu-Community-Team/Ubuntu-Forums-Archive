---
title: "Home NAS recommendation - Want full linux shell"
date: 2017-02-09
forum: The Cafe
---

### Post by jwhitener on 2017-02-09
Hello,

I was wondering if any of you have a recommendation for a home nas that has a full linux shell environment.  I'm most comfortable with Ubuntu/Debian based systems, so I thought I'd post on these forums to see if any of you have a NAS you like.

Basically, I want a NAS that has a full shell environment.  Rsync, grep, ls, find, sed, awk, etc.. 

I'd rather not build a custom NAS.  So if Qnap Synology, Netgear (what I have now, but a very old model) have a full linux environment, I'd love to hear about your experiences.  

I've been doing google searches for "nas with full bash environment" , etc., with little luck.  

I currently have a 4 bay Netgear readynas, and it has been great for the last 5-6 years, but it is starting to slow down and show its age.

---

### Post by wildmanne39 on 2017-02-09
*Thread moved to **The Cafe**.*

---

### Post by mastablasta on 2017-02-09
HP microserver. well built, small, versatile, linux certified.
I am using HP proliant N54L, not sure if you can still get it. it was cheap, relaible and very nicely made. but they have newer models available as well, might be sold at a higher price. they usually have plenty USB ports (extra external storage space?!) and with a bit of "hacking" one can add more disks inside as well (e.g. people added 2.5" drives into DVD / tape bay).

install the OS of your choosing. For "NAS like" interface install Openmediavault (debian based), NAS4free, Freenas (Both BSD based), ClearOS, Nethserver (both centos based), Zentyal (ubuntu based), or just use CentOS, Ubuntu, Debian... whatever you want.

we installed the OS on USB stick that was mounted on internal USB port, disk area has data disks in software (mdadm) raid 1. we are running Ubuntu server with Ajenti web interface.

these microservers have large fans and are very quiet. overall the whole setup was pricier than NAS, but offers so much more freedom and opportunity. i mean it has 4 GB ECC RAM alogn with a descent CPU. it draws a bit more power than similar Synology NAS. 

dependint on the needs (services), users and all that a Raspberry Pi can server as a NAS as well.

---

### Post by kevdog on 2017-02-09
I just built a FreeNAS system. I don't have a lot of experience with other NAS type systems but I'd have to say its very versatile.  Within FreeNAS you can install various linux distros if you want via the bhyve hypervisor.  Using bhyve I have both Ubuntu and Arch linux installed on the NAS.  I'd say go with one with a large community because depending on what you want to do with your NAS you're likely going to need help and instructions.  I'm using ZFS rather than RAID since after investigation and comparison between the two, it just seemed to have more features that were important to me.

---

### Post by gordintoronto on 2017-02-10
I use a netbook running Xubuntu as my file server. At the office I have a larger computer running Xubuntu with multiple internal and external drives, for backing up the main servers and users' workstations. We swap in new drives and archive the old ones on a schedule; the company has all the files created in the past dozen years. Up until three years ago we used tape, but it was slow and expensive.

The netbook doesn't draw much power, so it's good for a home installation.

---


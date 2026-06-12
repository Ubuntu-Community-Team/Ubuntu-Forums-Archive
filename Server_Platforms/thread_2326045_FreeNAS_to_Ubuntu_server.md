---
title: "FreeNAS to Ubuntu server"
date: 2016-05-27
forum: Server Platforms
---

### Post by lars17 on 2016-05-27
Hi all. 

I'm in the process of migrating from FreeNAS to Ubuntu server. that's due to general performance. Ive been having trouble with apps that fails, stops and not starting.
I've been using FreeNAS for 4 years now, and learned a a lot, but stil a rookie. Now i'm hoping that Ubuntu can give med a better joy and less time typing commands in console.

What ive been using FreeNAS for is Local storage for is:
Local storage for personal files and hard to get software
Personal Pictures and Home made movies.
local backup of Movies and TV-Shows for using with KODI in home network.


So I'm asking for some help til get me started.

First off. my Server spec.

CPU: Processor information
Intel(R) Core(TM) i3 CPU 540 @ 3.07GHz, 4 cores

Memory Real memory
7.51 GB total / 1006.98 MB used

Virtual memory
7.70 GB total / 0 bytes used

HDD
10x500GB (will be changed to 2TB drives when i have budget for it)
2x2TB 
(All drives are in a ZFS pool)

SAS controller
LSI SAS 9211-8i with p16 IT mode firmware
(I have a Lenovo SAS expander but not in use yet)

So far i have installed:

Ubuntu Server 16.04 LTS
MySQL server (for KODI purpose)
Webmin
ZFS-utils for linux 


1: I want to use the ZFS pool i have on FreeNAS, and be able to manage the pool from webmin.

2: share my pool om my LAN for both NFS and CIFS.

---

### Post by mastablasta on 2016-05-28
> **lars17 said:**
> 
1: I want to use the ZFS pool i have on FreeNAS, and be able to manage the pool from webmin.
webmin is not supported. although it works well for some you may have issues at home point with it. 

i am not exactly sure what you need help with or where you get stuck. however form your use description and GUI preferences it seems you migth be happier with something like Openmediavault (debian) or Nethserver (centos).

Zentyal (ubuntu) might be an overkill, but i will just mention it so you would explore the option.

Alos ClearOS (centos).

---

### Post by deadflowr on 2016-05-28
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2016-05-28
1. Forget webmin. Remove it, forget it, and never look back... Unless you want some things to inexplicably start failing after a while. Webmin is not supported nor recommended and can modify config files in its own way and not as the ubuntu server expects them to be.

2. Whats the problem with reusing the ZFS pool(s)? Did you try to import them in your new installation? Or you still haven't connected the disks that are part of the pools? You simply need to import them and they will be there. After that configure NFS and samba (CIFS).

---

### Post by lars17 on 2016-05-28
okey.. thanks for info 

How can i check ZFS featureflags on the ZFS version i'm currently running vs what my zpool on my FreeNAS is running.?

---

### Post by darkod on 2016-05-28
> **lars17 said:**
> okey.. thanks for info 

How can i check ZFS featureflags on the ZFS version i'm currently running vs what my zpool on my FreeNAS is running.?

Not sure about that. You'll probably have to google around a bit, specifying the flags you are interested in. But I believe that since ZFS is included in ubuntu now since 16.04 that it should support all flags. However that is only my opinion, you better investigate the flags that interest you...

---

### Post by kyle-peterson1 on 2016-06-04
I had nothing but troubles with trying to import my zfs mirror from freenas 9.10 in to ubuntu 16.04.  It would import successfully and you could access the files but when you ran any zfs command the process would hang.  In the end I had to use zfs send from freenas to ubuntu.

---

### Post by houstonbofh on 2016-06-06
I would not do this.

1) Nas4free (and freenas, but they hide more from their GUI) should not need you to spend a lot of time in the command line.  If they are, you need to look at why.  Going to Ubuntu will not fix this.

2) ZFS on Ubuntu is brand new.  Yes, people say it is stable, but it is not what BSD people call stable.  Not by far.  I have played with it, but I have not saved anything to it I did not have somewhere else.  It is simply not where ZFS on *BSD is yet, and I am not sure it every can be.

3) You mentioned Apps not starting.  I am guessing you are running things in the FreeBSD jails.  These are not trivial.  And a storage server does not make a good VM server.  If you absolutely positively must have it all on one box...
[INDENT]Install Ubuntu Server and KVM.
Install a Nas4free setup in a VM with hardware passthrough for all the drives.
Feel free to have your VMs mount their drives on the virtual Nas4free, just make sure you delay starting them.[/INDENT]
This setup is very cool and elegant!  And a pain to set up and manage! (And I have seen it in production!)

---

### Post by lukeiamyourfather on 2016-06-15
> **houstonbofh said:**
> ZFS on Ubuntu is brand new.  Yes, people say it is stable, but it is not what BSD people call stable.  Not by far.  I have played with it, but I have not saved anything to it I did not have somewhere else.  It is simply not where ZFS on *BSD is yet, and I am not sure it every can be.

The first GA release was over three years ago and there's been a regularly maintained PPA for Ubuntu the whole time. I've personally used it ever since the GA release on several machines, in several environments, and with hundreds of TB of data on dozens and dozens of disks. I can assure you it's stable. Much of the underlying code related to ZFS is not new. The part that's new to enable Linux support is the SPL.

[https://github.com/zfsonlinux/spl](https://github.com/zfsonlinux/spl)

Ubuntu 16.04 LTS is the first version of Ubuntu to ship with ZFS on Linux in the repositories. That's very different than the "brand new" used above.

---


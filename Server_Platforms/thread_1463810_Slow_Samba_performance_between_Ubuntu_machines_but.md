---
title: "Slow Samba performance between Ubuntu machines but fast with Windows and Mac OSX"
date: 2010-04-27
forum: Server Platforms
---

### Post by aquarat on 2010-04-27
Herro

This may not be the right place to post this... you'll probably soon see why.

If I try copying files using a Mac OSX machine or a Windows machine from one of my Ubuntu servers I get in excess of 45MB/sec. If I try the same operation between different Ubuntu machines (3 machines tried), I get around 6 - 10 MB/sec (fluctuates). If I try the same operation between Ubuntu machines using NFS I get to 55MB/sec.

It's really odd. On the Ubuntu machines I've tried mounting using smbmount, cifs and browsing the share in Nautilus... they all have about the same result (NFS goes fast though). I have also tried increasing the maximum tcp buffer size and I've tried increasing the buffer sizes in Samba's conf files, neither makes any noticeable difference.

The servers are :
Ubuntu Desktop 9.10 (x64) with 4GBs RAM, on an AMD Quad core.
Ubuntu Desktop 9.10 i386 with 2GBs RAM, Intel P4 with HT.

The machines' processors do not max out during file copy (this has been checked in htop showing all the extra stuff) and atop.

Each machine is sharing a raid device consisting of 10 drives each (mdadm). Both raid devices are formatted in JFS. NFS is also running on both machines. Both raid devices are 8 TB in size (10 one-TB drives on raid 6).

I only noticed it recently while trying to backup for the first time to an LTO-3 tape drive (needs either 40 or 80MB/sec to avoid buffer underruns).

NFS is fine for now... but it'd be great if anyone has any ideas :) . I realise Samba is a bit inefficient, but to this extent? arooooor

Tenks

---

### Post by 3L33T on 2010-04-27
> **aquarat said:**
> 
The servers are :
Ubuntu Desktop 9.10 (x64) with 4GBs RAM, on an AMD Quad core.
Ubuntu Desktop 9.10 i386 with 2GBs RAM, Intel P4 with HT.



Do these desktops have onboard Realtek (RTL8111/8168B) NIC?  If so, take a look at [THIS LINK]("http://www.linuxquestions.org/questions/linux-server-73/extremly-slow-samba-536370/").

When you mount the samba share (see /etc/fstab) try to mount the samba share as a "cifs" instead of "smbfs" and see if this helps.

---

### Post by cdenley on 2010-04-27
> **3L33T said:**
> Do these desktops have onboard Realtek (RTL8111/8168B) NIC?  If so, take a look at [THIS LINK]("http://www.linuxquestions.org/questions/linux-server-73/extremly-slow-samba-536370/").

I remember that problem.
[https://launchpad.net/bugs/161778](https://launchpad.net/bugs/161778)
It seemed to be fixed in intrepid. It was the RTL8169 driver on the client that was the problem for me.

---

### Post by aquarat on 2010-04-27
Hey 3L33T, thanks for the fast response :) and wow... yes... of the three Ubuntu machines, two have the onboard Realtek card you mentioned. The older P4 machine has a PCI Dlink Gigabit card installed. A few weeks back I tried transferring files from my Ubuntu laptop (Lenovo T61) to the Dlink-ed server and the speed was good on SMB.

> 
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


*a little while later*

Okay, I'll give the cifs option another try... and if that doesn't work debate buying another Gigabit card or sticking with NFS :P .

---


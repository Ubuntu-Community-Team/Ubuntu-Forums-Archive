---
title: "Dell PowerEdge 1950 with PERC 5/i RAID Controller Issues"
date: 2006-10-18
forum: Server Platforms
---

### Post by Avian00 on 2006-10-18
Hello,

I'm having an issue with the RAID controller on a Dell PowerEdge 1950.  ](*,)   It is a PERC 5/i RAID controller.  I have two SATA drives in a RAID 1 (mirrored) configuration.  I am attempting to install Ubuntu Server (Dapper) onto this server.  The way I would expect it to work is that in a RAID 1 setup, the two physical disks are not visable to the OS.  Only a single "logical" disk should be visible (which is actually my RAID 1 of the two disks).  Well for some reason, I see THREE disks when partitioning: sda, sdb, and sdc.  sda & sdb appear to by my phiscal disks while sdc appears to be my logical RAID 1 disk!  When I partition and format sdc, those changes get propogated to the other two drives, which further supports my theory that sdc is my RAID 1.  But why do I still see my two phsical disks?!  If I try installing the system to sdc, I get a Grub Error #21 when I try to boot.  The problem is further confused by the fact that the Desktop version of Ubuntu Dapper does NOT see the two physical disks and only sees the RAID 1 logical disk (the way it SHOULD be).  Can anybody shed some light on this?

Thanks in advance!

Matt

---

### Post by rcgabriel on 2006-10-27
Yeah, the same issue occurs with the Poweredge 2950.  See [this thread]("http://ubuntuforums.org/showthread.php?t=226114").  Ubuntu 6.06.1 LTS working fine here on 2 Poweredge 2950s, followed the instructions on page 3.  Basically, you just have to get GRUB to ignore sda and sdb and talk only to sdc, the logical RAID 1 drive.  The presence of sda and sdb doesn't really bother me since everything seems to be working just fine now.

I don't know why Desktop Ubuntu doesn't have this issue, that is strange.  But I'm not gonna worry about it if Server Ubuntu is working okay for now. :)

---


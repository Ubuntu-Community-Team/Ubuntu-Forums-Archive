---
title: "Ubuntu 7.04 on a New Intel SR2500ALLX Server"
date: 2007-06-27
forum: Server Platforms
---

### Post by cOque on 2007-06-27
Hello Everybody!

I'm just thinking of installing Ubuntu Server 7.04 (the 64 bit version maybe) onto a brand new server based on the Intel SR2500ALLX Platform, with 1 Xeon Quad-Core CPU, 4 GB of RAM and and 4 SATA 250GB Drives. I'm thinking in using the embedded RAID Feature to make a 0+1 (or 1+0, don't know which is better).

The purpose of this server is to handle a PHP based website with Apache 2, a MySQL Database (or maybe PostgreSQL), an SMTP Server and a File server (NFS, FTP, SMB).

I was wondering if any of you guys could give me some Tips for doing this installation, specially in the RAID part. Any help would be very apreciated!!

Thanks a lot!

---

### Post by Gruelius on 2007-06-28
Raid 1+0 is the better option i think, i know it sounds wierd but its done back to front so its striped (Speed then mirrored, Redundancy).

Installing wise, if the raid is handled by the hardware it should just appear as one device to ubuntu.

---


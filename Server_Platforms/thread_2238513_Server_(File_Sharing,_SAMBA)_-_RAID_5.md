---
title: "Server (File Sharing, SAMBA) - RAID 5"
date: 2014-08-08
forum: Server Platforms
---

### Post by skrydal on 2014-08-08
I try to make server, i will make two partition RAID 1 and RAID 5.
On RAID 5 I want to store data( I will use SAMBA), How I can store and share that partition in Ubuntu 14.04 LTS.

Thank you for any help.

---

### Post by TheFu on 2014-08-08
Samba doesn't care about RAID or not. That is a different layer.

Overview:
* create the RAID volumes as desired
* create the file systems on the RAID volumes
* setup samba to provide access to files anywhere on the system.

There are many how-tos for each of these things. They are really separate tasks.  [http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) and [http://www.howtoforge.com/](http://www.howtoforge.com/)  should help.

---

### Post by cariboo on 2014-08-09
Moved to Server Platforms.

---

### Post by skrydal on 2014-08-09
I have Lenovo thinkserver, where I configure two RAID partition (RAID 1 AND RAID 5) using BIOS SLI (btw I dont know how to torn off that RAID BIOS and make RAID partition during the installation of Ubuntu server. If I remove all RAID partition using SLI configuration BIOS, Ubuntu dont see any of disc during installation process). I make 3 partition then during installation of Ubuntu (one root, second swap and there are on sda partition which is RAID1 and one with mounting point /home sdb - which is RAID5). Now how to setup SAMBA to files can be stored on sdb(RAID5).

path = /home ????

---

### Post by bab1 on 2014-08-09
> **skrydal said:**
> I have Lenovo thinkserver, where I configure two RAID partition (RAID 1 AND RAID 5) using BIOS SLI (btw I dont know how to torn off that RAID BIOS and make RAID partition during the installation of Ubuntu server. If I remove all RAID partition using SLI configuration BIOS, Ubuntu dont see any of disc during installation process). I make 3 partition then during installation of Ubuntu (one root, second swap and there are on sda partition which is RAID1 and one with mounting point /home sdb - which is RAID5). Now how to setup SAMBA to files can be stored on sdb(RAID5).

path = /home ????

Install Samba and configure the shares at the bottom of the file: */etc/samba/smb.conf*

The examples in the file show how to do that.  A simple share would be```

[Share Name]
comment = description of share
path = /the/path/to/the/directory-you-are-sharing

```
The share is always referred to as //SERVER-NAME/Share-Name

You share directories (and all below) not partitions.  You do ***not*** want to share all of the sdb.

---

### Post by TheFu on 2014-08-10
Did you follow those links?

---


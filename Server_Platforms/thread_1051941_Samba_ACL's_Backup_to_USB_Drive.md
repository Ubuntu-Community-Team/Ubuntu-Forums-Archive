---
title: "Samba ACL's Backup to USB Drive"
date: 2009-01-27
forum: Server Platforms
---

### Post by linuxcorp on 2009-01-27
Hi There

I have a client that wants to backup his data to a USB drive.

Senario:
Ubuntu server 7.04
Samba 3 with acl support
Backup to USB drive

Currently the backups are running fine to the USB drive but the acl
information is not getting backed up. When the server auto mounts the usb drive it's doing it with out acl support.

How can i set it so that the USB drive gets auto mounted with acl support ?.

---

### Post by capscrew on 2009-01-27
> **linuxcorp said:**
> Hi There

I have a client that wants to backup his data to a USB drive.

Senario:
Ubuntu server 7.04
Samba 3 with acl support
Backup to USB drive

Currently the backups are running fine to the USB drive but the acl
information is not getting backed up. When the server auto mounts the usb drive it's doing it with out acl support.

How can i set it so that the USB drive gets auto mounted with acl support ?.

The ACL's are part of Linux not Samba.  I believe ACL's are set on a partition basis.  The USB drive is a separate partition and possibly a different FS structure.

---


---
title: "Samba &amp; Windows not enough space"
date: 2009-07-22
forum: Server Platforms
---

### Post by ndest964 on 2009-07-22
I have a server running Ubuntu 9.04 Server (AMD64) with Samba running on it.  I have a 1.5TB drive setup as a share.  This drive has over 700gigs free on it.  When I try copying 400 gigs from my Windows 7 machine it tells me that there is not enough free space.

I'm puzzled as the data should fit on the drive.

My fstab (big-daddy is the share):
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=67b0bad4-5b1f-4005-97c0-0e58de9e0e18 /               ext4    relatime,errors=remount-ro 0       1
# /media/data was on /dev/sda3 during installation
UUID=e61c9496-8a85-4499-a0b5-aea878ca1547 /media/data     ext4    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=257724be-5094-435a-8e8d-af4b376c6e6a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/big-daddy        ext4    defaults        0       2
/dev/sdc1       /media/downloads        ntfs    defaults        0       2

```

When I run df -h I get:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  1.2G   34G   4% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  364K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  140K  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-server/volatile
/dev/sda3             103G  188M   98G   1% /media/data
/dev/sdb1             1.4T  555G  751G  43% /media/big-daddy
/dev/sdc1             233G  110G  124G  48% /media/downloads
tmpfs                 1.5G  2.5M  1.5G   1% /lib/modules/2.6.28-13-server/volatile
/home/nickd/.Private   37G  1.2G   34G   4% /home/nickd
```

Here is my smb.conf which is pretty much out of the box:
```
[global]

   workgroup = ND-HOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes


[big-daddy]
  comment = Big Daddy (1.5TB)
  path = /media/big-daddy
  read only = no
  guest only = yes
  guest ok = yes

[downloads]
  comment = Downloads
  path = /media/downloads/admin
  read only = no
  guest only = yes
  guest ok = yes


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
```

I would appreciate any help in resolving this issue.

Thanks!
Nick

---

### Post by enz1m3 on 2009-07-24
are you sure you're copying to big-daddy and not downloads? can you send a screenshot of windows copying? (just to be sure)

---


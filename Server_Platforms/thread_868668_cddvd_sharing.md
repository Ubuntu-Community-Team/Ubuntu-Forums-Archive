---
title: "cd/dvd sharing"
date: 2008-07-24
forum: Server Platforms
---

### Post by VdubZA on 2008-07-24
I have one cd drive and one dvd drive on my Ububtu Server 8.04.1.
I want to both of them, but only manage to get the cd shared but not the dvd drive.
Here is the config I have.

/dev/scd0       /media/cdrom0    iso9660 defaults,auto,ro,user 0       0
/dev/scd1       /media/cdrom1    iso9660 defaults,auto,ro,user 0       0


mount -a
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by cariboo on 2008-07-28
If you are using samba have a look at this part of /etc/samba/smb.conf:

> # A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

Just change it to suit your needs.

Jim

---


---
title: "Beating a dead horse: ecrypted drive mount at login"
date: 2012-01-05
forum: Security
---

### Post by quequotion on 2012-01-05
I have an encrypted partition that I use for backups.

Originally, the drive was USB but recently I connected it to SATA.

Before, the drive would *usually* be available after login, but since changing to SATA (and thus changing the drive's name from sde to sda) it is *never* mounted at login, despite the password being stored.

To mount the drive, *I have to open nautilus and click on it once*.

It's not a lot of work, but it's tedious and easy to forget.

If I forget, deja-dup will fail to make backups to a drive that doesn't exist.

There must be a simple way to make this drive available at login. (ie *not* installing new sofware packages, writing a new shell script, or a full reinstall of ubuntu)

I am especially interested to know if, in some undocumented configuration file, all I have to do is change "/dev/sde" to "/dev/sda" or if there are larger issues here.

---

### Post by 2F4U on 2012-01-05
You could mount it through /etc/fstab.

---

### Post by mikaelcrocker on 2012-01-05
I would mount the drive with /etc/fstab.  I have heard of people using /etc/init.d/rc.local to mount a drive.  Personally for mounting at boot time i would go with fstab, I'm using it in tandem with s3fs.

---


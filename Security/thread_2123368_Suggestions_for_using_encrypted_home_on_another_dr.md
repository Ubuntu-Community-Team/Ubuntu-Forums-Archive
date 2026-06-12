---
title: "Suggestions for using encrypted home on another drive"
date: 2013-03-07
forum: Security
---

### Post by ld.4lpha on 2013-03-07
I have two drives, /dev/sda and /dev/sdb.  On /dev/sda I have installed 12.04 with an encrypted home directory.  On /dev/sdb, I previously had another distro installed also with an encrypted home directory.

I want to boot to my Ubuntu install, but have my home directory pointed to the encrypted home directory on /dev/sdb.

I can mount the /dev/sdb, and decrypt the home directory just fine using ecryptfs-recover-private.  What I'm not sure of is how to go about making this happen automagically.  I understand editing my fstab to mount the drive, but not exactly sure how to have the Ubuntu home point to (and decrypt) the home directory on the other drive at login.  The password to log into my Ubuntu install is the same as that to decrypt the /dev/sdb home directory.

Suggestions?

Thanks!
LD

---

### Post by ld.4lpha on 2013-03-13
Anybody?

---


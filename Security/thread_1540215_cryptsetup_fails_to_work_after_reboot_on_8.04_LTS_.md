---
title: "cryptsetup fails to work after reboot on 8.04 LTS server"
date: 2010-07-27
forum: Security
---

### Post by jo2317 on 2010-07-27
I have a 8.04 LTS server with two crypto setup disks.

They are specified in /etc/crypttab and both have separate key files that allowed them to be unlocked on boot.
They have been working unchanged and without problems for about two  years now, but after a long uptime (~260 days) I had an power  interruption today, and after the reboot, one of the crypt disks will  not open (but one does).

I have tried booting from 8.04 live desktop as well as 10.04 live cd & can see & recognise the luks info on both drives.

For the first one, I can run:
cryptsetup luksOpen /dev/sdb disk_b --key-file /path/to/key_b
that disk opens just fine--it's key file is a 1024kb file (originally from /dev/urandom)
 
However, If I try to run for the second disk:
cryptsetup luksOpen /dev/sdc disk_c --key-file /path/to/key_c
I get the following error:
Command failed: No key available with this passphrase.
 this key file is a 512kb file (again, from /dev/urandom created just  about the same time as the above one, and again, nothing's changed)
 
The only thing I can think of that might be different is that since the last reboot, I updated cryptsetup..

 Any help or thoughts would be extremely appreciated!!

---


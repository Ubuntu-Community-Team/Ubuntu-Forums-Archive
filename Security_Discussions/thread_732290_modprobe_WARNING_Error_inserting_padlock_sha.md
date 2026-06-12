---
title: "modprobe: WARNING: Error inserting padlock_sha"
date: 2008-03-22
forum: Security Discussions
---

### Post by MountainX on 2008-03-22
I'm getting the following warning/error on boot on a new installation of Hardy beta server i386. Things seem to work. Should I be concerned? How do I remove this error message if it isn't important? Otherwise, how do I fix it? 

Setting up cryptographic volume sdb1_crypt
enter LUKS pass...
[63.686712] padlock: VIA Padlock Hash Engine not detected.
modprobe: WARNING: Error inserting padlock_sha (/lib/modules/2.6.24/12-server/kernel/drivers/crypto/padlock-sha-.ko): No such device

key slot 0 unlocked.
Command successful.
cryptsetup: lvm fs found but no lvm configured

Setting up cryptographic volume sda2_crypt...
continuing with my next one gives the same error msg again.

---

### Post by MountainX on 2008-03-23
Is it better to post security questions during the week? When does this forum have the most eyeballs?

---

### Post by MountainX on 2008-03-24
I am still getting this error. But my server seems to run fine otherwise...

---

### Post by Adnarim on 2008-03-24
Hi,
I'm getting the same error and have made a bugreport about it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129)

Would be cool if you could confirm it there.

greets

---


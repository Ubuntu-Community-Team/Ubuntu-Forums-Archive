---
title: "LUKS USB drive not automounting in Jaunty"
date: 2009-06-09
forum: Security
---

### Post by goatmonkey on 2009-06-09
Hi.  New to the forums and could use a bit of help.

I've got an encrypted (LUKS) USB hard drive that won't automount when turned on.  Everything worked fine in 8.10:  log in, turn on the drive, password box pops up, enter password, drive mounted.  I've upgraded to 9.04 using update manager and now it asks the password but once the password is entered, the disk is not mounted.

The only mention of the same thing happening to anyone else is here:  [https://bugs.launchpad.net/ubuntu/+bug/363426](https://bugs.launchpad.net/ubuntu/+bug/363426) .  Just like in the post, the disk is actually opened under /dev/mapper and running /etc/init.d/hal restart and then udevadm trigger will get it mounted.  I can't pmount the disk because it complains that the disk is not removable.

Is there a way to fix this?  I'd really rather not reset hal and have to resort to sudo to get the drive open.  Is there some component that I'm missing?  Is an /etc/fstab entry required?  Oddly enough, I think I didn't have this problem with 9.04 beta on my laptop.

Thanks in advance!

---

### Post by goatmonkey on 2009-06-10
Is there a better section to ask about this?  I figured LUKS difficulties would go under security topics.  Any suggestions?

---

### Post by HermanAB on 2009-06-10
Weird, I answered you before, but my answer post is missing.

Anyhoo, I have seen the same thing once before.  I think it is due to a kernel module that is not loaded at startup.  Use lsmod and compare the modules immediately after boot and after getting it to work, then add the missing module to the modules configuration file in /etc.

---


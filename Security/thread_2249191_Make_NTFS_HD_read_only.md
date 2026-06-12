---
title: "Make NTFS HD read only"
date: 2014-10-20
forum: Security
---

### Post by jimmyh1972 on 2014-10-20
Hi
Is there a way to make NTFS hard drive (of windows in case of dual boot) read only without config fstab or using DISKS (I prefer terminal only)?
Thank's for helpers

---

### Post by TheFu on 2014-10-20
You can manually mount it with the "ro" option or if it is already mounted in through the fstab, use the "remount" option.  
**sudo mount -o ro,remout  /dev/xxxxxx  /path/to/mount/point**

I've done this for backup storage that wasn't actively being used during backup jobs. Handy.
It is also handy in CTF competitions ... you take over the website webpage change it to your team-name, then I use ACLs to make it rw for my userid only and remount the storage as RO, to mess with the other teams trying to modify it later.  Many so-called penetration testers don't really understand UNIX, so this freaks them out and they can't do anything.  OTOH, many do know UNIX well and only get slowed down for 5 seconds by this stuff.

---


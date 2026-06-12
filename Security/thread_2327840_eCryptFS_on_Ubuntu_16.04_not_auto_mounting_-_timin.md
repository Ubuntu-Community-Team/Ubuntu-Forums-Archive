---
title: "eCryptFS on Ubuntu 16.04 not auto mounting - timing issue ?"
date: 2016-06-15
forum: Security
---

### Post by Andrew_Welham on 2016-06-15
Originally posted in general help, but no one seemed to know the answer

Recently rebuilt (not upgraded) a server from Ubuntu 14.04 to 16.04 and things seem to be working fairly well, with the exception of accessing two encrypted nfs shares.
 If I manually mount them with mount -a everything is fine, no requests for passwords. so all the files including the fstab seem ok.
 If I reboot the server the nfs shares mount ok but the encrypted shares do not. If I login and sudo mount -a manually then every thing is ok.
 Looks like some type of timing issue, but I'm lost where to look.
 I could create a systemctl script to force the mount but that seems like a bit of a bodge for something which should happen automatically.

 My config is based on
[https://help.ubuntu.com/lts/serverguide/ecryptfs.html](https://help.ubuntu.com/lts/serverguide/ecryptfs.html)
 Any ideas?
 Also is eCryptFS still the recommended way for NFS disk encryption under Ubuntu 16.04. If I need to change now would be a good time
 Thanks

---

### Post by howefield on 2016-06-15
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2327755](http://ubuntuforums.org/showthread.php?t=2327755)

---


---
title: "[SOLVED] Strange rkhunter scan results"
date: 2007-04-19
forum: Server Platforms
---

### Post by wormser on 2007-04-19
I just installed Feisty Fawn and ran rkhunter.  I got the following strange results.

> * Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

I am not sure what to look for in those directories.  Personally I think the scan is bring up a false positive.  Any help would be appreciated.

Thanks

---

### Post by yabbadabbadont on 2007-04-19
Those **are** false positives.  It is perfectly normal to see those listed.  (on ubuntu at least)

---

### Post by wormser on 2007-04-19
Thanks for your reply.

---

### Post by Frank98 on 2007-05-31
If /etc/.java shows up with those files is it also a false positive? I'm not sure how to check if it's suspicious.

---

### Post by bananabob on 2007-06-05
Below are my results from rkhunter. I understand from above about the false positives, but what about the root logon message?


> Scanning for hidden files...  [ Warning! ]
Checking for allowed root login... Watch out Root login possible. Possible risk!
-----------------------------------------------------------------

Found warnings:
[09:58:04] WARNING, found:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 
[09:58:05] Warning: root login possible. Change for your safety the 'PermitRootLogin'

-----------------------------------------------------------------


---


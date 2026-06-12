---
title: "Memory Leak Server 14.04"
date: 2014-05-18
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2014-05-18
Fresh install with updates, ssh server, and samba. Bios install, not UEFI. Just finished the updates. On reboot I am greeted with this line after logging in.

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
```

What does it mean and or what do I do about it? Should I worry about it?

*EDIT* After having fiddled around a bit with the server, over ssh and directly I have seen this line popup a handful of times while doing varying things. Creating a directory, removing a file... typical management stuff it has popped a few times. Not often and there is nothing in the log that I can find.

---

### Post by trevor_allett on 2014-05-19
[http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)

---

### Post by Mike_Barnes on 2014-10-20
you guys rock. "sudo apt-get remove libpam-smbpass" fixed the problem

---


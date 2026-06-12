---
title: "Yet another question about mounting with user read/write access using vboxsf here"
date: 2008-01-05
forum: Virtualisation
---

### Post by kakao on 2008-01-05
Hi there.

I'm giving up on finding the answer myself and thus asking for help.

System is: Windows XP host, Ubuntu Gutsy 7.10 guest using Virtual Box, addition cd installed in Ubuntu guest. Windows folder set up called "sharefolder", Ubuntu mount point called /mount/point (not really ;) but I'll use it here).

The closest I got was using
```

sudo mount.vboxsf -o uid=1000,gid=1000,convertcp=iso8859-1 sharefolder /mount/point

```
but I still get
```

$ ls -ld /mount/point/
dr-xr-xr-x 1 user user 0 Jan  5 20:54
$ echo blubb > /mount/point/test.txt
bash: /mount/point/test.txt: Permission denied

```

I did the chmod and chown "tricks" (e.g. [other UF thread]("http://ubuntuforums.org/showthread.php?t=509500")) before (which doesn't make sense to me anyway) and after (which shouldn't be necessary) mounting sudoed. Unfortunatelly there is no umask= option for vboxsf type mount since that's the only thing that sounds like it could matter, still.

Though, I have found others with the same problem in [virtualbox forum]("http://forums.virtualbox.org/viewtopic.php?p=12147") and elsewhere. This to me seams Ubuntu specific because the way Ubuntu handles "user mounts"; from vbox help:

> 
The generic mount options (documented in the mount manual page) apply 
also. Especially useful are the options uid, gid and mode, as they 
allow access by normal users (in read/write mode, depending on the 
settings) even if root has mounted the filesystem.


Does anyone else see any options or what I did wrong? It would really be anoing if I had to always use sudo to write to the windows share folder! Thanks heaps in advance!

Cheers,
kakao.

---

### Post by jshanks on 2008-01-29
This is working for me:

sudo mount -t vboxsf sharename /home/username/mountpoint -o rw,exec,uid=1000,gid=1000,dev

It works with both Fedora and Ubuntu clients.

---


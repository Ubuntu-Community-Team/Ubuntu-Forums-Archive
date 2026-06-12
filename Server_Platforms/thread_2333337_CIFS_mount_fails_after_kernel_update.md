---
title: "CIFS mount fails after kernel update"
date: 2016-08-09
forum: Server Platforms
---

### Post by calzone2 on 2016-08-09
Hi,

I'm running multiple Ubuntu Servers which mounts a SMB share on a Windows Server 2010R2. The share is not password protected. This has been working flawlessly until a recent kernel update.

I use the following mount string in /etc/fstab:
```
//myserver/myshare    /media/folder     cifs    iocharset=utf8,guest        0       0
```

Since the kernel update I receive the following error message when trying to mount (sudo mount -a):
```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```
After some testing, researsching and installing older kernels I found out which kernels work and which don't. I have servers running both Ubuntu 15.10 and 16.04, both have the same problem.
16:04:
GNU/Linux 4.4.0-22-generic x86_64    Working
GNU/Linux 4.4.0-24-generic x86_64    Working
GNU/Linux 4.4.0-28-generic x86_64    Not working
GNU/Linux 4.4.0-31-generic x86_64    Not working
GNU/Linux 4.4.0-38-generic x86_64    Not working

15:10:
GNU/Linux 4.2.0-41-generic x86_64    Working
GNU/Linux 4.2.0-42-generic x86_64    Not working



Any one seen this or have any workaround? Should I report this as a bug?

---

### Post by howefield on 2016-08-09
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by calzone2 on 2016-09-23
I managed to solve this by replacing "guest" with "username=guest,password=" in fstab configuration. My fstab now looks like:
```
[COLOR=#000000][FONT=&amp]//myserver/myshare    /media/folder     cifs    iocharset=utf8,username=guest,password=        0       0[/FONT][/COLOR]
```

---


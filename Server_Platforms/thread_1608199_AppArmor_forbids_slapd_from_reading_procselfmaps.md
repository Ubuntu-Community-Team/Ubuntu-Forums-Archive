---
title: "AppArmor forbids slapd from reading /proc/self/maps"
date: 2010-10-28
forum: Server Platforms
---

### Post by nutznboltz on 2010-10-28
On Ubuntu Hardy amd64 (x86_64) my slapd repeatedly dies after printing a log message like this:

```
2010-09-28T16:41:23-04:00 molybdenum kernel 05 [kern.notice] kernel: [15908266.232011]
 audit(1285706483.638:69): type=1503 operation="inode_permission" requested_mask="::r"
 denied_mask="::r" name="/proc/22022/maps" pid=22038 profile="/usr/sbin/slapd"
 namespace="default"
```


Why does slapd even want to read /proc/self/maps at all?

Searching through the OpenLDAP source code does not show "proc/.*/maps", however that pattern is found in two of the shared libraries that slapd is linked with:
/lib/libpthread.so.0
/lib/libc.so.6

In both cases the string is really proc/self/maps.

Both of those are in the libc6 package.  After a lot of hair-pulling I managed to figure out how to get the source code to that. See
[http://ubuntuforums.org/showthread.php?t=1608117](http://ubuntuforums.org/showthread.php?t=1608117)

Now looking for where libc6 uses "proc/self/maps"
```

-*- mode: grep; default-directory: "~/src/libc6/glibc-2.7/build-tree/glibc-2.7/" -*-
Grep started at Thu Oct 28 17:34:54

find . -type f -print0 | xargs -0 -e grep -nH -e proc/self/maps
./nptl/pthread_getattr_np.c:76:  /proc/self/maps and locate the line into which
./nptl/pthread_getattr_np.c:78:      FILE *fp = fopen ("/proc/self/maps", "rc");
./debug/segfault.c:123:  int mapfd = open ("/proc/self/maps", O_RDONLY);
./sysdeps/unix/sysv/linux/libc_fatal.c:159:           int fd2 = open_not_cancel_2 ("/proc/self/maps", O_RDONLY);
./sysdeps/unix/sysv/linux/readonly-area.c:35:  FILE *fp = fopen ("/proc/self/maps", "rc");
./linuxthreads/attr.c:424:       /proc/self/maps and locate the line into which
./linuxthreads/attr.c:426:      FILE *fp = fopen ("/proc/self/maps", "rc");

```

The first grep hit is in function with documentation that's a puzzle to find:
pthread_getattr_np()

Even with manualpages-dev and glibc-doc packages installed there's still no output from "man pthread_getattr_np".

This online manual page exists though:

[http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_getattr_np.3.html](http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_getattr_np.3.html)

I'm still drilling with apt-file for the one that comes with Ubuntu Hardy (if any exists.)

---

### Post by nutznboltz on 2010-10-28
No joy.

```
sudo apt-file update
apt-file find pthread_getattr_np
```

reports nothing.

Now searching to see if there is any evidence that the pthread_getattr_np() function is even used.

---

### Post by nutznboltz on 2010-10-28
Probably not, it only appears in libpthread.so itself
```

$ ldd /usr/sbin/slapd | awk '{print $3}' | grep / | while read lib; do echo $lib; strings - $lib | grep pthread_getattr_np; done
/usr/lib/libldap_r-2.4.so.2
/usr/lib/liblber-2.4.so.2
/usr/lib/libdb-4.2.so
/usr/lib/libodbc.so.1
/usr/lib/libslp.so.1
/usr/lib/libsasl2.so.2
/usr/lib/libgnutls.so.13
/lib/libcrypt.so.1
/lib/libresolv.so.2
/usr/lib/libltdl.so.3
/lib/libwrap.so.0
/lib/libpthread.so.0
pthread_getattr_np
pthread_getattr_np.c
pthread_getattr_np
pthread_getattr_np
/lib/libc.so.6
/lib/libnsl.so.1
/lib/libdl.so.2
/usr/lib/libtasn1.so.3
/usr/lib/libz.so.1
/lib/libgcrypt.so.11
/lib/libgpg-error.so.0
```

---

### Post by nutznboltz on 2010-10-28
The other case appears to be that slapd SEGFAULTed and the catch_segfault() handler attempted to read from /proc/self/maps only to have AppArmor deny the request.

---

### Post by nutznboltz on 2010-10-29
So where to take this from here?

[LIST=1]
[*]Write a test case that tries to catch a segfault in an AppArmor restricted environment.
[*]Test on new versions of Ubuntu.
[/LIST]

---

### Post by nutznboltz on 2010-10-29
Well, good old catch_segfault() is still reading from /proc/self/maps in eglibc-2.12.1 on Maverick.  Some things never change. :)

So now to poke through AppArmor source to see if there are exceptions for /proc/self/maps and look at the Maverick OpenLDAP AppArmor profile for exceptions too.

---

### Post by nutznboltz on 2010-10-29
Seems this issue has been dealt with post-Hardy.

/etc/apparmor.d/abstractions/base contains:

```
  # glibc's *printf protections read the maps file
  @{PROC}/*/maps                 r,

```

Hardy does not have that.

So an SRU is required.

---

### Post by nutznboltz on 2010-10-29
An attempt a requesting an SRU:
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/668479](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/668479)

A procedure which has documentation only people who don't need the documentation can understand:
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---


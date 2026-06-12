---
title: "rsync -zhhP of umpc jaunty-live-i386.img does not work"
date: 2008-12-31
forum: Ubuntu Dev Link Forum
---

### Post by TDFlanders on 2008-12-31
Hi, am I using rsync in the wrong way or should I file a bug against this?

Thanks,

Thomas

thomas@thomas-laptop:~$ lsb_release -rd ; uname -a ; apt-cache policy linux rsync ; date ; rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/jaunty-desktop-i386.iso ./Desktop/rsync ; rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily/current/jaunty-alternate-i386.iso ./Desktop/rsync ; rsync -zhhP rsync://cdimage.ubuntu.com/ubuntu-umpc/daily-live/current/jaunty-live-i386.img ./Desktop/rsync ; date
Description:	Ubuntu jaunty (development branch)
Release:	9.04
Linux thomas-laptop 2.6.28-4-generic #5-Ubuntu SMP Fri Dec 26 22:48:51 UTC 2008 i686 GNU/Linux
linux:
  Installed: 2.6.28.4.4
  Candidate: 2.6.28.4.4
  Version table:
 *** 2.6.28.4.4 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
        100 /var/lib/dpkg/status
rsync:
  Installed: 3.0.4-3ubuntu1
  Candidate: 3.0.4-3ubuntu1
  Version table:
 *** 3.0.4-3ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status
Thu Jan  1 00:07:47 GMT 2009
jaunty-desktop-i386.iso
     691.51M 100%   13.75MB/s    0:00:50 (xfer#1, to-check=0/1)

sent 184.27K bytes  received 124 bytes  826.31 bytes/sec
total size is 691.51M  speedup is 3840.34
jaunty-alternate-i386.iso
     695.13M 100%   13.90MB/s    0:00:50 (xfer#1, to-check=0/1)

sent 184.73K bytes  received 126 bytes  1.31K bytes/sec
total size is 695.13M  speedup is 3850.61
@ERROR: Unknown module 'ubuntu-umpc'
rsync error: error starting client-server protocol (code 5) at main.c(1522) [receiver=3.0.4]
Thu Jan  1 00:14:05 GMT 2009
thomas@thomas-laptop:~$ ls -la ~/Desktop/rsync
total 2711116
drwxr-xr-x  2 thomas thomas      4096 2009-01-01 00:13 .
drwxr-xr-x 13 thomas thomas      4096 2008-12-31 07:57 ..
-rwxrwxrwx  1 thomas thomas 728897536 2009-01-01 00:13 jaunty-alternate-i386.iso
-rwx------  1 thomas thomas   1048576 2008-12-22 15:22 .jaunty-alternate-i386.iso.1t3TPT
-rw-r--r--  1 thomas thomas 725102592 2009-01-01 00:11 jaunty-desktop-i386.iso
-rw-------  1 root   root   525336576 2008-12-18 22:07 .jaunty-desktop-i386.iso.5QjjfO
-rw-------  1 thomas thomas 793051136 2008-12-29 08:37 jaunty-live-i386.img
thomas@thomas-laptop:~$

---

### Post by TDFlanders on 2008-12-31
Hi,

cleaned up the folder. It is not a permission nor an ownership issue.

Cheers,

Thomas

thomas@thomas-laptop:~$ date ; lsb_release -rd ; uname -a ; apt-cache policy linux rsync ; rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/jaunty-desktop-i386.iso ./Desktop/rsync ; rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily/current/jaunty-alternate-i386.iso ./Desktop/rsync ; rsync -zhhP rsync://cdimage.ubuntu.com/ubuntu-umpc/daily-live/current/jaunty-live-i386.img ./Desktop/rsync ; ls -la ~/Desktop/rsync ; date
Thu Jan  1 00:26:47 GMT 2009
Description:	Ubuntu jaunty (development branch)
Release:	9.04
Linux thomas-laptop 2.6.28-4-generic #5-Ubuntu SMP Fri Dec 26 22:48:51 UTC 2008 i686 GNU/Linux
linux:
  Installed: 2.6.28.4.4
  Candidate: 2.6.28.4.4
  Version table:
 *** 2.6.28.4.4 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
        100 /var/lib/dpkg/status
rsync:
  Installed: 3.0.4-3ubuntu1
  Candidate: 3.0.4-3ubuntu1
  Version table:
 *** 3.0.4-3ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status
jaunty-desktop-i386.iso
     691.51M 100%   10.48MB/s    0:01:05 (xfer#1, to-check=0/1)

sent 184.27K bytes  received 124 bytes  1.13K bytes/sec
total size is 691.51M  speedup is 3840.34
jaunty-alternate-i386.iso
     695.13M 100%   11.16MB/s    0:01:02 (xfer#1, to-check=0/1)

sent 184.73K bytes  received 126 bytes  1.23K bytes/sec
total size is 695.13M  speedup is 3850.61
@ERROR: Unknown module 'ubuntu-umpc'
rsync error: error starting client-server protocol (code 5) at main.c(1522) [receiver=3.0.4]
total 2196556
drwxrwxrwx  2 thomas thomas      4096 2009-01-01 00:31 .
drwxr-xr-x 13 thomas thomas      4096 2008-12-31 07:57 ..
-rwxrwxrwx  1 thomas thomas 728897536 2009-01-01 00:31 jaunty-alternate-i386.iso
-rwxrwxrwx  1 thomas thomas 725102592 2009-01-01 00:29 jaunty-desktop-i386.iso
-rwxrwxrwx  1 thomas thomas 793051136 2008-12-29 08:37 jaunty-live-i386.img
Thu Jan  1 00:32:08 GMT 2009
thomas@thomas-laptop:~$

---


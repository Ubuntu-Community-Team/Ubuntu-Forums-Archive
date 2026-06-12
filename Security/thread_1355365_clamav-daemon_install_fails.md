---
title: "clamav-daemon install fails"
date: 2009-12-14
forum: Security
---

### Post by dgermann on 2009-12-14
Hi--

In a server running 2.6.24-26-server #1 SMP Tue Dec 1 19:19:20 UTC 2009 i686 GNU/Linux, when I try to install clamav-daemon I get this error message: 
```
Unpacking clamav-daemon (from .../clamav-daemon_0.95.3+dfsg-1ubuntu0.09.04~hardy2_i386.deb) ...
Setting up clamav-daemon (0.95.3+dfsg-1ubuntu0.09.04~hardy2) ...
Replacement succeeded for "/usr/sbin/clamd".
 * Starting ClamAV daemon clamd                                                     [fail] 

```

I had a sources.list that gave me version 0.94.2, and I changed my sources list and re-ran sudo apt-get install clamav-daemon. That's what first produced this error.

I have since tried purging clamav-daemon and installing again, with same error resulting.

Here are some other things I have tried:
```
sudo clamd start
ERROR: initgroups() failed.

doug@bak:~$ clamd -V
ClamAV 0.95.3/10172/Mon Dec 14 17:53:58 2009
doug@bak:~$ clamscan -V
ClamAV 0.95.3/10172/Mon Dec 14 17:53:58 2009

```

I have clamav-daemon running on two other 8.04.1 machines, which are desktops, and not running the server version.

Any ideas?

Thanks!

PS this is a headless box and I am accessing it via ssh.

---

### Post by archolman on 2011-09-16
[SIZE=3]I have the same problem:
> 
~$ sudo clamd
ERROR: initgroups() failed.


[/SIZE][SIZE=3]10.04.2 on an [/SIZE][SIZE=3]Acer TravelMate 2413LM 
[/SIZE]

---

### Post by ubudog on 2011-09-16
> **archolman said:**
> [SIZE=3]I have the same problem:


[/SIZE][SIZE=3]10.04.2 on an [/SIZE][SIZE=3]Acer TravelMate 2413LM 
[/SIZE]

Hi, please start a new thread.

Edit: New thread:
[http://ubuntuforums.org/showthread.php?t=1845297](http://ubuntuforums.org/showthread.php?t=1845297)

---


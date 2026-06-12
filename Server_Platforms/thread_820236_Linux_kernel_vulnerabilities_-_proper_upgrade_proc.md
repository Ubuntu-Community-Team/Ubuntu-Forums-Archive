---
title: "Linux kernel vulnerabilities - proper upgrade procedure"
date: 2008-06-06
forum: Server Platforms
---

### Post by osjak on 2008-06-06
Hi folks,

I'm running a web server, don't have physical access to it. I have never done a kernel upgrade before and now it's time due to:
[http://ubuntuforums.org/showthread.php?t=817407](http://ubuntuforums.org/showthread.php?t=817407)

I did the usual stuff:

```
$sudo apt-get update
$sudo apt-get upgrade
```

It upgraded *linux* package and a bunch of others. I followed up with a server reboot.

Now, what's supposed to be a kernel version after this update? 

```
admin@www1:~$ uname -a
Linux www1.xxxxxx.com 2.6.15-51-server #1 SMP Tue Feb 12 17:12:18 UTC 2008 i686 GNU/Linux
```

Isn't it supposed to be 2.6.24-18? If so, what did I do wrong?

---

### Post by colo on 2008-06-06
The .24 Kernel series is featured in Ubuntu 8.04 (Hardy) only. Your release will continue to be supported with .15-kernel images with security fixes backported to this build.

Exec summary: everything in order, you did fine. :)

---

### Post by osjak on 2008-06-06
Whoo-hoo, I did something right! \\:D/
Thank you colo!!!

---


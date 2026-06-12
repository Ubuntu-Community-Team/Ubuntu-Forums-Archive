---
title: "Run Program on System Startup"
date: 2009-08-28
forum: Server Platforms
---

### Post by SoulMazer on 2009-08-28
Hi, I'm running a headless Ubuntu 9.04 server. I have written a small little Python program that I would like to run at machine startup. Initially, I just thought I would add it to my /etc/init.d/ directory and "chmod 755" it. This did not work, as a "ps | grep python" after a reboot found nothing.

So...I could have sworn I was doing everything correctly but I must not be. What can I do?

Thanks in advance.

---

### Post by rybl on 2009-08-28
Assuming you are in runlevel 2 try putting the script in the /etc/rc2.d/ directory.  It will need to be executable and be named like the other files in the directory.  Start with an S then a two digit number then the script name.  For example "S99MyScript".  The two digit number determines when it runs (lower is earlier).

Alternatively, you could just put this line in /etc/rc.local

```
/usr/bin/python /path/to/script/script_name.py
```

The rc.local file is executed at the end of every multi-user boot.

---

### Post by SoulMazer on 2009-08-28
Ok, putting the script name in /etc/rc.local did the trick.

For my future knowledge, runlevel 3 is text-only, correct?

Thanks again.

---

### Post by rybl on 2009-08-29
Debian based distrobutions do not make any distinction between runlevels 2-5, but traditionaly runlevel 3 would be multiuser with networking.  You can read more about it [here]("http://en.wikipedia.org/wiki/Runlevel#Typical_Linux_runlevels").

Ubuntu doesn't actually use sysvinit for startup, it uses upstart.  sysvinit scripts still work however so all the rc stuff will run fine.

---


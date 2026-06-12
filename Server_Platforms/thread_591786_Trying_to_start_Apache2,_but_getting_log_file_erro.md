---
title: "Trying to start Apache2, but getting log file error"
date: 2007-10-25
forum: Server Platforms
---

### Post by trymbill on 2007-10-25
I've been using Apache2 on my Ubuntu now for about a week.  Everything has been working fine, I've set it up so that it can talk to my Win2k3 server also and everything is going great, until this morning.

Now, it looked like my Apache was hanging because I couldn't open any websites on my server.  So I tried to force-reload it and then I got this error:

```

 * Starting web server (apache2)...                                                                                                                          (30)Read-only file system: apache2: could not open error log file /var/log/apache2/error.log.
Unable to open logs
```

It also happens when I try to just do a regular "start" or "restart" ...

I've tried to delete the log file /error.log but that doesn't work either.  I used this command:

```
sudo rm -f /var/log/apache2/error.log
rm: cannot remove `/var/log/apache2/error.log': Read-only file system
```

I also tried to chmod the error.log file, but that didn't work either:

```
sudo chmod 0777 /var/log/apache2/error.log
chmod: changing permissions of `/var/log/apache2/error.log': Read-only file system
```

Can some one explain to me what it is I'm doing wrong?

Thanks a lot in advance,
Magnus

---

### Post by whit on 2007-10-25
That's saying that the drive you're trying to write your logs to is mounted read only. It's not an Apache problem. Did your system boot up go normally? Were you remounting any partitions? I'd reboot the system and see if the problem's still there, or if any interesting error messages come up.

---

### Post by MJN on 2007-10-26
Agreed. If you take a look in /etc/fstab you will likely see that the partition that /var/log resides on (most likely the one mounted as /) has an option set to mount as read only in case of a significant error. This minimise data loss whilst allowing you to investigate, and possibly fix, what's wrong.
 
Check your logs (/var/log/syslog and the output of dmesg) and look for anything regarding your disks/partitions. I would do this sooner rather than later as whilst a reboot may appear to get you back on the road you really could do with finding out (before the logs disappear) why it went belly up in the first place.
 
Mathew

---

### Post by trymbill on 2007-10-26
Thanks guys.  I'm going to check it out when I get back home tonight :)

---


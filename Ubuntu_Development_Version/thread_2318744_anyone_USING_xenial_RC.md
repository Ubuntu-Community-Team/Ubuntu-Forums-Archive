---
title: "anyone USING xenial RC?"
date: 2016-03-28
forum: Ubuntu Development Version
---

### Post by Skaperen on 2016-03-28
i'm curious if anyone is actually *using* a 16.04 RC desktop.  is _upstart_ working OK?

---

### Post by vasa1 on 2016-03-28
By "RC" do you mean *release candidate*? AFAIK, there isn't one yet.

See [https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule)

---

### Post by bcschmerker on 2016-03-29
**Not yet.**  I'm already running Ubuntu® 16.03b2 as of 28 March 2016, but 16.04rc is not due out until [s]25[/s] *14* April.

---

### Post by Bucky Ball on 2016-03-29
> **bcschmerker said:**
> 16.04rc is not due out until 25 April.

Interesting. Four days after 16.04's final release!

Think you're reading [the schedule]("https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule") wrong and quoting the weeks in the far left column rather than the date in the column to the immediate right of that. April 14 for the RC. Final release April 21. :)

---

### Post by VMC on 2016-03-29
The Mar 24th installed ubuntu-mate installed  doesn't show any Upstart activity:
```
$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                  229-3ubuntu1                               amd64        system and service manager - PAM module
ii  libsystemd0:amd64                     229-3ubuntu1                               amd64        systemd utility library
ii  python3-systemd                       231-2build1                                amd64        Python 3 bindings for systemd
ii  systemd                               229-3ubuntu1                               amd64        system and service manager
ii  systemd-sysv                          229-3ubuntu1                               amd64        system and service manager - SysV links

$ dpkg -l|grep **upstart**
$ 
```

Also "/usr/lib/systemd" is present whereas Upstart isn't.

---

### Post by prusswan on 2016-03-29
upstart has been replaced by systemd as a default (except for official packages, existing scripts are not updated as far as I can tell)

---

### Post by grahammechanical on 2016-03-29
I believe that Ubuntu switched to systemd during the 15.10 development cycle. We got an Advanced option at Grub to load with upstart if we wished. I have not noticed if that upstart option is still there in 16.04. There is still upstart code in 16.04. I see it getting updated from time to time. It is just that a default install does not use upstart.

Regards.

---


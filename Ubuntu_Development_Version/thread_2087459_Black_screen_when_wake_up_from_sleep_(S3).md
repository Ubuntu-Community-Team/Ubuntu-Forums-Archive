---
title: "Black screen when wake up from sleep (S3)"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2012-11-23
I have an Asus laptop and Raring was working ok... some weeks ago.
After some updates I get an black screen when it wake up.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1082314](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1082314)

---

### Post by serdotlinecho on 2012-11-25
Same with me but on samsung netbook. After wake up from sleep, just black screen. I can't go to tty shell, magic sysrq also not working. Nothing, but just black screen,  I have to force poweroff, i'm afraid to "sleep" again :(

---

### Post by anca-emanuel on 2012-11-28
For now I suspect [https://launchpad.net/~robert-ancell](https://launchpad.net/~robert-ancell)

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor)

---

### Post by zika on 2012-11-28
I've "solved" that with```
apm=off
```in kernel line, until it get(s) fixed...

---

### Post by anca-emanuel on 2012-11-28
If this bug affects you, click on "affects me too"
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1082314/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1082314/+affectsmetoo)

---

### Post by zika on 2012-11-28
> **anca-emanuel said:**
> If this bug affects you, click on "affects me too"
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1082314/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1082314/+affectsmetoo)[https://www.youtube.com/watch?v=4e9CkhBb18E](https://www.youtube.com/watch?v=4e9CkhBb18E)
I thought I've already clicked "affects me too" for a bug for this... Who knows...

---

### Post by anca-emanuel on 2012-12-03
> **anca-emanuel said:**
> For now I suspect [https://launchpad.net/~robert-ancell](https://launchpad.net/~robert-ancell)

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor)

When I connect an second monitor, my laptop screen is working !
Updated bug report.
:guitar:

---

### Post by anca-emanuel on 2012-12-09
After the latest updates I no longer need to plug an external monitor to wake up normal like I did in Precise. The details are in bug report.

---

### Post by serdotlinecho on 2012-12-10
> After the latest updates I no longer need to plug an external monitor to wake up normal like I did in Precise. The details are in bug report.

Same here with current daily build raring ringtail. Wake up from sleep...asking for my password :D

```
~$ apt-cache policy unity compiz linux-image-generic linux-headers-generic
unity:
  Installed: 6.12.0daily12.12.05-0ubuntu1
  Candidate: 6.12.0daily12.12.05-0ubuntu1
  Version table:
 *** 6.12.0daily12.12.05-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
compiz:
  Installed: 1:0.9.9~daily12.12.05-0ubuntu2
  Candidate: 1:0.9.9~daily12.12.05-0ubuntu2
  Version table:
 *** 1:0.9.9~daily12.12.05-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
linux-image-generic:
  Installed: 3.7.0.5.9
  Candidate: 3.7.0.5.9
  Version table:
 *** 3.7.0.5.9 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
linux-headers-generic:
  Installed: 3.7.0.5.9
  Candidate: 3.7.0.5.9
  Version table:
 *** 3.7.0.5.9 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
xserver-xorg:
  Installed: 1:7.7+1ubuntu4
  Candidate: 1:7.7+1ubuntu4
  Version table:
 *** 1:7.7+1ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
xserver-xorg-video-intel:
  Installed: 2:2.20.14-0ubuntu1
  Candidate: 2:2.20.14-0ubuntu1
  Version table:
 *** 2:2.20.14-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
```

---


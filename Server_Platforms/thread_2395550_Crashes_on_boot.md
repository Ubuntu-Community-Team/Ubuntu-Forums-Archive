---
title: "Crashes on boot"
date: 2018-07-03
forum: Server Platforms
---

### Post by geohei on 2018-07-03
Hi.

I urgently need help with this here!

4 years old server.
Ubuntu 14.04 server i686.
Linux 3.13.0-149-generic was the last version to run flawlessly.
10 days ago, I upgraded to 3.13.0.151.
Server crashes then on boot.

Screen shows ...

```
Loading Linux 3.13.0-151-generic ...
Loading initial ramdisk ...
```

1 second later ... reboot.

Same with 3.13.0-151 recovery mode.
Same with 3.13.0-153 (most recent as of today).

_How can I find out_, after subsequent successful 3.13.0-149 bootup, _what exactly generates the crash_?

Thanks!

Neither this forum, nor Google could help.

---

### Post by malbo on 2018-07-06
Hello,
This bug : [https://bugs.launchpad.net/ubuntu/+source/amd64-microcode/+bug/1779092](https://bugs.launchpad.net/ubuntu/+source/amd64-microcode/+bug/1779092)

---

### Post by geohei on 2018-07-06
Correct!
[Boot fails with &#8220;Loading initial ramdisk &#8230;&#8221;/1052651#1052651]("https://askubuntu.com/questions/1052231/boot-fails-with-loading-initial-ramdisk/1052651#1052651")

... and fixed today!

---


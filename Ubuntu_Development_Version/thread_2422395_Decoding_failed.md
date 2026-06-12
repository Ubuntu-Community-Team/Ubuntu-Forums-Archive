---
title: "Decoding failed"
date: 2019-07-06
forum: Ubuntu Development Version
---

### Post by VMC on 2019-07-06
The latest Ubuntu ISO, after installation, I get "Initramfs unpacking failed: Decoding failed", on bootup.
Searching was nonexistent . I installed it twice, same result. Not sure if virtual install would have same issue.

Not going to report at the moment. Wait a day or two, as my last error was also cleared up.

But if someone has installed today's (7/6) ISO, remove quiet & splash at end of linux line and see if you get same message.

edit: I noticed at the end of the second install I got the message just before it stated reboot. Ubiquity normally takes a moment or two to install kernel and initram. It was way to fast.

---

### Post by VMC on 2019-07-07
If I change "update-initramfs" compression from *lz* to *gzip*, then it no longer fails.

[report]("https://bugs.launchpad.net/ubuntu/+bug/1835660")

---

### Post by VMC on 2019-07-11
As of todays' ISO installed (7/11), problem solved. I'll wait a couple more days to be sure before marking topic SOLVED.

---

### Post by P-I H on 2020-01-17
There is a bug report on this issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660)
I get this error on a triple boot system with Ubuntu 20.04, Windows 10 and Fedora 31, when I boot using the Fedora disk and select Ubuntu from Fedora's boot menu. When I boot using the Ubuntu disk, I don't get the message.

---

### Post by picode on 2020-02-14
> **VMC said:**
> If I change "update-initramfs" compression from *lz* to *gzip*, then it no longer fails.


I'm a complete newbie to Linux and I have no idea how to do what you said to do.
I managed to get to the TTY, but no idea what to do from there...

---

### Post by VMC on 2020-02-15
> **picode said:**
> I'm a complete newbie to Linux and I have no idea how to do what you said to do.
I managed to get to the TTY, but no idea what to do from there...
Go to my bug report above and read post#11

---


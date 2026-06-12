---
title: "skype, viber, falkon prermission denied error noble development"
date: 2024-01-03
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-01-03
Hello,

checking the packages in question I report the following:
For skype there is no deb file any more from skype website, just snap one. All of them, when trying to open them I'm getting a similar error:

viber:
[42233:42233:0104/024005.979079:FATAL:credentials.cc(126)] Check failed: . : Permission denied (13)
Trace/breakpoint trap (core dumped)

skype:
It was complaining as well, mentioning something about root. I tried to open skype (deb package) as root and then as regular user. The error vanished, yet skype does not launch.

falkon:
QSocketNotifier: Can only be used with threads started with QThread
[42359:42359:0104/024213.003981:FATAL:credentials.cc(125)] Check failed: . : Permission denied (13)
Trace/breakpoint trap (core dumped)

Unfortunately, when trying to report the errors that show up, I get a bag gateway or similar error. For falkon I created this bug report:
[https://bugs.launchpad.net/ubuntu/+source/falkon/+bug/2047986](https://bugs.launchpad.net/ubuntu/+source/falkon/+bug/2047986)

I also mention that blender, which now in noble is > 4.0 version, does not launch, since it requests a graphics card that is less than 10 years old.

Regards!

---

### Post by Claus7 on 2024-03-17
Hello,

I'm no longer facing this issue, so problem solved.

Regards!

---


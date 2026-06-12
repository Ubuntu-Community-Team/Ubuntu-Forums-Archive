---
title: "[SOLVED] Ubuntu Server Edition 8.04 as Virtual Box guest"
date: 2008-05-30
forum: Virtualisation
---

### Post by hrp2171 on 2008-05-30
Hello,

I've searched through this forum for a while but could not find a post title or a thread that touches on the issue I'm experiencing. So, here is my starting post.

Background:
Host: Windows XP Professional SP2
Guest: Ubuntu Server Edition 8.04LTS i386
VM program: Sun xVM VirtualBox 1.6.0

The installation went very well, but upon first boot, I get the following message:

This kernel requires the following features not present on the CPU: 0:6
Unable to boot - please use a kernel appropriate for your CPU.

I have also googled the error message but only one result was related.  Even then, there was no solution and it seems to be some kind of bug with VirtualBox-anyversion and Ubuntu Server Edition 8.04LTS as guest.

Has anyone else ran into this issue? Were you able to resolve it? What was your workaround?

Thank you so much.

Hector
:guitar:

---

### Post by bluefrog on 2008-05-30
machine settings/advanced tab/ Enable PAE

---

### Post by tighem on 2008-05-30
Sun even mentions it in their docs. Guess they really did support and test Ubuntu 8.04 before shipping 1.6!

---

### Post by hrp2171 on 2008-05-30
You guys ROCK!!! Thanks.

I should not have ***-u-me-d. :lolflag:

---


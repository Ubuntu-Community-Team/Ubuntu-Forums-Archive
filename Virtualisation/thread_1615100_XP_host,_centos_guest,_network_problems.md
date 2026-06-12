---
title: "XP host, centos guest, network problems"
date: 2010-11-06
forum: Virtualisation
---

### Post by samlabs821 on 2010-11-06
> **CharlesA said:**
> Be sure to use bridged networking if you want to access services running on the VM.

Hi, I have the similar problem. I am using windows xp on my host machine, and installed centos to my virtualbox.

I am using bridged networking.
this is addresses:

host:
192.168.120.50
255.255.255.0
192.168.120.1

*vm:*
192.168.1.2
255.255.255.0

on my *vm* there is running apache, how can I open website which is running on *vm* from my host machine?

---

### Post by CharlesA on 2010-11-06
They are on different subnets, so it would be complicated to access that machine from the host without jumping thru hoops.

---

### Post by arrrghhh on 2010-11-06
samlabs821 - we certainly can help, but I don't see anything to do with Ubuntu in your post...

---

### Post by CharlesA on 2010-11-06
Thread moved to ***Virtualization***, and title changed. Please don't hijack someone else's thread.

This has nothing to do with Ubuntu. Perhaps you should ask over on the virtualbox forums.

---


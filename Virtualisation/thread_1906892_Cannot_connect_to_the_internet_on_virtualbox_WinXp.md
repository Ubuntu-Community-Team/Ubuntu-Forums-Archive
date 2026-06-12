---
title: "Cannot connect to the internet on virtualbox WinXp guest (Ubuntu host)"
date: 2012-01-10
forum: Virtualisation
---

### Post by tkabir11 on 2012-01-10
Hi guys- I'm running a windows xp guest in virtualbox on ubuntu 11.10 host. I use a usb dongle to connect to the internet on the ubuntu host- and I want to use that same connection on the winxp guest in virtualbox- but I cannot connect. I have the guest additions installed in the vb guest OS. Any ideas what might be causing the problem and how I could connect?

Note: I didnt have this problem when I was running ubuntu in wubi---the vb guest os seemed to connect to the internet without me doing anything.

---

### Post by tkabir11 on 2012-01-10
Bump

---

### Post by jerrrys on 2012-01-10
VB guest-additions belong in the host and not the guest.

Did you install VB from there site or the software center?

---

### Post by tkabir11 on 2012-01-11
Its all good now- I just had to change the NAT adapter type in the VB network settings for the guest OS and now it's working :) Thanks anyways.

---

### Post by kapitanluffy on 2013-04-14
> **tkabir11 said:**
> Its all good now- I just had to change the NAT adapter type in the VB network settings for the guest OS and now it's working :) Thanks anyways.

what adapter type did you set it to?

---


---
title: "password protect access to NON-ubuntu partitions"
date: 2013-01-09
forum: Security
---

### Post by I_K on 2013-01-09
I have a dual boot ubuntu / windows. I want to password protect information exchange between partitions of ubuntu and windows. So that if ubuntu is hacked, information from windows partition will not suffer and vice versa.
For windows it is simple as windows can't read ext3 partitions, but when I log in
ubuntu I see windows partitions without mounting the in "Places"

So my question: how to password protect mounting of windows partitions in ubuntu. I would like to have to enter user/root password to access windows partitions.

P.S.
I use Ubuntu 10.04 LTS

---

### Post by Hungry Man on 2013-01-09
You don't need root to mount, so the only way to do this in any way that's even slightly effective is to encrypt the partition.

---

### Post by bodhi.zazen on 2013-01-09
> **Hungry Man said:**
> You don't need root to mount, so the only way to do this in any way that's even slightly effective is to encrypt the partition.

+1, Can't be done without encryption. If you do not use encryption, you can access the data with any live CD.

---

### Post by I_K on 2013-01-10
Hungry man, bodhi.zazen thank you for your replies.

---

### Post by Lfekey2 on 2013-01-10
You can use apparmor to block mount ntfs partitions. 
But it cannot protect you if they can access your hardware, or they get root.

---


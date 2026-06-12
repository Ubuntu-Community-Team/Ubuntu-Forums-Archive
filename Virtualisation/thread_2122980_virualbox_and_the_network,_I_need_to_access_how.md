---
title: "virualbox and the network, I need to access how?"
date: 2013-03-06
forum: Virtualisation
---

### Post by bghayad on 2013-03-06
I installed virualbox and I did installation from the iso image, the problem that when I start the instance, I can not ping it or ssh it. I tried too many settings in the network but all failed. 

I tried NAT, not attached, internal network, ... etc but no luck !

What is the solution to be able to access the instant from the same machine?

Regards
Bilal

---

### Post by coldraven on 2013-03-06
What OS is the host and what OS is the guest?

---

### Post by Cheesemill on 2013-03-07
If you want the VM to be on the same network as your host machine you need to use the bridged networking mode.

---


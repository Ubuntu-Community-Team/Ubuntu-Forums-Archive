---
title: "KVM without Virtualization Extensions"
date: 2014-06-26
forum: Virtualisation
---

### Post by kerryhall on 2014-06-26
Hi folks,

I have an old 64 bit machine that I want to use as a KVM host. The proc doesn't have virtualization extensions. I don't really care about performance, I would just like to be able to put this box to use. I want to be able to spin up virtual machines for testing, experimentation, etc.

So here's my question: is it possible to use KVM if my proc doesn't support virtualization extensions? (If so, I imagine I would just have to change one line in a config somewhere.)

Thanks!!

---

### Post by TheFu on 2014-06-28
No.

Use virtualbox or LXC or BSD jails.

---

### Post by houstonbofh on 2014-06-29
Kinda...  You can use libvirt and Qemu on the back end.  It is VERY slow.  Check Amazon for a processor you can plug in that has vxt.

---

### Post by kerryhall on 2014-06-30
I have a motherboard so laughably old that I don't even want to post what it is. Fine. It's a socket 939. Why let hardware go to waste? 

I'll go with LXC. 

Thanks folks!

---


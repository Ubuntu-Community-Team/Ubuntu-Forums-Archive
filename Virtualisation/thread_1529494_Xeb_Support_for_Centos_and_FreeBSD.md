---
title: "Xeb Support for Centos and FreeBSD?"
date: 2010-07-12
forum: Virtualisation
---

### Post by klabacita on 2010-07-12
Hi people.

 Just wondering, I have plans to run some vm with Xen, now I don't know  if I will use Centos 5.5 or Ubuntu as Host. I want to run as Guest:

 FreeBSD7/8 and Ubuntu 9/10.

Do u have this 2 OS as guest on production with Centos or Ubuntu as  Host?

Thanks!!!

---

### Post by sh1ny on 2010-07-12
You can't run xen on ubuntu host. You can run KVM with ubuntu host, and you can have BSD guests on it just fine.

---

### Post by klabacita on 2010-07-12
> You can't run xen on ubuntu host

What do u meant with this?

---

### Post by sh1ny on 2010-07-12
Means running Ubuntu as a dom0 xen ( host machine in which you run other virtual machines ) is **NOT** supported, and not possible.

---

### Post by klabacita on 2010-07-13
I'm new to ubuntu, them I can forget Ubuntu if I want to run Xen Dom-O.
 
Thanks for your info :o

---

### Post by sh1ny on 2010-07-13
Ubuntu uses KVM for virtualization, you can use that to run virtual machines instead of Xen.

---


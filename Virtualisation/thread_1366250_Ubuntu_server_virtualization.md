---
title: "Ubuntu server virtualization"
date: 2009-12-28
forum: Virtualisation
---

### Post by dobledosis on 2009-12-28
Hello everyone, I'm new to the forum. I wanted to register in the forum of [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/), but it seems that there is a bug, since i never get the confirmation email.

I need help with:

I have an intel i7 microprocessor that supports virtualization. I installed Windows 2008 server and VMware Server as the primary system, then ubuntu virtualized with 4 cpu. The problem is that I don`t get acceptable performance with the virtualized system. When the cpu consumption of the application i need to run is 50% on ubuntu, Windows 2008 server shows me less than 4% in whole system.

Now I want to try Ubuntu Server as the primary system.
 After installed:
Do I need to add any kind of driver to get the best performance of my i7?
Is there any virtualization on Ubuntu for me of acceptable performance?
Can I get the Linux-VServer better performance than the rest because it uses the same kernel?

Im new in the GNU Linux world, so i installed 2008 server because i want to step on firm ground. I have more windows knowledge, but I think I can try with Ubuntu.

 Thanks!

---

### Post by fouadatmeh on 2009-12-28
Hello,

I believe there still are issues with multiprocessor with virtualbox.. I have noticed that when running the guest with one processor it runs faster!..

---

### Post by dobledosis on 2009-12-28
I dnt have plans of using virtualbox, but thanks.

---

### Post by 32034 on 2009-12-28
> **dobledosis said:**
> I dnt have plans of using virtualbox, but thanks.

I switched from VMware to VirtualBox and have yet to regret making that decision.

---

### Post by fouadatmeh on 2009-12-28
I didn't notice u asked about vmware :(..

---

### Post by juancarlospaco on 2009-12-28
**Ubuntu-Minimal+KVM**

---


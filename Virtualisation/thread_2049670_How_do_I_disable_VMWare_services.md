---
title: "How do I disable VMWare services?"
date: 2012-08-29
forum: Virtualisation
---

### Post by wjbarber82 on 2012-08-29
Hi there, I've recently moved over from windows to Xubuntu and this is my first forum post (As usually everything I've needed to know has been right here! Excellent community I must say.)

I installed VMWare Workstation today and noticed that now, even when im not using vmware, a couple of related services are now loading at startup.

I've not noticed any degrading of performance from this, and despite my usual 'if it ain't broke don't fix it mentality' I've become accustomed already to not having things running that don't need to be. (One of the many reasons I moved over.)

Is there a way to make these services only load as needed, or perhaps make a little script to disable/enabled as required manually?

---

### Post by dino99 on 2012-08-29
[http://xubuntugeek.blogspot.fr/2011/12/add-application-to-xfcexubuntu-session.html](http://xubuntugeek.blogspot.fr/2011/12/add-application-to-xfcexubuntu-session.html)

---

### Post by wjbarber82 on 2012-08-29
Thanks for the reply, though that was actually the first place I checked.. I also made sure there was nothing in that 'local.rc' file... (I think thats what it was called) ... still no joy.

---

### Post by Elfy on 2012-08-29
*Thread moved to **Virtualization**.*

---

### Post by dcstar on 2012-08-30
> **wjbarber82 said:**
> Hi there, I've recently moved over from windows to Xubuntu and this is my first forum post (As usually everything I've needed to know has been right here! Excellent community I must say.)

I installed VMWare Workstation today and noticed that now, even when im not using vmware, a couple of related services are now loading at startup.

I've not noticed any degrading of performance from this, and despite my usual 'if it ain't broke don't fix it mentality' I've become accustomed already to not having things running that don't need to be. (One of the many reasons I moved over.)

Is there a way to make these services only load as needed, or perhaps make a little script to disable/enabled as required manually?

Installing VMware (or any VM system) involves deep hooking into the host OS so the VM system works when required.

It is pointless risk taking to try to play with any of these functions that impose a trivial impost on the host OS.

---


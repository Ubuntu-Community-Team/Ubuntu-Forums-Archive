---
title: "move virtual machine to hard drive?"
date: 2010-01-01
forum: Virtualisation
---

### Post by cenzorrll on 2010-01-01
hi, i was wondering if it was possible to build up a machine in virtualbox and when that's finished, copy the information to a hard drive as an actual system.

i'm wondering this because i experiment with all sorts of OS's and sometimes create a setup i really like, but as it's in a virtual machine i can't use it for my main OS. as short lived as it may be.  i know it's possible to virtualize a machine from an operating system already installed, but is it possible to do the reverse?

---

### Post by jocampo on 2010-01-02
I have not tested yet (in fact, was planning to do it soon) but I believe you can use "dd" command to extract or copy the partition info and create an iso or image. Then, dumped that onto the physical hard drive and recreate the machine from there.

---

### Post by jonest1 on 2010-01-02
Here's a page I found which may be helpful.

[http://chris-alex-thomas.com/blog/2009/03/17/migrate-virtualboxlinux-to-a-native-machine/](http://chris-alex-thomas.com/blog/2009/03/17/migrate-virtualboxlinux-to-a-native-machine/)

---

### Post by Cheesemill on 2010-01-02
Depends on the OS.
Linux = Yes
Windows= No

---


---
title: "Error at start"
date: 2014-09-28
forum: Virtualisation
---

### Post by Mr_Oreo on 2014-09-28
Hello all, im working on installing a virtual machine using the operative system Ubuntu i did everything like i did with my windows one but i keep getting this error at start, please help me :(
[COLOR=#000000]Here it is all the process that i make until the error: [/COLOR][https://www.youtube.com/watch?v=_NsY...QSPER2DqJbQ1aA]("https://www.youtube.com/watch?v=_NsYxeJjYIw&list=UUdFT-MBC3QSPER2DqJbQ1aA")

---

### Post by Vladlenin5000 on 2014-09-28
Hi, welcome.

Are your Virtualbox updated? If not please update it so we can troubleshoot from there.
Also make sure you're selecting the correct options if you're trying to do a normal installation process*.
There are VMs already made for VirtualBox, VMware, etc. for many linux distros, including Ubuntu, you can download and use right away.

* Creating a new VM by adding the installation CD/DVD ISO as a virtual drive and booting from it like you would do in a bare metal installation in a real machine.

---

### Post by Mr_Oreo on 2014-09-28
Yes its everything up-to-date, and i dont even get to installation process, i setup the VirtualBox, then i set it to the ubuntu .iso file, and when i launch it appear that.
How do i get that pre-made VMs?

---

### Post by Vladlenin5000 on 2014-09-28
I forgot to mention earlier your thread would be much better in the virtualisation section. Do NOT open a new thread, use the report post feature and request it. Meanwhile you should also edit your thread's title to reflect what's really going on; "error at start" could be anything.

What Ubuntu version? 32 or 64-bit?
And the host OS, 32 or 64-bit?
When creating a new VM have you selected the options according to the Ubuntu version?

---

### Post by howefield on 2014-09-28
Thread moved to the "*Virtualisation*" forum.

---

### Post by Mr_Oreo on 2014-09-28
They Ubuntu version that im using is the x32
And the host OS got the x32 and x64
Yup i did but my VirtualBox is only displayin the Ububtu x32 version, when i see guides on youtube its only Ubuntu, i dont know why my Visrtual Box is diferent if it is the last version

---

### Post by Mr_Oreo on 2014-09-28
Here it is all the process that i make until the error: [https://www.youtube.com/watch?v=_NsYxeJjYIw&list=UUdFT-MBC3QSPER2DqJbQ1aA](https://www.youtube.com/watch?v=_NsYxeJjYIw&list=UUdFT-MBC3QSPER2DqJbQ1aA)

---

### Post by Mr_Oreo on 2014-09-29
Someone?

---

### Post by ian-weisser on 2014-09-29
I've installed Ubuntu into VMs many times, and never had a kernel panic like that.
Are you sure your install media was good?
Did you do any unusual customizations?
Do you have any real or simulated hardware attached to the VM?

Personally, I would just reinstall the guest OS.
+1 to Vladlenin5000's suggestion: The thread title is ambiguous and unhelpful. Change it to something more descriptive.

---


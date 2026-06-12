---
title: "Android apps on Ubuntu?"
date: 2011-07-24
forum: Virtualisation
---

### Post by samigina on 2011-07-24
Hi, Android is linux, isnt?

Theres any way to run the android apps natively in Ubuntu?

---

### Post by Tylerjd on 2011-07-26
As an android developer:

Short Answer: No

Long Answer: No. The only way to run andorid apps on x86 (or amd64) architecture is to do one of the following:
[LIST]
[*]Grab the Android SDK. It includes an Android simulator that runs the full Andoid OS in a QEMU VM
[*]Grab [Android for x86]("http://www.android-x86.org/") and run stuff from there either natively or in an QEMU or VirtualBox VM
[/LIST]

But there is no way to run them natively. Android, while yes using the Linux kernel, it is a heavily modified version of the kernel, and they aren't compatible like you might think they are.

Sorry... [-(

---

### Post by samigina on 2011-07-27
Thank you for the answer ;)

---

### Post by llarsen on 2011-08-05
i havent tried it yet, but i was going to give it a shot later tonight. the Xen virtulization released an ARM processor virtualization source code. If i get it to work ill let you know

---


---
title: "Plans for the Next Linux Kernel Revealed"
date: 2007-02-12
forum: The Cafe
---

### Post by Rodneyck on 2007-02-12
**Plans for the Next Linux Kernel Revealed**

Matthew Broersma, Techworld.comMon Feb 12, 2:00 PM ET
Linux kernel maintainer Andrew Morton last week revealed some of his plans for the next kernel version, a few days after the final release of Linux 2.6.20.

Developers are currently revving up the development phase of the 2.6.21 kernel, with major additions planned for the next week or two, before beginning to lock down and stabilize the software.

In a message to the kernel developers mailing list, Morton gave an indication of some of the major new components that will go into 2.6.21. One change will be improvements to the KVM virtualization system, which made its debut in 2.6.20 along with an implementation of paravirtualization.

Another addition is an upgrade to the high-resolution kernel timers subsystem, which is designed to handle high-resolution and high-precision timer features that are beyond the standard timer subsystem. This is designed to allow for features that can, for instance, reduce power consumption by temporarily switching off the timer interrupt.

Morton said he would put other additions on hold for the time being, such as the reiser4 filesystem and readahead, a technique designed to improve file reading performance.
Among the several hundred patches Linus Torvalds has already integrated for the new kernel are those upgrading the ACPI subsystem, improving PlayStation 3 support and updating network and IDE drivers. ACPI is a standard for hardware recognition, motherboard and device configuration and power management.

Morton expressed some annoyance at the sluggishness with which patches were being handled by subsystem maintainers. "I'm getting fed up of holding onto hundreds of patches against subsystem trees, sending them over and over again and seeing nothing happen," he wrote.

[http://news.yahoo.com/s/pcworld/20070212/tc_pcworld/128937]("http://news.yahoo.com/s/pcworld/20070212/tc_pcworld/128937")

---

### Post by Choad on 2007-02-12
yay acpi

i have high hopes for feisty + my laptop

im setting myself up to be disapointed really

---

### Post by Hendrixski on 2007-02-12
I am continually impressed by those guys doing the Kernel maintenance.  It's really a huge task.  And I'm sure that making better paravirtualization isn't something that shows immediate rewards.  They have to wait for the technology that uses it to develop on Linux.  they have to be a step ahead of the demands of technology.

My hat is off to them.

---

### Post by Polygon on 2007-02-13
i hope with the acpi improvements they fix that sound is completely nonfunctional once i come out of suspend to ram / hibernate

of course, it will be a long while before we see these kernels inside of ubuntu, but hey its nice to know that its in development and be available soon :D

---

### Post by Quillz on 2007-02-13
Will the improved networking support be extended to Wi-Fi, as well? I'd like to see more NIC, especially those that use Atheros chipsets, supported out of the box, without needing to rely on third-party software like Madwifi.

---

### Post by macogw on 2007-02-13
Quillz, I'm using Feisty and since the first update after installing Herd 2 there is wifi roaming by default through the network manager applet.  I was, however, under the impression Feisty was going to end up with 2.6.20, not 2.6.21.

---


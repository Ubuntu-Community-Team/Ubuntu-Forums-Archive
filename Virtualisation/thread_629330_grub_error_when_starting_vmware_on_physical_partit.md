---
title: "grub error when starting vmware on physical partition"
date: 2007-12-02
forum: Virtualisation
---

### Post by askander on 2007-12-02
Hi, I've used this tutorial to virtualize a physical partition in vmware
[http://www.kriptopolis.org/virtualizar-una-particion-windows-ya-existente](http://www.kriptopolis.org/virtualizar-una-particion-windows-ya-existente) (is written in Spanish)

as a summary, I made a new hardwafre profile in windows, created a new virtual machine using vmware assistant, choosing the partitions where the boot is (partititon with ubuntu on it) and the partition with windows OS.

when I powered on the virtual machine, the grub menu appeared normally, but whenever I choose the windows option, it displays the following error
ERROR 13: INVALID OR UNSUPPORTED EXECUTABLE FORMAT

I also made some configurations to start with a floppy image, but when I'm typing the commands in the grub menu, the error appears again when I type
chainloader     +1

I'm using vmware server 1.0.4 and gutsy gibbon release, trying to virtualize Windows XP Professional SP2

any ideas? :(
thanks in advance.

---

### Post by MrGrey1 on 2008-07-24
Same problem as you, did you find a solution?

---


---
title: "todays tahir kernel panic after installing"
date: 2014-03-11
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-11
Says kernel panic no working init found

and a whole lot of stack traces

this PC is msi 7529 core2duo 4gb ram G31 chipset E6550 cpu 
AND it runs 13.10 fine. I am posting from it now.

---

### Post by Hreinsi on 2014-03-11
just install 3.13.0.17  kernel all fine.

---

### Post by sdowney717 on 2014-03-11
That is nice, on a Asus p5qc 14.04 e7400 cpu 64 bit is working fine.

This trusty on the msi is 64 bit, but should work being a core2duo.
I pulled the e6550 cpu out of the asus and it is in the msi board now.

---

### Post by sdowney717 on 2014-03-11
Took a picture of the screen
Any ideas?

---

### Post by sdowney717 on 2014-03-11
not syncing means grub error?
cant find the kernel, so grub is screwed up?

If so how to fix this?
There are three partitions inside an extended partition.

In extended partition sda2, Ubuntu 13.10 is in front of ubuntu 14.04 root system in front of 14.04 /home
I setup 14.04 with a separate /home.
a swap is at the end of sda2

sda1 is in front of sda2 and is currently empty being saved for windows.

going to try this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

that did not work, so I will wipe this disk and start over.

---


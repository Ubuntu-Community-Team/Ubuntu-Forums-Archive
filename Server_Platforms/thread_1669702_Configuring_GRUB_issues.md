---
title: "Configuring GRUB issues"
date: 2011-01-18
forum: Server Platforms
---

### Post by chrislynch8 on 2011-01-18
Hi,

I have a dev Server I installed 10.4LTS on it so I created three partitions

/dev/sda1 -> /boot
/dev/sda2 -> swap
/dev/sda3 -> /

I then created another partition to install another version of Ubuntu
/dev/sda4 -> /

Now when the server boots a GRUB menu appears but only with the option of select my install on /dev/sda4.

Two Questions

1: Can I have many installs use the same boot partition?
2: How do I configure GRUB so I can select the OS on /dev/sda3 or /dev/sda4

Rgds
Chris

---


---
title: "Command issue"
date: 2021-08-24
forum: Ubuntu Development Version
---

### Post by peter-1984 on 2021-08-24
Hi,
Please help to the following


peter@peter-VirtualBox:~$ sudo rcvboxadd setup
sudo: rcvboxadd: command not found

---

### Post by onflash on 2021-08-25
I just got these on an impish system by using the VitualBox VM menu item Devices > Insert Virtualbox Additions CD image...

From there ```
cd /media/`whoami`/VBox_GAs_6.1.26
./VBoxLinuxAdditions.run
```

It provided a notification that it required a build environment and to install gcc make perl, so I also ran ```
apt install gcc make perl
```

After that, ```
sudo rcvboxadd setup
``` built the kernel modules and updated the initramfs.  I rebooted to get the new modules as the output suggested and verified that Bidirectional copy/paste are working.

---

### Post by peter-1984 on 2021-08-25
Thanks a lot.

---


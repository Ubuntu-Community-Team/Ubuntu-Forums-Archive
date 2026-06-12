---
title: "Unable to install W7"
date: 2016-05-22
forum: Windows
---

### Post by JUSTERINI1 on 2016-05-22
Hi,
I've a dual boot with Ubuntu 14.04 and W7, since now with perfectly running. But I've reinstalled W7 do some issues, but after w7 cd had copied most of the files to his partition, on rebboting, Grub doesn't find the correct partition to continue installing W7 and I'm only allowed to run Ubuntu, so, I'm in a bucle, and unable to continue installing W7.
Any help please?

Thanks in advance.

---

### Post by ajgreeny on 2016-05-22
From your ubuntu installation open a terminal and run command ```
sudo update-grub
``` which may be all that is needed as that should reconfigure the system to add Windows to your grub menu.

---

### Post by JUSTERINI1 on 2016-05-24
Hi ajgreeny, Thanks, after updating, I realised, the problem wasn't grub.
the problem was the boot sector.
I followed Yannbuntu's thread:  [http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)  and now it's ok.

Thanks.
Justerini

---

### Post by ajgreeny on 2016-05-25
Great!
Please mark as solved from the Thread Tools menu up top.

---


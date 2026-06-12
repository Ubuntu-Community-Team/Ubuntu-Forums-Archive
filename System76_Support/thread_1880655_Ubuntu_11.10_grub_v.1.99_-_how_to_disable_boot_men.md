---
title: "Ubuntu 11.10 grub v.1.99 - how to disable boot menu"
date: 2011-11-14
forum: System76 Support
---

### Post by matan7779 on 2011-11-14
Hi all,
I have a single OS on the machine with:
Ubuntu 11.10
grub v.1.99
I am trying to disable the menu when the pc is booting (it gives the list of GNU ubuntnu list...). Sometimes this menu appears. 

I read in many forums that ther are  that I can install grub 2 and when i have the menu at the Tab "Boot options" I do not see the option: "Show bootloader menu" - hence i cannot disable it. The other plae it should be a /etc/grub/grub/cfg or at /etc/grub/menu.lst or at the the /etc/default.
Non of the above I see. I cannot find the menu.lst file.
Besides , for some reason I do not have /etc/grub folder, I only have  /etc/grub.d folder and I still do not see the menu.lst file.

Can someone help me to find this file or the place "hiddenmenu" field exists (so i can put #) or any other idea?!?!

Thanks a lot,
Matan

---

### Post by Liber81 on 2012-12-15
Hi,

I had exactly the same problem. I had to edit "config.cfg" manually, it means change all entries with "timeout=-1" to "timeout=0".
This is not safe procedure, but it works for me and it did not harm my system (Linux Mint 13 64bit).

---


---
title: "Moving /var to a new disk"
date: 2009-09-28
forum: Server Platforms
---

### Post by Kilimangaro on 2009-09-28
Hi all,

I've recently added a new disk to my system (/var was filled-up at 98%). Here is the procedure i followed :

Adding new disk (my new disk is /dev/sda1) and formating
# fdisk
# mkfs -t xfs /dev/sda1
# mkdir /var2
# mount /dev/sda1 /var2
# cp -a /var /var2
# vi /etc/fstab
Old line was :
UUID=bc68178f-d5a5-49bd-a135-490d0e1891f9 /var            xfs     relatime        0       2
Commented out
New line is :
/dev/sda1 /var            xfs     relatime        0       2

Cross my finger and reboot. Sadly  my system didnt reboot. I dont even see GRUB, just a flashing cursor :(

I reboot from a live CD and re-edit /etc/fstab commenting my new line and de-commenting the original one.

I reboot again and... nothing... just a flashing cursor :(:(:(

HELP plz !

Regards

---

### Post by ainsworth_t on 2009-09-28
How did you perform the fdisk and formatting? Was it from a LiveCD or from the system?

Have you tried unplugging the drive and re-booting?

---

### Post by Kilimangaro on 2009-09-28
I've found the problem.

My new disk was detected as master IDE instead of slave. Some jumpers tweak and everything is working fine !

---


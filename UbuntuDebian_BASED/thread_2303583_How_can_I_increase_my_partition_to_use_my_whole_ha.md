---
title: "How can I increase my partition to use my whole hard drive?"
date: 2015-11-19
forum: Ubuntu/Debian BASED
---

### Post by LXLE_users_22 on 2015-11-19
Hello, I have LXLE installed on my laptop, and I think when I first installed LXLE a while ago, I didn't allow the partition to use my whole hard drive. I have Googled, and Googled trying to figure out how to increase my partition size, and pretty much every article applied to users using VMware, or using dual boot. I'm just looking for a way to increase the amount of memory Linux is allowed to use on this hard drive. I am still sort of new to linux, I got it about a month ago after windows suddenly quit working, and I love this version of linux, if anybody could help me out with this, that would be totally cool, thanks.

---

### Post by howefield on 2015-11-19
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Portaro on 2015-11-20
You need to resize the partition , after this you need to update grub if you resize a / , /boot initi type partition , and if you have a space to the left of boot flag can occur a problem to update grub so before all and if you need a backup of a partition that is preceded of the / , /boot init flag partition and you need to do it before the rezise .

If the space is placed a right of your partition and if the partition is not a linux  / , /boot initi type partition I think that you dont need update grub simply resize to the free space alocated at right .

You can easily find the grub partition by -> [http://sourceforge.net/projects/bootinfoscript/?source=typ_redirect](http://sourceforge.net/projects/bootinfoscript/?source=typ_redirect)
remeber that this script generate a RESULTS.txt in the same path of the script.
And you can find all partitions by command lsblk for example.

Please follow the steps present on the following link ->[http://gparted.org/faq.php](http://gparted.org/faq.php)
[http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem](http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem)

I hope that this can help you.

---


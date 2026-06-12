---
title: "Problems with encrypted root filesystem"
date: 2007-05-07
forum: Server Platforms
---

### Post by tdn on 2007-05-07
I am trying to set up encrypted root filesystem with LUKS/cryptsetup. 

I have installed a base system on sda6 (2400MB partition), used sda2 (300MB partition) as /boot; 
then I have luksFormat'ed sda5 (50GB partition) and made an ext3 filesystem on that; 
then I copied everything from sda6 to sda5 and edited /etc/fstab to use /dev/mapper/root for / and edited /etc/crypttab to set up sda5 as /dev/mapper/root; 
then I ran update-initrd. 
Rebooted.

Now I cannot boot to my encrypted root fs.

---

### Post by tdn on 2007-05-07
I have added more details to this problem here:
[https://answers.launchpad.net/ubuntu/+question/6237](https://answers.launchpad.net/ubuntu/+question/6237)

I hope it helps.

(includes contents of various files and such.)

---


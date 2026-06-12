---
title: "how to recovery LVM"
date: 2010-01-28
forum: Server Platforms
---

### Post by Phulerock on 2010-01-28
I have 5 hdd, 
/dev/sda1 (for ubuntu OS)
1. /dev/sdb1
2. /dev/sdc1
3. /dev/sdd1
4. /dev/sde1

1+2+3+4 is /dev/fileserver with LVM configuration. I setup this via [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm).

But I affraid when my /dev/sda1 have trouble, how can I reinstall new Ubuntu without lost my data in the LVM.

Please help

---

### Post by ICEB3AR on 2010-01-28
Isn't it like this, that you install your os into /dev/sda1 like before with LVM. After installation you only add a logical volume group with /dev/sd[b,c,d,e]1 and mount this.

I'm not sure, but this way would make sense to mee.

---

### Post by Phulerock on 2010-01-28
> **ICEB3AR said:**
> Isn't it like this, that you install your os into /dev/sda1 like before with LVM. After installation you only add a logical volume group with /dev/sd[b,c,d,e]1 and mount this.

I'm not sure, but this way would make sense to mee.

Thanks man, I finished it, its really easy.

---


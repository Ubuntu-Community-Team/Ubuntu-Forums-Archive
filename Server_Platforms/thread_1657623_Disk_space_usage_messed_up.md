---
title: "Disk space usage messed up"
date: 2011-01-01
forum: Server Platforms
---

### Post by Coder68 on 2011-01-01
I have 5 2TB HD's in my raid 5.
These are drives:
sda
dsb
sdc
sde
**sdg**

But, in mdadm.conf I have:
DEVICE /dev/sda /dev/sdb /dev/sdc /dev/sde
ARRAY  /dev/md1 level=5 devices=/dev/sda,/dev/sdb,/dev/sdc,/dev/sde,**/dev/sdg**

Shouldn't my DEVICE also have /dev/sdg listed?

On cold boot, one of my drives does not show up. (I have not confirmed it is sdg yet.) Upon reboot (warm boot.) all 5 drives are there. Could this discrepancy in mdadm.conf be the reason why?

Thanks for the help,

Coder68

---


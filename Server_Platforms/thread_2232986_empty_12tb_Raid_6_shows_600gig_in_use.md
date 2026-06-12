---
title: "empty 12tb Raid 6 shows 600gig in use?"
date: 2014-07-05
forum: Server Platforms
---

### Post by oehq on 2014-07-05
Hello,

I built a new mdadm  raid on my server using mdadm with qty of six 3tb drives total 18tb.

commad = 
sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=6 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

it is my understanding that after building the raid 6 setup there would be 12 tb of usable space left.
However when i do a check it shows only 11.4 tb usable and there is 600 gig already in use?

Does anyone know why the whole 12tb is not usable?  
Is there a way to make it it all usable?

what is in the 600 gigs

Thanks for your help

---

### Post by ajgreeny on 2014-07-05
I don't know if it is different in a raid setup, but in normal ext# formatted drives there is a 5% reserved block area, which would account for the 600GB out of your total of 120000GB (ie 12TB).

This can be removed completely, or reduced, if you need to with tune2fs on a normal drive, but again I can't help with a raid system; tune2fs may still work, it's just that I don't know.

---

### Post by rubylaser on 2014-07-05
If the array is made up of disk partitions, this could certainly happen.  You should just use tune2fs to reduce the reserved space to zero on each disk like this.
```

tune2fs -m 0 /dev/sd1
etc.

```
and on the array
```

tune2fs -m 0 /dev/md0

```

---


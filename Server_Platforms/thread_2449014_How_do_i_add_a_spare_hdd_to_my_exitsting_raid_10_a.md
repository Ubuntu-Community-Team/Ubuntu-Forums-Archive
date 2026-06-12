---
title: "How do i add a spare hdd to my exitsting raid 10 array?"
date: 2020-08-18
forum: Server Platforms
---

### Post by math492m on 2020-08-18
hi im runnining ubuntu server 18.04 lts on my hp server 

and what i would like to know is how do i add a spare hdd to my exitsting raid 10 array?

all help is apriciated

---

### Post by darkod on 2020-08-18
Adding a spare should be easy by using mdadm --add.

Adjust the command as per your case. For example lets assume your array is md0 and the spare disk you want to add is /dev/sde1 (use partitions in mdadm, not whole disks):
```
sudo mdadm /dev/md0 --add /dev/sde1
```

That should add it as spare. Use --verbose to get more output while the command is running:
```
sudo mdadm /dev/md0 --verbose --add /dev/sde1
```

---

### Post by math492m on 2020-08-18
thanks

---


---
title: "Raid 5 self drive reassignment"
date: 2010-05-24
forum: Server Platforms
---

### Post by boutch55555 on 2010-05-24
Ok... a little background :
The raid array was manually created with mdadm and 4 X 1TB drives.
I expanded it twice, adding 2 more TB drives to the array, 1 at the time. It ran flawlessly for about 2 months. Then, I had some hardware problems (4 busted capacitors on motherboard). I replaced the board with the SAME one (and changed power supply, not taking chances), only to discover that my array now had a failed drive. I ordered a replacement, but this morning, while checking the status, I realised that one of the drives suddently (between 7 am and 11 am) reassigned itself as spare (!!!!)

Here's the output from /proc/mdstat :

```
md1 : active raid5 sdb1[4] sdc1[6](S) sdj1[2] sda1[7](F) sdd1[0] sdf1[1]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/4] [UUU_U_]
```

and the corresponding part of /etc/mdadm/mdadm.com :

```
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=7e6dd771:978550bd:16140f30:b13e114b
```

The weird thing here is that the config file states that there are only 4 drives in the array. I assume it must have been written at creation time and mdadm scans the drives to discover my config. 

Is there a safe way to reassign the spare drive where it was in the array ?? Why would a drive be reassigned as spare ?

Thanks

Mathieu

---

### Post by boutch55555 on 2010-05-24
I might delete the array and reassemble it if nothing else works, but I don't really want to try that...

---

### Post by boutch55555 on 2010-05-24
I just tried removing the failed drive (sda1) and adding it back :
```

mdadm --manage --set-faulty /dev/md1 /dev/sda1
mdadm /dev/md1 -r /dev/sda1
mdadm /dev/md1 -a /dev/sda1

```
But now I got 2 spare drives !!!

```
active raid5 sda1[6](S) sdb1[4] sdc1[7](S) sdj1[2] sdd1[0] sdf1[1]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/4] [UUU_U_]
```

HELP

---


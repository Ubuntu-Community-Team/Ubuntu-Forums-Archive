---
title: "raid1 drive failed - which one?"
date: 2011-01-04
forum: Server Platforms
---

### Post by buffchick on 2011-01-04
I've  got two drives mirrored. One drive is still working and accessible and  the other one is dead. Not even showing up in fdisk anymore. How do I  know which drive is sdd and which one is the failed sde? They both spin up and show in the card bios.

temp@nas:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdd1[1]
      312568576 blocks [2/1] [_U]

md2 : active raid1 sdb1[0] sdc1[1]
      976759936 blocks [2/2] [UU]

unused devices: <none>
temp@nas:~$

---

### Post by James78 on 2011-01-04
I think this command should give you some better insight..
```
sudo mdadm --detail /dev/md0
```

---

### Post by buffchick on 2011-01-04
Thanks! As it turns out... it was the pci slot on the motherboard! I hooked both HDD to my windows pc via usb and they were working. I swapped the raid card out and same problem. I moved PCI slots and everything's working again. Thanks for the response!

---


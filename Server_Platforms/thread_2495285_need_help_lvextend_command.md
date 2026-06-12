---
title: "need help lvextend command"
date: 2024-02-13
forum: Server Platforms
---

### Post by Heeter on 2024-02-13
Hi all

trying to 100% free this lvm, but I cannot get the command to work.

```

root@web:~# lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sr0                        11:0    1 1024M  0 rom  
vda                       252:0    0  250G  0 disk 
&#9500;&#9472;vda1                    252:1    0    1M  0 part 
&#9500;&#9472;vda2                    252:2    0    2G  0 part /boot
&#9492;&#9472;vda3                    252:3    0  248G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0  100G  0 lvm  /

root@web:~# pvs
  PV         VG        Fmt  Attr PSize    PFree   
  /dev/vda3  ubuntu-vg lvm2 a--  <248.00g <148.00g

root@web:~# lvextend -l +100%FREE -r /dev/ubuntu-vg/root
  Logical volume root not found in volume group ubuntu-vg.

root@web:~# df -hPT /
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4   98G   53G   41G  57% /

root@web:~#

```

What should I use as a command to 100% extend this to the full 250G?

I thought that I had it correct with
```

lvextend -l +100%FREE -r /dev/ubuntu-vg/root

```

Also tried
```

lvextend -l +100%FREE -r /dev/ubuntu--vg-ubuntu--lv/root

```

Regards

---

### Post by Heeter on 2024-02-13
Thanks for the PM, helped

---


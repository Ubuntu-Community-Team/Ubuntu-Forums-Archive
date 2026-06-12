---
title: "Shrink (virtual) hard disk"
date: 2019-04-23
forum: Virtualisation
---

### Post by joshi82 on 2019-04-23
Good morning,

I have one serverthat is pushing it´s limits in terms of hard disk space. It is all hosted on one big, (virtual) hard disk, and I was absolutely not aware that data usage will grow that much.

```

NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0  2,2T  0 disk
&#9500;&#9472;sda1   8:1    0  487M  0 part /boot
&#9500;&#9472;sda2   8:2    0  3,7G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0  3,7G  0 part /
&#9500;&#9472;sda4   8:4    0    1K  0 part
&#9500;&#9472;sda5   8:5    0  3,7G  0 part /usr
&#9500;&#9472;sda6   8:6    0  1,9G  0 part /home
&#9500;&#9472;sda7   8:7    0  7,5G  0 part /tmp
&#9500;&#9472;sda8   8:8    0 14,9G  0 part /var
&#9492;&#9472;sda9   8:9    0  1,9T  0 part /srv

```

So my plan is to add another disk, migrate /srv there, kill sda9 and then shrink the hard disk as much as possible (the actual file system), and then offline shrink the virtual hdd.
This worked once for me on a windows box, but I am not sure if this is a feasable way here on ubuntu. I would like to avoid further migrations (in terms of reinstall), if possible.

But, if you have other ways to accomplish that, I am more than interrested to hear them :)

Thanks in advance
Johannes

//Edit: I posted it here in hardware, since it is not strictly related to virtualisation....

---

### Post by wildmanne39 on 2019-04-23
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-04-23
Well, if you had installed with LVM, this would be easy.  Without it, well, I would reinstall now to avoid the coming issues next time.

BTW, a **df -Th** would be helpful and fdisk output.  The info above doesn't show the layout for which partitions are next to each other.

---

### Post by joshi82 on 2019-04-26
I didn´t install it, I inheritet it. Here is the output:

```
Filesystem    Type      Size In use Avail. Use% Mountpoint
udev           devtmpfs  2,0G       0  2,0G    0% /dev
tmpfs          tmpfs     405M     42M  363M   11% /run
/dev/sda3      ext4      3,7G    1,5G  2,0G   43% /
/dev/sda5      ext4      3,7G    2,5G 1022M   71% /usr
tmpfs          tmpfs     2,0G       0  2,0G    0% /dev/shm
tmpfs          tmpfs     5,0M       0  5,0M    0% /run/lock
tmpfs          tmpfs     2,0G       0  2,0G    0% /sys/fs/cgroup
/dev/sda1      ext2      457M    258M  175M   60% /boot
/dev/sda7      ext4      7,3G    608M  6,3G    9% /tmp
/dev/sda8      ext4       15G    6,3G  7,6G   46% /var
/dev/sda6      ext4      1,9G    2,9M  1,7G    1% /home
/dev/sda9      ext4      1,9T    1,8T   24G   99% /srv
cgmfs          tmpfs     100K       0  100K    0% /run/cgmanager/fs
tmpfs          tmpfs     405M       0  405M    0% /run/user/0

```

```
Medium /dev/sda: 2,2 TiB, 2362232012800 Bytes, 4613734400 SektorenEinheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0x581f6499


Gerät      Boot    Start       Ende   Sektoren Größe Id Typ
/dev/sda1           2048     999423     997376  487M 83 Linux
/dev/sda2         999424    8812543    7813120  3,7G 82 Linux Swap / Solaris
/dev/sda3        8812544   16625663    7813120  3,7G 83 Linux
/dev/sda4       16627710 4192206847 4175579138    2T  5 Erweiterte
/dev/sda5       16627712   24438783    7811072  3,7G 83 Linux
/dev/sda6       24440832   28344319    3903488  1,9G 83 Linux
/dev/sda7       28346368   43968511   15622144  7,5G 83 Linux
/dev/sda8       43970560   75218943   31248384 14,9G 83 Linux
/dev/sda9       75220992 4192206847 4116985856  1,9T 83 Linux

```

Is it possible to add another GPT-disk, migrate /srv there, delete sda9 and shrink the virtual sda to e.g. 100G? I assume this could be possible?

Thanks
Johannes

---

### Post by TheFu on 2019-04-26
> **joshi82 said:**
> I didn´t install it, I inheritet it. Here is the output:

```
Filesystem    Type      Size In use Avail. Use% Mountpoint
udev           devtmpfs  2,0G       0  2,0G    0% /dev
tmpfs          tmpfs     405M     42M  363M   11% /run
/dev/sda3      ext4      3,7G    1,5G  2,0G   43% /
/dev/sda5      ext4      3,7G    2,5G 1022M   71% /usr
tmpfs          tmpfs     2,0G       0  2,0G    0% /dev/shm
tmpfs          tmpfs     5,0M       0  5,0M    0% /run/lock
tmpfs          tmpfs     2,0G       0  2,0G    0% /sys/fs/cgroup
/dev/sda1      ext2      457M    258M  175M   60% /boot
/dev/sda7      ext4      7,3G    608M  6,3G    9% /tmp
/dev/sda8      ext4       15G    6,3G  7,6G   46% /var
/dev/sda6      ext4      1,9G    2,9M  1,7G    1% /home
/dev/sda9      ext4      1,9T    1,8T   24G   99% /srv
cgmfs          tmpfs     100K       0  100K    0% /run/cgmanager/fs
tmpfs          tmpfs     405M       0  405M    0% /run/user/0

```

```
Medium /dev/sda: 2,2 TiB, 2362232012800 Bytes, 4613734400 SektorenEinheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0x581f6499


Gerät      Boot    Start       Ende   Sektoren Größe Id Typ
/dev/sda1           2048     999423     997376  487M 83 Linux
/dev/sda2         999424    8812543    7813120  3,7G 82 Linux Swap / Solaris
/dev/sda3        8812544   16625663    7813120  3,7G 83 Linux
/dev/sda4       16627710 4192206847 4175579138    2T  5 Erweiterte
/dev/sda5       16627712   24438783    7811072  3,7G 83 Linux
/dev/sda6       24440832   28344319    3903488  1,9G 83 Linux
/dev/sda7       28346368   43968511   15622144  7,5G 83 Linux
/dev/sda8       43970560   75218943   31248384 14,9G 83 Linux
/dev/sda9       75220992 4192206847 4116985856  1,9T 83 Linux

```

Is it possible to add another GPT-disk, migrate /srv there, delete sda9 and shrink the virtual sda to e.g. 100G? I assume this could be possible?

Thanks
Johannes

This isn't a GPT disk. It is MBR.  sd4 is an "extended primary partition" and it includes sda5-sda9.  You can add another disk and move everything from sda9 over.  As long as the new storage is mounted so it appears to be /srv, that is 100% fine. We do that all-the-time.  Moving 1.8T of data isn't fun.

You won't be able to resize sda4 while there are other partitions inside it. At least, I don't think you can.  But if all of sda4 was an LVM2 partition, and each of the other logical partitions inside were actually LVs (logical volumes), then doing this would be trivial.  Moving an LV from 1 disk to another is trivial, with ext4 as the file system, you can easily reduce/extend LVs in size too.

So ... if you were to make the new disk GPT, create some partitions with a mix of normal partitions and 1 as an LVM2 partition, then create LVs for all the old partitions inside the extended partition, then you can prepare this system for unknown future needs, but retain flexibility.  Whether this effort is worth it to you depends.  "Change" and "new"  is the enemy of "stable."

BTW, it is most helpful to the wider community if the commands and options are included in the output. Thanks.

---


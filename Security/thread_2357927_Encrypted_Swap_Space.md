---
title: "Encrypted Swap Space"
date: 2017-04-07
forum: Security
---

### Post by KenUBF on 2017-04-07
I have a drive with LUKS encryption enabled and I wanted to ensure that my swap partition was also encrypted. So I ran > sudo blkid | grep swap and I got the following output:

> /dev/mapper/ubuntu--mate--vg-swap_1: UUID="b23fc070-c64e-4695-8364-057ad486edeb" TYPE="swap"
/dev/mapper/cryptswap1: UUID="8f3acd33-1e01-4092-8a23-c7ebac85e1cc" TYPE="swap" 

I'm still learning the Linux system so I'm not sure what to make of this. It appears as if I've got two swap partitions. One encrypted and one not. Or is this telling me something different?

---

### Post by TheFu on 2017-04-07
**lsblk** will show relationships between partitions, encryption, lvs and where swap is located.

---

### Post by KenUBF on 2017-04-08
Thanks for the reply. I ran the command and this was the output:

```
Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 170B56D2-008C-4436-8547-FEDF9AC89795


Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624    2050047     999424  488M Linux filesystem
/dev/sda3  2050048 7814035455 7811985408  3.7T Linux filesystem




Disk /dev/mapper/sda3_crypt: 3.7 TiB, 3999734431744 bytes, 7811981312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/ubuntu--mate--vg-root: 3.6 TiB, 3931144978432 bytes, 7678017536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/ubuntu--mate--vg-swap_1: 63.9 GiB, 68585259008 bytes, 133955584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/cryptswap1: 63.9 GiB, 68584734720 bytes, 133954560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

I'm not sure exactly how to interpret these results. I see some partitions that are listed as swap, but one appears to be in plain text since there is no cryptswap designation. Maybe it will make more sense to you. Thanks.

---

### Post by TheFu on 2017-04-08
That is not the output from the lsblk command.  This is mine:
```
$ lsblk
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
&#9500;&#9472;sda1                          8:1    0  487M  0 part  /boot
&#9500;&#9472;sda2                          8:2    0    1K  0 part  
&#9492;&#9472;sda5                          8:5    0 55.4G  0 part  
  &#9492;&#9472;sda5_crypt                252:0    0 55.4G  0 crypt 
    &#9500;&#9472;ubuntu--mate--vg-root   252:1    0 51.5G  0 lvm   /
    &#9492;&#9472;ubuntu--mate--vg-swap_1 252:2    0    4G  0 lvm   [SWAP]

```
The swap is under the sda5_crypt dmcrypt-container, which is under the sda5 partition. See?

---

### Post by KenUBF on 2017-04-08
Sorry about that. I can't figure out what I did. Maybe a typo.... But I copied/pasted the correct command from your post and got the same output. 

```

$ lsblk
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sr0                            11:0    1 1024M  0 rom   
sda                             8:0    0  3.7T  0 disk  
&#9500;&#9472;sda2                          8:2    0  488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0  3.7T  0 part  
&#9474; &#9492;&#9472;sda3_crypt                253:0    0  3.7T  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--mate--vg-root   253:1    0  3.6T  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--mate--vg-swap_1 253:2    0 63.9G  0 lvm   
&#9474;     &#9492;&#9472;cryptswap1            253:3    0 63.9G  0 crypt [SWAP]
&#9492;&#9472;sda1                          8:1    0  512M  0 part  /boot/efi
sr1                            11:1    1 1024M  0 rom   




```

It seems that according to this my swap partitions are in fact encrypted. Is that what you see too? Thanks for the help.

---

### Post by TheFu on 2017-04-08
looks like the swap VG contains a double-encrypted swap.  Everything in sda3_crypt is already encrypted.  Any performance issues?

---

### Post by KenUBF on 2017-04-08
No performance issues at all. Just installed 16.04 MATE a few days ago and I'm loving it. Thanks for that neat command.

---


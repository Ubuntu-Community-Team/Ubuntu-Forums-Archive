---
title: "Failed to create swap apace"
date: 2019-06-20
forum: Ubuntu Development Version
---

### Post by VMC on 2019-06-20
Trying both [s]Kubuntu 19.10[/s], Ubuntu 19.10 I get the following error:
"The creation of swap space in partition #7 of /dev/nvme0n1 failed"

I have used that swap partition for every install so far without failure. Why now?

```
[FONT=monospace][COLOR=#000000]nvme0n1                                                                          [/COLOR]
&#9500;&#9472;nvme0n1p1 vfat   ESP      961F-698A                              36.9M    62% /boot/efi
&#9500;&#9472;nvme0n1p2                                                                      
&#9500;&#9472;nvme0n1p3 ntfs   Acer     A85E213E5E2106A2                                     
&#9500;&#9472;nvme0n1p4 ext4   kubuntu  536e57a8-13d8-4d8f-b075-8c82d0e10634   39.5G    12% /
&#9500;&#9472;nvme0n1p5 ext4   deepin   bd88214a-b973-4563-85eb-cc77a8e0e914                 
&#9500;&#9472;nvme0n1p6 ext4            c52cc895-2c8a-45f9-9891-b8b9aa28064a                 
&#9492;&#9472;nvme0n1p7 swap            1cd70532-1599-489e-94ce-3318fd9c2834                [SWAP][/FONT]
```

[FONT=monospace]edit: xubuntu date June 5th works as expected. ubiquity 19.10.3[/FONT]

[FONT=monospace]edit2:The error only occurs using Kubuntu 19.10 and ubiquity version 19.10.5[/FONT]
[FONT=monospace]The current Ubuntu still uses ubiquity version 19.10.3

edit3: [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1833626")[/FONT]

---

### Post by dino99 on 2019-06-21
Parted has been updated several times recently; can be related

parted (3.2-25ubuntu3) eoan; urgency=medium

  * Revert back to 3.2-25, failed to make -partN work in d-i.

 -- Dimitri John Ledkov <xnox@ubuntu.com>  Fri, 21 Jun 2019 01:58:46 +0100

parted (3.2-25ubuntu2) eoan; urgency=medium

  * Previous upload was incorrect, actually do what it says on the tin.

 -- Dimitri John Ledkov <xnox@ubuntu.com>  Wed, 19 Jun 2019 23:10:12 +0100

parted (3.2-25ubuntu1) eoan; urgency=medium

  * _device_get_part_path: use -partN for dm partitions. As otherwise
    there are differences in devices naming between what parted creates,
    and what `udevadm trigger` will rename them to. LP: #1825189


 -- Dimitri John Ledkov <xnox@ubuntu.com>  Mon, 17 Jun 2019 16:21:08 +0100

---

### Post by VMC on 2019-06-21
I need verification for bug report. 
If someone is installing to hard drive (not virtual),  kubuntu 19.10 and have swap partition, will you please let me know if it fails swap. Then "me too" on bug report. Thanks.

---

### Post by VMC on 2019-06-21
June 21st ISO fixed the issue

---


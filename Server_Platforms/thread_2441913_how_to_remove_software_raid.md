---
title: "how to remove software raid"
date: 2020-04-27
forum: Server Platforms
---

### Post by sky55 on 2020-04-27
hello,

i have 40TB server from Hezner and they use SW raid, when i type lsblk i get -

```

root@Ubuntu-1804-bionic-64-minimal ~ # lsblkNAME    
MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda       8:0    0  9.1T  0 disk
&#9500;&#9472;sda1    8:1    0   16G  0 part
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sda2    8:2    0  512M  0 part
&#9474; &#9492;&#9472;md1   9:1    0  511M  0 raid1 /boot
&#9500;&#9472;sda3    8:3    0 1007G  0 part
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sda4    8:4    0  8.1T  0 part
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sda5    8:5    0    1M  0 part
sdb       8:16   0  9.1T  0 disk
&#9500;&#9472;sdb1    8:17   0   16G  0 part
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sdb2    8:18   0  512M  0 part
&#9474; &#9492;&#9472;md1   9:1    0  511M  0 raid1 /boot
&#9500;&#9472;sdb3    8:19   0 1007G  0 part
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sdb4    8:20   0  8.1T  0 part
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sdb5    8:21   0    1M  0 part
sdc       8:32   0  9.1T  0 disk
&#9500;&#9472;sdc1    8:33   0   16G  0 part
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sdc2    8:34   0  512M  0 part
&#9474; &#9492;&#9472;md1   9:1    0  511M  0 raid1 /boot
&#9500;&#9472;sdc3    8:35   0 1007G  0 part
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sdc4    8:36   0  8.1T  0 part
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sdc5    8:37   0    1M  0 part
sdd       8:48   0  9.1T  0 disk
&#9500;&#9472;sdd1    8:49   0   16G  0 part
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sdd2    8:50   0  512M  0 part
&#9474; &#9492;&#9472;md1   9:1    0  511M  0 raid1 /boot
&#9500;&#9472;sdd3    8:51   0 1007G  0 part
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sdd4    8:52   0  8.1T  0 part
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sdd5    8:53   0    1M  0 part



```

how can remove the raid and use all the 40TB for storage ?

i need it to be somethig like this -

```

NAME    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINTsda       8:0    0  9.1T  0 disk
&#9500;&#9472;sda1    8:1    0   16G  0 part [SWAP]
&#9500;&#9472;sda2    8:2    0  512M  0 part /boot
&#9500;&#9472;sda3    8:3    0 1007G  0 part /
&#9500;&#9472;sda4    8:4    0  8.1T  0 part /home
&#9492;&#9472;sda5    8:5    0    1M  0 part

sdb       8:16   0  9.1T  0 disk /home/driveb
sdc       8:32   0  9.1T  0 disk /home/drivec
sdd       8:48   0  9.1T  0 disk /home/drived


```

many thanks

---

### Post by darkod on 2020-04-28
For this you should talk to their support because it depends what type of console access they can offer you. It's not the same when the server is at your home next to you and you have complete access, and when it is in a datacenter managed by a provider.

And do not forget that actually using raid is recommended for data protection against disk failure. If you stop using raid you need to accept the risk of data loss if a disk breaks and you have no full backups.

Although in this case with 4 disks I see using raid6 unnecessary, too much space is wasted on the redundancy. Maybe raid5 would be better option.

---

### Post by sky55 on 2020-04-28
thank you for replying.

they give me rescue access and i can do what i want with disks from there, i did break the system many time from the rescue mode.

i have full backup on my Google drive that why i dont need any raid protection, i need full space. 

thanks again.

---

### Post by darkod on 2020-04-28
So what is the problem exactly? If you are doing the installation yourself simply don't tell it to set up raid during installation. If it has, that is because you are setting it up like that.

If you are still confused how to get rid of the mdadm superblock and you have the data backed up on another place, create new blank partition tables on the disks during the manual partitioning step. That will allow you to start with fresh disks and there shouldn't be any trace of raid.

---

### Post by sky55 on 2020-04-28
the installation is not done manually, they have a script that install Ubuntu, i can't edit it. just execute it.

---

### Post by darkod on 2020-04-28
Well then what you said in post #3 is not entirely correct because you don't have full control of the install process and with that of the disks. You need to talk to their support. Their script will keep using raid6 it seems and whether you can launch it yourself or not does not mean much control.

---

### Post by sky55 on 2020-04-28
LOL that was easy.

from rescue mode i can lunch the script and edit it before execution, just remove raid part and that it :lolflag:

---


---
title: "Question about resizing partitions on my serval"
date: 2008-09-26
forum: System76 Support
---

### Post by Replicon on 2008-09-26
I think I posted about this elsewhere a while back, but I think a new thread here will be good, since I have some questions specific to the default configuration.

I've only got 800MB free on there, and the new release is just around the corner, and I'm worried about running out of space during the update.

1) Is the default configuration of the ServalP such that I can resize my root partition? (I want to take a GB or two off of /home and put it on /). I heard that you can't always do that, and that if you want to, things have to be setup in a very specific way (partitions have to exist in same logical volume or somesuch). here is some useful info (not sure if this is enough to be able to tell):

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.6G  4.5G  795M  86% /
varrun                2.0G  128K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   52K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3             171G   86G   77G  53% /home


$ sudo fdisk -l /dev/sda

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4c2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         730     5859375   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             730        1692     7725585+  83  Linux
/dev/sda3            1692       24322   181776023   83  Linux


```


2) I am not dual-booting or anything like that. I keep reading online that if you're resizing a windows partition, you absolutely must defrag it before. Is that true of ext3 as well, or am I safe just doing it? (erm... how DO I defrag in linux? can I just do it from gparted, or is there another way, or is it, in fact, completely irrelevant in ext3?)


3) I plan on just burning a gpartedmagic iso and booting with it to get it done. Assuming condition 1 is met, is there anything I need to be aware of? Yes, I've backed up all my stuff. :)

Thanks!

---

### Post by Replicon on 2008-09-28
Ack!

So I basically did it. It all seemed to work, to produce what I wanted:

```

Old configuration: [  /  5.5GB   ][ swap 7.0GB ][         /home     170GB      ]
New configuration: [    /  7.5GB     ][ swap 7.0GB ][       /home     168GB    ]

```

However, now when I reboot, all I get is the "GRUB" flashing cursor of death.

I imagine it's just a matter of me having moved what GRUB looks for from the boot sector, and so I just need to reconfigure it somehow, but I am not quite sure how. Is there an easy way to fix this? thx!

---

### Post by unutbu on 2008-09-28
Try catlett's instructions on how to reinstall GRUB:
[http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)

---

### Post by Replicon on 2008-09-28
Alright, so I found a real old thread (bulldog's post [here](http://ubuntuforums.org/archive/index.php/t-283311.html)), which provided information on how to reinstall GRUB. I followed it, and it seems to have worked just fine.

The only difference I am seeing is that instead of getting the Ubuntu progressbar on boot, I get the "Reading files needed to boot", followed by the long list of "[ OK ]" checks. Doesn't bother me at all, but I do wonder if something else was setup "custom" originally.

edit: just saw your post unutbu; thanks!

---

### Post by jdb on 2008-09-28
> **Replicon said:**
> Alright, so I found a real old thread (bulldog's post [here](http://ubuntuforums.org/archive/index.php/t-283311.html)), which provided information on how to reinstall GRUB. I followed it, and it seems to have worked just fine.

The only difference I am seeing is that instead of getting the Ubuntu progressbar on boot, I get the "Reading files needed to boot", followed by the long list of "[ OK ]" checks. Doesn't bother me at all, but I do wonder if something else was setup "custom" originally.

edit: just saw your post unutbu; thanks!

edit /boot/grub/menu.lst and put the word splash on the end of the line that starts with "kernel /boot/".

---


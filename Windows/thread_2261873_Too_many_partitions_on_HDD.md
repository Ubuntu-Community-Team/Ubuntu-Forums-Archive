---
title: "Too many partitions on HDD"
date: 2015-01-21
forum: Windows
---

### Post by newbie13 on 2015-01-21
I don't if this is the right sub forum to post this question. It's not an OS based question but I took the screenshot from windows so I am posting it here (great logic! ;)).

As you can see in the screenshot that there are total 10 partitions on my hard disk. Out of which 3, 5, 6 are windows partitions, 8 is ubuntu partition, 9 is Kali linux partition, 10 is windows recovery partition and 7 is swap partition. What I don't understand is what are these 1, 2, and 4 partitions. I don't remember exactly how many were there(out of 1, 2 and 4) before installing ubuntu but I remember there was at least one such partition. It is also possible all of them were there.

Does anyone know what these partitions do? Is anything wrong with my laptop?

While installing ubuntu and kali, it gives an option to change path of installation of 'Device for bootloader'. Both the times, I have left it unchanged. And the grub menu shows all OSs correctly. Has leaving that thing unchanged caused so many partitions?

[ATTACH=CONFIG]259409[/ATTACH]

---

### Post by newbie13 on 2015-01-21
In case you need 'Status' column expanded.

[ATTACH=CONFIG]259411[/ATTACH]

---

### Post by ajgreeny on 2015-01-21
A screenshot from Windows disk-management is not very helpful as it does not tell you what the partitions are, and all ext# partitions are just mentioned as "Healthy Primary" or similar description; not much use when you want to know more about them.

Use gparted, either by installing it to your ubuntu or kali, or by booting to the live disk you used for installing Ubuntu. Gparted will tell us much more about those partitions and will let us see more about what all of them are.
You can also show the output of the terminal command ```
sudo parted -l 
``` in code-tags please (see my signature below for a how-to) which will again show much more useful info.

You were absolutely correct to leave the bootloader in the default device; it is only really useful to change that if you have two physical hard disks and want to, for example leave the windows bootloader on /dev/sda but put grub on /dev/sdb, or you might want to leave one Linux managing grub when you install a second Linux OS; in that situation you could choose to put grub on a partition of the second Linux OS making it ineffective except in a special situation where you are chainloading bootloaders.

---

### Post by newbie13 on 2015-01-22
Out put of 'sudo parted -l'
```
Model: ATA HGST HTS545050A7 (scsi)Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  420MB  419MB   ntfs            Basic data partition          hidden, diag
 2      420MB   693MB  273MB   fat32           EFI system partition          boot
 3      693MB   827MB  134MB                   Microsoft reserved partition  msftres
 4      827MB   166GB  165GB   ntfs            Basic data partition          msftdata
 5      166GB   166GB  472MB   ntfs                                          hidden, diag
 6      166GB   277GB  111GB   ntfs            Basic data partition          msftdata
 7      277GB   431GB  154GB   ntfs            Basic data partition          msftdata
 8      431GB   435GB  4096MB  linux-swap(v1)
 9      435GB   456GB  20.5GB  ext4
11      456GB   474GB  18.4GB  ext4                                          msftdata
10      474GB   500GB  25.8GB  ntfs            Basic data partition          hidden, msftdata

```

gparted screenshot
[ATTACH=CONFIG]259416[/ATTACH]

Furthermore I am also attaching a photo of boot manager. This comes up when I press F9 on start up, in order to boot into ubuntu.
[ATTACH=CONFIG]259417[/ATTACH]

When I had first installed ubuntu, there were only two ubuntu options. Then I messed up things in ubuntu two times and did fresh install both the times which has added 4 more ubuntu options.

After selecting any of those ubuntu options, grub menu appears
[ATTACH=CONFIG]259418[/ATTACH]

Everything is fine in grub menu.

I have uploaded boot manager's photo because it looks suspicious to me. Can't tell you definitely though, if it is the culprit or not.

PS - Although there are many tutorials to avoid pressing F9 at the start up to boot into any os other than windows, I am happy with it. Other OSs stay completely hidden this way, unless you check the disk manager.

---

### Post by newbie13 on 2015-01-24
ajgreeny?

---

### Post by newbie13 on 2015-01-29
anyone?

---

### Post by newbie13 on 2015-02-04
no one?

---

### Post by yancek on 2015-02-04
Partitions 1 and 5 are diagnostic partitions which are generally placed on the computer by major manufacturers with pre-installed windows systems.  Why you have two, I haven't got a clue.  Unusual.
Partition 2 is the EFI partition with the boot files meaning you are using UEFI/GPT to boot your systems.
Partition 3 is a problem, something wrong with it.  Might have been an MBR boot partition before using UEFI, I don't really know.
Partition 4 is probably the windows system partition.
Partitions 6 and 7, windows data partitions.
Partition 8, obviously swap.
Partitions 9 and 11 your Linux partitions.
Partition 10 is your enormous Recovery partition.  On the windows 7 I have it is 12GB.  Probably you have a different version of windows.

There is nothing wrong with the Linux partitions as all you have are the two for the Linux systems and swap.  The other weird partitions for windows don't have anything to do with Grub or Linux.  Maybe someone who uses windows regularly could explain what the third partition is if it is other than an unused mbr boot partition and why you have two diagnostic partitions, I don't know.  Other than that, if everything boots I wouldn't worry about it.

When you look at the EFI partition, partition 2, do you see efi files for Ubuntu and Kali?

---

### Post by newbie13 on 2015-02-05
Thanks..

Partition 3 shows this warning
Unable to detect file system! Possible reasons are:- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda3 is missing

Partition 10 is for windows 8 recovery

Couldn't understand the last part about partition 2. All three os are installed in UEFI mode.

I am concerned about so many tiny partitions created on the hdd. 

After I finish my final exams in march, I am gonna factory reset the laptop and install everything fresh. It is almost full now.

---

### Post by yancek on 2015-02-06
If you mount sda2, the EFI partition, you should see a number of files there relating to EFI.  Some for windows, some for Kali and some for Ubuntu.  I think the Ubuntu ones are those below:

> Boot files:        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi


---

### Post by newbie13 on 2015-02-08
sda2 is mounted but I can not open it. There is no option for it.
All those small partitions are shown in file manager except sda2 so may be efi files of ubuntu are on that partition as you were saying.

---

### Post by yancek on 2015-02-08
If sda2 is mounted, open a terminal and run:  df -h  that command should show where it is mounted.

---

### Post by newbie13 on 2015-02-09
it is mounted on "/boot/efi"

---


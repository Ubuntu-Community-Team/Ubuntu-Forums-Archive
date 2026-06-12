---
title: "[Ubuntu] RAID 6 replace disk, grub issue"
date: 2015-02-22
forum: Server Platforms
---

### Post by alex330 on 2015-02-22
Hi all,

[FONT=courier new]On one of our server, Ubuntu 10.04, 4 disks RAID 6, a disk started to have some "Offline uncorrectable sectors".
So I would like to replace it.[/FONT]

First I did:

```
mdadm --manage /dev/md0 --fail /dev/sdb2
mdadm --manage /dev/md0 --remove /dev/sdb2
```

Here is the result of **lsblk**:
```

[FONT=courier new]NAME                               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                                  8:0    0   1.8T  0 disk  
&#9500;&#9472;sda1                               8:1    0     1M  0 part  
&#9492;&#9472;sda2                               8:2    0   1.8T  0 part  
  &#9492;&#9472;md0                              9:0    0   3.7T  0 raid6 
    &#9500;&#9472;backupser-server-boot (dm-0) 252:0    0   952M  0 lvm    /boot
    &#9500;&#9472;backupser-server-swap (dm-2) 252:2    0   952M  0 lvm    [SWAP]
    &#9492;&#9472;backupser-server-root (dm-4) 252:4    0   3.7T  0 lvm    /
[/FONT][FONT=courier new]sdb                                  8:16   0   1.8T  0 disk  
&#9500;&#9472;sdb1                               8:17   0     1M  0 part  
&#9492;&#9472;sdb2                               8:18   0   1.8T  0 part [/FONT]

sdc and sdd are similar to sda
```


Then I shutdown the machine, replace the disk for a new one, and when I start the machine I have this:
```
error: no such disk.
grub rescue >
```

Here is the result of some command:
```

grub rescue > ls
(md/0) (hd0) (hd0,gpt2) (hd0,gpt1) (hd1) (hd1,gpt2) (hd1,gpt1) (hd2) (hd2,gpt2) (hd2,gpt1) (hd3)

grub rescue > set
prefix=(backupserver-boot)/grub
root=backupserver-boot

grub rescue> ls (md/0)
error: unknown filesystem.

grub rescue> ls (hd0)
error: unknown filesystem.

grub rescue> ls (hd0,gpt1)
error: unknown filesystem.

```

I was not the one who setup this machine. I'm a little bit confused between sda1 and [FONT=courier new]backupser-server-boot.
Here is the output of GParted before I removed the disk (the result is similar for all 4 disks):
```

(parted) print /dev/sdb                                                   
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  2000GB  2000GB                     raid
[/FONT]
```


What should I do in order to start Ubuntu (and then to install the new drive) ?

I'm hesitating to do:
```

grub rescue > set prefix=(md/0)/backupserver-boot/grub
grub rescue >  set root=(md/0)/backupserver-boot

```
But I don't want to mess up everything

---

### Post by ikki_72 on 2015-02-23
maybe you could clone them with clonezilla first

---

### Post by darkod on 2015-02-23
First issue on my mind is whether during the original install it was selected mdadm to boot degraded or not. It asks the question during install and if the person that installed it selected 'no', it will not boot degraded. But I don't know how it acts in that case and if the grub prompt can be because of that.

Another possibility is that part of the boot files is somehow not accessible, maybe because it's on raid6 array. I would never put the boot files on raid5 or raid6 because in those setups the files get split over many disks. Few years ago mdadm needed /boot to be separate outside of raid5/6 because of this. Now days it seems it says mdadm supports booting from raid5/6, but better be safe then sorry.

I'm not sure if you would like to use this ocassion and reorder the setup... for example I would create 2GB partitions on each disk, and the rest one big 2TB partition. From the four 2GB partitions you can create raid1 for /boot, and then have the rest in raid6 and LVM as you do now. But that means you have to copy the data temporarily to another location because you need to destroy the current array.

Another thing I don't understand is what's the purpose of having boot as LV inside LVM. The root LV has flexibility to be extended so in that case you might as well keep boot as folder in root. I see no point putting it into LVM although I can't say for sure that it's the cause of this problem. I really don't get what they were thinking...

In any case, either to copy data or to try to make the current setup work, you have to try if it can work from live mode. Boot the machine with ubuntu desktop cd in live mode, add the mdadm and lvm2 packages, and you can try something like:
```
sudo apt-get install mdadm lvm2
sudo mdadm --assemble --scan   (if that doesn't assemble the array don't bother with next command)
sudo vgchange -ay
```

That should try auto assemble of the raid and activation of the LVM. That will show you if you can get it running although you will need further steps to try making it boot. But it's a start if the raid and LVM can work...

---

### Post by alex330 on 2015-02-23
Thanks for your reply. I will try with the Ubuntu desktop cd in live mode.

More information: I put the old disk back, and I enter grub from the boot menu.
The command "set" gave me the same result for **prefix** and **root**.
The command "ls" gave me more results:
```

grub > ls
(backupserver-root) (backupserver-swap) (backupserver-boot) (md/0) (hd0) (hd0,gpt2) (hd0,gpt1) (hd1) (hd1,gpt2) (hd1,gpt1) (hd2) (hd2,gpt2) (hd2,gpt1)  (hd3) (hd3,gpt2) (hd3,gpt1)

```

When I look at the file **/etc/fstab** I can see that:
```

proc                          /proc                       proc   nodev,noexec,nosuid  0  0
[FONT=courier new]/dev/mapper/backupserver-root /     ext4   errors=remount-ro 0 1
/dev/mapper/backupserver-boot /boot ext4   defaults          0 2
/dev/mapper/backupserver-swap none  swap   sw                0 0[/FONT]

```

---

### Post by darkod on 2015-02-24
Yes, with the old disk it does seem to read the LVM correctly so it gives more options in the grub prompt. Did you maybe try to boot it with the old disk back? Now it doesn't boot automatically even with the disk back?

---

### Post by alex330 on 2015-02-24
With the old disk back, it boot automatically and I can access Ubuntu.

I put a new disk, and started Ubuntu live CD. When I tried to add a new disk to the RAID, mdadm is complaining that the new disk is not big enough (for just 1024kb difference...).
The new disk is a WD, and the other  ones are Seagate. Probably there is some small differences between manufacturers. So I will order a Seagate. And I will post later the result.

Result of **fdisk -l**:
```
[FONT=courier new]
Seagate: 2,000,396,746,752 bytes
WD     : 2,000,395,698,176 bytes[/FONT]
```

---

### Post by darkod on 2015-02-25
If it can boot with the old disk, what you can do is boot it once to check the mdadm degraded boot option and modify it to boot degraded. You can do that with:
```
sudo dpkg-reconfigure mdadm
```

It should ask you three questions, the last being if you want to boot degraded. If this was set to No, the machine will not boot after you remove one member disk.

As for the disk sizes, yes, unfortunately "identical" disks are not identical. Not up to the last Byte. That's why it's recommended to use partitions as members in mdadm, not whole disks (you have partitions, sdX2 which is OK). But when creating the partitions, at the end of the disk leave 10-15MB unpartitioned. Do not create the last partition up to the last sector of the disk. That will help compatibility in future because if disks have a difference, it should be only few MBs. However in your case right now there is no easy way to cut the partitions shorter, this is more for the future...

---

### Post by alex330 on 2015-03-02
Thank you for you reply.

I got a similar disk and I could add it to the RAID (still using the desktop live cd). It should take 4 or 5 hours, the time for the recovery to be done.
After that, I hope I can boot normally. I will post the result later.

---- EDIT ----
Everything is back to normal! 
After the recovery was done (it took around 5 hours, 2TB disk), I removed the Live CD and started the machine and it was OK!

Thank you for your help

---


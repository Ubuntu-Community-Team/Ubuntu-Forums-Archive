---
title: "Problem mounting sata hdd sg4"
date: 2012-04-14
forum: Server Platforms
---

### Post by mihaislack on 2012-04-14
This is dmesg relults, when i try "mount /dev/sg4 /xsys/" it tourns back "mount: /dev/sg4 is not a block device"
 I have an IBM x3650 with raid0 (3x146g) and a sata 2t drive.
 
What should i do to mount that drive?
 
Thankyou very much in advance
 
 
 
[    1.700279] scsi2 : ServeRAID
[    1.700615] scsi 2:0:0:0: Direct-Access     ServeRA  r1               V1.0 PQ: 0 ANSI: 2
[    1.712097] scsi 2:1:0:0: Direct-Access     MAXTOR   ATLAS15K2_147SAS BP05 PQ: 0 ANSI: 5
[    1.713510] scsi 2:1:1:0: Direct-Access     MAXTOR   ATLAS10K5_147SAS BP00 PQ: 0 ANSI: 5
[    1.718097] scsi 2:1:4:0: Direct-Access     WDC      WD20EADS-00W4B0  0A01 PQ: 0 ANSI: 5
[    1.719747] scsi 2:1:5:0: Direct-Access     FUJITSU  MBA3147RC        D305 PQ: 0 ANSI: 5
[    1.782461] scsi 2:3:0:0: Enclosure         IBM-ESXS VSC7160          1.06 PQ: 0 ANSI: 3
[    1.931636] sd 2:0:0:0: [sda] 859525120 512-byte logical blocks: (440 GB/409 GiB)
[    1.931654] sd 2:0:0:0: [sda] Write Protect is off
[    1.931657] sd 2:0:0:0: [sda] Mode Sense: 06 00 10 00
[    1.931667] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.931689] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, supports DPO and FUA
[    1.931860] scsi 2:1:0:0: Attached scsi generic sg2 type 0
[    1.932007] scsi 2:1:1:0: Attached scsi generic sg3 type 0
[    1.932158] scsi 2:1:4:0: Attached scsi generic sg4 type 0
[    1.932288] scsi 2:1:5:0: Attached scsi generic sg5 type 0
[    1.932456] scsi 2:3:0:0: Attached scsi generic sg6 type 13
[    1.946302]  sda: sda1 sda2
[    1.946572] sd 2:0:0:0: [sda] Attached SCSI removable disk
[    2.194482] ses 2:3:0:0: Attached Enclosure device
[    2.845292] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.344708] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.344715] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by darkod on 2012-04-14
What actually is the /dev/sg4 device? The array?

The array would be something like /dev/mapper/..... If the /dev/sg4 is one of the disks in the array, you can't mount it directly, you need to mount the array.

Can you post the output of:
car /proc/partitions

---

### Post by mihaislack on 2012-04-14
the array is formed from the MAXTOR and FUJITSU drives, WD drive 2t sata is not included in any aray, i entered in the raid bios and i only can format the sata drive , normaly how can i mount one new drive like this one?

---

### Post by mihaislack on 2012-04-14
"car /proc/partitions
No command 'car' found, but there are 28 similar ones
car: command not found"

---

### Post by darkod on 2012-04-14
> **mihaislack said:**
> "car /proc/partitions
No command 'car' found, but there are 28 similar ones
car: command not found"

Sorry, my error:
cat /proc/partitions

---

### Post by mihaislack on 2012-04-14
no problem 
[EMAIL="root@arh"]root@arh[/EMAIL]:~# cat /proc/partitions
major minor  #blocks  name
  11        0    1048575 sr0
   8        0  429762560 sda
   8        1  419842678 sda1
   8        2    9912105 sda2
 252        0    9912105 dm-0

---

### Post by darkod on 2012-04-14
Hold on, you want to add the new disk to the array or only use it separately from the array?

---

### Post by mihaislack on 2012-04-14
ok, let me explain
 
i have 3 drives sas for operating sistem and i whant so move the mail and www folder to one separated drive not aded in array

---

### Post by darkod on 2012-04-14
OK then. I think your new disk is /dev/sda. To confirm this, look at the info of parted for the disk:
sudo parted /dev/sda unit s print

At top it will print the model, size, total number of sectors, etc.

If you confirm that /dev/sda is your disk, you can create a partition on it with what ever tool you use. For a 2TB disk you will probably need to use GPT partition table, and for creating partitions you will need to use a tool able to work with GPT.

I haven't used them (I don't have GPT disks), but parted should be able to do it.

Once you have the printed results from the parted command above, we can talk about creating the partition(s) if you need help. Do you want only one partition on the whole disk?

EDIT: On the other hand, if you already have partitions created, we can discuss only mounting them.

---

### Post by mihaislack on 2012-04-14
no, i will partition the disk in 700G and the rest
sda is the raid array , the new one has no partition and now i realize i could not mount , but.... first thing i tried to fdisk /dev/sg4 and nothing happens.... terminal remains stuck until i hit CTRL+C
 
 
parted returns with "Model: ServeRA r1 (scsi)
Disk /dev/sda: 859525120s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start       End         Size        Type     File system  Flags
 1      63s         839685419s  839685357s  primary  ext4         boot
 2      839685420s  859509629s  19824210s   primary
"
 
 
 
> **darkod said:**
> OK then. I think your new disk is /dev/sda. To confirm this, look at the info of parted for the disk:
sudo parted /dev/sda unit s print
 
At top it will print the model, size, total number of sectors, etc.
 
If you confirm that /dev/sda is your disk, you can create a partition on it with what ever tool you use. For a 2TB disk you will probably need to use GPT partition table, and for creating partitions you will need to use a tool able to work with GPT.
 
I haven't used them (I don't have GPT disks), but parted should be able to do it.
 
Once you have the printed results from the parted command above, we can talk about creating the partition(s) if you need help. Do you want only one partition on the whole disk?
 
EDIT: On the other hand, if you already have partitions created, we can discuss only mounting them.

---

### Post by darkod on 2012-04-14
Well, it doesn't look like it can see the new disk at all. Because of that you can't do any partitioning.

Make sure the connections are OK. And don't connect it to the raid controller, connect it directly to a sata port on the MB if you have any. There is a chance that if you connect it to the raid controller, it can be used only inside the array.

The cat command should show you /dev/sdb in there somewhere. Then you will have to create partitions, and create entries in /etc/fstab to make them mount automatically.

But the first step is the disk to be seen.

---

### Post by mihaislack on 2012-04-14
i tried with gparted and it don't recognize the drive
 
in the raid bios i can see the 2Tb drive only i can not do anything with him there

---

### Post by darkod on 2012-04-14
I am not sure if it should be in the raid bios.

Do you have any other sata ports where you can connect it to the motherboard that do not belong to the raid ports?

Usually the boards have raid enabled sata ports, and "normal" sata ports.

I think your disk is connected to the raid ports and is being ignored if not used inside the array.

And usually you can't simply add it to the array unless starting from beginning, but you don't want to use it inside the array anyway.

Look for sata ports that do not belong to raid.

---


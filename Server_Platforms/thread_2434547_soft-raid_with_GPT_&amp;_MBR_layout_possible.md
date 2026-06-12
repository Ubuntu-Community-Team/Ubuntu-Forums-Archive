---
title: "soft-raid with GPT &amp; MBR layout possible?"
date: 2020-01-07
forum: Server Platforms
---

### Post by clusterix on 2020-01-07
Ubuntu 18.04.3 LTS
4.15.0-72-generic


a defective NVME drive was replaced by the datacenter today, unfortunately the new NVME was mistakenly set-up with GPT layout (original used MBR). I have noticed this later after drive integration ... reboot and raid syncing all went well without any errors:
```

# cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 nvme1n1p1[0] nvme0n1p1[2]
      33520640 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 nvme1n1p2[0] nvme0n1p2[2]
      523264 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 nvme1n1p3[0] nvme0n1p3[2]
      965991744 blocks super 1.2 [2/2] [UU]
      bitmap: 7/8 pages [28KB], 65536KB chunk

```


however, nvme list shows the namespace usage differently:
```

Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     S3xxxxxxxxxx2       SAMSUNG xxxx               1           1.02  TB /   1.02  TB    512   B +  0 B   EXA7301Q
/dev/nvme1n1     S3xxxxxxxxxx1       SAMSUNG xxxx               1         321.76  GB /   1.02  TB    512   B +  0 B   EXA7301Q

```
and gdisk -l
```

Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 

```

no issues w/ part. sizes
```

# lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
nvme0n1     259:0    0 953.9G  0 disk  
&#9500;&#9472;nvme0n1p1 259:1    0    32G  0 part  
&#9474; &#9492;&#9472;md0       9:0    0    32G  0 raid1 [SWAP]
&#9500;&#9472;nvme0n1p2 259:2    0   512M  0 part  
&#9474; &#9492;&#9472;md1       9:1    0   511M  0 raid1 /boot
&#9492;&#9472;nvme0n1p3 259:3    0 921.4G  0 part  
  &#9492;&#9472;md2       9:2    0 921.2G  0 raid1 /
nvme1n1     259:4    0 953.9G  0 disk  
&#9500;&#9472;nvme1n1p1 259:5    0    32G  0 part  
&#9474; &#9492;&#9472;md0       9:0    0    32G  0 raid1 [SWAP]
&#9500;&#9472;nvme1n1p2 259:6    0   512M  0 part  
&#9474; &#9492;&#9472;md1       9:1    0   511M  0 raid1 /boot
&#9492;&#9472;nvme1n1p3 259:7    0 921.4G  0 part 

```

everything works without any problems ... staff from the data center said there could be a slight loss in performance, but it would not absolutely necessary to re-setup everything immediately.
What do you think, can I rely on that ... so is a soft-raid w/ an GPT/MBR layout possible?

---

### Post by darkod on 2020-01-07
If you are worried about mdadm partitions being on GPT and MBR disks, I don't think you need to. mdadm works on partition level (when partitions are used as array members) so it wouldn't matter if those are GPT or MBR partitions.

---

### Post by clusterix on 2020-01-09
thanks for reply, but If one NVME runs on GPT and the other on an MBR layout, shouldn't that be visible in the disklabel?
both NVME show partition table disklabel type: dos
and a gdisk -l shows Found invalid GPT and valid MBR
```

# blkid /dev/nvme0n1
/dev/nvme0n1: PTUUID="4ff164f4" PTTYPE="dos"
# blkid /dev/nvme1n1
/dev/nvme1n1: PTUUID="4ff164f4" PTTYPE="dos"

gdisk -l /dev/nvme0n1
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present
***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.
*************************************************************** 

```

## edit ##
alignment check with parted does not show any errors or warnings
[FONT=Verdana]```
[/FONT]# sudo parted /dev/nvme0n1 align-check opt 1
1 aligned
# sudo parted /dev/nvme0n1 align-check opt 2
2 aligned
# sudo parted /dev/nvme0n1 align-check opt 3
3 aligned
# sudo parted /dev/nvme1n1 align-check opt 1
1 aligned
# sudo parted /dev/nvme1n1 align-check opt 2
2 aligned
# sudo parted /dev/nvme1n1 align-check opt 3
3 aligned[FONT=Verdana]
[/FONT]
```

---

### Post by darkod on 2020-01-09
Maybe it's invalid GPT table, or only remains of it? The message seems to say that too.

So maybe in fact both disks are running msdos table in fact.

What does parted say? Not just the allign check, print the table output.

```
sudo parted /dev/nvme0n1
unit MiB (not needed, my personal preference)
print
```

At the top together with disk info it will say whether the table is msdos or gpt.

---

### Post by clusterix on 2020-01-09
thanks [COLOR=#000000]Darko!
[/COLOR]the DC technical staff sent me following statement:
> 
The reason for the message despite the MBR partitions may be "old" remnants of a GPT partition, but this message should not have a negative impact on operation.


maybe converting in memory leads to strange outputs?
converting MBR to GPT format [COLOR=#000000][FONT=&quot]in memory.[/FONT][/COLOR]

```

# sudo parted /dev/nvme0n1
GNU Parted 3.2
Using /dev/nvme0n1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit MiB                                                         
(parted) print                                                            
Model: SAMSUNG MZVLB1T0HALR-00000 (nvme)
Disk /dev/nvme0n1: 976762MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start     End        Size       Type     File system  Flags
 1      1.00MiB   32769MiB   32768MiB   primary               raid
 2      32769MiB  33281MiB   512MiB     primary               raid
 3      33281MiB  976761MiB  943480MiB  primary               raid
 
# sudo parted /dev/nvme1n1
GNU Parted 3.2
Using /dev/nvme1n1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit MiB                                                         
(parted) print                                                            
Model: SAMSUNG MZVLB1T0HALR-00000 (nvme)
Disk /dev/nvme1n1: 976762MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start     End        Size       Type     File system  Flags
 1      1.00MiB   32769MiB   32768MiB   primary               raid
 2      32769MiB  33281MiB   512MiB     primary               raid
 3      33281MiB  976761MiB  943480MiB  primary               raid
 
 
# blkid
/dev/md0         5e39df1e-05f0-46b7-a56f-12134352bff4   swap       
/dev/md1         6264deeb-cea5-4537-bfcd-9a1fefcfa157   ext3       
/dev/md2         1a0cc092-a9f3-4e2d-b37d-a1e02132509a   ext4       
/dev/nvme0n1                                                       
/dev/nvme0n1p1   b6481137-e656-3bd0-f3ac-d16db16fe741   linux_raid_member rescue:0
/dev/nvme0n1p2   8d750efd-3e6d-a557-7cd3-4d63a8a97ae4   linux_raid_member rescue:1
/dev/nvme0n1p3   90e12ee6-caad-0590-a001-565990350608   linux_raid_member rescue:2
/dev/nvme1n1                                                       
/dev/nvme1n1p1   b6481137-e656-3bd0-f3ac-d16db16fe741   linux_raid_member rescue:0
/dev/nvme1n1p2   8d750efd-3e6d-a557-7cd3-4d63a8a97ae4   linux_raid_member rescue:1
/dev/nvme1n1p3   90e12ee6-caad-0590-a001-565990350608   linux_raid_member rescue:2

```


no error messages or warnings in system log files, the system also seems to be working properly ....

---

### Post by darkod on 2020-01-09
Yeah, you can see both partition tables are msdos. parted confirms that.

On one disk there are old remains of gpt table, and some tools can detect this and give you warnings. Other tools simply ignore it.

I think you can rest easy...

---

### Post by clusterix on 2020-01-09
Thank you for your efforts, I will stay calm ;-)

---


---
title: "Mounting Linux raid partition to save 14tb data"
date: 2020-05-08
forum: Server Platforms
---

### Post by rihc0 on 2020-05-08
Hello to the kind people those are reading this post.

I'm not really a Linux guy who knows how to do everything, i have followed some post on this and many other sites to solve my problem but not one post could help me but maybe you can.

storytime:
I have a Dell R720 server installed with ESXi 6.7 within ESXi I have made a virtual machine with Xpenology (DSM from synology) I gave this Virtual Machine a Virtual disk of 14 TB, but for some reason I can't acces my data by GUI or terminal. DSM says the storage pool has been crashed. but the Virtual Disk is there.

I know this is a problem i should post on xpenology but i think i have more options with you people and ubuntu. if someone could help me I would be glad.

I have installed a ubuntu virtual machine and connected the 14tb Virtual disk to it. 


Output of fdisk -l
```
root@vincent-virtual-machine:~# fdisk -l
Disk /dev/loop0: 27,9 MiB, 28405760 bytes, 55480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 54,97 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 240,82 MiB, 252493824 bytes, 493152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 62,9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 49,8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 54,97 MiB, 57618432 bytes, 112536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 255,58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Disk model: Virtual disk    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5dba0cc6

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sda1  *       2048   1050623   1048576  512M  b W95 FAT32
/dev/sda2       1052670 104855551 103802882 49,5G  5 Extended
/dev/sda5       1052672 104855551 103802880 49,5G 83 Linux


Disk /dev/sdb: 14 TiB, 15393162788864 bytes, 30064771072 sectors
Disk model: Virtual disk    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F1A69B9D-FE35-440B-8201-A9A1C670D8FB

Device       Start         End     Sectors  Size Type
/dev/sdb1     2048     4982527     4980480  2,4G Linux RAID
/dev/sdb2  4982528     9176831     4194304    2G Linux RAID
/dev/sdb3  9437184 30064566271 30055129088   14T Linux RAID


Disk /dev/mapper/osprober-linux-sdb3: 13,102 TiB, 15388226093056 bytes, 30055129088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/md2: 13,102 TiB, 15388225044480 bytes, 30055127040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

Output of mdadm --examine /dev/sd*
```
root@vincent-virtual-machine:~# mdadm --examine /dev/sd*
/dev/sda:
   MBR Magic : aa55
Partition[0] :      1048576 sectors at         2048 (type 0b)
Partition[1] :    103802882 sectors at      1052670 (type 05)
/dev/sda1:
   MBR Magic : aa55
/dev/sda2:
   MBR Magic : aa55
Partition[0] :    103802880 sectors at            2 (type 83)
mdadm: No md superblock detected on /dev/sda5.
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdb2.
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e83b0c59:a57672c5:81bc8de6:2ee43ed4
           Name : VinflixDSM:2
  Creation Time : Fri Jan 17 23:37:33 2020
     Raid Level : raid1
   Raid Devices : 1

 Avail Dev Size : 30055127040 (14331.40 GiB 15388.23 GB)
     Array Size : 15027563520 (14331.40 GiB 15388.23 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=0 sectors
          State : clean
    Device UUID : ea70f066:9d36166a:ff7b1eef:15a0369c

    Update Time : Fri May  8 16:00:55 2020
       Checksum : 7763dc4e - correct
         Events : 192


   Device Role : Active device 0
   Array State : A ('A' == active, '.' == missing, 'R' == replacing)
```

---

### Post by oldfred on 2020-05-08
Moved to the server sub-forum where users may be able to help.

---

### Post by darkod on 2020-05-09
This might be complicated because you have multiple layers... First VMware, then Synology.

I see in fdisk output there is some md2 device mentioned. Lets see what it has. Post the output of:
```
cat /proc/mdstat
sudo mdadm -D /dev/md2
```

Don't do anything else at the moment because wrong step during such rescue can make it much more difficult to save the data.

---

### Post by rihc0 on 2020-05-09
I thought so too, but it should not make a difference I think because it is a virtual disk  and it only sees the content of the virtual disk and not evetyhing under the virtual disk if you know what I'm saying. (sometimes I'm terrible at explaining things)

i have made a snapshot of the machine, I have tried some things before but nothing import. 




```
root@VinflixDSM:~# cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [raidF1] 
md2 : active raid1 sdb3[0]
      15027563520 blocks super 1.2 [1/1] [U]
      
md1 : active raid1 sdb2[0]
      2097088 blocks [12/1] [U___________]
      
md0 : active raid1 sdb1[0]
      2490176 blocks [12/1] [U___________]
      
unused devices: <none>
root@VinflixDSM:~# sudo mdadm -D /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Fri Jan 17 23:37:33 2020
     Raid Level : raid1
     Array Size : 15027563520 (14331.40 GiB 15388.23 GB)
  Used Dev Size : 15027563520 (14331.40 GiB 15388.23 GB)
   Raid Devices : 1
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sat May  9 05:30:13 2020
          State : clean 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : VinflixDSM:2  (local to host VinflixDSM)
           UUID : e83b0c59:a57672c5:81bc8de6:2ee43ed4
         Events : 192

    Number   Major   Minor   RaidDevice State
       0       8       19        0      active sync   /dev/sdb3
root@VinflixDSM:~# 
```

---

### Post by darkod on 2020-05-09
Well, that superblock looks OK. I don't know which filesystem is used. Not sure if blkid would show. Try:
```
sudo blkid
```

If the filesystem on md2 is ext4 or similar, you can try mounting it temporarily as read-only. Don't mount it for writes, to make sure nothing is written on md2 yet.
```
sudo mount -o ro /dev/md2 /mnt
ls /mnt
```

Does that show any folder structure?

The mount command might fail depending on how all of this is integrated one into the other. If this was a simple ubuntu server setup reading the array would be easy. But with VMware and Synology in the way, I don't know.

---

### Post by rihc0 on 2020-05-09
Something happend with the ubuntu virtual machine, I gotta re install it real quick

---

### Post by rihc0 on 2020-05-09
```
rihc0@rihc0-virtual-machine:~$ sudo -i
[sudo] password for rihc0: 
root@rihc0-virtual-machine:~# blkid
/dev/sda5: UUID="47bb378a-0048-4020-9309-aed57c800ec7" TYPE="ext4" PARTUUID="90e57f28-05"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sda1: UUID="5E00-3EED" TYPE="vfat" PARTUUID="90e57f28-01"
/dev/sdb1: UUID="703fe7fc-5125-5f38-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="cbe8ba00-3f3d-4d36-813c-f3c2c3a7cb09"
/dev/sdb2: UUID="60b54d3a-8cf2-9066-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="57e012c2-78a6-4857-a17e-b4d54ec8267b"
/dev/sdb3: UUID="e83b0c59-a576-72c5-81bc-8de62ee43ed4" UUID_SUB="ea70f066-9d36-166a-ff7b-1eef15a0369c" LABEL="VinflixDSM:2" TYPE="linux_raid_member" PARTUUID="d0f620c8-3760-4644-b578-55c26c8bee4e"
root@rihc0-virtual-machine:~# mount -o ro /dev/md2 /mnt
mount: /mnt: special device /dev/md2 does not exist.
root@rihc0-virtual-machine:~# ls /mnt
root@rihc0-virtual-machine:~# ls -al /mnt
total 8
drwxr-xr-x  2 root root 4096 apr 23 09:32 .
drwxr-xr-x 20 root root 4096 mei  9 13:40 ..
root@rihc0-virtual-machine:~# 


```


as you said the mount failed, i used btrfs i think, but not sure

---

### Post by darkod on 2020-05-09
Yeah but right now it failed because md2 doesn't even exist. It doesn't show in blkid.

I actually missed the part that you are you doing this in a virtual machine. I thought you took one disk and connected it to your desktop or something.

The virtual disk is reported as failed I believe. In such case I doubt a new VM would see it correctly.

But why do partitions report as "linux_raid_member" in blkid output? The VM should not see that part. VMware and then Synology will take care of the virtualization and the VMs see the vHDDs as standard disks. I don't get this...

In any case, if you want to try you need to assemble md2 first, and then try to mount read-only and check content. In case that works it would be something like:
```
sudo mdadm --assemble --verbose /dev/md2 /dev/sdb3
sudo mount -o ro /dev/md2 /mnt
ls /mnt
```

But honestly, I think you need to look at this from the start. For example, if VMware was the first thing you installed, and if it uses the big data disks as datastores, what is the status in VMware? What does it say for its datastore status?

---

### Post by rihc0 on 2020-05-09
```
root@rihc0-virtual-machine:~# sudo mdadm --assemble --verbose /dev/md2 /dev/sdb3
mdadm: looking for devices for /dev/md2
mdadm: /dev/sdb3 is busy - skipping
root@rihc0-virtual-machine:~# sudo mount -o ro /dev/md2 /mnt
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/md2, missing codepage or helper program, or other error.
root@rihc0-virtual-machine:~# ls /mnt
root@rihc0-virtual-machine:~# 
```

the datastore in ESXi seems to be okay, i can still use it and DSM also boots.

---

### Post by darkod on 2020-05-09
sdb3 might be part of differently named array now. Check again with:
```
cat /proc/mdstat
```

If both ESXi and DSM show fine, what actually crashed? Where was the raid array? Please explain little the setup.

Did you assign multiple virtual HDDs to the VM and created mdadm array from them?

I don't know DSM but since that is the next layer, check in DSM the storage status and what it says about the virtual HDD file of interest.

---

### Post by rihc0 on 2020-05-09
```
root@rihc0-virtual-machine:~# cat /proc/mdstat
Personalities : [raid1] 
md2 : active (read-only) raid1 dm-0[0]
      15027563520 blocks super 1.2 [1/1] [U]
      
unused devices: <none>
root@rihc0-virtual-machine:~# 

```

---

### Post by rihc0 on 2020-05-09
The setup:

the server Dell r720 has a raid controller, in that raid controller i have made a raid 5 virtual disk, this virtual disk has 5*4tb sas disks. 
I have installed ESXi on that virtual disk (I know should not have done that but it was my first time :( )
when esxi was installed a have made a datastore of the virtual disks called (vinflix) and it had to be formatted to VMFS5 or 6. 
when i made the DSM virtual machine i made a 14 TB virtual disk in the datastore (vinflix) and connected it to the DSM. 
the 14 tb virtual disk is a VMDK file

does this clarify things?

---

### Post by darkod on 2020-05-09
Sorry, but if that virtual HDD assigned to another VM is not readable correctly, I don't know what to do right now...

From what I read briefly DSM is storage manager and also used for virtualization. Which sort of makes it redundant to have both ESXi and DSM inside it.

Also, if I remember correctly, when installing ESXi it's better to create the raid array with ESXi, not to have it already prepared and created in the raid controller.

Anyway, not sure what the next step would be to save this because you have mixed so many technologies. The ubuntu VM shouldn't even see the raid array, it should show as standard HDD to it. VMs have no clue about the virtualization layer.

I also don't understand why you mixed up DSm at all. With ESXi already installed and one 14TB datastore, you can create VMs in VMware and that's it. You say this is Dell server and not Synology NAS so I wonder what role you planned DSM to do.

---

### Post by rihc0 on 2020-05-09
yea i know i messed up the installation, i was planning on making it better but this happend before i got the change, i think my server turned of onetime due something and DSM was shut down on a not propper way. 

this is what dsm says[ATTACH=CONFIG]285796[/ATTACH][ATTACH=CONFIG]285797[/ATTACH][ATTACH=CONFIG]285798[/ATTACH][ATTACH=CONFIG]285799[/ATTACH]

---

### Post by rihc0 on 2020-05-09
i have connected with ssh to the DSM and runned the same commands as you told before and i got different output.
```
root@VinflixDSM:~# blkid
/dev/synoboot1: SEC_TYPE="msdos" UUID="00C2-16A7" TYPE="vfat" PARTLABEL="boot" PARTUUID="43ddabd9-1b0a-4a24-a33a-b7f93d3dfe89"
/dev/synoboot2: SEC_TYPE="msdos" UUID="2016-2016" TYPE="vfat" PARTLABEL="image" PARTUUID="bcd36c68-5d88-4e89-8cf5-881cef727424"
/dev/sdm3: PARTLABEL="legacy" PARTUUID="a2977cff-866d-4ffe-8a51-9d0bdb238bb0"
/dev/sdb1: UUID="703fe7fc-5125-5f38-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="cbe8ba00-3f3d-4d36-813c-f3c2c3a7cb09"
/dev/sdb2: UUID="60b54d3a-8cf2-9066-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="57e012c2-78a6-4857-a17e-b4d54ec8267b"
/dev/sdb3: UUID="e83b0c59-a576-72c5-81bc-8de62ee43ed4" UUID_SUB="ea70f066-9d36-166a-ff7b-1eef15a0369c" LABEL="VinflixDSM:2" TYPE="linux_raid_member" PARTUUID="d0f620c8-3760-4644-b578-55c26c8bee4e"
/dev/md0: LABEL="1.42.6-23739" UUID="bdaba411-2a68-4978-8b4d-6fe37f884af5" TYPE="ext4"
/dev/md1: UUID="621c6d7e-e6c9-44df-bb40-9da3fe71bb37" TYPE="swap"
/dev/zram0: UUID="41a953dd-f79e-4b60-946e-41146df415b1" TYPE="swap"
/dev/zram1: UUID="85344dc9-de45-47bb-a9bf-01aa5f07c8e3" TYPE="swap"
/dev/zram2: UUID="6e6559e7-5cb0-4fde-839f-465bd4585e53" TYPE="swap"
/dev/zram3: UUID="23f9207e-eb7f-47f3-844f-328222b808b4" TYPE="swap"
/dev/zram4: UUID="7c3175d2-348b-415e-8459-ff8819f4a7ae" TYPE="swap"
/dev/zram5: UUID="1c659a52-9511-43cb-b6e5-7cba3688ed71" TYPE="swap"
/dev/zram6: UUID="c84f0f8e-ce27-41e0-b47b-2e27083be270" TYPE="swap"
/dev/zram7: UUID="7dc06454-960b-40eb-aeb2-83f7ff574e3b" TYPE="swap"
/dev/md2: LABEL="2020.01.17-22:37:49 v23739" UUID="96fc8365-d9a0-4278-a509-6568fde0e752" UUID_SUB="8722c636-8b79-4f7a-b40c-17683d79ddfe" TYPE="btrfs"

root@VinflixDSM:~# sudo mount -o ro /dev/md2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

root@VinflixDSM:~# dmesg | tail
[  558.589681] BTRFS: bad tree block start 0 10701049397248
[  558.589858] md/raid1:md2: syno_raid1_self_heal_set_and_submit_read_bio(1172): No suitable device for self healing retry read at round 2 at sector 21503434688
[  558.590445] md/raid1:md2: syno_raid1_self_heal_set_and_submit_read_bio(1172): No suitable device for self healing retry read at round 2 at sector 21503434712
[  558.591016] md/raid1:md2: syno_raid1_self_heal_set_and_submit_read_bio(1172): No suitable device for self healing retry read at round 2 at sector 21503434704
[  558.591599] md/raid1:md2: syno_raid1_self_heal_set_and_submit_read_bio(1172): No suitable device for self healing retry read at round 2 at sector 21503434696
[  558.592202] BTRFS: bad tree block start 0 10701049397248
[  558.592209] BTRFS error (device md2): BTRFS: md2 failed to repair btree csum error on 10701049397248, mirror = 2

[  558.593041] BTRFS: failed to read tree root on md2
[  558.607410] BTRFS: open_ctree failed

root@VinflixDSM:~# sudo mdadm --assemble --verbose /dev/md2 /dev/sdb3
mdadm: looking for devices for /dev/md2
mdadm: /dev/sdb3 is busy - skipping

root@VinflixDSM:~# sudo mount -o ro /dev/md2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

root@VinflixDSM:~# ls /mnt
root@VinflixDSM:~# cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [raidF1] 
md2 : active raid1 sdb3[0]
      15027563520 blocks super 1.2 [1/1] [U]
      
md1 : active raid1 sdb2[0]
      2097088 blocks [12/1] [U___________]
      
md0 : active raid1 sdb1[0]
      2490176 blocks [12/1] [U___________]
      
unused devices: <none>
root@VinflixDSM:~#

```

---

### Post by darkod on 2020-05-09
Hmmm... From my point of view if I understand it correctly:

1. The Disk 2 is the vmware disk presented to DSM and it's status is OK, the same as ESXi is showing you. That part looks OK.
2. However, the Volume 1 in DSM should probably be the volume created inside that Disk 2, and that Volume 1 says Crashed. This looks to be your problem, inside the DSM.

You did good with the latest intent to work inside the DSM. That is where you need to focus.

Stop trying with the mount command, I said it should work for ext filesystem, and you have btrfs inside DSM as you noticed.

Honestly, if you have backup of this data you should forget about saving it and simply destroy this server and start over again. And don't install DSM again. :)

Look at the scrrenshots, you have a storage manager without any raid redundancy or spare disks (from its point of view). It's useless to have it like that. You present single 14TB vmware disk to DSM and that's it. One disk, no raid, no spares. In such situation DSM is only one more layer of problems for you, not helping you with anything.

If you don't have a backup of the data and you desperately need it back, google around to find any type of rescue/repair procedure using ssh to VinflixDSM. Forget about the ubuntu VM. Your problem is in VinflixDSM and you need to work there to fix it.

Search for DSM repair instructions and general btrfs repair tutorials, that might help you too since the filesystem after all is btrfs.

Myself I don't have any experience with btrfs, I use ext4 only.

---

### Post by rihc0 on 2020-05-09
I know the problem but dont know how to solve it, dsm got shutdown in a bad way due something with the server. 

and this is the problem i think 
```
root@VinflixDSM:~# btrfs filesystem label /dev/md2
checksum verify failed on 10701049397248 found E4E3BDB6 wanted 00000000
checksum verify failed on 10701049397248 found E4E3BDB6 wanted 00000000
checksum verify failed on 10701049397248 found E4E3BDB6 wanted 00000000
checksum verify failed on 10701049397248 found E4E3BDB6 wanted 00000000
bytenr mismatch, want=10701049397248, have=0
Couldn't read tree root
```

but when i tried to fix it this happens. 

```
root@VinflixDSM:~# btrfs rescue zero-log /dev/md2
couldn't open RDWR because of unsupported option features (3).
ERROR: could not open ctree
root@VinflixDSM:~# 
```

you dont know how to solve this or someone who knows?

I don't want to use DSM but i don't know a good alternative for the filsm and series on my "nas", next time im gonna make the raid array in dsm it self with ext4 :P

---

### Post by darkod on 2020-05-09
We keep misunderstanding each other it seems. Now mentioning NAS confuses me.

Do you have only Dell server in your home LAN or Dell server plus Synology NAS for large storage?

Because I can see having a NAS mentioned previously.

---

### Post by rihc0 on 2020-05-09
ah, thats why i said ''nas'' it is not really a nas but i use it as a nas, what i have in my home is a dell r720 and a dell t420. 

but you dont know how to solve the error i have send in the previous post? or you dont know someone who knows?

---

### Post by darkod on 2020-05-09
From what I see here it doesn't look good...

[https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Storage/What_should_I_do_if_a_file_system_error_occurs](https://www.synology.com/en-global/knowledgebase/DSM/tutorial/Storage/What_should_I_do_if_a_file_system_error_occurs)

When you go to the link mentioned in the btrfs part:
[https://www.synology.com/en-uk/knowledgebase/DSM/tutorial/Storage/Btrfs_checksum_mismatch](https://www.synology.com/en-uk/knowledgebase/DSM/tutorial/Storage/Btrfs_checksum_mismatch)

> To resolve a checksum mismatch error:

If the Btrfs file system fails to restore the corrupted data, you will not be able to access the data. You can recover these data only if you had already backed them up to an offsite location (i.e., offsite backup) before data corruption occurred.

---

### Post by rihc0 on 2020-05-09
i cant just get rid of the checksums ? like deleting those checksums ?

---

### Post by darkod on 2020-05-09
I don't think so. That's a feature of btrfs. They help with data protection and probably the sudden poweroff left the filesystem unstable. That is why it doesn't want to mount I guess.

---

### Post by rihc0 on 2020-05-09
I guess the best option is using reclaime me data recovery :(

just keeps saying this it is kinda frustrating

```
root@VinflixDSM:~# btrfs check --repair /dev/md2
enabling repair mode
couldn't open RDWR because of unsupported option features (3).
Couldn't open file system
root@VinflixDSM:~# 


```

---

### Post by darkod on 2020-05-09
Can't synology forum help?

You don't even have a Synology NAS so it still puzzles me why and how you decide to go with DSM. From what I saw it is installed over web to the NAS. And you don't have one.

If one Dell server is using storage from another one, maybe go with simpler options like nfs or similar.

And reconsider whether you need ESXi or you can use native ubuntu virtualization like KVM. There is also ption of VirtualBox installed on ubuntu server.

Those options would give you better control over the storage, in theory.

It also depends if you can skip the server HW raid controller, which is often better to do if you want to use native mdadm.

---

### Post by rihc0 on 2020-05-09
I'm gonna ask on the synology forum for help thankyou a lot for your time and effort.

first I had a real synology nas but the hardware was just too slow.

I kinda like my esxi system, it is easy to use (normaly) and it works well (normaly)

---


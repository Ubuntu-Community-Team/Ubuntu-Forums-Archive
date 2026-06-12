---
title: "Can install Host on SSD and VMs on magnet HD?"
date: 2013-12-22
forum: Virtualisation
---

### Post by satimis on 2013-12-22
Hi all,

The price of SSD is still quite expensive.  Its booting speed is wonderful.  

I have an Intel SSD with 120G in capacity.  Would it be possible installing the host on SSD and the VMs on WD Black Label HD.  I have a spare WD Black Label HD of 1TB in capacity.  If it can work please advise how to setup this system.  TIA

Rgds
satimis

---

### Post by DuckHook on 2013-12-23
This is not difficult to do. The key is to delete the original "VirtualBox VMs" directory and then create it as a symlink to your real virtual machine directory on the HDD.

1. Install your host OS on your SSD.
2. Install VirtualBox to your host in the usual fashion (either from the repositories or using the Oracle PPA). The directory "VirtualBox VMs" will be created under your home directory as part of the install process.
3. Assuming that you've partitioned and formatted your HDD with ext4 and prepared it as your data disk, simply create a directory in it called anything you like: example "vmachines"
4. Configure this HDD partition to mount at startup with the proper entries in *fstab*
5. Delete *VirtualBox VMs* with:```
rm ~/"VirtualBox VMs"
```6. Create a symlink named *VirtualBox VMs* to the HDD directory (/path_to_directory/vmachines):```
cd ~
``````
ln -s /path_to_directory/vmachines "VirtualBox VMs"
```The usual cautions apply: case is critical, spelling is critical, etc. Thereafter, all VMs created in VirtualBox should automatically be created in your "vmachines" directory in the HDD.

---

### Post by satimis on 2013-12-23
Hi,

Lot of thanks for your detail advice.

> 
This is not difficult to do. The key is to delete the original "VirtualBox VMs" directory and then create it as a symlink to your real virtual machine directory on the HDD.

I have 4 hard drives connected on this PC:-

1)
120G SSD running (prepared for this test)

Host	Ubuntu 12.043 64bit
VirtualBox
VMs	fedora20/linuxmint16/ubuntu12.043/debian7.30 etc.

Not on LMV partitioning

2)
640G HD for data storage only

3)
2TB HD
Host	Ubuntu 12.043 64bit
VirtualBox
VMs	fedora20/linuxmint16/ubuntu12.043/debian7.30 etc.
on LVM partitioning

4)
1TB HD, prepared for this test to store VMs.

Now HD 3) can automatically detect other HDs after starting because it is on LVM partitioning.


Shall I
a) disconnect HDs 2) and 3) for this test?
b) run 'fdisk' on HD 1) to partition and format HD 4)?  And then mount it there?

Now on HD 1) (120G SSD)
$ ls /usr/share/virtualbox/```

nls                    src                     VBoxSysInfo.sh
rdesktop-vrdp-keymaps  VBoxCreateUSBNode.sh
rdesktop-vrdp.tar.gz   VBoxGuestAdditions.iso

```

$ ls /home/satimis/VirtualBox\ VMs/```

deb730dkssd00  fedora20dkssd00  mint16dkssd00  ub12043dkssd00

```
I suppose those are snapshot of VMS

$ ls /home/satimis/VirtualBox\ VMs/ub12043dkssd00/```

Logs  ub12043dkssd00.vbox  ub12043dkssd00.vbox-prev  ub12043dkssd00

```
VM images

> 
3. Assuming that you've partitioned and formatted your HDD with ext4 and prepared it as your data disk, simply create a directory in it called anything you like: example "vmachines"

I shall partition HD 4) into 2 partitons

1)
/data - 400G for data storage

2)
/vmachine - 600G

My question is;
a) Whether I can move the running VMs to /vmachine ?  Then recreate them on VirtualBox Manage (Graphic GU) using the image, ub12043dkssd00.vbox, for example ?

On HD 1) SSD
$ ls /home/satimis/VirtualBox\ VMs/```

deb730dkssd00  fedora20dkssd00  mint16dkssd00  ub12043dkssd00

```
I think those are VM folders?

$ ls /home/satimis/VirtualBox\ VMs/ub12043dkssd00/```

Logs  ub12043dkssd00.vbox  ub12043dkssd00.vbox-prev  ub12043dkssd00

```
VM images

Please advise.  Thanks

Rgds
satimis

---

### Post by DuckHook on 2013-12-23
> **satimis said:**
> Now HD 3) can automatically detect other HDs after starting because it is on LVM partitioning.Actually, both OSes including SSD (1) should be able to read LVMs (if they have been set up properly).> Shall I
a) disconnect HDs 2) and 3) for this test?This is not really necessary, but you can do so if you like. If you are concerned about inadvertently formatting the wrong HDD, then this is a good plan, but I would not bother and would simply proceed *very* carefully with things like partitioning. Before you do anything, back up your /home directory and all your VMs. You want to make sure that your worst case downside is no more than just a little wasted time restoring your backup.> b) run 'fdisk' on HD 1) to partition and format HD 4)? And then mount it there?I would simply use gparted because I find the graphical tool easier to see everything with (and therefore less prone to mistakes), but fdisk is also fine if you are sticking with MBR. If GPT partitioning, then fdisk won't work. If HD 4 is already partitioned and formatted, you don't have to repartition at all and can just use what is there now.> I suppose those are snapshot of VMSNo. Those are directories containing your actual VMs. Snapshots would appear as a subdirectory within each of those individual directories and would be called "Snapshots".> VM imagesVM images end with .vdi. VM definitions end with .vbox. Backup definitions end with .vbox-prev. Your vdi may be within the child directory "ub12043dkss00" which seems to be nested in the parent directory of the same name. In future, please post *ls* output using *ls -la* to differentiate file/directory/symlinks.> I shall partition HD 4) into 2 partitons

1)
/data - 400G for data storage

2)
/vmachine - 600GJust one partition will do if you like more flexibility. Both data and VMs can share a partition. All you need is to be able to symlink to a distinct directory, so your VMs directory doesn't have to be on its own partition, but two partitions are also okay if this is what you wish.> My question is;
a) Whether I can move the running VMs to /vmachine ? Then recreate them on VirtualBox Manage (Graphic GU) using the image, ub12043dkssd00.vbox, for example ?Using my technique, you cannot move a "running" VM. It must be powered down and dormant. And it is not as complicated as needing to recreate any VMs. Once the "VirtualBox VMs" directory is moved *and the symlink is properly created*, firing up VirtualBox will show the same VMs that you see now. Provided the symlink is named exactly the same as the directory that currently exists (i.e. it *must* be called *VirtualBox VMs*), then VirtualBox is "fooled" into sensing absolutely no change in its environment.> I think those are VM folders?> VM images...repeated questions from above? See answers above.

---

### Post by satimis on 2013-12-25
Hi DuckHook and all,

Merry Christmas

Performed following steps

$ sudo fdisk -l```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cde8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c92e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c92e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    58593279    29295616   83  Linux
/dev/sdb2        58595326    89843711    15624193    5  Extended
/dev/sdb3        89843712  1953520064   931838176+  83  Linux
/dev/sdb5        58595328    89843711    15624192   82  Linux swap / Solaris

Disk /dev/mapper/localhost-root: 85.5 GB, 85513469952 bytes
255 heads, 63 sectors/track, 10396 cylinders, total 167018496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/localhost-root doesn't contain a valid partition table

Disk /dev/mapper/localhost-swap_1: 34.3 GB, 34259075072 bytes
255 heads, 63 sectors/track, 4165 cylinders, total 66912256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/localhost-swap_1 doesn't contain a valid partition table
```


$ sudo fdisk -l | grep '^Disk'```

Disk /dev/mapper/localhost-root doesn't contain a valid partition table
Disk /dev/mapper/localhost-swap_1 doesn't contain a valid partition table
Disk /dev/sda: 120.0 GB, 120034123776 bytes
Disk identifier: 0x000cde8a
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
Disk identifier: 0x000c92e3
Disk /dev/mapper/localhost-root: 85.5 GB, 85513469952 bytes
Disk identifier: 0x00000000
Disk /dev/mapper/localhost-swap_1: 34.3 GB, 34259075072 bytes
Disk identifier: 0x00000000

```


Install gparted:
===============
$ sudo apt-get install gparted


$ sudo lshw -C disk```

  *-disk:0                
       description: ATA Disk
       product: INTEL SSDSC2CT12
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 300i
       serial: CVMP241104R8120BGN
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000cde8a
.....
  *-disk:1
       description: ATA Disk
       product: WDC WD1002FAEX-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 05.0
       serial: WD-WCATR2913437
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c92e3

```

On terminal;

$ sudo gparted
see Screenshot_01.png

right-click following devices;
/dev/sdb1
/dev/sdb2 (Resize/Move available)
/dev/sdb3
unallocated
-> "Delete" grayout without function.  

right-click following device;
/dev/sdb5
-> "Delete" and "Resize/Move" are available


Delete /dev/sdb5
see Screenshot_02.png


Now right-click on;
/dev/sdb2
-> "Delete" and "Resize/Move" are available

Delete /dev/sdb2
see Screenshot_03.png

-> Edit -> Apply All Operatons
-> Apply

see Screenshot_04.png

Save gparted_details.htm on /home/satimis/Pictures


/dev/sdb1 and /dev/sdb3
Right-click
-> "Delete" and "Resize/Move" are still grayout

Unmount /dev/sdb1 and /dev/sdb3
Right-click again
-> "Delete" and "Resize/Move" are now available

Delete both of them

-> Edit -> Apply All Operations

Success
Save Details "gparted_details_02.htm"

see Screenshot_05.png


Right-click on;
"unallocated"
-> New

Create as:  Primary Partition
File system:  ext4
Label:  blank
-> Add
-> Apply Pending Operation

Successful

see Screenshot_06.png

-> Quit gparted


I'm prepared to create One Partition

see Screenshot_07.png


$ ls -ald /media/7b9187d7-c139-4b7c-b893-0971b451261a/```

drwxr-xr-x 3 root root 4096 Dec 25 19:49 /media/7b9187d7-c139-4b7c-b893-0971b451261a/

```

Before proceeding further I have following 2 questions:

1)
whether I should run;
$ sudo chown -R satimis:satimis /media/7b9187d7-c139-4b7c-b893-0971b451261a/
?
to change permission

satimis is the user/admin of the SSD

2)
How to label "7b9187d7-c139-4b7c-b893-0971b451261a" with a shorter name easy to recognise?  I'm prepared adding 2 folders on this HD, say;
- VirtualBox VM (for VMs)
- Data (for storage of data files)


Hoping to have your suggestion.  TIA

(Screenshot_06/07 will be attached on another posting because only 5 files being allowed to upload per posting.

Rgds
satimis

---

### Post by satimis on 2013-12-25
Continued:-

Screenshot_06.png and Screenshot_07.png being attached to this posting

satimis

---

### Post by MartyBuntu on 2013-12-25
You don't need to do any of that.

You can assign default machine storage in the preferences tab.
I have a 60GB SSD and a 320GB storage drive dedicated to VirtualBox installs.

---

### Post by satimis on 2013-12-26
> **MartyBuntu said:**
> You don't need to do any of that.

You can assign default machine storage in the preferences tab.
I have a 60GB SSD and a 320GB storage drive dedicated to VirtualBox installs.
Hi,

Thanks for your advice.

Performed following steps;

On
-> Preference -> General
Default Machine Folder:
/media/7b9187d7-c139-4b7c-b893-0971b451261a/VirtualBox VMs (changed to)

VRDP Authentication Library: VBoxAuth

Installed OpenSUSE 13.1 but found;
$ ls -al /home/satimis/VirtualBox\ VMs/```

total 28
drwxrwxr-x  7 satimis satimis 4096 Dec 26 13:30 .
drwxr-xr-x 42 satimis satimis 4096 Dec 26 21:52 ..
drwxrwxr-x  3 satimis satimis 4096 Dec 22 19:08 deb730dkssd00
drwxrwxr-x  3 satimis satimis 4096 Dec 23 11:37 fedora20dkssd00
drwxrwxr-x  3 satimis satimis 4096 Dec 23 11:36 mint16dkssd00
drwxrwxr-x  3 satimis satimis 4096 Dec 27 01:36 opensuse13.1dkc800
drwxrwxr-x  3 satimis satimis 4096 Dec 23 11:36 ub12043dkssd00

```
opensuse13.1 still installed on previous folder.

```

drwxrwxr-x  3 satimis satimis 4096 Dec 22 19:08 deb730dkssd00
drwxrwxr-x  3 satimis satimis 4096 Dec 23 11:37 fedora20dkssd00
drwxrwxr-x  3 satimis satimis 4096 Dec 23 11:36 mint16dkssd00
drwxrwxr-x  3 satimis satimis 4096 Dec 23 11:36 ub12043dkssd00

```
were installed before editing "Default Machine Folder"

Whether I need to delete all of them first before installing OpenSUSE 13.1.  That is I have to start all from the beginning?

Rgds
satimis

---

### Post by MartyBuntu on 2013-12-26
Just move the previous machines to the new machine folder.

You may have to go into the settings to adjust a few things...maybe not. Just copy them over, don't delete any of them until you're satisfied with the changes.

---

### Post by satimis on 2013-12-27
> **MartyBuntu said:**
> Just move the previous machines to the new machine folder.

You may have to go into the settings to adjust a few things...maybe not. Just copy them over, don't delete any of them until you're satisfied with the changes.
Hi,

fedora20dkssd00```

Snapshot Folder:
/home/satimis/VirtualBox VMs/fedora20dkssd00/Snapshots

```

deb730dkssd00```

Snapshot Folder:
/home/satimis/VirtualBox VMs/deb730dkssd00/Snapshots

```

mint16dkssd00```

Snapshot Folder:
/home/satimis/VirtualBox VMs/mint16dkssd00/Snapshots

```

ub12043dkssd00```

Snapshot Folder:
/home/satimis/VirtualBox VMs/ub12043dkssd00/Snapshots

```

opensuse13.1dkc800```

Snapshot Folder:
/media/7b9187d7-c139-4b7c-b893-0971b451261a/VirtualBox VMs

```


$ ls -ald /media/7b9187d7-c139-4b7c-b893-0971b451261a/VirtualBox\ VMs/```

drwxr-xr-x 2 root root 4096 Dec 26 13:55 /media/7b9187d7-c139-4b7c-b893-0971b451261a/VirtualBox VMs/

```
I think the problem is here.  The folder is owned by "root"

Performed following steps:

$ sudo chown -R satimis:satimis /media/7b9187d7-c139-4b7c-b893-0971b451261a/VirtualBox\ VMs/

It is impossible moving the VM from folder-A to folder-B.  Even changing Snapshot Folder path.  On starting the VM

Warning:```

Failed to save the settings of the virtual machine opensuse13.1dkc800 to /home/satimis/VirtualBox VMs/opensuse13.1dkc800/opensuse13.1dkc800.vbox.

Runtime error opening '/home/satimis/VirtualBox VMs/opensuse13.1dkc800/opensuse13.1dkc800.vbox-tmp' for reading: -102(File not found.).

/home/vbox/vbox-4.3.6/src/VBox/Main/src-server/MachineImpl.cpp[10355] (nsresult Machine::saveSettings(bool*, int)).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: SessionMachine
Interface: IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}

```

IIRC I encountered the same problem several years before after moving VM and/or changing the name of VM.  I edited a *.xml file to fix the problem.  Unfortunately I couldn't recollect which *.xml file.

Either one of following method can move VM from folder-A to folder-B

1)
Create a new VM using the .vdi as source

OR

2)
Export the VM as .ova and import it again.

The only disadvantage is original VM name couldn't be retained.

Rgds
satimis

---


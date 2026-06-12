---
title: "Migrate your Ubuntu OS drive to a RAID-1 array"
date: 2011-08-25
forum: Tutorials
---

### Post by YesWeCan on 2011-08-25
[SIZE=4]**[COLOR=#000080]Migrate your Ubuntu OS drive to a RAID-1 array[/COLOR]**[/SIZE]

 [SIZE=2][COLOR=DarkSlateGray][FONT=Arial, sans-serif]last updated: 8 September 2011 by YesWeCan[/FONT][/COLOR][/SIZE]

 [FONT=Arial][SIZE=4][COLOR=#000080]Summary[/COLOR][/SIZE][/FONT]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Hi there. There are lots of guides around for installing Ubuntu to a RAID array from scratch. This guide shows you how to migrate an existing Ubuntu installation from a single drive to a RAID-1 array so you do not have to do a complete reinstall.[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The new array will use your original drive plus a new one and use mdadm with LVM volumes. The new array is created, degraded (one drive only), before your original disk is reformatted. This means you will be able to try out the new array and make sure it is working fine before you decide to switch over to it permanently.[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]For simplicity, this tutorial assumes you have root, home and swap partitions and no others.[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This tutorial has been verified using Ubuntu 10.10 and 11.04.[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][COLOR=#000080]*Estimated time to complete:*[/COLOR] 1 to 2 hours[/SIZE][/FONT][/COLOR]
 [SIZE=4][B][COLOR=#000080][FONT=Arial, sans-serif]

[/FONT][/COLOR][/B][COLOR=#000080][FONT=Arial, sans-serif]Prerequisites[/FONT][/COLOR][/SIZE]
 
[LIST]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You     are not a complete beginner. You are familiar with using the command     line, you understand drive and partition naming     conventions, you are familiar with Disk Utility and you have some     basic knowledge of mdadm and lvm.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You     have safely backed up any vital data. [COLOR=#ff0000]**Warning!**[/COLOR]     Some of the commands in this tutorial are capable of wiping out your     entire drive if you make a mistake.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Your     original drive has an MBR format (not GPT) and is BIOS booted (not     UEFI).[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Your     original drive has 3 partitions of interest: root, home and swap. It     contains no previous LVM, mdraid, Windows or dmraid metadata. Your     motherboard has RAID options disabled.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You     have a second drive that you are happy to reformat that is big     enough to contain the contents of the first; typically you would use     a drive of the same capacity.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You     have a live CD or USB of the same Ubuntu version as your OS.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You     have an internet connection.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Your     OS uses the Grub2 boot-loader (this tutorial does not work for     legacy Grub)[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Your     OS is Ubuntu 10.04 or newer.[/SIZE][/FONT][/COLOR]
[/LIST]
 

 [SIZE=4][COLOR=#000080][FONT=Arial, sans-serif]Method[/FONT][/COLOR][/SIZE]

 [SIZE=3][COLOR=#000080][FONT=Arial, sans-serif]**Prepare your new drive**[/FONT][/COLOR][/SIZE]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]1. Back     up vital files somewhere safe before you begin.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
2. Connect     up your new drive.[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]3. Boot     into your existing Ubuntu OS on your original drive[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
4. Open     a terminal and install the linux RAID and LVM utilites. You will be     asked to configure Postfix &#8211; choose &#8220;no configuration&#8221; if you     are unsure what this means.[/SIZE][/FONT][/COLOR]
     ```
sudo apt-get install mdadm lvm2
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?     This is a convenience so that when your original drive contents are     copied to the new drive OS, it will already have mdadm and LVM     installed and properly configured.[/SIZE][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

5. Use     **Disk Utility** to reformat the new drive:[/SIZE][/FONT][/COLOR]
     [COLOR=#000000]
&#8220;[FONT=Arial, sans-serif][SIZE=2]Format     Drive&#8221; to write a new Master Boot Record[/SIZE][/FONT][/COLOR]
     [COLOR=#000000]&#8220;[FONT=Arial, sans-serif][SIZE=2]Create     Partition&#8221; to m[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]ake     a partition [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]of     type &#8220;Empty&#8221;[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2].     Th[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]e size     of this partition [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]will     be [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]the     size of your whole[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     RAID array so [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]make     it[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2] big     enough for your needs but no bigger than your [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]original     drive capacity[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2].     If [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]your     new drive[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     is the same size as [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]the     original[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     you can just use the whole d[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]rive [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]for your     partition [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]if     you wish.[/SIZE][/FONT][/COLOR]
     [COLOR=#000000]&#8220;[/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Edit     Partition&#8221; to set the partition[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]     type [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]to[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]     &#8220;Linux RAID [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]au[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]todetect&#8221;.[/SIZE][/FONT][/COLOR]

     [SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]Why?     This drive will be formatted for use as a member of a RAID array by     creating a partition on it and allocating that partition to mdadm.     The partition must not be bigger than will fit on the original drive     and must be at least big enough to hold your original root, home and     swap space. You may create more partitions for other uses in the     future.[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]      [SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]The     &#8220;linux RAID autodetect&#8221; designation is not strictly necessary     because this designator is no longer used by the kernel during boot.     But it is a handy type because it distinguishes your RAID partitions     from others when you run commands like sfdisk.[/FONT][/COLOR][/SIZE]

  [SIZE=2]
[/SIZE]  [SIZE=3][COLOR=#000080][FONT=Arial, sans-serif]**Duplicate your files on a degraded array**[/FONT][/COLOR][/SIZE]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
6. Boot     off your live CD or USB[/SIZE][/FONT][/COLOR]
     [SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]Why?     It is not recommended to copy your root file system while it is     running because some files may change during the copy.[/FONT][/COLOR][/SIZE]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
7. Open     a terminal and become root[/SIZE][/FONT][/COLOR]
     ```
sudo -s
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

8. Install     mdadm and lvm. You will be asked to configure Postfix &#8211; choose &#8220;no     configuration&#8221;.[/SIZE][/FONT][/COLOR]
     ```
apt-get install mdadm lvm2
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=2]Why?     The Ubuntu live ISO does not come with mdadm and LVM pre-installed.[/SIZE][/FONT][/COLOR]

[COLOR=#000000][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2][COLOR=Black]9. [/COLOR]**Important!**[/SIZE][/FONT][/COLOR][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]**Check     your drive names.**[/SIZE][/FONT][/COLOR][FONT=Arial, sans-serif][SIZE=2]     These instructions assume [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]your     original d[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]rive     [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]is[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     sda and [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]your     new [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]d[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]rive[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     is sdb. [/SIZE][/FONT][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]**Change     as **[/SIZE][/FONT][/COLOR][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]**needed**[/SIZE][/FONT][/COLOR][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]**.**[/SIZE][/FONT][/COLOR][/COLOR]
     ```
sfdisk -luM
```     [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Make     a note of the partition numbers of your root, home and swap     partitions. You will need these in step 14.[/SIZE][/FONT][/COLOR]

     [SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]Why?     The naming of devices when you boot will depend on which you booted     first and how your BIOS decides to name them. Eg: it is possible     when you boot your original drive that it is named sda but when you     boot off another drive its name will have changed. You it is prudent     on each reboot to double-check what the names are. If you get this     wrong you will copy files to the wrong place and you may destroy     valuable data.[/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

10. Create     a degraded array on [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]the     new drive [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2](you     may choose a different array device name [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]than     [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]md0     [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]as     long as you are consistent in the rest of the tutorial[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]).[/SIZE][/FONT][/COLOR]
```
mdadm -vC /dev/md0 --level=1 -n2 /dev/sdb1 missing
mdadm -Ds
```[FONT=Arial][COLOR=#000000][SIZE=2]You     should see a single line similar to this but with a different UUID:[/SIZE][/COLOR][/FONT][COLOR=Navy][SIZE=2][FONT=Arial, sans-serif]
[/FONT][/SIZE][/COLOR][SIZE=2][COLOR=Navy][FONT=Arial, sans-serif]ARRAY /dev/md0 metadata=1.2 name=ubuntu:0 UUID=12345678:9ABCDEF0:12345678:9ABCDEF0[/FONT][/COLOR][/SIZE][COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1]

[SIZE=2]Why?     The mdadm.conf file tells mdadm what device name to give array that     it assembles during boot. If you do not specify one, in this case     /dev/md0, then it will choose an arbitrary one such as /dev/md127.     We want it to be a specific name that we recognize so that our mount     directive in fstab always works.[/SIZE][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]11. Declare[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     the RAID device an LVM physical volume and add it to a volume group     [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2](y[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]ou     may [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]choose[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     a different volume group name to &#8220;system&#8221; [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]as     long as you are consistent in the rest of the tutorial[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2])[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2].[/SIZE][/FONT][/COLOR]
```
pvcreate /dev/md0
vgcreate system /dev/md0
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?     Logical Volume Manager allows you to create one or more volume     groups that concatenate physical partitions and allows you to     subdivide them into logical volumes.[/SIZE][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=1][SIZE=2]

12. C[/SIZE][SIZE=2]reate     logical volumes (partitions). For simplicity, this tutorial assumes     you need only a root, [/SIZE][SIZE=2]home and swap[/SIZE][SIZE=2]     volume. You may make as many volumes as you like. You should specify     the size you want for each volume.[/SIZE][/SIZE][/FONT][/COLOR]
```

lvcreate  -n swap  -L 8G     system
lvcreate  -n root  -L 15G    system
lvcreate  -n home  -L 120G  system
```[SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]Why?     Your volume sizes do not have to be the same as the partition sizes     on your original drive but must be big enough to contain their     contents. You do not have to use the full size of your volume group.     You may create additional volumes now or later and you may resize     volumes later. The swap space is a volume within the RAID both for     convenience and so your system will continue to function properly in     the event that a drive fails while swap space is being used.[/FONT][/COLOR][/SIZE] 

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]13. Format     the new volumes. Ignore the bootbits warning.[/SIZE][/FONT][/COLOR]
```
mkswap        /dev/system/swap
mkfs.ext4     /dev/system/root
mkfs.ext4     /dev/system/home
```[SIZE=2][COLOR=#b80047][FONT=Courier 10 Pitch][COLOR=#004a4a][FONT=Arial, sans-serif]Why?     [/FONT][/COLOR][COLOR=#004a4a][FONT=Arial, sans-serif]LVM     volumes are like real partitions and must be formatted (BTW this is     true even if the volume group comprises physical partitions that     were already formatted).[/FONT][/COLOR][/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

14. Mount     the original drive partitions and the new drive's logical volumes.     This assumes that your original root is sda1, your original home is     sda2 and your original swap is sda3. [COLOR=#ff0000]**Change     as **[/COLOR][COLOR=#ff0000]**needed**[/COLOR][COLOR=#ff0000]**.**[/COLOR][/SIZE][/FONT][/COLOR]
```
mkdir  /mnt/oldRoot  /mnt/oldHome  /mnt/root  /mnt/home
mount  /dev/sda1         /mnt/oldRoot
mount  /dev/sda2         /mnt/oldHome
mount  /dev/system/root  /mnt/root
mount  /dev/system/home  /mnt/home
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

15. Copy your existing files across
    Be careful to include the trailing / and visually check that the directories look the same afterwards.
    The rsync -v option lists all files as it copies. This will slow down the copy so omit if desired.[/SIZE][/FONT][/COLOR]
```
rsync -avx   /mnt/oldRoot/  /mnt/root/
rsync -avx   /mnt/oldHome/  /mnt/home/

umount   /mnt/oldRoot    /mnt/oldHome
```[COLOR=#b80047][FONT=Courier 10 Pitch][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?[/SIZE][/SIZE][/FONT][/COLOR][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]The     original d[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]rive[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]     partitions are unmounted immediately after the copy [/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]as     a precaution to protect the[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]m[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif].[/FONT][/COLOR][/SIZE][/SIZE][/FONT][/COLOR] 


 [COLOR=#000080][FONT=Arial, sans-serif][SIZE=3]**Make the array bootable**[/SIZE][/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]16. Modify     fstab so that the LVM volumes are mounted at boot.[/SIZE][/FONT][/COLOR]
```
gedit  /mnt/root/etc/fstab
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]It     should have these entries:[/SIZE][/FONT][/COLOR]
```
proc                            /proc   proc   nodev,noexec,nosuid   0    0
/dev/mapper/system-root         /       ext4   errors=remount-ro     0    1
/dev/mapper/system-home         home    ext4   defaults              0    2
/dev/mapper/system-swap         none    swap   sw                    0    0

```[SIZE=2][COLOR=#b80047][FONT=Courier 10 Pitch][COLOR=#004a4a][FONT=Arial, sans-serif]Why?     [/FONT][/COLOR][COLOR=#004a4a][FONT=Arial, sans-serif]Your     original d[/FONT][/COLOR][COLOR=#004a4a][FONT=Arial, sans-serif]rive[/FONT][/COLOR][COLOR=#004a4a][FONT=Arial, sans-serif]     will have mounted by device name like /dev/sda or UUID. With LVM the     mount can be described more simply by using the volume group and     logical volume names.[/FONT][/COLOR][/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

17. Add     the new array details to the mdadm configuration file [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]so     that the array reassembles with the correct [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]device     [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]name     at boot time[/SIZE][/FONT][/COLOR]
```
mdadm -Ds >> /mnt/root/etc/mdadm/mdadm.conf
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

18. Chroot     into the new root file system:[/SIZE][/FONT][/COLOR]
```
mount -B /dev      /mnt/root/dev
mount -B /dev/pts  /mnt/root/dev/pts      
mount -B /sys      /mnt/root/sys
mount -B /proc     /mnt/root/proc      
chroot /mnt/root
```[COLOR=#b80047][FONT=Courier 10 Pitch][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?     [/SIZE][/SIZE][/FONT][/COLOR][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]Chroot     is a method that allows us to execute commands in the new file     system approximately as if we were booted into it. The new file     system still has boot loader and boot files copied from the     original. These will no longer work because the new filesystem uses     RAID and LVM and is on a different d[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif]rive[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#004a4a][FONT=Arial, sans-serif].     The following commands update those files.[/FONT][/COLOR][/SIZE][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][SIZE=2]
[/SIZE] 
19. Update     [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]Grub[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]'s     configuration file[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     and [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]install     it to the new MBR so that the new d[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]rive[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     will boot.[/SIZE][/FONT][/COLOR]
```
update-grub          
grub-install /dev/sdb
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

20. Update     the initial RAM filesystem to register these changes[/SIZE][/FONT][/COLOR]
```
update-initramfs -u
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

21. Leave     a marker so that in step 23 you can be sure you've booted the     degraded array[/SIZE][/FONT][/COLOR]
```
touch  thisIsTheRaidDrive
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

22. And     exit the chroot & root[/SIZE][/FONT][/COLOR]
```
exit
exit
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

23. Shutdown     and set your bios to boot the new drive. You should see a Grub2 menu     that has choices of your new Ubuntu (first entry) and your old     Ubuntu and memtest. There may be a warning message and/or approval     required to boot from a degraded array. At the login screen sign in     and check your marker to verify this is the new array (and not your     original OS) with [COLOR=Navy]ls /[/COLOR]. You may want to check everything looks     normal and your files are where they should be.[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

This     is a suitable point to pause the tutorial if you want. You can still     boot the original OS if you need to and you can continue to boot the     new OS on degraded RAID indefinitely.[/SIZE][/FONT][/COLOR] 


 [COLOR=#000080][FONT=Arial, sans-serif][SIZE=3]**Add Your Original Drive to the Array**[/SIZE][/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]24. Make     sure you have booted the new[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     RAID drive[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2](check     for [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]your[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]     marker with [COLOR=Navy]ls /[/COLOR])[COLOR=#ff0000][B].

[/B][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#000000][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]**Important!     Check your drive names.**[/SIZE][/FONT][/COLOR][FONT=Arial, sans-serif][SIZE=2]**     These instructions assume **[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**your     **[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**RAID**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**drive     **[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**is     **[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**now     **[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**sd**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**a**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**     and your original **[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**drive**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**is     sd**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**b**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**.     **[/SIZE][/FONT][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]**Change     as needed.**[/SIZE][/FONT][/COLOR][/COLOR]
```
sudo -s
sfdisk -luM
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?     The naming of drives when you boot will depend on which you booted     first and how your BIOS decides to name them. Eg: it is possible     when you boot your CD your original drive is named sda but when you     boot the RAID drive its name will have changed. You it is prudent on     each reboot to double-check what the names are. If you get this     wrong you will copy files to the wrong place and you may destroy     valuable data.[/SIZE][/SIZE][/FONT][/COLOR] [SIZE=2]
[/SIZE] 
[COLOR=#000080][FONT=Arial, sans-serif][SIZE=2][COLOR=#ff0000]**WARNING:     Your original d**[/COLOR][COLOR=#ff0000]**rive**[/COLOR][COLOR=#ff0000]**     will **[/COLOR][COLOR=#ff0000]**now **[/COLOR][COLOR=#ff0000]**be     erased**[/COLOR][COLOR=#ff0000]**.**[/COLOR][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

25. Check     that the partition table you are about to change is that of your     original drive[/SIZE][/FONT][/COLOR]
```
sfdisk -d /dev/sdb
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?     A double-check to make sure you are using the correct name for your     original drive so you don't accidentally erase the wrong one![/SIZE][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

26. Copy     the RAID drive's partition table to the original drive[/SIZE][/FONT][/COLOR]
```
sfdisk -d /dev/sda | sfdisk /dev/sdb
hdparm -z /dev/sdb
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=1][SIZE=2]Why?     This is a quick and accurate way to duplicate the partition     locations and sizes and will ensure the original drive can be added     to the array.[/SIZE][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

27. Add     the old drive to the array and start the resync[/SIZE][/FONT][/COLOR]
```
mdadm /dev/md0 --add /dev/sdb1
```[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

28. Watch     the resync progress[/SIZE][/FONT][/COLOR]
```
watch cat /proc/mdstat
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=2]Why?     It can take some time for the contents of the array to be copied to     the original drive. This is a handy way to see it progressing. You     may use your system as normal; you do not need to wait for this to     finish. You can even reboot before it has finished and it will pick     up from where it left off. However, you should not try to boot the     original drive on its own before the resync has completed.[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

29. Reconfigure     Grub's install package. In the menu be sure to select &#8220;Grub     install devices&#8221; /dev/sda and /dev/sdb (or whatever the names of     your drives are).[/SIZE][/FONT][/COLOR]
```
dpkg-reconfigure grub-pc
```[COLOR=#004a4a][FONT=Arial, sans-serif][SIZE=2]Why?     The package update manager needs to know about changes you have made     so that a future upgrade will install Grub properly. You also need     to make sure Grub is installed to the MBR areas of both drives so     that you can boot off either one in the event of a failure. Although     Grub was already installed to the new drive in step 19, tell the     package manager to install it there again anyhow.[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

30. Once     the resync has finished, you should confirm that you can boot off     either drive and boot degraded off either with the other     disconnected.[/SIZE][/FONT][/COLOR][COLOR=#000080][FONT=Arial, sans-serif][SIZE=2]

That's     it! :)
[/SIZE][/FONT][/COLOR] 


 [SIZE=3][COLOR=#000080][FONT=Arial, sans-serif]Useful Links[/FONT][/COLOR]
[/SIZE] 
 [COLOR=#000080][FONT=Arial, sans-serif][SIZE=2]Grub2, Ubuntu Community Documentation: [COLOR=#000000]_[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)_[/COLOR][/SIZE][/FONT][/COLOR]
 [COLOR=#000080][FONT=Arial, sans-serif][SIZE=2]LVM How-to:[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)_[/SIZE][/FONT][/COLOR]
 [COLOR=#000080][FONT=Arial, sans-serif][SIZE=2]L[/SIZE][/FONT][/COLOR][COLOR=#000080][FONT=Arial, sans-serif][SIZE=2]inux RAID [/SIZE][/FONT][/COLOR][COLOR=#000080][FONT=Arial, sans-serif][SIZE=2]wiki[/SIZE][/FONT][/COLOR][COLOR=#000080][FONT=Arial, sans-serif][SIZE=2], kernel.org:[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)_[/SIZE][/FONT][/COLOR]

---

### Post by Rob_H on 2012-01-28
Thank you for this! I am still trying to decide whether I want to migrate or just reinstall, but at least now I know what I'd be up against.

---


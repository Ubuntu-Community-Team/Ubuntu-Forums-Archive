---
title: "Convert my Asus u30jc physical machine to Virtualbox Virtual Machine"
date: 2012-02-27
forum: Virtualisation
---

### Post by jao_madn on 2012-02-27
Recently i upgraded my ubuntu lucyd 32 to 64 bit. in order to still used  my 32bit lucyd i decided to convert it to virtualbox VM. Below are my  steps and action taken to convert my physical machine which is asus  u30jc ubuntu 10.04 32bit to Virtualbox VM. Althought there are steps  taken thats been realized in the end that can be shortend. Please  forgive me for my English.

Steps/Path taken to convert my Asus u30jc Physical Lucyd 10.04 32bit ubuntu to VirtualBox VM
```
Physical Machine Properties
Hard disk:
    Disk /dev/sda: 500.1 GB, 500107862016 bytes
    255 heads, 63 sectors/track, 60801 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x76692ca

       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1               1        1912    15357116   83  Linux    (backtrack)
    /dev/sda2   *        1913       17113   122096640    7  HPFS/NTFS    (windows 7 64bit)
    /dev/sda3           17113       60802   350928897    f  W95 Ext'd (LBA)    extended partition
    /dev/sda5           17113       32411   122884717+   7  HPFS/NTFS    (Data partition)
    /dev/sda6           32412       42609    81915403+  83  Linux    (linux backup repositories)
    /dev/sda7           42610       45159    20480000   83  Linux    (root lucyd 32bit)
    /dev/sda8           45160       55358    81920000   83  Linux    (home lucyd 32&64bit)
    /dev/sda9           55359       58889    28362726   83  Linux    (linux backup repositories)
    /dev/sda10          58890       60801    15358108+  83  Linux    (lucyd 10.04 64bit)

    /dev/sda7: UUID="87de5c1e-8c48-4ea3-861f-03e8fce294ea" TYPE="ext4" 
    /dev/sda8: UUID="c42933d5-57c7-41cc-970b-b83ee8e09e96" TYPE="ext4"

```1.  Image the root partition /dev/sda7 using ddrescue, then convert the  image file using command "VBoxManage convertdd raw.img raw.vdi" into a  vdi
    Note: after trying to boot the converted_image_root.vdi in  virtualbox error msg indicates that no bootable media around. After  attach vdi to other VM it shows
    doesn't have a valid partition  table.Possible reason: since its a partition /dev/sda7 in the physical  machine maybe the partition table doesn't reside on it.
2. Create a  Virtual Machine with HD vdi the same size of the actual physical HD and a  second HD vdi for home since our home resides on other partition.
     Home vdi size doesn't matter the importance is that all the remaining  files would fit on the vdi(remaining files means i already transfer  those important
    files on the 64bit home directory the remaining  is a handful of directory, files, hidden files required for the system  to boot in normal 32bit desktop)
3. Mount the two newly created vdi  from the new virtual machine created in the other working linux VM, use  gparted to create a partition table and 
    a valid partition on the two vdi drive. /dev/sdb1 & /dev/sdc1
4.  For root, partition mount the converted vdi image (it doesn't have a  valid partition table but is mountable) and the first vdi of the newly  created VM 
    on other linux VM and boot the other linux VM. In the  linux command line of the other linux VM used rsync command to copy the  root files on the first
    newly creacted VM vdi "rsync -a /dev/sdb/ /dev/sdc1/
5.  For home, in my case i mount as shared folder the remaining home dir  & files on the other linux VM and rsync all the home to the second  newly created vdi HD
    rsync -a <other VM mount shared folder location> /dev/sdc1/
     Note: in this process i guess you can accomplished in many ways as an  example by taring the 32bit home dir and untar it in the second vdi or
     other steps it doesnt matter since i believe inside the remaining 32bit  home are dir/files/hidden file. the important is you copy all  dir/file/hidden files of
    32bit home inside the newly created second vdi HD
6.  After finish copied all the root and home HD to the two newly created  VDI HD. Install the grub boot loader in the first vdi HD or the root vdi
  ```
  Steps: mount /dev/sdb1 /mnt
            grub-install --root-directory=/mnt/ /dev/<sdb or sdb1>
            umount /mnt
    Change the UUID in the fstab in the mounted root with the correct UUID or the same UUID of the root vdi and home vdi
```7.  On my experience when i booted the newly created VM which the root and  home VDI attach it throws an error about loading modules something like  error in 
    /procs blah blah..the important is follow the message  and find some hints to point you on some of the possible solution. In my  case it show something in the
    UUID so i change the UUID to the original or the same in the physical UUID used tune2fs command
    "tune2fs /dev/sdb1 -U <your desired UUID>
8 Boot again and works fine my physical machine 32bit converted to virtualbox VM
9.  In addition i used two vdi HD for root and home. and the root is the  same size as the physical machine so i convert it to one vdi which is  partition with
    root and home.
    Steps:
    1. used clonezilla since it can clone HD in which only the size of the used space will be copied to other VDI HD
     2. Create a single VDI HD with the space that fits the root and home  partition size. Partition this VDI HD to root and home using gparted.
    3. used clonezilla local-device-partition to local-device -partition cloning
    4. clone the root and home VDI hd to single VDI hd with two partition:
        /dev/sdb1 to /dev/sda1 -- root
        /dev/sdc1 to /dev/sda1 -- home
    5. Install again the grub boot loader.

How about your physical to virtual conversion?

---

### Post by CharlesA on 2012-02-27
It would have been easier to just image the whole drive with something like Clonezilla and restore it to a VM.

Less steps, but you'd need at least a 500GB virtual drive for it to work.

---

### Post by jao_madn on 2012-02-28
> **CharlesA said:**
> It would have been easier to just image the whole drive with something like Clonezilla and restore it to a VM.

Less steps, but you'd need at least a 500GB virtual drive for it to work.

@ CharlesA: i bet your right. Im expecting this question also. This is one of the option i consider before i start. On my case, which i forget to add is that i stop using clonezilla when backup imaging my root for some reason clonezilla will stop working  if a partition or drive resides a bad sector which i had. Usually i used clonezilla before. thats why i used dd or ddrescue for imaging root backup

By the way thanks for interest in replies...

---


---
title: "Shrinking a virtual disk with Ubuntu and Vmware player"
date: 2012-11-10
forum: Virtualisation
---

### Post by idman6 on 2012-11-10
[B]HOW TO REDUCE THE SIZE OF A VMWARE VIRTUAL DISK THAT HAS THE ROOT 
PARTITION WHICH IS ALMOST AS SAME SIZE AS THE DISK ITSELF[/B]
(the good thing is you only need VmwarePlayer)

----- My Virtual OS is Ubuntu 10.04 LTS (it maybe different for you)
----- I use VmPlayer 2.5.1 (other versions higher than mine should be ok too)
----- My Virtual Disk Size is 64GB (desired final size is 15GB)


Before starting, go into the /boot folder of root file system and save all the file 
names somewhere else in case something goes wrong and you need to a manual boot with
"grub". It is not essential but it will save you time.

Also backup all of your data in case they get corrupted.

!!! Before reducing the size of your root partition, make sure you do not set a new size
smaller than the total size of all the file in your root partition. !!!

**A)** Virtual Machine Setup;
   We will add a new virtual disk with size which we think to be our final disk size,
   let's make it 16 Gbytes. 
   
   **1)** Go to the website "easyvmx.com" and create a temporart virtual machine with a 16GB 
      growable harddisk. Copy the harddisk "YourNewHDD.vmdk" file into your real 
      virtual machine folder: we will attach this disk to our machine.

   **2)** Now, open "YourVirtualMachine.vmx" with a notepad editor. Add the following to 
      the end of the file. Save the file. (Assuming you only have 1 HDD previously and
      you use the SCSI option)
      
             ----- scsi0:1.present = "TRUE"
----- scsi0:1.fileName = "YourNewHDD.vmdk"
----- scsi0:1.redo = ""
   

**B)** You must have a "Ubuntu 10.04 LTS" or another Live CD. Let's assume we have
   a "linuxos.iso" file for that. Using the "Devices->CD/DVD (IDE)" menu of VmPlayer
   connect the iso file to "D:" or another appropriate drive letter, and reboot
   your virtual machine.
   
**C)** When the machine boots and asks for installation, do not install and go for
   the "Try" option. When the boot is done open a terminal and resize the file system by

        ```
???? $ sudo e2fsck -f /dev/*
???? $ sudo resize2fs /dev/* 15G   (this may take a while)
``` **       [IMPORTANT NOTE]: **for the first vmachine I tried the 2 lines above worked for the 
                          upcoming "dd" partition copy stage, although gparted showed the
                          resized partition wasn't resized actually. However, in my second
                          try with another vmachine, "dd" stage always overflowed and gave
                          an error like "no more space left in the destination partition".
                          So, I leave the resizing to gparted as well.
        Open gparted, and resize the root partition /dev/* as 15*1024=15360.
                          
    
    "15G" means 15 gbytes, and "*" should be the root file system partition: it is usually
    "sda1" but if you are not sure you can use "gparted" or see it by installing "lvm2" by 
    the following
    
        ```
$ sudo gparted
```            or 
            
        ```
$ sudo apt-get install lvm2
$ lvmdiskscan
```**D)** Now, we have 15GB root file system. Check the size by mounting it:
        
        ```
$ sudo mount /dev/sda1 /mnt
$ df
$ sudo umount /mnt
```    Open "gparted":

        ```
$ sudo gparted
```    Go inside the disk "sdb", and create a 15GB ext4 partition in it. When we are done with
    shrinking, this partition will be our root file system partition named "sda1", but for now
    it is "sdb1". [You may notice "gparted" still reports "sda1" as 64GB. I do not know why,
    but it is better you do noy pay attention to it. -> Due to [IMPORTANT NOTE] above now
    gparted should show the correct size as 15GB]
    
    By using "manage flags" menu item in gparted add the flag 'boot' to sdb1, and quit gparted.
    
    Now, we copy our original partition in to our newly created partition by "dd""
    
        ```
$ sudo dd if=/dev/sda1 of=/dev/sdb1
```    Since the file system size in "sda1" is 15GB and "sdb1" size is 15GB, "dd" should not
    complain and do a 1-to-1 exact copy. But check the sizes of sda1 and sdb1 with gparted,
    and make sure sdb1 =< sda1
    
    Now, we will put a bootlader into this hdd to be able to get rid off the old one: 
    
        ```
$ sudo mount /dev/sdb1 /mnt
$ sudo grub-install --root-directory=/mnt /dev/sdb
$ sudo umount /mnt
```    When finished, "Power off and exit" the VmWarePlayer.
    
**E)** Open "YourVirtualMachine.vmx" and delete the lines you previously appended for the new hdd.
   Change "scsi0:0.fileName = "YourOriginalHDD.vmdk" to "YourNewHDD.vmdk". As a result we will
   have only 1 hdd (the small one)

F) Start your virtual machine with VmwarePlayer, your OS should boot with no interruption, if it
   gets stuck after BIOS with "grub" prompt, then you should manually load the kernel and boot it:
   
        ```
> root (hd0,0)
> find /grub/stage1 or /boot/grub/stage1
> kernel *bootfolderpathinyourrootfilesystem*/vmlinuz-[version] [parameters]
> initrd *bootfolderpathinyourrootfilesystem*/initrd[version]
> boot
```    'vmlinuz' and 'initrd' versions are in the /boot folder of your original file system
    
    You can automate this manual load by writing a "grub.conf" and put it into
    /boot/grub folder of your root file system.

---

### Post by nothingspecial on 2012-11-10
*Thread moved to **Virtualisation**.*

This post would be better on the community wiki rather than on the forums. If you need help with that you can contact the forum wiki team

[https://help.ubuntu.com/community/ForumWikiTeam](https://help.ubuntu.com/community/ForumWikiTeam)

---


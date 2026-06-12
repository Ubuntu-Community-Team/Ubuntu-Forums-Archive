---
title: "How to make a live CD/DVD from your harddisk installation"
date: 2008-02-05
forum: Tutorials
---

### Post by capink on 2008-02-05
The information in this thread has been moved to [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062094#post12062094](http://ubuntuforums.org/showthread.php?p=12062094#post12062094)

Thread closed.


[SIZE="6"]Transforming your Installation into a Live DVD/CD[/SIZE]




[SIZE="4"][COLOR="Purple"]*Update 1: This guide is updated to use grub2 instead of grub-legacy*[/COLOR][/SIZE]


[SIZE="4"][COLOR="Purple"]*Update 2: Appendix 2 shows how to make a bootable flash disk instead of a live CD.*[/COLOR][/SIZE]


This HOWTO is about making a live CD/DVD from the main system on your hard drive. This might be desired if you have customized your system and want to have it on CD.

Another approach that will be discussed here is building your live CD/DVD from scratch. This will be done by building a new system using debootstrap. This is usefull if you want to build a clean live CD, or if you want to build a minimal rescue cd. (Consult Appendix.1 for more details about building a CD from scratch).

The live CD is usually created with a filesystem called squashfs. Squashfs is read only compressed filesystem that allow us to squeeze our system into a single CD. Note that your system has to be about 2GB (this might need some trial an error) to produce a compressed image that fits on the CD. Otherwise, you will have to use a DVD, or you can use a flash disk as pointed out in Appendix. 2.




> [SIZE="5"]_*Background on live CD/DVD[/SIZE]_*

[SIZE="4"]**_Note: This section is a clarification of how live CD works. You don't have to read it. You can skip it if you want._**[/SIZE]

A live CD/DVD is basically a normal linux installation just like an ordinary harddrive installation. However, simply copying the harddirve installation over to a CD/DVD is not enough to produce a working system. *Why?* because there are still minor differences between a live CD/DVD and on ordinary harddrive installation. So in addition to copying our harddirve installation to the CD/DVD we must address those differences as well.

*So what are these differences?*

[LIST=1]



[*]The CD or DVD is read only media. Linux needs to have write access to certain parts of the system to be able to operate properly (like "/dev" "/proc" "/var" "/tmp"). There are a lot of approaches to address this problem. All of which utilize the system RAM. Some of these approaches enable write access only to essential directories and files, and hence, they do not allow the user to modify the system or install new packages while in the live CD. Other approaches, like [aufs2]("http://www.filesystems.org/project-unionfs.html") which is what is used in this guide, allows the user to write to any part of the system. This is done by merging part of the RAM with the read-only filesystem of the live CD/DVD and making the look like one filesystem that have read-write access. Aufs2 has to be mounted at boot in a certain manner.



[*]With the harddrive installation the location of the root filesystem is fixed. So it is passed to the kernel at boot time using the root=/dev/... parameter. With a live CD/DVD, the location of the root device is not fixed as the user might have multiple cdrom drives, these drives can be ide, scsi ... etc. So for the root filesystem to be mounted, there must be a way to identify the root device, and then we have to load the suitable kernel modules (to be able to access the cdrom controller as well as the CD filesystem). All this has to be done even before we have a root filesystem mounted.




[*]To fit on a CD, the filesystem is usually compressed using [squashfs]("http://squashfs.sourceforge.net/"). So we need to autodetect the filesystem type. We also need to have the proper modules for mounting it.
[/LIST]




These considerations require special preparation at boot time, some of which must be performed even before mounting the actual filesystem. How can we do this?

Linux introduced a mechanism that allow for such preparations at boot time before the actual root filesystem is mounted. It is called the initial root filesystem or initramfs. This mechanism is used also in mounting normal harddirve installations, as it adds flexibilty to the boot process.


[initramfs]("http://www.linuxdevices.com/articles/AT4017834659.html") is virtual filesystem. It is a compressed cpio (cpio is an archive format similar to tar) archive that contains a minimal shell, kernel modules necessary for mounting the root filesystem and number of scripts that perform some tasks at boot time. The most important of these scripts is a script called init located at the root of the initramfs.

*How does initramfs work?*

The boot loader loads both the kernel and the initramfs into memory and starts the kernel. The kernel then unpacks the initramfs and mount it as initial root filesystem, and then looks for the init program within the initial filesystem, and once it finds it, it executes it and hand the boot process over to it. This init scirpt is responsible for finding the real root filesystem and mounting it. It is also responsible for any special preparations required at boot time.

So any special operations required for booting the system from live media can be coded into the initramfs boot scripts.

*How is initramfs is created?*

We do not have to create initramfs manually (although it can be done). There are tools for creating and updating initramfs like the command update-initramfs. Moreover, these tools can include custom scripts into the initramfs if they are placed in a certain preset locations (/usr/share/initramfs/scripts). So all we have to do is dump our custom scripts (which will do all the required preparation for booting the live CD/DVD) into these preset locations, and then create a custom initramfs by running update-initramfs. 

We don't even have to write these scripts. Why? becuase there are packages that have scripts tailored for booting form live CDs. One of these packages is called casper (this is the package used in this howto). By installing casper into the system, it places the scripts in there proper locations (where they can be spotted by update-initrfamfs). The only thing we need to do after installing casper is running update-initramfs to create an initramfs suitable for live CD/DVD.







[SIZE="5"]_*The live CD/DVD structure:[/SIZE]_*

The directory tree of the live CD/DVD we are going to create is going to look like this:

```

(CD ROOT)
|-------+casper
|	|-------filesystem.${FORMAT}	
|	|-------[COLOR="Gray"]filesystem.manifest[/COLOR]
|	|-------[COLOR="Gray"]filesystem.manifest-desktop[/COLOR]
|	|-------vmlinuz
|	|-------initrd.img
|
|-------+boot
|	|--------+grub
|	|	 |--------grub.cfg
|	|
|	|-------[COLOR="Gray"]memtest86+[/COLOR]
|
|--------[COLOR="Gray"]md5sum.txt[/COLOR]

```



[LIST]/casper/filesystem.${FORMAT}: This is the container of the linux filesystem we are going to copy from our harddisk. It is usually a compressed filesystem like squahsfs.[/LIST]

[LIST][COLOR="Gray"]/casper/filesystem.manifest: This file is optional. You only need it if you decide to include the Ubuntu installer in the CD. The purpose of this file will be explained later.[/COLOR][/LIST]

[LIST][COLOR="Gray"]/casper/filesystem.manifest-desktop: This file is optional. You only need it if you decide to include the Ubuntu installer in the CD. The purpose of this file will be explained later.[/COLOR][/LIST]

[LIST]/casper/vmlinuz: The linux kernel. This is copied form the linux filesystem.[/LIST]

[LIST]/casper/initrd.img: the initramfs that contain the customizations necessary for the live CD/DVD.[/LIST]

[LIST]/boot/grub/grub.cfg: File containing boot options for the live CD/DVD.[/LIST]

[LIST][COLOR="Gray"]/boot/memtest86+: Optional file used to test the RAM of the machine form the live CD/DVD.[/COLOR][/LIST]

[LIST][COLOR="Gray"]/md5sum.txt: Optional file containing checksums for all the files in the CD.[/COLOR][/LIST]









[SIZE="5"]_*Outline of the steps:[/SIZE]_*

A. Prepare Our work environment.

B. Copy the Source system to the target directory.

C. Chroot into the new system and make some modifications.

D. Prepare The CD directory tree.

E. Build the CD/DVD



[COLOR="Purple"]**Appendix 1. Building the live media form scratch using Debootstrap.[/COLOR]**

[COLOR="Purple"]**Appendix 2. How to Boot the ISO from a flash disk.[/COLOR]**



[SIZE="5"]_*Conventions used in this HOWTO:[/SIZE]_*

[LIST][COLOR="Magenta"]Text highlighted in Magenta is meant to be replaced by the user's [SIZE="4"]_**custom value[/SIZE]_**[/COLOR]. e.g. I will use [COLOR="Magenta"]gedit[/COLOR] as my default text editor. Replace [COLOR="Magenta"]gedit[/COLOR] with your favorite text editor.[/LIST]
[LIST][COLOR="Blue"]Commands performed within a [SIZE="4"]_**chroot[/SIZE]_** will be in Blue.[/COLOR][/LIST]
[LIST][COLOR="Gray"][SIZE="4"]_**Optional[/SIZE]_** arguments or steps will be highlighted in Gray.[/COLOR][/LIST]










[SIZE="4"]_*A. Preparing the environment[/SIZE]_*

1. Set some variables

```
export WORK=[COLOR="Magenta"]~/work[/COLOR]
export CD=[COLOR="Magenta"]~/cd[/COLOR]
export FORMAT=squashfs
export FS_DIR=casper
```


The WORK Directory is where our temporary files and mount point will reside.
The CD is the location of the CD tree.
FORMAT is the filesystem type. We you are going to use a compressed squashfs.
FS_DIR is the location of the actual filesystem image within the cd tree.

Replace only the values highlighted in [COLOR="Magenta"]Magenta[/COLOR].




2. Create the CD and the WORK directory structure:

```
sudo mkdir -p ${CD}/{${FS_DIR},boot/grub} ${WORK}/rootfs
```


3. Install some packages on your current system:


```
sudo apt-get update
```
```
sudo apt-get install grub2 xorriso squashfs-tools [COLOR="Gray"]qemu[/COLOR]
```


[COLOR="Gray"]qemu[/COLOR] is optional. It is only needed for testing the cd before burning it. It can be substituted with any other virtualization software like virtualbox.








[SIZE="4"]_*B. Copy your installation into the new filesystem.[/SIZE]_*


```
sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/* \
--exclude=/sys/* --exclude=/tmp/* --exclude=/home/* --exclude=/lost+found \
--exclude=/var/tmp/* --exclude=/boot/grub/* --exclude=/root/* \
--exclude=/var/mail/* --exclude=/var/spool/* --exclude=/media/* \
--exclude=/etc/fstab --exclude=/etc/mtab --exclude=/etc/hosts \
--exclude=/etc/timezone --exclude=/etc/shadow* --exclude=/etc/gshadow* \
--exclude=/etc/X11/xorg.conf* --exclude=/etc/gdm/custom.conf \
--exclude=/etc/lightdm/lightdm.conf --exclude=${WORK}/rootfs / ${WORK}/rootfs
```


Note: rsync is used instead of cp to take advantage of the --one-file-system and the --exclude options.




If you have a separate boot partition you will have to copy it using the following command:

```
sudo cp -av /boot/* ${WORK}/rootfs/boot
```



[COLOR="Gray"](Optional) Copy settings in your home dir:


If you want to preseve your user account settings which are stored in your home directory, you can copy them to ${WORK}/rootfs/etc/skel/.

But first we have to define what files we want to copy. For example I am using xcfe4 as my DE, and it stores all it settings in a directory called .config in my home directory, so I am going to add .config to the variable $CONFIG:

```
CONFIG='.config .bashrc'
```

Now, Copy the CONFIG files using the following command:

```
[COLOR="Gray"]cd ~ && for i in $CONFIG
do
sudo cp -rpv --parents $i ${WORK}/rootfs/etc/skel
done[/COLOR]
```
[/COLOR]





[SIZE="4"]_*C. Chroot into the new system and modify it:[/SIZE]_*

1. Chroot into the copied system after mounting proc and dev:


```
sudo mount  --bind /dev/ ${WORK}/rootfs/dev
```
```
sudo mount -t proc proc ${WORK}/rootfs/proc
```
```
sudo mount -t sysfs sysfs ${WORK}/rootfs/sys
```
```
sudo chroot ${WORK}/rootfs /bin/bash
```


[COLOR="Blue"]N.B: All commands in Blue are done within a chroot.[/COLOR]

Now you are within chroot environment, type the following command:

```
[COLOR="Blue"]LANG=[/COLOR]
```




2. Install Packages Essential for live CD:


```
[COLOR="Blue"]apt-get update[/COLOR]
```
```
[COLOR="Blue"]apt-get install casper lupin-casper[/COLOR]
```

casper contains the live scripts.
	


[COLOR="Gray"]3. (Optional) If you want your live cd to have an installer, install the Ubuntu installer:

```
[COLOR="Blue"]apt-get install ubiquity ubiquity-frontend-gtk[/COLOR]
```

> Note: People using kde replace replace the previous command with

```
[COLOR="Blue"]apt-get install ubiquity ubiquity-frontend-kde[/COLOR]
```

Credit for this goes note to [Fragadelic]("http://ubuntuforums.org/member.php?u=386921") author of [remastersys]("http://www.remastersys.klikit-linux.com/"). [Remastersys]("http://www.remastersys.klikit-linux.com/").[/COLOR]



[COLOR="Gray"](Optional Step)Install any packages you want to be in the CD. Some of the following packages are useful in emergency situations:

```
[COLOR="Gray"]sudo apt-get install gparted ms-sys testdisk wipe partimage xfsprogs reiserfsprogs jfsutils ntfs-3g ntfsprogs dosfstools mtools[/COLOR]
```

gparted: patitioning tool. It is automatically installed as a dependecy of ubiquity.
testdisk: Partition scanner and disk recovery tool.
wipe: Secure file deletion.
partimage: backup partitions into a compressed image file (like norton ghost).
xfsprogs reiserfsprogs jfsutils: Tools for handling different filesystems.
mtools: Tools for manipulating MSDOS files

[/COLOR]




4. Update the initramfs:



First update modules.dep:

```
[COLOR="Blue"]depmod -a $(uname -r)[/COLOR]
```


```
[COLOR="Blue"]update-initramfs -u -k $(uname -r)[/COLOR]
```

As already metioned above, the initramfs is reponsible for much of the preparation required at the boot time of the CD/DVD. The updated initramfs now contain the live scirpts installed with casper.









5. Remove non system users

```
[COLOR="Blue"]for i in `cat /etc/passwd | awk -F":" '{print $1}'`
do
	uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
	[ "$uid" -gt "998" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null
done[/COLOR]
```

Non-system users are users created by you that have user id more than 999.

N.B: In case a user with uid 999 is present we remove as well because that uid is preserved for the live cd user.



6. Clean the system

First, clean apt cache

```
[COLOR="Blue"]apt-get clean[/COLOR]
```



Clean all the extra log files

```
[COLOR="Blue"]find /var/log -regex '.*?[0-9].*?' -exec rm -v {} \;[/COLOR]
```



The remaining log files are going to be zeroed lest the system complain if they are deleted.

```
[COLOR="Blue"]find /var/log -type f | while read file
do
	cat /dev/null | tee $file
done[/COLOR]
```


```
[COLOR="Blue"]rm /etc/resolv.conf /etc/hostname[/COLOR]
```



7. Exit chroot

```
[COLOR="Blue"]exit[/COLOR]
```





[SIZE="4"]_*D. Prepare The CD directory tree:[/SIZE]_*

1. Copy the kernel, the updated initrd and memtest prepared in the chroot:

```
export kversion=`cd ${WORK}/rootfs/boot && ls -1 vmlinuz-* | tail -1 | sed 's@vmlinuz-@@'`
```
```
sudo cp -vp ${WORK}/rootfs/boot/vmlinuz-${kversion} ${CD}/${FS_DIR}/vmlinuz
```
```
sudo cp -vp ${WORK}/rootfs/boot/initrd.img-${kversion} ${CD}/${FS_DIR}/initrd.img
```
```
sudo cp -vp ${WORK}/rootfs/boot/memtest86+.bin ${CD}/boot
```



[COLOR="Gray"]2. Generate manifest:

Note: This step is only needed if you installed the Ubuntu installer ubiquity. This step generates two files (filesystem.manifest & filesystem.manifest-desktop).

```
[COLOR="Gray"]sudo chroot ${WORK}/rootfs dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ${CD}/${FS_DIR}/filesystem.manifest[/COLOR]
```
```
[COLOR="Gray"]sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}[/COLOR]
```
```
[COLOR="Gray"]REMOVE='ubiquity casper user-setup os-prober libdebian-installer4'[/COLOR]
```
```
[COLOR="Gray"]for i in $REMOVE 
do
	sudo sed -i "/${i}/d" ${CD}/${FS_DIR}/filesystem.manifest-desktop
done
[/COLOR]
```

These two files are used by the ubiquity installer when installing to harddisk. These two files are just lists of packages. Ubiquity compares these two files and removes packages unique to filesystem.manifest. This way when installing to harddisk, packages like casper which is only useful in a live CD/DVD are removed. These packages that will be removed at install are defined in the variable $REMOVE[/COLOR]


3. Unmount bind mounted dirs:

```
sudo umount ${WORK}/rootfs/proc
```

```
sudo umount ${WORK}/rootfs/sys
```

```
sudo umount ${WORK}/rootfs/dev
```



4. Convert the directory tree into a squashfs:


```
sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} -noappend
```

Note: Make sure the resulting file size can fit into your live media.






5. Make filesystem.size


```
echo -n $(sudo du -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/${FS_DIR}/filesystem.size
```




6. Calculate MD5

```


find ${CD} -type f -print0 | xargs -0 md5sum | sed "s@${CD}@.@" | grep -v md5sum.txt | sudo tee -a ${CD}/md5sum.txt


```





7. Make Grub the bootloader of the CD


Make the grub.cfg

```
sudo [COLOR="Magenta"]gedit[/COLOR] ${CD}/boot/grub/grub.cfg
```


Copy the following text into it and save it.

```
set default="0"
set timeout=10

menuentry "Ubuntu GUI" {
linux /casper/vmlinuz boot=casper quiet splash
initrd /casper/initrd.img
}


menuentry "Ubuntu in safe mode" {
linux /casper/vmlinuz boot=casper xforcevesa quiet splash
initrd /casper/initrd.img
}


menuentry "Ubuntu CLI" {
linux /casper/vmlinuz boot=casper textonly quiet splash
initrd /casper/initrd.img
}


menuentry "Ubuntu GUI persistent mode" {
linux /casper/vmlinuz boot=casper persistent quiet splash
initrd /casper/initrd.img
}


menuentry "Ubuntu GUI from RAM" {
linux /casper/vmlinuz boot=casper toram quiet splash
initrd /casper/initrd.img
}

menuentry "Check Disk for Defects" {
linux /casper/vmlinuz boot=casper integrity-check quiet splash
initrd /casper/initrd.img
}


menuentry "Memory Test" {
linux16 /boot/memtest86+.bin
}


menuentry "Boot from the first hard disk" {
set root=(hd0)
chainloader +1
}
```





[SIZE="4"]_*E. Build the CD/DVD[/SIZE]_*

1. Make the ISO file

```
sudo grub-mkrescue -o ~/live-cd.iso ${CD}
```



2. Test the CD

Test using qemu emulator 
```
qemu -cdrom ~/live-cd.iso -boot d
```

Or use any other virtualization program you like.


**Update: As noted by [az]("http://ubuntuforums.org/member.php?u=844") in this [post]("http://ubuntuforums.org/showpost.php?p=4643009&postcount=18"), while testing the iso with qemu sometimes it drops you to an initramfs shell because of a problem with qemu. This behaviour has been confirmed by other users. In this case it is advisable to retest the iso with another virtualization software like virtualbox or to copy the iso to flash disk and test directly on your pc (See Appendix 2.).**


[COLOR="Gray"]3. (Optional) Clean our workspace

```
[ -d "$WORK" ] && rm -r $WORK $CD
```
[/COLOR]






[SIZE="5"]_*Final Notes:[/SIZE]_*



[LIST]If you are using a custom kernel make sure it has support for the following:


[LIST=1]
[*]Support of loopback device.
[*]Support for squashfs.
[*]Support for aufs2.
[*]Support for initramfs.
[/LIST]
[/LIST]



[LIST]There are some extra options I put in the grub menu:



[LIST=1]


[*]Start linux form RAM. This option is only possible if your ram is larger than data on the live media. This option can be useful if you are building a minimal command line rescue disc as it would enhance performance to start it from RAM.


[*]Start in presistent mode. To learn about it more look [here]("https://help.ubuntu.com/community/LiveCDPersistence").


[*]Start Linux in Text Mode. This will not start X. The user will be autologged into a virtual terminal (the kind of terminal you get when you press Alt+Ctrl+F1).
[/LIST]
[/LIST]







[SIZE="5"]_*Appendix 1. Building the live media form scratch using debootstrap.[/SIZE]_*

Instead of using your current installation to be the basis of you live CD, you can build a custom clean system from scratch using [debootstrap]("http://ubuntuforums.org/showpost.php?p=4887531&postcount=65"), and then use that as the basis of your CD. The modifications you have to make are:


[LIST]skip steps B & C alltogether. Instead, do the instructions listed [here]("http://ubuntuforums.org/showpost.php?p=4887531&postcount=65") to build your custom system from scratch using debootstarp[/LIST]

[LIST]after finishing the instructions of the guide mentioned above, you resume the steps in this guide, going straight to step D.[/LIST]




[SIZE="5"]_*Appendix 2. How to Make bootable USB flash[/SIZE]_*



Grub2 has many advantages. One of these is the ability to boot an ISO directly from HDD of a flash. This means that instead of burning the ISO to a CD/DVD you can just copy it to a USB flash disk and boot it from there.

Another big advantage of Grub2 is that it supports UUIDs and LABELs which are better than device names because they are subject to change especially with flash disks.

We need to know the UUID or the LABEL for the partition on which the ISO resides. We also need the device name of the usb flash (it will be used once to install grub to the flash drive). We can know that by issuing the following command which lists all the partition details:

```
sudo blkid
```


Take note of the flash UUID (or LABEL) and the flash device name ( e.g /dev/sdc not /dev/sdc1)

Now mount your flash drive:

```
sudo mount -t [COLOR="Magenta"]vfat[/COLOR] /dev/by-uuid/[COLOR="Magenta"]<insert uuid here>[/COLOR] /mnt
```

Install grub to the flash disk:

```
sudo grub-install --no-floppy --force --root-directory=/mnt [COLOR="Magenta"]/dev/sdc[/COLOR]
```

replace the [COLOR="Magenta"]/dev/sdc[/COLOR] with the device name of your flash. Note that we are using the device name of the flash itself not the partition in the flash (e.g. /dev/sdc not /dev/sdc1)


copy the ISO to the flash drive:

```
cp -v ~/live-cd.iso /mnt
```


Make the grub menu of the flash disk

```
sudo [COLOR="Magenta"]gedit[/COLOR] /mnt/boot/grub/grub.cfg
```

and add the following entry

```
set default="0"
set timeout=10


insmod [COLOR="Magenta"]ntfs[/COLOR]
search --no-floppy --fs-uuid [COLOR="Magenta"]<insert the UUID>[/COLOR] --set=usb
set iso_path=/live-cd.iso
loopback loop (${usb})${iso_path}
set root=(loop)
set bootopts="boot=casper iso-scan/filename=${iso_path} noprompt"

menuentry "Boot ISO from HDD/USB" {
linux (loop)/casper/vmlinuz $bootopts
initrd (loop)/casper/initrd.img
}
```


replace [COLOR="Magenta"]ntfs[/COLOR] with the filesystem of your flash disk. e.g ntfs, fat, ......

replace [COLOR="Magenta"]<insert the UUID>[/COLOR] with the UUID of your flash disk.

Note: If you want to use LABEL instead of UUID replace the first line in the entry with

```
search --no-floppy -l [COLOR="Magenta"]<insert the LABEL>[/COLOR] --set=usb
```



When you start you pc you have to select "boot from usb storage device" from your BIOS boot options.

---

### Post by pagadama on 2008-02-08
&#51221;&#47568; &#50976;&#50857;&#54620; &#51221;&#48372;&#51060;&#44400;&#50836;.
&#44048;&#49324;&#54633;&#45768;&#45796;.
Happy New Year!
(7. Feb is Korean Traditional New Year's day:))

---

### Post by RumorsOfWar on 2008-02-10
Great post! Thanks. I was looking at switching back to Ubuntu and this seals it.

---

### Post by capink on 2008-02-10
> **RumorsOfWar said:**
> Great post! Thanks. I was looking at switching back to Ubuntu and this seals it.

Can you confirm that it actually worked for you. What format did you go with? squashfs or ext2?

---

### Post by RumorsOfWar on 2008-02-16
I'm using Gutsy 64 alternate install.
I've added the apps I need, my system is up to 2.5 GB so I'll use ext2, DVD. 
I'm on step C, but when I "sudo LANG= chroot ${WORK}/rootfs /bin/bash", I get "sudo: LANG=: command not found" error. 
I'll keep trying, but if you know the problem, that would help :)
( to resume, do I need to reset the variables at the beginning of step A ?)

---

### Post by capink on 2008-02-16
> **RumorsOfWar said:**
> I'm using Gutsy 64 alternate install.
I've added the apps I need, my system is up to 2.5 GB so I'll use ext2, DVD. 
I'm on step C, but when I "sudo LANG= chroot ${WORK}/rootfs /bin/bash", I get "sudo: LANG=: command not found" error. 
I'll keep trying, but if you know the problem, that would help :)
( to resume, do I need to reset the variables at the beginning of step A ?)

replace the command with:

```
sudo chroot ${WORK}/rootfs /bin/bash
```

Once in chroot type this command before proceeding:

```
LANG=
```


You do not need to reset any of the variables as long as you are still working in the same terminal.

---

### Post by RumorsOfWar on 2008-02-16
And now I'm replying from my own live CD :guitar:
I think I messed up my first effort by missing some ext2 changes, so I redid it in squashfs.
In step C, using  'LANG=' after chroot worked. :)
I had to change a line at D/5  so grub set up for an x86_64-pc rather than i86, and this live cd environment hangs if I enable 3D. 
But this is very cool. I can restore or duplicate my Ubuntu setup faster, and without an internet.
Thanks Capink :)

If I may suggest, edit lines at C/1 and D/5 in the first post, and put a "*ext2" tag beside things that need appendix1.
This tutorial is worthy of being Sticky  :)

---

### Post by capink on 2008-02-16
> **RumorsOfWar said:**
> And now I'm replying from my own live CD :guitar:
I think I messed up my first effort by missing some ext2 changes, so I redid it in squashfs.
In step C, using  'LANG=' after chroot worked. :)
I had to change a line at D/5  so grub set up for an x86_64-pc rather than i86, and this live cd environment hangs if I enable 3D. 
But this is very cool. I can restore or duplicate my Ubuntu setup faster, and without an internet.
Thanks Capink :)


Glad it worked for you. Can you post the exact modification you did to menu.lst so that I can add it to my post (with credits ofcourse).

Also, what do you think messed up for you in ext2?

---

### Post by RumorsOfWar on 2008-02-17
> Can you post the exact modification you did to menu.lst
Sure, I wouldn't worry about crediting me though. My input was insignificant compared to yours. 
```
sudo cp -pv /usr/lib/grub/x86_64-pc/* ${CD}/boot/grub
```
In place of;
```
sudo cp -pv /usr/lib/grub/i386-pc/* ${CD}/boot/grub
```
> Also, what do you think messed up for you in ext2?
I went to step B before creating the virtual file system mentioned in appendix A.
 I just wasn't patient enough to read ahead and understand as much as I needed to. My bad. But a hint marker like "*ext2*" would have stopped me.
*edit* Now I see you did have the line there. I may have had it right.
 Oh well, I'm still reading through it and seeing how it works. :popcorn:

---

### Post by Tybion on 2008-02-23
Thanks, capink.  This is brilliant.  I am pasting it into a customized script specifically for me, but leaving all your comments in the script.

---

### Post by TheRoot on 2008-02-29
Thanks capink for this Tutorial, really it was great, and worked wonderful for me :-D

Wish you good luck.
BTW: Mabrook the CAF 2008 for Eygpt

---

### Post by capink on 2008-02-29
> **TheRoot said:**
> Thanks capink for this Tutorial, really it was great, and worked wonderful for me :-D

Wish you good luck.
BTW: Mabrook the CAF 2008 for Eygpt

Alla yebarek feek.

---

### Post by capink on 2008-02-29
> **Tybion said:**
> Thanks, capink.  This is brilliant.  I am pasting it into a customized script specifically for me, but leaving all your comments in the script.

The script is going to be handy whenever you want to repeat the process. I thought about making it in a script at first, but then I retreated and felt it is better to present it with a series of instructions so anyone can make a script of his own if he wishes. Good luck.

---

### Post by WebDesignHero on 2008-03-08
Hello,

Thanks for the well written and well formatted guide. I just have one issue:
Everything seems to work well, but after selecting the normal GUI option in GRUB I am dumped to
BusyBox ash shell where the prompt display ( initramfs ). Could anyone tell me what I messed up? I feel like the correct outcome should boot me into my normal GUI from the original install or something else.... I am working with Ubunut 7.10 and also tried this a few weeks ago on Debian 4.0 and had the same end result. Any help or explanation of why I got dumped into this shell instead of the system I thought I had squashed and put on the CD would be most helpful.

---

### Post by capink on 2008-03-09
After being dumped to the busybox shell, you should find a log file called live.log or casper.log. You can know the name of the log file by typing:

```
ls
```

After identifying the log filename, type the following command to view the content of the log:

```
cat /log/filename
```

The error message should give an idea about the problem you are facing.

---

### Post by joshrobinson on 2008-03-10
i followed your guide to the letter, but when i start the live cd, it loads the gnome desktop, then 5 seconds later bumps me back to the GDM login screen, and says user ubuntu will start in 10 seconds, logs in again and kicks back out, not sure what happend

---

### Post by Fred_E _krugar on 2008-03-10
Well mine worked in VirtualBox. But when I actually tried to boot to live CD it got stuck on FD0 I dont even own a floppy WTH do I do to get past that???

---

### Post by capink on 2008-03-10
> **joshrobinson said:**
> i followed your guide to the letter, but when i start the live cd, it loads the gnome desktop, then 5 seconds later bumps me back to the GDM login screen, and says user ubuntu will start in 10 seconds, logs in again and kicks back out, not sure what happend

I don't know what is causing this problem. Can you try logging from a text shell (press alt+f1 and then login and type the command startx -- :1)

---

### Post by capink on 2008-03-10
> **Fred_E _krugar said:**
> Well mine worked in VirtualBox. But when I actually tried to boot to live CD it got stuck on FD0 I dont even own a floppy WTH do I do to get past that???

That is most probably indicative of hardware problem. If the official Ubuntu cd is working fine for you, One hack you can try is copying the initrd from the official Ubuntu cd to replace the one in your custom cd (this will only work if both cds have exactly the same kernel version).

---

### Post by markp1989 on 2008-03-10
very nice how to , i will be using this later

---

### Post by Fred_E _krugar on 2008-03-11
On my homebrew cd the initrd is in the boot folder.
On the Ubuntu CD the initrd is in the casper folder could that bethe problem if it is how can I change the iso. ?

---

### Post by capink on 2008-03-11
the ISO image is read only. You will have to recreate it as follows:

- Mount you homemade custom iso:

```
sudo mount -o loop -t iso9960 /path/to/the/iso /mnt
```

- Copy the contents of the iso to a new folder:

```
mkdir ~/iso
```

```
sudo cp -a /mnt/* ~/iso
```

- Copy the initrd of the official cd after mounting it

```
sudo cp -vf /path/to/official/cd/casper/initrd.gz ~/iso/boot/initrd.gz
```

- Recreate the iso image:

```
sudo mkisofs -b boot/grub/stage2_eltorito \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-V "Custom Live CD" -cache-inodes -r -J -l \
-o ~/live-cd.iso ~/iso
```


Some Notes:
==========
- Make sure the official cd is working on your hardware.
- Only do the above under two conditions: The first is that both cds have exactly the same kernel version. The Second condition is that your custom cd is created with casper and not live-initramfs (since the official ubuntu cd is created with casper).
- This should work (provided that you are able to boot from the official ubuntu cd) but there is no guarantee it will. So please use Rewritable media to avoid wasting black cds while trying the different solutions to your problem.

---

### Post by Fred_E _krugar on 2008-03-12
Thank you I will try this.

---

### Post by stumpalump on 2008-03-13
So I have a question. Let's say my ubuntu install is almost 6.7Gb and I want to make a Dual Layer LIVE DVD complete with installer. How can I do this with the limitation in the iso 9660? Can I use UDF somehow?

---

### Post by capink on 2008-03-13
No you cannot use udf as it is not supported for the time being (neither casper not live-initramfs supports it). But you do not need to use udf becuase after compressing your system into a squashfs it will be about 2.7 GB.

---

### Post by Fragadelic on 2008-03-13
capink - very nice howto.

I am the creator of remastersys - [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) and have borrowed some of your ideas to improve how remastersys works.

You can also add a graphical grub boot to this by putting the splash image of your choice in boot of the cd tree and adding the following line above the boot entries:

splashimage=/boot/splash.xpm.gz

Or whatever name you used for the splash image.

Also, a quick question - I have always used "boot=casper" and never had an issue.  Where is BOOT=casper needed?

I don't think you need the rw or nopersistent.

---

### Post by Fragadelic on 2008-03-13
BTW, this is the best howto I've seen on this subject to date.

---

### Post by capink on 2008-03-13
> **Fragadelic said:**
> capink - very nice howto.

I am the creator of remastersys - [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) and have borrowed some of your ideas to improve how remastersys works.

Nice project.

I just started to learn python. I also intend to learn pyqt so maybe I will be able contribute to your project.

> **Fragadelic said:**
> You can also add a graphical grub boot to this by putting the splash image of your choice in boot of the cd tree and adding the following line above the boot entries:

splashimage=/boot/splash.xpm.gz

Or whatever name you used for the splash image.

Yes this is a nice feature. I already have a link explaining this in the final notes section. Another option is to use [grub-gfxboot]("http://ubuntuforums.org/showthread.php?t=208855"), this is supposed to produce more fancy graphics but I have not tried it yet.

> **Fragadelic said:**
> Also, a quick question - I have always used "boot=casper" and never had an issue.  Where is BOOT=casper needed?

I think I read somewhere that the BOOT=casper option is checked for by the main casper script before it takes control of the boot process. While the boot=casper option defines the directory where casper looks for the live image.

I have not tested this information, I just took it for granted. But since you are able to produce the same result using only boot=casper it seems it is redundant to use BOOT=casper.

> **Fragadelic said:**
> I don't think you need the rw or nopersistent.

These are indeed redundant.

> **Fragadelic said:**
> BTW, this is the best howto I've seen on this subject to date.

Thank you for the complement.

---

### Post by capink on 2008-03-13
Fragadelic, I hope you can help solve people problems that I don't have an answer for if your time permit.

---

### Post by Fragadelic on 2008-03-13
I saw your bit about the grub splash after I posted - lol.

Remastersys right now is using bash and zenity or kdialog for the gui frontend and now that I have things working pretty well, I will start to learn python myself and might convert it over.

I've been doing bash for so long and just find it easy to do and it works for what I need so I just went with it.  Its also easier for folks just starting with linux scripting to take a look at and see how I did certain things.

I've looked at a lot of howtos on making ubuntu livecd's but this one is definitely the most complete and very well written one that I've found.

I've bookmarked this thread for future reference for myself.

Please feel free to take a look at remastersys and let me know if you have any suggestions.  I still have some cleanup to do but it works pretty well so far on a number of system.  It was originally created on Kubuntu and Mint but I now use Klikit-Linux(Kubuntu based) and am part of the team there.

/etc/shadow and /etc/gshadow can stay as long as the normal users are cleaned out of it.  You can check /usr/bin/remastersys after you install it to see how I did it.  I got my info for the checks directly from how casper looks to see before it creates the livecd user.

Your howto deserves a webpage and not just to be here in the forum where it might get lost.

Let me know if you would like me to put it up on my website and then you can just give the link to folks.

---

### Post by Fragadelic on 2008-03-13
> **capink said:**
> Fragadelic, I hope you can help solve people problems that I don't have an answer for if your time permit.


I'll check back in the thread as I can and try to help where I can.

casper is very picky about a lot of things - lol.

One thing you might want to add is that mkisofs has a limit of 4.7GB so if the system is too large, it will not create the iso file.  Haven't found a way around that yet.

For those that find this prodecure a bit daunting, please feel free to try remastersys as it does this very thing from a simple gui without the need to copy the entire system to a temp area.

---

### Post by Fragadelic on 2008-03-13
> **joshrobinson said:**
> i followed your guide to the letter, but when i start the live cd, it loads the gnome desktop, then 5 seconds later bumps me back to the GDM login screen, and says user ubuntu will start in 10 seconds, logs in again and kicks back out, not sure what happend


Try going to a console term window and see if it is with gdm or not.

CTRL-ALT-F1

then take a look at the /var/log/gdm log files and see if there are any errors.

---

### Post by capink on 2008-03-13
> **Fragadelic said:**
> I saw your bit about the grub splash after I posted - lol.

Remastersys right now is using bash and zenity or kdialog for the gui frontend and now that I have things working pretty well, I will start to learn python myself and might convert it over.

I was thinking about learning kdialog or ssft to add gui to my bash scripts. But since my next project (a private one) will need a full blown gui I decided that  I will try learning pyqt.

> **Fragadelic said:**
> I've been doing bash for so long and just find it easy to do and it works for what I need so I just went with it.  Its also easier for folks just starting with linux scripting to take a look at and see how I did certain things.

Yes bash scripts are beautiful. And since casper itself is written in bash, it makes sense to use it for remastersys.


> **Fragadelic said:**
> Please feel free to take a look at remastersys and let me know if you have any suggestions.  I still have some cleanup to do but it works pretty well so far on a number of system.  It was originally created on Kubuntu and Mint but I now use Klikit-Linux(Kubuntu based) and am part of the team there.

I will defenitely look at remastersys and report back to you. By the way, this is the first time I know about Klikit-Linux. How is different from Kubuntu? I plan to switch into a good kde distro once 4.1 is released.

> **Fragadelic said:**
> /etc/shadow and /etc/gshadow can stay as long as the normal users are cleaned out of it.  You can check /usr/bin/remastersys after you install it to see how I did it.  I got my info for the checks directly from how casper looks to see before it creates the livecd user.

I will check /usr/bin/remastersys. But do you think it would be much different to keep the files? I think the ubuntu installer recreate these files anyway (I don't know how but I think it uses the commands pwconv & grpconv).

> **Fragadelic said:**
> Your howto deserves a webpage and not just to be here in the forum where it might get lost.

Let me know if you would like me to put it up on my website and then you can just give the link to folks.


Unfortunately I don't have a webpage. But it would be really nice if you hosted this guide on your website.


> **Fragadelic said:**
> One thing you might want to add is that mkisofs has a limit of 4.7GB so if the system is too large, it will not create the iso file. Haven't found a way around that yet.

The main problem for me is that ISO9660 cannot support single files larger than 4 GB. So the squashfs cannot be more than 4 GB.

Using udf is not possible because it is not supported by casper nor live-initramfs. But is not the main problem (As casper scripts can possilbly be modified to handle udf), the real showstopper here is that grub does not support booting from udf.

The only option remaining is to not create a squashfs. But to place the system in folder called /casper/squashfs.dir. This is supposedly supported by casper (by looking at the casper main scirpt it looks like it is possible but I have not tried it yet). But the problem here is does iso9660 support essential features of unix filesystems like symlinks, permissions and ownership?. On my system I'm able to create an ISO > 4.7 Gb using the original mkisofs (instead of the symlink created by genisoimage).

---

### Post by stumpalump on 2008-03-13
> **capink said:**
> No you cannot use udf as it is not supported for the time being (neither casper not live-initramfs supports it). But you do not need to use udf becuase after compressing your system into a squashfs it will be about 2.7 GB.

Okay well I kinda wanted to use ext2 rather than squash. Didn't you say that would make the disc run faster? So I kinda wanted to use that for loading times.

So I thought of maybe trying this
```

sudo dd if=/dev/zero of=${CD}/${FS_DIR}/filesystem.${FORMAT} bs=1024 count=7000000

```

And then somehow making a bootable udf out of the output. I know Nero can make udf discs and bootable DVDs but I couldn't merge the two...

Anyone have any ideas?

---

### Post by capink on 2008-03-13
> **stumpalump said:**
> Okay well I kinda wanted to use ext2 rather than squash. Didn't you say that would make the disc run faster? So I kinda wanted to use that for loading times.

So I thought of maybe trying this
```

sudo dd if=/dev/zero of=${CD}/${FS_DIR}/filesystem.${FORMAT} bs=1024 count=7000000

```

And then somehow making a bootable udf out of the output. I know Nero can make udf discs and bootable DVDs but I couldn't merge the two...

Anyone have any ideas?

Well, the recent updates to the guide suggested using uncompressed squashfs (by adding the -noI -noD -noF switches to mksquashfs) instead of ext2 and you would sitll get the same performance. You can still use ext2 if you want, but advantage to use an uncompressed squashfs is that you will not need to create a virtual filesystem.

The main problem preventing us from making a cd in UDF format is that grub does not support booting from a UDF image.

---

### Post by stumpalump on 2008-03-14
Okay, so I've done it with an uncompressed squashfs. Now, for some reason, when I try to make the actual iso, it goes through and does it but I can't find the file???

EDIT: Nevermind it was in root folder.

---

### Post by Fragadelic on 2008-03-14
capink - here is this howto on my webspace:

[http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html)

There is a link to it from the bottom of my webpage as well.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

I left it in a more printer friendly format so folks can print it out if they want to.

---

### Post by stumpalump on 2008-03-16
Okay, so when I made my DVD, I copied all the user settings over, but I didn't see anything that looked like my settings at all. I was kinda hoping that the DVD would boot and it would have my gtk/emerald theme, my menus, my awn etc...

Anyone know how I can do this?

---

### Post by capink on 2008-03-16
To preserve your settings you need to:

1. Konw exactly what are the files that store these settings (This is sometime tricky depending on the program). _Note that if you are storing the themes in your home directory they also have to be copied along with the config files._ I keep all my themes and graphics in a system wide directories to make them available to all users.

2. These files are not copied to the home directory of your live CD. they are copied to the /etc/skel of the live cd (${WORK}/rootfs/etc/skel) as explained in the optional part of step. B



If you are not able to determine what are the files that carry these config files, One solution is to copy all the config files in your home directory by replacing the optional commad in step B with this command:

```
cd $HOME && find . -type f | grep '^\./\.' \
| grep -vi -e 'cache' -e 'thumbnail' -e 'log' -e 'trash' \
-e 'history' -e 'snapshot' -e 'tmp' -e 'temp' -e \
'serverauth' -e 'ICEauthority'\
| while read file; do sudo cp -v --parents --preserve=mode $file ${WORK}/rootfs/etc/skel; done
```

---

### Post by stumpalump on 2008-03-16
I have all my themes saved on a different hard disk. So what you're saying is I would also have to copy the tar files over as well?

Do you happen to know where exactly the config file is that points to the tar files and all that?

---

### Post by capink on 2008-03-17
> **stumpalump said:**
> I have all my themes saved on a different hard disk. So what you're saying is I would also have to copy the tar files over as well?

Do you happen to know where exactly the config file is that points to the tar files and all that?

As far as I know the themes are usually stored in /usr/share or in home directory, but I don't use gnome nor compiz so maybe they can enable the user to store the themes elsewhere as in our case (you said you have them on another harddisk).

In the live CD, the themes must reside in same directory structure as in your host system. For example, if your themes are in /media/sda4/theme you have to copy them as follows to you work dir

```
sudo cp -av --parents /media/sda4/themes ${WORK}/rootfs
```

If you are not sure what are the config files that store the settings for your theme, you can copy all the config files in your home directory as I explained in my previous post.

---

### Post by stumpalump on 2008-03-17
Capink, thanks for your continued help in this thread.

Sorry if I was unclear before. What I meant was that I download all the .tar.gz's to another hard disk and then apply them in emerald/gtk. So what I'm trying to accomplish is to have the liveDVD I create use my theme by default as opposed to the human theme when it boots.

It is using my custom loading screen and my gdm though.

I'm kinda new to linux still. So when I import a theme from a .tar, you're saying it gets stored in /usr/share so that's what I need to copy, right? 

Also, I guess it would help if I knew which .conf stored all the default user paths/settings for the buttons, metacity, and emerald themes.

Thanks in advance for your reply, Capink

---

### Post by Fragadelic on 2008-03-17
Take a look at the global gconf settings as most of it is stored there.

---

### Post by capink on 2008-03-17
> **stumpalump said:**
> Capink, thanks for your continued help in this thread.

Sorry if I was unclear before. What I meant was that I download all the .tar.gz's to another hard disk and then apply them in emerald/gtk. So what I'm trying to accomplish is to have the liveDVD I create use my theme by default as opposed to the human theme when it boots.

It is using my custom loading screen and my gdm though.

I'm kinda new to linux still. So when I import a theme from a .tar, you're saying it gets stored in /usr/share so that's what I need to copy, right? 

Also, I guess it would help if I knew which .conf stored all the default user paths/settings for the buttons, metacity, and emerald themes.

Thanks in advance for your reply, Capink

Anything in /usr/share is already copied in step B. So if the theme is there you only need to copy the config file.

I am not sure, but I think when you applied the theme it has gone to the ~/.themes and ~/.emerald/theme directories. You can check this directory and check if your theme is there. If it is, you need to copy these directories along with some config files ( I not positive about the config files because I am using difffernt desktop evironment but try the ones in the command below ):

```

for i in .gconf .local .emerald .gnome2 .themes .compiz
do
sudo cp -r --preseve=mode ~/${i} ${WORK}/rootfs/etc/skel
done
```



These include .gconf folder as suggested by Fragadelic.

Or you can try the remastersys script by Fragadelic with the backup option. A link to it is present now in my opening post.

---

### Post by capink on 2008-03-17
> **Fragadelic said:**
> Take a look at the global gconf settings as most of it is stored there.

Hi Fragadelic. I just started looking into your scirpt. It is very nice. I will post my comments (and questions later) when I have more time to look at it more.

---

### Post by Fragadelic on 2008-03-17
> **capink said:**
> Hi Fragadelic. I just started looking into your scirpt. It is very nice. I will post my comments (and questions later) when I have more time to look at it more.
Thanks.  I still have some work to do on it in terms of cleanup of /var for the dist mode but its coming along.

I did some checking and pwconv and grpconv do rebuild the shadow and gshadow files so the next version will just omit those.

Any suggestions are greatly appreciated.

---

### Post by Fragadelic on 2008-03-18
I think I will add BOOT=casper to the grub entries in remastersys as well.  This might be the reason some folks have been getting it stopping at the (initramfs).  Not 100% sure but worth a try anyway.

---

### Post by Fragadelic on 2008-03-18
I did some quick checking and cannot find any reference to BOOT=casper anywhere on the web.  Everything I see refers to only boot=casper so I don't think that is it.

I think some of the folks that had issues were using Hardy 8.04 and I found a bug about that.

---

### Post by capink on 2008-03-18
I think I realize where I got confused about this whole BOOT=casper and boot=casper. I am currently using Debian which uses live-initramfs as a fork for casper. 

The [live-initramfs]("http://live.debian.net/other/manpages/live-initramfs.7.html") man said to use BOOT=live. I then converted the guide to work for both casper and live-initramfs. But casper have the boot=casper. So to make the guide support both, I added both BOOT and boot options.

---

### Post by capink on 2008-03-18
> **Fragadelic said:**
> I think I will add BOOT=casper to the grub entries in remastersys as well.  This might be the reason some folks have been getting it stopping at the (initramfs).  Not 100% sure but worth a try anyway.

The problem of people being dropped to an initramfs shell does not happen only with custom made cds. I was dropped to the same shell by the live Ubuntu Feisty Cd. It seems that this problem happens with certain types of hardware.

---

### Post by Fragadelic on 2008-03-18
> **capink said:**
> I think I realize where I got confused about this whole BOOT=casper and boot=casper. I am currently using Debian which uses live-initramfs as a fork for casper. 

The [live-initramfs]("http://live.debian.net/other/manpages/live-initramfs.7.html") man said to use BOOT=live. I then converted the guide to work for both casper and live-initramfs. But casper have the boot=casper. So to make the guide support both, I added both BOOT and boot options.

That makes sense.

---

### Post by Fragadelic on 2008-03-18
> **capink said:**
> The problem of people being dropped to an initramfs shell does not happen only with custom made cds. I was dropped to the same shell by the live Ubuntu Feisty Cd. It seems that this problem happens with certain types of hardware.
you are correct.  I found some references of it with regards to using acpi=off in the boot params to get by it.  Looks like it has problems loading the filesystem.squashfs after it boots initramfs - maybe a module loading issue.

---

### Post by vbgeek on 2008-04-12
Just finished applying the step in the tutorial and burning DVD now, anxious to see how it turns out.  I found one problem I wanted to point out, E. 2. has a typo:

-----------------------------------------
2. Test the CD

Test using qemu emulator 

Code:
qemu -cdrom ~\live-cd.iso -boot d
-----------------------------------------

That needs to be a forward slash.

My use of this is probably somethign that has not been tested, I am creating a DVD from a VMWare instance of Ubuntu 7.10 Gutys.  I have customized that with apps I use in my job, including a VPN client for connecting to my companies network.  My goal here is to make an emergency Live DVD.  I am on call off-hours and get tired of lugging my laptop with me for the occassional times I need it.  If I can boot this up in another PC and get VPN access, it will be cool.  We will see what happens.

---

### Post by capink on 2008-04-12
Thank you for pointing out the typo. I have corrected it.

---

### Post by gjhicks on 2008-04-21
Hi,

Thanks very much for the clearly explained procedure.

I used it successfully to create a LiveCD of my much-abbreviated IceWM-Gutsy hard disk install.

Bu then have had a rather bizarre problem (or series of problems).

After the intial sucess, have not been able to 'make' another LiveCD, when running the ISO under Qemu, keep getting dropped to the 'initramfs' error.

Noticed a couple of things that might be having an effect:

1) after the remove non-system errors, my username is gone from /etc/passwd but the screen messages at the conclusion of making the squashfs file include a mention of my username.

2) a package called 'live-initramfs' is supposed to be removed from the filesystem.manifest, to prepare the '-desktop file, but such a package doesn't seem to exist on the system (I followed all the installation instructions).

Bearing in mind my very limited knowledge of this 'live cd building' stuff, the above may be unrelated to the failure but thought it was worth letting you know.

Thanks again for the work you have put in.

Used your

---

### Post by capink on 2008-04-21
> **gjhicks said:**
> 
After the intial sucess, have not been able to 'make' another LiveCD, when running the ISO under Qemu, keep getting dropped to the 'initramfs' error.


As noticed by [az]("http://ubuntuforums.org/member.php?u=844") in this [post]("http://ubuntuforums.org/showpost.php?p=4643009&postcount=18"), this sometimes happens with qemu. To be sure try burning the iso to a REwritable cd and test on your machine directly without an emulator.

> **gjhicks said:**
> 
after the remove non-system errors, my username is gone from /etc/passwd

That is intended and is normal. The live cd will create a user of its own called ubuntu upon boot.

> **gjhicks said:**
> 
but the screen messages at the conclusion of making the squashfs file include a mention of my username.


That is probably because some of the files in the system are owned by the main user. To rectify this problem run these commands just after the fisrt command in step B (after copying your filesystem):

```
sudo find ${WORK}/rootfs -user [COLOR="magenta"]username[/COLOR] -exec sudo chown --no-dereference root {} \;
```

```
sudo find ${WORK}/rootfs -group [COLOR="magenta"]username[/COLOR] -exec sudo chgrp --no-dereference root {} \;
```

Replace [COLOR="magenta"]username[/COLOR] with the username of your original system.

> **gjhicks said:**
> 
2) a package called 'live-initramfs' is supposed to be removed from the filesystem.manifest, to prepare the '-desktop file, but such a package doesn't seem to exist on the system (I followed all the installation instructions).


Indeed, I have corrected this mistake by removing live-initramfs from the variable REMOVE (in step D.2)

---

### Post by LuisPT on 2008-04-22
Thanks guys for this wonderfull tutorial.

Well, I've built about 5 or 6 livecd using this guide, BUT all the times I get the same problem:

When I'm booting the iso with QEMU the boot process stops at (initramfs) prompt !!!!

I've tried to add acpi=off in grub, but that didn't resolve the problem.

When I'm at initramfs prompt.

I've tried also to add all_generic_ide since in booting with Gutsy I have to this also, but no way it stops also when detecting some hardware.

Now I've tried with VirtualBox and it works well, so it was a problem with QEmu.

But now I have a another problem:
- I've installed a debootstrap system and made the live cd from it.
- I've installed xdm on debootstrap
- But when I arrive to XDM Login screen it prompts for a username and a password that I don't now (I've tried my login and pass that I use in my Ubuntu Gutsy but it doens't work)
- Can I disable the login in LiveCD? How?
- I've installed also ubiquity, so doest it ask me for a new user and password when It starts to make the installation to hard disk?

Sorry for so many questions, but I'm just so close to make my LiveCD/Installation Custom CD.

Thanks in advance for your help.

---

### Post by capink on 2008-04-22
Unfortunately casper only supports gdm and kdm. Try adding the following parameter to grub entry:

```
textonly
```

This should log you to a text terminal where you can start GUI by typing:

```
startx -- :1
```


Edit: You can modify grub parameters temporarily without remastersing the cd. look of instructions in this [link]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html").

---

### Post by relugrigorescu on 2008-05-01
I made a custom live cd of my gutsy 64 with remastersys and it's not workin'
I get this error message about gdm :
"Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist. Please correct GDM configuration and restart GDM"

What do i did wrong ?? What can i do ??

---

### Post by yakshbuntu on 2008-05-02
Fantastic post. Thanks a lot. I created LiveDVD of my hardy installation and I can get back hardy to the state in liveDVD using ubiquity installer.

---

### Post by RumorsOfWar on 2008-05-03
I just tried to use my install disk on another machine ( it has the same processor and similar vid card), and it hung at 94% while configuring hardware. 
I'm wondering if my install disk is missing some hardware components because I started out with the Alt-install in the first place.
Any ideas?

---

### Post by capink on 2008-05-03
Most hardware drivers in linux are either part of the kernel (kernel modules), or come with xorg (video and output input devices). So I don't think the alt install would make any difference. I don't know what is the cause of your problems, maybe a certain piece like a motherbord controller is not supported. Sometimes it is helpful to try the latest version of the kernel when you have trouble with hardware.

---

### Post by jw5801 on 2008-05-03
> **RumorsOfWar said:**
> I just tried to use my install disk on another machine ( it has the same processor and similar vid card), and it hung at 94% while configuring hardware. 
I'm wondering if my install disk is missing some hardware components because I started out with the Alt-install in the first place.
Any ideas?

Are you certain there isn't an error in the disk from when you burned it? That sounds much much more likely.

---

### Post by gjhicks on 2008-05-05
Hello Capink,

Thanks for the suggestions about the stray non-root owned files.

Am most pleased to report that I successfully made a live cd of my IceWm-Gutsy hard disk install.  The ISO file was 224mb - so now I will try and reduce it to fit onto a small CD.

Great guide!  Thanks a lot!

Geoff

---

### Post by capink on 2008-05-05
These are instructions for people who want a live CD containing a clean system (or a minimal rescue disc), you can build a new custom Ubuntu from scratch using debootstarp, and then apply the steps of the guide to make a live cd out of it. These are the steps that will replace step B & C in the [original guide]("http://ubuntuforums.org/showpost.php?p=4277073&postcount=1") for people who wish to build a custom system from scratch, instead of using their harddrive installation as a basis.


[COLOR="Red"]**[SIZE="3"]Note: Before doing the steps below, you must perform step A in the [original guide]("http://ubuntuforums.org/showpost.php?p=4277073&postcount=1").[/SIZE]**[/COLOR]

[SIZE="4"]_*B. Build a custom system from scratch using debootstrap[/SIZE]_*

1. Install debootstrap

```
sudo apt-get install debootstrap
```

2. Run debootstrap to install the basic packages:

```
sudo debootstrap [COLOR="Magenta"]natty[/COLOR] ${WORK}/rootfs
```

Replace [COLOR="Magenta"]natty[/COLOR] with any other version you want (e.g. maverick, lucid, .....)

This step will take time as the deb files are downloaded.


Now you have a system the contain the basic packages. At this stage this system can only work as chroot system. But in the next steps we will modify it to be full system.



3. Prepare the new system before chrooting into it:

Modify the new system sources list:

```
sudo [COLOR="Magenta"]gedit[/COLOR] ${WORK}/rootfs/etc/apt/sources.list
```

And place the following text into it:


> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="Magenta"]natty[/COLOR] main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="Magenta"]natty[/COLOR] main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) [COLOR="Magenta"]natty[/COLOR]-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) [COLOR="Magenta"]natty[/COLOR]-security main restricted universe multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) [COLOR="Magenta"]natty[/COLOR] free non-free 

Note: Replace [COLOR="Magenta"]natty[/COLOR] with your version name. e.g. maverick




Copy the following files to have internet access within the chroot environment:

```
for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ${WORK}/rootfs/etc/; done
```



4. Chroot into the new system:

```
sudo mount --bind /dev ${WORK}/rootfs/dev
```

```
sudo mount -t proc proc ${WORK}/rootfs/proc
```

```
sudo mount -t sysfs sysfs ${WORK}/rootfs/sys
```




```
sudo chroot ${WORK}/rootfs /bin/bash
```


[COLOR="Blue"]Note: All commands in blue are run within chroot.[/COLOR]

```
[COLOR="Blue"]LANG=[/COLOR]
```


5. Once in chroot, modify the new system:

```
[COLOR="#0000ff"]apt-get update --allow-unauthenticated[/COLOR]
```

This will give you GPG warning because of third party repositories (Codecs repositories). Ignore it and proceed.



6. Install the multimedia repository keyrings ( to prevent apt from complaining about missing GPG ):

```
[COLOR="#0000ff"]apt-get -qq install wget && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -[/COLOR]
```





7. Install some important packages not included in the base install performed by debootstrap, most notably is the kernel:

```
[COLOR="#0000ff"]apt-get install linux-generic linux-headers-generic ubuntu-minimal ubuntu-standard[/COLOR]
```


Now, we have a complete command line system







8. To have a GUI system, install:

```
[COLOR="#0000ff"]apt-get install [COLOR="Red"]xorg[/COLOR] [COLOR="Magenta"]gdm openbox[/COLOR] [COLOR="Gray"]fbpanel thunar firefox mplayer w32codecs scite gqview xarchiver rxvt gtk2-engines xcursor-themes ttf-bitstream-vera ttf-dejavu ttf-freefont[/COLOR][/COLOR]
```

[COLOR="Red"]xorg[/COLOR] in necessary for a GUI.
Replace [COLOR="Magenta"]openbox[/COLOR] with your favorite window manager.
Replace [COLOR="Magenta"]gdm[/COLOR] with your favorite login manager. (Or you can do without login manager and user startx if you want)
The rest is optional. You can ignore them or replace them with your favorite programs. if you are a gnome fan you can install gnome-core. kde fans can install kde. xfce fans can install xfce4 ......

Note: If you want to build a system identical to official ubuntu replace all the packages above with just one metapackage called ubuntu-desktop (kubuntu-desktop for kubuntu, xubuntu-desktop for xubuntu)



By now you have built a complete GUI system. 




9. Install Packages Essential for live CD:


```
[COLOR="Blue"]apt-get update[/COLOR]
```
```
[COLOR="Blue"]apt-get install casper lupin-casper[/COLOR]
```

casper contain the live scripts.


[COLOR="Gray"]3. (Optional) If you want your live cd to have an installer, install the Ubuntu installer:

```
[COLOR="Blue"]apt-get install ubiquity ubiquity-frontend-gtk[/COLOR]
```

[QUOTE]
Note: People using kde replace replace the previous command with

```
[COLOR="Blue"]apt-get install ubiquity ubiquity-frontend-kde[/COLOR]
```
[/COLOR]


[COLOR="Gray"](Optional Step)Install any packages you want to be in the CD. Some of the following packages are useful in emergency situations:

```
[COLOR="Gray"]sudo apt-get install gparted ms-sys testdisk wipe partimage xfsprogs reiserfsprogs jfsutils ntfs-3g ntfsprogs dosfstools mtools[/COLOR]
```

gparted: patitioning tool. It is automatically installed as a dependecy of ubiquity.
testdisk: Partition scanner and disk recovery tool.
wipe: Secure file deletion.
partimage: backup partitions into a compressed image file (like norton ghost).
xfsprogs reiserfsprogs jfsutils: Tools for handling different filesystems.
mtools: Tools for manipulating MSDOS files

[/COLOR]



10. Update the initramfs:

Set the kernel version of the chroot env:

```
[COLOR="Blue"]export kversion=`cd /boot && ls -1 vmlinuz-* | tail -1 | sed 's@vmlinuz-@@'`[/COLOR]
```

First update modules.dep:

```
[COLOR="Blue"]depmod -a $kversion[/COLOR]
```

Update the initrd

```
[COLOR="Blue"]update-initramfs -u -k $kversion[/COLOR]
```

As already metioned above, the initramfs is reponsible for much of the preparation required at the boot time of the CD/DVD. The updated initramfs now contain the live scirpts installed with casper.




11. Clean apt cache

```
[COLOR="Blue"]apt-get clean[/COLOR]
```



12. Clean some dirs and files:

```
[COLOR="Blue"]rm /etc/resolv.conf[/COLOR]
```

```
[COLOR="Blue"]rm /etc/hostname[/COLOR]
```




13. Exit chroot

```
[COLOR="Blue"]exit[/COLOR]
```





[COLOR="Red"]**[SIZE="3"]Now resume the steps of the [original guide]("http://ubuntuforums.org/showpost.php?p=4277073&postcount=1") jumping directly to step D.1 in the [original guide]("http://ubuntuforums.org/showpost.php?p=4277073&postcount=1").[/SIZE]**[/COLOR]

---

### Post by Angus77 on 2008-05-06
Knoppix somehow "just works" on both 32- and 64-bit systems.  Is there some way to make an Ubuntu disc that does the same?

---

### Post by capink on 2008-05-09
> **Angus77 said:**
> Knoppix somehow "just works" on both 32- and 64-bit systems.  Is there some way to make an Ubuntu disc that does the same?

I have never used Knoppix before. But just by looking at  their site it seems that they make a live CD that contains mixture of 32-bit and 64-bit applications. To be more specific almost all the packages are 32-bit except the kernel and the development tools like gcc, which are 64 bit.

My Understanding is that while a 32-bit applications can work on both 32-bit 64-bit processors, 64-bit applications can only work on 64-bit processors. So, I think the version of Knoppix you are talking about will only work on 64-bit processors, since it contains a 64-bit processor, which will not work on 32-bit processors.

From I gathered from their site, Knoppix 64-bit edition is using 32-bit applications for various technical considerations, one of which is to be able to fit the distro into one cd.

---

### Post by Angus77 on 2008-05-11
Well, except that I downloaded and burned a copy of both the Japanese and English editions of Knoppix 5.1, and it ran on my home desktop (a 64-bit AMD Athlonx2), my office computer (a 32-bit 500MHz AMD something-or-other---really slowly) and a laptop at a class I'm going to (a 32-bit 1.8GHz something-or-other).  I still use it at the class.

I'd like to customize an Ubuntu live disk and be able to use it at home, work and school, which I can't do right now.

[Puppy Linux]("http://www.puppylinux.com/") also works on both 32- and 64-bit systems.

---

### Post by Oldsoldier2003 on 2008-05-12
very nice and comprhensive tutorial, I'm replying from my live cd so that tells you it definitely works :) the one thing I am having problems with at the moment is for some reason the cd mounts sda2 as the / partition. If it makes any sense thats the partition where my minimal Ubuntu install for building the live cd resides. unmounting sda2 with umount -l doesnt solve the problem.

I have tried removing all references to the device in /etc/fstab prior to creating the squashfs filesystem but that doesn't fix the issue either.Oddly enough Gparted (when run from the live cd) reports this partition as full when it is only maybe 10% full. Any thoughts on how to workaround this?

---

### Post by capink on 2008-05-12
In step C.5 we delete the fstab file. So, the live CD is supposed to not have fstab file. Are you sure you went through this step?

To make sure, please mount the squashfs (after mounting the iso) and see if there is a /etc/fstab there or not. If it present, you will have to redo the steps of the guide making sure that you get rid of this file. Squashfs is a read-only filesystem so you cannot delete the file once it is in the squashfs.

---

### Post by Oldsoldier2003 on 2008-05-12
> **capink said:**
> In step C.5 we delete the fstab file. So, the live CD is supposed to not have fstab file. Are you sure you went through this step?

To make sure, please mount the squashfs (after mounting the iso) and see if there is a /etc/fstab there or not. If it present, you will have to redo the steps of the guide making sure that you get rid of this file. Squashfs is a read-only filesystem so you cannot delete the file once it is in the squashfs.

I ran through the steps again and realized the problem was that the script in step c-5 was the problem. Rather than try to figure out why its choking i'll manually delete the files and give it another run through.

---

### Post by rraj.be on 2008-05-21
Hello geeks.......

i have came up to the last step of making ISO..

i have not yet burnt a single disk in ubuntu.......

whether we have to insert blank disk before this step

```
E. Build the CD/DVD

1. Make the ISO file

sudo mkisofs -b boot/grub/stage2_eltorito \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-V "Custom Live CD" -cache-inodes -r -J -l \
-o ~/live-cd.iso $CD


```

i entered this code without inserting any disk and i got thefollowing result

```
raj@raj-dworkstation:~/cd$ sudo mkisofs -b boot/grub/stage2_eltorito \
> -no-emul-boot -boot-load-size 4 -boot-info-table \
> -V "Custom Live CD" -cache-inodes -r -J -l \
> -o ~/live-cd.iso $CD
Unknown file type (unallocated) /home/raj/cd/.. - ignoring and continuing.
Size of boot image is 4 sectors -> No emulation
  0.94% done, estimate finish Wed May 21 13:38:49 2008
  1.88% done, estimate finish Wed May 21 13:38:49 2008
  2.81% done, estimate finish Wed May 21 13:39:24 2008
  3.75% done, estimate finish Wed May 21 13:39:42 2008
  4.69% done, estimate finish Wed May 21 13:39:31 2008
  5.63% done, estimate finish Wed May 21 13:39:42 2008
  6.57% done, estimate finish Wed May 21 13:39:34 2008
  7.51% done, estimate finish Wed May 21 13:40:08 2008
  8.44% done, estimate finish Wed May 21 13:40:00 2008
  9.38% done, estimate finish Wed May 21 13:40:03 2008
 10.32% done, estimate finish Wed May 21 13:39:56 2008
 11.26% done, estimate finish Wed May 21 13:40:00 2008
 12.20% done, estimate finish Wed May 21 13:39:54 2008
 13.14% done, estimate finish Wed May 21 13:39:57 2008
 14.07% done, estimate finish Wed May 21 13:40:07 2008
 15.01% done, estimate finish Wed May 21 13:40:08 2008
 15.95% done, estimate finish Wed May 21 13:40:04 2008
 16.89% done, estimate finish Wed May 21 13:40:05 2008
 17.83% done, estimate finish Wed May 21 13:40:07 2008
 18.77% done, estimate finish Wed May 21 13:40:03 2008
 19.70% done, estimate finish Wed May 21 13:40:05 2008
 20.64% done, estimate finish Wed May 21 13:40:06 2008
 21.58% done, estimate finish Wed May 21 13:40:03 2008
 22.52% done, estimate finish Wed May 21 13:40:04 2008
 23.46% done, estimate finish Wed May 21 13:40:09 2008
 24.40% done, estimate finish Wed May 21 13:40:06 2008
 25.33% done, estimate finish Wed May 21 13:40:07 2008
 26.27% done, estimate finish Wed May 21 13:40:05 2008
 27.21% done, estimate finish Wed May 21 13:40:06 2008
 28.15% done, estimate finish Wed May 21 13:40:07 2008
 29.09% done, estimate finish Wed May 21 13:40:08 2008
 30.03% done, estimate finish Wed May 21 13:40:05 2008
 30.96% done, estimate finish Wed May 21 13:40:06 2008
 31.90% done, estimate finish Wed May 21 13:40:07 2008
 32.84% done, estimate finish Wed May 21 13:40:08 2008
 33.78% done, estimate finish Wed May 21 13:40:05 2008
 34.72% done, estimate finish Wed May 21 13:40:06 2008
 35.66% done, estimate finish Wed May 21 13:40:07 2008
 36.59% done, estimate finish Wed May 21 13:40:05 2008
 37.53% done, estimate finish Wed May 21 13:40:06 2008
 38.47% done, estimate finish Wed May 21 13:40:06 2008
 39.41% done, estimate finish Wed May 21 13:40:05 2008
 40.35% done, estimate finish Wed May 21 13:40:05 2008
 41.29% done, estimate finish Wed May 21 13:40:06 2008
 42.22% done, estimate finish Wed May 21 13:40:07 2008
 43.16% done, estimate finish Wed May 21 13:40:05 2008
 44.10% done, estimate finish Wed May 21 13:40:06 2008
 45.04% done, estimate finish Wed May 21 13:40:06 2008
 45.98% done, estimate finish Wed May 21 13:40:05 2008
 46.92% done, estimate finish Wed May 21 13:40:05 2008
 47.85% done, estimate finish Wed May 21 13:40:06 2008
 48.79% done, estimate finish Wed May 21 13:40:04 2008
 49.73% done, estimate finish Wed May 21 13:40:05 2008
 50.67% done, estimate finish Wed May 21 13:40:03 2008
 51.61% done, estimate finish Wed May 21 13:40:04 2008
 52.55% done, estimate finish Wed May 21 13:40:05 2008
 53.48% done, estimate finish Wed May 21 13:40:03 2008
 54.42% done, estimate finish Wed May 21 13:40:04 2008
 55.36% done, estimate finish Wed May 21 13:40:04 2008
 56.30% done, estimate finish Wed May 21 13:40:05 2008
 57.24% done, estimate finish Wed May 21 13:40:05 2008
 58.18% done, estimate finish Wed May 21 13:40:04 2008
 59.11% done, estimate finish Wed May 21 13:40:03 2008
 60.05% done, estimate finish Wed May 21 13:40:03 2008
 60.99% done, estimate finish Wed May 21 13:40:02 2008
 61.93% done, estimate finish Wed May 21 13:40:03 2008
 62.87% done, estimate finish Wed May 21 13:40:03 2008
 63.81% done, estimate finish Wed May 21 13:40:04 2008
 64.74% done, estimate finish Wed May 21 13:40:04 2008
 65.68% done, estimate finish Wed May 21 13:40:03 2008
 66.62% done, estimate finish Wed May 21 13:40:04 2008
 67.56% done, estimate finish Wed May 21 13:40:03 2008
 68.50% done, estimate finish Wed May 21 13:40:03 2008
 69.44% done, estimate finish Wed May 21 13:40:03 2008
 70.37% done, estimate finish Wed May 21 13:40:02 2008
 71.31% done, estimate finish Wed May 21 13:40:01 2008
 72.25% done, estimate finish Wed May 21 13:40:02 2008
 73.19% done, estimate finish Wed May 21 13:40:02 2008
 74.13% done, estimate finish Wed May 21 13:40:01 2008
 75.07% done, estimate finish Wed May 21 13:40:02 2008
 76.00% done, estimate finish Wed May 21 13:40:01 2008
 76.94% done, estimate finish Wed May 21 13:40:03 2008
 77.88% done, estimate finish Wed May 21 13:40:03 2008
 78.82% done, estimate finish Wed May 21 13:40:02 2008
 79.76% done, estimate finish Wed May 21 13:40:02 2008
 80.70% done, estimate finish Wed May 21 13:40:02 2008
 81.63% done, estimate finish Wed May 21 13:40:02 2008
 82.57% done, estimate finish Wed May 21 13:40:01 2008
 83.51% done, estimate finish Wed May 21 13:40:00 2008
 84.45% done, estimate finish Wed May 21 13:40:01 2008
 85.39% done, estimate finish Wed May 21 13:40:01 2008
 86.33% done, estimate finish Wed May 21 13:40:01 2008
 87.26% done, estimate finish Wed May 21 13:40:01 2008
 88.20% done, estimate finish Wed May 21 13:40:01 2008
 89.14% done, estimate finish Wed May 21 13:40:00 2008
 90.08% done, estimate finish Wed May 21 13:40:01 2008
 91.02% done, estimate finish Wed May 21 13:40:01 2008
 91.96% done, estimate finish Wed May 21 13:40:01 2008
 92.89% done, estimate finish Wed May 21 13:40:01 2008
 93.83% done, estimate finish Wed May 21 13:40:01 2008
 94.77% done, estimate finish Wed May 21 13:40:00 2008
 95.71% done, estimate finish Wed May 21 13:40:01 2008
 96.65% done, estimate finish Wed May 21 13:40:01 2008
 97.59% done, estimate finish Wed May 21 13:40:01 2008
 98.52% done, estimate finish Wed May 21 13:40:01 2008
 99.46% done, estimate finish Wed May 21 13:40:01 2008
Total translation table size: 2048
Total rockridge attributes bytes: 1593
Total directory bytes: 5226
Path table size(bytes): 34
Max brk space used 0
532875 extents written (1040 MB)
raj@raj-dworkstation:~/cd$ 
```


I dont know what to do now......

please any one could help me.

---

### Post by rraj.be on 2008-05-21
I boot from my live cd that i have made.
its just getting into the shell and not showing the llogin screen

please help me

---

### Post by rraj.be on 2008-05-21
Which player can i uae to play the 3Gp videos in ubuntu..

Whih codec must i use.

could any one give me the exact command plz

---

### Post by capink on 2008-05-22
> **rraj.be said:**
> Which player can i uae to play the 3Gp videos in ubuntu..

The combination of mplayer and w32codecs can play 3gp. Before installing w32codecs you have to edit /etc/apt/sources.list and add to it the following:

> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Note: Replace hardy with your vesion codename.

Add the GPG key of the above repository:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
```

```
sudo apt-get update && sudo apt-get install mplayer w32codecs
```

---

### Post by frozer on 2008-05-25
Hi Capink!

You made a great work! I try to make custom CD for educational purposes (I'm a teacher) with a few of services in text mode - DNS, iptables, dhcpd etc and used your guide to create it.

But after loading, init wont mount /cdrom, so system stops on (initrafs) prompt. 
/casper.log:
Begin: Running /scripts/casper-premount
Done.
Done.
Unable to find a medium containing a live file system

But I can see device /dev/scd0 with live root fs, and can mount it manually to /casper, then mount squashfs live fs to root... 

Any ideas?

Thanks.

---

### Post by MikeRussell on 2008-05-28
After I mount the newly created file system and enter a chroot environment (step C.1.), I am unable to apt-get anything.  Any reason this would happen?
Mike

---

### Post by capink on 2008-05-29
> **MikeRussell said:**
> After I mount the newly created file system and enter a chroot environment (step C.1.), I am unable to apt-get anything.  Any reason this would happen?
Mike

Make sure the file /etc/resolv.conf is copies to your chroot filesystem:

```
sudo cp -v /etc/resolv.conf ${WORK}/rootfs
```

The previous command must be run outside chroot.

---

### Post by bayrem on 2008-06-08
hi,

Thaks for u'rer great tuto :d

I got one prob but before that I would like to share some prob that i got and succed to find an issue :

1. for people how use a virtuel machine, guys u must replace $(uname -r) but the real kernel release like 2.6.14-22-generic and not use the VM kernel who looks like this 2.6.14-22-virtual. that do not create a bootable kernel for real machines :d

My prob is this :

I have a login screen and I cannot login in the system

So how can I diagnostic the prob :
make a working auto-login  OR making a working use that can login.

No matter for me

Thank u all

Regards

---

### Post by bayrem on 2008-06-08
The prob is not only a login prob, I got many prob like mouse .. and I think it is a module loading prob, more informations bellow.

I saw some critical error messages (about depmod et modprob):

**modeprob /lib/modules/2.6.22-14-generic/module.dep : no such file or directory**


and then many error messages with :

**user not known to underlying authentification module**

Help please

Regards

---

### Post by capink on 2008-06-08
> **bayrem said:**
> 
**modeprob /lib/modules/2.6.22-14-generic/module.dep : no such file or directory**


This is probably because you did not perform the first command in step C.4 (which builds the file module.dep). Try redoing the two commands in step C.4 replacing $(uname -r) with your kernel version, so the commands should look:

```
depmod -a 2.6.22-14-generic
```

```
update-initramfs -u -k 2.6.22-14-generic
```

These two steps are done within chroot.

If this does not solve your problem, I don't think I have any other solution. But if you receive error messages post them, maybe someone would be able to help.

---

### Post by bayrem on 2008-06-09
I think that you're missing to mount /sys in [COLOR="Red"]C.1[/COLOR] I think :

```
HOME$ sudo mount -t sys -o bind /sys livecd/sys
```

Then, I made a new environnement and recompile all

no prb anymore  with :
```
modeprob /lib/modules/2.6.22-14-generic/module.dep : no such file or directory
```

but still can't login autologin. It display me the login screen. 

I made this changes for live user:

```
HOME$ sudo nano /PATH/TO/HOME/LIVECD/etc/casper.conf 

export USERNAME="MYUSERNAME"

export USERFULLNAME="MYUSERNAME"

export HOST="MYUSERNAME"

export BUILD_SYSTEM="MYUSERNAME"
```

and here for the password :

```
mkpasswd -s motdepasse

E/RzddfzlTY0A

HOME$ sudo nano /PATH/TO/HOME/LIVECD/usr/share/initramfs-tools/scripts/casper-bottom/10adduser

set passwd/root-password-crypted E/RzddfzlTY0A

set passwd/user-password-crypted E/RzddfzlTY0
```

**Nothing to do cannot login with MYUSER and THE PASS I MADE.**

P.S: Didn't made the step [COLOR="Red"]C.8[/COLOR] to delete non system users (note: MYUSER used for live session does not exist in my system users, I specially created with liveCD), does it bother auto login?

ANY help please

Regards

---

### Post by capink on 2008-06-09
> **bayrem said:**
> 

P.S: Didn't made the step [COLOR="Red"]C.8[/COLOR] to delete non system users (note: MYUSER used for live session does not exist in my system users, I specially created with liveCD), does it bother auto login?

ANY help please

Regards

The thing that bothers the autologin is havein a user with an id more than 999. So if MYUSER id is less than 999, there should be no problem. Anyway, you can try doing the steps as they are (without adding MYUSER) and see if that makes any difference.

---

### Post by bayrem on 2008-06-09
I test without adding user + i change the ID of my users to 888 and 889
No way it this same thing

Does some servers bother the liveCD

I have mysql and apache2 + openssh installed on that cd.

I heard that could have some probs if /etc/passwd and /etc/groups are different or there is some missing users in one or the other :(

I gave both files :
[B]
```
/etc/passwd[/B]
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
bayrem:x:888:888:,,,:/home/bayrem:/bin/bash
coucou:x:889:889:,,,:/home/coucou:/bin/bash
sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin
messagebus:x:104:111::/var/run/dbus:/bin/false
haldaemon:x:105:112:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
mysql:x:107:115:MySQL Server,,,:/var/lib/mysql:/bin/false

```
**etc/groups**
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:bayrem
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:bayrem
fax:x:21:
voice:x:22:
cdrom:x:24:bayrem,haldaemon
floppy:x:25:bayrem,haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:bayrem
dip:x:30:bayrem
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:bayrem
sasl:x:45:
plugdev:x:46:bayrem,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:bayrem
nvram:x:105:
fuse:x:106:
crontab:x:107:
ssh:x:108:
lpadmin:x:109:bayrem
admin:x:110:bayrem
bayrem:x:888:
coucou:x:889:
messagebus:x:111:
haldaemon:x:112:
powerdev:x:113:haldaemon
gdm:x:114:
mysql:x:115:
```

I'm desesperate :confused:

I need u're lights 

Regards

---

### Post by knadoor on 2008-06-10
thanks,

however is there any way to adapt this method on a Red Hat based system, that is, a system not based on debian?

More specifically for Fedora.

Thanks.

---

### Post by capink on 2008-06-11
> **knadoor said:**
> thanks,

however is there any way to adapt this method on a Red Hat based system, that is, a system not based on debian?

More specifically for Fedora.

Thanks.

Unfortunately no. Because casper scripts depends a lot on debconf, so even if you converted the casper debian package into rpm package, I am afraid it is not going to work.

But while gathering information for this guide, I think I saw some solutions for Fedora. So try searching google, you may find something. Also check this [site]("http://www.livedistro.org/").

---

### Post by Keith Hedger on 2008-06-14
Exellent howto booted to live cd first time, one question though the live cd booted to 800x600 how can i get it to use the nvidia driver that my main system uses ( or even just a higher resolution )

---

### Post by capink on 2008-06-14
> **Keith Hedger said:**
> Exellent howto booted to live cd first time, one question though the live cd booted to 800x600 how can i get it to use the nvidia driver that my main system uses ( or even just a higher resolution )

To keep your X settings don't delete the xorg.conf in step C.4. That works for me in Debian. But I am not sure about hardy because I have not tried it, and I heard it has a new way of setting resolution. You can find an answer to that in threads about resolution in hardy in forums.

---

### Post by spicewoodleo on 2008-06-17
I am having the same problem as RumorsOfWar. When I try to install from an image I generated from the above procedure, I get a stall at 94%.  Here is what I am seeing:  I looked at /var/log/syslog, and it is indicating a failure resolving the UUID  in spite of the fact that I do indeed have this UUID on /dev/sda5 (see log below, and output from ls_vol).  Upon further digging in the ubiquity scripts, particularly in /usr/share/ubiquity/install.py, I found that the "findfs" was failing because it was being run as 'chroot /target'.  When I looked at '/target/dev', it only had two entries in it: 'null' and 'tty',.  I was expecting (and so was findfs) the full compliment of /dev/xxx entries including /dev/sda... stuff.  "findfs UUID=xxxxxx" works fine if not run as 'chroot target'.  Here is my question, what step in this process left me without entries in the /target/dev during the ubiquity install? and what can I do to get them to be there?  Or is this some problem with Ubiquity?

Thanks very much, Leo

Here are the logs:
...
python: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --add /usr/sbin/update-initramfs
ubiquity: Running depmod.
ubiquity: Not updating initrd symbolic links since we are being updated/reinstalled
ubiquity: (2.6.22-14.46 was configured last, according to dpkg)
ubiquity: Not updating image symbolic links since we are being updated/reinstalled
ubiquity: (2.6.22-14.46 was configured last, according to dpkg)
ubiquity: Running postinst hook script /sbin/update-grub.
ubiquity: Searching for GRUB installation directory ...
ubiquity: found: /boot/grub
ubiquity: findfs
ubiquity: :
ubiquity: Unable to resolve 'UUID=4ee62f6e-c3b7-4052-9a4a-c93954d81ee6'
ubiquity: ^M
ubiquity: Cannot determine root device.  Assuming /dev/hda1
ubiquity: This error is probably caused by an invalid /etc/fstab
ubiquity: Searching for default file ...
ubiquity: found: /boot/grub/default
ubiquity: Testing for an existing GRUB menu.lst file ...
ubiquity:
ubiquity:
ubiquity: Could not find /boot/grub/menu.lst file.
ubiquity: Would you like /boot/grub/menu.lst generated for you?
ubiquity: (y/N)
<<< stalls here >>>

root@ubuntu:# vol_id /dev/sda5
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=4ee62f6e-c3b7-4052-9a4a-c93954d81ee6
ID_FS_UUID_ENC=4ee62f6e-c3b7-4052-9a4a-c93954d81ee6
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

---

### Post by spicewoodleo on 2008-06-19
Figured this out.  (This in Ubuntu 7.10 anyway).
I did 3 things:
1> I mounted sys on livecd/sys, as above where the /proc and /dev directories are mounted.  (don't think it made much difference though)

2> I mounted /dev/.static/dev while running mksquashfs, so that some minimal /dev entries end up there, and...

3> (Probably what fixed it)
I renamed /boot/initrd.img-`uname -r` to /boot/initrd.img-`uname -r`.bak in the chrooted section (in blue) as some code down in /var/lib/dpkg/info/linux-image-`uname -r`.postinst was looking to see if the initrd.image-`uname -r` file was there or not.  If so, ubiquity was assuming I was taking an upgrade path and not an install path, and it was ending up in the weeds.

I did this by adding a line just after the "rm -f /boot/*.bak" line in the chroot (blue) section:

rm  /boot/*.bak 2>/dev/null   # (existing)
mv  /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.bak

This did  the trick for me.  Thanks.

Leo :guitar:

---

### Post by umairmehmood on 2008-06-23
Hello!
This is really an excellent guide.
I am facing a few problems though:

System: Debian

I installed a fresh copy of Debian and followed the guide.
All went fine. No errors or warnings.
When i try to emulate the image, using QEMU, i cant get into the graphical interface.

This is the output which i can see:

> Uncompressing Linux...Ok, booting the kernel..
....
...
Loading, please wait...

BusyBox v1.1.3 (Debian) Built in shell (ash)
Enter help for a list of built in commands

/bin/sh: cant access tty; job turned off
(initramfs)

This is the command based interface i see..
I would like to see the graphical interface.
Am i doing anything wrong here?

---

### Post by Oldsoldier2003 on 2008-06-23
> **umairmehmood said:**
> Hello!
This is really an excellent guide.
I am facing a few problems though:

System: Debian

I installed a fresh copy of Debian and followed the guide.
All went fine. No errors or warnings.
When i try to emulate the image, using QEMU, i cant get into the graphical interface.

This is the output which i can see:



This is the command based interface i see..
I would like to see the graphical interface.
Am i doing anything wrong here?
I've had issues running an ISO in QEMU as well. I have managed to get the same ISO to run in virtualbox, or when burned to a CD. Even though there may be a workaround, I blame QEMU...

---

### Post by umairmehmood on 2008-06-24
You were right.
That was a problem with the QEMU.

I have the image, but all other applications which i wanted to be in the live CD are not available.
How can i make the Live CD to have my custom apps.

I was hoping, the Livé CD would have the same structure as my working Linux copy. (I was hoping for the same Desktop environment too).

What am i missing?

---

### Post by Oldsoldier2003 on 2008-06-24
> **umairmehmood said:**
> You were right.
That was a problem with the QEMU.

I have the image, but all other applications which i wanted to be in the live CD are not available.
How can i make the Live CD to have my custom apps.

I was hoping, the Livé CD would have the same structure as my working Linux copy. (I was hoping for the same Desktop environment too).

What am i missing?

If you follow the instructions for making a live cd from your existing installation it will have the same structure. If you are wanting to keep your current home directory and settings dont remove it. if you are wanting to create a livecd user with the same desktop and settings, then put the configurations in /etc/skel

---

### Post by umairmehmood on 2008-06-24
okey....i need to try this...before i can ask you something more  :)

One Question.

Does it matter if you are making an ext2 installation?

The only difference as far as i know is, 
In a standard installation, the files are compressed and hence the installation size is minimal.
In Ext2 installation, the size expands to meet the current size of your existing environment, BUT being Fast.

So, does the ext2 installation create any difference ?

---

### Post by blazercist on 2008-06-24
nice howto

---

### Post by umairmehmood on 2008-06-24
?

---

### Post by jokermatt999 on 2008-06-26
Nice tutorial. How difficult is this to adapt to a different system? To be more specific, how difficult/different would it be for Damn Small Linux or Puppy Linux?

---

### Post by umairmehmood on 2008-06-28
> if you are wanting to create a livecd user with the same desktop and settings, then put the configurations in /etc/skel 

I can see how to transfer the files, but how should i have the same desktop background copied too ?

---

### Post by Oldsoldier2003 on 2008-06-28
> **umairmehmood said:**
> I can see how to transfer the files, but how should i have the same desktop background copied too ?

If you save the wallpaper image in your home directory and set the desktop to use that file, save that file into the same place in /etc/skel/ . your copied configs will reference the file so it has to be in /etc/skel to be copied to the new account , or the desktop background will be blank/colored , instead of having a background wallpaper.

---

### Post by talikarng on 2008-06-29
Apologies in advance if this has already been suggested; but could someone please advise me if this is in any way problematic.

Instead of letting debootstrap download the deb files to create the chroot environment I stopped it when it started downloading. As sudo I then copied all of the deb files from /var/cache/apt/archives into the the target's /var/cac...... and when I re-ran debootstrap it just unpackaged them.

Obviously this left a lot of useless files in the target's /var/cache/apt/archives; so I erased them all.

---

### Post by karika200 on 2008-07-09
Hi!

I followed your instructions, but my live system doesn't wotk :\ It starts the boot process, but crashes at the initramfs... Here's the screenshot: [http://kepfeltoltes.hu/080709/scrsht1_www.kepfeltoltes.hu_.jpg](http://kepfeltoltes.hu/080709/scrsht1_www.kepfeltoltes.hu_.jpg)
I write into the menu.lst the next 3 menu items:

title		Debian GNU/Linux, kernel 2.6.18-6-486 (by karika200)
kernel		/boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw
initrd		/boot/initrd.gz

title		Memtest86+
kernel		/boot/memtest68+.bin

title		Start the installed OS
root		(hd0)

Why can't it mount the rootfs?:\ It writes "No such device", but there is some loop device in /dev...

thx, karika200

---

### Post by prototype_angel on 2008-07-10
Hi,

Thanks for the great guide. We want to make a livecd for our university linux user group and distribute them in our tutorials, seminars, etc.

I made quite a few changes to a fresh install like setting the sources.list, adding some introduction documents, some new packages etc.

Q1. I'm hoping that it will work with all the machines ubuntu normally works with.

Q2. Do I need to worry about the user that I'm creating it as? Meaning if someone installs a fresh copy will they be locked into the same username and password that I used?

Q3. Moreover, I'd love it if I could remaster ubuntu and still make it work with wubi. can someone point me to such a guide?

Thanks

---

### Post by jedi453 on 2008-07-10
Hi, Thanks for the great guide capink!

I was curious though would it be possible to use lzma compression for mksquashfs. I think it would be a great way to fit a little extra on a cd. I am not sure exactly how to rebuild the kernel with support for reading from an archive compressed with lzma. I would guess you would have to use the package "lzma-source", but beyond that I'm not sure what to do. I think it would be great to get working on many systems that are just barely too big for a CD. The closest I've come so far is finding the pre-built kernel from "http://www.squashfs-lzma.org/", however I've found hardware support to be insufficient for my system. Is there a way to get the hardware support of Ubuntu while getting the better compression ratios as well?

If that doesn't work, is there any other way to get a better compression ratio?

Thanks

---

### Post by jedi453 on 2008-07-10
karika200, Try burning the disk you made to a cd or dvd then boot from that. I've had the same problem trying to use an emulator to run the liveCD. If you've tried that or it doesn't work, try using this instead for your grub menu.lst:

```

title		Debian GNU/Linux, kernel 2.6.18-6-486 (by karika200)
kernel		/boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd		/boot/initrd.gz

title		Memory Test
kernel		/boot/memtest86+.bin

title		Start the installed OS
root		(hd0)
chainloader +1

```


prototype_angel, as long as you delete the files Capink suggests and use the step to create the empty gdm file, it should work. I made them from a password protected account before and have not seen any problems. If your worried about keeping files in your home account, copy them to "/etc/skel" before following this process. Only copy files you want readily accessable on the CD to /etc/skel/ , they will automatically be copied to /home/ubuntu when the cd boots. Be careful about this, because putting too much in /etc/skel will use a lot of ram.

---

### Post by jedi453 on 2008-07-10
Angus77, looks like you posted a while ago, but I think the problem you were having is that you have a 64-bit install on your desktop. The live cd's you make from it will only work on 64-bit machines. If you install a 32-bit version of Ubuntu alongside the 64-bit version (back up your stuff first) Then the 32-bit version should be able to make live-cds that can run on both 32-bit and 64-bit processors.

---

### Post by karika200 on 2008-07-10
Ahh, I was dumb.. I thought the linux-image*.deb package contains the squashfs and the unionfs modules... Now, I have installed these packages, and it works fine.:)

thx ;]

---

### Post by capink on 2008-07-11
> **jokermatt999 said:**
> Nice tutorial. How difficult is this to adapt to a different system? To be more specific, how difficult/different would it be for Damn Small Linux or Puppy Linux?

If these distros are based on Debian, all you have to do is to follow the instructions for making a live Cd in Debian. But you will end up with a live CD without installer. Also you have to make sure that repositories of the debian based distro contain the package live-initramfs.

---

### Post by capink on 2008-07-11
> **prototype_angel said:**
> Hi,

Q1. I'm hoping that it will work with all the machines ubuntu normally works with.

It should.

> **prototype_angel said:**
> Q2. Do I need to worry about the user that I'm creating it as? Meaning if someone installs a fresh copy will they be locked into the same username and password that I used?

No, the installer will ask him for a new username and password.

> **prototype_angel said:**
> Q3. Moreover, I'd love it if I could remaster ubuntu and still make it work with wubi. can someone point me to such a guide?


Unfortunately, I don't have any experiece with wubi.

---

### Post by herger on 2008-07-11
Hi.
Really beautiful thread and how-to!
I used to use remastersys, but the iso was incredibly slow when I used it as a live cd...
I will try Your method, thanks

Herger

---

### Post by capink on 2008-07-11
> **jedi453 said:**
> Hi, Thanks for the great guide capink!

I was curious though would it be possible to use lzma compression for mksquashfs. I think it would be a great way to fit a little extra on a cd. I am not sure exactly how to rebuild the kernel with support for reading from an archive compressed with lzma. I would guess you would have to use the package "lzma-source", but beyond that I'm not sure what to do. I think it would be great to get working on many systems that are just barely too big for a CD. The closest I've come so far is finding the pre-built kernel from "http://www.squashfs-lzma.org/", however I've found hardware support to be insufficient for my system. Is there a way to get the hardware support of Ubuntu while getting the better compression ratios as well?

If that doesn't work, is there any other way to get a better compression ratio?

Thanks


I have not looked at lzma yet. But in debian lenny which I am currently using, there is lzma-modules-$(uname -r). So you might want to install the debian kernel in Ubuntu and see how it works. But I cannot guarntee it will work.

Note that you have to install the following packages from Debian repositories together:

```
sudo apt-get install linux-image-$(uname -r) squashfs-modules-$(uname -r) unionfs-modules-$(uname -r) lzma-modules-$(uname -r)
```

where $(uname -r) is the kernel version.


Or if you do not mind it, you can switch to Debian.

---

### Post by bkrsml on 2008-07-19
I will be reposting this message as a reply to the top level post.  I am only doing this because I accidently replied to the wrong thread.

I agree with the others that this is a very well written how-to.

I tried a subset of the instructions for a different but related goal.  The results were not quite what I was looking for but I still think these instructions are close.

I know I was taking a lot of liberties with my subset of the instructions but I am hoping someone can help me with this or at least point me in the right direction.

Below are the details of my goal, the steps I used to try to reach it, and the results.  Thanks in advance for any help.

GOAL:
I have an SDHC card (High Capacity SD card) on a USB reader.  The card has a physical write protect switch which is an important reason I am using it.  I want to be able to run Ubuntu from the card like it was a regular drive and to run it when the card is write locked.  This thread caught my attention because I would like the write locked sessions to use the same image as the read-write mode.  I do not mind having to perform some simple steps from the read-write boot every time I want to update the write-protected image.

ACTIONS:
I installed from the 8.04.1 desktop CD and that worked fine.  I installed a package, a printer, and did other configuration.  Then to support the write locked boot I did the following:

1. Updated Packages

2. I issued the last command of C.1
LANG=

3. Changed the initial users uid to 500 to get it under 1000
sudo usermod -u 500 <username>

4. Installed casper discover1 xresprobe
I would like the write-locked boot to use the GDM configuration from the install because my driver and resolution are not detected correctly by the 8.04.1 LiveCD on the system I am using to build and test this card.  However I would also like the card to be portable across a wide number of machines and be able to detect settings (for both read/write and write-locked boots).

5. I then did step C.4
sudo depmod -a $(uname -r)
sudo update-initramfs -u -k $(uname -r)

6. I did not do step C.5.  I ran this step on a previous attempt and it created problems.  I think this is because I am running from the same system I am modifying (no chroot).  I did not do steps C.6 and C.7 because space is not too much of an issue at this point.

7. I did not do step C.8 because I was hoping the user id change mentioned in my step 3) above would take care of the issue.

8. I did not do step C.9 again because space was not an issue.

9. I did not do step C.10 because I was hoping to use the GDM configuration from my read-write install.

10. I did not do step C.11 again because space was not an issue.

11. I modified /boot/grub/menu.lst
I added an entry by coping the default that was already there.  I added boot=casper and nopersistent
title		Read Only Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=<ID> BOOT=casper boot=casper nopersistent rw quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

RESULTS:
If I choose the installed read-write default option from the grub menu everything seems to perform just as before.

If I choose the new "Read Only" option I seem to get pretty much an uncustom LiveCD image.  I was automatically logged in to the Live Session User, my driver and resolution were incorrectly detected, the user I created on install is not available, a printer I had registered was not available, and a package I had loaded was not found (however casper, discover1, and xresprobe were installed according to Synaptic).

---

### Post by adamogardner on 2008-07-19
cli - tech difficulties. making bootable dvd

ok so I am following the steps. I was converting the directory tree into a squashfs and it just ceased:

adamogardner@CRONUS:~$ sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
sudo: unable to resolve host CRONUS
Parallel mksquashfs: Using 2 processors
Creating little endian 3.1 filesystem on //filesystem., block size 131072.
[============================ ] 73842/149545 49%

so I opened a new tab and tried it again but to no avail:

adamogardner@CRONUS:~$ sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
sudo: unable to resolve host CRONUS
Can't find a SQUASHFS superblock on //filesystem.
Failed to read existing filesystem - will not overwrite - ABORTING!
To force Mksquashfs to write to this block device or file use -noappend
adamogardner@CRONUS:~$

Is my disk too small? how can I tell? What can I do?

---

### Post by bab1 on 2008-07-19
> adamogardner@CRONUS:~$ sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
sudo: unable to resolve host CRONUS

This appears to be a DNS problem with your setup.  Not the LiveCD setup.  Check to see if your hostname is resolved correctly.

---

### Post by Oldsoldier2003 on 2008-07-19
> **bab1 said:**
> This appears to be a DNS problem with your setup.  Not the LiveCD setup.  Check to see if your hostname is resolved correctly.
Yes its a problem with sudo resolving the host. It happens a lot with upgraded installations since gutsy.
To the OP:
Make sure the hostname in /etc/hosts matches the name in /etc/hostname , also be aware that if your hostname file or hosts file list your computer as hostname.somedomain sudo will fail. To fix it launch a text editor and remove the suffix (.somedomain). (Don't forget that you need to edit these files as superuser:
```
sudo nano /etc/hosts
```

---

### Post by bkrsml on 2008-07-20
This is was originally posted as a reply to a sub-thread.  I am now trying to post it as a reply to the top level post.  Sorry for the duplicate.

I agree with the others that this is a very well written how-to.

I tried a subset of the instructions for a different but related goal.  The results were not quite what I was looking for but I still think these instructions are close.

I know I was taking a lot of liberties with my subset of the instructions but I am hoping someone can help me with this or at least point me in the right direction.

Below are the details of my goal, the steps I used to try to reach it, and the results.  Thanks in advance for any help.

GOAL:
I have an SDHC card (High Capacity SD card) on a USB reader.  The card has a physical write protect switch which is an important reason I am using it.  I want to be able to run Ubuntu from the card like it was a regular drive and to run it when the card is write locked.  This thread caught my attention because I would like the write locked sessions to use the same image as the read-write mode.  I do not mind having to perform some simple steps from the read-write boot every time I want to update the write-protected image.

ACTIONS:
I installed from the 8.04.1 desktop CD and that worked fine.  I installed a package, a printer, and did other configuration.  Then to support the write locked boot I did the following:

1. Updated Packages

2. I issued the last command of C.1
LANG=

3. Changed the initial users uid to 500 to get it under 1000
sudo usermod -u 500 <username>

4. Installed casper discover1 xresprobe
I would like the write-locked boot to use the GDM configuration from the install because my driver and resolution are not detected correctly by the 8.04.1 LiveCD on the system I am using to build and test this card.  However I would also like the card to be portable across a wide number of machines and be able to detect settings (for both read/write and write-locked boots).

5. I then did step C.4
sudo depmod -a $(uname -r)
sudo update-initramfs -u -k $(uname -r)

6. I did not do step C.5.  I ran this step on a previous attempt and it created problems.  I think this is because I am running from the same system I am modifying (no chroot).  I did not do steps C.6 and C.7 because space is not too much of an issue at this point.

7. I did not do step C.8 because I was hoping the user id change mentioned in my step 3) above would take care of the issue.

8. I did not do step C.9 again because space was not an issue.

9. I did not do step C.10 because I was hoping to use the GDM configuration from my read-write install.

10. I did not do step C.11 again because space was not an issue.

11. I modified /boot/grub/menu.lst
I added an entry by coping the default that was already there.  I added boot=casper and nopersistent
title		Read Only Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=<ID> BOOT=casper boot=casper nopersistent rw quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

RESULTS:
If I choose the installed read-write default option from the grub menu everything seems to perform just as before.

If I choose the new "Read Only" option I seem to get pretty much an uncustom LiveCD image.  I was automatically logged in to the Live Session User, my driver and resolution were incorrectly detected, the user I created on install is not available, a printer I had registered was not available, and a package I had loaded was not found (however casper, discover1, and xresprobe were installed according to Synaptic).

---

### Post by capink on 2008-07-20
> **bkrsml said:**
> 

GOAL:
I have an SDHC card (High Capacity SD card) on a USB reader.  The card has a physical write protect switch which is an important reason I am using it.  I want to be able to run Ubuntu from the card like it was a regular drive and to run it when the card is write locked.  This thread caught my attention because I would like the write locked sessions to use the same image as the read-write mode.  I do not mind having to perform some simple steps from the read-write boot every time I want to update the write-protected image.



If I understood what you want to do properly, this [link]("http://ubuntuforums.org/showthread.php?t=707230") might help you achieve what you want. The method outlined there uses live-initramfs instead of casper. Keep in mind that people had a mixed results using this method depending on their hardware as well as the size of the image they are creating.

---

### Post by bkrsml on 2008-07-21
Thanks capink.  I looked at the link and it appears that it might get me what I want.  I am also going take a closer look at initramfs, live-initramfs, and casper.  I think I need to understand them at a lower level.

---

### Post by Rurushu on 2008-07-23
Thanks for the tutorial... It is really helpful

I have few questions, if that possible...

1. When I reboot my LiveCD, everything goes well.. grub starts, I choose an option, ubuntu loading, and then BusyBox shell starts instead of loading the system...

I tried cat casper.log

```
(initramfs) cat casper.log
/init: /init: 1: cannot open /dev/fd0: No such device or address
stdin: error 0
/init: /init: 1: cannot open /dev/fd0: No such device or address
stdin: error 0
/init: /init: 1: cannot open /dev/fd0: No such device or address
stdin: error 0
/init: /init: 1: cannot open /dev/fd0: No such device or address
stdin: error 0
Unable to find a medium containing a live file system
```

[EDIT]: ISSUE 1 SOLVED...

2. If I created a new filesystem, manifest, manifest-desktop and md5sum.text files... then replaced the files in ubuntu live cd with the new files... well that be enough? If no, why?!

Thanks alot

---

### Post by karika200 on 2008-07-24
In debian lenny repositories I can't found the unionfs modul for the precompiled(2.6.25) kernel, but there is a package aufs. I installed aufs, but at boot, it requires unionfs. What should I do?:\

---

### Post by karika200 on 2008-07-24
> **karika200 said:**
> In debian lenny repositories I can't found the unionfs modul for the precompiled(2.6.25) kernel, but there is a package aufs. I installed aufs, but at boot, it requires unionfs. What should I do?:\

union=aufs boot parameter rlz.. ^^ But now, I have kernel panic with the message "specify the file system"...

---

### Post by LuisPT on 2008-08-05
I'm making a livecd using a debootstrap (hardy 8.04.1) installation.

In STEP D1 (since I'm building from debootstrap) I've replaced the three commands of the original guide with the ones from appendix.2.

OK, everyting cool.

BUT, since I also installed ubiquity in deboostrap, I think I need to run the commands in Step D2 in order to Generate the manifest:

So I do:
sudo chroot ${WORK}/rootfs dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ${CD}/${FS_DIR}/filesystem.manifest

and:
sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}


**BUT when I do the following command:**
sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}

**IT RETURNS AN ERROR.**

Any Idea????

---

### Post by LuisPT on 2008-08-05
> **LuisPT said:**
> I'm making a livecd using a debootstrap (hardy 8.04.1) installation.

In STEP D1 (since I'm building from debootstrap) I've replaced the three commands of the original guide with the ones from appendix.2.

OK, everyting cool.

BUT, since I also installed ubiquity in deboostrap, I think I need to run the commands in Step D2 in order to Generate the manifest:

So I do:
sudo chroot ${WORK}/rootfs dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ${CD}/${FS_DIR}/filesystem.manifest

and:
sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}


**BUT when I do the following command:**
sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}

**IT RETURNS AN ERROR.**

Any Idea????

Sorry to bump again, but I forgot to give details about the error that happens to me when I do command sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop} in step D2.

> **[COLOR="Red"]cp: destination file argument is missing after`/home/cd/casper/filesystem.manifest{,-desktop}'[/COLOR]**
Try 'cp --help' for more informations
sed: it's not possible to read  /home/cd/casper/filesystem.manifest-desktop: File or directory doesn't exist
sed: it's not possible to read  /home/cd/casper/filesystem.manifest-desktop: File or directory doesn't exist
sed: it's not possible to read  /home/cd/casper/filesystem.manifest-desktop: File or directory doesn't exist
sed: não é possivel ler /home/cd/casper/filesystem.manifest-desktop: Ficheiro ou directoria inexistente
sed: it's not possible to read  /home/cd/casper/filesystem.manifest-desktop: File or directory doesn't exist
sed: it's not possible to read  /home/cd/casper/filesystem.manifest-desktop: File or directory doesn't exist
sed: it's not possible to read  /home/cd/casper/filesystem.manifest-desktop: File or directory doesn't exist
[COLOR="Red"]umount: /home/work/rootfs/dev: device is busy
umount: /home/work/rootfs/dev: device is busy[/COLOR]
Parallel mksquashfs: Using 2 processors
Creating little endian 3.1 filesystem on /home/cd/casper/filesystem.squashfs, block size 131072.
[==================================================================================================================             ] 25072/27696  90%


(I've translate the error to english, so sorry for some mistake).

Any Idea of what's happening???? :confused:

---

### Post by capink on 2008-08-05
> **LuisPT said:**
> Sorry to bump again, but I forgot to give details about the error that happens to me when I do command sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop} in step D2.



(I've translate the error to english, so sorry for some mistake).

Any Idea of what's happening???? :confused:

The first problem is probably due to your shell being set as /bin/sh instead of /bin/bash. Since /bin/sh does not understand brace extension it does not interpret the command properly. To solve this problem try replacing the command with this:

```
sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest ${CD}/${FS_DIR}/filesystem.manifest-desktop
```


As for the second problem, I think it can be solved by replacing the following command in step D.3:

```
sudo umount ${WORK}/rootfs/dev
```

with this commmand:

```
sudo mount --move ${WORK}/rootfs/dev /dev
```

---

### Post by chris4585 on 2008-08-07
hello capink, I finally got back to what I was working on say... 5? months ago.  Well after scratching my head, reading your guide, a few times, I finally made my livecd based off ubuntu 8.04.1 (its not done yet) but I have a working copy.  You're guide is awesome! It was easier then I thought after words, I still have a few things to fix though, just small things I can figure out with time.

EDIT: I have a few questions though, while installing from the livecd ubiquity gave me a error, (I didn't record the msg) but it installed just fine, have you encountered that problem?  I'll reinstall it in virtualbox again to report it.

the files that are placed in /etc/skel/ are they copied to every new user that is created?

---

### Post by capink on 2008-08-08
> **chris4585 said:**
> 

EDIT: I have a few questions though, while installing from the livecd ubiquity gave me a error, (I didn't record the msg) but it installed just fine, have you encountered that problem?  I'll reinstall it in virtualbox again to report it.

the files that are placed in /etc/skel/ are they copied to every new user that is created?

I think the error you are talking about is related to ubiquity looking for language packages to install from a local repository on the cd. Since we have not created this repository on the cd it gives the error. Maybe this can be solved by preseeding ubiquity. I might try it in the future as I am busy at the moment. The important thing is that it does not affect the installation process.

As for your second question, yes. The files are copied from /etc/skel to newly created user home directory.

Hope it will go smooth for you and you will enjoy your cutom made distro.

---

### Post by capink on 2008-08-08
> **chris4585 said:**
> 

EDIT: I have a few questions though, while installing from the livecd ubiquity gave me a error, (I didn't record the msg) but it installed just fine, have you encountered that problem?  I'll reinstall it in virtualbox again to report it.

the files that are placed in /etc/skel/ are they copied to every new user that is created?

I think the error you are talking about is related to ubiquity looking for language packages to install from a local repository on the cd. Since we have not created this repository on the cd it gives the error. Maybe this can be solved by preseeding ubiquity. I might try it in the future as I am busy at the moment. The important thing is that it does not affect the installation process.

As for your second question, yes. The files are copied from /etc/skel to newly created user home directory.

I Hope it will go smooth for you and you will enjoy your cutom made distro.

---

### Post by chris4585 on 2008-08-08
> **capink said:**
> I think the error you are talking about is related to ubiquity looking for language packages to install from a local repository on the cd. Since we have not created this repository on the cd it gives the error. Maybe this can be solved by preseeding ubiquity. I might try it in the future as I am busy at the moment. The important thing is that it does not affect the installation process.

As for your second question, yes. The files are copied from /etc/skel to newly created user home directory.

I Hope it will go smooth for you and you will enjoy your cutom made distro.

Thank you for replying and answering my questions. Ok the system seems to install just fine, besides that error, and when i'm using the system from hard disk nothing appears to be wrong.

Thanks again for the amazing guide and help

[IMG]http://i35.tinypic.com/2v3g3fo.jpg[/IMG]

---

### Post by umairmehmood on 2008-08-14
I am facing a weird problem.
I tried this guide for the first time and everything worked fine.
It generated a live ISO, which was working perfectly.

Now, using the same environment, with a couple of amendmends, i ran the procedure again for the Live ISO, but now my installation gets held up on the step:

"4. Convert the directory tree into a squashfs:"

The installer runs smoothly but gets held up at 96%.
No matter how long i wait, it does not resume.
I have to Ctrl+C to resume operations.

What do you think can the problem be ?

> 
root@opennms-liveCD:~# sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
Parallel mksquashfs: Using 1 processor
Creating little endian 3.1 filesystem on /home/opennms/Desktop/sample/cd/casper/filesystem.squashfs, block size 131072.
[===========================================================================================    ] 108436/112061  96%



---

### Post by capink on 2008-08-14
I don't know what is the cause of your problem. Maybe it is because the command is trying to append to the old squashfs instead of creating a new one. If this is the reason, then it can be solved by either deleting the old squashfs or replacing the command with the following:

```
sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} [COLOR="Red"]-noappend[/COLOR]
```

---

### Post by chris4585 on 2008-08-15
I agree with capink, I always delete my old squashfs before making a new one, just seems logical to me

---

### Post by umairmehmood on 2008-08-15
I did delete the contents of WORK and CD before running the scripts for new Image.

I now tried the command as advised:

> sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} -noappend

but still the same problem.
The squashfs stucks at 96%.

---

### Post by umairmehmood on 2008-08-16
I tried everything from scratch now.
Installed a fresh copy of Ubuntu 8.0.4 desktop.

Installed all necessary modules and then ran the scripts as mentioned in the guide.

The installer halts at the end.

> root@open-liveCD:~# sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} -noappend
Parallel mksquashfs: Using 1 processor
Creating little endian 3.1 filesystem on /home/open/cd/casper/filesystem.squashfs, block size 131072.
[================================================================================    ]  99466/103602  96%



With WORK:/tmp/work
CD: /home/open/cd
I am running ubuntu as a virtual Image using VMWARE. 

I don't understand.
The same settings were working fine before.

Some help would sure be appreciated!

---

### Post by chris4585 on 2008-08-16
why not if you dont find the solution, make a partition, about 4GB at most, and install ubuntu on there and start over? thats the only solution i can think of

EDIT: if you do that try copying your /work/rootfs/ to the new installation and try making a new squashfs and if the same thing happens then its either something to do with your rootfs or something i have no clue about..

sorry just trying to help

---

### Post by user11 on 2008-08-16
Or you could just use remastersys. I googled it, downloaded it, and now I can make custom live boot CDs with it. The only catch is that it doesn't save some important setting like auto login / automatic login, which I fixed by just editing /etc/gdm/gdm.conf before backing up (I also edited the UTC option in /etc/default/rcS). 

Now if I can just keep remastersys from deleting the /etc/timezone file I'm set. By the why, would anyone know how to fix that? :?

---

### Post by umairmehmood on 2008-08-17
chris4585:
I appreciate your help :)
I tired again but the same problem.
Really strange.

User11:

I tried Remastersys.
Remaster is in fact the same script automated!
I created the Live Image without any problem :D

I installed a few services like Tomact etc.
Now when i start Ubuntu form live image, it loads up tomcat too.
But i can't access it through the web interface.

I mean, [http://localhost:8081](http://localhost:8081) does not respond. !!

Could you think of any known problem ?

---

### Post by Skip Da Shu on 2008-08-17
> **capink said:**
> Can you confirm that it actually worked for you.

I'm really after a duplicate install from one of my dedicated 'number crunchers'... down to the same single user and password would be fine.  The only thing I really want different from machine to machine is the static IP address and hostname.

I've read thru this entire thread and it certainly seems as close as I've found so far and seems so well written that even "I" **might** be able to do it.

I have not looked into Remastersys yet, should I?

Sure wish I'd found this 5 machines ago.

Noob questions:

1) Is there any reason that you can think of that this would not work for on a Xubuntu 64b v8.04 (Hardy) system?

2) Since the Xubuntu machines don't have a CD burner on them can I create the .iso and save it on some samba shared storage and do the actual burn over on my WinXP box, then test it in a CD-ROM on the Xubuntu machine?

3) Lastly, and of less importance... Are there any simple changes to make my repeatable install even more complete?
 a) user=*me* & pw=*mine*
 b) gkrellm theme (by copying in home?)
 c) desktop launchers (by copying in home?}
 d) sources.list (assume will have to overlay after the install)
 e) apt proxy settings (only need to have the file /etc/apt/apt.conf.d/01proxy included)
 f) X11vnc setup (gdm.conf-custom, /etc/gdm/Init/Default, remote PW is someplace in Home also)
 g) xorg.conf (they all use same display when it's attached and all use vesa driver, assume I'll have to copy over after install)

Thanx in advance, Skip

---

### Post by Skip Da Shu on 2008-08-17
> **fragadelic said:**
> 10 - there are certain apps and libraries that ubuntu doesn't have on their livecd's and for whatever reason they cause the livecd to fail if they are installed - no workaround

delete me

---

### Post by umairmehmood on 2008-08-17
Is there any restriction to the live Cd as what apps can be run and others which cant.

For example, Is it only supposed to run system related apps and ignore user specified ones ?

I am observing this strange behavior with Tomcat.
Its included in the live distro. It is running perfectly, but i can't access my webapps.

---

### Post by capink on 2008-08-17
> **Skip Da Shu said:**
> 
I have not looked into Remastersys yet, should I?


Remastersys can do what this guide is doing in an automated way (i.e make a distribution from your hard disk installation). So it can save you the hussle if you are not comfortable with the command line. Also the remastersys author is very friendly and is open for questions. You can find a link to remastersys site at the end of the opening post of this thread.

The only thing that can be done using this method and not with remastersys, is creating a clean distro using the debootstrap method outlined in the guide.


> **Skip Da Shu said:**
> 
1) Is there any reason that you can think of that this would not work for on a Xubuntu 64b v8.04 (Hardy) system?

I have not tested it, but it should work. The only caveat here is that you will have to perform the instructions from a system with 64 bit kernel, otherwise you will not be able to chroot.

> **Skip Da Shu said:**
> 
2) Since the Xubuntu machines don't have a CD burner on them can I create the .iso and save it on some samba shared storage and do the actual burn over on my WinXP box, then test it in a CD-ROM on the Xubuntu machine?

Yes you can. But I do not have any experince in samba.
You can also test the iso in a virtual machine like virtualbox or vmware before burning it.

> **Skip Da Shu said:**
> 
 a) user=*me* & pw=*mine*

I am not sure what you mean?

> **Skip Da Shu said:**
> 
 b) gkrellm theme (by copying in home?)

Yes. But instead of copying to home you will copy to /etc/skel. Refer to the the end of step B to see how to do it

> **Skip Da Shu said:**
> 
 c) desktop launchers (by copying in home?}

Same as abobe. It is possible by creating a directory:

```
sudo mkdir ${WORK}/rootfs/etc/skel/Desktop
```


and copying the launchers to this directory.



> **Skip Da Shu said:**
> 
 d) sources.list (assume will have to overlay after the install)


Yes. You simply copy the sources.list file to:

```
${WORK}/rootfs/etc/apt
```

> **Skip Da Shu said:**
> 
 e) apt proxy settings (only need to have the file /etc/apt/apt.conf.d/01proxy included)

Same as above.

> **Skip Da Shu said:**
> 
 f) X11vnc setup (gdm.conf-custom, /etc/gdm/Init/Default, remote PW is someplace in Home also)

I do not advise missing with gdm config files because it can prevent the cd from logging in.

> **Skip Da Shu said:**
> 
 g) xorg.conf (they all use same display when it's attached and all use vesa driver, assume I'll have to copy over after install)

Yes.

---

### Post by nimam on 2008-08-19
* How can the name of live-session-user be changed from 'ubuntu' to our own?
* How can we use Ubuntu's own splashimage in grub for booting from cd?

---

### Post by capink on 2008-08-21
> **nimam said:**
> * How can the name of live-session-user be changed from 'ubuntu' to our own?

There are two ways to do this:
1. You can add the following parameter to your grub boot entry:

```
username=whatever_username_you_want
```

2. You can edit the file ${WORK}/rootfs/etc/casper.conf change the following entry:

```
export HOST="ubuntu"
```

into:

```
export HOST="whatever_username_you_want"
```



Note: If you do both methods, the first method will override the second one. That is, the username in your boot entry will override the username in /etc/casper.conf


> **nimam said:**
> * How can we use Ubuntu's own splashimage in grub for booting from cd?

To be able to use Ubuntu's splash Image you need to have the same exact kernel version in your system. IThis is not usually the case because the kernel in the splash image is usually older than your system kernel (if you are updating your system you will most likely have a newer version).

Supposing that you have the same kernel version as that of Ubuntu splash image, you have to do the following two steps:

1. Create the following directory:

```
sudo mkdir /casper
```

and place the splash image into it

2. Add the following entry to your grub menu:

```

title		RAM Session
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		[COLOR="Blue"]/boot/vmlinuz-$(uname -r)[/COLOR] BOOT=casper ro quiet splash
initrd		[COLOR="Blue"]/boot/initrd.img-$(uname -r)[/COLOR]

```

The text highlighted in [COLOR="Blue"]blue[/COLOR] should match the corresponding parts of your main system entry.



One the other hand, if your kernel is newer. You will have to extract the following two files from the splash image:

/boot/vmlinuz-....
/boot/initrd.img-.....

and place those two files in your /boot directory


Then you will add this entry to your grub file:

```

title		RAM Session
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		[COLOR="Red"]/boot/vmlinuz-$(uname -r)[/COLOR] BOOT=casper ro quiet splash
initrd		[COLOR="Red"]/boot/initrd.img-$(uname -r)[/COLOR]

```

The text highlighted in [COLOR="Blue"]blue[/COLOR] should match the corresponding parts of your main system entry.

The text highlighted in [COLOR="Red"]red[/COLOR] should match version of the two files you extracted from the splash image.

---

### Post by DemonBob on 2008-08-22
For Intrepid

In step A.3 

```
sudo apt-get install mkisofs grub squashfs-tools linux-ubuntu-modules-$(uname -r) qemu
```

should be
```

sudo apt-get install mkisofs grub squashfs-tools linux-headers-$(uname -r) qemu
```

linux-ubuntu-modules was merged with linux-headers i believe. 

Posting from a custom Intrepid Live cd as we speak :D


Questions:
1. Does the toram work in this guide? 
2. You got any easy to follow guides on making a custom boot splash/grub splash?

---

### Post by capink on 2008-08-22
> **DemonBob said:**
> For Intrepid

In step A.3 

```
sudo apt-get install mkisofs grub squashfs-tools linux-ubuntu-modules-$(uname -r) qemu
```

should be
```

sudo apt-get install mkisofs grub squashfs-tools linux-headers-$(uname -r) qemu
```

linux-ubuntu-modules was merged with linux-headers i believe.

Thanks for posting this information. I will add it to the guide



> **DemonBob said:**
> 1. Does the toram work in this guide?


It is working for me in Debian lenny with live-initramfs. If I remember correctly, it did work with casper and gutsy (not so sure) when I first wrote this guide. I do not have hardy or intrepid so I am not sure.


> **DemonBob said:**
> 2. You got any easy to follow guides on making a custom boot splash/grub splash?

There is a link in the final notes section. The link is not working currently but it is still stored in [google cache]("http://216.239.59.104/search?hl=en&q=cache%3Aruslug.rutgers.edu%2F~mcgrof%2Fgrub-images&btnG=Google+Search&meta=").

---

### Post by armageddon08 on 2008-08-26
ok.......I used remastersys to transfer my hdd install to dvd. Now, I can boot off the dvd and install the system very well. After installation when I can't boot into Ubuntu. It says..

```
Grub Loading
Stage1.5
Error15
```

What does this mean?

In my original system I had a custom grub splash image installed. Is that causing any problem?

---

### Post by DemonBob on 2008-08-27
For those of you making your own distro. 

You can edit /etc/lsb_release to edit distro information, version number and stuff. 

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu intrepid (development branch)"

```

---

### Post by chris4585 on 2008-08-27
hey I've been continuously building onto my rootfs and recreating iso's etc..
but There's been a update with these packages:

  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-generic linux-libc-dev

I'm not sure what I'd have to do to update my CD dir.. I don't want to screw up my cd dir

Also I've tried to change my user@host but editing the /etc/casper.conf didnt work

here's the contents of the file:
> 
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM

export USERNAME="open"
export USERFULLNAME="Live session user"
export HOST="box"
export BUILD_SYSTEM="Ubuntu"

EDIT: wouldnt I just delete my CD dir and recreate it completely? If so I think that'd be easier

---

### Post by capink on 2008-08-28
> **chris4585 said:**
> 

I'm not sure what I'd have to do to update my CD dir.. I don't want to screw up my cd dir


You just chroot into your CD dir and apply the updates. Before doing so you will have to set the enviroment:

```
export WORK=~/work
export CD=~/cd
export FORMAT=squashfs
export FS_DIR=casper
```


```
sudo mount -o bind /dev/ ${WORK}/rootfs/dev
```


```
sudo mount -t proc proc ${WORK}/rootfs/proc
```



```
sudo chroot ${WORK}/rootfs /bin/bash
```


[COLOR="#0000ff"]Commands in Blue are done within a chroot.[/COLOR]


```
[COLOR="#0000ff"]LANG=[/COLOR]
```


```
[COLOR="Blue"]apt-get update[/COLOR]
```


```
[COLOR="#0000ff"]apt-get upgrade[/COLOR]
```

```
[COLOR="Blue"]exit[/COLOR]
```

```
sudo umount ${WORK}/rootfs/proc
```

```
sudo umount ${WORK}/rootfs/sys
```

```
sudo umount ${WORK}/rootfs/dev
```



> **chris4585 said:**
> 
Also I've tried to change my user@host but editing the /etc/casper.conf didnt work

here's the contents of the file:

I have never tried doing it but according to the man pages this should do it. make sure that you are changing the casper.conf file in the CD tree, not the one in your root partition.

Also there is another way to change the username in my previous post. You can check it.


> **chris4585 said:**
> 
EDIT: wouldnt I just delete my CD dir and recreate it completely? If so I think that'd be easier


Yes that would do it. But you don't have to because you can upgrade your cd tree as illustrated above.

---

### Post by chris4585 on 2008-08-28
> **capink said:**
> You just chroot into your CD dir and apply the updates. Before doing so you will have to set the enviroment:

```
export WORK=~/work
export CD=~/cd
export FORMAT=squashfs
export FS_DIR=casper
```


```
sudo mount -o bind /dev/ ${WORK}/rootfs/dev
```


```
sudo mount -t proc proc ${WORK}/rootfs/proc
```



```
sudo chroot ${WORK}/rootfs /bin/bash
```


[COLOR="#0000ff"]Commands in Blue are done within a chroot.[/COLOR]


```
[COLOR="#0000ff"]LANG=[/COLOR]
```


```
[COLOR="Blue"]apt-get update[/COLOR]
```


```
[COLOR="#0000ff"]apt-get upgrade[/COLOR]
```

```
[COLOR="Blue"]exit[/COLOR]
```

```
sudo umount ${WORK}/rootfs/proc
```

```
sudo umount ${WORK}/rootfs/sys
```

```
sudo umount ${WORK}/rootfs/dev
```





I have never tried doing it but according to the man pages this should do it. make sure that you are changing the casper.conf file in the CD tree, not the one in your root partition.

Also there is another way to change the username in my previous post. You can check it.





Yes that would do it. But you don't have to because you can upgrade your cd tree as illustrated above.

I think we got terms mixed up

Ok, what I meant by CD dir is /home/chris/CD/ not /home/chris/work/rootfs/

What I meant was do I need to change which kernel to boot from the /home/chris/CD/ as we create in the step D. Prepare The CD directory tree and E. Build the CD/DVD or does it even matter at all, because I had to install the same kernel on my host system and my grub did not change so is it just a update on the same kernel?

sorry for all the confusion

and if that isnt true then..

my simplist guess is just move my /home/chris/CD/ to somewhere else (just in case I need it) and recreate my CD tree, not my rootfs

I've tried editing /home/chris/work/rootfs/etc/casper.conf and made a ISO after words but the host and user did not update on the iso

> I have never tried doing it but according to the man pages this should do it. make sure that you are changing the casper.conf file in the CD tree, not the one in your root partition.

So.. you mean /home/chris/work/rootfs/ ?

because in the CD tree /home/chris/CD/

here is what I have:

> .
|-- boot
|   |-- grub
|   |   |-- menu.lst
|   |   `-- stage2_eltorito
|   |-- initrd.gz
|   |-- memtest86+.bin
|   `-- vmlinuz
|-- casper
|   |-- filesystem.manifest
|   |-- filesystem.manifest-desktop
|   `-- filesystem.squashfs
`-- md5sum.txt

and I dont see casper.conf

Thanks for the help

---

### Post by capink on 2008-08-28
> **chris4585 said:**
> I think we got terms mixed up

Ok, what I meant by CD dir is /home/chris/CD/ not /home/chris/work/rootfs/

What I meant was do I need to change which kernel to boot from the /home/chris/CD/ as we create in the step D. Prepare The CD directory tree and E. Build the CD/DVD or does it even matter at all, because I had to install the same kernel on my host system and my grub did not change so is it just a update on the same kernel?


Actually you are right. If the updates have a new kernerl version you will have to repeat step D after the doing all the steps in my previous post. That is because the kernel in /home/chris/CD/boot must be the same version as the one in the squashfs. You will not have to edit grub menu.list because it does not refernce the kernel version (in step D the kernel is renamed to vmlinuz). And finally, you will also have to repeat step E.

> **chris4585 said:**
> 
sorry for all the confusion

and if that isnt true then..

my simplist guess is just move my /home/chris/CD/ to somewhere else (just in case I need it) and recreate my CD tree, not my rootfs

You will have to recreate both because as I pointed out earlier, the kernel on /home/chris/CD/boot must match the kernel in the squashfs.

> **chris4585 said:**
> 
I've tried editing /home/chris/work/rootfs/etc/casper.conf and made a ISO after words but the host and user did not update on the iso



So.. you mean /home/chris/work/rootfs/ ?


Yes I mean /home/chris/work/rootfs/. Sorry for the confusion, it was my mistake.

---

### Post by chris4585 on 2008-08-28
> **capink said:**
> 
You will have to recreate both because as I pointed out earlier, the kernel on /home/chris/CD/boot must match the kernel in the squashfs.


I'd like to clarify again, that as long as the squashfs matches the CD tree I shouldn't have to recreate my rootfs.  What I've been doing is when I want to make a new ISO just delete my old squashfs file in the CD tree and recreate the squashfs

Its worked quite well, its ok everyone makes mistakes

Thanks for your help! :D

---

### Post by maybeway36 on 2008-09-01
Sometimes when I build the CD and run it in QEMU or VirtualBox, I end up at the initramfs/busybox prompt.
The /casper.log (in QEMU) reads:
```
Begin: Running /scripts/casper-premount ...
Done.
Done.
mount: Mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

---

### Post by niccholaspage on 2008-10-25
I am having trouble following this guide in Intrepid Ibex...

---

### Post by capink on 2008-10-26
> **niccholaspage said:**
> I am having trouble following this guide in Intrepid Ibex...

I have not tested it on Intrepid. I don't plan to test it on Intrepid untill it is officially released. But you can refer to post number 143 on this thread on the modifications required to get this working under Intrepid.

---

### Post by niccholaspage on 2008-10-26
Thank you.

---

### Post by chris4585 on 2008-11-08
ok I figured it out on my own to discover that.. (funny enough) the package discover1 isn't in intrepid..

so does this mean I use the package discover instead?

---

### Post by capink on 2008-11-09
Yes it should work fine with discover. Also note that you do not need to install the package linux-ubuntu-modules-$(uname -r) anymore as it is now part of the main kernel package in intrepid.

---

### Post by chris4585 on 2008-11-09
> **capink said:**
> Yes it should work fine with discover. Also note that you do not need to install the package linux-ubuntu-modules-$(uname -r) anymore as it is now part of the main kernel package in intrepid.

Thanks for the reply, I wasn't sure about discover, I already did know about the linux-ubuntu-modules-$(uname -r) though.

So linux-ubuntu-modules-$(uname -r) is only needed for the host system (gutsy or hardy), for creating any kind of LiveCD?

and

So linux-headers-(uname -r) is only needed for the host system (intrepid) for creating any kind of LiveCD?

The reason why I was asking is because I'm making some scripts that I've made to make life easier and needed to know.

If you're interested... they're a little crude but they do get the job done!

[http://boxbuntu.com/downloads/Scripts/plusone-livecd-scripts/]("http://boxbuntu.com/downloads/Scripts/plusone-livecd-scripts/")

---

### Post by penC on 2008-11-10
Excellent guide! Thank you for this!

  pen

---

### Post by capink on 2008-11-10
> **chris4585 said:**
> So linux-ubuntu-modules-$(uname -r) is only needed for the host system (gutsy or hardy), for creating any kind of LiveCD?

They are required for both the host and the target (only in gutsy and hardy). They are required in the host to be able to create a squahsfs image. And they are required in the target to be able to mount the squashfs and the unionfs.

> **chris4585 said:**
> So linux-headers-(uname -r) is only needed for the host system (intrepid) for creating any kind of LiveCD?


linux-headers-(uname -r) is not really required. You can put it if you want it as part of your system though.

> **chris4585 said:**
> 
If you're interested... they're a little crude but they do get the job done!

[http://boxbuntu.com/downloads/Scripts/plusone-livecd-scripts/]("http://boxbuntu.com/downloads/Scripts/plusone-livecd-scripts/")

Intersting idea. I thought about making a script for the whole procedure, but I decided against it because I thought chrooting and installing packages would be better done interactively to react to any problems that might arise. Also there is a script that does a similar thing to this guide called remastersys. You can check the link for the script in the first post in this thread.

---

### Post by niccholaspage on 2008-11-10
I got an errors at the end of following your guide.

---

### Post by chris4585 on 2008-11-10
> **capink said:**
> They are required for both the host and the target (only in gutsy and hardy). They are required in the host to be able to create a squahsfs image. And they are required in the target to be able to mount the squashfs and the unionfs.




linux-headers-(uname -r) is not really required. You can put it if you want it as part of your system though.



Intersting idea. I thought about making a script for the whole procedure, but I decided against it because I thought chrooting and installing packages would be better done interactively to react to any problems that might arise. Also there is a script that does a similar thing to this guide called remastersys. You can check the link for the script in the first post in this thread.

Thanks for the clarification

With the scripts I tried to emphasize how easy it is to edit the system once after the first iso is made.

---

### Post by capink on 2008-11-11
> **niccholaspage said:**
> I got an errors at the end of following your guide.

Can you post the error messages and clarify which steps triggerd them.

---

### Post by niccholaspage on 2008-11-12
I will after school.

---

### Post by Spitphire on 2008-11-15
Minor problem..  I must admit i'm in a bit unfamiliar territory with chroot & debootstrap.

Anyway - I created a working live CD using the debootstrap method.  I added another user, while still in chroot.  When I boot the cd i would like it to ask me for a login prompt and not log in directly as 'ubuntu'

Anyone know how to fix this?  This is a text-only boot, there is no GUI..

The reason I would like to do this is because I would like certain files to be available upon login.. for example my ssh keys which i put in the home directory of the new user i created.

What I'm trying to accomplish is a bootable disc that that I can insert into my media center pc and execute dd over a ssh connection to the server, to clone the drive for backup purposes.  But I only allow ssh sessions with key.. So i need the keys available on the live cd..

Long story short - i just need to know how to make it go to a login prompt on boot up and not auto login as 'ubuntu'.

Thanks,
-spit

---

### Post by chris4585 on 2008-11-15
> **Spitphire said:**
> Minor problem..  I must admit i'm in a bit unfamiliar territory with chroot & debootstrap.

Anyway - I created a working live CD using the debootstrap method.  I added another user, while still in chroot.  When I boot the cd i would like it to ask me for a login prompt and not log in directly as 'ubuntu'

Anyone know how to fix this?  This is a text-only boot, there is no GUI..

The reason I would like to do this is because I would like certain files to be available upon login.. for example my ssh keys which i put in the home directory of the new user i created.

What I'm trying to accomplish is a bootable disc that that I can insert into my media center pc and execute dd over a ssh connection to the server, to clone the drive for backup purposes.  But I only allow ssh sessions with key.. So i need the keys available on the live cd..

Long story short - i just need to know how to make it go to a login prompt on boot up and not auto login as 'ubuntu'.

Thanks,
-spit

It would be easier to do the following (in my opinion)

first you'd have to change the user name to your user name on the livecd

set the variables you set before

```
export WORK=~/work
export CD=~/cd
export FORMAT=squashfs
export FS_DIR=casper

sudo mount -t proc proc ${WORK}/rootfs/proc
sudo mount -t sysfs sysfs ${WORK}/rootfs/sys
sudo mount --bind /dev ${WORK}/rootfs/dev
sudo chroot ${WORK}/rootfs /bin/bash

[COLOR="Blue"]nano /etc/casper.conf[/COLOR]
```

change the USERNAME= to fit the username you want to ssh with in nano

then within chroot run these commands

```
[COLOR="Blue"]export kversion=`cd /boot && ls vmlinuz-* | sed 's@vmlinuz-@@'`
depmod -a ${kversion}
update-initramfs -u -k ${kversion}[/COLOR]
```

then exit out of chroot

set your variables you set before

```
export WORK=~/work
export CD=~/cd
export FORMAT=squashfs
export FS_DIR=casper

sudo rm ${CD}/boot/initrd.gz
find ${WORK}/rootfs/boot -iname 'initrd.img*' -exec sudo cp -vp {} ${CD}/boot/initrd.gz \;
```

this should work


then copy your ssh key into ${WORK}/rootfs/etc/skel

then remove the old user you created

I think using userdel

then of course make a new iso

what you should get with this, is a autologin with your username, from what I read this should be what you want

---

### Post by capink on 2008-11-15
> **Spitphire said:**
> 

Long story short - i just need to know how to make it go to a login prompt on boot up and not auto login as 'ubuntu'.

Thanks,
-spit

For this to be done you will have to use live-initramfs instead of casper. After this it is just a matter of adding to following option to your grub boot entry.

```
noautologin
```


Note: Another solution is to stick to casper and use ALT + F(2) to switch to another getty and log in as whatever user you wish.

Beware though that if you opt to use live-initramfs, you will not be able to install ubiquity (The Ubuntu installer) as it depends on casper. Also, you need to do some modifications to the guide. They are as follows:

1. In step A.1 replace:

```
export FS_DIR=casper
```

with:

```
export FS_DIR=[COLOR="#ff0000"]live[/COLOR]
```


2. Replace the command in Step C.2 with:

```
apt-get install [COLOR="Red"]live-initramfs[/COLOR] unionfs-modules-$(uname -r) discover1 xresprobe
```

Note that in order to install live-initramfs you have to enable the universe repository in your chroot ennviroment. Here are guides to enable universe [,CLI]("https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0")).

3. Skip step C.3 and D.2 as you will not be using ubiquity.

4. In Step D.5 Replace every occurence of BOOT=casper and boot=casper in menu.lst with BOOT=live and boot=live respectively.

5. To disable automatic login in a text only system, add the following line to your main boot entry in menu.lst (In step D.5):

```
noautologin
```

---

### Post by Spitphire on 2008-11-16
```

 This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM

export USERNAME="am"
export USERFULLNAME="am"
export HOST="lp"
export BUILD_SYSTEM="Ubuntu"

```

I decided to put the files I need in /etc/skel . Great idea btw, don't know why I didn't think about doing that.  Thank you!

I changed /etc/casper.conf (as seen above)

When I boot the live CD though it still logs me in as ubuntu@ubuntu.

Am I missing something?

---

### Post by capink on 2008-11-16
> **Spitphire said:**
> ```

 This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM

export USERNAME="am"
export USERFULLNAME="am"
export HOST="lp"
export BUILD_SYSTEM="Ubuntu"

```

I decided to put the files I need in /etc/skel . Great idea btw, don't know why I didn't think about doing that.  Thank you!

I changed /etc/casper.conf (as seen above)

When I boot the live CD though it still logs me in as ubuntu@ubuntu.

Am I missing something?

If I remember correctly, chris4585 had a the same problem. Changing the username in casper.conf does not have the intended effect. Maybe it is a bug in casper. Maybe if you try to create the user with an id less than 999 the settings in casper.conf will be honoured.

---

### Post by Spitphire on 2008-11-16
> **capink said:**
> If I remember correctly, chris4585 had a the same problem. Changing the username in casper.conf does not have the intended effect. Maybe it is a bug in casper. Maybe if you try to create the user with an id less than 999 the settings in casper.conf will be honoured.


Ok, I didn't add the user 'am', i put the files i wanted access to in /etc/skel . for casper.conf to work correctly does the user need to be added to the system? or does is it suppose to add the user specified in casper.conf to the system upon boot up?

If casper creates the user, to achieve the desired results of a id less than 999 do you think changing /etc/adduser.conf to reflect so that the first user added would have an id less than 999?

I could change the following in /etc/adduser.conf:

```

FIRST_SYSTEM_GID=100
LAST_SYSTEM_GID=997

FIRST_GID=998
LAST_GID=29999

``` 

I haven't tried it yet, I'm just not exactly sure how casper creates the user ubuntu..

---

### Post by chris4585 on 2008-11-16
> **Spitphire said:**
> ```

 This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM

export USERNAME="am"
export USERFULLNAME="am"
export HOST="lp"
export BUILD_SYSTEM="Ubuntu"

```

I decided to put the files I need in /etc/skel . Great idea btw, don't know why I didn't think about doing that.  Thank you!

I changed /etc/casper.conf (as seen above)

When I boot the live CD though it still logs me in as ubuntu@ubuntu.

Am I missing something?

I explained how to change the user on the livecd before, its not as simple as just changing the file /etc/casper.conf and making a new iso, you have to update-initramfs then delete the old initrd in ${CD}/boot/ then copy the new initrd it from ${WORK}/rootfs/boot/ to ${CD}/boot/

I've attached a script that helps set the variables for you in a automatic way

just change/edit the two variables at the top of the file Set Names to the same variables as before then run the script and you'll be set (hopefully)

at one part of the scriipt it may seem as if its frozen its not, I need to fix this

---

### Post by chris4585 on 2008-11-16
> **Spitphire said:**
> Ok, I didn't add the user 'am', i put the files i wanted access to in /etc/skel . for casper.conf to work correctly does the user need to be added to the system? or does is it suppose to add the user specified in casper.conf to the system upon boot up?

If casper creates the user, to achieve the desired results of a id less than 999 do you think changing /etc/adduser.conf to reflect so that the first user added would have an id less than 999?

I could change the following in /etc/adduser.conf:

```

FIRST_SYSTEM_GID=100
LAST_SYSTEM_GID=997

FIRST_GID=998
LAST_GID=29999

``` 

I haven't tried it yet, I'm just not exactly sure how casper creates the user ubuntu..

casper creates the user during booting up as I understand, I'd say you'd have to update the initrd for this too (just a guess) I'd go for it and see what happens.

Update on the user@host thing, yes I did have issues with it, usually you get by default either ubuntu@ubuntu or casper@live, I know how to change ubuntu@ubuntu but not the latter...

---

### Post by Spitphire on 2008-11-16
> **chris4585 said:**
> I explained how to change the user on the livecd before, its not as simple as just changing the file /etc/casper.conf and making a new iso, you have to update-initramfs then delete the old initrd in ${CD}/boot/ then copy the new initrd it from ${WORK}/rootfs/boot/ to ${CD}/boot/


That did the trick, update-initramfs appeared to be the problem.  Guess I overlooked that initially.  Thanks again for your help! 

Everything works great now.  

I put the cd in, it creates a network connection to local lan and asks me if i would like to backup or restore hard drive.  Upon selection it creates ssh connection to server and starts cloning or restoring..

Very handy tutorial, helped a lot!

-spit

---

### Post by chris4585 on 2008-11-16
glad it worked right, just the other day I figured out how to fix the same issue

---

### Post by Kopachris on 2008-12-18
Hey, is there a way to get more compression?  Say, a 1:5 ratio instead of a 1:3 ratio?  My uncompressed system is 3.4GB, and the compressed system is 1.2GB.  I really want to get it down to less than 700MB, but removing enough software to make room would defeat the purpose of making the distro.  And I really don't want to limit it DVD-only releases, either.  I tried squashing the squashfs (it sounded like a good thing to do at the time, if it would read the squash within the squash), but it gave a segfault.  Can I compress it any more or take out some unnecessary stuff, or am I SOL?

---

### Post by ckomurlu on 2008-12-23
> **maybeway36 said:**
> Sometimes when I build the CD and run it in QEMU or VirtualBox, I end up at the initramfs/busybox prompt.
The /casper.log (in QEMU) reads:
```
Begin: Running /scripts/casper-premount ...
Done.
Done.
mount: Mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

Hi,
Thank you capnik for this great guide.
I generated the iso file, apperently with no problem. When I boot it in vbox, in the middle of the splash screen, it falls into a initrmfs shell. I checked casper.log and saw the same error message that maybeway36 reported above. 
What can be the cause?

There is an issue which can be related to this problem: During the preparetion of the iso, the only unexpexted event was that, I received an error in this step:

sudo umount ${WORK}/rootfs/sys

it gives: umount: <some path>/work/rootfs/sys: not mounted

Another clue is that, the current kernel is not 2.6.24.19-generic. I use a patched version -patched with rtai-. Well, I copy-pasted the menu.lst content, as given in the guide.

Thanks in advance.

---

### Post by Millzy on 2009-01-12
I'm hoping people are still using this How To and someone may have a solution for me.

I'm running Ubuntu 8.10 Server and have successfully completed almost all of the steps but i'm stuck on:

```

sudo mkisofs -b boot/grub/stage2_eltorito \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-V "Custom Live CD" -cache-inodes -r -J -l \
-o ~/live-cd.iso $CD

Error Msg:

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Uh oh, I cant find the boot image 'boot/grub/stage2_eltorito' !

```

I have looked in the /boot/grub directory but the only file close is just called stage2 and it isn't a boot image.

Any help would be most appreciated, would be a pity to have got this far and just scrap it all.

---

### Post by Kopachris on 2009-01-12
> **Millzy said:**
> I'm hoping people are still using this How To and someone may have a solution for me.

I'm running Ubuntu 8.10 Server and have successfully completed almost all of the steps but i'm stuck on:

```

sudo mkisofs -b boot/grub/stage2_eltorito \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-V "Custom Live CD" -cache-inodes -r -J -l \
-o ~/live-cd.iso $CD

Error Msg:

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Uh oh, I cant find the boot image 'boot/grub/stage2_eltorito' !

```

I have looked in the /boot/grub directory but the only file close is just called stage2 and it isn't a boot image.

Any help would be most appreciated, would be a pity to have got this far and just scrap it all.

Yep, it looks like you messed up while making the boot image.  I think you're going to have to do it over again.

---

### Post by Millzy on 2009-01-14
Thanks for replying, I will run through it again sometime. I found another article on "Making a Local Repository" which will suite me fine for now, i realize that i will have to install packages manually but it will do.

Might look into customizing a "Ubuntu Live CD" as well, i have seen a few walk through's but none that really stand out like this one.

---

### Post by prowebber on 2009-01-14
Cool. Really have try this one out.

---

### Post by jedi453 on 2009-01-24
> **Millzy said:**
> I'm hoping people are still using this How To and someone may have a solution for me.

I'm running Ubuntu 8.10 Server and have successfully completed almost all of the steps but i'm stuck on:

```

sudo mkisofs -b boot/grub/stage2_eltorito \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-V "Custom Live CD" -cache-inodes -r -J -l \
-o ~/live-cd.iso $CD

Error Msg:

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Uh oh, I cant find the boot image 'boot/grub/stage2_eltorito' !

```

I have looked in the /boot/grub directory but the only file close is just called stage2 and it isn't a boot image.

Any help would be most appreciated, would be a pity to have got this far and just scrap it all.

@Millzy:

Are you sure you ran this command from step D.5? 

```
sudo find /boot /usr/lib/grub/ -iname 'stage2_eltorito' -exec cp -v {} ${CD}/boot/grub \;
```

If you follow the steps below I think you should be all set as long as you didn't delete the $CD and $WORK directories or any of their contents. Please tell me if this works, or doesn't work. If it doesn't work I might be able to help if you reply. Good Luck

Run this to redefine your variables (if you changed ~/work and/or ~/cd to something else the first time you did this, change them back to those now):

```
export WORK=~/work
export CD=~/cd
export FORMAT=squashfs
export FS_DIR=casper
```

Then, run this to make sure all the proper tools (including grub) are installed:
```
sudo apt-get install mkisofs grub squashfs-tools squashfs-modules-$(uname -r)
```

Then make sure that ${CD}/boot/grub/menu.lst exists with:
```
ls ${CD}/boot/grub/menu.lst
```
If this returns "ls: cannot access ... " then ignore what I put below and start at step D.5. Otherwise continue with what I've wrote below.

Then, run this (I'm pretty sure you forgot this step) to copy your stage2_eltorito to ${CD}/boot/grub

```
sudo find /boot /usr/lib/grub/ -iname 'stage2_eltorito' -exec cp -v {} ${CD}/boot/grub \;
```

Then start again at step E.1

---

### Post by ranch hand on 2009-02-10
OK, So I am simple.  How in flinderation do you burn this to a CD/DVD?

---

### Post by miguelp on 2009-02-25
hello, this tut seems great, but i have a newbie question:

Lets say i create the live DVD correctly, if for some reason i messed up my installation of ubuntu, like delete the partiton (wasn't the first time) may i be able to reinstall the system from that costum live DVD, without loosing installed programs, kernel versions, drivers etc...?

will it work as a "system restore dvd" like does that came with windows?

I am a newbie with linux in general but i want to learn more, and hope soon completely abandon windows (as soon as adobe releases the Flash IDE to linux), i already use linux for development except for design (using Photoshop) and flash.

If i manage to create a DVD that lets me reinstall my custom linux system that would be just GREAT.

Thanks.

---

### Post by grndslm on 2009-02-26
> **ranch hand said:**
> OK, So I am simple.  How in flinderation do you burn this to a CD/DVD?If you run the remastersys script, you simply type one of these, depending on which mode of remastersys you chose:

sudo cdrecord /home/remastersys/remastersys/customdist.iso
-OR
sudo cdrecord /home/remastersys/remastersys/custombackup.iso

> **miguelp said:**
> Lets say i create the live DVD correctly, if for some reason i messed up my installation of ubuntu, like delete the partiton (wasn't the first time) may i be able to reinstall the system from that costum live DVD, without loosing installed programs, kernel versions, drivers etc...?Exactly.  Check out my sig for a SUPER easy guide to creating your own distro with remastersys.

> **miguelp said:**
> will it work as a "system restore dvd" like does that came with windows?Essentially... but this is way better because you can customize EVERYTHING that goes on the CD.

> **miguelp said:**
> I am a newbie with linux in general but i want to learn more, and hope soon completely abandon windows (as soon as adobe releases the Flash IDE to linux), i already use linux for development except for design (using Photoshop) and flash.I'm pretty sure you could add a virtual machine (like VMware Player, VMware Server, or VirtualBox) on top of your Ubuntu machine... then you can install XP in a virtual disk and whatever Flash apps you want inside that.  I'm pretty sure you can add Photoshop to wine, but it might be better to install to a virtual disk instead???

> **miguelp said:**
> If i manage to create a DVD that lets me reinstall my custom linux system that would be just GREAT.You betcha!  ;) ;) ;)

---

### Post by miguelp on 2009-02-26
Thanks a lot for the quick answer and for the tutorial.

liked, your sugestion about adding a virtual machine on top of ubuntu, better then install it in the hard drive and have to install grub again, i've tryed that once and did not end up so well... Maybe later i'll try again for now i'll stick with your sugestion, once again many thanks.

---

### Post by Marc666 on 2009-03-06
Hi everyBody, i need help.
This tuto is very cool and efficient but when i add some apps to the live Cd, at the boot time i receive a iO error "No Space left on Device".

Please help me.

Regards
Marc

---

### Post by kelscmi on 2009-03-12
I have a questions regarding the live CD/DVD after it is created.  I've been able to create the DVD, but one of the options during boot is install.  This option also appears once fully loaded (system > administration > install).  My question is what gets installed, the basic OS or everything on the live DVD?  Or put another way, can the install from a created DVD be used similarly as a cloned DVD using a different program (clonezilla or partimage)?

---

### Post by danielrs on 2009-03-15
I've followed this tutorial and I was able to finish it, but when I try to boot from the CD, it opens GDM and asks for the user and password, since I deleted all users, I can't login. Where have I made it wrong? Is it possible to login without re-creating the ISO?

Sorry if this have already been asked.

---

### Post by kelscmi on 2009-03-15
I created a live DVD using the backup option and burned it.  I then installed the OS into Virtualbox; during the install it asked for a user name, password, and computer name just as it would during an original install.  I used a different name and password but when I tried to log in the system said the user name and password were incorrect.  I actually had to use the user name and password that I used from the OS I had remastersys from.  
I hope that answers the question you were asking, I'm pretty new at this also so don't take it as expert.
If you created the image using the distribute option then I don't know, I have not tried that yet.  I can tell you the backup option includes your settings and data (evolution mail account and documents).

---

### Post by danielrs on 2009-03-15
I didn't use remastersys, I made this manually...

---

### Post by grndslm on 2009-03-16
> **danielrs said:**
> I've followed this tutorial and I was able to finish it, but when I try to boot from the CD, it opens GDM and asks for the user and password, since I deleted all users, I can't login. Where have I made it wrong?You prolly changed the GDM theme and didn't edit the /etc/gdm/gdm.conf and gdm.conf-custom files accordingly.  Check my sig if you did edit the theme.

---

### Post by dot2kode on 2009-03-17
Nice tutorial! I like using remastersys...very very simple and works very good...

---

### Post by grndslm on 2009-03-20
> **dot2kode said:**
> Nice tutorial! I like using remastersys...very very simple and works very good...
Thanks!

---

### Post by slickvguy on 2009-04-10
Have used remastersys w/o any problems. Have a few different/customized  livecd's too.

But I've been trying something a bit different and I can't get it to work properly. I wanted to make a custom "live" USB stick (w/o persistency).

I followed the guide on the first post of this thread as usual. Everything went smoothly ...but I can't get it to skip the login screen like the livecd's do. I always get the login screen - and I can't login because there are no users/passwords setup. The instructions in the guide causes the removal of all non-system users (< 1000) from /etc/passwd. I thought that the casper script creates a ubuntu user w/ a blank password w/ id 999? It does this when I use the ubuntu livecd. 

I've been comparing the Ubuntu livecd filesystem and initrd, as well as the files that remastersys generates - but I cannot see what I'm missing.

I tried changing the /etc/gdm.conf autologin keys to "true" and "ubuntu'. That didn't work either.

Help?

---

### Post by slickvguy on 2009-04-11
> **grndslm said:**
> You prolly changed the GDM theme and didn't edit the /etc/gdm/gdm.conf and gdm.conf-custom files accordingly.  Check my sig if you did edit the theme.

In my case, the gdm.conf has not been changed. I do not have a gdm.conf-custom file in my filesystem, but I do notice that in the script remastersys creates that file with a single "   " (a few spaces) line.

I've been comparing the remastersys generated files (which work as expected w/ autologin) versus my own (which prompts at the login screen for a non-existent user). The gdm.conf's are identical. 

What I don't understand (yet) is that when you mount the remastersys iso and look at /etc/gdm/gdm.conf, the AutomaticLoginEnable is false and AutomaticLogin is "". But AFTER you boot the livecd or iso, and check the gdm.conf, the entries have been changed to "true" and the username. So obviously a script/code in the startup process is changing those entries in that file. The timed login entries are changed as well.

Anyone? I know it's probably a very minor thing that is preventing mine from starting up properly, but I can't seem to find it! lol.

Update: OK. I grepped "gdm" in the decompressed initrd's. Found this...
```

# chroot needed to handle symlinks correctly
if chroot /root [ -f /etc/gdm/gdm-cdd.conf ]; then
    GDMCONF=/etc/gdm/gdm-cdd.conf
else
    GDMCONF=/etc/gdm/gdm.conf
fi

# chroot needed to handle symlinks correctly
if chroot /root [ -f ${GDMCONF} ]; then
    # Configure GDM autologin
    chroot /root sed -i \
        -e "s/^AutomaticLoginEnable=.*\$/AutomaticLoginEnable=true/" \
        -e "s/^AutomaticLogin=.*\$/AutomaticLogin=$USERNAME/" \
        -e "s/^TimedLoginEnable=.*\$/TimedLoginEnable=true/" \
        -e "s/^TimedLogin=.*\$/TimedLogin=$USERNAME/" \
        -e "s/^TimedLoginDelay=.*\$/TimedLoginDelay=10/" \
        ${GDMCONF}
fi


```

This must be where it's changing gdm.conf.

I'm sketchy on the chroot implications. 
The -f part is testing to see if the file exists. Which of course it does.
Not sure why the chroot /root is there??? Is it looking in /root/etc/gdm instead of /etc/gdm???
I guess that either it isn't finding the file OR it isn't able to write the changes to it.

---

### Post by slickvguy on 2009-04-11
Well, apparently I'm talking to myself here {crickets}, but I figured it out so perhaps this will help someone else avoid hours of frustration for such a minor problem.

For some reason - and I'm still not sure why - the permissions on 2 of the scripts in /casper/scripts/casper-bottom were 644 (i.e. no execute!) instead of 755. Of course, those two scripts would be: 10adduser and 15autologin! All of the scripts in my /usr/share/initramfs-tools/scripts/casper-bottom have theri permissions set properly. But for some reason - perhaps when I rsync'd everything over to the work directory? - the permissions on those 2 files changed (but not on the other scripts in that directory). Weird. I'd love to know what caused the permisions to change because I sure as heck didn't change them manually.

Anyways. Problem solved. Next... ;)

---

### Post by Skip Da Shu on 2009-04-11
> **slickvguy said:**
> Well, apparently I'm talking to myself here {crickets}, but I figured it out so perhaps this will help someone else avoid hours of frustration for such a minor problem. ... edited....
Anyways. Problem solved. Next... ;)Well I appreciate you posting the fix... this is on my soon-to-do list.

---

### Post by slickvguy on 2009-04-12
Found the culprit...

```

[ "$1" = "dist" ] && [ ! -d $WORKDIR/dummysys/home ] && mkdir $WORKDIR/dummysys/home
[ "$1" = "dist" ] && chmod 755 /usr/share/initramfs-tools/scripts/casper-bottom/*adduser /usr/share/initramfs-tools/scripts/casper-bottom/*autologin 
[ "$1" = "backup" ] && [ -d $WORKDIR/dummysys/home ] && rm -rf $WORKDIR/dummysys/home
[ "$1" = "backup" ] && chmod 644 /usr/share/initramfs-tools/scripts/casper-bottom/*adduser /usr/share/initramfs-tools/scripts/casper-bottom/*autologin

```

The first time I used remastersys to make a "backup" livecd, it CHANGED the permissions on those 2 scripts (10adduser and 15autologin) removing execution permission. Then when I went to make a liveusb a few days ago using capink's instructions, I copied over my entire filesystem (w/ a few excludes) to a temporary work directory. Thus when I chrooted to the work directory and created the new initrd, it used the non-executable versions w/o my realizing it. The sneaky part is that I used remastersys again after that to make a DISTRO (not backup) cdlive (for comparitive purposes) - so the script changed the permissions BACK to executable! lmao. Which is why when I took a look at them, they looked fine, and I had no idea that remastersys had actually change their permissions from executable, to non-executable, and back again to executable. Got it? ;)

As much as I appreciate the remastersys script, I wish coders would not write scripts that modify an installation's files w/o at the very least informing people of the changes. It's bad practice. This isn't the only place in the script that it does this either (changing installation files). There's no reason for that script to change ANY file on your system. It uses temporary work directories and files for many changes - why not do that for ALL changes (unless it cannot be done for some reason)? In this particular case, you can copy the casper files to a separate/temporary directory and use *those* files to create a custom initrd with mkinitramfs.

---

### Post by Proteusiq on 2009-04-19
Hej there!
  I followed everything in your tutorial,I did not follow from Scratch one but the normal.
   It looks like it working well but I do not know since I am stuck with a Login name and Password ....
    I tried the one I use in my PC but it wont work...

Any idea what is the name and password?? Please let me know! Thank you

---

### Post by capink on 2009-04-20
It should not ask you for a username or password. Are you sure you followed it to the letter, especially steps C.5, C.8 and C.10

---

### Post by maybeway36 on 2009-04-22
This erro is appearing in casper.log on my new Jaunty custom CD:
```
Begin: Running /scripts/casper-premount ...
Done.
Done.
/init: line 1: cannot open /dev/sda: no such file
mount: Mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```
This seems to happen when I build an Intrepid CD too? Anyone know why?

---

### Post by chris4585 on 2009-04-23
This tutorial was great, but needs to be updated IMO, a script I made use to work 100% flawless using these guidelines, now it hardly functions the same as it did.

---

### Post by maybeway36 on 2009-04-23
Update: I built my Jaunty CD on Intrepid, and it worked fine. Go figure. :)

---

### Post by uflieven on 2009-04-26
For those who don't know the login and the password, try the following:
username: ubuntu
password: (nothing) -> just press enter

Hope this helps...

I have a problem with jaunty. When booting from my live-cd, it got stuck almost halfway through the progress-bar. When I switch to a console, it seems to got stuck at configuring network interfaces.

After pressing Ctrl+Alt+Del, it continues and after it has booted up, I can use the internet without any problem. But the fact that it hangs halfway through the progress-bar and that i have to mess around to get my custom cd booted, annoys me. 

I'am using wicd as network manager instead of gnome-network-manager. Any ideas?

**Update:** Seems there's absolutely no problem with the instructions on this site, nor with my hardware. It has all to do with a missing package (but sadly enough i can't figure out which one...)

---

### Post by shafin on 2009-05-08
Thanks a lot for the guide, worked wonderfully on my Jaunty installation

---

### Post by ciborro on 2009-06-22
Hi,

Big thanks for this great tutorial.
Almost works perfect but...;)

I have one little problem, I would like to change one file ( something like this , I don't remember clearly because I write from work /etc/event/tty1 ) whatever ;) I would like to change line with getty to run /directory/myscript.sh on first console. But something changed this file after mksquashfs command. How to change this file permanently.

Regards.
Przemek.

---

### Post by Pax-Man on 2009-06-23
Great post! It helped me with my new notebook :)

---

### Post by Trapper on 2009-07-11
For me this was an excellent HowTo. I just followed the instructions and ended up with a LiveCD from my current Jaunty X86_64 install. Did another install from the livecd and it works just fine. Thanks for your work.

---

### Post by Trapper on 2009-07-12
What files would I have to edit to change the default desktop a bit? For example, on my jaunty livecd install I want a launcher for nautilus directly on the desktop and a couple of other launchers on the upper panel available to a new user at first login.

There are also a couple of options in nautilus that I would like to have enabled in the default nautilus configuration.

---

### Post by chris4585 on 2009-07-13
In the /etc/skell folder, everything you want the live user to be in the home folder put in /etc/skell.  For example if you want a launcher on your desktop put it /etc/skell/Desktop/ (of course after creating the Desktop folder).

Hope that helps

---

### Post by Trapper on 2009-07-13
Well, I will answer my own question for me. This is how I created a new default desktop, panels, etc. in gnome for new users:

I created an ordinary test user and set up the desktop background, panels, theme, nautilus, volume, etc. to my liking. Then I did this while logged in as the test user: (the long way for clarity)

[COLOR="Red"]WARNING!!! This is what I did and had success. It doesn't mean that you will. Do it at your own risk.[/COLOR]

In a terminal:
```
gconftool-2 --dump /apps/panel > /home/trapper/temp/new-panel-settings.xml
gconftool-2 --dump /apps/nautilus > /home/trapper/temp/new-nautilus-settings.xml
gconftool-2 --dump /apps/gnome > /home/trapper/temp/new-gnome-settings.xml
gconftool-2 --dump /apps/gnome-screensaver > /home/trapper/temp/new-gnome-screensaver-settings.xml
gconftool-2 --dump /apps/gnome-volume-control > /home/trapper/temp/new-gnome-volume-control-settings.xml
gconftool-2 --dump /desktop > /home/trapper/temp/new-desktop-settings.xml

sudo chown root:root /home/trapper/temp/new-panel.xml
sudo chown root:root /home/trapper/temp/new-nautilus-settings.xml
sudo chown root:root /home/trapper/temp/new-gnome-settings.xml
sudo chown root:root /home/trapper/temp/new-gnome-screensaver-settings.xml
sudo chown root:root /home/trapper/temp/new-gnome-volume-control-settings.xml
sudo chown root:root /home/trapper/temp/new-desktop-settings.xml


sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/trapper/temp/new-panel.xml
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/trapper/temp/new-nautilus-settings.xml
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/trapper/temp/new-gnome-settings.xml
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/trapper/temp/new-gnome-screensaver-settings.xml
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/trapper/temp/new-gnome-volume-control-settings.xml
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/trapper/temp/new-desktop-settings.xml
```

After I did all this I proceeded with the "How to make a live CD/DVD from your harddisk installation" howto. When I do an install from my new custom LiveCD and login for the first time all the preferences I had as the test user and saved via the gconftool-2 are now the default settings.

---

### Post by Trapper on 2009-07-13
> **chris4585 said:**
> In the /etc/skell folder, everything you want the live user to be in the home folder put in /etc/skell.  For example if you want a launcher on your desktop put it /etc/skell/Desktop/ (of course after creating the Desktop folder).

Hope that helps

Thanks. It seems we were both posting solutions about the same time. :-)

---

### Post by chris4585 on 2009-07-13
copying all of your config files is what i do, but if you want to actually install from the livecd and have every user have all the same config files you should put those files in /etc/skell.  Everytime a new user is created, /etc/skell is copied to the new user's home folder.

---

### Post by Trapper on 2009-07-14
> **chris4585 said:**
> copying all of your config files is what i do, but if you want to actually install from the livecd and have every user have all the same config files you should put those files in /etc/skell.  Everytime a new user is created, /etc/skell is copied to the new user's home folder.

Okay. I will give this method a try seeing that it seems a much easier process and has been mentioned a couple of times here. When you say to put all the config files into /etc/skel exactly what config files are you referring to? What I am wanting each new user to have is specifically customized panels, desktop background, application menu, and theme.

---

### Post by chris4585 on 2009-07-14
everything you had in your livecd user's directory counting the hidden files.

---

### Post by Trapper on 2009-07-14
> **chris4585 said:**
> everything you had in your livecd user's directory counting the hidden files.

Okay. I will try this and see how it compares to the way I did it. Thanks chris4585.

---

### Post by chris4585 on 2009-07-14
No problem dude.

---

### Post by Trapper on 2009-07-17
> **RumorsOfWar said:**
> I just tried to use my install disk on another machine ( it has the same processor and similar vid card), and it hung at 94% while configuring hardware. 
I'm wondering if my install disk is missing some hardware components because I started out with the Alt-install in the first place.
Any ideas?

Well, I am experiencing the same problem when I install my custom u904-64 livecd. It gets to 94% (hardware) and hangs for almost 10 minutes and then completes the install. I didn't see any problems for a while. Then I tried to print something. No cups. It was there, it's shows it's running, but nothing can connect. I totally removed everything related to cup and all my hp drivers, etc. and reinstalled. Still no cups access. The printer does get recognized by the hp install utility but it refuses to install it because of the cups problem.

Uniquely, this is on the same box I created my livecd  on and the printer works well there. Also when I boot up in the livecd the printer is also there. It just is not there and I can't get it there when I do an install to the hard drive. I worked for hours trying to get things straightened out but to no avail.

Utimately I resorted to recreating my custom livecd again, burned it to disk and tried again. Same results. I tried the complete process six more times. Same result except that one time it installed without hanging at 94% and I had printer support. Did another install on another partition using the same livecd and it hung at 94% and no printer again.

I've never had difficulty like this on this machine. I have 8.04 32 bit, 9.04 32 and 64 bit, karmic 32 and 64 bit  on the box and have not experienced this problem.

Oh well, I have a very nice custom cd setup but this problem negates all my work.

I find it real odd that I have the printer as the livecd user but not when I install to the hard drive. That's definetly not a hardware problem. All my other installs on this box back that up too.

---

### Post by Trapper on 2009-07-18
> **Trapper said:**
> Well, I am experiencing the same problem when I install my custom u904-64 livecd. It gets to 94% (hardware) and hangs for almost 10 minutes and then completes the install. I didn't see any problems for a while. Then I tried to print something.

I've yet to resolve this problem using this HowTo but I did easily resolve the problem using remastersys. The LiveCD I burned from the iso it created did a normal, successful install on the very first attempt. There was no minor hangup at 86% (languages) and no extended hangup at 94% (hardware). At 94% it did take a bit of time but there was obvious hard drive activity all during it rather than nothing happening. Most importantly, when I installed from the custom LiveCD, everything is as I desired and everything works, including cups and my printer.

I did the HowTo routine no less than 10 times. I've been working with computers since back in the day when the computer consisted of two 5 1/4' soft floppies. I'm no pro but I've installed complicated production postfix based mail server systems from scratch. I've gone through numerous other HowTo routines much more complicated than this one was. I am left with the assumption that there is something that's not addressed or addressed incorrectly in this HowTo. Obviously, something happens in remastersys that does not take place in this. I consider human error on my part but after so many attempts and taking extra effort to ensure I was taking all steps exactly according to instruction I am left with the feeling there's an instruction error somewhere. I do know one thing for certain. For clarity, non-bootstrap and bootstrap methods need to be in two distinctly different HowTo's rather than combined.

capink, I am not trying to bash. I am just trying to express my experience over the past few days and what my personal conclusions are. I've noted through the many pages of posts in this thread that many people seem to have had complete success. I have also noted though that others have been confronted with the same problem I have. There seems to be some circumstance that your routine does not address. Unfortunately, I have not been able to figure out what that circumstance is. Obviously, it is not a circumstance that everyone has. It does seem to be something that is handled in remastersys though.

Trapper

---

### Post by capink on 2009-07-18
> **Trapper said:**
> 

capink, I am not trying to bash. I am just trying to express my experience over the past few days and what my personal conclusions are. I've noted through the many pages of posts in this thread that many people seem to have had complete success. I have also noted though that others have been confronted with the same problem I have. There seems to be some circumstance that your routine does not address. Unfortunately, I have not been able to figure out what that circumstance is. Obviously, it is not a circumstance that everyone has. It does seem to be something that is handled in remastersys though.

Trapper

Don't worry, I know you are not bashing. This guide is not prefect. Some people have reported problems that I was not able to reproduce, and consequently not able to solve. Unfortunately I have been busy lately with not much time to improve the guide.

---

### Post by Trapper on 2009-07-18
> **capink said:**
>  Unfortunately I have been busy lately with not much time to improve the guide.

capink - I sure know what you are talking about concerning time. I've been there and have done that. A full plate.

I am going to keep plugging away at this and see what I can discover. I'll surely let you know if I find anything pertinent. 

There is one thing that keeps running across my mind when I run through the routine. It involves the mounting and unmounting of /rootfs/proc, sys, and dev. I note there's only code for mounting dev and proc. Then it jumps right into chroot. There's no sys mount. Here's the code in that section:

```
sudo mount -o bind /dev/ ${WORK}/rootfs/dev
sudo mount -t proc proc ${WORK}/rootfs/proc

sudo chroot ${WORK}/rootfs /bin/bash
```When unmounting the code is:

```

sudo umount ${WORK}/rootfs/proc
sudo umount ${WORK}/rootfs/sys
sudo umount ${WORK}/rootfs/dev

```When doing umount for /rootfs/sys I always encounter a not mounted message.

I really don't know if this is meaningful but it makes me wonder why there's a umount line for /rootfs/sys but no sort of mount line. I'd try to mount sys but I have no idea what the correct syntex would be.

That's about the only glaring discripency I have seen so far and I don't even know if it is actually a discripency. I just thought it was worth mentioning.

Trapper

---

### Post by capink on 2009-07-19
> **Trapper said:**
> 

That's about the only glaring discripency I have seen so far and I don't even know if it is actually a discripency. I just thought it was worth mentioning.

Trapper

You are right. I added the missing command to guide. Thank you.

---

### Post by Trapper on 2009-07-22
> **capink said:**
> You are right. I added the missing command to guide. Thank you.

I did a fresh install of U904-32. Cups was accessible and printer was available. I ran your routine with the correction. I burned the resulting iso to disk, booted it up and installed to a new partition from the gui. Everything was exactly as it should be in the new install except that cups was not accessible and consequently there was no printer support.

I then installed remastersys and created an iso using it, burned it to disk and installed to a new partition. It was exactly as it should be, cups was accessible and my printer was there.

I do note that I can burn the iso created with remastersys to a usb flash drive using the USB Startup Disk Creator in System/Administration. It refuses to burn the iso created with your routine though. The message is: "This is not a desktop install CD and thus cannot be used by this application."

Trapper

---

### Post by uflieven on 2009-08-13
I noticed, when working with Remastersys, there are created three folders in the root of the live-cd: casper, isolinux and preseed. In this guide, there's only a casper and a boot folder.

As I'm trying to put the live-cd splashes (splash.pcx and splash.png) on the cd, I guess it would be possible with remastersys, (because the isolinux folder which should contain the splashes exists on the resulting iso, so I guess adding the splashes there after running remastersys distcdfs could do the trick) but not with this guide. (as there's no isolinux folder created)

 Am I right, and if so, why doesn't this guide create an isolinux folder while remastersys does? Is there a logical explanation for this?

Thanks for your answer(s).

---

### Post by dimple148 on 2009-08-29
Hi,

Are these steps applicable to Ubuntu 9.04 installation?

Dimple.

---

### Post by &#913;&#957;&#964;&#974;&#957;&#951;&#962; on 2009-09-20
> **dimple148 said:**
> Hi,

Are these steps applicable to Ubuntu 9.04 installation?

Dimple.

Yes.

My question:

[B]sudo mkisofs -b /boot/grub/stage2_eltorito \
-no-emul-boot -boot-load-size 4 -boot-info-table \
-V "Custom Live CD" -cache-inodes -r -J -l \
-o ~/live-cd.iso $CD[/B]

I get this -> 

mkisofs -b /boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -V "Custom Live CD" -cache-inodes -r -J -l -o ~/live-cd.iso $CD
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to [email]debburn-devel@lists.alioth.debian.org[/email].

Tbh, there is an iso file but when I run it with qemu, it cannot boot.
What does this command do? (mkisofs -b /boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -V "Custom Live CD" -cache-inodes -r -J -l -o ~/live-cd.iso $CD)

---

### Post by Milleman on 2009-09-29
I've just found out that it is possible to make Casper to not autologin. In the file "/etc/casper.conf", just delete the login names:

```
export USERNAME=""
export USERFULLNAME=""
```

Then in chroot mode, create the user you like. Set the password and also create the home directory. After boot, it will ask for username and password. 

Done!

Best regards,
/Mill

---

### Post by Milleman on 2009-10-01
If I chose the "Persistent" option from the grub boot menu, the booting will be delayed and the following errors will be displayed about 6 times before the booting continues:

"**I/O error, dev fd0, sector 0**"


Is there a way to get rid of this?

Best regards,
Milleman


Solved!
The FD was absent but selected in BIOS. Just deselected the FD in BIOS and then the problem was gone!

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for a nice tutorial.

---

### Post by bsanyi on 2009-10-25
Hi,
does anyone have pactice on building live system with X from Karmic?  These steps are grat on Jaunty, but building a Karmic system fails for me.  The problem is somewhere around xorg, hal and udev.  These pachages does not like to be installed in a chroot-ed environment... Can you help me how to install them, please?

---

### Post by szerencsefia on 2009-10-31
To: **capink**

This is a very useful write-up, thank you for sharing your knowledge with us.

In may case it would be interesting to know what are the steps need to be
changed to make a livecd booting up on the way as written here:
**[COLOR="Navy"][http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2)[/COLOR]**
but having the configuration from my running system.

Do you think you can provide me with that information? :D

from: **Szerencsefia**

---

### Post by dashpilot79 on 2009-12-03
This is nearly exacetly what i wanted to do, but i was wondering is there a way to keep the users that i created also on the cd, as i wanted to us the cd as the normal boot for a server (i.e. if the system is compromised a hacker can only change items in the /swap /tmp /var directories?)

Thank You

---

### Post by zloty on 2009-12-20
Exelcent work!!!! Thanks for Your Tutu Capink :)
I'm Debian Lenny user (powerpc) & i need some help here:(
There is no any more unionfs-modules-[COLOR="Purple"]version[/COLOR] in Lenny repository.
> **capink said:**
> 

[LIST]Replace the command in Step C.2 with:

```
apt-get install [COLOR="Purple"]live-initramfs unionfs-modules-$(uname -r)[/COLOR] discover1 xresprobe
```[/LIST]

  
So i didn't install unionfs-modules but rest go fine.
I burn .iso image, then boot cd using yaboot. And i get this
```
Can not mount /dev/loop0 (/cdrom/live/filesystem.squashfs) on //filesystem.squashfs
mounting /dev/loop0 on //filesystem.squasfs failed: No such device

/bin/sh: cant access tty; job turned off
(initramfs)
```

I think the problem is from: skip install *unionfs-modules-$(uname -r)*
Do You have some clue for this ?
Sry for my bad english and thx for reply

**EDIT:**
Here is the clue:D for Lenny
```
[COLOR="Purple"]aufs-modules-$(uname -r)[/COLOR] insted of [COLOR="Purple"]unionfs-modules-$(uname -r)[/COLOR]
```

---

### Post by zloty on 2009-12-20
Here is me again, i've another problem.

I put livecd to cdrom & boot.
While booting livecd there is a part "configure X" and part "configure video" after that X server starts.
And then my system catch freeze ;/
I'm using framebuffer driver:fbdev
Is there any chance to skip this part "configure X" and "configure video" and use my xorg.conf insted of this??
I copied my xorg.conf to filesystem.squashfs but probably part "configure X" and "configure video" overwrite my xorg.conf
How to don't use those 2 scripts?
Cheers

---

### Post by mienai on 2009-12-28
A relatively newbie to Ubuntu/Linux here (Dual-booting Windows 7 and Karmic). I thought I understood, but I don't.

> **capink said:**
> ```
export WORK=[COLOR=Magenta]~/work[/COLOR]
export CD=[COLOR=Magenta]~/cd[/COLOR]
export FORMAT=squashfs
export FS_DIR=casper
```The WORK Directory is where our temporary files and mount point will reside.
The CD is the location of the CD tree.
FORMAT is the filesystem type. We you are going to use a compressed squashfs
FS_DIR is the location of the actual filesystem image within the cd tree.

[B]1) So we have to make a CD tree and Work directory, first? Before the below step? I have no idea how to make a CD tree...

2) I am confused/don't know how to [find and] enter directory locations in Ubuntu.[/B]

> 2. Create the CD and the WORK directory structure:

```
sudo mkdir -p ${CD}/{${FS_DIR},boot/grub} ${WORK}/rootfs
```**3) Wouldn't the location variable screw up the mkdir command? Or does the "export" prefix tell Ubuntu that {CD} and {WORK} are to be used from my specified locations?**

---

### Post by pIII on 2010-01-04
hi all, ive followed this guide few times and it had help me produced few functional liveDVD images under jaunty...but now im stuck with a login screen that keeps me out from login in. Im unsure whats wrong since on the local/base system i have gdm to autologin and while at chroot  i do delete all gdm related confs as suggested and apply the factory default file copy to the rootfs structure.. though i think that file is not even present under jaunty. (?)

at kernel boot i see the liveDVD trying to delete some default user and failing, it gets me til a login screen for which i have no valid password.

any help, tip or advice is greatly appreciated since i think im near to finish this customized image.

and thanks for the thread.
/pIII

---

### Post by DonaldJ on 2010-03-28
That's a hell of a lot of work for a novice, who just wants to click a mouse on "make live-cd", and the system makes the CD..  All he does is put a CD in the slot, and click mouse..  Returns in a couple hours, and the CD has popped out, ready as a bootable installation live-CD of his special personal designed OS CD, ready to drop-in at a seconds notice, when the OS so much as "happens to even twitch, flash, or hiccup wrong"...  as in "instant change the OS, at the drop of a CD, and the click of a mouse...  Maybe the original OS is saved in a partition..?  Maybe the OS can be totally formated and replaced at the click of a mouse..?
And on the "next rung".. if it were forever rewriting itself, it would grow software on-demand... "Cloud OS".. the one I talked about 30-years ago.. in which the OS floats upon itself in layers, in a stream of bio-data, in a loop, like a snake eating its own tail.. grown from this new plastic made of neon conditioned, plazma conditioned, petroleum based chemistry, in beehive matrix... A perpetually refreshed OS...  
Ubuntu is definitely the number one candidate for modification into a floating-OS.. Ubuntu has an honest sound base, which wouldn't crack under stress.. only get stronger processing-challenge.. thus "software grown on demand, guiding the soup"...

I was just a sitting here writing on my computer, when "a war landed on my back"...  then left when I showed it its reflection...  My peace!..


Translate that into "floating OS", and you have "floating OS"...


It all starts with "Live-CD at the click of a mouse"...   
From there "it's creek.. to river.. to Victoria falls"...

---

### Post by carlos.hernandez on 2010-06-24
Hi there, I´ve been using your guide to create a live CD from the scratch.
 
Now I´d like to know whether I would be able to create a live CD using WUBI (the program that runs Ubuntu as any other windows program).
 
The issue is that the network where I have ubuntu installed won´t let me download the packages I need to create the live cd...    it sucks...
I ave another machine with access to a network and no restrictions, but that machine only has windows and they won´t let me install linux...
 
quite a problem, haha    :confused:

---

### Post by capink on 2010-06-25
I have not really examined wuby at all because I don't use windows anymore. I plan on updating this guide in the future, but unfortunately I am quite busy right now.

Maybe I will be looking at wubi in the next update of this guide.

---

### Post by carlos.hernandez on 2010-06-25
What about a virtual machine?

Is the live cd doable from a virtual machine?

---

### Post by capink on 2010-06-25
Yes it is doable. You can either use the virtual machine to do the whole thing or just to download the packages and then transfer them to your ubuntu machine.

---

### Post by physeetcosmo on 2010-07-30
Wow, this is awesome.

It works with Ubuntu 10.04, i just finished building a LiveCD this morning!

---

### Post by TNAFan on 2010-07-31
Will this allow me to create a new customized distro based on Ubuntu?  (Like Mint or any of the *buntu's)

---

### Post by bcatt on 2010-08-18
I had this idea that I could build my ideal system in a virtual machine and export it into a work folder on my physical machine (so that my custom system won't include packages I won't use on that system - ie: the extra ones used to prepare the installation, temporary directories for making the cd structure, etc). Is that possible? If so, how?

Also, I want my custom installation to preserve the users and desktop configuration, as well as other changes, such as firefox add-ons...do I need to change anything in the instructions in order to achieve this?

Many thanks for any help.

---

### Post by huggies15 on 2010-08-19
Hi,
I want to make a live cd of my work laptop that contains some (free) wine programs. Will this method have them installed on the dvd as well, if not is there a way i can adapt the guide to make them work?
Unfortunately there are no alternatives to the programs, otherwise i would be all windows free by now :(
Steve

---

### Post by waqarafridi on 2010-08-28
I am using New ubuntu 10.04 and I went through all the Steps and they Worked perfectly, but Now I am stuck in the Step

$ sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}

it gives the following error

$ sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
Parallel mksquashfs: Using 4 processors
Creating 4.0 filesystem on /home/waqar/cd/casper/filesystem.squashfs, block size 131072.
Segmentation fault

The  rootfs size is 2.3 GB but I think that wont be a problem. I dont know what to do next, any kind of help would be Appreciated

---

### Post by GeoMX on 2010-09-10
Would it be possible to use GRUB2?

When installing grub-pc in the chroot environment, it asks for a device where to install GRUB to, I skip this step but would like to know if it's correct.

---

### Post by GeoMX on 2010-09-10
I'm actually testing my ISO in VirtualBox, I have some details but it works! Thanks a lot for your guide.

I have problems when selecting to boot in graphical mode, the system does not pass the usplash screen. Anyway, if booting to text mode, I can run "startx" and get into my window manager :).

Now I have to test using real media :).

> **GeoMX said:**
> 
When installing grub-pc in the chroot environment, it asks for a device where to install GRUB to, I skip this step but would like to know if it's correct.
I've found there is no problem with this.


> **GeoMX said:**
> Would it be possible to use GRUB2?
Now I see it can be done, but don't know what would be the "correct" method for adding custom entries to the GRUB menu.

---

### Post by GeoMX on 2010-09-13
I have one more question. I can not directly modify the default LiveCD user because it is created at boot time, how can I indicate a script to be executed when the LiveCD session starts?

---

### Post by GeoMX on 2010-09-18
Any idea?

---

### Post by TeamXlink on 2010-09-19
I'm confused with the optional part in Step B.

I'm trying to create a live cd of my server because I need that hard drive for something else.

My server files are all in my users home directory there is also a script in my home directory called from my rc.local file.

I don't understand what you mean by home settings.

Do I just leave out the exclude home part in the command before that?

Also, I'm doing this on a Ubuntu 8.04 Cli install.

Thank you.

EDIT:

I think I might have gotten it to work.

I did this:

```

QUAKE3='Quake3 .bashrc'

```

Then this:

```

cd ~ && for i in $QUAKE3
do
sudo cp -rpv --parents $i ${WORK}/rootfs/etc/skel
done

```

I'm unsure if this was correct or not.

Thank you.

EDIT 2:

You said this:

> (Optional Step)Install any packages you want to be in the CD. 

Does this mean by existing packages won't be on my cd?

Thank you.

---

### Post by GeoMX on 2010-09-20
> **GeoMX said:**
> I have one more question. I can not directly modify the default LiveCD user because it is created at boot time, how can I indicate a script to be executed when the LiveCD session starts?
Nevermind, I solved it, thanks again for this HowTo :).

---

### Post by rubal on 2010-09-21
i had js followed the complete steps for ubuntu10.04 and they got completed successfully..bt when i tried it in virtual box it had given me 

[I][B](initramfs) mount: mounting aufs on /root failed: No such device
aufs mount failed[/B][/I]

what should i do now..i dont hav any idea..m a newie:(

plzzz help..:(

---

### Post by grasmaaier on 2010-11-22
Dear all,

This tutorial has helped me a lot. I just create a working LiveCD with rdesktop.

But the network configuration "/etc/network/interfaces" on the livecd is removed.
How can I keep the network settings without loosing it?

Because the livecd does support wireless network and the livecd must take a specific wireless network created by myself.

Yours,
Jarl

---

### Post by mirix on 2010-11-28
Hello,

I am using Debian Squeeze and I would like to keep the existing user with all the configurations files and data. 

This could be useful for making an installable backup. However, in this case I would like to preserve a customized Wine installation and configuration and all the Windows programs installed. It is important that the user name remains the same.

Could you please, give me some hints on how to do this?

I have already done it with Remastersys, however, the Debian version of the Remastersys installer is rather buggy and rudimentary at this time. 

Best regards,

Mirix

---

### Post by rutharanga on 2010-12-03
Thanks a lot dude..
I have tried this and successfully created my own bootable ubuntu live CD.
This is one of the best tutorials i have refered coz presentation of the idea is so clear and not ambiguous.

thnx..  :):)

Rgrdz,
Ruwan Wickramarachchi.

---

### Post by rutharanga on 2010-12-03
I have created ubuntu liveCD using this tutorial and it was successful.
I also have installed ubuntu installer packages when I create my Live CD. 
Can u please give me the menu.lst entry to access ubuntu installer (Title like: "Install ubuntu on your computer")

---

### Post by soundworks on 2011-01-03
Hi,
my aim is to create a live Desktop cd with following features:
 no autologin, 
 users can only login with password.


What I have to do to remove autologin?
I read this whole thread, and just figured out that I have to use init-ramfs instead of casper as capink postet here: [http://ubuntuforums.org/showthread.php?t=688872&highlight=live+cd&page=17](http://ubuntuforums.org/showthread.php?t=688872&highlight=live+cd&page=17)

It would be very nice if anyone can just say me how to do this. 
Thanks in advance.

---

### Post by farmerjohn73 on 2011-02-17
It woked for me in the 3rd attempt.  I hope it works as capink said.

Thanks capink :)

---

### Post by jadeye on 2011-04-09
Hey capink and everyon,

I have tried this and had problems withit,

I wish to succeed so I am asking you to look at my post:

[http://ubuntuforums.org/showthread.php?p=10657607#post10657607](http://ubuntuforums.org/showthread.php?p=10657607#post10657607)

And tell me if I can do this at all???? maybe I am trying in vain.

Thanx.;)

---

### Post by prohp on 2011-04-11
Thanks for this tutorial! help me a lot!

just want to share with you how to create live-usb instead of cd/dvd

1. insert your dok, and create a new partition
fdisk /dev/sd<b>
[INDENT]1. hit **n** for new partition
2. hit **p** for primary partition
3. select partition number (1)
4. leave first & last cylinder as default (just hit enter)
5. hit **a** to set bootable flag and choose your partition numer (section 3)
6. hit **w** to write parition table.
[/INDENT]2. format partition to ext3 filesystem.
mkfs.ext3 -L LiveUSB /dev/sd<b><1>

3. mount your .iso (that you previously created) and your ext3 partition.
mkdir iso
mkdir liveusb
mount -o loop /path/to/your.iso iso
mount /dev/sd<b><1> liveusb

4. copy iso content to your dok
cp -r iso/* liveusb/

5. copy some grub files to your dok
cp -r /usr/lib/grub/i386-pc/{e2fs_stage1_5,stage1,stage2} liveusb/boot/grub

6. create grub boot loader
grub
[INDENT]-> device (hd2) /dev/sd<b>
-> root (hd2,0)
-> setup (hd2)
-> quit
[/INDENT]7. umount your iso file and your dok
umount liveusb
umount iso
rm -rf iso liveusb

That's it!
just set your bios to boot from usb and you're done :)

---

### Post by GeoMX on 2011-04-11
prohp: thanks for sharing, unfortunately I'm not able to try it on a Lucid installation since I can't find the files you mentioned. Should I try a previous version?

-------------------------------
edit:

I tried on a Karmic install and followed your instructions using two USB sticks, one is working fine, I have to check what the problem may be with the other, but anyway, thanks a lot for the information :).

---

### Post by prohp on 2011-04-12
I forgot to mention that I test this only with Ubuntu 10.10 (Maverick).
Anyway, try to find those file with:
```
find / -name 'e2fs_stage1_5'
```

---

### Post by joshj70 on 2011-04-17
Hi, I am trying to make a live cd out of my Maverick and everything works fine until I get to install casper xresprobe

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  localechooser-data user-setup
The following NEW packages will be installed:
  casper localechooser-data user-setup xresprobe
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 277kB of archives.
After this operation, 1061kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main localechooser-data all 2.12ubuntu3 [26.4kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/universe xresprobe i386 0.4.24ubuntu9 [19.6kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/main user-setup all 1.28ubuntu10 [152kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main casper i386 1.248.1 [79.0kB]
Fetched 277kB in 3s (69.7kB/s)  
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package localechooser-data.
(Reading database ... 123350 files and directories currently installed.)
Unpacking localechooser-data (from .../localechooser-data_2.12ubuntu3_all.deb) ...


```it just hangs here, its been going for over an hour with no progress, please help.

---

### Post by lazerz on 2011-04-21
Well em kinda stuck on step B where commands says something like 


[COLOR=#000000][FONT=Arial]sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/*\
 --exclude=/sys/* --exclude=/tmp/* --exclude=/home/*\
 --exclude=/lost+found / ${WORK}/rootfs


Im on this command for like more than 2 hours now? My vm running ubuntu is just 3 gb hard-disk space of 9.0 gb allocated? Is this behavior fine when will the new file-system be prepared...
[/FONT][/COLOR]

---

### Post by connect2jan on 2011-04-23
[hi capink]("http://ubuntuforums.org/member.php?u=200206")
exellent tutorial
i have small doubt at step A
**Replace only the values highlighted in [COLOR=Magenta]Magenta[/COLOR]**.
WHAT VALUES?
i have to use only dir names (not numaricals)right?

---

### Post by Mooty on 2011-05-01
@joshj70

Going by your log, it looks like /dev/pts wasn't mounted.

Did you try [https://help.ubuntu.com/community/LiveCDCustomization#Prepare%20and%20chroot](https://help.ubuntu.com/community/LiveCDCustomization#Prepare%20and%20chroot)

When I tried making a livecd, I never saw this thread, and used what's at that link, and worked fine.

---

### Post by connect2jan on 2011-05-03
[hi ]("http://ubuntuforums.org/member.php?u=200206")[capink]("http://ubuntuforums.org/member.php?u=200206")
 i done that steps A,B,C,D -without [SIZE=1][U][I]debootstrap
[/I][/U][I][B]so in home directory
cd dir(<inthat  boot dir,casper dir,md5sum.txt  )were there

 2)then i make that (in /home) cd 'dir to img file(.iso file),so using this .iso file i made usb drive to booable
so when i boot from usb
on screen below message

  [COLOR=Red]NO  DEFAULT or UI configaration directory found?
boot:
[/COLOR][/B][/I][I]when i try in google regarding this you have to rename isolinux to syslinux
but in that cd dir there is no isolinux dir?

whats wrong
plz any help
am i miss something[/I][U][I]
thanks
[/I][/U][/SIZE]

---

### Post by Omar.Fayyad on 2011-06-11
**Backtrack4 R2 installation** 			
 			 			 		   		 		 		I finally  installed backtrack4 r2 on my virtual hard disk(Virtual Box) and i found  unexpectedly that i dont have any permission to write to any file or  even to create one and i dont know why ...... could you help out!!!


Appreciate the support.

---

### Post by capink on 2011-06-15
First, I apologize for not answering people questions. I've been busy lately and did not have much time.

I updated the guide to support grub2 instead of grub-legacy. I also added instructions for how to boot the ISO from a flash disk instead of a CD/DVD.

This will probably be the last update to the guide. Again I'm sorry for the lack of support.

---

### Post by Darin722 on 2011-06-27
Great tutorial!  
I'm having an issue with login on the live cd though.  It asks for a login.  My specific details...
I'm trying to create a live cd of ubuntu 10.10 from an installation in virtual box.  

can anyone suggest how I can fix/troubleshoot this?

I've followed the tutorial as presented on the first page successfully, except that I had to add grep -v rootfs /proc/mounts > /etc/mtab just before installing casper to fix an error. df: warning:cannot read table of mounted filesystems:no such file or directory

edit:
I've noticed that even though I removed users with uid's greater than 999 from /etc/passwd (and copied /etc/passwd over /etc/passwd-) when I run the command sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} it reports the deleted users, rather it reports users from the /etc/passwd file of the host, not the one from which the users were deleted.  

Number of ids (unique uids + gids) 32
Number of uids 12
	root (0)
	daemon (1)
	couchdb (105)
	gdm (113)
	ubuntu (1000)
	speech-dispatcher (107)
	libuuid (100)
	syslog (101)
	unknown (997)
	test (1001)
	man (6)
	avahi-autoipd (103)

Here 'ubuntu' is the host system user I'm working as. I created the user "test" on the host system after removing all users from the /etc/passwd file for the live cd, just before creating the squashfs.  So why is mksquashfs reporting findings from the hosts /etc/passwd file, and is this why the live cd is prompting me for a login?

---

### Post by capink on 2011-06-27
Be sure you have done step C.5. Also be sure you successfully umounted ${WORK}/rootfs/{dev,proc,sys}.

Please give me the output of the following commands:

```
sudo cat ${WORK}/rootfs/etc/passwd
sudo ls sudo cat ${WORK}/rootfs/dev
sudo ls ${WORK}/rootfs/proc
sudo ls ${WORK}/rootfs/sys
```

Also it won't hurt to delete those files before making the squashfs image

```
sudo rm ${WORK}/rootfs/etc/mtab
sudo rm ${WORK}/rootfs/etc/passwd-
```

> **Darin722 said:**
> it reports users from the /etc/passwd file of the host, not the one from which the users were deleted.  


That is normal.

---

### Post by Darin722 on 2011-06-27
Thanks for the quick reply Capink!  You helpful folks in the linux community are one of the reasons I'm such a huge fan of the OS!


Ok, Following the tutorial as written: after unmounting, just before making squashfs in step D.4.  The outputs you requested.
```

ubuntu@lcd1:~$ sudo cat ${WORK}/rootfs/etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
usbmux:x:106:46:usbmux daemon,,,:/home/usbmux:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:117:RealtimeKit,,,:/proc:/bin/false
saned:x:111:118::/home/saned:/bin/false
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:113:120:Gnome Display Manager:/var/lib/gdm:/bin/false
vboxadd:x:999:1::/var/run/vboxadd:/bin/false
ubuntu@lcd1:~$ 
ubuntu@lcd1:~$ sudo ls sudo cat ${WORK}/rootfs/dev
ls: cannot access sudo: No such file or directory
ls: cannot access cat: No such file or directory
/home/ubuntu/work/rootfs/dev:
ubuntu@lcd1:~$ 
ubuntu@lcd1:~$ sudo ls sudo cat ${WORK}/rootfs/dev
ls: cannot access sudo: No such file or directory
ls: cannot access cat: No such file or directory
/home/ubuntu/work/rootfs/dev:
ubuntu@lcd1:~$ sudo ls ${WORK}/rootfs/proc
ubuntu@lcd1:~$ 
ubuntu@lcd1:~$ sudo ls ${WORK}/rootfs/sys
ubuntu@lcd1:~$ 

```
On a side note: after creating the squashfs I mounted it to have a look at /etc/passwd.  It does indeed have all the users from the original host's passwd file rather than the trimmed version.

---

### Post by Darin722 on 2011-06-27
Hm.  I seem to have confused myself along the way somewhere.  I just mounted the live-cd.iso and the filesystem.squashfs and looked at /etc/passwd again.  There are no users with uid's greater than 999.  When I start the iso in virtualbox though it still asks for a login.

---

### Post by capink on 2011-06-27
I think I know what is wrong there. Your /etc/passwd shows a user with an id 999 which is strange. Have you set that user manually. Anyway, we have to remove that user because id 999 is preserved for the live cd user. I updated thed guide to guard against this happening for anyone else.

You don't have to start over if you have not cleaned your workspace (the optional step D.3). Do the following:


```
export WORK=[COLOR="Magenta"]~/work[/COLOR]
export CD=[COLOR="Magenta"]~/cd[/COLOR]
export FORMAT=squashfs
export FS_DIR=casper
```


replace the values in [COLOR="Magenta"]Magenta[/COLOR] with the exact same values you used in your previous attempt.





chroot into the rootfs evn


```
sudo chroot ${WORK}/rootfs /bin/bash
```




Remove non system users (including uid 999)

```
[COLOR="Blue"]for i in `cat /etc/passwd | awk -F":" '{print $1}'`
do
	uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
	[ "$uid" -gt "998" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null
done[/COLOR]
```






Now, exit the chroot


```
[COLOR="Blue"]exit[/COLOR]
```




resume the steps of the guide at step D.4

---

### Post by Darin722 on 2011-06-27
Thanks!  That did the trick!


You've really helped my project along and helped open up a new playground of creating custom CDs  :)


The user with the uid of 999 was created by virtualbox when I installed the guest addins.

---

### Post by pathakvirendra on 2011-07-12
Hello I followed the step and at last iso image was formed. But when I boot from virtualbox I get hang up on 

(initramfs) terminal with the error 
           " mount : mounting aufs on root failed : No such device 
                    aufs mount failed "

I am using ubuntu 10.10. Looking for help !!!!

---

### Post by rajesh.kalapura on 2011-07-14
> **pathakvirendra said:**
> Hello I followed the step and at last iso image was formed. But when I boot from virtualbox I get hang up on 

(initramfs) terminal with the error 
           " mount : mounting aufs on root failed : No such device 
                    aufs mount failed "

I am using ubuntu 10.10. Looking for help !!!!

I had also same problem with remastered cd of Ubuntu Natty. Recompiling the Natty kernel with aufs2 is the only fix for this.Anyway I have successfully recompiled kernel with aufs2 and now it booted successfully.Thank you capink,for such a nice tutorial.:P:P:P

---

### Post by mbah.pande on 2011-08-02
what a good post :KS
i tried to make my own LiveDVD from natty with this tutorial but stuck in this when installing casper at chroot

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-7-generic
df: Warning: cannot read table of mounted file systems: No such file or directory
cryptsetup: WARNING: could not determine root device from /etc/fstab

how to resolve this error? ](*,)

---

### Post by capink on 2011-08-02
That error will not affect the end result. Continue the rest of the guide. It is not an error anyway, it just a warning. Most probably it is caused by the absence of mtab file in the chroot environment. As I said, this should not affect the process of creating a live CD.

---

### Post by jaakw on 2011-08-06
Hellow

I used this script to make my customized live DVD. On harddisk I made some modifications. Install smart card reader and some specific software. Among other things I install network printer (ower printserver). Printer works if I boot from HDD. If I test the iso then there is not printer in the system. Printer miss on the DVD to. Other modifications are OK. Smart card reader works and software is OK.

What must I do different that the printer will work on live DVD?

Regards
Jaak

---

### Post by capink on 2011-08-06
I don't know why your printer is not appearing. I guess the reason is that some files that are necessary for you printer to work are installed to your home directory. You have to identify these files and copy them to the /etc/skel in the live CD.

---

### Post by jaakw on 2011-08-06
> **capink said:**
> I don't know why your printer is not appearing. I guess the reason is that some files that are necessary for you printer to work are installed to your home directory. You have to identify these files and copy them to the /etc/skel in the live CD.

I installed the system as user administrator. In what directory must I search the files?
/home/administrator/
or
/root/

Files that I can assosiate with printing is situated in /etc/cups directory. What kind of files must I find more?

Regards,
Jaak

---

### Post by grubu on 2011-08-22
> **capink said:**
> [SIZE=4]Building the live media from scratch using debootstrap.[/SIZE]

Instead of using your current installation to be the basis of you live CD, you can build a custom clean system from scratch using, and then use that as the basis of your CD. The modifications you have to make are:

[SIZE=4][COLOR=Purple]*Update 1: This guide is updated to use grub2 instead of grub-legacy*[/COLOR][/SIZE]

These are instructions for people who want a live CD containing a clean system (or a minimal rescue disc), you can build a new custom Ubuntu from scratch using debootstarp, and then apply the steps of the guide to make a live cd out of it. These are the steps for people who wish to build a custom system from scratch, instead of using their harddrive installation as a basis.


[SIZE=5]_*Outline of the steps:*_[/SIZE]

A. Prepare Our work environment.

B. Copy the Source system to the target directory.

C. Chroot into the new system and make some modifications.

D. Prepare The CD directory tree.

E. Build the CD/DVD


[COLOR=Purple]**Appendix 1. Building the live media form scratch using Debootstrap.**[/COLOR]

[SIZE=5]_*Conventions used in this HOWTO:*_[/SIZE]

[LIST]
[*][COLOR=Magenta]Text highlighted in Magenta is meant to be replaced by the user's [SIZE=4]_**custom value**_[/SIZE][/COLOR]. e.g. I will use [COLOR=Magenta]gedit[/COLOR] as my default text editor. Replace [COLOR=Magenta]gedit[/COLOR] with your favorite text editor.
[/LIST]

[LIST]
[*][COLOR=Blue]Commands performed within a [SIZE=4]_**chroot**_[/SIZE] will be in Blue.[/COLOR]
[/LIST]

[LIST]
[*][COLOR=Gray][SIZE=4]_**Optional**_[/SIZE] arguments or steps will be highlighted in Gray.[/COLOR]
[/LIST]


[SIZE=4]_*A. Preparing the environment*_[/SIZE]

1. Set some variables

```
export WORK=[COLOR=Magenta]~/work[/COLOR]
export CD=[COLOR=Magenta]~/cd[/COLOR]
export FORMAT=squashfs
export FS_DIR=casper
```The WORK Directory is where our temporary files and mount point will reside.
The CD is the location of the CD tree.
FORMAT is the filesystem type. We you are going to use a compressed squashfs.
FS_DIR is the location of the actual filesystem image within the cd tree.

Replace only the values highlighted in [COLOR=Magenta]Magenta[/COLOR].




2. Create the CD and the WORK directory structure:

```
sudo mkdir -p ${CD}/{${FS_DIR},boot/grub} ${WORK}/rootfs
```3. Install some packages on your current system:


```
sudo apt-get update
``````
sudo apt-get install grub2 xorriso squashfs-tools [COLOR=Gray]qemu[/COLOR]
```[COLOR=Gray]qemu[/COLOR] is optional. It is only needed for testing the cd before burning it. It can be substituted with any other virtualization software like virtualbox.


[SIZE=4]_*B. Build a custom system from scratch using debootstrap*_[/SIZE]

1. Install debootstrap

```
sudo apt-get install debootstrap
```2. Run debootstrap to install the basic packages:

```
sudo debootstrap [COLOR=Magenta]natty[/COLOR] ${WORK}/rootfs
```Replace [COLOR=Magenta]natty[/COLOR] with any other version you want (e.g. maverick, lucid, .....)

This step will take time as the deb files are downloaded.


Now you have a system the contain the basic packages. At this stage this system can only work as chroot system. But in the next steps we will modify it to be full system.



3. Prepare the new system before chrooting into it:

Modify the new system sources list:

```
sudo [COLOR=Magenta]gedit[/COLOR] ${WORK}/rootfs/etc/apt/sources.list
```And place the following text into it:

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted universe multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free 
Note: Replace [COLOR=Magenta]natty[/COLOR] with your favorite version name. e.g. maverick




Copy the following files to have internet access within the chroot environment:

```
for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ${WORK}/rootfs/etc/; done
```[SIZE=4][U][I]C. Chroot into the new system and modify it:
[/I][/U][/SIZE]4. Chroot into the new system:

```
sudo mount --bind /dev ${WORK}/rootfs/dev
``````
sudo mount  -t proc proc ${WORK}/rootfs/proc
``````
sudo mount -t sysfs sysfs  ${WORK}/rootfs/sys
``````
sudo mount -t devpts devpts  ${WORK}/rootfs/dev/pts
``````
sudo chroot ${WORK}/rootfs  /bin/bash
```[COLOR=Blue]Note: All commands in blue are run within chroot.[/COLOR]

```
[COLOR=Blue]LANG=[/COLOR]
```5. Once in chroot, modify the new system:

```
[COLOR=#0000ff]apt-get update --allow-unauthenticated[/COLOR]
```This will give you GPG warning because of third party repositories (Codecs repositories). Ignore it and proceed.



6. Install the multimedia repository keyrings ( to prevent apt from complaining about missing GPG ):

```
[COLOR=#0000ff]apt-get -qq install wget && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -[/COLOR]
```7. Install some important packages not included in the base install performed by debootstrap, most notably is the kernel:

```
[COLOR=#0000ff]apt-get install linux-generic linux-headers-generic ubuntu-minimal ubuntu-standard[/COLOR]
```Now, we have a complete command line system







8. To have a GUI system, install:

```
[COLOR=#0000ff]apt-get install [COLOR=Red]xorg[/COLOR] [COLOR=Magenta]gdm openbox[/COLOR] [COLOR=Gray]fbpanel thunar firefox mplayer w32codecs scite gqview xarchiver rxvt gtk2-engines xcursor-themes ttf-bitstream-vera ttf-dejavu ttf-freefont[/COLOR][/COLOR]
```[COLOR=Red]xorg[/COLOR] in necessary for a GUI.
Replace [COLOR=Magenta]openbox[/COLOR] with your favorite window manager.
Replace [COLOR=Magenta]gdm[/COLOR] with your favorite login manager. (Or you can do without login manager and user startx if you want)
The rest is optional. You can ignore them or replace them with your favorite programs. if you are a gnome fan you can install gnome-core. kde fans can install kde. xfce fans can install xfce4 ......

Note: If you want to build a system identical to official ubuntu replace all the packages above with just one metapackage called ubuntu-desktop (kubuntu-desktop for kubuntu, xubuntu-desktop for xubuntu)



By now you have built a complete GUI system. 




9. Install Packages Essential for live CD:


```
[COLOR=Blue]apt-get update[/COLOR]
``````
[COLOR=Blue]apt-get install casper[/COLOR]
```casper contain the live scirpts.
discover1 & xresprobe are used for autodetectin hardware at startup.    


[COLOR=Gray]3. (Optional) If you want your live cd to have an installer, install the Ubuntu installer:[/COLOR]

```
[COLOR=Blue]apt-get install ubiquity ubiquity-frontend-gtk[/COLOR]
```Note: People using kde replace replace the previous command with

```
[COLOR=Blue]apt-get install ubiquity ubiquity-frontend-kde[/COLOR]
```[COLOR=Gray](Optional Step)Install any packages you want to be in the CD. Some of the following packages are useful in emergency situations:

```
[COLOR=Gray]sudo apt-get install gparted ms-sys testdisk wipe partimage xfsprogs reiserfsprogs jfsutils ntfs-3g ntfsprogs dosfstools mtools[/COLOR]
```gparted: patitioning tool. It is automatically installed as a dependecy of ubiquity.
testdisk: Partition scanner and disk recovery tool.
wipe: Secure file deletion.
partimage: backup partitions into a compressed image file (like norton ghost).
xfsprogs reiserfsprogs jfsutils: Tools for handling different filesystems.
mtools: Tools for manipulating MSDOS files

[/COLOR]



10. Update the initramfs:

Set the kernel version of the chroot env:

```
[COLOR=Blue]export kversion=`cd /boot && ls -1 vmlinuz-* | tail -1 | sed 's@vmlinuz-@@'`[/COLOR]
```First update modules.dep:

```
[COLOR=Blue]depmod -a $(uname -r)[/COLOR]
```Update the initrd

```
[COLOR=Blue]update-initramfs -u -k $kversion[/COLOR]
```As already metioned above, the initramfs is reponsible for much of the preparation required at the boot time of the CD/DVD. The updated initramfs now contain the live scirpts installed with casper.




11. Clean apt cache

```
[COLOR=Blue]apt-get clean[/COLOR]
```12. Clean some dirs and files:

```
[COLOR=Blue]rm /etc/resolv.conf[/COLOR]
``````
[COLOR=Blue]rm /etc/hostname[/COLOR]
```13. Exit chroot

```
[COLOR=Blue]exit[/COLOR]
```
[SIZE=4]_*D. Prepare The CD directory tree:*_[/SIZE]

1. Copy the kernel, the updated initrd and memtest prepared in the chroot:

```
export kversion=`cd ${WORK}/rootfs/boot && ls -1 vmlinuz-* | tail -1 | sed 's@vmlinuz-@@'`
``````
sudo cp -vp ${WORK}/rootfs/boot/vmlinuz-${kversion} ${CD}/boot/vmlinuz
``````
sudo cp -vp ${WORK}/rootfs/boot/initrd.img-${kversion} ${CD}/boot/initrd.img
``````
sudo cp -vp ${WORK}/rootfs/boot/memtest86+.bin ${CD}/boot
```[COLOR=Gray]2. Generate manifest:

Note: This step is only needed if you installed the Ubuntu installer ubiquity. This step generates two files (filesystem.manifest & filesystem.manifest-desktop).

```
[COLOR=Gray]sudo chroot ${WORK}/rootfs dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ${CD}/${FS_DIR}/filesystem.manifest[/COLOR]
``````
[COLOR=Gray]sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}[/COLOR]
``````
[COLOR=Gray]REMOVE='ubiquity casper user-setup os-prober libdebian-installer4'[/COLOR]
``````
[COLOR=Gray]for i in $REMOVE 
do
    sudo sed -i "/${i}/d" ${CD}/${FS_DIR}/filesystem.manifest-desktop
done
[/COLOR]
```These two files are used by the ubiquity installer when installing to harddisk. These two files are just lists of packages. Ubiquity compares these two files and removes packages unique to filesystem.manifest. This way when installing to harddisk, packages like casper which is only useful in a live CD/DVD are removed. These packages that will be removed at install are defined in the variable $REMOVE[/COLOR]


3. Unmount bind mounted dirs:

```
sudo umount ${WORK}/rootfs/proc
``````
sudo umount ${WORK}/rootfs/sys
``````
sudo umount ${WORK}/rootfs/dev/pts
``````
sudo umount ${WORK}/rootfs/dev
```4. Convert the directory tree into a squashfs:


```
sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} -noappend
```Note: Make sure the resulting file size can fit into your live media.






5. Make filesystem.size


```
echo -n $(sudo du -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/casper/filesystem.size
```6. Calculate MD5

```


find ${CD} -type f -print0 | xargs -0 md5sum | sed "s@${CD}@.@" | grep -v md5sum.txt |sudo tee ${CD}/md5sum.txt


```7. Make Grub the bootloader of the CD


Make the grub.cfg

```
sudo [COLOR=Magenta]gedit[/COLOR] ${CD}/boot/grub/grub.cfg
```Copy the following text into it and save it.

```
set default="0"
set timeout=10

menuentry "Ubuntu GUI" {
linux /boot/vmlinuz boot=casper quiet splash
initrd /boot/initrd.img
}


menuentry "Ubuntu in safe mode" {
linux /boot/vmlinuz boot=casper xforcevesa quiet splash
initrd /boot/initrd.img
}


menuentry "Ubuntu CLI" {
linux /boot/vmlinuz boot=casper textonly quiet splash
initrd /boot/initrd.img
}


menuentry "Ubuntu GUI persistent mode" {
linux /boot/vmlinuz boot=casper persistent quiet splash
initrd /boot/initrd.img
}


menuentry "Ubuntu GUI from RAM" {
linux /boot/vmlinuz boot=casper toram quiet splash
initrd /boot/initrd.img
}

menuentry "Check Disk for Defects" {
linux /boot/vmlinuz boot=casper integrity-check quiet splash
initrd /boot/initrd.img
}


menuentry "Memory Test" {
linux16 /boot/memtest86+.bin
}


menuentry "Boot from the first hard disk" {
set root=(hd0)
chainloader +1
}
```[SIZE=4]_*E. Build the CD/DVD*_[/SIZE]

1. Make the ISO file

```
sudo grub-mkrescue -o ~/live-cd.iso ${CD}
```2. Test the CD

Test using qemu emulator 
```
qemu -cdrom ~/live-cd.iso -boot d
```Or use any other virtualization program you like.


**Update: As noted by [az]("http://ubuntuforums.org/member.php?u=844") in this [post]("http://ubuntuforums.org/showpost.php?p=4643009&postcount=18"), while testing the iso with qemu sometimes it drops you to an initramfs shell because of a problem with qemu. This behaviour has been confirmed by other users. In this case it is advisable to retest the iso with another virtualization software like virtualbox or to copy the iso to flash disk and test directly on your pc (See Appendix 2.).**


[COLOR=Gray]3. (Optional) Clean our workspace

```
[ -d "$WORK" ] && rm -r $WORK $CD
```[/COLOR]






[SIZE=5]_*Final Notes:*_[/SIZE]



[LIST]
[*]If you are using a custom kernel make sure it has support for the following:
[LIST=1]
[*]Support of loopback device.
[*]Support for squashfs.
[*]Support for aufs2.
[*]Support for initramfs.
[/LIST]
 
[/LIST]



[LIST]
[*]There are some extra options I put in the grub menu:
[LIST=1]
[*]Start linux form RAM. This option is only possible if your ram is larger than data on the live media. This option can be useful if you are building a minimal command line rescue disc as it would enhance performance to start it from RAM.
[*]Start in presistent mode. To learn about it more look [here]("https://help.ubuntu.com/community/LiveCDPersistence").
[*]Start Linux in Text Mode. This will not start X. The user will be autologged into a virtual terminal (the kind of terminal you get when you press Alt+Ctrl+F1).
[/LIST]
 
[/LIST]



Hello capink, :popcorn:

thank you very much for the supply of this guide.

In order to have a better overview I tried to put together what should be needed for building a clean natty-live-cd, 
I hope you like it, please correct me if I mentioned something wrong.

---

### Post by capink on 2011-08-23
> **grubu said:**
> Hello capink, :popcorn:

thank you very much for the supply of this guide.

In order to have a better overview I tried to put together what should be needed for building a clean natty-live-cd, 
I hope you like it, please correct me if I mentioned something wrong.

Thank you for taking the time to put it together. This would make it easier for people wanting to make a clean CD. I posted a link to your post in the clean cd appendix. It will remain there as long as it in sync with the updates to the guide.

You joined the two guides fine, but while reading it I noticed a mistake I did in the original guide. In step C.10 replace [COLOR="Magenta"]$(uname -r)[/COLOR] with [COLOR="Magenta"]$kversion[/COLOR]. The old version would work only if the kernel is the same in both the chroot and the host.

---

### Post by grubu on 2011-08-23
Hello capink I hope it's replaced the right way.
The time sticking it together was a great pleasure as it seems that
I am a very good friend :) of working guides from beginning to end.

Capink, I have some problems with building a live-cd of my hd-installation,
tried it twice but all I am ending with is an iso which is not working either in 
qemu or from a normal boot. Also the structure within the iso seems to be 
not as it should.

Here is everything I did:

```

mkdir /media/ext4-external/work/
mkdir /media/ext4-external/cd/

export WORK=/media/ext4-external/work
export CD=/media/ext4-external/cd
export FORMAT=squashfs
export FS_DIR=casper

sudo apt-get update
sudo apt-get install grub2 xorriso squashfs-tools qemu

sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/* --exclude=/sys/* --exclude=/tmp/* --exclude=/home/* --exclude=/lost+found --exclude=/var/tmp/* --exclude=/boot/grub/* --exclude=/root/* --exclude=/var/mail/* --exclude=/var/spool/* --exclude=/media/* --exclude=/etc/fstab --exclude=/etc/mtab --exclude=/etc/hosts --exclude=/etc/timezone --exclude=/etc/shadow* --exclude=/etc/gshadow* --exclude=/etc/X11/xorg.conf* --exclude=/etc/gdm/custom.conf --exclude=${WORK}/rootfs / ${WORK}/rootfs

sudo mkdir -p ${CD}/{${FS_DIR},boot/grub} ${WORK}/rootfs

sudo mount --bind /dev/ ${WORK}/rootfs/dev
sudo mount -t proc proc ${WORK}/rootfs/proc
sudo mount -t sysfs sysfs ${WORK}/rootfs/sys
sudo mount -t devpts devpts ${WORK}/rootfs/dev/pts

sudo chroot ${WORK}/rootfs /bin/bash

LANG=
apt-get update
apt-get install casper
apt-get install ubiquity ubiquity-frontend-gtk
sudo apt-get install gparted testdisk reiserfsprogs jfsutils ntfs-3g ntfsprogs dosfstools mtools lvm2

depmod -a $(uname -r)
update-initramfs -u -k $(uname -r)

for i in `cat /etc/passwd | awk -F":" '{print $1}'`; do uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`; [ "$uid" -gt "998" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null; done

apt-get clean

find /var/log -regex '.*?[0-9].*?' -exec rm -v {} \;

find /var/log -type f | while read file; do cat /dev/null | tee $file; done

rm /etc/resolv.conf /etc/hostname

exit


export kversion=`cd ${WORK}/rootfs/boot && ls -1 vmlinuz-* | tail -1 | sed 's@vmlinuz-@@'`

sudo cp -vp ${WORK}/rootfs/boot/vmlinuz-${kversion} ${CD}/boot/vmlinuz

sudo cp -vp ${WORK}/rootfs/boot/initrd.img-${kversion} ${CD}/boot/initrd.img

sudo cp -vp ${WORK}/rootfs/boot/memtest86+.bin ${CD}/boot

sudo chroot ${WORK}/rootfs dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ${CD}/${FS_DIR}/filesystem.manifest

sudo cp -v ${CD}/${FS_DIR}/filesystem.manifest{,-desktop}

REMOVE='ubiquity casper user-setup os-prober libdebian-installer4'

for i in $REMOVE ; do sudo sed -i "/${i}/d" ${CD}/${FS_DIR}/filesystem.manifest-desktop; done

sudo umount ${WORK}/rootfs/proc
sudo umount ${WORK}/rootfs/sys
sudo umount ${WORK}/rootfs/dev/pts
sudo umount ${WORK}/rootfs/dev

sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT} -noappend

echo -n $(sudo du -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/casper/filesystem.size

find ${CD} -type f -print0 | xargs -0 md5sum | sed "s@${CD}@.@" | grep -v md5sum.txt |sudo tee ${CD}/md5sum.txt

sudo gedit ${CD}/boot/grub/grub.cfg
set default="0"
set timeout=10

menuentry "Ubuntu GUI" {
linux /boot/vmlinuz boot=casper quiet splash
initrd /boot/initrd.img
}
menuentry "Ubuntu in safe mode" {
linux /boot/vmlinuz boot=casper xforcevesa quiet splash
initrd /boot/initrd.img
}
menuentry "Ubuntu CLI" {
linux /boot/vmlinuz boot=casper textonly quiet splash
initrd /boot/initrd.img
}
menuentry "Ubuntu GUI persistent mode" {
linux /boot/vmlinuz boot=casper persistent quiet splash
initrd /boot/initrd.img
}
menuentry "Ubuntu GUI from RAM" {
linux /boot/vmlinuz boot=casper toram quiet splash
initrd /boot/initrd.img
}
menuentry "Check Disk for Defects" {
linux /boot/vmlinuz boot=casper integrity-check quiet splash
initrd /boot/initrd.img
}
menuentry "Memory Test" {
linux16 /boot/memtest86+.bin
}
menuentry "Boot from the first hard disk" {
set root=(hd0)
chainloader +1
}


sudo grub-mkrescue -o ~/live-cd.iso ${CD}

sudo qemu -cdrom ~/live-cd.iso -boot d

```


This line gave me some trouble:
```

echo -n $(sudo du -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/casper/filesystem.size

```

I am not sure if its syntax is wrong and this one would be right?:
```

echo -n $(sudo du / -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/casper/filesystem.size

```

Do you have an idea what I did wrong?
Thanks a lot for reading Capink.

---

### Post by capink on 2011-08-24
> **grubu said:**
> 
Capink, I have some problems with building a live-cd of my hd-installation,
tried it twice but all I am ending with is an iso which is not working either in 
qemu or from a normal boot. 

In what way is not working? Is it giving you error message at startup? If so please tell what is the error message.


> **grubu said:**
> Also the structure within the iso seems to be 
not as it should.



I will need to see the structure of the ISO. To do so do the following:

```
sudo apt-get install tree
```

and post the output of the following command:

```
sudo tree /media/ext4-external/cd/
```




> **grubu said:**
> This line gave me some trouble:
```

echo -n $(sudo du -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/casper/filesystem.size

```

Again please post the exact error message this command is giving you. Anyway, even without this command the ISO should boot fine. the file created above is only necessary for the installer.


One last question, have you been able to successfully create a clean cd from scratch?

---

### Post by grubu on 2011-08-25
Hello Capink,
hm, it seems that this structure is as it should be:

/media/ext4-external/cd/
&#9500;&#9472;&#9472; boot
&#9474;   &#9500;&#9472;&#9472; grub
&#9474;   &#9474;   &#9492;&#9472;&#9472; grub.cfg
&#9474;   &#9500;&#9472;&#9472; initrd.img
&#9474;   &#9500;&#9472;&#9472; memtest86+.bin
&#9474;   &#9492;&#9472;&#9472; vmlinuz
&#9500;&#9472;&#9472; casper
&#9474;   &#9500;&#9472;&#9472; filesystem.manifest
&#9474;   &#9500;&#9472;&#9472; filesystem.manifest-desktop
&#9474;   &#9500;&#9472;&#9472; filesystem.size
&#9474;   &#9492;&#9472;&#9472; filesystem.squashfs
&#9492;&#9472;&#9472; md5sum.txt

But when I look into the written iso I have something like three "grub" and three "casper" folders which looks by far different to any other livecd. Maybe it is just because the iso written in the right way.

I tried both guides a few times but can not get a working result. I have no clue on what I did wrong, but will try both again these days and then report the results I am getting.

---

### Post by GeoMX on 2011-09-05
I'm reading your updated guide and trying to create a USB instead of a Live CD, but when trying to boot from it, I finish with a BusyBox shell and this message:

*(initramfs) Unable to find a medium contining a live file system.*

Unless I copy the ${CD}/casper directory to the USB, but it beats the purpose of using the .iso doesn't it?
-----------------------
Right now I'm trying to boot using the files contained in the ISO as described by **prohp** in [261]("http://ubuntuforums.org/showpost.php?p=10663680&postcount=261") (but using grub2 instead of grub legacy), but no success till now.
-----------------------
I've succesfully booted from an USB stick using the casper directory files (not the live-cd.iso), the steps I followed:

[LIST=1]
[*]Mount USB stick (let's suppose it's mounted on /media/USB)
[*]Copy ${CD}/casper directory to USB stick
[*]Install GRUB to USB stick
sudo grub-install --no-floppy --force --root-directory=/media/USB  /dev/sdX
[*]Copy ${CD}/boot/vmlinuz,initrd.img,memtest86+.bin to /media/USB/boot/
[*]Edit grub.cfg, you can use similar options to the ones used for the live CD.
[/LIST]

---

### Post by capink on 2011-09-08
I don't know what is happening in your case. But since you are dropped into a tty shell it means that grub was able to load both the kernel and the initrd just fine. The problem is that for some reason initrd might not be able to mount the ISO image. To debug this: when you are dropped into the tty shell please type the following command:

```
cat casper.log
```

also to know whether the iso is mounted type:

```
ls /cdrom
```

Post the output of the previous two commands.


Some people reported problems when using usb3. If that is your case, try using an old usb2 port and see if there is any difference.

Last thing, I am trying to reproduce your problem. I what to know the format of your flash stick (vfat or ext2 ....)

---

### Post by GeoMX on 2011-09-08
Thanks for your reply, this is the output of the commands:

cat casper.log
[I]Begin: Running /scripts/casper-premount ...
Done.
Done.
Unable to find a medium containing a live file system[/I]

ls /cdrom
*(nothing)*

I've been trying with a FAT32 stick, after your comments I tried formatting it as ext3 but got same result.

---

### Post by capink on 2011-09-11
Sorry for the delay, I've been busy the past few days. I have not been able to identify the cause of your problem. It is working fine for me.

Please if any one tried creating bootable ISO using this guide share your experiences with us.

Last thing, try the usb stick with other machines to see if it will work. Maybe the problem is that casper initrd does not contain the drivers for your specific usb controller.

---

### Post by capink on 2011-09-12
One more thing. To be sure this is not a bug in casper, you can try using ubuntu's official ISO on your usb stick and see if it works. If it does not you can file a bug report to ubuntu devs.

---

### Post by imetallica on 2011-10-04
I've got a question about post 284: [http://ubuntuforums.org/showpost.php?p=11176942&postcount=284](http://ubuntuforums.org/showpost.php?p=11176942&postcount=284)

Is it possible to make some tweaks in the GNOME desktop look? Like, start with a different wallpaper for example.

Thanks in advance, and a nice guide. :-)

---

### Post by maramyfriend on 2011-10-13
Please excuse my ignorance but I wanted to make sure this is going to do what I think it will.

I have Ubuntu 11.4 installed on my desktop, I have installed the apps I want, installed oracle, and have it up and running.

Will this process basically give me a DVD so if I got a new computer and put that DVD into it I would have an exact replica of my current desktop installed?

Thanks

---

### Post by inameiname on 2011-10-14
> **maramyfriend said:**
> Please excuse my ignorance but I wanted to make sure this is going to do what I think it will.

I have Ubuntu 11.4 installed on my desktop, I have installed the apps I want, installed oracle, and have it up and running.

Will this process basically give me a DVD so if I got a new computer and put that DVD into it I would have an exact replica of my current desktop installed?

Thanks

If it all works correctly, it will create a new live DVD for you, just like the original Ubuntu 11.04 disc, but that disc will include the apps that you have installed, those you may have removed, including oracle installed, and etc. So yes, it should create an exact replica of your current desktop.

Speaking of that, why not just use Remastersys? It is a very small package that does all of that automatically for you. Unfortunately, it is a project that is no longer being developed. Fortunately, though, a fork of it, called Relinux, is in beta at the moment, and will ideally be a full replacement for it.

Anyway, Remastersys does full computer 'backups' (includes home folder) or 'distros' (no home folder) very easily. For 11.04, or Natty and earlier Ubuntu versions, you can still use Remastersys. I'll be sure to attach the last version of it that works for Ubuntu for you. Relinux, however, doesn't do a full computer 'backup' just yet, but that will soon be available. 

Here is relinux:

[http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)

---

### Post by rajesh.kalapura on 2011-10-20
Thanks Capink for such a nice tutorial.I have just made an Ubuntu 11.10 Live-cum-Install DVD with your tutorial.It contains almost all of my favourite software packages and having 3 GB in size. 
                                        After partitioning and user naming process,when I click the last install option ,the installing box that runs Ubuntu demos decreased to a small sized box.This is the only problem that I had faced,while installing with this Live-dvd.Anyway it's only a minor issue for me and I think it may be a fault from my side also....Thanks agian capink......:p:p:p

See the booting screen of the DVD I have made from Capink's guide

---

### Post by beer-in-box on 2011-10-21
Thank you for this tutorial which should be a wiki.
I tried it and worked good. There were some issues when I tried it on virtual machine, but it said that it was my fault with nVidia drivers and some configuration. 

So, I am going to reformat my system, update it, customize it and make a (insttallable) live cd out of it before doing anything stupid this time :)

---

### Post by gluni on 2011-10-24
Any chance to see an adaptation of this tutorial for other distributions?
Maybe sabayon?

thx anyway

---

### Post by Orion13622 on 2011-10-29
I'm a bit of an intermediate Linux user (slightly passed newbie) and I've followed the directions exactly like you have them, however I've noticed 3 things.

1.  Upon creating the MD5 hash, I get a permission denied for vmlinuz, but the rest of the files are ok.

2.  If I switch over to verbose mode (alt-F2) during boot, I see several Permission Denied messages during startup.

3.  Once the live DVD has started, I'm immediately taken to my login screen.  Neither my user name, nor password work when trying to log in.  I even went as far as making a user named ubuntu with a security of 999.  Still no joy.  Any suggestions would be greatly appreciated, as at this point, I'd love to have a Live DVD of my current system (11.04) that is installable, however if I can't get past the login screen, seems a bit of a moot point.

Just a shot in the dark, but I'm guessing that the MD5 Permission Denied error has something to do with this.  Many thanks in advance.

Orion

---

### Post by carloseros on 2011-11-01
its possible to do this on a debian installation :confused:, how to replace casper package?, because its not finding 



note: sorry for my english im not speak very well

---

### Post by carloseros on 2011-11-01
i got this little error! :confused:

sudo grub-mkrescue -o ~/live-cd.iso ${CD}
Unrecognized option `-o'
Usage: /usr/bin/grub-mkrescue [OPTION] SOURCE...
Make GRUB rescue image.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --output=FILE           save output in FILE [required]

/usr/bin/grub-mkrescue generates a bootable rescue image with specified source files or directories.

Report bugs to <bug-grub@gnu.org>.

---

### Post by carloseros on 2011-11-01
SOLUTION

$ sudo grub-mkrescue --output=live-cd.iso ${CD}

and it WORKED!
thanx!!!!! :)

this is for Ubuntu 10.10

---

### Post by User 04 on 2011-11-01
I read that it is possible to allocate new user name and password on re installation.

My question is, and hope not duplicating, if an application like MythTV is installed, will this still work properly.

This situation causes major problems with a Remastersys re install.

---

### Post by User 04 on 2011-11-05
[SIZE=2]Thanks carloseros for your command fix and thanks to capink for the guide.  To answer my own question, a new computer name and so on can be successfully allocated on installation without adverse effect on MythTV.[/SIZE]

---

### Post by undead2 on 2011-11-09
i want to create a custom distro. i want to change some default that they could be seen on my live disk: 
1) change default icon pack to faenza-ambiance 
2) change default start up apps to dockey & synapse & weather & blueman 
3) change default shell(GUI) to gnome3.2 
4) change default theme to adwaita 
5) change default cursor to adwaita
 any ideas?

---

### Post by undead2 on 2011-11-09
any ideas????
upppp...

---

### Post by undead2 on 2011-11-09
any ideas????
upppp...

---

### Post by Darin722 on 2011-12-06
I've run into a situation where it would be useful to create a live cd with non-system users intact.  

I tried to modify the procedure above to do so by dropping the routine that removes users and including rather than excluding shadow and gshadow, but grub-mkisofs fails with a "disk image not readable, so such file" error.

Any suggestions as to how to resolve this issue?

---

### Post by capink on 2011-12-07
> **Darin722 said:**
> but grub-mkisofs 


The Guide uses grub-mkresuce

> **Darin722 said:**
> 
Any suggestions as to how to resolve this issue?

There are two ways to this:

1. The first way is to add the following parameter to your boot options in grub.cfg:

```
username=[COLOR="Magenta"]whatever_username_you_want[/COLOR]
```

2. The second way edit the file ${WORK}/rootfs/etc/casper.conf change the following entry:

```
export USERNAME="[COLOR="Magenta"]whatever_username_you_want[/COLOR]"
```

After doing this, be sure to run the command update-initramfs within the chroot enviroment (Step C.4). And that the updated initrd is copied later to ${CD}/casper/initrd.img in step D.1


Note that either way you go, you will still have to preserve the shadow and gshadow ..... etc as you described in your post. To do it you replace the command in step B with the following one:
```

sudo rsync -av --one-file-system --exclude=/proc/* --exclude=/dev/* \
--exclude=/sys/* --exclude=/tmp/* --exclude=/home/* --exclude=/lost+found \
--exclude=/var/tmp/* --exclude=/boot/grub/* --exclude=/root/* \
--exclude=/var/mail/* --exclude=/var/spool/* --exclude=/media/* \
--exclude=/etc/fstab --exclude=/etc/mtab --exclude=/etc/hosts \
--exclude=/etc/timezone --exclude=/etc/X11/xorg.conf* \
--exclude=/etc/gdm/custom.conf --exclude=/etc/lightdm/lightdm.conf \
--exclude=${WORK}/rootfs / ${WORK}/rootfs
```


You will also have to skip step C.5

I have not tried any of this. You will have to try it yourself and see if it works.

---

### Post by Darin722 on 2011-12-14
Thanks for the reply Capink.

when you say add username=whateverUsername to bootoptions, do you mean like so...?

menuentry "Ubuntu GUI" {
linux /boot/vmlinuz boot=casper quiet splash username=dbAdmin
initrd /boot/initrd.img
}


Still getting the error..

...

> sudo grub-mkrescue --output=~/live-cd.iso ${CD}

Enabling BIOS support ...
Using GCRY_SHA.000;1 for /tmp/grub-mkrescue.bQShWUWJzO/boot/grub/i386-pc/gcry_sha1.mod (gcry_sha256.mod)
Using MULTIBOO.000;1 for /tmp/grub-mkrescue.bQShWUWJzO/boot/grub/i386-pc/multiboot2.mod (multiboot.mod)
Using GCRY_SHA.001;1 for /tmp/grub-mkrescue.bQShWUWJzO/boot/grub/i386-pc/gcry_sha256.mod (gcry_sha512.mod)
Using PASSWORD.000;1 for /tmp/grub-mkrescue.bQShWUWJzO/boot/grub/i386-pc/password.mod (password_pbkdf2.mod)
Using SEARCH_F.000;1 for /tmp/grub-mkrescue.bQShWUWJzO/boot/grub/i386-pc/search_fs_file.mod (search_fs_uuid.mod)
grub-mkisofs: Unable to open disc image file
: No such file or directory


I note that the output after "Enabling BIOS support" does not occur when I run the original version of the script (prior to editing to keep non-system users)

---

### Post by capink on 2011-12-14
> **Darin722 said:**
> Thanks for the reply Capink.

when you say add username=whateverUsername to bootoptions, do you mean like so...?



Yes

> **Darin722 said:**
> 
Still getting the error..

...

> sudo grub-mkrescue --output=~/live-cd.iso ${CD}

I am not able to troubleshoot that one. Try replacing it with:

```
sudo grub-mkrescue -o ~/live-cd.iso ${CD}
```

And see if it makes any difference.

---

### Post by kebabbaro on 2011-12-14
> **capink said:**
> Yes



I am not able to troubleshoot that one. Try replacing it with:

```
sudo grub-mkrescue -o ~/live-cd.iso ${CD}
```And see if it makes any difference.

I'm getting the same error, whereas entering your code triggers this other error:
```
Unrecognized option `-o'
Usage: /usr/bin/grub-mkrescue [OPTION] SOURCE...
Make GRUB rescue image.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --output=FILE           save output in FILE [required]

```Any help?

Or do you know any other way to build a liveISO from your HD installation?

---

### Post by capink on 2011-12-14
[http://ubuntuforums.org/showpost.php?p=11532322&postcount=167]("http://ubuntuforums.org/showpost.php?p=11532322&postcount=167")

---

### Post by Darin722 on 2011-12-15
> **capink said:**
> Yes



I am not able to troubleshoot that one. Try replacing it with:

```
sudo grub-mkrescue -o ~/live-cd.iso ${CD}
```

And see if it makes any difference.


I just ran grub-mkrescue directly from the command line instead of from the script and it worked fine!  

grub-mkrescue --output=~/live-cd.iso ~/cd

The live CD was generated and all users are intact and usable, so the greater part of the project at least is a success.  I'm still trying to debug why the script is throwing the error.  --go figure.

I checked the script var ${CD} and it appears to be fine. It's set to /home/dbadmin/cd which is the directory that contains /boot /casper, and /md5sum.txt


It also appears that the -o switch is no longer supported by grub-mkrescue, hence the use of --output=

anyway. Thanks for all your help!  I suspect the fault is some little detail.  If I find a solution I'll post it.

---

### Post by kebabbaro on 2011-12-16
> **capink said:**
> [http://ubuntuforums.org/showpost.php?p=11532322&postcount=167](http://ubuntuforums.org/showpost.php?p=11532322&postcount=167)

Thank you that fixed my problem.  I will try again your method ASAP, possibly building the ISO file with a burning tool like Brasero or something, and creating the bootable USB with the Ubuntu Disk Creator.  Will post the outcome here.

---

### Post by kebabbaro on 2011-12-19
Ok I made it.  Here's the solution: If grub-mkrescue command outputs an error, it is sufficient to burn the ISO using Brasero, and build the USB PenDrive using Unetbootin. The standard Ubuntu USB Disk Creator doesn't work though.

 To burn the ISO just drag and drop all the files inside the cd directory into the Brasero window. That is after you added permission to read to the filesystem.squashfs file inside the casper directory, for if you don't do that Brasero cannot burn that required file. 

FYI the procedure was tested on a Linux Mint 9 ( based on Ubuntu 10.04 ) machine. However, the grub-mkrescue command outputs that same error on both Linux Mint 9 32 bit and Ubuntu 10.04 64 bit.  

The only substantial change I made to these installations is changing the default directories location, I mean the location of Documents, Downloads, etc. I changed those locations by editing the ~/config/user-dirs.dirs file, putting those directories in a separate "storage" partition, and changing the /etc/fstab file of course in order to automatically mount that partition.
 This change i made on both my Linux Mint and Ubuntu machines. I dunno if this is somewhat related to the grub-mkrescue mulfunctioning.  

Thank you for your attention.

---

### Post by kebabbaro on 2011-12-19
> **kebabbaro said:**
>  I dunno if this is somewhat related to the grub-mkrescue mulfunctioning.  

No of course NOT!

I had the solution under my nose but I needed to write a post to realize it #-o

Obviously the reason why grub-mkrescue could not find the source file is the same reason why brasero could not read all the file: because the fylesystem.squashfs file, which is the major file containing the system data ( on my installation it is  2.5 GB big ), had no permission to be read, even from root.

So in the end it is sufficient to execute the following command:
```
sudo chmod +r ~/cd/casper/filesystem.squashfs
```to fix the problem.

That I just tested ):P

---

### Post by hsretry on 2011-12-23
Wow .. I was looking for something like this .. I am a newbie of sorts so I'd appreciate any inputs.
 
I am looking to make a live CD of my current setup of 10.04 so I can use it to re-install it in the likely case that I break my system while tinkering it. I think this is what is being intended by the instructions on the first page. Please correct me if I'm wrong.
 
If this works out will I have a live CD of 10.04 plus the extra packages that I have installed on my laptop after a clean install of the OS ? Again I'm a newbie who's broken his system on more than once and I want to have a backup that I can install without worrying about having internet to install a package ..
 
I'll be trying this anyways just for the experience !
Cheers,

---

### Post by kebabbaro on 2012-01-14
I have one little problem: after installing Ubuntu with the live media created using this procedure, I am not able to successfully login.  System prompts me to insert password at login screen but any password won't work, even the password I just chose during the installation process, why is that? :confused:

---

### Post by msmihai on 2012-01-18
Hi everybody!

I used this method and successfuly obtained a Live CD image that had all the packets that I had installed on my installation.

However, i would like the following as well:

- all that is related to gnome desktop to be saved ( so that the live distribution would have the same desktop, panel elements, etc.)
- firefox plugins and bookmarks saved as well

I manually added .config, .bashrc and .mozilla ( all folders in /home/mihai/, where mihai is my username) to the rootfs/etc/skel but that doesn not do the trick.

Any ideas?

---

### Post by User 04 on 2012-01-28
I have successfully created .iso's  for Ubuntu distributions from Ubuntu 9.10 up to Ubuntu 12.04 Beta 1.  However, with the latest updates can successfully create .iso, but when trying to install arrive at a log in screen with only one option, that is Guest Session, not able to enter ubuntu, no password.

Have also found that with the latest updates can no longer log in to root using previous processes.  Only able to log in with a password as "Computer User", or as Guest Session, no password.

Can provide a Clonezilla copy via my website if required.

---

### Post by Darin722 on 2012-02-04
> **msmihai said:**
> Hi everybody!

I used this method and successfuly obtained a Live CD image that had all the packets that I had installed on my installation.

However, i would like the following as well:

- all that is related to gnome desktop to be saved ( so that the live distribution would have the same desktop, panel elements, etc.)
- firefox plugins and bookmarks saved as well

I manually added .config, .bashrc and .mozilla ( all folders in /home/mihai/, where mihai is my username) to the rootfs/etc/skel but that doesn not do the trick.

Any ideas?

Can you mention what is and what is not being preserved?

---

### Post by Darin722 on 2012-02-04
> **kebabbaro said:**
> I have one little problem: after installing Ubuntu with the live media created using this procedure, I am not able to successfully login.  System prompts me to insert password at login screen but any password won't work, even the password I just chose during the installation process, why is that? :confused:

That sounds suspiciously like the problem I was originally having.  The problem turned out to be that there was a user that should have been deleted from the shadow and password files that wasn't being deleted.  Check to see that all users with user id's 998 and above are removed as per Capink's original tutorial [http://ubuntuforums.org/showthread.php?t=688872&highlight=users+%26gt%3B+999](http://ubuntuforums.org/showthread.php?t=688872&highlight=users+%26gt%3B+999)

---

### Post by acantonyclark1 on 2012-03-13
If you want to make Live CD/DVD then it is better to download Linux Install Disk. You can use this disk to boot your computer and repair computer from crashes. It contains both the kernel and the root file system.You can use this to boot your computer without hard drive. You can free download [Linux Install Disk]("http://www.linuxbootdisks.net") and can use free of cost.

---

### Post by Darin722 on 2012-03-21
> **acantonyclark1 said:**
> If you want to make Live CD/DVD then it is better to download Linux Install Disk. You can use this disk to boot your computer and repair computer from crashes. It contains both the kernel and the root file system.You can use this to boot your computer without hard drive. You can free download [Linux Install Disk]("http://www.linuxbootdisks.net") and can use free of cost.

Ah, but the point here is the ability to make a CUSTOM live cd, containing the programs and potentially data that we choose.

---

### Post by ezacon on 2012-04-15
I have successfuly built mi live CD from an installed Ubuntu Server 11.04.
I use it to automaticaly remove a partition in the computer where the live cd is booted. I have writed mi script and everithing is working fine.... except:
At boot, the live cd try to get an IP with dhcp, and produces a delay of 2 minutes in boot process. In my squash, /etc/network/interfaces has only lo configred, but in live cd, this file has entries for several interfaces. This network config file is not present in squash nor in inird.
Where did this file come from?
How can i avoid dhcp delay in boot. i dont need networking.

Thanks

---

### Post by capink on 2012-04-17
Append the following to the boot options in grub.cfg:

```
ip=frommedia
```

---

### Post by User 04 on 2012-05-12
> **User 04 said:**
> I have successfully created .iso's  for Ubuntu distributions from Ubuntu 9.10 up to Ubuntu 12.04 Beta 1.  However, with the latest updates can successfully create .iso, but when trying to install arrive at a log in screen with only one option, that is Guest Session, not able to enter ubuntu, no password.

Have also found that with the latest updates can no longer log in to root using previous processes.  Only able to log in with a password as "Computer User", or as Guest Session, no password.




Finally got time to look at this issue.


Access terminal,

sudo -i

gedit /etc/lightdm/lightdm.conf

add line,

greeter-show-manual-login=true

and this line if not already there,

user-session=ubuntu

mine now looks like this,

[SeatDefaults]
autologin-guest=false
autologin-user=user
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter
greeter-show-manual-login=true

Reboot and Bob's UR Uncle, although theses days he is prob UR trannie Aunt.

---

### Post by TheShadwofChaos on 2012-05-20
I just keep getting " invalid option -- '/'" Sorry about the stupid question but what am I missing?

---

### Post by goaliedude3919 on 2012-05-23
This is an excellent topic. I was hoping that there was a way to do this. I have Ubuntu on my Laptop and plan on putting it on the next Desktop that I get. I was dreading having to install all of my software again, so this will be a life saver.

---

### Post by roshgorg on 2012-05-26
I have a few questions. After completing this step, will the Ubuntu themes, splash screens, logos etc be installed ?

Will it be possible to :-

[LIST=1]
[*]add Ubuntu desktop GUI with Unity.
[*]add essential software and applications, including network.
[*]add other software
[*]And above all, I need to install my own kernel.
[*]I need to change the background images, logos and themes.
[*]Is it possible to change the boot animation ?
[*]I have read somewhere that, it is possible to change the prompt ubuntu@ubuntu to something else. How to change this ?
[/LIST]
  How is it possible? Will Ubuntu Customization Kit work ?

---

### Post by roshgorg on 2012-05-28
I got errors when executing two commands. They are given below. Please see these two errors.

```
root@roshan-Studio-1558:/# apt-get install casper lupin-casper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  localechooser-data user-setup
The following NEW packages will be installed:
  casper localechooser-data lupin-casper user-setup
0 upgraded, 4 newly installed, 0 to remove and 168 not upgraded.
Need to get 255 kB of archives.
After this operation, 954 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise/main localechooser-data all 2.39ubuntu2 [7004 B]
Get:2 http://in.archive.ubuntu.com/ubuntu/ precise/main user-setup all 1.42ubuntu3 [188 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ precise/main casper amd64 1.315 [53.8 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ precise/main lupin-casper all 0.51 [5888 B]
Fetched 255 kB in 20s (12.2 kB/s)                                              
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously unselected package localechooser-data.
(Reading database ... 142754 files and directories currently installed.)
Unpacking localechooser-data (from .../localechooser-data_2.39ubuntu2_all.deb) ...
Selecting previously unselected package user-setup.
Unpacking user-setup (from .../user-setup_1.42ubuntu3_all.deb) ...
Selecting previously unselected package casper.
Unpacking casper (from .../casper_1.315_amd64.deb) ...
Selecting previously unselected package lupin-casper.
Unpacking lupin-casper (from .../lupin-casper_0.51_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up localechooser-data (2.39ubuntu2) ...
Setting up user-setup (1.42ubuntu3) ...
Setting up casper (1.315) ...
update-initramfs: deferring update (trigger activated)
Setting up lupin-casper (0.51) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
df: Warning: cannot read table of mounted file systems: No such file or directory
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

```
root@roshan-Studio-1558:/# update-initramfs -u -k $(uname -r)
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
df: Warning: cannot read table of mounted file systems: No such file or directory
cryptsetup: WARNING: could not determine root device from /etc/fstab
root@roshan-Studio-1558:/# 

```

---

### Post by psrdotcom on 2012-05-29
Thank you very much guys .. Its been awesome response from all the users. :guitar:

---

### Post by karthick87 on 2012-06-23
Making bootable usb is not working. Could anyone help me with latest answers?

---

### Post by daniel_rodriguez on 2012-06-27
I could create the LiveCD but I want to add install option, is that possible?

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012418](http://ubuntuforums.org/showthread.php?t=2012418) 


Support threads regarding the wiki and it's content should be created in a suitable forum.

---


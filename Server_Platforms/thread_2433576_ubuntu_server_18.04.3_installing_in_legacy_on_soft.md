---
title: "ubuntu server 18.04.3 installing in legacy on soft raid 1 mbr fail"
date: 2019-12-21
forum: Server Platforms
---

### Post by scorpik on 2019-12-21
Ha all! I have 4 HDD 1TB. I want to install Ubuntu server 18.04.3 from native iso downloaded from ubuntu.com. I boot in legacy ubuntu server iso and create 3 partitions on each HDD:
```
 sda      8:0    1 931,5G  0 disk
&#9500;&#9472;sda1   8:1    1     1G  0 part 
&#9500;&#9472;sda2   8:2    1   900G  0 part 
&#9492;&#9472;sda3   8:3    1  30,5G  0 part 
sdb      8:16   1 931,5G  0 disk 
&#9500;&#9472;sdb1   8:17   1     1G  0 part 
&#9500;&#9472;sdb2   8:18   1   900G  0 part 
&#9492;&#9472;sdb3   8:19   1  30,5G  0 part 
sdc      8:32   1 931,5G  0 disk 
&#9500;&#9472;sdc1   8:33   1     1G  0 part 
&#9500;&#9472;sdc2   8:34   1   900G  0 part 
&#9492;&#9472;sdc3   8:35   1  30,5G  0 part 
sdd      8:48   1 931,5G  0 disk 
&#9500;&#9472;sdd1   8:49   1     1G  0 part 
&#9500;&#9472;sdd2   8:50   1   900G  0 part 
&#9492;&#9472;sdd3   8:51   1  30,5G  0 part 

```
Then I create three software raid:
```

md0 raid1  1G for /boot
md1 raid10 900G for /
md2 raid1 30,5G for SWAP

```

If I push "Done" to start install it fails. Installer create GPT and put EFI partition on one HDD and not on raid1 then installer fails to install
If I boot in Live-Desktop, create MBR on disks, create partitions  as listed above, then boot in legacy from ubuntu-server 18.04.3 iso, create soft raid from partitions:
```

md0 raid1  1G for /boot
md1 raid10 900G for /
md2 raid1 30,5G for SWAP

```

The installer don`t  give me access to push button "Done" to begin install beacause it is inactive.

How can I install ubuntu server 18.04.3 in legacy on MBR partitions soft raid1?
If installer can create only GPT partitions? why it can`t create EFI partition on soft raid1 and can`t create it on each hdd ? In this case if HDD with EFI partition dies, server will die with it.

---

### Post by TheFu on 2019-12-21
Why 4 disks?  I'd disconnect 2 of them for the OS installation, then add them back later, as and where needed.

Have you considered that the installer doesn't know how to boot from RAID-anything?
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html) explains RAID1 installs.

For RAID1, I'd use LVM during the install, then post-install setup a mirror.  Using LVM, there is no effective way to go from RAID1 to RAID10.  RAID10 is something that has to be added post-install and really only used for data storage, not the OS.

---

### Post by darkod on 2019-12-22
1. To use disks with MBR and Grub2 you need a small 1MiB partition with NO filesystem on it first. This is because grub2 it too big for MBR size and needs some additional space to save part of its files. DO NOT format this partition as anything, simply create it and leave it. Put the bios_grub flag on it. I suggest using terminal and parted from Live mode. When using GUI tools sometimes it formats by default without people noticing. I like parted because mkpart only creates partitions, does nothing about filesystem.

2. The installation of the bootloader MBR vs EFI depends on how you boot the iso. If you want MBR do not let the computer to boot the iso in EFI mode (it might do it automatically). Use the Boot Menu or anything similar to select what to boot from. On EFI boards you will have too devices, the standard DVD-ROM and the EFI DVD-ROM. It tries to create the EFI partition and install grub-efi because you have booted the EFI DVD-ROM.

---

### Post by scorpik on 2019-12-24
Thanks all!
I installed ubuntu-server 18.04.3 on soft raid in legacy mode MBR partitions. Here's How to do it:

1) I download "traditional installer" from [https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer](https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer)
2) Write ISO to USB and boot in legacy mode. Start installation.
3) Create partitions for soft raid and build raid. In my test configuration I have :
[COLOR=#0000cd]raid1 1GB md0 for /boot[/COLOR]
[COLOR=#0000cd]raid10 900GB md1 for /[/COLOR]
[COLOR=#0000cd]raid1 92GB md2 for swap[/COLOR]


4) Installation stoped with error installing grub-bootloader. I ignored this error and continued installation without install grub-bootloader. 
5) Download original ubuntu-server iso and boot from it. After selecting parameters of network interfaces I pressed ALT-CTRL-F2 and entered in console tty2
6) sudo -i
7) cat /proc/mdstat        # to see names of md devices and status
8) Stop all md devices:
mdadm --stop /dev/md126
mdadm --stop /dev/md125
mdadm --stop /dev/md127


8) convert  GPT to MBR on all disks:
gdisk /dev/sda
press r
press g
press w
then YES

convert other disks:
gdisk /dev/sdb
gdisk /dev/sdc
gdisk /dev/sdd

9) set active partitions. In my case partition 1 from soft raid1 for /boot :
fdisk /dev/sda
press a
press 1      # number of partition (to see: fdisk -l /dev/sda )
press w     # to write

fdisk -l /dev/sda
Device     Boot      Start        End    Sectors   Size Id Type/dev/sda1  *          2048    1953791    1951744   953M fd Linux raid autodetect
/dev/sda2          1953792 1759766527 1757812736 838,2G fd Linux raid autodetect
/dev/sda3       1759766528 1953523711  193757184  92,4G fd Linux raid autodetect

[COLOR=#ff0000]set active partitions on all hdd`s in soft raid1 for /boot
[/COLOR]fdisk /dev/sdb
fdisk /dev/sdc
fdisk /dev/sdd



10) Assemble soft raid with correct names:


mdadm --assemble --force /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm --assemble --force /dev/md1 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2
mdadm --assemble --force /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3


11) mount partitions for grub installation:
mount /dev/md1 /mnt
mount /dev/md0 /mnt/boot

# lsblk
```

sda       8:0    1 931.5G  0 disk   
&#9500;&#9472;sda1    8:1    1   953M  0 part   
&#9474; &#9492;&#9472;md0   9:0    0   952M  0 raid1  /mnt/boot
&#9500;&#9472;sda2    8:2    1 838.2G  0 part   
&#9474; &#9492;&#9472;md1   9:1    0   1.7T  0 raid10 /mnt
&#9492;&#9472;sda3    8:3    1  92.4G  0 part   
  &#9492;&#9472;md2   9:2    0  92.3G  0 raid1  
sdb       8:16   1 931.5G  0 disk   
&#9500;&#9472;sdb1    8:17   1   953M  0 part   
&#9474; &#9492;&#9472;md0   9:0    0   952M  0 raid1  /mnt/boot
&#9500;&#9472;sdb2    8:18   1 838.2G  0 part   
&#9474; &#9492;&#9472;md1   9:1    0   1.7T  0 raid10 /mnt
&#9492;&#9472;sdb3    8:19   1  92.4G  0 part   
  &#9492;&#9472;md2   9:2    0  92.3G  0 raid1  
sdc       8:32   1 931.5G  0 disk   
&#9500;&#9472;sdc1    8:33   1   953M  0 part   
&#9474; &#9492;&#9472;md0   9:0    0   952M  0 raid1  /mnt/boot
&#9500;&#9472;sdc2    8:34   1 838.2G  0 part   
&#9474; &#9492;&#9472;md1   9:1    0   1.7T  0 raid10 /mnt
&#9492;&#9472;sdc3    8:35   1  92.4G  0 part   
  &#9492;&#9472;md2   9:2    0  92.3G  0 raid1  
sdd       8:48   1 931.5G  0 disk   
&#9500;&#9472;sdd1    8:49   1   953M  0 part   
&#9474; &#9492;&#9472;md0   9:0    0   952M  0 raid1  /mnt/boot
&#9500;&#9472;sdd2    8:50   1 838.2G  0 part   
&#9474; &#9492;&#9472;md1   9:1    0   1.7T  0 raid10 /mnt
&#9492;&#9472;sdd3    8:51   1  92.4G  0 part   
  &#9492;&#9472;md2   9:2    0  92.3G  0 raid1

```


12)
root@ubuntu-server:~# mount --bind /dev /mnt/dev
root@ubuntu-server:~# mount --bind /dev/pts /mnt/dev/pts
root@ubuntu-server:~# mount --bind /proc /mnt/proc
root@ubuntu-server:~# mount --bind /sys /mnt/sys


13) chroot /mnt
14) install grub on each hdd:
grub-install /dev/sda
grub-install /dev/sdb
grub-install /dev/sdc
grub-install /dev/sdd

15) dpkg-reconfigure grub-pc        # select all /dev/sd*  to install ([COLOR=#ff0000]not md*[/COLOR])
16) reboot

[SIZE=5]Why standart setup ubuntu server 18.04.3 can`t do it?[/SIZE]

---

### Post by oldfred on 2019-12-24
As Darkod mentioned above you had gpt partitions and then needed either a 1MB unformatted partition with bios_grub flag for BIOS boot or an ESP - efi system partiiton for UEFI install.

If using MBR, you do not need those partitions, but MBR was created in mid 1980's so well known, but many kluges to keep it working with newer systems.  If using UEFI, gpt is strongly suggested.

When you converted after install, you reset all the UUIDs, so had to reinstall grub. Not sure if in some other places inside install is an old UUID that may cause issue. 
Better to have converted before install, if you really wanted MBR partitioning.

---

### Post by scorpik on 2019-12-26
Hi! Thank you for answering. The problem is in installer. It can`t install bootable system on soft raid1 disk. By default it uses GPT and there is no place were you can change it. In case of GPT  in Uefi, installer dont`accept to put ESP partition more than on 1 HDD. It is really big problem for server beacase if HDD with ESP partition will die, server will not boot. Please test it by yourself

---

### Post by CelticWarrior on 2019-12-27
> **scorpik said:**
> (...) installer dont`accept to put ESP partition more than on 1 HDD. It is really big problem for server beacase if HDD with ESP partition will die, server will not boot. Please test it by yourself

You can create other ESPs and copy the contents there but really systems should have only one as per design.
And if the drive fails the problem is the same in UEFI or Legacy.
And you can just add an ESP anyway to other RAID, softRAID drives or drives that are part of a LVM.

---

### Post by darkod on 2019-12-27
> **CelticWarrior said:**
> And if the drive fails the problem is the same in UEFI or Legacy.

Actually not. On the contrary...

Like you say, by design there is one ESP partition and if that disk fails it leaves your system unbootable.

On the other hand a legacy MBR boot together with mdadm sw raid offers redundancy because the bootloader files can be installed on each drive MBR, and the boot and OS files are protected by the mdadm raid redundancy. So as long as the array does not disassemble, losing one or multiple disks does not prevent the system to keep booting and working.

Going back to the thread topic I already explained what needed to be done but it wasn't followed. First of all, the OP never created the small 1MiB partition that needs to hold the Grub2 files in MBR boot with gpt disks. At least that info was not posted in the thread...

I had that setup for years and it surely works. The good thing with linux is that it doesn't mind using MBR boot with gpt disks. It does however need the 1MiB partition with bios_grub flag so that Grub2 installs correctly.

On the other hands there are motherboards that simply refuse to use MBR boot with gpt disks. But that is the board limitation, not ubuntu's.

For anyone else reaching this thread through a search engine, you don't have to do all the steps and conversions that the OP did. It is not the correct way and you can do this much simpler unless your HW is putting some limitations on you. But that is another topic.

---


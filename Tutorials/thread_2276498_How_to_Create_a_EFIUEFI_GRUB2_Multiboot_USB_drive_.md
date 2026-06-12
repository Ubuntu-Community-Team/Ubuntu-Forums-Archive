---
title: "How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images"
date: 2015-05-02
forum: Tutorials
---

### Post by sysmatck on 2015-05-02
For this Tutorial, there are some _Assumptions_: 


[LIST=1]
[*]You can format your usb drive (did you do a backup?)
[*]Your USB drive is the _/dev/sdb_ device (You can check yours with _sudo fdisk -l_ or using Gparted)
[*]Your USB drive will be mounted at _/mnt_
[*]You are using a Ubuntu distro (any Ubuntu flavour) - Could be a live session (LiveCD)
[*]You are logged with the first user (setted at installation or live session default)
[*]You are not afraid of Linux Command Interface
[/LIST]



**First Step: Format USB drive**

To create a EFI firmware compatible boot drive, you need a GPT partition table and at least one FAT32 partition. Do as follows...

> sudo apt-get install gdisk
sudo sgdisk --zap-all /dev/sdb

You probably need to remove and insert the USB drive again at this point for the kernel to update information about it...

> sudo sgdisk --new=1:0:0 --typecode=1:ef00 /dev/sdb
sudo mkfs.vfat -F32 -n GRUB2EFI /dev/sdb1

We are done with Step One, you can check modifications with _sudo parted -l_ or with Gparted.

**Second Step: ****Copy files and Set directory structure**

Let's mount the usb drive...
> sudo mount -t vfat /dev/sdb1 /mnt -o uid=1000,gid=1000,umask=022

To make life easier, I created a[ pack with all necessary files for you to modify as you need]("http://webativo.com/uploads/files/usb-pack_efi.zip"). If you don't trust my files, create yours using [this page as reference]("https://help.ubuntu.com/community/UEFIBooting"). Link to Download is: [http://webativo.com/uploads/files/usb-pack_efi.zip](http://webativo.com/uploads/files/usb-pack_efi.zip)

Extract the zip file and paste those inner files using Command Line Interface or a file manager you like.
> cd ~/Downloads/
unzip usb-pack_efi.zip
rsync -auv usb-pack_efi/ /mnt
 

The most important files are _bootia32.efi_ to boot on 32bit machines, _bootx64.efi_ to boot on 64bit machines and _grub.cfg_ to setup grub to load ISOs or chainload to other paths.

In the end, you might get a directory tree like this:
[IMG]http://webativo.com/galeria/1328201735/210.jpg[/IMG]


**Third Step: **[B]Install GRUB2 on the drive

[/B]> sudo grub-install --removable --boot-directory=/mnt/boot --efi-directory=/mnt/EFI/BOOT /dev/sdb

PS: Grub2 installation might throw some error messages, just ignore it.
PS: If you have problems to copy and paste content on /mnt, you can use sudo to do it

**Fourth Step: Setup ISOs to be loaded**

Put (copy) the .iso files you want to load in _/mnt/iso/_ and setup _grub.cfg_ like the existing examples...

Note that the most important variable to set is _isofile_. There is lots of examples on the web about how to configure grub2 menu. Use # to comment those lines you don't want to use, e.g. to hide a configuration of absent .iso at /iso.


**Last Step: Configure firmware and Test**

First and most important, deactivate secure boot on your computer's firmware. Search on the web if you don't know how.

To boot the USB drive you can set your machine firmware to search first for the USB device (boot order). Or you can choose what drive to boot as soon as you turn on your computer. Each manufacturer has its own keys to do it. Search for your machine's manual if needed.

---

### Post by sudodus on 2015-05-22
I tested your multiboot system in my Toshiba laptop, my only computer with UEFI.

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

It works well in UEFI mode :KS


Comments and tips:


1. If the user has two other mass storage devices connected, there is a risk that valuable data on

**/dev/sdb**

will be overwritten. Maybe the template should have

**/dev/sdx**

instead, and the user should change x to what it should be.


2. The grub-install command lacks a space between the boot directory and the device, should be

```
sudo grub-install --removable --boot-directory=/mnt/boot --efi-directory=/mnt/EFI/BOOT /dev/sdb 
```


 3. Maybe it would help to suggest an rsync command to copy the content of the zipfile to the pendrive, for example

extract files:

```
unzip usb-pack_efi
```

copy files:

```
sudo rsync -Havn usb-pack_efi/ /mnt
```

or an advanced unzip command line to do it directly.


4. I modified **grub.cfg** and could boot from the following iso files

[B]kubuntu-14.04.1-desktop-amd64.iso
ubuntu-14.04.2-desktop-amd64.iso
xubuntu-14.04.1-desktop-i386.iso
[/B]
Notice that I could also boot the 32-bit Xubuntu system in UEFI mode.


 5. But I could only boot in UEFI mode, not in BIOS mode alias CSM.

I did not even get to the grub menu in BIOS mode. Did I miss something? Have you managed to boot in BIOS mode with this system? Or is it an UEFI-only system?


 6. My computer has problems with the graphics when UEFI mode and rescue mode, I think it is because of **nomodeset** and I do not blame your multiboot system for it. I tried with and without **gfxpayload** without success.


 7. My modified **grub.cfg**:

```
submenu "Boot em HD " {
    #menuentry "Reboot em USB" {
    #    set root="(hd0)"
    #    chainloader +1
    #}
    menuentry "HD1 MBR" {
        set root="(hd1)"
        chainloader +1
    }
    menuentry "HD1 Particao 1" {
        set root="(hd1,msdos1)"
        chainloader +1
    }
    menuentry "HD1 Particao 2" {
        set root="(hd1,msdos2)"
        chainloader +1
    }
    menuentry "HD1 Particao 3" {
        set root="(hd1,msdos3)"
        chainloader +1
    }
    menuentry "HD2 MBR" {
        set root="(hd2)"
        chainloader +1
    }
    menuentry "HD2 Particao 1" {
        set root="(hd2,msdos1)"
        chainloader +1
    }
    menuentry "HD2 Particao 2" {
        set root="(hd2,msdos2)"
        chainloader +1
    }
    menuentry "HD2 Particao 3" {
        set root="(hd2,msdos3)"
        chainloader +1
    }
}

menuentry "Grub4dos - HBCD+"{
    # mudar (hd0,2) ou outros para diferentes computadores...

    setroot=(hd0,1)
    linux /boot/grub4dos/grub.exe
}

submenu "Teste de Memoria" {
    menuentry "memtest86+ 4.20" {
        linux16 /boot/memtest/memtest.bin
    }
    menuentry "memtest86+-5.01" {
        linux16 /boot/memtest/memtest86+-5.01.bin
    }
}


menuentry 'Kubuntu 14.04.1 amd64' {
    set isofile="/iso/kubuntu-14.04.1-desktop-amd64.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg noprompt noeject quiet splash --
    initrd (loop)/casper/initrd.lz
}

submenu "submenu Kubuntu 14.04.1" {
    menuentry 'Kubuntu 14.04.1 amd64 (failsafe)' {
        set isofile="/iso/kubuntu-14.04.1-desktop-amd64.iso"
        loopback loop $isofile
#        set gfxpayload=800x600x16,800x600
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg noeject nomodeset noapic --
        initrd (loop)/casper/initrd.lz
    }
}
menuentry 'Ubuntu 14.04.2 amd64' {
    set isofile="/iso/ubuntu-14.04.2-desktop-amd64.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg noprompt noeject quiet splash --
    initrd (loop)/casper/initrd.lz
}

submenu "submenu Ubuntu 14.04.2" {
    menuentry 'Ubuntu 14.04.2 amd64 (failsafe)' {
        set isofile="/iso/ubuntu-14.04.2-desktop-amd64.iso"
        loopback loop $isofile
#        set gfxpayload=800x600x16,800x600
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg noeject nomodeset noapic --
        initrd (loop)/casper/initrd.lz
    }
}

menuentry "Xubuntu 14.04.1 i386" {
        set isofile="/iso/xubuntu-14.04.1-desktop-i386.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noprompt noeject quiet splash --
    initrd (loop)/casper/initrd.lz
}

submenu "submenu Xubuntu 14.04.1 i386" {
    menuentry 'Xubuntu 14.04.1 i386 (failsafe)' {
        set isofile="/iso/xubuntu-14.04.1-desktop-i386.iso"
        loopback loop $isofile
#        set gfxpayload=800x600x16,800x600
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noeject nomodeset noapic --
        initrd (loop)/casper/initrd.lz
    }
}

```

---

### Post by sysmatck on 2015-05-22
Thankyou for testing sudodus! I'm glad it works for you (with needed ajustments)

1- I wrote an introduction for for this tutorial, I called it Assumption #2, where I observe this path issue. I prefer people to understand what they are doing, and sometimes is hard to figure exactly what users must type to get things done...

2- I just edited the post, and I corrected the command inserting the lacking space. I edited this post couple times, I suppose I removed accidentally on one of them...

3- Yes, I guess suggesting this commands is better (for the sake of completion), I'm glad you did it. I did not do it because I usually extract using GUI.

4- Nice! And good that you are also sharing the grub.cfg for others to use!

5- This is UEFI only system. But I guess it is possible to do a GRUB2 for both on a single drive. I also use something very similar to boot CSM using ext4 partitions. The downside of this (EFI) is that we must use a FAT32 partition to boot, so, if using a single FAT32 on a 32gb drive (just an example), you will be limited to 4gb max file size... I guess using two partitions will be a much more interesting solution for this "dual mode" boot device...

6- Hum... Research needed. There might have a kernel parameter that solves your problem...

Tnx! I will reply to this thread if I have some news or better ways to create this boot device (maybe on "dual mode"...)

---

### Post by oldfred on 2015-05-23
I noticed and reviewed your steps but have not tried it. 
I have UEFI install and just copied folders from my /EFI/Boot & /EFI/ubuntu onto flash drive.

With ISO I use grub2's loopmount, but invariable change to a newer ISO or add an ISO and forget to run sudo update-grub or edit grub.cfg.

I now use a configfile to call a text file in my ISO folder.

```
insmod part_gpt
insmod fat
set root='hd0,msdos1'

menuentry 'Live ISOs' {
configfile (hd0,1)/iso/livecdimage.cfg
} 
```

Then the livecdimage.cfg is just another boot stanza, but can be edited at will without updating grub.

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;


menuentry "gparted (Boot ISO Image via Grub2) " {
    insmod part_gpt
    set isofile="/iso/gparted-live-0.19.1-1-amd64.iso"
    loopback loop (hd0,1)$isofile
    linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
    initrd (loop)/live/initrd.img
}

menuentry "Mini Ubuntu-14.04.1-desktop" {
    set isofile="/iso/mini.iso"
    insmod part_gpt
    loopback loop (hd0,1)$isofile 
    linux (loop)/vmlinux boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/initrd.gz
}
```

---

### Post by sudodus on 2015-06-07
[SIZE=4]A USB multiboot pendrive that boots in UEFI and BIOS mode,
and that boots 32-bit and 64-bit operating systems.
[/SIZE]
I continued tweaking the USB pendrive according to [post #2]("http://ubuntuforums.org/showthread.php?t=2276498&p=13290123#post13290123").

[SIZE=4][SIZE=3]0. Perform the tasks in post #1 and #2 in UEFI mode[/SIZE]
[/SIZE]
I performed the tasks in post #1 and #2 in UEFI mode.
[SIZE=3]
[/SIZE][SIZE=4][SIZE=3]1. Boot another Ubuntu 14.04.2 LTS desktop (64-bit) system into BIOS mode[/SIZE]
[/SIZE]
Now I switched my computer (Toshiba laptop) to CSM alias BIOS mode and booted into a pendrive with Ubuntu 14.04.2 LTS desktop (64-bit). Boot another system, not the target pendrive.

[SIZE=4][SIZE=3]2. Install grub in BIOS mode[/SIZE]
[/SIZE]
I ran the following commands to install grub in BIOS mode. [COLOR=#0000ff]It complained but worked when forced, and did not overwrite the boot system for UEFI mode[/COLOR]. ***Check carefully the device id for your multiboot pendrive, so that you do not overwrite any valuable data!***

```
sudo lsblk -fm
```

```
sudo mount /dev/sd**[COLOR=#ff0000]x[/COLOR]**1 /mnt
sudo grub-install --force --removable --boot-directory=/mnt/boot /dev/sd**[COLOR=#ff0000]x[/COLOR]**
```

In my case **[COLOR=#ff0000]x[/COLOR]** was b, so I could use

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --force --removable --boot-directory=/mnt/boot /dev/sdb
```

[SIZE=4][SIZE=3]3. Enjoy the result :-)[/SIZE]
[/SIZE]
That's all. These simple operations managed to make the multiboot pendrive boot in both UEFI and BIOS mode. So now it is possible to use this pendrive to boot 'any computer' from an old 32-bit computer (in BIOS mode) to a new computer in BIOS mode as well as in UEFI mode. (But if the manufacturer has tweaked the UEFI system beyond the standard for UEFI, it might be hard to boot anything except Windows.)

I tested and can run Xubuntu (xubuntu-14.04.1-desktop-i386.iso) in these computers

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/), Intel i5, 64-bit: UEFI and BIOS, bought 2013
[http://www.asus.com/Motherboards/M2NVM_DVI/](http://www.asus.com/Motherboards/M2NVM_DVI/), AMD Athlon 64 X2, 64-bit: BIOS, bought 2008
[http://support.dell.com/support/edocs/systems/dim4600/en/4600i/sm/specs.htm](http://support.dell.com/support/edocs/systems/dim4600/en/4600i/sm/specs.htm), Pentium 4, 32-bit: BIOS, bought 2004

We know since before how to make it boot in UEFI mode. The following commands and output from the commands were run in a Dell Dimension 4600 with a Pentium 4 processor, which is a 32-bit system, that runs in BIOS mode.

```
xubuntu@xubuntu:~$ sudo lshw -class cpu
  *-cpu                   
       description: CPU
       [COLOR=#0000ff]product: Intel(R) Pentium(R) 4 CPU 2.80GHz[/COLOR]
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       version: 15.2.9
       slot: Microprocessor
       size: 2800MHz
       capacity: 3200MHz
       [COLOR=#0000ff]width: 32 bits[/COLOR]
       clock: 533MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
       configuration: id=0
xubuntu@xubuntu:~$ uname -a
[COLOR=#0000ff]Linux xubuntu 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux[/COLOR]
xubuntu@xubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
xubuntu@xubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL                    MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                 sda    111.8G root  disk  brw-rw----
&#9500;&#9472;sda1                                              &#9500;&#9472;sda1     1K root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs     winxp                               &#9500;&#9472;sda2  79.8G root  disk  brw-rw----
&#9500;&#9472;sda5 swap                              [SWAP]     &#9500;&#9472;sda5     4G root  disk  brw-rw----
&#9492;&#9472;sda6 ext4     ToriOS-i386                         &#9492;&#9472;sda6    28G root  disk  brw-rw----
sdb                                                 sdb    111.8G root  disk  brw-rw----
&#9492;&#9472;sdb1 ntfs     Backup                              &#9492;&#9472;sdb1 111.8G root  disk  brw-rw----
sdc                                                 sdc     14.6G root  disk  brw-rw----
&#9492;&#9472;sdc1 vfat     GRUB2EFI                 /isodevice &#9492;&#9472;sdc1  14.6G root  disk  brw-rw----
sr0                                                 sr0     1024M root  cdrom brw-rw----
sr1                                                 sr1     1024M root  cdrom brw-rw----
loop0  iso9660  [COLOR=#0000ff]Xubuntu 14.04.1 LTS i386[/COLOR] /cdrom     loop0    916M root  disk  brw-rw----
loop1  squashfs                          /rofs      loop1  883.8M root  disk  brw-rw----
xubuntu@xubuntu:~$ ls -l /isodevice/*
/isodevice/boot:
total 24
drwxr-xr-x 5 root root 8192 May 22 11:16 grub
drwxr-xr-x 2 root root 8192 May  2 17:46 grub4dos
drwxr-xr-x 2 root root 8192 May  2 17:46 memtest

/isodevice/EFI:
total 8
drwxr-xr-x 2 root root 8192 May  2 17:48 BOOT

/isodevice/iso:
total 3011408
-rwxr-xr-x 1 root root 1078804480 May 22 10:35 kubuntu-14.04.1-desktop-amd64.iso
-rwxr-xr-x 1 root root 1044381696 May 22 10:34 ubuntu-14.04.2-desktop-amd64.iso
-rwxr-xr-x 1 root root  960495616 May 22 10:35 xubuntu-14.04.1-desktop-i386.iso
xubuntu@xubuntu:~$ df 
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow              772216   98480    673736  13% /
udev              761528       4    761524   1% /dev
tmpfs             154444    1068    153376   1% /run
/dev/sdc1       15309832 3019472  12290360  20% /isodevice
/dev/loop0        937984  937984         0 100% /cdrom
/dev/loop1        905088  905088         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs             772216       8    772208   1% /tmp
none                5120       0      5120   0% /run/lock
none              772216      80    772136   1% /run/shm
none              102400      24    102376   1% /run/user
xubuntu@xubuntu:~$ find /isodevice/ -ls|grep -v /isodevice/boot/grub/i386-pc/
     1    8 drwxr-xr-x   5 root     root         8192 Jan  1  1970 /isodevice/
     7    8 drwxr-xr-x   5 root     root         8192 May  2 17:46 /isodevice/boot
    12    8 drwxr-xr-x   5 root     root         8192 May 22 11:16 /isodevice/boot/grub
    28   24 drwxr-xr-x   2 root     root        24576 Jun  7 05:13 /isodevice/boot/grub/i386-pc
   300    8 drwxr-xr-x   2 root     root         8192 Jun  7 05:13 /isodevice/boot/grub/locale
  1439    8 -rwxr-xr-x   1 root     root         1032 Jun  7 05:13 /isodevice/boot/grub/locale/en_AU.mo
  1440    8 -rwxr-xr-x   1 root     root          587 Jun  7 05:13 /isodevice/boot/grub/locale/en_CA.mo
  1441    8 -rwxr-xr-x   1 root     root         4464 Jun  7 05:13 /isodevice/boot/grub/locale/en_GB.mo
  1442  128 -rwxr-xr-x   1 root     root       130811 Jun  7 05:13 /isodevice/boot/grub/locale/es.mo
  1443   32 -rwxr-xr-x   1 root     root        31315 Jun  7 05:13 /isodevice/boot/grub/locale/zh_CN.mo
   306    8 drwxr-xr-x   2 root     root         8192 May 22 10:27 /isodevice/boot/grub/fonts
  1445 2352 -rwxr-xr-x   1 root     root      2405285 Jun  7 05:13 /isodevice/boot/grub/fonts/unicode.pf2
  1446    8 -rwxr-xr-x   1 root     root         2827 May 22 11:24 /isodevice/boot/grub/grub.cfg
  1447    8 -rwxr-xr-x   1 root     root         1024 May 22 10:27 /isodevice/boot/grub/grubenv
  1448    8 -rwxr-xr-x   1 root     root         2125 Jan  6 16:10 /isodevice/boot/grub/menu.lst
  1449    8 -rwxr-xr-x   1 root     root         3894 May 22 11:10 /isodevice/boot/grub/grub.cfg~
    13    8 drwxr-xr-x   2 root     root         8192 May  2 17:46 /isodevice/boot/grub4dos
  1452  232 -rwxr-xr-x   1 root     root       234697 Mar 31  2009 /isodevice/boot/grub4dos/grub.exe
  1453  216 -rwxr-xr-x   1 root     root       217769 Mar 31  2009 /isodevice/boot/grub4dos/g2ldr
    14    8 drwxr-xr-x   2 root     root         8192 May  2 17:46 /isodevice/boot/memtest
  1456  152 -rwxr-xr-x   1 root     root       150024 Aug 23  2013 /isodevice/boot/memtest/memtest86+-5.01.bin
  1457  168 -rwxr-xr-x   1 root     root       164504 Jan 23  2011 /isodevice/boot/memtest/memtest.bin
     8    8 drwxr-xr-x   3 root     root         8192 May  2 17:48 /isodevice/EFI
    16    8 drwxr-xr-x   2 root     root         8192 May  2 17:48 /isodevice/EFI/BOOT
  1460  608 -rwxr-xr-x   1 root     root       621056 Apr 28 13:51 [COLOR=#0000ff]/isodevice/EFI/BOOT/bootia32.efi[/COLOR]
  1461  904 -rwxr-xr-x   1 root     root       920064 Apr 29 20:38 [COLOR=#0000ff]/isodevice/EFI/BOOT/bootx64.efi[/COLOR]
     3    8 drwxr-xr-x   2 root     root         8192 May 22 10:38 /isodevice/iso
    19 1053520 -rwxr-xr-x   1 root     root     1078804480 May 22 10:35 /isodevice/iso/kubuntu-14.04.1-desktop-amd64.iso
    20 1019904 -rwxr-xr-x   1 root     root     1044381696 May 22 10:34 /isodevice/iso/ubuntu-14.04.2-desktop-amd64.iso
     4 937984 -rwxr-xr-x   1 root     root     960495616 May 22 10:35 /isodevice/iso/xubuntu-14.04.1-desktop-i386.iso

```

I think that [COLOR=#0000ff]/isodevice/EFI/BOOT/bootia32.efi[/COLOR] makes it possible to boot 32-bit systems while [COLOR=#0000ff]/isodevice/EFI/BOOT/bootx64.efi[/COLOR] makes it possible to boot 64-bit systems (in UEFI mode). Please correct me if I am wrong.
[SIZE=3]
[/SIZE][SIZE=4][SIZE=3]4. Welcome to test this multiboot system[/SIZE]
[/SIZE]
We need long time testing by several users to find out if this  system is stable, that it continues working in the long run.

Follow the instructions in this thread if you want to learn how to make a single boot or multiboot system for UEFI & BIOS, 32-bit & 64 bit systems. But if you want to make such a pendrive quickly, with Lubuntu 14.04.2 desktop 32-bit ISO file, you can get a compressed image file and install it according to the following link,

[A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523")

---

### Post by sysmatck on 2015-06-10
Hello Nio,

I did as you instructed and it works for me too! I tested on my Asus X54C, activating and deactivating the UEFI boot mode. I can boot on both modes... I will test this on old machines that has no UEFI and I will report results here...

I guess it is possible to force grub2 to install on i386 mode, or something like this on a UEFI booted system, so we could skip step 1 by adding some additional parameters to installation command. I need to check this out!

---

### Post by sysmatck on 2015-06-10
The additional grub2 possible parameters are:** --target=i386-pc** or [B]--target=x86_64-efi

[/B]I will try this again later. Let me test the drive as it is on old hardware first...

---

### Post by sudodus on 2015-06-10
As far as I can tell, this provides a simple method to create 'One pendrive for all computers', a truly portable pendrive, and with persistence you can carry your computer environment (added software, tweaks and personal files) in your pocket :-)

---

### Post by sysmatck on 2015-06-10
Ok, I just tested on some other machines... Works like a charm!

BIOS Motherboards:
ASRock G31M-VS
MSI G31M3-V2
Asus P6KPL-AM
Foxconn M61PMV
ASRock 980DE3/U3S3

---

### Post by sudodus on 2015-06-10
I made the USB boot drive and tested it in my Toshiba with UEFI and BIOS. I tested it in my daughter's HP ProBook 6450b (also with UEFI and BIOS)

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02218879](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02218879)

And I tested it in older computers with only BIOS, even an old Dell with Pentium 4 (32-bit). The same pendrive with a Lubuntu 32-bit iso file works in all the computers and modes (BIOS and UEFI) where I have tested it. 

- There is a hardware limit. The computer may be too weak to boot a current version of Lubuntu, or there is some hardware, for example graphics chip, where the available drivers do not work. But then it is possible to include iso files for other linux distros. See the following list that describes how to configure grub for several distros

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

- Another limit is where the system is so locked down by a non-standard UEFI system, that nothing but Windows works.

---

### Post by sudodus on 2015-06-11
[SIZE=4]Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers[/SIZE]

I made a system, where a shell-script helps performing the operations, that are described in this thread. I found that it is possible to do everything in either UEFI mode or BIOS mode, the two grub installations are simply done with two different command lines.

```
$ [COLOR=#0000cd]grep grub-install mk-grub-n-iso [/COLOR]
grub-install --force --removable --no-floppy --boot-directory=/mnt/target/boot --efi-directory=/mnt/target/EFI/BOOT "$2"
grub-install --force --removable --no-floppy --boot-directory=/mnt/target/boot "$2"
```

This works in an Ubuntu family operating system of ***version 14.04 LTS or newer***. (It is possible to use Ubuntu 12.04 LTS too, but it has an older version  of grub, and I have not found a method to make pendrives that boot in both UEFI and BIOS mode.)

This link describes how to install and use this system,

[Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

---

### Post by Starbeamrainbowlab on 2015-07-20
Is it possible to do this and allow windows to mount the partition?

Currently if I plug the flash drive into windows I get an "EFI System Partition" which I can't mount under windows 7.

If not, can I create a second "main" parition to store data & ISOs on?

---

### Post by sudodus on 2015-07-20
The EFI partition must have a FAT file system. Linux works best with linux file systems but Windows cannot mount partitions with linux file systems. So in order for Windows to mount them, you need FAT or NTFS file systems. If you want access the ISO files from both linux and Windows, I would recommend using the FAT32 file system (for the partition where you keep the ISO files).

Yes, you can create a second (or third etc) partition if you wish, but avoid storing the ISO files in two places.

*Edit:* There is one thing I should add - At least some versions of Windows have problems to mount more than one partition on USB drives. (I don't know if it affects all versions of Windows.) It wants to open the first one, but I am not sure what happens if the first partition is recognized as an EFI partition. I just checked: Windows 7 will only recognize the first partition (the EFI partition). Some other Windows version might mount the second partition, if it has a Windows file system. But to be sure, make a big first partition with the FAT32 file system, and keep the ISO files there, if you want them to be available from Windows.

---

### Post by Starbeamrainbowlab on 2015-07-20
Update:

By changing the partition to "0700" (A basic data partition) I can boot using UEFI + BIOS, but I can also see it in Windows.

---

### Post by sysmatck on 2015-12-29
> **Starbeamrainbowlab said:**
> Update:

By changing the partition to "0700" (A basic data partition) I can boot using UEFI + BIOS, but I can also see it in Windows.

Yes, I did some testing. I can also boot using 0700 as partition type. When using 1:ef00 the partition will not automount on Linux. But with 0700 it is mounted automatically. I supose this is an interesting information, if you want a partition to automount, maybe 0700 is a better option. If this will be just a boot partition, you might prefer not to mount...

---

### Post by sysmatck on 2015-12-29
Hello Again!

I just wanted to report that I'm being able to boot with UEFI/BIOS mode with a dual partition USB stick. The first partition is EF00 and the second one EXT4(8300). The boot and EFI directories were stored on the first partition e.g. /dev/sdb1 and the iso directory is located on EXT4 partition e.g. /dev/sdb2

I can boot with GRUB2 using the following code

```

menuentry 'Lubuntu 14.04 i386' {
		set isofile="/iso/lubuntu-14.04.2-desktop-i386.iso"
		**loopback loop (hd0,2)**$isofile
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noprompt noeject quiet splash --
		initrd (loop)/casper/initrd.lz
	}

```

Note the difference on "Loopback" line... This is it!

---

### Post by sudodus on 2015-12-29
Yes, it works :-)

I've done something similar as described in post #11 (and the link from there)

and also at the following link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by Elvizk on 2016-03-13
I tried this method but I cant able to boot Hiren boot iso.

[[img]http://s19.postimg.org/kvnw14zvj/image.png[/img]](http://postimg.org/image/kvnw14zvj/) [[img]http://s19.postimg.org/noh3l607z/image.png[/img]](http://postimg.org/image/noh3l607z/)

---

### Post by michael300 on 2016-04-01
Excellent write-up, very helpful. I've been looking for a solution to be able to have a multi-boot capable to run on EFI systems and legacy. I was wondering if it would be possible to boot a version of windows with this setup? I was able to get a multi-boot system through yumi that allowed me to chainload windows as well, however, yumi doesn't support efi/uefi systems... I'll do some tinkering to see if I can get it to work, but I was hoping somebody could point me in the right direction. Thanks!

---

### Post by oldfred on 2016-04-02
Windows will not boot from USB devices.

You can possibly create installer or repair disk with Windows but have to install it first then reconfigure with grub & ISO files.
I did create a BIOS Windows 7 repair flash drive. But it used so little space that I then decided to try to add grub & ISOs.
The main issue is the grub creates a /boot folder & Windows has a /Boot folder. In Linux case matter, but in Windows is does not. So you must have all files in same /Boot or /boot folder, but not both as Windows will not work with two /boot folders.

---

### Post by Sbininit on 2016-05-08
> **sysmatck said:**
> For this Tutorial, there are some _Assumptions_:    
[LIST=1] 
[*]You can format your usb drive (did you do a backup?) 
[*]Your USB drive is the _/dev/sdb_ device (You can check yours with _sudo fdisk -l_ or using Gparted) 
[*]Your USB drive will be mounted at _/mnt_ 
[*]You are using a Ubuntu distro (any Ubuntu flavour) - Could be a live session (LiveCD) 
[*]You are logged with the first user (setted at installation or live session default) 
[*]You are not afraid of Linux Command Interface 
[/LIST]
    **First Step: Format USB drive** computer. Each manufacturer has its own keys to do it. Search for your machine's manual if needed.    Hey when I do gdisk zap all,  I get an error number 2. Did not wipe out MBR. I went on with the tutorial to the letter and my USB wil not boot.  It pauses never showingthe USB grub.cfg then falls back to the main PC grub2 menu.  Any ideas?

---

### Post by Sbininit on 2016-05-08
> **sysmatck said:**
> For this Tutorial, there are some _Assumptions_: 


[LIST=1]
[*]You can format your usb drive (did you do a backup?) 
[*]Your USB drive is the _/dev/sdb_ device (You can check yours with _sudo fdisk -l_ or using Gparted) 
[*]Your USB drive will be mounted at _/mnt_ 
[*]You are using a Ubuntu distro (any Ubuntu flavour) - Could be a live session (LiveCD) 
[*]You are logged with the first user (setted at installation or live session default) 
[*]You are not afraid of Linux Command Interface 
[/LIST]



**First Step: Format USB drive**
computer. Each manufacturer has its own keys to do it. Search for your machine's manual if needed.


 Hey when I do gdisk zap all,  I get an error number 2. Did not wipe out MBR. I went on with the tutorial to the letter and my USB wil not boot.
 It pauses never showing the USB grub.cfg then falls back to the main PC grub2 menu.

Any ideas?

---

### Post by Sbininit on 2016-05-09
Hey Sysmatck! I have installed the bootlaoder to a new USB just as you have described here but cant boot to a grub menu in bios.
I did get an error messsage after gdisk zap all had run as follows : Warning MBR was not removed error 2.
Any suggestions?

---

### Post by sysmatck on 2016-05-09
> **Sbininit said:**
> Hey Sysmatck! I have installed the bootlaoder to a new USB just as you have described here but cant boot to a grub menu in bios.
I did get an error messsage after gdisk zap all had run as follows : Warning MBR was not removed error 2.
Any suggestions?

Yes there is something you can try. Using Gparted, go to menu "Devices" -> "Create partition Table". Choose GPT option. This is it, but remember, this will make empty everything on your drive... Always backup!

If you want to try any different command or understand better gdisk, follow [this link]("http://www.rodsbooks.com/gdisk/wipegpt.html")

---

### Post by Sbininit on 2016-05-09
> **sysmatck said:**
> Yes there is something you can try. Using Gparted, go to menu "Devices" -> "Create partition Table". Choose GPT option. This is it, but remember, this will make empty everything on your drive... Always backup!

If you want to try any different command or understand better gdisk, follow [this link]("http://www.rodsbooks.com/gdisk/wipegpt.html")

When I go through the instructions at the front of this thread and look in hexedit /dev/sdc1 I see this drive is not bootable.
Is that the way it should read?

I have no UEFI machine to boot it in now that I know of unless one of the lap tops around here happens to be so.

---

### Post by Sbininit on 2016-05-11
Testdisk fixed my MBR after everything else failed.

---

### Post by QDR06VV9 on 2016-05-11
> **Sbininit said:**
> Testdisk fixed my MBR after everything else failed.
Good Job and thanks for posting your solution.
Regards

---

### Post by Sbininit on 2016-05-24
Will older BIOS systems boot an EFI fromatted linux flash drive that boots up just like a live CD?

---

### Post by oldfred on 2016-05-24
The standard Ubuntu installer is both BIOS & UEFI.

But old BIOS systems will not boot UEFI only configured flash drive.

I normally create separate flash drives for BIOS & UEFI. 
But some have configured with both copies of grub, so you can boot both ways.

       Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode 16.04
[http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13468260#post13468260)
Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)

---

### Post by Sbininit on 2016-05-25
I found a way to get my GPT partitioned Tails USB  to boot on my older BIOS system by raising its boot flag which is not set by default. Getting that  OS to work with persistence has plagued me for a week now. It has to have been the most aggravating linux OS I have ever seen.

sudo parted /dev/sdc1
and type     disk_toggle pmbr_boot 
exit out and reboot, BAM done! Awsome! Why couldn't I have learned that a week ago?


Come to find out after much searching and  reading the bash scripts info .... none of the tails installers or create persistent scripts will run if they find the / partition is not GPT. The scripts error out immeditely and continues to boot without option for persistence.

The live-persistent script in the boot menu will not load if it finds no GPT partition. If that doesn't load then the Tails Greeter never offers to make a persistent storage device. This was a problem for me because I had not been able to make a GPT partition boot in my machine. 

I did get Tails USB working with a fat32 partition on sdc1 for my boot and grub2 folders.
sdc2 was ext3 for the iso or mounted and copied files systems via rsync.
Either way I could boot it but never was offered the persistence because the scripts will not run unless there is a GPT partiiton present named Tails.


 I never could make the USB boot in this tutorial in my computer so I'm gonna go back and try this with it as well.

---

### Post by sudodus on 2016-05-25
I think Tails is made to leave no traces, so it is the very opposite of a persistent live system.

---

### Post by Sbininit on 2016-05-25
> **sudodus said:**
> I think Tails is made to leave no traces, so it is the very opposite of a persistent live system.

Yes lots of folks like to use Tails to do their banking and stuff to avoid identity theft I suppose. 

I wanted to at least be able to save my background image, black theme on terminal, and mount folders and save installed programs.

It would be nice to have a script that would load all the stuff but thats a bit over my head currently.

 Then there'd be no need for persistence at all. A script to do all the above mentioned and  create mount points media/sda1 thru 10 /media/sdb1 thru 10, /media/sdc1 thru -10, media/sdg1-10 , /media/test  would be awesome! With that booting the iso would be cool. Plus an fstab builder, I almost forgot that one .

---

### Post by dosergio on 2016-12-30
this formatting results in a problem, some space must be left in disk partition (usually 1M) or grub complains

---

### Post by paulr-ta on 2017-05-05
For me to get this to work in Lubuntu 17.04 amd64, I had to install grub-efi-ia32 and grub-efi-ia32-bin, which removed grub-efi, grub-efi-amd64, and grub-efi-amd64-signed.  Yay! I finally got it!  lol :^)  Beautiful!  Thanks!  (maybe I should try to boot off of the hard drive before I post this... lol)

---

### Post by paulr-ta on 2017-05-05
Here are the steps I took to get this to work under Lubuntu 17.04 amd64:

sudo -i

# This will remove grub-efi, grub-efi-amd64, and grub-efi-amd64-signed, but didn't cause me any problems
apt-get install grub-efi-ia32

apt-get install gdisk

sgdisk --zap-all /dev/sd{USB_DEVICE}   # Ex. /dev/sdb

sgdisk --new=1:0:0 --typecode=1:ef00 /dev/sd{USB_DEVICE} # Ex. /dev/sdb

mkfs.vfat -F32 -n GRUB2EFI /dev/sd{USB_DEVICE}1  # Ex. /dev/sdb1

mount -t vfat /dev/sd{USB_DEVICE}1 /mnt  # Ex. /dev/sdb1

grub-install --removable --boot-directory=/mnt/boot --efi-directory=/mnt /dev/sd{USB_DEVICE}  # Ex. /dev/sdb

cd /mnt

mkdir iso

cd iso

cp -p /home/user/iso/lubuntu-17.04-desktop-amd64.iso .
cp -p /home/user/iso/zesty-custom.iso .

cd ../boot/grub/

vi grub.cfg
---
insmod part_gpt
insmod loopback
insmod all_video

menuentry 'Lubuntu 17.04 amd64 - custom' {
    set isofile="/iso/zesty-custom.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile liveimg noprompt noeject quiet splash --
    initrd (loop)/casper/initrd.lz
}

menuentry 'Lubuntu 17.04 amd64' {
    set isofile="/iso/lubuntu-17.04-desktop-amd64.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg noprompt noeject quiet splash --
    initrd (loop)/casper/initrd.lz
}
---

---

### Post by karthikeyanr2 on 2017-08-26
Hi @sysmatck, Very good thread. I was able to create a bootable usb and could test booting isos from BIOS as well as EFI from grub. But when i try to use grub4dos, it is not loading or finding the menu.lst. I do have the following in my grub.cfg

 set root=(hd0,1)
 linux /boot/grub4dos/grub.exe

It loads the grub4dos and shows the embedded menu ([http://diddy.boot-land.net/grub4dos/files/embedded.htm](http://diddy.boot-land.net/grub4dos/files/embedded.htm)) instead of loading the menu.lst file. I tried to resolve by searching through the forums  but no resolution yet. 

When i boot the USB in BIOS mode, the grub4dos command line gives the following error
grub>root
(hd0,0): Filesystem type unknown. partition type  0xEE

When i boot the USB in EFI mode
grub>root
Error 21: Selected disk does not exist

I tried to find a solution for this but after much trying i am writing here to check if anybody had the same issue and found a solution. Please let me know.

Thanks
Karthikeyan

---

### Post by C.S.Cameron on 2017-10-01
Quick Method

Make boot drive using mkusb with defaults.
Make iso folder on usbdata partition, add iso files to iso folder.
Mount usbboot partition and edit /boot/grub/grub.cfg to add menuentries similar to Sudodus's post 2 above, for each ISO file, however add:
```
set root=(hd0,1)
``` if not already there.


If individual persistence is required for each OS, casper-rw and home-rw files can be added to an unique named folder for each OS on a new FAT32 partition, then add:
```
persistent persistent-path=/<unique folder name>
```
to the grub.cfg menuentry.

---

### Post by sudodus on 2017-10-01
@C.S.Cameron,

Interesting method :-)

I think you might not use all defaults, but maybe modify the percentages of the drive for persistence and usbdata to match what you intend to do, how many iso files that you want to add, and how much persistence you want for each of them (if any).

---

### Post by C.S.Cameron on 2017-10-01
That is another nice thing about mkusb, you can modify the partitions without corrupting the drive, unlike Rufus or Startup Disk Creator.

---

### Post by C.S.Cameron on 2017-10-01
With the price of large capacity flash drives falling, it makes sense to do Full installs to a multiboot drive.
At least if stable and secure install is required.

With a GPT partition table create multiple ext4 partitions of at least 6GB.
Boot the installer USB, plug in the target USB.
At installation type select "Something else".
Choose sdc1 for "/".
Install grub to the root of the target device.

Repeat for sdc2, sdc3... for multiple OS.

A NTFS partition can be created for additional ISO's to Live boot or persistent boot, adding their menuentries to grub.cfg

---

### Post by sudodus on 2017-10-02
I agree with C.S.Cameron,

It is a good idea to do full installs to a multi boot USB drive. If you disconnect or unplug the internal drive before you start installing, the procedure will be like it would be, when you create a dual boot or multi boot system in an internal drive. (After installation you can plug the intermal drive back into the computer.)

See the following links and links from them,

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[askubuntu.com/questions/786986/boot-ubuntu-from-external-drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

[Booting USB drives with grub2 and iso files 'grub-n-iso'](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27)

---

### Post by karthikeyanr2 on 2018-06-21
After reading and understanding, I realized grub4dos cannot be used with UEFI mode. grub4dos booting in BIOS mode was not working for me because i used 0.4.4 version and once i found the latest version 0.4.6a, it started loading the menu.lst file.

---

### Post by C.S.Cameron on 2018-06-23
With YUMI UEFI Beta they have abandoned grub4dos, everything is FAT, persistence is again limited to 4GB.

I'm still wondering if there is any advantage for me to go with UEFI rather than BIOS?

---

### Post by oldfred on 2018-06-23
All my recent flash drives have been larger, so gpt partitioned and full installs.

Before I converted to UEFI, I did convert drives to gpt and included both the ESP for future UEFI boot and bios_grub for BIOS boot. Now all flash drives are UEFI, but may still have a bios_grub, just in case I want to experiment with BIOS again.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by sudodus on 2018-06-23
The default for mkusb persistent live drives is GPT, but there is an option to select an MSDOS partition table for computers, that need it, for example middle-aged HP computers. My son has an HP Elitebook 8560p, that won't boot from a USB drive via grub from GPT, but works well with the old style MSDOS partition table.

This computer has an old and primitive UEFI system, so we boot it in BIOS mode (including Windows 10 which is upgraded from Windows 7 and backed up with a Clonezilla image).

---

### Post by zazzlv7 on 2018-08-22
thanks for this great tutorial!
Helped me a lot!

---


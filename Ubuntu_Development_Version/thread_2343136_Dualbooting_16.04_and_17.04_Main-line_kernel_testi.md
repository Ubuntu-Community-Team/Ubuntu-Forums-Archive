---
title: "Dualbooting 16.04 and 17.04 Main-line kernel testing"
date: 2016-11-13
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-11-13
I have installed 17.04 alongside 16.04.
When I installed 17.04 it Installed grub and does not add 16.04 (even with manual update-grub2). I had to manually restore the /boot/efi/EFI folder to boot back in to 16.04.

I then did update-grub2 from 16.04 which found 17,04 and added a boot entry.
Then I purged (removed) grub from 17.04.

I was asked to install the latest Kernel from the main-line kernel ppa and report back. But when I install Kernels from that ppa there's no grub entry for it. There is however if the kernel is updated via apt.

My method of Installing is 

```
dpkg -i linux-header*
dpkg -i linux-image*

```
The kernel installed without error.

```
anders@lenox:~$ sudo ls -l /media/testing/boot/total 113256
-rw-r--r-- 1 root root  1406981 okt.  20 21:09 abi-4.8.0-27-generic
-rw-r--r-- 1 root root  1390740 okt.  30 00:44 abi-4.9.0-040900rc3-generic
-rw-r--r-- 1 root root   199472 okt.  20 21:09 config-4.8.0-27-generic
-rw-r--r-- 1 root root   201020 okt.  30 00:44 config-4.9.0-040900rc3-generic
drwxr-xr-x 2 root root     4096 nov.  13 18:08 efi
drwxr-xr-x 5 root root     4096 nov.  13 18:32 grub
-rw-r--r-- 1 root root 41190854 nov.  13 19:52 initrd.img-4.8.0-27-generic
-rw-r--r-- 1 root root 40423554 nov.  13 20:25 initrd.img-4.9.0-040900rc3-generic
-rw-r--r-- 1 root root   182704 jan.  28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 jan.  28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 jan.  28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  4059493 okt.  20 21:09 System.map-4.8.0-27-generic
-rw------- 1 root root  4073772 okt.  30 00:44 System.map-4.9.0-040900rc3-generic
-rw------- 1 root root  7477024 okt.  20 21:09 vmlinuz-4.8.0-27-generic
-rw------- 1 root root  7478936 nov.  13 18:11 vmlinuz-4.8.0-27-generic.efi.signed
-rw------- 1 root root  7477024 okt.  30 00:44 vmlinuz-4.9.0-040900rc3-generic
anders@lenox:~$ 

```

A manual update-grub2 from 16.04 did not give any result as to show the new 4.9 kernel.

Any tips is greatly appreciated! Maybe there's a better way to dualboot?

---

### Post by dino99 on 2016-11-14
In case of multiboot, one of the installed grub is the 'master' (usually the latest installed/upgraded) and then the other(s) have to be ran to be updated. Usually the bootloaders are installed in the same place (/dev/sda) and so replaced with each new install/upgrade.

---

### Post by izznogooood on 2016-11-14
Exactly.

My problem is: 16.04 does not find the latest kernel of 17.04 and 17.04 does not find 16.10 at all (With grub update). I am sure I have many kernels to test until this bug is fixed and would like a better solution than to re-write my efi dir every time...

---

### Post by jerrylamos on 2016-11-14
?
I'm quadruple booted here, trusty, xenial, zesty on a USB hard drive and Win10 on the built in drive.
Xenial was installed oldest, then zesty, and then trusty i386 for Picasa.  The ubuntu photo applications can't touch the variety of functions in Picasa. Even Google replaced Picasa with a app that doesn't match picasa functions.
I've installed many ubuntu's on the USB and don't have a clue what grub is booting.  I do sudo update-grub on each of the 3 ubuntu's after a new install.
Now I've had some problems in the recent past but not today....

The Win 10 is for a particular application my wife uses in support of one of her web sites.  The application won't run on ubuntu. 
Also, when I dump the Acer 5253 it will have Win10 for the next user.

---

### Post by izznogooood on 2016-11-17
I'm giving this a bump :)

---

### Post by jerrylamos on 2016-11-19
Not quite clear to me what steps you use after an install  Please be clear what you do.
```

1. finish install
2. reboot
3. sudo update-grub                        (check the screen as the command ececutes, as update-grub processes should mention all the bootable partitions even Windows)
4. sudo grub-install /dev/sdb           (whichever disk boots first, /dev/sda /dev/sdc/ ..,)
5. boot
6. first screen up should display all the bootable partitions, even Windows
7 move cursor to the desired partition with up and down arrows on the keyboard.  
    (not much time to do this before boot continues anyway.)
8. Do F10 or whatever the screen says to do to start 
    (not much time before boot continues anyway.)
```

Note there is a brief time to "e" edit an entry, then F10 to continue boot
    (not much time before boot continues anyway.)[/code]

My setups are a bit more complex with added entries to boot an .iso from the hard disk with a file 40_custom copied into /etc/grub.d before step 3. above.
No usb stick required just the .iso file as zsync'd from cdimages
Careful, can screw up boot here requiring a boot from something else even the .iso USB stick to edit mistakes

---

### Post by MikeMecanic on 2016-11-20
If this can help. We don’t know about your first installation?
 
 -First fresh install:  Erase disk with default installation YY (entire disk)
 -Second fresh install, 17.04 alongside 16.10 default installation (auto-resize)
 ```
$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
 NAME   FSTYPE   SIZE MOUNTPOINT LABEL
 sda           931.5G             
 &#9500;&#9472;sda1 vfat     512M /boot/efi   
 &#9500;&#9472;sda2 ext4   467.8G                     [COLOR=#ff3333][FONT=Liberation Serif]**&#8592;**[/FONT][/COLOR][COLOR=#ff3333]**YY**[/COLOR]
 &#9500;&#9472;sda3 swap     7.5G [SWAP]      
 &#9492;&#9472;sda4 ext4   455.8G /                   [COLOR=#ff3333][FONT=Liberation Serif]**&#8592;**[/FONT][/COLOR][COLOR=#ff3333]**ZZ   **[/COLOR] 
 sr0            1024M 

``` 
 
 ISO images were made under windows 10 with the help of Rufus 2.11 (UEFI boot only).
 *UEFI enable, boot secure enable during installation, custom keys enable, don't clear efi boot, fast boot disable, legacy disable. * 
 *@ Jerry Lamos :)*
 
 For YY
 ```
$  sudo update-grub  
  Generating grub configuration file ...
 Found linux image: /boot/vmlinuz-4.9.0-040900rc6-generic
 Found initrd image: /boot/initrd.img-4.9.0-040900rc6-generic
 Found linux image: /boot/vmlinuz-4.8.0-28-generic
 Found initrd image: /boot/initrd.img-4.8.0-28-generic
 [COLOR=#ff3333]Found Ubuntu Zesty Zapus (development branch) (17.04) on /dev/sda2[/COLOR]
 Adding boot menu entry for EFI firmware configuration
 done
 ~$ sudo grub-install /dev/sdb  
 Installing for x86_64-efi platform.
 Installation finished. No error reported.

``` 
 
 For ZZ
 ```
 $ sudo update-grub
 [Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.9.0-040900rc6-generic
 Found initrd image: /boot/initrd.img-4.9.0-040900rc6-generic
 Found linux image: /boot/vmlinuz-4.9.0-1-generic
 Found initrd image: /boot/initrd.img-4.9.0-1-generic
 Found linux image: /boot/vmlinuz-4.8.0-26-generic
 Found initrd image: /boot/initrd.img-4.8.0-26-generic
 [COLOR=#ff3333]Found Ubuntu 16.10 (16.10) on /dev/sda4[/COLOR]
 Adding boot menu entry for EFI firmware configuration
 done
 $ sudo grub-install /dev/sdb  
 Installing for x86_64-efi platform.
 Installation finished. No error reported.

``` 
 
 AMD Firmware enable in Software & Updates
 
 ```
$ dpkg -l|grep firmware

 ii  amd64-microcode                       3.20160316.2                             amd64        Processor microcode [COLOR=#ff3333]**firmware **[/COLOR]for AMD CPUs
 ii  fwupdate                              8-3                                      amd64        Tools to manage UEFI [COLOR=#ff3333]**firmware**[/COLOR] updates

 ii  libfwup0:amd64                        0.5-2ubuntu4                             amd64        Library to manage UEFI [COLOR=#ff3333]**firmware **[/COLOR]updates
 ii  libfwup1:amd64                        8-3                                      amd64        Library to manage UEFI [COLOR=#ff3333]**firmware**[/COLOR] updates
 ii  linux-[COLOR=#ff3333]**firmware **[/COLOR]                       1.161                                    all          Firmware for Linux kernel drivers

``` 
 
 All the best,

---


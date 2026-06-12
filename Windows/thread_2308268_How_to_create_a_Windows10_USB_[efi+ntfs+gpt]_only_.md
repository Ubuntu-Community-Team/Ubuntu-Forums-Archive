---
title: "How to create a Windows10 USB [efi+ntfs+gpt] only efi.. Easily..?"
date: 2016-01-01
forum: Windows
---

### Post by oklokl on 2016-01-01
unetbootin fat32... fail.. install.wim(4G)


I want to create a window10 usb ..  but..  fail..

Efi boot my computer.

Is there easily could?


I know that this is easy.  
```
git clone git://github.com/pbatard/rufus
```
But it does not install.(I want to do it.](*,))
I'm computer-illiterate



my fail..  list.. 
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
yumi (UI passwords and fat32 fail...)

[http://askubuntu.com/questions/489546/installing-winusb-on-ubuntu-14-04](http://askubuntu.com/questions/489546/installing-winusb-on-ubuntu-14-04)
winusb (ubuntu15.10~ 16.04~ start fail)

[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
.... fail.. efi.. complicacy(Very difficult)



conclusion ](*,)

Sorry.

---

### Post by yancek on 2016-01-01
My understanding is that unetbootin and pendrivelinux can be used to create Linux bootable flash drive.  Don't know that either will work with windows but I've never tried it.  You you have the windows iso downloaded, you can use the method described below to extract it, install Grub to the flash drive and boot windows from the flash drive to install.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by buzzingrobot on 2016-01-01
It's unclear if you're using Windows to do this, but, if you are, take a look here: [https://www.microsoft.com/software-download/windows10](https://www.microsoft.com/software-download/windows10)

If you're not using Linux, that link will redirect to another Microsoft location.

---

### Post by oklokl on 2016-01-01
I am the only Linux computers. ^^
There are no window system.

url... Too difficult. and gpt..64bit(not mbr)
url (I will try.):D
But thanks .. ^^

---

### Post by corneliuss2 on 2016-01-01
> **oklokl said:**
> gpt..64bit(not mbr)

All you have to do is put a GPT* partition table and format the USB flash drive to FAT32** (with GParted), mount Windows ISO (with FuriusISOMount) and copy Windows files to the flash drive. 

Only GUI software. It's not at all difficult. If you're following [this]("http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html"), you only need to follow steps 1 and 2 for Windows 8 and 10.

--
* EFI can boot from MS-DOS partition table (MBR) too, as long as the file system is FAT32 and the **boot*.efi** file is in **boot/efi** folder.
** Contents of untouched Windows ISO from Microsoft can be copied to FAT32 filesystems. However, if you have a modified Windows source with **install.wim** larger than 4 GB you have to make an EFI NTFS bootable flash drive.

---

### Post by oklokl on 2016-01-01
I thought FAT32's file size limitation was 4GB. FAT16's file size limitation should be 2GB. ^^;;
(Ubuntu program)Error install.wim copy to usb

my usb.. 8G~32G  
my install.wim file.. 4G~9G~ More than



sudo apt-get install grub

sudo grub-install --target=i386-pc --boot-directory="/media/test/123/boot" /dev/sdc

Unrecognized option `--target=i386-pc'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.


and.. my.. efi.. T..T.. gpt


I have thought more difficult. T^T

---


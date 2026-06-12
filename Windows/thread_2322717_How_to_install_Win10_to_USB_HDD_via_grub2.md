---
title: "How to install Win10 to USB HDD via grub2?"
date: 2016-04-30
forum: Windows
---

### Post by lei2 on 2016-04-30
Hello there,
I have a PC with Ubuntu14.04 installed, now I'm trying to install Windows10 to a USB hard drive. I've already installed the win10 image(install.wim) to the disk, but what should I do next ?
[ATTACH=CONFIG]268726[/ATTACH]

---

### Post by sudodus on 2016-04-30
I think Windows is made to work only in internal drives. It does not work from USB.

There is a workaround, if your computer is powerful enough and has enough RAM and drive space. You can run it in a virtual machine (for example with VirtualBox). And you can have your Ubuntu host system in a USB 3 drive, for example an SSD in a USB 3 box.

Edit: Or you can have only the virtual machine and the virtual disk in a USB 3 drive.

---

### Post by yancek on 2016-04-30
> I'm trying to install Windows10 to a USB hard drive. I've already  installed the win10 image(install.wim) to the disk, but what should I do  next ?

Nothing.  If you try to install windows to a usb drive, you will simply get the message below and the install will stop.  You've purchased a license to use windows on a single computer and if you were able to put it on a usb, you could possibly use it on multiple computers.

>  "windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports"

---

### Post by lei2 on 2016-04-30
Thanks, but I think I did work it out. I simply installed the win10 image to the USB hard drive using NT6 installer, activate the partition in DiskGenius, and rebuilt the MBR. I beleive your opinion is right, allowing windows to be installed on USB device will result in piracy problems and that's why MS featured WinToGo in Win10. Now if i choose the USB device as first order boot option, it will skip the grub menu and directly enter win10, which is surprisingly activated. I'm not sure if the image I used was a cracked one. But Win10 in USB3.0 is goddamn slow. It doesnt seem to be a good idea.

---

### Post by lei2 on 2016-04-30
Thanks, I just want a win10-to-go so that I could take my configurations wherever I go, but It seems that I have no choice other than WinToGo

---

### Post by Bucky Ball on 2016-04-30
*Thread moved to **Windows**.*

Where did you source the Win ISO/image from to create the USB and how did you create the USB?

---

### Post by lei2 on 2016-05-01
> **Bucky Ball said:**
> *Thread moved to **Windows**.*

Where did you source the Win ISO/image from to create the USB and how did you create the USB?

I downloaded the ISO file from some forum and "deployed" the image using an NT installer in WinPe. That image seems to be a insider version.

---

### Post by Bucky Ball on 2016-05-01
*Thread closed.*

From the forum Code of Conduct, which you read when you joined:

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings.

This is not the place to look for support for unlicensed versions of Windows or any other cracked software downloaded from 'some forum' or elsewhere, nor is it the best place to come for Windows support. There are other sites which I'm sure can help you out with both, perhaps the site where you found the Win ISO originally. Thanks.

---


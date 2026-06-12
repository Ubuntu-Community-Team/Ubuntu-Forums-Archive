---
title: "Install other version of Ubuntu from a iso file that is on my Desktop"
date: 2017-01-09
forum: Ubuntu/Debian BASED
---

### Post by y0d on 2017-01-09
Hi guys,

I want to ask you kindly for help. I want to install Kali on my pc. Now I have ubuntu14.04. If i have the iso file saved on my desktop, how can i run the file from terminal in order to boot the new Linux version?

PS. While using the BIOS, despite i set the priority of the stick, i can't have it run, and therefore i can't boot the new version.
Please help me to install this.

PPS--this is instalation from Ubuntu to Debian etc. I dont have windows and no other resource on this laptop, so is no dual boot, or boot from removable device.

Thank you in advance,
Y0D

---

### Post by deadflowr on 2017-01-09
Do you have the kali iso or the Ubuntu iso?
> how can i run the file from terminal in order to boot the new Linux version?
you can't
but you can add the iso to the boot menu using grub-iso method:
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

You might be better off, though, by figuring out where you erred in putting the image on the stick...
Can you post which method you used to put it on the stick? And perhaps post what the sticks contents look like.

---

### Post by QIII on 2017-01-09
Moved to Ubuntu/Debian BASED.

Kali is not based on Ubuntu.  It is based on Debian.

---

### Post by y0d on 2017-01-09
Hi there,

Thank you for your prompt answer.
I have 3 folders:
1. EFI
2.Install
3.Live

Made the bootable device by using;

sudo dd if=/home/y0d/file.img of=/dev/sd0 bs=1M

---

### Post by y0d on 2017-01-09
Hi there,

I have now Ubuntu14.04 installed and want to install and use Kali.
The iso will download to my Desktop.

---

### Post by yancek on 2017-01-09
Your post is confusing in that you initially say you want to install Kali from the iso on your Desktop then later refer to booting it from a usb.   Both should work if done correctly.   If the iso for Kali is on your Desktop, I don't see how the command you used would work as you don't use the correct path.   You also need to have the exact name of the iso file as well as the correct path to it.  I don't think '/dev/sd0' will work, it should be something like sdb or sdc but there is no way for us to know.  It would help if you posted the exact command you used.  

sudo dd if=/home/y0d/file.img of=/dev/sd0 bs=1M 		

It is possible to boot the Kali iso directly to install it but it is probably going to be simpler to use a bootable usb.  The Kali site has explicit instructions on how to create the bootable flash drive so have you read that?

---

### Post by ajgreeny on 2017-01-09
The difficulty of using an iso file on your disk and installing from that is that you will be unable to use any partition already in use, so will have to have a partition or partitions that are unmounted and not currently in use.  It is much easier to use a USB and boot from that.

Have a look at [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) and try mkusb which in my opinion is the best USB install disk creator and uses dd to do the job for you painlessly.

---

### Post by yancek on 2017-01-09
> The difficulty of using an iso file on your disk and installing from  that is that you will be unable to use any partition already in use, so  will have to have a partition or partitions that are unmounted and not  currently in use.  It is much easier to use a USB and boot from that.

I'd agree that using a usb is easier and mkusb is good software, particularly for new users.  I'm not sure I see your other point about partitions currently in use as one would certainly not want to install to a partition on which you have the iso or which has an operating system or data on it but an empty partition or unallocated spaace.  I haven't used any other method for years and boot the iso from the OS partition or from a separate data partition on which I have the various iso files.  Not a problem if you are familiar enough with Grub but it certainly would be less complicated for a new user to use a flash drive.

---

### Post by ajgreeny on 2017-01-10
> **yancek said:**
> I'm not sure I see your other point about partitions currently in use as one would certainly not want to install to a partition on which you have the iso or which has an operating system or data on it but an empty partition or unallocated space.
We might both know that you would not want to do that, but I'm not sure about y0d, who says he has Ubuntu 14.04 installed now but wants to use (replace it?) with kali; that was how I read it anyway.

@ y0d
Aside from all that, you are best advised to get a 4GB USB flash drive and then use mkusb to create an install USB, which is so much simpler than booting an iso file direct from grub.

---

### Post by yancek on 2017-01-10
I'm not sure if he wants to replace Ubuntu with Kali or keep both.  Not really clear to me.   The OP doesn't seem to have much knowledge so the only logical reason I can think of to use Kali is to learn computer forensics.  To do that without messing up his system, it would be much easier and more useful to use a flash drive on which to install Kali and the Kali site has extremely detailed instructions to do just that.

---


---
title: "Copying a bootable ISO file of Windows 10 on a flashdrive to another flashdrive?"
date: 2017-04-30
forum: Windows
---

### Post by cybrsaylr on 2017-04-30
Awhile back I created a bootable ISO of Windows 10 onto a 32 GB thumbdrive when you qualified to get the free download of W10. It worked fine installing W10 to my PC. Now I want to preserve this Win 10 ISO to another smaller 8 GB flashdrive so that the 32 GB flashdrive can be used for something else. Question is can you simply copy that ISO (drag & drop it) to another smaller flashdrive and will it still work fine in case it is needed to reinstall Win 10 in the future if needed?

---

### Post by yancek on 2017-04-30
Why don't you just use whatever method you used to put the windows iso on the 32GB flash to put it on the 8GB flash?
The only way I can think for the method you suggest to work is if you have a system on another drive with Grub and you manually put an entry to boot the 8GB flash drive.

---

### Post by Perfect Storm on 2017-04-30
Moved to Windows forum.

---

### Post by cybrsaylr on 2017-04-30
yancek

Not sure if Windows still allows it to be done as it was originally done, as that time frame has expired to get the free qualifying W10 ISO download.

---

### Post by yancek on 2017-04-30
If you still have the iso of windows or the extracted files from the iso, you can follow the procedure described at the link below.  Skip the part about installing Grub and juse create an entry based on the example they show and put it in your grub.cfg file for Ubuntu.  If you don't have Ubuntu or a Linux system...good luck.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by Frogs Hair on 2017-04-30
Just an FYI, MS severs record information about the device/hardware the free upgrade was performed on when activated. So, it wouldn't activate without charge if you used it on another device though it would be fine to use to repair an installation.

---

### Post by cybrsaylr on 2017-04-30
Well simply dragging and dropping all ISO files from 32GB flashdrive to the 8GB flashdrive doesn't work. Tried that and while the 32GB drive still will attempt to install W10 the 8GB drive just shows a 'boot error' when attempting to boot into W10 from it. 

I just want to save it to the smaller flashdrive in case it's needed for repair or re-installation of W10 (the little W10 is used) in the future on the legit PC and not put it onto any other device. Just not sure it this can still be done. Its been awhile since this ISO was created and don't really recall how I did it.

---

### Post by oldfred on 2017-04-30
Did you format flash drive as FAT32 (from Windows) and include boot flag. The copy of files should make it UEFI bootable.
You may have to run chkdsk on it to make sure FAT32 has correct configuration if formatted from Linux.

If you need BIOS boot you have to install the Windows boot loader to MBR of 8GB flash. You should be able to run the normal repairs from your Windows install. FixBoot, FixMBR, chkdsk, etc.

---

### Post by cybrsaylr on 2017-05-01
Fred, both 32GB and 8GB flashdrives list msdos as the basic Filesystem type. Believe when the MS sever was used to create the ISO in the 32GB drive, MS prepped it to the correct filesystem that works. Not sure about the 8GB drive.

The 32GB drive works fine. On startup, F12 is hit and a boot selection comes up. 32GB drive is selected and it goes right to a windows setup.

GParted shows both flashdrives are FAT 32 and have the same boot, lba flag.

---

### Post by LastDino on 2017-05-01
Have you tried this method?

[http://www.backup-utility.com/clone/how-to-copy-usb-to-usb-3889.html](http://www.backup-utility.com/clone/how-to-copy-usb-to-usb-3889.html)

Though as already mentioned, you will have to register again/activate again by paying for it in case of full install.

---

### Post by cybrsaylr on 2017-05-01
Ended up going back into Windows and using this link; [https://venturebeat.com/2016/01/04/how-to-create-a-bootable-windows-10-usb-flash-drive-2/](https://venturebeat.com/2016/01/04/how-to-create-a-bootable-windows-10-usb-flash-drive-2/)
Probably did something like this years ago but forgot how. It was pretty easy, just like Linux. About time Windows did something like this. 

Took about 30 minutes and now that 8GB flashdrive works for installing W10.

Thanks for the help.

---

### Post by LastDino on 2017-05-01
I'm glad things worked out for you. There is also tool called "Rufus" which is pretty useful in creating Windows bootable USB and MicroSD, it woks pretty similar to Linux bootable media creation tools.

---

### Post by oldfred on 2017-05-01
Are you copying with Linux tools or Windows tools.

When I made my Windows bootable flash drive from a Windows bootable DVD, I used the Windows commands to mount, format & copy from the DVD itself to copy to flash drive. That was for a Windows 7 repair disk. Have not tried with anything newer.

Missed page 2 and that already solved.

---

### Post by cybrsaylr on 2017-05-01
Dino, saw a link with "Rufus" but thought the link I used was easier.

Fred, at first tried using only Linux tools hoping a simple copy & paste would work. Then when that failed used Windows tools. Didn't want to bother with a terminal unless all the commands needed  were listed.

Was happy MS still lets you download W10 but know to make it work smoothly you still need a legit activation Key.

Actually at this point in time the only reason Windows in needed is to update a Garmin GPS. Garmin only supports Windows and Mac. Called Garmin asking if they ever plan to add Linux support. Their rep just laughed and said no. Asked why not and they said their are over 100 flavors of Linux! So which ones would they have to include to support?

---


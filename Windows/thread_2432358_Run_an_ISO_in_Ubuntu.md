---
title: "Run an ISO in Ubuntu"
date: 2019-12-01
forum: Windows
---

### Post by jmichaels1 on 2019-12-01
Windows has programs that let you run an .iso file, such as [https://www.redfox.bz/en/download.html](https://www.redfox.bz/en/download.html). You can see how it works here :[https://www.intowindows.com/installing-windows-7-without-using-dvdusb-drive-method-2/](https://www.intowindows.com/installing-windows-7-without-using-dvdusb-drive-method-2/)

Are there any programs that will do the same in Ubuntu? It messed up my Windows 7 boot and I was wondering if I can install without burning another DVD or USB drive, bc I don't want to empty one.

---

### Post by crip720 on 2019-12-01
Ubuntu usually does not mess up windows, unless someone installs over windows.  It might be ubuntu did not find windows to add to grub, but that should be fixable.  Please explain how windows boot is mess up.

---

### Post by ajgreeny on 2019-12-01
Depending on what you mean by "run an .ISO", the answer may be  that you certainly can.

I used to use a large USB flash drive to which I installed grub, created a custom grub.cfg file, then copied many .iso files to a folder on the USB.

This made it possible to boot to the USB drive, and choose whichever of the ISO files I wanted to run as a live system from the grub menu.  I have not done this now for a few years but I followed all the info at [https://ubuntuforums.org/showthread.php?t=1288604](https://ubuntuforums.org/showthread.php?t=1288604) and it worked perfectly.

As crip720 says, booting a live system should not cause any problems for your installed Windows system so it would be helpful to know exactly what you did and what the problem actually was.  Did you try  to install Ubuntu as a dual boot with Windows 10 or just run it as a live system?

Windows 10, if it came with your computer will undoubtedly be using UEFI but you may have installed or run ubuntu using MBR/BIOS and if that's the case the grub bootloader will not be able to see or boot Windows.

It will possibly be worth seeing exactly where you are at present so see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script from Ubuntu, using a live system if necessary.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

EDIT:
There is some more recent information about live booting an ISO file at [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) which may be better for you, particularly as it covers UEFI booting which my original link does not.

---

### Post by crip720 on 2019-12-01
The OP is asking to install Win 7 directly from the ISO file in Ubuntu without burning to a USB/DVD.

---

### Post by yancek on 2019-12-01
> It messed up my Windows 7 boot 

"It"?  What 'it' are you referring to?  As to booting a windows 7 installer, yes you can do that from any Linux system with Grub2 (actually Grub Legacy would work also).  If you have Ubuntu or any Linux system with Grub2, create an ntfs partition on your hard drive a little larger than the iso file.  Extract the iso file and copy the contents to that newly created ntfs partition and mark it as active and create an entry for Grub to boot it.  Actually, I'll just refer you to the web page which explains  it in detail so point in repeating everything here.  If you can follow detailed instructions, it should be no problem.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by uRock on 2019-12-01
Moved to "Windows" sub-forum.

There are plenty of tools for making a bootable ISO on a USB.

---

### Post by jmichaels1 on 2019-12-01
@urock I didn't ask how to make a bootable usb. I said I don't want to use a usb.

---

### Post by uRock on 2019-12-01
> **jmichaels1 said:**
> @urock I didn't ask how to make a bootable usb. I said I don't want to use a usb.

USB is the best you're going to get. I am quite surprised you haven't already ran down to the corner store to get one.

---

### Post by yancek on 2019-12-01
The best you are going to get for doing what you want is by using the method used at the link I posted earlier.  This is a Linux system with a Linux bootloader  booting a windows installer.   

The Grub2 bootloader will boot a Linux iso file directly without having to extract it which the windows software you refer to requires. Grub2 won't directly boot a closed source, proprietary windows iso and it's unrealistic to exect that.  The instructions are very explicit and simple to follow.

---

### Post by C.S.Cameron on 2019-12-01
UNetbootin 675 will make a Windows boot USB. 
It can also make a Frugal install on a corner of your hard drive, (so that a USB drive is not required for installation).
The install is temporary but can be used to install it's load to any drive on the computer.
There is a Linux version of 675 that seems to be working, but I have not tried installing Windows using a frugal install yet.

[https://unetbootin.github.io/linux_download.html](https://unetbootin.github.io/linux_download.html)

---

### Post by Skaperen on 2019-12-02
> **jmichaels1 said:**
> Windows has programs that let you run an .iso file, such as [https://www.redfox.bz/en/download.html](https://www.redfox.bz/en/download.html). You can see how it works here :[https://www.intowindows.com/installing-windows-7-without-using-dvdusb-drive-method-2/](https://www.intowindows.com/installing-windows-7-without-using-dvdusb-drive-method-2/)

Are there any programs that will do the same in Ubuntu? It messed up my Windows 7 boot and I was wondering if I can install without burning another DVD or USB drive, bc I don't want to empty one.

your post has a lot of vague references, making it hard to understand what you want to do.  where you say "It messed up ...", people are unsure what "it" refers to.  very few things will "mess up Windows 7", so we are guessing.  it looks like you are trying to re-install Windows 7.  i have heard that Windows 7 has a kind of rescue disk.  if si,the PC itself should be able to boot it.  we don't know if it could mess up Ubuntu.

normally PCs boot .iso recorded on a disk.  but you said "run an .iso file".  that sounds like you need a virtual machine.  it would run the .iso file, but you can't get easy access the the drive in the normal fashion.  unless you have a 2nd hard drive, virtual installing will be quite a difficult task because the one drive hosts both the systems.  having systems on separate drives would be a lot better.  having separate PCs would be the ultimate (lets you run both at the sane time,

---

### Post by yancek on 2019-12-02
> UNetbootin 675 will make a Windows boot USB]

Have you actually used unetbootin to create a bootable windows usb?  The page you linked to is just a download page.  I did a brief online search which gave me a few sites which indicated using unetbootin to create a bootable windows usb was possible but they were very brief and uninformative.  Historically, unetbootin has had 3 versions (windows, linux, mac) which could be used to create a bootable 'Linux' usb so if it now works to create a bootable windows, that would be something new.

---

### Post by ajgreeny on 2019-12-02
> **crip720 said:**
> The OP is asking to install Win 7 directly from the ISO file in Ubuntu without burning to a USB/DVD.
Ah!  I missed that, not having read the details in the two links provided.

Can you actually run Windows of any version as a live OS, which is what I thought was being asked about, not realising it was a Windows OS at all?

---

### Post by SeijiSensei on 2019-12-02
You can install Windows from its ISO image to a virtual machine in VirtualBox. Otherwise you need to create a physical boot medium.

---

### Post by ajgreeny on 2019-12-02
Thanks SeijiSensei, that is what I thought, ie, there is no such thing as a live Windows System, and a VM is not the same thing at all.

---

### Post by C.S.Cameron on 2019-12-02
**Rufus** now has an option to make a **"Windows To Go"** USB.
This is not a Live option but a Full install of Windows 10 to Flash drive.
I managed to fit it in a 16GB USB2 drive and it was slow, but stable.
It's creation was also very slow.
It does ask for a number.

---


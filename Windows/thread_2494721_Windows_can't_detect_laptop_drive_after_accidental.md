---
title: "Windows can't detect laptop drive after accidental ubuntu install"
date: 2024-01-24
forum: Windows
---

### Post by notzach on 2024-01-24
This morning a mad a mistake that was a lot worse then I thought...

I was trying to make a external SSD bootable ubuntu. When I was installing it I accidentally selected to wipe all the drives but the external was set as the main. After I realized my mistake I tried to reinstall windows but now the drive isn't detected. It shows up in the BIOS and it passes the storage test but windows installer doesn't recognize it and even diskpart doesn't see anything but a USB. After that I booted to an ubuntu usb and that detects the hard drive. I've tried changing the format of the hard drive and wiping it using the disk and gpart tools. I have a theory its a driver issue cause my mousepad only works if I boot from ubuntu but I'm absolutely stumped on what to do.

---

### Post by oldfred on 2024-01-24
Moved to Windows sub-forum.

If UEFI system, you need gpt partitioning and better to have blank drive for Windows install. Windows wants multiple required partitions.
Windows in UEFI mode will only install to gpt partitioned drives. If using gparted you have to select that in top menu.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

Also difficult to make Windows installer from Ubuntu. Microsoft has a .wim file that is over 4GB. But UEFI boot requires FAT32 which does not support files over 4GB. The Windows tool to create a live installer splits the .wim file into two parts. If using Linux, make sure you have newest instructions as a few now can create a Windows installer.
If UEFI system, the Product Key is in UEFI.

---

### Post by notzach on 2024-01-24
I just tried the gpt partition table. I tried unpartitioned and formated using ntfs and neither show up using my windows 11 installer usb. Although I don't know if i got the all the partition settings correct when setting it up.

---

### Post by yancek on 2024-01-25
Are you using the same windows installer usb you used to originally install windows?  Did you have windows installed when you purchased the computer?  Are you now using an iso you downloaded from the microsoft site and wrote to the usb?

A windows system won't recognize much of anything regarding a Linux system.  In Disk Management on an installed windows, you should be able to see the drives and partitions but won't be able to access anything.  I don't know what tools you have available on the windows installer. 

> I just tried the gpt partition table. I tried unpartitioned and formated  using ntfs and neither show up using my windows 11 installer  

What does tried the gpt partition table mean?  Did you change it from msdos to gpt?  I would have thought it already was gpt, did you check first?  How (what tool) did you do this?  Did you create a partition (or partitions) on which to install windows?  How did you do that, what tool did you use?  Something on the windows installer?  Probably best to leave the entire disk as free or unallocated space.

If you still have the Ubuntu install usb, you might try booting it and running either command below to get and post the output here so we have some actual information:

```
sudo parted -l
sudo fdisk -l
```

Another suggestion, since this is not a Linux or Ubuntu problem but a user error, you might be better off at a windows forum or checking the microsoft site for possible solutions or at least suggestions.

---


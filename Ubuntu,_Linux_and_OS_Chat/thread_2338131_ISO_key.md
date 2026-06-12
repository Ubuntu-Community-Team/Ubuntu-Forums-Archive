---
title: "ISO key"
date: 2016-09-24
forum: Ubuntu, Linux and OS Chat
---

### Post by binaryaura on 2016-09-24
I'm new to dual booting and now I have Ubuntu and Windows on two separate SSDs. I would like to avoid calling the boot menu every time I want to boot linux. My idea was to have a usb flash drive with an iso image that simply boots the ubuntu os over the windows os. With the flash drive, Ubuntu would boot, without it Windows. However, I'm unsure on how to go about this. Or where to look for information on this.

---

### Post by QIII on 2016-09-25
This sort of thing could likely be done.  My SBCs boot first to SD cards which direct the boot process to a proper hard drive for much faster operation. The only reason I leave the SD cards in the process is the simple fact that the hardware boot from SD or eMMC.

I'm sure you could arrange your boot order in such a way that the first boot option would be USB and that would direct the boot process to continue on the Linux SSD when the USB drive is present.  However, are you sure it would be more convenient than a couple of strikes of the down arrow key?

That is, if it can be done technically, do you have a compelling practical reason to do so?  If you really do, I'm sure someone would love to help you figure this out.  I don't intend to discourage you if you want to go this way.  I just want to make sure you understand your expectations as they relate to practical use.

---

### Post by oldfred on 2016-09-25
UEFI or BIOS?
You just need to set BIOS to boot flash drive first, then if not present it uses second choice in boot order.
Should be similar with UEFI, but some work better than others.
And UEFI external drives only boot from /EFI/Boot/bootx64.efi which you have to create after install.

I have both UEFI & BIOS full installs on flash drives, but only have Ubuntu on SSD, so that is my default boot. And in each I have multiple ISO as repair or install options. Only my old small flash drives were direct boot with grub to ISO.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[URL="http://ubuntuforums.org/showthread.php?t=1549847"]http://ubuntuforums.org/showthread.php?t=1549847

      [/URL]
 UEFI & BIOS & Live installer - sudodus
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506) 
    [URL="http://ubuntuforums.org/showthread.php?t=1549847"]https://help.ubuntu.com/community/Installation/UEFI-and-BIOS
[/URL]

---


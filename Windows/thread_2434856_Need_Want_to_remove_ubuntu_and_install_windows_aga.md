---
title: "Need Want to remove ubuntu and install windows again"
date: 2020-01-12
forum: Windows
---

### Post by nocruoro on 2020-01-12
Looks like i'm not leaving yet... 

**[COLOR=#b22222]Like the title said want to completely remove ubuntu and install windows again. [/COLOR]**

First off, I've tried using a ubuntu disk image mounter with this: [https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)
since i get one error while copying wim10 file saying Error splicing file: Input/output error and a error unable to create a support folder.

**WoeUSB doesn't seem to detect my usb while my usb is plugged**

[COLOR=#000000]I also cant get my laptop to detect my usb **during boot** if i use a windows media creation tool on my friends pc

does this guide work on all versions and not just ubuntu [I]14...online guide only mention 14 and 16
[/I][/COLOR]_[[COLOR=#000080]https://www.youtube.com/watch?v=P-h7VZNvKKA[/COLOR]]("https://www.youtube.com/watch?v=P-h7VZNvKKA")_[COLOR=#000000]
[/COLOR][U][COLOR=#000080]
[/COLOR][[COLOR=#000080]https://sysads.co.uk/2016/08/29/install-winusb-ubuntu-16-04/[/COLOR]]("https://sysads.co.uk/2016/08/29/install-winusb-ubuntu-16-04/")[/U]
or does anyone know a better guide?????????????????
.
.
[COLOR=#b22222]Note: I have no dvd/cd-drive so a installation disc is not a option  and i don't want any dual booting; Just eradicate Ubuntu 18.4.3 and get windows 10 back[/COLOR]

---

### Post by howefield on 2020-01-12
Thread moved to the "*Windows*" forum.

---

### Post by nocruoro on 2020-01-12
sorry but first post has been updated

---

### Post by Frogs Hair on 2020-01-12
I searched for a _current_ guide to creating a windows 10 usb from Linux. Below are two examples from well known sources. Your device if it came with Win 10 or upgraded from Win 7 is probably recorded on MS servers, so Win 10 could  activate without issue once logged into your MS account.

[https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu)


[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)

---

### Post by nocruoro on 2020-01-12
new issue with WoeUSBT it keeps saying my usb is busy when it isn't and it is a NTFS format
[ATTACH=CONFIG]284791[/ATTACH]


[I]
As for my MS Account i have one since windows was pre-installed (i don't remember if it's still have a account) Ubuntu was a emergency a clean installation after my computer was wrecked by a virus which destroyed a lot including the standard windows 10 boot loader[/I].

---

### Post by Frogs Hair on 2020-01-12
The second link may supply an alternative.

---

### Post by nocruoro on 2020-01-12
> **Frogs Hair said:**
> The second link may supply an alternative.

Still same issue. If i format for usb NTFS i can't mount and read it in file viewer. 


[B]I'm use the exfat option format (supposed to work for all computers) and i hope i dont get the copy errors all over again or even get stuck during copy process.

[/B]EDIT: i get again a similar error, the media file isn't big at all if i recreate it in windows. that usb drive is 60GB big

---

### Post by CelticWarrior on 2020-01-12
If you have access to a Windows computer my suggestion is to make the Windows installation media there, just download the ISO and follow instructions.
There's really no reliable method to do it with Ubuntu/Linux although the tool you've tried has been reported as working even with the current crop of Microsoft's ISOs. But all those reports are from properly working Ubuntu installation, something I sincerely doubt that you have at this point.

---

### Post by nocruoro on 2020-01-12
> **CelticWarrior said:**
> If you have access to a Windows computer my suggestion is to make the Windows installation media there, just download the ISO and follow instructions.
There's really no reliable method to do it with Ubuntu/Linux although the tool you've tried has been reported as working even with the current crop of Microsoft's ISOs. But all those reports are from properly working Ubuntu installation, something I sincerely doubt that you have at this point.

Then if the F2 is a **diagnosis button instead of loading a boot option** then which one is more likely for a Acer laptop F12 or F10?

---

### Post by oldfred on 2020-01-12
Standard keys, but best to look at your manual.

UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)
[http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by nocruoro on 2020-01-13
> **oldfred said:**
> Standard keys, but best to look at your manual.

UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)
[http://www.eightforums.com/](http://www.eightforums.com/)


Seems to be F12 for acer model notebooks. Don't have a manual, this laptop/notebook was a "hand-me-down" gift from my dad 2 years ago.

So if i keep things simple, use windows media create tool on a friends pc to fix my usb drive. turn off my notebook or use restart and quickly.... **press F12 while the usb is connected during reboot** **then i should be able to use a boot manager to see my usb drive and follow instructions?**


[I].
i need to work on this carefully or slowly this week. lot of with garbage maintenance at the supermarket i work at and snow shovelling where i live which takes a lot of energy out of me.[/I]

---

### Post by nocruoro on 2020-01-15
new problem i keep getting a required media driver or partition is missing during the installation. Is there anyway to diagnose this in ubuntu.

---

### Post by Frogs Hair on 2020-01-15
First try a different usb port if possible. This is a known problem so use the following search term to find possible solutions.

> required media driver or partition is missing

---

### Post by nocruoro on 2020-01-15
I'm also getting a recommendation on tenforums to di this

>  try booting a LIVE linux distro --e.g fedora from a USB drive and run gparted. It should see a disk -- then reformat that or even use the linux command mkfs.ntfs -f /dev/sdx where x is the nr of the HDD drive. (Install ntfs-3g if not installed on the live distro --you can install stuff - it's not persistent on next boot but it will work for what you need to do). 

can this work with any version of a ubuntu or inux installer to clean a drive?

---

### Post by oldfred on 2020-01-15
That is to create a NTFS partition for Windows install.

How did you create Ubuntu live installer. 
Multiple ways.
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by maryoung on 2020-01-15
I searched on Google but i didn't do that,we are allowed to make a Windows bootable USB on Linux.

---

### Post by oldfred on 2020-01-16
UEFI only uses FAT32 which has a size limit on one file of 4GB, but Windows wim is now too large, extracted into a NTFS partition and only boot files in FAT32.
[https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/](https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/)
[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)

---


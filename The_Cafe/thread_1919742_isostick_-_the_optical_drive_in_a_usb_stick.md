---
title: "isostick - the optical drive in a usb stick"
date: 2012-02-03
forum: The Cafe
---

### Post by mips on 2012-02-03
This is pretty cool!

[http://www.kickstarter.com/projects/elegantinvention/isostick-the-optical-drive-in-a-usb-stick](http://www.kickstarter.com/projects/elegantinvention/isostick-the-optical-drive-in-a-usb-stick)

> The isostick is a USB flash memory stick that likes to pretend it is also an optical (CD/DVD) drive. As far as the computer knows, there's two things in that little device: a flash drive and an optical drive.

Any CD/DVD images (also called ISO9660 or "iso" files) that you keep on the flash drive can be "inserted" into the optical drive. The computer will think there is a real optical drive there with a real disc in it! Of course, you can keep whatever you want on the flash drive, not just iso files.

You can boot from the optical drive as well, so you can keep your OS install images on there and use them as needed. Of course, that's not much good without the ability to change which iso is loaded on-the-fly. To solve that problem, we have a little thing we call "isosel," short for "iso selector," developed by our friend Stephen. Briefly, booting from the isostick's optical drive gives you a list of all your disc images, with the last-inserted one selected by default. It works much like any other boot manager: there is a (configurable) timeout, so if you don't do anything it will go ahead and boot the last-inserted image, so unattended installs will work fine.

The isostick also has a read-only switch so you never have to worry about a nasty virus hitching a ride on it. You can feel safe plugging the isostick into any computer with the switch in the Read-Only position, it's implemented fully in the device so there's no way for rogue software to override it.

Sometimes you're waiting around for something to complete and you're not sure if the computer has locked up or if it's just busy doing something. It has been said the "everything is better with blinkenlights." We couldn't agree more, so we put a nice bright LED in the isostick to show drive activity. That way at least you'll know if it's being accessed. But sometimes bright lights can be a problem, maybe you're a vampire and you work in the dark. We've got you covered: the brightness of the LED is completely configurable, you can even turn it off if you wish.

The isostick is targeted at IT people, computer technicians, and geeks in general that are sick and tired of carrying around lots of discs that always get lost, broken, scratched, or just stop working. Often times you'll have to update your discs with the latest patches or virus definitions or what-have-you. With isostick it's a breeze, just drop the new iso on the flash drive and you're ready to go!

Currently isostick supports the FAT32 filesystem. Despite this limitation, the isostick management software will automatically split up ISOs larger than 4GB, or you can do this yourself. You can format and partition it however you please, but for right now it can only make use of iso files on the first partition, which must be FAT32. Support for reading iso files from other partitions (so long as they are FAT32) will be coming soon. Support for other filesystems such as HFS+, ext2/3/4, and NTFS, is planned although that's a low priority so please don't expect it too soon!

On that note, isostick can be updated with new firmware as new features are added and bugs are fixed. There is no limitation on this, whether you're the first person or the 100th person to get one, everyone can always keep their isostick up to date with the latest firmware.

At the time of writing, the production boards are designed and we've tested a small run of them, shown here:
[IMG]http://farm4.static.flickr.com/3435/5798741545_6f2bfe2f08.jpg[/IMG]

There's still some kinks to be worked out and features to be added before we're ready to get them to the masses. That's where you come in. Your funding will help us finish things up and bring the isostick into production. With your help, we can start making the lives of geeks everywhere a lot easier!

Thank you very much for visiting and we hope you like isostick!

---

### Post by doorknob60 on 2012-02-03
Ooh I want one, but doesn't seem like they available to purchase yet, oh well :( I guess I can wait.

---

### Post by Copper Bezel on 2012-02-03
Sandisk tried a variation on this in the past, and it's terribly irritating in practice, but the implementation here seems much better. It'll be interesting to see how it goes. Convenient for boot disks, potentially (as it would be quicker to set up.)

---

### Post by wolfen69 on 2012-02-03
Me want! That would be sweet to have a 16gb version and put all of the major distros on it.

---

### Post by forrestcupp on 2012-02-03
Wow! That *is* cool. It's especially cool that you can have multiple ISOs on it and select the one you want to use.

---

### Post by mips on 2012-02-04
bump.

---

### Post by oldfred on 2012-02-04
Most computers in the last 5 or 6 years will directly boot USB flash drives. I have several flash drives with ISO. One is a full Ubuntu install plus several other ISO. One is a Windows repairCD with several other Linux repair ISO. And my main 4GB flash drive is filled with ISO for installing.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I did it before it was automated by scripts, in addition to the pendrive site mentioned before:

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by LinuxFan999 on 2012-02-04
This looks like a nice feature. I wish every flash drive had this feature.

---

### Post by kurt18947 on 2012-02-04
> **Copper Bezel said:**
> Sandisk tried a variation on this in the past, and it's terribly irritating in practice, but the implementation here seems much better. It'll be interesting to see how it goes. Convenient for boot disks, potentially (as it would be quicker to set up.)

Are you thinking about U3?  Yeah, that was irritating.  And for a while it seemed to be on other USB drives besides Sandisk.  At least Linux ignores it rather than creating a drive like Windows.

---

### Post by forrestcupp on 2012-02-04
> **oldfred said:**
> Most computers in the last 5 or 6 years will directly boot USB flash drives. I have several flash drives with ISO. One is a full Ubuntu install plus several other ISO. One is a Windows repairCD with several other Linux repair ISO. And my main 4GB flash drive is filled with ISO for installing.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I did it before it was automated by scripts, in addition to the pendrive site mentioned before:

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

That's pretty awesome. But it's still cool that these new USB sticks will be able to do all of that without any configuring.

---


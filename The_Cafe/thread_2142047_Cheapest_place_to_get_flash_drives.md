---
title: "Cheapest place to get flash drives?"
date: 2013-05-04
forum: The Cafe
---

### Post by colorend on 2013-05-04
I use quite a few different Linux distros, most of which are Ubuntu or Debian based, and this has left me with loads of massive iso files on my computer taking up space, and it'd be useful to be able to boot them all when I want, and to be able to delete them from the computer. For this I need about 25 USB flash drives, and I've looked all over the internet but I can't find any sites that sell flash drives in bulk for personal use, they're all aimed at businesses which I really don't want. Any sites that you guys use for flash drives? Preferably based in the UK but America is fine.

---

### Post by C.S.Cameron on 2013-05-04
The cheapest flash drives I have found are on the streets of New Delhi, ~$8 for a 64GB drive in original package.
Only problem is that the drive was hollow inside.

---

### Post by oldfred on 2013-05-04
Microcenters house brand has been good for me. My problem is they have a store only a few blocks down the street and I cannot checkout at cash register without seeing price has dropped and I can now buy a larger one. :)

And now they have USB3 versions for only a $1 more. I find even with my USB2 ports they are about 10% faster.
Do not know if they are in UK or not.

---

### Post by sanderj on 2013-05-04
> **colorend said:**
> I use quite a few different Linux distros, most of which are Ubuntu or Debian based, and this has left me with loads of massive iso files on my computer taking up space, and it'd be useful to be able to boot them all when I want, and to be able to delete them from the computer. For this I need about 25 USB flash drives, and I've looked all over the internet but I can't find any sites that sell flash drives in bulk for personal use, they're all aimed at businesses which I really don't want. Any sites that you guys use for flash drives? Preferably based in the UK but America is fine.

What do you mean with "flash drive"? If you mean 4GB USB sticks: they are available starting at 4.20 Euro incl VAT. And I suppose it is no problem to order 25 of them.

HTH

---

### Post by oldfred on 2013-05-04
You do not need 25 flash drives, just one large enough for all the ISO. I use several just to have alternatives. I have one larger flash drive with a full install and then several ISO in data partition, several 4GB flash with a couple of Ubuntu and several smaller ISOs.

While this says hard drive the only difference is you have to install grub to flash drive and manually maintain a grub.cfg.
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

      
 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sda
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)

I did it before others created scripts, but you can also use those now for many ISO.

 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by colorend on 2013-05-04
Sorry, I forgot to specify that they need to be 1gb and putting them on to a single memory stick would be a bit risky and I need them to be separate

---

### Post by Paqman on 2013-05-04
You shouldn't have to pay any more than about £2 each for 1GB sticks on Ebay.

---

### Post by Sam Mills on 2013-05-04
I always buy from newegg.com. Great prices and good customer service.

---

### Post by colorend on 2013-05-05
Okay thankyou all for your help, I can't actually find any on newegg.com so I'll
stick with eBay.

---

### Post by pqwoerituytrueiwoq on 2013-05-05
+1 newegg. got my 32gb for $13 and some odd cents
[http://www.newegg.com/USB-Flash-Drives/SubCategory/ID-522](http://www.newegg.com/USB-Flash-Drives/SubCategory/ID-522)
this is the one i got when it was on sale
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820313090](http://www.newegg.com/Product/Product.aspx?Item=N82E16820313090)
it makes a nice grub2 boot disk

---

### Post by pqwoerituytrueiwoq on 2013-05-05
deleted (not the thread i meant to post in)

---

### Post by stalkingwolf on 2013-05-05
you should also be able to find lots on ebay. i recently got a lot of 5 2gbs for under 10.00.i installed all my utilities on the like gparted and boot rescue.

---

### Post by Warpnow on 2013-05-06
Physical Store: Microcenter

Online: Dealextreme.com

DX is direct from china. Dirt cheap and discount if you buy more than 3 of any item.

---

### Post by ssam on 2013-05-08
you might want to look at [isostick]("http://isostick.com/"). its designed for just this sort of thing.

---


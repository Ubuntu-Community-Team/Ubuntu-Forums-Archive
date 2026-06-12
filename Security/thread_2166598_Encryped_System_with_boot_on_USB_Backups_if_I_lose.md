---
title: "Encryped System with /boot on USB: Backups if I lose the USB?"
date: 2013-08-10
forum: Security
---

### Post by DiagonalArg on 2013-08-10
If I put it on a USB, is there some automated way to keep a backup, in case I lose the USB?

I am thinking along the lines of an image of the partition, loaded up to a server every time GRUB updates.  Or any other idea that might be convenient.

(Forgive me if this is a stupid question.  If so it could be related to my easily admitted lack of understanding of GRUB!)

/DA

---

### Post by Ranko Kohime on 2013-08-10
No automated way that I know of...  But do you do automated updates, or manual?  (I manually install updates so that I don't get caught unaware by kernel updates)

If you do manual updates, it's quite possible to just have a shell script that does the update, images the USB after the update is finished, and uploads the image to your server of choice.

Alternatively, kernel updates within a specific version of Ubuntu, don't generally make or break most applications, so it may not be necessary that you have an updated /boot USB.  Meaning, you could back up now, do updates to the USB, and if the USB is lost, just load the old image from the server onto a new USB, and re-install the kernel updates.

---

### Post by DiagonalArg on 2013-08-11
Ranko - That's useful information.  Thanks for the idea.

Perhaps you could clear up a couple of things about GRUB for me?  

(1) If I have grub on a boot partition, and I have a backup of the _files_ on that partition (easy, using rsync), would that be enough for me to recreate the partition?  In other words, is there a use of "grub-install" or "update-grub" or whatever that would allow me to do this?  (That is, while I understand what the MBR is, I'm not at all clear on what gets installed to a linux boot disk, so I don't know what needs saving and what can be recreated.)
 
(2) Tangentially, but generally relevant, if I put GRUB on a USB as we're discussing here, then do you know of a way to additionally do live-installs on the remainder of the USB, so that I could have the choice in the grub menu to boot my machine with it's installed Ubuntu or some (live) other distro. 

Thanks for your help!
/DA

---

### Post by oldfred on 2013-08-11
If trying to recreate a grub, you have all the UUID issues. Any new partitions will have new UUIDs. But you can manually edit those in grub's menu. You probably have to reinstall grub to MBR as that creates the core.img that is the rest of the boot process. Not sure what all is in core.img.

I do not create installers anymore. I used to just copy ISO to flash drive and use grub2's loopmount to directly boot ISO. Works for Ubuntu desktop but not server and many repair ISO like parted magic, gparted etc. Then I have all those ISO on one flash drive to try to boot or use different repair tools.

Boot drive is alway hd0 from BIOS. so you can do the same type of grub entries and configuration as shown for a hard drive. Often issue is what boot parameters are needed and what path in ISO is kernel. Varies by distribution.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

There are some scripts that automate the install process of multiple ISO, but they reformat flash drive and just install ISO.

---

### Post by DiagonalArg on 2013-08-12
@oldfred -

Thanks, man.  All that stuff looks really good, & I'll study it carefully.  Couple questions left:

(1) Re "uuid issues", those would be the UUID's of the hard drives that GRUB's going to get the kernel from, not the USB's UUID, right (?)  In which case they wouldn't change, even if I lost the USB (?) So then having a backup of the files in /boot should be sufficient?

(2) When I recreate /boot & GRUB, how do I recreate the proper boot sectors on the USB?  Do I just use "make-grub" and then copy over the backed-up files?

(3) With Ubuntu on my desktop and GRUB on USB, if I'm mod'ing GRUB so's I could boot any of several ISO's, will I be able to put that USB into another machine (a Mac or PC) and boot one of the ISO's?  That's kind of what I was looking for...

(4) You know if there's any way to do a casper-rw if using an ISO of say, Ubuntu?

/DA

[Edited for clarity/ added a question]

---

### Post by oldfred on 2013-08-12
I have not tried copying entire boot partition to another drive. But I do add boot stanzas for internal installs to my flash drives. But UUID on flash drive will be different from UUID on hard drive and then it depends on how you copy or want to boot from If you want to use the kernel in a boot partition on a flash drive then grub must refer to partition on flash drive but install must reference UUID on hard drive. When /boot is separate boot stanzas have two UUID, one for kernel and grub and one for where install is. Most have same UUID as boot is a folder inside root.

I have done this but it then is just a separate grub boot, not using any kernel.
I actually now use gpt for all new devices, both hard drives and flash drives. But you can use MBR(msdos).

 Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

More links all essentially explaining the same process.

 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition if grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

I do not use persistence as I have a full install in a 8GB partition on my 16GB flash drive. I then use the remaining 8GB for data which includes some more ISO that I boot using the grub from the install.

---


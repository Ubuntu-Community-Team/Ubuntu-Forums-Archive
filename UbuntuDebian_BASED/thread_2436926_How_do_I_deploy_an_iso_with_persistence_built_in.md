---
title: "How do I deploy an iso with persistence built in?"
date: 2020-02-15
forum: Ubuntu/Debian BASED
---

### Post by lhh29936 on 2020-02-15
I have a Linux app that must be run from an OS on a USB stick as it is a disk/partition backup/clone app. I've created an iso built from a pared down version of Ubuntu 16.04 that works well. I want to distribute this to new Linux users and have the ability to update the app without the user needing to download an entire new iso, just download the app. I haven't figured out how to deploy an iso that has persistence already built in. I've tried with mkusb but can't figure out how to deploy the results (the multiple partitions). The app is designed for new linux users so I don't want to burden them with mkusb.

Could a wget function do the update?

Thanks in advance,
Larry

---

### Post by SeijiSensei on 2020-02-15
Is there some reason you can't just distribute the app itself [as a .deb]("https://packaging.ubuntu.com/html/packaging-new-software.html") and let your users install it on top of a normal Ubuntu distribution?

Also, standard support for 16.04 ends next year. You'd be better off building an ISO starting with 18.04.

---

### Post by lhh29936 on 2020-02-15
Thanks for the reply. [FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#000000] [/COLOR][/FONT]The app is a disk/partition cloning app so the partitions/disk must be unmounted for it to function. That is why what's being deployed as an iso with a minimal Ubuntu and the app pre-installed. The object is to have the end-user burn it to a USB once and then be able to update the app without having to burn a new iso to the USB.

---

### Post by sudodus on 2020-02-15
Maybe you can use a new feature or Ubuntu 19.10 and newer versions (and if you want a light-weight system, suitable for a USB pendrive, Lubuntu or Xubuntu), that makes it easier to create a persistent live drive.

Actually all you have to do is edit the iso file with sed in order to make it such that a persistent live drive will be created, when cloned to a USB pendrive and booted the first time.

Replace exactly 12 characters with exactly 12 other characters:
```

sed 's/quiet splash/persistent  /' lubuntu-19.10-desktop-amd64.iso > persistent-lubuntu-19.10-desktop-amd64.iso

sed 's/quiet splash/persistent  /' focal-desktop-amd64.iso > persistent-focal-desktop-amd64.iso

```

So the end user

1. downloads this 'persistent' iso file
2. clones it with 'any' cloning tool
3. boots into it
4. installs your application (via a tarball, debian file, PPA ..., whatever method you choose)

PPA is good for the end user, because it makes it easy to update & upgrade your tool. But you have to set up the PPA, which is a bit difficult.

[hr][/hr]
If you want to make it more convenient for the end user, you can create (a small) partition behind the cloned image, and then boot into it, install your application, make a [compressed] cloned image of the persistent live system with your application and distribute that [compressed] cloned image.

[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

An alternative, that might also be fairly portable ([installed into a USB pendrive](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)) is to create an installed OEM (installed) system where your application is installed, make a [compressed] cloned image and distribute that [compressed] cloned image.

[Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

You can use the Do It Yourself method too according to the following link

[Do it yourself - with the extraction method](https://help.ubuntu.com/community/Installation/iso2usb/diy)

---

### Post by lhh29936 on 2020-02-16
@sudodus, thanks for your reply. The app is targeted to new Linux users and is a disk/partition cloning app. The concept is to make it as easy as possible for them.The app itself is 22Mb, while the current iso, including the app, is 550Mb. Due to the rather small size of the iso, it might be easier to just have them download a new iso when there's an update and burn it to a USB.

---

### Post by sudodus on 2020-02-16
Yes, for new Linux user it might be easier to just have them download a new iso when there's an update and burn it to a USB.

But for slightly more experienced users with a slow or expensive internet connection, you might offer the application program via a tarball, debian package or PPA. It should not be too difficult, particularly if you have some kind of automatic system, that checks for updates, when connected to the internet.

---

### Post by lhh29936 on 2020-02-17
As a long time Linux user, I have to agree with you. However, all the info I've found is confusing about how to create a persistent partition and how to handle dependence and paths. The app is currently installed in the /home folder. How do I create a persistent folder for it? I just don't understand the relationship of the persistent partition to the iso. Is there a tutorial you can point me to that explains it in clear terms? This is my first attempt at deploying an app so I'm really a newbie even though I've been using Linux for 10 years.

Thanks for your input.

---

### Post by lhh29936 on 2020-02-17
@sudodus, maybe I'm confused. Here's the situation:  The iso is bootable and has a minimal version of Ubuntu and the app. The end-user downloads the iso and burns it to a USB. The user reboots to the USB to run the app. It doesn't get installed to a HD or SSD. I don't want the end-user to have to create a partition on the USB to download an updated app file to, so my thoughts are that I need to deploy the iso with the persistent partition already created or possibly a write a wget routine so the iso handles it internally.

What are your thoughts?

Larry

---

### Post by sudodus on 2020-02-17
Are you asking how ***you*** should do it and how to make it easy for a beginner with Linux? Or how to explain for a beginner how to do it?

With Ubuntu and the Ubuntu family flavours of version 19.10 and newer, it is easy.

1. Add the boot option persistent

2. Provide a **file** with the name **casper-rw** or a **partition** with the label **casper-rw**. A file should reside in a FAT32 file system and the size is limited to 4 GiB. A partition is only limited by the size of the drive.

Then, when you boot the live Ubuntu system, it will grab the casper-rw and make an overlay system with the root (that is in RAM), and you have a persistent live system. In such a system the /home directory will be stored in the casper-rw file or partition. I make tools for it, but I think you want to understand how to do it.

If you wish, you can add a **file** with the name **home-rw** or a **partition** with the label **home-rw** alongside casper-rw, and in such a system the content of the home directory will be saved there.

So I think ***you*** can and should do these things (with or without tools.)

**But and end user, particularly a beginner with Linux, should probably get a system, that is prepared by you**, so that the installation and maintenance should be rather easy (without manual messing with casper-rw or home-rw files or partitions). And such a system might be a cloned image of a persistent live system with your tool already installed and with an easy to learn or automatic mechanism to check for and perform updates.

---

### Post by sudodus on 2020-02-17
> **lhh29936 said:**
> @sudodus, maybe I'm confused. Here's the situation:  The iso is bootable and has a minimal version of Ubuntu and the app. The end-user downloads the iso and burns it to a USB. The user reboots to the USB to run the app. It doesn't get installed to a HD or SSD. I don't want the end-user to have to create a partition on the USB to download an updated app file to, so my thoughts are that I need to deploy the iso with the persistent partition already created or possibly a write a wget routine so the iso handles it internally.

What are your thoughts?

Larry

Yes, this is very similar to the image files, that I created a few years ago with mkusb installed according to [this link](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

---

### Post by sudodus on 2020-02-17
How detailed help do you need? If you upload your tool (22 MB) or your system image with the tool (550 MB) somewhere, I can download it, try to use it and maybe I can suggest some improvement, maybe even upload something that you can try to use and compare to your system.

By the way, is your tool easier to use compared to [Clonezilla](https://clonezilla.org)?

---

### Post by lhh29936 on 2020-02-17
@sudodus - one of my testers has a machine that won't boot a kernel newer than the 4.15 series, so I've been sticking with a Ubuntu 16.04 base. It's a Thinkpad, not sure what series but he's pretty Linux literate. If he's having problems with newer kernels, it's something I have to take into account. 

Let me see if I'm understanding what you proposed as a method for me to provide a ready for upgrade app using mkusb.
1.  Use the p option to create a persistent partition
2.  Create an img from the result of step 1.

---

### Post by lhh29936 on 2020-02-17
@sudodus, I sent you a PM with login info to download my stuff.

Larry

---

### Post by sudodus on 2020-02-18
Thanks for the PM with details to give me an opportunity to get your files and try to make a persistent live drive.

- I cloned from the iso file to a USB pendrive. It works for me both in UEFI mode and BIOS mode.

- I could not make the program file work in a standard Lubuntu 16.04.6 LTS system. There was a segmentation error.

- I could make a persistent live drive with your foxclone iso file, that boots in BIOS mode. **If you wish**, I can upload it for you to test. (I can upload a Lubuntu 16.04.6 LTS persistent live system too, and it works both in BIOS and UEFI mode.)

- But I could ***not*** make a persistent live drive with your foxclone iso file, that boots in UEFI mode.

There is something in the boot structure for UEFI, that does not match that of Ubuntu (and Lubuntu and the other community flavours). I spent a considerable amount of time trying to find a way to get around it, but failed.

[B]I think it is important to have a system that boots both in UEFI mode and BIOS mode. So I am sorry, but I don't know how to make such a persistent live drive using your iso file.
[/B]
- The easy alternative for you is to let people download new iso files, when they need a new version of your tool.

- An alternative is to create an installer system for your tool, that works in a light-weight flavour of Ubuntu (Lubuntu or Xubuntu) for people who prefer that to downloading a whole new iso file from you. We assume that those people can create their own persistent live drives using for example Lubuntu.

- A more difficult alternative is to make the UEFI boot system in your iso file such that it works more like that of Ubuntu, so that persistence will work also in UEFI mode. [An Ubuntu system and many other operating systems work in UEFI mode when extracted from the iso file to a FAT32 file system](https://help.ubuntu.com/community/Installation/iso2usb#For_an_UEFI_only_boot_flash_drive_you_need_no_installer). But the system in your iso file does not. If you can make that work (without destroying the ability to boot in BIOS mode), I can help you make a persistent live system that works both in BIOS mode and UEFI mode.

---

### Post by oldfred on 2020-02-18
Newest version of Ubuntu does not work with extracted method. The added a couple of links which do not work in FAT32 partitions.

Links in FAT32 error:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534)

---

### Post by sudodus on 2020-02-18
> **oldfred said:**
> Newest version of Ubuntu does not work with extracted method. The added a couple of links which do not work in FAT32 partitions.

Links in FAT32 error:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534)

Thanks for telling us, @oldfred.

Is this bug only affecting Focal so far?

The extraction method was good and has worked for years. Let us add heat to the bug report and push for a bug-fix so that those links will not be necessary.

---

### Post by oldfred on 2020-02-18
@sudodus
Have not tried extracted ISO for ages. Only tried it with 20.04 as I have one computer with only one drive and wanted to update it from old install. It also has 18.04, but is primarily a Windows computer for TV use as Linux did not (then) support most of the DRM restricted sites.

I normally just use grub2's loopmount to install from one drive to another. Is fast from RAM to drive. 

The only small USB flash drive I had was an old USB2 drive. Not using that again as extremely slow. I had forgotten how slow USB2 was. 
Decided to update my system's M2 SATA SSD drive with an NVMe drive. But put SATA SSD drive into a external enclosure. Makes for a faster larger external drive. Have so many larger flash drives now, will probable not buy any more.
Has full Ubuntu and will see if I can use it on my system to install like I do with my two drive systems using grub2's loopmount.

---

### Post by lhh29936 on 2020-02-18
@sudodus, which is the lightest, xubuntu or lubuntu? Whichever is lighter, I'll use to try and recreate the system.

Larry

---

### Post by lhh29936 on 2020-02-18
@sudodus - decided to try and rebuild with lubuntu 18.04 base. Will let you know when it's ready for you. I'll mark this thread as solved and start a new one specific to lubuntu base.

---

### Post by sudodus on 2020-02-18
> **lhh29936 said:**
> @sudodus, which is the lightest, xubuntu or lubuntu? Whichever is lighter, I'll use to try and recreate the system.

Larry

In 16.04 LTS and 18.04 LTS I think Lubuntu is slightly lighter. In Focal to become the next LTS release there is not much difference.

> **lhh29936 said:**
> @sudodus - decided to try and rebuild with lubuntu 18.04 base. Will let you know when it's ready for you. I'll mark this thread as solved and start a new one specific to lubuntu base.

The problem with your current iso file to make a persistent live system is not due to the version, but to the method that you create the boot mechanism for UEFI. You may have the same problem when you start from Lubuntu 18.04.x LTS.

So what you could do is to simply do what I did in the demo examples, that I referred to in an earlier post: Do not tamper with the iso file.

- Create a persistent live drive, which is well tested and works with mkusb. Choose an MSDOS partition table, because it will be easier to extract to a drive of different size compared to the master drive, where it was created.

- Install your tool, check that it works in the persistent live system.

- In order to get a minimal sized compressed image file you should overwrite all free space in the file systems with zeros. (When booted from another drive, it can be done by writing zeros to a file until each file system is full, and then remove those files). Then compression will work fairly well (clone with dd and compress with xz to 'file.img.xz').

- Create a compressed image file of the persistent live system, check that it works as expected, when you extract from the image to another USB pendrive.

- Later on you can create an installer (tarball or deb file or PPA) for your tool, an installer that works in Lubuntu and Xubuntu. This way users need not download a whole iso file in order to install and/or update your tool.

[hr][/hr]
Edit:

But your current iso file is small and looks quite nice. I think you can start by distributing your tool with this current iso file. Then you can work with a persistent live system as a possible next generation.

---

### Post by lhh29936 on 2020-02-18
@sudodus - I'm using grub-mkimage in a script to create the EFI partition as follows:

truncate -s 4M $BOOT_IMG
mkfs.vfat $BOOT_IMG
mkdir -p $BOOT_IMG_DATA/EFI/boot


grub-mkimage \
    -C xz \
    -O x86_64-efi \
    -p /boot/grub \
    -o $BOOT_IMG_DATA/EFI/boot/bootx64.efi \
    boot linux search normal configfile \
    part_gpt btrfs fat iso9660 loopback \
    test keystatus gfxmenu regexp probe \
    efi_gop efi_uga all_video gfxterm font \
    echo read ls cat png jpeg halt reboot


mcopy -i $BOOT_IMG -s $BOOT_IMG_DATA/EFI ::

Is there a better way?

---

### Post by sudodus on 2020-02-18
> **oldfred said:**
> @sudodus
Have not tried extracted ISO for ages. Only tried it with 20.04 as I have one computer with only one drive and wanted to update it from old install. It also has 18.04, but is primarily a Windows computer for TV use as Linux did not (then) support most of the DRM restricted sites.

I normally just use grub2's loopmount to install from one drive to another. Is fast from RAM to drive. 

The only small USB flash drive I had was an old USB2 drive. Not using that again as extremely slow. I had forgotten how slow USB2 was. 
Decided to update my system's M2 SATA SSD drive with an NVMe drive. But put SATA SSD drive into a external enclosure. Makes for a faster larger external drive. Have so many larger flash drives now, will probable not buy any more.
Has full Ubuntu and will see if I can use it on my system to install like I do with my two drive systems using grub2's loopmount.

I had to check with yesterday's daily iso file of Ubuntu Focal Fossa.

It works in UEFI mode, when extracted from the iso file (with rsync) to a FAT32 partition. I did nothing extra (no flags etc). There were some complaints (some error output), but after a few more seconds I reached the desktop, and it seems OK.

Please test it yourself, @oldfred. That bug seems to have died without any explicit action related to the bug report :-)

I followed my instructions at [help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy), but I think it works with any tool to create the FAT32 partition and to extract the content.

---

### Post by sudodus on 2020-02-18
> **lhh29936 said:**
> @sudodus - I'm using grub-mkimage in a script to create the EFI partition as follows:

truncate -s 4M $BOOT_IMG
mkfs.vfat $BOOT_IMG
mkdir -p $BOOT_IMG_DATA/EFI/boot


grub-mkimage \
    -C xz \
    -O x86_64-efi \
    -p /boot/grub \
    -o $BOOT_IMG_DATA/EFI/boot/bootx64.efi \
    boot linux search normal configfile \
    part_gpt btrfs fat iso9660 loopback \
    test keystatus gfxmenu regexp probe \
    efi_gop efi_uga all_video gfxterm font \
    echo read ls cat png jpeg halt reboot


mcopy -i $BOOT_IMG -s $BOOT_IMG_DATA/EFI ::

Is there a better way?

I think it is good way, quite simple, and the iso file works well. The 'only' problem (at least with 16.04.6) is that we don't know any way to create a persistent live drive with the system in the iso file, that boots also in UEFI mode. 

I'm sorry, but I don't know what is missing or 'wrong'. But the senior expert about UEFI boot at the Ubuntu Forums, @oldfred, has found our thread. Let us hope that he can advice how to modify your method.

---

### Post by TheFu on 2020-02-18
> **lhh29936 said:**
> @sudodus, thanks for your reply. The app is targeted to new Linux users and is a disk/partition cloning app. The concept is to make it as easy as possible for them.The app itself is 22Mb, while the current iso, including the app, is 550Mb. Due to the rather small size of the iso, it might be easier to just have them download a new iso when there's an update and burn it to a USB.

550MB!!!!  Perhaps use a smaller distro?  TinyCore fits in 16MB with an X/Windows GUI.  [http://tinycorelinux.net/](http://tinycorelinux.net/)  Your program is bigger than the OS!  Apps are packaged w/ the TCZ format and can be preinstalled.

Just something to consider.  Actually, mkusb w/TinyCore might be an interesting project.

---

### Post by sudodus on 2020-02-19
> **TheFu said:**
> 550MB!!!!  Perhaps use a smaller distro?  TinyCore fits in 16MB with an X/Windows GUI.  [http://tinycorelinux.net/](http://tinycorelinux.net/)  Your program is bigger than the OS!  Apps are packaged w/ the TCZ format and can be preinstalled.

Just something to consider.  Actually, mkusb w/TinyCore might be an interesting project.

@TheFu, Interesting :-)

Do you know how to create a TCZ package, and would you help explaining? Or even better, would you have time to do it?

---

### Post by TheFu on 2020-02-19
[http://tinycorelinux.net/architecture.html](http://tinycorelinux.net/architecture.html)
[http://tinycorelinux.net/arch_copymode.html](http://tinycorelinux.net/arch_copymode.html)

---

### Post by lhh29936 on 2020-02-19
@sudodus - I'm wondering whether building the iso on a drive with an msdos partition table or a gpt partition table makes a difference. I've building on a drive with a gpt partition table. Tomorrow I'll throw one of my spare drives into my development machine and set it up with an msdos partition table and move everything to it. Then I'll do a build and see if there's any difference. You already have a build from a gpt partition so I'll put a build from an msdos partition table up on the FTP site. Will let you know when it's up there.

---

### Post by sudodus on 2020-02-20
I *think* it should make no difference.

---

### Post by lhh29936 on 2020-02-22
@sudodus - I put a new iso on the ftp site. See if it's any better please

---

### Post by sudodus on 2020-02-23
> **lhh29936 said:**
> @sudodus - I put a new iso on the ftp site. See if it's any better please

Yes, I can manage this iso file dated 2020-02-22 with **mkusb**. I can make a persisstent live drive, that boots both in EFI mode and BIOS mode. I use the default settings in mkusb. This makes a GUID partition table (GPT). I also made a compressed image of this system, [FONT=Courier New]**foxclone30_2020-02-22_persistent-gpt-8GB.img.xz**[/FONT], that I uploaded to your FTP server.

Unfortunately the persistent live system with MSDOS partition table of your iso file does not boot in UEFI mode. This means that there is a complication, when creating a USB boot drive from the image: The end users must fix the backup partition table of the GPT. it is done automatically, it they use mkusb to {extract + clone} from the compressed image file to a USB pendrive. Otherwise they can use the tool [FONT=Courier New]**gdisk**[/FONT] manually or via the shellscript [gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix).

But it might be difficult to make it work from Windows.

If you install mkusb in the Foxclone operating system, the end users need not install it, and can use it also to create a persistent live system (of Foxclone). if they wish.

[hr][/hr]
I uploaded also a small tarball with three shellscripts, that I use to create compressed image: [FONT=Courier New]**mkpersimage**[/FONT] that calls [FONT=Courier New]mkxzimage[/FONT] that calls [FONT=Courier New]ender[/FONT]. They should be in PATH.

There is also a small file with the md5sums of the compressed image and the small tarball.

So in the future you should be able to use these three shellscripts to create your own compressed images of persistent live drives made by mkusb.

---

### Post by lhh29936 on 2020-02-23
@sudodus, Thanks for your help. I'll let you know if there are any other problems.

---

### Post by lhh29936 on 2020-02-24
@sudodus, I still don't understand how this would enable the replacement of the foxclone executable which is located in the /usr/local/sbin folder. Would the end-user place the new executable in the casper-rw partition or the usbdata partition? Do I need to create a /usr/local/sbin folder in the casper-rw partition? I've done a lot of reading but none that I've found explains how it all works. Can you point me to a tutorial that explains how it works rather than how to make it?

---

### Post by sudodus on 2020-02-25
The persistent live system uses an overlay method, so that you need not worry about where to put the updates. When you install or update something in the normal root partition (for example in /bin, /usr, /etc or in /home), *it will actually be stored automatically* in a corresponding location in the casper-rw partition. The important thing is that you shutdown or reboot the computer in a correct way and let the process finish before you unplug the USB pendrive.

Try it and let me know if it works for you. Good luck :-)

---

### Post by lhh29936 on 2020-02-25
So when the user wants to install a new update does it go into the casper-rw partition or the original location?

---

### Post by C.S.Cameron on 2020-02-25
Only the casper-rw and/or home-rw partitions are writable.
(With latest 20.04 daily, the persistent partition can be labeled "writable" rather than "casper-rw").

---

### Post by lhh29936 on 2020-02-27
@sudodus - I'm having trouble running your scripts. I used mkusb to create the persistent on /dev/sdd. After I reboot and insert the USB I can see the partitions are mounted. Here's what I'm getting when I run "sudo bash mkpersimage /dev/sdd". Yes, I did make sure that the folder with the scripts is in the path.



EDIT: Had to manually create mount points and install espeak. Also had to set the executable bit on mkxzimage and ender. It's working now but creating a much larger .img.xz when run against the same foxclone.iso. When I ran it, the result ended in 16GB.img.xz instead of 8GB.img.xz. My .img.xz is 1.1GB, yours is 787.7MB. I compared both yours and mine in Gparted after burning each to a USB and they both have the same partition sizes and use the same amount in each partition.  Can you explain what might of happened?

---

### Post by sudodus on 2020-02-28
> **lhh29936 said:**
> @sudodus - I'm having trouble running your scripts. I used mkusb to create the persistent on /dev/sdd. After I reboot and insert the USB I can see the partitions are mounted. Here's what I'm getting when I run "sudo bash mkpersimage /dev/sdd". Yes, I did make sure that the folder with the scripts is in the path.

EDIT: Had to manually create mount points and install espeak. Also had to set the executable bit on mkxzimage and ender. It's working now but creating a much larger .img.xz when run against the same foxclone.iso. When I ran it, the result ended in 16GB.img.xz instead of 8GB.img.xz. My .img.xz is 1.1GB, yours is 787.7MB. I compared both yours and mine in Gparted after burning each to a USB and they both have the same partition sizes and use the same amount in each partition.  Can you explain what might of happened?

0. Sorry for the extra trouble because I forgot to check and tell you about all the dependencies.

1. I would think that the result ended in 16GB.img.xz because you created the drive in a 16 GB pendrive and did not shrink and/or move the casper-rw partition and the usbdata partition to fit in an 8 GB pendrive (with some margin (say within 7.7 MB) because many pendrives are undersized (slightly below the nominal size)).

2. The difference in compressed size is because of the bigger size of the uncompressed image and *maybe partly* because of things you added to the casper-rw partition. I understand that you ran mkpersimage (and checked that the zeroising of free space worked as expected).

---

### Post by lhh29936 on 2020-02-28
> **sudodus said:**
> 0. Sorry for the extra trouble because I forgot to check and tell you about all the dependencies.

1. I would think that the result ended in 16GB.img.xz because you created the drive in a 16 GB pendrive and did not shrink and/or move the casper-rw partition and the usbdata partition to fit in an 8 GB pendrive (with some margin (say within 7.7 MB) because many pendrives are undersized (slightly below the nominal size)).

2. The difference in compressed size is because of the bigger size of the uncompressed image and *maybe partly* because of things you added to the casper-rw partition. I understand that you ran mkpersimage (and checked that the zeroising of free space worked as expected).


I used the same iso as I sent to you, nothing added. If the partition sizes between yours and mine are the same as well as the space used in each partition, I still don't understand the difference in size. Is the amount of compression based on the amount of free space? I'm going to try again tomorrow and will shrink both casper-rw and usbdata to 2GB before running mkpersimage. Will let you know how it turns out.

---

### Post by sudodus on 2020-02-29
Yes, the amount of compression depends on the amount of free space. But I think the difference is rather small. So there is probably some other thing too. Maybe you did not write zeros to all the free space in all the partitions. Or maybe you did not move the partitions, so that there was some 'hole' between the partitions with unallocated drive space, and that space was not zeroised.

---

### Post by lhh29936 on 2020-02-29
Here's what I did today. Took the same original iso that you used and burned it to a 16GB flash drive (the smallest I have). Ran mkusb then opened Gparted and shrank casper-rw and usbdata from 6+GB to 2GB then moved them so they contiguous .There was 9.63GB unallocated space at the end of the drive. I then ran your scripts and that resulted in dd_sda-5GB.img.xz that was 1.7GB in size. It seems like the zeroing isn't working. Any suggestions?

---

### Post by sudodus on 2020-02-29
You can zeroise the following way:

- Boot from another drive (not the persistent live drive)
- Mount a partition with a file system (read-write)
- cd to its mountpoint
- Write zeros until the partition is full: [FONT=Courier New]**sudo dd if=/dev/zero of=BLANK bs=4096**[/FONT]
- Delete the file [FONT=Courier New]**BLANK**[/FONT]
- cd from the mountpoint
- Unmount the partition
- Do the same for the next partition ...

This is implemented in [FONT=Courier New]**mkpersimage**[/FONT] and works for me. Maybe something is still missing in your computer for it to work. But you should be able to look at the code and use the method 'manually'.

---

### Post by lhh29936 on 2020-02-29
sudodus, when I run the script I'm getting the following error on each of the partitions:
```
dd: error writing '/mnt/sd1/blank': No space left on device 
```

Is this normal?  I'm going to try doing it manually in the morning.

Larry

---

### Post by sudodus on 2020-03-01
Yes, this is the normal output, when there is no space left on the device (the partition, that you mounted, and where you wrote the file 'blank'). Then delete the file, and you have zeroised the free space :-)

---

### Post by lhh29936 on 2020-03-01
sudodus - Doing the zeroing manually worked. I reduced the size of casper-rw and usbdata to 2GB before running the "[COLOR=#000000][FONT=&amp]**sudo dd if=/dev/zero of=BLANK bs=4096" **on the casper-rw, usbdata, and usbboot partitions mounted one at a time. I then ran mkxzimage and got [/FONT][/COLOR]dd-sda-6GB.img.xz which is 638.8MB. I can live with that. I'll see how it runs and let you know.

Edit: It wouldn't boot even in legacy boot.

---

### Post by sudodus on 2020-03-02
Did the original persistent live drive boot?

How did you create the persistent live system (the master system before creating the image)? Did you use the default GPT or an MSDOS partition table)? You need GPT to boot also in UEFI mode.

After extraction and cloning: Did you fix the backup partition table (either automatically by using mkusb to create the USB boot drive from the compressed image or by using gpt-fix or manually with gdisk)?

---

### Post by lhh29936 on 2020-03-02
Your [COLOR=#000000]persistent live drive [/COLOR] booted  Legacy only. Used mkusb to create the master image on USB with GPT partition table then used gpt-fix to make sure the backup partition table was fixed. I [COLOR=#000000]reduced the size of casper-rw and usbdata to 2GB and made sure there was no space between the partitions before running the "[/COLOR][COLOR=#000000][COLOR=#000000]**sudo dd if=/dev/zero of=BLANK bs=4096" **on the casper-rw, usbdata, and usbboot partitions mounted one at a time. I then ran mkxzimage. Should I have run gpt-fix after burning the .img file to the GPT partitioned USB?

NOTE: I'll be off-line for a week starting tomorrow. My sister is flying in from California and will be staying with me. We have a lot of catching up to do.[/COLOR][/COLOR]

---

### Post by sudodus on 2020-03-02
> **lhh29936 said:**
> Should I have run gpt-fix after burning the .img file to the GPT partitioned USB?


**Yes, this is** [the only instance] **where you need gpt-fix**: To fix the gpt backup partition table in the final USB boot drive. The reason is that the final drive's size is most likely different from the size of the original system from where you created the compressed image file.

---

### Post by lhh29936 on 2020-03-02
Thanks, I'll let you know how it's going when I'm back on-line next week.

---

### Post by sudodus on 2020-06-20
I tested today, and the current version of mkusb, 12.5.7 can create persistent live drives from Foxclone iso files, [FONT=Courier New]**foxclone34-02.iso**[/FONT], so if you wish you can provide upgrading to your end users without downloading the whole system. See the attached screenshot.

-o-

I tested also by adding mkusb, and it works.

---

### Post by lhh29936 on 2020-06-20
@sudodus, thanks for letting me know. I wasn't aware of a new version of mkusb. I'll definitely talk with the foxclone developer about it.

Also, thanks for your continued interest in the project. In addition to the deployment end of the project I'm also the web developer and getting ready to update the website. It all keeps this 71 year old guy occupied.

---


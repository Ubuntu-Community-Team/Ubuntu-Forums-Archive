---
title: "Installation on 2nd drive on a EFI/secure boot system"
date: 2014-02-19
forum: Ubuntu Development Version
---

### Post by emk on 2014-02-19
I want to install Trusty on a system with EFI / secure boot, but **not** on the first disk. I'd rather prefer to have it from a USB device (stick or USB drive) which I would like to be portable.

Bottom line, I want to have a portable installation - not in a squashfs or other layers in-between - on USB for EFI systems. So far, the EFI install instructions all assume that you want to install on disk #1, which should stay as it was to make the install portable. Trusty mainly for the fact that it's the newest and should support this best, as of tomorrow, it will have feature freeze, so no moving target.

Any ideas?

---

### Post by grahammechanical on 2014-02-19
I really do not understand the problem. You want to install Trusty on a USB memory stick. Where is the problem? That should be no different from installing any stable version of Ubuntu on to a memory stick. I have Trusty Edubuntu installed on a 16GB memory stick. I used Startup Disk Creator and I set it up with persistence.

The only issue a user has in using a "portable" install of Ubuntu is whether the boot system (BIOS/UEFI) is set to boot from an opperating system on a USB port before booting from an OS on a hard disk.

As I say, I do not understand your problem.

Regards.

---

### Post by ventrical on 2014-02-19
> **emk said:**
> I want to install Trusty on a system with EFI / secure boot, but **not** on the first disk. I'd rather prefer to have it from a USB device (stick or USB drive) which I would like to be portable.

Bottom line, I want to have a portable installation - not in a squashfs or other layers in-between - on USB for EFI systems. So far, the EFI install instructions all assume that you want to install on disk #1, which should stay as it was to make the install portable. Trusty mainly for the fact that it's the newest and should support this best, as of tomorrow, it will have feature freeze, so no moving target.

Any ideas?

  What I do is first have your bootable trusty.iso on a 2GB USB pendrive.  ( I do not use persistence as recommended by grahamechanical). Then have your empty formated 16GB or 32GB USB drive ready.  Then , what I do, is remove the hdd. At this point the 2GB drive will boot by default.  It will auto detect the other 16/32GB USB as your hdd. Then, just install ubuntu as you would  as if it were an hdd.  I have mine working on a B75MA-P45 with UEFI. I have, of course, disabled the UEFI.  It is a Ver 3.0 USB and works faster than  most hdds and is portable. There will sometimes be problems if you do a set-up on a machine with Intel Graphics adapter and then try to run it on a machine with ATi Graphics.. but for the most part , it jockeys correctly (for switching graphics adapters) on my machines.

  Others use persistence (as suggested by other) but I have found that this can really slow down the desktop experience.

Regards..

---

### Post by oldfred on 2014-02-19
Ubuntu will boot in BIOS or UEFI from gpt partitioned drives. And I have formatted flash drives with gpt and booted in BIOS mode. But have not actually booted with UEFI.
To have a full install on an external drive you have to partition with gpt. You can use gparted or gdisk. 
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
Or with gdisk
      
 sudo apt-get install gdisk
sudo gdisk /dev/sdb
Command (? for help): 

If sharing a flash drive with Windows you would have to have the first partition as NTFS, but otherwise for UEFI boot, the efi partition should be first and then the partitions you want for Ubuntu / (root), /home or data depending on size of your flash drive.

Then using Something Else or manual install format partitions and choose which partition to mount as / and other. 
Be sure on partitioning screen to choose to install the grub2 boot loader to sdb (or whatever drive is).

Whether hard drive or flash drive, install to any second drive is the same.

 **Two Drive UEFI installs**
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

---

### Post by emk on 2014-02-20
[QUOTE=grahammechanical]I really do not understand the problem. You want to install Trusty on a USB memory stick. Where is the problem? That should be no different from installing any stable version of Ubuntu on to a memory stick. I have Trusty Edubuntu installed on a 16GB memory stick. I used Startup Disk Creator and I set it up with persistence.

The only issue a user has in using a "portable" install of Ubuntu is whether the boot system (BIOS/UEFI) is set to boot from an opperating system on a USB port before booting from an OS on a hard disk.[/QUOTE]
No, this is not what I want. I thought the additional information was clear. I **do not** want to just simply install a Ubuntu distro on a USB stick. Others have already mentioned potential downsides to that, there are more. This is good for a limited live system, but nothing else.

I want a standard install to a portable medium which can be booted on a PC with EFI / secure boot. *Any* PC, if possible. The USB medium should be able to boot without BIOS / EFI changes, just by changing the boot order temporarily with [F12].

Every PC sold now has EFI and secure boot together with Windows 8. The USB medium should boot on these PCs without having to change their settings. You plug the stick  in, reboot with [F12], choose the stick and have Ubuntu. If you shut down and reboot, you get the normal Windows 8 again with EFI and secure boot.

---

### Post by emk on 2014-02-20
> **ventrical said:**
> I have, of course, disabled the UEFI.
My use case are laptops where I might not even be able to change settings, just boot. But I give your ideas a try, maybe I can get this to work with enabled EFI/secure boot.
> Others use persistence (as suggested by other) but I have found that this can really slow down the desktop experience.
Yes, one of many reasons why persistence and live CDs are of limited value. Good for a quick change of settings or rescue, but not more.

---

### Post by emk on 2014-02-20
> **oldfred said:**
> Ubuntu will boot in BIOS or UEFI from gpt partitioned drives. And I have formatted flash drives with gpt and booted in BIOS mode. But have not actually booted with UEFI.

Even if you didn't try with UEFI, it looks like at least one of your suggestions and links should be able to succeed. Thanks! If I find a painless way to install, I post it here. I surely can't be the only one who wants to boot Ubuntu on a machine where you have little to no options to change something.

---

### Post by ventrical on 2014-02-20
> **emk said:**
> My use case are laptops where I might not even be able to change settings, just boot. But I give your ideas a try, maybe I can get this to work with enabled EFI/secure boot.

Yes, one of many reasons why persistence and live CDs are of limited value. Good for a quick change of settings or rescue, but not more.


In this case then you can use <something else> (as suggested by OldFred) when the partitoner comes up after booting the trusty .iso and you should see the USB drive there and just choose that one and Ubuntu should install. Again , I know this is not exactly what you are looking for but on all the laptops I have  done this proceedure on I have always removed the physical hdd first.  The Ubuntu.iso seems to trick the PC into thinking that the USB is an actual hardrive and I have yet to have a fail using this manner and I have USB keys from 4 years ago that I installed this way that work on a dime.

 Yep .. even the USB ver 2.0 runs faster than most 7200 SATA hdds.

Regards..

---

### Post by ventrical on 2014-02-20
> **emk said:**
> No, this is not what I want. I thought the additional information was clear. I **do not** want to just simply install a Ubuntu distro on a USB stick. Others have already mentioned potential downsides to that, there are more. This is good for a limited live system, but nothing else.

I want a standard install to a portable medium which can be booted on a PC with EFI / secure boot. *Any* PC, if possible. 

As I said earlier, if you do the original install using a laptop with Intel Based graphics and then stick the key into a laptop with ATi graphics then there could be some problems on older machines, You can still get terminal but not desktop. Mostly older ATi. Otherwise it works just swell as a super_OS on most machines with different graphics. Perhaps this cycle may have solved that bug.

---

### Post by grahammechanical on 2014-02-20
Is there any difference technically between installing and booting Ubuntu from a USB memory stick or an external USB disk? I do not think so. I would not anticipate more problems trying it with Trusty Tahr then I would trying it with 13.10.
 
Mind you, I would use Nouveau as a way around the video driver not being suitable for the video adapter in the machine that the USB drive was being attached to. When we run a Ubuntu live session we use Nouveau. We do not set a specific video driver. Even then there are times when the nomodeset and other options are needed.

There would also be limitations on the data transfer rate of USB with USB 2 being slower than USB 3 and that may effect the user experience on certain machines. It is the hardware causing the limitation not the software installation.

I really do not see this thread as being appropriate for Ubuntu+1.

---

### Post by ventrical on 2014-02-20
> **grahammechanical said:**
> Is there any difference technically between installing and booting Ubuntu from a USB memory stick or an external USB disk? I do not think so. I would not anticipate more problems trying it with Trusty Tahr then I would trying it with 13.10.
 
Mind you, I would use Nouveau as a way around the video driver not being suitable for the video adapter in the machine that the USB drive was being attached to. When we run a Ubuntu live session we use Nouveau. We do not set a specific video driver. Even then there are times when the nomodeset and other options are needed.

There would also be limitations on the data transfer rate of USB with USB 2 being slower than USB 3 and that may effect the user experience on certain machines. It is the hardware causing the limitation not the software installation.

I really do not see this thread as being appropriate for Ubuntu+1.

 Perhaps you are correct that this thread is not topical to U+1, however, allow me first to attempt to answer some of your questions. 

 Yes .. USB ver 3.0 +  is much better and faster.  I mentioned ver 2.0 as it still is faster than most common hdds.

 Secondly, the OP was not asking about a live session. He wants to do a hard install on a USB stick with Trusty Tahr.  During the installation nouveau will be installed by default but there are some problems when swapping the USB stick out to a different box. Allow me to elaborate.  It means that if you take a normal SATA hdd and do an install of trusty on that SATA drive and that SATA drive is on a Dell machine with Intel graphics - and proceed to finish the instal : then: take the SATA drive out of the Dell and put it in a machine that had an ATi radeon graphics controller (or vis a versa) then there can be problems with borking lightdm, unity greeter etc. This same principle works on USB sticks which are swappable to other machines unless the machines are more current. 

Also , I think the OP is not talking about an External USB drive , but, rather a removable USB stick (which becomes an actual/virtual hdd ) when it is installed upon from a bootable .iso of Trusty (as which I just performed on by UEFI based machine *with* the physical hdd installed). I have used  yesterdays daily-current desktop-i386 and I have noticed that there is a performance lag already during the installation process but the *installation* on a 32GB Jet Transcend USB stick works exceptionally well. In the light that we are using trusty.iso as the system to be installed , then I think that this discussion is topical for U+1 until the OP has solved it  or oldfed has something to add.

 My Kindest Regards..

---

### Post by ventrical on 2014-02-20
@OP

 I tested my newly created Trusty from (Feb.19/14 daily-current)32GB USB Transcend Ver 3.0 on 5 different machines across 5 different graphics adapters, Intel, SandyBridge, nVidia 218/210, AMD/ATi HD 5450 etc... and I had one fail on a laptop with ATi Xpress 1250. It worked beautifully on all the other machines.

Also .. the reason to do these types of installs without hdd is because of GRuB. When the install is over it will pull in the partitions that are on the harddrive. However, you can install your USB stick in a machine that does not have a committed hdd and 

```


sudo update-grub

```

and this will correct the problem. Also, don't forget that if you install to USB  and have another hdd in that system that you will have to update the GRuB bootloader on that system also.

---

### Post by soum_axetuirk on 2014-02-20
1.Disable Ligacy USB support in BIos setting.
2.Make any USB bootable with "Universal Boot installer" or "Unetbootin".
3.now During boot must boot in to UEFI USB..
4.You will get a black GRUB menu.(it conferms tht you booted in EUFI mode.if colour is pink thn you booted in legacy mbr mode.)

Now you may install in to second drive or you may just use like that.

---

### Post by soum_axetuirk on 2014-02-20
A live OS runs actually from RAM.So no matter you are using 2.0 or 3.0 USB.
In 2.0 USB ,it may just take little more time to start.but after a system starts it doesnt matter you plugged your USB in 2.0 or 3.0
if you dont believe just remove the USB after starting of desktop.you can use your Ubuntu without problem.

---

### Post by ventrical on 2014-02-20
> **soum_axetuirk said:**
> A live OS runs actually from RAM.So no matter you are using 2.0 or 3.0 USB.
In 2.0 USB ,it may just take little more time to start.but after a system starts it doesnt matter you plugged your USB in 2.0 or 3.0
if you dont believe just remove the USB after starting of desktop.you can use your Ubuntu without problem.


The OP is talking about a committed , portable, USB stick in replacement of a physical hdd. No live session. Ubiquity/patitioner will work just fine for this proceedure.

Regards..

---

### Post by ventrical on 2014-02-20
@mod
maybe can put here if off topic:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by ventrical on 2014-02-20
Here is brief example of how I install system onto USB portable memory stick.

[http://www.youtube.com/watch?v=h8i67KksFlo&feature=youtu.be](http://www.youtube.com/watch?v=h8i67KksFlo&feature=youtu.be)

Regards..

---

### Post by cariboo on 2014-02-20
When doing a default install, whether on a usb thumb drive, or a regular HDD, the open source drivers for all 3 major graphics chipsets are installed. I have gnome-shell installed on a 16GiGB usb thumb drive, and have used it on systems with Nvidia graphics and Intel. Gnome-shell works the way it should, by just booting from the thumb drive, no matter what graphics chipset the system has.

---

### Post by emk on 2014-02-20
> **grahammechanical said:**
> I would not anticipate more problems trying it with Trusty Tahr then I would trying it with 13.10.
 
...

I really do not see this thread as being appropriate for Ubuntu+1.If there are no changes in "installer intelligence" for 13.10 to Trusty, I fully agree with this, maybe a mod can move the thread. I was hoping for some differences in Trusty compared to the older versions which would make it easier to set up such a system. Not a "more problems" issue, but a "less problems" one.

---

### Post by cariboo on 2014-02-20
> **emk said:**
> If there are no changes in "installer intelligence" for 13.10 to Trusty, I fully agree with this, maybe a mod can move the thread. I was hoping for some differences in Trusty compared to the older versions which would make it easier to set up such a system. Not a "more problems" issue, but a "less problems" one.

I'm not sure what problems you are referring to, but I would suggest you bring them to the [ubuntu-devel-dicuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list, if you want changes to be made, in the way the installer works. This is an unmoderated list, so it is open to anyone.

---

### Post by SuperFreak on 2014-02-20
> **ventrical said:**
> Here is brief example of how I install system onto USB portable memory stick.

[http://www.youtube.com/watch?v=h8i67KksFlo&feature=youtu.be](http://www.youtube.com/watch?v=h8i67KksFlo&feature=youtu.be)

Regards..

I notice in the video that the person disconnected his SSD. Is this necessary or just a precaution to avoid overwriting his install on the SSD?

---

### Post by ventrical on 2014-02-20
> **SuperFreak said:**
> I notice in the video that the person disconnected his SSD. Is this necessary or just a precaution to avoid overwriting his install on the SSD?


 No. It is not necessary - at least for my newer UEFI MoBo. It is necessary on machines .. say 2004-2006 or earlier.  I disconnect my SSD/HDD to better demonstrate to the noob how to achieve this with minimum brain cramps :) . It is also better to do it this way because then you eliminate GRuB problems on the USB stick. If a hdd is installed , then, during the installation , those other partitions will be amended to the GRuB menu on the USB stick. Then , when you boot on another box, that GRuB menu will still be there and you will have to take the extra step of 

sudo update-grub 

on both the USB stick and the hdd/SSD to parse out the extra entries.

Regards..

---

### Post by SuperFreak on 2014-02-20
Thanks,

---

### Post by ventrical on 2014-02-21
> **cariboo907 said:**
> When doing a default install, whether on a usb thumb drive, or a regular HDD, the open source drivers for all 3 major graphics chipsets are installed. I have gnome-shell installed on a 16GiGB usb thumb drive, and have used it on systems with Nvidia graphics and Intel. Gnome-shell works the way it should, by just booting from the thumb drive, no matter what graphics chipset the system has.


 I had some problems with graphics adapter cards when switching my portable USB during the raring and saucy cycle. There was a problem with the more legacy Dell Dimension desktops with Intel graphics adapter.  If you did an install on a USB using the Dell D and then tried to swap it out and then back into the Dell again it would bork the system (or graphical config files).

  It appears now  that this problem has been fixed with trusty. The boot sequence is correctly determining the proper video driver without borking the system. Even with a fail on one laptop , it was still able to correct, especially with troublesome ATi graphics cards.

 Sorry for off topic .. but this is good news all around , especially for those who are upgrading graphics cards  ..etc... I'll make a new post.

[http://ubuntuforums.org/showthread.php?t=2206946&p=12935688#post12935688](http://ubuntuforums.org/showthread.php?t=2206946&p=12935688#post12935688)

Regards...

---

### Post by SuperFreak on 2014-02-22
> **ventrical said:**
> No. It is not necessary - at least for my newer UEFI MoBo. It is necessary on machines .. say 2004-2006 or earlier.  I disconnect my SSD/HDD to better demonstrate to the noob how to achieve this with minimum brain cramps :) . It is also better to do it this way because then you eliminate GRuB problems on the USB stick. If a hdd is installed , then, during the installation , those other partitions will be amended to the GRuB menu on the USB stick. Then , when you boot on another box, that GRuB menu will still be there and you will have to take the extra step of 

sudo update-grub 

on both the USB stick and the hdd/SSD to parse out the extra entries.

Regards..


Just wondered if it is necessary to disconnect all drives or just the SSD where the OS and Grub are located? I have 2 data hard drives and I would prefer if possible not to have to disconnect all 3 drives

---

### Post by ventrical on 2014-02-22
> **SuperFreak said:**
> Just wondered if it is necessary to disconnect all drives or just the SSD where the OS and Grub are located? I have 2 data hard drives and I would prefer if possible not to have to disconnect all 3 drives


Yes .. that will work fine as long as your USB is set to boot. Even if you leave your SSD in, the Ubiquity partitioner will recognize both your USB flash and your SSD. There is a dialog bar at the bottom window of the partitoner with a DownArrow and clicking that will give you options where to install (be careful not to choose your data drives:) lol

  For the most part, this process is very stable all around with or wihtout hdds installed but I always like to keep the chanels clean. If there is any chance for the BIOS to produce a glitch, bug or fail then it is eliminated , usually, by removing  all hard drives off the motherboard.

  In earlier desktops/laptops it sometimes will not recognize the USB to be installed upon unless you remove the hdds.

---


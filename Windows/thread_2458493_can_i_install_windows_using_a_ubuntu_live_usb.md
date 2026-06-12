---
title: "can i install windows using a ubuntu live usb?"
date: 2021-02-25
forum: Windows
---

### Post by ianmcc1 on 2021-02-25
ive searched the forums but i cant find anything relating to my problem. 

my windows 10 system crashed - go figure

my win10 system crashed and was unable to recover it, i was in the middle of an update and we lost power due to bad weather, when the system restarted it was stuck in a boot up loop, recovery disk didnt work. so i used a ubuntu live usb to be able to get an os running. on a separate working PC i downloaded the windows media creation tool, and installed the win10 boot media to a usb. when i use the usb the bios screen loads, i boot from usb, a blank screen appears, the windows logo flashes for a split second and then the system reboots, resulting in a loop, i tried different usb ports, i use the same usb drive for the ubuntu live usb and ubuntu loads fine. so i know the drive works, and i would assume ubuntu needs the same bios settings to boot as win10 would. ive tried using the windows media kit, and a iso file using rufius to build the startup usb, nothing works. so, my question is can i use ubuntu live usb to load the windows iso into a partition on the hard drive? the computer doesnt have a cdrom. i wouldnt mind using ubuntu but my laser engraver and 3d printer software doesnt work with linux. i dont think anything in my bios has changed, but i can provide screen shots of the settings if that would help. i know this is a windows issue, and this is an ubuntu forum, but i have received zero help from the microsoft community, and im hoping i can get some guidance here. thank you all so much for reading, im frustrated and im about to shoot the computer in the face. 

i dont mind wiping the hard drive and starting over, and at this rate i would prefer it.  if you need any more information please let me know

cyberpower pc model c
motherboard: GA-AX370M-DS3H

---

### Post by howefield on 2021-02-25
Thread moved to the "*Windows*" sub forum for a better fit.

---

### Post by CelticWarrior on 2021-02-25
Any properly made Windows USB media should work. Typically when done with the Windows Media Creation tool it always works, never had a problem with those.

---

### Post by ianmcc1 on 2021-02-25
ive used the windows media creation tool in the past and havent had any problems back then, the bios picks up the usb drive in bios, tried both UEFI and standard options in the boot menu, but it doesnt work. i was hoping i could wipe the drive and use the ubuntu live usb to get an OS running, wipe the drive, download the windows ISO and extract it in a partition, if thats even possible. i have no problems installing ubuntu onto the hard drive if that would make things easier.

---

### Post by CelticWarrior on 2021-02-25
Wiping the whole drive, create a new partition table, etc. can be done within the Ubuntu live session among many other things. That shouldn't be necessary to repair or reinstall Windows though. And using any other bootable media isn't a requirement either, the Windows media has everything needed to repair or reinstall Windows.

Unlike many people think, Ubuntu is NOT a free repair tool for Windows. Surely in the past it could be used to trigger file system error correction tools or even to recover data in a Windows drive that doesn't boot but with the advent of the default Windows Fast Startup feature even that particular usage went out of fashion.

The problems booting a properly made Windows installation media are often related with incorrect settings in BIOS or UEFI. Any preinstalled Windows 8 or newer since 2012 at least is in UEFI hardware and in UEFI mode. So, the first thing to check is whether or not the external media is actually booting in UEFI mode.

What you think might be a solution really isn't.

---

### Post by ianmcc1 on 2021-02-25
my laser engrave and 3d printer wont work with ubuntu or hell id just run it instead of windows. my ubuntu live usb will boot in UEFI.

---

### Post by CelticWarrior on 2021-02-25
Don't know about laser engravers but 3D printers are, for the most part, OS agnostic and the software required for making the files to be printed exist for all platforms.

But all of this is off-topic. The problem you're having isn't, obviously, within the expertise of the typical user of this forum. There are plenty of online resources for Windows.

Again, I suspect the problem you're having stems from not knowing enough about UEFI. Yes, your Ubuntu live USB boots in UEFI mode but also in BIOS/legacy mode (it's an hybrid ISO) but ditto for the Windows installation media, at least if done using the official tool. Ergo, this isn't the problem. The problem is - probably - that you're booting it in other than the mode Windows was installed originally. Keep in mind that regardless of the installed OS mode most firmwares typically have "UEFI+Legacy" by default. The implication is that when booting external media users must choose from one of the two entries for the USB drive.

---

### Post by yancek on 2021-02-25
I'm not sure why the methods you have tried to create a bootable windows installer have failed.  Have you checked the BIOS to see if your hard drive which had windows on it is recognized there?  If not, no point wasting time as the drive is almost certainly dead.

>  can i use ubuntu live usb to load the windows iso into a partition on the hard drive?

It's possible but you would have to know how to install Grub to the USB not as part of the iso so you can modify the grub.cfg file.  Much easier for someone with no experience to install Ubuntu to a small 15GB partition on the drive and boot from it and then mount your windows iso, loop mount it and copy it to a separate partition on the drive with an ntfs filesystem.  The link below is one of a number of sites which explain how to create a bootable windows installer.  It talks specifically about creating a bootable windows usb but the steps are identical if you want to put it on a hard drive partition and boot from there.  Just replace all the references to the usb with the ntfs partition.

Was your windows 10 installed UEFI?

[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)

Another option is explained at the link below using unetbootin.  This also is specific to installing the windows installer to a usb but you should be able to point the iso of windows to an ntfs partition on your hard drive.

[https://www.wikihow.com/Install-Windows-from-Ubuntu](https://www.wikihow.com/Install-Windows-from-Ubuntu)

---

### Post by ianmcc1 on 2021-02-25
thanks for the help guys, @yancek ill give your solution a try. i dont care much for windows, i just want to run the software that ive paid for. if it doesnt work ill install a VM and run window through there and see if that works. thanks again.

---

### Post by C.S.Cameron on 2021-02-25
If it is just a matter of laser engraver and 3d printer software, you might get by installing **VirtualBox** from Ubuntu Software and installing Windows as a Virtual Machine.

---


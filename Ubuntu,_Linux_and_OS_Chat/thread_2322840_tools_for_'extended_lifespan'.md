---
title: "tools for 'extended lifespan'"
date: 2016-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by wilfried3 on 2016-04-30
Would it be an idea to include tools to update firmwares?
Specially for Distro's that expend the lifespan of older hardware.

For instance new HD / SSD firmware to get improved performance and reliabillity.
Mainboard BIOS upgrades to enable features?

Take for instance this post:
[http://metal03326.blogspot.nl/2012/04/samsung-p-ssd1800-firmware-update.html](http://metal03326.blogspot.nl/2012/04/samsung-p-ssd1800-firmware-update.html)

How would that work in *buntu? 
My thought here is an extra boot option with a few firmware tools.  (Or maybe just on a bootable USB?)
Though an official tool. With documentation etc. Available from the ubuntu website


What tools are available in Ubuntu to flash firmwares?

What are Pro's:

What are Con's:

---

### Post by deadflowr on 2016-04-30
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by grahammechanical on 2016-05-01
The people to supply utilities to flash a motherboard's BIOS chip to upgrade the motherboard firmware are the motherboard manufacturers. My motherboard manufacturer supplied a CD with various utilities on it that would flash the BIOS/CMOS from the operating system. As expected these were Windows programs. There were no Linux utilities supplied to flash the BIOS.

I have never had a need to flash the BIOS. It is a scary thing to do. It was not something that I was going to attempt just because I could but without a need to do it.

My motherboard BIOS has a built in function that will save a copy of the BIOS to a floppy disc or a USB stick and upgrade to the appropriate newer BIOS version. There is also a DOS utility that will run from a floppy disc to save the original BIOS & flash the chip with a newer version.

I think that you are asking too much from the Ubuntu developers. 

Regards

---

### Post by buzzingrobot on 2016-05-01
Some folks in the Fedora project have been working on a firmware updater for Linux. I believe an alpha-ish version has been implemented. Vendors, though, need to provide firmware packages that work with it.  That is, I don't think it will work with a firmware update embedded in a Window's .exe file.

Intel hardware using an Intel BIOS allows the BIOS to be updated in an OS-independent manner. 

Firmware updates are risky because a machine can be bricked if something goes wrong. (Like a power blip in the middle of the update.) I do them only when I know the update will fix a specific problem I want fixed.  Responsible vendors will make that info available in readme files, etc.

---

### Post by grahammechanical on 2016-05-01
> Intel hardware using an Intel BIOS allows the BIOS to be updated in an OS-independent manner.

Even  without an Intel BIOS there is a driver in Additional Drivers that will  run Intel microcode at every boot to modify the way the Intel CPU works  without the need to flash the BIOS. The check box is labelled "Using  Processor microcode firmware for Intel CPUs from intel-microcode  (proprietary)." I have no way of knowing if Additional Drivers has a  similar provision for AMD CPUs but there should be. It is possible to do  this in Debian.

[https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)

Regards

---

### Post by oldrocker99 on 2016-05-01
> **grahammechanical said:**
> Even  without an Intel BIOS there is a driver in Additional Drivers that will  run Intel microcode at every boot to modify the way the Intel CPU works  without the need to flash the BIOS. The check box is labelled "Using  Processor microcode firmware for Intel CPUs from intel-microcode  (proprietary)." I have no way of knowing if Additional Drivers has a  similar provision for AMD CPUs but there should be. It is possible to do  this in Debian.

[https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)

Regards
There is amd-microcode available for AMD users and the checkbox text is identical: "...for AMD CPUs from amd-microcode (proprietary)."

---

### Post by ZoiaGuyver on 2016-05-02
Just to jump in here. 

Flashing a bios is a hell of a lot different to just running a microcode update, a bios can handle the microcode updates (allows for further CPU support and fixes for some motherboards) but is **NOT** something you want people who are new to Ubuntu or Linux or even computers in general to have. Bios flashing can and will **Brick** a mainboard a Microcode on the other hand will not brick a CPU 9/10 it will just be ignored or skipped. 

The old saying goes "If it isn't broke, don't try and fix it" this for a bios update imo is fact, if a bios is working fine and does everything it needs to then leave it be (unless you can afford to replace the mobo, have a dual-bios board with a recovery switch). Microcode on the other hand can improve a lot of software support it can smooth out some rough edges in synthetic benchmarks or even provide access to new instructions (although it can also be used to "nerf" stuff i.e Intel blocking the non-K overclocking with Microcode updates). 

Putting that responsibility on an OS imo is taking matters way to far (whether the OS is Windows, OS-X, BSD or Linux). 

Firmware for HD or SDD drives may be able to work, but again they could be adversely affected (Bricking). 

Thats just my two pennies. Leave the Firmware updates as far away as you can from an OS responsibility.

---

### Post by buzzingrobot on 2016-05-02
> **ZoiaGuyver said:**
>  Leave the Firmware updates as far away as you can from an OS responsibility.

Agree, in general.  BIOS and other firmware updates, though, are an issue if you run only Linux, you actually need the update, and all available update methods assume the presence of Windows. Linux needs to deal with that, although any progress seems dependent on cooperation from vendors.

Finding out if your hardware does need an update is typically not the easiest thing to do. In my experience, the availability of these changes receive little or no publicity. The details of the changes may not be available, or may be inadequate, and are often in dev-speak and buried in changelogs/readmes posted on obscure vendor sites. Updates often apply to one or a very few systems from the vendor. The chances consumers can identify the specific component in their system is close to nil.

---

### Post by grahammechanical on 2016-05-02
There is also a big difference between using a driver to change the functionality of a CPU (microcode driver) and flashing the boot system (BIOS/UEFI) utility with a new utility.

There is something else that comes to mind. I have USB 2 hardware. Will a BIOS upgrade convert them into USB 3. I am not sure it is that simple. But how else can a person get increased USB speed except by going from USB 2 to USB 3? And that I think will require a hardware change.

Regards

---

### Post by poorguy on 2016-05-02
deleted.

---

### Post by ZoiaGuyver on 2016-05-03
Agree with you there @Buzzingrobot. Updates need to be easier to find and they must either open up the Bios/UEFI platforms or supply the needed tools to make the changes. Linux users in general are pretty quick on the uptake and don't mind a bit of light reading (at least over the years I've been around and yes I'm a dinosaur...). If the bios vendors just gave a quick guide to the tools, how and what is needed from inside an OS to update successfully the Linux crowd would probably have a tool done in a few weeks (one that would probably be compatible with a lot of platforms).

The problem as I see it though is with the vendors, they use the same excuse of Linux not having a huge market share (as does everyone else), too many distros. While I understand their point of view I also see it as a cop out. It's the same type of Proprietary nonsense Linux has faced for many years, hell were probably getting into it being decades.

I would love to see more vendors supply the tools needed, a bit like AMD are doing with AMDgpu using the opensource community to bolster efforts to advance. If the likes of AMI and Pheonix did that I think it would lead to some really interesting projects.

As for what @grahammechanical asked, the USB 2/3 can't be changed that easily unfortunately its down to the controller chip the vendor uses when they design the board.

---

### Post by grahammechanical on 2016-05-04
The opening session of the Ubuntu Online Summit had something important to say on this subject. It happens about 32 minutes into the session. Look at the slide labelled Convergence: desktop and listen to what is said about Firmware Updates being available & installable through Ubuntu Software. 

[http://summit.ubuntu.com/uos-1605/meeting/22663/ubuntu-online-summit-opening-plenary/](http://summit.ubuntu.com/uos-1605/meeting/22663/ubuntu-online-summit-opening-plenary/)

Ubuntu devs have done what they can about this. It is now up to the motherboard manufacturers to make this possible.

> USB 2/3 can't be changed that easily unfortunately its down to the controller chip the vendor uses when they design the board.

Thank you. My point being that Flashing the BIOS will not necessarily speed up USB download speeds as the link provided by the OP seemed to suggest. If the motherboard is already using USB to the maximum then flashing the BIOS will not change it for the better.

Regards

---

### Post by buzzingrobot on 2016-05-04
> **ZoiaGuyver said:**
> ...they must either open up the Bios/UEFI platforms or supply the needed tools to make the changes.

Well, I don't expect vendors to open their BIOS/UEFI code, at not in any way that permits or enables re-use and re-marketing.  They'd lose their business.  That's essentially why every business that's tried to market a retail Linux distribution has either failed or changed business model.

Hardware OEM sometimes make their own additions to BIOS/UEFI code they buy and that also encourages keeping thing proprietary.

I like Intel's approach.  They provide BIOS update exe's for click-and-execute use in Windows, as well as an archive that can be copied to a FAT32 USB drive.  Hit F7 on a reboot and a menu prompts you to select the USB and start the update. (I've had to update this Intel NUC 4 times in the last month or so.) There's the same option within the BIOS setup menu.  If all vendors put that kind of OS-independent update method in their code, the problem would be solved.

---

### Post by ZoiaGuyver on 2016-05-05
That's also true. A lot of the board manufacturers seem to have an OS-Independent way of updating (Asus, Asrock and Gigabyte are three i know have it on Mid/High end boards).

Haven't had a chance to watch all the vid @grahammechanical posted but it is good to hear that Ubuntu are trying!

---

### Post by kurt18947 on 2016-05-05
Re BIOS updates do modern motherboards still support updating via DOS? If so, how about a bootable FreeDOS device with the correct BIOS image on it? Or hit up a Windows using friend for a boot disk?

> There is something else that comes to mind. I have USB 2 hardware. Will a  BIOS upgrade convert them into USB 3. I am not sure it is that simple.  But how else can a person get increased USB speed except by going from  USB 2 to USB 3? And that I think will require a hardware change.

I'm considering the same thing. The option I'm seeing is a PCI-e expansion card. The PCI bus, while capable of greater than USB 2 data rates cannot keep up with USB 3 speeds. Then of course there's the question of linux support though most USB 3 cards I've looked at support older Windows OSs so I'd think linux support should be there.

---


---
title: "Lubuntu 15.10 installation from a CD"
date: 2015-06-09
forum: Ubuntu Development Version
---

### Post by neb8 on 2015-06-09
Hello,

I have an  older laptop without an internal CD/DVD drive.

I've attempted booting from several flash drive Ubutntu iso installations, without any success. Not sure what the problem is. The laptop bios has problems recognizing an OS installed onto USB sticks, displays no OS found message.

I've tried installing Lubuntu to the laptop from an iso installed on a usb hard drive without any success, the iso loads and starts to install but eventually freezes up and won't load the main Ubuntu installation menu.

* I  have an external USB CD drive. Before purchasing some blank 700 mb CD-R's I was wondering if there are any problems burning Lubuntu 15.10 to a 700mb CD-R?

or do I need to purchase an external USB DVD player/recorder? I have a bunch of DVDs some with Ubuntu installed. What I don't like about using DVD's is the wasted space. 

downloaded iso sizes.

wily-alternate-i386.iso    686.8 MB

wily-desktop-i386.iso  740.3 MB

---

### Post by yancek on 2015-06-09
Are you actually trying to install 15.10 as the final stable release will not be for another four months.  Better off with a current stable release.  Do you have any other operating system installed?  If so, what?  Some info on your hardware would be useful.  What software did you use to create the bootable flash drives?

---

### Post by Rex Bouwense on 2015-06-09
+1 yancek
Lubuntu generally has stayed within the 700 Mb limit of the CD, with one exception (Lubuntu 14.10).  When trying to boot from a flash drive, bare in mind that some older laptops recognize the flash drive as another hard drive so you have to check your Bios to insure that the flash drive (if it is recognized as another hard drive) is moved ahead of the real hard drive in the booting order.

---

### Post by neb8 on 2015-06-09
The first thing I did was check the bios to make sure of the boot order. It's a 32-bit rugged laptop with the latest bios, that was discontinued. 

Difficult to upgrade because of age  of the hardware  no longer has upgraded os drivers and the hardware architecture doesn't allow certain types of more modern adapters to be installed. (e.g. older mini pci slot technologies may not support some modern mini pci adapters that use newer pci standards.)

I was able to boot from another USB hard drive Ubuntu installation, however there are problems since the initial installation was using another pc with different hardware. Rather than trying to reconfigure the installation I decided to perform a clean (Lubuntu) install removing the existing Ubuntu 32-bit installation.  
____________

Unetbootin. 

No 15.10 would be a daily build installation. The final version I don't is due for several months. o

I run beta and a lot of non wily software. Older versions of software applications don't normally have any problems. If installing from a Ubuntu PPA distribution. I usually  rename it the latest PPA dist if no wily dist is available.

I have another 15.10 64-bit daily build installed on another PC without any problems. 

The laptop requires a 32-bit installation.

My question is mostly in regards to any Ubuntu installation from a CD ... a 700 MB CD-R should at least accept a 686.8 MB (iso) Alternate version?

I read about other methods of Ubuntu installations such using a slipstream connection with floppies. The installation software needs to be able to recognize and configure an internet connection.

---

### Post by grahammechanical on 2015-06-09
Rex is not talking about boot order but something else that happens when trying to load an OS from an external USB port.

The BIOS does not see the USB stick as an substitute optical drive but as an external USB drive and so we have to go into a BIOS boot setting and set the USB drive as the drive to load. We would have to do the same thing if we had two hard drives. And that is how the BIOS is seeing the USB stick. As another hard drive.

At least I have to do it this way to run Ubuntu off of a USB memory stick.

Regards.

---

### Post by neb8 on 2015-06-09
The laptop's AMI bios recognizes the flash drive as a USB - generic flash , shows Boot Device 1 - "USB - Generic Flash". 

With the internal hard drive disabled and the usb flashed enabled as the 1st boot device, during bootstrapping there is a bios message of "No Operating System Found"
If the internal hard drive is enabled as the second boot device the bios boots to the internal hard drive. 
If a USB hard drive is installed as the primary boot device the bios boots to the external USB drive.
Apparently the bios is unable to recognize the OS bootstrapping installed to the usb flash, which uses a different method of installing an iso to boot media.

---

### Post by v3.xx on 2015-06-09
How bout using that stick to install 15.04 then just upgrade to 15.10.

---

### Post by neb8 on 2015-06-09
I don't think a  15.04 flash stick install would be any different than a 15.10. It appears a hardware/software incompatibility exists somewhere i.e. (.e.g.) 1. the laptop bios and flash stick hardware 2. the laptop's bios isn't written to boot a usb flash drive. 3. incompatibility between the Ubuntu flash installation and the bios.

I'll probably try either a CD or DVD install from an external USB cd/dvd recorder drive. I have looked at many flash drives from named brand to generic, many are only re-branded ~$1.00 drives. Flash drive manufactures are still in development of their hardware, bios and media architectures.

---

### Post by sudodus on 2015-06-10
> My question is mostly in regards to any Ubuntu installation from a CD  ... a 700 MB CD-R should at least accept a 686.8 MB (iso) Alternate  version?

Yes,

If the Lubuntu desktop file of a version, say Wily, is oversized for CD,  the alternate iso file is probably still within CD size, so that you  can use your external CD drive to boot from it.

-o-

An alternative is to boot from a ***Plop*** CD or even a floppy for an old PC and chainload to a USB pendrive. [https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)

If you have an installed linux system with grub, you can make a menuentry for ***chainloading*** from there too (the 40_custom method).

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by Bucky Ball on 2015-06-10
*Thread moved to **Ubuntu Development Version**.*

15.10 is in development and not released until October. Discussion and problem solving of 15.10 should happen here. Thanks. :)

---

### Post by neb8 on 2015-06-10
> **sudodus said:**
> Yes,


An alternative is to boot from a ***Plop*** CD or even a floppy for an old PC and chainload to a USB pendrive. [https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)

If you have an installed linux system with grub, you can make a menuentry for ***chainloading*** from there too (the 40_custom method).

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

Ok, I'll go ahead and try a Plop installation. Previous attempts to boot from a wily-alternate.iso and wily-desktop.iso, (after editing of the 40_custom grub file), failed.  The iso would load but was unable to complete and froze up before loading the installation main menu.

I had previously created a separate installation partition then copied a wily iso file to a install_cd directory, but haven't yet configured  a grub boot.

Since I'm new to Linux I'm still becoming familiarized and learning some of the os basic fundamentals.

---

### Post by sudodus on 2015-06-10
This last description makes me think that maybe you were actually booting Lubuntu via the 40_custom method, but that you have another problem, maybe finding a suitable driver for the graphics card.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Even before knowing about your graphics chip, I suggest that you try with the boot option **nomodeset**. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by QDR06VV9 on 2015-06-10
Forgive my intrusion but maybe inxi?
```
sudo apt-get install inxi
```
and then in terminal
```
inxi -b
```
To show sudodus what specs your machine has, Below is mine.
```
me@me-Aspire-M3300:~$ inxi -b
System:    Host: me-Aspire-M3300 Kernel: 4.0.5-040005-lowlatency x86_64 (64 bit)
           Desktop: Gnome 3.14.4 Distro: Ubuntu 15.04 vivid
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 1400/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.09
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 2500.5GB (1.7% used)
Info:      Processes: 211 Uptime: 45 min Memory: 875.3/5967.1MB
           Client: Shell (bash) inxi: 2.2.16 

```

---

### Post by neb8 on 2015-06-10
System Manufacturer    Itronix Corp
System Model    IX270
System Type    X86-based PC
Processor    x86 Family 6 Model 14 Stepping 12 GenuineIntel ~1833 Mhz
BIOS Version/Date    American Megatrends Inc. Ver.117, 2/19/2009
SMBIOS Version    2.5
Total Physical Memory    3,072.00 MB
Adapter Description    ATI MOBILITY RADEON X300
Adapter RAM    128.00 MB (134,217,728 bytes)
Mobile Intel(R) 955XM/945GM/PM/GMS/940GML Express PCI Express

LSI Corporation ET-131x PCI-E Ethernet Controller (rev 01)

---

### Post by QDR06VV9 on 2015-06-10
Read through this, [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
I'm not real sure your going to get it done.(With a Quick look at your Specs)
I could be wrong.

---

### Post by neb8 on 2015-06-10
> **runrickus said:**
> Read through this, [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
I'm not real sure your going to get it done.(With a Quick look at your Specs)
I could be wrong.

I'm able to boot from a USB hard drive ok, both with a connected PC and the laptop.

---

### Post by sudodus on 2015-06-10
It is an old computer, and you may have better luck with either of the long term support versions 12.04 LTS or 14.04 LTS.

You should get a Lighter desktop environment, so Lubuntu 14.04.2 is a good choice. Lubuntu 12.04 has passed end of life, but you can try a community re-spin based on Ubuntu 12.04, for example LXLE and Bodhi.

And there might be problems with the graphics ATI MOBILITY RADEON X300 (I have no own experience of it). The support for it might be dropped in 15.10.

---

### Post by mörgæs on 2015-06-10
If everything else fails you can move the hard disk to another computer, install 15.04 or 15.10 and move the disk back.

---

### Post by neb8 on 2015-06-10
It turned out to be a 15.10 distribution compatibility problem.
A wily-desktop 32bit iso loads but hangs before loading the desktop.
None of the iso flash drive installs worked with this laptop, the install was from a hard drive installed iso, booted from grub. 

I was able to boot a Lubuntu 15.04 iso and install Lubuntu to the laptop. However there is no sound and LAN.
[COLOR=#ff8c00]
[/COLOR][I][COLOR=#800080]*** The wireless (wifi) adapter works ok. The hardwired LAN adapter isn't working (unable to create a LAN connection for a router and Internet connection) and there is no sound. I have tried installing & re-installing a device driver for the sound card, still unable to produce any sound. 

[/COLOR]Network adapter shows to be "UNCLAIMED". A driver was installed for the sound card [/I][COLOR=#000000]LSI Corporation ET-131x PCI-E Ethernet Controller (rev 01).[/COLOR]
_______

Lubuntu 32-bit installed it's own grub during installation, modifying the boot partition's mbr.
I found a grub customizer utility that allowed editing of the original 64-bit grub menu and write it's menu location back to the mbr.

[https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)

 Editing and saving grub menus may not function properly unless the mbr knows which grub installation to use.
The grub-customizer includes a mbr utility capable of writing the grub menu (being edited) location to the mbr.

e.g.

Device     Boot    Start       End  Sectors  Size Id Type
/dev/sda1 ====   5 Extended  [COLOR=#ff0000](MBR) <- bios boot partition[/COLOR]
/dev/sda2  *        -----  83 Linux[COLOR=#00ff00]             (Ubuntu 64-bit installation Grub menus)[/COLOR]
/dev/sda3 -------  83 Linux          [COLOR=#008000](Lubuntu 32-bit installation Grub menus)

[/COLOR]

---


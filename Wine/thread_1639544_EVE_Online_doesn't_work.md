---
title: "EVE Online doesn't work"
date: 2010-12-06
forum: Wine
---

### Post by RiskyShift on 2010-12-06
I am very new to Linux, and hoping that I can completely switch over when I build a new computer in a few weeks.

I followed the instructions on this website: [http://wiki.eveonline.com/en/wiki/Install_EVE_on_linux_with_wine](http://wiki.eveonline.com/en/wiki/Install_EVE_on_linux_with_wine)

I used this command in the launcher:  [I][B]wine explorer /desktop=EVE,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"

[/B][/I]When I run the launcher it shows the initial splash screen, the monitor goes black, then it comes up full screen but when it comes up full screen it shows this: 

Img is big so I will just link it: [http://temp329.s3.amazonaws.com/evebroke.jpg](http://temp329.s3.amazonaws.com/evebroke.jpg)


Notice how the top is weird. Usually under this graphic would be the log in boxes, but they do not show up here.

At this point I can't do anything. The mouse doesn't work, pressing ESC usually pulls up a menu, but that doesn't work either. It is completely unresponsive and I have to ALT-F4.

INFO:

Ubuntu 10.10 WUBI install
Trying to use EVE installed on windows (would this cause it?)


Anyone have any ideas?

---

### Post by RiskyShift on 2010-12-07
Anyone?

Would it make a difference if the original install was on Windows instead of Linux?

Maybe my video drivers are wrong? I notice in Linux they are called nvidia x-server drivers. Does that mean I have server drivers instead of 3d drivers?

---

### Post by khelben1979 on 2010-12-07
It's difficult to get Eve Online working with Wine. Have you tried other applications which uses Wine to see if the Wine application works correctly with your system?

Does your system meet the minimum system requirements:

    CPU: Intel Pentium® or AMD @ 1.5 GHz
    RAM: XP – 1 GB / Vista – 1.5 GB
    Video: 64 MB Shader Model 2.0 Graphics cards such as GeForce FX (5 series) class card or higher, ATi 9500, x300 series or higher and Similar chips from other manufacturers

Note that the above reflects about the Windows version where I cut off some information, with this in mind, it might be less efficient on a Linux system since OpenGL haveto emulate the DirectX which is used by Eve Online if I've understood it correctly.

**lspci** gives output about your hardware if you're uncertain and it makes it easier to know if that's part of the problem.

---

### Post by RiskyShift on 2010-12-08
I run EVE on XP all the time with no problems. I went through and ran some other applications with wine and they worked ok, but I haven't tried any 3d games other than EVE yet.

Here is a summery of computer stats:

   
**Computer:**    


Operating System   [Microsoft Windows XP Media Center Edition]("http://www.microsoft.com/windows/")    


OS Service Pack   Service Pack 3    


DirectX   [4.09.00.0904  (DirectX 9.0c)]("http://www.microsoft.com/windows/directx/")    


Computer Name   YOUR-55E5F9E3D2 (HOME)    


User Name   Chad        

**Motherboard:**    


CPU Type   [AMD Athlon 64, 2200 MHz (11 x 200) 3500+]("http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118,00.html")    


Motherboard Name   Unknown    


Motherboard Chipset   [ATI Radeon  Xpress 200, AMD Hammer]("http://www.ati.com/products/integrated.html")    


System Memory   1024 MB (PC3200 DDR SDRAM)    


BIOS Type   [Award  (11/15/05)]("http://www.phoenix.com/en/products/default.htm")    


Communication Port   ECP Printer Port (LPT1)        

**Display:**    


Video Adapter   [NVIDIA GeForce  210 (1024 MB)]("http://www.nvidia.com/view.asp?PAGE=products")    


Monitor   [Samsung SyncMaster 927DF(I)/927MB(I)/997DF/997MB [19" CRT]  (HCGXA10681)]("http://product.samsung.com/cgi-bin/nabc/product/b2c_product_type.jsp?prod_path=/Computers+and+Related/Monitor")        

**Multimedia:**    


Audio Adapter   ATI SB400 - AC'97 Audio Controller        

**Storage:**    


IDE Controller   Standard Dual Channel PCI IDE Controller    


IDE Controller   Standard Dual Channel PCI IDE Controller    


SCSI/RAID Controller   A54QMX5S IDE Controller    


Disk Drive   [ST3200826AS (200 GB, 7200 RPM, SATA)]("http://www.seagate.com/products")    


Disk Drive   Generic USB SD Reader USB Device    


Disk Drive   Generic USB CF Reader USB Device    


Disk Drive   Generic USB SM Reader USB Device    


Disk Drive   Generic USB MS Reader USB Device    


Optical Drive   JEBET NS9IJGHMJ0XY SCSI CdRom Device    


Optical Drive   [SONY DVD RW  DRU-840A]("http://www.sonyburners.com/products/index.php")    


SMART Hard Disks Status   OK

---

### Post by RiskyShift on 2010-12-08
Actually when I run:[I][B]

wine explorer /desktop=EVE,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"

[/B][/I]I just get the virtual desktop blue screen and nothing else***. ***I get the image in the original post when I run eve.exe in it's folder.

---

### Post by khelben1979 on 2010-12-08
Have you checked [WineHQ - Eve Online]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2249") and read through what other users have experienced in there?

I have a brother which is using a nVidia GTX 470 card and it's pretty powerful. Yet that didn't help him either to get the game working, so I'm not sure if your problem lies in the graphic card or the installed driver, especially if other games which uses Wine are working correctly.

I recommend you search [the Eve Online Forum]("http://www.eveonline.com/ingameboard.asp?a=topic&threadID=30457&page=80") to try and get a better answer. I've definitely read on the forum over there that it is possible to get Eve Online working and it's being confirmed by the WineHQ as well.

---

### Post by khelben1979 on 2010-12-09
I found [this thread]("http://ubuntuforums.org/showthread.php?t=1630052"). Disable audio in Wine by running [winecfg]("http://wiki.winehq.org/winecfg") and untick using window mode and let us know if it changes anything.

---

### Post by SamD42 on 2010-12-09
Had this problem last night. Try running:

winetricks d3dx9

Let that install, and then try again.

---

### Post by RiskyShift on 2010-12-09
Sweeeet.... That did it.

Thanks for the help!

---


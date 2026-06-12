---
title: "Display Issues on Sun xVM VirtualBox"
date: 2009-01-22
forum: Virtualisation
---

### Post by robert_rees on 2009-01-22
Hello Folks.  I am new to this, and have searched for someone with a similar issue with the search function but I cannot seem to find anyone with the problem I am having.

I have an Alienware M17 with Windows Vista 64Bit Edition running.  I recently installed the VirtualBox (it would not accept the 64bit edition that I downloaded first, so I went back and downloaded the 32bit) and successfullly installed and configured the Ubuntu 8.10 release.  My first issue is that the video size is limited to 800x600.  The virtualbox gives me a prompt that the guest OS is not running in 32 bit, and advises me to change it... but I cannot find out where.  When I open the display settings, I can find no tab or option to change it.  So basically I am stuck to 800x600.  I tired to go full screen with the VirtualMachine itself, and then change the display, but I get the same results.  

Just for reference, listed below is my system info:  My video cards (two) are ATI in crossfire.


[I]
[COLOR="Blue"]OS Name	Microsoft® Windows Vista™ Ultimate
Version	6.0.6001 Service Pack 1 Build 6001
Other OS Description 	Not Available
OS Manufacturer	Microsoft Corporation
System Manufacturer	Alienware
System Model	Alienware M17
System Type	x64-based PC
Processor	Intel(R) Core(TM)2 Extreme CPU Q9300  @ 2.53GHz, 2533 Mhz, 4 Core(s), 4 Logical Processor(s)
BIOS Version/Date	Intel W841.B10, 10/14/2008
SMBIOS Version	2.5
Locale	United States
Hardware Abstraction Layer	Version = "6.0.6001.18000"
Time Zone	Central Standard Time
Installed Physical Memory (RAM)	4.00 GB
Total Physical Memory	3.99 GB
Available Physical Memory	923 MB
Total Virtual Memory	8.16 GB
Available Virtual Memory	4.76 GB
Page File Space	4.29 GB

Name	ATI Mobility Radeon HD 3870
PNP Device ID	PCI\VEN_1002&DEV_9509&SUBSYS_207A161F&REV_00\6&7C2E2F2&0&00000008
Adapter Type	ATI Radeon Graphics Processor (0x9509), ATI Technologies Inc. compatible
Adapter Description	ATI Mobility Radeon HD 3870
Adapter RAM	512.00 MB (536,870,912 bytes)
Installed Drivers	atidxx32,atidxx64.dll,atiumdag,atiumdva,atiumd64.dll,atiumd6a.cap,atitmm64.dll
Driver Version	7.01.01.809
INF File	oem25.inf (ati2mtag_M76 section)
Color Planes	Not Available
Color Table Entries	4294967296
Resolution	1920 x 1200 x 59 hertz
Bits/Pixel	32
Memory Address	0xD0000000-0xDFFFFFFF
Memory Address	0xF82F0000-0xF82FFFFF
I/O Port	0x00002C00-0x00002CFF
IRQ Channel	IRQ 4294967292
Driver	c:\windows\system32\drivers\atikmdag.sys (7.1.1.809, 4.43 MB (4,642,816 bytes), 12/31/2008 1:46 PM)
	
Name	ATI Mobility Radeon HD 3870
PNP Device ID	PCI\VEN_1002&DEV_9509&SUBSYS_207A161F&REV_00\6&1198083A&0&00280008
Adapter Type	ATI Radeon Graphics Processor (0x9509), ATI Technologies Inc. compatible
Adapter Description	ATI Mobility Radeon HD 3870
Adapter RAM	512.00 MB (536,870,912 bytes)
Installed Drivers	atidxx32,atidxx64.dll,atiumdag,atiumdva,atiumd64.dll,atiumd6a.cap,atitmm64.dll
Driver Version	7.01.01.809
INF File	oem25.inf (ati2mtag_M76 section)
Color Planes	Not Available
Color Table Entries	Not Available
Resolution	Not Available
Bits/Pixel	Not Available
Memory Address	0xC0000000-0xFEBFFFFF
Memory Address	0xF8300000-0xF83FFFFF
I/O Port	0x00003000-0x00003FFF
IRQ Channel	IRQ 4294967294
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\atikmdag.sys (7.1.1.809, 4.43 MB (4,642,816 bytes), 12/31/2008 1:46 PM)

[/COLOR][/I]

---

### Post by Dedoimedo on 2009-01-22
You need to install guest additions to make your virtual machines behave as you expect them.

[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

Secondly, did you install 32-bit ubuntu on top of your 32-bit VB or 64-bit? Can you elaborate a bit on that part?

Dedoimedo

---

### Post by robert_rees on 2009-01-22
Dedoimedo,
Thank you for your qucick reply.  I will check your link out shortly.  

As for the VB I installed. It also is a 32 Bit.  I am not sure why it would not accept at 64Bit version either.  I am running Vista Ultimate 64Bit Edition, so I know that I am capable.

---

### Post by Dedoimedo on 2009-01-22
Rule of thumb:

32-bit virtualization - supports only 32-bit guests!
64-bit virtualization - both 32-bit and 64-bit.

So it figures out; your 32-bit VB can't run 64-bit guests, no matter what you have on the host, 32-bit or 64-bit ...

Dedoimedo

---

### Post by robert_rees on 2009-01-22
Sorry, not sure if i was clear.  They are both 32bit editions.  I tried to run the following prompt (as your link referred to) and I got a "permission denied" response. 

/media/cdrom0 pwd

Any suggestions?

---


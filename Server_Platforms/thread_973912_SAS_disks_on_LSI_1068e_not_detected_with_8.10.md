---
title: "SAS disks on LSI 1068e not detected with 8.10"
date: 2008-11-07
forum: Server Platforms
---

### Post by basdoorn on 2008-11-07
I am trying to install a new server with Ubuntu 8.10 server as replacement for an older server running Ubuntu 6.06 LTS. The new server is composed of the following components.

SuperMicro SuperServer 6015C-M3B barebone 
[http://www.supermicro.com/products/system/1U/6015/SYS-6015C-M3.cfm](http://www.supermicro.com/products/system/1U/6015/SYS-6015C-M3.cfm)

1x Intel Xeon L5420 2.5GHz Quadcore processor
2x Kingston PC6400 4GB Registered ECC memory
2x Seagate Cheetah 15k.5 146 GB harddisks

The harddisks are connected to the onboard LSI 1068e software RAID controller through the chassis backplane. I have created and initialized a RAID 1 array containing both disks succesfully.
I have tried using both the Ubuntu server x64 and Ubuntu alternate x64 media. In both cases the installer cannot detect any disks in my new server. It shows me a list of possible drivers, but neither mpt (e.g. mptsas) or megaraid drivers will work. In total I tried about a dozen different ones that could be related to my controller to no avail.
My previous server had normal SATA disks and was installed with no difficulty at all. Ubuntu has kept me quite happy up until now and I would like to keep using it if possible. I have some knowledge about partitioning and software raid in linux, but nothing much that can help me sort out this controller issue. On the website of LSI the product page features some driver downloads, but only for Red Hat Enterprise Linux and Suse Linux Enterprise Server editions. 

[http://www.lsi.com/storage_home/products_home/standard_product_ics/sas_ics/lsisas1068e/index.html](http://www.lsi.com/storage_home/products_home/standard_product_ics/sas_ics/lsisas1068e/index.html)

I have downloaded these drivers, but find myself with rpm packages and no clue how to apply them to the installation process of Ubuntu or knowing if this is possible at all. The server is sitting still on my desk at the moment, so there is time for some experimentation. I have sent an email to SuperMicro about this issue as well, but have not yet received a reply. Thanks in advance for any help.

---

### Post by basdoorn on 2008-11-10
This issue was NOT resolved, see the third post below. Ubuntu will see the disks and install on them, but the BIOS will not allow the system to boot from the LSI 1068e controller in my case. It turns out my mainboard has a jumper setting controlling Software RAID. If the jumper is in place, the MegaRAID BIOS loads and Ubuntu cannot do anything with it. If the jumper is removed, the controller works in IT RAID mode. In this mode, Ubuntu detects the drives just fine and allows me to setup soft raid in linux. Bye bye MegaRAID for me, linux soft raid 1 has worked perfectly in my last server and I am sure it will live up to the challenge in the new one as well. Below the section of the manual which describes the jumper setting.

JPA2 allows you to select the SAS RAID
mode. You can use either Software
RAID or IT RAID. Close this jumper to
use Software RAID (Default). Set this
jumper to open to use the IT RAID mode.
Contact Tech. Support at Supermicro for
more information. See the table on the
right for jumper settings.

I would have expected a better explanation about this disk-giving jumper. Surely SuperMicro has more customers using distros like Ubuntu that want to use their SAS controller... 
Anyway, this is how it works for my 6015C-M3B SuperMicro SuperServer case with X7DCL-3 mainboard. I reckon there are many others out there that like my server have an LSI 1068e controller and a similar jumper. The topic can be closed, hope somebody else can benefit.

---

### Post by basdoorn on 2008-11-13
Another unexpected issue arose with the IT RAID mode solution. I could no longer get my system to boot normally. Even with all boot options enabled in the BIOS, the system would refuse to boot the Ubuntu installation which did complete succesfully. Totally fed up with all these issues I decided to put in a decent RAID controller with proper linux support, a store nearby had an Adaptec 5405 on stock. Installed it, hooked up the cables to the backplane and everything is working fine now.
I do hope SuperMicro (and maybe other manufacturers) will provide a way to boot from disks on the LSI 1068e when not using the MegaRAID mode. Now instead of getting a complete solution in a box, you end up spending more money, time and effort getting yourself a RAID controller with decent open source driver and boot support in the end.
Of course, you could choose to put in a CD or USB key to boot from, or when you have SATA harddisks use the onboard SATA ports. Adding an additional SATA drive and using that to boot would work, but would cost you one out of four drive bays, eliminating the option of RAID 10 or RAID 5 with hot-spare. 
For me, these are no serious alternatives in a production server environment and certainly not what I wanted when I chose a barebone with SAS support. Hope someone else can benefit.

---

### Post by tecquilka on 2008-12-01
Hello,

one solution exist. I had same problem, and here is solution in flash LSI firmware.
At first, you should find SAS address on MainBoard (starting with 5003xxxxxxxxx). This step is very important.
Second step is flash BIOS (and firmware, etc). BUT BEFORE YOU'll flash BIOS, you MUST remove JPA2 (must by unplugged). After that you can flash BIOS.
After that, you'll be able to boot from SAS.

In my case this firmware help:
[ftp://ftp.supermicro.com/driver/SAS/LSI/1064_1068/IT/Firmware/B3/1.24.05/L4i/](ftp://ftp.supermicro.com/driver/SAS/LSI/1064_1068/IT/Firmware/B3/1.24.05/L4i/)

PS: It's good to do that from BOOT disket :-)

---

### Post by KotZer on 2008-12-02
> **tecquilka said:**
> Hello,

one solution exist. I had same problem, and here is solution in flash LSI firmware.
At first, you should find SAS address on MainBoard (starting with 5003xxxxxxxxx). This step is very important.
Second step is flash BIOS (and firmware, etc). BUT BEFORE YOU'll flash BIOS, you MUST remove JPA2 (must by unplugged). After that you can flash BIOS.
After that, you'll be able to boot from SAS.

In my case this firmware help:
[ftp://ftp.supermicro.com/driver/SAS/LSI/1064_1068/IT/Firmware/B3/1.24.05/L4i/](ftp://ftp.supermicro.com/driver/SAS/LSI/1064_1068/IT/Firmware/B3/1.24.05/L4i/)

PS: It's good to do that from BOOT disket :-)

Your answer seem to solve the problem but i would appreciate it if you gave more details ..  How should we search the sas adress. Do you suggest that we should patch the BIOS ??(I have had the same problem trying with 6.06 --> [http://ubuntuforums.org/showthread.php?t=646498](http://ubuntuforums.org/showthread.php?t=646498) )

---

### Post by tecquilka on 2008-12-05
Hello,
so I'll try to be more precisely.
We had some problem with SuperMicro SuperServer 6015C-M3B with X7DCL-3 mainboard.
At first we tried to solve problem with using SAS disks in system by "installing" some drivers (like kernel modules for RHEL on gentoo [gentoo wiki HowTo] etc., but it was useless).
After that, I had a look into manual of motherboard, and here was some part about possibility to not use hardware raid. You just need to find jumper called JPA2, and switch it to position "unplugged". After that, you'll not be able to set-up hardware raid, and u'll be able to see SAS disks from linux. But this mode have one great bug. U're not able to boot from SAS disks. U can use usb, cd or something else.
So for resolve this problem, we contact SuperMicro support. And SuperMicro support helped us :-)

What we need:
Have system bootable from SAS disks, so that means, FLASH LSI controller BIOS (or firmware, it doesn't matter, here is important this fact: "This is not BIOS of motherboard")
So at first some guy from supermicro asked me for serial number of MB... After that, he gave me firmware for my server.
But before flash, I had to be sure - JPA2 is switched to "unplugged" state.
After that I boot from diskette, and start flashing utility. Before flash utility asked me for SAS address of LSI controller, I had look on MB, and find it. Here is link where:
[http://picasaweb.google.cz/tecquilka/Unsorted#5276284506396727234](http://picasaweb.google.cz/tecquilka/Unsorted#5276284506396727234)
After that I finished flashing aaaaand boot from SAS disks.

In this state I'm not able to setup hardware raid (in fact, it's pseudo-hardware raid), but I'm able tu setup software raid, and boot from SAS disks... without any problem.

So solution is (for this time [05/12/08], maybe in future will be problem resolved):
FORGET on any special drivers (like RHEL drivers etc.).
FORGET on pseudo-hardware raid
Turn off LSI Raid features, and make your system useable ;-)


Note1: in IT RAID mode, the controller changes its PCI identification from "LSI MegaRAID SAS 8208ELP" to "LSI 1068E SAS", i.e. the plain LSI 1068 controller without pseudoraid features. Linux kernel supports this controller by mainline mptsas driver.
Note2: Support of SuperMicro can help you with determine which FirmWare you should use :-)

---

### Post by Synchro on 2009-01-29
I've run into this exact problem too. Supermicro told me to use drivers from [here]("ftp://ftp.supermicro.com/driver/SAS/LSI/1064_1068/SR/Driver/Linux/v12.07.1021.2008"), but that all seems to be for RHEL and SuSE. There is an rpm, but I've no idea how to make that available or use it at install time. Anyone else?

---

### Post by Synchro on 2009-02-06
Just to see if RedHat actually works with their drivers, I set up the installer and tried to use the drivers they pointed me at. It loads the driver image file ok, but then says that no devices of that type could be found. This seems to confirm that this motherboard is something of a washout, and doesn't really work with anything other than Windows.

---

### Post by RedShift1 on 2009-04-04
I have exactly the same problem with my [Supermicro X7SB3-F](http://www.supermicro.com/products/motherboard/Xeon3000/3210/X7SB3-F.cfm) motherboard. When setting the onboard LSI SAS controller to IT mode, the BIOS is unable to boot from the LSI SAS controller. I'm going to wait for a response from Supermicro (I've emailed them) before I flash my SAS controller with the firmware suggested above. Obviously this cannot be resolved by using other drivers.

---

### Post by Synchro on 2009-04-04
For the record, I eventually gave up on the built-in controller and bought a 3Ware 9690SA controller. That turned out to be defective, but that was fixed with a replacement.
I also ran into [this bug]("http://bugs.launchpad.net/ubuntu/+bug/312163"), which was fixed by building a 2.6.28 kernel.
All in all, not an easy or pleasant experience. Mind you, I now know more about my RAID controller than I would have had it not been so broken, so it's not a complete loss!

---

### Post by RedShift1 on 2009-04-06
I got answer from Supermicro and they provided me with new firmware for the onboard SAS controller for the X7SB3-F. The board can now boot from the SAS controller in IT (Iniator/Target) mode. I don't know if I'm allowed to redistribute the firmware I got from Supermicro so if you have this problem yourself you need to contact them directly and ask for the firmware.

---


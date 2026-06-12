---
title: "Dual booting Ubuntu and Windows XP using XP Bootloader"
date: 2009-02-13
forum: Windows
---

### Post by kikintosh on 2009-02-13
[SIZE="2"]There are thousands of post out there enough to get anyone confused and give up on the whole idea of dual booting:confused:.

I've been trying and testing for almost a week now, till finally i got it up and running very smoothly and easily.

**In this Tutorial I assume the you have installed windows, ubuntu and grub. non of these processes are explained here, this is only intended to help with the Dual Booting process ONLY**.


----------------------------------------------------------------
[U][B]
Here is my PC configuration[/B][/U]:
[COLOR="Navy"]
Pentium D 3.4 G Hz Core Duo Processor
GIGABYTE Mother board 945 system bus 1066
NVIDIA GeForce 7300 LE Display Adapter
2 GB of RAM
Two 250 GB Hard Drives

**_[COLOR="Black"]My Partition Structure is like this[/COLOR]_**:

Hard Drive 1:-
   Partition a: NTFS 50 GB Windows XP OS - Boot
   Partition b: NTFS 200 GB Data

Hard Drive 2:-
   Partition a: NTFS 205 GB - Data
   Partition b: EXT3 40 GB Ubuntu OS - Boot
   Partition c: SWAP 1 GB Linux Swap[/COLOR]


Note: this information is given as an example, it is NOT the required specification for this process.

------------------------------------------------------------


**Now back to work**

I had windows installed first and i didn't want Ubuntu or Grub to change any setting in windows or the mbr, so i disconnected the data cable to the xp hard drive before i setup Ubuntu. (if you don't know how to, just google it!)
[U]
After you finish installing everything and re-connecting the hdd's[/U]: 

1 - restart into ubuntu.

2 - Using a Flash Memory copy the /boot folder from ubuntu filesystem to the Flash Memory. [COLOR="Red"](Very Important to use the /boot folder installed by ubuntu)[/COLOR]

3 - restart into windows.

4 - download and extract the GRLDR file from [http://sourceforge.net/projects/grub4dos](http://sourceforge.net/projects/grub4dos)

5 - Place the GRLDR file on the Windows C:\ drive.

6 - Edit Boot.ini file and add the following line without the () then close and save:
(C:\GRLDR="Ubuntu 8.10 Linux OS").
[COLOR="Red"]Note: This step is very important, be very Careful not to mess the boot.ini[/COLOR].

7 - Adjust the windows bootloader menu to appear with a timer. (Mine is 3 sec).

8 - Restart.

9 - Select the Ubuntu OS.

10 - Finally Enjoy Dual Booting.



Hope this tutorial helps.


Regards[/SIZE]

---


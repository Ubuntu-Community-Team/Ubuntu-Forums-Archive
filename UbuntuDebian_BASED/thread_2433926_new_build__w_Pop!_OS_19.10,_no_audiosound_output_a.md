---
title: "new build  w/ Pop!_OS 19.10, no audio/sound output and CPU runs hot at idle"
date: 2019-12-27
forum: Ubuntu/Debian BASED
---

### Post by daverader1 on 2019-12-27
As a complete newbie user of any Linux distro, I am wading the waters  and learning on the fly. While it has been challenging and fun, I am  reaching a point of desperation with respect to a couple of lingering  issues I have not been able to resolve.

Disclaimer...I built my computer from scratch. The following link has  the parts list of my new build on which I have installed Pop!_OS 19.10. [https://pcpartpicker.com/user/daverader1/saved/9x7V7P](https://pcpartpicker.com/user/daverader1/saved/9x7V7P)

First problem....I have no audio. My speakers are plugged into the Line  Out on the MOBO. I've tried other outputs on the MOBO. I suspect this is  an issue w/ the setup of the OS.

Secondly, my CPU runs hot at idle, typically ranging 55-65 deg Celsius.  Can anyone provide constructive input to resolve these issues? Even  better, specific steps?

Thanks in advance for any worthwhile assistance that can be provided.

---

### Post by QIII on 2019-12-27
Moved to Ubuntu/Debian BASED

---

### Post by daverader1 on 2019-12-28
Update: I was able to bring about sound via the AlsaMixer in the terminal. I simply tabbed R<>L through the various options (having no clue what each one controls) and cranked up the volume on each to max. My subwoofer does sound very under-powered/muted, so perhaps there is still something to work on there. Not sure about that issue.

Any ideas about the CPU temps at idle? It's driving me bonkers.

---

### Post by oldfred on 2019-12-28
Even though AMD released a UEFI fix in July many vendors took several months to roll out updates for their motherboards.
Have you updated UEFI to latest available.

You also may need newest kernel.
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.4-Hwmon-Zen-2-Thermal](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.4-Hwmon-Zen-2-Thermal)

       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)

---

### Post by daverader1 on 2019-12-28
Pop!_OS 19.10 includes kernel 5.3, so I may need 5.4 as you mentioned. Not sure how to do this in Pop or any other distro for that matter.

I have not updated the UEFI to latest available. I downloaded the file but have no idea how to install it either.

Any specific steps that can be provided would be GREATLY appreciated.

---

### Post by daverader1 on 2019-12-28
So....I was able to update the kernel to 5.4. 

What can I do to update the UEFI?

---

### Post by oldfred on 2019-12-28
Do not have your system, but most UEFI have 3 ways to update.
From Windows, from a DOS bootable flash drive, or directly from UEFI which I use. 
Update file has to be either downloaded or extracted and in a FAT32 partition for UEFI to read it.

Some systems now directly update from Linux. But few motherboard mfgs. on list.
       [https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) 
    
I have changed mount of my ESP from Ubuntu's 0077 to defaults in fstab, so I can copy update file there. Not sure what your system does. You can use any FAT32 partition on a flash drive also.

---

### Post by daverader1 on 2019-12-28
I am running nearly the newest version of BIOS for my MOBO (F10, rather than the most current F11 that just released two weeks ago). I do need to update my MOBO drivers (if that is what you are referring to). I have downloaded the file onto a flash drive formatted w/ FAT32. But I am unable to run the .exe file to update the drivers in Pop! OS 19.10. 

My computer specs: [https://pcpartpicker.com/user/daverader1/saved/9x7V7P](https://pcpartpicker.com/user/daverader1/saved/9x7V7P)

---

### Post by oldfred on 2019-12-28
The download is a zip file. I think the .exe is for using Windows or a DOS flash drive.

In that zip is .f11 file. Do not know for sure, but if you go into UEFI and have that file on a FAT32 partition, it will let you load it directly from UEFI as an update.

---


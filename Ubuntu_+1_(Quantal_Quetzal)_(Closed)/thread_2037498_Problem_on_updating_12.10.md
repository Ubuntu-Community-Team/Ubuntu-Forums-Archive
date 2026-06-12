---
title: "Problem on updating 12.10"
date: 2012-08-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MrSums on 2012-08-04
I have had 12.10 running pretty well on my HP2133.  A couple of days ago I ran a standard update and its now broken.

I can get the machine to boot up into safe mode, so checking the Xorg.0.log I find a segmentation fault  - the final few lines of the log file read:

(EE) 10:  /usr/lib/xorg/modules/driver/openchrome_drv.so
(EE) 11: /usr/bin/X (InitOutput -)xb36)
(EE) 12: /usr/bin/X
(EE) 13: /lib/i386-linux-gnu/libc.so.6
(EE) 14: /usr/bin/X
(EE)
(EE) Segmentation fault at address 0xfc
Fatal server error:
Caught signal 11 (Segmentation fault). Server aborting

Any ideas please? Is this an openchrome issue or an Xorg issue. Should I roll back to a previous version

Cheers

Robert

---

### Post by Toz on 2012-08-04
Hello and welcome to the forums. I'm going to move this thread to the Ubuntu +1 section for better visiblity.

---

### Post by MrSums on 2012-08-07
Well I can partially help myself, but I'd appreciate any help to understand further:

I found a suggestion that I should enter :

             Driver                       "vesa"

into my xorg.conf file. Doing this solved the problem insofar as the machine is concerned, but I don't quite understand why - unless the openchrome driver is not fit for purpose on my HP2133. 

However, since I last played with xorg.conf I think things have changed (!). After the change I made, my xorg.con now contains only 12 real lines:

Section "Device"
   Identifier                      "Configured Video Device"
   Driver                            "vesa"       ; this is the line I input
EndSection

Section "Monitor"
  Identifier                     "Configured Monitor"
EndSection

Section  "Screen"
  Identifier                    "Default Screen"
  Monitor                       "Configured Monitor"
  Device                          "Configure Video Device"
EndSection


So the machine is working, but am I losing out on openchome? any help appreciated

Thanks

Robert

---

### Post by effenberg0x0 on 2012-08-07
> **MrSums said:**
> Well I can partially help myself, but I'd appreciate any help to understand further:

I found a suggestion that I should enter :

             Driver                       "vesa"

into my xorg.conf file. Doing this solved the problem insofar as the machine is concerned, but I don't quite understand why - unless the openchrome driver is not fit for purpose on my HP2133. 

However, since I last played with xorg.conf I think things have changed (!). After the change I made, my xorg.con now contains only 12 real lines:

Section "Device"
   Identifier                      "Configured Video Device"
   Driver                            "vesa"       ; this is the line I input
EndSection

Section "Monitor"
  Identifier                     "Configured Monitor"
EndSection

Section  "Screen"
  Identifier                    "Default Screen"
  Monitor                       "Configured Monitor"
  Device                          "Configure Video Device"
EndSection


So the machine is working, but am I losing out on openchome? any help appreciated

Thanks

Robert

Hi Robert,

It looks like this machine has a VIA VGA chipset so openchrome should be the way to go. However, I found some reports of people mentioning that drivers from VIA work better. There's some info here: [https://wiki.edubuntu.org/LaptopTestingTeam/HP2133#User_Related_Comments_.28Some_issues_may_be_resolved.29](https://wiki.edubuntu.org/LaptopTestingTeam/HP2133#User_Related_Comments_.28Some_issues_may_be_resolved.29)

Regards,
Effenberg

---

### Post by MrSums on 2012-08-08
Thanks for the input, helpful article - but it seems Via have not yet released a driver for 12.10. Could be I'll have to wait a while. Perhaps the Openchrome is not up to date yet either.

MrSums

---


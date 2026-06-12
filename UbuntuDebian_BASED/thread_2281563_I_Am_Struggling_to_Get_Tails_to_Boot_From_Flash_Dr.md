---
title: "I Am Struggling to Get Tails to Boot From Flash Drive"
date: 2015-06-07
forum: Ubuntu/Debian BASED
---

### Post by jim112 on 2015-06-07
Hi everyone,
I have been trying to get Tails burned onto and boot up from a flash drive for days now and I'm losing my mind from the series of PITA problems I've run into. Somehow I got Tails burned onto my USB drive using the instructions provided on the Tails website (I previously ran into a million random problems). Now when I try to boot from Tails, my USB drive will flash for about 15 seconds and then Ubuntu starts up with no errors or anything. I've tried researching this problem but I'm struggling to find similar situations or even understand some of what I'm reading. I'm a noob so I'm still learning a lot fo the language.

The flash drive that I'm using is a 4gb Dane-Elec and I burned the Tails ISO onto it straight out of the box. The format of the USB drive is FAT32. That's about all I know at this point. 

I read something yesterday that made me think this could be an issue with a missing driver. Is that possible/likely?

Please help as I am ready to pull my hair out at this point. 

Thanks in advance!

---

### Post by QIII on 2015-06-07
Moved to Ubuntu/Debian BASED.

---

### Post by jim112 on 2015-06-08
Anyone?

---

### Post by andrew102 on 2015-06-10
To boot from USB, it needs to be supported by BIOS. Modern computers with EFI usually allow for this, allow sometimes it needs to be enabled by entering the bios options and selecting legacy boot. Then select USB as boot option.

Also please note that for a bootable device, first the drive needs to be formatted as BOOTABLE. You need to extract the files from the .iso first and then copy to the drive. (i.e. If you have copied the raw .iso file to the / directory of the device then it will not work.)

Alternatively use an image burning tool to burn the .iso to CD (make sure you make it bootable in the process).

---


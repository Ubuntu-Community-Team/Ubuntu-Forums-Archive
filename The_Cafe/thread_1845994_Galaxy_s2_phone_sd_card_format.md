---
title: "Galaxy s2 phone sd card format"
date: 2011-09-18
forum: The Cafe
---

### Post by The Cog on 2011-09-18
I just bought a Galaxy s2 phone. I'd like to add an SD card to increase its memory (there's a micro-SD slot under the battery). Does anyone know how I should format the SD card? FAT/NTFS/ext2 etc?

Thanks.

---

### Post by NCLI on 2011-09-18
> **The Cog said:**
> I just bought a Galaxy s2 phone. I'd like to add an SD card to increase its memory (there's a micro-SD slot under the battery). Does anyone know how I should format the SD card? FAT/NTFS/ext2 etc?

Thanks.

fat32 I believe. Though I think the phone can take care of it on its own.

---

### Post by matchett808 on 2011-09-18
Hi, it should be FAT me thinks, my atrix is FAT - think its normal for android phones?

Give it a try, or put the SD card in the phone and go to settings > SD Card & phone storage, scroll down to the sd card feild, unmount, then format...

quick edit to fix the name of the menus!

---

### Post by The Cog on 2011-09-18
That was quick! Thank you, I'll try FAT32 then.
Cheers.

---

### Post by psrdotcom on 2011-09-18
After inserting the memory card into phone .. Go to settings and format the card in phone itself ..

---

### Post by koleoptero on 2011-09-18
I doubt you'll have to format the card.

---

### Post by aysiu on 2011-09-18
> **koleoptero said:**
> I doubt you'll have to format the card.
This is correct. The card will likely come formatted as FAT32 or FAT16 already.

---

### Post by The Cog on 2011-09-18
Fat32 worked nicely, thanks.

To use the USB connectivity to access the files on the phone from Ubuntu, you have to enable USB debugging on the phone first. (Under Settings -> Applications - Development).

Having connected the cable, pull down the status panel from the top and tap the **USB Connected** message. Then tap the **Connect USB Storage** button.

---

### Post by aysiu on 2011-09-18
That's odd. I don't have a Galaxy S2, but I've had two Android phones (MyTouch 3G and MyTouch 4G) and have never had to enable USB debugging to get Ubuntu to recognize it.

---

### Post by The Cog on 2011-09-18
If you don't enable debugging, as soon as you plug the USB lead in, something called "Samsung Kies" takes over. Apparently, it only talks to a windows-only custom client. I read it on the internet, so it must be true. Apart from which, without debugging enabled, Kies grabs the phone GUI and won't let you do anything (and no USB drives appear in thunar).

---

### Post by aysiu on 2011-09-18
Ah! Both my Android phones were HTC, so no Samsung custom software.

---

### Post by NCLI on 2011-09-19
I can confirm that Samsung's custom android build sucks hard... If you feel like it, install Cyanogenmod 7 :)

---


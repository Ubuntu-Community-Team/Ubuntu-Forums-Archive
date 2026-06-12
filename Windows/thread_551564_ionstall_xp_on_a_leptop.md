---
title: "ionstall xp on a leptop"
date: 2007-09-15
forum: Windows
---

### Post by Chymera on 2007-09-15
i got a fujitsu siemens laptop over here, which badly needed a windows reinstall.
I created a new partition from a part of the free space on it via a gparted livecd, and copied all important data to it. Now i boot from the winxp install cd, and after it copies the windows files on my hdd, it says it has to reboot.
ok, so it reboots, and gives me the following message "Disk error Press any key to restart"

The win install cd is authentic and came with the laptop.


...now, the laptop is not really mine, and its owner mentioned something about getting a bios virus some time ago. He is not very knowledgeable about computers, and i doubt he has any idea what a bios virus means.... also i beg to differ that an average user can get such a virus.

Anyway, could it be the cause of this? how can i check?

---

### Post by Imsati on 2007-09-15
Just off the top of my head...

Is the HDD seated properly? If it was removed it may not have been reinserted completely.
Is BIOS set to boot to the CD? Many models are (were) set to Floppy, HDD, then CD by default.

How old is the laptop? Is it the original HDD? Certain viruses can wreak havoc and literally destroy them. Sometimes they just fail too after a certain time. Older laptop drives *typically* have a shorter life span due to relatively-poor heat dissipation compared to desktops and/or newer laptops.

Did he say why he thought it was a BIOS virus and not something else?

--Jay

---

### Post by digital_exhaust on 2007-09-15
I'm pretty sure that the owner of the laptop meant to say" boot sector virus" rather than" bios virus", and the odds of a boot sector virus being the issue are slim to none... 

My money is on a bad install cd, perhaps try a different install disc.. Good luck..

---

### Post by Chymera on 2007-09-16
it was the install cd that came with the laptop, i tried another original cd of xp i had and it didnt even want to install, just said th computer has no hdd :confused:

Which is rather strange since i installed ubuntu on it without any problem.

---

### Post by smoker on 2007-09-17
a few suggestions: are you installing to the first partition on the hard drive?  on install did you choose a 'full' format for that partition, rather than quick? if problems continue, try deleting the first partition and creating a new bootable dos partition with a win98 boot disk if you can, or the gparted live-cd.

you could also check the drive out by downloading a diagnostic from the drive manufacturers website,

best of luck

---

### Post by Chymera on 2007-09-18
it has only one hdd, and yes, i am installing on the first partition, i have tried full formating with ntfs as well as fat32.

---

### Post by Imsati on 2007-09-20
Wow, I totally forgot about this thread--so sorry!

Are you still having problems with it? Shoot me an e-mail at [email]imsati@comcast.net[/email] if you are as I'm not sure when I'll have a chance to check these forums again. I'll try to offer some advice.

--Jay

---


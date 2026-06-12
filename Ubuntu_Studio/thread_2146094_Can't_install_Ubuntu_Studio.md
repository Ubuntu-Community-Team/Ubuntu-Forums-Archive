---
title: "Can't install Ubuntu Studio"
date: 2013-05-17
forum: Ubuntu Studio
---

### Post by David Matthew on 2013-05-17
Hi,

I'm new to Ubuntu, and am running Raring Ringtail 13.04 on a Lenovo Ideapad Z580. I wanted to configure it for audio but knowing now the complexities involved in getting the best working low-latency configuration up and running, I decided to install a distro specializing in audio/multimedia. This led me to Ubuntu Studio.

I downloaded the iso file, burnt it to a DVD using the program Ubuntu selects to do this by default, and rebooted my machine. I was brought to the boot menu, and when I clicked the DVD option I was brought to the expected options: Try Ubuntu Studio without Installing, Install Ubuntu Studio, Check disk for defects etc. All fine so far, but as soon as I select any of these options, the screen goes blank, and the disk loads for a second of two before beeping off, and the screen just stays blank from then on.

I've tried it several times, and even burnt another DVD thinking the disk might be faulty. Now even the standard install of Ubuntu seems to have been affected by this - sometimes the GRUB menu comes up instead of just booting up properly, and once or twice the screen just stayed completely blank upon starting up. 

Has all this something to do with graphic drivers maybe? I'm very new to all this, and would really appreciate some pointers.

Thanks.

---

### Post by cub on 2013-05-17
Did you check the downloaded file again the md5sum? It might be that the download was a bit corrupted?

---

### Post by Sylos on 2013-05-18
Try pressing F6 when you get to the Boot Selection Screen. Then select the "nomodeset" boot option and see if that helps.

Cheers

---

### Post by David Matthew on 2013-05-18
Thanks for the suggestions guys, I will check the downloaded iso file against the corresponding md5sum to verify that it wasn't corrupted.

Re: pressing F6 at the boot selection screen - it doesn't appear that I'm given that option. The screen I'm shown isn't [like this]("http://img827.imageshack.us/img827/3509/dgfdgrunningoraclevmvir.png") unfortunately. It's [like this]("http://screenshots.debian.net/screenshots/g/grub-pc/9747_large.png"), but the GRUB version is 2.00-13ubuntu3, and I'm given these options:

Try Ubuntu Studio without installing
Install Ubuntu Studio
OEM install (for manufacturers)
Check disc for defects

How would I go about setting nomodeset from there?

Thanks again.

---

### Post by Sylos on 2013-05-18
Ah - I see. 

At the bottom of the screen you have it mentions pressing 'e' to edit the commands. Press 'e' and add nomodeset to the end of the boot line.

Is that screen what you get with the Live CD/DVD as well? I thought that was only for an OS installed on the HDD.


Cheers

---


---
title: "[SOLVED] windows XP drivers on toshiba salelite"
date: 2008-07-21
forum: Windows
---

### Post by jnw222 on 2008-07-21
I have a toshiba satelite L35-S2366 that originally came with windows Vista installed

wiped everyting for ubuntu (vista too slow and broke) and now i have some windows games i want to run natively (i do not mind rebooting) at full speed but installing xp left me powerless as the wifi did not work

---

### Post by spud.dups on 2008-07-21
So is the problem that you can't get your wifi to work in winXP, or that you like to run xp in ubuntu so you can run your games and still have the internet work?

---

### Post by jnw222 on 2008-07-21
?
i am not trying to run in any virtualization software just xp by itself not in ubuntu

---

### Post by kerry_s on 2008-07-21
> **jnw222 said:**
> I have a toshiba satelite L35-S2366 that originally came with windows Vista installed

wiped everyting for ubuntu (vista too slow and broke) and now i have some windows games i want to run natively (i do not mind rebooting) at full speed but installing xp left me powerless as the wifi did not work

use the toshiba restore cd to install the wireless driver in xp, use the update driver and point it to the cd.

---

### Post by seanc7 on 2008-07-21
Have you looked on the Toshiba website to see if they have XP versions of the drivers?

---

### Post by jnw222 on 2008-07-25
i tried he website and vista recovery disk but after the install nothing changed

i am trying to use xp SP3 now after an upgrade from Sp1

---

### Post by rockface on 2008-07-25
> **seanc7 said:**
> Have you looked on the Toshiba website to see if they have XP versions of the drivers?

Toshiba don't have the most user friendly of web sites. Could this be a laptop with only Vista drivers?

Had a brief look through Google results and on some forums solutions have been found to work around some problems. But it is not easy and people seem have to go out of their way to install XP on this device.

---

### Post by jnw222 on 2008-07-25
They seem to only have drivers for vista

---

### Post by estamand on 2008-07-25
Check the Toshiba Europe website.  They seem to have XP Drivers

[http://www.toshiba-tro.de/](http://www.toshiba-tro.de/)

---

### Post by rockface on 2008-07-25
> **estamand said:**
> Check the Toshiba Europe website.  They seem to have XP Drivers

[http://www.toshiba-tro.de/](http://www.toshiba-tro.de/)

I was intrigued by the initial web page introduced by this URL, it seems to have  a superior interface to other Toshiba web sites. But you click on 'Driver Downloads' it returns you to a menu based system that left me scratching my head. I got this menu when visiting Toshiba's web site in the first place.

'Chasing my tail' would be a good description on trying to make sense of various Toshiba web sites as far as driver support goes. I have seen some workarounds for graphics, sound, ethernet etc but not wi-fi.

If the Toshiba L35-S2366 you mention has a number of variations this also effects the driver situation.

If you can gain access to all drivers for your model of laptop try them all, Vista back to 2000 (if they are even available). What do you have to loose?

I wish you luck.

---

### Post by jnw222 on 2008-07-26
wifi-done
sound-not done 
display-in progress

---

### Post by hllon4whls on 2008-08-28
From the toshiba website download the following drivers.
ati_24711c.exe - video chipset driver
realtek_25234A.exe
modem_driver_24711c.exe
ta8wlanax.exe (not the one that says foxconn)

You will need the realtek 3d maybe high def audio utility to make the sound work and you cant use the wifi utility with you your wifi card 
(filename su200wlanutilax.exe)-do not load.

I gave you mostly partial file names. You should be able to find them. I used L35 XP in the ask iris search engine to find these. Dont worry if it doesnt match your computer model exactly. I just did this myself on my second attempt to load XP. I have no hardware errors and everything from the sound to the wifi works perfectly. I have no use for the modem, so I didnt try it but it seems to be happy.

The toshiba driver section seems to be down for maintenance, so I couldnt get any more info. If you follow wiht the suggestions, I think that you can get everything to work as I have.

Good luck and it feels pretty good once you have it all working like you want it to.

---


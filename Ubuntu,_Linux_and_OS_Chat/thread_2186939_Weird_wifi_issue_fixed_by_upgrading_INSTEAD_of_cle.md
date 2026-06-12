---
title: "Weird wifi issue fixed by upgrading INSTEAD of clean install"
date: 2013-11-10
forum: Ubuntu, Linux and OS Chat
---

### Post by user1397 on 2013-11-10
Just thought I'd share my weird experience.  

So since kernel 3.something I've had to attach the following to my grub boot kernel parameters to make wifi (and standby) work on my laptop "acpi_backlight=vendor"

My 13.04 install was working perfectly, but when 13.10 came out I decided to wipe and install 13.10 (because I was excited to try it out and I wanted updated programs of course).

So I installed and my wifi would simply not work.  I tried to research on here and elsewhere to see if other people had similar issues.  Several people had my exact issue but I could not find a reliable fix.  Basically, when I looked for wifi networks, it showed 1 bar for all of the nearby networks, and when I tried to connect to mine, it would ask me for the password, I would put it in, and then it would just ask me for the password again.  I could never actually connect to it (I even tried other, unprotected networks and still no go).

I started thinking it was an ubuntu thing so I tried linux mint, then linux mint debian edition, then I tried actual debian testing, and all of them had the same problem.

So, I decided to just reinstall 13.04 out of frustration.  Then the epiphany happened, and I just tried the regular update method to upgrade from 13.04 to 13.10 and voila! Everything worked...

WEIRD HUH?

I mean, to me it sounds like somehow my wifi was configured (I don't know if the driver or what else) correctly in 13.04, and when I upgraded those settings didn't change, whereas it somehow wasn't configured on the clean install of 13.10.  I still don't know exactly what could have not been configured (there are no proprietary drivers in use on my laptop.)

---

### Post by philinux on 2013-11-10
Moved to U L and OS chat.

---

### Post by craig10x on 2013-11-11
It might be because when upgrading, most basic settings are actually carried over to the new version...i use the upgrade option on the iso disc installer and when i do, the majority of my settings are remembered...things like the way i adjusted things in system settings, settings on my installed applications, my browser extensions and settings, and even the URL caches...plus all the data i had (photos, music, docs, etc)...like just about everything...so maybe that is why...

Just curious...which method did you use for your upgrade?  The software updater? terminal method or iso installer method (like i do)?
And how long did it take (just wondering) :D

Perhaps others will have their theories as to why that was...but i have a suspicion that mine might be right...it may sound strange but i think there could be merit to it....;)
And of course, when doing a clean install, EVERYTHING (including all settings) gets wiped out...not so with the UPGRADE method...

---

### Post by craig10x on 2013-11-12
I guess the original poster isn't coming back...and no one else commented here anyway...oh well...i was curious to the method he used to do his upgrade but i think my theory probably holds...the upgrades do bring over the settings from your original install and since it worked in his old version it carried over to the new one as well...what was different about the new version that prevented him from setting it correctly (when he originally did the clean install) will probably remain a mystery...

---


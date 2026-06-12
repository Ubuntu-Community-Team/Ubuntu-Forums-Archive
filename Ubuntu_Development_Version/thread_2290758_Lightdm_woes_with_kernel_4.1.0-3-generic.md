---
title: "Lightdm woes with kernel 4.1.0-3-generic"
date: 2015-08-15
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-08-15
With the upgrade to 4.1.0-3-generic, lightdm starts after the 2nd or 3rd attempt to boot. Has this happen to anyone else?

---

### Post by dino99 on 2015-08-15
no problem here on i386 & gnome-shell session

---

### Post by rrnbtter on 2015-08-15
Greetings,
I'm fairly certain that it is not kernel related.  More like a dependency problem. If you have "proposed" enabled "stuff happens". Also, dino99 is correct that the Gnome desktop is not affected with this problem since it uses gdm and not lightdm. 
The solution for me was to reinstall from the latest Ubuntu desktop iso. The nice thing about Ubuntu (and Gnome) is that if your partitions are setup right and your update procedure is right all of your software settings will be preserved. Hence a reinstall takes at most thirty minutes.  Have fun with your learning opportunity!

---

### Post by vandend278 on 2015-08-15
> **Chanath said:**
> With the upgrade to 4.1.0-3-generic, lightdm starts after the 2nd or 3rd attempt to boot. Has this happen to anyone else?


sudo apt-get install --reinstall lightdm

you're good, reboot.

---

### Post by ventrical on 2015-08-15
> **Chanath said:**
> With the upgrade to 4.1.0-3-generic, lightdm starts after the 2nd or 3rd attempt to boot. Has this happen to anyone else?

Certain hardware can produce these scenarios. What are your mobo/graphics card specs?

Regards..

---

### Post by QDR06VV9 on 2015-08-15
> **ventrical said:**
> certain hardware can produce these scenarios. What are your mobo/graphics card specs?

Regards..
+1:d
VinDSL a couple of weeks ago went through similar.
Regards

---

### Post by Chanath on 2015-08-15
> **vandend278 said:**
> sudo apt-get install --reinstall lightdm

you're good, reboot.

Thanks! This was what I did after few tries of booting to lightdm with this kernel. I did few dist-upgrades and its working now. There was no problem with the older kernel at all. :)

@ventrical 
No, this was not a hardware problem, as I was using this laptop with precise too.

@dino99 and rrnbtter
This was a lightdm problem, not a gdm problem.

---

### Post by rrnbtter on 2015-08-15
Greetings,
I never said it was a GDM problem but it was a incomplete lightdm upgrade problem that caused the system to lose the display setup. Hence the solution in post #4 wouldn't work.  This will sound odd but if you "sudo apt-get install gdm, reboot and then run post #4 it will work. That is because gdm isn't broken and it will re-setup the display and lightdm will follow the gdm settings when you reinstall it (lightdm).

---

### Post by Chanath on 2015-08-15
> **rrnbtter said:**
> Greetings,
I never said it was a GDM problem but it was a incomplete lightdm upgrade problem that caused the system to lose the display setup. Hence the solution in post #4 wouldn't work.  This will sound odd but if you "sudo apt-get install gdm, reboot and then run post #4 it will work. That is because gdm isn't broken and it will re-setup the display and lightdm will follow the gdm settings when you reinstall it (lightdm).

Can't afford to do that. If I do sudo apt-get install gdm, I'd get hell of a lot unnecessary files installed. 
> 0 upgraded, 167 newly installed, 0 to remove and 0 not upgraded.
Need to get 49,4 MB of archives.
After this operation, 209 MB of additional disk space will be used.
I'm not in a hurry, so I'd wait for the Ubuntu devs to find a way out of the lightdm problem. Mine actually had gone.:)

---


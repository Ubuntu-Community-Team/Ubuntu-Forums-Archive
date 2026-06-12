---
title: "should I reinstall windows programs after a wine upgrade?"
date: 2009-03-19
forum: Wine
---

### Post by gatorbrit on 2009-03-19
After installing a new version of wine, does it make sense to reinstall the windows software?

Will the windows software work "better" automatically, or do improvements to wine only affect new installations of software?

Thanks

---

### Post by hikaricore on 2009-03-19
No you do not need to reinstall software after a WINE update.

---

### Post by Meow27 on 2009-03-19
for very unsupported programs yes, but overall, the files are not extracted incorrectly during install in Wine, so the overall answer is no.

and when i mean unsupported, i mean something that has a garbage rating in appdb

---

### Post by hikaricore on 2009-03-19
> **Meow27 said:**
> for very unsupported programs yes, but overall, the files are not extracted incorrectly during install in Wine, so the overall answer is no.

and when i mean unsupported, i mean something that has a garbage rating in appdb


Upgrading WINE will not affect winetricks or other dlls including overrides.

If you have a program that requires you to tweak the hell out of WINE just to get it to run you probably shouldn't be updating WINE anyway.

---

### Post by cogadh on 2009-03-19
Even with unsupported/garbage rated software, you still don't need to reinstall them (assuming they were never uninstalled) when you update Wine. Updating Wine just updates the Wine "application" itself, it doesn't technically make any changes to the .wine directory or any of your settings, so whatever is installed will be exactly the same as it was before you updated.

---

### Post by ahso4271 on 2010-12-01
updated from 1.3.7 to 1.3.8 by compiling the source (as always) and i always had to reinstall all windows apps. Now i did a copy of .wine but still it doesnt work. Any hints on how to upgrade without reinstalling all?
Thanks

---

### Post by WienerWuerstel on 2010-12-01
> **ahso4271 said:**
> updated from 1.3.7 to 1.3.8 by compiling the source (as always) and i always had to reinstall all windows apps. Now i did a copy of .wine but still it doesnt work. Any hints on how to upgrade without reinstalling all?
Thanks

Use the Ubuntu Wine PPA.

---

### Post by ahso4271 on 2010-12-01
my fault sorry. Works fine, even Tomb Raider Underworld.

---


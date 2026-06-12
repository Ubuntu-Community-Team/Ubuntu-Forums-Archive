---
title: "Fonts"
date: 2007-11-13
forum: Ubuntuzilla
---

### Post by kalpik on 2007-11-13
Hi!

Just installed ubuntuzilla firefox on a gutsy installation. Everything seems fine, but the fonts are a bit off. It seems as if ubuntuzilla firefox is not picking up msttcorefonts. Did i miss anything?

---

### Post by adza on 2007-11-14
the ms fonts are not free as in beer and freedom, hence not included as default in the distro. to get the fonts your are after (and some other really cool stuff as well), ```
 sudo apt-get install ubuntu-restricted-extras 
``` have fun :)

---

### Post by kalpik on 2007-11-14
The issue is not that! I already HAVE the fonts installed! They were working fine on the official build.. Just that the ubuntuzilla build (2.0.0.9) does not render using those.

---

### Post by kalpik on 2007-11-14
Anyone else facing this issue? i.e. difference in font rendering between the ubuntu build and the mozilla build?

---

### Post by kalpik on 2007-11-14
Ok, im posting screenshots:

Ubuntu Build:
[[IMG]http://img250.imageshack.us/img250/3645/screenshototherantivirucf3.th.png[/IMG]](http://img250.imageshack.us/my.php?image=screenshototherantivirucf3.png)

Mozilla (Ubuntuzilla) Build:
[[IMG]http://img339.imageshack.us/img339/3807/screenshototherantivirutg4.th.png[/IMG]](http://img339.imageshack.us/my.php?image=screenshototherantivirutg4.png)

---

### Post by nanotube on 2007-11-14
hmm.. i don't know what's up with this...
have you tried looking in firefox fonts preferences to see if maybe there's something there you could change?
or see if the ms fonts even show up in the font selection dialogs?

---

### Post by kalpik on 2007-11-14
The font preferences are exactly the same in both builds. :(

---

### Post by kalpik on 2007-11-16
So i checked out switfox, and swiftfox maintains the font rendering. Guess ill stick with swiftfox then.

---

### Post by nanotube on 2007-11-17
> **kalpik said:**
> So i checked out switfox, and swiftfox maintains the font rendering. Guess ill stick with swiftfox then.

ok, cool. sorry i wasn't able to solve your font problem with the official mozilla build...

---

### Post by kalpik on 2007-11-17
No problem! Thanks for your help :)

---

### Post by BillShepp on 2007-12-13
I see the difference in fonts as well.  I believe the issue is that the standard build of Firefox has the configuration option "--disable-freetype2", while the Ubuntu build does not.  I find my menu fonts with the standard build are much thinner than with the Ubuntu build.

---


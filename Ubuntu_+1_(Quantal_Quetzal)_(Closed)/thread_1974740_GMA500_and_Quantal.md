---
title: "GMA500 and Quantal"
date: 2012-05-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fjgaude on 2012-05-06
On my Dell mini 1010n I opened a new partition and loaded 12.04, then changed the repository to qualtal and upgraded the system to 12.10. Then noticed the screen brightness was set to about half with the keys for up and down not working. And it wouldn't go to sleep. Changed to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet console=tty1 acpi_osi=Linux mem=896mb"
```

and removed ```
ADD_PARAMETERS='--quirk-vbemode-restore'
``` in /etc/pm

Results: nothing worked. Brightness low and no suspend much less resume.

But everything else was fine, so far. gtkperf ran at 36.50, about the same as in 12.04.

It's a start, huh, Luca?

---

### Post by lucazade on 2012-05-06
Thanks for pointing this out fjgaude.. 
I'll give Quantal a look in the next months when more updated bits will be in :)

---

### Post by fjgaude on 2012-05-06
I'm dual-booting my Dell and with the install of 12.10 a new grub.conf was made, of course. But that file wasn't like it should be for the 12.04 boot left my perfect install not working fully correct.

I did an update-grub, grub-install and the 12.04 is back to perfect. Wow! Can't be too careful with the really early builds.

---

### Post by cmccauley on 2012-05-11
Wow, was just about to upgrade my Mini 10 with the daily Quantal iso. Thanks for the warnings.

Chris

---

### Post by fjgaude on 2012-05-11
I just keep watching this important link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

The guys keep it up to date. We are almost there; kernel 3.4 seems to have things in it not to gma500's liking. But I'm sure this will get fixed before release.

I'm fully satisfied with 12.04 now.

---

### Post by mikewhatever on 2012-06-11
The recently released Alpha1 just worked on a Dell mini 10 here. It still runs Unity2d, which will have been dropped sometime into the cycle, and the module was renamed from psb_gfx to gma500_gfx. Brightness keys worked too, though the brightness notification didn't show.

---

### Post by fjgaude on 2012-06-11
Glad things are working correctly for you, well, almost. Mine is the same on 12.04. With 12.10 I did nothing and it is working fine also, except for Suspend and Resume... that'll be fixed likely as we get close to release in October.

---


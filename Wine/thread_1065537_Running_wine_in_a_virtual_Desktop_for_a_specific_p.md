---
title: "Running wine in a virtual Desktop for a specific program only"
date: 2009-02-10
forum: Wine
---

### Post by AllRadioisDead on 2009-02-10
Hi, I recently installed Halo custom edition. I had to configure wine to use a virtual desktop for halo to display properly, but I don't want all my programs using the virtual Desktop. How can I fix this?

---

### Post by hikaricore on 2009-02-10
> **ihermit said:**
> Hi, I recently installed Halo custom edition. I had to configure wine to use a virtual desktop for halo to display properly, but I don't want all my programs using the virtual Desktop. How can I fix this?

> wine explorer /desktop=Halo,**1400x1050** _whateverthebinaryforhaloiscalled_

Launch halo as such^  replacing the desktop size of **1400x1050** with whatever you need it to be sized at and replacing _whateverthebinaryforhaloiscalled_ with the name of the Halo binary.

This way you can launch Halo in it's own virtual desktop and have all other WINE applications launch normally (after of course modifying the setting for WINE).

---

### Post by Ng Oon-Ee on 2009-02-10
The other way is to use WINEPREFIX=<somedirectory> in front of all your HALO related commands, and creating a copy of ~/.wine in <somedirectory> which is only used for HALO.

This has the added benefit that your HALO installation and all its settings/registry fixes is separate from your main ~/.wine installation.

---

### Post by cb951303 on 2009-02-10
another way is to fireup winecfg, add and select halo.exe in the applications list, enabling virtual desktop

---

### Post by AllRadioisDead on 2009-02-10
> **cb951303 said:**
> another way is to fireup winecfg, add and select halo.exe in the applications list, enabling virtual desktop
Woah! I didn't know you could do that, that's incredible. I had no idea the wine CFG allowed you to configure settings for specific programs, thanks a lot! Thanks for the other posts as well, but this one really blew me away.

---

### Post by hikaricore on 2009-02-10
> **cb951303 said:**
> another way is to fireup winecfg, add and select halo.exe in the applications list, enabling virtual desktop

Meh I completely forgot about that.

When I was your age we didn't have fancy winecfg individual applicaion configuration.
We walked uphill both ways through the lava to launch our apps and they all ran at 1fps.
And you know what?  We liked it.  :lolflag:

---


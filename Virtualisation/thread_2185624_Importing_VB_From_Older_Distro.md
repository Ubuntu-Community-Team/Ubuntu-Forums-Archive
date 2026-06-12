---
title: "Importing VB From Older Distro"
date: 2013-11-03
forum: Virtualisation
---

### Post by NM5TF on 2013-11-03
Hi Gurus...

I have a Virtual Box running WinXP under Ubuntu 12.04.3 that I would like to import
into my Ubuntu 14.04 distro....is this even possible :?

If so, how would that be done :confused:

I need to use XP for on-line training to keep my HazWOpER Certification up to date
and the training system only runs under IE8...yeah I know, but have no choice in the
matter:-(

I no longer have access to the Win XP install disc, so can't just re-install it in 14.04:-({|=

TIA,

Tommy

---

### Post by Habitual on 2013-11-03
File > Export Appliance
on the new host
File Import Appliance

---

### Post by NM5TF on 2013-11-03
> **Habitual said:**
> File > Export Appliance
on the new host
File Import Appliance

thanx for quick response habitual...

if I understand this correctly...log into 12.04...export appliance...log into 14.04...import appliance...

correct???

Tommy

---

### Post by Habitual on 2013-11-03
Yes, the export creates an .ova file. You will have to move that file to the new instance|host|whatever and then
File > Import Appliance...
point it at the same .ova and
bingo.

---

### Post by NM5TF on 2013-11-04
thanks Habitual...

working great now....was almost too easy

Tommy

---

### Post by Habitual on 2013-11-04
You're very welcome.

---


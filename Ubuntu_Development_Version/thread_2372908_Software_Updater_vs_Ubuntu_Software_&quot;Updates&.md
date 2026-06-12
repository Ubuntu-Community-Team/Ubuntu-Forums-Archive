---
title: "Software Updater vs Ubuntu Software &quot;Updates&quot;"
date: 2017-09-30
forum: Ubuntu Development Version
---

### Post by horizonbrave on 2017-09-30
Hi,
I'm running an updated version of 17.10.
Please, could someone clarify me what's the "Updates" tab in Ubuntu Software? Is it intended for updating the system like in Gnome Software?
Does it create any conflict with Software Updater? I'm just a bit confused about this two updating tools in the system and about how they interact between each other or what are Canonical plans with them.

Many thanks :)

---

### Post by dino99 on 2017-09-30
As you says, its confusing, not user friendly. For updating/upgrading, synaptic is a way better tool, even if it is quite old and not really maintained nowadays; its a pitty.

---

### Post by ventrical on 2017-09-30
> **dino99 said:**
> As you says, its confusing, not user friendly. For updating/upgrading, synaptic is a way better tool, even if it is quite old and not really maintained nowadays; its a pitty.

yep.. new gnome3 even has it's "own" synaptic type package updater..

```

gnome-packagekit

```

regards.

---

### Post by dino99 on 2017-09-30
Thanks Ventrical for that info, i was not aware about it.

System Tools -> Package to load it: looks good, but still less configurable than synaptic.

---

### Post by flocculant on 2017-10-01
To actually answer the question - 

Updates" tab in Ubuntu Software - to tell the system where updates will come from.

Software Updater - to actually update software.

---

### Post by jbicha on 2017-10-01
The GNOME/Ubuntu Software app can also update device firmware, GNOME Shell extensions, Snap apps, and Flatpak apps.

There are some things it can't do yet:
- Update your system apps (traditional apt packages) without requiring you to reboot and install them "offline"
- Integrate with Ubuntu's system for upgrading to a new Ubuntu release (for instance, Ubuntu 17.04 &#8594; Ubuntu 17.10)
- Respect Ubuntu's Phased Updates system (Software Updater is the only thing in Ubuntu that does)

As a workaround for those issues, the system app update feature has been disabled in the GNOME/Ubuntu Software app for 17.10. Therefore, Software Updater and GNOME/Ubuntu Software provide updates for different things.

I think the long-term goal is to drop the Software Updater app but that will require significant developer work.

By the way, the GNOME/Ubuntu Software app has been switched during the 17.10 release cycle to use the same PackageKit system used by upstream. #1 wasn't a problem before that but is an issue for all GNOME distros.

---


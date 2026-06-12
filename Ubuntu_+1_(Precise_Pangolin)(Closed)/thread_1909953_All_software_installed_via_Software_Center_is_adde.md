---
title: "All software installed via Software Center is added to the Launcher"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-16
I've been testing Software Center now, as it is a little more mature than previous releases. 

Not sure if this is a new feature. Every software added via Software Center is now added to the launcher. Sometimes it makes no sense (like when you install flashplugin-installer. Users might not want it on the launcher anyway). 

It's necessary to right-click the software icon it and select "Unlock from Launcher" for every newly installed software that shouldn't be on the launcher.

This is not a bug per se, but it seems a little odd as a default behaviour IMO.

---

### Post by dino99 on 2012-01-16
yeah it needs some more fine tunes, might needs a config files (maybe dconf already do that) to set preferences instead of needing to unlock each time the "nonsense" entries.

---

### Post by mc4man on 2012-01-16
> **effenberg0x0 said:**
> I've been testing Software Center now, as it is a little more mature than previous releases. 

Not sure if this is a new feature. Every software added via Software Center is now added to the launcher. Sometimes it makes no sense (like when you install flashplugin-installer. Users might not want it on the launcher anyway). 

It's necessary to right-click the software icon it and select "Unlock from Launcher" for every newly installed software that shouldn't be on the launcher.

This is not a bug per se, but it seems a little odd as a default behaviour IMO.

I would think the auto add is a design change so no bug there but apps that don't have .desktops being added would be. 
Haven't been using S-C much so only came across 1 'improper' addition some time ago (7zip
Have a report on though no action, there could be other reports, don't know

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/907160](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/907160)

---

### Post by kyleabaker on 2012-01-16
It looks like Bilal is working on something like this. Sounds more annoying than useful. I usually like to select the specifc apps that are locked to the dock, not just add everything I install.

[https://bugs.launchpad.net/unity/+bug/761851](https://bugs.launchpad.net/unity/+bug/761851)

---


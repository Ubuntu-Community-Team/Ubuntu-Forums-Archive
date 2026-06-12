---
title: "&quot;Add a New Printer&quot;  greyed out"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by thekat on 2012-04-19
I have been running 12.04 Beta 2 since it's release, both at home and at work.
Both use Gnome-panel (not unity although it is installed)

 /etc/group on both are the same...
and both my locallly attached and network printer both work without
incident...

I have removed the cups printing package and reinstalled it..
still no joy...

anyone else run into this..?

tk

---

### Post by thekat on 2012-04-19
I logged back in via Unity (2D) and could configure my printers, so I must be missing a 'Gnome specific' app for printer configuration...

I will keep searching..

tk

---

### Post by jbicha on 2012-04-19
You need to install cups-pk-helper.

I just uploaded a 0ubuntu8 version of gnome-session-fallback that will recommend that. I hadn't seen this bug before because I always get GNOME Classic for free by installing GNOME Shell which did recommend cups-pk-helper.

---


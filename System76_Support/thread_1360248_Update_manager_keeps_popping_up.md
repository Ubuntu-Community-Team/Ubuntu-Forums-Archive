---
title: "Update manager keeps popping up"
date: 2009-12-20
forum: System76 Support
---

### Post by porlaizquierda on 2009-12-20
update manager keeps popping up. when i click the check icon it says it's downloading repositories and then i get a pop up that says:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and inside that box it says:

Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.



what's going on? would appreciate knowing what's up and how to fix that. thanks.

---

### Post by Wobblybob on 2009-12-20
sounds like you still have the install from CDROM ticked in [System], [Admin...],  [Software Sources], [Ubuntu software] tab and untick the option in the installable from CD-Rom/DVD box.

---

### Post by lrcaballero on 2009-12-20
Try this:

System/Administrator/Synaptic package manager

On the left hand side window you will see:

All
Broken

Select broken and see if there is anything that needs to be fix and just follow-through do install and/or fix (sorry can;t remember)

this helped me fix an issue i had with something I was downloading and got interrupted.

Good Luck

Luis

---


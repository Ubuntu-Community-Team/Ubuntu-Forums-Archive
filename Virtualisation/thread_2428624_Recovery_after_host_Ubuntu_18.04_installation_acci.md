---
title: "Recovery after host Ubuntu 18.04 installation accidentally booted as guest VM"
date: 2019-10-07
forum: Virtualisation
---

### Post by buppaclaus on 2019-10-07
I'm running Ubuntu 18.04/Win10 dual boot on a Dell Precision 5520, and recently installed and configured VMBox for Win10 raw physical drive access. This allows me to boot to windows when the full power of the hardware is required, or more easily/usually run the same Windows installation as a less powerful virtual machine from Ubuntu the rest of the time.

Unfortunately I got caught by a windows automatic update/restart that rebooted the virtual machine guest into the grub default ubuntu installation ie. The host OS was running itself as the guest OS as well.

This 'recursive' boot caused an unknown amount of corruption, and I can no longer boot into Ubuntu (windows is fine). I've tried:


[LIST]
[*]fsck'ing all drives.
[*]boot-repair from a live cd [http://paste.ubuntu.com/p/zyWrSg2YGm/](http://paste.ubuntu.com/p/zyWrSg2YGm/)
[*]Advanced boot/recovery options from the grub menu - journalctl log attached in case it helps.
[/LIST]

I've duplicated the single internal 2Tb SSD so that potentially destructive repair attempts can be tried - at this point I'm stumped and happy to try just about anything...

Do I need to reinstall Ubuntu? Any other ideas?

Any help would be very appreciated :)

---

### Post by wildmanne39 on 2019-10-07
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by buppaclaus on 2019-10-07
Sorry, failed to attach journalctl file in original post

---


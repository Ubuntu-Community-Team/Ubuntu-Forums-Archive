---
title: "Selectively blocking automount"
date: 2011-05-18
forum: Security
---

### Post by ThuisLinux on 2011-05-18
Is it (still) correct that automount is launched directly from UDEV as I understand from this [announcement ]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2005-December/000028.html")made in 2005?

If so, could anybody help me identifying the rules that are involved in automounting?

I should test again, but was under the impression that automount still worked with the udev daemon (and udisk daemon) stopped.



More in detail, we are trying to build a few live cd's, a part of them should not automount USB flash drives at all, some others should only accept specific USB drives. XFCE is used on the live cd's.

What looked as a simple problem turns out to be quite complex. Maybe I am missing something obvious. The users on the live CD have no root access. Changing the settings in Thunar volman and changing the access rights on the files in the user profile resulted in the file being replaced if the user changed the settings. Maybe it is possible with the Mandatory setting of gconf, but I don't see a volman schema for Gconf.

It is not that complex to match a specific  USB drive with a udev rule and give it a name, but the /dev/sd? name will still be generated for all drives, probably created by the kernel and adapted by other rules in UDEV. And automount is launched, I suppose by a message coming from UDEV or the kernel to the user's file manager.  Is that correct?


It would be great if somebody could show us the right track

---


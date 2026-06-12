---
title: "Ubuntu Host WinXP Client CDROM Failure after Gutsy Upgrade"
date: 2008-03-25
forum: Virtualisation
---

### Post by clarkburbidge on 2008-03-25
I just noticed that the CDROM was no longer available in my vmware player WinXP client.

I'm fairly certain that after the upgrade to Gutsy it broke. I'm guessing that there is an new mounting for the CDROM in the fstab in Gutsy?!?! anyone?

In the /etc/fstab the /media/cdrom is set to /dev/scd0, but in the *.vmx file the setting for CDROM is for /dev/hda.

When I changed the hda to scd0 in the *.vmx file all was good!

---


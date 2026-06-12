---
title: "remove mounted links media from desktop?"
date: 2008-02-06
forum: Ubuntu Customization Guide
---

### Post by n-alexander on 2008-02-06
How to remove these mounted disks etc from the desktop? Now I have all my Windows disks there, and DVD/flash when inserted.

I looked in places I could think and searched forums..

Thanks,
Alex

---

### Post by liniaal on 2008-02-07
there are several solutions for this. i also hate these things popping up. to keep the dvd's/flash cards/usb memories on your desktop (which i find a nice feature), you could choose to mount all your partitions elsewhere, default is /mnt.
i for example have
/mnt/data (files)
/mnt/media (audio video etc)
/mnt/tmp (downloads)
and if i still any signs of windows on my pc they probably would hang out at
/mnt/winxp
or something like that.

there is also a possibility to remove these "partition" icons from your desktop altogether (better said, stop them from showing up). fire up your *gconf-editor* (if you are very familiar with windows, this is kind of a registry editor on gnome. i don't use it very much though (i mean not as much as regedit.exe on windows... glad that that time is over :P). well nav to /apps/nautilus/desktop/ and uncheck the box next to "volumes_visible".
log out & back in and voila!
if you want the first behaviour, ask for it and i'll explain it a bit better.

---

### Post by n-alexander on 2008-02-08
> **liniaal said:**
> there are several solutions for this. i also hate these things popping up. to keep the dvd's/flash cards/usb memories on your desktop (which i find a nice feature), you could choose to mount all your partitions elsewhere, default is /mnt.
i for example have
/mnt/data (files)
/mnt/media (audio video etc)
/mnt/tmp (downloads)
and if i still any signs of windows on my pc they probably would hang out at
/mnt/winxp
or something like that.

there is also a possibility to remove these "partition" icons from your desktop altogether (better said, stop them from showing up). fire up your *gconf-editor* (if you are very familiar with windows, this is kind of a registry editor on gnome. i don't use it very much though (i mean not as much as regedit.exe on windows... glad that that time is over :P). well nav to /apps/nautilus/desktop/ and uncheck the box next to "volumes_visible".
log out & back in and voila!
if you want the first behaviour, ask for it and i'll explain it a bit better.

Cool, thanks.

I thought it would watch the mount table and show them anyway. But it is really the second solution that I wanted.

Do you know where gconf-editor keeps the actual config file?

---

### Post by #Reistlehr- on 2008-02-08
For clearity, anything that gets mounted in the /media dir, gets placed on the desktop. For example, USB Drivers, extra partitions.. If you dont want certain ones to show up, change /etc/fstab to mount them to /mnt instead of /media

gconf doesnt keep actual *editable* files. You have to use the gui. It's easy to use though.

---


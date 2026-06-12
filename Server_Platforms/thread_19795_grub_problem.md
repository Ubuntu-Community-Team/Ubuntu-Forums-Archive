---
title: "grub problem"
date: 2005-03-13
forum: Server Platforms
---

### Post by dgo on 2005-03-13
hi there,

i have sucessfully installed ubuntu with grub.
no i want to move the harddisk to a new server. but when i start the new server i get the messages "grub loading 1.5" or something like this and then "grub is loading, please wait..." but then, nothing happens at all. what can i do about this?
there is no second harddisk in the old computer so grub should be fine.

thanks for help

florian

---

### Post by alastair on 2005-03-14
Does the new server have the disk on the same channel and config i.e.

If it was /dev/hda (and root /dev/hda1, say), is it still primary IDE channel and master?

---


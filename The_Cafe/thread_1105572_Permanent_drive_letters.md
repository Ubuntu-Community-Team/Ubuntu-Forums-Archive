---
title: "Permanent drive letters"
date: 2009-03-24
forum: The Cafe
---

### Post by Bungo Pony on 2009-03-24
Is there any way to make a drive's letter permanent? For example, I have a USB stick with data on it. I would like it to ALWAYS be sda6, no matter which port I put it in. That way, I could selectively access the data on that particular drive whenever I need to and always find it, even if I have other USB sticks plugged in.

---

### Post by yabbadabbadont on 2009-03-24
Not easily, if at all.  It would take some fancy udev rules, probably based on the UUID of the filesystem on the stick (which would change if you ever reformat it).  Your best bet is to make sure to assign a unique label to the USB stick(s).  Then it(they) should show up with that label when inserted.

---

### Post by Polygon on 2009-03-25
for me, if you label your usb stick (like actually give it a fat32 volume name), gnome will always mount it under that name (like /media/YOUR_NAME_HERE

otherwise, i think the best bet would to be to access the drive through UUID's, since thats the whole point of them.

---


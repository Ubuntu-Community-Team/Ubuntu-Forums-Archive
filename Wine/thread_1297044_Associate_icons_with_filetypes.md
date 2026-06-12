---
title: "Associate icons with filetypes"
date: 2009-10-21
forum: Wine
---

### Post by nikkkko on 2009-10-21
Hi,

Does anyone know how to associate an icon with a wine app filetype?  I use SketchUp a lot and would like all my .skp and .skb files to have the right icon.  I can change them for each individually, but it would be much nicer if they had the correct icon by default.

Thanks

---

### Post by nikkkko on 2009-10-30
---bump---

---

### Post by alex.rayu on 2009-10-30
The easy way is this: see what icon is currently used and overwrite it with your own in the icons folder.

Or, start gconf-editor, and in the HKEY/LOCAL-MACHINE/CANONICAL/LINUX/... kidding.

---

### Post by nikkkko on 2009-10-30
That's just the point - if I could figure out where it's getting it's icon from I could change it.

---

### Post by alex.rayu on 2009-10-30
Oh it's somewhere in /var/shared/ - I bet you can google for "Ubuntu where icons stored"

---

### Post by nikkkko on 2009-10-30
Somewhere in usr/share I presume, but these are Wine app file types I'm trying to change.  I don't see where they are stored.

Hey ho.

Anyone?

---

### Post by nikkkko on 2009-10-30
Anyway, the SketchUp file icons are stored in 

/home/-username-/.local/share/icons

but the file uses a standard text looking icon.  I can neither find where the standard icon sits nor what tells ubuntu to use that icon instead of the correct one.

---

### Post by alex.rayu on 2009-10-30
Yeah - if you donload icons from internet and place them in /home/user-name/.icons - then you can install them. The other sets of icons that are system icons are stored in... yeah - just search for them.

---


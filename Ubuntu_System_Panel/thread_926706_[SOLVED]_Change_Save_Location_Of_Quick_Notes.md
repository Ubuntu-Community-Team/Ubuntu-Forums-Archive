---
title: "[SOLVED] Change Save Location Of Quick Notes?"
date: 2008-09-22
forum: Ubuntu System Panel
---

### Post by Ms_Angel_D on 2008-09-22
Is it possible to change the default location where files are saved using the quick notes plugin? I would rather they saved to documents as opposed to my desktop.

Thanks,
Angel

---

### Post by Malac on 2008-09-22
Wish they were all that easy, :)
New gconf key /apps/usp/plugins/notes/save_path and option in preferences Notes Tab.

Change committed to SVN Rev #353

---

### Post by Ms_Angel_D on 2008-09-22
WOW SWEET Thanks Very Very MUCH :D :D

---

### Post by Ms_Angel_D on 2008-09-22
hmm it's still saving to the desktop...

I have tried setting the path to both

/home/angel/Documents/TXT/Quick_Notes

and 

/home/angel/Documents/TXT/Quick_Notes/

with no luck :confused:

---

### Post by Ms_Angel_D on 2008-09-22
Nevermind for some reason the first restart of Gnome didn't work but the second time I restarted the panels it took.

---

### Post by Malac on 2008-09-23
> **MetalHellsAngel said:**
> Nevermind for some reason the first restart of Gnome didn't work but the second time I restarted the panels it took.Odd :confused: glad it worked for you finally.

---


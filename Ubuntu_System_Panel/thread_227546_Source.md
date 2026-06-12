---
title: "Source?"
date: 2006-08-01
forum: Ubuntu System Panel
---

### Post by Phrodo_00 on 2006-08-01
Hi, Chanders is doing some pretty nice work over here =D> , however, Chanders, I'm not a ubuntu user right now (migrated to a more do-it-for-yourself distro), and I'd really love to have this working on it (from the screenshots it looks a whole lot better than the sled menu), so could you publish the source someday?. Also, I know you're doing this for Ubuntu and everything, but could you, like in the future or maybe right now, worring about not tide it too tightly to ubuntu, or if you do so (wich would be great for ubuntu too, now that I think about it) still provide a distro-neutral version?...

---

### Post by Note360 on 2006-08-01
Sorry the source is already published it is inside the .deb. Open up the .deb in a archive manager and extract the code. in data.tar.gz is the source.

---

### Post by _profox on 2006-08-01
Our code is already very distro-neutral. We even make use of the icon "distributor-logo" by default, on ubuntu you'll get the ubuntu logo, on suse the suse logo, on fedora the fedora logo, archlinux the archlinux logo, etc. etc.

Our code is also not tied to ubuntu itself. It's tied to GTK/GNOME right now for the most part, but it will work on any GNOME system.

(In the future we might also consider a QT/KDE port)

The code is fully open source and you can edit the main python code directly from here after installation:

/usr/bin/usp

the .glade file is here: /usr/share/usp/usp.glade

Have fun with it ;) and if you do something cool with it, let us know :) thanks

---

### Post by Phrodo_00 on 2006-08-02
wow!, glad to hear that. So I were just talking out of the unkowledge (heck, does that word exist?) after all

---


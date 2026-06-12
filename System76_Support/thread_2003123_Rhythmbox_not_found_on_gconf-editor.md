---
title: "Rhythmbox not found on gconf-editor"
date: 2012-06-13
forum: System76 Support
---

### Post by jcvalverde on 2012-06-13
I want to change the music files directory which appears as "Multiple Locations Set" on my Rhythmbox to a set of directories of my choice. But using the UI it only lets me select one. I read using gconf-editor under /apps/rhythmbox I could achieve this, but there's no rythmbox under my /apps on gconf-editor. Has this changed? If not, how can I get it in there?

Best regards

---

### Post by drs305 on 2012-06-13
If you are familiar with gconf-editor you will somewhat recognize dconf-editor. Install dconf-tools and then open the editor. Unfortunately, I haven't found a way to use a search function, but rhythmbox settings can be made from the command line as well.

The section you are looking for (I think) is org.gnome.rhythmbox.rhythmdb (org > gnome > rhythmbox > rhythmdb > locations). It might also be in the rhythmbox > library > source section.

---


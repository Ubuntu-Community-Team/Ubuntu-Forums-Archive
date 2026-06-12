---
title: "Eog and glib2.0_2.31"
date: 2011-11-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-15
The newest update to eog in Precise does not work with glib2.0 (2.31).
Those using Ricotz Gnome-shell testing PPA have installed the new glib2.0.
That causes eog to crash.

There is a patch for eog in Ricotz PPA (3.2.1-0ubuntu2~12.04~ricotz0), but the Precise version is newer.

---

### Post by Harry33 on 2011-11-15
Regarding Ricotz Gnome-shell Testing PPA this is fixed now with a newer update of
Eog_3.2.1-0ubuntu2+12.04~ricotz0.

The precise version 3.2.1-0ubuntu2 depends on the newre libjpeg8
and the ricotz version depends on the older libjpeg62,
but so does Precise libpoppler13, libqt4-gui, libgegl-0.0-0 and libreoffice-core too..

---

### Post by Harry33 on 2011-11-23
The newest Eog_3.2.2-2ubuntu1 in Gnome-Shell Testing PPA is now built against libjgp8.
This works very well with glib2.0_2.31.3 of the same PPA.

---


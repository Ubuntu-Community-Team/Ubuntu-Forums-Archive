---
title: "gtkpod not working on 12.10 Alpha"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by geordiejohn on 2012-08-02
hello i had gtkpod working on 12.04 but now i have 12.10 and when i try to install gtkpod from the software center i get this msg-

 The following packages have unmet dependencies:

gtkpod: Depends: gtkpod-data (= 2.1.2-1) but 2.1.2-1 is to be installed
        Depends: libatomicparsley0 (= 2.1.2-1) but 2.1.2-1 is to be installed
        Depends: libgtkpod1 (= 2.1.2-1) but 2.1.2-1 is to be installed
        Depends: libanjuta-3-0 (>= 2:3.2.0) but 2:3.5.4-0ubuntu2 is to be installed
        Depends: libc6 (>= 2.7) but 2.15-0ubuntu15 is to be installed
        Depends: libcurl3-gnutls (>= 7.16.2) but 7.26.0-1ubuntu1 is to be installed
        Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1ubuntu1 is to be installed
        Depends: libgdl-3-2 (>= 3.0.0) but 3.4.2-1 is to be installed
        Depends: libglib2.0-0 (>= 2.31.8) but 2.33.6-1 is to be installed
        Depends: libgtk-3-0 (>= 3.0.0) but 3.5.8-0ubuntu2 is to be installed

any ideas on how i can get gtkpod working please?
thank you.

---

### Post by Elfy on 2012-08-02
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by dino99 on 2012-08-02
****
any ideas on how i can get gtkpod working please?
thank you.
    ******

- learn what "bleeding edge" means
- learn what "partial updates" means

12.10 is still in early development, then its also holidays time :P

---

### Post by jfernyhough on 2012-08-02
The version in the repo depends on older GNOME libraries (3.4.2, Quantal has 3.5.4 at the moment). It won't work until it's been rebuilt to use the newer versions.

You could try the latest from their Sourceforge page: [http://sourceforge.net/projects/gtkpod/files/](http://sourceforge.net/projects/gtkpod/files/)

---

### Post by geordiejohn on 2012-08-02
thank you.

---

### Post by jbicha on 2012-08-02
The current version of gtkpod won't compile with the current libraries in Quantal.

---


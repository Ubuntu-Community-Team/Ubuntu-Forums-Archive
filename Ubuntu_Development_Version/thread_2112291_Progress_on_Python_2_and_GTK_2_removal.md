---
title: "Progress on Python 2 and GTK 2 removal"
date: 2013-02-04
forum: Ubuntu Development Version
---

### Post by forcecore on 2013-02-04
How far is 13.04 on removal of GTK2 and Python3 from default release?

---

### Post by jpeddicord on 2013-02-04
> **forcecore said:**
> How far is 13.04 on removal of GTK2 and Python3 from default release?

You mean Python 2.x right? :P

---

### Post by grahammechanical on 2013-02-04
13.04 is not yet finished. Any answer that anyone of us might give would be inaccurate until after release date.

I am using a 13.04 install that started out as a 12.10 install and a search of Synaptic for GTK2 shows

gtk2-engines-pixbuf
overlay-scrollbar-gtk2
python-gtk2
gtk2-engines
libglib-perl
libpangol-perl
rox-filer
libgtk2-perl

I am just a simple community volunteer tester. I cannot say why this stuff is there or if it should be removed. Some of it may have come from my installation of Fvwm-crystal as an alternative desktop. Who knows?

Regards.

---

### Post by forcecore on 2013-02-04
jpeddicord: yup i mean Python 2.x, nothing special but Ubuntu becomes lighter and cleaner in future if exessive stuff is removed.

---

### Post by Harry33 on 2013-02-04
> **forcecore said:**
> How far is 13.04 on removal of GTK2 and Python3 from default release?

GTK2 is not going anywhere, not in the near future.

---

### Post by forcecore on 2013-02-04
> **Harry33 said:**
> GTK2 is not going anywhere, not in the near future.

Yes it may stay on reposirory forever but it should be ejected from default .iso release.

---

### Post by pressureman on 2013-02-04
> **forcecore said:**
> Yes it may stay on reposirory forever but it should be ejected from default .iso release.

That would break Firefox.

[https://bugzilla.mozilla.org/show_bug.cgi?id=627699](https://bugzilla.mozilla.org/show_bug.cgi?id=627699)

---

### Post by Harry33 on 2013-02-05
Also, porting LibreOffice to GTK+3 is not ready yet.
Then of course we have Thunderbird and we have Gimp.

---


---
title: "Korais"
date: 2009-11-11
forum: Ubuntu Christian Edition
---

### Post by jonathonblake on 2009-11-11
All:

Is Korais too specialized/exotic to be included in an Ubuntu Christian Edition repository? [http://korais.sourceforge.net/](http://korais.sourceforge.net/)

This is an editor for writing texts or emails in Aramaic, Ancient Greek (Polytonic) and Modern Greek (Monotonic), Coptic, Cypriot Syllabogram, Etruscan,  Hebrew, Old Persian, Phoenician, Ugaritic, and Linear B.

jonathon

---

### Post by simosx on 2009-11-17
> **jonathonblake said:**
> All:

Is Korais too specialized/exotic to be included in an Ubuntu Christian Edition repository? [http://korais.sourceforge.net/](http://korais.sourceforge.net/)

This is an editor for writing texts or emails in Aramaic, Ancient Greek (Polytonic) and Modern Greek (Monotonic), Coptic, Cypriot Syllabogram, Etruscan,  Hebrew, Old Persian, Phoenician, Ugaritic, and Linear B.

jonathon

Korais requires Java, so you need to make sure there is space for the JRE.
In addition, it appears there have not been active development recently, which would be a negative. Finally, the canonical way of adding support for new scripts is to use the facilities already available in the system.

Ideally, it would be better to 
1. create keyboard layouts for those scripts, such as Aramaic, Coptic, etc.
2. package those fonts that support the scripts

Ubuntu 9.10 and forward support IBus (SCIM successor), so any complex scripts can be supported. Currently, Monotonic and Polytonic (Ancient) Greek are supported in Linux with the basic input methods (does not even require IBus). 
You will probably be in a position to find existing SCIM/IBus keyboard layouts for those scripts you mention above.

Doing it the proper way, you will be able to write those scripts in any editor area, including Firefox, OpenOffice, and what not.

---


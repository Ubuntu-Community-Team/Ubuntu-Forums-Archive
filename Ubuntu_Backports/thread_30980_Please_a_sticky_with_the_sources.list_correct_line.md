---
title: "Please a sticky with the sources.list correct lines"
date: 2005-05-01
forum: Ubuntu Backports
---

### Post by fabiang on 2005-05-01
Hi,

From some weeks ago the backports repository say's me: Internel Server Error, whell, today i came back and i see "file not found" ¿the path of repository backports was changed?

I have the nexts line in mi sources.list
> 
#proyecto backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
 
and i see a file not found error:

> ...
W: No se puede leer la lista de paquetes fuente [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No existe el fichero o el directorio)
...


Can you put a sticky whith the correct path,when the patch changes the sticky was be upgraded...

---

### Post by jdong on 2005-05-01
Strange... Those are the correct addresses.

---


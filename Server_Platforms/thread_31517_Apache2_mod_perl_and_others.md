---
title: "Apache2 mod_perl and others"
date: 2005-05-03
forum: Server Platforms
---

### Post by blueshome on 2005-05-03
I've reinstalled apache2
after
perl python and php modules don't works.
in the directory mods-available
no mention abouts this modules
and the same in mods-enabled

Can someone help me to find a solution

Thanks everybody

---

### Post by defkewl on 2005-05-04
[QUOTE=blueshome]I've reinstalled apache2
after
perl python and php modules don't works.
in the directory mods-available
no mention abouts this modules
and the same in mods-enabled

Can someone help me to find a solution

Thanks everybody[/QUOTE]
 How did you reinstall it? Did you use apt-get upgrade?

---

### Post by blueshome on 2005-05-04
no
before:
apt-get --purge remove apache2
(and other related package)
after
apt-get install apache2

It' seems tha after a reinstallation
the modules for perl, python and php are lost....

---

### Post by alastair on 2005-05-04
libapache2-mod-perl2

is probably needed - as well, or instead of. Perhaps the same for PHP (which I don't use).

I checked via :

apt-cache search apache2 | grep perl

---


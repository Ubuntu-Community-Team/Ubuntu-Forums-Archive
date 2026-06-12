---
title: "instalación de kooka"
date: 2009-07-29
forum: Software
---

### Post by mafabuda on 2009-07-29
INstale hace unos dias ubuntu 9.04, no tuve ningun problema hastq que quise instalar kooka, los paquetes comienzan a bajar, pero luego me dice que no encuentra ningun paquete con el nombre kooka. Intente la instalación de dos maneras dieferentes y paso lo mismo.
Con sudo apt-get install y con sudo aptitude install. que puedo hacer?

---

### Post by guillermolisi on 2009-07-29
Revise en mi 9.04 KDE 4.3RC3 y en los repos no figura el paquete Kooka.

---

### Post by Fak89 on 2009-07-29
Yo me fije en Synaptic y tampoco encontre el paquete, pero aca tenes la descarga..

[ftp://ftp.suse.com/pub/people/freitag/kooka/kooka-0.44.tar.bz2](ftp://ftp.suse.com/pub/people/freitag/kooka/kooka-0.44.tar.bz2)
```
$tar -xjvf kooka-0.44.tar.bz2

$cd kooka-0.44

$./configure

$make

$make install
```

---


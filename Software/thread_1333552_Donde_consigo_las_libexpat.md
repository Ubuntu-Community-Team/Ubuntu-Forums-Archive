---
title: "Donde consigo las libexpat?"
date: 2009-11-21
forum: Software
---

### Post by alehawk on 2009-11-21
Hola, estoy tratando de usar el dbdesigner (copia dl modelright en windows) y no puedo hacerlo correr de ninguna forma, pide librerias por todos lados, algunas las consegui de otras distribuciones de linux como gentoo pero hay otras que no pued conseguirlas por ninguna lado...[FONT=monospace]

libexpat.so.0: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio

es el error que tira ahora, lei que hay que linkear otra libreria a esta pero la realidad es que hago un find de libexpat* y no tengo absolutamente ninguna libreria que contenga libexpat en el nombre.
Alguien sabe como solucionar esto? alguien tiene esta slibrerias como para pasarmelas?
Gracias!
[/FONT]

---

### Post by guillermolisi on 2009-11-23
Desde donde bajaste el programa ?

---

### Post by alehawk on 2009-11-23
De aca [http://fabforce.net/dbdesigner4/](http://fabforce.net/dbdesigner4/)

---

### Post by guillermolisi on 2009-11-23
Baje el tarball y vi que esta probado en SUSE y RedHat, por eso hay un RPM ademas del tarball.

Mirando la documentacion incluida en el tarball, el documento DBDesigner4.spec, menciona componentes de KDE3 (/opt/kde3/share/applnk/Programming) o, al menos, asume que se esta usando esta version de KDE.

En los repositorios de Ubuntu esta el paquete libexpat1, en el main repository (por lo menos de Karmic)
Ese paquete contiene
> XML parsing C library - runtime library

This package contains the runtime, shared library of expat, the C
library for parsing XML.y en Karmic se instala como
> /lib/libexpat.so.1.5.2
/lib/libexpatw.so.1.5.2Busca con Synaptic Package Manager por libexpat y deberias ver lo mismo que mencione (a menos que estes utilizando otra version de Ubuntu que no incluya este paquete)

---

### Post by alehawk on 2009-11-24
Gracias guillermo por tu respuesta, efectivamente tengo instalado el paquete libexpat1 pero voy a /usr/lib y no tengo esas librerias... en que ruta las tenes vos? Yuna ultima consulta, asumiendo que las consiguiera, las renombro para que las tome?
Saludos y gracias.

---

### Post by guillermolisi on 2009-11-24
> **alehawk said:**
> Gracias guillermo por tu respuesta, efectivamente tengo instalado el paquete libexpat1 pero voy a /usr/lib y no tengo esas librerias... en que ruta las tenes vos? Yuna ultima consulta, asumiendo que las consiguiera, las renombro para que las tome?
Saludos y gracias.
No se renombra, se linkea con "ln" asi tenes una sola instancia que se actualiza cada vez que cambia la version/sub version.
Si el programa necesita "ver" las librerias en determinado path, hace el link ahi y proba.

En Ubuntu se instala en
```
/.
/lib
[B]/lib/libexpat.so.1.5.2
/lib/libexpatw.so.1.5.2[/B]
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libexpat1
/usr/share/doc/libexpat1/copyright
/usr/share/doc/libexpat1/changelog.gz
/usr/share/doc/libexpat1/changelog.Debian.gz
[B]/lib/libexpat.so.1
/lib/libexpatw.so.1[/B]
```
Esta informacion te la brinda Synaptic (Installed Files)

---

### Post by alehawk on 2009-11-25
Ahi lo hice funcionar... gracias por tu ayuda, sin ella hubiera sido imposible! :)

---


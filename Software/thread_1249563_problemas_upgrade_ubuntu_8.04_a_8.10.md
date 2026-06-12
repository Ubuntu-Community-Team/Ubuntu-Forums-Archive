---
title: "problemas upgrade ubuntu 8.04 a 8.10"
date: 2009-08-25
forum: Software
---

### Post by zionwing on 2009-08-25
buenas, necesito ayuda porque he estado tranado de dar upgrde a mi distro de ubuntu pero me tira errores.
llevo poco tiempo con linux, quiero pasar de win a linux y he estado como un mes solo utilizando ubuntu para acostumbrarme y todo eso.

el asunto es que tengo instalada la version 8.04 y trate de hacer el upgrade como dice la pagina oficial de ubuntu por internet.
pero no me sale la opcion de dar upgrade
ademas me tira los siguientes errores cuando aprieto comprobar en el gestor de actualizaciones.

________________
W: Imposible obtener [http://ubuntu.org.ua/getdeb/Release.gpg](http://ubuntu.org.ua/getdeb/Release.gpg)  No pude resolver 'ubuntu.org.ua'

W: Imposible obtener [http://ubuntu.org.ua/getdeb/es.bz2](http://ubuntu.org.ua/getdeb/es.bz2)  No pude resolver 'ubuntu.org.ua'

W: Imposible obtener cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Imposible obtener cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
________

espero me puedan ayudar, estaba pensando en bajar el disco de la version 9.04 y reinstalar todo pero no quiero perder los programas ya instalados ni tener que darme la lata de volver a bajarlos para instalarlos, ademas de que los he configurado y personalizado y no quiero perder todo eso.
busqué algunas erramientas para dar backup pero lo que encontre no es lo que buscaba.

porfis podrian ayudarme?? a reparar el error o como dar backup a mis programas y todo eso???

---

### Post by Mister X on 2009-08-25
Andá a sistema -> herramientas -> origenes del software

En la primer solapa seleccioná otro servidor Ej: servidor para argentina (eso deberia solucionar el problema de la coneccion)
y en la solapa actualizaciones, en actualizacion de la distribucion, elejí: ediciones normales (eso te habilita a actualizar a una version que no sea LTS, como la 8.10)

despues abri el gestor de actualizaciones, ahi ya te deberia habilitar para hacer la actualizacion de version.

---


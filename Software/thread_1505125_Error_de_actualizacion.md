---
title: "Error de actualizacion"
date: 2010-06-08
forum: Software
---

### Post by walmunga on 2010-06-08
estaba todo bien disfrutaba de mi linda computadora con ubuntu 10.04 hasta que me salio un tremendo cartelito en el panel de arriba de color rojo con un signo de exclamacion, ahora, toque y se abrio el gestor de actualizaciones y me salta un cartel que dice lo siguiente cuando le doy a actualizar

[B]Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  No pude conectarme a archive.getdeb.net:80 (81.92.203.249). - connect (110: Expiró el tiempo de conexión)
Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-es.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-es.bz2)  Imposible conectar a archive.getdeb.net:http:
Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Imposible conectar a archive.getdeb.net:http:
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/B]

ante la situacion de que no entiendo un pomo de lo que dice tuve q recurrir al foro a ver si alguien tiene idea de que cuernos significa este cartelito desde ya muchas gracias

---

### Post by el_eternauta on 2010-06-09
> **walmunga said:**
> estaba todo bien disfrutaba de mi linda computadora con ubuntu 10.04 hasta que me salio un tremendo cartelito en el panel de arriba de color rojo con un signo de exclamacion, ahora, toque y se abrio el gestor de actualizaciones y me salta un cartel que dice lo siguiente cuando le doy a actualizar

[B]Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  No pude conectarme a archive.getdeb.net:80 (81.92.203.249). - connect (110: Expiró el tiempo de conexión)
Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-es.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-es.bz2)  Imposible conectar a archive.getdeb.net:http:
Imposible obtener [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Imposible conectar a archive.getdeb.net:http:
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/B]

ante la situacion de que no entiendo un pomo de lo que dice tuve q recurrir al foro a ver si alguien tiene idea de que cuernos significa este cartelito desde ya muchas gracias

Existe un problema temporal con los repositorios principales de GetDeb, por eso te sale ese error. No es tu máquina. Podrías solucionarlo agregando las direcciones de los mirrors a tu sources.list!

Acá te dejo algo como para que empieces: 

[http://www.taringa.net/posts/linux/5717976/Arreglar-repositorios-de-Getdeb.html]("http://www.taringa.net/posts/linux/5717976/Arreglar-repositorios-de-Getdeb.html")

Saludos.

---


---
title: "Como comparto carpeta con Samba???"
date: 2009-09-22
forum: Software
---

### Post by matias_tati on 2009-09-22
Hola la cosa es asi tengo una particion NTFS y quiero compartir una carpeta en ella con otra pc que tiene windows en mi red hogareña que debo hacer???
Gracias!!!

---

### Post by GGsalas on 2009-09-22
> **matias_tati said:**
> Hola la cosa es asi tengo una particion NTFS y quiero compartir una carpeta en ella con otra pc que tiene windows en mi red hogareña que debo hacer???
Gracias!!!

Yo he accedido a carpetas de otras computadoras (Windows) llendo a "Lugares > Red" y ya está. Si queres compartir vos, pones botón derecho sobre la carpeta y "compartir"

Lo que no se es si hay alguna manera más adecuada entre 2 computadoras con Ubuntu (es mi caso), pero ya es otro tema

---

### Post by guillermolisi on 2009-09-23
> **GGsalas said:**
> Yo he accedido a carpetas de otras computadoras (Windows) llendo a "Lugares > Red" y ya está. Si queres compartir vos, pones botón derecho sobre la carpeta y "compartir"

Lo que no se es si hay alguna manera más adecuada entre 2 computadoras con Ubuntu (es mi caso), pero ya es otro tema
[otro_tema]
Podes usar NFS
[/otro_tema]

---

### Post by matias_tati on 2009-09-23
Si eso lo hago hace tiempo pero no es que quiero pasar un archivo sino compartir especificamente una carpeta en mi particion NTFS donde guardo mi musica y donde dicha particion es de datos. Si la quisiera mover a la particion de ubuntu no me alcanzaria el espacio.
Gracias...

---

### Post by guillermolisi on 2009-09-23
> **matias_tati said:**
> Si eso lo hago hace tiempo pero no es que quiero pasar un archivo sino compartir especificamente una carpeta en mi particion NTFS donde guardo mi musica y donde dicha particion es de datos. Si la quisiera mover a la particion de ubuntu no me alcanzaria el espacio.
Gracias...
Lo del NFS era para GSalas, con los tags del caso ya que ciertamente no es tema de este thread.

---

### Post by juancarlospaco on 2009-09-23
**Lugares--->Conectar con el Servidor...**
[IMG]http://img97.imageshack.us/img97/6143/tempq.jpg[/IMG]

*Podes usar SSH tambien*
:)

---

### Post by GGsalas on 2009-09-23
> **matias_tati said:**
> Si eso lo hago hace tiempo pero no es que quiero pasar un archivo sino compartir especificamente una carpeta en mi particion NTFS donde guardo mi musica y donde dicha particion es de datos.

No logro comprender lo que decis, yo de esta manera edito y abro archivos de otra compu y todavía me queda una particion (que no recuerdo si es FAT32 o NTFS de la época en la que usaba W$)

Lo que no he podido hacer es configurar un programa de backup para que use una carpeta de la otra máquina, tal vez tu consulta es por el mismo problema, aunque a mi me da lo mismo hacerlo en EXT4 o en NTFS. Estuve [buscando sobre NFS]("http://linuteca.com/comparte-archivos-con-nfs-en-ubuntu/") y parece algo complejo :P ¿Hay algún tutorial y/o manual sobre SSH, NFS y demás maneras de compartir archivos y carpetas? Gracias :D

---

### Post by matias_tati on 2009-09-23
> **GGsalas said:**
> No logro comprender lo que decis, yo de esta manera edito y abro archivos de otra compu y todavía me queda una particion (que no recuerdo si es FAT32 o NTFS de la época en la que usaba W$)

Lo que no he podido hacer es configurar un programa de backup para que use una carpeta de la otra máquina, tal vez tu consulta es por el mismo problema, aunque a mi me da lo mismo hacerlo en EXT4 o en NTFS. Estuve [buscando sobre NFS]("http://linuteca.com/comparte-archivos-con-nfs-en-ubuntu/") y parece algo complejo :P ¿Hay algún tutorial y/o manual sobre SSH, NFS y demás maneras de compartir archivos y carpetas? Gracias :D

Disculpa no habia entendido del todo...

Cuando le doy click derecho opciones de comparticion/ compartir me sale esto

[[img]http://h.imagehost.org/t/0920/Pantallazo-File_Manager.jpg[/img]](http://h.imagehost.org/view/0920/Pantallazo-File_Manager)

---

### Post by guillermolisi on 2009-09-23
> **GGsalas said:**
> No logro comprender lo que decis, yo de esta manera edito y abro archivos de otra compu y todavía me queda una particion (que no recuerdo si es FAT32 o NTFS de la época en la que usaba W$)

Lo que no he podido hacer es configurar un programa de backup para que use una carpeta de la otra máquina, tal vez tu consulta es por el mismo problema, aunque a mi me da lo mismo hacerlo en EXT4 o en NTFS. Estuve [buscando sobre NFS]("http://linuteca.com/comparte-archivos-con-nfs-en-ubuntu/") y parece algo complejo :P ¿Hay algún tutorial y/o manual sobre SSH, NFS y demás maneras de compartir archivos y carpetas? Gracias :D
Fijate en [http://ubuntu-ar.org/node/219](http://ubuntu-ar.org/node/219) que tenes un indice de tutoriales.

---

### Post by matias_tati on 2009-09-23
Estuve googleando pero da la casualidad que l mismo error los tuvieron en dos post de Ubuntu-Es y esta saturada la page.....

---

### Post by josecuervo86 on 2009-09-23
Usa el cache de Google, abajo del Enlace principal dice Cache, medio tenue, apreta ahí, y si tarda mucho, apreta donde dice "versión solo texto"

---

### Post by matias_tati on 2009-09-23
Buenisimo lo solucione aca esta la solucion [http://74.125.47.132/search?q=cache:HTT0ZHe8VTIJ:www.ubuntu-es.org/%3Fq%3Dnode/114406+a+%C2%ABred+compartida%C2%BB+devolvi%C3%B3+el+error+255:+net+usershare+add:+cannot+share+path&cd=2&hl=es&ct=clnk&gl=ar](http://74.125.47.132/search?q=cache:HTT0ZHe8VTIJ:www.ubuntu-es.org/%3Fq%3Dnode/114406+a+%C2%ABred+compartida%C2%BB+devolvi%C3%B3+el+error+255:+net+usershare+add:+cannot+share+path&cd=2&hl=es&ct=clnk&gl=ar) por si a alguien mas le pasa gracias Josecuervo no sabia eso ya habia renegado un millon de veces cone este tema

---

### Post by josecuervo86 on 2009-09-23
> **matias_tati said:**
> Buenisimo lo solucione aca esta la solucion [http://74.125.47.132/search?q=cache:HTT0ZHe8VTIJ:www.ubuntu-es.org/%3Fq%3Dnode/114406+a+%C2%ABred+compartida%C2%BB+devolvi%C3%B3+el+error+255:+net+usershare+add:+cannot+share+path&cd=2&hl=es&ct=clnk&gl=ar](http://74.125.47.132/search?q=cache:HTT0ZHe8VTIJ:www.ubuntu-es.org/%3Fq%3Dnode/114406+a+%C2%ABred+compartida%C2%BB+devolvi%C3%B3+el+error+255:+net+usershare+add:+cannot+share+path&cd=2&hl=es&ct=clnk&gl=ar) por si a alguien mas le pasa gracias Josecuervo no sabia eso ya habia renegado un millon de veces cone este tema

Hace bastante tiempo que la gente de ubuntu-es anda teniendo problemas con la pagina. Ojalá se solucione rapido, hay mucha info interesante ahí.

---


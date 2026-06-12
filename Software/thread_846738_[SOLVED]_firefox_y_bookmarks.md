---
title: "[SOLVED] firefox y bookmarks"
date: 2008-07-01
forum: Software
---

### Post by ramiro_md on 2008-07-01
Ubunteros, resulta que cambie mi version de ubuntu (de hh a gusty). La cuestion que guarde la carpeta del home .mozilla xq ahi es donde estan los bookmarks (segun tengo entendido). Cuando instale gusty pege la carpeta .mozilla al nuevo home de gusty, pero al abrir firefox no aparecieron mis bookmarks :confused: no se si me podrian dar una mano con esto =)

---

### Post by Hei Ku on 2008-07-01
Al iniciar el firefox te crea un perfil dentro de .mozilla/firefox
Fijate que debes tener dos carpetas de perfiles, la nueva y la vieja. Copia la vieja a la nueva y ya esta.

---

### Post by EnriqueK on 2008-07-02
No lo veo tan simple, resulta que HH trae por defecto firefox3 , allí los marcadores no se almacenan en el tradicional bookmarks.html sino que lo hacen en un nuevo archivo denominado places.sqlite , la posibilidad que veo que tenés es correr el Live CD de Hardy , poner .mozila en la carpeta de usuario y arranca firefox3 , luego entras a editar marcadores  y luego lo exportas a archivo HTML y allí si te va a generar un archivo bookmarks.html que podrás poner en Gutsy que usa firefox2.

---

### Post by ramiro_md on 2008-07-02
La solucion de hei ku no va =S...cuando queria iniciar firefox me decia q ya estaba en uso y no se q cosa.....acto seguido klo desinstale y estoy buscando la version 3 para gutsy...espero encontrarla xD.ALguien sabe donde conseguirla ¿¿
Sino, voy a hacer lo q enrique dce..Un saldo

---

### Post by Hei Ku on 2008-07-02
te fijaste que al copiarlo quedara con permisos de lectura y escritura? Porque si lo moviste pueden haber quedado mal los permisos. Y fijate en en mozilla.org que estaba el binario para instalar el Firefox 3

---

### Post by EnriqueK on 2008-07-02
El Firefox3 nunca va a estar en los repositorios de Gutsy, por lo que la forma de tenerlo es bajandolo directamente de Mozilla , descomprime el siguiente archivo, lo colocas por ejemplo en /opt y creas un enlace al escritorio del ejecutable (no hay nada que compilar), recomiendo que desinstales el firefox2 que viene con Gutsy , salvo que quieras complicarte un poco y crear un nuevo profile para el firefox3 y así poder usar cualquiera de los dos (no al mismo tiempo).
[http://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/es-ES/firefox-3.0.tar.bz2](http://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.0/linux-i686/es-ES/firefox-3.0.tar.bz2)

---

### Post by ramiro_md on 2008-07-02
SOlucionadisimo !...miren este link: [http://comulinux.blogspot.com/2007/12/firefox-3-en-ubuntu-710.html](http://comulinux.blogspot.com/2007/12/firefox-3-en-ubuntu-710.html) a mi me sirvio.=)

---


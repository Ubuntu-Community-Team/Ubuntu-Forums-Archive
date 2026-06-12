---
title: "Problema al actualizar VLC!"
date: 2009-08-30
forum: Software
---

### Post by el_eternauta on 2009-08-30
[I][B]No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  mozilla-plugin-vlc: Depende: vlc-nox (= 1.0.1-1~ppa4) pero 0.9.9a-2ubuntu1 va a ser instalado
                      Depende: libvlc2 (>= 1.0.0~rc1) pero 0.9.9a-2ubuntu1 va a ser instalado
  vlc: Depende: vlc-nox (= 1.0.1-1~ppa4) pero 0.9.9a-2ubuntu1 va a ser instalado
       Depende: libvlccore2 (>= 1.0.0~rc1) pero no va a instalarse
E: Paquetes rotos[/B][/I]

La hago corta: tengo la versión 0.9.9 de VLC y al querer actualizar siguiendo esta guía: [http://chuyuseche.wordpress.com/2009/08/03/reproductor-vlc-1-0-1-para-ubuntu-9-04-jaunty/]("http://chuyuseche.wordpress.com/2009/08/03/reproductor-vlc-1-0-1-para-ubuntu-9-04-jaunty/") me sale eso en consola! ¿Qué estoy haciendo mal?

---

### Post by Hei Ku on 2009-08-30
Proba haciendo un sudo apt-get dist-upgrade

El tema es que me parece que no desinstalaste el vlc antes de probar instalar desde este ppa, asi que tenes un lio de dependencias interesante.

---

### Post by el_eternauta on 2009-08-30
Probé haciendo sudo apt-get dist-upgrade siguiendo esta guía: [http://catrip.wordpress.com/2009/07/07/trucosolucion-instala-vlc-1-0-0-en-ubuntu-jaunty/]("http://catrip.wordpress.com/2009/07/07/trucosolucion-instala-vlc-1-0-0-en-ubuntu-jaunty/")y al parecer todo iba bien pero al abrir VLC sigo con la misma versión 0.9.9.- No entiendo!

---

### Post by Hei Ku on 2009-08-30
Verifica que el vlc en ese repositorio no tenga un nombre ligeramente diferente. Por lo que vi, tiene varias versiones de vlc, asi que probablemente tenga un nombre como vlc-1.0.1 o algo asi.

---

### Post by el_eternauta on 2009-08-30
Y cómo hago para borrar todo rastro de VLC y poder instalar desde cero la nueva versión? No quisiera quedarme sin usarlo porque es el que más me gusta. Tampoco he logrado ponerlo en una ventana, así en ventanas separadas como está esta versión no me gusta. He seguido guías donde te dicen como hacerlo pero nada, sigue igual.

---

### Post by Hei Ku on 2009-08-30
desde Synaptic lo podes instalar y desinstalar.

---


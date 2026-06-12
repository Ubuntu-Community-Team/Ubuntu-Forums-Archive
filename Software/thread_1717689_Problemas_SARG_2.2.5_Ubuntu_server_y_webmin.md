---
title: "Problemas SARG 2.2.5 Ubuntu server y webmin"
date: 2011-03-30
forum: Software
---

### Post by quedefantasma on 2011-03-30
Por error borre el archivo sarg.conf... Desinstale y reinstale el sistema varias veces (y con diferentes metodos) pero el sarg.conf no se regenera en el sistema... Estoy perdido.

Alguien que pueda orientarme? Desde ya...muchas Gracias.

Slds.

---

### Post by guillermolisi on 2011-03-30
Que instalaste y desinstalaste, Sarg ? Webmin ? Ambos ?
Como hiciste la desinstalacion ?

---

### Post by quedefantasma on 2011-03-30
Solo SARG (y alguna dependencia) Lo hice desde el modulo de WEBMIN y desde Linea de comandos... Tambien ejecute autoremove y cleanup...para ver si solucionaban algo.

SARG en un principio creo los archivos SARG.CONF y Las carpetas IMAGES, FONTS, y LENGUAGES bajo el directorio /etc/squid...

Cuando desinstale, borre esas carpetas también...al reinstalar, se crean las carpetas...pero no el contenido de las mismas ni el archivo sarg.conf

---

### Post by guillermolisi on 2011-03-30
Si desinstalaste purgando el paquete Sarg, con lo cual borra tambien todo archivo de configuracion, y volviste a instalarlo deberia crearte el juego de archivos y directorios tal como lo hizo la primera vez, /etc/sarg/sarg.conf incluido.

Webmin me parece una muy buena herramienta pero el unico user que no me genera desconfianza al momento de usar ciertas funciones basicas es root y en general este usuario esta deshabilitado en Ubuntu, por lo cual recurro a Synaptic, Aptitude o apt-get para trabajar desinstalaciones con remocion completa (purge) del paquete y su reinstalacion (como si fuera la primera vez).

Es decir, saquemos de juego como esta configurado Webmin usando herramientas mas directas y veamos que sucede.

---

### Post by quedefantasma on 2011-04-01
> **guillermolisi said:**
> Si desinstalaste purgando el paquete Sarg, con lo cual borra tambien todo archivo de configuracion, y volviste a instalarlo deberia crearte el juego de archivos y directorios tal como lo hizo la primera vez, /etc/sarg/sarg.conf incluido.

Webmin me parece una muy buena herramienta pero el unico user que no me genera desconfianza al momento de usar ciertas funciones basicas es root y en general este usuario esta deshabilitado en Ubuntu, por lo cual recurro a Synaptic, Aptitude o apt-get para trabajar desinstalaciones con remocion completa (purge) del paquete y su reinstalacion (como si fuera la primera vez).

Es decir, saquemos de juego como esta configurado Webmin usando herramientas mas directas y veamos que sucede.

Mi comprender... pruebo y comento. Slds.

---


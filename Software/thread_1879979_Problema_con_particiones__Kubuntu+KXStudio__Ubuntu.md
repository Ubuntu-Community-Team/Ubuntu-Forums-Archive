---
title: "Problema con particiones  Kubuntu+KXStudio / Ubuntu"
date: 2011-11-12
forum: Software
---

### Post by daggaz on 2011-11-12
Hola,
Tengo dos particiones; una con KXStudio sobre Kubuntu y otra con Ubuntu normal; ambos comparten mi carpeta /home. Hice esto por que es un lío hacer cosas sencillas como ver una película o poner música en KXstudio, ya que Pulse-audio toma el control del audio y no hay, por ejemplo, control de volumen máster (el icono de la bocina de la barra superior ya no sirve para nada) o conexión automática a los audífonos al conectarlos a la salida, todo debe hacerse mediante Jack; y esto va muy bien cuando quiero hacer música, pero cuando no, es un problema; por eso preferí hacer dos particiones, una para trabajar con audio y otra para trabajar con todo lo demás.
El problema vino cuando al instalar KXStudio en mi partición con Kubuntu, alteró también de alguna manera la partición de Ubuntu... No puedo configurar nada del audio ahora (se deshabilitó el icono de la barra)  y la apariencia cambió de forma extraña... Ahora las ventanas tienen una fea decoración color naranja chillón y los botones están del lado derecho de la ventana... Ya probé cambiar el tema y no funcionó.

¿Qué puedo hacer para dejar mi Ubuntu natural de nuevo (con ALSA y su tema Ambience)? ¿Debo re-instalarlo? ¿Por que KXStudio modificó mi Ubuntu si este se encontraba en otra partición diferente? ¿Fue por compartir /home?
: /
Espero me puedan ayudar; de antemano gracias.

---

### Post by daggaz on 2011-11-13
Bueno, encontré la respuesta en Hispasonic; resulta que KXStudio realiza  los cambios en la configuración de Audio directamente en la carpeta del  usuario; no en la del sistema; por lo que al compartir directorio /home  con el mismo usuario las configuraciones en ambas particiones se verán  afectadas (y más tratándose de la misma distro).
Una solución simple sería crear un nuevo usuario en Ubuntu y punto; pero  dado que entonces no tendría caso tener las particiones para Kubuntu,  lo que haré será instalar de nuevo Ubuntu desde 0 y crear dos usuarios,  uno para Audio y otro para todo lo demás; crear una carpeta compartida y  en el usuario de audio instalaré KXStudio y algún entorno gráfico como  LXDE o Lightbox (o hasta KDE, que es el nativo de KXStudio).

---


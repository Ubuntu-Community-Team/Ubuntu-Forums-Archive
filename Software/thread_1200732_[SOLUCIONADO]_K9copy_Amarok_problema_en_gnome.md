---
title: "[SOLUCIONADO] K9copy Amarok problema en gnome"
date: 2009-06-30
forum: Software
---

### Post by aledruetta on 2009-06-30
Hola Comunidad!

Estoy con un problema en dos aplicaciones "K": Amarok y K9copy. No tengo certeza de que el problema sea común a las dos, pero los problemas comenzaron al mismo tiempo, entonces, quizá estén relacionados.

Ubuntu Jaunty Jackalope. Gnome. Acer Aspire 4310.

Amarok: no reproduce los audios de la biblioteca. Esos audios están en un disco USB externo. Amarok los carga, organiza la biblioteca, pero no los reproduce (que sería lo más interesante en este caso ¿no?)

K9copy: cuando intento ingresar a la aplicación aparece un mensaje de error:
[html]Ha ocurrido un error fatal
 The application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at http://bugs.kde.org. Useful details include how to reproduce the error, documents that were loaded, etc.
[/html]Esto comenzó a suceder (k9copy) mientras estaba intentando configurar la aplicación. Añadí el dispositivo cdrom0 y cuando di "aceptar" saltó la ventanita.

¿Alguna recomendación?
¿Cómo puedo brindar más información útil?

Saludos y muchas gracias,
Alejandro.

El mismo post en Argentina Loco Team:
[http://ubuntuforums.org/showthread.php?t=1200727](http://ubuntuforums.org/showthread.php?t=1200727)

---

### Post by kamus on 2009-06-30
Quizas se trata de un bug, prueba buscando información en la url que te menciona el log o en bugs.launchpad.net. Tambien puedes ejecutar en una terminal "ubuntu-bug amarok" y un asistente enviara un reporte con documentos anexados ;)

Saludos

---

### Post by Carlos C on 2009-06-30
Sobre amarok, para estar seguros de que no sea el mismo problema, necesitaríamos saber si te da algún tipo de error cuando tratas de reproducir los archivos. ¿Antes los reproducía o nunca lo ha hecho? ¿Qué formato de archivos son?

---

### Post by aledruetta on 2009-06-30
> **kamus said:**
> Quizas se trata de un bug, prueba buscando información en la url que te menciona el log o en bugs.launchpad.net. Tambien puedes ejecutar en una terminal "ubuntu-bug amarok" y un asistente enviara un reporte con documentos anexados ;)

Saludos

Voy a intentar con lo que me sugerís, pero nunca reporté un bug... y si está en inglés... no sé si voy a sacar provecho de la información.

> **Carlos C said:**
> Sobre amarok, para estar seguros de que no sea el mismo problema, necesitaríamos saber si te da algún tipo de error cuando tratas de reproducir los archivos. ¿Antes los reproducía o nunca lo ha hecho? ¿Qué formato de archivos son?

A ver... yo probé Amarok en una instalación anterior de Jaunty, y sí, los reproducía. Después formateé por otra cuestión, reinstalé, y recién ayer instalé Amarok, cargué la biblioteca e intenté reproducir. Ahora no reproduce los audios de la biblioteca.

Son archivos mp3. La biblioteca es grande, unos 60 Gb ¿tendrá algo que ver?

Y probé. No reproduce archivos sueltos que arrasto al Amarok. 

Lo peor de todo, creo que cometí el peor error de mi vida. Me reorganizó todas las carpetas de música no sé con qué criterio, algo así como "por autor", pero ustedes saben que en los mp3 suelen no estar completa la información. Así que ahora tengo todo mezclado. Creo que me voy a suicidar!!!!!!! Por qué me tenía que ir a meter con KDE!!¿?!!?!

---

### Post by kamus on 2009-06-30
> **aledruetta said:**
> Voy a intentar con lo que me sugerís, pero nunca reporté un bug... y si está en inglés... no sé si voy a sacar provecho de la información.



A ver... yo probé Amarok en una instalación anterior de Jaunty, y sí, los reproducía. Después formateé por otra cuestión, reinstalé, y recién ayer instalé Amarok, cargué la biblioteca e intenté reproducir. Ahora no reproduce los audios de la biblioteca.

Son archivos mp3. La biblioteca es grande, unos 60 Gb ¿tendrá algo que ver?

Y probé. No reproduce archivos sueltos que arrasto al Amarok. 

Lo peor de todo, creo que cometí el peor error de mi vida. Me reorganizó todas las carpetas de música no sé con qué criterio, algo así como "por autor", pero ustedes saben que en los mp3 suelen no estar completa la información. Así que ahora tengo todo mezclado. Creo que me voy a suicidar!!!!!!! Por qué me tenía que ir a meter con KDE!!¿?!!?!

El asistente esta en español y el formulario de launchpad esta en ingles pero tambien es semi-asistido y no es muy complicado de completar, cualquier duda puedes postear en el foro ;)

Saludos

---

### Post by guillermolisi on 2009-06-30
Me parece que reportar como bug que Amarok 2.0.2 no reproduce archivos mp3 cuando hay otras instalaciones en las que si funciona, es algo apresurado.

Algo me dice que puede haber alguna inconsistencia en las versiones de librerias necesarias de KDE 4 para que funcionen correctamente Amarok y, tal vez tambien, K9copy.

Ale dijo estar usando Gnome como entorno grafico y agrego estas aplicaciones KDE a el.

Estoy usando ambas aplicaciones en KDE 4.2.4 con JJ y ambas funcionan perfectamente bien.

---

### Post by Carlos C on 2009-07-01
Respecto al problema de k9copy. Dices que apareció cuando añadiste el cdrom. Puede que el problema sea de los archivos de configuración. No estoy seguro, pero creo que los archivos están en /home/tu_nombre_usuario/.kde/share/config. Creo que son dos archivos que tendrías que eliminar y probar de nuevo.

---

### Post by aledruetta on 2009-07-01
> **Carlos C said:**
> Respecto al problema de k9copy. Dices que apareció cuando añadiste el cdrom. Puede que el problema sea de los archivos de configuración. No estoy seguro, pero creo que los archivos están en /home/tu_nombre_usuario/.kde/share/config. Creo que son dos archivos que tendrías que eliminar y probar de nuevo.

Voy a probar lo que me decís, pero creo que no dará resultado porque ya realicé una búsqueda de todos los archivos y carpetas con la cadena "k9copy", borré todo y reinstalé, y sigue dando el mismo error.

Veo qué encuentro en esa carpeta y aviso el resultado.

Saludos y gracias,
Alejandro.

---

### Post by aledruetta on 2009-07-01
Buenísimo, Carlos C, resucitó K9copy!!!!

Los archivos borrados son:
```
k9copyrc k9copy
```
Qué extraño que cuando borré todo no tuve el mismo resultado.

Ahora voy a poder convertir "La última tentación de Cristo" de Scorsese!!!

Lo de Amarok ya mucho no me importa porque con el odio que le agarré, calculo que nunca más voy a querer usarlo. Me va a llevar algunos años reorganizar mi biblioteca musical, si es que alguna vez lo consigo.

Saludos y gracias,
Alejandro.

---

### Post by radixs on 2009-07-03
Tengo la impresion que el problema de amarok es que te faltan librerias, prueba con lo siguiente

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by aledruetta on 2009-07-03
> **radixs said:**
> Tengo la impresion que el problema de amarok es que te faltan librerias, prueba con lo siguiente

```
sudo apt-get install libxine1-ffmpeg
```

Gracias radixs,

Será de utilidad para algún otro ubuntero, yo desistí de Amarok.
¡Aguante Rhythmbox! Es feo pero nunca me traicionó, jejeje.

---

### Post by Carlos C on 2009-07-04
Bueno, creo que podemos dar el thread por solucionado entonces.

---


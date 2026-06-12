---
title: "Instalando Panflute"
date: 2011-01-16
forum: Software
---

### Post by patraicio on 2011-01-16
Saludos colegas:

Visitando un blog dónde el autor mostraba los cambios a su escritorio en Ubuntu 10.10 me encontré con la fascinante opción de poder manejar el reproductor de música desde el panel superior de Gnome. Buscando posibles programas -él no mencionaba cual era- dí con Panflute, el que me gustó por su variada compatibilidad con reproductores conocidos de ubuntu. El programa básicamente lo que hace es usar la interfaz de un reproductor (Amarok, Guadalyaque, Rhythmbox, etc.) y poner los botones básicos en el panel, todo bien hasta ahí.
Bajé la versión 0.7.0 de [aquí]("http://www.kuliniewicz.org/music-applet/") (link luego a launchpad), al descomprimir el archivo .tar .gz y aplicar ./configure a la carpeta para comenzar a instalar me sale la siguiente respuesta: **Could not find Python Headers**. Busco en internet, con lo que llego a:

> $ sudo apt-get update 
$ sudo apt-get install python-dev

Vuelvo a la carpeta de panflute para hacer un ./configure y me sale de respuesta:

> No package 'pygobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGOBJECT_CFLAGS
and PYGOBJECT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Nuevamente busco en internet y me informó sobre las características del paquete Pygobject, lo descargo (de [aquí]("http://live.gnome.org/PyGObject#Downloads")) y como es un .tar.gz aplico ./configure a la carpeta que descomprimo, la respuesta es:

> *** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: maybe you want the pygobject-2-4 branch?

Voy al gestor de paquetes Synaptic y me doy cuenta de que el único paquete relacionado con Glib es:
> glibc-doc
Embedded GNU C Library: Documentation

Ahora, todo esto sucedió antes de tener que formatear, ya que me encontraba buscando información sobre ese paquete que no sé que hace -GLIB-, cuando reinicio y el arranque se queda pegado en: **Check battery state .... [OK]**. Obviamente me mandé un condoro de tanto instalar cosas que no sabia para lo que eran -de echo no recuerdo si instalé algo relacionado con Glib (creo que meti mano en una libreria GTK+)-. Al final tuve que formatear y salvo la "paja" de reinstalar algunas cosas de nuevo no me vi mayormente afectado.
Con respecto a mi problema: ahora me encuentro en el punto muerto que menciono mas arriba (GLIB) y no he querido hacer nada debido a lo que me pasó antes. La verdad fuera de Panflute no sé que son las otras cosas con las que he estado jugando (sé que pygobjet es para programar, y está relacionado con pythón, por lo que supongo que mi programa está hecho en ese lenguaje, por ello me pedía ese paquete), lo que también me sirvió para darme cuenta de que existe muy poca información sobre asuntos más técnicos relacionados con linux, las wikis están muy atrasadas y los blog's y foros no dan a basto para tanta cosa nueva.
Desearía saber si alguien me puede ayudar, recomendandome otro programa que satisfaga mi necesidad o delineando el camino que me queda por recorrer. Si hablé de más sobre cosas que no comprendo, perdón, no es de soberbio pero traté de leer y entender lo que pude (solo leo inglés de modo técnico y con nociones casi binarias, por lo que un documento de instrucciones no lo comprendo mucho, por no decir nada), por lo demás soy solo un simple estudiante pa' profe de Historia tratando de lidiar con linux.

Desde ya -y como siempre- gracias.

Saludos!

---

### Post by asterix77 on 2011-01-17
Revisa el siguiente post, te puede ayudar a compilar el programa. Pero una recomendación: siempre es bueno tratar de buscar cualquier programa en formato deb, y para eso lo mejor es el amigo google.

[http://ubuntuforums.org/showthread.php?t=1665382](http://ubuntuforums.org/showthread.php?t=1665382)

En el siguiente link está en formato deb, simplemente una vez descargado haces un doble click y esperas a que se instale, si faltan dependencias, automáticamente la descargará.

[http://www.espaciolinux.com/foros/software/antiguo-music-applet-gnome-cambia-panflute-applet-t47664.html](http://www.espaciolinux.com/foros/software/antiguo-music-applet-gnome-cambia-panflute-applet-t47664.html)

Saludos

---

### Post by asterix77 on 2011-01-17
Revisa el siguiente post, te puede ayudar a compilar el programa. Pero una recomendación: siempre es bueno tratar de buscar cualquier programa en formato deb, y para eso lo mejor es el amigo google.

[http://ubuntuforums.org/showthread.php?t=1665382](http://ubuntuforums.org/showthread.php?t=1665382)

En el siguiente link está en formato deb, simplemente una vez descargado haces un doble click y esperas a que se instale, si faltan dependencias, automáticamente la descargará.

[http://www.espaciolinux.com/foros/software/antiguo-music-applet-gnome-cambia-panflute-applet-t47664.html](http://www.espaciolinux.com/foros/software/antiguo-music-applet-gnome-cambia-panflute-applet-t47664.html)

Saludos

---

### Post by patraicio on 2011-01-17
Sí comprendo la facilidad del .deb, pero mi drama a veces es tener poca fe en ciertas fuentes. En particular ahora me conformé con llegar a la página de desarrollo del programa, no busqué más.
Con respecto a mi problema y según lo que expuse aquí, ¿no hice nada de más al instalar el compilador que mencionas? es decir, si un proceso -el que me indicaste tú y el que hice yo- no anula al otro.
Por último muchísimas gracias, de verdad me salvaste de una situación incomoda. Ojalá este post pueda ayudar a otras futuras consultas.

Saludos y gracias denuevo!


PD: Todo lo anterior sucedió simplemente por querer poner la maldita cap de mi escritorio en el post correspondiente de este foro :evil:

---

### Post by RafaelG on 2011-01-18
> **patraicio said:**
> 
PD: Todo lo anterior sucedió simplemente por querer poner la "_maldita_" cap de mi escritorio en el post correspondiente de este foro :evil:

Patraicio,

Favor recuerda el codigo de conducta y trata de conservar un buen vocabulario al momento de ingresar post en el forum.

Saludos cordiales,

---

### Post by moreback on 2011-01-18
glib también tiene paquetes de desarrollo que puedes necesitar, como libglib2.0-dev

Saludos.

---

### Post by patraicio on 2011-01-27
> **RafaelG said:**
> Patraicio,

Favor recuerda el codigo de conducta y trata de conservar un buen vocabulario al momento de ingresar post en el forum.

Saludos cordiales,


OK, disculpa ... la emoción de la "escribición"

Saludos!

---


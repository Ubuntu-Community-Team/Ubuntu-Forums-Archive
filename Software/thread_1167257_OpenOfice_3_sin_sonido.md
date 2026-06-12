---
title: "OpenOfice 3 sin sonido"
date: 2009-05-22
forum: Software
---

### Post by NickCis on 2009-05-22
Hola, hace poco instale kubuntu 9.04, que viene con el openOffice 3, y no tengo sonido :S. Como se podria solucionar?.

Puse esto en consola para ver si era un error de configuracion, capas sirve:
```
newpc@newpc-desktop:~$ sudo update-alternatives --config java
[sudo] password for newpc:

Sólo hay un programa que provee java
(/usr/lib/jvm/java-6-sun/jre/bin/java). No se configurará nada.
newpc@newpc-desktop:~$

```

Saludos.

Edit: estoy casi seguro que el problema es de java, no del openoffice, por que tambien tengo problemas con el jdownloader (cada vez qe lo abro es como si lo abriera por primera vez, y otras cosas). Sera que me falta instalar algo?. Ahh mi Kubuntu es 32 bits...

---

### Post by Mauro22 on 2009-05-22
Doy por hecho que tenes permisos para escribir en la carpeta de JDownloader...


Probaste corriendolo como otro usuario o como el mismisimo root ??

---

### Post by NickCis on 2009-05-23
Sisi, lo de la carpeta si, tengo los permisos.
Dsp pruebo con sudo por qe otro usuario no tengo en la pc.

Y que me dicen que el openoffice 3 no tenga sonido, no puede ser un problema de la maquina virtual de java?.

Saludos.

---

### Post by staar on 2009-05-23
por lo que googlee, para tener sonido en OOo, tenés que instalar el Java Media Framework...

[http://java.sun.com/javase/technologies/desktop/media/jmf/2.1.1/download.html]("http://java.sun.com/javase/technologies/desktop/media/jmf/2.1.1/download.html")

[http://forums.sun.com/thread.jspa?threadID=5368614&tstart=1]("http://forums.sun.com/thread.jspa?threadID=5368614&tstart=1")

saludos

---

### Post by NickCis on 2009-05-23
Tengo problemas para instalar el JMF, no puedo, como dicen esas instrucciones (eso de renombrar el bin, ponerle zip, descomprimirlo y te aparece un archivo, que lo renombras a bin).
Cuando descomprimo el bin (renombrado a zip) me aprece una carpeta con 3 subcarpetas, ahi que hago?.

Saludos.

Edit: Continue googleando y parece que el problema con el JMF es re comun y a nadie le anda. Lo que no entiendo es por que en Ubuntu 8.04 el OpenOffice.Org 2 anda con sonido y completo, y ahora en Kubuntu 9.04 el OpenOffice.org 3 el sonido no anda. No entiendo por que los desarrolladores de Ubuntu incluyen una aplicacion que no anda totalmente...

---

### Post by Hei Ku on 2009-05-23
> **NickCis said:**
> No entiendo por que los desarrolladores de Ubuntu incluyen una aplicacion que no anda totalmente...

Quizas no lo encontraron al error, y recien lo vieron una vez lanzada esta version. Los cambios de version siempre traen aparejado algun problema.
Esta reportado el bug? Podes ayudar a solucionarlo? Buenisimo.

Por otro lado, me suena un poco arrogante el comentario. Cualquiera se puede equivocar. No te parece?

---

### Post by pablo.s on 2009-05-23
Yo no termino de entender
que significa "OpenOffice 3
sin sonido". Yo he utilizado
el programa de presentaciones
y si me funciona el sonido.

---

### Post by NickCis on 2009-05-23
Tenes razon, pido perdon por el comentario.
Igual, este error tambien lo tuve al intentar instalar OpenOffice.org 3 en ubuntu 8.04, creo que es un error conocido (hice un post en este foro, no lo pude resolver el error, lo que me forso volver a openoffice 2). Lo que no entiendo es por que no anda OpenOffice3.

Puede instalar el JMF usando esta guia [http://munguis.wordpress.com/2008/04/15/instalando-el-java-media-framework-jmf-en-ubuntu/](http://munguis.wordpress.com/2008/04/15/instalando-el-java-media-framework-jmf-en-ubuntu/)
Haciendo la prueba de la pagina de java, me dice que tengo instalado JMF, pero sigo sin sonido en Open Office, seguire buscando en Google, pero la verdad ni idea...

Saludos, si es un bug que tengo que reportar, como lo hago?.

---

### Post by NickCis on 2009-05-23
> **pablo.s said:**
> Yo no termino de entender
que significa "OpenOffice 3
sin sonido". Yo he utilizado
el programa de presentaciones
y si me funciona el sonido.

Significa que las presentaciones que tiene sonido, no hacen ni Mu. Si probas los sonidos de la galeria de reproduccion del Open Office, tampoco nada. Si creo una presentacion y le agrego un archivo de musica, el archivo esta, pero no hay musica. Si uso el reproductor de medios (para probar si anda el sonido) del Open Office, con cualquier archivo de musica, tampoco anda. 
Alguna Idea?.
Saludos.

Edit: Agrego informacion, ejecutando OpenOffice por consola me da esto (al intentar reproducir algo):
```
(openoffice.org:3876): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(openoffice.org:3876): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(openoffice.org:3876): GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(openoffice.org:3876): GStreamer-CRITICAL **: gst_bus_add_watch_full: assertion`GST_IS_BUS (bus)' failed

(openoffice.org:3876): GStreamer-CRITICAL **: gst_bus_set_sync_handler: assertion `GST_IS_BUS (bus)' failed

(openoffice.org:3876): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(openoffice.org:3876): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(openoffice.org:3876): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(openoffice.org:3876): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(openoffice.org:3876): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed
```

Devuelta pido perdon por mi comentario, la verdad me calente, por que estube toda la tarde con eso del JMF, y recien que lo pude instalar el sonido sigue sin andar,,, Por favor no me tomen mal...

---

### Post by Hei Ku on 2009-05-23
Esta es la guia oficial sobre como reportar bugs: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Por otro lado, yo buscaria por el lado de Java y la interaccion con el engine de sonido de gnome. OpenOffice hace uso y abuso de java. Demasiado para mi gusto. Fijate por el seteo que tiene, a ver si esta apuntando a un engine de sonido equivocado.

---

### Post by NickCis on 2009-05-23
> **Hei Ku said:**
> Esta es la guia oficial sobre como reportar bugs: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Por otro lado, yo buscaria por el lado de Java y la interaccion con el engine de sonido de gnome. OpenOffice hace uso y abuso de java. Demasiado para mi gusto. Fijate por el seteo que tiene, a ver si esta apuntando a un engine de sonido equivocado.

Ahora me fijo en toda la configuracion del OpenOffice, del java no se como fijarme :S... Pero el engine de sonido en Gnome es el mismo qe en mi Kubuntu?.

Saludos.
P.D.: a alguien le anda el sonido en Kubuntu 9.04 con OpenOffice3?

---

### Post by NickCis on 2009-05-24
Nadie sabe de que depende el sonido en OpenOffice?....

Saludos.

---

### Post by Hei Ku on 2009-05-24
El OO.org usa directamente el JFM de java. Uno de los problemas es que hay muy pocos plugins o codecs para este. Asi que incluso si lo logras hacer andar, no necesariamente te va a andar en todos los casos.

En varios posts que encontré, habian tenido suerte con los mp3, pero no todos los .avi andaban dependiendo del encoding de sonido que hubieran utilizado.

Una solucion era probar con el Go-OO, que es un fork de OpenOffice que usa gstreamer en vez de java.

---

### Post by gmunioz on 2009-05-24
Hola nic....:

Se de que depende:

Si la versión de OOo que estas usando incluye el parche para utilizar

gstreamer para la reproducción multimedia, tienes que instalar gstreamer

con todos sus plug-ins.

Si la versión de ubuntu no incluye soporte para gstreamer, debes entonces

buscar cómo utilizar el "java media framework".

Si has conseguido activar el sonido con "java media framework" de manera

que se puedan insertar sonidos en las aplicaciones de Openoffice, pero lo

que ocurre es que no se tiene sonido en las presentaciones en Power 

Point puede que el sonido provenga de un mp3, este formato que no está 

soportado por jmf

En definitiva, la versión oficial de OOo para Linux no incluye soporte

multimedia, es necesario instalar el jmf que no tiene soporte para mp3,

las variantes de OOo que utilizan gstreamer, hacen necesario tener todos 

los plugins instalados.

Como se ve es un problema de openoffice no de Ubuntu o gnulinux

Saludos.

---

### Post by NickCis on 2009-05-24
Solucionado instalando todos los gstreamer pluings, por que logre instalar el jmf pero era lo mismo que nada.

Muchas gracias :P

---


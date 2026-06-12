---
title: "Kdenlive: Plugin para video en reversa, no puede ser tan comlejo."
date: 2009-10-17
forum: Software
---

### Post by daggaz on 2009-10-17
Hola.
Bueno, una de las únicas cosas que me lamento en Kdenlive es que haga falta la simple función de voltear un video (ponerlo en revesa), cosa que hasta con Kino se puede hacer fácil (pero no a una sola sección). 
Busqué en internet y resulta que hay una manera de lograrlo y es instalando Kdenlive desde la versión MLT (o algo así): [http: //en.wikibooks.org/wiki/Kdenlive/Video_effects]("http://en.wikibooks.org/wiki/Kdenlive/Video_effects") (ver *Speed*).
Entonces averiguo que rayos es eso de la versión de MLT. Entonces, según la documentación ([http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/installing-source/installing-mlt-rendering-engine](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/installing-source/installing-mlt-rendering-engine)) necesito bajar e instalar los paquetes de MLT desde aquí: [http://www.mltframework.org/twiki/bin/view/MLT/](http://www.mltframework.org/twiki/bin/view/MLT/)
Bien. La bajo,pero oh sorpresa, para instalar MLT es necesario las siguientes dependencias:  *avformat, ffmpeg, bluefish, dv, libdv, gtk2, mainconcept, resample, sdl, vorbis, xml* según esta página (y según la consola cuando traté de instalarlo la primera vez): [http://www.mltframework.org/twiki/bin/view/MLT/Install](http://www.mltframework.org/twiki/bin/view/MLT/Install)
Bueno, a buscar estas dependencias, aformtunadamente muchas de ellas no fueron complicadas, pero llego a *GTK2* y me entero de que que necesito más dependencias para intalar estas cuatro antes de poder instalar *GTK: Fontonfig, Cairo, libtiff,  Pango, PKG, ATK, Glib*, y no recuerdo si alguna otra más ([http://library.gnome.org/devel/gtk/unstable/gtk-building.html](http://library.gnome.org/devel/gtk/unstable/gtk-building.html)). Para colmo, ATK y Pango me piden más dependencias.
Me pierdo en este mundo de dependencia y finalmente creo haber instalado todo para poder instalar el endemoniado GTK pero la terminal me sale con lo siguiente: 
```
/usr/local/lib/libgio-2.0.so: undefined reference to `g_error_new_valist'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_array_unref'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_hostname_is_non_ascii'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_hostname_to_ascii'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_mkstemp_full'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_array_get_type'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_byte_array_unref'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_mapped_file_unref'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_byte_array_get_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_array_get_element_size'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_main_context_get_thread_default'
collect2: ld returned 1 exit status
make[4]: *** [gtk-query-immodules-2.0] Error 1
make[4]: se sale del directorio `/home/diego/gtk+-2.18.2/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: se sale del directorio `/home/diego/gtk+-2.18.2/gtk'
make[2]: *** [all] Error 2
make[2]: se sale del directorio `/home/diego/gtk+-2.18.2/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/diego/gtk+-2.18.2'
make: *** [all] Error 2

```
al hacer *make* y con
```
collect2: ld returned 1 exit status
make[3]: *** [gtk-query-immodules-2.0] Error 1
make[3]: se sale del directorio `/home/diego/gtk+-2.18.2/gtk'
make[2]: *** [install-recursive] Error 1
make[2]: se sale del directorio `/home/diego/gtk+-2.18.2/gtk'
make[1]: *** [install] Error 2
make[1]: se sale del directorio `/home/diego/gtk+-2.18.2/gtk'
make: *** [install-recursive] Error 1

```
Al *make install*.
En fin. Sigo con la instalación de MLT para ver si funciona y raro pero logro compilarlo aparentemente bien.
Luego procedo a instalar de nuevo Kdenlive (por que tuve que desinstalarlo al desinstalar mi antiguo MLT). Y al iniciarse se vuelve más lento que antes. Busco la famoso función de reversa dentro de la opción para cambiar el tiempo y nada, la busco en la librería de efectos y tampoco.

Ya no sé que hacer y me quedé sin ganas de pensar, tengo como tres días trabado en esto y necesito editar un video con esta mentada reversa para antes del 30 de Octubre.
No sé si más bien no sepa aún compilar bien. De las veces que lo he hecho muy pocas he logrado hacer que todo funcione bien, y casi siempre hay que instalar un mar de dependencias... 

Ojalá alguien me pueda ayudar, gracias.

---

### Post by pablo.s on 2009-10-17
> **daggaz said:**
> Ya no sé que hacer y me quedé sin ganas de pensar, tengo como tres días trabado en esto y necesito editar un video con esta mentada reversa para antes del 30 de Octubre.
No sé si más bien no sepa aún compilar bien. De las veces que lo he hecho muy pocas he logrado hacer que todo funcione bien, y casi siempre hay que instalar un mar de dependencias... 

Ojalá alguien me pueda ayudar, gracias.

Mira, hay un pequeño programa
que se llama Avidemux que hace
este tipo de efectos (no he comprendido
si necesitas un flip o un reverse, pero
puede hacer ambos efectos) sin tanta
complicación.
Avidemux funciona en su versión QT
sin ninguna dependencia de GTK.
Puedes bajarlo desde [Getdeb]("http://www.getdeb.net/search.php?keywords=avidemux") o desde
Synaptic.

---


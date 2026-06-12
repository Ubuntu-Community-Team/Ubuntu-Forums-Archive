---
title: "&quot;glXCreatePixmap&quot; when GLX 1.3 is not supported"
date: 2009-11-25
forum: Software
---

### Post by aledruetta on 2009-11-25
Hola Comunidad!

Ayer comenzó a ocurrir lo siguiente con mi Ubuntu Karmic:

La sesión inicia sin efectos de escritorio, sin screenlets y sin decoración de ventanas. Activo Compiz Fusion Icon y veo que tiene seleccionado el decorador Gtk y Metacity. Cambio a Compiz como gestor de ventanas y, aparentemente, todo bien. Pero, al reiniciar, todo está como antes.

Abrí la terminal y hice algunas pruebas con:
```
metacity --replace
compiz --replace
```Con la segunda opción arroja lo siguiente:
```
karmic@karmic-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```Busqué en Google y hay un bug reportado:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=551647](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=551647)

Pero, si existe, no encuentro alguna solución más o menos comprensible (para mí)

¿Alguna sugerencia?

Saludos!

PD: en algunos cambios de compiz a metacity, se tilda el panel de gnome y únicamente saliendo por Ctrl + Alt + F2 consigo reiniciar.

---

### Post by Mauro22 on 2009-11-25
Probá lanzando Compiz sin el --replace

Proba este script que a mi me salvó 2 veces ya.

[http://www.4shared.com/file/138070946/4e007a79/compiz-check.html](http://www.4shared.com/file/138070946/4e007a79/compiz-check.html)

Te dice que está mal y lo arregla solo.

---

### Post by aledruetta on 2009-11-25
> **Mauro22 said:**
> Probá lanzando Compiz sin el --replace

Proba este script que a mi me salvó 2 veces ya.

[http://www.4shared.com/file/138070946/4e007a79/compiz-check.html](http://www.4shared.com/file/138070946/4e007a79/compiz-check.html)

Te dice que está mal y lo arregla solo.

Hola Mauro!

Voy a dejar el script como último recurso, a ver si surge alguna solución un poco menos "a ciegas".

Lanzando compiz sin --replace se recupera la decoración de ventanas y los efectos de escritorio, pero creo que es lo mismo que hace con --replace. El problema es que si llego a cerrar en algún momento la terminal, o si intento enviar el proceso a segundo plano con Ctrl + Z, pierdo el control del escritorio y tengo que salir vía tty1.

Por ahora, lo que hice fue agregar en "Aplicaciones al inicio" una entrada con el comando "compiz", de esa manera el escritorio inicia normal cuando inicio el sistema. No así cuando cierro sesión y la abro nuevamente, ahí el problema persiste.

Por el momento, así puedo trabajar (espero no tener alguna otra sorpresa), pero sería interesante encontrar una solución como la gente.

---

### Post by Luciano90 on 2009-11-30
> **aledruetta said:**
> Hola Mauro!

Voy a dejar el script como último recurso, a ver si surge alguna solución un poco menos "a ciegas".

Lanzando compiz sin --replace se recupera la decoración de ventanas y los efectos de escritorio, pero creo que es lo mismo que hace con --replace. El problema es que si llego a cerrar en algún momento la terminal, o si intento enviar el proceso a segundo plano con Ctrl + Z, pierdo el control del escritorio y tengo que salir vía tty1.

Por ahora, lo que hice fue agregar en "Aplicaciones al inicio" una entrada con el comando "compiz", de esa manera el escritorio inicia normal cuando inicio el sistema. No así cuando cierro sesión y la abro nuevamente, ahí el problema persiste.

Por el momento, así puedo trabajar (espero no tener alguna otra sorpresa), pero sería interesante encontrar una solución como la gente.

Al hacer Ctrl+Z el proceso se pone en pausa, y ahi se "cuelga" el X.

Hay dos formas de hacerlo:
compiz &
desde un terminal
ó
Alt+F2 > compiz

---

### Post by aledruetta on 2009-12-01
> **Luciano90 said:**
> Al hacer Ctrl+Z el proceso se pone en pausa, y ahi se "cuelga" el X.

Hay dos formas de hacerlo:
compiz &
desde un terminal
ó
Alt+F2 > compiz

Gracias Luciano por la info, eso va a ayudar en momentos críticos. Hasta que salga un parche.

¿Me recomendás que en Aplicaciones al Inicio coloque "compiz &" en lugar de "compiz" a secas?

---


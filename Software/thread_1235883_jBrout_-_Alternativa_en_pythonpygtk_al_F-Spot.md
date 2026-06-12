---
title: "jBrout - Alternativa en python/pygtk al F-Spot"
date: 2009-08-09
forum: Software
---

### Post by santiagoward2000 on 2009-08-09
Hola gente!
Hoy, dando vueltas por Google, encontré este programa: [jBrout]("http://code.google.com/p/jbrout/"), un organizador de fotos escrito en python/pygtk.
Entre sus características, se encuentran:
[LIST]
[*]Gestión de Álbumes / fotos (= carpetas / archivos)
[*]Etiqueta fotos con palabras clave IPTC
[*]Uso interno Exif jpeg miniatura
[*]Comentarios en fotos (JPEG con comentarios) y en el álbum (archivo de texto en la carpeta)
[*]Girar sin pérdida JPEG (y miniatura Exif jpeg interna)
[*]Utilice información EXIF (fecha, tamaño ..)
[*]Búsqueda de imágenes (etiquetas, comentarios, fecha, ...)
[*]Uso de plugins (para exportar a html/galería, para actuar como un httpserver, para exportar fotos para ser enviadas por correo, ...)
[*]Trabaja sin base de datos! (sólo un archivo xml que se puede reconstruir a partir de cero)
[*]Maneja un montón de fotos (más de 30000 según el autor, yo lo confirmo con 3699)
[*]Exporta a cuentas de Flickr y Picasa Web (confirmo Picasa Web)
[*]Utiliza un sistema de canasta para recoger algunas fotos
[*]Puede ser localizada (actualmente la versión Inglés y Francés)
[*]Crear un mínimo de información Exif para imágenes sin Exif
[*]Rotación automática de imágenes
[/LIST]

Comparando el F-Spot con jBrout, usando la misma cantidad de fotos, el último usa menos memoria (20.2 MB contra 34.1 MB), pero al cargar los thumbnails, su uso aumenta bastante (llegó a 350 MB con todas mis fotos, mientras que F-Spot no subió de 100 MB), por lo que cargar muchas fotos al mismo tiempo en un sistema con poca RAM puede ser un problema. Además, aunque no se pueda medir, parece responder mucho más rápido. Finalmente, el plugin para exportar fotos vía mail no requiere abrir otro programa para funcionar, a diferencia del F-Spot que abre el Evolution (o el que se encuentre definido por defecto en GNOME).
Las únicas desventajas que encontré son que sólo está en inglés y francés, y que sólo puede manejar JPEGs (en realidad dicen que esta versión soporta imágenes RAW, pero no tengo ninguna dando vueltas como para probarlo).
En su wiki explican cómo instalarlo desde sus repositorios, pero algunas de sus características no me anduvieron (subir fotos a picasaweb), mientras que otras todavía no se encuentran en esa versión (sólo puede enviar mails por smtp sin autorización, por lo que no podía usar Gmail). Entonces me instalé su versión svn, y hasta ahora me anda todo.

En caso de que haya convencido a alguien de usarlo, acá va una guía con lo que encontré. Usé básicamente lo que hay en el [wiki de Ubuntu]("https://help.ubuntu.com/community/jBrout"), pero tuve que usar otra dirección svn y agregar unos paquetes más que requiere la nueva versión.

[LIST=1]
[*]Primero, instalamos los paquetes que vamos a necesitar. Arbimos la terminal e ingresamos:
```
sudo apt-get install subversion python-lxml python-imaging jhead exiftran libimage-exiftool-perl python-pyexiv2
```
[*]Después bajamos los archivos del svn:
```
sudo svn checkout http://jbrout.googlecode.com/svn/trunk/jbrout /usr/lib/jbrout
```
[*]Finalmente lo probamos con:
```
/usr/lib/jbrout/jbrout.py
```[/LIST]

Si todo va bien, podemos crear el un lanzador:

_**GNOME**_
Vamos a usar el editor de menú alacarte:
[INDENT][LIST]
[*]Click derecho Aplicaciones
[*]Editar menú
[*]En gráficos, click en Nuevo Item
[*]Nombre: jBrout (por ejemplo, pueden poner lo que quieran)
[*]Comando: /usr/lib/jbrout/jbrout.py
[/LIST][/INDENT]
Y listo! 

_**Xfce**_
En caso de que usen Xfce, se puede crear el lanzador de la siguiente forma, ya que no hay ningún editor de menú:
[LIST=1]
[*]En una terminal, ingresamos:
```
cd /usr/share/applications
sudo mousepad jBrout.desktop
```
[*]En mousepad, ponemos:
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=jBrout
Comment=
Categories=Application;Graphics;
Exec=/usr/lib/jbrout/jbrout.py
Icon=/usr/lib/jbrout/data/gfx/jbrout.ico 
Terminal=false
StartupNotify=false

```
[*]Grabamos, cerramos mousepad.
[*]_Nota:_
[INDENT]Cuando recién lo instalamos, la opción para definir programas externos no anda en Xfce. Esto es porque tiene que abrir un archivo de texto, y viene con un par de programas definidos, pero no incluye mousepad. Para arreglarlo, en una terminal hacemos:
```
sudo mousepad /usr/lib/jbrout/jbrout.py
```
Buscamos las siguientes líneas:
```
if JBrout.conf.has_key("editor"):
            runWith([JBrout.conf["editor"],"notepad.exe","leafpad","scite","gedit","kate","gvim"],unicode(JBrout.toolsFile))
        else:
            runWith(["notepad.exe","leafpad","scite","gedit","kate","gvim"],unicode(JBrout.toolsFile))
```
y agregamos **"mousepad"** en las dos listas, para que quede así:
```
if JBrout.conf.has_key("editor"):
            runWith([JBrout.conf["editor"],"notepad.exe","leafpad","scite","gedit","kate","gvim","mousepad"],unicode(JBrout.toolsFile))
        else:
            runWith(["notepad.exe","leafpad","scite","gedit","kate","gvim","mousepad"],unicode(JBrout.toolsFile))
```
Ahora tendría que andar esa opción. Si alguien usa algún otro editor de texto, también lo pueden agregar de esta forma.[/INDENT]
[/LIST]
Y ahora sí, listo! Si alguien necesita ver algúna imagen, adjunto una.
Espero que le sirva a todo aquel que busque algo más rápido que F-Spot, o que simplemente odie Mono ;)
Si tienen algún problema avisen.
Saludos!

---

### Post by juancarlospaco on 2009-08-09
Que bueno!!!, yo estoy usando el Clon Libre del Adobe LightRoom, se llama **BlueMarine**, 
esta developeaó en Javas, pruebenlo lo recomiendo tambien, 
podes poner tus fotos en una especie de mini-google-earth local
*(imagenes de la tierra de la Nasa usa)*,
para cuando haces un viajes y eso.

:)

---

### Post by santiagoward2000 on 2009-08-09
> **juancarlospaco said:**
> Que bueno!!!, yo estoy usando el Clon Libre del Adobe LightRoom, se llama **BlueMarine**, 
esta developeaó en Javas.

:)

Yo lo probé en algún momento (si no me equivoco, fue a partir de un post tuyo :)), pero me faltaban algunas cosas, mientras que tenía MUCHAS otras que nunca en mi vida iba a usar. Además a mí me crasheaba mucho (pero tengo ese problema con muchos programas java, no sé por qué).
Este es más parecido a Picasa o F-Spot, enfocado más en ordenar y compartir, y no tanto en editar fotos.

_PS:_
¡Qué bien que me siento ahora que me liberé completamente de Mono!

---

### Post by juancarlospaco on 2009-08-09
Ya se, pero como todo, va evolucionando, ahora esta mejor, le falta todavia, 
pero deci la verdad, parece un proyecto bien encaminado, ojala el autor lo termine,
me parece que un reemplazo Open Source del Adobe LightRoom es bueno.

[I]Mono no me j**e por la Licencia, me j**e por lo lento que es,
fijate el SQLite portado a los Monos, 
tanto laburo para obtener lo mismo pero 6 veces mas lento [/I]:(

---

### Post by Hei Ku on 2009-08-09
Probaron el Digikam y la integracion con Marble? Te deja hacer lo mismo.

---

### Post by santiagoward2000 on 2009-08-09
Mi idea era buscar algo más liviano. Para usar digiKam tengo que instalar 250MB de dependencias de KDE, y la verdad que no me interesan las opciones tipo geotag (eso es lo que hace la integración con Marble, no?). Yo sólo buscaba algo para organizar fotos, mandarlas por mail o subirlas a Picasa. Y jBrout hace todo eso! :)

---

### Post by santiagoward2000 on 2009-08-09
> **santiagoward2000 said:**
> Entonces me instalé su versión svn, y hasta ahora me anda casi todo (hay una opción para definir programas externos, por ejemplo para usar GIMP para editar las fotos, cuando lo elijo no me abre ningún menú).

Bueno, estuve investigando un poco más. Aparentemente, esta opción tendría que abrir un archivo de texto, donde se definen los programas externos. Supongo que debe estar escrito para usar gedit, y por eso no me anda en mi Xubuntu. Pero lo pude hacer igual abriendo con mousepad el archivo **~/.jbrout/tools.txt**. Habilité la que viene por ejemplo y ahora me aparece una opción cuando selecciono alguna foto para editarla en GIMP :). Se parece a la forma en que se definen las custom actions en thunar, está muy bueno!
Ahora tengo que ver cómo hacer que se abra mousepad con la opción del programa. Supongo que debe estar en el archivo **externaltools.py**. Aunque no sé mucho de python, voy a ver qué averigüo.
Saludos!

_EDIT:_
¡Lo encontré! Había que editar el archivo **jbrout.py**, y en las líneas:
```
if JBrout.conf.has_key("editor"):
            runWith([JBrout.conf["editor"],"notepad.exe","leafpad","scite","gedit","kate","gvim"],unicode(JBrout.toolsFile))
        else:
            runWith(["notepad.exe","leafpad","scite","gedit","kate","gvim"],unicode(JBrout.toolsFile))
```
hay que agregar **"mousepad"** en las 2 listas.

---

### Post by marianom on 2009-08-10
Gracias Santiago por la recomendación, viniendo de vos la voy a considerar seriamente.
Me encanta F-Spot pero el mono me pesa mucho (en la conciencia)...

---

### Post by santiagoward2000 on 2009-08-10
Por las dudas hago una aclaración más sobre algo que recién probé. Aunque es verdad que al principio jBrout usa menos memoria que F-Spot, después de ver algunas fotos esto cambia bastante. Una vez que cargan los thumbnails de las fotos, jBrout no los vuelve a tocar, mientras que F-Spot va borrando algunas para liberar memoria.
Esto hace que F-Spot sea más lento, sobre todo porque si subimos y bajamos varias veces, tiene que cargar las fotos una y otra vez. Sin embargo, esto logra que al cargar muchas fotos, el uso de memoria no suba tanto (yo no pude hacer que llegue a más de 100MB).
jBrout, al dejarlas en la memoria, hace que una vez que las cargó, moverse por las fotos sea más rápido, pero requiera más memoria. En mi caso, con 3729 fotos llegó a usar 350MB (no quiero imaginarme lo que usó el creador del programa que asegura que anda con más de 30000). Lo aclaro en caso de que alguien quiera usarlo en un sistema con poca RAM. En ese caso, cargar todas las fotos al mismo tiempo puede ser un problema.
Saludos!

---

### Post by jordilin on 2009-08-11
> **santiagoward2000 said:**
> Por las dudas hago una aclaración más sobre algo que recién probé. Aunque es verdad que al principio jBrout usa menos memoria que F-Spot, después de ver algunas fotos esto cambia bastante. Una vez que cargan los thumbnails de las fotos, jBrout no los vuelve a tocar, mientras que F-Spot va borrando algunas para liberar memoria.
Esto hace que F-Spot sea más lento, sobre todo porque si subimos y bajamos varias veces, tiene que cargar las fotos una y otra vez. Sin embargo, esto logra que al cargar muchas fotos, el uso de memoria no suba tanto (yo no pude hacer que llegue a más de 100MB).
jBrout, al dejarlas en la memoria, hace que una vez que las cargó, moverse por las fotos sea más rápido, pero requiera más memoria. En mi caso, con 3729 fotos llegó a usar 350MB (no quiero imaginarme lo que usó el creador del programa que asegura que anda con más de 30000). Lo aclaro en caso de que alguien quiera usarlo en un sistema con poca RAM. En ese caso, cargar todas las fotos al mismo tiempo puede ser un problema.
Saludos!
Yo probé el jBrout con unas pocas fotos y de seguida me subió a 100Mb mientras que F-Spot con unas menos me usaba solo 35Mb. Me he bajado el código del jbrout y la mayoría del código está en un sólo fichero de casi 3000 líneas, lo cuál no es que sea muy modular. He probado el phraymd [https://launchpad.net/phraymd](https://launchpad.net/phraymd) y parece que ande un poco mejor, igualmente esta en fase de desarrollo.

---

### Post by santiagoward2000 on 2009-08-11
> **jordilin said:**
> Yo probé el jBrout con unas pocas fotos y de seguida me subió a 100Mb mientras que F-Spot con unas menos me usaba solo 35Mb. Me he bajado el código del jbrout y la mayoría del código está en un sólo fichero de casi 3000 líneas, lo cuál no es que sea muy modular. He probado el phraymd [https://launchpad.net/phraymd](https://launchpad.net/phraymd) y parece que ande un poco mejor, igualmente esta en fase de desarrollo.

Hmm, parece interesante. Voy a probarlo en algún momento. Igual, como nunca reviso TODAS mis fotos, la memoria no es tanto problema, y no lo llevo a más de 50 MB.
Además tengo que ver qué características trae, porque ando fascinado con la opción de usar **"External Tools"** (puedo mandar fotos por bluetooth!).
Gracias por la recomendación, voy a comentar cuando lo pruebe.
Saludos!

---

### Post by jordilin on 2009-08-11
Acabo de probar el digikam [http://www.digikam.org/](http://www.digikam.org/), que aunque es una aplicacion con look and feel de Kde, esta pero que muy bien y de un toque muy profesional. Yo de momento me quedo con el F-Spot.

---


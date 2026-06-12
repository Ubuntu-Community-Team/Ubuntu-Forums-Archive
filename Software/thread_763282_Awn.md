---
title: "Awn"
date: 2008-04-22
forum: Software
---

### Post by ramiro_md on 2008-04-22
Hola ubunteros...tengo una consulta sobre awn !...resulta que lo instale de maravillas pero, quiero desactivar la opcion de que las ventanas minimizadas se vean en la barra..se que es con un applet, pero al desactivarlo y reiniciar el pc el applet se vuelve a activar :confused:..si tiene alguna idea del por que ? contestenme...desde ya muchas gracias =)

---

### Post by _kAz_ on 2008-04-30
> Hola ubunteros...tengo una consulta sobre awn !...resulta que lo instale de maravillas pero, quiero desactivar la opcion de que las ventanas minimizadas se vean en la barra..se que es con un applet, pero al desactivarlo y reiniciar el pc el applet se vuelve a activar ..si tiene alguna idea del por que ? contestenme...desde ya muchas gracias =)
Fijate si lo encontras en alguna de estas carpetas:

/usr/lib/awn/applets
o
/home/[tu_nombre_de_usuario]/.config/awn/applets

---

### Post by _kAz_ on 2008-04-30
Aprovecho para preguntar yo también.

1. Quiero instalar el awn-extra-applets, pero cuando estoy haciendo el ./configure me sale un error, no encuentra un python gtkmozembed. Instalé todo lo que tuviera relacion desde synaptic y nada.

2. Me faltan 3 elementos para hacerlo completamente funcional:
    a. Menú de Ubuntu (vendría a ser el "cajón" que tiene las aplicaciones+lugares y sistema)
    b. Papelera
    c. Mostrar escritorio (el icono que te minimiza todas las ventanas)

3. ¿Cómo hago para que inicie automáticamente al encender la pc?

Por ahora eso nomás. Salu3.

---

### Post by spg76 on 2008-04-30
> **ramiro_md said:**
> Hola ubunteros...tengo una consulta sobre awn !...resulta que lo instale de maravillas pero, quiero desactivar la opcion de que las ventanas minimizadas se vean en la barra..se que es con un applet, pero al desactivarlo y reiniciar el pc el applet se vuelve a activar :confused:..si tiene alguna idea del por que ? contestenme...desde ya muchas gracias =)

No sé si entiendo bien lo que queres, pero no hay ningún applet en Awn que te oculte las ventanas minimizadas.
 
> **_kAz_ said:**
> Aprovecho para preguntar yo también.

1. Quiero instalar el awn-extra-applets, pero cuando estoy haciendo el ./configure me sale un error, no encuentra un python gtkmozembed. Instalé todo lo que tuviera relacion desde synaptic y nada.

2. Me faltan 3 elementos para hacerlo completamente funcional:
    a. Menú de Ubuntu (vendría a ser el "cajón" que tiene las aplicaciones+lugares y sistema)
    b. Papelera
    c. Mostrar escritorio (el icono que te minimiza todas las ventanas)

3. ¿Cómo hago para que inicie automáticamente al encender la pc?

Por ahora eso nomás. Salu3.

1 y 2. En la wiki de Awn podés chequear si te falta alguna dependencia en [http://wiki.awn-project.org/Dependency_Matrix](http://wiki.awn-project.org/Dependency_Matrix). Fijate donde dice "Debian-based".
Si queres evitarlo, podes recurrir al repositorio de Reacocard para instalar awn-extras. Está bastante actualizado y a mí me funciona perfecto habiendo compilado Awn desde bzr.
Para esto agrega las siguiente líneas a sources.list:
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```
Y después hacé:
```
sudo apt-get update
sudo apt-get install awn-core-applets-bzr
```

3. En Awn Manager hay una casilla bajo en título "Startup behaviour" que dice "Automatically start AWN on login". Tildala y con eso debería bastar.

---

### Post by _kAz_ on 2008-05-01
Buena genio!!!

Primero me fije en los requerimientos, me faltaban un par. Igual cuando hice el ./configure se paro en el mismo error.

Así que fui a por el synaptic y agregué los repositorios. En un momento me asusté porque me borro el avant-window-navigator... Después me avive que tenia que instalar la versión bzr ;)

Por cierto, y en esto me estoy poniendo muyyyyy puntilloso, hay alguna forma de eliminar el panel por defecto, o aunque sea cambiar los botones de ocultación por uno transparente??? Me molesta sobremanera ese cuadradito blanco ahi abajo, jeje. Adjunto imagen para ser más gráfico.

Salu3.

---

### Post by spg76 on 2008-05-01
En el foro de Awn hay un thread sobre este tema en [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1792&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1792&page=1&isLive=true).
Te copio y traduzco:
> Turns out that if you go to /apps/panel/toplevels/top_panel_screen0 in gconf-editor and turn off expand and set monitor=3, that does the trick. Of course you'll probably want to first delete various apps from the top panel if they conflict with any awn apps (e.g., notification area).
"Al parecer si vas a /apps/panel/toplevels/top_panel_screen0 en gconf-editor y deshabilitas expand y pones monitor=3, eso funciona. Por supuesto que probablemente querras borrar primero varias aplicaciones de panel superior si tienen algún conflicto con alguna aplicación de awn (por ejemplo, notification area)."

Tené en cuenta que yo no lo probé, y está basado en la experiencia de otro usuario. Cualquier duda posteala en ese thread de Awn que seguro te lo solucionan.
Espero que te sirva.

---

### Post by benjamin_linux on 2008-08-28
Voy a revivir el post...

sigo las indicaciones, pero este es el resultado de apt-get install...

"
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  awn-core-applets-bzr: Depende: libawn0-bzr pero no va a instalarse
E: Paquetes rotos
"

Qué puedo hacer???

---

### Post by Hei Ku on 2008-08-28
que te dice si pones:

sudo apt-get install libawn0-bzr

---

### Post by benjamin_linux on 2008-08-28
Me aparece lo mismo y:

Los siguientes paquetes tienen dependencias incumplidas:
  libawn0-bzr: Entra en conflicto: **libawn0**
E: Paquetes rotos

---

### Post by pol666 on 2008-08-28
que sale cuando buscas en synaptic textualmente **libawn0 ** ?

---

### Post by benjamin_linux on 2008-08-28
libawn0 aparece instalada, es del avant window navigator...

No entiendo, (las librerías de) los applets de AWN entran en conflicto con (las librerías de) AWN??

Tengo que reemplazarlas??

---

### Post by pol666 on 2008-08-28
mmm no tengo idea.  

Te doy un consejo, capas te interesa. Podes probar Cairo-Dock, es una buena dock, que en la ultima version tiene todo lo que tiene AWN y mas...  el problema es que es un poco mas dificil de configurar. De todos modos, ahora me parece mas funcional

---

### Post by luks911 on 2008-08-28
> **benjamin_linux said:**
> libawn0 aparece instalada, es del avant window navigator...

No entiendo, (las librerías de) los applets de AWN entran en conflicto con (las librerías de) AWN??

Tengo que reemplazarlas??

Lo que debe estar pasando es que tenés instalado libawn0 pero lo que necesitás para los applets en la versión de los repositorios (la bzr) es el paquete libawn0-bzr. Son la misma cosa en distintas versiones y no pueden convivir, digamos. 
Capaz que estás confundiendo versiones y poniendo parte de los repositorios de Ubuntu y parte de los de reacocard. Una posibilidad: desinstalá todo lo de AWN y volvé a instalarlo marcando siempre la version bzr. Los paquetes principales son:
avant-window-navigator-bzr
awn-core-applets-bzr
awn-manager-bzr

---

### Post by benjamin_linux on 2008-08-29
Tenías razón luks911,

cuando iba a desinstalar desde Synaptics mi AWN noté que ahora me aparecía la versión bzr, desinstalé e intenté poner la versión bzr desde ahí pero me tiró error... Lo hice desde la consola y funcionó, me instaló el dock y se ejecutaba, pero cuando quería acceder a preferencias me aparecía un error... Entonces las "reinstalé" desde Synaptic y ahora sí, se me instaló todo..........

Mucho la verdad no me gusta, me parecía mucho mejor la versión normal. Me interesa mucho tener /home por ejemplo en la barra, pero por ejemplo la Terminal no me funciona, la tengo que cargar como lanzador y no me reconoce los íconos automáticamente para hacerlo, tengo que buscarlos manualmente en /usr/share...... y se cargan bastante feo la verdad los applets.

En fin, dicen que kairo-dock es mejor?

---

### Post by pol666 on 2008-08-29
cairo-dock.

A mi parecer si, La ultima version esta traducida por lo menos algunas cosas en ingles (la anterior estaba en polaco xD) y tiene plugins y applets que antes no tenia. Fijate busca los paquetes .deb, hay dos uno con el programa y otro con los applet y temas.

---

### Post by luks911 on 2008-08-29
> **benjamin_linux said:**
> Tenías razón luks911,

cuando iba a desinstalar desde Synaptics mi AWN noté que ahora me aparecía la versión bzr, desinstalé e intenté poner la versión bzr desde ahí pero me tiró error... Lo hice desde la consola y funcionó, me instaló el dock y se ejecutaba, pero cuando quería acceder a preferencias me aparecía un error... Entonces las "reinstalé" desde Synaptic y ahora sí, se me instaló todo..........

Mucho la verdad no me gusta, me parecía mucho mejor la versión normal. Me interesa mucho tener /home por ejemplo en la barra, pero por ejemplo la Terminal no me funciona, la tengo que cargar como lanzador y no me reconoce los íconos automáticamente para hacerlo, tengo que buscarlos manualmente en /usr/share...... y se cargan bastante feo la verdad los applets.

En fin, dicen que kairo-dock es mejor?

Desde la última versión hay que buscarle los íconos a las aplicaciones, eso es un poco molesto. Igual me gusta más que Cairo y los applets me funcionan. Pero podemos probar y elegir.

Saludos

Saludos

---

### Post by ogromano on 2008-08-30
Hola a todos...

Una pregunta y un comentario....

En el menu de "Keyboard Shortcuts" le puse que sacara el menu principal con Alt+F1 y funciona de maravilla. Se puede ponerle eso al AWN?

Probe el Cairo-Dock y aunque tiene todas las posibilidades de configuracion que me gustaria que AWN tuviera, la verdad no me gusto tanto. Me parecio un AWN en drogas! Se mueve un monton y se lleva un monton de la memoria en hacer los efectos... me gusta mas AWN porque es mas tranquilo. Ahora que si funcionara al 100% y tuviera mas applets, seria feliz! :)

---

### Post by luks911 on 2008-08-30
No sé si entendí lo que querés. Si es agregar un menú como el que se despliega al hacer clik en Aplicaciones (o en tu caso con Alt+F1), se puede con el applet AWN Main menu. Es como el botón de Aplicaciones, pero en el dock dell AWN: lo clikeas y se despliegan los menús de Accesorios, Gráficos, Herramientas del Sistema, etc, etc.

Saludos

---

### Post by ogromano on 2008-08-30
Casi exactamente lo que quiero... ya tengo el applet puesto ahora quiero que con Alt+F1 u otra combinacion salga el menu de ahi en vez del panel escondido que tengo por si las dudas de que me falle AWN. :)

---

### Post by luks911 on 2008-08-30
Ah, ¿que el menú del applet del AWN se despliegue al presionar la combinación de teclas? En principio diría que no se puede, al menos no con el AWN y los applets como vienen, aunque ni idea. Capaz que metiendo mucha mano sí, pero ya escapa a mis posibilidades, je.
Otra posibilidad, si querés agilizar la ejecución de programas usando sólo teclas es usar GnomeDO.

---

### Post by benjamin_linux on 2008-09-10
Vuelvo para contarles: estoy ENAMORADO de cairo dock. Primero instalé la versión 1.3 y el hecho de que estuviese en francés no era lo peor, no me gustó para nada. Pero la última versión, 1.6x, además de estar completamente en inglés, me pareció genial. Mucho más estable que la anterior y la verdad MUY pero MUY linda y con los mismos applets o más que AWN.

---

### Post by pol666 on 2008-09-10
ahá, lo mismo digo, dio un paso grande en esta version.

Aunque tengo un problema, En Awn cuando por ejemplo miminizaba el firefox, este quedaba en el mismo icono del lanzador, ahora con cairo cada vez que abro una aplicacion se me abre un icono aparte.

Se que se puede, por que esta llena de opciones, pero ¿como hago para que no abra un icono aparte?

---

### Post by benjamin_linux on 2008-09-10
Creo que es:

Configuración > TaskBar > Mix launchers and applis (tildá esa opción)

---


---
title: "Nuevita en Ubuntu"
date: 2011-04-26
forum: Software
---

### Post by NekoSushi on 2011-04-26
Holis!
Aqui una nueva integrante a su mundo y foro de Ubuntu :biggrin:

Siempre, estando en Windows, tenia la idea de pasarme a Ubuntu, porque mi PC no es de las mejores y tengo entendido que Linux consume menos PC que Windows (XP / Ubuntu)

Y hoy mismo instale Lubuntu, y me agrado.
Ya tengo todo actualizado, y ahora faltan las aplicaciones y toques personales.
Aqui mis preguntontas:

- Como instalo / activo los efectos visuales?
- Luego de actualizarse el SO, se instalan tambien los codecs de audio / video?
- Cual es el mejor reproductor de video? (no busco calidad, solo rendimiento)
- Yo solo encontre como instalar los drivers de la grafica, los demas drives se autoinstalan?
- Yo tengo 3 discos rigidos, y Lubuntu me detecta solo 2, en el BIOS los detecta bien
- Como desinstalo aplicaciones?
- Como es el tema de los virus?
- Las opciones del Mouse no guarda mis preferencias

- Lei por ahi, que luego de instalar los drivers de la grafica nVIDIA, tiene que aparecer su logo al iniciar el SO para saber que todo funciona bien, pero a mi no me aparece (solo cambio el logo de Lubuntu por el texto Ubuntu 10.10)

Si son muchas preguntas, el punto que mas me interesa es el de los discos rigidos  :biggrin:

Hace poquito que aprendi lo que es la Terminal, Sudo, los comandos, Synaptic, etc. Muy basico para unos, no tanto para otros :biggrin:

*Perdon si no estoy en la seccion correcta*

Gracias!

---

### Post by ivanovnegro on 2011-04-26
!Bienvenida!

Pues sí, tienes un montón de preguntas.
Como no uso Lubuntu ni siquiera sé si se pueden usar los efectos.
Cuando quieres abrir por ejemplo un archivo MP3 tendría que salirte un popup diciéndote que te faltan los codecs y los podrías instalar fácilmente. Pero tambén puedes añadir el repositorio de Canonical Partners en el Centro de Software como fuente para poder usar los codecs privativos.

El mejor reproductor de vídeo, te puedo recomendar el VLC, lo instalas desde el Centro de Software.

Desinstalar también funciona desde el Centro de Software o si quieres el Synaptic.

Con los virus no te preocupes, esto no es un problema de Linux.

[Aquí]("https://wiki.ubuntu.com/Lubuntu") un poco de información.

!Disfruta Lubuntu!

---

### Post by juancarlospaco on 2011-04-26
> **NekoSushi said:**
> 
- Como instalo / activo los efectos visuales?

Necesitas tener los Drivers de la placa de Video, 
igualmente te comento que consumen un poquitin mas de recursos que no usarlos, 
depende de gustos. Debes tener Compiz instalado.

> **NekoSushi said:**
> 
- Luego de actualizarse el SO, se instalan tambien los codecs de audio / video?


No necesariamente..., 
si necesitas usar algun Formato Propietario puedes instalar los Extras Restringidos,
en tu gestor de paquetes preferidos buca e instala lubuntu-restricted-extras,
o en una Ventana de terminal:

[sudo apt-get install lubuntu-restricted-extras]("apt:lubuntu-restricted-extras")

> **NekoSushi said:**
> 
- Cual es el mejor reproductor de video? (no busco calidad, solo rendimiento)


[VLC]("apt:vlc")

> **NekoSushi said:**
> 
- Yo solo encontre como instalar los drivers de la grafica, los demas drives se autoinstalan?


Demas Drivers de que?, mayormente se instalan si son necesarios,
se poria decir que se *"autoinstalan"* si tienes internet en la myoria de los casos.

> **NekoSushi said:**
> 
- Yo tengo 3 discos rigidos, y Lubuntu me detecta solo 2, en el BIOS los detecta bien


Los otros Discos los usabas en windows o algun otro SO?, para saber que formato tienen,
Igualmente lo deberias ver en el menu de Lugares o Places.

> **NekoSushi said:**
> 
- Como desinstalo aplicaciones?


Depende de como lo instales, 
desde cada gestor de paquetes tiene la opcion de desinstalarlos tambien,
sino desde una ventana de Terminal puedes desinstalarlos:

Para Desinstalar, Sin remover la configuracion de ese programa:
sudo apt-get remove NOMBREdePAQUETE

ejemplo: sudo apt-get remove vlc

Para Desinstalar y Remover la configuracion de ese programa:

sudo apt-get purge NOMBREdePAQUETE

ejemplo: sudo apt-get purge vlc

El programa debe estar instalado para poder removelo o purgarlo.
La diferencia es que remove DEJA la configuracion aunque desinstala el programa,
de manera tal que si lo vuelves a instalar iniciara y funcionara
con la ultima configuracion que le habias puesto antes de desinstalarlo;
y purge ELIMINA la configuracion, 
de manera tal que si lo vuelves a instalar iniciara y funcionara 
con la configuracion que trae por defecto, la configuracion *de fabrica*.

> **NekoSushi said:**
> 
- Como es el tema de los virus?

No te afectan :)

> **NekoSushi said:**
> 
- Las opciones del Mouse no guarda mis preferencias

Que opciones?, que quieres hacer?

> **NekoSushi said:**
> 
- Lei por ahi, que luego de instalar los drivers de la grafica nVIDIA, tiene que aparecer su logo al iniciar el SO para saber que todo funciona bien,

No, no necesariamente.

:D

---

### Post by joseluis on 2011-04-26
hola, y bienvenida!
Yo no se mucho, pero tengo bastante tiempo por las filas de Ubuntu. 
Ante todo, lo que sería importante saber es qué maquina tenés. Porque quizás te convenga más Ubuntu en lugar que Lubuntu.
Yo uso Lubuntu en la biblioteca de mi trabajo. y sirve genial en maquinas muy viejitas, pero obviamente no busco efectos especiales.
Si buscás efectos especiales necesitás  tarjeta gráfica un tanto potente, integrada o no. Y si tenés eso, quizás debieras pensar en otra versión (Ubuntu).

En cuanto a los codex, te bajás el paquete desde Synaptic, que dice algo así como Extras Restringidos Ubuntu, o similar, no me acuerdo ahora como se dice en ingles, que te mete todo lo necesario para multimedia.

Reproductor de video, el que viene en Lubuntu, Gnome Player anda de 10! con esos codex.

Instalación y desintalación, por Sinaptic, y listo.

Suerte!! y contá como te fue

---

### Post by NekoSushi on 2011-04-26
Holis!

El problema que tenia con los discos era que uno de ellos no estaba montado, al querer montarlo daba un error, Buscando por ahi lei que usando la aplicacion MountManager Se solucionaba, y asi fue :biggrin:

El problema que tengo con el mouse es que lo configuro desde *Preferencias > Teclado y Raton* pero luego de presionar en aceptar reviso nuevamente y esta como antes (como si fuera "solo lectura")
Nose si es para configurarlo desde ahi, pero busco para no tener que hacer doble-clik tan rapido.

VLC. Hay alguna opcion que permita la relacion de aspecto libre? (que el tamaño del video se adapte a la ventana) esa opcion la tiene el Gnome Player, pero no guarda esa preferencia al salir de la aplicacion. Mas me cambie de Windows a Ubuntu por esta razon, Cuando reproducia videos y en escenas en donde habia mucho "movimiento" (nose como se llama eso) el uso del CPU aumentaba haciendo que el video se des-sincronice del audio.

Las caracteristicas de mi PC son
nVIDIA 6200 256mb
768mb RAM
Intel Celeron D 2.8Ghz

Probe anteriormente Ubuntu, y si funcionaban los efectos, pero al reproducir videos como que hacia una pausa cada 10s, no sabia (y aun no) mucho de de Linux/Ubuntu en esos dias, lo que me regrese a Windows. Nuevamente en mi cabeza el tema de Ubuntu, encontre Lubuntu, lo instale y me agrado, pero esto de que no me guarde las preferencias me vuelve loca. Es problema de configuracion o de Lubuntu? :confused:

Gracias!

---

### Post by joseluis on 2011-04-26
Con esa maquina, andá para ubuntu, sin dudarlo, para tener los efectos que quieras. Además tenés más soporte. Lubuntu está muy bueno, tiene soporte, pero es para maquinas mas reducidas en su potencial. Y no encontrarás mucha gente que lo use, por lo tanto, las preguntas muchas veces podrían quedar sin responder. En cambio, con Ubuntu,  es más fácil resolver algunas cosas.

---

### Post by ivanovnegro on 2011-04-26
> **joseluis said:**
> Con esa maquina, andá para ubuntu, sin dudarlo, para tener los efectos que quieras. Además tenés más soporte. Lubuntu está muy bueno, tiene soporte, pero es para maquinas mas reducidas en su potencial. Y no encontrarás mucha gente que lo use, por lo tanto, las preguntas muchas veces podrían quedar sin responder. En cambio, con Ubuntu,  es más fácil resolver algunas cosas.

En mi opinion está muy bien con Lubuntu, tengo otra máquina con iguales datos y no va de maravilla sobre todo no con efectos.
Lubuntu tiene casi el mismo soporte como Ubuntu porque es un derivado. No hay nada que temer.

---

### Post by ivanovnegro on 2011-04-26
> **NekoSushi said:**
> Holis!

El problema que tenia con los discos era que uno de ellos no estaba montado, al querer montarlo daba un error, Buscando por ahi lei que usando la aplicacion MountManager Se solucionaba, y asi fue :biggrin:

El problema que tengo con el mouse es que lo configuro desde *Preferencias > Teclado y Raton* pero luego de presionar en aceptar reviso nuevamente y esta como antes (como si fuera "solo lectura")
Nose si es para configurarlo desde ahi, pero busco para no tener que hacer doble-clik tan rapido.

VLC. Hay alguna opcion que permita la relacion de aspecto libre? (que el tamaño del video se adapte a la ventana) esa opcion la tiene el Gnome Player, pero no guarda esa preferencia al salir de la aplicacion. Mas me cambie de Windows a Ubuntu por esta razon, Cuando reproducia videos y en escenas en donde habia mucho "movimiento" (nose como se llama eso) el uso del CPU aumentaba haciendo que el video se des-sincronice del audio.

Las caracteristicas de mi PC son
nVIDIA 6200 256mb
768mb RAM
Intel Celeron D 2.8Ghz

Probe anteriormente Ubuntu, y si funcionaban los efectos, pero al reproducir videos como que hacia una pausa cada 10s, no sabia (y aun no) mucho de de Linux/Ubuntu en esos dias, lo que me regrese a Windows. Nuevamente en mi cabeza el tema de Ubuntu, encontre Lubuntu, lo instale y me agrado, pero esto de que no me guarde las preferencias me vuelve loca. Es problema de configuracion o de Lubuntu? :confused:

Gracias!

El problema es que el VLC tiene un montón de opciones, tienes que aplicar todos los cambios para que se guarden, eso a mí me pasa también muchas veces.

---

### Post by NekoSushi on 2011-04-26
Umm, creo que llegue tarde para ver las respuestas, Me cambie a Ubuntu, capas ahora que se "un poco mas" de Ubuntu no tenga problemas. Mi problema siempre fue el rendimiento, tengo un trauma :biggrin:

Bueno, creo que sera para mañana mi proximo post, ya que ahora esta actualizandose Ubuntu y descarga muuy lento.

Mañana o si no me duermo luego les cuento.

No quisiera terminar nuevamente en Windows :/

Gracias!

---

### Post by joseluis on 2011-04-27
Tranquila..a esta altura, y con todo lo que te moviste, dificilmente vuelvas a windows, esto es un viaje de ida, y las dificultades nos estimulan, porque al investigar, averiguar, y meter mano, uno se va metiendo mas en este mundo. Y ya no querrás salir.

---

### Post by Liv~ on 2011-04-27
> **joseluis said:**
> Tranquila..a esta altura, y con todo lo que te moviste, dificilmente vuelvas a windows, esto es un viaje de ida, y las dificultades nos estimulan, porque al investigar, averiguar, y meter mano, uno se va metiendo mas en este mundo. Y ya no querrás salir.

Definitivamente.
Yo tampoco hace mucho que hice el cambio y también tuve (y sigo teniendo) dudas, algunas logro resolverlas sola, otras necesito ayuda, otras siguen esperando ser resueltas... jaja. Quizás a los golpes, pero vas aprendiendo, y está bueno, más si te interesa el tema :)

---

### Post by NekoSushi on 2011-04-27
Holas!
En la noche se termino de actualizar el sistema, luego de reiniciar conecte los 2 discos de datos que tengo, y oh! sorpresa, error (el error se producia antes de llegar al escritorio). Como supuse que seria error de los discos lo deje para mañana (hoy). Luego de pelear unas horas logre que funcione bien.

Ahora en Ubuntu, El sistema funciona bien, con los efectos del compiz y demas, pero con el VLC hay veces que el video cuando hay "mucho movimiento" produce una pausa (como que se esta sincronizando con el audio). Alguna recomendacion? o sera problemas de codecs?

Grax! :biggrin:

---

### Post by NekoSushi on 2011-04-28
Yap.

Probando varios reproductores se soluciono el problema :mrgreen:
Por ahora no tengo problemas en encontrar programas similares que usaba en Windows.
Si hay problemas ya me veran por el foro otra vez :mrgreen:

Gracias!!

---

### Post by joseluis on 2011-04-29
que reproductor usaste por fin? sería bueno que comentes

---


---
title: "Problemas con consumo de RAM"
date: 2009-06-07
forum: Software
---

### Post by losoollenos on 2009-06-07
Hola buenas tardes a tod@s !!!!
Quisiera preguntar si alguien ya tuvo este problema y si se puede hacer algo al respecto.
Lo mísmo me pasa tanto en Herdy AMD 64 cuanto en Jaunty AMD64: el consumo re RAM va aumentando a medida que corran los minutos, sin aplicaciones corriendo, nada más prendido el cpu y va escalando de a poco pero constantemente la demanda de RAM. Las otras noches dejé encendido a propósito el cpu y a la mañana marcaba 1.5 gb !!!!
Será algun problema de hardware?

Gracias por vuestra atención

---

### Post by losoollenos on 2009-06-07
Perdón, olvidaba dejar esto, el problema parece ser "gnome-panel" ??

En este momento marca 1.1 GIB.............

---

### Post by juancarlospaco on 2009-06-07
No, Linux usa diferente la RAM que Windows, 
depende como lo mires, tiende siempre a llenar la RAM, mas alla de cuanta tengas.

Crea Buffers i/o de dispocitivos lentos, como los discos rigidos, para funcionar mas rapido,
bajo demanda, toda esa ram se libera instantaneamente, pero si esta ociosa le da utilidad.
[I]
salu2[/I]

---

### Post by guillermolisi on 2009-06-07
> **losoollenos said:**
> Perdón, olvidaba dejar esto, el problema parece ser "gnome-panel" ??

En este momento marca 1.1 GIB.............
Si queres monitorear que aplicacion /servicio esta consumiendo mas RAM, usa "htop" y ordena la salida por consumo de RAM.

---

### Post by losoollenos on 2009-06-07
> **juancarlospaco said:**
> No, Linux usa diferente la RAM que Windows, 
depende como lo mires, tiende siempre a llenar la RAM, mas alla de cuanta tengas.

Crea Buffers i/o de dispocitivos lentos, como los discos rigidos, para funcionar mas rapido,
bajo demanda, toda esa ram se libera instantaneamente, pero si esta ociosa le da utilidad.
[I]
salu2[/I]

Y por que no me pasa usando 32 Bit ?

---

### Post by losoollenos on 2009-06-07
> **guillermolisi said:**
> Si queres monitorear que aplicacion /servicio esta consumiendo mas RAM, usa "htop" y ordena la salida por consumo de RAM.

Gracias, pero es normal o no este consumo, estaría mal metiéndome si hago lo que me decís?

---

### Post by Hei Ku on 2009-06-07
Postea la salida de poner top en la consola. Principalmente lo que esta en la parte superior. Eso nos va a dar una mejor idea de qué es cache y qué es consumo real.

---

### Post by guillermolisi on 2009-06-07
> **losoollenos said:**
> Gracias, pero es normal o no este consumo, estaría mal metiéndome si hago lo que me decís?
Para poder decirte si es normal o no necesitaria algo mas de informacion detallada sobre que procesos tenes corriendo, caracteristicas de tu maquina, carga del equipo (load), detalle del consumo de RAM en Kernel/SO, cache, usuario/programas y alguna otra cosa mas.

El asunto es que si un programa esta "descontrolado" y a raiz de eso consume mucha memoria, entonces es algo anormalmente normal. Se entiende a que me refiero ?

No entiendo a que te referis con lo de "estaria mal metiendome si hago lo que me decis ?".

---

### Post by losoollenos on 2009-06-07
> **Hei Ku said:**
> Postea la salida de poner top en la consola. Principalmente lo que esta en la parte superior. Eso nos va a dar una mejor idea de qué es cache y qué es consumo real.

Esto tengo.........

---

### Post by losoollenos on 2009-06-07
> **guillermolisi said:**
> Para poder decirte si es normal o no necesitaria algo mas de informacion detallada sobre que procesos tenes corriendo, caracteristicas de tu maquina, carga del equipo (load), detalle del consumo de RAM en Kernel/SO, cache, usuario/programas y alguna otra cosa mas.

El asunto es que si un programa esta "descontrolado" y a raiz de eso consume mucha memoria, entonces es algo anormalmente normal. Se entiende a que me refiero ?

No entiendo a que te referis con lo de "estaria mal metiendome si hago lo que me decis ?".

Amd 5200 64x2, 2 gib de ram, disco de 500, video on board de 128 nvidia 6100, mother ecs.
Me refería a que si por ejemplo algun programa está con algun conflicto y la bajamos la demanda de ram,no estamos arreglando el problema, si?

Garcias

---

### Post by guillermolisi on 2009-06-07
> **losoollenos said:**
> Esto tengo.........
No veo que ningun proceso consuma mas memoria que la considerada normal para cada uno. Son todos valores razonablemente bajos.

Ademas, hay una buena cantidad de memoria libre que se aprovecha como cache y buffers (casi medio Gb RAM para swap cache) del sistema con lo cual le respuesta ante lecturas en el disco rigido deberia ser muy buena ya que hay grandes posibilidades de contar sectores pertinentes (a esa busqueda) en memoria. (no es necesario acceder al disco rigido nuevamente).

El criterio de aplicacion es: mientras tengas RAM que no demandes, se usara toda la posible para mejorar la respuesta del sistema tomandola para buffers y cache. Toda memoria que no se use, efectivamente libre y ociosa, es dinero a la basura porque ya la pagaste y no la aprovechas.

---

### Post by losoollenos on 2009-06-07
Bueno me pone muy contento que así sea !!!
Un usuario normal como yo tiende a pensar que una alta ocupación de Ram perjudica la fluidez del sistema, jeje.
Como es algo por todos lados criticado del w vista y w en general, que para optimizar sus funcionamientos conviene liberar ram, es más o menos una preconcepción que se va instalando.

Ok muchas gracias

---

### Post by guillermolisi on 2009-06-07
> **losoollenos said:**
> Bueno me pone muy contento que así sea !!!
Un usuario normal como yo tiende a pensar que una alta ocupación de Ram perjudica la fluidez del sistema, jeje.
Como es algo por todos lados criticado del w vista y w en general, que para optimizar sus funcionamientos conviene liberar ram, es más o menos una preconcepción que se va instalando.

Ok muchas gracias
Ese es otro tema que tiene que ver con la administracion de memoria que cada programa hace.

Uno de los vicios mas criticados en Windows es la pesima politica de administracion de memoria que hacen muchos de sus programas, sean del SO o accesorios, ocupando espacios fragmentados inultimente, como si fuera basura que el programa ha dejado, y que, por alguna razon, quedan ahi hasta que se reinicie el sistema.

---

### Post by josecuervo86 on 2009-06-07
Esto me hace acordar algo....

---

### Post by dirty fingers on 2009-06-07
jaja ese nautilus tiene todo un record

---

### Post by josecuervo86 on 2009-06-07
De una, no vi nada parecido en toda la Googlosfera (?)

---

### Post by losoollenos on 2009-06-07
La duda que me queda es por que se va incrementando el uso de la ram y no se mantenga en algun rango. También me gustaría saber por que esto no me pasa en Ubuntu 32 bit....

---

### Post by Hei Ku on 2009-06-07
Ese Nautilius me parece que esta un poco fuera de rango. Por el resto, mi maquina llega a tomar casi los 4GB de RAM completos, pero los libera cuando es necesario.
Cuando tenía 2GB los tenía casi siempre a tope. Lo importante es que no tengas nada de la particion swap en uso.

---

### Post by staar on 2009-06-07
es así, mi pc también usa toda la memoria fisica todo el tiempo (760 Mb de 768 Mb totales) y no toca la swap (eso se puede cambiar), y cero dramas, cuando algún programa la necesita, se libera al toque...

saludos

---

### Post by sdennie on 2009-06-07
Si no estas tocando al swap, no hay ningun problema.  Fijate con:

```

free -m

```

Debes tener algo asi:

```

             total       used       free     shared    buffers     cached
Mem:          4052       1718       2333          0         63       1314
-/+ buffers/cache:        [COLOR="Red"]340[/COLOR]       3712
Swap:         5726          [COLOR="Red"]0[/COLOR]       5726

```

Los numeros de rojo son los importantes.  Si los dos estan bastante chicos (son de megabytes), todo bien.

Tambien, hay un par de "kernel tunables" para manejar esas cosas.  Por ejemplo, si queres echar el cache (que no es recomendable si no estas haciendo benchmarks) podes usar:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Tambien, linux tiene una cosa que se llama "swappiness".  Es decir el nivel de consumo de RAM donde el kernel empienza a bajar cosas a swap.  Por defecto, es 60.  Por lo que veo, es un numero bastante abstracto pero podes ponerlo desde 0 a 100.  0 significa no usa swap hasta que la maquina no tiene mas memoria y 100 es mas parecido a Windows (que siempre esta usando swap).  Para cambiarlo, usa:

```

sudo sh -c "echo 'vm.swappiness = SWAPPINESS_QUE_QUERES_USAR' >> /etc/sysctl.conf
sudo sysctl -p

```

Para verificar que funciono:

```

cat /proc/sys/vm/swappiness

```

---

### Post by josecuervo86 on 2009-06-07
Si los numeros rojos tienen que estar bajos, los mios estan al reves :P

---

### Post by sdennie on 2009-06-07
> **josecuervo86 said:**
> Si los numeros rojos tienen que estar bajos, los mios estan al reves :P

Bueno, siempre depende como usas la maquina.  Vos tenes 3G (en realidad seguro que tenes 4G pero estas usando Ubuntu 32bit sin un kernel con PAE asi que solo podes usar 3.2G) y no estas usando swap.  1.2G de RAM usado no es tan malo si tenes aplicaciones pesados abiertos.  Como Lisi dijo, fijate con htop a ver si hay una applicacion que esta volviendo loco con la memoria sin razon.

---

### Post by josecuervo86 on 2009-06-07
> **sdennie said:**
> Bueno, siempre depende como usas la maquina.  Vos tenes 3G (en realidad seguro que tenes 4G pero estas usando Ubuntu 32bit sin un kernel con PAE asi que solo podes usar 3.2G) y no estas usando swap.  1.2G de RAM usado no es tan malo si tenes aplicaciones pesados abiertos.  Como Lisi dijo, fijate con htop a ver si hay una applicacion que esta volviendo loco con la memoria sin razon.

Todo acertado, menos lo de 32 bits, uso 64 bits pero no me reconoce los 4G. Igual ese es otro asunto y tendria que compilar el kernel para que me los reconozca (lo digo por que la BIOS y Hardware lsiter me reconocen los 4G) pero como acabo de decir ese es otro tema (tratado en un thread específico)

Aca va la imagen de htop (no entendi nada de lo que aparecia :D)

Ahh, y solo tengo abierto firefox :S

---

### Post by sdennie on 2009-06-07
> **josecuervo86 said:**
> Todo acertado, menos lo de 32 bits, uso 64 bits pero no me reconoce los 4G. Igual ese es otro asunto y tendria que compilar el kernel para que me los reconozca (lo digo por que la BIOS y Hardware lsiter me reconocen los 4G) pero como acabo de decir ese es otro tema (tratado en un thread específico)

Aca va la imagen de htop (no entendi nada de lo que aparecia :D)

Ahh, y solo tengo abierto firefox :S

64bit siempre va a usar mas memoria que 32bit pero, eso parece un poco extremo.  Si queres abrir un thread sobre 4G de RAM, hacelo.  Si hablas ingles, fijate aca primero: [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by josecuervo86 on 2009-06-07
Lo voy a consultar shaun. Por el tema de los 4G de Ram ya abrí un post y tuve un kernel panic jeje. Voy a probar de vuelta con el link que me diste a ver si puedo habilitar PAE (que no lo pude encontrar cuando compile :P). Despues comento en el post viejo que tal me fue ;)

Este es el post viejo: [http://ubuntuforums.org/showthread.php?t=1115454]("http://ubuntuforums.org/showthread.php?t=1115454")

---

### Post by losoollenos on 2009-06-08
Bueno de curioso paso los pantallazos de la pc de mis chicos, tiene mother Msi p35, placa de video nvidia 8600 gt 256 ddr3, 2 gib de ram. Sin abrir programas se mantiene en alrededor de los 250/260 de ram. Entonces ésta anda mal por no "ocupar" los recursos?
Como dijo Guillermo me está derrochando la guita !!!! jejeje

Saludos

---

### Post by losoollenos on 2009-06-08
Perdón por insistir pero creo que tiene que haber algun problema.

Hoy por ejemplo quedó mi pc prendida desde la mañana, cuando vine al mediodía no pude ejecutar nada, sólo aparecía esto:

"Falló al bifurcar (fork) (No se puede asignar memoria)"

Lo mísmo me apareció ahora a la noche cuando llegué a casa, no responde ningun intento de abrir ni consola ni el monitor o cualquier aplicación, siempre sale el "Falló al bifurcar (fork) (No se puede asignar memoria)"
Tuve que reiniciar, esto es lo único que si funcionó, el botón de apagar.
El único dato que pude conseguir es el del screenlet de Ram que estaba en el 63%.
Espero que se pueda solucionar.......

Saludos y muchas gracias !!!!

---

### Post by Hei Ku on 2009-06-09
Hace poco hubo alguien que tenía problemas con el Nautilius, similares a lo tuyo. 

Podes probar de desactivar los previews y scripts que tengas puestos en el Nautilius? No es normal que un solo programa consuma tanto, salvo que estes haciendo alguna cosa muy loca.

---

### Post by josecuervo86 on 2009-06-09
Estoy ahi arriba Hei... era yo :D

---

### Post by guillermolisi on 2009-06-09
> **losoollenos said:**
> Bueno de curioso paso los pantallazos de la pc de mis chicos, tiene mother Msi p35, placa de video nvidia 8600 gt 256 ddr3, 2 gib de ram. Sin abrir programas se mantiene en alrededor de los 250/260 de ram. Entonces ésta anda mal por no "ocupar" los recursos?
Como dijo Guillermo me está derrochando la guita !!!! jejeje

Saludos
Esa situacion se da casualmente porque no se ha generado necesidad de cargar contenido en el cache / buffers en memoria solamente porque la maquina no se ha usado, al menos es lo que entiendo esta sucediendo.

Que pasa si la usas un dia entero y tomas las misma mediciones al final del dia ?

---

### Post by losoollenos on 2009-06-09
> **guillermolisi said:**
> Esa situacion se da casualmente porque no se ha generado necesidad de cargar contenido en el cache / buffers en memoria solamente porque la maquina no se ha usado, al menos es lo que entiendo esta sucediendo.

Que pasa si la usas un dia entero y tomas las misma mediciones al final del dia ?

Lo que te puedo decir es que después de usarla un rato navegando, escuchando mp3, abrir algun correo pps y no mucho más se queda en alrededor de los 320/330, no se me sigue disparando la ram.

Tenés alguna idea por dónde puede venir el error que comenté más arriba 
"Falló al bifurcar (fork) (No se puede asignar memoria)" ?

Muchas gracias

---

### Post by Hei Ku on 2009-06-09
Eso es que llenó la memoria RAM y llenó la swap. Un leak de memoria extremadamente feo.

---

### Post by sdennie on 2009-06-09
> **guillermolisi said:**
> Esa situacion se da casualmente porque no se ha generado necesidad de cargar contenido en el cache / buffers en memoria solamente porque la maquina no se ha usado, al menos es lo que entiendo esta sucediendo.

Que pasa si la usas un dia entero y tomas las misma mediciones al final del dia ?

Exactamente.  Tambien, podes usar preload y/o readahead para forzar cosas al cache antes de que las usas.  Preload es super facil:

```

sudo apt-get install preload

```

Despues de un par de dias, preload va a entender lo que haces con la maquina y trata de siempre mantener las cosas mas utiles en el cache.  Readahead es un poco mas dificil a armar pero, aca tenes una guia en ingles: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by losoollenos on 2009-06-09
Ya estoy instalando "preload"....

---

### Post by losoollenos on 2009-06-11
Bueno quería comentar que solucioné este problema desactivando tres o cuatro screenlets, principalmente creo que el problemático era el "WallpaperClock", este yo había comentado en otro post que me tiraba unos pantallazos marrones a cada rato.
Ahora anda bien, ayer la dejé descargando unas pelis con Transmission toda la noche; se mantuvo en 315 mb de ram + o - desde la noche hasta el otro día, un relojito !!! jeje

Saludos y muchas gracias a tod@s

---

### Post by staar on 2009-06-12
sería bueno que reportes el bug (o por lo menos le avises) al creador, es un fallo grave ese che, puede j*****e algo importante a alguien...

saludos

---

### Post by losoollenos on 2009-06-12
Lo haría con gusto pero no estoy seguro (so&#314;o sospecho, más o menos como del padre grassi jajaja) cual es el del problema.....sí podría volver a probar de a uno con tiempo y ver.
Tampoco podría dar mucha más información de la que apareció en el post ni sabría cómo reportar el bug, en todo caso voy a tratar de informarle al creador y si me dicen que información más técnica sería bueno reportar y cómo obtenerla se la paso.

Saludos

---


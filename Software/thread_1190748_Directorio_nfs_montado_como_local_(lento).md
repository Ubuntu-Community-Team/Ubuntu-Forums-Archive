---
title: "Directorio nfs montado como local (lento)"
date: 2009-06-18
forum: Software
---

### Post by electronpositivo on 2009-06-18
Hola!

Les planteo un reto que tengo. En una red con 20 ordenadores, hago un montaje de un directorio puesto en el servidor en cada ordenador:

mount 192.168.1.200:/home /home/users

De manera que los directorios personales de cada usuario se monta desde el servidor y se conecten desde el ordenador que sea siempre tengan todo igual (el mismo escritorio, ficheros...).

El problema viene cuando una gran parte de los ordenadores están accediendo, haciendo el funcionamiento bastante lento. Mi reto es que los usuarios no noten que el sistema se ralentiza por este motivo.

¿Se les ocurre alguna posibilidad o planteamiento distinto para que la velocidad sea más alta?

Espero haya quedado claro mi reto

Gracias por su tiempo

---

### Post by dirty fingers on 2009-06-18
No me da la cuenta un numero lindo. Si es una red de 100Mb/s (lo mas común) estas jodido.

Esto es un trabajo que estas haciendo para alguna empresa ?

---

### Post by electronpositivo on 2009-06-18
La red es de 100, efectivamente. Lo tengo montado en un instituto de secundaria.

Si no recuerdo mal, en windows con los perfiles móviles, cada vez que el usuario inicia sesión se copia automáticamente su perfil del servidor al equipo local y al finalizar la sesión se actualizan los cambios en el servidor, con lo que el trabajo durante la sesión es bastante rápido (pese al inconveniente de tener que esperar unos segundos al principio y al final de la sesión).

El inconveniente que tengo ahora es que estoy trabajando directamente en el servidor y esto hace que ubuntu parezca más lento que windows (os podéis imaginar los comentarios de los chavales...).

¿Cómo puedo mejorar esto? No sé si el planteamiento que me he hecho de montar el directorio del servidor directamente es el más adecuado para lograr lo que quiero.

Gracias por atenderme

---

### Post by guillermolisi on 2009-06-18
La red tiene un hub (si es que aun existen tales equipos) o un switch ?

La maquina que posee el recurso exportado corre Ubuntu server u otra version ?

Esa maquina esta dedicada a tal efecto o es de un usuario mas ?

Coincido en la apreciacion respecto del ancho de banda.

Si las PCs estan en una red de 100mbps entonces el acceso a la maquina que posee el recurso exportado deberia estar en una troncal de 1Gbps para no tener cuello de botella en los accesos concurrentes.

---

### Post by electronpositivo on 2009-06-18
Los tengo conectados mediante switch, ubuntu server totalmente dedicado.

No es viable (por presupuesto) montar la red con 1Gbps, por eso el planteamiento lo estoy haciendo por software.

Simplemente, con que se sincronizara automáticamente el directorio local del usuario que iniciara sesión con el directorio que existe en el servidor pienso que sería suficiente... es lo que se me ocurre.

¿Cómo lo veis?

---

### Post by dirty fingers on 2009-06-18
ummmm quizas si montas un proxy de cache en cada terminal para amortizar los cambios de información transitorios y tambien asignas distinta prioridad de acceso al servidor para evitar la saturación de pedidos podría andar. 
igual jajaja te veo mal mal , no me cierra la idea.

---

### Post by electronpositivo on 2009-06-18
Lo del proxy cache no se me había ocurrido. Aunque lo veo un poco rebuscado, investigaré al respecto. Muchas gracias.

¿Más ideas?

---

### Post by guillermolisi on 2009-06-18
> **dirty fingers said:**
> ummmm quizas si montas un proxy de cache en cada terminal para amortizar los cambios de información transitorios y tambien asignas distinta prioridad de acceso al servidor para evitar la saturación de pedidos podría andar. 
igual jajaja te veo mal mal , no me cierra la idea.
El problema de usar un proxy con cache es que el usuario efectuara los cambios en ese lugar y no en el destino real (el server NFS). Si se interrumpe la red, hay colisiones, se corta la luz, etc, y justo esta editando un archivo lo mas probable es que quede corrupto e inservible.

La red NO debe ser toda de 1Gb sino solamente el tramo que conecta el server con el resto de las maquinas. Con que tengas una boca de 1Gb en el switch es suficiente.

---

### Post by matuu! on 2009-06-18
> **electronpositivo said:**
> 
¿Se les ocurre alguna posibilidad o planteamiento distinto para que la velocidad sea más alta?


Hay una posibilidad, quizás rozando la locura, pero posible.. Podés utilizar dos placas en el server y un switch que soporte port trunking (en switch administrables), y asi "doblar" la velocidad. 

En linux existe una caracteristica llamada bonding, que hace que dos placas tengan el mismo IP, proporcionandote más ancho de banda y balanceo de carga y redundancia (si falla una, sigue solo la otra totalmente tranparente para el usuario). Aparte, creo que no necesitas soporte en el switch ;)

No he tenido tiempo de ponerme con esto, pero la idea es muy llamativa. 
Te dejo algunos link para que veas.
[http://www.ubuntu-es.org/?q=node/68774](http://www.ubuntu-es.org/?q=node/68774)   /*acá te da una ejemplo de como hacerlo*/
[http://www.overclockers.cl/foros/index.php?showtopic=103023](http://www.overclockers.cl/foros/index.php?showtopic=103023)

Bueno che, espero te sirva.
Suerte!

---

### Post by biale on 2009-06-19
Y yo tambien coincido con la apreciación del ancho de banda, y agrego la necesidad de un servidor que se la banque (SCSIs, etc, etc).

No es el mismo caso de los perfiles obligados o móviles de W. ya que supuestamente se trata de un un mecanismo optimizado por diseño. Así y todo cuando lo implemente aparecieron los problemas de ancho de banda y servidor. Válido a nivel de prototipo pero poco mantenible bajo condiciones reales de funcionamiento.

Mi idea sería montar solo un pedazo del home, lo estrictamente necesario ¿/home/Documentos?. Algo que solo impacte en el momento de browse - leer - guardar. Y que además no cuelgue a la máquina completa por dependencias con la red.

Si pretendes perfiles obligados, habría que evaluar otras alternativas. Si pretendes perfiles moviles, es un tema. Quizas (o sea: no lo se) sea posible considerar alguna idea proveniente de los conceptos de "tiny client"

Mucha suerte, saludos a todos.

---

### Post by electronpositivo on 2009-06-23
Os agradezco las ideas que me estáis proponiendo. El caso es que olvidé comentaros algo:

[LIST]
[*]Tenemos otros 20 ordenadores formando una red en otro edificio.
[*]Las 2 redes se comunican a través de 2 routers wifi (WRT54GS).
[*]El server está cableado en una de las redes y a la otra va por wifi.
[/LIST]


Teniendo esto en cuenta, os comento:

Dirty Fingers - Proxy-cache: La idea sería instalar Squid en cada cliente (cada cliente sería servidor de sí mismo), ¿correcto? Si no fuera por el problema que comenta guillermolisi, lo intentaría, pero me parece que podría ser bastante fastidioso.

guillermolisi - Switch 1Gbps: El mayor problema que le veo a esto es el de la wifi, me parece que no quedaría solucionado con esto.

matuu! - Bonding: Esto parece muy interesante y lo probaré para optimizar la lectura/escritura, aunque el tema de la wifi me parece que tampoco lo soluciona.

biale - /home/Documentos: Si lo hago de esta manera, cuando un usuario se loguee en otro cliente, no tendrá las preferencias del escritorio, marcadores de firefox... tal y como lo tenía en el otro cliente, ¿cierto?. Esto es lo que pretendo evitar y tengo en mente desde el principio. Aunque si no hay más remedio, lo tendría que hacer tal y como comentas. No sé qué quieres decir con lo del tiny client (he googleado y no he encontrado nada aclaratorio).

Teniendo en cuenta la nueva variable que os he comentado al principio (la wifi), ¿se os ocurre algo más?

Gracias de nuevo por estrujaros el cerebro para echarme una mano

---

### Post by guillermolisi on 2009-06-23
> **electronpositivo said:**
> Os agradezco las ideas que me estáis proponiendo. El caso es que olvidé comentaros algo:

[LIST]
[*]Tenemos otros 20 ordenadores formando una red en otro edificio.
[*]Las 2 redes se comunican a través de 2 routers wifi (WRT54GS).
[*]El server está cableado en una de las redes y a la otra va por wifi.
[/LIST]


Teniendo esto en cuenta, os comento:

Dirty Fingers - Proxy-cache: La idea sería instalar Squid en cada cliente (cada cliente sería servidor de sí mismo), ¿correcto? Si no fuera por el problema que comenta guillermolisi, lo intentaría, pero me parece que podría ser bastante fastidioso.

guillermolisi - Switch 1Gbps: El mayor problema que le veo a esto es el de la wifi, me parece que no quedaría solucionado con esto.

matuu! - Bonding: Esto parece muy interesante y lo probaré para optimizar la lectura/escritura, aunque el tema de la wifi me parece que tampoco lo soluciona.

biale - /home/Documentos: Si lo hago de esta manera, cuando un usuario se loguee en otro cliente, no tendrá las preferencias del escritorio, marcadores de firefox... tal y como lo tenía en el otro cliente, ¿cierto?. Esto es lo que pretendo evitar y tengo en mente desde el principio. Aunque si no hay más remedio, lo tendría que hacer tal y como comentas. No sé qué quieres decir con lo del tiny client (he googleado y no he encontrado nada aclaratorio).

Teniendo en cuenta la nueva variable que os he comentado al principio (la wifi), ¿se os ocurre algo más?

Gracias de nuevo por estrujaros el cerebro para echarme una mano
Squid debe tener una sola instancia en un solo server. De nada sirve tener mas de una a menos que seas un proveedor de servicios de Internet y tu trafico sea extremadamente grende (ahi tendrias variso servidores, no uno solo, de cara a Internet).

Si en el otro edificio tienen otra red inalambrica entonces deberias conectar ambos switches, el de un edificio y el del otro, a 1Gb.
Luego, el router WiFi en el otro edificio conectado a una de las bocas del switch a 100mbps.

De esta forma tendrias los clientes accediendo simultaneamente a un backbone de 1Gb pero indivualmente a 100Mb. De esa forma no tendrias cuellos de botella entre una red y las demas (considerando Internet otra de las redes).

---

### Post by biale on 2009-06-24
Me reintegro al foro. ..

¿“Tiny Client”? Basicamente lo que quise decir es que la actividad en el home de cada usuario es mucho mayor de la que parece, que los directorios y archivos ocultos se modifican muchisimo. Llamese configuraciones de Firefox como lo comentaste (incluyendo cache e histórico), sesiones de Nautilus, los .png, etc, etc. Si el simple screenlet medidor de CPU también almacena cada tanto los datos que va mostrando en .xsession<algo>!

Con “tiny client” quise significar cualquier esquema que permite obtener una estación de trabajo  alivianada y obteniendo lo que necesita desde un servidor. No te digo que implementes “EyeOS”, peró si que le pegues un vistazo como para ver los rumbos de la tecnológía.

Solo algo que encontré muy rápidamente y en forma inesperada: “As with many other such products, the thin client uses Microsoft's Remote Desktop Protocol (RDP) to connect to a hosted Windows XP session...” Jamás lo hubiera pensado asi.

Una posibilidad que se me acaba de ocurrir es copiar desde el servidor solo los archivos de configuración necesarios y modificados (¿grsync?) al arrancar la sesión de usuario. Para luego reponer las modificaciones al servidor cuando se cierra la sesión.

Saludos!

---

### Post by guillermolisi on 2009-09-24
> ¿Cómo se puede hacer esto? Lo plantée hace un tiempo en otro post y al final lo di por imposible: [http://ubuntuforums.org/showthread.php?t=1053946](http://ubuntuforums.org/showthread.php?t=1053946)

Sería la opción ideal!

Movido al [thread original]("http://ubuntuforums.org/showthread.php?t=1053946") ya que para este estaba OT.

---

### Post by gmunioz on 2009-09-24
Hola ele.....:

Puede que lo que necesites sea: rsync

rsync es una herramienta que permite sincronizar remotamente

ordenadores. Es útil para realizar copias incrementales de datos.

si un directorio (carpeta) mide 3 GB y queremos almacenarla en 

otro ordenador, sólo la primera vez los 3 GB serán transferidos, 

luego sólo se transferirán los pequeños cambios que haya entre el

servidor principal donde están los datos y los ordenadores donde 

se hayan hecho los cambios.

Puedes dar permisos de solo lectura a las configuraciones, para

que permanezcan inmodificables y permitir solo la actualización

de los datos que consideres se deben actualizar.

---

### Post by electronpositivo on 2009-09-24
> **gmunioz said:**
> Hola ele.....:

Puede que lo que necesites sea: rsync

rsync es una herramienta que permite sincronizar remotamente
ordenadores. Es útil para realizar copias incrementales de datos.
si un directorio (carpeta) mide 3 GB y queremos almacenarla en 
otro ordenador, sólo la primera vez los 3 GB serán transferidos, 
luego sólo se transferirán los pequeños cambios que haya entre el
servidor principal donde están los datos y los ordenadores donde 
se hayan hecho los cambios.
Puedes dar permisos de solo lectura a las configuraciones, para
que permanezcan inmodificables y permitir solo la actualización
de los datos que consideres se deben actualizar.

El rsync sería una opción muy interesante si solamente sincronizara el directorio del usuario que se está logueando tanto al entrar como al salir... ¿se puede hacer esto? ¡Sería ideal!

---

### Post by Hei Ku on 2009-09-24
Se pueden poner scripts al inicio y a la salida. El único problema en estos casos es cuando se les corta la luz a la mitad y no salen como corresponde.

---

### Post by gmunioz on 2009-09-24
Hola ele....:

En este sitio tienes un tutorial y algunos scripts interesantes:

[http://www.mexicoextremo.com.mx/content/view/31/62/](http://www.mexicoextremo.com.mx/content/view/31/62/)

---

### Post by electronpositivo on 2009-09-24
gmunioz: He leido el manual de rsync con los scripts de ejemplo, pero me faltan algunas cosas.

Hei Ku: Dices que se puede programar al inicio y a la salida, pero no me queda claro si te refieres a cada vez que un usuario se [loguea]/[sale de su sesión] o al sistema.

Lo interesante sería rsync al inicio/salida de la sesión de cada usuario. Hace tiempo lo di por imposible, ¿se puede?

---

### Post by Hei Ku on 2009-09-24
Sí, me refería al inicio/salida de sesión. Se puede.

---

### Post by electronpositivo on 2009-09-24
> **Hei Ku said:**
> Sí, me refería al inicio/salida de sesión. Se puede.

OK. Pues entonces perfecto. ¿Serías tan amable de indicarme cómo? [-o<

---

### Post by Hei Ku on 2009-09-24
Fijate en /etc/gdm/PostSession/Default

Eso es para sesiones de gnome, y ejecutaría para todos lo mismo. Para el inicio, fijate que debe haber un PreSession

---

### Post by electronpositivo on 2009-09-24
> **Hei Ku said:**
> Fijate en /etc/gdm/PostSession/Default

Eso es para sesiones de gnome, y ejecutaría para todos lo mismo. Para el inicio, fijate que debe haber un PreSession

Qué bueno! =D> ¿Cómo es que no respondiste hace tiempo al [post en el que lo preguntaba]("http://ubuntuforums.org/showthread.php?t=1053946")?

---

### Post by Hei Ku on 2009-09-24
Ja. En esa epoca estaba tan tapado de trabajo que gracias si podía pasar por casa cada tanto. :lolflag:

Ademas que no es mi area de experiencia, solo sabía que se podía hacer.

---

### Post by electronpositivo on 2009-10-05
> **Hei Ku said:**
> Ja. En esa epoca estaba tan tapado de trabajo que gracias si podía pasar por casa cada tanto. :lolflag:

Ademas que no es mi area de experiencia, solo sabía que se podía hacer.

:lolflag:

Abusando de vuestra sabiduría... ¿sabéis si esto es posible también con kdm?

---


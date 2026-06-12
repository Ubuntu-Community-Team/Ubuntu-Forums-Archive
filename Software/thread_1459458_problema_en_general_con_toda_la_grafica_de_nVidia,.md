---
title: "problema en general con toda la grafica de nVidia, ventanas y escritorio en Mint"
date: 2010-04-21
forum: Software
---

### Post by pcman1 on 2010-04-21
[FONT=Comic Sans MS]Hola Amigos de Ubuntu, les Saluda un amigo que ha tenido varios problemas con la Distro de Linux, Linux Mint 8 Helena, les detallo mi problema:

** primero tengo una torre o Computador algo Viejito ya , es un pentium 4 con 1 giga de ram , y tarjeta nVidia FX4400, el disco duro esta particionado en 4, para linux mint ,para el Grub2,para datos y para windows xp,

**Los problemas comenzaron con la configuracion de la pantalla y de la tarjeta grafica, iniciaba con la configuracion por defecto del software de nvidia , yo le cambiaba la resolucion de 1024x768 a 1280x1024, y cuando la queria guardar la configuracion ,no lo hacia, y aparecia este error: " Failed to parse existing X config file '/etc/X11/xorg.conf'! " , busque por la red y fui probando alguna soluciones posibles, pero no me resultaban.

**dejé ese problema sin arreglar por un momento, y me puse a modificar el Grub2 con un programa que instale, el administrador de arranque, y le hice algunos cambios, como que inicie como predeterminado el windows, el tiempo de espera sea de solo 5 segundos y lo ultimo que hice fue aumentar la resolucion del inicio del grub a 1024x768 ,antes estaba en 640x480 creo, y esto me causo un problema con el inicio de linux mint, no me reconocia la tarjeta grafica, por lo que iniciaba sin la tarjeta grafica, disminui la resolución del grub2 y creo que la deje como estaba , y no me funcionaba esto, volvia a iniciarse sin la tarjeta grafica y sin poder restaurar configuraciones anteriores de la tarjeta grafica, por lo que debia iniciar sin la tarjeta.
Estas soluciones no funcionaban,por lo que hice algo que no haria en Windows, borrar todos lo que hay en Home o Sistema de Archivos ,algo que lei para que se restaurase a su configuracion inicial, asi que lo hice... aca hablan algo al respecto ( [http://www.ubuntu-es.org/?q=node/58144#comment-151746](http://www.ubuntu-es.org/?q=node/58144#comment-151746) ) , creo que no me significo nada raro , yo borre todos las configuraciones que estaban fuera de las carpetas, los que parecen documentos de textos.

**Supuse que debia restaurar la configuracion inicial del Grub2 , lo hice con una serie de comandos,algo como sudo update...etc...etc y lo dejo como estaba y ahi se inicio con normalidad linux con la tarjeta grafica, volvi a experimentar con el problema de la configuracion de la tarjeta grafica , pero todavia no tenia solucion hasta que hice algo que encontre en algun foro, y lo hice:

1. Cambiar nombre a xorg.conf, en mi caso lo cambié a xorg.conf.old
2. Ejecutar nvidia-settings como superusuario: $ sudo nvidia-settings
3. Clikar en "Save X Configuration File"
4. En el cuadro de diálogo clickear en Show preview...
5. Copiar el texto del preview
6. ir a /etc/X11/ y *crear archivo xorg.conf y pegar en él el contenido del preview anterior, guardar los cambios y listo.
( Fuente : [http://www.ubuntu-es.org/?q=node/117128](http://www.ubuntu-es.org/?q=node/117128) )

Y me arreglo el problema de no guardar la configuracion de resolucion de mi tarjeta grafica, por lo menos algo ya habia resultado bien...  : )

** Luego actualice la mayoria de las versiones de los paquetes de linux con el "administrador de paquetes de linux" los que se podian y habian versiones nuevas, y esto me provoco que de las normales 5 entradas en el grub; (iniciar linux creo 2.6.31-14, linux 2.6.31-14 recovery mode,memory test, memory test console y windows Xp) ,paso a creo 7 entradas y le agrego linux 2.6.31-20 y linux 2.6.31-20 recovery mode.... Esto significa que si continuo actualizando esto me apareceran nuevas entradas en el grub2???...... como podria modificar esto??

** Y ahora un problema adicional que me ha aparecido que creo que es por la tarjeta grafica o por el famoso Xconf , es que el terminal me aparece totalmente blanco. No se ve ningún texto. Todos los marcos de los cuadros de diálogo de, por ejemplo, el Synaptic se ven invisibles, o cuando debe confirmarse algo con mi clave tambien me sale en blanco...tambien desaparecieron los marcos de las ventanas (donde están los botones para cerrar, maximizar y restaurarlas).... ha quedado bastante raro esto, quizas esto sucedio por problemas de la tarjeta nVidia o por que yo he tratado de modificar la apariencia de linux, pero que no he hecho mucho, en la apariencia o en el compiz config...en el cual ahora se demora en bastante en cambiar los detalles o no lo hace, y si quisiera instalar un nuevo tema , no se puede ya que linux me manda un error :

"Este tema no se mostrara como se pretende porque el motor de temas GTK+ necesario " ubuntulooks " no esta instalado"

y sigue sin aparecerme los marcos de las ventanas o el terminal normal ...todo en blanco....  que puedo hacer???

Para que me aparescan las ventanas momentaneamente escribo esto en el terminal :
"
metacity --replace

"
y lo hace pero cuando cierro el terminal este no se cierra, y se queda pegado el sistema...por lo que aplico  Ctrl +Alt + Backscape e inicio de nuevo mi sesion....



*****  Si lo sé ....son muchas dudas ,pero veremos si tienen alguna solucion

Saludos desde Concepcion Chile.

Y desde luego Gracias de Antemano  : )
[/FONT]

---

### Post by moreback on 2010-04-24
- Puedes eliminar los kernels viejos desintalando con Synaptic los paquetes linux-image-2.5.xx-yy que no estés usando. Te recomiendo dejar los dos últimos que tienen mayor número de revisión (el número que viene después del guión).

- Lo de metacity --replace ejecútalo mejor con Alt+F2 y después vas a** Sistema -> Preferencias -> Aplicaciones al inicio**, te metes en la pestaña **Opciones** y pulsas el botón "**Recordar las aplicaciones ejecutándose actualmente**".

---

### Post by pcman1 on 2010-04-26
Gracias por molestarte en responder, intentare eso que me dices de borrar la actualizacion mas antigua, respecto a la apariencia , el problema radica que escribo  [FONT=Comic Sans MS]metacity --replace  y se me ven bien las ventanas , pero si me voy a centro de control ....apariencia, .....pestaña efectos visuales, me aparece que no tiene Ninguno, esto significa que cuando cierro ventanas y las abro lo hace sin ningun tipo de efectos visuales, que es algo que caracteriza a linux....

es una pena....sigo buscando alguna solucion,...respecto a los drivers de la tarjeta m dice que tiene la version privativa de estos, quizas es ese el problema...


saludos y nuevamente gracias por responder

Saludos
[/FONT]

---


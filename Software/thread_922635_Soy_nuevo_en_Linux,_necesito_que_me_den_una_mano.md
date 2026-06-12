---
title: "Soy nuevo en Linux, necesito que me den una mano"
date: 2008-09-17
forum: Software
---

### Post by blankopirata on 2008-09-17
Hola muchachos, la verdad que siemrpe use windows, de hecho nunca vi una pc con linux. Pero vi algunos videos y fotos y me gusto y me interesa aprender cosas nuevas. Bueno aca mis preguntas:
(Antes que nada aclaro que soy bastante bruto hasta para formatear e instalar windows)
1. Me baje el ISO de Ubuntu 8.04 y puse la imagen en un CD, ahora mi duda es: ¿boteo e instalo como si cuando instalo un windows? en mi caso tengo Discos C y D, instalaría en el C: (donde esta windows) y me lo cambiaria por windows, **¿los datos del D no se pierden verdad?**
2. Todos los programas que tengo hechos backup en un DVD q son por ejemplo en .rar o la musica en .mp3 o las pelis en .avi o el curriculum ^^ en .doc **¿Van a dejar de servirme?**
3. Los drivers que me trajo la compu osea los cds originales de los drivers **¿me sirven?**
4. Todas esas cosas de Ubuntu que me llamaron la atencion por ejemplo "Compiz Fusion" se pueden instalar o es con otro ISO distinto al que baje?
5. He estado leyendo varias cosas para ver si me las arreglaba solo y vi que hay mucho de comandos en la "terminal" (es la 1ra vez que escucho de eso) ¿es imprescindible usarla verdad? ¿es facil de usarla?

Bueno creo que son mis mayores miedos...
Desde ya les agradezco la ayuda que me puedan dar.
Saludos, quiero ser uno mas en Ubuntu!!

---

### Post by santiagoward2000 on 2008-09-17
BIENVENIDO!
Con respecto a la primera pregunta, si bajaste el CD que se llama "DesktopCD", cuando bootees vas a poder entrar a Ubuntu sin tener que instalarlo. Ahí vas a poder probar todo lo que quieras, y cuando te sientas cómodo podés instalarlo directamente desde ahí. Hay un instalador bastante simpático, que no necesita mucho conocimiento. Sobre el disco D, ahí vas a tener que fijarte bien. En el instalador te pregunta cómo querés que se formatee el disco. Si no elegís que te borre todo va a quedar tu disco D. Es más, si querés podés cambiar el tamaño de alguna sin tener que borrar Windows, cosa de poder entrar al sistema que quieras cuando prendés la máquina.
Acerca de la seguna pregunta, no. Vas a tener que instalar algunos paquetes para que anden, pero no va a haber problema. Instalás **ubuntu-restricted-extras** y vas a tener todo eso (si después necesitás ayuda para instalarlo avisá). Para instalar paquetes se bajan directamente de los repositorios de Ubuntu, y desde un programa que se llama **Synaptic**, lo único que tenés que hacer es buscarlo y decirle que lo instale.
Con el tema de los drivers, no te sirven (seguramente son todos para Windows) y no te van a hacer falta. Ubuntu tiene drivers para casi todo ya instalados, y algunos que se instalan bastante fácil (como para las placas de video). Ahí puede que tengas algún problema con algún modem o placa de red. Si te pasa, contanos que hardware tenés para ver si te podemos ayudar.
Compiz Fusion viene instalado de fábrica desde Ubuntu 7.10. Una vez que instales los drivers de tu placa de video tendría que andar. Después para configurarlo vas a tener que instalar **compizconfig-settings-manager**, como para activar el cubo y demás cosas.
Sobre la terminal, normalmente no es impresindible, casi siempre hay algún programa gráfico para hacer lo que quieras hacer. Igual, en mi caso, le terminé agarrando el gustito, es mucho más cómoda para algunas cosas.
Como ya dije, si tenés alguna duda avisá.
SUERTE!

---

### Post by eldragon on 2008-09-17
> **blankopirata said:**
> 
1. Me baje el ISO de Ubuntu 8.04 y puse la imagen en un CD, ahora mi duda es: ¿boteo e instalo como si cuando instalo un windows? en mi caso tengo Discos C y D, instalaría en el C: (donde esta windows) y me lo cambiaria por windows, **¿los datos del D no se pierden verdad?**


primero a lo primero, deberias empezar a olvidar la distincion de particiones con letras de unidad, eso en linux no existe. en linux todo parte desde el directorio raiz ( / ), desde ahi se 'montan' todas las unidades. (y otras cosas, que no vienen al caso).

si queres instalar en el 'disco C' de windows, deberias de averiguar cual de los 2 es a la hora de utilizar el instalador de ubuntu. una manera facil de hacer esto es con el tamaño ;)

vas a tener que etrar a particionar manualmente. algo un tanto mas tedioso, y aparentenete.. por lo que decis, no te va a resultar muy facil que digamos. asi, que, segui leyendo abajo a ver si te gusta lo que propongo.

> 
2. Todos los programas que tengo hechos backup en un DVD q son por ejemplo en .rar o la musica en .mp3 o las pelis en .avi o el curriculum ^^ en .doc **¿Van a dejar de servirme?**


los programas no son compatibles. pero siempre hay alternativas que se acercan lo suficiente e incluso a veces superan a su contraparte de windows. sobre documentos, mp3, etcetera, salvo raras excepciones, no vas a tener problemas.

Como tenes todo backupeado (supongo que esto incluye a tu disco D), te recomendaria eliminar ambas particiones, y decirle a ubuntu que se encargue de todo. en linux no es tan importante separar datos del sistema operativo, porque el disco no se particiona como en windows. y te va a resultar mas facil instalar.

> 
3. Los drivers que me trajo la compu osea los cds originales de los drivers **¿me sirven?**


los cds con los drivers de tus dispositivos no son de mucha utilidad. por lo general, por suerte, todo anda sin necesidad de instalar ningun driver. pero para estar seguros de esto, deberiamos de saber que hardware tenes. cualquier otro driver, si existiese para linux, se baja gratuitamente de internet.


> 
4. Todas esas cosas de Ubuntu que me llamaron la atencion por ejemplo "Compiz Fusion" se pueden instalar o es con otro ISO distinto al que baje?

si, si tenes una tarj de video NVIDIA / ATI o INTEL. eso anda desde el vamos en ubuntu. se puede instalar de manera muy sensilla un app para configurar efectos mas avanzados (como los que probablemente hayas visto en youtube


> 
5. He estado leyendo varias cosas para ver si me las arreglaba solo y vi que hay mucho de comandos en la "terminal" (es la 1ra vez que escucho de eso) ¿es imprescindible usarla verdad? ¿es facil de usarla?


bueno eso de leer. al principio, la terminal parece algo feo y asusta. pero es mas facil para la gente del foro guiar por texto que por menues graficos. despues, si te convertis en un ávido usuario de linux, la vas a notar imprescindible, y vas a ver que no hay nada que no puedas hacerle a tu pc desde ella. muy, pero MUY recomendado acostumbrarse. no por ultima necesidad, sino por sus ventajas. una vez que logres manejar la terminal con moderada fluidez, vas a aprender mucho mas sobre como funciona el SO en general, y te va a ayudar a poder arreglartelas mas solo que ahora :D


> 
Bueno creo que son mis mayores miedos...
Desde ya les agradezco la ayuda que me puedan dar.
Saludos, quiero ser uno mas en Ubuntu!!


fijate, antes que nada. de hacer backups. y si seguis con miedos, hay algo que se llama WUBI install que se hace dentro de windows. no es lo ideal, pero se instala el SO como si fuera un programa mas, y cuando bootees lo podes probar. si lo rompes en el proceso, lo podes volver a instalar desde 'agregar o quitar programas' de windows. 

aca te doy una lista con las razones por las cuales yo no instalaria linux:

[LIST]
[*]uso muchos juegos 3d o de windows en general.
[*]adicto al MS office
[*]tengo un ipod nuevo y quiero usar itunes
[*]me encantan los virus / spyware / adware
[/LIST]

cualquier cosa chifla :D

---

### Post by blankopirata on 2008-09-17
Muchisisisimas gracias! No me puedo quejar, me han contestado todo :P bueno me mando nomas y despues les cuento si tengo algun problemita!

Gracias muchachos!

PD: Por el lado de las desventajas muchas gracias por informarmelas! pero = me convence, me lo llevo :P

---

### Post by sajnox on 2008-09-17
> **blankopirata said:**
> 
1. Me baje el ISO de Ubuntu 8.04 y puse la imagen en un CD, ahora mi duda es: ¿boteo e instalo como si cuando instalo un windows? en mi caso tengo Discos C y D, instalaría en el C: (donde esta windows) y me lo cambiaria por windows, **¿los datos del D no se pierden verdad?**

No, la instalacion no es como en windows. Como te comento Santiago es un Live CD. El sistema arranca desde el CD y se carga en memoria sin tocar tu disco rigido, de esta manera podes ver si el sistema reconoce todo tu hard.

No borres tu instalacion de windows, simplemente dale espacio a la particion donde lo tenes para que entre Ubuntu, con 10gb te alcanza. Cuando arrancas con el Live CD tenes un programa que se llama editor de particiones el cual es muy intuitivo y te permite redimensionar las particiones (ojo que no vas a encontrar el disco C: sino probablemente sda1=C y sda2= D)
De esta manera tenes la opcion cuando arranca la PC de elegir que sistema operativo vas a usar, esto te lo configura la instalacion no tenes que preocuparte demasiado...PERO LEE LA GUIA UBUNTU ([www.guia-ubuntu.org](www.guia-ubuntu.org))
> 2. Todos los programas que tengo hechos backup en un DVD q son por ejemplo en .rar o la musica en .mp3 o las pelis en .avi o el curriculum ^^ en .doc **¿Van a dejar de servirme?**

Los programas algunos te pueden servir y otros no, existe un programa que da soporte para que se carguen programas hechos para windows, pero no todos funcionan. Igual siempre recomendamos que busques alguna alternativa hecha para Linux (generalmente las hay) a usar un programa para windows por mas bueno que este sea. Los mp3 y los documentos de ofimatica los vas a poder abrir tranquilamente con el open office que viene incluido en la instalacion del sistema
> 3. Los drivers que me trajo la compu osea los cds originales de los drivers **¿me sirven?**

Salvo que tengas drivers para Linux no creo que sirvan demasiado, pero no los tires

> 4. Todas esas cosas de Ubuntu que me llamaron la atencion por ejemplo "Compiz Fusion" se pueden instalar o es con otro ISO distinto al que baje?

Depende de la placa de video que tengas y como se configura para que esto ande, si tenes una nvidia o una ati no vas a tener problemas. Primero instala el sistema y despues te avanzamos con este tema.

> 5. He estado leyendo varias cosas para ver si me las arreglaba solo y vi que hay mucho de comandos en la "terminal" (es la 1ra vez que escucho de eso) ¿es imprescindible usarla verdad? ¿es facil de usarla?

Lo que podes llegar a necesitar en un principio lo podes solucionar con aplicaciones graficas no te preocupes.

Contanos como te fue, tambien seria util que nos describas que hardware tenes

Saludos

---

### Post by blankopirata on 2008-09-17
Gracias por todas las respuestas.
Estoy viendo de tener todo bien hecho back y terminando de grabar las ultimas cositas para ya meterme sin temor a perder nada.
Con respecto a mi pc, es asi:
Intel Dual Core 2140 1.60GHz
1 GB Ram
HD 160GB
NVIDIA GeForce 7300 GT

Mmm nose que dato mas hara falta. Despues les cuento como me fue con la instalación.
Saludos!

---

### Post by santiagoward2000 on 2008-09-17
> **blankopirata said:**
> Gracias por todas las respuestas.
Estoy viendo de tener todo bien hecho back y terminando de grabar las ultimas cositas para ya meterme sin temor a perder nada.
Con respecto a mi pc, es asi:
Intel Dual Core 2140 1.60GHz
1 GB Ram
HD 160GB
NVIDIA GeForce 7300 GT

Mmm nose que dato mas hara falta. Despues les cuento como me fue con la instalación.
Saludos!

Eso tendría que andar sin problemas. Cualquier cosa, como dijo sajnox, probá el LiveCD a ver si anda todo antes de instalarlo.
Saludos

---

### Post by leo_rockway on 2008-09-17
Hola, blankopirata, bienvenido a la comunidad.

¿Tenés internets desde el live cd? Creo que es una de las cosas más importantes... es bastante incomodo usar Ubuntu sin internets.

Una cosa que podés hacer para que veamos detalladamente qué hardware tenés es ir a la terminal (Accesorios > Terminal creo que es... no uso Gnome así que no estoy seguro) y tirar el comando lspci, copiar lo que te devuelva y pegarlo acá. Que no te de miedo la terminal, una vez que te acostumbrás es muy buena (no es absolutamente necesario aprender a usarla mas si recomendable).

Una de las cosas más molestas de configurar suele ser la placa WiFi (pero nada que no se pueda solucionar). Si no tenés una placa WiFi quedate tranquilo, todo el resto del hard que mencionás anda sin problemas.

Cualquier problema que tengas recordá que Google es tu amigo, así como la guía Ubuntu. Si después de buscar no encontrás la respuesta que necesitás chiflá que acá siempre alguien te va a ayudar.

---

### Post by blankopirata on 2008-09-17
Hola! Bueno esto es lo que me tiro cuando le puse ese comando:

00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
04:04.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)


Por otro lado, ya lo instale de una formatie todo XD y bue aca me salto para instalar el driver de la placa de video pero no el de sonido, por lo tanto, lo busque y lo baje para linux es un archivo ".bz2" y ni idea de como instalarlo. Recien me percato de que también cambia todo eso xD ya no existe mas el ".exe" verdad? 
Agradezco sus respuestas.

---

### Post by pol666 on 2008-09-17
no, no existe el .exe , despues eso lo hablamos de wine pero otro tema.


los bz o gz despues de un tar son archivos comprimidos y empaquetados..
si te bajaste un driver es seguramente por que adentro tiene script o codigos y los tenes que instalar manualemente pero... No tenes sonido para nada? 

fijate en el mixer, que tengas altos los parlantes y trata de probar los sonidos es raro que no tengas audio

---

### Post by blankopirata on 2008-09-17
No nada de nada sonido che :(
El tema del video instale el controlador privativo algo asi, pero me da muy poca resolucion por lo tanto tampoco se como instalar bien el driver de video.
toy sin sonido y sin video :P espero tu respuesta.
Gracias por darme bola.
PD casi me olvido, estuve tratando de instalar bien el video con una guia q vi por ahi pero cuando puse unas cosas algo asi: "sudo aptitude install envyng-core envyng-gtk" me pedia el password del "sudo" si mal no entendi, pero no podia escribir osea apretaba y no salia nada :S

---

### Post by pol666 on 2008-09-17
lo de video es solucionable..Instala nvidia settings  desde el programa que se llama synaptic esta en sistema>administracion

ese va a ser tu gestor de paquetes. instala nvidia-settings, una vez instalado la cmabias desde ahi.

Otra cosa, cuando escribis un pass de sudo, lo escribis pero no aparece, cosa de seguridad, vos dale enter cuando lo terminas de escribir. Igual NO instales cosas que no sabes, no pongas envy ;)


lo de sonido, todavia no me cierra te tendria que andar, te fijaste en serio si todos los volumenes estan OK?. cualquier cosa reinicia y fijate si estan los sonidos al arranque...

---

### Post by blankopirata on 2008-09-17
Hola viejo, active eso del nvidiasettings, pero me tira un error cuando lo abro algo del xconfig

El sonido definitivamente no funca, me fije el volumen, reinicie a ver si algo pero nada..
Sigo sin sonido y sin video jaja me la quiero cortar  encima ahora nose q paso que se desconfiguro el teclado.
Gracias por la paciencia

---

### Post by pol666 on 2008-09-17
y que error hombre!?


lo del teclado capas por se reconfiguro el servidor grafico, cambialo de vuelta.

Los driver privativos estan instalados? 
anda a controlador de driver restringidos (en administracion) y activalos

---

### Post by blankopirata on 2008-09-17
Ya esta lo del sonido, estaba tildado Headphones jaja ahora nose como configurarlo para 5.1 pero bueno ya vere..
con respecto a lo de drivers privativos, ni bien puse ubuntu lo instale al de nvidia que me daba poca resolucion, pero despues lo saque y ahora en administracion no me la opcion de drivers privativos >S 
Perdon por mi bruteza...
PD como configuro de vuelta el servidor grafico

---

### Post by lega on 2008-09-17
por las dudas, nvidia settings llamalo desde la consola con sudo nvidia-settings cambia a la resolucion deseada aplica y guardá, si te dice que va a escribir el xorg ponele que si

---

### Post by pol666 on 2008-09-17
a ver no entendi muy bien que hiciste con los driver...Vos tenes quie ir a controladores de driver restringidos y activarlos. Nada mas, despues desde el nvidia-settings cambias la resolucion, es eso.

lo de 5.1 despues te digo, es muy facil ;)

---

### Post by blankopirata on 2008-09-17
Gracias por las ayudas muchachos, lo que paso es que en la desesperacion habia instalado y desinstalado como 50 veces de 20 maneras distintas por eso se me armo un quilombo en la pc, asique lo q hice fue formatear de nuevo y listo :P si total rcien empezaba, Asique ahora hago bien al pie de la letra eso. Cualquier cosa les aviso.
Saludos y Gracias!

---

### Post by blankopirata on 2008-09-17
Siii! ^^ Pudeee jeje ya tengo el video bien configuradito :P ahora si no es joderte mucho, como hago con lo del 5.1? y como pongo y/o configuro el compiz fusion?
Muchas graciasss cheee!

---

### Post by nemodot on 2008-09-17
Ubuntu viene con Compiz instalado, lo puedes activar luego de instalar los drivers de la placa de video como veo que ya hiciste. Desde Sistema->Preferencias->Apariencia->efectos visuales podes elegir entre tres tipos que usan compiz.

Lo que no viene con ubuntu es la pantalla para la configuración de compiz y el tray icon que puedes instalar con lo siguiente:

```
sudo apt-get install compizconfig-settings-manager fusion-icon

```

Luego lo configuras desde Sistema-> preferencias->"Configuración avanzada de los efectos de escritorio"

---

### Post by pol666 on 2008-09-17
jajaja esta bien asi se aprende ;) pero ahora si tenes un problema, googlea y fijate que siempre hay solucion  a los problemas :).. si no encontras nada en google aca estamos para ayudar...

btw..

Sonido 5.1:

Abris una terminal y pones sudo gedit /etc/pulse/daemon.conf

te va  a salir un archivo de texto con la configuracion del Pulseaudio (cliente de sonido)... anda a abajo del archivo y busca donde dice

> ;default-sample-channels = 2


cambialo por

> default-sample-channels = 6


Importante sacarle el ";" que te quede textualmente como lo puse.

Despues reinicia para que vuelva a cargar el daemon y listo. 

No te asustes si cuando inicias de vuelta no te suenan los otros parlantes, anda al mixer de sonido, y en preferencias tilda todas las casillas y levantalas todas (por que nunca se sabe cuales son en verdad ^^)

---

### Post by nemodot on 2008-09-17
Quiero seguir ayudando pero no me gusta frecuentar los foros. Como sé que un principiante ambicioso en linux generalmente solicita asesoramiento te dejo mi MSN por si queres ayuda en vivo y en directo:

[email]roasted.coffee.beans@hotmail.com[/email]

---

### Post by eldragon on 2008-09-17
> **nemodot said:**
> Quiero seguir ayudando pero no me gusta frecuentar los foros. Como sé que un principiante ambicioso en linux generalmente solicita asesoramiento te dejo mi MSN por si queres ayuda en vivo y en directo:

[email]roasted.coffee.beans@hotmail.com[/email]

no es para ser desconfiado, pero ojo con gente que de consejos fuera de foros publicos si no los conoces. especialmente si no estas seguro de lo que te hace hacer. 

si decidis hacer esto...antes de ejecutar cualquier comando confirma con google. o el foro. para verificar mejor.


sobre el password prompt no escribiendo nada, es normal... tan solo escribi y dale enter :D

---

### Post by pol666 on 2008-09-17
por favor, en una comunidad de software libre nadie le va a decir algo para hacerle daño como.. e**jecuta sudo rm / -r** NO LO HAGAS xD en serio, NO.

bueno... como deciamos, respecto al compiz, hacele caso a nemodot que esta bien, te dejo mi blog ahi deje una guia para personalizar Ubuntu

[http://tuxear.wordpress.com]("http://tuxear.wordpress.com")

(esta en paginas anteriores...)

---

### Post by eldragon on 2008-09-17
> **pol666 said:**
> por favor, en una comunidad de software libre nadie le va a decir algo para hacerle daño como.. e**jecuta sudo rm / -r** NO LO HAGAS xD en serio, NO.

bueno... como deciamos, respecto al compiz, hacele caso a nemodot que esta bien, te dejo mi blog ahi deje una guia para personalizar Ubuntu

[http://tuxear.wordpress.com]("http://tuxear.wordpress.com")

(esta en paginas anteriores...)

no, no digo nada sobre el usuario que se ofrece y da su mail...pero es de buena practica no confiar ciegamente en desconocidos...yo por lo menos no lo haria....

---

### Post by santiagoward2000 on 2008-09-17
> **pol666 said:**
> por favor, en una comunidad de software libre nadie le va a decir algo para hacerle daño como.. e**jecuta sudo rm / -r** NO LO HAGAS xD en serio, NO.

Yo vi eso TANTAS veces en los foros en inglés... Acá no pasa, pero por las dudas no es mala idea buscar en Google qué es cada comando antes de usarlo.

---

### Post by blankopirata on 2008-09-17
Mil gracias!!! Ya me estoy manejando mas o menos bien, metiendo mano pero ahora con mas cuidado jaja.
Muchisimas gracias pol666 por tenerme tanta paciencia, si necesito algo te agrego entonces.
Gracias eldragon por preocuparte!
Muchas gracias!

---

### Post by eldragon on 2008-09-18
> **blankopirata said:**
> Mil gracias!!! Ya me estoy manejando mas o menos bien, metiendo mano pero ahora con mas cuidado jaja.
Muchisimas gracias pol666 por tenerme tanta paciencia, si necesito algo te agrego entonces.
Gracias eldragon por preocuparte!
Muchas gracias!

me alegra poder ayudar.... ahora solo por curiosidad...si tenes algo de tiempo, contanos como llegaste a ubuntu, o linux en general? que te decidio probarlo...etcetera.... :popcorn:

---

### Post by nemodot on 2008-09-19
Jaja, esta bien, puedes desconfiar, es saludable. Iba a sugerir eso del sudo rm para que nunca lo hicieras por que te borra el directorio principal del sistema y kaputt

---

### Post by WanderingKnight on 2008-09-19
> Iba a sugerir eso del sudo rm para que nunca lo hicieras por que te borra el directorio principal del sistema y kaputt

Te borra TODO, incluídos todos los archivos de cualquier partición que tengas montada, no solo el sistema.

---

### Post by pol666 on 2008-09-19
mira, te explico vos ves ese comando como algo destructivo, pero es una sintaxis nomas, 

sudo rm -rf /

Sudo: permisos de administrador, lo tenes que usar cada vez que hagas algo en el sistema

rm: comando para borrar

-r: recursivo f: SIn preguntas

/: es la raiz del sistema ahi esta TODO.

[IMG]http://1.bp.blogspot.com/_7c760YbgrE4/SKbTwysZsII/AAAAAAAACa8/E4-9xzsVe1I/s400/whoops.png[/IMG]


jajaj la desvirtue un poco. Saludos


Edit: No, no lo hagas ^^

---

### Post by santiagoward2000 on 2008-09-19
> **WanderingKnight said:**
> Te borra TODO, incluídos todos los archivos de cualquier partición que tengas montada, no solo el sistema.

Pero no mató al gatito! :lolflag:
[http://www.youtube.com/watch?v=wWOjmvWPRvQ]("http://www.youtube.com/watch?v=wWOjmvWPRvQ")

---


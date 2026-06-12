---
title: "Instalar 10.04 con Win7 y otros SOs en multiple boot"
date: 2010-05-02
forum: Software
---

### Post by rhoemers on 2010-05-02
> **santiagoward2000 said:**
> Hola!
El GRUB tendría que detectarte el Vista y Ubuntu sin problemas (en teoría). A mí en mi laptop me dio problemas para arrancar el Dell MediaDirect, entonces tuve que quedarme con el arrancador del Vista. Lo que tenés que hacer es, cuando te pide si querés instalar el GRUB, tocar el botón donde dice **Avanzado...** e instalarlo en la misma partición que instalaste Ubuntu. Cuando reinicies, te va a entrar al Vista sin preguntar.
Entonces instalá el [EasyBCD]("http://neosmart.net/dl.php?id=1"), y elegís para que te aparezca Ubuntu en el arranque del Vista. Acá te dejo una guía más detallada (tiene fotitos!):
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
Está en inglés, pero es bastante simple. Si tenés algún problema avisá!
Suerte!

_EDIT:_
Igual aclaro que al Vista podía entrar sin ningún problema con el GRUB, así que si no tenés alguna otra cosa rara instalada, no haría falta que te compliques la vida con el EasyBCD.

Ante todo buenas noches, bueno veo que ya ha pasado poco mas de un año que discutian este post, tengo un par de dudas que espero me sepan poder ayudar , acabo de bajarme el nuevo ubuntu (10.4), pero antes de instalarlo he de decir que tengo una pc con 3 S.O (win7 , xp y server 2003) cada uno en una partición ademas de tener un par de particiones mas (una de datos y la ultima sin formato en donde pienso instalar el ubuntu), bueno asi kmo estoy tengo un arranque dual que lo logre usando el EasyBCD ya que tenia instalado xp y win 7 y al final instale el server2003 , con el easybcd  fue muy facil agregar la entrada para el win 7 ya que sin este solo me figuraban el xp y server2003 , bueno veo que este sw tmbn tiene opcion para agregarle una entrada de alguna distribucion de linux , por ello mi duda es como me recomendarian instalar el ubuntu ya que veo han cambiado un par de cosas desde la vez que lo tuve instalado (hace un par de años) como que ahora usa grub 2 y antes solo usaba xp y server 2003 por lo que el grub me hacia el arranque dual sin mayores problemas.

Pero ahora , con el nuevo arranque del win 7 veo que seria hacer una especia de "triple arranque" y recurro a ustedes a que me orienten:

1) si como he leido aki seria factible instalar el ubuntu 10.4 sin el grub, asi entro a mis S.O microsoft y usando el EasyBCD le agrego la correspondiente entrada de linux y asi en una misma pantalla asumo tendria mis 4 opciones de S.O.

2) O, instalo normalmente el ubuntu creando mis 3 particiones( /, swap y /home) en esa particion libre que destine inicialemente  y asigno el grub2 a mi particion de ubuntu , como lo hice en la epoca que usaba ubuntu y no me generaba mayores problemas al arrancar alguien a probado si me hace el "triple boteo" haciendolo de esta manera o quizas aya algun problema??

Mcuhas gracias por su tiempo y por las respuestas que puedan brindarme anteriormente.

PD:  el enlace a la guia que puso el usuario santiagoward2000 veo que ya no esta funcionando asi que de sugerirme la primera opcion espero me guien de como hacerlo ya que me da un poco de temor el instalar el nuevo ubuntu x ello ademas de tambien tener muchas ganas por ya probarlo ya que estoy en una nueva maquina..:)

---

### Post by santiagoward2000 on 2010-05-02
Bienvenido rhoemers!
Personalmente nunca probé tener tantos sistemas juntos, pero me imagino que grub no tendría problemas en manejarlo. Simplemente instalá Ubuntu en la partición sin formato, revisá que durante la instalación encuentre los 3 sistemas y no tendrías que tener ningún problema.
También se puede usar EasyBCD, pero la versión 2, ya que a partir de Ubuntu 9.10 se actualizó a grub2, y este no es soportado por EasyBCD 1. Para bajar esta versión (que todavía está en beta) tenés que ir a este foro:
[http://neosmart.net/forums/showthread.php?t=642]("http://neosmart.net/forums/showthread.php?t=642")
y registrarte (re molesto, no?).
Si te decidís a instalarlo de esta manera y el link con la guía sigue caído, avisá y trato de reescribir una guía acá. De todas maneras, en este caso creo que con grub vas a estar bien.
Saludos!

---

### Post by rhoemers on 2010-05-03
Gracias por la bienvenida y la tan rápida respuesta que me has proporcionado **santiagoward2000 **bueno por tu sugerencia procedere a intentar instalar ubuntu y vere si me detecta los sistemas operativos con que vengo trabajando, de no ser asi reinicio el equipo para detener la instalación no? hasta esa instancia no me afectaria aun en nada el detenerla cierto? y por otro lado , si ya me registre y baje el beta del EasyBDS (la Build 93) pues de no funcionar lo primero te agradeceria me indicases  como instalaria linux  y de que manera usaria este software para agregar correctamente mi entrada al arranque de linux [B]. 

[/B]Entonces tratare de averiguar si en caso de entrar al paso de que reconozcon los S.O de no hacerlo si reiniciar no me afecta en nada aun, antes de probar a instalar el ubuntu

Nuevamente te agradezco por tu tiempo y apoyo :D

---

### Post by santiagoward2000 on 2010-05-03
> **rhoemers said:**
> Gracias por la bienvenida y la tan rápida respuesta que me has proporcionado **santiagoward2000 **bueno por tu sugerencia procedere a intentar instalar ubuntu y vere si me detecta los sistemas operativos con que vengo trabajando, de no ser asi reinicio el equipo para detener la instalación no? hasta esa instancia no me afectaria aun en nada el detenerla cierto?

No es necesario reiniciar la máquina. Hasta ese punto lo único que se hace es completar datos, como nombre de usuario y zona horaria, y opciones de la instalación, pero no instala nada todavía. Solo haría falta que hagas click en salir. Pegate una vuelta por este post, que explica cómo se hace la instalación para el dual boot, te puede ayudar:
[http://www.backports.ubuntuforums.org/showthread.php?p=8038137]("http://www.backports.ubuntuforums.org/showthread.php?p=8038137")

> **rhoemers said:**
> y por otro lado , si ya me registre y baje el beta del EasyBDS (la Build 93) pues de no funcionar lo primero te agradeceria me indicases  como instalaria linux  y de que manera usaria este software para agregar correctamente mi entrada al arranque de linux [B]. 

[/B]Entonces tratare de averiguar si en caso de entrar al paso de que reconozcon los S.O de no hacerlo si reiniciar no me afecta en nada aun, antes de probar a instalar el ubuntu

Nuevamente te agradezco por tu tiempo y apoyo :D

En caso de que quieras hacerlo de esta manera, la instalación se lleva a cabo de casi la misma manera. En la pantalla que te deja particionar el disco, elegí **"Especificar particiones manualmente"** y anotá el nombre de la partición donde se va a instalar Ubuntu (lo vas a necesitar después).
En la pantalla final (antes de elegir instalar) hay que clickear sobre el botón **Advanced**. Eso abre una ventana como la siguiente:
[IMG]http://www.dedoimedo.com/images/computers_new_2/dual-ubuntu-bootloader.jpg[/IMG] Ahí revisá que la opción **"Install boot loader** esté activada, y en **"Device for boot loader installation"** seleccionás la partición donde instalaste Ubuntu.
Cuando reinicies la máquina al final, tendría que aparecer el arranque de Windows como lo tenés ahora, con solo los 3 Windows. Entrá al que tenga instalado EasyBCD. Lo abrís, vas a **"Add/Remove entries"**, ahí vas a la pestaña que dice **"Linux"** y tendrías que poder agregarlo sin problemas, como agregaste los otros.
**[COLOR="Red"]Por las dudas, te recomiendo hacer un backup de toda información importante que tengas[/COLOR]**, pero creo que no vas a tener problemas.
Espero que te sirva. Suerte!

_EDIT:_
Estuve leyendo acerca de un bug en la versión de grub que viene con Lucid que trae problemas para armar un dual-boot. Me imagino que aca puede traer problemas también. Si alguien tiene más información al respecto estaría bueno que comente, antes que trate de instalar Ubuntu.

---

### Post by rhoemers on 2010-05-04
Buenas noches, que bueno que entre a dar una ojeada antes de instalar, es mas estoy navegando desde el live cd de ubuntu en este momento ya me disponia a instalar, decidi entrar nuevamente haber si habia alguna novedad, y viendo tu comentario me puse a leer y veo q varios estan teniendo problema con su grub en esta nueva versión, segun leo no solo para reconocer otros S.O windows sino tambien incluso otras distribuciones linux, entonces creo que me esperare un poco mas haber que pasa :( a aguantarme las ganas nomas jeje.

Muchas gracias por la respuesta tan oportuna santiagoward2000.Saludos

---

### Post by rhoemers on 2010-05-04
Molestando nuevamente adjunto un par de capturas sobre la parte de información de mis discos duros, donde si me aparece que esta el arranque del win7.

[IMG]http://img15.imageshack.us/img15/2738/screenshotzq.png[/IMG]

[IMG]http://img402.imageshack.us/img402/791/screenshot1ov.png[/IMG]

---

### Post by santiagoward2000 on 2010-05-04
> **rhoemers said:**
> Molestando nuevamente adjunto un par de capturas sobre la parte de información de mis discos duros, donde si me aparece que esta el arranque del win7.

Bueno, eso parece estar bien, y por lo que comento Guille en el thread original:
> **guillermolisi said:**
> El bug del Grub para la 10.04 esta solucionado de origen para la version final, por esa razon demoraron algunas horas su lanzamiento el jueves 29 de Abril.

yo diría que es seguro proseguir con la instalación. Si te surge alguna otra duda, no tengas miedo de preguntar.
Suerte!!

_PS:_
Muchísimas gracias por la aclaración sobre el bug Guille! :D

---

### Post by rhoemers on 2010-05-05
Buenas noches, hace un par de horas instale el éxito el ubuntu 10.04 y pues no hubo problema alguno con el grub , este me reconoce todos mis demás S.O (Windows 7, XP y server 2003), asi que estoy feliz por ello, de aqui solo tendre alguna molestia supongo cuando me toque formatear un windows jeje, ahora despues de agregar unos repositorios e instalar uno que otro programa adicional acabo de instalar el driver de mi tarjeta de video(una ATi Radeon HD4800) con el que la instalacion fue exitosa pero no me sale la ventana de configuración , bueno agregare compiz y ver que efectos nuevos me encuentro asi que solo me queda agradecer a santiagoward2000 por su ayuda prestada y recién caigo en cuenta que estoy en el team argentino de la parte del foro jaja si note que eras argentino pero no sabia que estaba clasificada la web, bueno me despido y un fuerte abrazo!:p

---

### Post by santiagoward2000 on 2010-05-05
> **rhoemers said:**
> Buenas noches, hace un par de horas instale el éxito el ubuntu 10.04 y pues no hubo problema alguno con el grub , este me reconoce todos mis demás S.O (Windows 7, XP y server 2003), asi que estoy feliz por ello, de aqui solo tendre alguna molestia supongo cuando me toque formatear un windows jeje, ahora despues de agregar unos repositorios e instalar uno que otro programa adicional acabo de instalar el driver de mi tarjeta de video(una ATi Radeon HD4800) con el que la instalacion fue exitosa pero no me sale la ventana de configuración , bueno agregare compiz y ver que efectos nuevos me encuentro asi que solo me queda agradecer a santiagoward2000 por su ayuda prestada y recién caigo en cuenta que estoy en el team argentino de la parte del foro jaja si note que eras argentino pero no sabia que estaba clasificada la web, bueno me despido y un fuerte abrazo!:p

Me alegro que haya salido todo bien :D. Fue un placer ayudarte y espero seguir viéndote por acá.
Un saludo!

---

### Post by AliFX on 2010-05-05
Hola a todos,

     Yo he instalado primero Windows 7 y posteriormente Ubuntu 10.04 en mi computadora, pero al parecer soy el único que no ha logrado resolver el problema del GRUB y el MBR que a algunos se les ha presentado, en el menú aparece para seleccionar Windows 7, pero al hacerlo se reinicia la PC, es decir, el GRUB escribió en el MBR, así que no tengo modo de acceder a Windows, he intentado todos los métodos pero no logro que Windows arranque, hasta donde sé Ubuntu 10.04 trabaja con GRUB2, he intentado con utilidades como SuperGrub, pero nada, si recupero el arranque de WIndows pierdo el de Ubuntu y viceversa, si alguien puede ayudarme en éste caso, y hago énfasis en  que he intentado con todos los métodos posibles que sugieren en los foros, sin embargo no he tenido resultados satisfactorios.

   Gracias y saludos,

   Alí

---


---
title: "VirtualBox y WinXP"
date: 2007-09-15
forum: Software
---

### Post by matog on 2007-09-15
Hola gente. Estoy con Feisty amd64, y me puse a probar el virtualBox.

Configuro la mauqina virtual con el wizard que tiene por ahí, y me pongo a instalar el xp sp2.
Va todo sospechosamente bien hasta que, durante la copia de archivos (previa a la instalacion del xp) me dice que no puede copiar el d3dramp.dll.

Puedo omitir, reintentar o salir. Con volver a intentar no soluciono nada, sigue quedandose con ese problema. Omito y luego, durante el resto de la copia me tira problemas similares con otros archivos.

Obviamente, despues se cancela la instalaciónporque faltan archivos.

Alguno tuvo exito?

---

### Post by FlyerDie on 2007-09-15
Disculpa mi ignorancia, pero nunca trabaje con VirtuaBox... la copia de archivos que te referis es durante la instalacion en la pantalla AZUL de windows XP? la del comienzo de todo me refiero...
Ese CD de XP que utilizas estas seguro que funciona correctamente y que no tiene archivos corruptos? 
Tenes posibilidad de probarlo con una instalacion en VMWare?

Para descartar que sea problema del CD o de otra cosa.

---

### Post by LaHire on 2007-09-15
> **FlyerDie said:**
> Disculpa mi ignorancia, pero nunca trabaje con VirtuaBox... la copia de archivos que te referis es durante la instalacion en la pantalla AZUL de windows XP? la del comienzo de todo me refiero...
Ese CD de XP que utilizas estas seguro que funciona correctamente y que no tiene archivos corruptos? 
Tenes posibilidad de probarlo con una instalacion en VMWare?

Para descartar que sea problema del CD o de otra cosa.

Es muy probable que sea el cd

Aunq si fuera problema de virtualizacion...no te deberia dejar siquiera empezar a copiar archivos....creo yo, al menos.

---

### Post by matog on 2007-09-15
Si, es la pantalla azul del comienzo.
El CD funciona correctamente, hace unos días lo usé para instalar XP en otra maquina.
Voy a ver con el VMWare, el VirtualBox pintaba sencillo de usar, por eso lo tenia.
Veo que pasa y les comento!

Gracias!

---

### Post by sajnox on 2007-09-15
Hola, 

Yo tengo el XP corriendo sobre el virtualbox y me anda diez puntos. Si estas seguro que no es el CD (disculpa que insista pero suena a que es el CD), proba generando una iso del CD y usalo en la unidad de CD virtual, tenes esa opcion con el virtualbox

Saludos

---

### Post by matog on 2007-09-16
Ya está. Se instaló, con algún problemita pero al menos arranca.
La los discos de red, después de mucho "reiniciar", los tomó como corresponde.
El único problema es que no puedo hacer anda internet, por uno de los dll que no instaló (y después se negó a registrar), pero no importa, no lo quería para eso. No sigo porque es mas un tema de windows que de ubuntu.

Una sola observación: el XP anda mejor virtualizado que nativo!!! Un avión, corre muy muy bien. Estoy chocho!!!
Ahora voy por algún OS de Apple....

Saludos!

---

### Post by FlyerDie on 2007-09-16
mmm..ahora que te funciono, yo sacaria de la VirtualBox ACPI para esta virtual machine, ya que al menos en SUSE es una de las opciones para deshabilitar si tenes problemas con lectoras de CD (que seria un caso probable...) o con CDROMs.

---

### Post by jpmorelli on 2007-09-16
Si sirve como dato, yo también cargué un Windows XP SP2 en Virtualbox y no tuve ningun problema... hasta corría mejor que en otras máquinas reales, en serio !

---

### Post by cseljatib on 2007-09-17
hola por ahi,
tb he instalado VirtualBox, y luego winXP y M.office 2002, todo corre bien hasta ahora!!. Lo instale basicamente para poder usar MSN, se que en linux hay opciones, pero ninguna ofrece tener video-chat-talk en un solo programa.
Bueno, pero les escribo para hacerles una consulta:
Como puedo generar un acceso directo a WinXP desde ubuntu??, es decir, sin necesidad de abrir VirtualBox y click en 'start'.

alguna sugerencia?

gracias

---

### Post by matog on 2007-09-23
Al final, parece que era el CD (que instalandolo en una maquina real funciona bien). "Conseguí" una versión WinXP Unattended y se instaló en 20 minutos en la maquina virtual (con el otro estuvo 3 horas...)

Que barbaro funciona el VirtualBox!

---

### Post by vk-cdg on 2007-09-24
Que es mejor ¿Virtual Box o VM Ware? y por que? digamos, que razones/experiencias tiene cada uno?

---

### Post by FlyerDie on 2007-09-24
virtualbox tengo entendido que no esta soportando NAT, solamente Bridge...:(
La ventaja contra VMware es que es software libre virtualbox ;) el resto creo que es igual...

---

### Post by Mataca on 2007-09-25
Chicos, como me acabo de comprar una pc nuevita, con una gforce 76000gt quiero jugar a buenos juegos sin necesidad de tener una particion con guindow$. Sinceramente no me copa nada tener una particion Ntfs solo para jugar...

Es mejor usar Wine o Cedega que instalar Virtual Box? quiero saber con que aplicación obtengo mejor performance. Ya que estamos con este tema, me ayudan?

---

### Post by kowal on 2007-09-25
> **Mataca]Chicos, como me acabo de comprar una pc nuevita, con una gforce 76000gt quiero jugar a buenos juegos sin necesidad de tener una particion con guindow$. Sinceramente no me copa nada tener una particion Ntfs solo para jugar...
 
 Es mejor usar Wine o Cedega que instalar Virtual Box? quiero saber con que aplicación obtengo mejor performance. Ya que estamos con este tema, me ayudan?[/quote]

Wine/Cedega no es lo mismo que Virtual Box/VMware. 

Wine (Wine Is Not an Emulator) es un API que puede llegar a correr algunas aplicaciones nativas de Windows sin necesidad de instalar Windows. Muy pocos juegos 3D/DirectX pueden funcionar bajo Wine.
Cedega es una especie de fork de Wine, pero que es pago. Efectivamente, puede correr una gran gama de juegos 3D, aunque no esperes poder usar _todos_.
Virtual Box/VMware requieren de Windows. Sirven prácticamente poco y nada para 3D/DirectX/juegos de Windows. VMWare quizá tenga un poquito de ventaja, pero todavía está muy, MUY experimental ese tema en máquinas virtuales.

Yo te diría que si sos un jugón compulsivo, vayas haciendo espacio para un XP (o Vista cuando vayan saliendo los nuevos juegos). Pero no dejes de tener en cuenta que en Linux existen muchos juegos nativos y buenos (no solamente el frozen bubble, que dicho sea de paso es simple pero es un juegazo :P). Hay varios posts sobre juegos en Linux por acá y varios sitios que el amigo Google te va a saber mostrar.

[QUOTE=vk-cdg said:**
> Que es mejor ¿Virtual Box o VM Ware? y por que? digamos, que razones/experiencias tiene cada uno?

Lo mejor de VMware: mejor performance, más pulido, fácil configuración de red, vmware tools, etc. Lo malo es que es privativo.
Lo mejor de Virtual Box: Es código abierto, es libre, es un serio rival de VMware y va camino a superarlo.

Por ahora me quedo con VMware Player (es gratuito, pero cerrado). Eso si.. instalando las VMware tools.

Saludos!

---

### Post by Mataca on 2007-09-26
Alta respuesta Kowal, me abriste la mente =) Muchas gracias 

Desde mi humilde opinión y mi poco conocimiento opino que por otro lado se que hay muchos juegos buenos, pero a mi forma de ver ni se comparan con los que hay para guindow$. 
Quizá se deba a que la plataforma de Bill este mas "pulida" o "mejorada"  para los juegos (onda el uso del directx, que quizá sea una re maza) Eso no lo sé, pero estaría tener la opción para usar los mismos juegos con Ubuntu (no me importaria pagar por un juego, mientras que sean Open Source) que los que hay para Win.

Ojala los desarrolladores se fijen mas en nuestra comunidad y que los mismos juegos que desarrollan pa la gente de redmon, los hagan para que corran nativamente en gnu/linux.

---

### Post by vk-cdg on 2007-09-26
> **kowal said:**
> 
Lo mejor de VMware: mejor performance, más pulido, fácil configuración de red, vmware tools, etc. Lo malo es que es privativo.
Lo mejor de Virtual Box: Es código abierto, es libre, es un serio rival de VMware y va camino a superarlo.

Por ahora me quedo con VMware Player (es gratuito, pero cerrado). Eso si.. instalando las VMware tools.

Saludos!

Con el VMWare Player puero crear una máquina virtual? 
No lo vi en detalle pero me pareció que no se podía, que era solo para correr máquinas ya hechas.

---

### Post by kowal on 2007-09-26
> **Mataca said:**
> Alta respuesta Kowal, me abriste la mente =) Muchas gracias 

Desde mi humilde opinión y mi poco conocimiento opino que por otro lado se que hay muchos juegos buenos, pero a mi forma de ver ni se comparan con los que hay para guindow$. 
Quizá se deba a que la plataforma de Bill este mas "pulida" o "mejorada"  para los juegos (onda el uso del directx, que quizá sea una re maza) Eso no lo sé, pero estaría tener la opción para usar los mismos juegos con Ubuntu (no me importaria pagar por un juego, mientras que sean Open Source) que los que hay para Win.

Ojala los desarrolladores se fijen mas en nuestra comunidad y que los mismos juegos que desarrollan pa la gente de redmon, los hagan para que corran nativamente en gnu/linux.

La alternativa libre a DirectX/Direct3D es OpenGL (ver [http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL](http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL)). La gran ventaja de OpenGL es que es portable a Linux, Mac OS, Windows, etc. (no así Direct3D). Pero bueno, ya sabemos que los juegos mueven _mucha_ guita y siempre salen arreglos monetarios con las compañías de hard o con M$ (y el tema de la portabilidad les importa poco o nada).

[quote=vk-cdg]Con el VMWare Player puero crear una máquina virtual? 
No lo vi en detalle pero me pareció que no se podía, que era solo para correr máquinas ya hechas.[/quote]

Yo uso [www.easyvmx.com](www.easyvmx.com) que permite crear el archivo ".vmx" para poder correrlo en el Player. Después instalás un SO ahí (recomiendo utilizar un .ISO del SO como unidad de CD en la maq. virtual). Y por último buscás el ISO que anda dando vueltas por ahí con las VMware Tools ([acá](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html) hay un ejemplo en inglés).

Saludos

---

### Post by FlyerDie on 2007-09-26
> **kowal said:**
> 
Yo uso [www.easyvmx.com](www.easyvmx.com) que permite crear el archivo ".vmx" para poder correrlo en el Player.
Excelentisimo aporte...!!
no conocia esta herramienta, muy piola ;)

---

### Post by godzeus on 2007-09-28
Personalmente, prefiero Virtualbox, la version 1.5 esta muy buena. Ademas lei que hay que hacer un par de cosas para poder ejecutar las MV con VMPlayer.
Yo tengo un XP SP2 instalado, corriendo Visual Studio 2005 (probe Mono y no me convencio)y la verdad, anda excelente.

PD: "Particion NTFS" que es eso? LaCatrera(nombre de mi maquina) no conoce ese tipo de sistema de archivos.

PD: Perdon el Off-Topic, pero cada dia que pasa con Ubuntu, mas me alegro de haber borrado Billdow$ para siempre.

Saludos:)

---

### Post by carverri on 2008-09-19
Hola

He instalado Virtualbox y despues he intentado con varias versiones instalar winxp. aparentemnte todo va bien, pero cuando, durante la istalcion hace el primer arranque de windosw xp para seguir instalando, aparece una de las tipicas pantallas azules de error que detienen la maquina y no puedo continuar.

Es una lata, porque utilizo algun programa como RatDVD que aun no existen para Ubuntu y tengo que arrancar desde la otra particion.

Alguna idea?

---

### Post by faktorqm on 2008-09-20
Con respecto a la pregunta de Mataca, les recuerdo a todos que ni VirtualBox ni VMware aceleran graficamente, por mas placa de video que tengas. Por lo tanto, no solo no es lo mismo que WINE si no que si anduviese, tampoco lo haria bien. O sea, si no te anda en WINE, si o si necesitas levantar un windows ("fisico" si se quiere) para juegar. 
Casos como el del que necesita un programa en particular, Vbox o VMware es lo mejor. Salu2!

---

### Post by Patchiu on 2008-09-22
> **faktorqm said:**
> Con respecto a la pregunta de Mataca, les recuerdo a todos que ni VirtualBox ni VMware aceleran graficamente, por mas placa de video que tengas. Por lo tanto, no solo no es lo mismo que WINE si no que si anduviese, tampoco lo haria bien. O sea, si no te anda en WINE, si o si necesitas levantar un windows ("fisico" si se quiere) para juegar.
Esta es una de las GRANDES dudas que tengo...
Porque yo pensaba que haciendo esto iba a poder jugar a los juegos nuevos, por mas que ya sepa que tengo menos Ram que usando Windows como se debe. 

OFF TOPIC: Sinceramente.. rompe DEMASIADO ver como entre WINE, CROSSOVER, PLAYONLINUX y CEDEGA (la version demo porque no me da para pagar la full version y no se consigue) se te rien en la cara de como podes jugar juegos viejos y los nuevos juegos es IMPOSIBLE jugarlos....... a no ser que hagas una particion para Windows... ](*,)
No puedo hacen andar ni CRYSIS, ni RACE DRIVER GRID, ni LOST PLANET, ni BIO-SHOCK y unos cuantos mas...
Ubuntu es taaaan bueno y tan completo, que no necesito "emular Windows" para otra cosa que no sean juegos... y que no lo pueda hacer... da muuucha bronca... =(

Volviendo al topic..
Gracias por sacarme la duda. Ya que para lo unico que queria instalar un Win Virtual era para poder jugar a los juegos que no puedo hacer correr ni con Wine, ni la demo de cedega, ni con playonlinux, ni con crossover.
Salu2!

---


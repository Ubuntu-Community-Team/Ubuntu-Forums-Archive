---
title: "¿Cómo encender la computadora y que Ubuntu arranque por defecto?"
date: 2010-10-11
forum: Software
---

### Post by guillejcopello on 2010-10-11
Hola, soy nuevo en Ubuntu y tengo la siguiente necesidad:
Quiero que mi máquina arranque en Ubuntu por defecto luego de tocar el botón de encendido sin tener que elegir entre windows o Ubuntu. Habitualmente hay alguna distracción que hace que se me pase el tiempo para elegir entre uno y el otro y para cuando quiero darme cuenta ya estoy escuchando el maldito sonido de inicio de windows y eso es muy molesto.
Aclaración: Tengo instalado Ubuntu en el mismo disco que windows y uso ambos sistemas de manera compartida.

Gracias y saludos

Guille

---

### Post by alfplayer on 2010-10-11
Hola.

Te recomiendo buscar con Google algo simple como esto. Se puede hacer cambiando la variable *GRUB_DEFAULT* en el archivo */etc/default/grub*, y después actualizando el inicio con *update-grub*.

---

### Post by Rolo linux on 2010-10-11
Hola:

Puedes instalar desde el Centro de software de Ubuntu: **StartUp-Manager** (en español **Administrador de arranque**) y luego lo configuras para que la opción de sistema operativo por defecto sea Ubuntu, además del tiempo de espera por si quieres entrar en Windows. A mi me funcionó  bien cuando todavía tenía instalado XP.

Saludos.

---

### Post by matias_tati on 2010-10-12
Que raro como lo instalaste pq a mi me toma por defecto Ubuntu

---

### Post by chulelinux on 2010-10-12
Lo más fácil es utilizar como te señalan el administrador de arranque, pero también podés modificar la grub utilizando la terminal y siguiendo esta guía [http://www.guia-ubuntu.org/index.php?title=GRUB#Grub_2](http://www.guia-ubuntu.org/index.php?title=GRUB#Grub_2) 
slds

---

### Post by guillejcopello on 2010-10-28
[SIZE=2]Gracias por las sugerencias.
He instalado el **Administrador de arranque** y toqueteado las variables de [/SIZE]*[SIZE=2]GRUB_DEFAULT[/SIZE]*[SIZE=2] pero solo me permiten elegir las opciones de la segunda pantalla que aparece cuando enciendo la máquina.
La primer pantalla me dice:
Seleccione el sistema operativo con el que desea iniciar:
-Microsoft windows XP....
-Ubuntu

Acá por defecto el selector aparece marcando windows (si pasan 25 segundos entra solo en windows).
Luego de selecionar Ubuntu llego a la pantalla que sí puedo modificar con el Administrador de arranque o variando el GRUB_DEFAULT. Pero lo que yo quiero cambiar es el tema de la primer pantalla.

Si a alguien se le ocurre otra solución le agradecería me la comente.

Gracias

Guille[/SIZE]

---

### Post by alfplayer on 2010-11-01
Me pregunto cómo fueron instalados Windows y Ubuntu en dual-boot.

---

### Post by guillejcopello on 2010-11-01
Instalé Ubuntu 10.04LTS (versión Lucid Lynx) siguiendo las instrucciones del disco. Lo instalé compartido con Windows. Desde Ubuntu puedo entrar a Windows y ambos comparten el mismo espacio en el disco rígido. Uso Ubuntu sin necesitar tener el CD-ROM en la compactera.
No se si mi descripción satisface la pregunta pero, repito, soy nuevo en Ubuntu. 
Si pudieran guiarme para que les diera información más específica estaría buenísimo.
Gracias

Guille

---

### Post by guillermolisi on 2010-11-02
Instalaste dentro de Windows o en una particion libre del disco rigido ?

Cuando instalas dentro de Windows se utiliza un programa llamado Wubi.
Cuando instalas en una particion libre del disco rigido usas el programa que te muestra en que lugar del disco se instalara y ahi podes confirmar la propuesta o elegir una distitna (dependiendo del espacio libre que tengas y de tus conocimientos).

En el CD de instalacion vienen las dos alternativas.
La principal diferencia operativa para instalar de una u otra forma radica en haber iniciado la maquina con el CD o haber iniciado la maquina con Windows y, con este funcionando, poner el CD de Ubuntu para que aparezca una ventana proponiendote instalar Ubuntu dentro de Windows (Wubi).

---

### Post by guillejcopello on 2010-11-02
Instalé Ubuntu poniendo el CD con windows prendido y después tomé la opción de "instalar Ubuntu dentro de windows".
Espero que eso les diga algo.
 
Guille

---

### Post by guillermolisi on 2010-11-02
> **guillejcopello said:**
> Instalé Ubuntu poniendo el CD con windows prendido y después tomé la opción de "instalar Ubuntu dentro de windows".
Espero que eso les diga algo.
 
Guille
Nunca use Wubi pero hasta donde se, para que funcione Ubuntu tenes que iniciar si o si Windows porque con Wubi ejecutas Ubuntu como si fuera una aplicacion mas de Windows (por eso se habla de instalar Ubuntu "dentro" de Windows y por eso las soluciones via GRUB no resultaron).

---

### Post by guillejcopello on 2010-11-02
O sea que por la forma en que instalé Ubuntu mi problema no tendría una solución y la solución sería reinstalar Ubuntu por fuera de windows.
Gracias por sacarme la duda y por la buena onda.
Saludos

Guille

---

### Post by alfplayer on 2010-11-02
Lo que faltaría hacer es cambiar en windows dos cosas: la entrada que se carga por defecto (pasaría a ser Ubuntu), y disminuir el tiempo de 25 a un tiempo como por ejemplo 5 segundos (todo se puede hacer desde windows). No recuerdo cómo se logra. Se puede buscar en la web.

---

### Post by guillermolisi on 2010-11-02
> **guillejcopello said:**
> O sea que por la forma en que instalé Ubuntu mi problema no tendría una solución y la solución sería reinstalar Ubuntu por fuera de windows.
Gracias por sacarme la duda y por la buena onda.
Saludos

Guille
Entiendo que asi seria la forma para poder iniciar la PC solamente desde Ubuntu (y eventualmente hacer lo propio con Windows, pero en forma alternada y excluyente, no simultanea).

Tal vez quien tenga mas experiencia con Wubi pueda definir categoricamente el tema.

---

### Post by guillejcopello on 2010-11-02
Listo, solucionado. Como aconsejaron, le busqué la vuelta por windows.
En una página encontré las instrucciones para que Ubuntu inicie como sistema operativo por defecto habiendo sido instalado con Wubi dentro de windows.
1-Entrar a windows
2-Botón derecho sobre "Mi PC" (o la de Bill)
3-Entrar en "Propiedades"
4-Entrar en Avanzadas
5-Luego en "Opciones de Inicio y recuperación" (o algo por el estilo)
6-Después en Settings u Opciones
7-Hay aparece la opción de inicio por Windows o por Ubuntu. Y también se puede elegir el tiempo de espera.
8-Reiniciar
9-No hacer nada por que ya entra directo en Ubuntu
:biggrin:
Muchas gracias a todos

Guille

---

### Post by guillermolisi on 2010-11-02
Gracias vos por este aporte.

---

### Post by Pan0ramix on 2011-06-05
muchas gracias. era lo que necesitaba. Es asi, con Wubi instalar Ubuntu deja un Grub (pantalla de inicio) para seleccionar el SO de arranque. Bastante feíta por cierto. Siempre instalé Ubuntu con Wubi, pues todas las pc que tengo vienen con Windows de fábrica. Tambien busqué por mil lados, hasta encontré un WinGrub para personalizar el Grub, pero no le di mas importancia. Ahora voy a formatear nuevamente e instalar Win7 64 bits. Esto me deberá permitir instalar Lucid en 64 bits. Veremos. 
No se cómo es instalar en una partición ¿debería dejar una particion libre cuando instale Win7? Si es así preparo el fijo antes...
Ya probaré y vendré con comentarios de cómo me fue.

---

### Post by guillejcopello on 2011-06-05
Si vas instalar Lucid (Ubuntu 10.04 LTS) en una partición a parte te conviene hacerlo cuando instalás windows (o visceversa). En la del laburo quise instalar Lucid en una pc con una sola partición, toda para windows. Cuando quise pedirle al disco de Lucid que haga una partición propia, ocurrió un error. Y luego no me dejaba intalar más Ubuntu en partición propia. Tené cuidado si no queres perder información que tengas en windows.
Moraleja: windows se fue por la ventana. Bienvenido Natty narwhal.

Guille

---

### Post by Pan0ramix on 2011-06-27
Bueno, vuelvo con los comentarios prometidos. La cosa está por la mitad... tengo formateada la machine pero no me deja usar una nueva partición. Creo que voy a cambiarme a un disco mas grande y ahi probaré de nuevo. 

Seven en 64 anda bien; claro, se morfa toda la ram (ya tiene 4 GB) e intuyo que con el tiempo se pondrá más y mas pesada con tooooodas esas actualizaciones benditas que trae....

Ahora bien, suspendí el proyecto de reinstalar Lucid. ¿por qué? Pues, lucid viene de 10.04 y actualizarle los kernels creo que va a ser muuuy largo. ¿vale la pena? No lo sé, asi que esperaré a la próxima LTS release que venga para usar. Mientras tanto, usaré Maverick en la netbook, que le aprovecha al 100% todas las bondades de ésta. 

¿Alguna sugerencia? Un saludo a todos.

---


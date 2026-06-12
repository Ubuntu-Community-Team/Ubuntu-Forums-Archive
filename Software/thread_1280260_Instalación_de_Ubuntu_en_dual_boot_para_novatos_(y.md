---
title: "Instalación de Ubuntu en dual boot para novatos (y no tanto)"
date: 2009-10-01
forum: Software
---

### Post by josecuervo86 on 2009-10-01
[SIZE="5"][COLOR="DarkRed"]Instalación de Ubuntu 9.04 con Dual Boot[/COLOR][/SIZE]

Bueno, voy a tratar de mostrar como se instala Ubuntu 9.04 en dual boot con Window$ para aquellos que recien incursionan en el mundo de GNU/Linux y quieren probarlo.

Como primer paso, y antes que nada, hay que tener un CD con Ubuntu. Esto como se consigue? O bien pidiendo uno a [Canonical]("https://shipit.ubuntu.com/") o bajandose la [imagen]("http://www.ubuntu.com/getubuntu/download") desde la pagina de Ubuntu para despues grabarla en un CD.

Suponiendo que tenemos el CD, procederemos a la instalación.

En primer lugar, para instalar desde un CD, debemos hacer que nuestra maquina (ya sea Desktop o Notebook) bootee desde la unidad de CD-ROM. Esto significa que en lugar de buscar archivos de inicio en el disco rígido (HDD, donde está instalado tu sistema operativo actual) lo hará en el CD ¿Cómo se hace eso? Muy fácil, cuando inicia la maquina oprimimos el botón DEL para poder entrar al BIOS (en algunos Mothers se ingresa al BIOS oprimiendo alguna otra tecla. Ver manual del mother, pero en general alguna F será&#8230;). Una vez dentro hay que desplazarse por las opciones con las flechas del teclado ya que no se puede usar el mouse. Para modificar las opciones hay que utilizar el + y &#8211; respectivamente. Como vemos en la figura de abajo, buscamos la opción Boot y ahí seleccionamos CD-ROM Drive, **ATENCIÓN!** En algunos BIOS el orden de booteo está dentro de las opciones Advanced settings, ahí elegimos como First Boot al CD-ROM y listo. Después nos movemos a la solapa Exit y seleccionamos SAVE AND EXIT para guardar los cambios. El sistema se reiniciará y la máquina booteará desde el CD-ROM *. **[1]**

Otra forma de hacer esto es directamente entrar a las opciones de booteo, a las que generalmente se accede apenas prendes la maquina, apretando F8 o F12 segun el caso. Una vez ahí, y habiendo metido el CD en la compactera, eligen que bootee primero desde el CD. Si ya esta asi, dejenlo nomas. **[2]**

[IMG]http://a.imagehost.org/0653/boot.jpg[/IMG]

La primera imagen que veran sera esta:

[IMG]http://a.imagehost.org/0766/01_14.png[/IMG]

Elijen **Español** y le dan Enter. Nos aparecera algo así:

[IMG]http://a.imagehost.org/0761/02_8.png[/IMG]

Si quieren instalar de una, sin probar antes, le dan a **Instalar Ubuntu**

Va a cargar por algunos segundos

[IMG]http://a.imagehost.org/0939/04_7.png[/IMG]

Y cuando termine de cargar la barra, el sistema estara listo para ser instalado. Aquí comienza la instalación *per se*.

Lo primero que les pide es la configuración de idiomas que van a usar. Elijan **Español** y continuen

[IMG]http://a.imagehost.org/0714/05_2.png[/IMG]

Lo siguiente es la configuración horaria. Seleccionen la banda horaria que este en su pais.

[IMG]http://a.imagehost.org/0854/06_10.png[/IMG]

Es hora de configurar la disposición de teclas de su teclado. El mio es Español, pero no todos son así. Para eso en la parte inferior izquierda hay un recuadro donde pueden fijarse a ver si los caracteres coinciden. Seleccionen uno y prosigan.

[IMG]http://a.imagehost.org/0839/07_1.png[/IMG]

A continuación viene lo mas importante: decidir de que manera vamos a instalar:

[IMG]http://a.imagehost.org/0514/09.png[/IMG]



[SIZE="3"]Aqui termina la primera parte, la segunda a continuación!![/SIZE]

---

### Post by josecuervo86 on 2009-10-01
[SIZE="3"]Empieza la segunda parte!!!!!![/SIZE]


Como dijimos que vamos a instalar con **Dual Boot**, seleccionamos la opción que dice "Instalarlo junto a los otros, elijiendo entre ellos en cada inicio". Una vez seleccionado, se van a la barra de abajo y mueven la pestañita blanca para asignarle a Ubuntu el espacio de disco que ustedes estimen conveniente.

[IMG]http://a.imagehost.org/0609/10_8.png[/IMG]

[IMG]http://a.imagehost.org/0033/11_12.png[/IMG]

Ya falta poco, luego de esto nos pedira algunas cosas como su nombre, el nombre de usuario, contraseña y nombre del equipo. Ustedes sabrán que poner :)

[IMG]http://a.imagehost.org/0720/12_3.png[/IMG]

El siguiente paso es donde ustedes pueden importar datos que estan en su partición de Windows, para poder usarlos desde su home. No es un paso obligatorio y si quieren se lo pueden saltear.

[IMG]http://a.imagehost.org/0696/13_8.png[/IMG]

Y por fin llegamos al ultimo!!! Aqui les mostrara un resumen de lo que hicieron en el proceso de instalación. Si esta todo bien, pongan **Instalar** :)

[IMG]http://a.imagehost.org/0981/14_20.png[/IMG]

Luego de unos minutos (dependiendo de cada maquina) el sistema estara instalado:

[IMG]http://a.imagehost.org/0668/15_4.png[/IMG]

Aprietan reiniciar y listo! Ya tienen Ubuntu instalado en su maquina con Dual Boot, para poder correr junto con su Window$.

Espero les sirva a aquellos que recien se inician. Si les parece que hay que modificar algo, avisen!!

Saludos!!

* creditos a Sleeping Beauty y djgus por la sección del seteo de la BIOS.

**Agregados:**
Este tutorial en PDF: [http://www1.ubuntuforums.org/attachment.php?attachmentid=130652&d=1254615953](http://www1.ubuntuforums.org/attachment.php?attachmentid=130652&d=1254615953)
El tutorial de [Sleeping Beauty]("http://www1.ubuntuforums.org/member.php?u=908840"): [http://www1.ubuntuforums.org/attachment.php?attachmentid=130503&d=1254495304](http://www1.ubuntuforums.org/attachment.php?attachmentid=130503&d=1254495304)
Tutorial para escuchar Mp3's cedido por [Cajuma]("http://www1.ubuntuforums.org/member.php?u=856640"): [http://ubuntuforums.org/attachment.php?attachmentid=130668&d=1254625342](http://ubuntuforums.org/attachment.php?attachmentid=130668&d=1254625342)

---

### Post by pablo.s on 2009-10-01
Está lindo el tutorial!

---

### Post by santiagoward2000 on 2009-10-01
Muy bueno josecuervo86!
Sticky?

---

### Post by Sleeping Beauty on 2009-10-02
Lindo y simple! Muy parecido a lo que vengo armando, solo que yo agregué algo de como se cambia el booteo en BIOS (No se olviden de los ignorantes como yo que no sabía ni como se ingresaba a esa zona restringida para gurús :P )

---

### Post by edudelsur on 2009-10-02
> **Sleeping Beauty said:**
> Lindo y simple! Muy parecido a lo que vengo armando, solo que yo agregué algo de como se cambia el booteo en BIOS (No se olviden de los ignorantes como yo que no sabía ni como se ingresaba a esa zona restringida para gurús :P )
que arreglaste? el orden? como haces?

---

### Post by Sleeping Beauty on 2009-10-02
> **edudelsur said:**
> que arreglaste? el orden? como haces?

Aca tenes una ayuda con el orden de booteo en BIOS, el resto es muy similar al tutorial de josecuervo. Lo hicimos con djgus que es el que me salva a mi siempre en casa ja...

---

### Post by djgus on 2009-10-02
Bueno espero que les sirva el tutorial de instalacion, si alguno todavia tiene dudas, que diga en que parte se quedo y vere como ayudarlo. 
Saludos

---

### Post by josecuervo86 on 2009-10-02
Gracias a todos! Hay le agregué una foto de las opciones de booteo, para aclarar un poco mas ;)

---

### Post by rubioo on 2009-10-02
Quedo muy lindo jose :D

> **santiagoward2000 said:**
> Sticky?

+1

---

### Post by pol666 on 2009-10-02
Copado!, despues agrego la instalación con particionado manual para tener  la /home separada de la raíz y una swap a medida.

---

### Post by harryscode on 2009-10-02
Muy bueno, Gracias JoseCuervo y Sleeping Beauty por armar tan buenos tutos bien basicos. Más de uno estará agradecido

---

### Post by Mauro22 on 2009-10-03
Che, haganlo Sticky si no se va a perder entre los post!!

---

### Post by guillermolisi on 2009-10-03
> **Mauro22 said:**
> Che, haganlo Sticky si no se va a perder entre los post!!
En cuanto avisen que esta terminado se pegotea con mucho gusto :)

Me parece que falta, por lo menos, lo que estaba tratando de documentar Slepping Beauty, que no es menor (ni ella ni su agregado :) ).

---

### Post by pablo.s on 2009-10-03
Ah, y ya que están con ganas, 
me hacen lo mismo pero con la 
versión Alternate en sus dos 
variantes: instalación recomendada
y particionamiento manual...
Es chiste, no me peguen.

---

### Post by Sleeping Beauty on 2009-10-03
> **guillermolisi said:**
> En cuanto avisen que esta terminado se pegotea con mucho gusto :)

Me parece que falta, por lo menos, lo que estaba tratando de documentar Slepping Beauty, que no es menor (ni ella ni su agregado :) ).
Es mejor directo como un post o como pdf para descargar? En el finde se termina de detallar un poco mas la parte de BIOS que es la que da más miedo de tocar :-k

---

### Post by guillermolisi on 2009-10-03
> **Sleeping Beauty said:**
> Es mejor directo como un post o como pdf para descargar? En el finde se termina de detallar un poco mas la parte de BIOS que es la que da más miedo de tocar :-k
Lo que te sea mas comodo. Si va como PDF existe la alternativa que el que ya sabe como hacerlo ni lo abre.

---

### Post by Applelnx on 2009-10-03
Muy bueno. Yo creo que deberian hacerlo en pdf tambien. Saludos!!

---

### Post by josecuervo86 on 2009-10-03
Bueno, le agregue la parte del seteo de la BIOS que puso Sleeping Beauty en su versión PDF asi queda mas completo :)

Saludos!

---

### Post by josecuervo86 on 2009-10-03
Aprovecho y de paso les dejo el PDF que acabo de armar :)

Saludos!

---

### Post by Cajuma on 2009-10-03
Muy bueno chicos !!! , yo le agregaría lo siguiente, ya que vi un post en el que
decia que no podia reproducír MP3 y otras yerbas:

[ATTACH]130668[/ATTACH]

Gentileza da Ubuntu Life.
En el caso de agregar Medibuntu hay un .deb empaquetado por JC.Paco
que no tuve tiempo de buscarlo pero se que esta entre los post del Foro.
Saludos. :KS

---

### Post by matias_tati on 2009-10-04
Te felicito Jose...Sticky...

---

### Post by guillermolisi on 2009-10-04
Muy buen trabajo. Felicitaciones !

---

### Post by Sleeping Beauty on 2009-10-05
quedó muy bien, gracias por incorporarnos José!

---

### Post by guillermolisi on 2009-10-05
Agregado como tutorial en el website de Ubuntu-ar, seccion Tutoriales

---

### Post by josecuervo86 on 2009-10-05
> **Sleeping Beauty said:**
> quedó muy bien, gracias por incorporarnos José!

De nada Sleeping Beauty! :)

> **guillermolisi said:**
> Agregado como tutorial en el website de Ubutu-ar, seccion Tutoriales

Buenisimo Guille! :)

---

### Post by manodigital on 2009-10-08
:P José C, muchas gracias por este tutorial, ya que me decidí a instalar ubuntu 9.04, que lo tenia bajado desde mayo, ahora recién lo estoy aprendiendo a usar, y me parece un espectáculo. El tutorial me ha servido de maravillas, si bien soy un usuario experto, siempre es bueno tener una ayuda para poder hacer las cosas de una y bien.

saludos cordiales.

---

### Post by josecuervo86 on 2009-10-08
Manodigital, me alegro muchisimo que te sirva! Muchas gracias!

Saludos

---

### Post by guillermolisi on 2009-10-10
> Buenas noches, soy nuevo por acá. Estoy incursionando por primera vez en Ubuntu y segui la guia que ustedes plantean en este post, todo barbaro hasta que entra a leer el cd y la pantalla se ve toda rayada se ve que carga el programa de instalacion y todo, pero no se ve mucho porque esta todo rallado... estuve viendo de ver otras alternativas pero nada, ¿alguien me podrá dar una mano con esto?

Saludos y suerte.
Emiliano.

Ese post esta en un thread nuevo en la seccion Hardware: [http://ubuntuforums.org/showthread.php?t=1288047](http://ubuntuforums.org/showthread.php?t=1288047)

---

### Post by guillermolisi on 2009-10-11
> **10921 said:**
> hola :
ante todo me presento soy cristian y me registre hace poco , como vi que esto era para novatos lo lei y segui todos los pasos , y logre instalar ubuntu correctamente , hasta hay todo bien pero lo que pasa es que cuando quiero reiniciar con el otro sistema operativo este no logra iniciarse .
desde ya les agradeceria su ayuda .
saludos .
Movido a la seccion Software

---

### Post by luica on 2009-10-13
una duda y el particionado para / y /home,  el live cd hace la particion automaticamente?? gracias...

---

### Post by NGP on 2009-10-27
Muy bueno este instructivo!! Yo tengo que hacer al revés. Me compré una mini laptop que viene con Ubuntu y quiero instalar el XP. Quiero que me de  la opción al inicio para elegir con cual arrancar. Será muy díficil?
 
Gracias!!!!!:D

---

### Post by guillermolisi on 2009-10-27
> **luica said:**
> una duda y el particionado para / y /home,  el live cd hace la particion automaticamente?? gracias...
El unico particionado automatico es el que se menciona "por defecto" cuando utilizas todo el disco para Ubuntu (creo que tambien figura como automatico).

Para establecer otra disposicion de particionado hay que ingresar en modo manual y determinar que particion se creara y sus caracteristicas, aunque tambien uses todo el disco para Ubuntu.

---

### Post by fedeavila on 2009-10-27
> **pol666 said:**
> Copado!, despues agrego la instalación con particionado manual para tener  la /home separada de la raíz y una swap a medida.

ya lo agregaste?? leí que es más seguro tener la /home separada de la raíz y me gustaría implementar eso para cuando salga karmic jeje

---

### Post by ChiniBox on 2009-11-11
Buenas,
Istale el Ubuntu en una particion que cree en un rigido en el que tengo el XP segun lo que esta en este tutorial, pero no he logrado que me de a elegir con cual iniciar el sistema, la Pc sigue iniciandose directo en XP, sabes como corregir este problema?
Gracias y saludos

---

### Post by ChiniBox on 2009-11-11
> **djgus said:**
> Bueno espero que les sirva el tutorial de instalacion, si alguno todavia tiene dudas, que diga en que parte se quedo y vere como ayudarlo. 
Saludos
Buenas,
Istale el Ubuntu en una particion que cree en un rigido en el que tengo el XP segun lo que esta en este tutorial, pero no he logrado que me de a elegir con cual iniciar el sistema, la Pc sigue iniciandose directo en XP, sabes como corregir este problema?
Gracias y saludos

---

### Post by djgus on 2009-11-11
Hola: mira el menu de booteo se hace solo cuando instalas, pero contame un poco mas como hiciste la particion y la instalacion, por logica se tendria que haber hecho el menu solo. De ultima reinstala ubuntu y fijate que hay una opcion que te da para generar el dual boot.
Cualquier otra duda avisame y lo vemos
Saludos

---

### Post by madbyte on 2009-11-12
Hola

Aprovecho este post para comentarles como me fue instalando Ubuntu en una máquina que ya tenía Windows XP. 
No quería tocar el XP, asi que me compré un disco nuevo, lo particioné e instale primero Ubuntu y después de unas semanas de uso le instale en la otra partición Windows 7. La instalación de Windows creó un cargador en el disco con XP, asi que si quería usar Ubuntu tenía que elegir como boot el disco 2 y ahi arrancaba el Grub dándome sólo 2 opciones, entrar a Ubuntu ó al arrancador de Windows, si elegía esta, me cargaba el menu de arranque de Windows 7, es decir que desde el menú del Grub no podía elegir entre Windows 7 o el XP. Y acá fue donde surgió el problema, porque si desde el Grub elegía Windows, y despues XP la máquina se reseteaba, si elegía Windows 7 andaba bien. Quice solucionar el problema a travez del Grub pero no encontré muchos datos o tutoriales para modificar el arranque teniendo estos 3 sistemas operativos, o como hacer para pasar el Grub del disco 2 al disco 1. La solución la encontré usando EasyBCD, tienen una versión beta, que se puede bajar del foro de NeoSmart Technologies, que soporta el Grub 2, asi que desde Windows 7 y con el EasyBCD pude modificar las opciones de arranque y le pude agregar Ubuntu al menú. Ahora directamente arranco con el disco 1 y tengo acceso a los 3 sistemas operativos.
La única modificación que le hice al Grub desde Ubuntu fue hacer que el tiempo de espera sea 0 usando el *Administrador de Arranque*.

Saludos

---

### Post by antarezx on 2013-08-12
Hola ya llevo tiempo con esta cuenta, dejo sugerencias personales de como se puede cambiar mas fácil de windows a linux:

-Para mi la mejor opción es usar al instalar el particionado en modo avanzado, separando la partición raíz / de la HOME
   +Esto para que se pueda reescribir el sistema operativo tantas veces como quiera y no se toquen nuestros archivos de HOME
   +Experimentar con otros sistemas operativos sin preocuparnos de respaldar (Si eres novato trata de respaldar por si te                    equivocas)

-Creo que para una guía un poco mas completa se puede agregar lo básico de instalación para el sistema operativo y también  agregar como reparar el grub de linux y el mbr de windows, esto para mejorar la experiencia y transición del usuario de windows a  linux. (No estoy seguro si poner los manuales juntos o separados).

-La instalación de software básico como el de ubuntu-restricted-extras preferentemente sugerir el software mas usado por los  novatos que empiezan en este nuevo mundo.Y creo que eso es todo, se que existe mucha información en google pero hay veces en las que uno no puede encontrar lo que necesita y seria mas fácil si lo principal estuviera todo junto, por eso creo que para esto sirven estos foros.

Bueno eso es todo.
Un abrazo psicológico y espero que le sirva a alguien.

---


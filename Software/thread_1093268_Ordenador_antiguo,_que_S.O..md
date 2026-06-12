---
title: "Ordenador antiguo, que S.O.????"
date: 2009-03-11
forum: Software
---

### Post by dani2001es on 2009-03-11
Tengo un portátil con 60mb de ram, que distro puedo instalar? Me gustaría que tuviera modo gráfico.

---

### Post by Dan_Dranath999 on 2009-03-11
fluxbuntu, damn small linux, puppy linux...

creo que los últimos 2 pueden arrancar con 16 y 40 megabytes de RAM. según he leído en algunos foros...

el LiveCD de Damn Small Linux anda por debajo de los 50 megas (se supone que cabe en una CD Business Card) y el Puppy Linux en 90, por lo que te recomiendo que te bajes alguna imagen de cd, la grabes y pruebes qué tan van en tu máquina antes de instalar.

---

### Post by josecuervo86 on 2009-03-11
Yo probaria con Damn Small Linux[0], funciona con al menos 50 de Ram

[0][http://damnsmalllinux.org/index_es.html]("http://damnsmalllinux.org/index_es.html")

---

### Post by pablo.s on 2009-03-11
Me causa mucha gracia el hecho,  de que en cada post que alguien pregunta por alguna opción para instalar en una maquina a la que se le pasó el cuarto de hora, se mencionen distribuciones que no están relacionadas ni remotamente con Ubuntu.

**Damn Small Linux** y  **Puppy Linux** son distribuciones **AJENAS**. Hay muchas opciones para recomendarle a los que preguntan. Por ejemplo: **Crunchbang Linux** es un Ubuntu con OpenBox, **LinuxMint** versión Felicia viene con Fluxbox, **Ubuntu Mini Remix** viene de entrada con consola, **U-lite** viene con LXFE y seguro que que se me cuela una drag queen, según Calamaro.

No pretendo tirar de las orejas de nadie, solamente agrupar las tropas para que no se vayan para otras filas. Y no me vengan con eso de que mientras sea Linux está bien.
Saludos

---

### Post by anarko on 2009-03-11
El muchamo pregunto que distro puede instalar en una portatil con 64Mb de ram, no pregunto que hijo bobo de ubuntu pede instalar en esa PC.

OnTopic : yo lo hice en un celeron 500 con 64Mb, instale un 804 alternate "pelado" osea no le deje instalar mas que el kernel y el sistema base y luego instale el X y el Gnome pelados y andaba 10 puntos. Lo mismo podes hacer con un netinstal de debian.

Si la portatil tiene un slot de memoria DIMM por 70pe le podes poner 128 Mb mas y es un mundo diferente.

---

### Post by pablo.s on 2009-03-11
Dame tu definición de "hijo bobo". Me interesa saberlo. A ver si quizá GNU/Linux entra en la categoria "hijo bobo" de Unix. Con suerte todo lo que hace el movimiento free software entra en la categoria "hijo bobo" de la industria del software privativo.
Te pido, eso si que reflexiones antes de responder. Saludos

---

### Post by Hei Ku on 2009-03-11
Por favor, moderen sus respuestas y mantengan la discusion al tema y de manera civilizada.

En cuanto a ofrecer distros que no sean basadas en Ubuntu: Mucha gente aca usa otras distros y recomienda lo que le funciona. Si hay gente que tiene experiencia en distros pequeñas y ademas basadas en Ubuntu, mejor.

---

### Post by guillermolisi on 2009-03-12
> **dani2001es said:**
> Tengo un portátil con 60mb de ram, que distro puedo instalar? Me gustaría que tuviera modo gráfico.
Asumo que una portatil con 60Mb de RAM debe ser, como maximo, PentiumII o equivalente.
Es decir, la maquina debe tener 64Mb de los cuales 4Mb se usan para video lo cual deja un margen bastante estrecho para usar escritorios graficos (Gnome, KDE 3.5).

Si mi apreciacion es correcta, pensaria en Ubuntu-Lite con LXDE para ver si la respuesta del conjunto es razonable.

Si se mueve gomosa, cambiaria el escritorio grafico por un Windows Manager como los que te mencionaron (OpenBox, FluxBox, Enlightenment) entre otros (hay muchos WM para elegir y probar).

Por que me mantendria enla linea de Ubuntu ? Por la posibilidad de mantener actualizado todo a traves de los repositorios y contar con la posibilidad de elegir y usar varias alternativas como Aptitude, apt-get, llegado el caso Synaptic.

---

### Post by NickCis on 2009-03-13
Que andaria mejor un netinst (o como sea) de debian o una instalacion alternate (la que solo instala el modo de consola) de ubuntu?.

Se hacer la instalacion alternate de ubuntu, pero ni idea la de debian, pueden explicar un poco de eso?.

Saludos.

---

### Post by pablo.s on 2009-03-13
La diferencia **principal** es que la imagen de netinst no debe llegar a 30 MB para bajar, mientras que la imagen de la alternate es de 650-700 MB. En la capacidad de elegir solo los paquetes que te interesan instalar las dos son similares, con la diferencia que la netinst los baja del repositorio y la alternate los saca del CD (o pendrive).
Otra cosita, la alternate no anda en modo consola, es un modo gráfico pero medio crudo, creo que es ncurses. Quienes hayan instalado Warty-Hoary-Breezy y hasta Dapper saben como es (los debianitas tambien).
Saludos a todos.

---

### Post by NickCis on 2009-03-13
> **pablo.s said:**
> La diferencia **principal** es que la imagen de netinst no debe llegar a 30 MB para bajar, mientras que la imagen de la alternate es de 650-700 MB. En la capacidad de elegir solo los paquetes que te interesan instalar las dos son similares, con la diferencia que la netinst los baja del repositorio y la alternate los saca del CD (o pendrive).
Otra cosita, la alternate no anda en modo consola, es un modo gráfico pero medio crudo, creo que es ncurses. Quienes hayan instalado Warty-Hoary-Breezy y hasta Dapper saben como es (los debianitas tambien).
Saludos a todos.

Ok, pense que no tenia entorno grafico por que siempre tenia qe instalar el xorg + al desktop enviroment o window manager y dsp tirar el startx.

Respecto al debian, si agarro debian e instalo desde 0, podre hacer un SO que utilice menos recursos que haciendo lo mismo con Ubuntu?.

Ahh, y respecto a window managers, probe el Enlighment (E17) con el Opengeu, live Cd. Pero a mi maquina vieja no le da para eso. Queria probarlo haciendo una instalacion desde minima, como tengo que instalarlo, hay que compilarlo?, existe alguna deb para Hardy o para Debian lenny?.

Para los que quieren probar Openbox, les recomiendo que instalen LXDE que usa openbox y no viene tan pelado. Usen los repositorios de Lxde:
Para intrepid:
```

deb http://ppa.launchpad.net/lxde/ubuntu intrepid main
deb-src http://ppa.launchpad.net/lxde/ubuntu intrepid main 
```
Para Hardy:
```

deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main 
```

Edit: encontre lo del PPA [https://launchpad.net/~lxde/+archive/ppa](https://launchpad.net/~lxde/+archive/ppa)

Saludos.

---

### Post by pablo.s on 2009-03-13
Cuidado con Enlightenment, que da la impresión de ser ligero pero no es asi. Tiene un grado de preciosismo que tienta, aunque eso implica que, como vieja con collares de oro, sea caro de mantener. Si te interesa podés instalar una alternate con lo minimo y luego seguir los pasos que dice [aqui]("http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs") para obtener el bling-bling. Luego empezás a ponerle widgets, barrita de acá, barrita de allá, sensor de temperatura y cuando te das cuenta ya parece una carroza del sambodromo.

Con lo que preguntás de Debian, no creo que consuma menos recursos que si lo hacés con Ubuntu. Pero puede ser mucho más estable (porque los paquetes de Debian son muy pulidos, probados hasta que no existan bugs). 

Para bajos recursos vuelvo a recomendar Openbox. Yo lo utilizo en una EEEPC.
Saludos

---

### Post by pol666 on 2009-03-14
No vas a poder correr ningun desktop completo con esa cantidad de memoria, pero capaz con un netinstall de debian y un ICEWM u openbox lo sacas andando.

---

### Post by eldragon on 2009-03-14
> **pablo.s said:**
>   Y no me vengan con eso de que mientras sea Linux está bien.
Saludos

en realidad. a quien le importa que corre en la maquina? el post es sobre una distribucion que ande bien, no especifica que sea *buntu.

yo personalmente instalaria Arch, porque arranca bien con lo basico, y de ahi le vas asignando vos la complejidad que aguante la maquina. pero requiere un poco mas de tiempo para configurar.

---

### Post by guillermolisi on 2009-03-14
> **NickCis said:**
> Ok, pense que no tenia entorno grafico por que siempre tenia qe instalar el xorg + al desktop enviroment o window manager y dsp tirar el startx.

Es que *no* es un entorno grafico propiamente dicho, por eso la necesidad de instalar los paquetes que mencionas y por eso tanto Netinstall como Alternate lo usan para procesos de instalacion livianos.

---

### Post by NickCis on 2009-03-14
Entonces Netinst es lo mismo que la instalacion minima de Ubuntu (solo que uno es debia y baja todos los debs d internet, y el otro los tiene en CD).?

Saludos.

---

### Post by jjgomera on 2009-03-14
tanto la netinstall de debian, como el alternate de ubuntu tiene instalador grafico, bastante parecidos entre si,
Eso si de manejador de ventanas, olvidate de un entorno de escritorio completo, te recomiendo openbox, podrias probar [crunchbang linux]("http://crunchbanglinux.org/") que es un ubuntu con openbox.

Yo lo hice sobre una ubuntu normal: [http://linexiando.blogspot.com/2008/07/openbox-en-ubuntu-804.html](http://linexiando.blogspot.com/2008/07/openbox-en-ubuntu-804.html), y estoy la mar de contento

---

### Post by jjgomera on 2009-03-14
> **NickCis said:**
> Entonces Netinst es lo mismo que la instalacion minima de Ubuntu (solo que uno es debia y baja todos los debs d internet, y el otro los tiene en CD).?

Saludos.
para hacer una instalacion minima + xorg + manejador de ventanas es una gran opcion, (mejor que la alternate porque muchos de los programas que la alternate lleva no los vas a instalar) apenas 15 minutos tarda el proceso, eso si, si instalas un manejador de ventas necesitaras instalar uno a uno los programas que necesites, empezando por una terminal, si no te gusta xterm, un navegador de archivos...

---

### Post by gmunioz on 2009-03-14
Hola nic...:

Mi sugerencia es que te bajes Debian NetInstall y solo instales el servidor, con esto iniciaras en consola y verás si corre adecuadamente, safisfecho con su desempeño y velocidad de inicio.

Puedes continuar agregándole las gráficas y un entorno o manejador de ventanas, y logrado esto recien ir instalando aplicaciones livianas segun necesidad.

Por ejemplo para utilizar una combinación recomendable de fluxbox, mrxvt, gkrellm y rox-filer, lo haces mediante los comandos:

su
apt-get update
apt-get upgrade
apt-get install x-window-system fluxbox mrxvt gkrellm rox-filer

E inicias las gráficas con

startx

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - 22 Mad Jaunty User.**

---

### Post by pablo.s on 2009-03-14
> **eldragon said:**
> en realidad. a quien le importa que corre en la maquina? el post es sobre una distribucion que ande bien, no especifica que sea *buntu.

yo personalmente instalaria Arch, porque arranca bien con lo basico, y de ahi le vas asignando vos la complejidad que aguante la maquina. pero requiere un poco mas de tiempo para configurar.

Bueno hombre, entonces te sugiero que en los foros de Archlinux propongas que instalen Ubuntu, asi quedás como un veleta pero internacionalmente, eh, no vaya a ser que se arme una flame war y nos tengamos que insultar porque la gente no se da cuenta que este foro es de Ubuntu. Estoy en lo cierto?

---

### Post by NickCis on 2009-03-15
gmunioz voy cuando tenga tiempo hago lo que me decis.
Me parece que voy a instalar Openbox, Pcmanfm, Leafpad, muine, abyword, algun visor de pdf y otro de ppt.

La otra es que instale LXDE que usa Openbox y mas o menos los programas que dije mas arriba, cuando pruebe comento :P

Saludos.

P.D.: cuando hago el netinstall de debian, no me instala nada, ni siquiera el vii, nano o xterm?.

---

### Post by init1 on 2009-03-15
> **NickCis said:**
> Que andaria mejor un netinst (o como sea) de debian o una instalacion alternate (la que solo instala el modo de consola) de ubuntu?.

Se hacer la instalacion alternate de ubuntu, pero ni idea la de debian, pueden explicar un poco de eso?.

Saludos.
Es posible hacer un netinst de Ubuntu con el "mini.iso". Es muy similar al netinst de Debian. Creo que la instalacion del "mini.iso" y netinst de Debian sea bastante fácil, pero no es gráfico. 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by pol666 on 2009-03-16
El netinstall de DEebian es re facil, ademas tenes todo bien preparado, y ni hablar sí compilas algunas cosas.

---

### Post by jjgomera on 2009-03-16
> **NickCis said:**
> gmunioz voy cuando tenga tiempo hago lo que me decis.
Me parece que voy a instalar Openbox, Pcmanfm, Leafpad, muine, abyword, algun visor de pdf y otro de ppt.

La otra es que instale LXDE que usa Openbox y mas o menos los programas que dije mas arriba, cuando pruebe comento :P

Saludos.

P.D.: cuando hago el netinstall de debian, no me instala nada, ni siquiera el vii, nano o xterm?.

en el netinstall hay un paso en el que eliges lo que instalar (sudo tasksel en cualquier debian ubuntu ya instalada) y en que deberías de elegir solo la ultima opción de sistema estandart, con eso se instala el sistema base, sin x ni escritorio pero si con nano (vi y xterm no lo sé) (si eliges entorno de escritorio te instalará gnome). Cuando termina la instalación arrancas en modo consola y instalas ahí lo que quieras, empezando por el xserver-xorg

---

### Post by ramiro_md on 2009-03-16
Te recomiendo Puppy LInux, usa JWM. Nunca lo probé en una pc con 60mb de ram, pero en las características dice que debería andar. 
En mi caso obtuve muy buenos resultados en un pc con 128 mb de ram.

---

### Post by Dan_Dranath999 on 2009-03-25
> **pablo.s said:**
> Me causa mucha gracia el hecho,  de que en cada post que alguien pregunta por alguna opción para instalar en una maquina a la que se le pasó el cuarto de hora, se mencionen distribuciones que no están relacionadas ni remotamente con Ubuntu.

Si cuando alguien decide usar Windows para tal o cual tarea, la posición de la mayoría de la comunidad es "Bien. Usa lo que funcione para tí", me parece que por lo menos debería darse el mismo trato a otras distribuciones.  

> **pablo.s said:**
> **Damn Small Linux** y  **Puppy Linux** son distribuciones **AJENAS**. 

Se supone que Damn Small Linux puede expandirse y convertirse a una instalación DEBIAN completa. Ubuntu está basado en Debian. Yo veo una clara inter-relación entre estas distribuciones, de AJENO nada.

> **pablo.s said:**
> No pretendo tirar de las orejas de nadie, solamente agrupar las tropas para que no se vayan para otras filas. Y no me vengan con eso de que mientras sea Linux está bien.
Saludos

Pensaba que éramos una comunidad de USUARIOS, no una SECTA. Pero como usted quiera, excelentísimo líder, fuente de toda sabiduría ¡Salve! ¡Salve!. [Tampoco sabía que estabamos en guerra con Fedora, Mandriva, Arch etc...]

---

### Post by pablo.s on 2009-03-25
> **Dan_Dranath999 said:**
> Pensaba que éramos una comunidad de USUARIOS, no una SECTA. Pero como usted quiera, excelentísimo líder, fuente de toda sabiduría ¡Salve! ¡Salve!. [Tampoco sabía que estabamos en guerra con Fedora, Mandriva, Arch etc...]

Sabes cual es mi réplica a tu sabiduria?  **ESTA**

---

### Post by Dan_Dranath999 on 2009-03-25
> **pablo.s said:**
> Sabes cual es mi réplica a tu sabiduria?  **ESTA**


Gracias, oh gran maestro iluminado. Vuestra pronta (aunque algo breve pero no por ello menos sabia) respuesta no sólo me ha llenado de un gozo sin precedentes, sino que confirma vuestra santidad y legendario liderazgo informático. ¡Que presten oídos los infieles de Novell, que escuchen la palabra los herejes de Red Hat, y que tiemblen los paganos de Microsoft, que las calles serán abarrotadas con el HARDWARE DE LOS NO-CREYENTES!

---

### Post by faustileon on 2009-03-25
El primer post de pablo.s que cita Dan_Dranath999 estaba ya 100 m antes del borde de las regalas de este foro.  Pero el final de la contestación de éste último, definitivamente fuera de las reglas, por unos 500 m.  La contestación de pablo.s, 5 km afuera y la última de Dan_Dranath999 10km.  Me parece que algún administrador debería hacer limpieza, ¿no? (incluyendo este mismo comentario) Porque si hablamos de cómo se ve todo esto desde "afuera" (mal usada esta palabra para referirse a los que no usan GNU/Linux/Ubuntu), les aviso que lo suyo, reconociendo que me pongo la gorra de vigilante, se ve bastante feo.  Y Dan_Dranath999, nada de lo que haya puesto pablo.s te autoriza a insultarnos a todos los demás.  Nadie te dijo nada (ni le dice nunca nada a nadie en este foro) con respecto a ser del norte, el sur, el este o el oeste.  Como sureño te pido que te ahorres la ironía.  Gracias.

---

### Post by Dan_Dranath999 on 2009-03-25
> **faustileon said:**
> Nadie te dijo nada (ni le dice nunca nada a nadie en este foro) con respecto a ser del norte, el sur, el este o el oeste.  Como sureño te pido que te ahorres la ironía.  Gracias.


Anotado y corregido en el post. La procedencia no debería ser nunca objeto de debate, y me disculpo en cuanto a ello. Pero el resto se queda.

---

### Post by faustileon on 2009-03-25
Todo bien.  Es que... honestamente, entiendo para dónde va pablo.s y algo de razón tiene, sin embargo, está clarísimo en las reglas del foro que lo primero es ayudar y dar respuesta a las preguntas, desde ese lugar es perfectamente válido (y además amable, y además habla bien de esta comunidad) incluir otras distros en la respuesta.  Así que, finalmente, estoy de acuerdo en lo que decís en tu post.  Solo te podrías haber ahorrado el palito final, que provoca su encendida y desubicada respuesta (creo que en Méjico y España se entiende, en Argentina es una respuesta de moneda corriente -casi una costumbre, incluso entre amigos-) y, como te dije, aunque fue con mucha más altura que la suya insultante, la última con referencia a los puntos cardinales.  Por lo demás, aceptada la disculpa y sugiero, si no lo hacen los administradores, en un tiempo prudencial borrar/editar nosotros mismos nuestros posts.
Gracias.

---

### Post by Dan_Dranath999 on 2009-03-25
No creo que sea necesario borrar nada más de lo que se ha escrito aquí... 

Aparte de algunos comentarios sarcásticos, y una referencia geográfica fuera de contexto (que ya me he encargado de eliminar) esto está todavía MUY MUY LEJOS de los encendidos debates en inglés en este mismo foro.

Y los puntos que se han tocado son importantes, como para dejarlos pasar ignorados:

1.- ¿Somos o debemos ser una comunidad cerrada a otros sistemas operativos e incluso a otras distribuciones de Linux?

2.- ¿Hasta qué punto es válida la militancia en el uso de una herramienta como es un sistema operativo? 

En el punto 1, veo muy difícil centrar los foros solamente en las distribuciones de Canonical y derivados de la comunidad (aunque cada distro tenga sus foros), ya que el sistema GNU/Linux está hecho con el trabajo de mucha gente en todo el mundo, y el desarrollo de la interfaz gráfica, herramientas y aplicaciones repercute en todo el ecosistema Linux, y en BSD y en OpenSolaris... (el escritorio KDE ya está disponible para Windows en Beta, no digo más) 

Creo que es una cuestión estéril buscar la separación de UBUNTU vs. el resto de Distros Linux, puesto que el hecho de que Ubuntu tuviese algo que no haya sido derivado de o haya influenciado en otras distribuciones linux, IRÍA EN CONTRA DE LA FILOSOFÍA DE UBUNTU, DE LINUX Y DEL SOFTWARE LIBRE EN GENERAL: el código es de todos para ser usado por todos, por tanto: Ubuntu = Mandriva = Opensuse = DSL = Arch = Fedora = ... 

y Vamos todos por el mismo camino, hacia el mismo lugar y compartiendo las herramientas.

---

### Post by jjgomera on 2009-03-25
> **Dan_Dranath999 said:**
> 
Creo que es una cuestión estéril buscar la separación de UBUNTU vs. el resto de Distros Linux, puesto que el hecho de que Ubuntu tuviese algo que no haya sido derivado de o haya influenciado en otras distribuciones linux, IRÍA EN CONTRA DE LA FILOSOFÍA DE UBUNTU, DE LINUX Y DEL SOFTWARE LIBRE EN GENERAL: el código es de todos para ser usado por todos, por tanto: Ubuntu = Mandriva = Opensuse = DSL = Arch = Fedora = ... 

y Vamos todos por el mismo camino, hacia el mismo lugar y compartiendo las herramientas.

totalmente esteril y perjudicial para esta comunidad

yo no uso ubuntu, uso debian, si esta fuera una comunidad de ubuntu solo, ¿qué hago yo aquí?

---

### Post by pablo.s on 2009-03-25
Por el presente mensaje pido disculpas por mi comportamiento
en este foro, asi como a las personas que pude haber ofendido.
Sin otro particular, les deseo lo mejor. Saludos y todos en paz.

---

### Post by faustileon on 2009-03-25
Todo bien, somos todos grandes y sabemos lo que hacemos.  Coincido casi plenamente con tus opiniones (un "casi" prácticamente preventivo).  Lo último que digo es que, para expresar tu disenso, no hacía falta el sarcasmo, que dispara el exabrupto, en lugar de la reflexión, que a su vez dispara más sarcasmo en vos.  Nadie habló de cercenar el debate o dejar pasar por alto temas que, evidentemente, son importantes y merecen ser discutidos.  Pero en ese sentido (al igual que con respecto a flames y ataques personales -personalizados-), las reglas del foros SON CLARÍSIMAS: es un foro técnico y no de debate sobre GNU/Linux/software libre y cada thread debe intentar ceñirse al tema por el cual fue abierto.  Por eso, yo, por mi parte, en un par de días, una vez crea que hayan leido mis posts quienes correspondan, los borro.  Repito, cada uno es grande y sabe lo que hace. De nada sirve seguir viendo quién la tiene más grande. Gracias y saludos.

---

### Post by infernus92 on 2009-03-26
dentro de las distros de ubuntu podrias probar con fluxbuntu o ubuntu mini remix (no creo que tolere un Xubnuntu)... tambien hay otras livianitas como pupy linux, slackware, etc...

---

### Post by Hei Ku on 2009-03-26
Como verán, "limpié" un poco la discusion.
Primero, ya estaban advertidos sobre moderar el tono de los posts.
Segundo, en esta comunidad hay lugar para todos y varios de los que mas aportan usan otras distros, y algunos hasta usan ese otro sistema operativo.
Tercero, hay varios moderadores, no hacen falta extras.
Cuarto, que personas nuevas en el grupo hablen sobre qué es o debería ser esta comunidad, es casi risible. Deberían primero conocerla, participar y recien despues emitir opinion.
Quinto, espero no tener que volver a moderar este post.

Cualquier queja sobre lo que hice, por PM a mí o a Sajnox. NO DENTRO DE ESTE THREAD.

A partir de este momento, pueden continuar con la discusion original. Muchas gracias!

---


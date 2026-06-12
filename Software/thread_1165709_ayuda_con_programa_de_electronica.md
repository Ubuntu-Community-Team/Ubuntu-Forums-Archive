---
title: "ayuda con programa de electronica"
date: 2009-05-20
forum: Software
---

### Post by infernus92 on 2009-05-20
hola... otra vez dando vueltas por el foro, pero esta vez con un problemita que agradeceria si me pueden ayudar...
hoy me estoy viendo obligado a usar window$ porque estoy haciendo un trabajo de electronica para la escuela... el problema es que tengo que usar SI O SI el programa de diseño Eagle version 5.0. Lamentablemante no puedo usar ningun otro porque Eagle no permite compatibilidad ni siquiera con versiones anteriores ni posteriores del mismo programa...
en ubuntu logre instalar muy simplemente la version 4.16r2 pero no es compatible con la version 5.0 que tengo en window$ y en la escuela (por eso no puedo usar otra)
a traves de wine logre instalar la version 5.0 pero al intentar crackearle el crack no funciono y sin crack, no anda el keygen... y ademas no se que paso que tampoco puedo desinstalarlo desde wine

si alguno me pudiera dar alguna idea, dato, link o algo asi le agradezco mucho...

Saludos

PD: ya intente bajarlo desde la web oficial y me da un archivo en formato run que no se como hacer andar

---

### Post by pablo.s on 2009-05-20
sh nombre_de_archivo.run

Por lo general se debe ejecutar
como superusuario.

---

### Post by eldragon on 2009-05-20
eagle, de cadsoft, tiene su version nativa en linux. es lo que uso yo actualmente para hacer los circuitos impresos. uso la version demo que soporta placas de hasta 10cm x 10cm.

sobre el crackeo, no creo que sea conveniente hablar de esos temas en este foro. no esta permitido...

fijate en los repositorios, me parece que estaba la ultima vez que me fije, sino bajalo de la pagina

---

### Post by infernus92 on 2009-05-20
no sabia eso del crackeo... pido disculpas...
yo tambien tengo esa version que esta en los repositorios pero tengo el problema de la compatibilidad todavia... gracias lo mismo
y gracias pablo.s voy a hacer lo que dijiste a ver si resulta

Saludos

---

### Post by infernus92 on 2009-05-21
gracias pablo.s con lo que me dijiste anduvo... pero pasa lo que dice eldragon... solo se pueden hacer plaquetas de hasta 10x10cm... pero bueno... mejor que nada es

Saludos

---

### Post by Charlymagnus on 2009-11-27
Hola a todos, me presento soy nuevo en el foro y novato tambien en el uso de Ubuntu:La cuestion es que navegando y buscando soluciones a mi problema, me tope con una solucion posible atraves del post de infernus92.Sucede que soy usuario del Eagle V.4.16r2, que utilizo desde hace varios años pero en Windows y estoy tratando de instalarlo en Ubuntu.Veo que infernus92 lo ha logrado y si no es muy tarde, por el tiempo que ha pasado del ultimo post,me gustaria que infernus92 me diga, por favor como lo ha logrado ya que luego de proceder desde terminal con el comando correspondiente, me sale el siguiente mensaje:
error: Dependencias fallidas:
	/bin/sh se necesita por eagle-lin-eng-4.16r2-1.i586
	libX11.so.6 se necesita por eagle-lin-eng-4.16r2-1.i586
	libXext.so.6 se necesita por eagle-lin-eng-4.16r2-1.i586
	libc.so.6 se necesita por eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.0) se necesita por eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.1) se necesita por eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.1.3) se necesita por eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.2) se necesita por eagle-lin-eng-4.16r2-1.i586
	libdl.so.2 se necesita por eagle-lin-eng-4.16r2-1.i586
	libdl.so.2(GLIBC_2.0) se necesita por eagle-lin-eng-4.16r2-1.i586
	libdl.so.2(GLIBC_2.1) se necesita por eagle-lin-eng-4.16r2-1.i586
	libm.so.6 se necesita por eagle-lin-eng-4.16r2-1.i586
	libm.so.6(GLIBC_2.0) se necesita por eagle-lin-eng-4.16r2-1.i586
...y sinceramente no se como instalar dichas librerias.Lo he intentado desde sinaptic y desde aplicaciones y no aparecen en los repositorios.
Se que el programa esta orientado a Fedora, pero si infernus92 lo logro, espero su respuesta, la cual agradezco de antemano.
Si no has logrado superar el problema de la limitacion del tamaño de las placas tal vez pueda ayudarte infernus, solo hazmelo saber desde privado.
Seguramente me diran que ya hay una version de Eagle desde repositorios, lo se.Pero a esta version le he tomado cariño y es la que quiero instalar por las compatibilidades que tengo con la de Windows ¿ se entiende?
Aclaro que yo uso la distro de Ubuntu 8.04 con el EMC2 descargada desde el sitio ([http://www.linuxcnc.org/)que](http://www.linuxcnc.org/)que) es practicamente igual que las otras versiones.
Mis disculpas por lo extenso del post y cualquier duda que quieran evacuar sobre el uso del Eagle, con todo gusto tratare de responderles.Un abrazo.

---


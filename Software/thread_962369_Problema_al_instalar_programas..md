---
title: "Problema al instalar programas."
date: 2008-10-29
forum: Software
---

### Post by Just64 on 2008-10-29
Soy totalmente nuevo en Ubuntu, el primer problema q tengo es:
[[IMG]http://img510.imageshack.us/img510/8451/pantallazo1er9.th.png[/IMG]](http://img510.imageshack.us/my.php?image=pantallazo1er9.png)[[IMG]http://img510.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
Como se ve ahy me tira un error al querer instalar diferentes programas como el winamp o msn, alguna solucion?

---

### Post by lega on 2008-10-29
Hola, bienvenido

los programas que intestas instalar no te van a funcionar en Ubuntu, al menos no como pretendes instalarlos,porque son para Windows que es un SO totalmente diferente a Linux, te recomiendo una página para leer es ideal para cualquier persona que empieza con ubuntu

Suerte

[http://www.guia-ubuntu.org/index.php?title=Portada](http://www.guia-ubuntu.org/index.php?title=Portada)

---

### Post by Just64 on 2008-10-29
Pero ahy gente q usa el msn en el Ubuntu, no? Al menos me parecio verlo en un par de screenshots.

OffT: Una ves q descargo todas las actualizaciones se instalan solas?

---

### Post by kbzon_v8 on 2008-10-29
Hay diferentes clientes de mensajeria para Ubuntu, como aMsn o Pidgin que viene instalado por defecto, por lo menos en Hardly Heron. No si si habra uno con la interfaz igual al MSN. 

las actualizaciones una vez que le das a descargar te baja los paquetes y cuando termina de bajarlo le das a instalar y listo.

Sino te vas a:

Sistema > Administración > Orígenes de Software > Actualizaciones > Actualizaciones Automáticas

Y seleccioná:  "Instalar actualizaciones de seguridad sin confirmación".

Espero que te sirva.
Saludos!

---

### Post by Aspergillus on 2008-10-29
Para clientes de mensajeria instantanea lease msn, te recomiendo ahora que sos nuevo que uses "Pidgin" que ya viene instalado, una vez que empieces a ver como agregar programas al source y tal que instales "emesene"

programas para escuchar musica, si queres alguno con la interfaz parecida al winamp de toda la vida abris una terminal escribis "sudo synaptic" y una vez dentro con "Ctrl+F" buscas el Audacious o sino Xmms el que quieras y lo marcas para instalar y lo instalas, fijate que ademas para esos programas en el mismo synaptic te va a tirar para instalarle varios plugins interesantes

---

### Post by Just64 on 2008-10-29
> **kbzon_v8 said:**
> Hay diferentes clientes de mensajeria para Ubuntu, como aMsn o Pidgin que viene instalado por defecto, por lo menos en Hardly Heron. No si si habra uno con la interfaz igual al MSN. 

las actualizaciones una vez que le das a descargar te baja los paquetes y cuando termina de bajarlo le das a instalar y listo.

Sino te vas a:

Sistema > Administración > Orígenes de Software > Actualizaciones > Actualizaciones Automáticas

Y seleccioná:  "Instalar actualizaciones de seguridad sin confirmación".

Espero que te sirva.
Saludos!

Antes de seguir, estas modificaciones van a seguir vigentes cuando istale el Ubu 8.10? El 8.10 se baja como actualizacion mas o tengo q reinstalar?

Eso se aplica a las descargas q hice antes de modificar esa opcion? Osea, las descargas q hice sin haber tildado esa opcion, se van a instalar solas o las tengo q instalar yo?

Ya baje el Audacious, ahora como lo instalo? En caso de q se instale solo donde esta el programa?

Tambien baje el aMsn, pero al intentar instalarlo aparece este error:
[[IMG]http://img402.imageshack.us/img402/5156/pantallazoor3.th.jpg[/IMG]](http://img402.imageshack.us/my.php?image=pantallazoor3.jpg)[[IMG]http://img402.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Sudo se utiliza para ejecutar programas?

Disculpen x la preguntas tan obvias para la moyoria seguramente pero tengo menos de 24 horas en el Ubuntu.

---

### Post by faktorqm on 2008-10-29
Hola y bienvenido al foro. 2 cosas para instalar programas:

1) Sistema -> administracion -> gestor de paquetes synaptic
Ahi pones, primero recargar, luego buscar, y pones el nombre del programa que queres buscar, le das doble click y te lo instala junto con sus dependencias sin tocar nada todo automatico.

2) Aplicaciones -> añadir y quitar. Es un toque mas explicativo que el anterior, pero tiene menos appz para elegir. Pero te dice que es cada una digamos, con una puntuacion, todo. 

Espero te haya sido de ayuda, Cualquier cosa no dudes en preguntar. Salu2!

---

### Post by Just64 on 2008-10-29
> **faktorqm said:**
> Hola y bienvenido al foro. 2 cosas para instalar programas:

1) Sistema -> administracion -> gestor de paquetes synaptic
Ahi pones, primero recargar, luego buscar, y pones el nombre del programa que queres buscar, le das doble click y te lo instala junto con sus dependencias sin tocar nada todo automatico.

2) Aplicaciones -> añadir y quitar. Es un toque mas explicativo que el anterior, pero tiene menos appz para elegir. Pero te dice que es cada una digamos, con una puntuacion, todo. 

Espero te haya sido de ayuda, Cualquier cosa no dudes en preguntar. Salu2!

Funciono exelente! Gracias!

Me queda una pregunta pendiente: 
El Ubuntu 8.10 se instala como actualizacion o ahy q reistalar el ubuntu entero?

---

### Post by hictio on 2008-10-29
> **Just64 said:**
> Funciono exelente! Gracias!

Me queda una pregunta pendiente: 
El Ubuntu 8.10 se instala como actualizacion o ahy q reistalar el ubuntu entero?

Podes de las dos formas, o bajar el CD, o hacerlo desde el propio 8.04.
Es mas "limpio", si aplica el termino, hacer backup de lo que tenes, bajar el CD con 8.10, e instalar arriba de la anterior, desde cero.

Tambien podes, cuando instalas, crear una particion separada para el /home/, que es donde se guardan los archivos de los usuarios, '/home/raul', '/home/pampita', etc.
Asi, si haces una instalacion a otra version de Ubuntu, o de otro Linux, podes indicar al instalador que no formatee esa particion, asi guardas toda la data de update a update.

Por supuesto, todos los programas, que normalmente van a otros directorios del sistema, tenes que re-instalarlos.

---

### Post by Just64 on 2008-10-29
Pero si bajo el CD y me lo pongo a instalar, el mimso Ubu 8.10 va a reconocer q tengo instalado el 8.04 y va a "pisar" a este ultimo e instalar el 8.10, reemplazando el 8.04? O ahy alguna otra forma mejor? No me importa perder las cosas q modifique/agregue al 8.04 xq recien lo habre podido usar como mucho 5 horas, entre el laburo y la facu...

Otra cosa, entro a la terminal, la pongo en modo tradicional de pantalla completa,(crt + alt + f1) y dsp no se q sentencia poner para poder salir de la terminal. Tengo q reiniciar la PC.

---

### Post by hictio on 2008-10-29
> **Just64 said:**
> Pero si bajo el CD y me lo pongo a instalar, el mimso Ubu 8.10 va a reconocer q tengo instalado el 8.04 y va a "pisar" a este ultimo e instalar el 8.10, reemplazando el 8.04? O ahy alguna otra forma mejor? No me importa perder las cosas q modifique/agregue al 8.04 xq recien lo habre podido usar como mucho 5 horas, entre el laburo y la facu...

Otra cosa, entro a la terminal, la pongo en modo tradicional de pantalla completa,(crt + alt + f1) y dsp no se q sentencia poner para poder salir de la terminal. Tengo q reiniciar la PC.

Tenes particiones en tu disco actual? Digo para Ubuntu? O esta todo instalado en una sola particion?
Calculo que una instalacion normal, si no le das ningun parametro te va a formatear todo, e instalar arriba, especialmente si no hay particiones en el sistema (una para /home, otra para /usr, para /tmp, etc), pero la verdad no te lo podria asegurar, porque todas las instalaciones de Ubuntu que hice las hice con la herramienta de particion, no se si es el Disk Druid, de forma manual.

Para volver al entorno grafico, tipea Ctrl + Alt + F7

---

### Post by faktorqm on 2008-10-30
> **hictio said:**
> Tenes particiones en tu disco actual? Digo para Ubuntu? O esta todo instalado en una sola particion?
Calculo que una instalacion normal, si no le das ningun parametro te va a formatear todo, e instalar arriba, especialmente si no hay particiones en el sistema (una para /home, otra para /usr, para /tmp, etc), pero la verdad no te lo podria asegurar, porque todas las instalaciones de Ubuntu que hice las hice con la herramienta de particion, no se si es el Disk Druid, de forma manual.

Para volver al entorno grafico, tipea Ctrl + Alt + F7

Jo! Disk Druid le batio! que maestro! Lo ultimo que me acuerdo de eso es un red hat 9... 
Ubuntu usa una modificacion del parted para la instalacion, y el alternate usa el particionador del Debian. 
Deja 10gb para el "/", el doble de tu ram para el swap, y el resto para tu "/home". Si queres mas detalle busca en el foro que esta lo explicamos mil veces. Salu2!

---

### Post by hictio on 2008-10-30
> 
Jo! Disk Druid le batio! que maestro! Lo ultimo que me acuerdo de eso es un red hat 9... 


Hiciste que me sienta viejo :p :D

*Vieca!! Vieca!! la pastilla!!! Vieca*

---

### Post by Just64 on 2008-10-30
Leyendo la guia del ubuntu lei esto:

> **Guia Ubuntu said:**
> #  Para una correcta actualización, asegúrate de que tienes instalado el paquete:

   1. si usas Ubuntu: ubuntu-desktop 

Como se si tengo dicho paquete?

---


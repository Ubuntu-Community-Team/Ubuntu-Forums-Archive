---
title: "Virtual Box Ubuntu 8.10"
date: 2009-03-31
forum: Software
---

### Post by talamilla on 2009-03-31
Hola amigos según lo que podido ver es posible correr windows desde ubuntu usando Virtual Box, pero no he visto que se pueda correr un windows preinstalado, al parecer VBox permite instalarlo y correrlo desde la maquina virtual, pero quisiera correr el xp que instale antes que UBUNTU, estoy migrando y para algunas cosas tengo que reiniciar y arrancar windows para luego volver a ubuntu, y asi sucesivamente. Les recuerdo que apenas llevo unos dias con ubuntu, he logrado poner barras de iconos, compiz, etc... y me esta gustando trabajar desde allí, en fin espero algun aporte, saludos):P

---

### Post by guillermolisi on 2009-03-31
> **talamilla said:**
> Hola amigos según lo que podido ver es posible correr windows desde ubuntu usando Virtual Box, pero no he visto que se pueda correr un windows preinstalado, al parecer VBox permite instalarlo y correrlo desde la maquina virtual, pero quisiera correr el xp que instale antes que UBUNTU, estoy migrando y para algunas cosas tengo que reiniciar y arrancar windows para luego volver a ubuntu, y asi sucesivamente. Les recuerdo que apenas llevo unos dias con ubuntu, he logrado poner barras de iconos, compiz, etc... y me esta gustando trabajar desde allí, en fin espero algun aporte, saludos):P
Me parece, y digo me parece porque no termine de buscar documentacion al respecto, que en el mejor de los casos podrias importar la maquina Windows real al entorno de VBox para usar esa instalacion (que en realidad terminaria siendo una copia del preinstalado).

Si se pueden migrar imagenes de VMs de un VMware a VBox, por ejemplo, pero migrar de una instalacion tipica hasta aqui no tengo leido nada.

En el peor de los casos vas a tener que hacer backup de los archivos que quieras preservar, instalar una nueva instancia de WinXP dentro de VBox y restaurar ese backup en la nueva maquina Windows (VBox). Los programas que utilices actualmente los deberas volver a instalar en esa nueva maquina.

---

### Post by talamilla on 2009-03-31
> **guillermolisi said:**
> Me parece, y digo me parece porque no termine de buscar documentacion al respecto, que en el mejor de los casos podrias importar la maquina Windows real al entorno de VBox para usar esa instalacion (que en realidad terminaria siendo una copia del preinstalado).

Si se pueden migrar imagenes de VMs de un VMware a VBox, por ejemplo, pero migrar de una instalacion tipica hasta aqui no tengo leido nada.

En el peor de los casos vas a tener que hacer backup de los archivos que quieras preservar, instalar una nueva instancia de WinXP dentro de VBox y restaurar ese backup en la nueva maquina Windows (VBox). Los programas que utilices actualmente los deberas volver a instalar en esa nueva maquina.

Pues es muy buena idea, podria usar norton ghost con un Clon liviano y restaurarlo dentro de VBox, el unico problema es que mi Clon actual es algo pesado por cantidad de programas, haré un nuevo clon e intentaré. Una preguntita mas.... es necesario tener una maquina muy poderosa para hacer eso?(seguramente dependerá de lo que tenga instaldo en el clon) saludos

---

### Post by josecuervo86 on 2009-03-31
Mira, me parece que encontre la solución, pero implica el uso de software cerrado, asique no se si se puede poner el link. Igual me aparecio en google con un par de tags bastante simples.

En cuanto a la maquina; va a depender de lo que tengas instalado en windows. Yo he emulado en una notebook de 512 de ram con un window$ bastante recortado

---

### Post by guillermolisi on 2009-03-31
> **josecuervo86 said:**
> Mira, me parece que encontre la solución, pero implica el uso de software cerrado, asique no se si se puede poner el link. Igual me aparecio en google con un par de tags bastante simples.

En cuanto a la maquina; va a depender de lo que tengas instalado en windows. Yo he emulado en una notebook de 512 de ram con un window$ bastante recortado
A que te referis con "software cerrado" ?
Es software propietario pero libre o es software cuyo uso requiere de una licencia paga ?

Si es software propietario y puede solucionar el requerimiento que se plantea no hay ningun problema en darlo a conocer.

De hecho NortonGhost es propietario y requiere de una licencia.

Por otra parte no veo el uso del Ghost como alternativa factible ya que necesita que el disco de la VM este particionado para bajar la imagen (y para eso habra que instalar un SO antes, asi que estamos en mas o menos la misma situacion que comente antes).

Mi recomendacion para una buena experiencia con Vbox es algun procesador de doble nucleo y 1Gb RAM.

---

### Post by talamilla on 2009-03-31
> **guillermolisi said:**
> A que te referis con "software cerrado" ?
Es software propietario pero libre o es software cuyo uso requiere de una licencia paga ?

Si es software propietario y puede solucionar el requerimiento que se plantea no hay ningun problema en darlo a conocer.

De hecho NortonGhost es propietario y requiere de una licencia.

Por otra parte no veo el uso del Ghost como alternativa factible ya que necesita que el disco de la VM este particionado para bajar la imagen (y para eso habra que instalar un SO antes, asi que estamos en mas o menos la misma situacion que comente antes).

Mi recomendacion para una buena experiencia con Vbox es algun procesador de doble nucleo y 1Gb RAM.

José: a que soft haces referencia? no creo que este prohibido poner el nombre.


Guillermo: Tienes rozón luego de pensar un momento me di cuenta de que NGhost no es una opción. Tengo 2 gb de ram y un doble núcleo, creo que mi problema seria el espacio a usar en mi disco de 150 gb, ya que Ubuntu esta en una partición de 10, 40 gb para WinXP y el resto es para mis archivos personales.

---

### Post by josecuervo86 on 2009-03-31
Gracias por la aclaración Guillermo, mira aca[0] te dejo el link de Taringa! donde te muestra como hacer lo que queres (creo)

Pasa que es la versión cerrada de VirtualBox la que te permite hacer eso y estaba en un dilema moral, que por error traslade al foro :)

[0][http://www.taringa.net/posts/linux/1611488/Virtualizar-particion-existente-de-Windows-en-Linux!!!.html]("http://www.taringa.net/posts/linux/1611488/Virtualizar-particion-existente-de-Windows-en-Linux!!!.html")

---

### Post by guillermolisi on 2009-03-31
> **josecuervo86 said:**
> Gracias por la aclaración Guillermo, mira aca[0] te dejo el link de Taringa! donde te muestra como hacer lo que queres (creo)

Pasa que es la versión cerrada de VirtualBox la que te permite hacer eso y estaba en un dilema moral, que por error traslade al foro :)

[0][http://www.taringa.net/posts/linux/1611488/Virtualizar-particion-existente-de-Windows-en-Linux!!!.html]("http://www.taringa.net/posts/linux/1611488/Virtualizar-particion-existente-de-Windows-en-Linux!!!.html")
No tenes que tener ningun dilema porque no hay tal cosa.
VBox tiene su edicion comunitaria, OSE, y la propietaria que se diferencian por su tipo de licencia y funcionalidades, pero ningun gatito se muere porque alguien use la version propietaria de un software que le resuelve un requerimiento (si asi fuera no habria ya mas gatos vivos, solamente por usar los drivers nVidia quedarian algunos pocos maullando).

El problema no esta en usar o no usar sino en que empresas como nVidia no terminan de comprender cual es el nuevo paradigma en el cual deben moverse y como suscribirlo sin que sus competidores tengan acceso a tecnologia competitiva y sensiblemente diferencial para copiarlos.

En todo caso son decisiones personales usar o no sotware privativo, una ventaja mas del SL.

---

### Post by talamilla on 2009-03-31
Muchas gracias a ambos, voy a seguir los consejos de amigo taringuero y lo voy a probar por primera ves en mi desktop que no tiene muchas cosas importantes, saludos les avisaré como me fue. Saludos

---

### Post by josecuervo86 on 2009-03-31
De nada capo! mucha suerte

---

### Post by talamilla on 2009-04-01
Una pregunta mas... por que se cambio el color del foro en esta discusión.?

---

### Post by Hei Ku on 2009-04-01
Es 1ro de Abril, conocido en el norte como "April's Fool". Algo similar al Día de los Inocentes nuestro. Los sites suelen hacer distintas bromas, entre esas poner este color horrible.

---

### Post by talamilla on 2009-04-01
> **Hei Ku said:**
> Es 1ro de Abril, conocido en el norte como "April's Fool". Algo similar al Día de los Inocentes nuestro. Los sites suelen hacer distintas bromas, entre esas poner este color horrible.

Jejejeje, si sabia del 1 de abril mi XP SP3 según he leído no me hiba a afectar, sin embargo nunca se sabe. Saludos

---

### Post by sebastianabate on 2009-04-01
No es para nada necesario usar un software privativo para hacer lo que necesitás (excepto el Windows que querés virtualizar, claro)

Lo único que necesitás es una imágen de CD de Ubuntu Desktop, el VirtualBox, y el CD de instalación de tu XP.

Lo que tenés que hacer es crear un disco virtual en el VB que apunte a tu disco físico desde una consola, así:

VBoxManage internalcommands createrawvmdk -filename /home/tu_usuario/VirtualBox/disco_WindowsXP_Real/xpreal.vdmk -rawdisk /dev/sdb -register

donde /dev/sdb es el disco físico donde está instalado el XP, y /home/tu_usuario/VirtualBox/disco_WindowsXP_Real es un lugar temporal.

Después creás una nueva VM en VB para un Ubuntu, con un disco virtual con la misma capacidad que el disco real tiene ocupada actualmente más unos cuantos gigas para futuro crecimiento) y la memoria que creas conveniente para tu XP virtualizado, y después le agregas como segundo disco el disco que creaste en el paso anterior (xpreal.vdmk). Configurás la VM para que arranque desde la imagen de CD del Ubuntu, y sólo desde CD (deshabilitá el resto de las opciones, esto es muy importante), y arrancás la VM.

Una vez que arrancó Ubuntu ejecutás el Partition Editor y copiás la partición del Windows XP del disco real al disco virtual. Cuando termina de copiar apagás la VM.

Acto seguido reconfigurás la VM para que sea un Windows XP, le quitás el disco real creado con el primer comando (xpreal.vdmk), quedando únicamente el disco virtual recién clonado; y la configurás para que monte el CD de instalación del XP (en vez de la imágen del CD de Ubuntu); también seleccionás el disco rígido como segunda opción en el orden de booteo (después del CD).

Cuando volvés a arrancar la VM presionás cualquier tecla para que arranque la instalación de Windows XP (cuando te aparezca la leyenda en pantalla) y hacés una reparación/reinstalación del XP (pisando la anterior, sin formatear por supuesto, para que te mantenga todas tus configuraciones y aplicaciones previas); luego de reinstalar aplicás todos las actualizaciones y parches que encuentres con Windows Update, sacás el CD de XP de tu lectora, reiniciás la VM, instalás los Guest additions, y voilá!!! Tenés tu XP "Real" virtualizado en VirtualBox.

Este proceso es lento, engorroso y muy tedioso; pero te aseguro que funciona, yo lo hice con me vieja instalación de XP cuando me pasé definitivamente a Ubuntu y lo tuve un tiempo para ir rescatando las cosas que necesitaba. Al poco tiempo ya lo había borrado de mi máquina.[I]

PD: espero haber sido lo suficientemente claro con la explicación y no haberme saltado ningún paso. Si tenés cualquier duda consultá bien antes de empezar con el proceso, y por supuesto asegurate de tener un Backup al día antes de empezar.
[/I]

---

### Post by guillermolisi on 2009-04-01
> **sebastianabate said:**
> No es para nada necesario usar un software privativo para hacer lo que necesitás (excepto el Windows que querés virtualizar, claro)

Lo único que necesitás es una imágen de CD de Ubuntu Desktop, el VirtualBox, y el CD de instalación de tu XP.

Lo que tenés que hacer es crear un disco virtual en el VB que apunte a tu disco físico desde una consola, así:

VBoxManage internalcommands createrawvmdk -filename /home/tu_usuario/VirtualBox/disco_WindowsXP_Real/xpreal.vdmk -rawdisk /dev/sdb -register

donde /dev/sdb es el disco físico donde está instalado el XP, y /home/tu_usuario/VirtualBox/disco_WindowsXP_Real es un lugar temporal.

Después creás una nueva VM en VB para un Ubuntu, con un disco virtual con la misma capacidad que el disco real tiene ocupada actualmente más unos cuantos gigas para futuro crecimiento) y la memoria que creas conveniente para tu XP virtualizado, y después le agregas como segundo disco el disco que creaste en el paso anterior (xpreal.vdmk). Configurás la VM para que arranque desde la imagen de CD del Ubuntu, y sólo desde CD (deshabilitá el resto de las opciones, esto es muy importante), y arrancás la VM.

Una vez que arrancó Ubuntu ejecutás el Partition Editor y copiás la partición del Windows XP del disco real al disco virtual. Cuando termina de copiar apagás la VM.

Acto seguido reconfigurás la VM para que sea un Windows XP, le quitás el disco real creado con el primer comando (xpreal.vdmk), quedando únicamente el disco virtual recién clonado; y la configurás para que monte el CD de instalación del XP (en vez de la imágen del CD de Ubuntu); también seleccionás el disco rígido como segunda opción en el orden de booteo (después del CD).

Cuando volvés a arrancar la VM presionás cualquier tecla para que arranque la instalación de Windows XP (cuando te aparezca la leyenda en pantalla) y hacés una reparación/reinstalación del XP (pisando la anterior, sin formatear por supuesto, para que te mantenga todas tus configuraciones y aplicaciones previas); luego de reinstalar aplicás todos las actualizaciones y parches que encuentres con Windows Update, sacás el CD de XP de tu lectora, reiniciás la VM, instalás los Guest additions, y voilá!!! Tenés tu XP "Real" virtualizado en VirtualBox.

Este proceso es lento, engorroso y muy tedioso; pero te aseguro que funciona, yo lo hice con me vieja instalación de XP cuando me pasé definitivamente a Ubuntu y lo tuve un tiempo para ir rescatando las cosas que necesitaba. Al poco tiempo ya lo había borrado de mi máquina.[I]

PD: espero haber sido lo suficientemente claro con la explicación y no haberme saltado ningún paso. Si tenés cualquier duda consultá bien antes de empezar con el proceso, y por supuesto asegurate de tener un Backup al día antes de empezar.
[/I]
Sebastian

Te animas a revisar tu explicacion para generar un tutorial y publicarlo en la seccion de tutos del website de Ubuntu-ar dentro de un corto/mediano plazo ?

Creo que a mas de uno le va a venir de primera contar con alternativas como esta al momento de decidir abandonar Windows.

---

### Post by sebastianabate on 2009-04-01
> **guillermolisi said:**
> Sebastian

Te animas a revisar tu explicacion para generar un tutorial y publicarlo en la seccion de tutos del website de Ubuntu-ar dentro de un corto/mediano plazo ?

Creo que a mas de uno le va a venir de primera contar con alternativas como esta al momento de decidir abandonar Windows.

Nunca hice ningún tutorial, pero siempre hay una primera vez para todo ;). Voy a aprovechar el feriado de mañana para empezar a revisar los pasos y verificar que no haya dejado nada de lado; y el fin de semana empiezo a darle forma y a capturar algunas pantallas. No te prometo un corto plazo, pero sí me comprometo a tenerlo en un mediano plazo.

PD: ¿Existe algún tutorial para armar tutoriales? ¿Alguna plantilla con un formato a respetar? ¿Límites en cuanto a espacio a ocupar (por el tema de las capturas de pantalla), restricciones en cuanto a material con copyright (por las capturas de pantalla de la instalación de Windows), o alguna otra cosa que tenga que tener en cuanta? Ya di de alta mi cuenta en Ubuntu-ar, pero no veo una opción para crear un nuevo tutorial, lo único que me deja crear es un story; ¿lo empiezo como un story y después algún moderador lo mueve a la parte de tutoriales?

---

### Post by guillermolisi on 2009-04-01
> **sebastianabate said:**
> Nunca hice ningún tutorial, pero siempre hay una primera vez para todo ;). Voy a aprovechar el feriado de mañana para empezar a revisar los pasos y verificar que no haya dejado nada de lado; y el fin de semana empiezo a darle forma y a capturar algunas pantallas. No te prometo un corto plazo, pero sí me comprometo a tenerlo en un mediano plazo.

PD: ¿Existe algún tutorial para armar tutoriales? ¿Alguna plantilla con un formato a respetar? ¿Límites en cuanto a espacio a ocupar (por el tema de las capturas de pantalla), restricciones en cuanto a material con copyright (por las capturas de pantalla de la instalación de Windows), o alguna otra cosa que tenga que tener en cuanta? Ya di de alta mi cuenta en Ubuntu-ar, pero no veo una opción para crear un nuevo tutorial, lo único que me deja crear es un story; ¿lo empiezo como un story y después algún moderador lo mueve a la parte de tutoriales?
SI te sirve de guia, cualquiera de los tutoriales recientemente publicados por Sismo puede ser una buena referencia.

En cuanto al formato no tienen mucha vuelta y decididamente es poner en palabras e imagenes lo mismo que uno experimento al hacer lo que se documenta en el tutorial (una buena forma es ir tomando nota de cada paso, con sus detalles, para luego terminar de darle forma y que sea entendible por otros.

Empezalo como Story, no lo publiques hasta que este terminado y despues lo ubico en la seccion correspondiente (ademas de actualizar el indice).
Ubicarlo donde va es una pavada.

Tambien podes usar un editor HTML y despues copias y pegas el source (asi va con todos los tags) en el story recien abierto.

Un consejo: las imagenes/screenshots que uses alojalas en servidores del tipo ImageShack, Photobucket, etc. y usas el link de acceso directo a cada archivo en el doc para que se resuelva y se muestre adecuadamente.

Cualquier inconveniente o duda no dejes de consultarme.

---

### Post by talamilla on 2009-04-03
Muchas gracias por las respuestas, estuve intentando con el tuto de taringa pero esa version del VBox al parecer no esta para UBUNTU INTREPID. Seguiré  investigando, y esperando el tuto de sebas. saludos

---

### Post by josecuervo86 on 2009-04-03
Capo, anduve buscando y hay una version para Intrepid, bajatela de aca [0]

[0][http://dlc.sun.com/virtualbox/vboxdownload.html#linux]("http://dlc.sun.com/virtualbox/vboxdownload.html#linux")

---

### Post by talamilla on 2009-04-03
> **josecuervo86 said:**
> Capo, anduve buscando y hay una version para Intrepid, bajatela de aca [0]

[0][http://dlc.sun.com/virtualbox/vboxdownload.html#linux]("http://dlc.sun.com/virtualbox/vboxdownload.html#linux")

Gracias, ya mismo lo descargo pruebo... jeje.
saludos

---


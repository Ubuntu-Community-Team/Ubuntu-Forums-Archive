---
title: "Instalar Ubuntu"
date: 2013-04-18
forum: Software
---

### Post by becerro on 2013-04-18
Bueno antes que nada les comento que soy nuevo en el foro y deseo entrar en el mundo de ubuntu xD, lo e intentado instalar 1 ves, no lo pude lograr, hoy aquí con ustedes tengo fe que voy a poder.
 Les dejo algunos datos de mi maquina quiero saber si puedo llegar a tener algún inconveniente con mi pc, me gustaría que me den tips para tener en cuenta durante la instalación.


mother ecs p4m800pro-m478
ram 1.5 gb
micro intel pentium 4
via/s3g unichrome pro ip




 Desde ya muchas gracias saludos.

---

### Post by papibe on 2013-04-18
Bienvenido al foro, becerro! ):P

Las últimas versiones de Ubuntu han sido diseñadas para computadoras mas nuevas. Dado que tu computadora tiene unos años, te recomiendo una versión differente: [Xubuntu]("http://xubuntu.org/"). Esta versión es mucho más liviana en recursos y se va a sentir mucho más rápida en el hardware que tienes.

Recuerda visitar el foro seguido.
Saludos.

---

### Post by becerro on 2013-04-19
bueno muchas gracias, en la pagina descargo una iso del xubuntu, mi pregunta es si con el demonstool puedo levantarla e instalar xubuntu desde windows sin hacer un cd

---

### Post by papibe on 2013-04-20
No, no puedes instalar Ubuntu desde Windows, si no que tienes que bootear tu computadora desde el CD.

Primero crea el CD. Recuerda que tienes crearlo desde la imagen del ISO, y **no** un CD de datos en el que copias el ISO como un archivo.

Después tienes que entrar al BIOS de tu computador y configurarlo de que inicie desde el CDROM antes que el disco duro.

De esta manera cuando reinicies, deberia leer el CD y mostrarte el menu de instalación de Ubuntu.

Aclara un poco tus dudas?  Cuéntanos como te va.
Saludos.

---

### Post by gmunioz on 2013-04-20
Sumimasen por la intromisión:
Mi sugerencia es que instales Xubuntu 32 bits, con particionamiento manual en al menos tres particiones, una primaria activa, de entre 15 y 20 gigas, sistema ext4, punto de montaje /, una lógica, sistema de intercambio, de 1 giga, montaje por defecto, una lógica del resto libre del disco, sistema ext4, punto de montaje /home, el Grub en el mbr de /dev/sda.
Si piensas mantener Windows, es conveniente elimines ccleaner mediante todos los archivos basura, todas las aplicaciones innecesarias, que corras scandisk y defrag, antes de liberar espacio en el disco para instalar Xubuntu.
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.10/release/xubuntu-12.10-desktop-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.10/release/xubuntu-12.10-desktop-i386.iso)
Con unetbootin puedes hacer un pendrive booteable
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---


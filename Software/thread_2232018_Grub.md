---
title: "Grub"
date: 2014-06-29
forum: Software
---

### Post by Vero1 on 2014-06-29
Hola,

Uso Ubuntu 12.04.

Tengo un gran problema. Actualmente estoy escribiendo desde el LiveCD.
Hace 3 días vengo batallando para tener arranque.

La cuestión es ésta: 

Tengo un Disco de 500 Gib donde tengo instalado Ubuntu. En la partición orilginal que hice cuando lo instalé me había quedado espacio sin asignar.
Tenía otro disco con Windows pero ese disco murió.
Como me conviene, a veces, tener tambien Windows, quise instalarlo junto a Ubuntu. Sé que es conveniente hacer al revés, primero Windows y luego Ubuntu, pero se dió así.
Bueno, reparticioné el disco de manera que me quedara ese espacio sin asignar al final.( Aclaro que la partición Boot, que lo tengo aparte, su principio no se tocó para nada. Es la particiòn sda1.) Lo formateé como ntfs - 80 Gib. Inserté el disco de Windows pero instaló nada más que el 1%. No se pudo seguir más porque tambien el CD murió. Al quitar el CD y reiniciar, me salió una leyenda: error al cargar silstema operativo.
Supuse que había problemas con el Grub porque Windows se había apoderado del arranque. Usé el SuperGrubDisk2 pero no funcionó. Tambien el SuperGrubDisk (ya que había leído que podría servir igual) pero tampoco funcionó.
Usé boot-repair y no sirvió. Hice lo que dice el How-To de Ubuntu y tampoco sirvió. Traté de usar un programa de Ubuntu-guía para hacer Reset del Grub pero se me colgó en el medio.

He consultado con otras personas. He visto muchas entradas en Google pero nada sirve.

Lo último que hice antes de que el programa se colgara, fue eliminar el Grub(es el programa que menciono más arriba: Reset Grub ) y lo eliminé con la intención de re-instalarlo con ese mismo programa. De todas formas estaba sin Grub.

Teniendo en cuenta que soy Co-Administradora de una página en Facebook, ésto de no poder usar Ubuntu en forma normal me trae muchos inconvenientes, como supondrán.

Les agradecería mucho si me dan una mano con este problema y les agradezco de antemano.
p.d.

aquì el último resultado obtenido de boot-repair : [http://paste.ubuntu.com/7719007 ](http://paste.ubuntu.com/7719007 )  (ésto fué antes de eliminar Grub).

Por favor los e-mails a [email]veronicab647@hotmail.com[/email]     que es la dirección que puedo usar desde el LiveCD.

---

### Post by DaniPhii on 2014-06-29
Hola. :)

Cuando me ha pasado lo que a ti te ocurre, lo primero que pienso en hacer es recuperar todos mis datos en un HDD externo y reescribir la tabla de particiones por completo. También lo que hago yo es instalar GRUB en el disco en cuestión, no en una de sus particiones (es decir, yo lo instalaría en /dev/sda en lugar de en /dev/sda1, ya que me da menos problemas). Y en unas circunstancias así, yo aprovecharía para instalar Ubuntu 14.04 ya que estamos.

Cuando te refieres a que el CD ha muerto, ¿quieres decir el lector o el disco? Yo haría una memoria USB de arranque para instalar Windows y otra para Ubuntu 14.04.

No sé si te he ayudado, pero es lo que yo haría.

---

### Post by Vero1 on 2014-07-01
Hola :-)

Agradezco tu comentario pero al no tener Grub no puedo recuperar nada.  Aparte Windows no está instalado porque lo eliminé con GParted.

Cuando me refiero a que el CD ha muerto, me refiero al CD porque si fuera la lectora no podría estar escribiendo desde el Live CD.

Saludos

---


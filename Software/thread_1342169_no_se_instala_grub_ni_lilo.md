---
title: "no se instala grub ni lilo"
date: 2009-11-30
forum: Software
---

### Post by el_baby on 2009-11-30
Hola gentes...

estoy tratando de instalar un ubuntu 8.04 mínimo en una PC con 2gb de RAM y disco SATA de 160Gb... estoy usando el "mini CD" que pasé a un USB con unetbootin.

El tema es que el USB bootea OK, se instala sin mayores problemas, pero cuando tiene que instalar GRUB dice:

[!!] Install the GRUB boot loader on a hard disk
Installation step failed

Volví al menú e intenté nuevamente, pero siempre da igual... probé con LILO, tanto en el MBR como en la partición /dev/sdb1, pero sin éxito...

Googleé un poco pero en todos los casos era problema de máquinas muy chicas o de poco espacio en disco, cosa que yo no tengo... ¿alguno tiene alguna idea de para donde agarrar?

Desde ya, muchas gracias.

---

### Post by guillermolisi on 2009-11-30
Aparenta ser alguna diferencia de identificacion del disco rigido por parte del instalador.
Es decir, el instalador intenta grabar Grub/LILO en el MBR de /dev/hda pero ese disco SATA se reconoce como /dev/sda, por ejemplo.

Cuando quiere grabar el MBR no encuentra ninguna unidad y patea el proceso con ese mensaje de error.

Podras verificar donde quiere grabar el MBR y como identifica la maquina al disco SATA (fdisk por ejemplo) ?

/dev/sdb1 a que pertenece, a un medio de la PC ? Al pendrive ?

---

### Post by el_baby on 2009-11-30
> **guillermolisi said:**
> Podras verificar donde quiere grabar el MBR y como identifica la maquina al disco SATA (fdisk por ejemplo) ?
¿cómo averiguo dónde quiere grabar el MBR?

> **guillermolisi said:**
> /dev/sdb1 a que pertenece, a un medio de la PC ? Al pendrive ?
Ya no me acuerdo bien... estoy empezando de 0 de nuevo... 

En princpio lo que veo abriendo la consola con alt-f2 es que detecta como /dev/sda al pendrive que estoy usando para instalar y como /dev/sdb al disco interno...

---

### Post by guillermolisi on 2009-11-30
> **el_baby said:**
> ¿cómo averiguo dónde quiere grabar el MBR?

Normalmente en el momento en que te pregunta si queres grabar Grub en el MBR o en / directory deberia mostrarte/darte la posibilidad de indicarle en que medio de almacenamiento hara esa operacion y ahi cambias por la denominacion correcta (por eso mi pregunta sobre como identifica al disco rigido y poder diferenciarlo del pendrive u otro medio similar).

Estaba pensando que cuando entras en la etapa del particionador tenes vista de como identifica la unidad de disco (y sus particiones)

---

### Post by el_baby on 2009-11-30
Mmmmhhhh... paremos un cacho... ya traté un par de veces y ahora se me colgó en distintos lugares... me parece que el disco tiene algún moco físico... ¿alguien conoce algo piola para chequear un disco físicamente? debería ser booteable...

---

### Post by guillermolisi on 2009-11-30
> **el_baby said:**
> Mmmmhhhh... paremos un cacho... ya traté un par de veces y ahora se me colgó en distintos lugares... me parece que el disco tiene algún moco físico... ¿alguien conoce algo piola para chequear un disco físicamente? debería ser booteable...
Ojo que nos vamos de topico con esto ultimo ... y si abris un thread especifico en Hardware (los discos se pueden patear) y despues seguimos con este ?

---

### Post by el_baby on 2009-12-01
Tenés razón... y al final ERA el hardware... pero no el disco... estaba dañada la RAM... la chequeé con el memory test al bootear el CD y mandó basura... cambié el DIMM y anduvo...

---


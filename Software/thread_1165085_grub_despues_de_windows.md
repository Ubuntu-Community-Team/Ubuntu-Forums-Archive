---
title: "grub despues de windows"
date: 2009-05-20
forum: Software
---

### Post by joseluis on 2009-05-20
hola..imagino que este tema ya habrá sido tratado, pero el tema es el siguiente.
tengo en un disco maestro windows xp y en uno exclavo ubuntu 9.04.
El grup anda bien (un poco lento, pero es otra historia).
el tema es que voy a tener que reinstalar el win y eso ocasionará, seguramente, la perdida del grub.
la pregunta es si es posible copiar el grub a una parte del disco para despues volver a pegarlo en su correspondiente lugar y asi no perderlo. Si esto se puede ¿en qué lugar lo encuentro?
si no se puede..¿como reinstalo despues el grub en el caso de desaparicion?
gracias

---

### Post by josecuervo86 on 2009-05-20
El grub se encuentra en /boot/grub y lo que tenes que copiar es el contenido del archivo menu.lst.

---

### Post by staar on 2009-05-20
la reinstalación de Ventanas va a sobreescribir la MBR, un lugar especial al inicio del disco, que es donde se aloja GRUB, pero no va a tocar la carpeta /boot/grub que es donde se alojan las configuraciones de este, asi que no es necesario que hagas un backup...

para reinstalar GRUB en la MBR, podés usar el SuperGrubDisk [http://www.supergrubdisk.org]("http://www.supergrubdisk.org"), un cd booteable que te permite hacerlo, por las configuraciones del dual boot no te preocupes, van a estar a salvo en la partición de ubuntu, y GRUB las va a tomar cunado lo reinstales...

OJO, todo esto funciona si solo reinstalás Ventanas, sin cambiar el orden de los discos, o agregar/quitar particiones, porque en ese caso puede que haya mambo con el menu.lst (el archivo de configuración principal de GRUB)

saludos

---

### Post by joseluis on 2009-05-20
bien...gracias...es lo que necesitaba

---


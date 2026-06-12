---
title: "Grub, Ubuntu y Win"
date: 2009-08-16
forum: Software
---

### Post by Rick58 on 2009-08-16
Buenos días a todos, mi primer post en el foro... 
Les presento la situación:  un pc con dos discos duros, en el maestro, una sola partición en ntfs con winxp y en el esclavo,  ubuntu 9.04 todo funcionando perfecto, con Grub para administrar el arranque dual. 
Quiero hacer lo siguiente: en el segundo disco, instalar un win 98, en un pequeño espacio y luego volver a instalar ubuntu. Se me ocurrió: particionar el segundo disco con fat32 (solo una parte) desde el win xp; luego inhabilitar el primer disco e instalar el win 98 en el segundo; habilitar nuevamente el primer disco, instalar ubuntu y que Grub maneje el arranque de los tres sistemas. 
Sería posible? o digo una burrada?
Aclaración: la opción de borrar el XP y empezar de cero, no va  (aunque sería lo correcto...)
Muchas gracias !!

---

### Post by guillermolisi on 2009-08-16
> **Rick58 said:**
> Buenos días a todos, mi primer post en el foro... 
Les presento la situación:  un pc con dos discos duros, en el maestro, una sola partición en ntfs con winxp y en el esclavo,  ubuntu 9.04 todo funcionando perfecto, con Grub para administrar el arranque dual. 
Quiero hacer lo siguiente: en el segundo disco, instalar un win 98, en un pequeño espacio y luego volver a instalar ubuntu. Se me ocurrió: particionar el segundo disco con fat32 (solo una parte) desde el win xp; luego inhabilitar el primer disco e instalar el win 98 en el segundo; habilitar nuevamente el primer disco, instalar ubuntu y que Grub maneje el arranque de los tres sistemas. 
Sería posible? o digo una burrada?
Aclaración: la opción de borrar el XP y empezar de cero, no va  (aunque sería lo correcto...)
Muchas gracias !!
En principio y respecto del Grub no veo razon para que no funcione como vos queres.

Lo que no recuerdo es si WinXP formatea FAT32 (hace mucho tiempo que no uso FAT32).

---

### Post by Rick58 on 2009-08-17
Gracias por tu respuesta. En cuanto a formatear desde XP, ahora tampoco recuerdo, creo que sí se puede, pero de última, ese no sería el problema porque borro las particiones y luego con un disco de inicio de win y fdisk lo formateo. Mi duda principal era en cuanto a la instalacion del Win 98 en un segundo disco, cómo iba a afectar una vez que habilite los dos discos nuevamente en la bios...

---

### Post by guillermolisi on 2009-08-17
Cuando hagas esa instalacion en el segundo disco, Win98 grabara en el MBR de esa unidad.

Luego, cuando instales Ubuntu, deberia detectar que hay otros sistemas operativos e incluirlos en el Grub que podes determinar grabarlo en el MBR del primer disco o del segundo disco. Para grabr el Grub en el MBR del primer disco, este tiene que estar on line al momento de la instalacion.

Si el primer disco al momento de la instalacion de Ubuntu no esta disponible, no detectara los SOs que existan en el. Vas a tener que agregarlos a mano o elegir con las opciones de inicio del BIOS desde que disco inicias la maquina.

---

### Post by Rick58 on 2009-08-17
Ok, Guillermo, muchas gracias!
Será cuestión de ponerse manos a la obra.
Un saludo

--
Ric

---


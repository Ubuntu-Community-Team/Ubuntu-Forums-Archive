---
title: "Agrandar partición raíz (tengo 15gb de espacio libre sin asignar)"
date: 2009-11-12
forum: Software
---

### Post by nahuel_89p on 2009-11-12
Bueno gente, es eso del título. Tengo ubuntu karmic.
Desde el gparted me sale esto:

Tengo 1 disco duro, con las siguientes particiones:

**/dev/sda1/**  (esta es la particion mas grande, de 80 gb, de sistema NTFS, donde tengo peliculas y musica)
**/dev/sda2/** (Adentro de esta partición tengo varias particiones: )
--**/dev/sda8/** (mi directorio raíz /... de 15 gb, Ext3)
--**/dev/sda9/** (una swap)
--**/dev/sda5/** (otra swap)
--**/dev/sda6/** (una partición ext3 de 300 mb, la reduje completamente porque no quería borrarla y hacer macana)
--**sin asignar** 15GB libres
--**/dev/sda7/** (otra swap)


En fin, la idea es agrandar mi directorio raíz esos 15gb libres. Pero es raro porque el gparted me pediría desmontarla, y me huele mal eso de desmontar el directorio raíz... como lo hago? desde algun livecd? tengo riesgos de arruinar el arranque aún si sigo las instrucciones fielmente?.
Bueno, es eso, agradezco cualquier sugerencia.

Ah, y otra cosa... como verán tengo un lío de particiones innecesarias. puedo corregir eso? me gustaria tener la particion NTFS, la partición raíz, y una swap nada mas.
Saludos.

---

### Post by aledruetta on 2009-11-13
En principio, yo eliminaría dos de las tres swap, dejando una con un equivalente a la mitad de la memoria RAM pero no más de un Gb (creo que era así) y también la partición de 300 Mb.

Y, a mi modo de ver, a los otros 15 Gb, les daría formato ext4 con Gparted y le asignaría /home como punto de montaje. Redimencionaría esa home, para aprovechar los espacios liberados de las swap y los 300 Mb. De esa forma te quedaría una swap, una raíz de 15 Gb y una home de 15 Gb.

Para hacer todo eso no necesitarías desmontar tu raíz y puedes hacerlo desde una sesión normal.

Edito: me corrijo. Al eliminar las particiones que te dije, como los 15 Gb no están asignados, lo que vas a tener es un espacio no asignado igual a la suma de todo eso. Así que, directamente, le das formato y punto de montaje /home, y ya está.

Me corrigen si estoy hablando pavadas.

---

### Post by gmunioz on 2009-11-14
Hola Nahuel:

Mi sugerencia es que previo a realizar alguna modificación:

Ejecutes en consola:

sudo fdisk -l

copies y pegues su salida

Y pegues el contenido de tu archivo

/etc/fstab

---

### Post by chamacocab on 2010-02-24
esto aplicaria para mi caso??

o que puedo hacer???

tengo un disco duro de 320gb en el cual tengo instalado windows y ubuntu solo que en ubuntu no tego suficiente espacio que tengo que hacer?? para asignarle mas espacio tengo 200Gb libres soy nuevo en ubuntu!!

gracias!!

---

### Post by Tosh78 on 2010-02-24
Para agregarle espacion a Ubuntu deberias iniciar con el live-cd. Una vez ahi, busca un programa llamado G-parted (Gestor de particiones) y vas a poder achicar la particion de Windows y agrandar la de Ubuntu. 
No puedo ayudarte mas, porque no das explicaciones de cual es tu caso.
Cualquier cosa volve a postear con mas info y te ayudamos.

---


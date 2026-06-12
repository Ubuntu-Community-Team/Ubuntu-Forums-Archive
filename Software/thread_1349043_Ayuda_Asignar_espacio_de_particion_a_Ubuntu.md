---
title: "Ayuda: Asignar espacio de particion a Ubuntu"
date: 2009-12-07
forum: Software
---

### Post by matias_tati on 2009-12-07
Hola bueno les cuento:
Tengo tres particiones: Una para Ubuntu, una para Windows y la otra es NTFS que uso para guardar datos.
Ahora quiero darle todo el espacio de la particion NTFS de datos a la particion de Ubuntu, ya que quiero tener todos mis datos en mi home.
Pero tengo algunas dudas:
Primero si se puede hacer
Si luego puedo acceder a mis datos desde windows....
Y si es conveniente hacerlo quizas tenga alguna contra que no considere.
Saludos!!!!

---

### Post by leonardomdq on 2009-12-07
Para gestionar particiones uso **GParted**, que lo podes instalar desde Synaptic.
Lo que no puede asegurarte si podes acceder a los datos que tengas en windows, pero calculo que si.
Seria bueno que algunos de los chicos que estan mas al tanto del tema te aseguren eso asi te quedas tranquilo..

Saludos
[B][URL="http://tuxpepino.wordpress.com/2007/06/13/gparted-gestiona-tus-particiones-graficamente/"]
[/URL][/B]

---

### Post by gmunioz on 2009-12-08
Hola leo....:
Si quieres continuar accediendo a tus datos desde Windows,
deja todo como esta,

Microsoft no da soporte para sistemas de archivos GnuLinux,
y los drivers existentes ni se acercan a la efectividad de
ntfs-3g de GnuLinux para el uso de particiones ntfs.

Si quieres acceder a tus datos, directamente desde /home,
simplemente haz un enlace en tu /home/usuario a la partición
ntfs, y trabajarás como si estuviera en tu /home/usuario (de
hecho lo esta, para eso son los enlaces)

---

### Post by matias_tati on 2009-12-08
O sea que es imposible acceder desde windows a una particion de linux?
Esto parece decir lo contrario
[http://www.cristalab.com/tips/como-acceder-a-particiones-de-linux-en-windows-xp-c50659l/](http://www.cristalab.com/tips/como-acceder-a-particiones-de-linux-en-windows-xp-c50659l/)
Y con los enlaces lo intente pasa que hay otro tema cada vez que boro algo debo borrarlo directamente no lo puedo mover a la papelera y es un poco molesto.

---

### Post by biale on 2009-12-08
Ext2ifs no funcionaba con particiones ext4 ni con particiones ext3 formateadas con inodos de 256 bits.

Pareciera que ext2fsd si funciona con particiones ext3 "inodo 256".

O sea que antes de hacer modificaciones habria que probar...

---

### Post by matias_tati on 2009-12-08
Si lo instale pero no funco.
Mis problemas con los enlaces son dos...
Primero que sigo sin poder mover archivos a la pepelera. Y otra que cada vez que abro el home con los enlaces los emblemas aprecen como cortados se ve horible. Deber ser un error de nautilus....

---

### Post by biale on 2009-12-08
Para que no haya problemas con los enlaces la partición NTFS debería estar montada desde el arranque y usando la fstab...

---

### Post by matias_tati on 2009-12-08
Y no podria montar mi particion dentro del home de alguna forma????
O me borraria el contenido del home?

---

### Post by guillermolisi on 2009-12-08
> **matias_tati said:**
> Y no podria montar mi particion dentro del home de alguna forma????
O me borraria el contenido del home?
Podes crearte un directorio para usarlo como punto de montaje dentro de tu /home.

Por ejemplo creas /home/matias/mis_datos_ntfs y montas esa particion NTFS con tus datos en el (es decir, cuando no tengas nada montado ese directorio estara vacio y cuado montes la particion veras todo su contenido).

De esa forma tendras todo lo de tu /home incluyendo lo de la particion NTFS (como si fuera el contenido de un directorio).

---

### Post by guillermolisi on 2009-12-09
> **matias_tati said:**
> Bueno lo hize con los enlaces. Pero esos empblemas que levan son feos feos, se pueden quitar de alguna forma?
Para no empiojar este thread, si esta resuelto por favor marcalo como tal.

Esta pregunta va en thread aparte, en Software.

---


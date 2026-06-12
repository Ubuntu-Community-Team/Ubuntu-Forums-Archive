---
title: "Modificar Tabla de particiones"
date: 2008-05-28
forum: Software
---

### Post by pol666 on 2008-05-28
Hola gente, hace poco modifique las particiones y pese a mi ignorancia aprendi que no puedo hacer mas de 4 particiones primarias por lo que movi unos archivos y pude particionar bien... ahora tengo pensado instalar una distribucion asi que voy a tener Modificar la tabla de particiones:



Actualmente es asi

[IMG]http://i29.tinypic.com/10qe3uw.png[/IMG]


Lo mejor seria poder realizar bien las particiones LOGICAS y PRIMARIAS
sin perder datos o tener que borrar alguna particion.

Ah y otra cosa, el espacio para hacer la ext3 donde se va a poner la nueva distro lo voy a sacar de "/" que tiene 18gb

Tambien se daran cuenta de lo mal que esta hecha la particion SWAP es un garabato de particiones que hice cuando empesaba en esto y nunca lo arregle

ASi que bueno aconsejenme como tengo que organizar mejor las particiones para que quede

-Windows 40gb
-/home 90gb
-/ con ubuntu 12gb
-/ con otra distro linux 6gb
-Swap con un poquito mas de 980 mb (osea redondearlo a 1gb)


A y otra preguntita: Para instalar otra distribucion en otra particion es necesario tener separada /boot en una particion aparte? en caso que no haga falta eso, Cuando instale la nueva distribucion el grub cambiara? (osea las configuraciones del grub, grub grafico, tiempo, ordemn de arranque etc)

---

### Post by juanman on 2008-05-29
Hola pol666, lo q yo haria sería:
1) Hacer un backup de datos importantes (siempre hay q hacerlos, xq como dijo Tusam, esto puede fallar :P)
2) Reiniciar con un live cd, cualquiera de ubuntu sirve
3) Con el gparted, borrar la particion swap y la extended
4) Redimensionar sda4 hasta 12gb
5) Crear nueva particion extended con todo el espacio libre
6) Crear particion logica (dentro de extended) de 6 gb para la otra distro
7) Crear swap con el espacio libre
8) Aplicar cambios y, si crees en Dios, rezá; si sos cabalero, cruzá los dedos o aplicá la cábala correspondiente :D
Naaa, no es tanto riesgo...

> Para instalar otra distribucion en otra particion es necesario tener separada /boot en una particion aparte? 

Nop, solo es recomendable en algunos casos, como por ej, si usas un filesystem medio loco, como xfs...

> en caso que no haga falta eso, Cuando instale la nueva distribucion el grub cambiara? (osea las configuraciones del grub, grub grafico, tiempo, ordemn de arranque etc)

Depende de la opcion q elijas en la instalacion de la nueva distro. Por defecto, la mayoria te instalan el gestor de arranque en el mbr, o sea, te tapa el grub anterior con sus configuraciones. No es mucho problema, entrando a la instalacion q tenia el viejo grub, se reinstala con un 
```
grub-install /dev/sda
``` y lo recuperas.
Sino en la instalacion de la nueva distro, elegis q instale el grub en la particion (/dev/sda5 en vez de /dev/sda por ej), pero creo q vas a tener q modificar el menu.lst del grub q ya tenias para agregarle la opcion de la nueva distro... 
Trabalenguas? Si no te quedó claro, chiflá :P

Saludos

---

### Post by pol666 on 2008-05-29
Ah pero creo que no me deja hacer una particion logica mas. para eso tengo que borrar otra...No la podre mover?


El / de ubuntu y el / de la "otra" distro y el NTFS lo queria poner en particiones primarias

el /home y la swap en lógica

Va bien? 

Con respecto al GRUB.. un lindo problema ese por que si yo instalo por ejemplo Slacware y me tapa el grub de ubuntu, Entre tneer qe lidiar con una distro nueva voy a tener que configurar el GRUB desde ahi, y me va a costar..

Me gustaria seguir usando el GRUB de ubuntu que ya tengo todo configurado

---


---
title: "Problemas navideños con las particiones"
date: 2008-12-24
forum: Software
---

### Post by ramiro_md on 2008-12-24
Gente ando con un problema de último momento. Resulta que por cuestiones que no van al caso me ví obligado a volver a instalar windows xp.
Cuando inicié el instalador de xp y borré la partición ntfs donde estaba instalado antigüamente xp y proseguí a instalar el sistema me salta diciendo "que ya agoté las partciiones disponibles para el disco" o algo así. Si bien tengo entendido solo se pueden tener 4 particiones por disco, pero con las ¿extendidas? se pueden tener 4 más, y me pareció raro que me diga eso porque yo tengo una extendida con dos particiones dentro...asique por ese lado flayo mal jejeje.
Hasta ahí no me preocupe mucho, porque pensaba entrar con el live cd de ubuntu y corrergir el tema particiones,pero al ingresar a gparted desde el live cd, gparted no me reconoce las partciiones, me toma todo el disco con espacio sin asignar (149 gb), lo cual me fue muy extraño porque desde el livecd pude ingresar a las particiones y ver los datos dentro de ellas, además ubuntu me bootea.
Realmente no tengo idea de cómo solucionar ese temita de gparted, de todos modos ubuntu me anda y por ahora no me hago dramas, pero no me pone feliz que gparted no me tome las particiones jeje.
SI alguien me puede dar una mano le estaré agradecido =) y que tengan una noche buena copada y una feliz navidad !!.

---

### Post by ramiro_md on 2008-12-27
Bueno gente, he investigado un poco más el tema, y por suerte no fui al único que le paso. Y googleando, encontré una herramienta llamada testdisk, entonces decidi instalarla desde el livecd y correrla siguiento este how to: [http://www.otrobloggeek.com/blog/2007/12/howto-recuperar-una-tabla-de-particiones-danada-con-mucha-suerte/](http://www.otrobloggeek.com/blog/2007/12/howto-recuperar-una-tabla-de-particiones-danada-con-mucha-suerte/).
La cosa es que si bien me recuperó una partición (de windows) que había eliminado, en gparted la tabla de particiones sigue sin aparecer :s
Tengo ganas de solucionar esto sin tener que formatear el disco ¬¬. Cualquier aporte es bienvenido, gracias.

---

### Post by faktorqm on 2008-12-28
mmm huelo algunos problemas ahi.

Comencemos por la teoria: En un disco con tabla de particiones MSDOS originalmente sólo se podian tener 4 particiones primarias. Existen otros tipos de tablas de particiones (sun solaris, para mac, etc), pero no es posible hacerlas booteables con un bios normal de pc (hasta lo que yo se). Luego se invento lo que se denomino particion extendida, que es una particion que en si no sirve de nada, solo alberga particiones logicas, esa es su unica funcion, a su vez, esta particion, ocupa el espacio de una primaria, por lo tanto, en un disco como maximo se puede tener 3 primarias, mas una extendida. 
Solo se puede tener una extendida por disco, y la extendida puede albergar como maximo 7 particiones logicas. (si mal no recuerdo)

Vamos por la practica: cuando reinstalas windows, tenes que reinstalar el grub, eso para la parte del booteo.
Para la parte de que no te gparted no te reconoce las particiones, es que por algun motivo no puede o no sabe leer la tabla de particiones. podes probar con acronis disk director o ranish partition manager y restaurar la copia del mbr al mbr original. (mucho ojo con esto) o algunos programas te dejan armar un mbr nuevo segun las particiones que tenes en el disco (testdisk, opcion mas recomendable y saludable para estas fiestas)
Para la parte de que no te deja crear particiones, revisa el tema de las primarias, extendidas, logicas, etc.

Si necesitas saber mas, aca podes llegar a encontrar algo, aunque bastante escueto para mi gusto [http://es.wikipedia.org/wiki/MBR](http://es.wikipedia.org/wiki/MBR)
Salu2!!!!

---

### Post by ramiro_md on 2008-12-28
GRacias Martin x la data, pero el tema es que bootear me bootea todo joya. El problema mio es que necesito tocar una partición y gparted no me recononce ninguna, me marga todo el disco con espacio sin asignar :s...y onda nada que ver porque puedo acceder a las particiones desde ubuntu y a sus datos, es más aca dejo la salida de fdisk -l:
```
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xec9bec9b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2568    20627428+   7  HPFS/NTFS
/dev/sda2            2569        4493    15462562+  83  Linux
/dev/sda3            4494        4748     2048287+  82  Linux swap / Solaris
/dev/sda4            4749       19458   118158075    f  W95 Ext'd (LBA)
/dev/sda5            4749        6042    10394023+  83  Linux
/dev/sda6            6043       19457   107755956    7  HPFS/NTFS

```
UN saludo y gracias.

---

### Post by faktorqm on 2008-12-29
La salida del comando que pasaste esta mal. Me parece que tenes el mbr roto, por no decir que estoy seguro, por que el resultado del fdisk deberia ser en los sectores de comienzo-fin correlativos, y por ejemplo ahi el sda4 termina en el 19458, cuando la particion sda6... TAMBIEN! tenes dos particiones en el mismo espacio en disco! sos un grosso! sabelo! :D

Yo haria una copia de tu mbr actual con dd (ver comando en link de wikipedia o en blog que pasaste vos) y despues le doy al testdisk para que arme una nueva tabla. De ultima, si no te anda nada, volves a restaurar la copia del mbr con un live cd y dd de vuelta (guarda el .bin en un pendrive).

Mira el mio para comparar:

```

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xdc1edc1e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1276    10249438+  83  Linux
/dev/sda2            1277        9786    68356575   83  Linux
/dev/sda3            9787       19457    77682307+  83  Linux

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x58e50353

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        1275    10241406   83  Linux
/dev/sdb2            1276        1584     2482042+  82  Linux swap / Solaris
/dev/sdb3            1585       10533    71882842+  83  Linux
/dev/sdb4           10534       19457    71682030   83  Linux

```

Fijate como los sectores de comienzo-fin son correlativos.

Sólo gnu/linux en mi pc... :KS (que tiene que ver no?)

Salu2!!!

EDITO: Incluso sabes que me da la sensacion? de que en realidad no la borraste la particion... dale gas al ranish partition manager y fijate que te muestra.

---

### Post by ramiro_md on 2008-12-29
GRacias x toda la data, probé con testdisk y si podía arreglar el mbr y tampoco funcionó asique formatee y cargue todo de nuevo :( GRacias de tdoos modos :)

---


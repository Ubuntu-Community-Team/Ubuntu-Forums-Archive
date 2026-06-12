---
title: "Ext2IFS"
date: 2008-11-04
forum: Software
---

### Post by Tosh78 on 2008-11-04
Buenas gente, como andan? Ando con un temita con el EXT2IFS. Resulta que desde wingarch lo instale y me reconoce las particiones Ext3, pero el problema es que cuando intento ingresar a una me dice que no tiene formato y me sugiere formatearla. Alguien tiene idea de por que pasa esto y como se puede solucionar? No se si tenga algo que ver, pero cuando instale un juego no me dejaba correrlo (en wingarch) porque decia que faltaban archivos, pero no espscificaba cuales. Sospecho que la causa de Ext2IFS puede ser que a wingarch le falten archivos que utiliza. Algnua idea?

---

### Post by Mister X on 2008-11-04
Seguramente no es la respuesta que estas buscando, pero a mi ni loco se me ocurriria darle la oprtunidad a win de acceder al filesystem de linux

---

### Post by Tosh78 on 2008-11-04
Me parece que es mucho mas seguro usar una particion EXT3 que una NTFS para mis datos. Alguna otra idea?

---

### Post by pol666 on 2008-11-04
Es por que apagaste la pc mal, reinicia anda a ubuntu, apagala bien y volve a windows

---

### Post by valucha on 2008-11-05
[COLOR="Plum"][COLOR="Plum"][COLOR="DarkOrchid"]Lo del ext2ifs es un tema, a mi me anda perfecto pero mi novio con un windows recién instalado tiene tu mismo problema. Lo que hizo fue reinstalarlo 2 o 3 veces y reiniciar y mágicamente anduvo, no sabemos por qué, pero bueh, ahora no se le caga más.

COn respecto a los archivos perdidos de WIndows, me parece que no tiene nada que ver con el ext2ifs.[/COLOR][/COLOR][/COLOR]

---

### Post by EnriqueK on 2008-11-05
Recomiendo instalar en Xp el "Total Commander" y además unos plugins para que pueda acceder a particiones Linux, se consiguen plugins tanto para EXT como para particiones Reiserfs, inclusive se consoguen para solo lectura, la ventaja es clara, solo accedes a particiones linux cuando lo necesitas y además puedes acceder a particiones Reiserfs

---

### Post by Tosh78 on 2008-11-07
Gracias por la ayuda! Pero por el momento sigue pasandome lo mismo, igual que con el Total Comander, no tengo idea de por que sera.
Tenias razon Valucha, lo de los archivos no tiene nada que ver, ya lo solucione a eso.

---

### Post by majatu on 2008-11-10
Buenas, me ha pasado y me sigue pasando cada tanto...

Lo que pasa es que en Windows si usas muchos pendrives, creas, montas o desmontas unidades de cd o dvd virtuales o cosas así o la verdad que a veces pasa "solo", se te desconfiguran las letras de las unidades que asignaste con Ext2IFS (como ser A: C: D: ... etc).

**Solución:** Desde Windows te vas a Mi Pc/Panel de Control/Ext2IFS (creo que se llama así el icono, sino busca el mismo icono que tiene el instalador del Ext2IFS)

Se te abre un programa igual que cuando lo configuraste en la instalación y tenes que cambiarle de letra a la partición de Linux.

Reinicias y listo, tendría que funcionarte ahora.


Espero te ayude, un saludo! ;)

---

### Post by Zootropo on 2008-11-12
> **Mister X said:**
> Seguramente no es la respuesta que estas buscando, pero a mi ni loco se me ocurriria darle la oprtunidad a win de acceder al filesystem de linux

Yo llevo años haciéndolo y nunca he tenido ningún problema.

Piensa que las especificaciones de ext2 y ext3 son públicas. Me fío menos de usar ntfs-3g para escribir en particiones NTFS en Linux (y aun así lo he usado alguna que otra vez)

---

### Post by Zootropo on 2008-11-12
> **majatu said:**
> Buenas, me ha pasado y me sigue pasando cada tanto...

Lo que pasa es que en Windows si usas muchos pendrives, creas, montas o desmontas unidades de cd o dvd virtuales o cosas así o la verdad que a veces pasa "solo", se te desconfiguran las letras de las unidades que asignaste con Ext2IFS (como ser A: C: D: ... etc).

**Solución:** Desde Windows te vas a Mi Pc/Panel de Control/Ext2IFS (creo que se llama así el icono, sino busca el mismo icono que tiene el instalador del Ext2IFS)

Se te abre un programa igual que cuando lo configuraste en la instalación y tenes que cambiarle de letra a la partición de Linux.

Reinicias y listo, tendría que funcionarte ahora.


Espero te ayude, un saludo! ;)

O puedes usar una letra da unidad que no te vayan a pisar. Yo uso la L:, de Linux :-P

---


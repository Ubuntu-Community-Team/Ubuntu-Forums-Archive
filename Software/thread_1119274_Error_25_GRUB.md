---
title: "Error 25 GRUB"
date: 2009-04-07
forum: Software
---

### Post by ramiro_md on 2009-04-07
Bueno gente, hace unas hora tuve un pequeño drama con una Pentium II, y anuncié que iba a tener otros, y la profecía se cumplió.
Pude instalar Debian en el único disco de la pc (6gb), particoné para la swap, Instalé el GRUB, todo muy lindo.
Cuando intento iniciar me sale error 25 de GRUB..algo así:
```
GRUB Loading stage 1.5

GRUB loading, please wait...
Error 25
```

Cuestión que busqué por google y lo único certero que encontré era que se debía a un error de lectura del disco :-|.
Probé con super grub disk y no pude solucionar nada :S
Si alguien me puede tirar un salva vidas se lo agradecería jeje

---

### Post by guillermolisi on 2009-04-07
> **ramiro_md said:**
> Bueno gente, hace unas hora tuve un pequeño drama con una Pentium II, y anuncié que iba a tener otros, y la profecía se cumplió.
Pude instalar Debian en el único disco de la pc (6gb), particoné para la swap, Instalé el GRUB, todo muy lindo.
Cuando intento iniciar me sale error 25 de GRUB..algo así:
```
GRUB Loading stage 1.5

GRUB loading, please wait...
Error 25
```Cuestión que busqué por google y lo único certero que encontré era que se debía a un error de lectura del disco :-|.
Probé con super grub disk y no pude solucionar nada :S
Si alguien me puede tirar un salva vidas se lo agradecería jeje
El BIOS de esa maquina tiene la posibilidad de convertir la geometria del disco con LBA, Normal o Large ?

Esta activada la funcion LBA ?
Si es asi, cambia a Normal y volve a instalar.

---

### Post by ramiro_md on 2009-04-07
> **guillermolisi said:**
> El BIOS de esa maquina tiene la posibilidad de convertir la geometria del disco con LBA, Normal o Large ?

Esta activada la funcion LBA ?
Si es asi, cambia a Normal y volve a instalar.

Me aniquilaste con la pregunta. ni idea como fijarme eso :confused:

---

### Post by Hei Ku on 2009-04-07
En el menu del bios de la mother. En la parte de setup general debe aparecer.

---

### Post by ramiro_md on 2009-04-07
Si, lo encontré en "standar cmos setup". Dice LBA Mode y esta en on y me deja cambiarlo a off únicamente, lo cambio a off e instalo nuevamente ?.

---

### Post by guillermolisi on 2009-04-07
> **ramiro_md said:**
> Si, lo encontré en "standar cmos setup". Dice LBA Mode y esta en on y me deja cambiarlo a off únicamente, lo cambio a off e instalo nuevamente ?.
Correcto ! Desactiva LBA, volve a instalar y conta como te fue !

Por las dudas, fijate si ese BIOS tiene una opcion de reconocimiento automagico de discos.
Esa funcionalidad te sugiere una alternativa como la favorita (la primera de una lista de tres) y luego dos mas de las cuales una suele ser NORMAL. Si la encontras, revisala y asegurate que este seleccionada esa opcion.

---

### Post by ramiro_md on 2009-04-07
> **guillermolisi said:**
> Correcto ! Desactiva LBA, volve a instalar y conta como te fue !

Por las dudas, fijate si ese BIOS tiene una opcion de reconocimiento automagico de discos.
Esa funcionalidad te sugiere una alternativa como la favorita (la primera de una lista de tres) y luego dos mas de las cuales una suele ser NORMAL. Si la encontras, revisala y asegurate que este seleccionada esa opcion.

Bueno, gracias ahí pruebo...y si hay una opción de reconocimiento automático de discos, la utilicé cuando coloqué este disco de 6gb antes de instalar Debian.

---

### Post by ramiro_md on 2009-04-07
Señores,formatié, instalé nuevamente y el problema persiste :S

---

### Post by guillermolisi on 2009-04-08
> **ramiro_md said:**
> Señores,formatié, instalé nuevamente y el problema persiste :S
Me da la impresion de que o Grub no termina de actualizar bien la instalacion o esta grabando con informacion erronea.

Teniendo un solo disco deberia grabar en el MBR del unico que tenes [hd(0,0)] a menos que la BIOS posea una proteccion contra virus que impida que esto se lleve a cabo adecuadamente.

Ademas he visto esto:> 
**25** : **"Unrecognized command"** This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.

en [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

En algun momento tuve algo parecido en unas Compaq DeskPro (PII) y recuerdo que en una oportunidad le corri un particionador (fdisk, parted o similar) para borrar toda informacion de particionamiento en el disco. Despues hice el proceso normal y salio funcionando.

En otra oportunidad termine editando la informacion del Grub en el disco usando chroot desde el LiveCD (hay mucha info en el foro al respecto). Esto fue con 7.04 (long time ago).

El disco esta como Master del canal IDE primario ?
Esta dentro de la lista de dispositivos a usar para el boot ?
Revisaste en donde quiere grabar Grub despues de particionar y antes de aplicar ese particionado ? (deberia decir hd(0,0) si lo instalas en el MBR del disco).

---

### Post by ramiro_md on 2009-04-08
Guille gracias por la data, recien me levanto y me estoy por ir a la facu je, cuando vuelvo pruebo con lo que me comentás. 
Noté que el disco estaba jumpeado como slave, eso tal vez ayude, y en este momento estoy bajando un livecd de fluxbuntu para bootear en esa maquina y ver como esta el archivo de configuración del grub.
Un saludo y gracias.

---

### Post by faktorqm on 2009-04-08
Yo no coincido con Guille, yo entraria a la bios, le habilitaria el LBA al disco o lo dejaria como lo deja la autodeteccion, y despues si tenes el hiren's boot cd a mano (sino bajatelo), arranca el ranish partition manager, borrale todas las particiones al disco, y en la parte de tipo de tabla de particiones, le tenes que poner "Unknow IPL". 
Luego reinstalas. Salu2!

---

### Post by ramiro_md on 2009-04-08
GRacias por la data MArtin. Borré las particiones con Regnash y luego reinstalé y salió andando todo :D.
Ah otra cosa, que clásico (si se puede llamar así) el que paso jejeje se quedaron calentitos los tristeros =).

---


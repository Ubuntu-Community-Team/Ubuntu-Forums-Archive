---
title: "Memtest - Error 28"
date: 2008-08-31
forum: Software
---

### Post by santiagoward2000 on 2008-08-31
Hola gente!
Hoy quise hacer un memtest, y me tiró este error:
> Error 28 : selected item cannot fit into memory
Tengo 2gb de RAM, por lo que me parecio medio raro que "no pueda entrar". Probé correr el memtest del CD de Ubuntu, y ese lo corrió sin quejarse.
Estuve buscando pero la explicacián más razonable que encontré hablaba de limpiar la memoria, sacarle el polvo, etc. Pero no creo que el problema esté ahí, sino no hubiera podido correrlo desde el cd, no?
Alguien me puede ayudar?
Gracias!

---

### Post by niko_3100 on 2008-09-01
reinstala el memtest, nunca me fije pero tendria que estar en los repositorios de ubuntu, en synaptics.

---

### Post by santiagoward2000 on 2008-09-01
Jaja! No se me habia ocurrido!
Igual no me deja reinstalarlo. :(
> E: /var/cache/apt/archives/memtest86+_1.70-3ubuntu1_i386.deb: subprocess new post-removal script returned error exit status 2

Gracias!

---

### Post by WanderingKnight on 2008-09-01
memtest generalmente tira algun false-positive aislado. Es cuestion de dejarlo corriendo mucho mas.

Tene en cuenta que hay que dejarlo varias horas para que realmente valga el testeo.

---

### Post by santiagoward2000 on 2008-09-01
> **WanderingKnight said:**
> memtest generalmente tira algun false-positive aislado. Es cuestion de dejarlo corriendo mucho mas.

Tene en cuenta que hay que dejarlo varias horas para que realmente valga el testeo.

Si, el problema es que no empieza a correr. Cuando lo selecciono, me tira ese error, me pide que toque alguna tecla y vuelve al grub.
Gracias!

*EDIT:*
Ahora que lo pienso, no se si tendrá algo que ver, pero instalé grub-gfxboot siguiendo el post de faktorqm de este thread: [http://ubuntuforums.org/showthread.php?t=781053&page=2&highlight=grub+grafico]("http://ubuntuforums.org/showthread.php?t=781053&page=2&highlight=grub+grafico") Lo que me parece más raro, es que cuando prendo la máquina me aparece el gfx que puse, pero cuando sale del memtest, me aparece una pantalla tipo el grub original.

---

### Post by faktorqm on 2008-09-02
si vos sabes que medio me arrepiento de haber instalado esa cosa... como es muy vieja,  me volo la particion de windows (que nunca volvi a reinstalar :P) y cada vez que actualiza el kernel me lo limpia... fijate de desinstalarlo a mi me anduvo mal, a otro capaz le anduvo bien pero a mi no :(

---

### Post by santiagoward2000 on 2008-09-02
Probé desinstalarlo y volver a intalar el grub seguía sin andar (y seguía sin poder reinstalar el memtest). Hasta formatié el disco e instalé de nuevo y sigue sin andar. Ya revisé el CD y no me tiró ningún error. :confused:

---

### Post by niko_3100 on 2008-09-02
Si tenes windows proba de instalar el memtest desde windows a er que pasa.

---

### Post by santiagoward2000 on 2008-09-02
> **niko_3100 said:**
> Si tenes windows proba de instalar el memtest desde windows a er que pasa.

Fui a [www.memtest.org]("www.memtest.org"). Ahí hay isos para hacer un disco de boot. Pero no veo nada para instalar en Windows (aunque hay un exe que dice Pure DOS). ¿Son todos para correr desde un cd, usb, diskette, etc? Porque para eso uso el del CD de Ubuntu (que desde el CD si anda).
Gracias!

---

### Post by WanderingKnight on 2008-09-04
No tendria mucho sentido correr memtest desde un sistema operativo relativamente moderno. Ya desde el vamos hay un monton de memoria a la que no podria acceder, asi que no hay "memtest para Windows", como tampoco hay "memtest para Linux". Simplemente las distros de Linux suelen incluirlo como agregado ;)

---

### Post by santiagoward2000 on 2008-09-04
> **WanderingKnight said:**
> No tendria mucho sentido correr memtest desde un sistema operativo relativamente moderno. Ya desde el vamos hay un monton de memoria a la que no podria acceder, asi que no hay "memtest para Windows", como tampoco hay "memtest para Linux". Simplemente las distros de Linux suelen incluirlo como agregado ;)

Gracias por la explicación. Es que me parecía raro no poder correrlo desde el grub, y no sabía si había algún problema con mi ram. Pero hoy lo corrí varias veces desde el CD y no apareció ningún error. Supongo que no tengo nada de que preocuparme.

---


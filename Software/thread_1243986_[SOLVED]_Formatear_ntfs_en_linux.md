---
title: "[SOLVED] Formatear ntfs en linux"
date: 2009-08-19
forum: Software
---

### Post by gabi_bh on 2009-08-19
Hola, me idea es la siguiente, tengo instalado ubuntu 9.04 en mi pc y anda de maravillas, el problema es q no puedo jugar al PES 2009, entonces yo habia dejado un porcion de disco para intalar windwos vista asi poder jugar... el problema es que cuando quiero instalar windows vista me dice q no exite particion bla bla bla bla...

Mi pregunta es: **¿Como puedo crear una particion ntfs desde linux?**

Yo ya probe con el gparted, el problema de este es que no me dejaba ninguna opcion, es decir entraba al programa, veia las opciones pero estaban deshabilitadas, aclaro que entre como administrador...

Espero que puedan ayudarme...

Muchas gracias...

---

### Post by gmunioz on 2009-08-19
Hola gab....:

1- Los discos rígidos solo aceptan 4 particiones,
por eso se suele hacer una primaria y otra extendida
para crear dentro de la extendida todas las lógicas
necesarias y vences así esta limitación, debes
contyrolar esto.

2- Gparted para crear particiones en sistema de
archivos ntfs, requiere la instalación previa de
las ntfsprogs

3- Si estas en una sesión desde el disco rígido
las particiones estan montadas y no pueden ser
modificadas, para modificarlas es necesario operar
desde una sesión live.

---

### Post by cmarchesin on 2009-08-19
Gabi_bg, 
No se puede trabajar por completo con las particiones cuando esta corriendo la instalación de Ubuntu, como dicen más arriba es necesario correr el gparted desde un livecd. Te dejo el link[ http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.5-2/gparted-live-0.4.5-2.iso/download]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.5-2/gparted-live-0.4.5-2.iso/download") .Grabalo en un cd y botea desde ahi, deberias poder redimensionar las particiones y generar nuevas incluso NTFS. Se me ocurren otras alternativas pero recurriendo a software privativo (no quiero empezar con el pie izquierdo! je je).

Comentame como resulto.

Saludos,
 
- Catriel -


> **gabi_bh said:**
> Hola, me idea es la siguiente, tengo instalado ubuntu 9.04 en mi pc y anda de maravillas, el problema es q no puedo jugar al PES 2009, entonces yo habia dejado un porcion de disco para intalar windwos vista asi poder jugar... el problema es que cuando quiero instalar windows vista me dice q no exite particion bla bla bla bla...

Mi pregunta es: **¿Como puedo crear una particion ntfs desde linux?**

Yo ya probe con el gparted, el problema de este es que no me dejaba ninguna opcion, es decir entraba al programa, veia las opciones pero estaban deshabilitadas, aclaro que entre como administrador...

Espero que puedan ayudarme...

Muchas gracias...

---

### Post by staar on 2009-08-19
solo agrego que gparted también está incluido en el livecd de ubuntu, se lo encuentra en Sistema > Administración > Editor de particiones

saludos

---

### Post by gabi_bh on 2009-08-22
Muchisimas gracias a todos!, solucionado!

---


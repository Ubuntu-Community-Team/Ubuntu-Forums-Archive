---
title: "instalacion ubuntu 9.04"
date: 2009-03-27
forum: Software
---

### Post by .NicK_LoVe on 2009-03-27
Hola, si en la parte donde pregunta el lugar de instalacion de grub le pongo que no lo instale, no modica el mbr??

Mi pregunta es porque tengo el apestoso vista instalado y quiero probar instalar el ubuntu 9.04 sin alterar el mbr.

Gracias.

---

### Post by pablo.s on 2009-03-27
Si no le instalás GRUB no solo no te va a tocar la MBR, sino
que tampoco te va a arrancar Ubuntu muchachin!

---

### Post by luks911 on 2009-03-27
> **.NicK_LoVe said:**
> Hola, si en la parte donde pregunta el lugar de instalacion de grub le pongo que no lo instale, no modica el mbr??

Mi pregunta es porque tengo el apestoso vista instalado y quiero probar instalar el ubuntu 9.04 sin alterar el mbr.

Gracias.

Con el GRUB instalado podés acceder a los dos sistemas, al menos con WIn XP, no sé con vista. Pero como dice pablo, sin GRUB es seguro imposible acceder a Ubuntu.

---

### Post by santiagoward2000 on 2009-03-27
Hola!
El GRUB tendría que detectarte el Vista y Ubuntu sin problemas (en teoría). A mí en mi laptop me dio problemas para arrancar el Dell MediaDirect, entonces tuve que quedarme con el arrancador del Vista. Lo que tenés que hacer es, cuando te pide si querés instalar el GRUB, tocar el botón donde dice **Avanzado...** e instalarlo en la misma partición que instalaste Ubuntu. Cuando reinicies, te va a entrar al Vista sin preguntar.
Entonces instalá el [EasyBCD]("http://neosmart.net/dl.php?id=1"), y elegís para que te aparezca Ubuntu en el arranque del Vista. Acá te dejo una guía más detallada (tiene fotitos!):
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")
Está en inglés, pero es bastante simple. Si tenés algún problema avisá!
Suerte!

_EDIT:_
Igual aclaro que al Vista podía entrar sin ningún problema con el GRUB, así que si no tenés alguna otra cosa rara instalada, no haría falta que te compliques la vida con el EasyBCD.

---

### Post by .NicK_LoVe on 2009-03-28
Muchas gracias por las respuestas!! 

Yo había instalado el vista boot pro que es un gestor de vista, pero estaba por instalar ubuntu sin el grub y claro no iba a arrancar.

Así que ahora voy a instalar el grub en la partición de ubuntu y voy a ver si con el vista boot pro lo agrego al arranque y sino pruebo el EasyBcd que el tutorial que me pasaron esta de fiesta.

Saludos !!:)

---

### Post by .NicK_LoVe on 2009-03-30
Bueno, al final use el EasyBcd y esta andando ubuntu en mi pavilion dv6768se !!!

Saludos y gracias de nuevo !!!

:guitar:

---

### Post by santiagoward2000 on 2009-03-30
> **.NicK_LoVe said:**
> Bueno, al final use el EasyBcd y esta andando ubuntu en mi pavilion dv6768se !!!

Saludos y gracias de nuevo !!!

:guitar:

De nada! :P

---

### Post by z37a on 2009-03-30
En tu caso particular te recomiendo crear una particion aparte solo para el /boot, por una simple razon, te arrepentis(esperemos que no) borras la particion de linux y el grub no te va a arrancar mas y no vas a saber que hacer, si tenes una particion aparte para el /boot la safas, el grub te arranca igual, y esa particion solo necesita 128MB de espacio(y le sobra con eso), asi que si borras el / y dejas esta particion de 128MB pro lo menos Windows te va a arrancar sin problemas!!!!!!

---

### Post by Andyvec on 2009-03-31
SI ya lo tenés instalado o pensás instalarlo sin modificar la MRB de Windows podés usar el Super Grub Disk, que se puede bootear de un CD o pendrive, esto te permitirá arrancar Linux, Win o lo que sea utilizando el Grub que trae el CD.

También podés restablecer el MRB de Windows en caso de que lo hayas sobreescrito por uno de Linux y también te permite instalar Grub si tienes el de Windows.

En fin, es una herramienta muy completa con muchos usos.
Website: [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by guillermolisi on 2010-05-04
El thread habla sobre la version 9.04 y estan con la 10.04. No es lo mismo y no es especifico del thread.

Bloque de posts movidos [aqui]("http://ubuntuforums.org/showthread.php?t=1472242").

El bug del Grub para la 10.04 esta solucionado de origen para la version final, por esa razon demoraron algunas horas su lanzamiento el jueves 29 de Abril.

---


---
title: "Expandir particion EXT2 sin perder Ubuntu?"
date: 2009-09-13
forum: Software
---

### Post by crynof on 2009-09-13
Hola como estan?
Tnego un problema, instale ubuntu 9.04 y me estoy quedando sin espacio.
Alguien sabe como puedo expandir la particion EXT2 sin perder ubuntu?.
Es que lo tengo bastante personalizado y no creo que me acuerde que instale y que no instale si es que quiero reinstalar, aparte del trabajo que llevaria configurar todo.
Alguien sabe como expandir laparticion??
Saludos y muchas gracias

---

### Post by gmunioz on 2009-09-13
Hola cry....:

Si tienes espacio libre o puedes liberarlo

desde una sesión live, con las particiones

desmontadas, utilizando gparted, el editor de

particiones lo puedes hacer sin problemas.

---

### Post by crynof on 2009-09-13
Muchas gracias gmunioz :)
Es fiable ese metodo?
por que no me acuerdo si es que antes lo hice con el gparded en sesion live o no, pero al redimensionar la particion, despues me quedo dando error 55 parece, o algo asi, pero no pude entrar mas, y tuve que formatear, y es lo que no quiero, por eso pregunto si el metodo es fiable y sin riesgo de perdida de datos.
Es seguro el Gparted?, lo has hecho, o alguien lo ha hecho en una EXT2?
Saludos y muchas gracias de nuevo

---

### Post by Fisaulerod on 2009-09-13
Tengo la misma pregunta para una EXT4

---

### Post by AlexDDR on 2009-09-14
Por mi experiencia, cuando uno modifica las particiones (borrar , crea , agranda) el grub fallará y no podras inresar a ubuntu, simplemente porque el grub no encuentra la particion que buscaba antes y que como uno modifico, el gparted creo un nuevo identificador unico para las particiones, lo que no ocurre cuando uno solo ormatea las particiones sin modificar sus limites.

Dependiendo de la ocacion y como no recuedo ahora, lo que hacia es si me resultaba cambiar el dispositivo a mano en el grub o en el menu.lst. Pro lo mas recurrente era reinstalar el Grub con un live cd, de hecho es bastante sencillo.

Por pereza estoy esperando a Karmic para redimensionar una particion, ejeje



saludos

---

### Post by gmunioz on 2009-09-14
Hola....:

El procedimiento es igual para todo tipo de

sistemas de archivos.

Efectivamente, al cambiar el tamaño de una

partición, deja de ser la que era, para 

convertirse en otra, y debería cambiar su 

uuid, mediante blkid, sudo blkid /partición

se averigua su nueva uuid y se la reemplaza

en el menu.lst del Grub y en fstab.

---


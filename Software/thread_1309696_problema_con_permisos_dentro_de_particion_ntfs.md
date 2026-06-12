---
title: "problema con permisos dentro de particion ntfs"
date: 2009-11-01
forum: Software
---

### Post by WormiS on 2009-11-01
HOla denuevo...
monte mi particion para que la reconosca automaticamente en el fstab con el sgte codigo
"/dev/sda5 /media/disco2 ntfs-3g uid=1000,gid=1000 0 0"
me funciono bien, tengo permisos para modificar leer y crear archivos... pero
cuando intento cambiar los permisos dentro de 1 de las carpeta que hay en el disco no me deja... intente con "sudo chmod 770 /media/disco2/documentos/"... la consola me admite el comando pero a la hora de revisar los permisos con propidades sobre la carpeta estos no se han modificado...

alguna ayuda?

---

### Post by moreback on 2009-11-01
Hola, bienvenido a los foros, como veo que no eres usuario nuevo, te recuerdo que tenemos algunas reglas que hay que respetar para mantener el orden. Una de ellas es la de publicar en el sub-foro que corresponda y que en tu caso debe ser en Software.

Te aconsejaría [leer las normas]("http://ubuntuforums.org/showthread.php?t=1162750") y los post que están al comienzo de cada sub-foro.

Saludos.

---

### Post by WormiS on 2009-11-01
lo siento no me di cuenta... no se como borrar el post asique si es posible que algun mod lo mueva lo agradeceria...

y si me ayudan mejor hahaha ;)

---

### Post by Patriciologico on 2009-11-02
Movido.

---

### Post by Carlos C on 2009-11-02
> **WormiS said:**
> HOla denuevo...
monte mi particion para que la reconosca automaticamente en el fstab con el sgte codigo
"/dev/sda5 /media/disco2 ntfs-3g uid=1000,gid=1000 0 0"
me funciono bien, tengo permisos para modificar leer y crear archivos... pero
cuando intento cambiar los permisos dentro de 1 de las carpeta que hay en el disco no me deja... intente con "sudo chmod 770 /media/disco2/documentos/"... la consola me admite el comando pero a la hora de revisar los permisos con propidades sobre la carpeta estos no se han modificado...

alguna ayuda?

Hola. Si lo que estás intentando es modificar permisos de una carpeta ubicada en una partición ntfs no podrás, porque ese tipo de particiones es nativa de Windows, el que no utiliza el sistema de permisos que usa Linux.

Saludos.

---

### Post by WormiS on 2009-11-07
> **Carlos C said:**
> Hola. Si lo que estás intentando es modificar permisos de una carpeta ubicada en una partición ntfs no podrás, porque ese tipo de particiones es nativa de Windows, el que no utiliza el sistema de permisos que usa Linux.

Saludos.

muchas gracias por la respuesta....

---

### Post by moreback on 2009-11-07
Dentro de la línea de opciones de /etc/fstab que corresponde a esa partición, creo que se pueden usar fmask y dmask para indicar una máscara con la que se le darán los permisos a las carpetas y a los archivos.

Lo que no estoy seguro si funcionan para NTFS, para FAT sí.

Más info con **man mount**.

---


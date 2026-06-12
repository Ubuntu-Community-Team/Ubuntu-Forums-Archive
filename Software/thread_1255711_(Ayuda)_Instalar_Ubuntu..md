---
title: "(Ayuda) Instalar Ubuntu."
date: 2009-09-01
forum: Software
---

### Post by C:\DOS\RUN on 2009-09-01
Hola soy nuevo en el foro... y mucho de linux y ubuntu no se. Bueno tengo un disco de 320GB en el que hace poco tenia a Windows Xp en lso 320G. en todos lados decian que el windows 7 dejaria a xp en el pasado (?), bueno quise comprobarlo yo, y cree una particion de 50gb con el PM.8 y en ella instale el windows 7 todo bien, el boteo bien, pero no pude conectar mi moden de ninguna forma, asi que decidi regresar a ubuntu, (Que una vez tube en otra pc vieja) 

Puedo instalar Ubuntu 9.04 sobre el Windows 7? y si pudiera qy lo instalara que pasaria con el booteo del windows 7 desaparece y aparece el de linux, o la placa buscara el boteo de 7 y al no encontrarlo se quede en negro la pantalla que es mi gran DUDA...

les agradesco su ayuda :D

---

### Post by Tosh78 on 2009-09-01
No deberias tener problemas. Ejecuta el Live cd y ahi te va a preguntar como lo queres instalar, podes elegir las particiones que tengas o formatear todo con GPARTED (gestor de particiones) y despues elegir esa particion para Ubuntu.

---

### Post by totolinux on 2009-09-01
hola bienvenido: por lo que he leído y creo de hecho me ha pasado con xp. es que siempre tenés que instalar ubuntu luego de instalar cualquier windows porque estos borran el grub (programa de booteo). deberías instalar ubuntu en la partición de w7 y crear además una swap. luego al final de la instalación, se cargará el grub para elegir entre ubuntu y xp. 
PD:hace un respaldo de todo lo importante antes de proceder ;D saludos suerte...

---

### Post by gmunioz on 2009-09-01
Hola c\dos....:

Si quieres tener inicio dual (Windows XP - Ubuntu)

Pon a salvo tus archivos de datos.

Reinstala Windows XP, borrando todas las particiones, y

creando una de unos 30 gigas, para instalar, otra del 

resto menos unos 30 gigas, para alojar datos a compartir

ambas en sistema de archivos ntfs.

Una vez configurado este, cierra normalmente e instala

Ubuntu, con particionamiento manual y al menos tres

particiones, una primaria de 15 gigas, sistema de archivos

ext4, punto de montaje /, una lógica, sistema 

de archivos intercambio, de 1 giga, una lógica del resto 

disponible, sistema de archivos ext4 punto de montaje /home

---

### Post by C:\DOS\RUN on 2009-09-01
Bueno, pero si entonces lo instalo sobre el windows seven formatiando la particion de este, al reinicciarse, tendria que enviarme al booteo seguro no?

---

### Post by gmunioz on 2009-09-01
Hola c:\do.....:

Al reinstalar Windows XP, iniciaras con este.

Al agregarle Ubuntu, iniciarás con el Grub

que te dará la opción de iniciar con Ubuntu

por defecto, luego de unos segundos o con 

Windows XP seleccionandolo. Este orden de

inicio se puede cambiar editando el archivo 

de configuración, /boot/grub/menu.lst

---

### Post by C:\DOS\RUN on 2009-09-02
> **gmunioz said:**
> Hola c:\do.....:

Al reinstalar Windows XP, iniciaras con este.

Al agregarle Ubuntu, iniciarás con el Grub

que te dará la opción de iniciar con Ubuntu

por defecto, luego de unos segundos o con 

Windows XP seleccionandolo. Este orden de

inicio se puede cambiar editando el archivo 

de configuración, /boot/grub/menu.lst

No, perp yo no quiero reinstalar xp, ya lo tengo con 230gbs, y en los otros 50gbs tengo al windwos seven, sobre el seven (los 50gbs) quiero instalar ubuntu, el booteo funcionara bien?

---

### Post by Hei Ku on 2009-09-02
El problema puede estar en que win7 haya modificado como es el booteo de winxp. En ese caso, al eliminarlo vas a tener que recuperar el booteo de xp. Despues de eso, podes instalar ubuntu como siempre junto al xp que se llevan barbaro.

---

### Post by gmunioz on 2009-09-02
Hola c:\dos....:

Este es un foro Ubuntu.

Sobre Windows 7, acerca del

cual ignoro todo, tal como

de Windows Vista, deberás

preguntar en un foro Windows.

Si logras eliminar Windows 7

y que el ordenador inicie con 

Windows XP, cuando instales

Ubuntu en el espacio donde estaba 

Windows 7, te dará, tal como ya

te lo expresé, la opción de iniciar

con los dos, Ubuntu y Windows XP

---


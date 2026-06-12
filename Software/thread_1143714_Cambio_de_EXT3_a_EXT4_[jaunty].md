---
title: "Cambio de EXT3 a EXT4 [jaunty]"
date: 2009-04-30
forum: Software
---

### Post by prostata on 2009-04-30
Leo aquí [http://kaeltas.blogspot.com/2009/04/como-cambiar-el-sistema-de-ficheros-de.html](http://kaeltas.blogspot.com/2009/04/como-cambiar-el-sistema-de-ficheros-de.html) que haciendo una instalación limpia de la Jaunty este ya se instala en EXT4, yo tengo el disco particionado, una para WXP, muy poquito espacio dedicado, y luego la mayor parte del disco es para Ubuntu.

Hice una instalación limpia de la Jaunty en la partición reservada al mismo, eliminé dicha partición con Geparted, de forma que todo el espacio asiganado a ubuntu quedó limpio. al hacer la instalación se fue directamente a EXT3, no a EXT4...se debe a que no tengo instalado el Grub2???. En fin no se a que puede deberse y me gustaría salir de dudas para poder actualizar el sistema de arhivos a EXT4

Saludos

---

### Post by Hernán-Amaya on 2009-04-30
yo instalé desde el alternate y la tuve que elegir que sea ext4 por que elige ext3 por omisión.

---

### Post by fmsismo on 2009-04-30
Ojo que ext4 no es todo lo estable que es ext3.  Por eso ext4 no viene por defecto (no esta tan maduro).  Ergo, si están haciendo una tesis, no la pongan en un ext4 :-P

---

### Post by joseluis on 2009-04-30
ext4 es una opción. Por defecto ubuntu 9.04 te pone que hagas todo en ext3. Si queres ext4 tenes que buscar la opcion en el formateo

---

### Post by prostata on 2009-04-30
Pues no me acuerdo ahora mismo, si venía en el formateo, pero me temo que no, o no lo vi. Pasó directamente sin más a EXT3 sin preguntar nada de nada, ¿en que momento aparece la opción previo al formateo...?? No mandó ningún mensaje para que decidiese si quería una u otra extensión, por eso te hago la pregunta...

Saludos

---

### Post by fmsismo on 2009-04-30
Tenes que hacer la instalación manual en lugar de la automática.

---

### Post by pablo.s on 2009-04-30
En el particionado manual aparece
la opción de Ext4.

---

### Post by prostata on 2009-04-30
Gracias por vuestros aportes, los tendré muy encuenta para la proxima vez, porque habrá otra proxima vez...


Saludos

---

### Post by rubioo on 2009-04-30
También podes pasar de ext3 a ext4 asi: [http://ubuntulife.wordpress.com/2009/03/07/convertir-de-ext3-a-ext4/]("http://ubuntulife.wordpress.com/2009/03/07/convertir-de-ext3-a-ext4/") aunque es mas "prolijo" formatear y empezar de cero.

     Saludos

---


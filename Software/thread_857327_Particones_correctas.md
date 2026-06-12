---
title: "Particones correctas"
date: 2008-07-12
forum: Software
---

### Post by nicolab10 on 2008-07-12
Bueno como no pude solucionar el tema de wine, les agradeceria si me explicaran una forma correcta de hacer particones usando ubuntu y windows.
Windows solo lo voy a  usar como una consola de juegos asi que pienso ponerle mas o menos 20 gb, mi disco duro es de 160gb.

Si pueden expliquenme paso a paso como debo hacer para instalar los dos juntos porque lo he intentado anteriormente y no habia forma de entrar a ubuntu, solamente entraba a windows.

Saludos, Nicolab10

---

### Post by nicolab10 on 2008-07-12
alguien me puede ayudar por favor??

---

### Post by Mauro22 on 2008-07-12
Si podes borrar todo el disco mejor.

Primero instala windows y despues linux.

1) Con el CD de windows eliminas todas las particiones y creas una de 20gb y lo instalas ahi.

2) Luego de la instalacion de windows, pones el cd de Ubuntu.

3) En la parte de particionar, elegis la opcion manualmente y haces:

* Una particion para el sistema, Formato: Ext 3 y Punto de montaje: /
* Una particion para tus datos, Formato: Ext 3 y Punto de montaje: /home
* Una particion swap, Formato: Swap. (En teoria del doble de la RAM)

4) Te queda algo asi:

<---20GB XP----><----XGB / -----><----- XGB /home><----Swap---->

Linux se encargara de instalar el Grub y todo eso...

---

### Post by [P]oli on 2008-07-12
Cuando tuve Win XP y Ubuntu en Dual Boot, instalé (en un disco de 80Gb)
[CENTER][WinXP - 10GB]
[Ubuntu - 10GB]
[Datos - 59GB]
[Swap - 1GB][/CENTER]
**A veces varía por unos pocos Mb :P*

Y el orden de instalación fue:
**1-** Instalo WinXP y cuando hago las particiones, hago TODAS, incluyendo la swap, pero sin fomatear ninguna (salvo la que va a tener el WinXP, obvio :P)
**2-** Instalo Ubuntu, formateando las demás particiones (la de Ubuntu con punto de montaje **/**), y la de **Datos** como **FAT32** (muy importante, ya que ambos sistemas operativos lo reconocen sin problemas ;))

Y ahí debería funcionar todo sin problemas, ;)

pd: Recién veo el post de Mauro ajajaj

---

### Post by cmarchesin on 2009-11-06
Que juegos estas pensando correr ?? Talvez otra opción sea armar una virtual de Win en tu ubuntu y correr los juegos en la virtual. Para que esto funcione decentemente tener que contar con minimo 2 Gb ram. De todas maneras esto lo podes probar antes de instalar el dual boot ubuntu/windows  y si no funciona seguir con la idea original. Saludos ...

---

### Post by -=The_Chacal=- on 2009-11-07
No mareen al pibe.

Primero instalas el windows en todo el disco sin hacerte mucha complicacion. Despues seguite este tuto y sale como trompada:

[http://ubuntuforums.org/showthread.php?t=1280260](http://ubuntuforums.org/showthread.php?t=1280260)

consejo: si la vas a usar para correr juegos yo te recomiendo mas de 20 GB en windows, aunque depende que juegos corras.

edit: el de arriba me lo revivio y cai xD

---

### Post by cmarchesin on 2009-11-07
The Chacal,

No es intención de nadie mareara nicolab pero me parece bueno ofrecer todas las resoluciones posibles para que :

a - pueda elegir la que mas le guste (ya sea for facilidad de implementación, eficiencia, etc)

b - conozca otras formas de solucionar su problema. Esta es una manera de compartir los conocimientos que uno tiene (podrán ser mucho o pocos .. pero se pueden compartir). 

esta es la verdadera forma de aprender.
Acá la corto ... entiendo que es un espacio de resolucion tecnica y no de discusion de principios ...

Saludos ... 

catriel 

> **-=The_Chacal=- said:**
> No mareen al pibe.

Primero instalas el windows en todo el disco sin hacerte mucho quilombo. Despues seguite este tuto y sale como trompada:

[http://ubuntuforums.org/showthread.php?t=1280260](http://ubuntuforums.org/showthread.php?t=1280260)

consejo: si la vas a usar para correr juegos yo te recomiendo mas de 20 GB en windows, aunque depende que juegos corras.

edit: el de arriba me lo revivio y cai xD

---

### Post by guillermolisi on 2009-11-07
Si se usara Windows para jugar entonces la mejor recomendacion es optar por dual boot ya que es la unica forma de obtener aceleracion grafica completa en forma directa desde el hardware real.
Tambien se puede jugar con Win virtualizado pero como el software de virtualizacion hace abstraccion del harware (para armar la VM) nunca va a funcionar igual que en el primer caso.

---

### Post by alfplayer on 2009-11-07
Este thread es del año pasado.

---

### Post by cmarchesin on 2009-11-07
: (

> **alfplayer said:**
> este thread es del año pasado.

---


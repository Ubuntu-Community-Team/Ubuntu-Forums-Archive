---
title: "Se tilda a cada rato pero mouse y sonido siguien funcionado"
date: 2010-05-20
forum: Software
---

### Post by geropa on 2010-05-20
Hola a todos. 
     Mi problema es que ubuntu se tilda durante 20 segundos,a veces mas y otras veces menos,pudiendo mover solo el mouse y seguir escuchando la musica en ese intervalo, pero todo sigue funcionado normalmente(descargas, sonido, algun que otro proceso,, etc). Esto me sucedio en ubuntu 9.10 y ahora en 10.04 en ambas versiones de 32 y 64 bit. tengo una amd 64 athlon X2 con 1 gb de ram y placa de video integrada GeForce 6100.y no se cual pude ser el problema. les agradeceria mucho su ayuda.

---

### Post by Excedio on 2010-05-20
Google Translation

> My  problem is that ubuntu is branded for 20 seconds, sometimes more and  sometimes less, and can move only the mouse and keep listening to the  music in this range, but everything is working normally (downloads,  sound, some by another process, etc. .) This happened to  me on ubuntu 9.10 and 10.04 In both now 32 and 64 bit. I have a amd  athlon 64 X2 with 1 gb of ram and integrated GeForce video card 6100.y  which could not be the problem. I would greatly  appreciate your help.

---

### Post by angry_johnnie on 2010-05-20
trata de ir a terminal virtual cuando ocurra, y ejecuta el comando top, para determinar que proceso o aplicacion es la causante del problema.

por cierto, podrias intentar preguntar en un subforo como [estos]("http://ubuntuforums.org/forumdisplay.php?f=183"), ya que este, en general, maneja todo en ingles.


translation (sort of):  :-)

try going to a virtual terminal when it happens, and execute the top command, to determine which process or application is causing the problem.

by the way, you could try a [subforum]("http://ubuntuforums.org/forumdisplay.php?f=183"), given this one is mainly an english forum.

---

### Post by bapoumba on 2010-05-21
Hello,
I have moved this thread to one of the Spanish speaking Locos sub-forum.

---

### Post by guillermolisi on 2010-05-21
> **bapoumba said:**
> Hello,
I have moved this thread to one of the Spanish speaking Locos sub-forum.
Thanks a lot, bapoumba !

---

### Post by guillermolisi on 2010-05-21
> **geropa said:**
> Hola a todos. 
     Mi problema es que ubuntu se tilda durante 20 segundos,a veces mas y otras veces menos,pudiendo mover solo el mouse y seguir escuchando la musica en ese intervalo, pero todo sigue funcionado normalmente(descargas, sonido, algun que otro proceso,, etc). Esto me sucedio en ubuntu 9.10 y ahora en 10.04 en ambas versiones de 32 y 64 bit. tengo una amd 64 athlon X2 con 1 gb de ram y placa de video integrada GeForce 6100.y no se cual pude ser el problema. les agradeceria mucho su ayuda.
Desde la observacion, pudiste determinar si la interrupcion es regular en el tiempo ?
Alguna operacion que siempre anteceda a este sintoma ?
Cuando esto sucede, hay uso intensivo de disco ?

Cuando la maquina funciona normalmente, funciona bien, fluida ?

Revisaste los logs en busca de algun indicio ? Particularmente /var/log/dmesg y /var/log/Xorg.0.log, como para empezar.

No es mala idea monitorear con top o htop desde una terminal.

---


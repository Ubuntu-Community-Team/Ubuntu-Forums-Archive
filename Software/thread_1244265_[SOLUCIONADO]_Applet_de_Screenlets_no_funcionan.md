---
title: "[SOLUCIONADO] Applet de Screenlets no funcionan"
date: 2009-08-19
forum: Software
---

### Post by Chogogo on 2009-08-19
Hola. Recien instalé Jaunty y he tenido algunos problemas para ponerlo a punto. Uno de ellos son los applets de Screenlets. Sencillamente no funciona ninguno. Instalo el programa con apt-get, lo ejecuto desde el menu de aplicaciones, seleciono uno de los applets mostrados en el "screenlets-Manager" y luego le doy al boton "launch/Add" pero no sucede nada, no aparece ningún applet ni tampoco ningun mensaje de error.

Que puede estar pasando y como podría solucionarlo

Saludos, gracias de antemenao y Que Dios los bendiga

---

### Post by Carlos C on 2009-08-19
Mira en este enlace:

[http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/](http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/)

recomiendan un par de paquetes que debes tener instalados.
Saludos.

---

### Post by Chogogo on 2009-08-19
> **Carlos C said:**
> Mira en este enlace:

[http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/](http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/)

recomiendan un par de paquetes que debes tener instalados.
Saludos.

Hola.
Seguí las recomendaciones del enlace que en resumen son instalar los paquetes "python-gnome2-extras" y "python-feedparser", pero no funcionó
Puedo ver los Gadgets en la ventana principal pero no logro activarlos sobre el escritorio. Alguna sugerencia??

Gracias y que Dios los bendiga

---

### Post by Carlos C on 2009-08-19
y cómo los estás activando? Entiendo que se seleccionan del listado y luego se selecciona la casilla Start/Stop.

---

### Post by Chogogo on 2009-08-20
> **Carlos C said:**
> y cómo los estás activando? Entiendo que se seleccionan del listado y luego se selecciona la casilla Start/Stop.

Pues he probado de todas formas. Seleccionanado la casilla Start/Stop, sin seleccionar, Al iniciar, mediante  un lanzador en el escritorio...pero nada. Simplemente no salen.  Por alguna parte leí que Compiz tenía que estar funcionando correctamente para que funcione este programa.. es verdad? . Me preocupa que esto sea un signo de algún fallo en Compiz... como averiguo si se trata de un problema de el Compiz o solo del programa.
 Yo tengo Compiz y asceleración de video, utilizo Emerald y tengo instalado Fusion Icon, pero Pierdo los efectos de escritorio al activar el Pluggin del Cubo. habrá alguna relación?? 

Gracias y Que Dios los bendiga..

---

### Post by nopersona on 2009-08-20
abre screeblets por terminal y pega la salida cuando no abren.

---

### Post by Chogogo on 2009-08-21
> **nopersona said:**
> abre screeblets por terminal y pega la salida cuando no abren.

Aqui está la salida
=========================
Launching Screenlet from: /usr/share/screenlets/Clock/ClockScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/ClockScreenlet.log
sh: cannot create /home/omar/.config/Screenlets/ClockScreenlet.log: Permission denied
======================================

Pero ya lo solucioné. Era obvio (Persmission denied). La solucion: cambiarle los persmisos a la carpeta /home/omar/.config/Screenlets/   Y listo!

Saludos y que Dios los bendiga

---

### Post by Carlos C on 2009-08-21
Lo cual demuestra que la técnica de correr el comando desde el terminal es más que útil. :)

---


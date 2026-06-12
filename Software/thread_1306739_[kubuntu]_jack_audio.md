---
title: "[kubuntu] jack audio"
date: 2009-10-30
forum: Software
---

### Post by Barasuishou on 2009-10-30
hola bueno quería probar jack(nose como se dice si gestor de sonido o que), y lo instalé con esta guía ([http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730)), todo bien la instalación y todo, pero tengo un problema al iniciar qjackctl abre el jack pero abre otra ventana que dice esto 

17:33:46.562 Patchbay desactivada.
17:33:46.566 Reiniciar estadísticas.
17:33:46.666 Script de inicio...
17:33:46.666 artsshell -q terminate
17:33:46.669 Cambió el gráfico de conexiones ALSA.
sh: artsshell: not found
17:33:47.092 El script de inicio finalizó con estado 32512.
17:33:47.093 JACK está iniciándose...
17:33:47.094 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -m
17:33:47.101 JACK se inició con PID=5494.
17:33:47.308 Cambios en las conexiones ALSA.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216022848, from thread -1216022848] (1: Operation not permitted)
cannot create engine
17:33:47.473 JACK ha sido detenido satisfactoriamente.
17:33:47.474 Script de post - apagado...
17:33:47.474 killall jackd
jackd: proceso no encontrado
17:33:47.934 El script de post - apagado finalizó con estado 256.
17:33:49.360 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
17:33:59.848 Cambió el gráfico de conexiones ALSA.

antes de esto aparece un cartel que no pudo conectarse a jack

alguien me podría ayudar, quisiera probar esto ya que intento grabar y/o editar audio en linux

PD:uso kubuntu 9.10 x86

---

### Post by guillermolisi on 2009-10-30
> **Barasuishou said:**
> hola bueno quería probar jack(nose como se dice si gestor de sonido o que), y lo instalé con esta guía ([http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730)), todo bien la instalación y todo, pero tengo un problema al iniciar qjackctl abre el jack pero abre otra ventana que dice esto 

17:33:46.562 Patchbay desactivada.
17:33:46.566 Reiniciar estadísticas.
17:33:46.666 Script de inicio...
17:33:46.666 artsshell -q terminate
17:33:46.669 Cambió el gráfico de conexiones ALSA.
sh: artsshell: not found
17:33:47.092 El script de inicio finalizó con estado 32512.
17:33:47.093 JACK está iniciándose...
17:33:47.094 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -m
17:33:47.101 JACK se inició con PID=5494.
17:33:47.308 Cambios en las conexiones ALSA.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
[COLOR=Red]cannot use real-time scheduling (FIFO at priority 10) [for thread -1216022848, from thread -1216022848] (1: Operation not permitted)[/COLOR]
cannot create engine
17:33:47.473 JACK ha sido detenido satisfactoriamente.
17:33:47.474 Script de post - apagado...
17:33:47.474 killall jackd
jackd: proceso no encontrado
17:33:47.934 El script de post - apagado finalizó con estado 256.
17:33:49.360 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
17:33:59.848 Cambió el gráfico de conexiones ALSA.

antes de esto aparece un cartel que no pudo conectarse a jack

alguien me podría ayudar, quisiera probar esto ya que intento grabar y/o editar audio en linux

PD:uso kubuntu 9.10 x86
Por el mensaje que marque en color, necesitas usar un kernel RealTime (RT) en lugar de un Server o Generic para que Jack funcione.

---


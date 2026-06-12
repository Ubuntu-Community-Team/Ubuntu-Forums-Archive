---
title: "[problema] Aceleracion cooler en notebook IBM"
date: 2009-11-04
forum: Software
---

### Post by vairo on 2009-11-04
Buenas, soy nuevo en el foro y algo nuevo en linux también.

Mi problema es que antes, en windows tenia un programita llamado TPfancontrol para acelerar las RPM del cooler de mi notebook (Thinkpad T60) y ahora en ubuntu encontré unas cuantas formas de hacerlo, a travez de unas aplicaciones simples y de forma manual por consola.

*Estoy corriendo ubuntu 9.10 actualizado de un 9.04*
He seguido todas las instrucciones que ponen [AQUI ]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed")
Como no pude encontrar el archivo ¨/etc/modprobe.d/options¨ busque por [este hilo ]("http://ubuntuforums.org/showthread.php?t=836958")y segui los paso que realizo [richard.e.morton]("http://ubuntuforums.org/member.php?u=590754") (ultima respuesta) ya que dice que estaba corriendo la misma ver. que yo (9.10)
Hasta he conseguido instalar el programa y todo, pero el problema esta lo siguiente:

```
[gaston@gaston-UBUNTU:~$ sudo -i
[sudo] password for gaston: 
root@gaston-UBUNTU:~# echo level 0 > /proc/acpi/ibm/fan
root@gaston-UBUNTU:~# cat /proc/acpi/ibm/fan 
status:        enabled
speed:        0
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
root@gaston-UBUNTU:~# cat /proc/acpi/ibm/fan 
status:        enabled
speed:        2542
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
root@gaston-UBUNTU:~# 

```Donde dice ¨level: auto¨ se supone que tiene que decir 0.
Y si prestan atención parece que en un momento el sistema me responde al comando pero luego vuelve a ¨auto¨ y vuelve a arrancar el cooler que apague, me deja sin poder modificar nada.

**[COLOR=Red]Aclaracion:[/COLOR]** se que no es buena idea tener el cooler apagado, solo lo hice como ejemplo

De antemano muchísimas gracias.

---


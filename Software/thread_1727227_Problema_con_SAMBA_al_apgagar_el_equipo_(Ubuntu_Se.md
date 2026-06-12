---
title: "Problema con SAMBA al apgagar el equipo (Ubuntu Server 10.04)"
date: 2011-04-12
forum: Software
---

### Post by Dago_Ô on 2011-04-12
Qué tal ubunteros y ubunteras

Monté un pequeño servidor de archivo para una red de equipos con Widnows  XP SP3 utilizando SAMBA.  La distro de linux utilizada en el equipo  servidor es Ubuntu Server 10.04 32bit.
La configuración de samba es bastante simple.  Básicamente se tiene una  solo recurso compartido con sguridad de nivel usuario y solo 1 usuario  es utilizado para acceder éste (ese usuario lo utilizan todos los  clientes con WinXP para acceder al recurso compartido).
El archivo de configuración smb.conf no tiene ningún error de sintaxis  ni ortografía (probado con el comando testparm) y en general el recurso  compartido funciona absolutamente bien, no hay problemas ni de permisos  ni de disponibilidad.
El problema viene cuando se apaga el equipo servidor, en concreto, con el comando *"shutdown -h now"*.   Una vez que el equipo vuelve a inicarse, se cargan los demonios smbd y  nmbd si ningún problema, pero al intentar acceder al recurso compartido  desde los equipos con WinXP aparece el mensaje de que no se tiene  permisos de acceso.  El problema se soluciona reiniciando ya sea el  demonio smbd o nmbd (con cualquiera que se reinicie vuelve todo a la  normalidad), con el comando "sudo restart smbd" o "sudo restart nmbd"
Este problema no sucede reiniciando la máquina, es decir con el comando *"shutdown -r now"*.
He buscado por varios lados para tratar de solucionar el problema, pero  no he tenido suerte.  A ver si alguien me ayuda a encontrar el problema.
Saludos y gracias desde ya.

---


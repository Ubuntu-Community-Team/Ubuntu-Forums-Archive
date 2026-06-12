---
title: "[SOLVED] VirtualBox error 1909"
date: 2008-06-04
forum: Software
---

### Post by atari130xe on 2008-06-04
Gente acabo de instalar VirtualBox, para variar estoy muy contento con Ubuntu pero mi hna. usa PalTalk, el cual no funca bien con Wine (se instala perfecto pero lo inicia y al toque se "cuelga" y se cierra), decidí instalar VirtualBox, todo bien creo la "maquina virtual" y cuando pongo el CD de XP sale un error: 

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

what the hell? jejeje :lolflag:

---

### Post by sajnox on 2008-06-04
> Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups.

Vas por Sistema/Administracion/Usuarios y Grupos desbloqueas la pantalla seleccionas gestionar grupos y en el grupo "vboxusers" agregas a tu usuario. 

Con eso deberia andar.

Obviamente se puede hacer con la consola mucho mas facil y rapido, pero creeme que usar la opcion grafica todavia no mato a nadie. :)

---

### Post by atari130xe on 2008-06-04
Jejeje estaba por responderme yo mismo, eso pasa por arrebatado, por no leer lo que dice la PC, solucionado! Gracias como siempre! :)

---


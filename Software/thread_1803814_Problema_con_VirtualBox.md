---
title: "Problema con VirtualBox"
date: 2011-07-13
forum: Software
---

### Post by pelaolinux on 2011-07-13
Que tal amigos, mi problema es el siguiente: 

resulta que instale ubuntu 11.04 en mi Compaq Presario f500, luego instale virtualbox. Me estuvo funcionando excelente la maquina virtual con winxp, hasta que hoy entre en ella y me muestra el siguiente error el cual muestro en el siguiente [enlace]("http://img71.xooimage.com/files/3/d/d/pantallazo-2ac9b1e.png").

me gustaría saber la solución de este problema y además saber como puedo compartir las carpetas con la maquina virtual, por que, al agregarla en la opción que me da Virtualbox no sucede nada. El otro día en una charla de ubuntu que hicieron me comentaron que se podía instalar un paquete para el virtualbox que soluciona el problema con el compartimiento de carpetas y otros mas.

espero que puedan ayudarme y mi forma de redactar mi problema no sea muy ambigua. 

Saludos!!!:D

---

### Post by varunendra on 2011-07-14
English Translation for others (via Google Translate):
> ....Ubuntu 11.04 is to install on my Compaq Presario f500, then install virtualbox. I was working great with winxp virtual machine, until today between it and shows me the following error which shows the link below.

 I want to know the solution to this problem and also know how I can share folders with the virtual machine, why, when you add the option that Virtualbox gives me nothing happens. The other day in a talk that made ubuntu told me they could install a package for virtualbox that solves the problem with sharing folders and others....@pelaolinux,

Hope you can read and understand English.

For running a VM (removing the error message):

[LIST=1]
[*]Install the same version of **linux-headers** as the version of linux-kernel that you are currently using,
[*]Reinstall **virtualbox-ose-dkms** package from synaptic
[*]Run this command in terminal: ```
sudo modprobe vboxdrv
```
[*]Run virtualbox. This time you should be able to run VMs without any errors.
[/LIST]
For 'Shared Folders', you need to install 'Guest Additions' in the operating system you are running inside the virtual machine. Then goto the virtual machine's System Settings and define a path for the folder that you want to share with your virtual machine.


Translation of above in spanish :confused: :-
> Para el funcionamiento de una máquina virtual (quitar el mensaje de error):

     1) Instalar la misma versión de linux-headers de la versión de linux-kernel que se está utilizando actualmente,
     2) Vuelva a instalar virtualbox-ose-dkms paquete desde synaptic
     3) Ejecutar este comando en el terminal: [CÓDE] sudo modprobe vboxdrv [/code]
     4) Ejecutar VirtualBox. Esta vez usted debe ser capaz de ejecutar máquinas virtuales sin ningún error.

 Para "Carpetas compartidas", es necesario instalar "Guest Additions en el sistema operativo que está ejecutando en la máquina virtual. Ir a continuación, Configuración de la máquina virtual del sistema y definir una ruta de la carpeta que desea compartir con su máquina virtual.[Hope some spanish-speaking member can follow up from here]

---

### Post by nechus on 2011-07-14
Hola,

A ver, te lo explico en palabras fáciles porque no conozco los términos técnicos.

Seguramente hiciste una actualización en algún momento. Esto borró la información de VirtualBox que había en el kernel ("módulos" o algo así).

Para que eso no pase, instala el paquete dkms con Synaptic y reinstala VirtualBox con el mismo Synaptic. Eso no va a borrar tu XP. Entonces, cada vez que actualices tu sistema, los "módulos" de VirtualBox en el kernel se reinstalarán.

Al menos eso es lo que me había pasado a mí.

Suerte

---

### Post by pelaolinux on 2011-07-16
> **nechus said:**
> Hola,

A ver, te lo explico en palabras fáciles porque no conozco los términos técnicos.

Seguramente hiciste una actualización en algún momento. Esto borró la información de VirtualBox que había en el kernel ("módulos" o algo así).

Para que eso no pase, instala el paquete dkms con Synaptic y reinstala VirtualBox con el mismo Synaptic. Eso no va a borrar tu XP. Entonces, cada vez que actualices tu sistema, los "módulos" de VirtualBox en el kernel se reinstalarán.

Al menos eso es lo que me había pasado a mí.

Suerte

Gracias, ahora me funciona como antes. :D 
Saludos!

---


---
title: "[SOLVED] Cambio de Gnome a XFCE bajo Ubuntu 9.04"
date: 2009-07-30
forum: Software
---

### Post by guidito73 on 2009-07-30
Buenas gente! Les comento un poco lo que estuve haciendo hoy.

Ubuntu ya andaba muy lento en la PC de mi novia, así que decidí instalar Xubuntu. Lo que hice fue formatear el / de Ubuntu, y dejar el /home y el swap que tenía anteriormente. 

**Primer problema:** el /home obviamente desapareció, no lo reconoce en Xubuntu, sino que tengo uno nuevo (nada de configuraciones, ni documentos ni musica anteriores). Es imposible hacer esto?

**Segundo:** el escritorio está muerto. Tras haber instalado Audacious (con un par de librerias que pedía), el escritorio desapareció. Pude hacer volver los paneles, pero el fondo y los accesos directos jamás volvieron.

**Tercero:** Inicia con una resolución predeterminada de 1280x1000 y algo. Aunque la cambio por otra (1024*768) al reiniciar vuelve a la de 1280...

Bueno, es eso más que nada, pero lo que más molesta es no poder acceder al /home anterior (que vale la aclaración, no fue formateado).

Cualquier ayuda es bienvenida!

---

### Post by guillermolisi on 2009-07-30
El /home original reside en otra particion con lo cual tenes que montarlo para que pueda ser utilizado.
Deberia reemplazar el /home nuevo, el que se genero cuando reinstalaste.

Podes probar montandolo a mano y luego de verificar que este funcionando bien, incluirlo en el /etc/fstab para que sea montado cada vez que inicies.

Supongo que el fondo y demas cosas del escritorio apareceran al montar el /home original.

Sobre la resolucion habira que contar con mas datos sobre la placa de video y el monitor, pero primero resolve lo del /home y despues vemos que mas falta.

---

### Post by guidito73 on 2009-07-30
Ah, ah ah, perfecto. Ahora, como hago para montar el /home original sobre el nuevo? Me podrías guiar?? :D segun el monitor de sistema, el / es sda7 y el /home es sda5 en /media/disk.

Por las dudas: el monitor es un LG 710E. Sobre la placa de video, esto me tira hardinfo:

> -PCI Devices-
Host bridge		: Silicon Integrated Systems [SiS] 741/741GX/M741 Host 
PCI bridge		: Silicon Integrated Systems [SiS] SiS AGP Port 
ISA bridge		: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] 
IDE interface		: Silicon Integrated Systems [SiS] 5513 [IDE] 
Modem		: Silicon Integrated Systems [SiS] AC'97 Modem Controller 
Multimedia audio controller		: Silicon Integrated Systems [SiS] AC'97 Sound Controller 
USB Controller		: Silicon Integrated Systems [SiS] USB 1.1 Controller 
USB Controller		: Silicon Integrated Systems [SiS] USB 1.1 Controller 
USB Controller		: Silicon Integrated Systems [SiS] USB 1.1 Controller 
USB Controller		: Silicon Integrated Systems [SiS] USB 2.0 Controller 
Ethernet controller		: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet 
VGA compatible controller		: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


EDIT: Bueno, toqueteando el fstab, pude montar el /home original, pero solamente una vez que inició Xubuntu (obviamente con la línea del mntaje del home comentada). Cuando intento dejar la linea sin comentar y reinicio, me tira un problema con algo de GNOME y me tira una terminal en modo a prueba de fallos...
Les dejo mi fstab:
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=83c9b037-e3b9-4b84-9fde-e13558a4facb /               ext3    relatime,errors=remount-ro 0       1
# dev/sda5 home
#UUID=e7ddc1eb-3af1-4c16-be3c-1528ec2b2c88 /home               ext3 defaults        0       2
# swap was on /dev/sda6 during installation
UUID=55023ef4-baf2-4f97-9ccf-23406c216f04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Como ven, ahi dejo comentado el home porque sino es imposible acceder al SO. Hay algo que esté haciendo mal? Porque cuando saco el # de la linea, y uso > mount -a el home se monta normal y funca bien, pero al reiniciar vuelve todo para atrás...

---

### Post by guillermolisi on 2009-07-31
Respecto del fstab, por que dice "defaults" y no "relatime" ?
Lo pusiste vos o estaba asi en el original ?

Hay algo que no termino de comprender. Si descomentas la linea que monta el /home de /dev/sda5 decis que no podes acceder al SO pero luego decis que con esa linea descomentada lo podes montar con "mount -a" .... Si no podes acceder al SO como haces para montarlo ?

Luego, el UUID del /dev/sda5 es el correcto ?
Hay un tutorial sobre [como obtener el UUID de una particion]("http://ubuntu-ar.org/node/214") en el web site de Ubuntu-ar

---

### Post by guidito73 on 2009-07-31
Bueno, lo cambié a relatime, nada... sigo sin poder entrar. 

> Hay algo que no termino de comprender. Si descomentas la linea que monta el /home de /dev/sda5 decis que no podes acceder al SO pero luego decis que con esa linea descomentada lo podes montar con "mount -a" .... Si no podes acceder al SO como haces para montarlo ?

Al no lograr entrar, me tira a un modo en terminal. Desde ahi entro al fstab, lo comento y puedo entrar nuevamente. No hay inconvenientes a la hora de montarlo desde el SO cargado, con el fstab previamente comentado.

Si, el UUID es el correcto, si no ni siquiera podría montarlo con mount -a.

El error que me da al iniciar intentando montar el home en el fstab es:

> No exec line in the session file: gnome.
Running the GNOME failsafe session instead.

> Could not find the GNOME installation, will
try running the "failsafe xterm" session.

**_Ya solucioné el montaje del home! Solamente tenía que modificar el archivo .drmc del home original y cambiar "gnome" por xfce! Era simple, pero no me había dado cuenta. Ahora queda el modificar la resolución de escritorio a 1024x768!_**

---

### Post by guillermolisi on 2009-07-31
Excelente !

Te pido un favor, el tema de ajustar la resolucion tiene varios threads desarrollados. Fijate lo que se ha hablado en ellos y si seguis con inconvenientes abri uno especifico para el tipo de placa que estas usando, en la seccion Hardware. Podra ser ?

Si me permitis, cambio el asunto de este thread para que sea mas acorde con lo tratado (Problemas al pasar de Gnome a XFCE, por ejemplo). Que te parece ?

---

### Post by guidito73 on 2009-07-31
Hecho, muchas gracias! :D

---


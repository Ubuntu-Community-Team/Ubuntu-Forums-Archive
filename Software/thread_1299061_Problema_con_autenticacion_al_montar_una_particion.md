---
title: "Problema con autenticacion al montar una particion"
date: 2009-10-23
forum: Software
---

### Post by eddiemolko on 2009-10-23
Hola a todos, les comento mi problema.
Ayer actualize mi ubuntu a la RC 9.10.
Todo bien, me gusta bastante, pero cuando intento montar la particion en la que tengo Window$ me pide contraseña.
Antes no me lo pedia y habia logrado hacer que se automonte al iniciar para tener un enlace al escritoria de windows en mi ubuntu. Pero ahora no puedo porque siempre que intento montar la unidad me pide la contraseña.

El mensaje dice lo siguiente:

Authenticacion is required to mount the device
Una aplicacion esta intentando realizar una accion que necesita permisos especiales. Es necesario autenticarse para realizar dicha accion.
Contraseña:___________
Detalles:
Drive: ATA WDC WD3200AAKS-22B3A0 (01.03A01)
Device /dev/sda2
Accion: org.freedesktop.devicekit.disks.filesystem-mount-system-internal
Proveedor: THe DeviceKit Project


Alguien sabe algo?

---

### Post by jpernesto_666 on 2009-10-30
Si,es lo único que no me ha gustado hasta ahora de esta versión y no encuentro como hacer que no pida la autentificación,es molesto ](*,),si sabes algo comenta porfa,sale.

---

### Post by BlackHero on 2009-10-30
probaron cambiando los permisos a mount? o talves teniendo un solo usuario "root". 
Saludos espero solucionen su problema

---

### Post by VitoTorres on 2009-11-01
[http://forums.fedoraforum.org/showpost.php?p=1284201&postcount=12](http://forums.fedoraforum.org/showpost.php?p=1284201&postcount=12)

---

### Post by moreback on 2009-11-01
Creo que se soluciona marcando **Montar sistemas de archvio en espacio de usuario (FUSE)** de la pestaña **Privilegios del usuario** en el editor de propiedades de tu cuenta de usuario (**Sistema -> Administración -> Usuarios y grupos**).

Saludos.

PD: hay que deslogearse para que se apliquen los cambios

---

### Post by geralexcas on 2009-11-05
funciona de la siguiente forma editando  el archivo  
[I][I]fstab de /etc  en la consola escribi sudo gedit /etc/fstab despues de colocar la
contraseña podemos editar este archivo es recomendable antes sacar una copia
de segurida por si las moscas mi fstab es asi:




# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=0d704535-3073-4ed9-89e5-aa71f71259ac /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=04674798-5be2-4139-b529-9f17d68e3682 /home           ext4    defaults        0       2

# swap was on /dev/sda3 during installation
UUID=58ec4ba5-e513-4a86-a469-05e68c6c3f48 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

 /dev/sda1 /media/win7 ntfs users  0 0
/dev/sda6 /media/datos  ext3  users 0 0




las dos ultimas lineas las coloque teniendo encuenta la informacion que da gparted
sobre las particones el tedice si es sda1 sda2 o como lo tengas en tu sistema
con el comado sudo mkdir hice las carpetas win7 y datos dentro de media
que son los puntos de montaje donde quedan las particiones grabas sales 
y ejecutas el comado sudo mount -a y listo sin tener que reiniciar
 este dato lo tome de  

file:///media/datos/mis%20hayudas/editar%20fstab%20para%20asignar%20punto%20de%20montaje/003329.html

gparted lo instalas con la ayuda de  gestor de paquetes synacptic

[/I][/I]

---

### Post by granjer on 2009-11-11
Bueno, después de leer este post y otros como este sin solución, al fin encontré un programa que da solución a este problema. 

Copio y pego de [aquí]("http://d800ubuntu.blogspot.com/2009/11/montar-particiones-sin-contrasena.html"):

> Después de actualizar a ubuntu 9.10 las particiones empezaron a pedir autentificación o contraseña para ser montadas, lo cual, aunque evidentemente es más seguro, no deja de ser un coñazo. Para solucionar esto resulta que hay que editar el archivo /etc/fstab. Esto para un inexperto como yo, es algo casi imposible ya que aunque seguí las indicaciones encontradas en foros y demás no conseguí dejarlo a mi gusto. Por suerte encontré [esta pagina]("http://www.lagg3r.com.ar/montar-particiones-al-inicio-en-ubuntu/") en la que hablan del "Gestor de dispositivos de almacenamiento", que no es más que un editor gráfico del archivo /etc/fstab.

Para instalarlo solo hay que ir al centro de software de ubuntu, buscar el "Gestor de dispositivos de almacenamiento" e instalarlo. Una vez instalado lo encontraremos en < Sistema - Administración - Dispositivos de almacenamiento >.

Con este gestor podemos hacer que cualquier usuario pueda montar las particiones deseadas, con lo que dejará de pedirnos la dichosa autentificación, podemos decirle que particiones se montan automáticamente al inicio y un sinfín de opciones más.Espero que os sea de ayuda.

Saludos.

---

### Post by guillermolisi on 2009-11-11
> **granjer said:**
> Bueno, después de leer este post y otros como este sin solución, al fin encontré un programa que da solución a este problema. 

Copio y pego de [aquí]("http://d800ubuntu.blogspot.com/2009/11/montar-particiones-sin-contrasena.html"):

Espero que os sea de ayuda.

Saludos.
Lo has puesto en practica y funciona correctamente ?

---

### Post by granjer on 2009-11-12
> **guillermolisi said:**
> Lo has puesto en practica y funciona correctamente ?

Si. Aunque ahora me encuentro con otro problema, y es que no me deja compartir la particion en red. A ver si consigo arreglarlo.

Saludos.

---

### Post by Umanchuk on 2009-11-15
tengo un problema parecido con ese mensaje de error pero no tiene q ver nada con particiones la cosa es que el error me lo lanxa al querer instalar programas no puedo entrar al virtualbox no puedo modificar configuracion de usuarios puedo entrar como root en terminal la ventana que me lanxa el error tiembla y se desaparec dice 

[I]a politica del sistema impide modificar la configuracion

[/I]Una aplicacion esta intentando realizar una accion que necesita permisos especiales. Es necesario autenticarse para realizar dicha accion.

Fallo de autentificacion

lo triste es q no me deja autentificarme o como soy nuevo en linux tal vez no sepa pero ratifico q dsd terminal si puedo mediante su 

en el virtualbox me dice 

**[Error in SUPR3HardenedMain]("http://forums.virtualbox.org/viewtopic.php?f=7&t=11961&start=0")**


Effective UID is not root (euid=1000 egid=1000 uid=1000 gid=1000) (rc=-10) 
It may help to reinstall VirtualBox.

---


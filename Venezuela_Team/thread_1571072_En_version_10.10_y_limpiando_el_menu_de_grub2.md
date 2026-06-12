---
title: "En version 10.10 y limpiando el menu de grub2"
date: 2010-09-09
forum: Venezuela Team
---

### Post by galanh on 2010-09-09
Ahora me encuentro en la version 10.10, en Maverick Meerkat.
 

 En Lucy Lynx hice el siguiente comando para actualizar a la nueva version:
 

 ```
update-manager -d
``` No se puede dejar por horas la instalacion sola porque te pregunta  
 sobre la actualizacion del Gurb y no sigue hasta que no respondes.
 

 Al terminar la nueva instalacion hice limpieza del menu del Grub2:
  como explican en:
 

 [http://oelliston.wordpress.com/2010/05/22/clean-up-the-new-ubuntu-grub2-boot-menu-how-to-geek/](http://oelliston.wordpress.com/2010/05/22/clean-up-the-new-ubuntu-grub2-boot-menu-how-to-geek/)
 

 1) Con Synaptic removi los tres paquetes del kernel 2.6.32.20
 

 2) edite el archivo **solo lectura** /etc/grub.d/20_memtest86+
 como explican el el link de arriba.
 Hay que guardarlo en /home/yo/temp y luego con el comando remplazarlo.
 

 ```
sudo mv  /home/yo/temp  /etc/grub.d/20_memtest86+
``` todavia me falta poner a bootear el window7 por defecto :D

---


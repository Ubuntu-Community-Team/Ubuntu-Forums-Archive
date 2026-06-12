---
title: "[SOLVED] Pasar Hardy Heron a otro disco"
date: 2008-07-12
forum: Software
---

### Post by rojojuan on 2008-07-12
Hola gente.

Tengo Hardy Heron instalado en un disco IDE. En otro IDE Win (que ya uso muy poco) Agregué uno Sata de mayor tamaño. 
Ahora bien, quiero pasar la instalación completa de Hardy (tal como está), que tengo en el IDE al SATA. 
El IDE donde tengo HH lo formatearía y me quedaría para datos.
Probé con el comando DD pero me deja el disco SATA igual al IDE, desperdiciando la capacidad que tiene el primero.
Hay alguna otra manera de hacerlo, aprovechando su tamaño?
Si la hay, hay que tocar alguna cosa, aparte de modificar el Grub?
Tendré que instalar nuevamente Ubuntu?

---

### Post by Hei Ku on 2008-07-12
Probaste de aumentarle el tamaño desde el gparted? obviamente con la particion desmontada. Desde un LiveCD es lo mas facil.

---

### Post by rojojuan on 2008-07-12
> **Hei Ku said:**
> Probaste de aumentarle el tamaño desde el gparted? obviamente con la particion desmontada. Desde un LiveCD es lo mas facil.

Garicas por responder.
Sí, lo hice con GParted pero después de hacerlo no me reconoció más el disco. Será algún problema del fstab o permiso o algo parecido?

---

### Post by Hei Ku on 2008-07-12
Probaste de montarlo a mano, desde la consola a ver qué dice?

por ejemplo:

sudo mount /dev/sda1 /media/sda1

---

### Post by rojojuan on 2008-07-13
Después de varios intentos logré solucionar el problema. Por si a otro le sirve:
Procedimiento que seguí para trasladar todo el Ubuntu de hdb a sdc.
1.- Con DD if=/dev/hdb of=/dev/hdc b=1M copié el disco.
2.- Con Gparted formatié con ext3 lo que sobró de sdc.
3.- Modifiqué el /etc/fstab incluyendo el nuevo disco.
4.- Otorgué permisos completos sudo chmod 777 /media/sd1,   sudo chmod 777 /media/sd3,  sudo chmod 777 /media/sd2
5.- Modifiqué el /boot/grub/menu.lst para que arranque desde hd2,0
Muchas gracias Hei Ku

---


---
title: "editando grub del karmic - agregando otro s.o."
date: 2010-04-15
forum: Software
---

### Post by mama21mama on 2010-04-15
Hola,

> # (3) Puppy Linux
title Puppy Linux 4.3.1 Frugal
rootnoverify (hd0,6)
kernel /puppy431/vmlinuz pmedia=atahd
initrd /puppy431/initrd.gz 


algo como esto debo poner en el grub del karmic.
pero esta lioso, con el grub2 en mi caso.

Alguien sabe como puedo hacer?

---

### Post by granjero on 2010-04-16
hola mama21mama. El otro día yo agarré un disco rígido desconecté el mio donde tengo ubuntu KK e instalé un winchot....

luego conecté mi disco rígido con ubuntu.
bootié ubuntu e instalé desde el centro de soft el "administrador de arranque"

cuando lo corrí desde Sistema > Administración > Administrador de arranque hizo unos procesos y me agregó solito el winchot en dev/sda1 si que tenga que devanarme mucho el seso....

fijate si te hace lo mismo....

salud!

---

### Post by mama21mama on 2010-04-16
pero no puedo así, yo lo quiero hacer una instalación frugal de puppy.

---

### Post by mama21mama on 2010-04-16
Hola, buscando dias he encontrado la solucion; en el chat irc.irc-hispano.org canal #ubuntu

Para poder hacer funcionar ubuntu karmic koala y puppy linux 4.3.1 instalación frugal

1º

tienes que añadir una entrada al sistema operativo que quieras añadir al grub2 en el archivo /etc/grub.d/40_custom

```
sudo gedit /etc/grub.d/40_custom
```




> 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Puppy Linux 4.3.1 Frugal" {
          insmod hfsplus
          set root=(hd0,1)
          linux /puppy431/vmlinuz pmedia=atahd
          initrd /puppy431/initrd.gz
}


la entrada seria...

> 
menuentry "Puppy Linux 4.3.1 Frugal" {
          insmod hfsplus
          set root=(hd0,1)
          linux /puppy431/vmlinuz pmedia=atahd
          initrd /puppy431/initrd.gz
}


2º

después de modificar el custom haz un

```
sudo update-grub
```

esto ara que la nueva entrada sea guardada en /boot/grub/grub.cfg

4º para ver el menu del grub hay que editar el en el archivo 
```
sudo gedit /etc/default/grub
```

 asegurate de q la linea GRUB_HIDDEN_TIMEOUT= tiene un # delante
luego 

```
sudo update-grub
```

eso es todo,  gracias a fosco_ por los datos.

[Fuente]("http://www.murga-linux.com/puppy/viewtopic.php?p=410885&sid=45ab524bde47b31e6b6b84ab74537863#410885")

---


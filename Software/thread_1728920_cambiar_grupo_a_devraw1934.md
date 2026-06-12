---
title: "cambiar grupo a /dev/raw1934"
date: 2011-04-14
forum: Software
---

### Post by granjero on 2011-04-14
hola, uso Kino para capturar video con una cámara Panasonic. La pc tiene muchos usuarios, de los cuales el único con permisos de admin es el mio. Para que Kino tenga acceso al modulo /dev/raw1934 (placa firewire pci) tengo que ejecutar Kino como superusuario desde consola.

Yo necesito que los usuarios sin permisos de admin capturen video también. 

Tocando y tocando llegué a la feliz conclusión que si le cambio el grupo a /dev/raw1934 a un grupo que hice que se llama todos. Todos los que pertenecen al grupo pueden tener acceso al modulo.

El problema surge cuando la pc se apaga. Luego del reboot los permisos del modulo vuelven a ser root:root y no root:todos como le asigné con

```
sudo chwon root:todos /dev/raw1934
```

En el chat de #ubuntu-es me dijeron que lo tengo que setear en rc.local pero no se como.

alguna idea?

salud!

---

### Post by alfplayer on 2011-04-14
Si /dev/raw1934 se crea cuando inicia el sistema simplemente sería ejecutar ese comando en rc.local (sin sudo porque el usuario es root en rc.local). Si /dev/raw1934 se crea cuando se conecta la cámara creo que es necesario modificar la configuración de udev (no estoy seguro de esto porque nunca lo hice).

---

### Post by granjero on 2011-04-14
hola, ya lo solucioné metiendo mano... al principio no funcionó porque la linea la había puesto debajo del exit 0

/etc/rc.local quedó así:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#linea para que se pueda usar kino por todos los usuarios
chown root:todos /dev/raw1394

exit 0

```

saludos!

---


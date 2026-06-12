---
title: "Que paso con esta Instalacion?"
date: 2009-08-09
forum: Software
---

### Post by Refreshment on 2009-08-09
Albricias:

Tengo 2 Discos Duros. Uno de ellos con Ubuntu. La primera vez instale la version 9.04 de 32 Bits. Una vez lo actualice, reinicie pero nunca mas volvio a subir. Entonces decidi instalar la version 9.04 de 64 bits. Use el "Live CD" de Ubuntu, borre las particiones que hice para el de 32 BITS y cree unas nuevas.

El asunto es que en el "grub" al tiempo de arranque me aparece 2 cosas:
-Iniciar con Ubuntu 2.6.algo.11
-Iniciar con Ubuntu 2.6.algo.13

Es decir, existen remanentes de la instalacion anterior y me estan ocupando varios gigabytes.

Que puedo hacer?

Otra cosa si quiero tener Windows 7 y Ubuntu en el mismo disco. Me recomiendan instalarlo Windows primero y despues Ubuntu? Por lo que he visto, instalarle Windows 7 sobre el Ubuntu es demasiado complejo para mis conocimientos limitados.

Gracias.

---

### Post by guillermolisi on 2009-08-09
> **Refreshment said:**
> Albricias:

Tengo 2 Discos Duros. Uno de ellos con Ubuntu. La primera vez instale la version 9.04 de 32 Bits. Una vez lo actualice, reinicie pero nunca mas volvio a subir. Entonces decidi instalar la version 9.04 de 64 bits. Use el "Live CD" de Ubuntu, borre las particiones que hice para el de 32 BITS y cree unas nuevas.

El asunto es que en el "grub" al tiempo de arranque me aparece 2 cosas:
-Iniciar con Ubuntu 2.6.algo.11
-Iniciar con Ubuntu 2.6.algo.13

Es decir, existen remanentes de la instalacion anterior y me estan ocupando varios gigabytes.

Que puedo hacer?

Otra cosa si quiero tener Windows 7 y Ubuntu en el mismo disco. Me recomiendan instalarlo Windows primero y despues Ubuntu? Por lo que he visto, instalarle Windows 7 sobre el Ubuntu es demasiado complejo para mis conocimientos limitados.

Gracias.
En el Grub veras los kernels que ya utilizaste anteriormente. Por eso tenes el primero que vino con la version final de 9.04, el 2.6.28-11 y el que se genero al actualizar (el que termina con -13).

No ocupan "varios gigabytes" pero aun asi se pueden quitar los que no uses utilizando el gestor de paquetes Synaptics removiendo (con muchisimo cuidado) las versiones antiguas llamadas "image" y "headers".

Mi recomendacion es dejar siempre una antigua que se sepa funciona bien, por si pasa algo malo con el kernel nuevo, para que sea una alternativa cuando el mas reciente no funciona.

Para contar con una maquina con dual-boot Win-Ubuntu las recomendaciones son primero instalar Win y luego Ubuntu. El gestor de inicio de Win borra la informacion que exista previa a su instalacion, por lo que si tenias Ubuntu y luego instalas Win dejara Ubuntu sin posibilidad de inicio (tendras que reconstruir Grub para recuperar el dual boot con Linux). Todo esto no es para usar Wubi, sino cada SO en una particion distinta.

---

### Post by Refreshment on 2009-08-09
Gracias Guillermo.

Pero que hay de las carpetas? Por que veo folders con el nombre del usuario que utilice para la instalacion del Ubuntu de 32 Bits.

Entonces cual es la forma de eliminar o desinstalar completamente Ubuntu? Dado que probalemente use un dual boot con Windows 7, tendre que hacerlo eventualmente.

---

### Post by staar on 2009-08-09
mmm posteá la salida de correr ```
sudo fdisk -l
``` en una terminal, para que veamos como están tus particiones, y ver si la anterior instalación todavía está ahí...

saludos

---

### Post by fgl82 on 2009-08-10
Hola, como te dijeron, tenés que fijarte cómo están tus particiones.

Si ya tenés hechas dos particiones, entonces es más fácil.

Pero en cualquier caso podés hacer lo siguiente:

1) Booteá desde el live cd de ubuntu.
2) Si no viniera instalado el gestor de particiones (creo que sí, pero por las dudas) deberías instalarlo, se llama gparted
3) Desde el gparted vas a poder borrar toda tu instalación de ubuntu, dado que te va a permitir formatear por completo la unidad donde lo tengas ubicado (esto acarrea por supuesto la pérdida de todos tus datos, no sólo el SO).
4) En caso de que no tengas 2 particiones, también podés crearlas desde gparted achicando la partición existente y creando una nueva en el espacio libre disponible.
5) Luego, podés reiniciar la pc e instalar Windows 7 y luego Ubuntu

¡Saludos!

---

### Post by Refreshment on 2009-08-10
Excusas por la tardanza. Dure un tiempo fuera y ademas no tengo ni idea quien es el senor "sudo". De todas formas esto fue lo que imprimio en pantalla:

[IMG]http://img195.imageshack.us/img195/7691/tablaparticiones2.png[/IMG]

En lo referente al disco el directorio "/" figura con 14 GiB y el "/home" con 900 Gib. Ahora bien estoy al tanto de que los discos no tienen disponioble to el espacio publicitado pero no me parece que solo valla a tener 914 GiB disponible. No me parce posible que se consuman sobre 70 Gib solo en instalacion.

---

### Post by guillermolisi on 2009-08-10
Es -l, no -i. Deberia quedarte "fdisk -l" (menos ele minuscula)

---

### Post by staar on 2009-08-10
hay dos particiones de linux (una bastante más grande que la otra), podrías postear la salida (podés pegar el texto en un mensaje, es más cómodo que una captura, y si usas el tag CODE mejor, solo recordá que en la terminal para copiar tenés que apretar Ctrl + Shift + C) de correr ```
mount
``` para ver cual es la partición que no está siendo usada por el sistema...

saludos

---

### Post by Refreshment on 2009-08-10
Si, una particion es mucho mas grande que la otra. Pero no recuerdo bien los tamanos que le di. Recuerdo que al swap le di 4 GB, a Root no recuerdo y todo el resto a home.

Los resultados del "mount":

yanki@TenHen:~$ mount
/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/yanki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=yanki)
/dev/sda5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

Para que sirve esto?

Por cierto, donde me inicio para aprender un poco estos comando?

---

### Post by staar on 2009-08-10
el comando mount (corrido a secas, sin parámetros) lista los sistemas de archivos (incluyendo, pero no limitándose a, las particiones) actualmente montados en el sistema, el fdisk con el parámetro -l lista información sobre los discos conectados, en particular la tabla de particiones, debe correrse como administrador, por lo que se le agrega el sudo adelante...

bueno, particiones con otra instalación de ubuntu no hay, lo que se me ocurre es que hayas usado la misma (sin haberla formateado) para el /home en ambas instalaciones, es correcto? si es así podés borrar lo viejo sin problema...

podés pasarte por los threads que están como stickys en la parte inicial del foro, tienen buena información, y uno de ellos contiene muchos enlaces que te pueden servir para aprender...

la otra es el simple toqueteo, hasta que rompés algo e intentás arreglarlo :-D

saludos

---

### Post by Refreshment on 2009-08-10
Gracias por tu ayuda star. :)
> **staar said:**
> 

bueno, particiones con otra instalación de ubuntu no hay, lo que se me ocurre es que hayas usado la misma (sin haberla formateado) para el /home en ambas instalaciones, es correcto? si es así podés borrar lo viejo sin problema...

saludos
Recuerdo claramente, que introduje el live cd y borre las partciones. 
De todas formas 900 en home y 14 en root para un disco de 1 TB. Donde se fue el resto?

Revisando en "mis lugares" encontre carpetas de la instalacion anterior y no me deja borrarlas. Estoy usando windows en este momento. Luego vere que carpetas son esas y veremos si me pueden dar una mano.

Gracias a todos por la ayuda hasta el momento.

---


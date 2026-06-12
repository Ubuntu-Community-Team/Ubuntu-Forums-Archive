---
title: "Ayuda en instalacion"
date: 2011-03-21
forum: Software
---

### Post by JoSeba76 on 2011-03-21
Hace poco me compre una notebook Dell Inspiron M5030, con las siguientes características:

AMD Athlon 2.2 64bit
3GB memoria ram ddr3
500GB de disco duro

Tengo un problema de instalacion con Ubuntu 10.10 y Ubuntu 11.04 en esta notebook, el problema es que luego de la seleccion de idioma y luego de elegir si probar o instalar, empiesa a cargar y la instalacion o la prueba queda en una pantalla negra con el guion bajo titilando, lo he dejado por unos 45 min aprox y nada.

Por lo que he leido en otros foros tiene algo q ver con  la forma en que se maneja el disco duro (tecnologia ATA o con tecnologia AHCI) eh probado lo siguiente:
- Desactivar el modo AHCI desde el bios y en windows (lo necesito por cuestiones laborales) y al reiniciar win7 no lo hace
- Instale Ubuntu 10.04 (instala y botea bien) sin embargo al actualizarso al 10.10 me vuelve a tirar el mismo problema
- Pude instalar Ubuntu 10.10, pero tube q desactivar el AHCI desde la pantalla de inicio del LiveUSB (despues de elegir el idioma), puse F6 y luego AHCI=OFF, sin embargo al sacar el USB y arrancar normalmente, este no llega a la pantalla de login
- y por ultimo tengo instalado debian squezze, me instalo y me carga sin problema

Se me a ocurrido una solucion, que no se como hacerla, ya q soy un usuario nuevo en ubuntu: y es instalar en modo AHCI=OFF y una ves q termine la instalacion, antes de sacar el USB y reiniciar, modificar desde la terminal (o si es en modo grafico mejor) algun archivo de instalacion para q quede de ese modo

desde ya muchas gracias

Seba

---

### Post by gmunioz on 2011-03-21
Para activar esa opción por defecto en el inicio de tu pc:
Ubuntu ahora trae por defecto el gestor de arranque Grub2.
Para desactivar el ACPI en el arranque del sistema:

Editas el archivo /etc/default/grub
sudo su
nano /etc/default/grub

Buscas la línea:

GRUB_CMDLINE_LINUX=""

Y la dejas asi:

GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"

Guardas el archivo
Actualizas el GRUB

update-grub

La próxima vez que reinicies la máquina, iniciará con dichas opciones, en el ejemplo se han desactivado también APIC y LAPIC

Para poder editar el archivo debes hacerte dueño de la partición de instalación, una vez  terminada la misma, en ves de reiniciar continuas usando el sistema live y:

En una consola (aplicaciones &#8211; Accesorios &#8211; Terminal)
Ejecutas
Para loguearte como administrador

sudo su

Para identificar la partición de la instalación de Ubuntu en el rígido

fdisk -l

suponiendo sea /dev/sda1

Para montarla

mount /dev/sda1 /mnt

Si /boot esta en partición separada, suponiendo sea /dev/sda2

mkdir /mnt/boot
mount /dev/sda2 /mnt/boot

Monta los dispositivos del sistema

mount - &#8211;bind /dev /mnt/dev
mount - &#8211;bind /proc /mnt/proc
mount - &#8211;bind /sys /mnt/sys

chroot del sistema instalado en el disco y montado

chroot /mnt

Editas el archivo /etc/default/grub

nano /etc/default/grub

Guardas el archivo con los cambios sugeridos

Cierras el editor y ejecutas para incorporar los cambios

update-grub

Y ya puedes cerrar la sesión y reiniciar.

---

### Post by JoSeba76 on 2011-03-21
Gracias gmunioz por la ayuda, sin embargo hay algo que creo que estoy haciendo mal, voy a poner unos screens de lo que tengo por ahite da un mejor panorama de lo que tengo


Esta es la particion de mi disco, sda5 es el root (/) y el sda7 el home.

[[IMG]http://img863.imageshack.us/img863/3912/particiones.png[/IMG]](http://img863.imageshack.us/i/particiones.png/)

Monto en el sda5, en la particion raiz /

[I]mkdir /mnt/boot
mount /dev/sda5 /mnt/boot[/I]

va todo bien, hasta que monto los dispositivos del sistema:

[I]mount &#8211;bind /dev /mnt/dev
mount &#8211;bind /proc /mnt/proc
mount &#8211;bind /sys /mnt/sys[/I]

ahi me larga un mensaje

[[IMG]http://img31.imageshack.us/img31/8479/grubbind.png[/IMG]](http://img31.imageshack.us/i/grubbind.png/)

despues pruebo con:
*mount --bind /dev /mnt/dev*

[[IMG]http://img88.imageshack.us/img88/8479/grubbind.png[/IMG]](http://img88.imageshack.us/i/grubbind.png/)

y por ultimo el chroot

[[IMG]http://img822.imageshack.us/img822/2541/chroot.png[/IMG]](http://img822.imageshack.us/i/chroot.png/)

eh podido modificar el archivo desde nano, sin embargo cuando intento actualizar el grub me da un error, 

en fin espero aver sido lo mas especifico posible, y de nuevo gracias por la ayuda.

NOTA: actualise debian en mi notebook y ahora me tiro el error del cuelgue, la pantalla negra al iniciar el sistema

---

### Post by gmunioz on 2011-03-22
No tienes /boot en partición separada.
Por lo tanto solo debes ejecutar:

Para montarla
sudo su
mount /dev/sda5 /mnt

Para montar los dispositivos del sistema

mount - &#8211;bind /dev /mnt/dev
mount - &#8211;bind /proc /mnt/proc
mount - &#8211;bind /sys /mnt/sys

Para chroot del sistema instalado en el disco y montado

chroot /mnt

Para editar el archivo /etc/default/grub

nano /etc/default/grub

Guardas el archivo con los cambios sugeridos

GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"

Cierras el editor y ejecutas para incorporar los cambios

update-grub

Y ya puedes cerrar la sesión y reiniciar.

Ahora:
Si tienes Debian instalado
¿Qué Grub estás usando, el de Ububntu o el de Debian?
¿Cuál es la partición de Ubuntu /deb/sda5 ó /dev/sda7?

---

### Post by JoSeba76 on 2011-03-24
Mil gracias gmunioz, y disculpa la tardanza, pero recien ahora tube tiempo para poder dedicarme a la instalacion, pude instalar perfectamente y sin problemas ubuntu 10.10

[[IMG]http://img189.imageshack.us/img189/2342/pantallazo1qk.png[/IMG]]("http://img189.imageshack.us/i/pantallazo1qk.png/")



[I]¿Qué Grub estás usando, el de Ububntu o el de Debian?
¿Cuál es la partición de Ubuntu /deb/sda5 ó /dev/sda7?[/I]

yo cuando instale debian borre ubuntu, siempre instale de la misma forma en el sda5 puse el root (/) y en el sda7 puse el home sea debian o ubuntu y cuando actualise debian se me trabo al reiniciar
En este caso hice lo mismo, puse "/" en sda5 y home en sda7 (formate ambas particiones)

Sin embargo me gustaria corregirte ya que en esta parte:

mount –bind /dev /mnt/dev
mount –bind /proc /mnt/proc
mount –bind /sys /mnt/sys

tube que poner de la siguiente manera:

mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

con 2 guion medio delante de bind

Ahora a mi me queda la siguiente duda:
Porque si despues de instalar ubuntu tengo q montar esas partes ?

Mil gracias de nuevo, Seba

(como pongo solucionado en el mensaje)

---

### Post by gmunioz on 2011-03-25
1- Si es doble guión, pero no se ve, edito con espacio para que se vea.
2- Lo que ocurre es que desde una sesión live, estas trabajando con el sistema live, del cdrom, cargado en memoria y lo que necesitas hacer es trabajar sobre el ubuntu instalado y para eso debes montar el sistema instalado en una jaula mediante chroot, así dentro de la ventana de la terminal todo lo que haces lo haces sobre el sistema instalado y no sobre el sistema que inició el pc.

---


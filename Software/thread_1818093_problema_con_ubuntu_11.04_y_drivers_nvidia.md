---
title: "problema con ubuntu 11.04 y drivers nvidia"
date: 2011-08-04
forum: Software
---

### Post by sitodonosti on 2011-08-04
Hola, hace poco instale ubuntu 11.04 en un ordenador, con una tarjeta ati, y unity iba bien y demás. Ahora he querido instalarlo en otro que tengo desde hace 5 años, tarjeta gforce 8600 gt, el caso es que al instalarlo no me aparece con unity sino con gnome.

Bueno intente instalar gnome 3.0 pero no me funcionaba, asique pense pues será el driver. Intente instalar el nuevo driver bajandomelo desde la misma página de nvidia. Total que cerre sesión presione alt+contrl+f1 y no me parece nada. Osea no puedo instalar el nuevo driver. 

Espero haberme explicado. Sabeis a q es debido, tanto lo de no tener unity como el porque no puedo acceder al tty1?

---

### Post by guillermolisi on 2011-08-04
Es conocido que teniendo Unity al instalar Gnome3 el primero se rompe y hay que realizar todo un proceso de recuperacion (si no se puede/quiere reinstalar).

El tema del driver es cosa aparte y para lograr instalarlo primero cambiaria el driver de ATI por el VESA para luego instalar el de nVidia.

---

### Post by sitodonosti on 2011-08-05
> **guillermolisi said:**
> Es conocido que teniendo Unity al instalar Gnome3 el primero se rompe y hay que realizar todo un proceso de recuperacion (si no se puede/quiere reinstalar).

El tema del driver es cosa aparte y para lograr instalarlo primero cambiaria el driver de ATI por el VESA para luego instalar el de nVidia.

no si en el que quiero instalar gnome3 no tengo unity tengo el gnome que te instala ubuntu en vez de unity, el 2. algo, no me acuerdo muy bien.

Pero si mi tarjeta es nVidia como voy a instalar un driver ati?

---

### Post by gmunioz on 2011-08-05
Para instalar el driver propietario de nvidia, es necesario iniciar en modo texto, al iniciar se pulsa escape, en el menu del grub se elige netroot, la contraseña es la de usuario, ahora en modo solo texto, consola, terminal, se puede instalar el driver, siguiendo las indicaciones de la página de nvidia.

---

### Post by guillermolisi on 2011-08-06
> **sitodonosti said:**
> no si en el que quiero instalar gnome3 no tengo unity tengo el gnome que te instala ubuntu en vez de unity, el 2. algo, no me acuerdo muy bien.

Pero si mi tarjeta es nVidia como voy a instalar un driver ati?
Perdon, me quede con la tarjeta de video de la primer maquina que mencionaste.

Para instalar el driver de nVidia tenes que proceder tal como menciono Gmuñoz.

Ubuntu 11.04 instala Unity y Gnome2 y cuando inicias sesion elegis si lo haces con uno o con otro. Cuando instalas Gnome3 se rompe Unity y ahi empiezan los problemas, a menos que primero hayas desinstalado completamente Unity.

Asi y todo, Gnome3 puede que no funcione bien si no detecta capacidades de aceleracion grafica adecuadas, cosa que recien tendrias despues de instalar correctamente el driver nVidia.

---

### Post by sitodonosti on 2011-08-25
> **gmunioz said:**
> Para instalar el driver propietario de nvidia, es necesario iniciar en modo texto, al iniciar se pulsa escape, en el menu del grub se elige netroot, la contraseña es la de usuario, ahora en modo solo texto, consola, terminal, se puede instalar el driver, siguiendo las indicaciones de la página de nvidia.

No tengo la opción que me dices de netroot...solo recovery y safe mode... lo consegui una vez pero al volver a instalar ubuntu no me a aparecido...

---

### Post by gmunioz on 2011-08-25
Si no aparece el menu del Grub:
Editas el archivo /etc/default/grub
sudo su
gedit /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
**GRUB_HIDDEN_TIMEOUT=5**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Cambias 0 por un tiempo en segundos suficiente, en el ejemplo 5, de espera para pulsar escape:
GRUB_HIDDEN_TIMEOUT=5
Guardas el archivo
Cierras Gedit y como dice el el principio del archivo, ejecutas
update-grub, para que el cambio se registre.
Reinicias.
Pulsas escape
En el menu del Grub eliges recovery
En el submenu eliges netroot.

---


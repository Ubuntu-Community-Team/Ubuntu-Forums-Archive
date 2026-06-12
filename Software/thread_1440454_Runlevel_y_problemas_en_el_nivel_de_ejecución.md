---
title: "Runlevel y problemas en el nivel de ejecución"
date: 2010-03-27
forum: Software
---

### Post by chulelinux on 2010-03-27
Qué tal, 
Tengo instalado Karmic y no puedo modificar el modo en que inicia el sistema. Con el sys rc conf modifico los servicios que quiero habilitar o desabilitar y no pasa nada. Pero si cambio el nivel de ejecución por terminal por ej con init 5, ahí sí me modifica los servicios que esta corriendo el sistema. Es como si el sistema se iniciase con un nivel de ejecución por default que no se puede modificar y no pude encontrar como solucionarlo pues entre otras cosas quiero que arranque con cups habilitado para usar la impresora pero siempre lo tengo que habilitar manualmente. 

Se agradece cualquier ayuda porque quiero dejar de depender absolutamente del win pero siempre me faltan 2 para el peso.
slds

---

### Post by alfplayer on 2010-03-27
La instalación típica de Ubuntu inicia por defecto con el runlevel 2. Se puede editar los symlinks de /etc/rc2.d o se puede usar una intefaz gráfica como Boot-Up Manager que se instala con el paquete "bum".

---

### Post by chulelinux on 2010-04-01
Gracias Alfplayer... el tema es que ya probé con boot-up manager y el tema es que no me modificaba el inicio. Eso es lo raro que me sucede, no se modifica el modo en que inicia. Por otro lado, runlevel en la terminal me tira unknow.
Sls

---

### Post by Mister X on 2010-04-02
no se te entendí bien, pero podes editar el runlevel por defecto en /etc/init/rc-sysinit.conf
```
# Default runlevel, this may be overriden on the kernel command-line
# or by faking an old /etc/inittab entry
env DEFAULT_RUNLEVEL=2

```

---

### Post by chulelinux on 2010-04-02
El script rc-sysinit está en runlevel 2 por default... el tema es que no inicia en 2. Prendo la máquina y no me carga el nivel de ejecución por defecto. Ahora si pongo en un terminal init 2, si se carga todo lo que corresponde a ese nivel de ejecución. Dejo una copia del scrip de rc-sysinit por si alguien me puede ayudar o ve algún error. Otra cosa que di cuenta es que si no cargo manualmente el nivel de ejecución con init 2 y reinicio la máquina, el grub de inicio no se comporta de la misma manera (se queda frenado en grub esperando que elija el SO) que si la reinicio habiendo cargado manualmente el nivel 2 antes(carga automáticamente el SO que tengo marcado por defecto). 
No le encuentro la vuelta... 



# rc-sysinit - System V initialisation compatibility
#
# This task runs the old System V-style system initialisation scripts,
# and enters the default runlevel when finished.

description	"System V initialisation compatibility"
author		"Scott James Remnant <scott@netsplit.com>"

start on filesystem and net-device-up IFACE=lo
stop on runlevel

# Default runlevel, this may be overriden on the kernel command-line
# or by faking an old /etc/inittab entry
env DEFAULT_RUNLEVEL=2

# There can be no previous runlevel here, but there might be old
# information in /var/run/utmp that we pick up, and we don't want
# that.
#
# These override that
env RUNLEVEL=
env PREVLEVEL=

task

script
    # Check for default runlevel in /etc/inittab
    if [ -r /etc/inittab ]
    then
	eval "$(sed -nre 's/^[^#][^:]*:([0-6sS]):initdefault:.*/DEFAULT_RUNLEVEL="\1";/p' /etc/inittab || true)"
    fi

    # Check kernel command-line for typical arguments
    for ARG in $(cat /proc/cmdline)
    do
	case "${ARG}" in
	-b|emergency)
	    # Emergency shell
	    [ -n "${FROM_SINGLE_USER_MODE}" ] || sulogin
	    ;;
	[0123456sS])
	    # Override runlevel
	    DEFAULT_RUNLEVEL="${ARG}"
	    ;;
	-s|single)
	    # Single user mode
	    [ -n "${FROM_SINGLE_USER_MODE}" ] || DEFAULT_RUNLEVEL=S
	    ;;
	esac
    done

    # Run the system initialisation scripts
    [ -n "${FROM_SINGLE_USER_MODE}" ] || /etc/init.d/rcS

    # Switch into the default runlevel
    telinit "${DEFAULT_RUNLEVEL}"
end script

---

### Post by chulelinux on 2010-04-02
Pude encontrar algo que al fin solucionó el problema.... Según lo que encontré es un Bug de la versión de upstar que no lanza los scrips. Esta funciona bien: 

sudo apt-get install upstart=0.6.3-10 

y para evitar tener que destildarla en las actualizaciones podemos usar

sudo apt-get install wajig
sudo wajig hold upstart

y para desbloquearla

sudo wajig unhold upstart

La info y solución la encontré en [http://www.ubuntu-es.org/?q=node/121357#comment-370726](http://www.ubuntu-es.org/?q=node/121357#comment-370726)

Saludos

---


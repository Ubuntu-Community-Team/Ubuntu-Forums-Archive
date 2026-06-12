---
title: "[SOLVED] Problema Vbox Puel 1.6 error arranque de windows XP"
date: 2008-06-23
forum: Software
---

### Post by Cristian CP on 2008-06-23
Hola gente:
Quería consultarle, porque cuando trato de arrancar la maquina virtual de XP me tira un msj de error que paso a pegar;
"
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}"

Bueno, espero si alguien sabe como resolverlo. Saludos a todos.

---

### Post by guillermolisi on 2008-06-23
> **Cristian CP said:**
> Hola gente:
Quería consultarle, porque cuando trato de arrancar la maquina virtual de XP me tira un msj de error que paso a pegar;
"
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}"

Bueno, espero si alguien sabe como resolverlo. Saludos a todos.

Ese error aparece cada vez que actualizas el kernel de Ubuntu y no se acompaña la instalacion de los modulos guest y el que corresponde al vboxdrv (vboxdrv.ko) de VirtualBox para el nuevo kernel instalado y en uso (booted).

Por ejemplo, actualmente estoy usando el kernel 2.6.24-19-generic. Para que mis VM de VBox OSE funcionen tengo que tener instalados los paquetes:
[INDENT]virtualbox-ose-guest module for linux-image-2.6.24-19-generic
[/INDENT][INDENT]virtualbox-ose module for linux-image-2.6.24-19-generic
[/INDENT]Si los buscas con Synaptic (con poner virtualbox alcanza) te aparece todo lo que necesitas y te falta instalar. En tu caso deberian ser los indicados con PUEL en lugar de OSE (a menos que Sun no distribuya los modulos PUEL tal como lo hace con la version OSE y se obtengan del site de VirtualBox).

Proba y cualquier cosa avisa.

---

### Post by sdennie on 2008-06-24
Si estas usando el PUEL, despues de actualizar el kernel tenés que compilar el driver.  Es re-facil:

```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by Cristian CP on 2008-06-24
Si, Vor!! Esta era la solucion, muy fácil como decis, había buscado por ese lado pero no habré puesto bien el nombre del driver. Saludos!

---


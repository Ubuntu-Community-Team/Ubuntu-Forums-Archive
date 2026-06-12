---
title: "VirtualBox - Kernel driver not installed"
date: 2013-03-24
forum: Software
---

### Post by aledruetta on 2013-03-24
Hola comunidad!

Tengo un problema con VirtualBox en Ubuntu 12.04.2. Cuando quiero iniciar una máquina virtual me tira este error:
```
 Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


```
Ya ejecuté en el terminal:
```
sudo /etc/init.d/vboxdrv setup
```
Y el resultado fue:
```
sudo: /etc/init.d/vboxdrv: comando não encontrado
```
También verifiqué que el paquete DKMS ya está instalado.

Sé que es un error que ya ha sido reportado en varios lugares, estuve googleando. Pero no he encontrado solución.

Alguna sugerencia?

---

### Post by guillermolisi on 2013-03-25
Por que no verificas la existencia y permisos de ese archivo en /etc/init.d ?

En mi caso ```
ls -al /etc/init.d/vboxdrv 
-rwxr-xr-x 1 root root 12629 Mar  5 11:43 /etc/init.d/vboxdrv
```

---

### Post by aledruetta on 2013-03-25
Hola Guillermo,

El archivo no existe... y si intento instalarlo me dice que no ha podido localizar el archivo vboxdrv.

Por qué será?

---


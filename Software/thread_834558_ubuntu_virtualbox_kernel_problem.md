---
title: "ubuntu virtualbox kernel problem"
date: 2008-06-19
forum: Software
---

### Post by juanlagrutta on 2008-06-19
Antes que nada, no puedo creer lo espectacular que es linux, ubuntu, realmente no lo conocia. Hace 1 mes que lo tengo y lo estoy conociendo.
Tengo la version Hardy Heron para AMD 64. creo.
El problema, necesito tener el virtualbox dentro de ubuntu porque uso autoca y realmente funciona bien ahi. Al principio instale virtualbox, me funcionaba bien, excepto por los USB que mas alla de hacer todas las cosas que estan publicadas me fue imposible conseguirlo. Instale el windows xp y el autocad, funcionaba perfecto hasta que una vez quise iniciar virtualbox y me tiro este error:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Probe todo lo que sale publicado, pero me fue imposile hacerlo funcionar.
Espero que alguien me ayude porque ya no encuentro nada nuevo para hacer.
Creo que todo empezo cuando se me actualizo el sistema........

Espero que alguien me ayude porque necesito usar AutoCad, y odio WINDOWS.

Desde ya muchas gracias.
Saludos.

---

### Post by mauimike on 2008-06-19
Check 'proposed' in your Software Sources. Reload and then install ose-modules for the new kernel.

---

### Post by Mister X on 2008-06-19
La funcionalidad de USB y otras tambien interesantes solamente estan en la version comercial, no en la libre.

---

### Post by juanman on 2008-06-19
En español a 'proposed' se les llama paquetes no publicados...

---

### Post by sdennie on 2008-06-19
En realidad es mas facil a usar virtualbox desde: [http://www.virtualbox.org/](http://www.virtualbox.org/).  Lo que pasa es que despues de actualizar el nucleo no tenes el driver pero con lo de virtualbox.org, si tenes un problema asi, podes decir:

```

sudo /etc/init.d/vboxdrv setup

```

Y listo.  

Antes de instalar el .deb desde virtualbox.org debes borrar virtualbox-ose:

```

sudo apt-get purge virtualbox-ose

```

---


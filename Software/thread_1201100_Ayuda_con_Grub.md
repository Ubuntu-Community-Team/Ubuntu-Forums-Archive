---
title: "Ayuda con Grub"
date: 2009-06-30
forum: Software
---

### Post by Plastiko on 2009-06-30
Que tal, tengo un par de dudas y quisiera ver si me pueden ayudar a resolver este pequeño detalle que tengo con Grub.

Acabo de resivir una actualización y cuando inicia Grub me salen 2 Kernel de Ubuntu, no se si sea necesario quitar el que ya no uso de la lista de inicio o dejarlo así como esta y la segunda, como hago para que GRUB tome Win XP como boot primario?

les dejo una pic.

Saludos.

---

### Post by staar on 2009-06-30
si la nueva revisión del kernel te funciona bien, podés borrar la anterior sin dramas si querés, el sistema la deja por cualquier problema que pueda surgir con la nueva y que no te permita iniciar...

para editar la lista del grub (y muchas otras opciones de este) se modifica el archivo /boot/grub/menu.lst, la opción ```
default X
``` donde X es un número (empezando desde 0), indica cual es la entrada seleccionada por defecto en el menú, si nunca la modificaste debe estar en 0, y, por ejemplo, para que seleccione XP con el menú asi como lo tenés, tendrías que cambiarlo por 6 (porque XP está en la sexta línea del menú), OJO que para modificar este archivo tenés que hacerlo con sudo ```
sudo gedit /boot/grub/menu.lst
```

existe un programa, llamado startup-manager ```
sudo aptitude install startup-manager
``` que permite modificar varias opciones del grub de manera gráfica, entre ellas cuantos kernels querés que apartezcan en el grub, una vez instalado, lo encontrás en Sistema > Administración > Administrador de arranque

saludos

---

### Post by bichopro on 2009-06-30
Borrar un kernel antiguo

Se pueden seguir los siguientes pasos:

verificar las versiones disponibles en nuestro sistema:

> sudo dpkg -l | grep linux-image

ejecuta el comando:

> uname -r

te mostrara la version del kernel booteado

borrar las versiones antiguas que no utilizamos:

> sudo apt-get remove --purge KERNEL


Donde KERNEL es la versión a eliminar, algo del estilo "linux-image-2.6.20-15-generic".

Tambien puedes instalar ubuntu tweak que tiene una funcion de un click para hacerlo

---

### Post by Plastiko on 2009-06-30
> **staar said:**
> si la nueva revisión del kernel te funciona bien, podés borrar la anterior sin dramas si querés, el sistema la deja por cualquier problema que pueda surgir con la nueva y que no te permita iniciar...

para editar la lista del grub (y muchas otras opciones de este) se modifica el archivo /boot/grub/menu.lst, la opción ```
default X
``` donde X es un número (empezando desde 0), indica cual es la entrada seleccionada por defecto en el menú, si nunca la modificaste debe estar en 0, y, por ejemplo, para que seleccione XP con el menú asi como lo tenés, tendrías que cambiarlo por 6 (porque XP está en la sexta línea del menú), OJO que para modificar este archivo tenés que hacerlo con sudo ```
sudo gedit /boot/grub/menu.lst
```existe un programa, llamado startup-manager ```
sudo aptitude install startup-manager
``` que permite modificar varias opciones del grub de manera gráfica, entre ellas cuantos kernels querés que apartezcan en el grub, una vez instalado, lo encontrás en Sistema > Administración > Administrador de arranque

saludos
Ah buenisimo gracias lo voy a intentar en un momento y comento.

> **bichopro said:**
> Borrar un kernel antiguo

Se pueden seguir los siguientes pasos:

verificar las versiones disponibles en nuestro sistema:



ejecuta el comando:



te mostrara la version del kernel booteado

borrar las versiones antiguas que no utilizamos:




Donde KERNEL es la versión a eliminar, algo del estilo "linux-image-2.6.20-15-generic".

Tambien puedes instalar ubuntu tweak que tiene una funcion de un click para hacerlo

Si de hecho es lo que quiero hacer borrar el kernel que ya no uso ya que la lista es muy grande y quiero resumir.

Gracias.

Saludos.

---

### Post by Plastiko on 2009-06-30
Bueno ya pude poner Xp como boot primario.

pero quise instalar el programa que me menciona **staar **pero me sale el siguiente error

```
mhz@IBM:~$ sudo aptitude install startup-manager
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "startup-manager"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "startup-manager"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

```y con respecto a quitar el kernel que ya no utilizo me sale esto:

```
mhz@IBM:~$ sudo apt-get remove --purge linux-image-2.6.28.11-generic
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete linux-image-2.6.28.11-generic

```Bueno como quiera que sea lo principal que deceaba lo pude resolver gracias a ustedes.

Una vez mas gracias y a seguir aprendiendo.

Saludos.

---

### Post by staar on 2009-06-30
capaz (es muy probable, hace mucho que no lo uso o instalo) que me equivoqué en el nombre exacto del paquete, probá buscándolo por Synaptic pero quitando, o corriendo de lugar, el guión...

saludos

---


---
title: "Grub2: error 15 (Quiero llorar)"
date: 2009-12-24
forum: Software
---

### Post by daggaz on 2009-12-24
Hola,
Ahora sí me enojé con Ubuntu. Resulta que tras la actualización de Jaunty a Karmic tuve muchos problemas que poco a poco solucioné en su mayoría, pero no siempre de la mejor manera y no todos.
Pero bueno, el peor de todos los problemas y creo que el peor problema que he tenido en Ubuntu apareció hoy. Hace un par de días Ubuntu me recomendó probar en nuevo Grub, lo hice y me gustó, por que luego de pasarme a Karmic el Grub anterior marcaba en la lista una instalación de Güindous Vista... Raro, por que no tengo nada de Micro$oft. Al fin, me pareció que Grub 2 funcionaba bien por que ya no mencionaba a Win.
Tras probarlo en unos cinco booteos, decidí pasar a ese Grub luego de que Ubuntu me proguntó si deseaba quedarme con ese Grub. Luego de instalarlo me dijo que copiaría la configuración del Grub anterior, y que si quería borrar esta configuración usara unos comandos que me dió. De momento no lo consideré necesario.
Hoy por la mañana encendí mi PC con algo de prisa y me topé con un mensaje:
```

GRUB, Loading Stage 1.5.

GRUB loading, Pease Wait...
Error 15


```Y ya... Nada más! Me lllevó el diablo un rato tratando de cambiar cosas desde el bios, ya que parecía que eso a algunos les había funcionado, según leí en cinco minutos corriendo por foros en internet desde mi vieja iBook que apenas si puede con Firefox. Al final no logré hecharlo a andar y desistí. Hoy en la noche volví a tratar y nada. inserté un Live CD y cual no es mi sorpesa al notar que la PC no reconoce la Unidad (Y esto no sé si darle gracias a mi "amigo" Koala, que desde que se instaló genero conflictos con el harware y la unidad de DVD no funcionaba correctamente)... Tratao de seleccionar la unidad con la cual inciar y me da dos opciones, HD y algo así como Red, y ninguna de las dos funciona, ambas mandan al final el Grub y ahí queda todo.

Mi última opción es tratar de correr Ubuntu en Live desde un USB, pero como por ahora no tengo una máquina adecauda para hacerlo le pedí a alguien que lo hicera por mi. La cosa es que una vez que tenga mi Ubuntu Live no sé que más debo hacer... Alguien me puede ayudar con eso?
Me urge mucho hacer funcionar esa máquina, tengo trabajo pendiente y muchos archivos que por tonto no he respaldado....

PD: Perdón el tono y el modo del post, pero es que estoy de verdad enjoado con Ubutu el dí de hoy... Me da mucho coraje por que normalmente tengo el sentimiento opuesto :'<

---

### Post by sanderd17 on 2009-12-24
Thanks to the google translate service I've been able to read your message. I've had the same problem with grub. Some webpages said I had to 'chroot' into my ubuntu installation with the live cd to repair grub but I think that's to advanced for me. Anyway, for me the only option was to reinstall ubuntu from the live cd. Normally this should still work. Karmic isn't able to change your bios so I think you changed your bios and made the CD to boot after the HD.

---

### Post by guillermolisi on 2009-12-24
> **sanderd17 said:**
> Thanks to the google translate service I've been able to read your message. I've had the same problem with grub. Some webpages said I had to 'chroot' into my ubuntu installation with the live cd to repair grub but I think that's to advanced for me. Anyway, for me the only option was to reinstall ubuntu from the live cd. Normally this should still work. Karmic isn't able to change your bios so I think you changed your bios and made the CD to boot after the HD.
Traduccion:

Gracias al servicio de traduccion de Google pude leer tu mensaje. He tenido el mismo problema con Grub. Algunas paginas web dicen que debo ejecutar "chroot" dentro de mi instalacion Ubuntu desde el LiveCD para reparar Grub pero pienso que esto es demsiado avanzado para mi. De cualquier forma la unica opcion para mi fue reinstalar Ubuntu desde el LiveCD. Normalmente esto deberia funcionar. Karmic no puede cambiar tu BIOS asi que pienso que cambiaste tu BIOS haciendo que el CD inicie despues que el HD.

PS: Thanks, sander17 :)

---

### Post by oktubrer on 2009-12-24
Mmm yo últimamente estoy probando otras distros, y por comodidad dejo que sobrescriban el grub en el mbr.
Después para restaurar el de ubuntu, desde una consola de root (suponiendo por ejemplo que ubuntu está instalado en /dev/sda1)
```

mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda

```

Desde un live cd es lo mismo.
Esto vuelve a instalar el grub que encuentra en /dev/sda1 en el MBR, por lo que no se si te ayudará.  Quizás en lugar de reinstalarlo habría que repararlo de alguna manera.

Edito: tené en cuenta que esto la forma de referirse al disco y las particiones puede variar, por ejemplo SDx es para discos SATA.

---

### Post by daggaz on 2009-12-25
Hola.
Antes que nada vuelvo a disculparme por el tono del primer post. 

 Ya pude ejecutar el Live CD.Había olvidado que cuando compré la PC le cambié la unidad por que no era quemador de DVD, y me supongo que la BIOS no la reconoce como propia o algo asì, ya ven que las PC de marca luego son muy caprochosas... Asì que le puse la unidad anterior y funcionó muy bien.PUde bajar desde ahí la versión 9.10 y cargarla a un USB.
Ahora estoy corriendo en Live 9.10. Intenté lo que mencionas, que de hecho encontré en una página, pero resulta que la terminal me manda el siguiente error... 
 ```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mount /dev/sda5 /mnt
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# mount --bind /sys /mnt/sys
root@ubuntu:~# chroot /mnt
chroot: no se puede ejecutar la orden «/bin/bash»: Error de formato ejecutable
root@ubuntu:~# 
``` No sé si se deba a que mi pc es a 64bits y quizás la versión de Ubuntu es para 32.
 

 Por cierto, mi *fdisk* es:
 ```
 sudo fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pistas, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6df09df

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         255     2048256   82  Linux swap / Solaris
/dev/sda3             256       38913   310520385    5  Extendida
/dev/sda5            4117       38913   279506871   83  Linux
/dev/sda6             256        4116    31013419+  83  Linux

```
 Estoy pensando muy seriamente en solucionar tipo Windous... Respadar todo en un HD externo, formatear y reinstalr...




Gracias

---

### Post by BionicSeahorse on 2009-12-26
Hols daggaz,

Ya que tienes GRUB2, haz tratado de utilizar [FONT="Courier New"]update-grub[/FONT] desde una terminal dentro de un LiveCD?

No te preocupes por tus datos, ya que GRUB no los toca. GRUB solamente se encarga de inicializar tu disco duro.

Si usas update-grub y no te funciona, intenta borrar todo lo relacionado con grub y reinstalándolo de nuevo:

```
# apt-get remove --purge grub-pc grub-common && apt-get install grub-pc
```

Te paso un link de la mejor guía que he encontrado acerca de GRUB2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Ojalá y ésto te haya servido de algo!

---

### Post by daggaz on 2009-12-26
Hola. Gracias a todos por su ayuda.
Pero ya está todo solucionado, la solución la  encontré en la página **mundogeek.net**. Posteo aquí lo que hice:


 Una vez arrancada la distribución Live CD (vesrión para USB Pendrive en mi caso)abriremos la consola e introduciremos el siguiente comando para ver las particiones disponibles en el disco:
 ```
sudo fdisk -l
``` Debemos buscar la partición en la que se encuentra instaladao Ubuntu en nuestro disco duro (/dev/sda5 en mi caso) y montarla
 ```
sudo mount /dev/sda5 /mnt
``` En el improbable caso de que crearas una partición independiente para */boot* durante la instalación de Ubuntu, también tendrás que montarla, en */mnt/boot*.
 Una vez montada la partición, podremos instalar GRUB 2 usando la instalación anterior. Ejecuta el siguiente comando sustituyendo /dev/sda por el disco en el que quieres instalar el cargador (OJO, el disco, no la partición, es decir, será algo del tipo /dev/sda, no /dev/sdaX)
 ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` Si todo funcionó correctamente debería decir algo como
 ```
Installation finished. No error reported.
    This is the contents of the device map /mnt/boot/grub/device.map.
    Check if this is correct or not. If any of the lines is incorrect,
    fix it and re-run the script `grub-install’.

    (hd0) /dev/sda
``` Reiniciamos, y ahora deberíamos ver nuestro antiguo menú de GRUB 2. Como es posible que alguna entrada haya quedado huérfana, una vez iniciada nuestra distro Linux ejecutaremos el comando
 ```
sudo update-grub
``` Y eso es todo. Sólo necesitamos estos pocos comandos para recuperar GRUB 2 [IMG]http://www.ubuntu-es.org/misc/smileys/smile.png[/IMG]

---


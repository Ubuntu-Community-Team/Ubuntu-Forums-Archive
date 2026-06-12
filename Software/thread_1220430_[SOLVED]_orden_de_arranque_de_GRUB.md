---
title: "[SOLVED] orden de arranque de GRUB"
date: 2009-07-22
forum: Software
---

### Post by drazhe on 2009-07-22
Hola, existe alguna manera de poner un orden espesifico en el GRUB de ubuntu? es decir, instalando asi como bien, pone primero a Ubuntu y luego a los otros SOs, hay alguna manera de poner a XP adelante de todo? cosa de que a menos que se haga algo, arranque XP.

Pregunto, porque me instale mi querido linux en la maquina de mis padres, pero como ellos no son muy duchos en la materia, preferiria que arranque XP sin tener que tocar nada...

---

### Post by staar on 2009-07-22
Alt + F2

*gksudo gedit /boot/grub/menu.lst*

modificar la opción que dice: *default    0*, cambiando el número por el correspondiente a la entrada que se quiere poner por defecto, empezando a contar desde cero, e incluyendo la entrada 'Otros sistemas operativos' como válida...

saludos

---

### Post by Hei Ku on 2009-07-22
Como recomendación, despues de cada edición del menu.lst te conviene hacer:

sudo update-grub

---

### Post by drazhe on 2009-07-23
lo mas parecido a default 0 o al orden que aparece en el GRUB es esta parte del codigo de ese archivo

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1




lo que me estan diciendo es que corte y pegue 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

a la parte de arriba, antes que la de ubuntu???

---

### Post by staar on 2009-07-23
la opción default generalmente está al principio del archivo, si no está podés agregarla vos, es solo una nueva línea de texto que diga ```
default   número
```

si preferis, podés mover la parte de Ventanas hacia arriba, pero fijate de ponerla antes de la línea que pone ```
### BEGIN AUTOMAGIC KERNELS LIST
``` y acordate de borrar o comentar la entrada ```

title Other operating systems:
root
``` para que quede más bonito (no afecta en nada que la dejes)

saludos

---

### Post by drazhe on 2009-07-23
digamos que quedaria algo asi despues del arrelgo??

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-13-generic
uuid 96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro quiet splash 
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid 96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro quiet splash 
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=96cd8b4a-d0ff-4579-8d1d-0440762e5721 ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid 96cd8b4a-d0ff-4579-8d1d-0440762e5721
kernel /boot/memtest86+.bin
quiet



perdon si soy muy molesto con estos temas, no soy muy ducho en temas de linux en general y ya me mande varias...

---

### Post by aledruetta on 2009-07-23
Hola,

Existe un paquete (está en Synaptic) que se llama:
```
startupmanager
``` 
Ahí podés configurar gráficamente varias opciones del Grub, entre ellas, la de qué SO inicia por defecto, cuantos segundos se muestra el menú de arranque, si se muestran varias versiones de Kernel o uno solo, etc.
Es una forma práctica y sencilla como alternativa a las otras opciones comentadas.

Saludos y suerte,
Alejandro.

---

### Post by drazhe on 2009-07-23
aledruetta

Funciona perfecto la aplicacion que me recomendaste!!! ahora mis padres no van a tener problema ya que no tienen que hacer nada raro para que arranque su wuindow$ jejeje

muchas gracias!
solo me quedan los 2 detalles de la resolucion y el plugin para flash de opera, que por alguna razon anda en FF, pero no en el opera......

---

### Post by guillermolisi on 2009-07-23
> solo me quedan los 2 detalles de la resolucion y el plugin para flash de opera, que por alguna razon anda en FF, pero no en el opera......
Por el tema Flash y Opera, fijate en este thread:

[http://ubuntuforums.org/showthread.php?t=1209755](http://ubuntuforums.org/showthread.php?t=1209755)

Si coincide con tu caso, agregate a el. 

Si es otra cosa totalmente distinta, abri otro con un asunto que sea significativo para lo que tratara el thread.

El tema de este thread es otro y lo marco como solucionado.

---


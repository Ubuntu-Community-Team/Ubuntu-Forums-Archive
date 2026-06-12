---
title: "[SOLVED] Kinit"
date: 2008-06-30
forum: Software
---

### Post by Vero1 on 2008-06-30
Hola,

Cuando arranco el sistema, entre otras cosas, me sale lo siguiente:

Kinit: no resume image, doing normal boot.

Despues de éso se va al tty1 pero luego aparece gdm.

Cuál puede ser el problema?

Gracias

---

### Post by Mister X on 2008-06-30
No se si te entiendo el problema, el mensaje de kinit quiere decir que no encontro ninguna imagen (no está restaurando el sistema de una hibernacion) y carga normalmente el sistema.
Tal vez lo que te falta es el splash (la barra de progreso de carga)?

---

### Post by Vero1 on 2008-06-30
No Mister X, 

No hiberné para nada y la barra de progreso sale pero hace como cuando está puesto el CD de Hardy, como si estuviera buscando, hasta que se estabiliza y se va llenando. Eso es otra cosa que me llama la atención.

Repito como es el problema.
Enciendo la máquina y todo va bien hasta que aparece la pantalla negra con varias cosas que no puedo copiar porque va muy rápido. Lo que sí pude copiar es lo que dice de Kinit: no resume image. Doing normal boot. Despues de eso va al tty.1 pero enseguida sale la pantalla naranja con el cursor y luego el login.

---

### Post by Mauro22 on 2008-06-30
Encontre esto:

[quote="Luis"]

Seguimos con bugs de ubuntu, éste es igual de tocapelotas que el anterior, sale un cartel así (aprox según el ordenador) y a los 40 segundos sigue arrancando Loading, please wait…
kinit: name_to_
 dev_t(/dev/disk/by-uuid/489a5508-8b66-471c-a111-4db9076dd216) = hdc5(22,5)
kinit: trying to resume from /dev/disk/by-uuid/489a5508-8b66-471c-a111-4db9076dd216
kinit: No resume image, doing normal boot…
 La solución que he encontrado es reformatear la memoria swap, en mi caso es la partición /dev/sda3 


```
**root@4testing:/home/luis#** swapoff /dev/sda3
**root@4testing:/home/luis#** mkswap /dev/sda3
Setting up swapspace version 1, size = 1159757 kB
no label, UUID=956bfd14-2062-4e04-97d0-2d2e40dc5567
**root@4testing:/home/luis#** update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
```

Y todo vuelve a la normalidad[/quote]

---

### Post by Vero1 on 2008-06-30
Hola Mauro,

Agradezco tu ingformación pero ésto del Kinit apareció de buenas a primeras. Si fuera un bug no tendría que haber aparecido antes(digo yo, por ahí me equivoco). Salvo que sea por la actualización del kernel.

Yo tengo mis serias dudas sobre el xorg.conf que NO es el normal.
Aparte tengo dos problemas mas que están en otros posts, todos producidos despues de la actualización del kernel.

Mauro, hay alguna forma de volver al kernel que tenía antes de la actualización y si es así, es conveniente?

Gracias

---

### Post by Mauro22 on 2008-06-30
Si no eliminaste las entradas del menu.lst del grub, tenes varios kernels para elegir.

Si lo borraste, creo que con grub-update, volves a ponerlos.


Si es conveniente, calculo que no, alguna mejora debe tener, pero si es de vida o muerte, entonces si, ha por el!


:guitar:

---

### Post by Vero1 on 2008-07-01
Mauro 22,

No entiendo mas nada.

No toqué nada, salvo instalar el controlador de nvidia con envying y ya no me aparece lo de kinit, lo que me aparece ahora es algo con respecto al Network Manager, pero al final inicia normalmente.

No toco mas nada por el momento.

Gracias una vez mas por tu interés en mis problemas.:D

saludos

---

### Post by Mauro22 on 2008-07-01
jeje, no hay problema.

"Lo que funciona no se toca!"

---


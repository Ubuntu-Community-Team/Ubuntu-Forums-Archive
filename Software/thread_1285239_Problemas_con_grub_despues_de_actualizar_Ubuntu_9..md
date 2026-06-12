---
title: "Problemas con grub despues de actualizar Ubuntu 9.04"
date: 2009-10-07
forum: Software
---

### Post by heroesfg on 2009-10-07
[SIZE=2]Buenos dias gente, les queria contar lo que me paso cuando actualice Ubuntu 9,04 para que si a alguien le paso lo mismo sepa como solucionarlo.

   Luego de instalar las actualizaciones que tenia, no me arrancaba Ubuntu, grub me tiraba un error 11 algo con "invalid string" o algo parecido y cuando precionaba una tecla que me lo pedia volvia al grub.

    Entonces entre a editar la linea de grub con la tecla e y resulto que al lado de la linea de root aparecia el numero de serie de mi rigido, lo cambie por 'root (hd0,0)' y pude entrar en ubuntu, luego ahi edite el menu.lst (/boot/grub/) y cambie root ..... por root (hd0,0). 

    Espero que le sea de utilidad, acuerdense de entrar a editar este archivo como root (su o sudo). Un saludo
[/SIZE]
"Nunca el peon se come al Rey" Divididos

---

### Post by ALEXEX on 2009-10-07
> **heroesfg said:**
> [SIZE=2]Buenos dias gente, les queria contar lo que me paso cuando actualice Ubuntu 9,04 para que si a alguien le paso lo mismo sepa como solucionarlo.

   Luego de instalar las actualizaciones que tenia, no me arrancaba Ubuntu, grub me tiraba un error 11 algo con "invalid string" o algo parecido y cuando precionaba una tecla que me lo pedia volvia al grub.

    Entonces entre a editar la linea de grub con la tecla e y resulto que al lado de la linea de root aparecia el numero de serie de mi rigido, lo cambie por 'root (hd0,0)' y pude entrar en ubuntu, luego ahi edite el menu.lst (/boot/grub/) y cambie root ..... por root (hd0,0). 

    Espero que le sea de utilidad, acuerdense de entrar a editar este archivo como root (su o sudo). Un saludo[/SIZE][SIZE=2]


Gracias por tu aportación Heroes, fijate que a mi me paso lo mismo hace tiempo, cuando iniciaba con Ubunty, aunque no tengo mucho tiempo para ser sincero.

Lamentablemente a falta de mi conocimiento tuve que darle boom a la netbook e instalar de nuevo el SO, pero creo q e aprendido de mis errores.
[/SIZE]

---

### Post by faktorqm on 2009-10-08
¿El numero de serie de tu disco rigido? Lo dudo seriamente. 

Lo que no dudo es que probablemente tenga el UUID de la particion y no su numero de serie. Para recuperar el UUID de una particion se puede hacer 

```
lbkid /dev/sda1
```

o blkid no recuerdo exactamente. salu2!

---

### Post by guillermolisi on 2009-10-08
Hay un [tutorial]("http://ubuntu-ar.org/node/214") en el website de Ubuntu-ar que explica como recuperar el UUID de una particion de disco rigido.

---

### Post by guisheca on 2009-10-08
Lo que no entiendo es porque una actualización te cambie el UUID del disco.

---

### Post by fmsismo on 2009-10-08
No cambia el UUID del disco a no ser que formatees la partición.  Lo que pudo pasar es que se halla editado el grub.conf y cuando se implemento el cambio genero conflictos.  Igual cuando ve algo no estándar avisa que se quiere hacer con las diferencias de versiones.

---

### Post by staar on 2009-10-08
este es un bug conocido en grub, el problema pasa porque otras distros usan el número de partición para especificarle la partición raíz al grub, y ubuntu usa el uuid```
title           Arch Linux
**root            (hd0,5)**
kernel          /boot/vmlinuz26 root=/dev/disk/by-uuid/d9cb3911-a82b-4d25-873f-de6a999ec931 ro vga=840 quiet
initrd          /boot/kernel26.img

title           Ubuntu 9.10
**uuid            09d8ffe1-c2b1-42b4-bd52-1a31522b60b4**
kernel          /boot/vmlinuz-2.6.31-11-generic root=UUID=09d8ffe1-c2b1-42b4-bd52-1a31522b60b4 ro quiet splash
initrd          /boot/initrd.img-2.6.31-11-generic
quiet
``` entonces, a veces, cuando se corre un update-grub (como cuando se actualiza el kernel) este la pifia y reemplaza donde dice *uuid* por *root* (el uuid no cambia), y hay que arreglarlo a mano, como hizo el OP, o volviendo a poner *uuid*...

saludos

---


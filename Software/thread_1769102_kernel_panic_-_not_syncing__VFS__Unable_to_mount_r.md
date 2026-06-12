---
title: "kernel panic - not syncing : VFS : Unable to mount root fs on unknown - block (0,0)"
date: 2011-05-27
forum: Software
---

### Post by granjero on 2011-05-27
Hola, ayer me pasó algo de lo más extraño. Tengo dos PC con Ubuntu 10.04 enfrentadas que tenían un kit teclado/mouse inalámbrico marca microsoft que se interferían mutuamente.
Cansado de escuchar quejas por ese tema compré un kit genius ps2 y saqué uno de los inalámbricos y puse el kit ps2 todo con la pc encendida. Configuro la distribución del teclado, cierro todos los programas y pongo reiniciar para asegurarme que cuando vuelva a encender la máquina tenga todo configurado correctamente. Para mi sorpresa luego del bip del mother y la pantalla con la el nombre del mother me encuentro con la siguiente leyenda.

```
kernel panic - not syncing : VFS : Unable to mount root fs on unknown - block (0,0) 
```

Después de un rato de sufrir y evaluar si iba a reinstalar o qué lo solucioné de la siguiente manera. Gracias m4v.

Bootié una live session de 10.04
Abrí una terminal
```
sudo fdisk -l
```
Ahí vi que la partición de sistema que bootea era /dev/sda5
```
sudo mount /dev/sda5 /mnt
```
luego
```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
```

luego 
```
$ sudo chroot /mnt
update-initramfs -u -v 
grub-install --recheck /dev/sda 
update-grub
reboot

```

y salió andando.

Espero que le sirva a alguien!

Salud!

---

### Post by Cristoforus28 on 2011-06-08
Como hago esto para Fedora( me paso lo mismo ) alguien me podra decir??/:D

Fedora 15 Lovelock:popcorn::KS

---

### Post by fmsismo on 2011-06-08
Lo mismo que hizo con ubuntu para fedora te sirve.  Podes usar cualquier disco para el rescate.  Yo por lo general uso finnix [http://www.finnix.org/](http://www.finnix.org/).

Saludos

---

### Post by aleixsr on 2012-05-06
> **granjero said:**
> Hola, ayer me pasó algo de lo más extraño. Tengo dos PC con Ubuntu 10.04 enfrentadas que tenían un kit teclado/mouse inalámbrico marca microsoft que se interferían mutuamente.
Cansado de escuchar quejas por ese tema compré un kit genius ps2 y saqué uno de los inalámbricos y puse el kit ps2 todo con la pc encendida. Configuro la distribución del teclado, cierro todos los programas y pongo reiniciar para asegurarme que cuando vuelva a encender la máquina tenga todo configurado correctamente. Para mi sorpresa luego del bip del mother y la pantalla con la el nombre del mother me encuentro con la siguiente leyenda.

```
kernel panic - not syncing : VFS : Unable to mount root fs on unknown - block (0,0) 
```

Después de un rato de sufrir y evaluar si iba a reinstalar o qué lo solucioné de la siguiente manera. Gracias m4v.

Bootié una live session de 10.04
Abrí una terminal
```
sudo fdisk -l
```
Ahí vi que la partición de sistema que bootea era /dev/sda5
```
sudo mount /dev/sda5 /mnt
```
luego
```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
```

luego 
```
$ sudo chroot /mnt
update-initramfs -u -v 
grub-install --recheck /dev/sda 
update-grub
reboot

```

y salió andando.

Espero que le sirva a alguien!

Salud!

Pues a mi me ha funcionado perfectamente, muchas gracias.

---

### Post by fixberal on 2013-04-07
Muchas Gracias, ya estaba a punto de reinstalar el ubuntu, por que no podia desbloquear, tenia el ubulion con los mejores programas en todas sus areas, estaba bien cargado, por que es un regalo para mi hijo, pero al tratar de configurar el teclado, por que es aleman, y va para suramerica, hay algunas teclas adicionales, ademas que le habia cambiado el teclado al portatil, tenia el unconveniente que con algunas teclas salian eran numeros, trate de darle la nueva configuracion, cuando se me bloqueo totalmente, pero GRACIAS a tus recomendaciones volvio a funcionar nuevamente, con respecto al problema de que en  algunas teclas salian numeros, le di a la tecla  que esta en la parte de arriba enseguida de F12....Num Rollen, bueno en algunos teclados esta en otro lado, con  eso se arreglo mi problemita.
Nuevamente muchas gracias, eres un Genio. Saludos.

---

### Post by Jaginus on 2013-09-11
Muchisimas gracias [**[COLOR=#000000]aleixsr[/COLOR]**]("http://ubuntuforums.org/member.php?u=118568"). Un año después de escribirlo, tu post me ha salvado la vida :-D

---


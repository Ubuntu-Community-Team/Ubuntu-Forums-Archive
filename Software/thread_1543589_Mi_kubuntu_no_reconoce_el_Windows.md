---
title: "Mi kubuntu no reconoce el Windows"
date: 2010-08-01
forum: Software
---

### Post by mininata on 2010-08-01
Hola:
Despues de instalar el kubuntu, no puedo iniciar el windows xp.
Antes tenia un disco duro donde en una particion estaba instalado el windows, y otras 4 reserve para el linux.
Despues, coloque otro disco nuevo, hice particion de arranque que la deje sin formatear, instale en una de las particiones el windows, en otras documentos.
Al instalar el kubuntu formatee la primera particion del disco nuevo que es el principal.
Pues, el kubuntu me reconocio el windows antiguo y el nuevo no. Pero desde el propio os veo las particiones y los datos, o sea que no esta borrado.
Intente modificar el archivo de configuracion de grub pero no dio resultado.

Por favor, si alguien puede ayudar o indicar donde puedo buscar la ayuda.

---

### Post by juanman on 2010-08-03
Abri un konsole (alt f2 -> konsole) y escribi:

```
sudo update-grub2
```

Esto deberia redectar los sistemas operativos que tenes instalados y crear un nuevo archivo de configuracion del grub...

Si no funciona, chiflá

---

### Post by mininata on 2010-08-03
Menos mal! Creí que este foro no tiene gente.

Lo que me dices no funciona. También intenté cambiar manualmente la entrada del grub.cfg poniendo la direccion del disco (que sería hd0,2) y tampoco hace nada.

Y ayer aparte se me quedó la pantalla en negro (pasó sin hacerle nada). Supongo que no arrancaba el escritorio. Y no pude arreglarlo de ninguna forma. Al final me instalé xubuntu. Va mas rápido pero el mismo problema: no reconoce el windows.

---

### Post by juanman on 2010-08-04
Bien, lo de editar manualmente el grub.cfg sirve como prueba, pero despues de una actualizacion o cuando se hace un update-grub2, los cambios se pierden...

Para q esto no pase, habria q agregar la entrada del windows q no reconoce en /etc/grub.d/40_custom

Pasanos la salida del comando: sudo fdisk -l
que va a mostrar la tabla de particiones de los 2 discos...

Cuando decis q no anda entrar a windows, tira algun error? O solo se queda la pantalla en negro? Probaste sacando el otro disco a ver q pasa?

---

### Post by mininata on 2010-08-04
Esto lo que me hace al regenerar nuevo grub:

```
nata@nata-desktop:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done
nata@nata-desktop:~$
```O sea, que ahora me encuentra dos linuxes: 22 y 21. No sé si eso sería por actualizar, pero el linux sigue siento uno.
Me encuentra el windows antiguo en el diso 2 partición 1.
No me encuentra el windows nuevo en el disco 1, partición 2.
(El arranque se hace desde el disco 1 partición 1).

Ya que ahora la partición 1 del disco 1 está como activa, teóricamente si quito el segundo disco, seguirá arrancando desde esta partición, donde esta el menú de arranque. Como poner la partición 2 (que es donde está el nuevo Windows) como activa no lo sé. Si quito el primer disco, no me resuelve el problema, ya que es donde está el windows que no arranca.

No me da ningún error, simplemente no aparece en el menú el windows que quiero arrancar, así que no puedo acceder a él. La pantalla en negro se me quedó en el kubuntu. Al arrancar la maquina no se cargaba lo que sea, solo veía el skype. Al reiniciar la máquina no se arreglaba. Intenté reinstalar o arreglar el kubuntu y seguía igual. Así que instalé el xubuntu, es muy diferente, me cuesta trabajo orientarme donde están las cosas pero por lo menos puedo acceder al ordenador y documentos. (Lo descargué y grabé arrancando desde el live cd de kubuntu).

La salida del comando de fdisk:
([FONT=monospace]/dev/sda5 es[/FONT] donde creo que está el windows que no arranca)


```
nata@nata-desktop:~$ sudo fdisk -l

Disco /dev/sda: 300.1 GB, 300069052416 bytes 
255 cabezas, 63 sectores/pista, 36481 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x73d3c109

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema 
/dev/sda1   *           1         261     2096451   83  Linux
/dev/sda2             262       36481   290937119+   f  W95 Ext'd (LBA)
/dev/sda5             262        5100    38869236    7  HPFS/NTFS
/dev/sda6            5101       15554    83971723+   b  W95 FAT32
/dev/sda7           15555       26008    83971723+   7  HPFS/NTFS
/dev/sda8           26009       36481    84124341    7  HPFS/NTFS

Disco /dev/sdb: 40.1 GB, 40060403712 bytes 
255 cabezas, 63 sectores/pista, 4870 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x10bd10bd

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema 
/dev/sdb1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sdb2            1531        4870    26828519+   f  W95 Ext'd (LBA)
/dev/sdb5            1531        2017     3906250   83  Linux
/dev/sdb6   *        2313        2702     3125000   83  Linux
/dev/sdb7            3061        4590    12289693+   b  W95 FAT32
/dev/sdb8            4591        4870     2249068+  82  Linux swap / Solaris
/dev/sdb9            2017        2312     2373632   83  Linux
/dev/sdb10           2702        3060     2882560   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco 
nata@nata-desktop:~$
```

---

### Post by mininata on 2010-08-05
He probado modificar el 40_custom. Al elegir esta entrada de menú arranca el windows antiguo en vez del nuevo. (O sea, que con las dos entradas arranca el mismo windows - el antiguo y no el que yo quiero). Igual no escribo bien la descripción para el menú.
Aquí pongo la parte del archivo de la entrada generada automaticamente para el windows antiguo y la que puse yo para el nuevo. Sólo cambié el nombre del disco. Igual hay que poner algo más.

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 583c8aeb3c8ac40a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 583c8aeb3c8ac40a
    drivemap -s (hd0,2) ${root}
    chainloader +1
}
### END /etc/grub.d/40_custom ###
```

---


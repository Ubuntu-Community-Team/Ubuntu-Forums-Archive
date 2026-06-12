---
title: "No lee Tarjetas SD en Ubuntu-Studio 13.10"
date: 2014-01-31
forum: Ubuntu Studio
---

### Post by rjaubert on 2014-01-31
Estimados amigos, tengo una PC con la siguiente versión:
[B]Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

[/B]
El problema que tengo es que no hay manera que al insertar mi tarjeta SD en el multi lector de tarjetas me lo lea, si lo hace en el puerto USB y en el MicroSD.
al dar la instrucción : lsusb me aparece lo siguiente:

Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 046d:0824 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rene@rene-desktop:~$ lsusb
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 046d:0824 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**dando la instrucción: sudo fdisk -l me arroja lo siguiente:**

Disco /dev/sdc: 1030 MB, 1030225920 bytes
4 cabezas, 3 sectores/pista, 167680 cilindros, 2012160 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *         227     2012159     1005966+   6  FAT16

he buscado e intentado una solución que reemplaza una línea de comando en el archivo: **/etc/default/grub** la linea de comando: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" y la reemplazo por: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"
pero no me funcionó

Cabe destacar que también me sugirieron insertar la tarjeta antes de cargar el sistema, pero igual no me la reconoció.

Una solución temporal que encontré y si me funciona solo si ejecuto el comando desde terminal, y esto cada vez que necesito leer la tarjeta, ya que si la saco y se desmonta, al ingresarla nuevamente no me la reconoce ni monta. El comando es el siguiente: **sudo rmmod usb_storage ; sudo modprobe usb_storage**
Como les repito, me funciona pero lo que busco es que al insertar la tarjeta la reconozca y monte el volumen.

Por favor si alguien tiene alguna solución para esto se lo agradecería.

Saludos cordiales, ):P

---


---
title: "Borrar Grub del mbr e instalarlo en otro HD"
date: 2009-07-12
forum: Software
---

### Post by Cajuma on 2009-07-12
[LEFT]Hola a todos:
Tengo dos sata en mi pc en el 1ro dos particiones C y D y en el 2do Kubuntu 9.04 y JJ 
al instalar Kubuntu en la primera particion del 2do sata, no desconecte el sata 1, y se instalo el Grub en el mbr de xp, el tema es que ese disco lo quiero sacar para ponerlo
en otra maquina, pero si lo hago no va a arrancar ninguno , estuve averiguando y
la opcion de  fixmbr fix boot, con un disco de xp no es posible, ya que este es un desatendido y no trae esa opcion por defecto (tengo el dvd).
Por otro lado me baje y grabe el Super grub, con eso tengo solucionado el arranque del
2do sata (kubuntu y JJ), pero la opcion de reparacion del mbr es la misma, alguien me puede orientar ?
Detallo las particiones:

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xfb12fb12

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5151    41375376    7  HPFS/NTFS
/dev/sda2            5152       19457   114912945    f  W95 Ext'd (LBA)
/dev/sda5            5152       19457   114912913+   7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2717c543

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       10260    82413418+  83  Linux
/dev/sdb2           10261       19457    73874902+   f  W95 Ext'd (LBA)
/dev/sdb5           10261       19076    70814488+  83  Linux
/dev/sdb6           19077       19457     3060351   82  Linux swap / Solaris

Desde ya muchas gracias, por su tiempo.
Cajuma.
[/LEFT]

---

### Post by staar on 2009-07-12
según recuerdo el mismo SGD puede instalar un bootloader para Ventanas en la MBR, basta con seleccionar esa opción y tener cuidado de que lo haga en el disco correcto...

saludos

---

### Post by Cajuma on 2009-07-12
Gracias Staar, se que el SGD, lo hace pero en el xp original, este es un desatendido y no es igual. de todas maneras, gracias por tu respuesta.
Saludos.

---

### Post by staar on 2009-07-13
y cual es la diferencia? aunque sea un desatendido, no creo que ninguno esté tan modificado como para variar la secuencia de inicio...

SGD no requiere del disco original de Ventanas, lo que hace es instalar syslinux en la MBR y este carga por chainloading lo que haya en la primera partición del primer disco, en este caso, tu XP...

no es exactamente lo mismo, pero en la práctica funciona igual que si tuvieras el ntldr...

saludos

---

### Post by Cajuma on 2009-07-13
Gracias Staar, disculpame que no te conteste antes, pero se me corto
la luz y no tengo ups.
El tema es que  quiero sacar el xp y ponerlo en otra maquina, en la mia
queda el JJ, que el arranque se lo arreglo con SGD.
La cosa es si el xp arrancaria solo en otra maquina....
Saludos.

---

### Post by staar on 2009-07-13
sip, si instalas syslinux en la MBR de ese disco, sip...

saludos

---

### Post by Cajuma on 2009-07-13
Ok gracias por tu respuesta, pruebo y te cuento.
:popcorn:Saludos !!!

---


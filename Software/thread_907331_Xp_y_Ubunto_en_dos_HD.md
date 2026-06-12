---
title: "Xp y Ubunto en dos HD"
date: 2008-09-01
forum: Software
---

### Post by arysar on 2008-09-01
Hola,

Ya tenía instalado windows XP e instalé la ultima version de Ubuntu en un HD nuevo que puse en la maquina. Se instaló todo bien pero al bootear solo lo hace en windows XP, hay alguna manera de hacer un DUAL Boot sin volver a instalar?

Gracias

---

### Post by Lobo_Gris on 2008-09-01
Hola, no se bien como lo instalaste, mas haya de que decis que en dos HD, pero ¿Y si seteas como disco de arranque el HD de Ubuntu en el BIOS? Salvo que el Ubuntu despues no te reconozca el windows, que se hayan instalado completamente independientes, creo que podria ser una solucion.

Saludos Gonzalo.

---

### Post by pol666 on 2008-09-01
Mete el live cd de ubuntu, anda al editor de particiones y localiza el disco donde esta ubuntu, hace click derecho y mete en donde dice "manage flags" y ahi setealo en "boot".

---

### Post by sajnox on 2008-09-01
> **pol666 said:**
> Mete el live cd de ubuntu, anda al editor de particiones y localiza el disco donde esta ubuntu, hace click derecho y mete en donde dice "manage flags" y ahi setealo en "boot".

Disculpame Pol pero me parece que no solucionas nada con eso, por que necesita que el bios le de prioridad en el arranque el disco que tiene el Ubuntu

Entra al bios y cambiale el orden de arranque en las opciones de booteo

---

### Post by faktorqm on 2008-09-02
> **sajnox said:**
> Entra al bios y cambiale el orden de arranque en las opciones de booteo

eso es lo que hay que hacer, seguro que como instalaste ubuntu en otro hd te puso el grub (administrador de arranque) en ese disco, entonces cuando lo cambies desde la bios te va a aparecer, para iniciar win desde el primer disco, o ubuntu desde el segundo. 
Si lo cambias y no te aparece, postea por que capaz se te instalo mal el grub, salu2!

---

### Post by arysar on 2008-09-02
Gracias, hoy voy a probar de cambiar el orden de boteeo en el bios y veo si me aparece el windows.

Lo que quería hacer también y no pude era importar las configuraciones de usuario, se ve que eso anda solamente cuando instalas en el mismo HD.

---

### Post by faktorqm on 2008-09-02
Te digo la verdad, nunca lo hice. Instalacion nueva vida nueva para mi xD

---

### Post by cdesseno on 2008-09-02
Lo que podés hacer sino es ejecutar el Live CD de Ubuntu, bajarte alguna app GUI como "Administrador de arranque" (está en los repositorios oficiales) y configurar para que bootee el GRUB desde Ubuntu. Lo raro es que si instalaste Ubuntu más tarde no haya aparecido el GRUB, al revés si pasa porque XP te lo pisa.

---

### Post by sajnox on 2008-09-02
No lo mareemos mas al amigo, aparentemente el problema es que la maquina cuando inicia va a buscar el primer disco, el cual no tuvo modificacion alguna ya que windows esta en el segundo, entonces la maquina arranca va al primer disco y encuentra un sistema operativo, el cual bootea. Esto viene seteado del bios y ninguno de los programas que mencionaron lo modifica (no se si hay programas para modificar el bios)

Si modifica el orden de booteo al segundo disco va a encontrar el grub y tambien la ubicacion de windows. Si en el peor de los casos no lo encuentra modificarlo es realmente simple

Saludos

---

### Post by arysar on 2008-09-02
Cambié el orden de booteo al segundo HD y me da invalid partition table...

Con live CD trate de instalar el grub en el hd de windows pero no pude, igual creo que no era una buena idea.

---

### Post by sajnox on 2008-09-03
Entra con el Live cd y en una terminal escribi

```
sudo fdisk -l
```

Postea lo que te devuelve

Saludos

---

### Post by arysar on 2008-09-03
Bueno, acá está el resultado:


ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3b28f0b1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        8581    68926851    7  HPFS/NTFS
/dev/sda2            8582       19457    87361470    c  W95 FAT32 (LBA)

Disco /dev/sdb: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0d390d39

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extendida
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by sajnox on 2008-09-03
Ok, por lo que pude Googlear del error que tenes puede ser que este corrompida la MBR del disco 2, para eso nuevamente arrancas con un Live CD y haces lo siguiente:

1) Instalar lilo

```
sudo apt-get install lilo
```

2) Reparar el MBR

```
sudo lilo -M /dev/sdb
```

Salis y reinicias dando como opcion de booteo el disco esclavo

Contanos si funciona

---

### Post by arysar on 2008-09-04
Mmmmm por que lilo y no grub??? dicen que el grub es más mejor...

encontré que para grub deberia usar lo siguiente:

sudo grub
find /boot/grub/stage1

This will give and output of (hdax,x)In the next steps replace the x's with the appropraite numbers.

root (hdx,x)

setup (hdx)

quit

---

### Post by arysar on 2008-09-08
El lilo se instaló pero no me anduvo, el grub tampoco lo pude arreglar, así que instalé de nuevo, especificando esta vez donde quería que me instalara el grub. Ahora bootea, aparece el menú con distintas opciones incluida windows XP, pero cualquiera que elija me sale:

Error 22: No such partition

Entré a editar el booteo de linux y tenía root(hd1,5), lo cual estaba mal, debía ser root(hd1,0) la primera particion del segundo disco. Lo cambie y me da

Error 17: cannot mount selected partition. 

Ya busqué en la web y voy a probar con lo que dice en:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Gracias a todos.

---

### Post by Afkael on 2008-09-08
hola, te cuento que tengo también 2 HDD, uno de 200GB con WinXP que lo instalé desconectando el otro disco, y otro de 80GB que, una vez instalado el WinXP, lo puse para que booteada desde él y DESPUES instalé el Kubuntu.
Osea:
1) Instalé WinXP en un disco de 200GB
2) Cambié el orden de booteo para que lo hiciera primero desde el de 80GB
3) Instalé Kubuntu por defecto

Así todo lo instalado después de WinXP se instaló en el disco de 80GB (incluido Grub)... Solamente asi me funcionó, antes me daba Error 12 o algo así...
Al terminar las opciones de instalación (y antes de empezar el proceso en si - instalar - ) hay una opción que dice avanzadas que creo que desde alli se puede solucionar y elegir que el HDD de Win como para bootear, pero no supe cómo hacerlo y además queria dejar el disco de WinXP intacto por lo que si cambio el orden de booteo nuevamente, botee win sin pasar por grub. Saludos

---

### Post by arysar on 2008-09-16
Resumen final:
Tenía windows xp instalado en un HD puse otro HD como secundario e instalé ubuntu. Cambié el orden de boteeo y aunque los dispositivos estaban bien puestos en en grub, no arrancaba ni windows ni ubuntu.

Lo que me funcionó fue poner el disco en el que había instalado ubuntu como primario el de windows como secundario , después modifiqué el menu.lst básicamente como dice acá:
[http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)
y anduvo!

Gracias

---


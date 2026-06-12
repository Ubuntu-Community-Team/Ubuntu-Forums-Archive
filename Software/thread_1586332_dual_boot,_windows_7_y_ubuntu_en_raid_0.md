---
title: "dual boot, windows 7 y ubuntu en raid 0"
date: 2010-10-01
forum: Software
---

### Post by sebadito on 2010-10-01
intentando instalar ubuntu 10.04 x64

tengo 2 discos sata2 en raid  0 por software (creo, no se si se llama asi, lo hice desde el bios  setup) tengo windows 7 en una paraticon, en otra particon tengo datos. y  eh creado las particiones correspondientes para instalar linux ubuntu,  cree particon logica para / , formato ext4.otra particion para swap de 5  gb temgo 4 de ram. otra particion /home, ext4.
todas las particiones estan en el raid 0

comienzo inatalacion sin problemas hasta q al final intenta instalar el grub, y me sale el mensaje:

no se puede instalar GRUB en dev/sda
la ejecucion de grub-install /dev/sda failed

esto es un error fatal

pongo  aceptar, y eligo q instale grub en todas las demas particiones q  aparecen en el listado, pero en todas me sale el mismo error, y pongo  continuar sin instalar, y no inicia mas ubuntu, directamente arranca win  7


aca hice un fdisk -l iniciando con el cd live de ubuntu

ubuntu@ubuntu:~$ sudo fdisk -l

Atención: el indicador 0x0000 inválido de la tabla de particiones 5 se corregirá mediante w(rite)

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xf6bd111b

Dispositivo Inicio Comienzo Fin Bloques Id Sistema

/dev/sda1 * 1 13 102400 7 HPFS/NTFS

La partición 1 no termina en un límite de cilindro.

/dev/sda2 13 13062 104812544 7 HPFS/NTFS

/dev/sda3 13062 121577 871645057 f W95 Ext'd (LBA)

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x81738173

Dispositivo Inicio Comienzo Fin Bloques Id Sistema

/dev/sdb1 1 60802 488385528+ 42 SFS

Disco

/dev/sdc: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x2c5ac072

Dispositivo Inicio Comienzo Fin Bloques Id Sistema

/dev/sdc1 1 60802 488383488 7 HPFS/NTFS

ubuntu@ubuntu:~$

parece  que me reconece los discos por separado y no el raid. aunque cuando  instale y particione me reconocio el disco raid como 1 solo de 1000 gb y  luego instale normalmente

desde ya muchusimas gracias!!!!3

mother asus m4a78
memoria 4 gb dd2 800
video ati 4850 1 gb
phenom 2 x4 810
2 discos en raid 0 wd 500 gb sata 2 32 mb caviar black
1 disco wd 500 gb sata 2 32 mb caviar black

---

### Post by guillermolisi on 2010-10-01
Es que salvo que esa motherboard tenga una controladora de arreglo de discos inteligente (cosa que encarece mucho el precio de la placa) el RAID por BIOS no sirve y tenes que terminar utilizandolo por software usando los paquetes DMRAID, MDADM, RAIDUTILS, etc. (creacion, mantenimiento y administracion).

Ni siquiera las que viene con un modulo para usar en tiempo de instalacion, conocidas por simular un RAID (fake RAID) sirven.

Esa es una razon por la cual no podes instalar satisfactoriamente Grub.

Edit: Grub no se instala en una particion, se instala en una unidad de disco.

---

### Post by sebadito on 2010-10-02
ok, y si instalo ubuntu en el otro disco fuera del raid? eh probado y me da el mismo error del gub. no "encuentra" el raid.
y si compro una placa controladora raid, seria por hardware. En ese caso el grub se instalaria sin problemas no?
vi unas placas (controladora raid) con chip sil3512 que tienen 2 slots sata2, bastante economicas, ahi pondria los 2 discos para armar el raid, y el disco restante lo conectaria directamente al mother, en este caso habria problemas para instalar windows 7 y ubuntu en el raid ? y el 3 disco seria reconocido?

perdon mi ignorancia y muchisimas gracias por ayudarme

edit: la placa controladora mensionada es sata1, tendria q buscar una sata2 verdad? para no estar limitada la velocidad de tranferencia?

---

### Post by guillermolisi on 2010-10-02
Para que te funcione bien la instalacion de Grub teniendo Ubuntu instalado en un solo disco, sin RAID, tenes que cambiar la configuracion del BIOS para que la controladora se muestre como SATA comun. Luego no deberias tener problemas al grabar Grub en hd0 (el disco donde este instalado Ubuntu).

Si vas a comprar una controladora, cerciorate bien que sea inteligente, es decir que el arreglo de discos lo administre via hardware, y que su driver funcione bien bajo Ubuntu (para la version que estes usando). Es decir, que no sea otra placa de fake RAID.

No deberias tener problemas para tener Win7 y Ubuntu conviviendo en el mismo arreglo de discos. Instala primero Win y despues Ubuntu.

El tercer disco lo podrias configurar como spare disk (de repuesto para el arreglo con lo cual si se te arruina uno de los otros dos la controladora automaticamente utiliza este en forma transparente para continuar funcionando con el arreglo) o como unidad independiente (al estar siendo controlada por la motherboard).

Sata1 tiene menor ancho de banda que Sata2 => no aprovechas a fondo la velocidad de transferencia que poseen los discos Sata2 usando controladoras Sata1.

---

### Post by sebadito on 2010-10-03
bueno muchisimas gracias por ayudarme, voy a ver si compro la placa controladora, quede caliente con ubuntu, tengo ganas de probarlo, pero no quiero desarmar el raid, compre los 2 discos justamente para armar raid 0. pero bue, veo lo que hago.

---


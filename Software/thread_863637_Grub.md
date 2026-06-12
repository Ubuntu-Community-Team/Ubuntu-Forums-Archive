---
title: "Grub"
date: 2008-07-18
forum: Software
---

### Post by ramiro_md on 2008-07-18
Hola muchachos, ando con un problemilla de aquellos, resulta que instale el OpenSuse 11..y en el grub no me aparecia mi ubuntu 7.10 =( al toquetear el menu.lst desde ubuntu con el livecd se palmo todo ! no puedo entrar a suse ni a ubuntu solo a win =S...(para mi fue una mala jugada de este ultimo ¬¬ jejeje) y cuando quize rescatar el grub con el super grub disk supuestamente lo soluciona..pero al querer entrar a suse me tira error 15 :( y para ubuntu ni opcion me da =S...espeor q me den una mano xq estoy al horno !!.Un saludo

---

### Post by Mauro22 on 2008-07-18
1) Configurar grub. Para ello hacemos:

sudo fdisk -l y nos devuelve algo asi:

```

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
**/dev/sda1               1        3647    29294496   83  Linux**
/dev/sda2            3648       11428    62500882+  83  Linux
/dev/sda3           11429       11780     2827440    f  W95 Ext'd (LBA)
/dev/sda4   *       11781       19457    61665502+   b  W95 FAT32
/dev/sda5           11429       11780     2827408+  82  Linux swap / Solaris

```En mi caso me corresponde sda1, ahi dice que es la particion linux y por el tamaño yo se que es el sistema y no la /home.

Entonces, sabiendo eso:
sudo grub-install /dev/sda1 (en mi caso)

O sino asi:

```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # Te va a salir algo asi
grub> root (hdx,y)
grub> setup (hdx)

```

:lolflag:

---

### Post by ramiro_md on 2008-07-18
Mauro gracias por responder. Pero al hacer el grub-install me dice

ubuntu@ubuntu:~$ sudo grub-install /dev/sda4
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

Y con al otra opcion (la cual utilize con anterioridad para agrgar a ubuntu al grub de suse y se descajeto todo) me sale lo siguiente

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,3)
grub> root (hd0,3)    
root (hd0,3)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,3)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

Lo cual me hace suponer que etsa todo OK pero no :S sigue si andar el grub para los sistemas linux.

---

### Post by Mauro22 on 2008-07-18
Cuando hiciste grub install en sda4, lo hiciste desde un livecd no?

Estaba montado ese disco?



Que te hace la PC? Te va directamente a winxp?

---

### Post by ramiro_md on 2008-07-18
Si lo hice desde el livecd, las particiones estan montadas xq las veo desde "equipo".
Cuando inicia la pc se carga el grub de suse con la opcion OpenSuse 11 y Windows. Si elijo suse salta error 15, si eligo windows arranca la compu en windowws lo mas bien.

---

### Post by smo0th on 2008-07-18
con el live cd activa el community maintained software(universe) en synaptic>>settings>>repositories, en la terminal dale ```
sudo agt-get update
sudo apt-get install testdisk
testdisk

```
entras y te vas hasta donde dice analyse, le das proceed y te escanea el disco, ahi dice que particion esta marcada como bootable, primaria, secundaria, etc. checa que tu particion de ubuntu sea booteable y reinicia, espero esto ayude de algo

---

### Post by ramiro_md on 2008-07-18
Interesante el programa, peor no me sirve, es mas me ha asustado el maldito ¬¬ esto es lo que me tira

Disk /dev/hdb - 730 MB / 696 MiB - CHS 23 255 63 (RO)
     Partition               Start        End    Size in sectors



Structure: Ok.


Keys A: add partition, L: load backup, Enter: to continue


(????????) que ha pasado ?? que no lee mis particiones ???  :confused:

---

### Post by Mauro22 on 2008-07-19
Probaste el comando update-grub?

---

### Post by Hernán-Amaya on 2008-07-19
Hola Ramiro. 
Fijate en este post, que habla sobre como recuperar el grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

espero que te sirva

---

### Post by ramiro_md on 2008-07-19
GRacias por el link hernan pero nada..al montr me sale lo siguiente

ubuntu@ubuntu:/$ sudo mount -t ext2 /dev/sda4 /mnt/root
mount: /dev/sda4 ya está montado o /mnt/root está ocupado
mount: según mtab, /dev/sda4 está montado en /media/disk
ubuntu@ubuntu:/$ sudo mount -t ext2 /dev/sda6 /mnt/root
mount: /dev/sda6 ya está montado o /mnt/root está ocupado
mount: según mtab, /dev/sda6 está montado en /media/disk-1

No se pued edesinstalar el grub y voolverlo a instalar y asi que agarre configuraciones nuevas?

---

### Post by ramiro_md on 2008-07-19
**ESte es el menu.list de ubuntu**

# Modified by YaST2. Last modification on jue jul 17 14:18:57 ART 2008
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,3)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0
    root (hd0,3)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_WDC_WD1600AAJS-_WD-WMAP93209212-part4 resume=/dev/sda3 splash=silent showopts vga=0x317
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,3)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0
    root (hd0,3)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_WDC_WD1600AAJS-_WD-WMAP93209212-part4 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x317
    initrd /boot/initrd

**Este el de suse**

Modified by YaST2. Last modification on Fri Jul 18 14:56:28 ART 2008
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.9-0.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.25.9-0.2-default root=/dev/disk/by-id/scsi-SATA_WDC_WD1600AAJS-_WD-WMAP93209212-part6 resume=/dev/sda3 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.25.9-0.2-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.9-0.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.25.9-0.2-default root=/dev/disk/by-id/scsi-SATA_WDC_WD1600AAJS-_WD-WMAP93209212-part6 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x317
    initrd /boot/initrd-2.6.25.9-0.2-default

###Don't change this comment - YaST2 identifier: Original name:  openSUSE 11.0 (/dev/sda4)###
title openSUSE 11.0 (/dev/sda4)
    root (hd0,3)
    configfile /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,5)
    chainloader (hd0,0)+1

POr si sirve de algo, aqui van **mis particiones**

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       17759   121676310    f  W95 Ext'd (LBA)
/dev/sda3           17760       18121     2907765   82  Linux swap / Solaris
/dev/sda4           18122       19457    10731420   83  Linux
/dev/sda5            2612       16481   111410743+   7  HPFS/NTFS
/dev/sda6           16482       17759    10265503+  83  Linux

---

### Post by Mauro22 on 2008-07-20
Te encontre esto:

[http://sourceforge.net/projects/grub4dos](http://sourceforge.net/projects/grub4dos)


Es un instalador de grub desde windows :s


jeje, a probarlo!

---

### Post by ramiro_md on 2008-07-22
Ohh..que lastima que no me pegue una vuelta por el foro antes =S...desinstale suse y lo volvi a instalar total no perdia nada importante, resulta que el grub (de suse) anda lo mas bien ahora, pero me gustaria saber como agrego una entrada para ubuntu ! antes de volver a hacer giladas =S..un saludo..espero noticias =)

---


---
title: "Instalacion Ubuntu 10.4 crea Problema arranque Windows 7 con GRUB"
date: 2010-04-30
forum: Software
---

### Post by Squal472 on 2010-04-30
Buenas... Tengo un problema.

Tenia una instalacion unica de Windows 7, al instalar Ubuntu 10.4 e intentar iniciar Windows 7 desde el GRUB no me carga, sale una pantalla negra y me lleva nuevamente al GRUB, solo me carga ubuntu.

Tengo 3 discos duros.

- Datos Nuevo
- Sistema Nuevo
- Datos viejos (En este tengo 2 particiones, una con datos y otra que era C estaba formateada, aca tambien esta el windows 7 loader y el GRUB)
[B]
update-grub2[/B]
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb3
done
**cat /etc/mtab**
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb5 /home reiserfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/squal/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=squal 0 0
/dev/sdb2 /media/Ubuntu fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sdb3 /media/Datos fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sdc1 /media/Sistema\040Nuevo fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda1 /media/Datos\040Nuevo fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

**cat /etc/fstab**

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2bd56833-4980-45c5-8a4e-bab1f38c2a00 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=23f97763-3f17-49f1-8bcc-81ae25b1d4ed /home           reiserfs defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=bcfb7cf3-d440-4301-bf39-1f629b7cbc9b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by leonardomdq on 2010-05-01
Hola Squal472 , pasate por este thread que esta la solucion a tu problema, es un bug en el grub de Lucid.  [http://ubuntuforums.org/showthread.php?t=1465303](http://ubuntuforums.org/showthread.php?t=1465303)

Saludos

---

### Post by jacsami on 2010-05-07
Buenas. Acabo de instalar el 10.04 y he tenido un problema parecido pero la solución propuesta no me funciona. No sé si es el mismo problema. Doy detalles. Tengo instalados los dos sistemas pero arranca con el grub de Ubuntu. Al actualizarlo a Ubuntu 10.04 ya me dio un aviso de que una partición daba un fallo advirtiendo de que podía no arrancar correctamente. Lo ignoré y continué fiándome de Ubuntu. El caso es que ahora me aparece en el menu del grub para arrancar con ubuntu y con windows 7 pero cuando selecciono windows 7 se reinicia y vuelve al menú del grub, de forma que no puedo entrar en windows 7. He probado casi de todo, lo primero la opción que aquí proponéis, y no funciona, reinstalar grub... No es problema de que haya eliminado la partición de windows 7, pues está ahí físicamente, pero no lo arranca. Incluso he probado con un disco de recuperación de windows 7, y me dice que no hay ningún problema con el arranque de windows. Pero al reiniciar sigue sin entrar en windows. Resumiendo creo que es un problema con el grub que no consigo solucionar. Me gusta ubuntu, pero hay cosas importantes que sólo puedo hacer con windows, así que os agradecería que me echáseis una mano pronto. No domino demasiado ubuntu, así que no seais muy técnicos porfa. Os lo agradezco de antemano.

---

### Post by pserra on 2010-05-15
a mi me pasa lo mismo con el vista, ahora provaré de instalar el LILO.

---

### Post by biale on 2010-05-15
Justamente había pensado iniciar un thread con este tema, pero visto de una manera mas genérica.

Yendo a lo específico, tengo entendido que WVista y W7 pueden tener problemas con Grub y a la larga con el dual boot. O sea: W$ con grub y no Grub con W$. Pero no se si este es el caso.

Si tuviera que salir desesperadamente del paso y sin mucha técnica, trataría de reponer en el disco el arranque de windows y hacer desaparecer el grub. 

Y en forma provisoria usaría alguna forma del "Super Grub disk" para arrancar a Ubuntu. Como algo mas complicado también se puede instalar el grub en un Pen drive.

Un saludo a todos...

---

### Post by biale on 2010-05-15
Leí muy rápido: si hay tres discos es probable que alguno de los enlaces esté equivocado. 

De todas maneras lo anterior vale y se puede incluso tener un arrancador distinto por disco y seleccionar el disco/ arrancador por opción de bios.

---

### Post by guillermolisi on 2010-05-15
Para saber que esta pasando creo que siempre amerita ver la salida de fdisk y como esta generado el archivo /boot/grub/grub.cfg y/o /etc/grub.d/30_os-prober (eventualmente y por las dudas /etc/grub.d/40_custom).

Creo que es informacion basica como para entender el contexto de cada situacion.

---

### Post by lucasgz on 2010-05-17
buenas perdon que me cuele en tu post pero tengo el mismo problema, solo que al iniciar Win Xp se queda eternamente en pantalla negra, yo no se demasiado pero creo que el grub me genera mal la entrada del window o algo asi.

sudo fdisk -l
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x8c6e8c6e

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        9728    57167302+   f  W95 Ext'd (LBA)
/dev/sda5            2612        5222    20972826    7  HPFS/NTFS
/dev/sda6            5223        7833    20972826    7  HPFS/NTFS  (ACA TENGO EL SISTEMA WIN XP)
/dev/sda7            7834        9728    15221556    7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000867f0

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        1245    10000431   83  Linux
/dev/sdb2            1246       19457   146287859+   5  Extendida
/dev/sdb5            1246        1369      995998+  82  Linux swap / Solaris
/dev/sdb6            1370       19457   145291828+  83  Linux





grub.cfg
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 06a85ba1a85b8dd5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

pd: solucionado reinstalando todo xd
 [http://www.linuxquestions.org/questions/linux-software-2/windows-xp-blank-screen-on-boot-after-installing-fedora-core-9-a-644041/](http://www.linuxquestions.org/questions/linux-software-2/windows-xp-blank-screen-on-boot-after-installing-fedora-core-9-a-644041/)

[http://ubuntuforums.org/showthread.php?t=1306547](http://ubuntuforums.org/showthread.php?t=1306547)

---

### Post by romeluko on 2010-06-10
Yo tengo el problema anteriormente mencionado, Una vez instalado Ubuntu 10.04 y Windows 7 (OJO que me pasaba lo mismo con Ubuntu 9.10 y Windows Vista), al querer entrar a Windows 7 a veces entraba y la mayoria de veces no paraba de reiniciarse la maquina.

Ahora bien, probe algo que me funciono pero solo en Windows Vista - Ubuntu 9.10, desactive el adaptador wireless, y no mas se reiniciaba la maquina.

Es molestoso estar desactivando el wireless y volviendolo a activar, alguien encontro otra solucion??

Saludos.

---


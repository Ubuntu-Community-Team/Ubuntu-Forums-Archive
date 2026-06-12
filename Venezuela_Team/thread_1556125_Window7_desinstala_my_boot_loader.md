---
title: "Window7 desinstala my boot loader"
date: 2010-08-19
forum: Venezuela Team
---

### Post by galanh on 2010-08-19
Hola

El problema es el siguiente:
Window7 desinstala mi boot loader

My Ubuntu 10.04.1 corre perfecto.
Puedo apagar o re-arracar sin problemas.
Hasta puedo arracar el Window7.

Pero cuando salgo de Window7 y trato de bootear la maquina
obtengo este mensage:
 
 no module found
Aborted. Press any key to exit
Intel UNDI, PXE-2.1 (build 083)
….................................................  .......
PXE-M0F-Exiting PXE ROM
Operating System not found

Lo unico que puedo hacer es usar de nuevo el CD 10.04.1 de instalacion.
Alguien me podria dar una mano porque no salgo de este punto?

Corri el siguiente script que muestra donde estan instalado el boot.
En el foro en Ingles nadie contesta.

```

Boot Info Script 0.55    dated February 15th, 2010                     
  
 ============================= Boot Info Summary: ============================== 
  
  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  
     partition #5 for /boot/grub. 
  
 sda1: __________________________________________________  _______________________ 
  
     File system:       vfat 
     Boot sector type:  Dell Utility: Fat16 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:   
     Boot files/dirs:   /COMMAND.COM 
  
 sda2: __________________________________________________  _______________________ 
  
     File system:       ntfs 
     Boot sector type:  Grub 2 
     Boot sector info:  Grub 2 is installed in the boot sector of sda2 and  
                        looks at sector 948745976 of the same hard drive for  
                        core.img, but core.img can not be found at this  
                        location. No errors found in the Boot Parameter Block. 
     Operating System:   
     Boot files/dirs:   /bootmgr /Boot/BCD 
  
 sda3: __________________________________________________  _______________________ 
  
     File system:       ntfs 
     Boot sector type:  Windows Vista/7 
     Boot sector info:  No errors found in the Boot Parameter Block. 
     Operating System:  Windows 7 
     Boot files/dirs:    
  
 sda4: __________________________________________________  _______________________ 
  
     File system:       Extended Partition 
     Boot sector type:  - 
     Boot sector info:   
  
 sda5: __________________________________________________  _______________________ 
  
     File system:       ext4 
     Boot sector type:  - 
     Boot sector info:   
     Operating System:  Ubuntu 10.04.1 LTS 
     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
  
 sda6: __________________________________________________  _______________________ 
  
     File system:       swap 
     Boot sector type:  - 
     Boot sector info:   
  
 =========================== Drive/Partition Info: ============================= 
  
 Drive: sda ___________________ __________________________________________________  ___ 
  
 Disk /dev/sda: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
  
 Partition  Boot         Start           End          Size  Id System 
  
 /dev/sda1                  63        80,324        80,262  de Dell Utility 
 /dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS 
 /dev/sda3          30,800,325   529,014,566   498,214,242   7 HPFS/NTFS 
 /dev/sda4         529,014,782   976,773,119   447,758,338   5 Extended 
 /dev/sda5         529,014,784   958,537,727   429,522,944  83 Linux 
 /dev/sda6         958,539,776   976,773,119    18,233,344  82 Linux swap / Solaris 
  
  
 blkid -c /dev/null: __________________________________________________  __________
                                                                                               __________________


```

---

### Post by RafaelG on 2010-08-20
> **galanh said:**
> 
Window7 desinstala mi boot loader
[/CODE]

Estimado,

Que instalaste primero el Ubuntu o el Windows? Por que si instalaste primero ubuntu y despues Windows entonces te pasara siempre lo mismo por ese motivo siempre es recomendable instalar Windows primero y despues instalar ubuntu desde el bio para que pueda tener el booteo correspondiente de ubuntu con el Grub por que windows abosorve el grub si lo instalas despues de ubuntu.

Saludos!

---

### Post by galanh on 2010-08-22
Hola Rafael
La laptop es una Dell Studio (i7) y vino con Window7.
 

 Situación de la semana pasada es la siguiente:
Al correr el disco de instalación de Ubuntu 10.04 
acepte la partición por defecto que se propuso, completé  
 la instalación. Pude entrar en Ububtu y luego en Window  
 pero al salir de Window el mensaje era:
 Operating System not found
 

 La situación hoy es la siguiente:
 Después de muchas vueltas que no te puedo  
 contar para no enredar mas la cosa,  
 la laptop bootea en Window pero el menu Grub2 no aparece.
 Las 6 particiones están en el disco, porque puedo verlas entrando  
 con el disco de instalación del Ubuntu y haciendo el comando:
 ```
sudo fdisk -l
```
 

 Mi ultima idea es la siguiente:
 Puedo tratar de instalar de nuevo el Ubunto como ya lo he hecho  
 varias veces. Borrando las dos particiones particiones de Linux y Linux-swap
  y volviendolas a crear. Pero esta vez voy a borrar definitivamente la  
 particion Dell Utility que parece que no sirve para nada y esta ocupando  
 el primer lugar.
 En el primer re-arranque en el que si aparece el menú de Grub2 me voy para  
 Window7 para que este automaticamente se de cuenta de que el disco ha cambiado  
 y se adapte a la nueva organización de particiones.
 

 Tengo otra laptop Lenovo-Cantv con la que trabajo y tiene solo Lucy Lynx.
 Experimento con la laptop Dell nueva, pero el Window lo necesito  
 para otras aplicaciones que el Ubuntu no realiza y cada desastre que  
 hago me cuesta horas para recuperarlo, por eso no me he lazado hacerlo
pero ganas no me faltan.:D

---

### Post by FeRe on 2010-10-25
Hola, Yo tengo una Alienware Mx15 (Desde hace 2 días), pasa que viene con 3 particiones, una fat16 donde esta el boot, una de OS Recovery y el Windows7. Usando la herramienta del LiveCd de Ubuntu, hice espacio e instale y todo bonito, hasta que entre a Windows7 y reinicié y apareció esto:

no module name found
Aborted. Press any key to exit.
Intel(R) Boot Agent GE v1.3.35
Copyright (C) 1997-2009, Intel Corporation.

PXE-E61 : Media test failure, check cable
PXE-M0F : Exiting Intel Boot Agent.
Operating System not found

Nunca quise formatear todo y en los foros de Ubuntu en ingles decían que, borrando el Dell DataSafe se arreglaba, no se si eso funcione, ya que, el problema es la partición fat16 donde hay archivos de Dell o eso me parece, bueno yo en mi Alienware no tengo Dell datasafe (Y la tengo hace 2 días) solo tengo el Alienware Respawn, bueno borre ese, pero, igual me seguia dando el problema.

He aquí la solución: [http://www.ubuntu-es.org/node/136958](http://www.ubuntu-es.org/node/136958) .... El ultimo post es el que me funciono.

Lo que hice fue restaurar el Grub2 usando el LiveCd [http://new.taringa.net/posts/linux/5684737/Configurar-Grub-2-para-Window](http://new.taringa.net/posts/linux/5684737/Configurar-Grub-2-para-Window)...

Lo que de verdad me soluciono el problema fue instalar un programa llamado Burg en ubuntu que modifica el aspecto visual del Grub2, y ahora entro a Windows 7 y reinicio y todo normal, Burg me salvo la vida.

Disculpen si el post es muy largo ... pero después de lo que pase creo que todo usuario de dell debería leerlo

---


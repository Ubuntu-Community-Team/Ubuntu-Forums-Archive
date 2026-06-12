---
title: "[SOLVED] Problemas con k3B"
date: 2008-05-27
forum: Software
---

### Post by Vero1 on 2008-05-27
Hola,

Nuevamente aquí con un problema.

Resulta que quiero quemar en un CD Hardy Heron. He probado Brasero pero no me lo graba y estoy probando k3B pero me contesta que hay un error porque no tiene permiso para ingresar en el device y no sé qué tengo que hacer.
No entiendo qué clase de permiso necesita porque en la configuración no encuentro nada al respecto.

Agradezco desde ya si me pueden dar una mano con este problema.

saludos
p.d.
aclaro que tengo Ubuntu Gutsy pero anteriormente he podido grabar con k3B.
Tambien he tratado de usar Nerolinux pero como ya lo he usado, se venció el plazo de prueba.

---

### Post by ariel on 2008-05-27
> **Vero1 said:**
> Hola,

Nuevamente aquí con un problema.

Resulta que quiero quemar en un CD Hardy Heron. He probado Brasero pero no me lo graba y estoy probando k3B pero me contesta que hay un error porque no tiene permiso para ingresar en el device y no sé qué tengo que hacer.
No entiendo qué clase de permiso necesita porque en la configuración no encuentro nada al respecto.

Agradezco desde ya si me pueden dar una mano con este problema.

saludos
p.d.
aclaro que tengo Ubuntu Gutsy pero anteriormente he podido grabar con k3B.
Tambien he tratado de usar Nerolinux pero como ya lo he usado, se venció el plazo de prueba.

una solucion quick&dirty (pero no recomendable) es, sudo k3b, o sudo brasero

Para una solucion real, pinta que el problema esta en fstab, proba hacer 
cat /etc/fstab

y fijate si esta tu cdrom ahi. Deberia. En mi caso:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Vero1 on 2008-05-28
Hola ariel, gracias por responder.

Mi fstab dice:

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


qué debo agregarle?

Ah, me olvidaba decir que yo tengo Gnome, no Kde, pero igualmente he podido antes grabar con k3B.

Gracias

---

### Post by faktorqm on 2008-05-29
No actualizaste a HH todavia?

la linea te deberia quedar asi:

```
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

Salu2!

---

### Post by Vero1 on 2008-05-29
Hola factorqm,

Justamente el problema está en que no puedo quemar el CD de Hardy y por eso pedí ayuda.

Ahora voy a editar el fstab y agrego lo que me dices pues el mío no está así.
Me falta utf8.

Muchas gracias.

---

### Post by Vero1 on 2008-05-29
> **Vero1 said:**
> Hola factorqm,

Justamente el problema está en que no puedo quemar el CD de Hardy y por eso pedí ayuda.

Ahora voy a editar el fstab y agrego lo que me dices pues el mío no está así.
Me falta utf8.

Muchas gracias.

Acabo de agregar lo que faltaba en el fstab y probé nuevamente usar k3B para quemar el CD, pero sigue fallando.Informa que cdrecord has no permission to open the device. Copié el informe, es largo y si no va aquí pido perdon

```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
ASUS CRW-5232A3 1.02 (/dev/hdb, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ASUS    '
Identification : 'CRW-5232A3      '
Revision       : '1.02'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A (CD-RW)
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1362944 = 1331 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
Track 01: data   697 MB        
Total size:      800 MB (79:18.88) = 356916 sectors
Lout start:      800 MB (79:20/66) = 356916 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11078 (97:34/22)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 2933
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/bin/wodim: faio_wait_on_buffer for writer timed out.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF FF 89 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (valid) 
resid: 63488
cmd finished after 21.874s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 63488 bytes
BFree: 1331 K BSize: 1331 K
Starting new track at sector: 0
Track 01:    0 of  697 MB written.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (valid) 
resid: 63488
cmd finished after 0.038s timeout 200s
/usr/bin/wodim: The current problem looks like a buffer underrun.
/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/wodim: Please report.
/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
Track 01: data   697 MB        
Total size:      800 MB (79:18.88) = 356916 sectors
Lout start:      800 MB (79:20/66) = 356916 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11078 (97:34/22)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 2933
Errno: 0 (Success), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 02 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x02 (medium not present - tray open) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 6.420s timeout 200s
Errno: 0 (Success), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 02 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x02 (medium not present - tray open) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 200s
write track data: error after 0 bytes
Writing  time:  395.372s
Average write speed  12.1x.
Fixating...
Errno: 0 (Success), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 02 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x02 (medium not present - tray open) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.034s timeout 200s
Trouble flushing the cache
Fixating time:   40.299s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdb speed=4 -dao driveropts=burnfree -eject -data -tsize=356916s -
```

---

### Post by sajnox on 2008-05-29
No te hagas problema que lo podes poner por aca al error, lo que generalmente hacemos es tagearlo con code para que sea mas prolijo dentro del foro.

---

### Post by faktorqm on 2008-05-30
Parece ser un problema de permisos, probaste la solucion de ariel? sudo k3b? Salu2!

---

### Post by Vero1 on 2008-06-03
Bueno, se solucionó pero no con el k3B. 
Al final se grabó con el grabador nativo de Ubuntu.
Gracias a todos.

---


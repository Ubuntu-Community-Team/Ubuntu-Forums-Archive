---
title: "Problemas al reproducir cd de audio"
date: 2010-05-09
forum: Software
---

### Post by harryscode on 2010-05-09
Tengo el siguiente problema, cuando quiero escuchar un cd de audio, cualquier reproductor (rhytmbox, vlc, etc) lo reproduce pero entrecortado, como que tarda en cargar el buffer demasiado. Pense que el problema era del cd en cuestion pero probè varios y resulto lo mismo. Probe la lectora de dvd en windows (tengo dual boot) y funciona bien (por eso lo puse acà en soft y no en hard). Cuando quiero abrir el medio con nautillus me tira lo siguiente 
DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name :1.80 was not provided by any .service files

Alguien conoce si es un bug, o si tengo que toquetear algo en cuestión?. La lectora es una samsung y estoy con Lucid.
Gracias

---

### Post by guillermolisi on 2010-05-09
Te fijaste si hay eventos registrados en /var/log/dmesg respecto de la unidad de CD/DVD ?

---

### Post by harryscode on 2010-05-10
> **guillermolisi said:**
> Te fijaste si hay eventos registrados en /var/log/dmesg respecto de la unidad de CD/DVD ?

Hay, y disculpame porque de esto ni en chino lo entiendo, 6 archivos de dmesg (dmesg, dmesg.0, dmesg.1.gz, dmesg.2.gz, dmesg.3.gz y dmesg.4.gz). ¿Qué es lo que tendría que buscar o que tendría que fijarme para que les pueda servir o me indique que es lo que falla/falta?

Esto es lo que encontré referente a cd-rom en dmesg 

[    2.287638] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB01 PQ: 0 ANSI: 5
[    2.295742] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.295753] Uniform CD-ROM driver Revision: 3.20
[    2.296051] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.296214] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.296574] scsi 2:0:0:0: Direct-Access     ATA      WDC WD200EB-00BH 15.1 PQ: 0 ANSI: 5
[    2.296886] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.297268] sd 2:0:0:0: [sdb] 39102336 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    2.297387] sd 2:0:0:0: [sdb] Write Protect is off
[    2.297393] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.297452] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.297853]  sdb: sdb1
[    2.324439] sd 2:0:0:0: [sdb] Attached SCSI disk 

y esto en dmesg.0

2.311898] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB01 PQ: 0 ANSI: 5
[    2.319995] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.320025] Uniform CD-ROM driver Revision: 3.20
[    2.320789] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.321242] sr 3:0:0:0: Attached scsi generic sg2 type 5

Gracias por la ayuda.

---

### Post by alfplayer on 2010-05-10
Los dmesg._número_ son registros viejos (se van rotando, o sea, los registros viejos quedan en estos archivos). El actual es *dmesg*.

---

### Post by guillermolisi on 2010-05-10
> **harryscode said:**
> Hay, y disculpame porque de esto ni en chino lo entiendo, 6 archivos de dmesg (dmesg, dmesg.0, dmesg.1.gz, dmesg.2.gz, dmesg.3.gz y dmesg.4.gz). ¿Qué es lo que tendría que buscar o que tendría que fijarme para que les pueda servir o me indique que es lo que falla/falta?

Esto es lo que encontré referente a cd-rom en dmesg 

[    2.287638] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB01 PQ: 0 ANSI: 5
[    2.295742] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.295753] Uniform CD-ROM driver Revision: 3.20
[    2.296051] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.296214] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.296574] scsi 2:0:0:0: Direct-Access     ATA      WDC WD200EB-00BH 15.1 PQ: 0 ANSI: 5
[    2.296886] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.297268] sd 2:0:0:0: [sdb] 39102336 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    2.297387] sd 2:0:0:0: [sdb] Write Protect is off
[    2.297393] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.297452] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.297853]  sdb: sdb1
[    2.324439] sd 2:0:0:0: [sdb] Attached SCSI disk 

y esto en dmesg.0

2.311898] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB01 PQ: 0 ANSI: 5
[    2.319995] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.320025] Uniform CD-ROM driver Revision: 3.20
[    2.320789] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.321242] sr 3:0:0:0: Attached scsi generic sg2 type 5

Gracias por la ayuda.
Bueno, si no hay mas entradas que esas referidas a CD/DVD, para mi funciona todo bien a nivel hardware (drivers incluidos). Asi que el problema viene por otro lado.

---

### Post by harryscode on 2010-05-11
Gracias Guillermo, ¿alguna idea de por donde tendría que fijarme para ver cual es el problema?

---

### Post by guillermolisi on 2010-05-11
> **harryscode said:**
> Gracias Guillermo, ¿alguna idea de por donde tendría que fijarme para ver cual es el problema?
Se me ocurren varias: Tamaño de buffers, configuracion de PulseAudio, prioridad de uso de CPU, configuracion de calidad de la reproduccion (mas calidad => mas uso de CPU).

Igualmente si ese mensaje de error es permanente, entonces es posible que algo no este correctamente instalado, que este faltando alguna libreria, que haya problemas de versionado, etc. y por eso ese comportamiento

---

### Post by harryscode on 2010-05-11
> **guillermolisi said:**
> Se me ocurren varias: Tamaño de buffers, configuracion de PulseAudio, prioridad de uso de CPU, configuracion de calidad de la reproduccion (mas calidad => mas uso de CPU).

Igualmente si ese mensaje de error es permanente, entonces es posible que algo no este correctamente instalado, que este faltando alguna libreria, que haya problemas de versionado, etc. y por eso ese comportamiento
Ok. Gracias.

---


---
title: "Error al formatear disco duro externo con ext4E"
date: 2012-07-23
forum: Software
---

### Post by donmatas on 2012-07-23
Estimad@s:

Tengo un disco duro externo Toshiba HDDR500E04X de 500 GB. Lo tenía con NTFS, pero la verdad es que no sirve mucho para archivos grandes tipo películas. Por eso pensé en darle formato Ext4, que entiendo es mucho mejor aunque no es compatible con window$ pero me da lo mismo. El problema es que no he podido hacerlo. He intentado con Gparted y vía botón derecho/formatear. En este último caso me arroja el siguiente error:

```
Error formatting volume
Error creating file system: helper exited with exit code 1: 2002: error writing 131072 bytes: Success

```

Gparted me anuncia error pero no da detalles (me propone ir a una página y hacer un montón de trámites burocráticos)

Agradezco cualquier ayuda,
saludos
DM

---

### Post by donmatas on 2012-07-23
Logré darle formato con la herramienta de utilidad de discos de gnome pero ahora me lanza el siguiente error al intentar montar el disco:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by donmatas on 2012-07-23
Lo solucioné creando una partición extendida con Gparted. Esta no me dio problemas. Luego hice una partición lógica con ext4 y una pequeña con ntfs (no se si será necesaria esta última, pero así lo hice y me resultó)

---

### Post by donmatas on 2012-07-24
> **donmatas said:**
> Lo solucioné creando una partición extendida con Gparted. Esta no me dio problemas. Luego hice una partición lógica con ext4 y una pequeña con ntfs (no se si será necesaria esta última, pero así lo hice y me resultó)

La solución duró bastante poco. Al conectar el disco duro externo solo se monta la partición NTFP. La partición ext4 lanza el siguiente error:

```
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

Al intentar montarlo desde la utilidad de discos aparece lo siguiente:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Cualquier orientación se agradece.

---


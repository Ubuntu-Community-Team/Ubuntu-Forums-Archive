---
title: "Problema con partición Windows.."
date: 2008-12-20
forum: Software
---

### Post by morefeo on 2008-12-20
Hola a todos, verán, tengo dos pequeños problemsa con la partición Windows, y antes que todo explicaros.

Problema 1:

Toqueteando Windows pues borré cosas que no debía y ahora ni se inicia, así que quiero conseguir archivos bastante importantes de ahí, por lo que me puse a instalar varios linux a ver que tal eran.

Con GuadaLinex(versión de linux basado en ubuntu de andalucía) podía ver perfectamente la partición Windows y entrar en ella.

Ahora tengo Ubuntu 8.0.4 y la partición Windows no se me puede montar. Teniendo en cuenta que la versión de Guadalinex era la 3, estaría basado en ubuntu 6 más o menos, el cual no traía por defecto el ntfs-3g.

Problema 2:

Parece que cierta ruta de la partición de Windows está dañada, y desde Guadalinex me aparecía: "Contenido ilegible". En dicha ruta es donde tengo uno de los archivos que más necesito recuperar.

¿Alguien puede ayudarme, por favor?

---

### Post by sajnox on 2008-12-20
Para montar una particion de windows "rebelde" podes hacer lo siguiente

1) Listado de discos y particiones con el siguiente comando

```
sudo fdisk -l

```
Y la respuesta es algo parecido a esto:

```
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xb8000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825        6247    19462716   83  Linux
/dev/sda6            6375       19456   105081133+   7  HPFS/NTFS
/dev/sda7            6248        6374     1020096   82  Linux swap / Solaris

```

En este caso la particion que tiene windows es /dev/sda1 que al final de la linea dice HPFS/NTFS

Entonces

1) Crear un punto de montaje

```
sudo mkdir /media/windows

```
2) Montar la particion con la opcion force

```
sudo mount -t ntfs-3g -o force /dev/sda1 /media/windows

```
Con esto debes tener la particion montada

Si queres que la particion se monte automaticamente con el inicio pasanos la salida del comando 

```
cat /etc/fstab
```

---

### Post by morefeo on 2008-12-20
Este es mi fdisk:

```
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       16840   135267268+   7  HPFS/NTFS
/dev/sda2           16841       19456    21013020    5  Extendida
/dev/sda5           16841       17494     5253223+  83  Linux
/dev/sda6           17496       19327    14715508+  83  Linux
/dev/sda7           19328       19456     1036161   82  Linux swap / Solaris
```

Y este mi intento de montaje...
```
Failed to read last sector (312576641): Argumento inválido
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sda1': Argumento inválido
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

No entiendo por que le cuesta tanto montarse, si Guadalinex lo hizo por sí solo.

---


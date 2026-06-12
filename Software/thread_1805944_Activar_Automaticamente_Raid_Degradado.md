---
title: "Activar Automaticamente Raid Degradado"
date: 2011-07-16
forum: Software
---

### Post by Fistandantilus on 2011-07-16
Hola a todos!,

Últimamente estuve haciendo unas pruebas en una maquina virtual con mdadm para tener claro como armar un raid y despues, si lo consigo, comprarme un par de discos y armarmelo de enserio. 

El tema es que cuando simulo sacar un disco el raid se pone inactivo y no puedo hacer para que me lo active automaticamente, por lo que me genera un erro en el boteo pidiendome confirmación para continuar por no poder montar el raid ya que lo tengo en el fstab.

Configuracion:

```
fistan@u-server2:~$ ls -l /dev | grep -v tty | grep -v ram | grep -v loop
total 0
drwxr-xr-x 2 root root         760 2011-07-16 21:52 block
drwxr-xr-x 2 root root          60 2011-07-16 21:52 bsg
drwxr-xr-x 3 root root          60 2011-07-16 21:52 bus
lrwxrwxrwx 1 root root           3 2011-07-16 21:52 cdrom -> sr0
drwxr-xr-x 2 root root        2540 2011-07-16 21:52 char
crw------- 1 root root      5,   1 2011-07-16 21:52 console
lrwxrwxrwx 1 root root          11 2011-07-16 21:52 core -> /proc/kcore
crw-rw---- 1 root root     10,  58 2011-07-16 21:52 cpu_dma_latency
drwxr-xr-x 5 root root         100 2011-07-16 21:52 disk
lrwxrwxrwx 1 root root           3 2011-07-16 21:52 dvd -> sr0
crw-rw---- 1 root root     10,  61 2011-07-16 21:52 ecryptfs
crw-rw---- 1 root video    29,   0 2011-07-16 21:52 fb0
lrwxrwxrwx 1 root root          13 2011-07-16 21:52 fd -> /proc/self/fd
crw-rw-rw- 1 root root      1,   7 2011-07-16 21:52 full
crw-rw-rw- 1 root fuse     10, 229 2011-07-16 21:52 fuse
crw-rw---- 1 root root     10, 228 2011-07-16 21:52 hpet
drwxr-xr-x 3 root root         200 2011-07-16 21:52 input
crw-rw---- 1 root root      1,  11 2011-07-16 21:52 kmsg
srw-rw-rw- 1 root root           0 2011-07-16 21:54 log
drwxr-xr-x 2 root root         120 2011-07-16 21:52 mapper
crw-rw---- 1 root root     10, 227 2011-07-16 21:52 mcelog
brw-rw---- 1 root disk      9,   0 2011-07-16 21:52 md0
crw-r----- 1 root kmem      1,   1 2011-07-16 21:52 mem
drwxr-xr-x 2 root root          60 2011-07-12 21:24 net
crw-rw---- 1 root root     10,  57 2011-07-16 21:52 network_latency
crw-rw---- 1 root root     10,  56 2011-07-16 21:52 network_throughput
crw-rw-rw- 1 root root      1,   3 2011-07-16 21:52 null
crw-rw---- 1 root root      1,  12 2011-07-16 21:52 oldmem
drwxr-xr-x 2 root root          60 2011-07-16 21:52 pktcdvd
crw-r----- 1 root kmem      1,   4 2011-07-16 21:52 port
crw------- 1 root root    108,   0 2011-07-16 21:52 ppp
crw-rw---- 1 root root     10,   1 2011-07-16 21:52 psaux
drwxr-xr-x 2 root root           0 2010-04-19 06:30 pts
crw-rw-rw- 1 root root      1,   8 2011-07-16 21:52 random
crw-r--r-- 1 root root     10,  62 2011-07-16 21:52 rfkill
lrwxrwxrwx 1 root root          22 2011-07-16 21:52 root -> mapper/u--server2-root
lrwxrwxrwx 1 root root           4 2011-07-16 21:52 rtc -> rtc0
crw-rw---- 1 root root    254,   0 2011-07-16 21:52 rtc0
lrwxrwxrwx 1 root root           3 2011-07-16 21:52 scd0 -> sr0
crw-rw---- 1 root cdrom    21,   0 2011-07-16 21:52 sg0
drwxrwxrwt 2 root root          40 2011-07-16 21:52 shm
crw-rw---- 1 root root     10, 231 2011-07-16 21:52 snapshot
lrwxrwxrwx 1 root root          24 2011-07-16 21:52 sndstat -> /proc/asound/oss/sndstat
brw-rw---- 1 root cdrom    11,   0 2011-07-16 21:52 sr0
lrwxrwxrwx 1 root root          15 2011-07-16 21:52 stderr -> /proc/self/fd/2
lrwxrwxrwx 1 root root          15 2011-07-16 21:52 stdin -> /proc/self/fd/0
lrwxrwxrwx 1 root root          15 2011-07-16 21:52 stdout -> /proc/self/fd/1
crw-rw-rw- 1 root root      1,   9 2011-07-16 21:52 urandom
crw-rw---- 1 root root    252,   0 2011-07-16 21:52 usbmon0
crw-rw---- 1 root root    252,   1 2011-07-16 21:52 usbmon1
drwxr-xr-x 2 root root         100 2011-07-16 21:52 u-server2
brw-rw---- 1 root disk    251,   0 2011-07-16 21:52 vda
brw-rw---- 1 root disk    251,   1 2011-07-16 21:52 vda1
brw-rw---- 1 root disk    251,   2 2011-07-16 21:52 vda2
brw-rw---- 1 root disk    251,   5 2011-07-16 21:52 vda5
brw-rw---- 1 root disk    251,  16 2011-07-16 21:52 vdb
brw-rw---- 1 root disk    251,  32 2011-07-16 21:52 vdc
brw-rw---- 1 root disk    251,  33 2011-07-16 21:52 vdc1
brw-rw---- 1 root disk    251,  40 2011-07-16 21:52 vdd
brw-rw---- 1 root disk    251,  41 2011-07-16 21:52 vdd1
crw-rw---- 1 root root     10,  63 2011-07-16 21:52 vga_arbiter
crw-rw-rw- 1 root root      1,   5 2011-07-16 21:52 zero

``````
fistan@u-server2:~$ sudo mdadm --query --detail /dev/md0
[sudo] password for fistan: 
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jul 15 19:08:38 2011
     Raid Level : raid1
     Array Size : 5119488 (4.88 GiB 5.24 GB)
  Used Dev Size : 5119488 (4.88 GiB 5.24 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 16 21:46:21 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : fcdc9268:a18c759f:617c1376:d8b720b8 (local to host u-server2)
         Events : 0.112

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1     251       49        1      active sync   /dev/vdd1

``````
fistan@u-server2:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=fcdc9268:a18c759f:617c1376:d8b720b8 auto=md

``````
fistan@u-server2:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/u--server2-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/vda1 during installation
UUID=2602be25-5758-4ff8-ac7b-295ffafe773c /boot           ext2    defaults        0       2
/dev/mapper/u--server2-swap_1 none            swap    sw              0       0
/dev/mapper/u--server2-datos    /media/datos    ext4    defaults,usrquota,grpquota    1    1
# ACA ME GENERA ERROR EN BOOTEO
/dev/md0    /media/raid ext4 defaults    1    1 

``````
fistan@u-server2:~$ cat /etc/initramfs-tools/conf.d/mdadm 
# mdadm boot_degraded configuration
#
# You can run 'dpkg-reconfigure mdadm' to modify the values in this file, if
# you want. You can also change the values here and changes will be preserved.
# Do note that only the values are preserved; the rest of the file is
# rewritten.
#
# BOOT_DEGRADED:
# Do you want to boot your system if a RAID providing your root filesystem
# becomes degraded?
#
# Running a system with a degraded RAID could result in permanent data loss
# if it suffers another hardware fault.
#
# However, you might answer "yes" if this system is a server, expected to
# tolerate hardware faults and boot unattended.

BOOT_DEGRADED=true

```Si quito el dispositivo "/dev/vdd" me tira una confirmacion en boot(ver img) y el raid queda asi:

```
fistan@u-server2:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive vdc1[0](S)
      5119488 blocks
       
unused devices: <none>

``````
fistan@u-server2:~$ sudo mdadm --query --detail /dev/md0
[sudo] password for fistan: 
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.

```Si quiero que vuelva a estar activo tengo que hacer lo siguiente:

```

fistan@u-server2:~$ sudo mdadm --stop /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: stopped /dev/md0
fistan@u-server2:~$ sudo mdadm --assemble --scan
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 has been started with 1 drive (out of 2).
fistan@u-server2:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 vdc1[0]
      5119488 blocks [2/1] [U_]
      
unused devices: <none>
fistan@u-server2:~$ sudo mdadm --query --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jul 15 19:08:38 2011
     Raid Level : raid1
     Array Size : 5119488 (4.88 GiB 5.24 GB)
  Used Dev Size : 5119488 (4.88 GiB 5.24 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 16 21:51:51 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : fcdc9268:a18c759f:617c1376:d8b720b8 (local to host u-server2)
         Events : 0.112

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1       0        0        1      removed

```Según leí se puede configurar el mdadm para que mande un mail cuando tiene un error en/los raid, aunque todavía no llegue a esa parte no le encuentro la vuelta para que me lo active de todas maneras al iniciar.

Saludos!.

---

### Post by Fistandantilus on 2011-07-22
Bueno, despues de probar e investigar me di cuenta que el que estaba equivocado soy yo :)

El tema este: 
Si está configurado, por medio del arch /etc/mdadm/mdadm, que debe inicializar el array 'X' con 'n' cantidad de discos ya sea explicita(a mano en el arch de conf) o implicitamente(en el superbloque que se genera en cada uno de los discos que hay en el raid) y uno de esos discos desaparecio, el evento que en realidad dispara es "DeviceDisappeared" y no inicia el raid por ser un error crítico. Solo nosotros podemos tomar la responsabilidad de continuar sin un disco que ya no está, sin saber el sistema por que no está mas.

El raid es marcado como "Degraded" cuando se detecta un error en uno de los discos y este es marcado como "faulty":

1) Raid5 sincronizado con 1 spare
```

root@u-server2:/dev# mdadm --query --detail md0
md0:
        Version : 01.00
  Creation Time : Wed Jul 20 14:16:28 2011
     Raid Level : raid5
     Array Size : 2047104 (1999.46 MiB 2096.23 MB)
  Used Dev Size : 1023552 (999.73 MiB 1048.12 MB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 22 14:13:24 2011
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           Name : u-server2:1  (local to host u-server2)
           UUID : 1e13d2b0:1f53b455:41f457bd:3fc414d9
         Events : 123

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1     251       49        1      active sync   /dev/vdd1
       3     251       64        2      active sync   /dev/vde

       4     251       80        -      spare   /dev/vdf

```2) Simulo un error de hardware en /dev/vde y chequeo el estado del raid
```

root@u-server2:/dev# mdadm --manage md0 --fail vde
mdadm: set vde faulty in md0
root@u-server2:/dev# mdadm --query --detail md0
md0:
        Version : 01.00
  Creation Time : Wed Jul 20 14:16:28 2011
     Raid Level : raid5
     Array Size : 2047104 (1999.46 MiB 2096.23 MB)
  Used Dev Size : 1023552 (999.73 MiB 1048.12 MB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 22 14:13:55 2011
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           Name : u-server2:1  (local to host u-server2)
           UUID : 1e13d2b0:1f53b455:41f457bd:3fc414d9
         Events : 128

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1     251       49        1      active sync   /dev/vdd1
       4     251       80        2      spare rebuilding   /dev/vdf

       3     251       64        -      faulty spare   /dev/vde

```3) Simulo un error de hardware en /dev/vdf(el spare que tomo acción en el raid) y chequeo el estado del raid

```

root@u-server2:/dev# mdadm --query --detail md0
md0:
        Version : 01.00
  Creation Time : Wed Jul 20 14:16:28 2011
     Raid Level : raid5
     Array Size : 2047104 (1999.46 MiB 2096.23 MB)
  Used Dev Size : 1023552 (999.73 MiB 1048.12 MB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 22 14:18:43 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : u-server2:1  (local to host u-server2)
           UUID : 1e13d2b0:1f53b455:41f457bd:3fc414d9
         Events : 168

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1     251       49        1      active sync   /dev/vdd1
       2       0        0        2      removed

       3     251       64        -      faulty spare   /dev/vde
       4     251       80        -      faulty spare   /dev/vdf

```4) Reinicio la maquina y veo como quedó el raid

```

root@u-server2:/dev# mdadm --query --detail md0
md0:
        Version : 01.00
  Creation Time : Wed Jul 20 14:16:28 2011
     Raid Level : raid5
     Array Size : 2047104 (1999.46 MiB 2096.23 MB)
  Used Dev Size : 1023552 (999.73 MiB 1048.12 MB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 22 14:20:23 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : u-server2:1  (local to host u-server2)
           UUID : 1e13d2b0:1f53b455:41f457bd:3fc414d9
         Events : 174

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1     251       49        1      active sync   /dev/vdd1
       2       0        0        2      removed

```a)Me lo inició automaticamente, sin tener que activarlo a mano
b)Lo marcó como "degraded" y me envio el mail correspondiente
c)Me quitó automaticamente los discos marcados como "faulty"

5) Apago la vm, quito los dicos y veo como quedó el raid

```

root@u-server2:/dev# mdadm --query --detail md0
md0:
        Version : 01.00
  Creation Time : Wed Jul 20 14:16:28 2011
     Raid Level : raid5
     Array Size : 2047104 (1999.46 MiB 2096.23 MB)
  Used Dev Size : 1023552 (999.73 MiB 1048.12 MB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 22 14:23:57 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : u-server2:1  (local to host u-server2)
           UUID : 1e13d2b0:1f53b455:41f457bd:3fc414d9
         Events : 178

    Number   Major   Minor   RaidDevice State
       0     251       33        0      active sync   /dev/vdc1
       1     251       49        1      active sync   /dev/vdd1
       2       0        0        2      removed

```Idem punto anterior. Y ahora no se registro el error "DeviceDisappeared" como en el caso anterior, cuando solo quite los disco, ya que estos ya fueron marcados como erroneos y descartados.

Espero que alguien le sirva esto.

Saludos a Todos!.

---


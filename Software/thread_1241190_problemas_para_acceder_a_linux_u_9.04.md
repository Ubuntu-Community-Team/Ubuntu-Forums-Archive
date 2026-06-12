---
title: "problemas para acceder a linux u 9.04"
date: 2009-08-15
forum: Software
---

### Post by pepelepuf on 2009-08-15
[FONT=Verdana]Amigos. [/FONT]
[FONT=Verdana]Soy nuevo en esto de linux. Tengo ubuntu 9.04. Mi rpobela son dos. [/FONT]
 
[FONT=Verdana]- cuando incio ubuntu me aparece el siguiente mensaje: [/FONT]
[FONT=Verdana]"GDM no pudo crear una nueva entrada de autorizacion en el disco. Poiblemente no hay espacio en el disco. Error: No hay espacio libre en el disposditivo" [/FONT]
[FONT=Verdana]Luego de eso me pide login pasword, los ingreso y me aparece este otro mensaje: [/FONT]
 
[FONT=Verdana]" 32 packages can be updated [/FONT]
[FONT=Verdana]26 updated are security updated. [/FONT]
[FONT=Verdana]-Bash: No hay control de tareas en este shell. [/FONT]
[FONT=Verdana]jose@jose-laptop: $ [/FONT]
 
[FONT=Verdana]Sobre esto no se que hacer. [/FONT]
 
[FONT=Verdana]2. Cuando intento ingresar en modo prueba de errores aparece lo siguiente [/FONT]
[FONT=Verdana]- me pide login, luego pasword. Cuando hago todo eso me aparece este siguiente mensaje y no se que hacer: [/FONT]
 
[FONT=Verdana]"Enter the name of the host and port (host:port) you want to log in to. [/FONT]
 
[FONT=Verdana]Espero que me ayuden pq he intentao muchas cosas pero sin exito. [/FONT]
[FONT=Verdana]Gracias de antemano.[/FONT]

---

### Post by Carlos C on 2009-08-16
¿Cómo instalaste Ubuntu? ¿compartes el disco con otro sistema operativo? ¿Hiciste un particionado manual? Por favor copia lo que te sale cuando escribes en el terminal:
```
sudo fdisk -l
```
Saludos.

---

### Post by v1nsai on 2009-08-16
Le sugiero que vuelva a instalar, parace que algo ha fallado durante la instalacion.  Usted ha dicho que estas nuevo en linux para que no tienes data importante en el disco, verdad?

---

### Post by pepelepuf on 2009-08-16
Hola carlos y gracias por tu procupacion.
Mira esto aparece al ingresar lo que meseñalaste:
 
fdisk: invalid option --´1´
usage:fdisk [-b SSZ] [-U] DISK        Change partition table
         fdisk -1 [-b SSZ] [-u] DISK    List partition table(s)
         fdisk -s PARTITION               Give partition size(s) in blocks
         fdisk -v                               Give fdisk version
Here DISK is something like/dev/hdb or /dev/sda
and PARTITION is something like /dev/hda67
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors.
 
Eso aparece :)

---

### Post by robertor on 2009-08-16
> **pepelepuf said:**
> Hola carlos y gracias por tu procupacion.
Mira esto aparece al ingresar lo que meseñalaste:
 
fdisk: invalid option --´1´
usage:fdisk [-b SSZ] [-U] DISK        Change partition table
         fdisk -1 [-b SSZ] [-u] DISK    List partition table(s)
         fdisk -s PARTITION               Give partition size(s) in blocks
         fdisk -v                               Give fdisk version
Here DISK is something like/dev/hdb or /dev/sda
and PARTITION is something like /dev/hda67
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors.
 
Eso aparece :)

Carlos C lo que te decia que pusieras en la terminal era fdisk -l no -1... en palabras seria fdisk menos ele, **no** fdisk menos uno.
Tirate tambien un ```
df -h
```

Saludos!
Roberto

---

### Post by pepelepuf on 2009-08-16
jajoajojoaa, perdona parecia 1:P
 
Mira esto aparece:
 
[SIZE=2][FONT=Calibri][FONT=Calibri]1.[/FONT]       [/FONT][FONT=Calibri]Esto aparece agrgando lo que me señalas ingresando L en vez de 1[/FONT][/SIZE]
[FONT=Calibri][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri][SIZE=2]Disk /dev/sda: 50.0 GB 50018393008 bytes[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]255 heads, 63 sectors/track, 6081 cylinders[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]Units= cylinders  of  16065* 512= 8225280 bytes [/SIZE][/FONT]
[FONT=Calibri][SIZE=2]Disk identifier: 0x02d102d1[/SIZE][/FONT]
[FONT=Calibri][SIZE=2] [/SIZE][/FONT]
[FONT=Calibri][SIZE=2]Device boot                       Start                        End                   Blocks         id       system[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]/dev/sda1 *                         1                            5593               44925741     83       Linux[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]/dev/sda2                           5594                      6081                3919860       5       Extended[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]/dev/sda5                         5920                         6081               1301233       82    Linux swap/solaris[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]/dev/sda6                           5594                        5897              2441817       83      Linux[/SIZE][/FONT]
[FONT=Calibri][SIZE=2]/dev/sda7                           5898                       5919               176683*      82     Linux swap/solaris[/SIZE][/FONT]
[SIZE=2][/SIZE] 
[FONT=Calibri][SIZE=2]Position table entries are not in disk order[/SIZE][/FONT]
[FONT=Calibri][SIZE=2][/SIZE][/FONT] 
[FONT=Calibri][SIZE=2][FONT=Calibri][FONT=Calibri][SIZE=2]2 ingresando[/SIZE][/FONT]       [/FONT] df –h[/SIZE]
[SIZE=2]Filesystem                  Size         Used      Avail     use%                  mounted on[/SIZE]
[SIZE=2]/dev/sda1                    43g          25g        16g        62%                            /[/SIZE]
[SIZE=2]Tmpfs                         218M          0          218M    0%                      /lib/init/rw[/SIZE]
[SIZE=2]Varrun                         218M        8.0K     218M    1%                    /var/run[/SIZE]
[SIZE=2]Varlock                        218M        0            218M    0%                  /var/lock[/SIZE]
[SIZE=2]Udev                           218M         148K    218M    1%                      /dev[/SIZE]
[SIZE=2]Tmpfs                           218M        0           218M      0%          /dev/shm[/SIZE]
[SIZE=2]Lrm                             218M        2.4M       215M     2%       /lib/modules/2.628-11-generic/volatile[/SIZE]
[SIZE=2] [/SIZE][SIZE=2] [/SIZE]
[SIZE=2]Gracias denuevo  Roberto.[/SIZE]
[/FONT]

---

### Post by Carlos C on 2009-08-17
Hay un pequeño desorden con las particiones. Te lo pregunto de nuevo: ¿Tienes más de un sistema operativo instalado? Porque veo que tienes dos particiones swap (algo que no es necesario, se puede usar la misma para todas las distro instaladas). ¿Cómo fue que instalaste? Explica bien por favor lo que hiciste.

---

### Post by pepelepuf on 2009-08-17
Hola roberto.
 
Respecto si tengo dos sistemas operativos solo tengo el de linux u 9.04.
 
Respecto de como fue instalado es una historia larga. En lineas generales mi computador tenia antes el windows point (una version de windows modificada). Llego un momento en que mi computador se hecho a paerder, no lo podia hacer arrancar y fue, digamos por accidente, que un amigo me recomendo instalar el linux explicandome toas las ventajas que tenia. Respecto a esto ultimo fue este amigo quien lo instalo y no se que manojo hizo, pq necesito harto tiempo a raiz de que tuvo que configurar lo relacionado con las graficas. A groso modo eso te puedo contar roberto.
 
Un saludos y muchas gracias otra vez.
 
JOSE LUIS.

---

### Post by Carlos C on 2009-08-22
La verdad es que te recomiendo instalar todo nuevamente, usando el LiveCD de Ubuntu. Trata de hacer una instalación limpia, creando una tabla de particiones nueva. Ya que no intentas compartir el mismo disco con otro sistema operativo no es necesario tener más de una partición swap, me parece que tu amigo se enredó un poco y te dejó un pequeño gran desorden. Por esta misma razón, para evitar que algo así vuelva a pasarte, te sugiero leas el siguiente enlace en donde se explica el tema del particionado:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

Saludos.

---

### Post by gmunioz on 2009-08-22
Hola y sumimasen por la intromisión:

Mi sugerencia es que:

a) Inicies la instalación desde un live-cd de Ubuntu.

b) Cuando llegues a particionamiento, elijas manual.

c) Elimines todas las particiones, comenzando por la
   última (/dev/sda7)

d) Crees las siguientes:

Una primaria, activa, sistema de archivos ext4, punto
de montaje /, de 12 gigas

Una lógica, sistema de archivos intercambio, montaje
por defecto, de 1 giga

Una lógica, sistema de archivos ext4, punto de montaje
/home, del resto de los gigas

Apliques lo cambios y termines la instalación.

---


---
title: "Problemas con GParted tratando de redimensionar las particiones"
date: 2012-02-18
forum: Software
---

### Post by madbyte on 2012-02-18
Hola,

Después de actualizar semanalmente Ubuntu 11.10 me salió un mensaje diciendo que me quedaba poco espacio en la partición asignada a **/**. Como en **/home** tengo varios gigas libres, decidí pasar unos cuantos a **/**. Use un USB stick con Ubuntu 10.04 y la aplicación GParted para realizar la tarea... Redimensione, **/home** y **swap** corriéndome hacia **/** y deje que la aplicacion haga lo suyo. Cuando vuelvo GParted estaba cerrada con un mensaje de error en la terminal, que lamentablemente perdí, pero se parecía mas un crash que un error en el disco porque me pedía mandar un informe con los datos del problema. Salgo del Live entro (por suerte) en Ubuntu corro GParted y me tira lo siguiente:

[IMG]http://www.picamatic.com/show/2012/02/18/08/13/8233568_932x651.png[/IMG]

Que muestra los 10 Gigas liberados de **/home**. En este punto estoy logeado como root porque pretendía realizar solo el redimensionamiento de la parte **extended, **pensando en 2 cosas: Que la 1era tarea se habia llevado a cabo sin errores, y que fallo cuando quiso redimensionar la **extended** (2da tarea).

Al intentar realizar esa tarea con la nueva versión de GParted (0.8.1) obtengo esto:

```

======================
libparted : 2.3
======================
No se pueden satisfacer todas las restricciones en la partición.
Backtrace tiene 10 llamadas en espera:
  10: /lib/libparted.so.0(ped_assert+0x29) [0xb778eb99]
  9: /lib/libparted.so.0(+0x42497) [0xb77c7497]
  8: /lib/libparted.so.0(+0x10f76) [0xb7795f76]
  7: /lib/libparted.so.0(ped_disk_set_partition_geom+0x197) [0xb7796ff7]
  6: /usr/sbin/gpartedbin() [0x80c61a4]
  5: /usr/sbin/gpartedbin() [0x80c9542]
  4: /usr/sbin/gpartedbin() [0x80c982e]
  3: /usr/sbin/gpartedbin() [0x8086f5d]
  2: /lib/i386-linux-gnu/libpthread.so.0(+0x6d31) [0xb6b8dd31]
  1: /lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0xb6add0ce]
La aserción (metadata_length > 0) en ../../../libparted/labels/dos.c:2178 en la función add_logical_part_metadata() ha fallado.

```y para peor un cfdisk /dev/sdb me tira:

```

ERROR MUY GRAVE: Partición lógica incorrecta 6: Solapamiento de particiones lÃ

```y esto me tira fdisk -lu:

```

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x98ce98ce

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS/exFAT

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x58404473

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1              63   874369754   437184846    7  HPFS/NTFS/exFAT
/dev/sdb2   *   874369755   894370679    10000462+  83  Linux
/dev/sdb3       894370804   976768064    41198630+   5  Extendida
/dev/sdb5       974760129   976768064     1003968   82  Linux swap / Solaris
/dev/sdb6       914952192   974759935    29903872   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

```Que se puede hacer??

---

### Post by euzkoarima on 2012-02-21
Lo único que se me ocurre es recomendarte probar con SystemRescueCD [0] y dentro de ese liveCD el ultilitario TestDisk [1]
No puedo asegurar que te solucione nada, pero si el problema es solapamiento (como dice uno de los mensajes) TestDisk es capaz de dar una mano en esos casos.

[0] [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage")

[1] [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Saludos,
Eduardo

---

### Post by madbyte on 2012-02-26
Gracias por la info, he probado y pude terminar de completar el movimiento de las particiones "Paso a Paso" es decir no de un solo saque, moviendo de a 4/5 gigas por vez, de esa manera no me tiraba error GParted. Igual cfdisk me sigue tirando el error de solapamiento, estuve leyendo varios post relacionados y no pude sacar nada en concreto. Por ahora mi Ubuntu anda de 10 y ya tengo 10Gigas mas para **/**, aunque no se si está como para un SOLVED. Asi quedo mi disco:

GParted
[IMG]http://www.picamatic.com/show/2012/02/26/10/06/8248312_787x527.png[/IMG]



sudo fdisk -l
```

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x58404473

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1              63   874369754   437184846    7  HPFS/NTFS/exFAT
/dev/sdb2   *   874369755   914948095    20289170+  83  Linux
/dev/sdb3       914948096   976771071    30911488    5  Extendida
/dev/sdb5       974760129   976771071     1005471+  82  Linux swap / Solaris
/dev/sdb6       914952192   974759935    29903872   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

```
sudo parted /dev/sdb
```

GNU Parted 2.3
Usando /dev/sdb
¡Bienvenido/a a GNU Parted! Teclee «help» para ver la lista de órdenes.
(parted) print                                                            
Modelo: ATA WDC WD5000AAKS-0 (scsi)
Disco /dev/sdb: 500GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Typo      Sistema de ficheros  Banderas
 1      32,3kB  448GB  448GB   primary   ntfs
 2      448GB   468GB  20,8GB  primary   ext4                 arranque
 3      468GB   500GB  31,7GB  extended
 6      468GB   499GB  30,6GB  logical   ext4
 5      499GB   500GB  1030MB  logical   linux-swap(v1)

(parted)                                                                  

```


Saludos

---

### Post by guillermolisi on 2012-02-27
Gparted y parted tuvieron actualizaciones desde la 10.04 a la 11.10.

Para casos como este mi sugerencia es que la maniobra se haga siempre desde una sesion Live con la misma version (y arquitectura) que la del SO que esta instalado.

---

### Post by Flip10 on 2012-03-15
Hola madbyte tengo la misma intención que tu, no puedo actualizar a Ubuntu 11.10 por falta de espacio en la partición **/** y como tengo bastante espacio en **/home** quiero redimensionar esa partición. Mis particiones están distribuidas de la misma forma que las tuyas y me imagino que tendré el mismo problema que tu. ¿Has seguido lo propuesto por euzkoarima para solucionarlo?

Otra duda, leí al respecto que gparted no puede redimensionar particiones lógicas, ni tampoco una extendida si no está vacía, ¿como lo has hecho tu?

¿Has seguida algún manual? y si es así podrías recomendarmelo? 

Gracias, saludos!

---

### Post by madbyte on 2012-03-23
Hola,

Como dice guillermolisi usa la versión de GParted correspondiente a tu versión de Ubuntu. Yo arranque desde un LiveUSB y redimensione todo con GParted. Como habrás leído, el proceso tuvo sus inconvenientes, pero la versión de Live que yo usé correspondía a una versión anterior a mi Ubuntu actual. Tenes que ir haciendo espacio "corriendo" (una especie de shift register jeje) la cantidad de gigas que vas liberando desde **/home** hacia la particion a donde queres terminar. Hay en youtube montones de videos y muchos tutoriales dando vueltas.

Saludos

---

### Post by EnriqueK on 2012-03-24
Tal vez con solo mover y emlazar el caché sea suficiente y así te evitás el tener que redimensinar partiones, aspecto este que en lo personal lo encuentro peligroso, ejecutá los siguientes comandos
sudo mv /var/cache/apt/archives /home
sudo ln -s /home/archives /var/cache/apt
Terminado esto, probá en actualizar, ahora los paquetes descargados se alojarán en /home/archives y allí tienes mucho espacio disponible.
Si a pesar de haber hecho lo anterior te sigue dando problemas de falta de espacio, sugiero NO usar Gparted, sino emplear el siguiente método  el cual es totalmente seguro al menos si vas a requerir tener otro DD para realizar el proceso.
[http://ubuntuforums.org/showthread.php?t=1759591](http://ubuntuforums.org/showthread.php?t=1759591)

---


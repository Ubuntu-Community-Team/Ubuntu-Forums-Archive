---
title: "Poco espacio en particion de Ubuntu"
date: 2009-09-05
forum: Software
---

### Post by matias_tati on 2009-09-05
Hola tengo este problema de que me quedo sin espacio en la particion de Ubuntu. Tengo 3 una para Ubuntu, una para windows y otra NTFS para datos como debo hacer tengo riesgo de perder mis datos? Pq lei otros post pero no se si seria aplicable a mi cuando se trata de datos prefiero consultar antes. Gracias!!!

---

### Post by gmunioz on 2009-09-05
Hola mat....:

Ejecuta en consola:

[HTML]sudo fdisk -l  *(es ele no uno ni i)*[/HTML]

Pega la salida en el post

---

### Post by matias_tati on 2009-09-05
matias@matias-desktop:~$ sudo fdisk -l  *(es ele no uno ni i)*
bash: error de sintaxis cerca de token no esperado `('
matias@matias-desktop:~$ sudo fdisk -l
[sudo] password for matias: 

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x26022602

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            5100       19131   112712008+   7  HPFS/NTFS
/dev/sda3            2551        5099    20474842+   f  W95 Ext'd (LBA)
/dev/sda5            2551        4987    19575171   83  Linux
/dev/sda6            4988        5099      899608+  82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco
matias@matias-desktop:~$ 

Grax

---

### Post by gmunioz on 2009-09-05
Hola mat...:

Según fdisk, que nunca se equivoca tienes:

/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS

Es la partición que aloja a MS Windows

/dev/sda3 2551 5099 20474842+ f W95 Ext'd (LBA)

Es la partición extendida que aloja a las lógicas

/dev/sda5 2551 4987 19575171 83 Linux

Es la partición root /

/dev/sda6 4988 5099 899608+ 82 Linux swap / Solaris

Es la partición swap

/dev/sda2 5100 19131 112712008+ 7 HPFS/NTFS

Es la partición ntfs de datos

Por lo expuesto tienes dedicado a Ms Windows 25,3 gigas

lo que es sobre abundante.

Lo más practico sería a mi entender:

1 - Desde MS Windows corre chkdsk /f sobre c:
    
    Luego corre defrag y cierra correctamente, dejando

    establecido nuevamente que en el proximo inicio corra

    chkdsk /f sobre c:

2- Desde una sesión live, desmonta las particiones

   Inicia gparted, Sistema - Administración - Editor de particiones

   Reduce la partición /dev/sda1 en lo que consideres adecuado

   Aumenta /dev/sda5 en la cantidad que le has disminuido a

   /dev/sda1

   Aplica los cambios.

   Verifica la uuid de /dev/sda5, ejecutando en consola

   sudo vol_id --uuid /dev/sda5

   anota la misma

   monta la partición /dev/sda5

   accede a los archivos:

   /etc/fstab

   /boot/grub/menu.lst

   constata que la uuid de /dev/sda5 no haya variado, si 
   
   ha variado, cambiala  por la obtenida con el comando

   sudo vol_id --uuid, ejecutando en consola:

   sudo gedit

   Buscas los archivos y los editas.

   Cierra la sesión live y reinicia, primero con Ms Windows, 

   luego con Ubuntu.

---

### Post by matias_tati on 2009-09-05
Momento que soy lento........Podrias especificar los pasos un poco mas? Con leerlos solamente me perdi. Crei que era algo mas facil....

---

### Post by gmunioz on 2009-09-05
Hola mat...:

Es más dificil escribirlo que hacerlo.


1- Ejecutar en MS Windows, chkdsk /f y defrag sobre c:

c: de MS Windows es /dev/sda1 para Ubuntu.

chkdsk se ejecuta en consola de MS Windows y se programa

para el siguiente inicio, al dejarlo programado preparas 

a MS Windows  para que chequee las modificaciones y se adapte.

2- Las modificaciones de las particiones se hacen con las

particiones desmontadas, por lo tanto debes hacerlas desde

una sesión live, con un live cd de Ubuntu por ejemplo.

Luego de ejecutar el punto 1, inicias con un live cd.

Seguramente Ubuntu montará las particiones, las desmontas 

en consola con la orden

sudo umount /dev/sda1

sudo umount /dev/sda5

Estas particiones son contiguas, por lo que le saques a

/dev/sda1, c: de MS Windows, se lo prodrás agregar a /dev/sda5

/ de Ubuntu.

Esto lo haces desde el Editor de particiones.

Una vez iniciado, eliges /dev/sda, iluminas /dev/sda1, elige 

modificar y la reduces, luego eliges /dev/sda5 y la aumentas

hasta aqui nada se ha hecho, todo se hará recien cuando pulses

aplicar y aceptes que se apliquen los cambios, si te arrepientes 

o asustas, cierras gparted y nada pasó.

3- MS Windows es quisquilloso y a veces los cambios de particiones

lo afectan, al programar a chkdsk, se soluciona este posible problema.

4- Ubuntu registra en /etc/fstab y en /boot/grub/menu.lst las 

particiones mediante su uuid, al modificar /dev/sda5 es posible que

cambie ó no, si cambia no iniciará Ubuntu y deberás corregirlas

mediante una sesión live, para evitarlo directamente una vez hechos

los cambios de particiones, antes de cerrar la sesión live revisas

la uuid de la partición /dev/sda5, si cambió, la cambias ya por la

nueva uuid, en ambos archivos.

---

### Post by matias_tati on 2009-09-06
Hooa cuando inicio el gparted me deja achicar sda1 pero no me deja agrandar sda5. Como lo hago?

---

### Post by gmunioz on 2009-09-07
Hola mat....:

Incorpora primero el espacio liberado a la

partición extendida

/dev/sda3

Luego le agregas lo incorporado a la extendida

/dev/sda3 a la lógica 

/dev/sda5

---


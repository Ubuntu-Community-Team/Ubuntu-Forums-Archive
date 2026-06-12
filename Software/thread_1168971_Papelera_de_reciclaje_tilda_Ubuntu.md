---
title: "Papelera de reciclaje tilda Ubuntu"
date: 2009-05-24
forum: Software
---

### Post by aledruetta on 2009-05-24
Hola Comunidad!

Ayer comenzó a suceder (o mejor dicho, ayer percibí que esto estaba sucediendo) algo extraño con mi Ubuntu Jaunty. Cuando vacío la papelera se tilda el sistema. Queda congelado, no puedo hacer nada más, ni mover el puntero del mouse.

Acontece si borro un archivo grande, una película, por ejemplo, pero también si se trata de un archivo de unos pocos kb.

Cuando pasa esto, tengo que apagar la portátil y volver a encenderla. Cuando vuelve a cargar el sistema, llega hasta un 80% más o menos y se tilda otra vez. Recién la segunda vez que apago y inicio, se carga el sistema.

No tengo idea de a qué otro suceso lo puedo vincular como para saber cuál puede ser el origen del problema.

¿Alguien tiene idea de qué puede estar causando esto?

Saludos y muchas gracias,
Alejandro.

---

### Post by aledruetta on 2009-05-24
Perdón, quise corregir un error de ortografía en el título y apareció el post duplicado.
Quizá los administradores puedan borrarlo.
Gracias,
Alejandro.

---

### Post by Carlos C on 2009-05-24
Tienes más de un disco? de haber más de uno, tienes particiones en formato ntfs o fat32? Por favor, dinos que resultado obtienes cuando escribes en el terminal:
```
sudo find / -type d -name *Trash*
```

---

### Post by aledruetta on 2009-05-25
Tengo un disco, donde está Ubuntu con formato Ext4, y tengo un disco USB WesterDigital formateado en NTFS. Pero al disco USB lo uso para backup, por lo tanto, rara vez está conectado a la portátil.

La consola me tira lo siguiente:

```
/home/alejandro/.local/share/Trash
/root/.local/share/Trash

```

Algo que también noté ahora, y que puede estar relacionado, es que, si voy a Lugares-->Equipo-->Propiedades, a veces reconoce el tamaño del disco y el espacio que queda libre del mismo, y otras veces no, dice "desconocido". 

Saludos y muchas gracias,
Alejandro.

---

### Post by Carlos C on 2009-05-25
> **aledruetta said:**
> La consola me tira lo siguiente:

```
/home/alejandro/.local/share/Trash
/root/.local/share/Trash

```
Probemos primero con vaciar la papelera. Para ello usa estos dos comandos:
```
rm -rf /home/alejandro/.local/share/Trash
sudo rm -rf /root/.local/share/Trash
```Mucho cuidado con estos comandos. Debes copiarlos tal y como están, para que se borre recursivamente todo lo que está al interior de ambas carpetas.
Lo otro que me parece importante es esto:
> Algo que también noté ahora, y que puede estar relacionado, es que, si voy a Lugares-->Equipo-->Propiedades, a veces reconoce el tamaño del disco y el espacio que queda libre del mismo, y otras veces no, dice "desconocido". Creo que, con la papelera vacía, debes verificar el sistema de archivos de tu disco duro. Te recomiendo que inicies Ubuntu con un LiveCD, ya que necesitas que tus particiones no estén montadas). Después ejecuta el siguiente comando para que sepas la ruta de tus particiones:
```
sudo fdisk -l
```Por ejemplo, a mí me aparece algo como esto:
```
/dev/sda1   *           1       29214    14723541   83  Linux
/dev/sda2           29214       33103     1959930   82  Linux swap / Solaris
/dev/sda3           33103       77520    22386577+  83  Linux
```Para verificar el sistema de archivos en las particiones sda1 y sda3 debo ejecutar los siguientes comandos:
```
e2fsck -p /dev/sda1
e2fsck -p /dev/sda3
```e2fsck es el comando que verifica el sistema de archivos. El parámetro "-p" permite reparar automáticamente todo lo que sea seguro reparar. Para más información sobre este comando puedes mirar [acá]("http://blockdeubuntu.blogspot.com/2009/01/escaneando-el-sistema-de-archivos-de.html"). Demorará un tiempo, así que tienes que armarte de paciencia y, recuerda, los discos no deben estar montados.

---

### Post by aledruetta on 2009-05-25
Hola Carlos,

Seguí tus instrucciones, pero con los comandos se borraron las carpetas Trash, junto con el contenido.

Así que, lo que hice fue:
```
sudo nautilus
```
y volvía a crear los dos directorios, el de usuario y el de root.
La duda que me queda es respecto a los permisos:
```
drwxr-xr-x 2 root root 4096 2009-05-25 12:16 Trash
drwxr-xr-x 2 alejandro alejandro 4096 2009-05-25 12:15 Trash
```
¿Están bien así? ¿Tengo que modificar algo?

Lo del Live CD todavía no lo probé. En un minuto lo hago y después comento el resultado.

Saludos y muchas gracias,
Alejandro.

---

### Post by Carlos C on 2009-05-25
> **aledruetta said:**
> Hola Carlos,

Seguí tus instrucciones, pero con los comandos se borraron las carpetas Trash, junto con el contenido.

Así que, lo que hice fue:
```
sudo nautilus
```y volvía a crear los dos directorios, el de usuario y el de root.
La duda que me queda es respecto a los permisos:
```
drwxr-xr-x 2 root root 4096 2009-05-25 12:16 Trash
drwxr-xr-x 2 alejandro alejandro 4096 2009-05-25 12:15 Trash
```¿Están bien así? ¿Tengo que modificar algo?
.
No es necesario que en tu papelera el grupo tenga permisos de lectura y ejecución. Basta con que los permisos sean tuyos. Los permisos debieran verse así:
```
drwx------ 4 carlos carlos 4096 2008-11-01 14:31 Trash
```Si tienes dudas de cómo configurarlo puedes hacerlo desde nautilus:
[[IMG]http://img26.imageshack.us/img26/8718/papelerausuario.th.jpg[/IMG]]("http://img26.imageshack.us/my.php?image=papelerausuario.jpg")
En el caso de la papelera del root es lo mismo:
```
drwx------ 4 root root 4096 2008-11-01 20:10 Trash
```Visto desde nautilus:
[[IMG]http://img26.imageshack.us/img26/6359/papeleraroot.th.jpg[/IMG]]("http://img26.imageshack.us/my.php?image=papeleraroot.jpg")

---

### Post by aledruetta on 2009-05-25
> **Carlos C said:**
> ...ejecuta el siguiente comando para que sepas la ruta de tus particiones:
```
sudo fdisk -l
```...Para verificar el sistema de archivos en las particiones sda1 y sda3 debo ejecutar los siguientes comandos:
```
e2fsck -p /dev/sda1
e2fsck -p /dev/sda3
```...Demorará un tiempo, así que tienes que armarte de paciencia y, recuerda, los discos no deben estar montados.

Hola Carlos,

```
sudo fdisk -l
``` me tira:
```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x97be5b6a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9667    77650146   83  Linux
/dev/sda2            9668        9729      498015    f  W95 Ext'd (LBA)
/dev/sda5            9668        9729      497983+  82  Linux swap / Solaris
```y
```
e2fsck -p /dev/sda1
``` me tira:
```
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda1
/dev/sda1: limpio, 180981/4857856 ficheros, 14729099/19412536 bloques

``` Pero lo tira al instante, no demora ni un segundo.

¿Se puede interpretar algo de esos datos?

Saludos y muchas gracias,
Alejandro.

---

### Post by aledruetta on 2009-06-12
Hola Comunidad,

Vuelvo a insistir con la pregunta porque no logré solucionar el problema. Reinstalé el sistema, con lo cual resolví otros problemas que tenía, pero cuando vacío la papelera con archivos voluminosos, como una imagen iso de un DVD por ejemplo, se tilda el sistema al mejor estilo Windows (pero sin pantalla azul) y no queda otra que apagar la portátil a lo bruto y reiniciar.

Si a alguien se le ocurre qué hacer, le estaré sumamente agradecido.

Saludos, 
Alejandro.

---

### Post by CdK1 on 2009-06-12
Veamos, yo haría lo siguiente:

Usar Mi laptop sin conectar el disco, en ningún caso... y por ende avisar,
dar modelo del Laptop y versión del kernel...

---

### Post by Carlos C on 2009-06-12
Pienso lo mismo. Primero ver si ocurre sin el disco usb conectado. Además, dar más datos sobre tu equipo.

Lo otro que me gustaría sugerir es que esto puede estar relacionado con un bug que pagondel me mostró cuando le comenté sobre tu problema:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824)

Si es así, lo mejor sería que en tu caso instalaras Ubuntu con ext3, que nunca da problemas.

---

### Post by aledruetta on 2009-06-14
> **CdK1 said:**
> Veamos, yo haría lo siguiente:

Usar Mi laptop sin conectar el disco, en ningún caso... y por ende avisar,
dar modelo del Laptop y versión del kernel...

El modelo de la máquinita es: Acer Aspire 4310.
El kernel es: Linux 2.6.28-11-generic (i686)
SO: Ubuntu 9.04 Jaunty Jackalpe.
El sistema de archivos: Ext4.

> **Carlos C said:**
> 
Lo otro que me gustaría sugerir es que esto puede estar relacionado con un bug que pagondel me mostró cuando le comenté sobre tu problema:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824)

Si es así, lo mejor sería que en tu caso instalaras Ubuntu con ext3, que nunca da problemas.

Y... posiblemente el problema venga por ese lado, pero ¿cómo saberlo? ¿reinstalando el sistema en Ext3?

---

### Post by Carlos C on 2009-06-14
> **aledruetta said:**
> Y... posiblemente el problema venga por ese lado, pero ¿cómo saberlo? ¿reinstalando el sistema en Ext3?

Sí, es lo que yo haría, reinstalaría Ubuntu pero con sistema ext3. Porque si efectivamente es tu caso, ese bug aún no se ha solucionado satisfactoriamente.

---


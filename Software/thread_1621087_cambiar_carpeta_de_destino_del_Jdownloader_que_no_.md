---
title: "cambiar carpeta de destino del Jdownloader que no sea (/)"
date: 2010-11-13
forum: Software
---

### Post by juakel on 2010-11-13
Que tal gente, me acabo de descargar el JD pero no puedo configurar la carpeta de descarga, las particiones son asi:
en el disco C: tengo instalado el windows y junto con el el ubunto 10.10, pero no dentro de windows, si no como la tercer opcion que ofrece al instalar el ubunto.
en la otra particion ( E:) es para todo lo que sea datos.
ahora el problema es que cuando voy a cambiar la carpeta de destino del JD en el ubunto solo me aparece la raiz (/), no se como se puede hacer para que me descargue en el disco (E:)

si algien sabe desde ya le agradesco su ayuda, soy nuevo y poco a poco voy aprendiendo de este hermoso y poderoso OS...

muchas gracias...

---

### Post by granjero on 2010-11-15
hola, una pregunta, el disco e:\ ubuntu lo monta al iniciar?

porque si no lo monta no lo vas a ver....

además ubuntu no usa letras para los distintos HD sino que los monta como directorios del sistema de archivos, por lo que seguramente tu disco e:\ se encuentre montado en /media (si es que lo monta al inicio) o en /mnt no estoy seguro de como es la instalación por wubi....

contanos más sobre como están tus discos duros en ubuntu así te podemos ayudar....

copiá la salida del comando 

```
sudo fdisk -l
```


salud!

---

### Post by juakel on 2010-11-15
que tal granjer, gracias por responder... aquie estan los datos que me pediste, la verdad que mucho no entiendo, estoy empezando recien en esto...

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0728cd9b

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3040    24414062+   7  HPFS/NTFS
/dev/sda2            6376       38913   261361485    7  HPFS/NTFS
/dev/sda3            3040        4256     9765888   83  Linux
/dev/sda4            4256        6375    17026049    5  Extendida
/dev/sda5            6127        6375     1999872   82  Linux swap / Solaris
/dev/sda6            4256        6126    15025152   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

cualquier cosa que necesites pregunta nomas...

saludos...

---

### Post by marcelo_bur on 2010-11-15
> **granjero said:**
> hola, una pregunta, el disco e:\ ubuntu lo monta al iniciar?

porque si no lo monta no lo vas a ver....

además ubuntu no usa letras para los distintos HD sino que los monta como directorios del sistema de archivos, por lo que seguramente tu disco e:\ se encuentre montado en /media (si es que lo monta al inicio) o en /mnt no estoy seguro de como es la instalación por wubi....

contanos más sobre como están tus discos duros en ubuntu así te podemos ayudar....

copiá la salida del comando 

```
sudo fdisk -l
```


salud!


Hola. Yo actualmente estoy usando ubuntu 10.04 instalado dentro de XP con wubi. Funciona igual que si estuviese instalado en una particion, pero hay ciertas cosas que no ves. Voy a tratar de explicarme para evitar consusiones...

Yo tengo en dos particiones que desde Windows se ven como C e I. Dentro de C tengo instalado XP y dentro de este Ubuntu 10.04.

Ahora bien, si estoy XP puedo ver el contenido de C y de I, pero no veo los archivos de Ubuntu 10.04

Pero si abro Ubuntu 10.04 (instalado dentro de XP con Wubi) veo todo el contenido de Ubuntu, como es lógico, mas el contenido de I que, también como es lógico, en Ubuntu aparece con otra identificacion dentro de /media, pero no veo nada de lo que hay guardado en XP (C)

Bueno, no estoy seguro si supe explicarme ni si sirve para algo el comentario, tal vez si.

Saludos

---

### Post by granjero on 2010-11-15
mirá juakel, yo tampoco soy muy experimentado en este asunto pero por lo que se ve en la salida de ese comando tenes un disco de 320GB partido en varios pedazos....


ahora lo que hay que identificar es cuál es la partición que windows llama e:\ es winxp o win7?

imagino que es la /dev/sda2 porque /dev/sda1 y /dev/sda2 son las únicas formateadas en NTFS y la sda1 debe ser la sel sistema....

también creo que puede ayudar que postees tu fstab

que es el archivo que le indica a tu SO que particiones montar y donde.

fijate de abrir el archivo /etc/fstab y copiar acá el contenido.

creo que ese es el camino para ir viendo cual es cual partición.

salud!

---

### Post by samuel.fdez.8 on 2011-04-06
Hola, creo que aparentemente tengo la solución al problema.

En realidad, el problema no es tal. Yo también intenté cambiar la carpeta de destino de jDownloader, y me encontré con que no podía salir más allá de ( / ). Bien, busqué qué ruta tenía mi Disco Duro Externo, que se hallaba montado en /media. Efectivamente, busqué esa carpeta y ahí estaba mi Disco Duro Externo. Simplemente, busqué esa carpeta en ( / ) y seleccioné el lugar deseado. 
Espero que sea útil.
Un saludo.

---


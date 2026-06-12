---
title: "Copiar partición Linux a otro disco sin perder permisos"
date: 2009-05-21
forum: Software
---

### Post by moreback on 2009-05-21
Necesitaba trasladar mi instalación de Ubuntu a un disco nuevo y no quería reinstalar todo (ya me había aburrido haciéndolo con el Vista jaja). Teniendo una sola partición raíz, pregunté por alguna secuencia de comandos que me permitiera restaurar mi instalación de Ubuntu.

Existen dos métodos, uno es con el comando **dd** y el otro usando **rsync**. El primero lo explica **gmunioz**:

[quote=gmunioz]
El comando dd, es el que permite realizar esa y muchas otras tareas. El procedimiento sería: 
 
Suponiendo que: 
 
El disco rígido A  es el fuente  a clonar 
El disco rígido B es el destino, donde se clonara el A 
El disco rígido A debe estar  como maestro o principal (segun sea pata o sata), 
El disco rígido B como esclavo o secundario (segun sea pata o sata) 
 
Es decir que el disco rígido A será sda y el disco rígido B será sdb. 
 
Una vez configurados los discos, se reinicia el sistema con un  LiveCD. Terminada la carga de la distribución preferida (ubuntu), se abre una  una consola. Para ello se pulsa Aplicaciones - Accesorios - Terminal. Previo constatar que los discos no estan montados, en caso de estar montados se los desmonta, se ejecuta en la consola: 
 
```
sudo dd if=/dev/sda of=/dev/sdb bs=1M
```**¿qué hacen esta orden y sus parámetros?**
 
Sugerencia, siempre que se trabaje con sudo, antes de ejecutar, averiguar que hace la orden, con la orden en consola:  man comando 
 
**dd** = es un comando que copia byte a byte 
**if=** indica el dispositivo desde donde se copiara, origen 
**of=** indica el  dispositivo hacia donde se copiara, destino 
**bs=1M** indica que el copiado se efectuará mega a mega 
 
Si este procedimiento, mas difícil de detallar que de ejecutar, no te satisface o eres un usuario muy winuser, existe una aplicación gráfica, clonezilla para efectuar este procedimiento en forma gráfica.[/quote]

A todas luces se veía que el comando dd era mi salvación, pero cuando recibí la respuesta yo ya había particionado mi disco y me había hecho una partición nueva con ext4. En este caso el comando dd me habría copiado todo incluyendo el sistema de archivos (que era ext3).

Como no quería esto me decidí a leer la página de manual de rsync(1) para poder entender el segundo método con **rsync**:

El comando que me iba a servir tenía de la siguiente forma.
```
**sudo rsync -va -H -A -X /mnt/VIEJO/ /mnt/NUEVO**
```(Ojo con la barra inclinada después de VIEJO ya que eso hace que rsync *copie los archivos que están dentro de ese directorio sin incluir a éste*).

Después tuve que editar el **/etc/fstab** usando el UUID de mi nueva partición raíz (el que se puede ver haciendo clic en el icono de la partición montada en el escritorio, seleccionando Propiedades y luego la pestaña Volume) y reasignar la partición de la swap. 
 
También tuve que editar el **/boot/grub/menu.lst** para cambiar los UUID y la partición raíz, la que cambió a (hd0,6). 
 
Lo más complicado fue instalar el Grub en el MBR, pero revisando la ayuda del Super Grub Disk, encontré la solución: Primero en un terminal escribimos 
```
sudo grub
```para entrar a la consola del Grub y luego tipeamos los siguientes comandos: 
 ```
device (hd3) /dev/sda   # aqui es donde estaba ubicado mi disco nuevo 
root (hd3,6)            # se indica la particion donde se encuentra el directorio /boot 
setup (hd3)             # se instala grub en el mbr 
quit
```Finalmente se reinicia y se disfruta.
 
*PD: Este en un resumen del antiguo post [http://foros.ubuntu-cl.org/viewtopic.php?t=8392](http://foros.ubuntu-cl.org/viewtopic.php?t=8392)*

---

### Post by vargux on 2009-05-22
Excelente método !!!

Quizás también puede servir esto:

1.- _*[http://sigt.net/archivo/consejos-al-migrar-gnulinux-a-otro-disco-duro.xhtml](http://sigt.net/archivo/consejos-al-migrar-gnulinux-a-otro-disco-duro.xhtml)*_

2.- Un poco vieja, pero de algo sirve: *_[http://www.videosinformatica.es/biblioteca/doc/articulos/clonar_partimage.pdf](http://www.videosinformatica.es/biblioteca/doc/articulos/clonar_partimage.pdf)_*

Saludos...

---


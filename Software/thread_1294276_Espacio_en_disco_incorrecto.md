---
title: "Espacio en disco incorrecto"
date: 2009-10-18
forum: Software
---

### Post by VTCop on 2009-10-18
Hola chicos, tengo un problema con mi Ubuntu Inteprid.

El caso es que mi disco es de 80GB, y lo uso 100% para ubuntu, pero no se por qué ahora me dice que el sistema de archivo (/) es de sólo 6,1GB y que sólo me queda 1,4GB libres !!!!

He creado el fichero /forcdfsck para que haga un chequeo del disco en el inicio, pero nada, sigue informándome mal del tamaño del disco

¿qué puedo hacer? Creo que esto ocurrió apartir de que airodump-ng dejara el sistema colgado.

```
tommy@Lenovo:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4cd723ce-2619-4bd1-897e-9eb0744ad546 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=54c90f19-dd14-436d-8c60-4de005dcb76e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tommy@Lenovo:~$ 


```

---

### Post by Mauro22 on 2009-10-18
Postea la salida de:

```
sudo fdisk -l
```

es ele minuscula no un 1 ni una i

---

### Post by EnriqueK on 2009-10-18
Es posible que tengas la papekera de /root llena, esto ocurre cuando se intenta borrar como administrador en forma gráfica usando **sudo nautilus**, probá con ejecutar 
```
sudo rm -Rf /root/.local/share/Trash/files/*
sudo rm -Rf /root/.local/share/Trash/info/*
```

---

### Post by VTCop on 2009-10-20
No, ese no es el problema. Con gparted me muestra que la partición de intercambio tiene 65GB, mientras que la del sistema de ficheros sólo tiene 6.1GB :confused:

La única explicación que se me ocurre es que a la hora de instalar Ubuntu particioné el disco de ese modo, pero luego seleccioné equivocadamente el uso de cada partición, y claro, no me había dado cuenta hasta ahora que me ha hecho falta el espacio.

Vamos, que no es ningún problema en realidad, sino que estoy un poco atontao

Gracias

---

### Post by guidito73 on 2009-10-20
Ok, no hay problema. Intenta grabar [GParted](http://gparted.sourceforge.net/) en un CD, lo corres como LiveCD (booteando).

Esta utilidad te permite manipular tus particiones, formatear, etc. Cuidado que podes mandar alguna macana grande. Aparentemente, tenés una partición de intercambio DEMASIADO grande. Reduciéndola y pasando el espacio libre a tu / o /home (si lo tenés) debería ser suficiente.

Fijate que muestra ahí y de última consultas nuevamente por acá.

---

### Post by VTCop on 2009-10-20
Efectivamente así es como solucioné el problema. Arranque desde el LiveCD de Ubuntu Inteprid y utilicé el gestor de particiones para reducir la partición de swap, de 61GB a 7GB y luego extendí la partición del sistema de ficheros (EXT3) para que pasase de 6,1GB a 62GB.

Tenía los ... de corbata, porque no me fíaba mucho de tocar la partición en la que tengo el sistema de ficheros, pero todo funcionó ok, cero problemas,.

---

### Post by guidito73 on 2009-10-20
Genial entonces.

Lo único, 7 Gb de Swap es demasiado. Usá el doble de RAM que tenés, y si tenés más de 1 Gb de RAM, le pones lo mismo que tenes de RAM. (512 = 1 GB. 1 GB = 1GB, 2 GB = 2 GB, etc)

---

### Post by VTCop on 2009-10-21
Gracias por la recomendación. En realidad tengo 3GB de RAM, y seguí la regla del doble, sin restricciones :)

---

### Post by adrix000 on 2011-11-30
> **EnriqueK said:**
> Es posible que tengas la papekera de /root llena, esto ocurre cuando se intenta borrar como administrador en forma gráfica usando **sudo nautilus**, probá con ejecutar 
```
sudo rm -Rf /root/.local/share/Trash/files/*
sudo rm -Rf /root/.local/share/Trash/info/*
```

Perfecto!! Muchas gracias, a mi esto me sirvio muchisimo!
En mi caso estaba creando una imagen con Remastersys, y me daba error porque el tamaño de la imagen superaba el maximo de un DVD. Sin embargo el "Analizador de disco duro" me daba 4GB de espacio ocupado. Resulta que en la papelera del root tenia mas de 25GB :P jajaja
En fin, me salvaron

Saludos y gracias nuevamente

---


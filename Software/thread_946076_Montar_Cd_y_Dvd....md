---
title: "Montar Cd y Dvd..."
date: 2008-10-13
forum: Software
---

### Post by NorreJa! on 2008-10-13
Hola gente, no puedo montar ni el cd ni el dvd. He intentado con varias cosas que he leido por la web pero nada resulto.

aqui les dejo el fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=9d109a4e-417d-4f7d-8463-4895be3a5d76 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdc2
UUID=E1D4-6258  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/hdc4
UUID=46576c1b-929c-4406-a454-f5dcab10284f none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0




intente cambiar el noauto por auto de hdb y hdd pero cuando quiero modificar los cambios me dice que no tengo permisos, siendo que soy el admin.

El "disco C" de windows y los pendrives me los monta bien.

Gracias!

---

### Post by juanman on 2008-10-13
Hola, parece q tenes 2 lectoras de cd/dvd... En las 2 tenes problemas? Proba desde la consola con:
```
sudo mount /dev/hdb
```

Te tira algun error? Cual?


Sino proba editando el fstab. Para editarlo con permisos escribi en consola 
```
gksu gedit /etc/fstab
```

Y cambia /dev/hdb por /dev/scd0 y /dev/hdd por /dev/scd1

Guarda y sali...

Proba en consola con ```
sudo mount /dev/scd0
```


La opcion noauto es para q no se monte el disco apenas inicia el sistema (mas exactamente cuando se ejecuta mount -a, q es llamada al inicio). Es recomendada dejarla para discos extraibles (cd, disketts, pendrives, etc)

Conta como te fue...

---

### Post by NorreJa! on 2008-10-13
Modifique el fstab como me dijiste, y en la consola, me sale esto:

carlos@Multivac:~$ gksu gedit /etc/fstab
carlos@Multivac:~$ sudo mount /dev/scd0
mount: No se ha encontrado el medio
carlos@Multivac:~$ sudo mount /dev/scd1
mount: el dispositivo especial /dev/scd1 no existe


Gracias por la ayuda!

---

### Post by faktorqm on 2008-10-14
Pone un cd/dvd en alguna de las lectoras y proba:

```
sudo mount /dev/hdb /media/cdrom0 -t iso9660 -o user,noauto,exec,utf8
```

o en si es la otra:

```
sudo mount /dev/hdc /media/cdrom1 -t iso9660 -o user,noauto,exec,utf8
```

Salu2!

---

### Post by NorreJa! on 2008-10-17
No funcionó, saben que, mejor voy a tratar de conectar los discos al IDE1 e IDE2 "normalmente"

el rigido como master en ide1, el cd/dvd como slave y el otro en el ide 2.

Quizas, quizas...

Cualquier cosa chiflo...

Gracias!

---


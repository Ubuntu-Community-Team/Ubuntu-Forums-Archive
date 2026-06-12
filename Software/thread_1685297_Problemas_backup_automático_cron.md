---
title: "Problemas backup automático cron"
date: 2011-02-10
forum: Software
---

### Post by granjero on 2011-02-10
Hola. Ando con algunos problemas al tratar de automatizar un backup de un server ubuntu 10.04

Son dos bakups los que tengo que hacer.

el primero y más pesado son todos los datos del server.
el segundo y menos voluminoso es la base de datos de un soft

Primero les dejo crontab:

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
45 5 * * *	root	copiarcuotas.sh
* 1 * * 2,3,4,4,6	root	backup-datos.sh
* 6 * * 2,3,4,4,6	root	backup-lapa.sh

#

```

primer script backup-datos.sh

```
#!/bin/bash
tar -czf /media/500Gb/BACKUPS/datos-"$(date +%Y-%m-%d)".tar.gz /home/isec/SERVER

```

segundo script backup-datos.sh

```
tar -czf /media/500Gb/BACKUPS/datos-"$(date +%Y-%m-%d--%H:%M:%S)"hs.tar.gz /home/isec/SERVER

```


El primer problema que tuve es que los bakups de la primera semana salieron corruptos todos en el mismo punto. Creo que era porque no terminaba de hacerlo y cron mandaba a hacer el otro bakup. Ahora deje a cron que arranque el bakup grande a la 1.00am y el otro a las 6.00am

El segundo problema que tuve fue que anoche le agregué más parametros a date, como muestra el segundo script y me llenó el disco rigido de bakups.

les dejo el ls que hice hoy a la mañana.

```
total 374G
-rw-r--r-- 1 root root 8,6G 2011-01-29 09:21 datos-2011-01-29.tar.gz
-rw-r--r-- 1 root root 8,9G 2011-02-01 10:28 datos-2011-02-01.tar.gz
-rw-r--r-- 1 root root 9,1G 2011-02-02 09:47 datos-2011-02-02.tar.gz
-rw-r--r-- 1 root root 8,8G 2011-02-03 09:11 datos-2011-02-03.tar.gz
-rw-r--r-- 1 root root  18G 2011-02-05 13:03 datos-2011-02-05.tar.gz
-rw-r--r-- 1 root root  12G 2011-02-08 13:02 datos-2011-02-08.tar.gz
-rw-r--r-- 1 root root  12G 2011-02-09 14:03 datos-2011-02-09.tar.gz
-rw-r--r-- 1 root root 7,3G 2011-02-10 04:37 datos-2011-02-10--01:00:01hs.tar.gz
-rw-r--r-- 1 root root 7,1G 2011-02-10 04:37 datos-2011-02-10--01:01:01hs.tar.gz
-rw-r--r-- 1 root root 6,8G 2011-02-10 04:37 datos-2011-02-10--01:02:02hs.tar.gz
-rw-r--r-- 1 root root 6,5G 2011-02-10 04:37 datos-2011-02-10--01:03:02hs.tar.gz
-rw-r--r-- 1 root root 6,3G 2011-02-10 04:37 datos-2011-02-10--01:04:02hs.tar.gz
-rw-r--r-- 1 root root 6,3G 2011-02-10 04:37 datos-2011-02-10--01:05:02hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-10 04:37 datos-2011-02-10--01:06:02hs.tar.gz
-rw-r--r-- 1 root root 6,1G 2011-02-10 04:37 datos-2011-02-10--01:07:03hs.tar.gz
-rw-r--r-- 1 root root 5,9G 2011-02-10 04:37 datos-2011-02-10--01:08:03hs.tar.gz
-rw-r--r-- 1 root root 5,8G 2011-02-10 04:37 datos-2011-02-10--01:09:04hs.tar.gz
-rw-r--r-- 1 root root 5,8G 2011-02-10 04:37 datos-2011-02-10--01:10:03hs.tar.gz
-rw-r--r-- 1 root root 5,7G 2011-02-10 04:37 datos-2011-02-10--01:11:04hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-10 04:37 datos-2011-02-10--01:12:04hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-10 04:37 datos-2011-02-10--01:13:04hs.tar.gz
-rw-r--r-- 1 root root 5,1G 2011-02-10 04:37 datos-2011-02-10--01:14:04hs.tar.gz
-rw-r--r-- 1 root root 5,2G 2011-02-10 04:37 datos-2011-02-10--01:15:05hs.tar.gz
-rw-r--r-- 1 root root 5,0G 2011-02-10 04:37 datos-2011-02-10--01:16:05hs.tar.gz
-rw-r--r-- 1 root root 5,0G 2011-02-10 04:37 datos-2011-02-10--01:17:11hs.tar.gz
-rw-r--r-- 1 root root 4,8G 2011-02-10 04:37 datos-2011-02-10--01:18:04hs.tar.gz
-rw-r--r-- 1 root root 4,8G 2011-02-10 04:37 datos-2011-02-10--01:19:05hs.tar.gz
-rw-r--r-- 1 root root 4,8G 2011-02-10 04:37 datos-2011-02-10--01:20:04hs.tar.gz
-rw-r--r-- 1 root root 4,8G 2011-02-10 04:37 datos-2011-02-10--01:21:04hs.tar.gz
-rw-r--r-- 1 root root 4,8G 2011-02-10 04:37 datos-2011-02-10--01:22:05hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:23:04hs.tar.gz
-rw-r--r-- 1 root root 4,8G 2011-02-10 04:37 datos-2011-02-10--01:24:05hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:25:05hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:26:07hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:27:06hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:28:07hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:29:06hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:30:07hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:31:07hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:32:07hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:33:07hs.tar.gz
-rw-r--r-- 1 root root 4,7G 2011-02-10 04:37 datos-2011-02-10--01:34:07hs.tar.gz
-rw-r--r-- 1 root root 4,5G 2011-02-10 04:37 datos-2011-02-10--01:35:09hs.tar.gz
-rw-r--r-- 1 root root 4,5G 2011-02-10 04:37 datos-2011-02-10--01:36:07hs.tar.gz
-rw-r--r-- 1 root root 4,4G 2011-02-10 04:37 datos-2011-02-10--01:37:10hs.tar.gz
-rw-r--r-- 1 root root 4,5G 2011-02-10 04:37 datos-2011-02-10--01:38:08hs.tar.gz
-rw-r--r-- 1 root root 4,5G 2011-02-10 04:37 datos-2011-02-10--01:39:11hs.tar.gz
-rw-r--r-- 1 root root 4,4G 2011-02-10 04:37 datos-2011-02-10--01:40:07hs.tar.gz
-rw-r--r-- 1 root root 4,5G 2011-02-10 04:37 datos-2011-02-10--01:41:08hs.tar.gz
-rw-r--r-- 1 root root 4,5G 2011-02-10 04:37 datos-2011-02-10--01:42:09hs.tar.gz
-rw-r--r-- 1 root root 4,4G 2011-02-10 04:37 datos-2011-02-10--01:43:08hs.tar.gz
-rw-r--r-- 1 root root 4,4G 2011-02-10 04:37 datos-2011-02-10--01:44:08hs.tar.gz
-rw-r--r-- 1 root root 4,3G 2011-02-10 04:37 datos-2011-02-10--01:45:08hs.tar.gz
-rw-r--r-- 1 root root 4,3G 2011-02-10 04:37 datos-2011-02-10--01:46:09hs.tar.gz
-rw-r--r-- 1 root root 4,4G 2011-02-10 04:37 datos-2011-02-10--01:47:09hs.tar.gz
-rw-r--r-- 1 root root 4,3G 2011-02-10 04:37 datos-2011-02-10--01:48:11hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:49:10hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:50:11hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:51:09hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:52:11hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:53:12hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:54:11hs.tar.gz
-rw-r--r-- 1 root root 4,1G 2011-02-10 04:37 datos-2011-02-10--01:55:11hs.tar.gz
-rw-r--r-- 1 root root 4,2G 2011-02-10 04:37 datos-2011-02-10--01:56:08hs.tar.gz
-rw-r--r-- 1 root root 4,1G 2011-02-10 04:37 datos-2011-02-10--01:57:11hs.tar.gz
-rw-r--r-- 1 root root 4,0G 2011-02-10 04:37 datos-2011-02-10--01:58:11hs.tar.gz
-rw-r--r-- 1 root root 4,0G 2011-02-10 04:37 datos-2011-02-10--01:59:12hs.tar.gz
-rw-r--r-- 1 root root 843M 2011-01-29 07:16 lapa-2011-01-29.tar.gz
-rw-r--r-- 1 root root 843M 2011-02-01 07:16 lapa-2011-02-01.tar.gz
-rw-r--r-- 1 root root 843M 2011-02-02 07:16 lapa-2011-02-02.tar.gz
-rw-r--r-- 1 root root 843M 2011-02-03 07:14 lapa-2011-02-03.tar.gz
-rw-r--r-- 1 root root 886M 2011-02-05 05:39 lapa-2011-02-05.tar.gz
-rw-r--r-- 1 root root 886M 2011-02-08 05:26 lapa-2011-02-08.tar.gz
-rw-r--r-- 1 root root 886M 2011-02-09 02:32 lapa-2011-02-09.tar.gz
-rw-r--r-- 1 root root 436K 2011-02-10 06:59 lapa-2011-02-10.tar.gz
-rw-r--r-- 1 root root    0 2011-02-10 11:04 ls.txt
-rw------- 1 root root  184 2011-02-09 14:31 nohup.out
drwxr-xr-x 2 root root 4,0K 2011-02-10 10:50 temp
```


si ejecuto el comando del script a mano desde una consola por ssh con 
 nohup y & al final el bakup lo hace de pelos.




acepto tips sugerencias y demás ayudas!

salud!

---

### Post by mama21mama on 2011-02-10
2,3,**4**,4,6

como que se repite el mismo día.
y así hará backup a cada minuto.

mas info de [cron]("http://doc.ubuntu-es.org/Cron")

---

### Post by granjero on 2011-02-11
UHHH no puedo creer que se me paso eso!

 hoy no lo hizo el bakup por ejemplo

ahora arreglo eso!

gracias mama21mama!


salud!

---

### Post by juancarlospaco on 2011-02-11
```
#!/bin/bash
# -*- coding: utf-8 -*-
#
# Un par de variables para facilitar las cosas. 
# Se puede probar si estan OK con: echo $variable, ejemplo: echo $milog
milog=/media/500Gb/BACKUPS/log-$(date +%Y-%m-%d--%H:%M).txt
mitar=/media/500Gb/BACKUPS/datos-$(date +%Y-%m-%d--%H:%M).tar.gz
mimd5=/media/500Gb/BACKUPS/md5-$(date +%Y-%m-%d--%H:%M).txt
#
# Fecha, hora y espacio libre en el medio de backup, quedan registradas en el log.
echo " Comienza backup" > $milog
date +%Y-%m-%d_%H:%M:%S >> $milog
df -h /media/500Gb/BACKUPS/ >> $milog
#
tar --totals -czf $mitar /home/isec/SERVER >> $milog
#
sleep 3
md5sum $mitar >> $mimd5
# se puede chequear integridad luego con: md5sum --check $mimd5
#
date +%Y-%m-%d_%H:%M:%S >> $milog
echo " Fin backup" >> $milog

```

Se asume que tenes el NTP corriendo homogeneo en toda la red.

Como no vamos a estar mirando la Terminal no tiene sentido usar " tee " en la redireccion de la salida al log.

El " #-*- coding: utf-8 -*- " es por si algun dia por error o casualidad alguna Ñ o á&#263;é&#324;tó pasa por nuestro script.

MD5Sum asegura siempre la integridad de nuestro archivo de backup para saber si esta sano o no.

Revisalo, probalo, pregunta... creo que para tus necesidades es mas que suficiente.

*Se podria hacer que te mande el log por mail al terminar, pero eso ya es otro cuentito.*

---

### Post by granjero on 2011-02-14
hola nuevamente.

Gracias mama21mama y JuanCarlosPaco por las ayudas.

el fin de semana volvió a enloquecer el bakup y me lleno el HD de bakup con muchos pedazos de tar. les dejo el ls -lh que hice el sábado al mediodía!

```
total 454G
-rw-r--r-- 1 root root 8,6G 2011-01-29 09:21 datos-2011-01-29.tar.gz
-rw-r--r-- 1 root root 8,9G 2011-02-01 10:28 datos-2011-02-01.tar.gz
-rw-r--r-- 1 root root 9,1G 2011-02-02 09:47 datos-2011-02-02.tar.gz
-rw-r--r-- 1 root root 8,8G 2011-02-03 09:11 datos-2011-02-03.tar.gz
-rw-r--r-- 1 root root  18G 2011-02-05 13:03 datos-2011-02-05.tar.gz
-rw-r--r-- 1 root root  12G 2011-02-08 13:02 datos-2011-02-08.tar.gz
-rw-r--r-- 1 root root  12G 2011-02-09 14:03 datos-2011-02-09.tar.gz
-rw-r--r-- 1 root root  12G 2011-02-10 11:28 datos-2011-02-10--11:06:40hs.tar.gz
-rw-r--r-- 1 root root  12G 2011-02-11 09:59 datos-2011-02-11--09:38:11hs.tar.gz
-rw-r--r-- 1 root root 7,9G 2011-02-12 05:27 datos-2011-02-12--01:00:01hs.tar.gz
-rw-r--r-- 1 root root 7,9G 2011-02-12 05:27 datos-2011-02-12--01:01:01hs.tar.gz
-rw-r--r-- 1 root root 7,6G 2011-02-12 05:27 datos-2011-02-12--01:02:01hs.tar.gz
-rw-r--r-- 1 root root 7,4G 2011-02-12 05:27 datos-2011-02-12--01:03:01hs.tar.gz
-rw-r--r-- 1 root root 7,2G 2011-02-12 05:27 datos-2011-02-12--01:04:02hs.tar.gz
-rw-r--r-- 1 root root 7,2G 2011-02-12 05:27 datos-2011-02-12--01:05:02hs.tar.gz
-rw-r--r-- 1 root root 7,1G 2011-02-12 05:27 datos-2011-02-12--01:06:02hs.tar.gz
-rw-r--r-- 1 root root 7,1G 2011-02-12 05:27 datos-2011-02-12--01:07:03hs.tar.gz
-rw-r--r-- 1 root root 7,1G 2011-02-12 05:27 datos-2011-02-12--01:08:02hs.tar.gz
-rw-r--r-- 1 root root 7,0G 2011-02-12 05:27 datos-2011-02-12--01:09:03hs.tar.gz
-rw-r--r-- 1 root root 7,0G 2011-02-12 05:27 datos-2011-02-12--01:10:03hs.tar.gz
-rw-r--r-- 1 root root 6,8G 2011-02-12 05:27 datos-2011-02-12--01:11:03hs.tar.gz
-rw-r--r-- 1 root root 6,8G 2011-02-12 05:27 datos-2011-02-12--01:12:04hs.tar.gz
-rw-r--r-- 1 root root 6,5G 2011-02-12 05:27 datos-2011-02-12--01:13:04hs.tar.gz
-rw-r--r-- 1 root root 6,5G 2011-02-12 05:27 datos-2011-02-12--01:14:04hs.tar.gz
-rw-r--r-- 1 root root 6,5G 2011-02-12 05:27 datos-2011-02-12--01:15:05hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:16:05hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:17:12hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:18:04hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:19:04hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:20:04hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:21:05hs.tar.gz
-rw-r--r-- 1 root root 6,2G 2011-02-12 05:27 datos-2011-02-12--01:22:05hs.tar.gz
-rw-r--r-- 1 root root 6,0G 2011-02-12 05:27 datos-2011-02-12--01:23:05hs.tar.gz
-rw-r--r-- 1 root root 6,1G 2011-02-12 05:27 datos-2011-02-12--01:24:06hs.tar.gz
-rw-r--r-- 1 root root 6,0G 2011-02-12 05:27 datos-2011-02-12--01:25:05hs.tar.gz
-rw-r--r-- 1 root root 5,7G 2011-02-12 05:27 datos-2011-02-12--01:26:06hs.tar.gz
-rw-r--r-- 1 root root 5,2G 2011-02-12 05:27 datos-2011-02-12--01:27:05hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:28:07hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:29:07hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:30:06hs.tar.gz
-rw-r--r-- 1 root root 5,2G 2011-02-12 05:27 datos-2011-02-12--01:31:07hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:32:05hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:33:08hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:34:09hs.tar.gz
-rw-r--r-- 1 root root 5,2G 2011-02-12 05:27 datos-2011-02-12--01:35:08hs.tar.gz
-rw-r--r-- 1 root root 5,1G 2011-02-12 05:27 datos-2011-02-12--01:36:10hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:37:08hs.tar.gz
-rw-r--r-- 1 root root 5,1G 2011-02-12 05:27 datos-2011-02-12--01:38:11hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:39:11hs.tar.gz
-rw-r--r-- 1 root root 5,1G 2011-02-12 05:27 datos-2011-02-12--01:40:07hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:41:08hs.tar.gz
-rw-r--r-- 1 root root 5,2G 2011-02-12 05:27 datos-2011-02-12--01:42:07hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:43:07hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:44:07hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:45:08hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:46:07hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:47:08hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:48:06hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:49:06hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:50:07hs.tar.gz
-rw-r--r-- 1 root root 5,0G 2011-02-12 05:27 datos-2011-02-12--01:51:08hs.tar.gz
-rw-r--r-- 1 root root 5,0G 2011-02-12 05:27 datos-2011-02-12--01:52:08hs.tar.gz
-rw-r--r-- 1 root root 5,3G 2011-02-12 05:27 datos-2011-02-12--01:53:08hs.tar.gz
-rw-r--r-- 1 root root 5,1G 2011-02-12 05:27 datos-2011-02-12--01:54:09hs.tar.gz
-rw-r--r-- 1 root root 5,2G 2011-02-12 05:27 datos-2011-02-12--01:55:11hs.tar.gz
-rw-r--r-- 1 root root 5,0G 2011-02-12 05:27 datos-2011-02-12--01:56:11hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:57:09hs.tar.gz
-rw-r--r-- 1 root root 5,4G 2011-02-12 05:27 datos-2011-02-12--01:58:10hs.tar.gz
-rw-r--r-- 1 root root 843M 2011-01-29 07:16 lapa-2011-01-29.tar.gz
-rw-r--r-- 1 root root 843M 2011-02-01 07:16 lapa-2011-02-01.tar.gz
-rw-r--r-- 1 root root 843M 2011-02-02 07:16 lapa-2011-02-02.tar.gz
-rw-r--r-- 1 root root 843M 2011-02-03 07:14 lapa-2011-02-03.tar.gz
-rw-r--r-- 1 root root 886M 2011-02-05 05:39 lapa-2011-02-05.tar.gz
-rw-r--r-- 1 root root 886M 2011-02-08 05:26 lapa-2011-02-08.tar.gz
-rw-r--r-- 1 root root 886M 2011-02-09 02:32 lapa-2011-02-09.tar.gz
-rw-r--r-- 1 root root 889M 2011-02-10 19:45 lapa-2011-02-10.tar.gz
-rw-r--r-- 1 root root 889M 2011-02-11 10:03 lapa-2011-02-11.tar.gz
-rw-r--r-- 1 root root  80K 2011-02-12 06:59 lapa-2011-02-12.tar.gz
-rw-r--r-- 1 root root    0 2011-02-12 19:35 ls2.txt
-rw-r--r-- 1 root root 6,0K 2011-02-10 11:04 ls.txt
-rw------- 1 root root  368 2011-02-11 10:01 nohup.out
drwxr-xr-x 2 root root 4,0K 2011-02-10 19:38 temp

```

Ya arreglé el error de tener el día 4 repetido dos veces.

¿Por qué enloquece de esa manera al hacer bakup con cron? 

si ejecuto el script manualmente anda de maraviilas, lo mismo que si escribo la línea que hace el script. Pero con cron no para de hacer agua.

help!

](*,)](*,)](*,)

---

### Post by mama21mama on 2011-02-14
> m h dom mon dow user	command
* 1 * * 2,3,4,6	root	backup-datos.sh

le seguís dando a cada minuto.
podes decir en formato letras cada cuento quieres el cron?

---

### Post by juancarlospaco on 2011-02-14
El error esta en el Cron.

Postea lo del Cron tambien a ver que acontece...

PD: pusiste para que cree los " log " a ver si no tira nada raro ?

---

### Post by granjero on 2011-02-15
mama21mama, yo quiero que todos los martes, miércoles, jueves, viernes y sábados a la 1.00am haga el bakup de datos. Los mismos dias a las 6.00am haga el otro bakup.

Juan Carlos Todavía no probé el tema de los logs.


> root@ServerDatos:/media/500Gb/BACKUPS# cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
45 5 * * *	root	copiarcuotas.sh
* 1 * * 2,3,4,5,6	root	backup-datos.sh
* 6 * * 2,3,4,5,6	root	backup-lapa.sh

#
root@ServerDatos:/media/500Gb/BACKUPS# 

Gracias por todo!

---

### Post by granjero on 2011-02-15
ya cambié cron 

quedó así:

```
root@ServerDatos:/media/500Gb/BACKUPS# cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
45 5 * * *	root	copiarcuotas.sh
01 1 * * 2,3,4,5,6	root	backup-datos.sh
01 6 * * 2,3,4,5,6	root	backup-lapa.sh

#
root@ServerDatos:/media/500Gb/BACKUPS# 

```

era eso?

salud!

---

### Post by granjero on 2011-02-16
Hola, Con el último crontab anoche hizo los bakups a la perfección.
Cuando tenga un rato voy a meter mano a los scripts y hacer que genere los logs. 

Muchas gracias!

Salud!

---

### Post by granjero on 2011-02-16
me quedé maquinando con el tema del log y al final hice un script basado en el que posteó Juancarlospaco.

se los paso:

```
#!/bin/bash
# -*- coding: utf-8 -*-
#
# Un par de variables para facilitar las cosas. 
# Se puede probar si estan OK con: echo $variable, ejemplo: echo $log
log=/media/500Gb/BACKUPS/logs/datos-log
bakup=/media/500Gb/BACKUPS/datos/datos-backup-$(date +%Y-%m-%d_%H:%M:%S)hs.tar.gz
#
# Fecha, hora y espacio libre en el medio de backup, quedan registradas en el log.
echo "             ." >> $log
echo "               ." >> $log
echo "                 ." >> $log
echo "                   ." >> $log
echo " xxxxxxxxxxxxxxxxxxxxxxxxxx" >> $log
echo "  I N I C I A    B A K U P " >> $log
echo " xxxxxxxxxxxxxxxxxxxxxxxxxx" >> $log
echo " " >> $log
echo " FECHA DE INICIO:" >> $log
echo " " >> $log
date +%A-%F_%R:%S >> $log
echo " " >> $log
echo " CAPACIDAD DEL DISCO:" >> %log >> $log
echo " " >> $log
df -h /media/500Gb/BACKUPS/ >> $log
#el próximo es el comando que hace el bakup
#
tar --totals -czf $bakup /home/isec/SERVER >> $log
#
#deja registro del archivo
echo " " >> $log
echo " MD5SUM" >> $log
echo " " >> $log
md5sum $bakup >> $log
echo " " >> $log
echo " FECHA DE FIN:" >> $log
echo " " >> $log
date +%A-%F_%R:%S >> $log
echo " " >> $log
echo " -----------------------------------" >> $log
echo "  F I N    D E L    B A C K U P  ;-D" >> $log
echo " -----------------------------------" >> $log
#fin del script

```

Este en vez de hacer un log por cada bakup tiene un solo archivo de log y mete el resultado del md5dum en el mismo log.



salud!

---

### Post by granjero on 2011-02-19
Para cerrar con un moño les dejo el log que tiene unos días ya! 

```
cat /media/500Gb/BACKUPS/logs/datos-log 
             .
               .
                 .
                   .
 xxxxxxxxxxxxxxxxxxxxxxxxxx
  I N I C I A    B A K U P 
 xxxxxxxxxxxxxxxxxxxxxxxxxx
 
 FECHA DE INICIO:
 
jueves-2011-02-17_00:01:41
 
 CAPACIDAD DEL DISCO:
 
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sdb1             459G  139G  297G  32% /media/500Gb
 
 MD5SUM
 
91acf853622b6a732162145d0b702ae8  /media/500Gb/BACKUPS/datos/datos-backup-2011-02-17_00:01:41hs.tar.gz
 
 FECHA DE FIN:
 
jueves-2011-02-17_00:24:53
 
 -----------------------------------
  F I N    D E L    B A C K U P  ;-D
 -----------------------------------
             .
               .
                 .
                   .
 xxxxxxxxxxxxxxxxxxxxxxxxxx
  I N I C I A    B A K U P 
 xxxxxxxxxxxxxxxxxxxxxxxxxx
 
 FECHA DE INICIO:
 
Thursday-2011-02-17_01:01:01
 
 CAPACIDAD DEL DISCO:
 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  151G  285G  35% /media/500Gb
 
 MD5SUM
 
af7e13f619639e8d5deea5a223005a34  /media/500Gb/BACKUPS/datos/datos-backup-2011-02-17_01:01:01hs.tar.gz
 
 FECHA DE FIN:
 
Thursday-2011-02-17_01:24:06
 
 -----------------------------------
  F I N    D E L    B A C K U P  ;-D
 -----------------------------------
             .
               .
                 .
                   .
 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
  I N I C I A   B A K U P   D A T O S 
 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
 
 FECHA DE INICIO:
 
Friday-2011-02-18_01:01:01
 
 CAPACIDAD DEL DISCO:
 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  124G  313G  29% /media/500Gb
 
 MD5SUM
 
4c2d1d3ae6779e33170668c72b53b48a  /media/500Gb/BACKUPS/datos/datos-backup-2011-02-18_01:01:01hs.tar.gz
 
 FECHA DE FIN:
 
Friday-2011-02-18_01:24:11
 
 -----------------------------------
  F I N    D E L    B A C K U P  ;-D
 -----------------------------------
             .
               .
                 .
                   .
 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
  I N I C I A   B A K U P   D A T O S 
 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
 
 FECHA DE INICIO:
 
Saturday-2011-02-19_01:01:01
 
 CAPACIDAD DEL DISCO:
 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  136G  300G  32% /media/500Gb
 
 MD5SUM
 
727708271bd8f77892d705bb861cec2f  /media/500Gb/BACKUPS/datos/datos-backup-2011-02-19_01:01:01hs.tar.gz
 
 FECHA DE FIN:
 
Saturday-2011-02-19_01:24:15
 
 -----------------------------------
  F I N    D E L    B A C K U P  ;-D
 -----------------------------------

```


Lo úico raro es que me cambió el idioma del día. No es grave pero no se por qué. Creo que fue luego de un apt-get upgrade pero cuando tiro el comando en consola me da el resultado en español. RARO NO?

Salud!

---


---
title: "Backup de datos"
date: 2012-10-01
forum: Software
---

### Post by Fitomar on 2012-10-01
Buenas soy un poco nuevo en este mundo de Linux y necesito un poco de ayuda...

voy al grano...
Necesito realizar backup de una carpeta y su contenido alojada en una PC llamemos la PCservidor a otra PC llamemos la PCBackup.

Busque algun Soft que me ayude pero la mayoria es para realizar backup pero no remotamente, mi idea es que mi pcbackup se conecte via ssh o similar a mi PCserver y copie los datos o la carpeta a mi pcbackup, de forma automatica y en un horario determinado por mi.
Serian tan amables de ayudarme...
muchas gracias de antemano...
:)

---

### Post by 1clue on 2012-10-01
Hola,

Estoy tratando de ayudar a través de Google Translate así que por favor perdone cualquier error.

¿Los dos equipos que ejecutan algún tipo de Linux o Unix? La ayuda que dan es diferente dependiendo de si se utiliza Windows.

Si he entendido bien que usted está poniendo una copia de seguridad de PCservidor a una ubicación en PCBackup, y que PCservidor y PCBackup ambos existen en la misma red local.

¿La copia de seguridad debe ser un archivo comprimido zip o puede ser un literal duplicado de la carpeta original?

---

### Post by Fitomar on 2012-10-01
Gracias por la pronta respuesta. 

Efectivamente ambas se encuentran en la misma red, ambas son Linux Ubuntu. 

En cuanto a su ultima pregunta, con un duplicado del original me basta. :)
Muchas Gracias...

---

### Post by 1clue on 2012-10-01
Fitomar,

Aceptar que usted necesita servidor ssh que se ejecuta en el dispositivo remoto, y usted necesita un shell de línea de comandos.

Dejando a los directorios descomprimido tiene un acceso muy fácil, pero utiliza más espacio en el sistema de copia de seguridad.

Usted necesitará:
1. Una cuenta en PCServidor que tiene acceso de lectura a todo el contenido del directorio de copia de seguridad.
2. Una cuenta en PCBackup que ha leído y acceso de escritura al directorio de destino. Tiene mucho sentido para el usuario de copia de seguridad a ser especial sólo para copias de seguridad, y por la ubicación de destino para estar dentro del directorio principal del usuario. Voy a llamar a ese usuario backup_user

Yo creo que fuera la solución. Si usted tiene muchos directorios en muchos equipos, entonces usted necesita alguna manera de no perder de vista que las copias de seguridad de procedencia.

Entonces, ¿cómo haría esto, haría directorios en PCBackup así:

/ home / backup_user / backups / PCServidor / mi_directorio / donde mi_directorio es un nombre único que le dice lo que es este directorio. Esto le permite tener varios directorios de la copia de seguridad desde el mismo servidor, y varios servidores que tienen directorios de la copia de seguridad.

Hay dos maneras de hacer esto: Desde PCServidor o de PCBackup.

De PCServidor:

**scp-prd /ruta/al/mi_directorio  backup_user@PCBackup:/home/backup_user/backups/PCServidor/2012-10-01/**

De PCBackup:

**scp-prd usuario@PCServidor:/path/to/mi_directorio  /home/backup_user/backups/PCServidor/my_directory/2012-10-01/**

Gracias

---

### Post by Fitomar on 2012-10-01
Muchas gracias...

Lo probare a ver como me va, otra consulta mas..

Como puedo hacer para que esto lo haga de forma automatica es decir  en un dia y horario especifico.

Gracias

---

### Post by Fitomar on 2012-10-01
servbackup@servbackup-System-Product-Name:~$ scp -prd fito@192.168.1.126:/home/ticpy/backup  /home/servbackup/Backup/prueba 
fito@192.168.1.126's password: 
Presentacion.ppt                              100% 4096     4.0KB/s   00:00    
Mapa TX - Fibra Optica 08-2011 Model (1).pdf  100%  147KB 147.3KB/s   00:01    
Mapa TX - Fibra Optica 08-2011 Model (2).pdf  100%   57KB  56.5KB/s   00:00    
escuelas.qgs                                  100% 4096     4.0KB/s   00:00    
emslapcv1.pdf                                 100% 4096     4.0KB/s   00:00    
planillas2.sql                                100%  535KB 535.0KB/s   00:00    
Resumen primer parcial BD 3.docx              100%   13KB  13.3KB/s   00:00    
paraguaydb2.sql                               100% 4096     4.0KB/s   00:00    
PLANNACIONALDEMIGRACIONASWL230305.pdf         100%   64KB  64.0KB/s   00:00    
CAP+13+-+OPERADOR_RED_HAT_FEDORA.pdf          100%   28KB  27.8KB/s   00:00    
CAP_12~1.PDF                                  100%   13KB  12.5KB/s   00:00    
CAP+8-+OPERADOR_RED_HAT_FEDORA.pdf            100%   10KB   9.8KB/s   00:00    
CAP+3+-+OPERADOR_RED_HAT_FEDORA.pdf           100%   16KB  16.4KB/s   00:00    
Ejercitario_cap8_cap9.docx                    100% 4096     4.0KB/s   00:00    
CAP+4+-+OPERADOR_RED_HAT_FEDORA.pdf           100%   20KB  20.1KB/s   00:00    
Ejercitario_Linux.txt                         100% 4096     4.0KB/s   00:00    
ejercitario_10_linux.txt                      100%  140     0.1KB/s   00:00    
CAP+6+-+OPERADOR_RED_HAT_FEDORA.pdf           100%   33KB  32.7KB/s   00:01    
CAP+2+-+OPERADOR_RED_HAT_FEDORA.pdf           100%   37KB  37.3KB/s   00:00    
cursolinux.pdf                                100% 1520KB   1.5MB/s   00:01    
Ejercitario_CAP8.txt                          100%  427     0.4KB/s   00:00    
ejercicitarioCAP1al5.pdf                      100% 4096     4.0KB/s   00:00    
servbackup@servbackup-System-Product-Name:~$ 

Lo hice con una carpeta de prueba y funciona muy bien... ahora como puedo hacer para que no me pida Contraseña y que el proceso me lo haga en forma automatica en un dia y horario especifico..

Disculpe que pregunte mucho... pero realmente agradezco su ayuda =)

---

### Post by 1clue on 2012-10-01
Para una marca de tiempo: Tengo un guión que escribí lo que permite una marca de tiempo con lo que usted necesita delimitador. Yo lo llamo 'ts' para marca de tiempo pero que no se traducirá al español, creo.

Usted necesita este script para estar en su ruta de ejecución, uso / usr / local / bin

Yo lo uso así:
ts -:
****** 2012-10-01-03:22:46

El - es el delimitador que usé para la fecha, y: es el delimitador que utilicé para el tiempo.

Yo lo uso así:

echo "la fecha y hora es` ts - : `"
la fecha y la hora es 2012-10-01-15:25:03


/usr/local/bin/ts
```

#!/bin/bash
# Prints the current date using 2 specified delimiters, in ISO format.
# For example, 'ts - :' returns something like '2010-11-02-12:53:02'
date +%Y$1%m$1%d-%H$2%M$2%S

```

Para ejecutar esto en un horario que yo usaría chrontab. Puede ser de uso fácil manera de poner esto en marcha, pero yo uso la línea de comandos. Usted debe explorar que con 'crontab hombre "y volver a preguntar si necesita ayuda.

Gracias.

---


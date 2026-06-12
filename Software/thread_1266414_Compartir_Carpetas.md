---
title: "Compartir Carpetas"
date: 2009-09-14
forum: Software
---

### Post by doncentineo on 2009-09-14
Hola, sobre un Windows 2003 Server tengo cargada una una maquina vitual (VitualBox) y sobre ella a 

Ubuntu 8.10
El problema que tengo es q hace un tiempo un ex-compañero de oficina coloco una carpeta del Ubuntu 

como Compatida para poder verla desde windows \\IP_del_ubuntu\
Ahora necesito q esa carpeta ya no este compartida pero no logro de q mnera la compartio, NO utilizo 

Samba, tampoco utilizo la opcion de compartir carpeta q se encuentra al dar un clic derecho sobre la 

carpeta, tampoco utilizo la opcion de compartir carpetas que tiene el VitualBox; no se q otra opcion 

haya utilizado mi problema es q no encuentro como hacer para q esa carpeta ya no sea compartida.
Desde ya gracias por las sugerencias.

---

### Post by Hei Ku on 2009-09-14
si corres netstat en el ubuntu, que proceso te dice que esta escuchando en el port de SMB?

---

### Post by doncentineo on 2009-09-15
Al correr el netstat me muestra 5 procesos de los cuales 2 son del smbd, ninguno de los otros tres procesos estan ocupando los puertos del samba. Adjunto el resultado del netstat:

Conexiones activas de Internet (solo servidores)
Protocolo Recv-Q Send-Q Dirección Local Dirección Externa Estado       PID/Program name
tcp        0      0 127.0.0.1:8100          0.0.0.0:*               ESCUCHAR    4167/soffice.bin
tcp        0      0 0.0.0.0:139             0.0.0.0:*               ESCUCHAR    5867/smbd       
tcp        0      0 0.0.0.0:21              0.0.0.0:*               ESCUCHAR    6814/vsftpd     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               ESCUCHAR    4077/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               ESCUCHAR    5867/smbd

---

### Post by Hei Ku on 2009-09-15
Tenes corriendo, y escuchando samba. Seguro que no esta configurado para compartir esa carpeta?

---

### Post by doncentineo on 2009-09-16
Lo tengo a Samba instalado y configurado pero para otra carpeta. La carpeta q me esta generando problemas la compartieron antes de instalar samba.

Gracias.

---

### Post by guillermolisi on 2009-09-16
> **doncentineo said:**
> Lo tengo a Samba instalado y configurado pero para otra carpeta. La carpeta q me esta generando problemas la compartieron antes de instalar samba.

Gracias.
Hay un solo servidor Samba en esa red ?

Luego, podrias mostrarnos el contenido del archivo /etc/samba/smb.conf ?

---


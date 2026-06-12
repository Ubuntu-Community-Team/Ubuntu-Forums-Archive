---
title: "ayuda con debian"
date: 2010-02-02
forum: Software
---

### Post by santiago79 on 2010-02-02
hola gente tengo una consulta, empresa a laburar en un lugar y tiene un server con windows 2003 y 2 con debian tengo muchas preguntas respecto a eso pero por lo pronto necesito ayuda para configurar uno de los debian
la onda es asi:
el pibe que estaba antes me dejo esto 

"Roles y servicios que ofrece este servidor en la red local e internet:
Gateway de red. (NAT y Forwarding)
Mediante este equipo los equipos de la red logran ‘conectarse’ a Internet, a todos los protocolos (ftp, ftps, smtp, pop3, etc.)  excepto http"

la idea mía es armar una pc backup para esta ya la tengo lista solo me falta saber como se configura eso
sin entorno gráfico y con la menor cantidad de paquetes que se pueda ya que son medias viejitas las pc jeje
la pc tiene 2 placas de red.
muchas gracias de antemano

---

### Post by juancarlospaco on 2010-02-02
Lo que necesitas es copiar las carpetas de /etc de los servicios que presta el servidor,
ejemplo si da servicio de squid, copiar la carpeta /etc/squid/

eso teoricamente lo tiras en un Servo nuevo/VM de Lab y sale andando,
teniendo las mismas config de NIC obvio.

teoricamente son standard, o sea los /etc de Debian deberian andar igual en Ubuntu Server.

Recomiendo Ubuntu Server.
Recomiendo hacer VM de Lab.
Suscribite al USN.
Aprende de ETCKeeper.

:)

---

### Post by santiago79 on 2010-02-02
si pero la idea es poder configurarlo yo para por ejemplo se prende fuego la pc y poder hacerlo en otro hardware,
si tengo pensado probar con ubuntu server lo tengo que bajar  antes de irme lo voy a dejar bajando, instale debian en la pc que va a hacer esa función y durante la instalación me detecto las placas de red le puse no configurar red ahora y ahora desde ifconfig no me detecta las placas

---

### Post by juancarlospaco on 2010-02-02
*Por eso...*, 
hacete un backup de /etc, con eso tiras los archivos en el hardware nuevo y listo.

Esa es la gracia de tener las config en un archivo de texto plano legible,
no como en otros sistemas que quedan en un Registro en egipcio, y hay que hacer 180mil click.

Se me prende fuego la PC, 
agarro otra con la misma cantidad de placas de red,
ubuntu server, copio archivos al /etc desde mi backup, 
reinicio, Up'N'Running, a cobrar.

Documenta como estan hechas las configuraciones, abri los archivos de configuracion,
leelos, documentalos, ensaya recrearlos en una VM de Lab.

---

### Post by santiago79 on 2010-02-02
y esta medio complicado porque esa pc no tiene nada osea trabajo en ssh alguna manera de montarle un pendrive podria ser

---

### Post by juancarlospaco on 2010-02-02
**Lugares--->Conectar con el Servidor--->SSH**


Util tambien:
python -m SimpleHTTPServer

:)

---

### Post by santiago79 on 2010-02-02
me estoy expresando mal, yo estoy en una pc con windows xp y manejo los servidores de debian con putty

---

### Post by juancarlospaco on 2010-02-02
Te invito a instalarte Ubuntu :)

*Para redes y servidores no hay nada mejor*

---

### Post by santiago79 on 2010-02-02
no puedo por que en el laburo no quieren en mi casa si lo uso igual voy a ver si puedo instalarlo y configurarlo en la pc que quiero hacer backup del debian

---

### Post by juancarlospaco on 2010-02-02
Instalalo en un Pendrive y usalo de ahi. :)

---

### Post by alfplayer on 2010-02-02
No entiendo cómo puede ser que trabajes con servidores con linux y que no puedas usar una computadora con linux.

Desde windows te podrías conectar con WinSCP al servidor SSH de debian transfiriendo archivos con el protocolo SFTP (que funciona sobre el protocolo SSH).

---

### Post by santiago79 on 2010-02-03
y viste como son, yo de mil amores usaria ubuntu en el trabajo, yo trabajo con putty para acceder a via ssh a debian

---

### Post by santiago79 on 2010-02-03
me baje el WinSCP y la verdad una maravilla de 10 me copie la carpeta etc de los 2 debian así que muchísimas gracias 
ahora voy a tratar de armar un server con ubuntu server que cumpla la función de router  y que atravez de el se puedan conectar a todo menos HTTP
si alguien sabe eso como se hace le voy a agradecer mucho la ayuda :D

---


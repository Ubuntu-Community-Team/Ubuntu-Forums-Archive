---
title: "Como hago una particion?"
date: 2009-04-25
forum: Software
---

### Post by WooS on 2009-04-25
Gentes tengo una duda xq cdo instale ubuntu no pude hacer las particiones que queria...
Lo que necesito es si alguien m puede decir como hago o con que programa puedo hacer particiones d mi disco xq tengo winXP con Ubuntu 8.10 y necesito crear una particion (no importa si win no la reconoce, prefiero q ande bien en Ubuntu) x si algun dia pasa algo con mi SO y lo tengo q reinstalar
Saludos

---

### Post by Air23 on 2009-04-25
Usa GParted
```
sudo apt-get install gparted
```
Luego lo encontras en: Sistema > Administracion > Editor de particiones

---

### Post by WooS on 2009-04-26
m salta esto =S
woos@woos-laptop:~$ sudo apt-get install gparted
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete gparted no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
E: El paquete gparted no tiene candidato para su instalación

---

### Post by Hei Ku on 2009-04-26
Postea tu archivo /etc/apt/sources.list

Algo no esta bien, porque deberias tener ese paquete.

---

### Post by WooS on 2009-04-26
Ahi va el archivo q decias... 
Entre en una pagina a ver si m decia algo pero encontre q tenia q escribir sudo aptitude gparted o algo asi y al parecer lo instalo pero no lo peudo encontrar por ningun lado =(

---

### Post by Tosh78 on 2009-04-26
Creo que la mejor opcion es que uses el Live CD, es decir el CD de instalacion de Ubuntu. Yo siempre lo hago desde ahi. Una vez que arrancas tu maquina booteando desde el CD, anda a Gestion de particiones o algo asi. No me acuerdo bien en que menu estaba y no tengo Ubuntu aca para fijarme, pero fijate que lo vas a ver.
Una vez que arrancas el Gparted te van a aparecer las particiones que tenes y si apretas el boton derecho te va a dar las opciones de lo que podes hacer.
Cualquier cosa volve a postear.

---

### Post by KaKuS on 2009-04-27
Anda a "Sistema -> Administración -> Gestor de paquetes Synaptic"

Hace clic en "Buscar"

Pone "gparted"

Instalalo

Ahora desde "Sistema -> Administración -> Editor de paticiones" lo podes usar

Link a la página del gparted: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

### Post by WooS on 2009-05-11
Gentes no m anda el Gparted
Tengo una particion grande d 120Gb con Ubuntu y una pequeña d 20 con Windows
Quise ahicar la d 120 para crear una nueva de respaldo pero m sale eso desde el live cd...
Si alguien sabe usarlo bien plis miren el archivo adjunto...saludos!

---

### Post by EnriqueK on 2009-05-11
No vas a poder editar particiones si estas se encuentran montadas, por lo que comentas, es evidente que tienes montada la partición de Ubuntu, por lo que para poder achicarla solo va a ser posible usando Gparted que tiene el Live CD de instalación y asegurate de no montar la partición donde se encuentre Ubuntu.

---


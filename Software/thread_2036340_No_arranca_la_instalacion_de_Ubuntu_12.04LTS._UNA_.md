---
title: "No arranca la instalacion de Ubuntu 12.04LTS. UNA BRONCA!!"
date: 2012-08-01
forum: Software
---

### Post by Lauthi on 2012-08-01
Bueeenas, tengo una MSi CR600. (Intel dual core 2.00ghz, 4gb de ram, geforce 8200g, etc) 

Probe todas las altenativas, diferentes isos, de la pagina de ubuntu, de un torrent, de diferentes pendrives pero no hay caso. 

**_PASA LO SIGUIENTE:_** 


Bootea -> Pongo instalar Ubuntu -> Carga el logon de ubuntu con los puntitos abajo -> Ahora viene el problema despues del logon aparece el fondo de color de la instalacion y ninguna ventana de instalacion queda ahi trabado.. alguna ayuda porfavooooooor?

---

### Post by gmunioz on 2012-08-01
Ubuntu 12.04 tiene problemas de gráficas.
Descarga y graba la versión alternate:
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04/release/ubuntu-12.04-alternate-amd64+mac.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04/release/ubuntu-12.04-alternate-amd64+mac.iso)
Inicia con ella, e instala con particionamiento manual, en al menos 3 particiones:
Una primaria, activa (si se puede) o sino lógica, de unos 30 gigas, sistema ext4, punto de montaje /
Una lógica, sistema de intercambio, de 1 giga para uso comun o de 12 gigas si piensas hibernar o suspender.
Una lógica, del resto de los gigas libres, sistema ext4, punto de montaje /home
El Grub en el mbr de /dev/sda

Si tienes otro operativo, desde el otro operativo previamente debes correr su scandisk y defrag, ver que no haya mas de 3 particiones primarias, si hay mas deberàs mover los datos y eliminarlas, y dejar espacio libre sin particionar.

Al iniciar del disco rígido es posible que de problemas de gráficas, deberàs iniciar en modo de recuperaciòn, submenus network, root en ese orden y desde la terminal ejecutar
sudo su
jockey-text -l
te aparecerá el driver privativo Nvidia y lo hablitas con :
jockey-text -e driver
donde driver es lo que te informa el comando.
luego reinicias normal
reboot

---

### Post by Lauthi on 2012-08-01
Entendi todo hasta la parte de "deberàs iniciar en modo de recuperaciòn, submenus network, root en ese orden etc en adelante!!

La vercion que me recomendaste la voy a hacer bootear desde un usb. Que más tengo que hacer?

---

### Post by gmunioz on 2012-08-02
Aclaraciones:
Grabas la iso en cd/dvd/usb, inicias con este dispositivo, el alternate cd no tiene sesión live, con eso se evitan los problemas de gráficas y demás, usuales en los live-cd. Instalas con particionamientoo manual. Terminada la instalación, reinicias desde el disco rígido, es aqui donde nuevamente pueden aparecer problemas con las gráficas privativas (Ati -Nvidia), si fuera asi, reinicias pulsando al reiniciar la tecla mayusculas para ver el menu del Grub, una vez en el menu del Grub se elige recuperación, en recuperación aparece un submenu amplio, de este submenu, eligiendo primero network y luego root, se inicia en una terminal, como administrador conectado a Internet (si la tarjeta de red fue reconocida) entonces con los comandos descriptos se pueden instalar los drivers privativos.

---

### Post by peporret on 2013-01-18
Hola yo soy nuevo en esto y estoy intentando instalar ubuntu 12.041 en una samsung N150 plus desde un pen drive. La cuestión es que me sale el menú con las opciones de instalación o usarlo sin instalar y cuando elijo una de las dos, sea cual sea, hace el amago de iniciar el proceso pero luego se reinicia la máquina. ¿A qué se debe esto? hay algún tipo de solución? Gracias por adelantado.

---


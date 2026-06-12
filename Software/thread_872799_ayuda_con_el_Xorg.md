---
title: "ayuda con el Xorg"
date: 2008-07-28
forum: Software
---

### Post by elmigue87 on 2008-07-28
hola teniendo problemas con un juego en ubuntu, con el Nexuiz me di cuenta que Xorg lo tengo andando mal, va o que yo que es mal por que el juego no me dejaba usar el mouse y se me tildaba y buscando informacion sobre eso encontre que abia que configurar el Xorg bien y cuando intente configurar el mio me dio esto
desktop:~# Xorg -configure

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
y tambien haciendo esto me daba esto

~# X -config /root/xorg.conf.new

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
----------------------------------------------------------------------
ahora yo no se que hacer :( no se si es que no lo tengo instalado o que. si alguien me podria ayudar para poder configurarlo bien aparte tambien leendo por ahi vi que decian que si el Xorg no funciona bien ubuntu tambien funcionaria mal andaba lento.
bueno a mi me anda un poco lenteja pero no pensaba que era de eso tengo una maquina amd64  1.8 + memoria 512+nvidia 6200 de 256 y un disco de 20gb. no se si es una buena maquina para ubuntu.pero megustaria que me ayuden a repararla para que pueda funciona bien.
desde ya mucha gracias .
saludo..
miguel

---

### Post by sdennie on 2008-07-28
Fijate si tenés los drivers de nvidia en Sistema->Administración->Controladores de Hardware.

---

### Post by elmigue87 on 2008-07-28
si lo tengo instalado bien, lo instale con el envy, pero lo que me da error es el X.org que cuando lo intento configurar me da los errores de arriba.

---

### Post by Mauro22 on 2008-07-29
Eso es porque queres modificar el xorg.conf cuando esta siendo usado por una terminal X

Hace:

Control + Alt + F1 para entrar en modo texto

sudo rm /tmp/.X0-lock

con eso cerras la sesion grafica y despues corre el comando... aunque ese nunca lo vi ¿?
El que uso yo es:

dpkg-reconfigure xserver-xorg



Acordate de hace una copia del xorg.conf actual por si las dudas:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp

Y para reemplazar la copia por si sale mal:

sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf

---

### Post by elmigue87 on 2008-07-30
muchas gracias amigo me salvaste, haber si no me decis de alguna pagina buena para poder modificar la grafica osea un buen tema para la pantalla esos que traen como reloj y el clima, asi puedo tunear mi ubuntu, el que tengo instalado ahora es el de ubuntu studio sarpa pero pudre, jeje.
bueno muchas gracias
suerte
miguel

---

### Post by Mauro22 on 2008-07-30
Principalmente estas:

[http://www.gnome-look.org/](http://www.gnome-look.org/)

[http://www.kde-look.org/](http://www.kde-look.org/)


Lo que se agregan al escritorio son Screenlets, desklets o gDesklets (busca en el foro que hay info). Para algunos de estos es necesario tener compiz o acceleracion grafica..




En mi post anterior, fijate que abajo a la derecha hay una medallita :D, dale clic para agradecerme :D:D 


:lolflag:

---


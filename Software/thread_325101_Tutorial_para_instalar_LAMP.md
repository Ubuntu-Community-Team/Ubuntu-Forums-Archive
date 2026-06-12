---
title: "Tutorial para instalar LAMP?"
date: 2006-12-25
forum: Software
---

### Post by Hex_Mandos on 2006-12-25
Alguien tiene alguna idea de como instalar un server Apache/mySQL/PHP sin armar una instalación nueva de Ubuntu? Estuve googleando (y buscando en el foro de howtos) pero la verdad es que no tengo demasiada idea del tema y lo poco que encontré no me sirvió de mucho, porque jamás en mi vida usé un http server en una máquina mía. Mi experiencia técnica es muy escasa en este tema. En particular, me gustaría saber como setear un server DNS BIND. Si alguien tiene alguna idea de donde encontrar un tutorial, agradeceré eternamente.

(Aclaro, esto lo quiero para boludear, aprender, y a lo mejor usar alguno de los dominios que tengo "en parrilla". No estoy desesperado por una cuestión laboral/comercial ni nada parecido.)

---

### Post by lavaramano on 2006-12-25
si queres levantar un lamp sin muchas vueltas te recomiendo esto: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

ahora si queres meter mano y romper cosas, ahi ya no puedo ayudarte tanto :P

---

### Post by marianom on 2006-12-26
Yo te puedo ayudar con compilacion de apache y php desde el fuente si lo llegas a necesitar.
Avisame.

---

### Post by jmn2k1 on 2006-12-27
Y no probaste instalando los tres desde Synaptic??
Creo haberlo instalado de esa forma sin ninguna complicacion...

---

### Post by az on 2006-12-27
> **jmn2k1 said:**
> Y no probaste instalando los tres desde Synaptic??
Creo haberlo instalado de esa forma sin ninguna complicacion...


LAMP:
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Bind:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Apesadumbrado esas clases particulares están en inglés... ¿Alguien puede traducirlas quizá?

---

### Post by Hex_Mandos on 2006-12-27
Mil gracias... igual, parece que voy a conseguir una máquina vieja por dos mangos para armar un server. Ahí hago, deshago y destrozo sin comerme puteadas.

---

### Post by jpmorelli on 2006-12-27
Lo de apachefriends donde esta el Xampp es una masa !!! ni siquiera hay que instalar !
Solo descomprimis donde lo queres y despues corres:

xampp start
xampp stop

hasta tiene un script para hacer un wizard de la seguridad y poner todos los pass.

---

### Post by euzkoarima on 2006-12-27
Tambien te puede servir esta guía [http://howtoforge.com/lamp_installation_ubuntu6.06]("http://howtoforge.com/lamp_installation_ubuntu6.06")

---

### Post by Hex_Mandos on 2006-12-27
El problema de xamp es que dicen que es para testeos, porque aparentemente no es seguro configurarlo así. Para desarrollos, joya. Pero quiero la cosa en serio.

euzkoarima: mil gracias, encontré ese sitio hace un tiempo, pero de vuelta requiere instalar desde 0. Ahora que conseguí máquina seguro que lo uso. ;)

---

### Post by Dr. Falken on 2006-12-28
bajando ubuntu server, y eligiendo la opción de instalar un LAMP server: [http://www.ubuntu.com/server](http://www.ubuntu.com/server)

Es la opción más fácil por goleada


El doc

---

### Post by jpmorelli on 2006-12-28
> **Dr. Falken said:**
> bajando ubuntu server, y eligiendo la opción de instalar un LAMP server: [http://www.ubuntu.com/server](http://www.ubuntu.com/server)

Es la opción más fácil por goleada


El doc

Tenes toda la razon !!!

---

### Post by albatroz2k on 2007-02-21
En la misma página de Xampp dice como "asegurar" tu instalación de Xampp.

> **Hex_Mandos said:**
> El problema de xamp es que dicen que es para testeos, porque aparentemente no es seguro configurarlo así. Para desarrollos, joya. Pero quiero la cosa en serio.

euzkoarima: mil gracias, encontré ese sitio hace un tiempo, pero de vuelta requiere instalar desde 0. Ahora que conseguí máquina seguro que lo uso. ;)

---

### Post by jjgomera on 2008-05-16
> **az said:**
> LAMP:
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Bind:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)


Apesadumbrado esas clases particulares están en inglés... ¿Alguien puede traducirlas quizá?

thanks

No se porque la gente se empeña en recomendar instalar xampp, cuando en ubuntu, y sin tener que instalar el sistema desde cero, es tan fácil con este comando

---

### Post by mattinsalto on 2009-12-24
Si escribes *sudo tasksel* en la linea de comndos te sale el asistente en el cual eliges LAMP Server y te instala todo automáticamente.

---

### Post by spongebobp2m on 2009-12-26
...mmm...

para mi, lo mejor y mas facil, descargate xampp y dale para adelante, es muy sencilla la instalación, y si querés, create una partición para /opt y te olvidas de los cambios en el s.o.

---

### Post by juancarlospaco on 2009-12-27
LAMP no tiene mucho que ver con Bind.
*Pero se pueden instalar juntos igual.*
:)

---


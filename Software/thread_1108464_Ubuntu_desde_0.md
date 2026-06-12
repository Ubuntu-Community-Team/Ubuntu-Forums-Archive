---
title: "Ubuntu desde 0"
date: 2009-03-27
forum: Software
---

### Post by Elrengo on 2009-03-27
Buenas tardes noche gente, aca vuelvo yo a molestarlos, ya cada vez menos pero siempre leyendolos y asesorandome.

Bueno vamos al caso. tengo una pc "viejita", tiene un procesador VIA de 800MHZ, 1 GB de ram con un disco de 120GB ide.

Lo que tengo ganas de armar es un SO basado en ubuntu, al cual "todas" aplicaciones se las instale yo, hasta el escritorio, ya que probe con xubuntu, y anda bastante trabado.

La idea es instalar solo las aplicaciones q utilizo, que no son muchas comparadas con las que vienen con el gnome-desktop. (lease audacius, firefox, thunderbird, y no muchas mas). tambien estuve investigando sobre aplicaciones mas livianas como pcmanfm (manejador de archivos), y la idea es instalar xfce(a ver si hay diferencia con xubuntu, o fluxbox)

Estoy googleando, pero tampoco se bien que es lo que tengo que buscar.


Si me pueden ortientar un poco, se los agradeceria

Saludos


Matias


EDIT:  espero que cuando arranque en modo consola tenga a mano el apt-get. Aclaro que no soy un usuario muuuy avanzado que digamos, pero me las arreglo casi siempre.

---

### Post by guillermolisi on 2009-03-27
> **Elrengo said:**
> Buenas tardes noche gente, aca vuelvo yo a molestarlos, ya cada vez menos pero siempre leyendolos y asesorandome.

Bueno vamos al caso. tengo una pc "viejita", tiene un procesador VIA de 800MHZ, 1 GB de ram con un disco de 120GB ide.

Lo que tengo ganas de armar es un SO basado en ubuntu, al cual "todas" aplicaciones se las instale yo, hasta el escritorio, ya que probe con xubuntu, y anda bastante trabado.

La idea es instalar solo las aplicaciones q utilizo, que no son muchas comparadas con las que vienen con el gnome-desktop. (lease audacius, firefox, thunderbird, y no muchas mas). tambien estuve investigando sobre aplicaciones mas livianas como pcmanfm (manejador de archivos), y la idea es instalar xfce(a ver si hay diferencia con xubuntu, o fluxbox)

Estoy googleando, pero tampoco se bien que es lo que tengo que buscar.


Si me pueden ortientar un poco, se los agradeceria

Saludos


Matias


EDIT:  espero que cuando arranque en modo consola tenga a mano el apt-get. Aclaro que no soy un usuario muuuy avanzado que digamos, pero me las arreglo casi siempre.

Para buscar informacion en Google pondria Window manager y luego afinaria la punteria. Hay varios WM para elegir y probar. Inclusive LXDE que personalmente me parecio mas liviano que XFCE.

Si no te das maña con apt-get podes probar Aptitude que a pesar de no ser grafico no te deja de frente a una consola vacia.
La recomendacion para lo que queres llevar a cabo es usar un CD Alternate de Ubuntu (o alguna variante liviana, mas pequeña, como U-Lite, etc.)

---

### Post by Elrengo on 2009-03-27
Muchas gracias guille, en estos momentos estoy leyendo.

Pero la verdad es que no se bien como hacer para instalar el sistema y que quede en modo texto. sin entorno grafico, para que de ahi en mas, yo instale todos los programas que necesito, incluidos entre ellos, algun entorno grafico que ire probando hasta q alguno me agrade.

Saludos  
Matias

---

### Post by guillermolisi on 2009-03-27
> **Elrengo said:**
> Muchas gracias guille, en estos momentos estoy leyendo.

Pero la verdad es que no se bien como hacer para instalar el sistema y que quede en modo texto. sin entorno grafico, para que de ahi en mas, yo instale todos los programas que necesito, incluidos entre ellos, algun entorno grafico que ire probando hasta q alguno me agrade.

Saludos  
Matias

Las distribuciones Ubuntu Alternate poseen instaladores en modo texto y si no elegis un escritorio grafico (y el Xserver) te queda la consola al finalizar la instalacion inicial, que pareceria ser lo que queres lograr.

Luego de probar un escritorio grafico/WM para que vuelva a quedar en modo texto vas a tener que desinstalar el escritorio /WM que probaste y tambien el Xserver (para luego volverlo a instalar cuando pruebes el siguiente desktop/WM grafico)

---

### Post by Elrengo on 2009-03-27
Gracias gracias, ahora estoy bajando el alternate cd

Dps les cuento como me esta yendo.

Saludos

Matias

---

### Post by gmunioz on 2009-03-28
Hola Matias:

A partir de Intrepid, el alternate cd no trae mas al server para instalar.

Debes bajar el cd de la versión server.

Una vez instalado y funcionando y previos:

apt-get update
apt-get upgrade

Pudes comenzar instalando las gráficas y un escritorio liviano, para luego desde el, comenzar a instalar aplicaciones, lo haces mediante por ejemplo:

apt-get install x-window-system-core gdm synaptic lxde

Saludos.

---

### Post by Elrengo on 2009-03-28
Me pasa algo raro en la pc, baje el cd alternate de ubuntu.
y cuando bootea en la pc que lo quiero instalar, no me sale la pantalla habitual con la opcion para elejir idioma y los modos.

Pero esto pasa solo en esta pc, que tiene un procesador VIA de 800Mhz, y un motherboard con video integrado.

Este es el link del fabricante y modelo


[http://www.jetway.com.tw/jw/motherboard_view.asp?productid=65&proname=625EMP]("http://www.jetway.com.tw/jw/motherboard_view.asp?productid=65&proname=625EMP")


bueno, el caso no seria tan grave, ya que al escribir CLI, o CLI-EXPERT, podria instalarlo igual.

Pero me dice q no encuentra el nucleo de linux, y ya probe la integridad de la imagen del cd, es mas, la baje 2 veces de servidores distintos por precaucion, y no funciona en ningna.

Tendra algo que ver el chipset de la pc?

Me parece q xubuntu no me reconcia los dirvers de la placa de video


Saludos

Matias

---

### Post by guillermolisi on 2009-03-28
> **Elrengo said:**
> Me pasa algo raro en la pc, baje el cd alternate de ubuntu.
y cuando bootea en la pc que lo quiero instalar, no me sale la pantalla habitual con la opcion para elejir idioma y los modos.

Pero esto pasa solo en esta pc, que tiene un procesador VIA de 800Mhz, y un motherboard con video integrado.

Este es el link del fabricante y modelo


[http://www.jetway.com.tw/jw/motherboard_view.asp?productid=65&proname=625EMP](http://www.jetway.com.tw/jw/motherboard_view.asp?productid=65&proname=625EMP)


bueno, el caso no seria tan grave, ya que al escribir CLI, o CLI-EXPERT, podria instalarlo igual.

Pero me dice q no encuentra el nucleo de linux, y ya probe la integridad de la imagen del cd, es mas, la baje 2 veces de servidores distintos por precaucion, y no funciona en ningna.

Tendra algo que ver el chipset de la pc?

Me parece q xubuntu no me reconcia los dirvers de la placa de video


Saludos

Matias
Probaria iniciar esa maquina con un LiveCD, a ver que pasa.
Si el LiveCD funciona, entonces el Alternate tambien deberia hacerlo al instalar.

No tengo la mas minima idea de cuan compatible es ese procesdor y su chipset con la arquietectura Intel (que tambien usa AMD).

---

### Post by hictio on 2009-03-28
Elrengo,

Te paso estos dos links, a mi me ayudaron que jode para la instalacion de Ubuntu en maquinas viejas.
Yo lo instale (8.04 & 8.10) en una verdadera catramina, Pentium MMX @ 333MHz con 512 MB de RAM y una GeForce II de 64MB.
Bueno, una catramina para hoy en dia...

. [Installation on low memory systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
. [Ubuntu Minimal Desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

Aca estan mis experiencias en la instalacion en mi maquina: [Some Orbis-Tertius Ubuntu install notes](ttp://oesediez.blogspot.com/2008/08/some-orbis-tertius-ubuntu-install-notes.html).
En mi caso, los problemas se debieron fundamentalmente a que la maquina era demasiado lenta para la instalacion. Por supuesto, no quedo otra opcion que hacer la instalacion con el CD Alternate, -y no creo en tu caso, pero en el mio, no tuve otra- hacer la instalacion de Gnome (o el Desktop Environment o Window Manager que quieras usar) a posteriori.

---

### Post by SLA_leandrin on 2009-03-29
> **Elrengo said:**
> Buenas tardes noche gente, aca vuelvo yo a molestarlos, ya cada vez menos pero siempre leyendolos y asesorandome.

Bueno vamos al caso. tengo una pc "viejita", tiene un procesador VIA de 800MHZ, 1 GB de ram con un disco de 120GB ide.

Ejem, perdón... pero me parece que con un procesador como ese y 1 Gb de RAM Ubuntu te debería andar bien... y mejor aún Xubunto. 

Por ejemplo yo ahora, en una laptop con un procesador a 800 Mhz y 1 Gb de RAM, con openSuse 11.1 con KDE 4.2 y con VirtualBox con Windows XP y me anda 10 puntos. Probaste Ubuntu (con gnome) y no Xubuntu, a ver que pasa?

---

### Post by hictio on 2009-03-29
Comparto la opinion de SLA_leandrin. Quizas el LiveCD funcione un poco lento, pero una vez instalado, te tendria que andar bien.
Por supuesto, depende mucho que aplicaciones vas a usar, especialmente si vas a usar varias al mismo tiempo :) , pero estas bien, especialmente de RAM.

---


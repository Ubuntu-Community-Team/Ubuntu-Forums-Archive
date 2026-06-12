---
title: "[SOLUCIONADO] Problema ATI Mobility Radeon HD4330 - Ubuntu Jaunty"
date: 2009-08-20
forum: Software
---

### Post by pepetendos on 2009-08-20
Hola, ayer tube un problema con la configuracion grafica en ubuntu, en el portatil un DELL Inspiron 1545 intente cambiar la configuracion para que se viese el escritorio en un monitor de sobremesa y no pude, por lo que decidi desistalar el driver que descague de la pagina de ati e instalar el que viene en el synaptic, cuando desistale el driver decidi equivocadamente reiniciar sin instalar los driver de synaptic y al iniciar me sale la pantalla con las letras de ubuntu y la barra cargando y de pronto se distorsiona y la pantalla se pone como cuando una television no tiene señal y ahi se queda, no me deja ni cambiar al entorno de trabajo 1 (Ctrl+Alt+F1) la grafica es una ATI Mobility Radeon HD4330, tengo el archivo de los driver de la pagina de ATI pero al entrar en modo recovery no me deja instalarlo, empieza como a instalarlo y me da el siguiente error:
 
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro
 
Removing temporary directory: fglrx-install.xdRCSD
 
Tambien e editado el archivo xorg poniendo el contenido del archivo default y el failsafe y me hace lo mismo y e probado con el comando 
 
dpkg-reconfigure -phigh xserver-xorg
 
y el 
 
dpkg-reconfigure xserver-xorg
 
desde el modo recovery y luego entrando en root y solo me dice de configurar el teclado. ahora mismo mi archivo xorg esta asi.
 
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
 
Section "Monitor"
Identifier "Configured Monitor"
EndSection
 
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
 
 
Soy nuevo en ubuntu y ya e tenido este problema antes y mi solucion a sido reinstalarlo, e mirado en foros a ver si alguien tenia mi problema y e intentado varias cosas y nada, me gustaria poder solucionarlo sin tener que llegar a reinstalarlo, gracias.
 
Por cierto mi version de ubuntu es la jaunty.

---

### Post by pepetendos on 2009-08-21
Gracias a los que habeis leido el post, ya e conseguido solucionarlo el problema de la grafica, para ello me descargue la ultima version de los drivers desde la pagina no oficial de drivers ati para Linux, después desde el live cd copie el archivo .run en la raiz de mi ubuntu, reinicie y entre en modo recovery, desde el menú del modo recovery selecione entrar como root y una vez alli hice

#cd /

Para ir al raiz donde tengo el archivo .run con los drivers y ejecutamos (sin las comillas)

#sh &#8220;nombre del archivo.run&#8221;

La ultima versión de los drivers si me dejo instalarlos sin problema, siguiendo los pasos que te indica, no tiene mucha coplicacion, después edite el archivo xorg.conf que se encuentra en el directorio /etc/X11, para lo cual me servi de backup que tenia de cuando me funcinaba bien el ubuntu

#cd /etc/X11
#cp &#8220;backup de xorg&#8221; xorg.conf

Me a costado dos tardes leyendo por foros y quebrándome la cabezo pero de nuevo tengo funcionando ubuntu sin tener que reinstalarlo

---

### Post by augias on 2009-08-21
pucha que bacan, te felicito por haber solucionado tu problema. yo hubiera desistido despues de unas horas y reinstalado el OS. se aprecia tambien que hayas puesto la solucion a tu problema, por si a alguien le llega a pasar lo mismo. animo que haciendo vas aprendiendo y mejorando la experiencia en linux. 

¿haz podido extender tu escriorio al segundo monitor? a mi me resulto a la primera desde las preferencias de gnome (tarjeta intel).

---


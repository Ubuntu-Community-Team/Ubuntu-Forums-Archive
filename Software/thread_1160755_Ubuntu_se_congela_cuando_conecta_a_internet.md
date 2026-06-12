---
title: "Ubuntu se congela cuando conecta a internet"
date: 2009-05-15
forum: Software
---

### Post by ideafix on 2009-05-15
Buenas gente. Me pasa algo rarisimo. Resulta que instale el Ubuntu Studio y despues de conectar a internet (por cable, por wireless no pude) y pasado un minuto, se congelo. Sin desesperarme, entre a win, verifique q todo andaba, reinicie y entre a ubuntu (comun) y OH sorpresa, me pasa lo mismo, se conecta a internet y muere. En ambos casos lo unico que queda es apagar a lo bestia (Nota: si aprieto el boton de encendido aparece si quiero apagar, reiniciar...pero sin efecto alguno, si no puedo ni mover el mouse!. Y tambien siguio andando la musica :O)
Creo...creo que no toq nada raro cuando configure la red en ubuntu studio, lo hice desde lo grafico digamos....
No se bien q datos pasarles, por ahi si me dicen les digo, pero (como dice bart) me dejo de 6 el problema.
Tengo: el win 7, ubuntu 8.10 64 bits y Ubuntu Studio 9.04 AMD64.

Saludos y desde ya gracias!!!!

---

### Post by emiliano_raso on 2009-05-16
Probá conectandote a WiFi por consola:

```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid nombre_de_tu_red key tu_clave
sudo dhclient wlan0
```

---

### Post by ideafix on 2009-05-16
Gracias, pero no anduvo. Perdon q no copie el error, pero era algo con el tema de key. Es q por eso tampoco me esforze por conectar desde el administrador de red, porque las unicas opciones que tenia para elegir, eran WEP, y mi clave es WAP. Lo que si me fije es que el controlador de la placa esta perfecto, la reconocio, y el driver esta en uso.
Volviendo al tema, ahora vi mas exactamente donde se "congela": cuando el gestor de actualizaciones se pone a bajar. Avanza un poco y plaf muere. Como dije es raro, algunas cosas andan, pero basta hacer un click como para q todo se congele. hice un

sudo apt-get autoclean

para eliminar cosas sueltas, pero igual, empieza a bajar y se cuelga.

Ah, Ubuntu (el comun) ya no se cuelga, lo estoy usando ahora mismo (igual lo estoy vigilando ¬¬).

---

### Post by Hei Ku on 2009-05-16
Postea tu archivo /etc/network/interfaces

Asi vemos como tenes configurada la red.

---

### Post by Hernán-Amaya on 2009-05-16
Fijate si sacas el gestor de actualizaciones del inicio de gnome. Y proba si podes navegar o si podes bajar las actualizaciones a mano o por synaptic o por aptitude.

---

### Post by ideafix on 2009-05-16
mi archivo /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface


iface eth0 inet dhcp

auto eth0

ja la sigo embarrando ahora ni siquiera conecta por la cableada. :P

---

### Post by Hei Ku on 2009-05-16
Y... no. Que tocaste? Porque el archivo interfaces esta vacio. No va a conectar ni a cañonazos.

---

### Post by guillermolisi on 2009-05-16
Estas usando Network Manager por casualidd ?

---

### Post by ideafix on 2009-05-16
Bueno va de nuevo el archivo, ja ya arregle la cableada

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Desactive en programas que inician el que avisa de las actualizaciones, y el que busca controladores de hardware (porque cuando antes quise habilitar el de nvidia empezo a descargar y murio la notebook) y hasta ahora puedo navegar sin problemas.
Hice 

Sudo aptitude upgrade

sin problemas, actualizo bien.

Que me recomiendan: instalo el network manager? (ah perdon , no, no lo estoy usando para el que pregunto, porque no esta instalado)
Dejo deshabilitado que busque actualizaciones? De ahora en mas lo voy a tener q hacer manual?
El driver de nvidia voy a buscar si hay manera de bajarlo por terminal. Saludos!!

Edito: se vuelve a colgar cuando trato de instalar el driver por aptitude. Baje el .deb, no hubo problemas, pero cuando empezo a descargar las dependencias, se colgo. :S

---

### Post by ideafix on 2009-05-18
Bueno, les comento:

1-Supuestamente navegaba bien, si no hacia nada de actualizar ni nada andaba todo, hasta q entre a clarin, y se colgo. Entonces me acorde de que a un amigo le paso cuando toco windows con la optimizacion del tune up, q modifico el MTU. Entonces investigue el tema del MTU en ubuntu, y termine añadiendo

mtu 1400

al archivo /etc/network/interfaces

Una vez hecho eso, pude bajar driver de nvidia, e instale el network manager

2-Con el network manager, la wireless salio andando, y ya ahi si tengo mi Ubuntu Studio sin problemas

El tema es q me sigue llamando la atencion porq con la cableada se muere al actualizar. La verdad no probe el MTU en 1500 (como lei que es por defecto) porque estoy poniendo a punto el studio. Despues pruebo. ¿Habra sido ese el problema?

PD: no se como hacer, pero el titulo del post tendria q ser "Ubuntu Studio se congela cuando conecta a internet" :P

---


---
title: "control ancho de banda"
date: 2008-08-27
forum: Software
---

### Post by cbiragnet on 2008-08-27
Hola. tengo que controla el ancho de banda en una red local, tengo instalado un server ubuntu con 2 placas de red. La red tiene 2 tipos de direcciones IP. Alguien me puede decir cual sería la herramienta mas facil y practica a utilizar. Muchas gracias.

---

### Post by faktorqm on 2008-08-27
Y lo mejor es squid... tiene algunos problemas pero si los salteas anda bien. 
Si no podes usar proxy por algun motivo, podes hacer control de ancho de banda por iptables pero tenes que hacer un script y es mas complicado, yo tengo uno creo por ahi de un chabon que lo hizo pero es muy zarpado, o sea, si lo necesito cambiar por algo a veces se me complica. 
Tambien tenes pfsense, un openbsd version live cd orientado a redes que te deja hacer eso tambien, aunque no veo que aplique segun tu caso, ya que ya tenes el server instalado y funcionando, pero bueno, te lo comento igual por las dudas. Salu2!

---

### Post by cbiragnet on 2008-08-27
Gracias por tu pronta respuesta, estuve leyendo y probando un poco con squid y oi hablar de las iptables, lo que necesitaría es una guia de como poder llevar a cabo este trabajo. salu2.

---

### Post by gmunioz on 2008-08-29
Hola cbi...:
Para controlar el ancho de banda debes utilizar las herramientas que vienen en linux:

Un controlador de tráfico (tc)
Un temporizador (htb).

Estas herramientas, al formar parte del propio sistema operativo tiene un elevado nivel de eficiencia y precisión.

Es muy importante tener en claro antes de empezar a limitar algo, saber los limites propios de lo que queremos limitar.

Se debe establecer primero el ancho de banda máximo disponible en las  líneas de transmisión, por ejemplo:
10Mbps (Clase 1). 
Luego se deben definir todos los límites previstos o CLASES. 
Por ejemplo los diferentes límites serán:
512Kbps (Clase 2)
256Kbps (Clase 3)
24Kbps (Clase 4)
Con estos valores tenemos definidas 4 CLASES. Esto significa que tendremos algunos servicios, usuarios o subnets, con 1Mbps, otros con 512Kbps, otros con 256Kbps y los últimos con 24Kbps.

Luego se debe empezar a definir que corresponderá a cada clase.

Para que cada sector o servicio corresponda a una determinada CLASE se deben aplicar FILTROS. 

Luego que tenemos las CLASES y los FILTROS, sólo  queda escribir el Script, archivo de texto plano ejecutable, que implemente el limitador.

Por ejemplo en un servidor Linux por donde pasa todo el tráfico de Internet, videoconferencia y correo corporativo, que tiene dos placas de red, una externa (eth0) y la otra interna (eth1),

La distribución de direcciones ip y puertos es la siguiente:
La Gerencia forma una subnet con la siguiente numeración: 192.168.21.0/24.
La Sucursal es la subnet 192.168.31.0/24
El resto de los usuarios pertenecen a la subnet 192.168.1.0/24
El puerto usado por Squid, el proxy de internet es el 3128

Se definen las 4 clases de ancho de banda:
   1. 10Mbps
   2. 256 Kbps
   3. 128 Kbps
   4. 24Kbps

Se define que grupo pertenece a cada clase:
Gerencia pertenecerá a la Clase I
Internet pertenecerá a la Clase II
El resto de los usuarios ocupará la Clase III
La sucursal será parte de la Clase IV. 
En el caso de la sucursal, por ejemplo, los servicios de internet y correo corporativo estarán limitados a 24Kbps

El Script tendría el siguiente contenido:
=====================Comienzo===========================================
#!/bin/bash

# Se define la placa de red interna, a administrar.

DEV=eth1

# Se define el camino al comando "tc", para el caso de que no este en el PATH

TC=tc ; este es el caso en el que esta en el PATH

# Se definen todos los limites de ancho de banda a utilizar en Kbps.

RATE1=1000
RATE2=256
RATE3=128
RATE4=24

# Se eliminan definiciones anteriores de FILTROS y CLASES

$TC qdisc del dev $DEV root 2>&1 >/dev/null

# Se definen las CLASES existentes, ademas de la CLASE root y la CLASE master necesarias para el funcionamiento del script.

# CLASE root y master

$TC qdisc add dev $DEV root handle 1: htb default 60

$TC class add dev $DEV parent 1: classid 1:1 htb rate ${RATE1}kbit

# CLASES y orden prioridad

# CLASE I

$TC class add dev $DEV parent 1:1 classid 1:10 htb rate ${RATE}kbit ceil ${RATE}kbit prio 1

$TC qdisc add dev $DEV parent 1:10 handle 10: sfq perturb 10

# CLASE II

$TC class add dev $DEV parent 1:1 classid 1:20 htb rate ${RATE2}kbit ceil ${RATE2}kbit prio 2

$TC qdisc add dev $DEV parent 1:20 handle 20: sfq perturb 10

# CLASE III

$TC class add dev $DEV parent 1:1 classid 1:30 htb rate ${RATE3}kbit ceil ${RATE3}kbit prio 3

$TC qdisc add dev $DEV parent 1:30 handle 30: sfq perturb 10

# CLASE IV

$TC class add dev $DEV parent 1:1 classid 1:40 htb rate ${RATE4}kbit ceil ${RATE4}kbit prio 1

$TC qdisc add dev $DEV parent 1:40 handle 40: sfq perturb 10

# Se definen los FILTROS.

# FILTRO1 (Subnet GERENCIA a CLASE I)

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip dst 192.168.21.0/24 flowid 1:10

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip src 192.168.21.0/24 flowid 1:10

# FILTRO2 (INTERNET a CLASE II)

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip dport 3128 flowid 1:20

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip sport 3128 flowid 1:20

# FILTRO3 (Subnet RESTO USUARIOS a CLASE III)

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip dst 192.168.1.0/24 flowid 1:30

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip src 192.168.1.0/24 flowid 1:30

# FILTRO4 (Subnet SUCURSAL a CLASE IV)

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip dst 192.168.31.0/24 flowid 1:40

$TC filter add dev $DEV parent 1: protocol ip prio 1 u32 match ip src 192.168.31.0/24 flowid 1:40

=================================Fin=================================

El script se guarda como un archivo de texto, con un nombre, por ejemplo limitador.sh y se le dan permisos de ejecución con la orden:
sudo chmod a+x limitador.sh
 
Te sugiero leas los manuales de los comandos utilizados y sobre como configurar Squid.

Saludos.
Gabriel.
*Solo doy soporte para Ubuntu* - **6666** - *Más malo que el diablo*

---

### Post by faktorqm on 2008-08-30
Muy bueno, pero todo eso es estatico, o sea, el que baja a 24 va a bajar aunque este la empresa entera desconectada... y eso es poco eficiente. Si no hay nadie, que baje a lo que dé, si estan todos, que limite estatico. Salu2!

---

### Post by cbiragnet on 2008-09-08
realmente les agradezco a ambos el trabajo de contestar mis dudas, todo esto está clarificando mi panorama. se podra pedir entonces si pueden hacer algun ejemplo que no sea estatico. muchas gracias nuevamente.

---

### Post by ariel on 2008-09-11
> **gmunioz said:**
> Hola cbi...:
Para controlar el ancho de banda debes utilizar las herramientas que vienen en linux:

Un controlador de tráfico (tc)
Un temporizador (htb).

*............*

La explicacion es excelente, gracias!

Como menciona Gabriel, el trabajo lo hace "TC", "tc" es la interfaz para usuario de la funcion "Linux Traffic Control" que provee el Kernel de linux. Squid no tiene nada que ver con esto.

Linux TC es muy potente. En la configuracion que muestra Gabriel, el trafico es encolado usado el scheduler mas simple, PRIO, que se basa en la simple prioridad y limites de cada clase. Por eso, los pibes de la clase 4 del ejemplo no pueden consumir mas de 24Kbps incluso si nadie mas esta usando el canio de 10Mbps.

Obviamente Linux TC provee schedulers mucho mas sofisticados que PRIO. Por ejemplo, CBQ, que permite definir prioridades y anchos de banda maximos y promedios para cada clase para situaciones de congestion, y que si hay ancho de banda suficiente, deja que aca usuario tome lo que necesite.

Hay toneladas de buenos how-to's en internet. Uno piola es:

[http://lartc.org/]("http://tldp.org/HOWTO/Traffic-Control-HOWTO/index.html")

Otro mas simple:

[http://www.linux.org/docs/ldp/howto/Traffic-Control-HOWTO/intro.html](http://www.linux.org/docs/ldp/howto/Traffic-Control-HOWTO/intro.html)

---

### Post by mama21mama on 2010-02-27
Yo ando buscando algo para limitar 2 usuarios mas en mi karmic.
Se le puede hacer alguna modificación al script para limitar usuarios?

Saludos

---

### Post by juancarlospaco on 2010-02-28
*Fijate que se puede hacer Round-Robin y es simple.*

---

### Post by mama21mama on 2010-02-28
> Round Robin DNS es una técnica en la cual el balanceo de carga es realizada por un servidor DNS en lugar de una máquina estrictamente dedicada. Esta técnica se suele usarse en grandes redes o redes IRC.

Para los que no tenemos grandes redes lo más interesante sería la posibilidad de balanceo de carga sin la necesidad de un equipo adicional dedicado a esta tarea.

Round robin funciona respondiendo a las peticiones DNS con una lista de direcciones IP en lugar de una sola (todas ellas deberían hospedar el mismo contenido). El orden con el cual las direcciones IP de la lista son retornadas es la base del round robin, actuando en ciclos. ... [Fuente]("http://bytecoders.homelinux.com/content/balanceo-de-carga-round-robin-dns.html")


Creo que no es lo que busco

---

### Post by juancarlospaco on 2010-02-28
*Nop, va... si, pero no.*

Round-Robin es un algoritmo que se usa para balanceo de cargas, pero es generico,
en este caso se puede aplicar como modulo del Kernel, como configuracion de Squid, DNS, etc.

---


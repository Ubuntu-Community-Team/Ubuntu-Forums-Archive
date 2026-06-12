---
title: "problemon con cortafuegos"
date: 2008-12-09
forum: Software
---

### Post by deafters on 2008-12-09
Hola, resulta que necesito compartir internet desde mi xubuntu a xp y lei que la forma era hacerlo a traves de iptables y que una de las formas de configuración mas sencilla era con firestarter ( que no e sun firewall sino una interfaz gráfica de configuración), bien lo instale, seguí el wizard, pero a la hora de lanzarlo en la terminal de comandos me sale esto: "External network device ppp0 is not ready. Aborting.." y en la interfaz gráfica me dice lo siguiente : 
no se pudo arrancar el cortafuegos
el dispositivo ppp0 no esta preparado
compruebe que la configuración de su dispositivo de red y asegúrese de que su conexión a internet esta disponible.

Por supuesto que tire un ifconfig y mi ppp0 esta conectado, asi que agradecere muchisimo vuestra ayuda, un saludo cordial a todos

---

### Post by hictio on 2008-12-09
Un par de cosas, por chequear nada más...

Tu máquina xubuntu tiene 2 tarjetas de red?
Cómo está conectada a internet? (Ethernet o USB)
Y cómo está conectada la xubuntu a la red interna?
Tenés un switch o va directo a la máquina XP?

---

### Post by deafters on 2008-12-09
> **hictio said:**
> Un par de cosas, por chequear nada más...

Tu máquina xubuntu tiene 2 tarjetas de red?
Cómo está conectada a internet? (Ethernet o USB)
Y cómo está conectada la xubuntu a la red interna?
Tenés un switch o va directo a la máquina XP?

hola, antes que nada gracias por tu interes, te cuento mi maquina que tiene ubuntu ( que es la que quiero usar para compartir internet) tiene un modem speedtouch 330 que esta andando ( y es por donde entra internet) y una placa de red ( que es por donde pienso darle internet al xp a travez de un cable cruzado), nuevamente mil gracias.

---

### Post by guillermolisi on 2008-12-09
> **deafters said:**
> hola, antes que nada gracias por tu interes, te cuento mi maquina que tiene ubuntu ( que es la que quiero usar para compartir internet) tiene un modem speedtouch 330 que esta andando ( y es por donde entra internet) y una placa de red ( que es por donde pienso darle internet al xp a travez de un cable cruzado), nuevamente mil gracias.

Entonces me animaria a decirte que Firestarter esta asumiendo que la placa de red es la que tiene la conexion a Internet, por eso el error.

Tenes que decirle que esa no es la interface de red a Internet sino la otra, la que posee ppp0.

Como esta identificada la interface donde esta conectado el modem ? (ifconfig en la consola deberia ser de utilidad para esto).

---

### Post by mhoyos on 2008-12-09
> **deafters said:**
> mi maquina que tiene ubuntu ( que es la que quiero usar para compartir internet) tiene un modem speedtouch 330 que esta andando ( y es por donde entra internet) y una placa de red ( que es por donde pienso darle internet al xp a travez de un cable cruzado), nuevamente mil gracias.

el modem, como lo tenes conectado al ubuntu ??

la placa de red, esta libre ?? 

salu2

---

### Post by hictio on 2008-12-09
> **deafters said:**
> hola, antes que nada gracias por tu interes, te cuento mi maquina que tiene ubuntu ( que es la que quiero usar para compartir internet) tiene un modem speedtouch 330 que esta andando ( y es por donde entra internet) y una placa de red ( que es por donde pienso darle internet al xp a travez de un cable cruzado), nuevamente mil gracias.

Ok, tenes todo bien preparado :)

Nunca use Firestarter, siempre lo hice con scripts, te recomiendo el de Technion, que además esta muy bien comentado línea por línea que hace cada una de ellas.

[http://files.directadmin.com/services/all/iptables](http://files.directadmin.com/services/all/iptables)

---

### Post by deafters on 2008-12-09
> **guillermolisi said:**
> Entonces me animaria a decirte que Firestarter esta asumiendo que la placa de red es la que tiene la conexion a Internet, por eso el error.

Tenes que decirle que esa no es la interface de red a Internet sino la otra, la que posee ppp0.

Como esta identificada la interface donde esta conectado el modem ? (ifconfig en la consola deberia ser de utilidad para esto).


Si si, eso ya lo revise y esta bien configurado, no puedo darle y me estoy volviendo loco jajajajaaja, mil gracias por tu aporte

---

### Post by deafters on 2008-12-09
> **mhoyos said:**
> el modem, como lo tenes conectado al ubuntu ??

la placa de red, esta libre ?? 

salu2

el modem esta conectado a mi ubuntu via usb y la placa de red esta libre, muchas gracias por interesarte , un cordial saludo

---

### Post by deafters on 2008-12-09
> **hictio said:**
> Ok, tenes todo bien preparado :)

Nunca use Firestarter, siempre lo hice con scripts, te recomiendo el de Technion, que además esta muy bien comentado línea por línea que hace cada una de ellas.

[http://files.directadmin.com/services/all/iptables](http://files.directadmin.com/services/all/iptables)

muchas gracias por tu data, si no le encuentro solución a lo de firestarter tendre que implementarlo y seguramente estaré nuevamente molestando por aqui ;), un cordial saludo

---

### Post by Hei Ku on 2008-12-09
No es un problema de tu pc, sino un tema en el firestarter. Hay algo mal configurado y no se banca la traducción al español de unos chequeos que hace.

Esta es la solución:

abrí una terminal y escribi

```

sudo gedit /etc/firestarter/firestarter.sh

```

después tenes que cambiar la linea

```

MASK=`/sbin/ifconfig $IF | grep Mas | cut -d : -f 4`

```

le tenes que agregar el tilde al mas o sea que quede

```

MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`

```

Creo que son 2 lugares donde hace un "grep Mas" y tenés que cambiarlo, pero no estoy seguro.

Gracias a Pablo Atheist por la solución.

---

### Post by deafters on 2008-12-10
> **Hei Ku said:**
> No es un problema de tu pc, sino un tema en el firestarter. Hay algo mal configurado y no se banca la traducción al español de unos chequeos que hace.

Esta es la solución:

abrí una terminal y escribi

```

sudo gedit /etc/firestarter/firestarter.sh

```

después tenes que cambiar la linea

```

MASK=`/sbin/ifconfig $IF | grep Mas | cut -d : -f 4`

```

le tenes que agregar el tilde al mas o sea que quede

```

MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`

```

Creo que son 2 lugares donde hace un "grep Mas" y tenés que cambiarlo, pero no estoy seguro.

Gracias a Pablo Atheist por la solución.

hola, te cuento que si hago eso cambia el error original que puse al principio del post por el siguiente:
 
no se pudo arrancar el cortafuegos, error desconocido.

no obstante, si le doy aceptar a esa advertencia pareceria funcionar ya que si bloqueo todo el trafico , ni siquiera puedo navegar desde mi ubuntu, 

millon de gracias

---

### Post by Hei Ku on 2008-12-10
Fijate bien que reglas tenés, y si hiciste bien el cambio realmente, porque no debería darte error alguno.

---

### Post by deafters on 2008-12-11
> **Hei Ku said:**
> Fijate bien que reglas tenés, y si hiciste bien el cambio realmente, porque no debería darte error alguno.

geacias por seguir ayudandome, te cuento que revise todo el sh de firestarter y usando la busqueda en documento , busque todos los grep, para chequear que estuviese todo como me lo indicaste y asi y todo cuando abro la interfaz de firestarter me sigue diciendo el mismo error.
en cuanto al trafico, lo filtra igualmente y a pesar de ese error aparentemente.
mil gracias por tu tiempo

---

### Post by guillermolisi on 2008-12-11
> **deafters said:**
> geacias por seguir ayudandome, te cuento que revise todo el sh de firestarter y usando la busqueda en documento , busque todos los grep, para chequear que estuviese todo como me lo indicaste y asi y todo cuando abro la interfaz de firestarter me sigue diciendo el mismo error.
en cuanto al trafico, lo filtra igualmente y a pesar de ese error aparentemente.
mil gracias por tu tiempo

Considera que el filtrado lo hace el propio firewall del kernel. Firestarter no es un firewall, solo una interfaz grafica que permite establecer las reglas en forma mas amigable.

Suponiendo que sea un problema de idioma, como dice Hei Ku, probaste Firestarter en ingles como para descartar eso como posible causa ?

---

### Post by deafters on 2008-12-11
> **guillermolisi said:**
> Considera que el filtrado lo hace el propio firewall del kernel. Firestarter no es un firewall, solo una interfaz grafica que permite establecer las reglas en forma mas amigable.

Suponiendo que sea un problema de idioma, como dice Hei Ku, probaste Firestarter en ingles como para descartar eso como posible causa ?

Hola soy conciente de mis limitaciones en linux ubuntu ya que soy muy nuevo,pero con apt-get install frestarter me lo instala en español, como deberia hacer para instalarlo en ingles desde los repositorios?
desde ya muy agradecido

---

### Post by Hei Ku on 2008-12-11
El problema no es el idioma del firestarter, sino de algunos comandos que usa el sh.

Podes postear tu firestarter.sh, para ver que esté todo ok?

---

### Post by deafters on 2008-12-12
> **Hei Ku said:**
> El problema no es el idioma del firestarter, sino de algunos comandos que usa el sh.

Podes postear tu firestarter.sh, para ver que esté todo ok?
 gracias por la colaboracion , aqui te lo dejo

#!/bin/bash
#-----------( Firestarter Control Script )-----------#

# Load Configuration
source /etc/firestarter/configuration 2>&1

# --(Set program paths)--

IPT=/sbin/iptables
IFC=/sbin/ifconfig
MPB=/sbin/modprobe
LSM=/sbin/lsmod
RMM=/sbin/rmmod


# --(Extract Network Information)--

# External network interface data
IP=`/sbin/ifconfig $IF | grep inet | cut -d : -f 2 | cut -d \  -f 1`
MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`
BCAST=`/sbin/ifconfig $IF |grep Bcast: | cut -d : -f 3 | cut -d \  -f 1`
NET=$IP/$MASK

if [ "$NAT" = "on" ]; then
	# Internal network interface data
	INIP=`/sbin/ifconfig $INIF | grep inet | cut -d : -f 2 | cut -d \  -f 1`
	INMASK=`/sbin/ifconfig $INIF | grep Más | cut -d : -f 4`
	INBCAST=`/sbin/ifconfig $INIF |grep Bcast: | cut -d : -f 3 | cut -d \  -f 1`
	INNET=$INIP/$INMASK
fi

#if [ "$MASK" = "" -a "$1" != "stop" ]; then
#	echo "External network device $IF is not ready. Aborting.."
#	exit 2
#fi

if [ "$NAT" = "on" ]; then
	if [ "$INMASK" = "" -a "$1" != "stop" ]; then
		echo "Internal network device $INIF is not ready. Aborting.."
		exit 3
	fi
fi

# --(Helper Functions)--

# Scrub data parameters before use
scrub_parameters () {
	target=`echo $target | sed 's/ //'g`
	port=`echo $port | sed 's/ //'g |  sed "s/-/:/"`
	ext_port=`echo $ext_port | sed 's/ //'g |  sed "s/-/:/"`
	int_port_dashed=`echo $int_port | sed 's/ //'g |  sed "s/:/-/"`
	int_port=`echo $int_port | sed 's/ //'g |  sed "s/-/:/"`
	if [ "$target" == "everyone" ]; then target=0/0
	else if [ "$target" == "firewall" ]; then target=$IP
	else if [ "$target" == "lan" ]; then target=$INNET
	fi fi fi
}


# --(Control Functions)--

# Create Firestarter lock file
lock_firestarter () {
	if [ -e /var/lock/subsys ]; then
		touch /var/lock/subsys/firestarter
	else
		touch /var/lock/firestarter
	fi
}

# Remove Firestarter lock file
unlock_firestarter () {
	if [ -e /var/lock/subsys ]; then

		rm -f /var/lock/subsys/firestarter
	else
		rm -f /var/lock/firestarter
	fi
}

# Start system DHCP server
start_dhcp_server () {
	if [ "$DHCP_DYNAMIC_DNS" = "on" ]; then
		NAMESERVER=
		# Load the DNS information into the dhcp configuration
		while read keyword value garbage
			do
			if [ "$keyword" = "nameserver" ]; then
				if [ "$NAMESERVER" = "" ]; then
					NAMESERVER="$value"
				else
					NAMESERVER="$NAMESERVER, $value"
				fi
			fi
			done < /etc/resolv.conf

		if [ "$NAMESERVER" != "" ]; then
			if [ -f /etc/dhcpd.conf ]; then
				sed "s/domain-name-servers.*$/domain-name-servers $NAMESERVER;/" /etc/dhcpd.conf > /etc/dhcpd.conf.tmp
				mv /etc/dhcpd.conf.tmp /etc/dhcpd.conf
			fi
			if [ -f /etc/dhcp3/dhcpd.conf ]; then
				sed "s/domain-name-servers.*$/domain-name-servers $NAMESERVER;/" /etc/dhcp3/dhcpd.conf > /etc/dhcp3/dhcpd.conf.tmp
				mv /etc/dhcp3/dhcpd.conf.tmp /etc/dhcp3/dhcpd.conf
			fi
		else
			echo -e "Warning: Could not determine new DNS settings for DHCP\nKeeping old configuration"
		fi
	fi

   if [ -e /etc/init.d/dhcp3-server ]; then
		/etc/init.d/dhcp3-server restart > /dev/null
	elif [ -e /etc/init.d/dhcpd ]; then
		  /etc/init.d/dhcpd restart > /dev/null
	elif [ -e /etc/init.d/dnsmasq ]; then
		  /etc/init.d/dnsmasq restart > /dev/null
	else
		/usr/sbin/dhcpd 2> /dev/null
	fi

	if [ $? -ne 0 ]; then
		echo Failed to start DHCP server
		exit 200
	fi
}

# Start the firewall, enforcing traffic policy
start_firewall () {
	lock_firestarter
	source /etc/firestarter/firewall 2>&1
	retval=$?
	if [ $retval -eq 0 ]; then
		echo "Firewall started"
	else
		echo "Firewall not started"
		unlock_firestarter
	exit $retval
fi
}

# Stop the firewall, traffic flows freely
stop_firewall () {
	$IPT -F
	$IPT -X
	$IPT -Z
	$IPT -P INPUT ACCEPT
	$IPT -P FORWARD ACCEPT
	$IPT -P OUTPUT ACCEPT
	$IPT -t mangle -F 2>/dev/null
	$IPT -t mangle -X 2>/dev/null
	$IPT -t mangle -Z 2>/dev/null
	$IPT -t nat -F 2>/dev/null
	$IPT -t nat -X 2>/dev/null
	$IPT -t nat -Z 2>/dev/null
	retval=$?
	if [ $retval -eq 0 ]; then
		unlock_firestarter
		echo "Firewall stopped"
	fi
	exit $retval
}

# Lock the firewall, blocking all traffic
lock_firewall () {
	$IPT -P INPUT DROP
	$IPT -P FORWARD DROP
	$IPT -P OUTPUT DROP
	$IPT -F;
	$IPT -X
	$IPT -Z
	retval=$?
	if [ $? -eq 0 ]; then
		echo "Firewall locked"
	fi
	exit $retval
}

# Report the status of the firewall
status () {
	if [ -e /var/lock/subsys/firestarter -o -e /var/lock/firestarter ]; then
		echo "Firestarter is running..."
	else
		echo "Firestarter is stopped"
	fi
}

case "$1" in
start)
	start_firewall
 	if [ "$NAT" = "on" -a "$DHCP_SERVER" = "on" ]; then
		start_dhcp_server
	fi
;;
stop)
	stop_firewall
;;
lock)
	lock_firewall
;;
status)
	status
;;
reload-inbound-policy)
	source /etc/firestarter/inbound/setup 2>&1
;;
reload-outbound-policy)
	source /etc/firestarter/outbound/setup 2>&1
;;
*)
	echo "usage: $0 {start|stop|lock|status}"
	exit 1
esac
exit 0

---

### Post by Hei Ku on 2008-12-13
Hmmm, parece estar bien.

Si ponés:
```

sudo /etc/firestarter/firestarter.sh

```

Que error te tira?

---

### Post by deafters on 2008-12-13
> **Hei Ku said:**
> Hmmm, parece estar bien.

Si ponés:
```

sudo /etc/firestarter/firestarter.sh

```

Que error te tira?

ningun error me tira , pero en la linea de comados sale lo siguiente:
usage: /etc/firestarter/firestarter.sh {start|stop|lock|status} y vuelve al interprete de comandos

---

### Post by Hei Ku on 2008-12-13
Perdón, me olvidé de decirte yo.

```

sudo /etc/firestarter/firestarter.sh stop
sudo /etc/firestarter/firestarter.sh start

```

---

### Post by deafters on 2008-12-13
> **Hei Ku said:**
> Perdón, me olvidé de decirte yo.

```

sudo /etc/firestarter/firestarter.sh stop
sudo /etc/firestarter/firestarter.sh start

```

sandro@sandro-desktop:~$ sudo /etc/firestarter/firestarter.sh stop
[sudo] password for sandro: 
Firewall stopped

sandro@sandro-desktop:~$ sudo /etc/firestarter/firestarter.sh start
Firewall started
Failed to start DHCP server
sandro@sandro-desktop:~$ 

aparentemente no puede arrancar el servidor dhcp ( aunque si me fijo en la interface del firestarter el dhcp es habilitado), che mil gracias por la ayuda jamas pense que esta comunidad me podia llegar a dar tanta pelota por ser nuevo, SUPER AGRADECIDO Y ESTOY APRENDIENDO UNA BANDA DE COSAS, MILLON DE GRACIAS !!!!

---

### Post by deafters on 2008-12-13
YAHOOOOOOOOOO LO SOLUCIONE!!!!!!
les cuento que hice, como conte en mi post anterior note ese :Failed to start DHCP server
así que fui a lo mas facil e instale el gdhcpd y asi re configure el dhcp y lo puse a correr luego arranque firestarter y voilaaaaaa todo funcionado sin error alguno 
millon euros de gracias a todos los que me prestaron su tiempo ( EN ESPECIAL A HEI KU, GUILLERMOLISI, HICTIO, Y MHOYOS)

---

### Post by Hei Ku on 2008-12-13
Me alegro!!
Queremos medallitas!! :D

---

### Post by guillermolisi on 2008-12-15
> **deafters said:**
> YAHOOOOOOOOOO LO SOLUCIONE!!!!!!
les cuento que hice, como conte en mi post anterior note ese :Failed to start DHCP server
así que fui a lo mas facil e instale el gdhcpd y asi re configure el dhcp y lo puse a correr luego arranque firestarter y voilaaaaaa todo funcionado sin error alguno 
millon euros de gracias a todos los que me prestaron su tiempo ( EN ESPECIAL A HEI KU, GUILLERMOLISI, HICTIO, Y MHOYOS)

Bueno, ahora que salio el tema, tuve un problema parecido hace tiempo y resulto que para que Firestarter funcione bien tenes que tener instalados los paquetes bind y dhcp (client).

Lo importante es que funciono y aprendiste algo mas.
Felicitaciones (y animate y hacele click a la medallita :p )

---

### Post by deafters on 2008-12-16
saludos muchachos, ya fueron las medallitas para ambos ;), perdón por la tardanza en hacerlo pero no me daba cuenta del tema de la medallita y pensé que era una broma por lo de patan en el escuadrón diabólico  jajajajajajjajajajaj

):P

---


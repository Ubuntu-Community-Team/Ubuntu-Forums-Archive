---
title: "Conexión ADSL Sion - ayuuuda"
date: 2008-05-26
forum: Software
---

### Post by athnea on 2008-05-26
Ayer instalé Ubuntu y estoy tratando de configurar internet. La conexión es ADSL y bastante difícil de hacer. Encontré unas páginas que explican cómo instalar con mi servidor (SION), pero seguí sus instrucciones sin éxito. Entre sí varían un poco, pero ninguna funcionó.
Ya no sé qué hacer. Tampoco sé qué postear. Cuando termino de hacer todo y ejecuto "sudo pon sion debug dump logfd 2 nodetach", me salta un texto enorme con toda clase de errores, que varían según la forma de configurar internet que haya aplicado. 
Para quien pueda (y amablemente quiera) ayudarme, ¿qué datos son necesarios?
Comienzo dejando los links de las páginas.


1. [http://www.yoreparo.com/foros/linux/152772.html](http://www.yoreparo.com/foros/linux/152772.html) --> el último post
2. [https://lists.ubuntu.com/archives/ubuntu-es/2006-March/013499.html](https://lists.ubuntu.com/archives/ubuntu-es/2006-March/013499.html) --> una seguidilla de preguntas y respuestas
3. [http://sicarul.blogspot.com/2007/01/linux-sion.html](http://sicarul.blogspot.com/2007/01/linux-sion.html)

¡Ayuuuuuda!

---

### Post by leonardo83 on 2008-05-26
Bueno, no estoy muy al tanto deSION pero decime, eso no es cable modem no?
Te conectas por placa de red?
si es asi (al menos como yo hice con speedy) podes usar la configuracion ppoeconfig para crear la conexion, sino danos mas detalles que si puedo te tiro una mano (igual hace poco domino linux pero puedo ayudarte como para devolverle el favor a la muchachada :) )

Saludos!

---

### Post by athnea on 2008-05-26
¡Hola!
No es cable módem, es una conexión por VPN. Lo que viene a ser ADSL (o si no, lo que viene a ser es que estoy mandando fruta =P). 
No se puede instalar tan fácil como cable módem (una amiga pasó de XP a Ubuntu sin tener que hacer nada complicado para conectar a Internet).
Si te fijás en los links que dejé, creo que vas a sacar más datos de los que yo pueda darte (quizá esto es facilísimo y me estoy complicando).
Por ahora no encontré modo de configurar el pptp ni nada de eso.

Gracias por la atención :)

---

### Post by athnea on 2008-05-27
este es el error que tira 


iilustra@iilustra-deska:~$ sudo pon sion debug dump logfd 2 nodetach
pppd options in effect:
debug debug		# (from command line)
nodetach		# (from command line)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-mschap-v2		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename sion		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.68.24 --nolaunchpppd		# (from /etc/ppp/peers/sion)
local		# (from /etc/ppp/options.pptp)
noaccomp		# (from /etc/ppp/options.pptp)
hide-password		# (from /etc/ppp/options)
ipcp-accept-local		# (from /etc/ppp/options.pptp)
ipcp-accept-remote		# (from /etc/ppp/options.pptp)
ipparam sion		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
proxyarp		# (from /etc/ppp/options.pptp)
usepeerdns		# (from /etc/ppp/peers/sion)
noccp		# (from /etc/ppp/options.pptp)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection refused
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.68.24
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
Couldn't get channel number: Input/output error
Script pptp 172.16.68.24 --nolaunchpppd finished (pid 5911), status = 0x1

---

### Post by faktorqm on 2008-05-27
Bueno voy a intentar algo. La proxima las salidas de comandos entre tags de code por favor....

El plug-in del network manager para pptp, el pptp y el ppp:

```
sudo apt-get install network-manager-pptp pptp-linux ppp pppconfig
```

Luego de eso, tenes que averiguar que tipo de autenticacion usa sion para darte internet, vi por ahi que pap, o sea, sin autenticacion, pero si es asi, debes "sacar" chap, mschap, y otras mas de un archivo.

El del blog difiere mucho con el de yoreparo, y el de la lista de mail no explica nada me parece. Proba tambien de darle "sudo pon sion" asi de una. Salu2!

---

### Post by athnea on 2008-05-27
Hola, gracias por la respuesta.
Sion es PAP. No entiendo cómo se "sacan" las opciones que me dijiste. 

Después de mi post, modifiqué unas cosas y este es el nuevo error que me tira.


```
iilustra@iilustra-deska:~$ sudo pon sion debug dump logfd 2 nodetach 
[sudo] password for iilustra: 
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename sion		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
usepeerdns		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x85da79a1> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x2df72b5c> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x2df72b5c> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x85da79a1> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0x2df72b5c]
sent [LCP EchoRep id=0x0 magic=0x85da79a1]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x1 <addr 200.81.163.146> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.163.146> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.163.146> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 200.81.163.146> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
replacing old default route to eth0 [172.16.68.1]
local  IP address 200.81.163.146
remote IP address 200.69.45.2
primary   DNS address 200.69.32.5
secondary DNS address 200.69.32.9
Script /etc/ppp/ip-up started (pid 6014)
Script /etc/ppp/ip-up finished (pid 6014), status = 0x0
rcvd [LCP TermReq id=0x2 "Peer not responding"]
LCP terminated by peer (Peer not responding)
Connect time 0.3 minutes.
Sent 255662020 bytes, received 0 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 6021)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 6021), status = 0x0
Script pptp 172.16.1.2 --nolaunchpppd finished (pid 6002), status = 0x0
Modem hangup
Connection terminated.
```

¿Avancé o retrocedí? ¿Qué me está faltando?
No puedo ejecutar solo "sudo pon sion".

Edit: mis datos en cmd->ipconfig.

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 172.16.68.24
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   : 172.16.68.1

Adaptador PPP SION               :

        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 200.81.161.11
        Máscara de subred . . . . . . . . : 255.255.255.255
        Puerta de enlace predeterminada   : 200.81.161.11

dns primario: 172.16.1.5
dns secundario: 172.16.1.3 (son diferentes a los que aparecen en el code)


Muchas gracias por la ayuda, me estoy volviendo loca.

---

### Post by faktorqm on 2008-05-27
Avanzaste. Instalaste los paquetes que te dije o hiciste otra cosa?

Mas alla de eso, ahi lo que veo yo, es que la direccion IP tuya es 172.16.68.24 y en la ULTIMA salida del comando sale 172.16.1.2, cuando en la ANTERIOR salia (la que me parece a mi que es la correcta) 172.16.68.24.
No se de donde lo habras cambiado pero para mi ahi "hay una punta", cambialo y volve a probar. 

Te hablo de esta linea:

```

iilustra@iilustra-deska:~$ sudo pon sion debug dump logfd 2 nodetach 
[sudo] password for iilustra: 
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename sion		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
[COLOR="Red"]**_pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)_**[/COLOR]
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
usepeerdns		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 1
Using interface ppp0
.....

```

Te dije lo del sudo pon solo por que en el blog lo hacia asi el chabon. Salu2!

---

### Post by athnea on 2008-05-28
¡Vamos que de a poco se puede!
Gran avance: logré que conectara. Pero a una velocidad de módem de 56 k (y tengo 6 megas de velocidad) y desconectándose en menos de 8 minutos. 

Así se ve en la terminal:

```
Script /etc/ppp/ip-up started (pid 7119)
Script /etc/ppp/ip-up finished (pid 7119), status = 0x0
```
[COLOR="Red"]
Esto es mientras que internet funciona[/COLOR]

```
Terminating on signal 2
Child process pptp 172.16.1.2 --nolaunchpppd (pid 7114) terminated with signal 2
Modem hangup
Connect time 8.5 minutes.
Sent 270859 bytes, received 816223 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 7167)
Connection terminated.
Script /etc/ppp/ip-down finished (pid 7167), status = 0x0
```

[COLOR="Red"]Y ahí se corta.[/COLOR]

Toqueteé tanto que no sé bien qué hice. De hecho, creo que deshaciendo cambios sucedió este medio milagro. Ahora el asunto es que funcione a velocidad promedio y no se corte. ¡Ayyuuuuda!


Dejo cómo tengo todo configurado. Si algún dato es imprudente, porfa avisen. Espero que estos datos sean útiles para algún usuario de sion con mi mismo problema 

/etc/ppp/options.pptp
```

# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
#refuse-eap
#refuse-chap
#refuse-mschap

# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate

# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose with of the following sections you will use. Note that MPPE
# requires the use of MSCHAP-V2 during authentication)

# http://ppp.samba.org/ the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
#require-mppe-128
# }}}

# http://polbox.com/h/hs001/ fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}
```

/etc/ppp/pap-secrets

```
# Secrets for authentication using PAP
# client server secret IP addresses
contrarebelion * (password)
```

pap-secrets
```

#!/bin/sh
#
# This script is run by pppd when there's a successful ppp connection.
#
PRIMARY=eth1
SERVER=172.16.1.2
CONNECTION=$6
if [ "${CONNECTION}" = "" ]; then
CONNECTION=${PPP_IPPARAM}; fi
TUNNEL=$1
if [ "${TUNNEL}" = "" ]; then
TUNNEL=$[PPP_IFACE]; fi
if [ "${CONNECTION}" = "sion" ] ; then
/sbin/route add -host ${SERVER} dev ${PRIMARY}
/sbin/route del default ${PRIMARY}
/sbin/route add default gw $5 dev ${TUNNEL}

fi
```


ip down

```

#!/bin/sh
#
# This script is run by the pppd _after_ the link is brought down.
# It uses run-parts to run scripts in /etc/ppp/ip-down.d, so to delete
# routes, unset IP addresses etc. you should create script(s) there.
#
# Be aware that other packages may include /etc/ppp/ip-down.d scripts (named
# after that package), so choose local script names with that in mind.
#
# This script is called with the following arguments:
#    Arg  Name                          Example
#    $1   Interface name                ppp0
#    $2   The tty                       ttyS1
#    $3   The link speed                38400
#    $4   Local IP number               12.34.56.78
#    $5   Peer  IP number               12.34.56.99
#    $6   Optional ``ipparam'' value    foo

# The  environment is cleared before executing this script
# so the path must be reset
PATH=/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin
export PATH

# These variables are for the use of the scripts run by run-parts
PPP_IFACE="$1"
PPP_TTY="$2"
PPP_SPEED="$3"
PPP_LOCAL="$4"
PPP_REMOTE="$5"
PPP_IPPARAM="$6"
export PPP_IFACE PPP_TTY PPP_SPEED PPP_LOCAL PPP_REMOTE PPP_IPPARAM

# as an additional convenience, $PPP_TTYNAME is set to the tty name,
# stripped of /dev/ (if present) for easier matching.
PPP_TTYNAME=`/usr/bin/basename "$2"`
export PPP_TTYNAME 

# If /var/log/ppp-ipupdown.log exists use it for logging.
if [ -e /var/log/ppp-ipupdown.log ]; then
  exec >> /var/log/ppp-ipupdown.log 2>&1
  echo $0 $*
  echo
fi

# This script can be used to override the .d files supplied by other packages.
if [ -x /etc/ppp/ip-down.local ]; then
  exec /etc/ppp/ip-down.local "$*"
fi

run-parts /etc/ppp/ip-down.d \
  --arg="$1" --arg="$2" --arg="$3" --arg="$4" --arg="$5" --arg="$6"
```


peers sion
```

pty "pptp 172.16.1.2 --nolaunchpppd"
name contrarebelion
remotename sion
file /etc/ppp/options.pptp
ipparam sion
usepeerdns
defaultroute
replacedefaultroute

```


Inicié sesión con 
```
sudo pon sion debug dump logfd 2 nodetach

```

Una cosa que hice fue agregar un route con 
```
sudo route add host 172.16.1.2 gw 172.16.68.1

```

No tengo la menor idea de si eso funcionó.
También puse 
```
route add default gw 172.16.68.1
```

---

### Post by faktorqm on 2008-05-28
Bueno, vamos por partes, primero que nada, gracias por postear todo, sos una buena forera. 

Con lo del default route gw la limaste, asi que eso no va. Igual no te preocupes que cada vez que reinicias se "borra".

"Espero que estos datos sean útiles para algún usuario de sion con mi mismo problema" -> si, quedate tranquila que del resultado de esto vamos a hacer un tutorial seguro...

En este archivo, (DEJANDO EL RESTO DE LOS ARCHIVOS COMO ESTAN) 
/etc/ppp/options.pptp agrega la primera linea.

```

#Lock the port
lock

# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
#refuse-eap
#refuse-chap
#refuse-mschap

# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate

# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose with of the following sections you will use. Note that MPPE
# requires the use of MSCHAP-V2 during authentication)

# http://ppp.samba.org/ the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
#require-mppe-128
# }}}

# http://polbox.com/h/hs001/ fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}

```

Volve a probar ahi. y tambien postea la salida del comando y /var/log/ppp.log y la salida del comando "sudo ifconfig" asi vemos que puede llegar a pasar. Salu2!!

---

### Post by athnea on 2008-05-28
¡Hola! Gracias por tu ayuda!
Aquí van los resultados:

[COLOR="DarkOrange"]EDIT: ERROR DE NOVATA[/COLOR]

Acostumbrada al bloc de textos de win, cometí el siguiente error: no copié desde el comienzo el archivo de option.pptp. Recién me di cuenta de que cuando abro algo con el gedit, se abre a partir de la línea que modifiqué por última vez. Asi que las dos veces que lo abrí, la parte arriba de "autorization" no aparecía, pero sí la tenía. Así que lo que sigue a continuación no sirve, porque [COLOR="DarkOrange"]ya tenía la línea de lock[/COLOR].

**Modificando la línea que dijiste ("lock")**:

```
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename sion		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
usepeerdns		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x23cd834a> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0xeadde45d> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0xeadde45d> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x23cd834a> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0xeadde45d]
sent [LCP EchoRep id=0x0 magic=0x23cd834a]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x1 <addr 200.81.160.54> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.160.54> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 200.81.160.54> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
replacing old default route to eth0 [172.16.68.1]
local  IP address 200.81.160.54
remote IP address 200.69.45.2
primary   DNS address 200.69.32.5
secondary DNS address 200.69.32.9
Script /etc/ppp/ip-up started (pid 5982)
Script /etc/ppp/ip-up finished (pid 5982), status = 0x0
rcvd [LCP TermReq id=0x2 "Peer not responding"]
LCP terminated by peer (Peer not responding)
Connect time 0.4 minutes.
Sent 309160068 bytes, received 0 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 5992)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 5992), status = 0x0
Script pptp 172.16.1.2 --nolaunchpppd finished (pid 5971), status = 0x0
Modem hangup
Connection terminated.
```

No hubo conexión, o duró muy poco. 

----

No encontré el archivo ppp.log, pero en la misma carpeta hay uno llamado **ppp-connect-errors**. No sé si servirá, pero por las dudas posteo.

```

anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.1.2
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection refused
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.68.24
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection refused
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.68.24
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection refused
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.68.24
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection refused
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 172.16.68.24
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection timed out
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 200.81.161.145
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: Connection timed out
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 200.81.161.145
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
```

**Sudo ifconfig**

```
eth0      Link encap:Ethernet  direcciónHW 00:50:fc:97:f7:f5  
          inet dirección:172.16.68.24  Difusión:172.16.68.255  Máscara:255.255.255.0
          dirección inet6: fe80::250:fcff:fe97:f7f5/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:41969 (40.9 KB)  TX bytes:7400 (7.2 KB)
          Interrupción:5 Dirección base: 0xd400 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:1034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1034 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:51700 (50.4 KB)  TX bytes:51700 (50.4 KB)
```


> **faktorqm said:**
> Con lo del default route gw la limaste, asi que eso no va. Igual no te preocupes que cada vez que reinicias se "borra".

Andá a saber la fruta que me mandé siguiendo instrucciones que leí en internet :P

¡Muchas gracias por tu ayuda! Y sí, un tutorial, para sacar algo bueno de este sufrimiento :P

¡Saludos!



---------------------- Edit --------------------
PD: Volviendo muy atrás, faktorqm, me habías dicho que instalara el plug-in del network manager para pptp, el pptp y el ppp. Lo que yo tengo instalado es network-manager-pptp_0.6.5+svnhead2574-0ubuntu1_i386.deb, ¿es lo mismo? No hice lo de "sacar" las opciones chap y mschap porque no sé cómo hacerlo. Quizá esto no sea necesario, pero aclaro por las dudas :)


PD2: En la página [https://lists.ubuntu.com/archives/ubuntu-es/2006-March/013499.html](https://lists.ubuntu.com/archives/ubuntu-es/2006-March/013499.html) comienza una seguidilla de mensajes que pueden ser interesantes si sabés de lo que hablan (no como yo). El pibe tenía un problema similar al mío y al final se puede conectar. Además aparece cómo él tiene configurados los archivos de /etc/ppp/. Quizá a vos te pueda resultar útil ver esos mensajes. De ahí saqué lo de "add route", porque aparentemente eso era lo que le faltaba al pibe.



[QUOTE=happy ending del problema]

> Podrias probar lo siguiente:
> route add -host 172.16.1.2 gw 172.16.49.1
>
> luego agregar las lineas al final de /etc/ppp/peers/sion:
> defaultroute
> replacedefaultroute
>
> luego ejecutas
> sudo pon sion debug dump logfd 2 nodetach
>
> y nos cuentas :)

Pues Sí, muchísimas gracias.
Este es mi primer mail enviado desde mi nuevo Ubuntu.
Te agradezco infinitamente tu ayuda y a los demás que hacen igual que tú.
En cuanto pueda organizarme un poco (bajar de los repositorios y
configurar), trataré de hacer un tutorial para que los próximos la
tengan más fácil.[/QUOTE]

---

### Post by athnea on 2008-05-28
Hoy probé de nuevo con la configuración como estaba ayer --> **no funcionó**. Lo que sí, no puse nada de route. ¿Habrá sido esa la diferencia? Porque hoy me tiró los errores habituales.

Por otro lado, no posteé el **/etc/ppp/options**, así que acá va:
```

# /etc/ppp/options
lock
hide-password
noipx
# ---<End of File>---
```

Dejo resultado de un ping

```
iilustra@iilustra-deska:~$ sudo ping 200.69.45.2
PING 200.69.45.2 (200.69.45.2) 56(84) bytes of data.
```

Un route

```
iilustra@iilustra-deska:~$ sudo route
Tabla de rutas IP del núcleo
Destino Puerta de Enlace Genmask Banderas Metrica Ref Uso Interfaz
172.16.68.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
```

netstat -r

```
iilustra@iilustra-deska:~$ sudo netstat -r
Tabla de rutas IP del núcleo
Destino Puerta de Enlace Genmask Banderas MSS Ventana irtt Interfaz
172.16.68.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         172.16.68.1     0.0.0.0         UG        0 0          0 eth0

```

(No sé si servirá de algo, pero si se lo compara con el pibe del link que dejé en el post anterior, difiere en el 255.255.255.0 y el 255.255.0.0).

---

### Post by Sicarul on 2008-05-28
Hola, antes que nada me presento, soy Pablo Seibelt, athnea me encontro y me envio un e-mail por un post en mi blog en el que explicaba como hice funcionar Sion. ([http://sicarul.blogspot.com/2007/01/linux-sion.html]("http://sicarul.blogspot.com/2007/01/linux-sion.html"))

Antes que nada, te recomiendo que por las dudas revises o 1° en una computadora con Windows o 2° preguntandole a Sion, si tenes bien todos los datos, y tambien fijate bien por que creo que hay otros programas para conectarte.

Esa configuracion me andaba a veces si a veces no, velocidades medio raras, a veces si a veces no, y encima incluso con windows se cortaba todo el tiempo Sion, desrecomendado al 100%, pero si no tenes otra opcion por X motivo que usar Sion, yo diria que sigas probando configuraciones y vayas documentando/anotando lo mas posible todas las cosas raras que hagas, por que si con un comando lo haces andar despues te podes hacer un script que al inicio corra ese comando y listo.

Yo me acuerdo de tocar algo de las route y que me ayudara, pero no se, el resto esta todo en mi blog, ya ni me acuerdo como hice me pase a Fibertel y se corta una vez cada 3 meses un par de minutos, Sion se cortaba un promedio de 2-3 veces por dia, a veces mas, era insoportable.

Saludos y disculpas por no poder ayudar mas, ojala te sirva y puedas solucionar tu problema(La mejor solucion es cambiar a otro proveedor, creeme, pero sino, la mejor de las suertes en hacerlo andar, yo se que se puede, a no perder las esperanzas!).

---

### Post by athnea on 2008-05-29
Gracias, Sicarul. Lamentablemente me tengo que quedar con Sion que, dicho sea de paso, me está funcionando muy bien. Pero sí, sería más fácil tener un bendito módem y ahorrarme todos estos problemas.

Una cosa de la que me di cuenta... no me funciona el network manager. Cuando intento ejecutar el nm-applet, titilan el iconito de red y me tira un error. 

```
** (network-admin:5880): CRITICAL **: Unable to lookup session information for process '5880'

(network-admin:5880): Gtk-WARNING **: Unknown property: GtkComboBox.items
```

Hasta ahora no configuré una cuenta VPN en las conexiones de red... ¿será ese mi problema? Antes faktorqm me dijo que instalara el network manager pero no sabía que era un programa :P (pensé que era algo así como archivos, jiji). Y ahora que me doy cuenta de que es un programa, no lo puedo ejecutar.

(Probablemente me quieran matar cuando lean que durante todo este tiempo no configuré nada en la red)

---

### Post by faktorqm on 2008-05-29
ajá!! te deschavaste sola! :P

Bueno, esto es un gran gran gran bardo, asi que voy a intentar generar un "como" de como tendrias que tener las cosas, pero quedate tranquila que estamos a punto de conectarnos :P

abri la terminal y escribi:
 
```
sudo ifconfig eth0 172.16.68.24 netmask 255.255.255.0 broadcast 172.16.68.255
```

```
route add default gw 172.16.68.1
``` (éste si estaba bien)

```
sudo gedit /etc/resolv.conf
```

borras todo lo que haya y ahi pegas esto:

```

nameserver 172.16.1.5
nameserver 172.16.1.3

```

Guardas y cerras, asi volvemos a la terminal.
Ahora entramos a comparar los contenidos de los archivos, lo que yo te decia que quitaras las autenticaciones es en este archivo que te tiene que quedar asi:

/etc/ppp/options.pptp

```

debug
lock

# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do EAP, CHAP, or MSCHAP, MSCHAP-V2
refuse-eap
refuse-chap
refuse-mschap
refuse-mschap-v2

# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate

# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose with of the following sections you will use. Note that MPPE
# requires the use of MSCHAP-V2 during authentication)

# http://ppp.samba.org/ the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
#require-mppe-128
# }}}

# http://polbox.com/h/hs001/ fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}

```

/etc/ppp/peers/sion

```

pty "pptp 172.16.1.2 --nolaunchpppd"
noauth
name contrarebelion
remotename PPTP
file /etc/ppp/options.pptp
persist
ipparam sion
noipdefault
defaultroute
proxyarp

```

Los archivos:

/etc/ppp/options
/etc/ppp/pap-secrets
/etc/ppp/ip-up
/etc/ppp/ip-down

No los toques!!!! Solo asegurate obviamente de que en pap-secrets esta bien puesta la contraseña y el usuario :P

Bueno, ahi vamos a probar con sudo pon sion debug blabla y te fijas que pasa. Si no anda, ahora si por favor volve a postear ifconfig, route, netstat -r, y la salida obviamente, y si encontras algo en los errores... capaz lo podemos usar.

Lo del network-admin lo hiciste desde a interfaz grafica y no pasa nada? Y en sistemas -> administracion -> red? hacerlo por interfaz grafica es lo mismo que los comandos que te puse arriba. el del ifconfig y route. 

Bueno, espero que haya servido, Salu2!!

---

### Post by athnea on 2008-05-29
> **faktorqm said:**
> ajá!! te deschavaste sola! :P

Y bueno. Desde el comienzo debí dejar autorización expresa para ser tratada como una idiota :P Imaginate que esto es un fascículo de "ubuntu for dummies".

> **faktorqm said:**
> 
Bueno, esto es un gran gran gran bardo, asi que voy a intentar generar un "como" de como tendrias que tener las cosas, pero quedate tranquila que estamos a punto de conectarnos :P 

¡¡No sé cómo agradecerte la ayuda!! Pero aún no funciona :(


Paso acá los resultados de cada acción.

**sudo ifconfig eth0 172.16.68.24 netmask 255.255.255.0 broadcast 172.16.68.255**

```
iilustra@iilustra-deska:~$ sudo ifconfig eth0 172.16.68.24 netmask 255.255.255.0 broadcast 172.16.68.255
iilustra@iilustra-deska:~$ 
```

Así se ve en mi terminal. O sea: no dice si lo aceptó o no. Igual, no sé si así debería ser.

**route add default gw 172.16.68.1**

```
iilustra@iilustra-deska:~$ sudo route add default gw 172.16.68.1
iilustra@iilustra-deska:~$ 
```

(después de probar de conectar, reinicié y volví a poner este comando. Ahí apareció 
```
iilustra@iilustra-deska:~$ sudo route add default gw 172.16.68.1
SIOCADDRT: El fichero ya existe)
```

**sudo gedit /etc/resolv.conf**

Lo abrí y me apareció tal cual habías escrito en el post.

Agregué 
```
refuse-eap
refuse-chap
refuse-mschap
refuse-mschap-v2
```
en options.pptp

Y cambié
```
#Lock the port
lock
```
(así estaba antes)
por
```
debug
lock
```
tal como dijiste.

puse "**pon sion**..."

```
sudoiilustra@iilustra-deska:~$ sudo pon sion dump debug logfd 2 nodetach
[sudo] password for iilustra: 
pppd options in effect:
debug debug		# (from command line)
nodetach		# (from command line)
persist		# (from /etc/ppp/peers/sion)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-mschap-v2		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename sion		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
noipdefault		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 20
Using interface ppp1
Connect: ppp1 <--> /dev/pts/3
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbca5272c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbca5272c> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbca5272c> <pcomp> <accomp>]
Terminated
Script pptp 172.16.1.2 --nolaunchpppd finished (pid 6275), status = 0x8f
Modem hangup
Connection terminated.
using channel 21
Using interface ppp0
Connect: ppp0 <--> /dev/pts/3
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x400951e4> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x400951e4> <pcomp> <accomp>]
sent [LCP ConfNak id=0x2 <magic 0xd11b0e45>]
rcvd [LCP ConfNak id=0x2 <magic 0xd11b0e45>]
sent [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0x99d67d88> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0x99d67d88> <pcomp> <accomp>]
sent [LCP ConfNak id=0x3 <magic 0x1abf6740>]
rcvd [LCP ConfNak id=0x3 <magic 0x1abf6740>]
sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0x8a291292> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0x8a291292> <pcomp> <accomp>]
sent [LCP ConfNak id=0x4 <magic 0xe761a5b0>]
rcvd [LCP ConfNak id=0x4 <magic 0xe761a5b0>]
sent [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0xa66078cc> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0xa66078cc> <pcomp> <accomp>]
sent [LCP ConfNak id=0x5 <magic 0x6e4acb73>]
rcvd [LCP ConfNak id=0x5 <magic 0x6e4acb73>]
sent [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0xecc85d3f> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0xecc85d3f> <pcomp> <accomp>]
sent [LCP ConfNak id=0x6 <magic 0xd59fcefa>]
rcvd [LCP ConfNak id=0x6 <magic 0xd59fcefa>]
sent [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0xc49cb1de> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0xc49cb1de> <pcomp> <accomp>]
sent [LCP ConfNak id=0x7 <magic 0xbcd81c73>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x874473c8> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x874473c8> <pcomp> <accomp>]
sent [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0xc49cb1de> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x7 <asyncmap 0x0> <magic 0xc49cb1de> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0x874473c8]
sent [LCP EchoRep id=0x0 magic=0xc49cb1de]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x1 <addr 200.81.163.195>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.163.195>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 200.81.163.195>]
[COLOR="Red"]replacing old default route to eth0 [172.16.68.1]
local  IP address 200.81.163.195
remote IP address 200.69.45.2[/COLOR]
Script /etc/ppp/ip-up started (pid 6292)
Script /etc/ppp/ip-up finished (pid 6292), status = 0x0
rcvd [LCP EchoReq id=0x1 magic=0x874473c8]
sent [LCP EchoRep id=0x1 magic=0xc49cb1de]
rcvd [LCP EchoReq id=0x2 magic=0x874473c8]
sent [LCP EchoRep id=0x2 magic=0xc49cb1de]
rcvd [LCP EchoReq id=0x3 magic=0x874473c8]
sent [LCP EchoRep id=0x3 magic=0xc49cb1de]
rcvd [LCP TermReq id=0x2 "Peer not responding"]
LCP terminated by peer (Peer not responding)
Connect time 0.4 minutes.
Sent 293986189 bytes, received 48 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 6297)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 6297), status = 0x7
Script pptp 172.16.1.2 --nolaunchpppd finished (pid 6283), status = 0x0
Modem hangup
Connection terminated.
using channel 24
Using interface ppp1
Connect: ppp1 <--> /dev/pts/3
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x8fb23d54> <pcomp> <accomp>]
sent [LCP ConfReq id=0x8 <asyncmap 0x0> <magic 0x94967873> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x8fb23d54> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x8 <asyncmap 0x0> <magic 0x94967873> <pcomp> <accomp>]
sent [PAP AuthReq id=0x2 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0x8fb23d54]
sent [LCP EchoRep id=0x0 magic=0x94967873]
rcvd [PAP AuthAck id=0x2 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x3 <addr 200.81.161.131>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 200.81.161.131>]
rcvd [IPCP ConfAck id=0x4 <compress VJ 0f 01> <addr 200.81.161.131>]
replacing old default route to eth0 [172.16.68.1]
local  IP address 200.81.161.131
remote IP address 200.69.45.2
Script /etc/ppp/ip-up started (pid 6310)
Script /etc/ppp/ip-up finished (pid 6310), status = 0x0
```

Y así continuaba una y otra vez hasta que me cansé.
Un pregunta: ¿está bien que aparezca lo que marqué en rojo?

**ifconfig**

```
iilustra@iilustra-deska:~$ sudo ifconfig
[sudo] password for iilustra: 

eth0      Link encap:Ethernet  direcciónHW 00:50:fc:97:f7:f5  

          inet dirección:172.16.68.24  Difusión:172.16.68.255  Máscara:255.255.255.0

          dirección inet6: fe80::250:fcff:fe97:f7f5/64 Alcance:Vínculo

          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1

          RX packets:2450 errors:0 dropped:0 overruns:0 frame:0

          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0

          colisiones:0 txqueuelen:1000 

          RX bytes:355459 (347.1 KB)  TX bytes:58634 (57.2 KB)

          Interrupción:5 Dirección base: 0xd400 



lo        Link encap:Bucle local  

          inet dirección:127.0.0.1  Máscara:255.0.0.0

          dirección inet6: ::1/128 Alcance:Anfitrión

          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1

          RX packets:116 errors:0 dropped:0 overruns:0 frame:0

          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0

          colisiones:0 txqueuelen:0 

          RX bytes:5800 (5.6 KB)  TX bytes:5800 (5.6 KB)



ppp0      Link encap:Protocolo punto a punto  

          inet dirección:200.81.161.121  P-t-P:200.69.45.2  Máscara:255.255.255.255

          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1450  Metric:1

          RX packets:5 errors:0 dropped:0 overruns:0 frame:0

          TX packets:355238 errors:0 dropped:0 overruns:0 carrier:0

          colisiones:0 txqueuelen:3 

          RX bytes:138 (138.0 B)  TX bytes:122487528 (116.8 MB)
```


**route**
```

iilustra@iilustra-deska:~$ sudo route

Tabla de rutas IP del núcleo

Destino Puerta de Enlace Genmask Banderas Metrica Ref Uso Interfaz

200.69.45.2     *               255.255.255.255 UH    0      0        0 ppp0

172.16.68.0     *               255.255.255.0   U     0      0        0 eth0

link-local      *               255.255.0.0     U     1000   0        0 eth0

default         200.69.45.2     0.0.0.0         UG    0      0        0 ppp0

default         *               0.0.0.0         U     0      0        0 ppp0

```

**netstat -r**

```
iilustra@iilustra-deska:~$ sudo netstat -r

Tabla de rutas IP del núcleo

Destino Puerta de Enlace Genmask Banderas MSS Ventana irtt Interfaz

200.69.45.2     *               255.255.255.255 UH        0 0          0 ppp0

172.16.68.0     *               255.255.255.0   U         0 0          0 eth0

link-local      *               255.255.0.0     U         0 0          0 eth0

default         200.69.45.2     0.0.0.0         UG        0 0          0 ppp0

default         *               0.0.0.0         U         0 0          0 ppp0
```


configuración de red según aparece en **sistema &#8594; admin &#8594; red**


[B]conexión cableada &#8594; propiedades de eth0
dirección ip estática[/B]
```
dirección ip 172.16.68.24
máscara de sub-red 255.255.255.0
dirección de la puerta de enlace 172.16.68.1
```

[B]general
configuración del anfitrión[/B]
```
nombre del equipo: iilustra-deska
nombre del dominio: (nada)
```

me parece que esto no tiene nada que ver... pero el network manager no me parecía un programa :P

**dns**
```
172,16,1,5
172.16.1.
```
[B]
anfitriones[/B]
```
dirección ip		alias
127,0,1.1		iilustra-deska
::1			ip6-localhost
 ip6-loopback
fe00::0			ip6-localnet
ff00::0			ip6-mcastprefix
ff02::1			ip6-allnodes
ff02::2			ip6-allrouters
ff02::3			ip6-allhosts
```


> **faktorqm said:**
> Los archivos:

/etc/ppp/options
/etc/ppp/pap-secrets
/etc/ppp/ip-up
/etc/ppp/ip-down

No los toques!!!! 

Jajajaja, buenísima aclaración. No, no lo hice :)

> **faktorqm said:**
> Solo asegurate obviamente de que en pap-secrets esta bien puesta la contraseña y el usuario :P

Tan dummy no, por favor. Algo de orgullo tengo. O no.
Está puesto "nombre usuario * pass", sin las comillas. Y donde dice nombre usuario está mi nombre de usuario y donde dice pass está mi contraseña. Ehhh... ¿tienen que estar separadas del asterisco por un espacio? D'oh!




"Lo del network-admin lo hiciste desde a interfaz grafica y no pasa nada? Y en sistemas -> administracion -> red? hacerlo por interfaz grafica es lo mismo que los comandos que te puse arriba. el del ifconfig y route."

No puedo ejecutarlo. 

```
iilustra@iilustra-deska:~$ sudo killall nm-applet
iilustra@iilustra-deska:~$ sudo nm-applet
```

Para asegurarme de que cargue. Las computadoritas de redes titilan y aparece un triángulo con un !, que desaparece. Cuando entro en red a través del ícono:

```
(network-admin:7247): Gtk-WARNING **: Unknown property: GtkComboBox.items
** (network-admin:7247): CRITICAL **: Unable to lookup session information for process '7247'
 
```

Así que no tengo ninguna solapa de VPN ni puedo acceder haciendo clic derecho o izquierdo sobre el ícono. 


Saludos! La próxima es la vencida!!

---

### Post by faktorqm on 2008-05-30
Hola, te estaba haciendo un post re lindo y se me quedo sin espacio el disco, se me cerro el opera, y el gestor de actualizaciones se colgo asi que todo mal. fui a una consola y le puse la 28 en la cabeza al linux y se recató y cuando volvi... el opera no me guardo lo que habia escrito, de hecho no me daba la opcion para abrir sesion anterior.... asi que nada.

Te posteo cortito :P (cada cambio se suma al anterior) la onda es que estamos re bien, sobre la pista. ya conecta, autentica, y luego te tira un error, naturalmente de ruteo. (LCP significa Link Control Protocol)

1) agrega repalcedefaultroute al /etc/ppp/peers/sion y te tiene que quedar:

```

pty "pptp 172.16.1.2 --nolaunchpppd"
noauth
name contrarebelion
remotename PPTP
file /etc/ppp/options.pptp
persist
ipparam sion
noipdefault
proxyarp
defaultroute
replacedefaultroute

```

2) si sigue sin andar, agregamos usepeerdns y te tiene que quedar:

```

pty "pptp 172.16.1.2 --nolaunchpppd"
noauth
name contrarebelion
remotename PPTP
file /etc/ppp/options.pptp
persist
ipparam sion
noipdefault
proxyarp
defaultroute
replacedefaultroute
usepeerdns

```

3) Ahora si, si sigue sin andar probamos con routear a manopla:

```
sudo route add host 172.16.1.2 gw 172.16.68.1
```

aunque para mi sigue estando mal ese comando (tengo dudas acerca de su efectividad).

En la salida que posteaste, se distinguen bien 3 partes, una que conecta y rebota, otra que conecta, autentica, y rebota, y otra lo mismo que la ultima. vamos que ya estamos! :D

---

### Post by athnea on 2008-05-30
> la onda es que estamos re bien, sobre la pista.
Yo sigo con mis esperanzas en alto hasta que digas que no se puede!

](*,)

Una cosa. Cuando abrí el /etc/ppp/peers/sion (ya tipeo esa dirección hasta dormida) me di cuenta de que me faltaba la línea de proxyarp. A mí me pareció haber hecho la prueba con esa línea, porque copié lo de tu post y lo pegué. Por las dudas hice la prueba con esto:

```
pty "pptp 172.16.1.2 --nolaunchpppd"
noauth
name contrarebelion
remotename PPTP
file /etc/ppp/options.pptp
persist
ipparam sion
noipdefault
defaultroute
proxyarp
```

y el resultado fue diferente.


iilustra@iilustra-deska:~$ sudo pon sion dump debug logfd 2 nodetach

pppd options in effect:

```
debug debug		# (from command line)
nodetach		# (from command line)
persist		# (from /etc/ppp/peers/sion)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-mschap-v2		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename PPTP		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
noipdefault		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
proxyarp		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x51b6ab42> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x746500c6> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x746500c6> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x51b6ab42> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0x746500c6]
sent [LCP EchoRep id=0x0 magic=0x51b6ab42]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x1 <addr 200.81.161.213>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.161.213>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 200.81.161.213>]
not replacing existing default route via 172.16.68.1
Cannot determine ethernet address for proxy ARP
local  IP address 200.81.161.213
remote IP address 200.69.45.2
Script /etc/ppp/ip-up started (pid 5957)
Script /etc/ppp/ip-up finished (pid 5957), status = 0x0
rcvd [LCP EchoReq id=0x1 magic=0x746500c6]
sent [LCP EchoRep id=0x1 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x2 magic=0x746500c6]
sent [LCP EchoRep id=0x2 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x3 magic=0x746500c6]
sent [LCP EchoRep id=0x3 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x4 magic=0x746500c6]
sent [LCP EchoRep id=0x4 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x5 magic=0x746500c6]
sent [LCP EchoRep id=0x5 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x6 magic=0x746500c6]
sent [LCP EchoRep id=0x6 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x7 magic=0x746500c6]
sent [LCP EchoRep id=0x7 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x8 magic=0x746500c6]
sent [LCP EchoRep id=0x8 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x9 magic=0x746500c6]
sent [LCP EchoRep id=0x9 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0xa magic=0x746500c6]
sent [LCP EchoRep id=0xa magic=0x51b6ab42]
rcvd [LCP EchoReq id=0xb magic=0x746500c6]
sent [LCP EchoRep id=0xb magic=0x51b6ab42]
rcvd [LCP EchoReq id=0xc magic=0x746500c6]
sent [LCP EchoRep id=0xc magic=0x51b6ab42]
rcvd [LCP EchoReq id=0xd magic=0x746500c6]
sent [LCP EchoRep id=0xd magic=0x51b6ab42]
rcvd [LCP EchoReq id=0xe magic=0x746500c6]
sent [LCP EchoRep id=0xe magic=0x51b6ab42]
rcvd [LCP EchoReq id=0xf magic=0x746500c6]
sent [LCP EchoRep id=0xf magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x10 magic=0x746500c6]
sent [LCP EchoRep id=0x10 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x11 magic=0x746500c6]
sent [LCP EchoRep id=0x11 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x12 magic=0x746500c6]
sent [LCP EchoRep id=0x12 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x13 magic=0x746500c6]
sent [LCP EchoRep id=0x13 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x14 magic=0x746500c6]
sent [LCP EchoRep id=0x14 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x15 magic=0x746500c6]
sent [LCP EchoRep id=0x15 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x16 magic=0x746500c6]
sent [LCP EchoRep id=0x16 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x17 magic=0x746500c6]
sent [LCP EchoRep id=0x17 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x18 magic=0x746500c6]
sent [LCP EchoRep id=0x18 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x19 magic=0x746500c6]
sent [LCP EchoRep id=0x19 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x1a magic=0x746500c6]
sent [LCP EchoRep id=0x1a magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x1c magic=0x746500c6]
sent [LCP EchoRep id=0x1c magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x1d magic=0x746500c6]
sent [LCP EchoRep id=0x1d magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x1e magic=0x746500c6]
sent [LCP EchoRep id=0x1e magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x1f magic=0x746500c6]
sent [LCP EchoRep id=0x1f magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x20 magic=0x746500c6]
sent [LCP EchoRep id=0x20 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x21 magic=0x746500c6]
sent [LCP EchoRep id=0x21 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x22 magic=0x746500c6]
sent [LCP EchoRep id=0x22 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x23 magic=0x746500c6]
sent [LCP EchoRep id=0x23 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x24 magic=0x746500c6]
sent [LCP EchoRep id=0x24 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x25 magic=0x746500c6]
sent [LCP EchoRep id=0x25 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x26 magic=0x746500c6]
sent [LCP EchoRep id=0x26 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x27 magic=0x746500c6]
sent [LCP EchoRep id=0x27 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x28 magic=0x746500c6]
sent [LCP EchoRep id=0x28 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x29 magic=0x746500c6]
sent [LCP EchoRep id=0x29 magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x2a magic=0x746500c6]
sent [LCP EchoRep id=0x2a magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x2b magic=0x746500c6]
sent [LCP EchoRep id=0x2b magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x2c magic=0x746500c6]
sent [LCP EchoRep id=0x2c magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x2d magic=0x746500c6]
sent [LCP EchoRep id=0x2d magic=0x51b6ab42]
rcvd [LCP EchoReq id=0x2e magic=0x746500c6]
sent [LCP EchoRep id=0x2e magic=0x51b6ab42]
Terminating on signal 2
Child process pptp 172.16.1.2 --nolaunchpppd (pid 5946) terminated with signal 2
Modem hangup
Connect time 3.9 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 6000)
Connection terminated.
Waiting for 1 child processes...
script /etc/ppp/ip-down, pid 6000
Script /etc/ppp/ip-down finished (pid 6000), status = 0x0
```


Se queda haciendo sent / rcvd, pero internet NO funciona. Además no manda ni envía nada.  

Acá dejo las pruebas con las últimas configuraciones de /peers/sion que dejaste en el post.

```

pty "pptp 172.16.1.2 --nolaunchpppd"
noauth
name contrarebelion
remotename PPTP
file /etc/ppp/options.pptp
persist
ipparam sion
noipdefault
proxyarp
defaultroute
replacedefaultroute
```

```
iilustra@iilustra-deska:~$ sudo pon sion dump debug logfd 2 nodetach
pppd options in effect:
debug debug		# (from command line)
nodetach		# (from command line)
persist		# (from /etc/ppp/peers/sion)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-mschap-v2		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename PPTP		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
noipdefault		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
proxyarp		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 3
sing interface ppp0
connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x44fffed1> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x82ac3be8> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0x82ac3be8> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x44fffed1> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0x82ac3be8]
sent [LCP EchoRep id=0x0 magic=0x44fffed1]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x1 <addr 200.81.162.119>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.162.119>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 200.81.162.119>]
replacing old default route to eth0 [172.16.68.1]
[COLOR="DarkOrange"]Cannot determine ethernet address for proxy ARP[/COLOR]
local  IP address 200.81.162.119
remote IP address 200.69.45.2
Script /etc/ppp/ip-up started (pid 6050)
Script /etc/ppp/ip-up finished (pid 6050), status = 0x0
rcvd [LCP EchoReq id=0x1 magic=0x82ac3be8]
sent [LCP EchoRep id=0x1 magic=0x44fffed1]
rcvd [LCP EchoReq id=0x2 magic=0x82ac3be8]
sent [LCP EchoRep id=0x2 magic=0x44fffed1]
rcvd [LCP EchoReq id=0x3 magic=0x82ac3be8]
sent [LCP EchoRep id=0x3 magic=0x44fffed1]
cvd [LCP TermReq id=0x2 "Peer not responding"]
LCP terminated by peer (Peer not responding)
Connect time 0.4 minutes.
Sent 290409870 bytes, received 0 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 6055)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 6055), status = 0x0
script pptp 172.16.1.2 --nolaunchpppd finished (pid 6045), status = 0x0
Modem hangup
Connection terminated.
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xce916125> <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xce916125> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0xce916125> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0xce916125> <pcomp> <accomp>]
Terminating on signal 2
Child process pptp 172.16.1.2 --nolaunchpppd (pid 6065) terminated with signal 2
Modem hangup
Connection terminated.
```


Yo terminé la conexión. 

Ahora con

```
pty "pptp 172.16.1.2 --nolaunchpppd"
noauth
name contrarebelion
remotename PPTP
file /etc/ppp/options.pptp
persist
ipparam sion
noipdefault
proxyarp
defaultroute
replacedefaultroute
usepeerdns
```

```
iilustra@iilustra-deska:~$ sudo pon sion debug dump logfd 2 nodetach
pppd options in effect:
debug debug		# (from command line)
nodetach		# (from command line)
persist		# (from /etc/ppp/peers/sion)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-mschap-v2		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name contrarebelion		# (from /etc/ppp/peers/sion)
remotename PPTP		# (from /etc/ppp/peers/sion)
		# (from /etc/ppp/options.pptp)
pty pptp 172.16.1.2 --nolaunchpppd		# (from /etc/ppp/peers/sion)
hide-password		# (from /etc/ppp/options)
ipparam sion		# (from /etc/ppp/peers/sion)
noipdefault		# (from /etc/ppp/peers/sion)
defaultroute		# (from /etc/ppp/peers/sion)
replacedefaultroute		# (from /etc/ppp/peers/sion)
proxyarp		# (from /etc/ppp/peers/sion)
usepeerdns		# (from /etc/ppp/peers/sion)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xcf39a258> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0xf789f7b5> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0xf789f7b5> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xcf39a258> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="contrarebelion" password=<hidden>]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x1 <addr 200.81.161.30> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.161.30> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 200.81.161.30> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 200.81.161.30> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
replacing old default route to eth0 [172.16.68.1]
Cannot determine ethernet address for proxy ARP
local  IP address 200.81.161.30
remote IP address 200.69.45.2
primary   DNS address 200.69.32.5
secondary DNS address 200.69.32.9
Script /etc/ppp/ip-up started (pid 6102)
cript /etc/ppp/ip-up finished (pid 6102), status = 0x0
rcvd [LCP EchoReq id=0x1 magic=0xf789f7b5]
sent [LCP EchoRep id=0x1 magic=0xcf39a258]
rcvd [LCP EchoReq id=0x2 magic=0xf789f7b5]
sent [LCP EchoRep id=0x2 magic=0xcf39a258]
cvd [LCP TermReq id=0x2 "Peer not responding"]
LCP terminated by peer (Peer not responding)
Connect time 0.2 minutes.
Sent 188096502 bytes, received 153 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 6106)
sent [LCP TermAck id=0x2]
Script /etc/ppp/ip-down finished (pid 6106), status = 0x0
Script pptp 172.16.1.2 --nolaunchpppd finished (pid 6097), status = 0x0
Modem hangup
Connection terminated.
using channel 6
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x447b4ba0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0xab0d699e> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth pap> <magic 0xab0d699e> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0x447b4ba0> <pcomp> <accomp>]
sent [PAP AuthReq id=0x2 user="contrarebelion" password=<hidden>]
rcvd [LCP EchoReq id=0x0 magic=0xab0d699e]
sent [LCP EchoRep id=0x0 magic=0x447b4ba0]
rcvd [PAP AuthAck id=0x2 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 200.69.45.2>]
rcvd [IPCP ConfNak id=0x3 <addr 200.81.162.125> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 200.81.162.125> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
rcvd [IPCP ConfAck id=0x4 <compress VJ 0f 01> <addr 200.81.162.125> <ms-dns1 200.69.32.5> <ms-dns3 200.69.32.9>]
replacing old default route to eth0 [172.16.68.1]
Cannot determine ethernet address for proxy ARP
local  IP address 200.81.162.125
remote IP address 200.69.45.2
primary   DNS address 200.69.32.5
secondary DNS address 200.69.32.9
Script /etc/ppp/ip-up started (pid 6121)
Script /etc/ppp/ip-up finished (pid 6121), status = 0x0
Terminating on signal 2
Connect time 0.1 minutes.
Sent 57091332 bytes, received 0 bytes.
restoring old default route to eth0 [172.16.68.1]
Script /etc/ppp/ip-down started (pid 6125)
sent [LCP TermReq id=0x3 "User request"]
Child process pptp 172.16.1.2 --nolaunchpppd (pid 6116) terminated with signal 2
Modem hangup
Connection terminated.
Script /etc/ppp/ip-down finished (pid 6125), status = 0x0
```



```
iilustra@iilustra-deska:~$ sudo route add host 172.16.1.2 gw 172.16.68.1
host: Host desconocido
```

No sé si ya hice esta pregunta: ¿por qué como IP y DNS me aparecen otros valores cuando ejecuto pon sion?

```
local  IP address 200.81.161.30
remote IP address 200.69.45.2
primary   DNS address 200.69.32.5
secondary DNS address 200.69.32.9
```

Sólo marco esto porque me parece raro. Si está bien que así sea y la explicación es larga y técnica, no es necesaria :P Pero quizá tengo algo que ver. Sólo estoy tratando de colaborar, aunque entienda menos de la mitad de lo que está pasado :oops:

La próxima será, la próxima será!! [-o<
Lo peor es que necesito internet sí o sí, y hasta ahora casi no he podido usar el ubuntu. Y claro, cómo no va a ser más fácil windows, si sion te manda un técnica a la casa que se pasa una hora configurándote la conexión... así cualquiera. Debería ser ilegal que yo no reciba soporte por usar un OS no-$. Otra conspiración sionista, eh! :P*

* chiste, chiste, espero no herir sensibilidades :)

---

### Post by faktorqm on 2008-05-30
Che bueno, te tengo que decir que el error es el mismo entre ayer y hoy para todas las configuraciones posibles....

No solucioné nada de ayer a hoy :( pero al menos me saqué todas las dudas.

Lo que yo probaria, es un live cd, arrancas, e instalas el network-manager-pptp y configuras graficamente la VPN. (todo sin reiniciar lo tenes que hacer y sin tocar ningun archivo de todos lo que venimos tocando esta semana). 

Si te anda ahi, entonces es problema de tu instalacion. si no anda, la ultima que se me ocurre, es mandar todos los posts juntos en un solo mail a la lista de correo de ubuntu-ar, que capaz alguien con experiencia en VPN nos puede ayudar.

Lo de los ip's y los DNS's requiere una explicación extensa y técnica, pero básicamente una VPN es una LAN a través de internet. Cuando hacemos este proceso, lo que vos estas haciendo es formar parte de la red de sion como si fuera local. O sea, vos estás conectada a la red de ellos, por algún motivo te desconectan (posiblemente errores en el protocolo) y no tenés internet. 

El error es siempre el mismo, no se si te lo puse antes, pero LCP es link control protocol. Creo que voy a leer más la documentacion de ppp...

Proba eso y nos fijamos a ver que pasa. Salu2!

---

### Post by athnea on 2008-05-31
> **faktorqm said:**
> Lo que yo probaria, es un live cd, arrancas, e instalas el network-manager-pptp y configuras graficamente la VPN. (todo sin reiniciar lo tenes que hacer y sin tocar ningun archivo de todos lo que venimos tocando esta semana). 

¡Hola! Ayer me enteré que hay un bug en el network manager y cuando tengo deshabilitada la ip itinerante en redes, no puedo ver el plugin de vpn. Así que saqué la opción y me apareció el plugin. ¿Te parece que va a ser más fácil configurar así? Me aparecen tres opciones para VPN y no sé cuál elegir. Espero que esto sea un mediano avance. Parece que si no voy a tener que instalar telecentro y adiós sion.

Mientras tanto voy a ver si puedo por mi cuenta.
Gracias, saludos!

---

### Post by faktorqm on 2008-05-31
Decime que opciones te aparecen y te voy guiando. Salu2!

---

### Post by athnea on 2008-05-31
Holaaa, acá dejo todas las opciones que me aparecen tal como aparecen. Thank you very much.


panel conexiones VPN --> añadir
crear conexión vpn - 1 de 2
**selecciones qué tipo de conexión vpn desea crear**
conectar con: 
1. compatible cisco vpn client (vpnc)
2. open vpn client
3. pptp tunnel

**[SIZE="4"]con compatible cisco vpn client (vpnc)[/SIZE]**
crear conexión 2 de 2
conection name ____________________
connection information
a. required
gateway _________________
group name_______________
b. optional
o override user name
o use domain for authentication
o only use vpn connectios for these addresses
o disable nat traversal
o enable weak single des encryption
o allow using NULL encryption

[B][SIZE="4"]
con  open vpn client[/SIZE][/B]
connection name ___________
connection information
a. required
gateway addres _____________
gateway port (aparece 1194)
connection type 
- x.509 certificates
- preshared keys
- password authentication
- x.509 with password authentication
CA file _________
certificate __________
clave _________

[SIZE="4"][B]
con pptp tunnel[/B][/SIZE]
1. conexión
nombre de la conexión _________
tipo windows vpn (pptp)
pasarela _______________


2. autenticación
o autenticar compañero
o rechazar eap (esta está marcada)
o rechazar chap
o rechazar ms chap

3. compresión y encriptación
compresión
o requerir compresión mppc
o permitir compresión deflate
o permitir compresión bsd

encriptación
o requerir encriptación mppe
o requerir encriptación mppe de 128 bits (marcada)
o activar mppe de estados

4. opciones ppp
a. opciones ppp personalizadas ___________-
b. opciones ip
o usar dns del compañero (marcada)
o accesos exclusivo al dispositivo (bloqueo tipo uucp) (marcada)
o depurara salida
o requerir dir. ip explítica (opción no habilitada)

c. parámetros de paquetes
MTU: 1406
MRU: 1416

d. retardos y expiraciones
retraso de conexión (no habilitado)
lcp-echo-failure 10
lcp-echo-interval 10

5. enrutado
o dnd del compañero a través del túnel (marcado)
o solamente utilizar vpn para estas direcciones

---

### Post by faktorqm on 2008-05-31
**[SIZE="4"]con pptp tunnel[/SIZE]**

1. conexión
nombre de la conexión: [COLOR="Red"]sion[/COLOR]
tipo windows vpn (pptp) 
pasarela: [COLOR="Red"]172.16.1.2[/COLOR]


2. autenticación
o autenticar compañero [COLOR="Red"]NO[/COLOR] 
o rechazar eap [COLOR="Red"]SI[/COLOR] 
o rechazar chap [COLOR="Red"]SI[/COLOR] 
o rechazar ms chap [COLOR="Red"]SI[/COLOR] 

3. compresión y encriptación
compresión
o requerir compresión mppc [COLOR="Blue"]NO SÉ[/COLOR]
o permitir compresión deflate [COLOR="Red"]NO[/COLOR] 
o permitir compresión bsd [COLOR="Red"]NO[/COLOR] 

encriptación
o requerir encriptación mppe [COLOR="Red"]NO[/COLOR] 
o requerir encriptación mppe de 128 bits [COLOR="Red"]NO[/COLOR]
o activar mppe de estados [COLOR="Red"]NO[/COLOR]

4. opciones ppp
a. opciones ppp personalizadas ___________-[COLOR="Blue"]NO SÉ[/COLOR]
b. opciones ip
o usar dns del compañero [COLOR="Red"]SI[/COLOR] 
o accesos exclusivo al dispositivo (bloqueo tipo uucp) [COLOR="Red"]SI[/COLOR] 
o depurara salida [COLOR="Red"]NO[/COLOR] 
o requerir dir. ip explítica (opción no habilitada)

c. parámetros de paquetes
MTU: 1406 [COLOR="Blue"]DEJALO COMO ESTA[/COLOR]
MRU: 1416

d. retardos y expiraciones
retraso de conexión [COLOR="Red"]HABILITALO[/COLOR] 
lcp-echo-failure 10
lcp-echo-interval 10

5. enrutado
o dnd del compañero a través del túnel [COLOR="Red"]SI[/COLOR] 
o solamente utilizar vpn para estas direcciones [COLOR="Red"]SI[/COLOR] 

Vamos a ver si arranca! :D

---

### Post by athnea on 2008-05-31
> **faktorqm said:**
> 
d. retardos y expiraciones
retraso de conexión [COLOR="Red"]HABILITALO[/COLOR] 
lcp-echo-failure 10
lcp-echo-interval 10

Está deshabilitada como opción; pero dice 0.


> **faktorqm said:**
> 
o solamente utilizar vpn para estas direcciones [COLOR="Red"]SI[/COLOR] 


Acá tengo la opción de completar qué direcciones.

Hasta ahora no anduvo. Otra vez sopa. Eso sí: yendo a red, no tengo habilitada la opción de cableado y, además, está con IP itinerante. En cuando la activo y pongo Ip estática, ya no puedo acceder a las opciones de VPN.

Arghhhhhh, me parece que me paso a Telecentro :P

---

### Post by elrengo79 on 2008-06-05
te dejo un machete que tenia de ayuda para cuando instalaba conexiones pptp hace unos años.En ese momento se usaba el paquete rp-pptp, no se como sera ahora.


1) en primer instancia el archivo /etc/ppp/pap-secrets  conteniendo
el logins/pass para la conexion y contiene lo siguiente :

#  client            server        secret    IP adress
usuario@advancedsl	*	password


No tenemos que olvidar que este archiho debe tener permisos tal que
solo lo pueda ver un administrador (root )

chmod 700 /etc/ppp/pap-secrets



2) la segunda etapa de configuracion del ppp se hace sobre el archivo
/etc/ppp/options  el cual contiene los parametros a pasarle a PPPD :


/etc/ppp/options  contiene lo siguiente :

debug
name "usuario@advancedsl"
noipdefault
defaultroute

3 )por ultimo debemos especificarles los dns  , se modifica el archivo
/etc/resolv.conf  para que quede como sigue :

nameserver 200.10.122.11
nameserver 200.9.212.5


4. Conneccion / desconeccion:
La configuracion esta lista
Para realizar la conexion, simplemente tipeamos:

pptp 10.0.0.138

siendo 10.0.0.138  la direccion ip de nuestro modem, esperamos unos
segundos y despues tipeamos

ifconfig

y deberia aparecer una nueva interface llamada ppp0 con una ip asignada
que es la coneccion ppp lograda con ADSL  .

Para desconectarnos, debemos tipiar :

killall pppd ; killall pptp ; rm -rf /var/run/pptp/

Nota : es importante matar estos 2 procesoso y despues con el rm borrar
dicho directorio porque sino el pptp no detecta que se deconecto y
no nos deja volver a reconectarnos en el futuro .


pptp 10.0.0.138 file /etc/ppp/pptp-options

---


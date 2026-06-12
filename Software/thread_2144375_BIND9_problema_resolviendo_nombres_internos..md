---
title: "BIND9 problema resolviendo nombres internos."
date: 2013-05-11
forum: Software
---

### Post by MeduZa on 2013-05-11
Hola comunidad, no soy de hacer muchas preguntas pero aca estoy :( , tengo un server que maneja los nombres usando BIND9.
Para la red interna tengo una zona (poseidon) y para las resoluciones externas hago forward con cache, todo funciona de maravillas, todas las PC / Periféricos (tablets, laptops. o todo lo que pida un IP) de mi red obtienen su IP via DHCP y todas se ven las unas a las otras (ej: haciendo PING a sus HOSTNAMES o IPs) también todas tienen Internet y pueden hacer Ping a cualquier dirección externa sin problemas.
Todas las PC ven al server (poseidon) que tiene IP estático (es la única con IP estático) y a los otros servers (son IP dinámicos pero siempre obtienen el mismo IP, así lo tengo seteado en el DHCP).

El problema es que el server BIND9 (poseidon) no ve a nadie en la RED por su nombre (si por su IP), el si puede resolver nombres externos (usando el ISP)

Estuve buscando en Internet desde hace bastante y no consigo la respuesta, se que me falta algo o el orden de la resolución esta mal, se que mis archivos de zona y seteos de BIND9 están correctos, pero esto es otra cosa que se me debe haber olvidado hacer :(

ejemplos:
desde un server llamado (apolo) a mi pc (xenoid):
root@Apolo# nslookup xenoid
Server:		192.168.16.1
Address:	192.168.16.1#53

Name:	xenoid.Poseidon
Address: 192.168.16.104

y reverso:
root@Apolo# nslookup 192.168.16.104
Server:	192.168.16.1
Address:	192.168.16.1#53

104.16.168.192.in-addr.arpa	name = Xenoid.Poseidon.

pero desde Poseidon a Xenoid:
root@Poseidon:# nslookup xenoid
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find xenoid: SERVFAIL
lo mismo con el IP (reverse)
root@Poseidon:# nslookup 192.168.16.104
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find 104.16.168.192.in-addr.arpa: SERVFAIL

si le hago ping lo mismo el IP anda pero el nombre no
root@Poseidon# ping xenoid
ping: unknown host xenoid
root@Poseidon:# ping 192.168.16.104
PING 192.168.16.104 (192.168.16.104) 56(84) bytes of data.
64 bytes from 192.168.16.104: icmp_req=1 ttl=64 time=0.256 ms
64 bytes from 192.168.16.104: icmp_req=2 ttl=64 time=0.178 ms
^C
--- 192.168.16.104 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.178/0.217/0.256/0.039 ms

Saludos y desde ya muchas gracias

PD: si necesitan ver algún seteo, pidan, ya que no tengo idea donde puede ser que este fallando y por eso no puse nada.

---

### Post by biale on 2013-05-14
A diferencia del resto poseidon tiene dos piezas, una es el DNS server y la otra un cliente, como cualquier otra máquina. Supongo que la falla se da a nivel del cliente.

Si Poseidon puede resolver hacia afuera, pero no hacia adentro, esta pasando por alto su propia funcionalidad. Definiciones estáticas que habría que revisar.

Edito. Y de mis recuerdos de Samba: tambien hay que tener en cuenta la "(seudo) cadena de búsqueda". 

Hace muchas lunas que no toco DNS, pero igual espero sea de utilidad...

---

### Post by MeduZa on 2013-05-15
a veces los problemas mas complejos tienen una solución tan simple que es prácticamente invisible!
tenias razón, cometí un error en el resolv.conf
había puesto sin darme cuenta 192.168.1.1 (eth0 conectado a WAN) en vez de 192.168.16.1 (br0 conectado a LAN + WIFI), ni bien setié eso pude ver a xenoid desde poseidon :P
Te agradezco el empujón, me hizo ver algo que antes (lo revise mucho ehehhe) no veia! porque revisaba otras configuraciones que y todas estaban bien


otra pregunta (esta mas bien del tipo mataburro):

ahora nslookup resuelve xenoid, pero si no pongo el domino resuelve a un ip externo, ¿porque mira primero afuera (WAN) y después adentro (LAN)? [COLOR="#FF0000"](ojo esto solo pasa con nslookup ya que ping resuelve xenoid a el ip LAN)[/COLOR]

#nslookup xenoid
Server:		192.168.16.1
Address:	192.168.16.1#53

Non-authoritative answer:
Name:	xenoid
Address: 67.215.65.132

root@Poseidon:~# nslookup xenoid.poseidon
Server:		192.168.16.1
Address:	192.168.16.1#53

Name:	xenoid.poseidon
Address: 192.168.16.104



nslookup 192.168.16.104
Server:		192.168.16.1
Address:	192.168.16.1#53

104.16.168.192.in-addr.arpa	name = Xenoid.Poseidon.

---

### Post by biale on 2013-05-19
Esta faltando anexar el sufijo faltante en forma automatica. Yo lo conocía desde el lado cliente por configuración estatica o DHCP (era "domain name"?). Ignoro como se puede hacer en forma generica desde el servidor DNS. 

Era un tema cuando se configuraba mas de un dominio local. En ese caso se tendria que especificar una cadena de búsqueda dependiente de la conexion del equipo que emite la consulta.

---


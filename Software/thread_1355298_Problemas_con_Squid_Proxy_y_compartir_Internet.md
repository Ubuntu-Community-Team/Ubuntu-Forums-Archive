---
title: "Problemas con Squid Proxy y compartir Internet"
date: 2009-12-14
forum: Software
---

### Post by matiaz on 2009-12-14
¿Qué tal gente? Si puedo solucionar este tema del proxy, no voy a tener nada que envidiarle a Windows. Les pido una mano porque estoy renegando hace unos días y no puedo hacerlo andar.

El tema es así, necesito compartir internet de mi PC (tarjeta de red -eth0) al rango de ip 172.27.x.x (conexión GPRS -ppp0). Desde Windows lo hacía con CCProxy y destilando la opción "Usar puerta de enlace predeterminada en la red remota" en la conexión GPRS.

El asunto es que quiero hacer lo mismo desde Karmic. Tengo instalado Squid 2.7 y la última versión de Webmin. Cualquier dato que precisen me lo piden ;)

*Agrego: * Al momento de compartir internet, las dos conexiones están online.

Saludos, gracias anticipadas..

---

### Post by gmunioz on 2009-12-15
Hola mat..:

Prueba con iptables:

Iptables funciona de forma parecida a las reglas de acceso del proxy squid, pero no te limita las conexiones. Con squid no puedes usar pop3 
ni smtp.

Iptables hace NAT/MASQUERADE de una red, esto es simplemente enmascarar las ip's de dicha red con otra diferente.

La forma de utilizar iptables, es ir escribiendo regla por regla.
Como estas reglas se guardan en memoria, perdiéndose cuando apagas el ordenador, para evitarlo, lo que puedes hacer es escribir en orden las reglas en un script, el cual puedes ejecutar en el inicio del sistema

Primero habilita definitivamente el forwarding en el kernel, ejecutando en consola:

```
sudo gedit /etc/sysctl.conf
```

Buscas las líneas que dicen:

```
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1


# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1
```

Y las dejas asi, sin almohadilla en las que dice net.ipv4.xxxxxxxx:

```
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```
Guardas el archivo.

Pulsas nuevo y le pegas este contenido:

```
#!/bin/sh
# Script para habilitar conexión compartida de internet
# Dispositivo de red local eth0
# Direcciones de red privada 192.168.0.0/24 (máscara de 24 bits: 255.255.255.0)

# Limpieza de las reglas preexistentes

iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

# Habilitar el NAT
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -d 0.0.0.0/0 -j MASQUERADE

# Dejar pasar los paquetes ICMP
iptables -A INPUT -i eth0 -p ICMP -j ACCEPT

# Permitir conexiones al puerto 80 (HTTP)
iptables -A INPUT -i eth0 -p TCP –dport 80 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 25 (SMTP)
iptables -A INPUT -i eth0 -p TCP –dport 25 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 10000 (Webmin)
iptables -A INPUT -i eth0 -p TCP –dport 10000 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 53 (DNS)
iptables -A INPUT -i eth0 -p TCP –dport 53 -m state –state NEW -j ACCEPT

# Permitir conexiones al puerto 22 (SSH)
iptables -A INPUT -i eth0 -p TCP –dport 22 -m state –state NEW -j ACCEPT

# Aceptar paquetes de conexiones ya establecidas
iptables -A INPUT -p TCP -m state –state RELATED -j ACCEPT

# Rechazar paquetes de conexiones nuevas
iptables -A INPUT -i eth0 -m state –state NEW,INVALID -j DROP

# Rechazar paquetes de forwarding de conexiones no establecidas
iptables -A FORWARD -i eth0 -m state –state NEW,INVALID -j DROP

```
Lo guardas en /etc/init.d con el nombre firewall
Le das permisos de ejecución:

```
sudo chmod +x /etc/init.d/firewall
```

Y lo pones en el arranque del sistema:

```
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall
```

Configuración de los clientes
En los clientes de tu red local, lo único que tendrás que hacer es 
poner como puerta de enlace predeterminada (o gateway), la ip de la 
maquina que acabas de configurar.

---

### Post by matiaz on 2009-12-15
Te agradezco muchísimo la respuesta Gabriel pero necesito sí o sí conectar a los clientes desde proxy. Como dije en mi primer post, necesito compartir internet en conexiones GPRS. Dicho en criollo: quiero tener internet gratarola en los celulares y hasta donde sé, éste es el único método posible.

En Windows, configurado de la forma que dije anteriormente, conectando los clientes (celulares) a la dirección IP que me da la red GPRS al conectar un celular como módem en mi PC, sale andando. Necesito que Squid haga lo que hace CCProxy en Windows.

Solamente tengo que compartir el puerto 8080 y si puedo definir ciertas páginas, mejor.

Por si alguno le interesa, en Ubuntu uso DDClient para actualizar un dns dinámico registrado en [www.dyndns.org]("http://www.dyndns.org"). De esta forma, conecto los celulares al proxy "loquesea.dyndns.org" en vez de la dirección IP dinámica que me da la conexión GPRS al momento de conectarme a dicha red con el celular que uso como módem.

En definitiva tengo dos conexiones activas: una banda ancha y una "red privada" que no es más que la conexión GPRS en un punto de acceso que no cobra.

Espero que puedan ayudarme con esta. Si necesitan más info pregunten ;)

---

### Post by gmunioz on 2009-12-15
Hola mat...:

Interesante trabajo, una vez funcionante si puedes pon un tutorial detallado al respecto.

Squid es un Servidor Intermediario (Proxy) de alto desempeño, que puede funcionar como Servidor Intermediario (Proxy) y caché de contenido de Red para los protocolos HTTP, FTP, GOPHER y WAIS, Proxy de SSL, caché transparente, WWCP, aceleración HTTP, caché de consultas DNS, filtración de contenido y control de acceso por IP y por usuario.

Consiste básicamente en un programa principal como servidor, un programa para búsqueda en servidores DNS, programas opcionales para reescribir solicitudes y realizar autenticación y algunas herramientas para administración y y herramientas para clientes.

Al iniciar Squid da origen a un número configurable (5, de modo predefinido a través del parámetro dns_children) de procesos de búsqueda en servidores DNS, cada uno de los cuales realiza una búsqueda única en servidores DNS, reduciendo la cantidad de tiempo de espera para las búsquedas en servidores DNS.

No puede ser utilizado como Servidor Intermediario (Proxy) para protocolos como SMTP, POP3, TELNET, SSH, IRC, etc. Si se requiere intermediar para cualquier protocolo distinto a HTTP, HTTPS, FTP, GOPHER y WAIS se requerirá hacer uso de un servidor SOCKS como Dante

No se instala por defecto, pero se encuentra en los repositorios de Ubuntu, por lo que puede ser instalado a través de Synaptic, Aptitude o apt-get

Configuración

Squid utiliza el archivo de configuración localizado en /etc/squid/squid.conf, y se puede editar con el siguiente comando, en modo consola (terminal)

```
sudo gedit /etc/squid/squid.conf
```

Para editar al menos los siguientes parámetros:

```
http_port

cache_dir
Al menos una Lista de Control de Acceso
Al menos una Regla de Control de Acceso
httpd_accel_host
httpd_accel_port
httpd_accel_with_proxy
```


**Parámetro http_port**

Los Puertos Registrados recomendados para Servidores Intermediarios (Proxies) pueden ser el 3128 y 8080 a través de TCP.

```
# You may specify multiple socket addresses on multiple lines.

# Default: http_port 3128
http_port 3128
http_port 8080

```
 
Si se desea incrementar la seguridad, puede vincularse el servicio a una IP que solo se pueda acceder desde la red local. Considerando que el servidor utilizado posee una IP 10.140.111.1, puede hacerse lo siguiente:

```
# You may specify multiple socket addresses on multiple lines.

# Default: http_port 3128
http_port 10.140.111.1:3128
http_port 10.140.111.1:8080

```

**Parámetro cache_mem.**

El parámetro cache_mem establece la cantidad ideal de memoria para lo siguiente:

Objetos en tránsito.
Objetos frecuentemente utilizados (Hot).
Objetos negativamente almacenados en el caché.
De modo predefinido se establecen 8 MB. Si se posee un servidor con al menos 128 MB de RAM, 16 MB es el valor para este parámetro:

```
cache_mem 16 MB
```

**Parámetro cache_dir:**

El parámetro cache_dir se utiliza para establecer que tamaño se desea que tenga el caché en el disco duro para Squid. De modo predefinido Squid utilizará un caché de 100 MB, de modo tal que encontrará la siguiente línea:

```
cache_dir ufs /var/spool/squid 100 16 256
```

Mientras más grande sea el caché, más objetos se almacenarán en éste y por lo tanto se utilizará menos el ancho de banda. La siguiente línea establece un caché de 700 MB:

```
cache_dir ufs /var/spool/squid 700 16 256
```

Los números 16 y 256 significan que el directorio del caché contendrá 16 directorios subordinados con 256 niveles cada uno.

```
Parámetro ftp_user.
```

Al acceder a un servidor FTP de manera anónima, de modo predefinido Squid enviará como clave de acceso Squid@. Puede establecerse una dirección de correo especificada como clave de acceso:

```
ftp_user proxy@gmail.com
```

**Controles de acceso.**

Las Listas de Control de Acceso definen una red o bien ciertas máquinas en particular. A cada lista se le asignará una Regla de Control de Acceso que permitirá o denegará el acceso a Squid.
Listas de control de acceso, se establecen con la siguiente sintaxis:

```
acl [nombre de la lista] src [lo que compone a la lista]
```

Si se desea establecer una lista de control de acceso que abarque a toda la red local, basta definir la IP correspondiente a la red y la máscara de la sub-red. Por ejemplo, si se tiene una red donde las máquinas tienen direcciones IP 10.140.111.n con máscara de sub-red 255.255.255.0, podemos utilizar lo siguiente:

```
acl miredlocal src 10.140.111.0/255.255.255.0
```

Más conveniente es definir una Lista de Control de Acceso especificando un archivo localizado en cualquier parte del disco duro, y la cual contiene una lista de direcciones IP.:

```
acl permitidos src "/etc/squid/permitidos"
```

El archivo /etc/squid/permitidos contendría algo como siguiente:

```
10.140.111.2
10.140.111.3
10.140.111.4
10.140.111.5
10.140.111.6
```

En caso de querer restringir el acceso de una pc, basta con eliminarla de la lista.

Listas de control de acceso: Bloqueo de Dominios de Destino.

Es conveniente definir una Lista de Control de Acceso especificando los dominios bloqueados en un archivo localizado en cualquier parte del disco duro, y la cual contiene una lista de los dominios:

```
acl bloqueados dstdomain "/etc/squid/bloqueados"
```

El archivo /etc/squid/bloqueados contendría algo como siguiente:
 

```
www.microsoft.com
www.ibm.com
www.hotmail.com

```
 
Reglas de Control de Acceso.

Las Reglas de control de Aceso definen si se permite o no el acceso hacia Squid. Se aplican a las Listas de Control de Acceso. Deben colocarse en la sección de reglas de control de acceso definidas por el administrador, es decir, a partir de donde se localiza la siguiente leyenda:
 

```
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
```

La sintaxis básica es la siguiente:

```
http_access [deny o allow] [lista de control de acceso]
```

En este ejemplo la regla que establece acceso permitido a Squid a la Lista de Control de Acceso denominada permitidos:

```
http_access allow permitidos
```

La expresión !, significa no. Pueden definirse así respecto de dos listas de control de acceso, lista1 y lista2, que se permite el acceso a Squid a lo que comprenda lista1 excepto aquello que comprenda lista2:

```
http_access allow lista1 !lista2
```

Esta regla es útil cuando se tiene un gran grupo de IP dentro de un rango de red al que se debe permitir acceso, y otro grupo dentro de la misma red al que se debe denegar el acceso.

Aplicando Listas y Reglas de control de acceso.

Considerando como ejemplo que se dispone de una red 10.140.111.0/255.255.255.0, si se desea definir toda la red local, utilizaremos la siguiente línea en la sección de Listas de Control de Acceso:

```
acl todalared src 10.140.111.0/255.255.255.0
```

Listas de Control de Acceso: definición de una red local completa

```
# Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl todalared src 10.140.111.0/255.255.255.0

```
 
A continuación procedemos a aplicar la regla de control de acceso: 

```
http_access allow todalared
```

Reglas de control de acceso: Acceso a una Lista de Control de Acceso.


```
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
http_access allow localhost
http_access allow todalared
http_access deny all

```
 

La regla http_access allow todalared permite el acceso a Squid a la Lista de Control de Acceso denominada todalared, la cual está conformada por 10.140.111.0/255.255.255.0. Esto significa que cualquier máquina desde 10.140.111.1 hasta 10.140.111.254 podrá acceder a Squid.

Si solo se desea permitir el acceso a Squid a ciertas direcciones IP de la red local, deberemos crear un archivo que contenga dicha lista, en modo consola ejecutar

```
sudo gedit /etc/squid/listas/redlocal
```

Incluir las direcciones IP que desea confirmen la Lista de Control de acceso;


```
10.140.111.1
10.140.111.4
10.140.111.17
10.140.111.19
10.140.111.21

```
 
Denominaremos a esta lista de control de acceso como redlocal:

```
acl redlocal src "/etc/squid/listas/redlocal"
``` 

Listas de Control de Acceso: definición de una red local completa


```
# Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl redlocal src "/etc/squid/listas/redlocal"

```
 
Aplicar la regla de control de acceso:

```
http_access allow redlocal

```
Reglas de control de acceso: Acceso a una Lista de Control de Acceso.

```
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
http_access allow localhost
http_access allow redlocal
http_access deny all

```

La regla http_access allow redlocal permite el acceso a Squid a la Lista de Control de Acceso denominada redlocal, la cual está conformada por las direcciones IP especificadas en el archivo /etc/squid/listas/redlocal. Esto significa que cualquier máquina no incluida en /etc/squid/listas/redlocal no tendrá acceso a Squid.

**Parámetro chache_mgr.**

De modo predefinido, si algo ocurre con el caché, se envia un mensaje de aviso a la cuenta webmaster del servidor, puede especificarse una distinta si se considera conveniente;

```
cache_mgr webmaster@gmail.com
```

Caché con aceleración.
Cuando un usuario hace petición hacia un objeto en Internet, este es almacenado en el caché de Squid. Si otro usuario hace petición hacia el mismo objeto, y este no ha sufrido modificación alguna desde que lo accedió el usuario anterior, Squid mostrará el que ya se encuentra en el caché en lugar de volver a descargarlo desde Internet.
 

Proxy Acelerado
En la sección HTTPD-ACCELERATOR OPTIONS deben habilitarse los siguientes parámetros:

```
httpd_accel_host virtual
httpd_accel_port 0
httpd_accel_with_proxy on

```
 

Para crear el directorio cache, en modo consola ejecutamos;

```
sudo /usr/local/squid/sbin/squid -z
```

Iniciar, reiniciar y añadir el servicio al arranque del sistema.
Para iniciar por primera vez Squid en modo consola:

```
sudo service squid start
```

Para reiniciar en modo consola ejecutar:

```
sudo service squid restart
```

Para que Squid se inicie de manera automática al inicio el sistema, en modo consola ejecutar:

```
sudo chkconfig squid on
```

Cualquier error al inicio de Squid solo significa que hubo errores de sintaxis, errores de teclado o de las rutas hacia los archivos de las Listas de Control de Acceso.

Para realizar el diagnóstico de problemas indicándole a Squid que vuelva a leer configuración, lo cual devuelve los errores que existen en el archivo /etc/squid/squid.conf, en modo consola ejecutar:

```
sudo service squid reload
```

En caso de errores graves que no permiten iniciar el servicio, examinar el contenido del archivo /var/log/squid/squid.out ejecutando en consola:

```
less /var/log/squid/squid.out
```

Ajustes para el muro corta-fuegos.
Re-direccionamiento de peticiones a través de iptables y Firestarter.

Para dar salida transparente hacia Internet a ciertos servicios yo al mismo tiempo re-direccionar peticiones hacia servicio HTTP para pasar a través del el puerto donde escucha peticiones Squid (8080), de modo que no haya salida alguna hacia alguna hacia servidores HTTP en el exterior sin que ésta pase antes por Squid, los protocolos HTTPS, FTP, GOPHER ni WAIS, deben ser filtrados a través del NAT.

El re-direccionamiento se hace a través de iptables. Suponiendo que la red local se accede a través de una interfaz eth1, el siguiente esquema ejemplifica un re-direccionamiento:

```
sudo /sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
```

Lo anterior, que requiere un guión de cortafuegos funcional en un sistema con dos interfaces de red, hace que cualquier petición hacia el puerto 80 (servicio HTTP) hecha desde la red local hacia el exterior, se re-direccionará hacia el puerto 8080 del servidor.

Utilizando Firestarter, la regla anteriormente descrita se añade en el archivo /etc/firestarter/user-post.

```
sudo gedit /etc/firestarter/user-post
```

y se agrega la línea

```
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080

```

---

### Post by matiaz on 2009-12-15
Te agradezco el mini-tutorial, había leído varias guías pero eran muy extensas, acá está lo escencial. Te hago una consulta ¿Estaría bien la siguiente línea, considerando que la conexión "local" en este caso es "ppp0", la conexión que está conectada a Internet es "eth0" y el único puerto aceptado por squid va a ser 8080?

sudo /sbin/iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 8080 -j REDIRECT --to-port 8080

Si tenés tiempo te dejo mi squid.conf para que lo revises porque todavía no puedo conectarme desde el celular. Seguramente me falta configurar algo.

Gracias por las respuestas. Si logro hacerlo funcionar, les dejo su merecida guía para tener GPRS gratis.

---

### Post by gmunioz on 2009-12-15
Hola mat...:

Ejecuta antes de:


```
sudo /sbin/iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 8080 -j REDIRECT --to-port 8080
```

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

### Post by matiaz on 2009-12-15
Hay avances gente. Si uso desde el Firefox como proxy la dirección que me da el celular que se conecta a la PC y a la red "privada", funciona. Si uso "localhost 8080" también.

El problema viene cuando trato de conectarme desde el celular. La regla que tengo en el Squid es la siguiente:

acl localnet src 172.27.0.0/16 *(el rango de IP "privadas" es 172.27.x.x-172.27.255.255)*

Desde el Iptables hice:

echo 1 > /proc/sys/net/ipv4/ip_forward
sudo /sbin/iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 8080 -j REDIRECT --to-port 8080

¿Alguna idea?

EDIT: Probé dejando solo una IP desde la configuración del Squid y tampoco funcionó, creo que el error está en el IpTables. También probé compartir internet con Firestarter sin éxito. Ahora volví a las reglas del Firewall por defecto.

---

### Post by alfplayer on 2009-12-16
Para configurar Squid en Ubuntu Server 9.10 para una LAN hace unas semanas lo único que fue necesario agregar en mi configuración fueron dos líneas:

```
acl mired src 192.168.1.0/24
```
```
http_access allow mired
```

La primera parece que ya fue agregada, faltaría la segunda.

El nombre de la red se puede elegir pero es necesario que coincidan en las dos líneas.

Después de realizar los cambios, para hacer valer la nueva configuración:
```
sudo /etc/init.d/squid restart
```

Espero que sea útil.

---

### Post by matiaz on 2009-12-16
Gracias por la respuesta alfplayer, tengo configurada la regla acl con su correspondiente "http_access".

No entiendo por qué no funciona, estoy casi seguro de que es un problema de IPTables..


EDIT: Modifiqué el valor de "acl" por el siguiente:
```
acl localnet src 172.27.0.0-172.27.255.255/255.255.255.255
```

Creo que ahí está escrito de forma correcta pero sigo sin poder conectar.

---

### Post by guillermolisi on 2009-12-16
> **matiaz said:**
> Gracias por la respuesta alfplayer, tengo configurada la regla acl con su correspondiente "http_access".

No entiendo por qué no funciona, estoy casi seguro de que es un problema de IPTables..


EDIT: Modifiqué el valor de "acl" por el siguiente:
```
acl localnet src 172.27.0.0-172.27.255.255/255.255.255.255
```Creo que ahí está escrito de forma correcta pero sigo sin poder conectar.
Me acabo de fijar como tenemos configurado Squid en el laburo y la parte que mencionas esta de la siguiente forma:
```
acl our_networks src 192.168.0.0/16 172.16.0.0/16
http_access allow our_networks
http_access allow localhost
```con esto se permite el acceso compartido a dos LANs distintas (una por placa de red) y esta funcionando con alrededor de 70 maquinas mas servers sin problemas.

Edit: 172.27.x.x no es un bloque privado de IPs, por que lo asignas a la LAN ?

---

### Post by alfplayer on 2009-12-16
> **guillermolisi said:**
> Edit: 172.27.x.x no es un bloque privado de IPs, por que lo asignas a la LAN ?

Ese rango es privado al estar incluído en el bloque privado 172.16.0.0 - 172.31.255.255 (según RFC 1918 ).

Hay que entender que Squid es un proxy (para conectarse a través del proxy los programas como los navegadores deben estar configurados apropiadamente). En cambio, iptables trabaja con paquetes.

---

### Post by guillermolisi on 2009-12-16
> **alfplayer said:**
> Ese rango es privado al estar incluído en el bloque privado 172.16.0.0 - 172.31.255.255 (según RFC 1918).

Gracias por la aclaracion.

---

### Post by matiaz on 2009-12-16
También probé con ese rango de IP guillermolisi (172.27.0.0/16) y no hay caso. No puedo conectar desde los celulares usando el proxy.

Usando desde Firefox "localhost" o la dirección que me da la conexión ppp0 (celular que se conecta al punto de acceso gratuito), el proxy anda 10 puntos.

> **alfplayer said:**
> Hay que entender que Squid es un proxy (para conectarse a través del proxy los programas como los navegadores deben estar configurados apropiadamente). En cambio, iptables trabaja con paquetes.
Esto es lo que tenía entendido, ahí reinicié los valores del Iptables. Algo me está faltando configurar, tal vez fuera de Squid.

---

### Post by Arian_Tux on 2010-01-09
Gracias por el mini tutorial. Pero me pasa algo similar :popcorn: 
Resulta que me quedo con ubuntu 8.04 porque luego me termino mi contrato de internet y consegui otro pero a las alturas del nuevo ubuntu 9.10.

No puedo compartir el internet, aqui estan mi reglas squid y iptables:

Squid.conf
# Default: http_port 3128
http_port 3128
http_port 8080
cache_mem 64 MB
cache_dir ufs /var/spool/squid 700 16 256
ftp_user [email]proxy@su-dominio.net[/email]
ftp_passive on

acl permitidos src "/etc/squid/permitidos"
http_access allow permitidos

# Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl redlocal src "/etc/squid/permitidos"

http_access allow redlocal


httpd_accel_host virtual
httpd_accel_port 0
httpd_accel_with_proxy on
httpd_accel_uses_host_header on


acl SSL_ports port 443 563 
acl Safe_ports port 80 21 443 563 70 210 1025-65535 
acl Safe_ports port 280        # http-mgmt 
acl Safe_ports port 488        # gss-http 
acl Safe_ports port 591        # filemaker 
acl Safe_ports port 777        # multiling http 
acl CONNECT method CONNECT

Iptablesconf
#!/bin/sh 
## SCRIPT de IPTABLES - ejemplo del manual de iptables 
## Ejemplo de script para firewall entre una red local a internet 
## Internet ---- eth1 ---- Linux (firewall)----- eth0 ------ LAN 

echo -n Aplicando Reglas de Firewall... 

## reglas 
## 
iptables -F 
iptables -X 
iptables -Z 
iptables -t nat -F 

## Establecimiento de politica por defecto 
iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD ACCEPT 
iptables -t nat -P PREROUTING ACCEPT 
iptables -t nat -P POSTROUTING ACCEPT 

## Empezamos a filtrar 
## eth1 es el interfaz conectado al router ó modem y eth0 a la LAN 

/sbin/iptables -A INPUT -i lo -j ACCEPT 

# Al firewall tenemos acceso desde la red local LAN 
iptables -A INPUT -s 192.168.0.0/24 -i eth0 -j ACCEPT 

# Ahora hacemos enmascaramiento de la red local 
# y activamos BIT DE FORWARDING (necesario pues sera parte del enrutado) 

iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -d 0.0.0.0/0 -j MASQUERADE 

# Direcciona para hacer nat en nuestra LAN al puerto 8080 al 80 
# (en mi caso uso squid y dansguardian este ultimo libera en el port 8080) 
# (Si solo usas squid es por el port 3128) 
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# Permitimos hacer forward de paquetes en el firewall, es decir 
# que otras máquinas puedan salir a traves del firewall. 
echo "1" > /proc/sys/net/ipv4/ip_forward 


# En mi caso a veces uso webserv entonces debo abrir el port 80. 
iptables -A INPUT -p tcp --dport 80 -j ACCEPT 

#aqui si deseas abrir mas puertos solo copia la linea anterior y 
#cambia el numero de puerto que quieres abrir y si es tcp o udp. 

## Y ahora cerramos los accesos indeseados del exterior: 
## 0.0.0.0/0 significa: cualquier red 
## Cerramos el rango de puertos conocidos 
## Si quieres abrir puertos debes abrirlos antes de las siguientes lineas. 
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 1:1024 -j DROP 
iptables -A INPUT -s 0.0.0.0/0 -p udp --dport 1:1024 -j DROP 

# Cerramos el puerto de gestión webmin si es que lo tienes funcionando. 
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 10000 -j DROP 

echo "firewall activado"

Eso es lo que tengo ya que lo saque de este mismo foro pero hace como un año xD. Creo que debo actualizarme a la ultima version de Ubuntu 9.10.

Pero en conexiones debo tener eth0 y eth1?
la ip de internet es 65.164.29.7
entonces en eth0 coloco mi Ip, mascara de sudred y gateway con sus DNS.

Ahora en eth1 que debo colocar????? Solo se que la ip de internet es mi gateway xD
Como quedaria
Ip: ??????? tengo que inventarme la ip? 192.168.0.0?
Mascara: ????
Gateway: 65.164.29.7
DNS: 65.167.31.142

En firefox mi proxy seria la ip 65.164.29.7? y puerto 3128 o 8080?

Agradeceria mucho su colaboracion amigos. Y tuve comprar una tarjeta 8400Gs para disfrutar de compiz fusion a full :KS y de los demas juegos xD. Para que vean que estoy muy feliz con mi distribucion!

En espera de su ayuda y colaboracion.

---

### Post by gmunioz on 2010-01-09
Hola ari....:

Detalla:

Con que se conecta eth0
Con que se conecta eth1


Comenta con # http_port 8080
Para que tu proxy quede en 3128

---

### Post by Arian_Tux on 2010-01-11
Perdoname Che que ya dias no me aparezco. Resulta que en conexiones cableadas me aparecen 
eth1 
pan0

cree una conexion eth2 para ver si me funcionaba lo demas pero nada.
en la pan0 habia colocado
Ip: 192.168.0.1
MAsk 255.255.255.0 
Sin gateway

lo mismo hice con el eth2 pero nada. No se porque todavia no puedo compartir el internet. Y me puse a actualizar el ubuntu a la version 9.10 porque no puedo eliminar las conexiones que he creado. 

La ethernet eth1 es la que se conecta a internet y creo que cambio ya que le dije a una compañia sobre mi internet y como no sabian de ubuntu no se que hicieron ya que no estaba en casa cuando paso eso. Creo que me borraron la conexion eth0 ya que no me aparece y eso habra cambiado mucho el script de iptables para redireccionar y conectarme.

Muchas gracias y en espera de su ayuda.

---

### Post by Arian_Tux on 2010-01-13
Al final lo que hice fue instalar Ubuntu desktop 9.10 e instalar linux-server y squid.
Ahora tengo que empezar a configurar squid e iptables.
Mi eth0 se conecta a internet
Mi eth1 se conecta a la red local.

Algun consejo?????

---

### Post by Arian_Tux on 2010-01-14
Al final coloque eth0 como local y eth1 como internet. Pero como se donde se aloja la memoria cache?? 
probe colocar esto:
httpd_accel_host virtual
httpd_accel_port 0
httpd_accel_with_proxy on
httpd_accel_uses_host_header on

Pues hace un año me funciono pero hoy en la version 9.10 no xD y de paso pues me pregunto si eso acelera la memoria cache o algo por estilo???? :popcorn:

Gracias por su ayuda.

---


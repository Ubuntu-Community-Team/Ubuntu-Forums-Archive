---
title: "Consulta sobre WINS"
date: 2010-07-05
forum: Software
---

### Post by W31RD on 2010-07-05
Hola a todos, esta es mi primer consulta en el foro :)

Les comento el problema:

Tengo un Ubuntu 10.04 Lucid Lynx en una red Windows con un DC Windows 2003 Server R2.

La cuestión seguramente es muy simple para algunos, pero me está friendo el cerebro:

¿Como configuro el servidor WINS en mi Ubuntu para poder resolver sin problema hostnames de equipos Windows?

Si mal no me equivoco por lo que estuve investigando, hay que modificar el archivo /etc/resolv.conf, el cual es modificado cada vez que se reinicia el equipo, volviendo a su configuración por default tal lo indica el archivo grub.cfg (corríjanme si me equivoco).

La cuestión es que al utilizar IP Dinámicas brindadas por un servidor DHCP, siempre me sucede lo mismo y tengo que andar modificando éste archivo cada vez que inicio el equipo.


¿Hay manera de no tener que generar un script o modificarlo manualmente cada vez que se inicia el sistema utilizando IP's dinámicas?

Voy a seguir investigando, pero cualquier dato será super bienvenido!


Muchas gracias a todos,

Slds!

---

### Post by jpmorelli on 2010-07-05
Me parece que el archivo donde tenés que poner la configuracion que querés que quede cada vez que se enciende el equipo es el /etc/rc.local
Por lo menos ahí es donde yo pongo las rutas fijas en mi firewall
Suerte !

---

### Post by W31RD on 2010-07-05
> **jpmorelli said:**
> Me parece que el archivo donde tenés que poner la configuracion que querés que quede cada vez que se enciende el equipo es el /etc/rc.local
Por lo menos ahí es donde yo pongo las rutas fijas en mi firewall
Suerte !

Muchas gracias por responderme! Si, ahí podría generar algún script que me haga el cambio... pero me gustaría poder directamente modificar desde el archivo que modifica por default cada vez que inicia el equipo al archivo resolv.conf, así directamente agrego search xxxxxxxxx.xxx y me resuelve por nombre las pc's del dominio.

Igualmente, muchas gracias por tu ayuda, la voy a implementar hasta ver si alguien sabe como modificar directamente el archivo resolv.conf.


Slds!

---

### Post by guillermolisi on 2010-07-05
Creo que tambien podrias configurar el servidor DHCP para que entregue las mismas IPs siempre a las mismas tarjetas de red identificando las MAC address.

La otra alternativa es poner en marcha un DNS interno con lo cual invocas a las maquinas por sus nombres y este servicio las ubica por IP.

De cuantas maquinas estamos hablando ?

---

### Post by W31RD on 2010-07-05
> **guillermolisi said:**
> Creo que tambien podrias configurar el servidor DHCP para que entregue las mismas IPs siempre a las mismas tarjetas de red identificando las MAC address.

La otra alternativa es poner en marcha un DNS interno con lo cual invocas a las maquinas por sus nombres y este servicio las ubica por IP.

De cuantas maquinas estamos hablando ?


Guillermo, muchas gracias por responder! Te comento que no tengo acceso a los servidores, ya que es una empresa muy grande y no tengo permisos con mi usuario. Son mas de 2000 pc's en la red, por lo que necesitaría solamente agregar al archivo resolv.conf la línea que diga search dominio.com, ya que con eso me funciona, pero cada vez que reinicio se me borra.

Además, tengo una IP dinámica.

¿Alguna idea de como evitar eso?

Slds!

---

### Post by guillermolisi on 2010-07-05
> **W31RD said:**
> Guillermo, muchas gracias por responder! Te comento que no tengo acceso a los servidores, ya que es una empresa muy grande y no tengo permisos con mi usuario. Son mas de 2000 pc's en la red, por lo que necesitaría solamente agregar al archivo resolv.conf la línea que diga search dominio.com, ya que con eso me funciona, pero cada vez que reinicio se me borra.

Además, tengo una IP dinámica.

¿Alguna idea de como evitar eso?

Slds!
Hablar con los admins ? :)

No haria nada sin su consentimiento. Aqui hay ejemplos de acciones aisladas y cuando esta gente, responsables por el mantenimiento de los recursos informaticos de la empresa, tomo conocimiento revirtieron todo lo hecho por quien avanzo sin charlarlo con ellos.

---

### Post by W31RD on 2010-07-06
> **guillermolisi said:**
> Hablar con los admins ? :)

No haria nada sin su consentimiento. Aqui hay ejemplos de acciones aisladas y cuando esta gente, responsables por el mantenimiento de los recursos informaticos de la empresa, tomo conocimiento revirtieron todo lo hecho por quien avanzo sin charlarlo con ellos.


Guillermo,

Sería lo ideal! Pero la burocracia de este lugar genera lo mismo a que hable con la pared. No hay problema con que utilice el Ubuntu en la red, la cuestión es que al ser un entorno mayormente Windows, no van a realizar ningún cambio ni asignarme una IP fija, por lo que estoy a la buena de Dios.

Yo en un momento había realizado unos cambios con la ayuda de una persona del área de administración de servidores Linux (que es a lo que apunto en un futuro), pero en éste momento se encuentra de viaje.

Por eso consultaba si alguno se acordaba la manera de modificar el default del resolv.conf para que solamente al final me agregue la línea search dominio.xxx para la resolución de los WINS.

Igualmente, muchas gracias a ambos por sus respuestas !

Slds!

---

### Post by guillermolisi on 2010-07-06
Con esa maquina estas usando Network Manager para gestionar las conexiones de red ?

---

### Post by W31RD on 2010-07-06
> **guillermolisi said:**
> Con esa maquina estas usando Network Manager para gestionar las conexiones de red ?

No, solamente configuré el archivo /etc/network/interfaces de esta manera:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

Pero la vez pasada pudimos hacerlo sin utilizar nada, voy a investigar eso de Network Manager, no lo conozco.

Slds!

---

### Post by guillermolisi on 2010-07-06
El Network Manager es el Gestor de Conexiones de Red y podes configurar todas las conexiones con todas las alternativas que necesitas.

Si queres volver a editar ese archivo, en mi casa, LAN con IPs fijas, uso esta configuracion que va a modo de ejemplo:

> iface eth0 inet static
address 90.0.0.1
netmask 255.255.255.0
gateway 90.0.0.2
network 90.0.0.0
dns-nameservers 90.0.0.2
dns-search unimix
auto eth0

---

### Post by W31RD on 2010-07-07
> **guillermolisi said:**
> El Network Manager es el Gestor de Conexiones de Red y podes configurar todas las conexiones con todas las alternativas que necesitas.

Si queres volver a editar ese archivo, en mi casa, LAN con IPs fijas, uso esta configuracion que va a modo de ejemplo:

Gracias por la info! Sería ideal tener una IP fija, ya que podría modificar sin problemas así el archivo resolv.conf, pero al utilizar DHCP se reescribe. Voy a seguir investigando el archivo grub.cfg a ver si encuentro la línea donde ordena modificar el archivo resolv.conf y así quitarla, para dejarle la configuración que yo quiera y no la que entrega el servidor, ya que es incompleta (si, los admins de acá no soy una joyita).

Espero a ver si a alguien se le ocurre como puede ser, si llego a encontrar algo lo posteo :)

Saludos y mil gracias!

---

### Post by jpmorelli on 2010-07-08
Aaaahhh, me parece que yo una vez estuve con el mismo tema para probar en mi red.
Estuve buscando la solución pero nada, fue hace mucho.
Igualmente esto te puede servir para que no te modifique el resolv.conf
[http://www.ubuntu-ve.org/?q=node/979]("http://www.ubuntu-ve.org/?q=node/979")
Si bien es viejito, el comando es correcto.
Suerte !

---

### Post by biale on 2010-07-09
Gente, yo pase por lo mismo y les cuento lo que hice.

En mi trabajo no tengo a Ubuntu instalado, pero levante una sesión live con el CD de Karmic (No Lucid). Out of the box Encontro y accedió bien a todo.

Pero en mi casa la situación cambia por dos razones. La primera es que en principio no hay equipos Windows que puedan ejecutar la función del master browser de red. La segunda es que tengo los paquetes de Samba instalados, y eso cambia las cosas.

El eje principal fué configurar a /etc/nsswitch.conf alterando la supuesta cadena de búsqueda:```

# hosts:        files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```
Dije la "supuesta cadena de búsqueda" porque la cosa NO es tan simple como una cadena de busqueda. "wins" debe ir al principio y no en otro lugar.

El siguiente punto es que en los archivos /etc/hosts y /etc/samba/smb.conf (si esta instalado samba) no haya metidas de pata. La parte relevante de mi archivo de samba es:
```


# ******************************************
# Antes de tocar algo verificar los archivos
# /etc/hosts y /etc/nsswitch
# ******************************************

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = RED

# *** No hizo falta activar!!
# Supuestamente este nombre debería ser distinto al que aparece en /etc/hosts
# netbios name = NOMBRE_NETBIOS

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#  wins support = no
# *** Aunque ya andaba bien, igual decidi activar el servidor.
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
# *** Quitar comentario si activo al servidor Wins (wins support = yes)
# *** Ademas quise poner wins antes de todo para salvar errores en /etc/hosts
    name resolve order = wins lmhosts host bcast

```

Con Lucid y para samba las cosas cambian:
```

sudo apt-get install samba
sudo apt-get install winbind	# Lucid: no se instala por default!!!  		
sudo apt-get install smbfs  libpam-smbpass  libsmbclient
# gadmin-samba			# Samba GUI

```

Con esto lo tengo andando win a ubuntu, ubuntu a win y ubuntu a ubuntu.

Si un host se llama "p24" y estamos resolviendo netbios bien lo siguiente tendría que funcionar:
ping p24
# sshfs -o idmap=user $USER@192.168.5.32:/home/  /media/dat-p24/	# Sin Wins
  sshfs -o idmap=user $USER@p24:/home/           /media/dat-p24/	# Con Wins
y asi siguiendo.

Atención que la solución no es gratis. Liferea deja de funcionar al instante. Rhytmbox se cae por signal 11 si no se inhiben algunos de los accesos a internet (tienda ubuntu, algo de FM). Hay que desabilitar todo e ir habilitando funciones de a una.

Un saludo a todos

---

### Post by W31RD on 2010-07-12
> **jpmorelli said:**
> Aaaahhh, me parece que yo una vez estuve con el mismo tema para probar en mi red.
Estuve buscando la solución pero nada, fue hace mucho.
Igualmente esto te puede servir para que no te modifique el resolv.conf
[http://www.ubuntu-ve.org/?q=node/979](http://www.ubuntu-ve.org/?q=node/979)
Si bien es viejito, el comando es correcto.
Suerte !

JPMORELLI, muchas gracias por la info! Me sirvió mucho, está bueno. Igualmente, puse en funcionamiento lo que me indicó BIALE, pero realmente muchas gracias!

> **biale said:**
> Gente, yo pase por lo mismo y les cuento lo que hice.

En mi trabajo no tengo a Ubuntu instalado, pero levante una sesión live con el CD de Karmic (No Lucid). Out of the box Encontro y accedió bien a todo.

Pero en mi casa la situación cambia por dos razones. La primera es que en principio no hay equipos Windows que puedan ejecutar la función del master browser de red. La segunda es que tengo los paquetes de Samba instalados, y eso cambia las cosas.

El eje principal fué configurar a /etc/nsswitch.conf alterando la supuesta cadena de búsqueda:```

# hosts:        files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```Dije la "supuesta cadena de búsqueda" porque la cosa NO es tan simple como una cadena de busqueda. "wins" debe ir al principio y no en otro lugar.

El siguiente punto es que en los archivos /etc/hosts y /etc/samba/smb.conf (si esta instalado samba) no haya metidas de pata. La parte relevante de mi archivo de samba es:
```


# ******************************************
# Antes de tocar algo verificar los archivos
# /etc/hosts y /etc/nsswitch
# ******************************************

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = RED

# *** No hizo falta activar!!
# Supuestamente este nombre debería ser distinto al que aparece en /etc/hosts
# netbios name = NOMBRE_NETBIOS

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#  wins support = no
# *** Aunque ya andaba bien, igual decidi activar el servidor.
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
# *** Quitar comentario si activo al servidor Wins (wins support = yes)
# *** Ademas quise poner wins antes de todo para salvar errores en /etc/hosts
    name resolve order = wins lmhosts host bcast

```Con Lucid y para samba las cosas cambian:
```

sudo apt-get install samba
sudo apt-get install winbind    # Lucid: no se instala por default!!!          
sudo apt-get install smbfs  libpam-smbpass  libsmbclient
# gadmin-samba            # Samba GUI

```Con esto lo tengo andando win a ubuntu, ubuntu a win y ubuntu a ubuntu.

Si un host se llama "p24" y estamos resolviendo netbios bien lo siguiente tendría que funcionar:
ping p24
# sshfs -o idmap=user $USER@192.168.5.32:/home/  /media/dat-p24/    # Sin Wins
  sshfs -o idmap=user $USER@p24:/home/           /media/dat-p24/    # Con Wins
y asi siguiendo.

Atención que la solución no es gratis. Liferea deja de funcionar al instante. Rhytmbox se cae por signal 11 si no se inhiben algunos de los accesos a internet (tienda ubuntu, algo de FM). Hay que desabilitar todo e ir habilitando funciones de a una.

Un saludo a todos

BIALE, funcionó! Realmente me sirvió, y al no utilizar ni Liferea ni Rhytmbox no tengo problema en realizar estos cambios.

Cualquier eventualidad que tenga con esta configuración la posteo (si es que hay alguna).

Nuevamente, muchas gracias a todos !

Tema solucionado!

Slds!

---


---
title: "Ayuda con red local ubuntu-win xp"
date: 2010-07-15
forum: Software
---

### Post by Packo_z007 on 2010-07-15
Antes que nada hola a todos. Llevo un par de semanas usando ubuntu 10.04 y todavia no puedo crear una red con windows xp. Encontre varios tutoriales para samba y logre ver los archivos de ubuntu desde xp pero nada mas. En resumen:
-instale samba
-lo configure segun varios tutoriales
-lo desinstale
-instale samba 4 y trate de configurarlo tambien
-desactive el firewall de ubuntu

Ahora no obtengo ningun error sino que me pide usuario y contraseña. Usando el usuario de samba que coincide con el de xp no puedo acceder. La verdad no se que mas intentar.

Por ultimo, en el cuadro Sistema/Preferencias/Comparticion de archivos personales, no puedo compartir archivos en red por que dice que los paquetes necesarios no estan instalados y no se cuales son.

Desde ya muchas gracias. Saludos

---

### Post by Peter Smile on 2010-07-15
¿Concretamente qué es lo que hiciste y cómo lo hiciste? ¿Querés acceder a las carpetas de XP desde Ubuntu o al revés? ¿Modificaste el archivo /etc/samba/smb.conf ?

---

### Post by Packo_z007 on 2010-07-16
Pude ver las carpetas compartidas de ubuntu desde XP. Y si modifique /etc/samba/smb.conf. esta adjunto a este mensaje. Gracias.

---

### Post by Peter Smile on 2010-07-16
Antes que nada una pavada sólo para descartarla. En la línea 107 tenés ```
security = SHARE
```

¿Por qué no lo ponés en minúsculas? (se supone que va así) ```
security = share
```

Si no es eso probamos otras cosas.

---

### Post by Packo_z007 on 2010-07-16
Cambie SHARE por share y nada. Desinstale samba y nautilus y no lo pude reinstalar XD, asi que reinstale ubuntu. Con todo en limpio volvi a instalar samba, modifique smb.conf y cree el archivo lmhosts. 
Desde la pc con XP puedo ver las carpetas compartidas en ubuntu, pero solo verlas, no acceder.
Por otro lado, la pc con ubuntu solo puede verse a sí misma en el grupo de trabajo, y cuando trato de acceder al equipo me da un error que dice: **No se pudo montar el lugar**. Falló al obtener la lista de comparticion del servidor. 
Desde ya muchas gracias por la ayuda.

---

### Post by biale on 2010-07-17
Revisar la FWall de Windows. Fijate que la compu Windows pueda verse y "accederse" a si misma como sitio de red. 

Levanta una sesión con el live CD de Ubuntu y ajusta la configuración de red. Deberías acceder a Windows OK.

Del archivo smb.conf observo que simultaneamente estarías codificando el archivo estático lmhosts y fijando soporte de WINS. Mi sugerencia es tratar de configurar lo menos posible.

Pegale un vistazo a un thread reciente que trata sobre WINS (!)

Para probar el acceso de windows a ubuntu retira los comentarios de las lineas para compartir la lectora de CD y ubica algún CD o DVD que tengas dando vueltas.

Si lo tenés instalado, el Zenmap/ nmap debería mostrar los puertos 139 y 445 abiertos.

Un saludo a todos.

---

### Post by sant on 2010-07-17
Está ufw activado en tu sistema?.De ser así deberás permitir el acceso a samba.

Aquí tienes información que te podría servir de ayuda:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)
[http://tuxpepino.wordpress.com/2007/06/03/compartir-carpetas-entre-windows-y-ubuntu-linux/](http://tuxpepino.wordpress.com/2007/06/03/compartir-carpetas-entre-windows-y-ubuntu-linux/)

---

### Post by Packo_z007 on 2010-07-17
La pc con windows si puede verse y accederse a si misma.No entendi muy bien lo del cd de ubuntu, pero lo que hice fue iniciar ubuntu desde el cd en la pc que tiene linux instalado, y tampoco pude entrar por la red. 
Lei el post de WINS, y me di cuenta de que no tenia instalado ni winbind ni smbfs, asi que trate de instalar winbind, pero la instalacion no termina. Queda en Starting the Windbind daemon winbind y no avanza. Probe varias veces y pasa lo mismo.

El firewall esta desactivado segun gufw. Ademas instale zenmap y los puertos estan abiertos. 

Con respecto a los tutoriales esos, ya los habia visto, es más, estaba siguiendo al de tuxpepino.

La verdad no se que mas hacer. Gracias

---

### Post by alfplayer on 2010-07-17
No sé si ese tutorial es útil para 10.04, pero Ubuntu cambia muy rápido, y en general es necesario seguir tutoriales actualizados.

---

### Post by sant on 2010-07-17
¿ Has probado desde Inicio - Ejecutar - Abrir  \\  IP privada del Equipo al que queremos acceder ?

---

### Post by biale on 2010-07-18
La idea de levantar una sesión live con el CD de Karmic es para probar que en modo cliente y sin la presencia de Samba y sus etceteras un Ubuntu pueda acceder a Windows. En esa sesión live, ¿Estaría la placa de red bien configurada? ¿Computadoras pingueables entre si? ¿la sesion live accedía a Internet (Google por ejemplo)?

Cuando te aparece una pantalla de login/ password, acordate que en principio hay sensibilidad mayúsculas/minusculas de ambos lados: Juan vs juan; RED vs red y así siguiendo. 

Winbind no es crítico. Te evita el tener que manejarte con la dirección de IP en lugar del nombre del host. Si por alguna causa no instala bien es preferible no tenerlo. 

El comando ps debe encontrar operativos a smbd y a nmbd y solo si winbind esta operativo a winbindd

La idea es tratar de codificar lo menos posible, "mas es peor". Conviene "retirar" los archivos lmhosts y smbpass.

Revisar muy bien a smb.conf!

wins server = 10.0.0.4  Le estas diciendo que use un servidor wins externo (?)

name resolve order = lmhosts host wins bcast  Esto puede anular a wins (?)

interfaces = 10.0.0.0/8 eth0 eth1  ¿tenes dos tarjetas de red?  Por las dudas sacalo.

Por ahora:
; local master = yes
; domain master = no
; preferred master = yes

Que dice "testparm"?

Pinguea las máquinas entre si y esas direcciones usaremos.

Proba y postea con:
Apuntado desde (1) ubuntu a windows y (2) ubuntu a "si mismo"
Modifica la direcciones de ip, el directorio compartido y el usuario

smbclient -L  //192.168.6.35/apublico  --user=juancito

smbclient -L  //127.0.0.1/

Acordate que donde uno toca algo hay que reiniciar los servicios o la máquina.

---

### Post by Packo_z007 on 2010-07-18
Voy a probar en un rato por que no tengo la pc libre ahora. Lo que si me olvide de decir y no se si será importante, es que la pc con ubuntu, no esta conectada al router via ethernet sino via USB. Muchas gracias por las respuestas.

---

### Post by biale on 2010-07-18
USB en lugar de eth molesta pero no impide. Lo ideal sería una conexión por cable provisoria para disminuir la incertidumbre, o sea ponerse en las mejores condiciones posibles.

Donde se accede por dirección de IP lo importante para empezar es tener esa dirección de IP en la subred con lo que sea.
Si se hace mensión de una interfase en principio debería coincidir con exactitud. Pero a veces toma eth aunque sea wlan.

Podemos suponer que las dos PCs comparten la subred sin enrutamientos?

Ahora me doy cuenta que no mensione al archivo smbusers. Si no esta mejor.

---

### Post by Packo_z007 on 2010-07-19
Bueno, probe un par de cosas. Aqui estan los resultados:

**Montando una sesión con el CD en la pc con ubuntu**. El eth1 es el USB. Tambien probe conectandolo via ethernet pero los resultados son los mismos.

```

ubuntu@ubuntu:~$ smbclient -L //10.0.0.3/
Enter ubuntu's password: 
Connection to 10.0.0.3 failed (Error NT_STATUS_UNSUCCESSFUL)
ubuntu@ubuntu:~$ smbclient -L //10.0.0.4/
Enter ubuntu's password: 
Connection to 10.0.0.4 failed (Error NT_STATUS_CONNECTION_REFUSED)
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:89:16:5c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1d:8b:0d:09:47  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:8bff:fe0d:947/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20191 (20.1 KB)  TX bytes:14316 (14.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)

```**Desde la version de ubuntu que tengo instalada:**
```

franco@pc3000:~$ ping -c 5 10.0.0.3
PING 10.0.0.3 (10.0.0.3) 56(84) bytes of data.
64 bytes from 10.0.0.3: icmp_seq=1 ttl=128 time=0.966 ms
64 bytes from 10.0.0.3: icmp_seq=2 ttl=128 time=1.20 ms
64 bytes from 10.0.0.3: icmp_seq=3 ttl=128 time=1.19 ms
64 bytes from 10.0.0.3: icmp_seq=4 ttl=128 time=1.14 ms
64 bytes from 10.0.0.3: icmp_seq=5 ttl=128 time=1.20 ms

--- 10.0.0.3 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 0.966/1.141/1.206/0.100 ms
franco@pc3000:~$ smbclient -L //10.0.0.3/
Enter franco's password: 
Connection to 10.0.0.3 failed (Error NT_STATUS_UNSUCCESSFUL)
franco@pc3000:~$ smbclient -L //10.0.0.4/
Enter franco's password: 
Domain=[CASA] OS=[Unix] Server=[Samba 3.4.7]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

```La ip 10.0.0.3 corresponde a la pc con windows XP y 10.0.0.4 a la pc con ubuntu.
[B]
Por último dejo el smb.conf[/B]:

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#...
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Casa

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = wins lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 10.0.0.0/8 eth0 eth1

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

   client ntlmv2 auth = no

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


```Además borre el archivo lmhosts. Gracias

Edito:

**Testparm:**
```

franco@pc3000:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = CASA
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

---

### Post by biale on 2010-07-21
De la sesión bajo live CD observo que aparece "Enter ubuntu's password:" 
¿Definiste en tu Win un usuario "ubuntu"? Para ingresar a windows necesitas usar una cuenta de usuario que este definida (existente)en tu windows. Luego necesitas ingresar la clave de ese usuario Windows. En principio esa clave no debe ser nula.  A su vez el share (la rama compartida) debe tener permisos de lectura para ese usuario que ingresaste o su grupo local.

smbclient -L ///10.0.0.3/ --user=<usuario_que_uses_en_windows>

smbclient -L ///10.0.0.3/ --user=Administrador

---

### Post by biale on 2010-07-21
Para el smb.conf:

'client lanman auth' is disabled -> comentamos estas dos lineas

#  security = share
#  client ntlmv2 auth = no

Al final de todo y para compartir algo, agregamos:

[franco]
 	comment = ubuntu-franco
 	path = /home/franco
	writeable = no
	browseable = yes
	guest ok = no
	read list = @users
	write list = franco

Reinicializar la PC y probar...

---

### Post by Packo_z007 on 2010-07-23
Ahora mejoró :D. Hice los cambios en smb.conf y ahora la pc con ubuntu puede acceder a si misma sin inconvenientes.

```
franco@pc3000:~$ smbclient -L //10.0.0.3/ --user=franco
Enter franco's password: 
Domain=[CASA] OS=[Unix] Server=[Samba 3.4.7]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    franco          Disk      ubuntu-franco
    IPC$            IPC       IPC Service (pc3000 server (Samba, Ubuntu))
    música         Disk      
Domain=[CASA] OS=[Unix] Server=[Samba 3.4.7]

    Server               Comment
    ---------            -------
    PC3000               pc3000 server (Samba, Ubuntu)
    PC4200               PC arriba

    Workgroup            Master
    ---------            -------
    CASA                 PC3000
franco@pc3000:~$ smbclient -L //10.0.0.4/ --user=franco
Enter franco's password: 
Connection to 10.0.0.4 failed (Error NT_STATUS_UNSUCCESSFUL)

```

Pero si trato de acceder desde windows a ubuntu, al clickear en una carpeta compartida, obtengo un error que dice que no tengo los permisos necesarios para acceder.

Si trato de entrar desde ubuntu a windows desde nautilus, al hacer click en el equipo, me dice falló al obtener la lista de comparticion del servidor.


No tengo muy en claro como gestionar los usuarios de samba. Actualmente en ubuntu, xp y samba tengo una cuenta con usuario franco, y el mismo password para todas. Muchas gracias.

---

### Post by biale on 2010-07-24
"Desde Windows a Ubuntu". En el share [franco] había puesto:

guest ok = no
read list = @users

Y ahora descubro que en Lucid por default "franco" no estaría como miembro del grupo 100 "users". Modificamos la linea para agregarte:

guest ok = no
read list = @users, franco

Tambien para probar se podría haber puesto "guest ok = yes" (sin las comillas).

Ademas y para probar podemos compartir la u de CD/DVD que no tiene problemas con los permisos. (Ojo: un CD/DVD tiene que estar previamente "montado" desde ubuntu)

# A sample share for sharing your CD-ROM with others.
[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /cdrom
   guest ok = yes

Hasta ahí los permisos propios de samba.

¿Tocaste los permisos de ubuntu?  Para hacerla facil, necesitamos lectura y ejecución para la cadena de directorios, empezando por el mismo /home. Por default octal 755. Y algún archivo final para probar con 644, aunque con menos andaría.

---

### Post by Packo_z007 on 2010-07-24
Con esos ultimos cambios puedo acceder sin problemas desde windows a ubuntu. Funciona perfecto.  Desde ubuntu a windows sigo teniendo el mismo problema.

No toqué los permisos de las carpetas de ubuntu. Solo comparti la carpeta "Musica" mediante la GUI. Muchisimas gracias.

---

### Post by biale on 2010-07-24
Casi solved!

"Ubuntu a Windows".

Parece facil, pero WXP se fué modificando de a poco hasta llegar a tener un sistema de permisos con una complejidad espeluznante.

Para probar conviene desactivar la firewall de WXP, sin olvidarse de reactivarla despues. "WXP la necesita"

WXP también tiene un doble juego de permisos de acceso. A nivel de la cadena de directorios y a nivel del share.

A nivel de cadena de directorios existe un modo básico para compartir y un modo avanzado. Y a su vez el modo avanzado tiene un segundo modo avanzado.

Si todo funciona como me gustaría en las carpetas tenés dos solapas. Una para la seguridad en general y otra para la función de compartir.

A nivel de share (compartir) asegurate de dar (por lo menos) permisos de lectura al grupo de los usuarios locales. También se podría dar permisos de lectura al grupo "todos", no es dañino. Tip: trata de que el nombre del share tenga hasta 8 caracteres sin blancos en el medio.

A su vez la seguridad local debería permitir el acceso en modo lectura y ejecución al grupo "Usuarios" y asegurarse que tu cuenta de usuario este (también) en ese grupo. Y cuando digo "carpeta" se entiende "esta carpeta, subcarpeta y archivos"

En lo demás, y salvo de que un archivo tenga ACL propia, trabaja por herencia. Tendría que funcionar.

Y si no trabajas con un usuario "recortado" podes reemplazar donde dije grupo "Usuarios" con el grupo "Administradores"

Acordate que el acceso desde Linux require la mensión correcta tanto del usuario como del grupo de trabajo.

Por las dudas aclaro que WXP tiene un bonito comando de consola "cacls" para mostrar los permisos, aunque dudo que el problema este alli.

Lo que compartas debe aparecer en "Mis sitios de red", "Ver equipos del grupo de trabajo", etc

Exitos!

---

### Post by Packo_z007 on 2010-07-29
Gracias por contestar y mil disculpas por no haber respondido antes. Bueno resulta que el problema de configuracion creo que no esta en windows. Antes de instalar ubuntu en la otra pc, tenia XP tambien, y la red funcionaba perfectamente. 
Desde XP puedo ver y acceder a ambas pcs sin problemas. 

 En ubuntu, cuando hago click en el equipo con XP ni si quiera me pide el usuario o el password. Sólo me da el error de Falló al montar..etc. 

Lo digo sin saber, pero creo que puede ser un problema con algun puerto que utilice samba o con las cuentas de usuario. No tengo idea como diagnosticar eso. Muchas gracias

---

### Post by biale on 2010-07-31
Buen dato, lo raro hubiera sido que así funcionara. Acordate que no estabamos resolviendo netbios.

Desde Ubuntu (hacia windows) postea que se sale con:

smbtree -b -d 2

Deberia mostrar todos los "shares" que compartiste en WXP.

---

### Post by Packo_z007 on 2010-08-04
Muestra solo los shares de Ubuntu( PC3000 ):

```

franco@pc3000:~$ smbtree -b -d 2
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth1 ip=fe80::21d:8bff:fe0d:947%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=10.0.0.3 bcast=10.0.0.255 netmask=255.255.255.0
Enter franco's password: 
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permiso denegado
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
CASA
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el fichero ó directorio
    \\PC3000                 pc3000 server (Samba, Ubuntu)
Got a positive name query response from 127.0.0.1 ( 10.0.0.3 10.0.0.4 )
        \\PC3000\música            
        \\PC3000\IPC$               IPC Service (pc3000 server (Samba, Ubuntu))
        \\PC3000\franco             ubuntu-franco
        \\PC3000\cdrom              Samba server's CD-ROM
        \\PC3000\print$             Printer Drivers

```

---

### Post by biale on 2010-08-04
Los shares de Windows no estan llegando.

Fijate que Ubuntu (10.0.0.4) intenta usar la dirección de Windows como si fuera propia, en eth1 (?):

```
La ip 10.0.0.3 corresponde a la pc con windows XP y 10.0.0.4 a la pc con ubuntu.
```

> added interface eth1 ip=10.0.0.3 bcast=10.0.0.255 netmask=255.255.255.0

```
Got a positive name query response from 127.0.0.1 ( 10.0.0.3 10.0.0.4 
```

Por broadcast (-b) ni siquiera obtiene a la pc windows. Ahora no aparece...

```
   PC4200               PC arriba
```

(1) Parece haber una galleta en la definiciones de IP. Como asignas las direcciones de IP de los equipos, fijas o dhcp?
(2) Luego de alguna prueba, puede haber quedado en algun archivo de configuracion de Ubuntu la direccion 10.0.0.3 ?  

- Si repetis el comando anterior con "PC arriba" apagada no debería aparecer mas que una y solo una direccion de IP. O sea "nadie de afuera va a responder los broadcast"

- Se podría intentar cambiar provisoriamente la direccion de IP de Windows (Ej: 10.0.0.10) para evitar el solapamiento. Los shares (o al menos la PC) deberían aparecer.

---

### Post by Packo_z007 on 2010-08-09
> 1) Parece haber una galleta en la definiciones de IP. Como asignas las direcciones de IP de los equipos, fijas o dhcp?
(2) Luego de alguna prueba, puede haber quedado en algun archivo de configuracion de Ubuntu la direccion 10.0.0.3 ?(1)Ambas estaban con dhcp. Ahora le puse fija a windows, en 10.0.0.3 ( No se como hacerlo en ubuntu ).
(2)Efectivamente, me habia quedado un lmhosts en windows. Lo borre y ahora cambió un poco la cuestion:

```
franco@pc3000:~$ smbtree -b -d 2
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth1 ip=fe80::21d:8bff:fe0d:947%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=10.0.0.4 bcast=10.0.0.255 netmask=255.255.255.0
Enter franco's password: 
Got a positive name query response from 10.0.0.4 ( 10.0.0.4 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permiso denegado
Got a positive name query response from 10.0.0.4 ( 10.0.0.4 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
CASA
Got a positive name query response from 10.0.0.4 ( 10.0.0.4 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
    \\PC4200                 PC arriba
    \\PC3000                 pc3000 server (Samba, Ubuntu)
        \\PC3000\música            
        \\PC3000\IPC$               IPC Service (pc3000 server (Samba, Ubuntu))
        \\PC3000\franco             ubuntu-franco
        \\PC3000\cdrom              Samba server's CD-ROM
        \\PC3000\print$             Printer Drivers
franco@pc3000:~$ smbclient -L //10.0.0.3/ --user=franco
Enter franco's password: 
Connection to 10.0.0.3 failed (Error NT_STATUS_UNSUCCESSFUL)
franco@pc3000:~$ 

```

Sinceramente aprecio muchisimo la ayuda que me estas dando. Gracias.

---

### Post by guillermolisi on 2010-08-09
Para configurar una placa de red con IP estatica tenes por lo menos dos formas: Network Manager o editar el archivo /etc/network/interfaces.

Si utilizas esta ultima opcion te deberia quedar mas o menos asi (salvando las diferencias de bloques IP y cantidad de placas para tu red en uso):

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth1 inet dhcp
#auto eth1

iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
auto eth1

iface eth0 inet static
address 90.0.0.1
netmask 255.255.255.0
gateway 90.0.0.2
network 90.0.0.0
dns-nameservers 90.0.0.2
dns-search unimix
auto eth0
```

---

### Post by biale on 2010-08-09
La idea era fijar la dirección de IP del Windows en un valor distinto para desacoplar el broadcast de alguna definición que hubiera quedado. Por eso lo de "10.0.0.10".

No hace falta tocar la dirección de IP Ubuntu.

Puede haber quedado en Windows alguna otra modificación?
Que tiene el archivo de /etc/hosts de Ubuntu?

Ademas del nombre del host, smbtree debería mostrar los shares que Windows publica. Ubuntu no esta interpretando los shares que Windows publica o eventualmente Windows no los esta publicando. 

Encuentro un detalle que no es menor: ¿volviste a Samba3 o en este momento quedo instalado Samba4? .

Porque Samba 3 y Samba 4 son distintos. Por ejemplo, Samba 4 utiliza un binder propio o sea que no debería haberse instalado Winbind, etc.

Si quedo Samba 4, lo mejor es: (1) Salvar el archivo smb.conf que tenemos (2) Desinstalar el forma completa Samba y Winbind (3) Borrar las logs de Samba (/var/log/samba si mal no recuerdo) (4) Reinstalar Samba3 y Winbind. (5) Reponer el archivo smb.conf que modificado.

Por la dudas también hay que asegurarse que el archivo nsswitch sea coherente con el archivo smb.conf.

Luego de eso, fijate si la salida de los comandos "smbtree -b -d 2" y "smbtree -N -d 2" son parecidas: "muestran los shares de WXP".

---

### Post by biale on 2010-08-09
Equivoque al flag!  Donde dice "smbtree -N -d 2" debe decir:
  "smbtree -S -d 2"

---

### Post by Packo_z007 on 2010-08-18
Cambie de ip a 10.0.0.10 y el problema persiste.

En windows estoy seguro de que no toque nada mas

El archivo /etc/hosts dice :

```

127.0.0.1    localhost
127.0.1.1    pc3000

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Actualmente uso la version 3.4.7 de samba


El archivo nsswitch:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```La salida de los comandos smbtree
```
franco@pc3000:~$ smbtree -b -d 2
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth1 ip=fe80::21d:8bff:fe0d:947%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=10.0.0.3 bcast=10.0.0.255 netmask=255.255.255.0
Enter franco's password: 
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permiso denegado
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
CASA
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
    \\PC4200                 PC arriba
    \\PC3000                 pc3000 server (Samba, Ubuntu)
        \\PC3000\música            
        \\PC3000\IPC$               IPC Service (pc3000 server (Samba, Ubuntu))
        \\PC3000\franco             ubuntu-franco
        \\PC3000\cdrom              Samba server's CD-ROM
        \\PC3000\print$             Printer Drivers
franco@pc3000:~$ smbtree -S -d 2
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface eth1 ip=fe80::21d:8bff:fe0d:947%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=10.0.0.3 bcast=10.0.0.255 netmask=255.255.255.0
Enter franco's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permiso denegado
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
CASA
Got a positive name query response from 10.0.0.3 ( 10.0.0.3 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No existe el archivo o directorio
    \\PC4200                 PC arriba
    \\PC3000                 pc3000 server (Samba, Ubuntu)
franco@pc3000:~$
```Por ultimo, hoy actualice samba a la version 3.4.7. Mientras instalaba me dio la opcion de reemplazar el archivo smb.conf actual o conservarlo. Lo reemplace y no cambio nada asi que lo restaure despues. Por si sirve de algo dejo las diferencias entre ambos archivos

```
--- /etc/samba/smb.conf 2010-08-18 00:52:43.187438891 -0300
+++ /var/run/samba/upgrades/smb.conf 2010-08-18 00:52:43.277438962 -0300
@@ -42,7 +42,7 @@
 
 # Windows Internet Name Serving Support Section:
 # WINS Support - Tells the NMBD component of Samba to enable its WINS Server
- wins support = yes
+# wins support = no
 
 # WINS Server - Tells the NMBD components of Samba to be a WINS Client
 # Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
@@ -53,14 +53,14 @@
 
 # What naming service and in what order should we use to resolve host names
 # to IP addresses
-; name resolve order = wins lmhosts host wins bcast
+; name resolve order = lmhosts host wins bcast
 
 #### Networking ####
 
 # The specific set of interfaces / networks to bind to
 # This can be either the interface name or an IP address/netmask;
 # interface names are normally preferred
-; interfaces = 10.0.0.0/8 eth0 eth1
+; interfaces = 127.0.0.0/8 eth0
 
 # Only bind to the named interfaces and/or networks; you must use the
 # 'interfaces' option above to use this.
@@ -99,9 +99,7 @@
 # in this server for every user accessing the server. See
 # /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
 # in the samba-doc package for details.
-# security = share
-
-# client ntlmv2 auth = no
+# security = user
 
 # You may wish to use password encryption. See the section on
 # 'encrypt passwords' in the smb.conf(5) manpage before enabling.
@@ -315,12 +313,12 @@
 ; write list = root, @lpadmin
 
 # A sample share for sharing your CD-ROM with others.
-[cdrom]
- comment = Samba server's CD-ROM
- read only = yes
- locking = no
- path = /cdrom
- guest ok = yes
+;[cdrom]
+; comment = Samba server's CD-ROM
+; read only = yes
+; locking = no
+; path = /cdrom
+; guest ok = yes
 
 # The next two parameters show how to auto-mount a CD-ROM when the
 # cdrom share is accesed. For this to work /etc/fstab must contain
```

---

### Post by biale on 2010-08-24
Fijate si los servicios winbindd y nmbd estan corriendo...

Si winbindd esta corriendo, tal como esta la configuración,
pone en el archivo smb.conf:

  wins support = yes

  name resolve order = wins lmhosts host bcast

OJO: en la linea anterior NO pongas dos veces a wins porque trae problemas.

Y si anda peor volvé atras las modificaciones.

smbtree debería mostrar los mismos shares que muestra WXP con el comando de consola:

  net share

Por lo menos "IPC$"

---

### Post by Packo_z007 on 2010-08-26
Estan corriendo windbind ( con una sola d ) y nmbd tambien. Probe haciendo esos cambios y nada. Ni si quiera veo el equipo con xp. Gracias.

---


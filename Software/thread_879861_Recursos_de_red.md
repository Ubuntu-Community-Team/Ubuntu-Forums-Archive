---
title: "Recursos de red"
date: 2008-08-04
forum: Software
---

### Post by Simbiosys on 2008-08-04
Hola, como andan? 
Tengo el siguiente inconveniente, en mi trabajo tenemos una PC con Windows XP y comparte una carpeta e impresora. En esa impresora todos imprimen, claro... todos menos yo.

Desde otra PC desktop con Ubuntu 7.10 está configurada la impresora e imprime sin problemas, también desde 2 Powerbook y 1 iMac, desde otros Windows también.

Pero yo... no, cuando entro a Red e ingreso a la pc en cuestión, tampoco veo los recursos compartidos... ahora si escribo en el URL la dirección smb correcta, ingresa. Pero con la impresora estoy perdido... ¿Cual puede ser el problema? probé reinstalando SAMBA pero sigo con inconvenientes.

Desde ya, mil gracias.

pd: la impresora es una HP 1020

---

### Post by User21 on 2008-08-07
Tenemos la misma impresora en mi oficina, y no hemos tenido ningun problema. Incluso puedo imprimir desde el LIVE CD sin dramas. Hiciste el asistente de agregar impresora ?

---

### Post by faktorqm on 2008-08-07
postea el smb.conf a ver que esta pasando. me parece MUY raro... fuiste a sistema -> administracion -> samba? salu2!

---

### Post by Simbiosys on 2008-08-19
[HTML]#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = DOMINIOARKIOS

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

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
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[/HTML]

Antes funcionaba, mi problema es que no veo los recursos de red... tampoco veo la impresora... por ejemplo entro a smb://192.168.X.X y se que en esa IP hay compartida 2 carpetas y una impresora, ahora desde mi laptop no veo esos recursos. Me aparece en blanco...

muchas gracias!!!

---

### Post by faktorqm on 2008-08-20
hace

```
sudo cp /etc/smb.conf /etc/smb.conf_vacap
```

y luego edita el que tenes y dejalo como algo asi:

```

[global]
workgroup = DOMINIOARKIOS
server string = %h server (Samba, Ubuntu)
dns proxy = no
security = share

```

entonces ahi te fijas bien. si podes acceder y demas a todos lados. si podes le vas agregando cosas de a poco y viendo si todo funciona hasta saber cual de todas las lineas es la que produce la falla. Yo habia hecho un tutorial de samba, anda por ahi en este foro. Salu2!!

---

### Post by Simbiosys on 2008-08-20
**faktorqm**, muchas gracias por tu respuesta! Te cuento que hice lo que dijiste, te dejo un cat del archivo de configuración actual de mi samba:
[HTML]
#
# Samba Sapote
#

[global]
workgroup = DOMINIOARKIOS
server string = %h server (Samba, Ubuntu)
dns proxy = no
security = share
[/HTML]

Reinicié el servicio y nada. Reinicié la computadora y nada... el problema persiste. Para ser un poco mas práctico, te dejo una captura de pantalla de lo que veo cuando accedo a una computadora de mi red desde mi laptop y un ejemplo de cuando accedo desde otra computadora con Windows.

---

### Post by faktorqm on 2008-08-21
La verdad no se che.. habria que ver el dominio que tipo de seguridad tiene, o de ponerle la opcion netbios name al smb.conf con el mismo nombre que a la pc en windows.
te tendria que quedar 

```
netbios name = nombre_pc
```

ahora no tengo un ubuntu cerca, pero en casa tengo un icono en sistema -> administracion -> samba, queria pasarte el nombre del paquete pero bueno... no tengo un ubuntu cerca. cualquier cosa despues te lo paso. Desde ahi configuras todo re bien y te escribe automaticamente el smb.conf.

Si te sirve, yo hice un tutorial de samba (basico) para compartir algunas cosas, leelo capaz te sirve. [http://ubuntuforums.org/showthread.php?t=697717](http://ubuntuforums.org/showthread.php?t=697717)

fijate que a lo ultimo dice que puertos usa samba, capaz los tenes filtrados por el firewall. revisa primero eso antes que nada. salu2!

---

### Post by Simbiosys on 2008-08-22
Estimado, gracias por tu rta.
Te comento que ahora que lo nombrás, en algún momento instalé Firestarter pero como no me resultó útil lo borre... ¿como hago para verificar los puertos? Agregando eso que me dijiste, el problema persiste. Probé volver a reinstalar el samba y tampoco...

Gracias por tu ayuda :guitar:

---

### Post by Simbiosys on 2008-08-25
Hola, instale el Firestarter nuevamente e intente configurarlo... sin éxito, creo que es el iptables el que me bloquea el tema de la red... les dejo dos capturas de pantalla, no se porque no funciona... configuré como corresponde (o como creo que corresponde) el Firestarter pero el problema persiste...

Gracias

---

### Post by Simbiosys on 2008-08-25
Agrego: ahora tampoco veo las pcs que forman parte del grupo de trabajo... aparece 0 elementos.

Vamos de mal en peor!! jaja... estoy evaluando reinstalar todoooooo!! :(

---

### Post by Simbiosys on 2008-08-25
El error en Firestarter fue que la regla la armé mal, puse:

192.168.1.0/255

En verdad, lo que va despues de la "/" es la notación [CIDR]("http://en.wikipedia.org/wiki/CIDR#CIDR_and_masks").

Quedó asi:

192.168.1.0/24

Ahhh....

Ya puedo imprimir (pude agregar la impresora poniendo directamente la dirección de SMB://)
Las pcs las veo, los grupos de trabajo también pero **los recursos compartidos, no**. :mad:

En el caso de algunas computadoras sí me muestra y en otras no... ¿Que carancho puede ser ahora? Estoy taaaaaan cerca de la solución.... :confused:

---

### Post by faktorqm on 2008-08-25
uf! que lio! el admin de la red no esta no? :P

Lo que ves en algunas si y en otras no, tenes que fijarte bien por donde estas pasando (va, yo haria eso) revisar si desde otra pc si se ven los recursos, compartir algo en la mia para ver si los demas me ven, revisar que el usuario (y la contraseña) con el que me estoy conectando sea el correcto, fijarte que no te bloquee tu propio firewall, o el del otro, si el antivirus del otro por alguna casualidad de la vida te bloquea por que pìensa que sos un virus tonces no te da acceso a lectura, si el tipo tiene 2 firewall y vos no lo sabes, pueden pasar 1000 cosas! suerte con eso y cualquier cosa pregunta! salu2!

---

### Post by hector_roberts on 2009-02-17
despues de una actualización de ubuntu el 16/02/2009 tengo el mismo problema, solo puedo ver los recursos compartidos poniendo smb: en la barra del nautilus, cuando antes no era necesario. Además, no puedo imprimir en la laser compartida. Espero no tener que reinstalar. Como comentario, la pc donde esta instalada la impresora laser cada tanto había que reiniciarla para que imprima, lo raro es que todos los puestos windows imprimen y mi puesto linux no, pero bueno, quiero creer que algo de culpa tiene el WINDOWS  de la pc donde está conectada la laser. Sigo participando.je.

---


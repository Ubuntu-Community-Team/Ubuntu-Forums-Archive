---
title: "Samba me está dando un baile....."
date: 2010-09-18
forum: Software
---

### Post by dam1977 on 2010-09-18
A mi jefe se le ocurrió la excelente idea de que en mi equipo tenga el disco externo donde se guardan todos los archivos de trabajo de la empresa, debido a que mi maquina con Ubuntu (dice) es la única que no tiene problemas. Barbaro. Ahora vienen los problemas. Instalé Samba. Fuí a Sistema/Administración/Samba e hice todos los pasos de configuración. Pero cuando se quiere acceder desde otra máquina (son 5 y todas con Windows XP), aparece la carpeta compartida (Archivos de Trabajo) pero cuando se quiere entrar aparece un cartelito diciendo que el recurso de red no está compartido. Reviso desde mi equipo la configuración, agrego una carpeta en mi equipo como recurso de red y esa carpeta si se puede usar desde otros equipos. El problema afecta solamente al dichoso disco externo (un WD de 500 gigas). Alguna manera de salvar la situación y no quedar como el traste con mi jefe? Por favor y gracias a todos!!! (Guillermolisi salvameeeee)

---

### Post by beren.olvar on 2010-09-18
podrias postear tu /etc/samba/smb.conf ?

segun parece seria necesario anhadir las lineas
force user = nombre_de_usuario
force group = nombre_de_usuario
para que lo comparta con los permisos adecuados.

---

### Post by formerlypoliticalusername on 2010-09-18
Oye solo por si te puede ayudar por que no pruebas gadmin-samba 0.2.8,es una interfaz gráfica muy completa.suerte.está en synaptic.

---

### Post by dam1977 on 2010-09-19
Gracias y les comento... Deseo configurar el acceso al disco externo de tal modo que todos los usuarios y sus equipos tengan acceso de lectura y escritura. Más adelante veré cómo limitar el acceso de cada usuario a las carpetas que usa cada uno. Pero por el momento quiero solo que todos puedan acceder. El lunes a primera hora estoy tratando de romper mi cabeza con el asunto...

---

### Post by dam1977 on 2010-09-20
Bueno, ahi va mi fstab!
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = exoz

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

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
#   security = SHARE

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = share
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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

[EXOZ MAIN]
	path = /media/EXOZ MAIN
	writeable = yes
;	browseable = yes
	guest ok = yes

[ARCHIVOS DE TRABAJO]
	path = /media/EXOZ MAIN/EXOZ/EXOZ/ARCHIVOS DE TRABAJO
	writeable = yes
;	browseable = yes
	guest ok = yes

---

### Post by biale on 2010-09-20
Que te muestra el testparm? Fijate los dos espacios en blanco en ARCHIVOS DE TRABAJO:

path = /media/EXOZ MAIN/EXOZ/EXOZ/ARCHIVOS DE TRABAJO

---

### Post by granjero on 2010-09-20
fijate de descomentar la línea de security

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
# security = SHARE

dejala así

security = SHARE

sin el numeral
ahí todos deberían poder escribir y ver si dramas.

y copia el resultado de "testparm"

y como te dice biale, el tema de los espacios en los nombres de directorio no son amigables

para completarlos andá poeniendo en una terminal 

/media/EX[tab] al poner tab te autocompleta y vas a ver que mete unas barras. hacé así hasta llegar al final de la linea que querés y copiala al smb.conf

porque no te va a reconocer los espacios.

salud!

---

### Post by dam1977 on 2010-09-24
Ahi va el resultado del testparm:
daniel@EXOZ-daniel:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[EXOZ MAIN]"
Processing section "[ARCHIVOS DE TRABAJO]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = EXOZ
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
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

[EXOZ MAIN]
	path = /media/EXOZ MAIN
	read only = No
	guest ok = Yes

[ARCHIVOS DE TRABAJO]
	path = /media/EXOZ MAIN/EXOZ/EXOZ/ARCHIVOS DE TRABAJO
	read only = No
	guest ok = Yes
daniel@EXOZ-daniel:~$

---

### Post by granjero on 2010-09-24
buenas...

el testparm lo hiciste sin tocar nada todavía. no?

fijate que no te está tomando el 

security = share

y los directorios siguen con los espacios...
eso seguro es parte del problema.


te dejo una copia del testparm de mi disco compartido

```
administrador@zeta:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[disco-zeta]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = ZETA
	server string = zeta
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
	unix extensions = No
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[disco-zeta]
	path = /home/administrador/publico
	read only = No
	guest ok = Yes

```

me parece que los espacios los deberías poner así

```

[EXOZ MAIN]
path = /media/EXOZ\ MAIN/

[ARCHIVOS DE TRABAJO]
path = /media/EXOZ\ MAIN/EXOZ/EXOZ/ARCHIVOS\ DE\ TRABAJO/

```

o así que es como tuve que poner en el fstab una vez...

```
//192.168.1.122/datos/carpeta\040compartida
```

"\040" reemplaza el espacio en el fstab

no estoy seguro como funciona en samba

salud!

---

### Post by faktorqm on 2010-09-25
yo acá hice un tutorial (esta en el foro igual) para que te puedas defender con samba.

puede ser que hayan cambiado algunas cosas, aunque no creo, cualquier cosa chifla salu2!

[http://www.sismonda.com.ar/procedimientos/samba-para-compartir-carpetas-en-una-red-hogareñ](http://www.sismonda.com.ar/procedimientos/samba-para-compartir-carpetas-en-una-red-hogareñ)

---

### Post by dam1977 on 2010-09-30
Saqué los espacios de EXOZ MAIN. Pero en el testparm sigue sin aparecer la linea security = SHARE. No entiendo por que extraña razón. Y sigo sin poder compartir el disco externo...

---

### Post by granjero on 2010-10-01
copia el resultado de testparm con las modificaciones y el smb.conf nuevo...

salud!

---


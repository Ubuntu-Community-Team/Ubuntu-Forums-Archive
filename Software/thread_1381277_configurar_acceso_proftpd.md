---
title: "configurar acceso proftpd"
date: 2010-01-14
forum: Software
---

### Post by _ZeTa on 2010-01-14
buenas a todos!
mi problema radica en que necesito configurar el FTP de un servidor y la verdad es que ya me está quedando grande...
segui lo que decía [esta guia]("http://www.frikis.org/staticpages/index.php?page=proftpd") y la verdad es que no me resultó...

me sale el siguiente error cuando trato de conectarme:

```
Comando: USER usuario
Respuesta: 331 Password required for usuario
Comando: PASS ********
Respuesta: 530 Login incorrect.
Error: Error crítico
Error: No se pudo conectar al servidor
```

Les dejo mi proftpd.conf para ver si ahi está el problema.

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"zarq"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
DefaultRoot			~
AuthUserFile			"/etc/passwd"
AuthGroupFile			"/etc/group"

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			6

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log
ExtendedLog /var/log/proftpd/proftp.down_up_log WRITE,READ write
ExtendedLog /var/log/proftpd/proftpd.auth_log  AUTH auth
ExtendedLog /var/log//proftpd/proftpd.paranoid_log ALL default

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

<Directory /var/www/talcaorg/>
Umask 		077 077
AllowOverwrite	on
<Limit READ WRITE STOR>
AllowAll
</Limit>
</Directory>
```


saludos! ;)

---

### Post by CdK1 on 2010-01-14
Ese usuario que conecta, es un usuario del sistema?

---

### Post by _ZeTa on 2010-01-14
seps, lo cree como usuario de sistema y lo puse como sbin/false

---

### Post by CdK1 on 2010-01-14
Creo que ahí está el error, trata de conectarte con un usario válido, que tenga shell...

---

### Post by Carlos C on 2010-01-15
Sin querer desvirtuar la conversación, ¿no has considerado configurar ssh para tener sftp que es más seguro?

Saludos.

---

### Post by _ZeTa on 2010-01-18
sftp... mmm de hecho yo lo ocupo, pero el problema es que los usuarios que vaya creando son los que necesitan accesar a la información y no todos saben como configurar un cliente ftp para que acceda por sftp.

La idea es que no cambie el sistema, pero voy a leer al respecto.
Gracias Carlos!



> **CdK1 said:**
> Creo que ahí está el error, trata de conectarte con un usario válido, que tenga shell...

y como se hace eso???
traté de conectarme con root, pero me sale el mismo error...

---


---
title: "No accedo a Directorios Samba desde Windws XP"
date: 2011-12-09
forum: Software
---

### Post by javierlinux1 on 2011-12-09
Retomo el tema SAMBA, hace unos días abrí un hilo por un error, acá: [http://ubuntuforums.org/showthread.php?t=1887257](http://ubuntuforums.org/showthread.php?t=1887257) y se pudo solucionar.

El problema ahora es que desde los puestos con Windows no puedo acceder a los directorios compartidos en el Server Linux, se ven en el Explorador de Archivos, pero si intento acceder me pide usuario y conraseña y cuando se los doy los vuelve a pedir y no accede.

Para hacer pruebas cree en el server un usuario javier, clave 1234 con smbpasswd -a javier y en Windows XP cree el mismo usuario, con la misma clave con permisos de Administrador, pero no hay caso. En mi consulta anterior está el smb.conf que esta usando el servidor.

Si alguien ve cual es mi error, agradezco la ayuda.

Javier

---

### Post by javierlinux1 on 2011-12-17
Sigo sin poder solucionar esto. Me gustaría saber si la falta de respuestas se debe a lagun error en la formulación de la consulta. Es un tema que necesito solucionar y no encuentro donde puede estar mi error. Si alguien me puede ayudar, agradecido.

---

### Post by granjero on 2011-12-21
las carpetas compartidas por samba tienen permiso de escritura y lectura para el usuario que las tiene que leer?

que te da la salida de ```
testparm
``` en el servidor?

---

### Post by javierlinux1 on 2011-12-27
> **granjero said:**
> las carpetas compartidas por samba tienen permiso de escritura y lectura para el usuario que las tiene que leer?

que te da la salida de ```
testparm
``` en el servidor?

Gracias por responder, no estuve unos días, aquí me reporto y pego abajo la salida del comando testparm:

[root@servidor:/]$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Sueldos]"
Processing section "[Catedral]"
Processing section "[Publico]"
Processing section "[homes]"
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = ESTUDIO
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
        name resolve order = lmhosts host wins bcast
        printcap name = cups
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        valid users = nobody
        read only = No

[Sueldos]
        comment = Directorio Sueldos
        path = /data/sueldos
        valid users = nobody
        read only = No

[Catedral]
        comment = Directorio Catedral
        path = /data/catedral
        valid users = nobody
        read only = No

[Publico]
        comment = Directorio Publico
        path = /data/publico
        valid users = nobody
        read only = No

[homes]
        valid users = nobody
        read only = No

Espero sus comentarios. Y gracias de antemano.
Saludos

---

### Post by biale on 2011-12-27
Fijate como estas mapeando al usuario "javier" en sl archivo smbusers.

Fijate ademas que permisos en "modo local" tiene el usuario javier. O (solo para probar) dale permisos 777 a toda la cadena que contiene el share. Mínimo, permisos de ejecución a nivel de toda la cadena de directorios.

---

### Post by granjero on 2011-12-28
a mi me llama la atención que todas las llaves tengan esto

```
valid users = nobody
```

Esta es una de las llaves de mi server...

```
[Secretaria General]
	path = /home/SERVER/secretaria-general
	valid users = @secretaria
	read list = @secretaria
	write list = @secretaria
	force group = secretaria
	create mask = 0770
	directory mask = 0770
```

la arroba indica grupo....

salud!

salud!

---

### Post by biale on 2011-12-28
De acuerdo, convendría sacarlo. Yo no lo tengo activo:

```

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

```

Para un ejemplo de share, donde los usuarios de los grupos users y p24 leen, pero solo el usuario pruebas escribe:

```

[pPublico]
	comment = pruebas-Publico
	path = /home/pruebas/Público
	writeable = no
	browseable = yes
	guest ok = no
	read list = @users, @p24
	write list = pruebas

```

Ahora bien, si el usuario pruebas hace un login al server en modo local, puede operar sobre el directorio. Tiene permisos de ejecución sobre  /home/pruebas y permisos de escritura sobre Público

---


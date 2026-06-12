---
title: "Problema con CUPS"
date: 2009-08-14
forum: Software
---

### Post by leosr on 2009-08-14
Hola.
En un thread preguntaron cómo compartir impresoras entre dos PCs con Ubuntu (en mi caso Ubuntu JJ y Xubuntu JJ usando LXDE), seguí el tutorial que pasaron ([http://ubuntu-ar.org/node/202](http://ubuntu-ar.org/node/202)) y no pude hacer que funcione.
Ahora tengo el problema que la PC servidor, donde estan conectadas las impresoras, no me reconoce ninguna. Seguro que toqué algo que no debía.
Cuando  abro el menú Sistema-Administración-Impresoras aparece como desconectada del servidor CUPS.

Salu2

---

### Post by leosr on 2009-08-19
Hola. Alguien que pueda ayudarme?

Gracias!

---

### Post by gmunioz on 2009-08-19
Hola leo...:

No seas impaciente, si no obtienes respuestas

es que nadie sabe la misma, ten en cuenta que

somos simples usuarios.

Si el servidor cups no aparece al abrir la

configuración es porque no esta o esta defectuoso

prueba ejecutar:

sudo apt-get install cups

sudo cupsd

Y prueba con la aplicación de configuración

---

### Post by leosr on 2009-08-20
> **gmunioz said:**
> Hola leo...:

No seas impaciente, si no obtienes respuestas

es que nadie sabe la misma, ten en cuenta que

somos simples usuarios.

Si el servidor cups no aparece al abrir la

configuración es porque no esta o esta defectuoso

prueba ejecutar:

sudo apt-get install cups

sudo cupsd

Y prueba con la aplicación de configuración
Gracias por tu respuesta!
Esto es lo que me tira la terminal:
```
leo@Semprom2600-desktop:~$ sudo apt-get install cups
[sudo] password for leo: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
cups ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libvlccore0
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 25 no actualizados.
leo@Semprom2600-desktop:~$ sudo cupsd
cupsd: Child exited with status 1!
leo@Semprom2600-desktop:~$ 

```

Saludos.

---

### Post by josecuervo86 on 2009-08-20
Proba esto:
```
sudo apt-get install --reinstall ssl-cert
```

Si no te anda fijate aca:
 
[http://www.go2linux.org/etc-cups-ssl-server.crt-is-a-bad-symlink-No-such-file-or-directory](http://www.go2linux.org/etc-cups-ssl-server.crt-is-a-bad-symlink-No-such-file-or-directory) 

y aca 

[http://crunchbanglinux.org/forums/post/205/#p205](http://crunchbanglinux.org/forums/post/205/#p205)

---

### Post by gmunioz on 2009-08-21
Hola leo...:

El mensaje:

cupsd: Child exited with status 1!

Significa que al intentar cargar cups algo falló.

Para saber que falló, deberias investigar el el

archivo log de cups

/var/log/cups/error_log

/var/log/cups/access_log

---

### Post by leosr on 2009-08-21
> **gmunioz said:**
> Hola leo...:

El mensaje:

cupsd: Child exited with status 1!

Significa que al intentar cargar cups algo falló.

Para saber que falló, deberias investigar el el

archivo log de cups

/var/log/cups/error_log

/var/log/cups/access_log

Hola. En el archivo /var/log/cups/access_log no hay nada, en el archivo /var/log/cups/error_log está lo siguiente:
```
E [21/Aug/2009:13:53:34 -0300] Bad netmask value 192.168.1.33/38 on line 33.
E [21/Aug/2009:13:53:34 -0300] Unknown Location directive Allow on line 33.
E [21/Aug/2009:13:54:13 -0300] Bad netmask value 192.168.1.33/38 on line 33.
E [21/Aug/2009:13:54:13 -0300] Unknown Location directive Allow on line 33.
E [21/Aug/2009:13:55:44 -0300] Bad netmask value 192.168.1.33/38 on line 33.
E [21/Aug/2009:13:55:44 -0300] Unknown Location directive Allow on line 33.
E [21/Aug/2009:13:56:03 -0300] Bad netmask value 192.168.1.33/38 on line 33.
E [21/Aug/2009:13:56:03 -0300] Unknown Location directive Allow on line 33.
```
La ip de del servidor es 192.168.1.33 que es donde están conectadas las impresoras. Yo estuve metiendo mano al archivo /etc/cups/cupsd.conf. Este es el contenido del archivo:
```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen 192.168.1.33:631
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow 192.168.1.33/38
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow localhost
  Allow 192.168.1.34
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#
```

Saludos.

---

### Post by leosr on 2009-08-21
> **josecuervo86 said:**
> Proba esto:
```
sudo apt-get install --reinstall ssl-cert
```

Si no te anda fijate aca:
 
[http://www.go2linux.org/etc-cups-ssl-server.crt-is-a-bad-symlink-No-such-file-or-directory](http://www.go2linux.org/etc-cups-ssl-server.crt-is-a-bad-symlink-No-such-file-or-directory) 

y aca 

[http://crunchbanglinux.org/forums/post/205/#p205](http://crunchbanglinux.org/forums/post/205/#p205)

Por lo que dice el archivo /var/log/cups/error_log no parece ser el mismo problema. Te parece que pruebe igual?
sudo apt-get install --reinstall ssl-cert lo hice pero no pasó nada raro
Gracias!

---

### Post by josecuervo86 on 2009-08-21
Proba con el primero, no pasa nada.

---

### Post by leosr on 2009-08-21
> **josecuervo86 said:**
> Proba con el primero, no pasa nada.

Probé pero sigue sin andar.

---

### Post by gmunioz on 2009-08-22
Hola leo...:

1- Deberias leer algo sobre redes:

Tu red privada se encuentra dentro del rango

192.168/16 y le corresponde una netmask de

255.255.255.0 que en el formato que usas seria /24

2- Deberias leer los logs:

Cups muy sabiamente te informa:

Bad netmask value 192.168.1.33/38 on line 33.

Por lo tanto deberias cambiar la línea

192.168.1.33/38

Por

192.168.1.33/24

---

### Post by leosr on 2009-09-15
> **gmunioz said:**
> Hola leo...:

1- Deberias leer algo sobre redes:

Tu red privada se encuentra dentro del rango

192.168/16 y le corresponde una netmask de

255.255.255.0 que en el formato que usas seria /24

2- Deberias leer los logs:

Cups muy sabiamente te informa:

Bad netmask value 192.168.1.33/38 on line 33.

Por lo tanto deberias cambiar la línea

192.168.1.33/38

Por

192.168.1.33/24

Hola. Hice el cambio que sugerís y sigue sin andar.

Gracias.

---

### Post by Hei Ku on 2009-09-15
Podes pasar nuevamente los logs, a ver qué dice ahora?

El "no me anda" no nos brinda la informacion necesaria para poder darte una mano. ;)

---

### Post by faruca71 on 2010-04-29
la solución que halle es SIMPLE solo agregue la palabra from despues de allow como muestro abajo.

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow from 192.168.1.33/38
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow from localhost
  Allow from 192.168.1.34
</Location>

---

### Post by chulelinux on 2010-04-30
Leí el post y no se bien pero creo que lo que se señala es que no anda el servicio cups y por ende las impresoras.... o es un problema de red? Si no anda el cups, a mi me pasaba algo parecido, y nunca me reconocía la impresora. Solo logré hacerlo andar cargando en cada sesión manualmente cups hasta que di cuenta a partir de otro post que era un problema del nivel de ejecución donde la nueva versión de upstar tenía un bug que no cargaba el run level al inicio, por lo tanto tampoco cargaba algunos servicios entre ellos cups y así no se reconocían las impresoras.

abrí un terminal, pone runlevel y fijate si te tira unknow. Si es así, volvé a una versión anterior de upstar y seguramente se soluciona el tema.

La solución en mi caso fue esta...

[http://ubuntuforums.org/showthread.php?t=1440454](http://ubuntuforums.org/showthread.php?t=1440454)

Disculpas si entendí mal cual era el problema.
Saludos

---


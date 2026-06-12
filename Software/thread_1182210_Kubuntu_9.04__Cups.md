---
title: "Kubuntu 9.04 | Cups"
date: 2009-06-08
forum: Software
---

### Post by NickCis on 2009-06-08
Hola, tengo problemas con Cups. Antes andaba todo bien, desde que intente compartit la impresora con otra pc se me murio todo :S.

Si intento entrar a la configuracion por pagina ( [https://localhost:631](https://localhost:631) ) me dice que la pagina no existe.

Si intento reiniciar el servicio, la consola no me da ninguna respuesta:
```
newpc@newpc-desktop:~$ sudo /etc/init.d/cups restart
newpc@newpc-desktop:~$ sudo /etc/init.d/cups start
newpc@newpc-desktop:~$
```
( el paquete cupsys se encuentra instalado, pero no existe el servicio cupsys, si no cups).

Actualmente, no me reconoce la impresora que tenia antes instalada, cuando intento imprimir algo solo me da para elegir "Generic Printer".

Adjunto mi /etc/cups/cupsd.conf :
```
#
# "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $"
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
# Listen localhost:631
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
  Allow 10.8.16.1
  Allow 10.8.16.2
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow 10.8.16.1
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
# End of "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $".
#

```

Alguna idea de como puedo solucionar esto?.

Saludos.

---

### Post by Hei Ku on 2009-06-08
Si, tenes que instalar la ultima version de hplip, desde [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Fijate que están las instrucciones para instalarlo en Ubuntu y el script que te baja se encarga de desinstalar la version actual.

---

### Post by NickCis on 2009-06-09
Me tira este error:
```
RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
```

El problema es que si tengo instalando el paquete cupsys y el paquete cups no existe...
Alguna idea? Probe reinstalando el cupsys con sudo apt-get install --reinstall cupsys pero el problema sigue.

Saludos =P

---

### Post by Hei Ku on 2009-06-09
como que no existe el paquete cups? Yo lo tengo aca.
El cupsys es un paquete de transicion, deberías tener el cups.

---

### Post by NickCis on 2009-06-09
No se que problema tenia el cups.
Reinstale el paquete cups (sudo apt-get install --reinstall cups ) y ahora estoy instalando el hplib.

Saludos, y muchas gracias.

---

### Post by NickCis on 2009-06-09
Ese Hplib no me encontro la impresora, la termine instalando desde la pagina de configuracion del Cups ([https://localhost:631](https://localhost:631)), lo instale con el driver HP Deskject 610c - CUPS+GUTENPRINT v5.2.3 (en). Me imprime correctamente. (es una Hp deskject 610c)

Recomiendan que intente instalar el hplib?.

Saludos.

---

### Post by Hei Ku on 2009-06-09
Recordá esta frase: Si anda, NO LO TOQUES!!!!

:lolflag:

---

### Post by NickCis on 2009-06-09
> **Hei Ku said:**
> Recordá esta frase: Si anda, NO LO TOQUES!!!!

:lolflag:

jeje, ok ok :P.

Muchas gracias

---


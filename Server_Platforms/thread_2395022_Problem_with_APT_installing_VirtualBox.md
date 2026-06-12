---
title: "Problem with APT installing VirtualBox"
date: 2018-06-25
forum: Server Platforms
---

### Post by josedb on 2018-06-25
With last updates, iam having two problems. Cannot boot to RAID 0 anymore, and iam stuck with the virtualbox installation.
For booting correctly i have to select the previuous kernel
Iam using Ubuntu Server 16.04 amd64

This is the console output:


```
 sudo apt upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n]
Configurando virtualbox (5.1.34-dfsg-0ubuntu1.16.04.2) ...
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
insserv: warning: script 'K01screen-cleanup' missing LSB tags and overrides
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
initctl: Imposible conectar con Upstar: Failed to connect to socket /com/ubuntu/upstart: Conexión rehusada
insserv: script virtualbox: service vboxdrv already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error al procesar el paquete virtualbox (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Se encontraron errores al procesar:
 virtualbox
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---


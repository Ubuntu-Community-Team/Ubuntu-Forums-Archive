---
title: "I can not uninstall HP-HEALTH"
date: 2010-05-07
forum: Server Platforms
---

### Post by Tres_Iqus on 2010-05-07
and  tried several commands but I could not uninstall the application, I want  to move to the new version of Ubuntu Server amd64 and gives me this  error
my server is HP Proloant ML110 G5
any idea how to fix

# sudo apt-get install update-manager-core 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
update-manager-core ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 14 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 0B/544kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
AVISO: ¡No se han podido autenticar los siguientes paquetes!
  hp-health
¿Instalar estos paquetes sin verificación [s/N]? s
Seleccionando el paquete hp-health previamente no seleccionado.
(Leyendo la base de datos ...  00%
122724 ficheros y directorios instalados actualmente.)
Preparando para reemplazar hp-health 8.2.5.47-11 (usando .../hp-health_8.2.5.47-11_amd64.deb) ...
  Using Proliant Standard
     IPMI based 1XX System Health Monitor
  Using standard Linux IPMI device driver
  Shutting down Proliant Standard
     IPMI based 1XX System Health Monitor (hpasmpld):         [ FAILED ]
  
invoke-rc.d: initscript hp-health, action "stop" failed.
dpkg: aviso: script de `pre-removal' antiguo devolvió un error de salida 1
dpkg - probando el script del nuevo paquete en su lugar...
  Using Proliant Standard
     IPMI based 1XX System Health Monitor
  Using standard Linux IPMI device driver
  Shutting down Proliant Standard
     IPMI based 1XX System Health Monitor (hpasmpld):         [ FAILED ]
  
invoke-rc.d: initscript hp-health, action "stop" failed.
dpkg: error al procesar /var/cache/apt/archives/hp-health_8.2.5.47-11_amd64.deb (--unpack):
 el subproceso script pre-removal nuevo devolvió el código de salida de error 1
  Using Proliant Standard
     IPMI based 1XX System Health Monitor
  Using standard Linux IPMI device driver
  Starting Proliant Standard
     IPMI based 1XX System Health Monitor (hpasmpld):         [ FAILED ]
  
invoke-rc.d: initscript hp-health, action "start" failed.
dpkg: error al reorganizar:
 el subproceso script post-installation instalado devolvió el código de salida de error 61
Se encontraron errores al procesar:
 /var/cache/apt/archives/hp-health_8.2.5.47-11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---


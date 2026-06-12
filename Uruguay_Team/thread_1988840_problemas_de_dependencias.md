---
title: "problemas de dependencias"
date: 2012-05-28
forum: Uruguay Team
---

### Post by optofer on 2012-05-28
Hola estpy intentando intalar 12.04   y tengo programas con problemas de dependencia.
Intente con  dpkg --configure -a  y  tengo esta respuesta del sistema .


  	 	 	 	 	 	   fernanado@fernanado-System-Product-Name:~$ sudo dpkg --configure -a 
 [sudo] password for fernanado:  
 dpkg: problemas de dependencias impiden la configuración de unity: 
  unity depende de libunity-core-5.0-5 (= 5.12-0ubuntu1); sin embargo: 
   La versión de `libunity-core-5.0-5' en el sistema es 5.12-0ubuntu1.1. 
  unity depende de unity-common (= 5.12-0ubuntu1); sin embargo: 
   La versión de `unity-common' en el sistema es 5.12-0ubuntu1.1. 
 dpkg: error al procesar unity (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de libbamf0: 
  libbamf0 depende de bamfdaemon (= 0.2.114-0ubuntu1); sin embargo: 
   La versión de `bamfdaemon' en el sistema es 0.2.118-0ubuntu0.1. 
 dpkg: error al procesar libbamf0 (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de libbamf3-0: 
  libbamf3-0 depende de bamfdaemon (= 0.2.114-0ubuntu1); sin embargo: 
   La versión de `bamfdaemon' en el sistema es 0.2.118-0ubuntu0.1. 
 dpkg: error al procesar libbamf3-0 (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de vlc-plugin-pulse: 
  vlc-plugin-pulse depende de vlc-nox (= 2.0.1-4); sin embargo: 
   La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1. 
 dpkg: error al procesar vlc-plugin-pulse (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de vlc-nox: 
  vlc-nox depende de libmatroska4; sin embargo: 
   El paquete `libmatroska4' no está instalado. 
  vlc-nox depende de libvlccore4 (>= 1.1.0); sin embargo: 
   El paquete `libvlccore4' no está instalado. 
  vlc-nox depende de libx264-116; sin embargo: 
   El paquete `libx264-116' no está instalado. 
 vlc-data (2.0.1-4) rompe vlc-nox (<< 2.0.1-3) y es instalado. 
   La versión de `vlc-nox' que se desconfigurará es 1.1.12-2~oneiric1. 
 dpkg: error al procesar vlc-nox (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de syslinux: 
  syslinux depende de syslinux-common (= 2:4.04+dfsg-1ubuntu1); sin embargo: 
   La versión de `syslinux-common' en el sistema es 2:4.05+dfsg-2. 
 syslinux-common (2:4.05+dfsg-2) rompe syslinux (<< 2:4.05+dfsg-2) y es instalado. 
   La versión de `syslinux' que se desconfigurará es 2:4.04+dfsg-1ubuntu1. 
 dpkg: error al procesar syslinux (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de vlc: 
  vlc depende de vlc-nox (= 2.0.1-4); sin embargo: 
   La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1. 
 dpkg: error al procesar vlc (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de vlc-plugin-notify: 
  vlc-plugin-notify depende de vlc-nox (= 2.0.1-4); sin embargo: 
   La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1. 
 dpkg: error al procesar vlc-plugin-notify (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de usb-creator-common: 
  usb-creator-common depende de syslinux; sin embargo: 
  El paquete `syslinux' no está configurado todavía. 
 dpkg: error al procesar usb-creator-common (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de indicator-appmenu: 
  indicator-appmenu depende de libbamf3-0 (>= 0.2.110); sin embargo: 
  El paquete `libbamf3-0' no está configurado todavía. 
 dpkg: error al procesar indicator-appmenu (--configure): 
  problemas de dependencias - se deja sin configurar 
 dpkg: problemas de dependencias impiden la configuración de usb-creator-gtk: 
  usb-creator-gtk depende de usb-creator-common (= 0.2.38); sin embargo: 
  El paquete `usb-creator-common' no está configurado todavía. 
 dpkg: error al procesar usb-creator-gtk (--configure): 
  problemas de dependencias - se deja sin configurar 
 Se encontraron errores al procesar: 
  unity 
  libbamf0 
  libbamf3-0 
  vlc-plugin-pulse 
  vlc-nox 
  syslinux 
  vlc 
  vlc-plugin-notify 
  usb-creator-common 
  indicator-appmenu 
  usb-creator-gtk 
 fernanado@fernanado-System-Product-Name:~$  
  

perdon lo  extenso de esto pero como lo soluciono

---

### Post by optofer on 2012-05-28
haciendo aptitude  dist-upgrade tengo esto  ?como reparo el sistema 


fernanado@fernanado-System-Product-Name:~$ sudo aptitude dist-upgrade
Se actualizarán los siguientes paquetes:         
  syslinux vlc-nox 
Se configurarán los siguientes paquetes que están ahora parcialmente instalados:
  usb-creator-common usb-creator-gtk vlc vlc-plugin-notify vlc-plugin-pulse 
2 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0 B/2.829 kB de archivos. Después de desempaquetar se usarán 247 kB.
¿Quiere continuar? [Y/n/?] y
dpkg: problemas de dependencias impiden la configuración de syslinux:
 syslinux depende de syslinux-common (= 2:4.04+dfsg-1ubuntu1); sin embargo:
  La versión de `syslinux-common' en el sistema es 2:4.05+dfsg-2.
syslinux-common (2:4.05+dfsg-2) rompe syslinux (<< 2:4.05+dfsg-2) y es instalado.
  La versión de `syslinux' que se desconfigurará es 2:4.04+dfsg-1ubuntu1.
dpkg: error al procesar syslinux (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de usb-creator-common:
 usb-creator-common depende de syslinux; sin embargo:
 El paquete `syslinux' no está configurado todavía.
dpkg: error al procesar usb-creator-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de usb-creator-gtk:
 usb-creator-gtk depende de usb-creator-common (= 0.2.38); sin embargo:
 El paquete `usb-creator-common' no está configurado todavía.
dpkg: error al procesar usb-creator-gtk (--configure):
 problemas de dependencias - se deja sin configurarNo se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                            No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                     No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»

dpkg: problemas de dependencias impiden la configuración de vlc-nox:
 vlc-nox depende de libmatroska4; sin embargo:
  El paquete `libmatroska4' no está instalado.
 vlc-nox depende de libvlccore4 (>= 1.1.0); sin embargo:
  El paquete `libvlccore4' no está instalado.
 vlc-nox depende de libx264-116; sin embargo:
  El paquete `libx264-116' no está instalado.
vlc-data (2.0.1-4) rompe vlc-nox (<< 2.0.1-3) y es instalado.
  La versión de `vlc-nox' que se desconfigurará es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc-nox (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de vlc-plugin-notify:
 vlc-plugin-notify depende de vlc-nox (= 2.0.1-4); sin embargo:
  La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc-plugin-notify (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de vlc:
 vlc depende de vlc-nox (= 2No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                     No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                              No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                       No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                .0.1-4); sin embargo:
  La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de vlc-plugin-pulse:
 vlc-plugin-pulse depende de vlc-nox (= 2.0.1-4); sin embargo:
  La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc-plugin-pulse (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 syslinux
 usb-creator-common
 usb-creator-gtk
 vlc-nox
 vlc-plugin-notify
 vlc
 vlc-plugin-pulse
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
dpkg: problemas de dependencias impiden la configuración de vlc-plugin-pulse:
 vlc-plugin-pulse depende de vlc-nox (= 2.0.1-4); sin embargo:
  La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc-plugin-pulse (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de vlc-nox:
 vlc-nox depende de libmatroska4; sin embargo:
  El paquete `libmatroska4' no está instalado.
 vlc-nox depende de libvlccore4 (>= 1.1.0); sin embargo:
  El paquete `libvlccore4' no está instalado.
 vlc-nox depende de libx264-116; sin embargo:
  El paquete `libx264-116' no está instalado.
vlc-data (2.0.1-4) rompe vlc-nox (<< 2.0.1-3) y es instalado.
  La versión de `vlc-nox' que se desconfigurará es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc-nox (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de syslinux:
 syslinux depende de syslinux-common (= 2:4.04+dfsg-1ubuntu1); sin embargo:
  La versión de `syslinux-common' en el sistema es 2:4.05+dfsg-2.
syslinux-common (2:4.05+dfsg-2) rompe syslinux (<< 2:4.05+dfsg-2) y es instalado.
  La versión de `syslinux' que se desconfigurará es 2:4.04+dfsg-1ubuntu1.
dpkg: error al procesar syslinux (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de vlc:
 vlc depende de vlc-nox (= 2.0.1-4); sin embargo:
  La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de vlc-plugin-notify:
 vlc-plugin-notify depende de vlc-nox (= 2.0.1-4); sin embargo:
  La versión de `vlc-nox' en el sistema es 1.1.12-2~oneiric1.
dpkg: error al procesar vlc-plugin-notify (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de usb-creator-common:
 usb-creator-common depende de syslinux; sin embargo:
 El paquete `syslinux' no está configurado todavía.
dpkg: error al procesar usb-creator-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de usb-creator-gtk:
 usb-creator-gtk depende de usb-creator-common (= 0.2.38); sin embargo:
 El paquete `usb-creator-common' no está configurado todavía.
dpkg: error al procesar usb-creator-gtk (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 vlc-plugin-pulse
 vlc-nox
 syslinux
 vlc
 vlc-plugin-notify
 usb-creator-common
 usb-creator-gtk
                                                 
fernanado@fernanado-System-Product-Name:~$

---

### Post by pablorubianes on 2012-05-29
hola una consulta, vi abajo de tu nick que tenes xubuntu 8.04, estas intentando actualizar a la 12.04 desde ahi? si es asi, por eso te revienta, y te recominedo que instales de 0.
Sino, contame un poco mas como es que estas haciendo.

Saludos!

---

### Post by optofer on 2012-05-29
Hola Pablo mira no eso es la versión que tenia cuando me registre en el foro ahora actualice desde 11.10.
Si bien tenia un problemita con 11.10 ,que se cerraba la sección  inesperadamente, en medio de una actualización  igual se me cerraba, una tranza.
La idea de actualizar fue para tratar de corregir ese problema. 
El tema es que no consigo una herramienta que resuelva los problemas de dependencias y por orgullo no quiero borrar todo y arrancar de cero , el sistema funciona es solo problemas de dependencias  que no me molestan en el funcionamiento de la maquina

---


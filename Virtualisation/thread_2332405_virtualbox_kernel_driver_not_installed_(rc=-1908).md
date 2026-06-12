---
title: "virtualbox kernel driver not installed (rc=-1908)"
date: 2016-07-31
forum: Virtualisation
---

### Post by gari2 on 2016-07-31
Hi,

I've been using VBox and I didn't have any problems until yesterday but suddenly I found myself with this:

[ATTACH=CONFIG]270475[/ATTACH]

I had the same problem but I solved it. However, now I can't.

Thanks for your help.

---

### Post by ajgreeny on 2016-07-31
What happens when you run the suggested command ```
sudo /etc/init.d/vboxdrv setup
```
Which version of Ubuntu are you using as host?  I am not sure if 16.04 which is using systemd instead of upstart means that the command no longer works as I have not yet moved to 16.04 from my 14.04 host.

Also which version of VBox are you using?  I upgraded to 5.1 a couple of weeks ago having used 5.0 for some time but I had to quickly downgrade to 5.0.26 almost immediately as 5.1 gave me no end of problems and 5.0 was running guests perfectly for me, and is again following the downgrade.

---

### Post by gari2 on 2016-07-31
I'm using Ubuntu 14.04 and VirtualBox 5.1. When I run that command I see this:

```
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)
```

I downgraded to 5.0.26

---

### Post by MAFoElffen on 2016-08-01
The new vbox module sometimes has a problem installing that new vbox kernel module... if there are any pieces of the old module left on the system. 

Try this:
```

sudo apt-get remove --purge virtualBox-dkms
sudo apt-get install virtualbox-dkms

```

---

### Post by gari2 on 2016-08-02
Yes, I tried that but there is a warning about UEFI Secure Boot and I don't know if I do have to disable it. Moreover, modprobe doesn't work.

```
Desinstalando virtualbox-5.0 (5.0.26-108824~Ubuntu~trusty) ...
Procesando disparadores para gnome-menus (3.10.1-0ubuntu2) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu1) ...
Procesando disparadores para bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para mime-support (3.54ubuntu1.1) ...
Procesando disparadores para shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Procesando disparadores para hicolor-icon-theme (0.13-1) ...
Seleccionando el paquete virtualbox-dkms previamente no seleccionado.
(Leyendo la base de datos ... 901180 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../virtualbox-dkms_4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1_all.deb ...
Desempaquetando virtualbox-dkms (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Seleccionando el paquete virtualbox previamente no seleccionado.
Preparando para desempaquetar .../virtualbox_4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1_amd64.deb ...
Desempaquetando virtualbox (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Seleccionando el paquete virtualbox-qt previamente no seleccionado.
Preparando para desempaquetar .../virtualbox-qt_4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1_amd64.deb ...
Desempaquetando virtualbox-qt (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Procesando disparadores para man-db (2.6.7.1-1ubuntu1) ...
Procesando disparadores para ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Procesando disparadores para hicolor-icon-theme (0.13-1) ...
Procesando disparadores para gnome-menus (3.10.1-0ubuntu2) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu1) ...
Procesando disparadores para bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para mime-support (3.54ubuntu1.1) ...
Procesando disparadores para shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Configurando virtualbox-dkms (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Loading new virtualbox-4.3.36 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-65-generic
Building initial module for 3.19.0-65-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-65-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-65-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-65-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-65-generic/updates/dkms/

depmod....

DKMS: install completed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * modprobe vboxdrv failed. Please use 'dmesg' to find out why
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Configurando virtualbox (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * modprobe vboxdrv failed. Please use 'dmesg' to find out why
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Configurando virtualbox-qt (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Procesando disparadores para shim-signed (1.18~14.04.1+0.8-0ubuntu2) ...
```

---

### Post by MAFoElffen on 2016-08-03
You said you were running v5.1... Yet your error says that theere is pieces of 4.3.36 left conflicting with your new install, therefore cannot load your newer module.
```

invoke-rc.d: initscript virtualbox, action "restart" failed.
Configurando virtualbox (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules

```
Please remove and purge the old version of VirtualBox and install fresh. That way it gets rid of those offending old, left-over pieces.

---

### Post by gari2 on 2016-08-04
I did that but an error appeared again.

```
gari@gari-X550LA:~$ sudo apt-get remove --purge virtualBox-dkms
[sudo] password for gari: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic virtualbox virtualbox-qt virtualbox-source
Use 'apt-get autoremove' to remove them.
Se instalarán los siguientes paquetes extras:
  virtualbox-source
Los siguientes paquetes se ELIMINARÁN:
  virtualbox-dkms*
Se instalarán los siguientes paquetes NUEVOS:
  virtualbox-source
0 actualizados, 1 se instalarán, 1 para eliminar y 0 no actualizados.
Se necesita descargar 0 B/674 kB de archivos.
Se liberarán 3.768 kB después de esta operación.
¿Desea continuar? [S/n] s
Seleccionando el paquete virtualbox-source previamente no seleccionado.
(Leyendo la base de datos ... 902963 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../virtualbox-source_4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1_all.deb ...
Desempaquetando virtualbox-source (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
dpkg: virtualbox-dkms: problemas de dependencias, pero se desinstalará de todas formas
 tal y como se solicitó:
 virtualbox depende de virtualbox-dkms (>= 4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) | virtualbox-source (>= 4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) | virtualbox-modules; sin embargo:
  El paquete `virtualbox-dkms' va a ser desinstalado.
 El paquete `virtualbox-source' no está configurado todavía.
  El paquete `virtualbox-modules' no está instalado.

(Leyendo la base de datos ... 902967 ficheros o directorios instalados actualmente.)
Desinstalando virtualbox-dkms (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.36
Kernel:  3.19.0-65-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.3.36
completely from the DKMS tree.
------------------------------
Done.
Configurando virtualbox-source (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
gari@gari-X550LA:~$ sudo apt-get remove virtualbox
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic virtualbox-source
Use 'apt-get autoremove' to remove them.
Los siguientes paquetes se ELIMINARÁN:
  virtualbox virtualbox-qt
0 actualizados, 0 se instalarán, 2 para eliminar y 0 no actualizados.
Se liberarán 79,2 MB después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 902695 ficheros o directorios instalados actualmente.)
Desinstalando virtualbox-qt (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Desinstalando virtualbox (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Procesando disparadores para man-db (2.6.7.1-1ubuntu1) ...
Procesando disparadores para shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Procesando disparadores para gnome-menus (3.10.1-0ubuntu2) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu1) ...
Procesando disparadores para bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para mime-support (3.54ubuntu1.1) ...
Procesando disparadores para hicolor-icon-theme (0.13-1) ...
gari@gari-X550LA:~$ sudo apt-get remove --purge virtualbox
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic virtualbox-source
Use 'apt-get autoremove' to remove them.
Los siguientes paquetes se ELIMINARÁN:
  virtualbox*
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 902407 ficheros o directorios instalados actualmente.)
Desinstalando virtualbox (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
Purgando ficheros de configuración de virtualbox (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
gari@gari-X550LA:~$ sudo apt-get remove virtualbox*
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando «virtualbox-modules» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-3.0» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-3.1» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-3.2» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-modules» para la expresión regular «virtualbox*»
Nota, seleccionando «unity-scope-virtualbox» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-2.0» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-2.1» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-2.2» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-source» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-dkms» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-dbg» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-dkms» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-x11» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-ose» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-additions-iso» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-qt» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-additions» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-5.0» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-5.1» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-4.0» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-4.1» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-4.2» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-4.3» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-source» para la expresión regular «virtualbox*»
Nota, seleccionando «virtualbox-guest-utils» para la expresión regular «virtualbox*»
Package 'virtualbox-2.0' is not installed, so not removed
Package 'virtualbox-2.1' is not installed, so not removed
Package 'virtualbox-2.2' is not installed, so not removed
Package 'virtualbox-3.0' is not installed, so not removed
Package 'virtualbox-3.1' is not installed, so not removed
Package 'virtualbox-3.2' is not installed, so not removed
Package 'virtualbox-4.0' is not installed, so not removed
Package 'virtualbox-4.1' is not installed, so not removed
Package 'virtualbox-guest-additions' is not installed, so not removed
Package 'virtualbox-modules' is not installed, so not removed
Package 'virtualbox-ose' is not installed, so not removed
Package 'unity-scope-virtualbox' is not installed, so not removed
Package 'virtualbox' is not installed, so not removed
Package 'virtualbox-dbg' is not installed, so not removed
Package 'virtualbox-dkms' is not installed, so not removed
Package 'virtualbox-guest-additions-iso' is not installed, so not removed
Package 'virtualbox-guest-dkms' is not installed, so not removed
Package 'virtualbox-guest-source' is not installed, so not removed
Package 'virtualbox-guest-utils' is not installed, so not removed
Package 'virtualbox-guest-x11' is not installed, so not removed
Package 'virtualbox-qt' is not installed, so not removed
Package 'virtualbox-4.2' is not installed, so not removed
Package 'virtualbox-4.3' is not installed, so not removed
Package 'virtualbox-5.0' is not installed, so not removed
Package 'virtualbox-5.1' is not installed, so not removed
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic
Use 'apt-get autoremove' to remove them.
Los siguientes paquetes se ELIMINARÁN:
  virtualbox-source
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 782 kB después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 902405 ficheros o directorios instalados actualmente.)
Desinstalando virtualbox-source (4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1) ...
gari@gari-X550LA:~$ nano /etc/apt/sources.list
gari@gari-X550LA:~$ sudo apt-key add oracle_vbox_2016.asc
gpg: no se puede abrir «oracle_vbox_2016.asc»: No existe el archivo o el directorio
gari@gari-X550LA:~$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -0- | sudo apt-key add -
wget: opción incorrecta -- «0»
wget: opción incorrecta -- «-»
Uso: wget [OPCIÓN]... [URL]...

Intente «wget --help» para tener más opciones.
gpg: no se han encontrado datos OpenPGP válidos
gari@gari-X550LA:~$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
OK
gari@gari-X550LA:~$ wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
OK
gari@gari-X550LA:~$ sudo apt-get update
Des:1 http://security.ubuntu.com trusty-security InRelease [65,9 kB]
Des:2 http://download.virtualbox.org trusty InRelease [7.158 B]                
Ign http://es.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Obj http://repository.spotify.com stable InRelease                             
Obj http://ppa.launchpad.net trusty InRelease                                  
Des:3 http://www.geogebra.net stable InRelease [8.862 B]                       
Des:4 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Des:5 http://es.archive.ubuntu.com trusty-updates InRelease [65,9 kB]          
Des:6 http://download.virtualbox.org trusty/contrib amd64 Packages [1.887 B]   
Obj http://ppa.launchpad.net trusty InRelease                                  
Obj http://repository.spotify.com stable/non-free amd64 Packages               
Des:7 http://deb.torproject.org jessie InRelease [4.229 B]                     
Des:8 http://www.geogebra.net stable/main amd64 Packages [3.716 B]             
Obj http://extras.ubuntu.com trusty Release                                    
Obj http://ppa.launchpad.net trusty/main amd64 Packages                        
Des:9 http://download.virtualbox.org trusty/contrib i386 Packages [1.914 B]    
Obj http://repository.spotify.com stable/non-free i386 Packages                
Des:10 http://deb.torproject.org jessie/main Sources [2.290 B]                 
Des:11 http://security.ubuntu.com trusty-security/main Sources [118 kB]        
Des:12 http://www.geogebra.net stable/main i386 Packages [3.720 B]             
Obj http://extras.ubuntu.com trusty/main Sources                               
Obj http://ppa.launchpad.net trusty/main i386 Packages                         
Des:13 http://deb.torproject.org jessie/main amd64 Packages [3.390 B]          
Obj http://ppa.launchpad.net trusty/main Translation-en                        
Obj http://extras.ubuntu.com trusty/main amd64 Packages                        
Des:14 http://deb.torproject.org jessie/main i386 Packages [3.389 B]           
Obj http://es.archive.ubuntu.com trusty-backports InRelease                    
Obj http://extras.ubuntu.com trusty/main i386 Packages                         
Obj http://ppa.launchpad.net trusty/main amd64 Packages                        
Obj http://es.archive.ubuntu.com trusty Release.gpg                            
Des:15 http://security.ubuntu.com trusty-security/restricted Sources [4.064 B] 
Obj http://ppa.launchpad.net trusty/main i386 Packages                         
Des:16 http://es.archive.ubuntu.com trusty-updates/main Sources [379 kB]       
Obj http://ppa.launchpad.net trusty/main Translation-en                        
Des:17 http://security.ubuntu.com trusty-security/universe Sources [38,0 kB]   
Des:18 http://security.ubuntu.com trusty-security/multiverse Sources [2.760 B] 
Des:19 http://security.ubuntu.com trusty-security/main amd64 Packages [510 kB] 
Des:20 http://es.archive.ubuntu.com trusty-updates/restricted Sources [5.360 B]
Ign http://download.virtualbox.org trusty/contrib Translation-es_ES            
Ign http://repository.spotify.com stable/non-free Translation-es_ES            
Des:21 http://es.archive.ubuntu.com trusty-updates/universe Sources [160 kB]   
Ign http://download.virtualbox.org trusty/contrib Translation-es               
Ign http://repository.spotify.com stable/non-free Translation-es               
Ign http://download.virtualbox.org trusty/contrib Translation-en               
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign http://extras.ubuntu.com trusty/main Translation-es_ES                     
Des:22 http://es.archive.ubuntu.com trusty-updates/multiverse Sources [7.137 B]
Des:23 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13,0 kB]
Ign http://extras.ubuntu.com trusty/main Translation-es                        
Des:24 http://es.archive.ubuntu.com trusty-updates/main amd64 Packages [876 kB]
Ign http://www.geogebra.net stable/main Translation-es_ES                      
Des:25 http://security.ubuntu.com trusty-security/universe amd64 Packages [130 kB]
Ign http://deb.torproject.org jessie/main Translation-es_ES                    
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://www.geogebra.net stable/main Translation-es                         
Ign http://deb.torproject.org jessie/main Translation-es                       
Ign http://www.geogebra.net stable/main Translation-en                         
Des:26 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4.990 B]
Ign http://deb.torproject.org jessie/main Translation-en                       
Des:27 http://security.ubuntu.com trusty-security/main i386 Packages [477 kB]  
Des:28 http://security.ubuntu.com trusty-security/restricted i386 Packages [12,7 kB]
Des:29 http://es.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15,9 kB]
Des:30 http://security.ubuntu.com trusty-security/universe i386 Packages [131 kB]
Des:31 http://es.archive.ubuntu.com trusty-updates/universe amd64 Packages [367 kB]
Des:32 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5.178 B]
Des:33 http://security.ubuntu.com trusty-security/main Translation-en [282 kB] 
Des:34 http://es.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [14,9 kB]
Des:35 http://es.archive.ubuntu.com trusty-updates/main i386 Packages [837 kB]
Des:36 http://security.ubuntu.com trusty-security/multiverse Translation-en [2.570 B]
Des:37 http://security.ubuntu.com trusty-security/restricted Translation-en [3.206 B]
Des:38 http://security.ubuntu.com trusty-security/universe Translation-en [77,2 kB]
Des:39 http://es.archive.ubuntu.com trusty-updates/restricted i386 Packages [15,6 kB]
Des:40 http://es.archive.ubuntu.com trusty-updates/universe i386 Packages [368 kB]
Des:41 http://es.archive.ubuntu.com trusty-updates/multiverse i386 Packages [15,3 kB]
Des:42 http://es.archive.ubuntu.com trusty-updates/main Translation-en [421 kB]
Des:43 http://es.archive.ubuntu.com trusty-updates/multiverse Translation-en [7.661 B]
Des:44 http://es.archive.ubuntu.com trusty-updates/restricted Translation-en [3.699 B]
Des:45 http://es.archive.ubuntu.com trusty-updates/universe Translation-en [193 kB]
Obj http://es.archive.ubuntu.com trusty-backports/main Sources                 
Obj http://es.archive.ubuntu.com trusty-backports/restricted Sources           
Obj http://es.archive.ubuntu.com trusty-backports/universe Sources             
Obj http://es.archive.ubuntu.com trusty-backports/multiverse Sources           
Obj http://es.archive.ubuntu.com trusty-backports/main amd64 Packages          
Obj http://es.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Obj http://es.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Obj http://es.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Obj http://es.archive.ubuntu.com trusty-backports/main i386 Packages           
Obj http://es.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Obj http://es.archive.ubuntu.com trusty-backports/universe i386 Packages       
Obj http://es.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Obj http://es.archive.ubuntu.com trusty-backports/main Translation-en          
Obj http://es.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Obj http://es.archive.ubuntu.com trusty-backports/restricted Translation-en    
Obj http://es.archive.ubuntu.com trusty-backports/universe Translation-en      
Obj http://es.archive.ubuntu.com trusty Release                                
Obj http://es.archive.ubuntu.com trusty/main Sources                           
Obj http://es.archive.ubuntu.com trusty/restricted Sources                     
Obj http://es.archive.ubuntu.com trusty/universe Sources                       
Obj http://es.archive.ubuntu.com trusty/multiverse Sources                     
Obj http://es.archive.ubuntu.com trusty/main amd64 Packages                    
Obj http://es.archive.ubuntu.com trusty/restricted amd64 Packages              
Obj http://es.archive.ubuntu.com trusty/universe amd64 Packages                
Obj http://es.archive.ubuntu.com trusty/multiverse amd64 Packages              
Obj http://es.archive.ubuntu.com trusty/main i386 Packages                     
Obj http://es.archive.ubuntu.com trusty/restricted i386 Packages               
Obj http://es.archive.ubuntu.com trusty/universe i386 Packages                 
Obj http://es.archive.ubuntu.com trusty/multiverse i386 Packages               
Obj http://es.archive.ubuntu.com trusty/main Translation-es                    
Obj http://es.archive.ubuntu.com trusty/main Translation-en                    
Obj http://es.archive.ubuntu.com trusty/multiverse Translation-es              
Obj http://es.archive.ubuntu.com trusty/multiverse Translation-en              
Obj http://es.archive.ubuntu.com trusty/restricted Translation-es              
Obj http://es.archive.ubuntu.com trusty/restricted Translation-en              
Obj http://es.archive.ubuntu.com trusty/universe Translation-es                
Obj http://es.archive.ubuntu.com trusty/universe Translation-en                
Ign http://es.archive.ubuntu.com trusty/main Translation-es_ES                 
Ign http://es.archive.ubuntu.com trusty/multiverse Translation-es_ES           
Ign http://es.archive.ubuntu.com trusty/restricted Translation-es_ES           
Ign http://es.archive.ubuntu.com trusty/universe Translation-es_ES             
Descargados 5.670 kB en 14seg. (382 kB/s)                                      
Leyendo lista de paquetes... Hecho
gari@gari-X550LA:~$ sudo apt-get install virtualbox-5.1
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  libsdl-ttf2.0-0
Se instalarán los siguientes paquetes NUEVOS:
  libsdl-ttf2.0-0 virtualbox-5.1
0 actualizados, 2 se instalarán, 0 para eliminar y 9 no actualizados.
Necesito descargar 71,6 MB de archivos.
Se utilizarán 174 MB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Des:1 http://es.archive.ubuntu.com/ubuntu/ trusty/universe libsdl-ttf2.0-0 amd64 2.0.11-3 [15,0 kB]
Des:2 http://download.virtualbox.org/virtualbox/debian/ trusty/contrib virtualbox-5.1 amd64 5.1.2-108956~Ubuntu~trusty [71,6 MB]
Descargados 71,6 MB en 1min. 14seg. (960 kB/s)                                 
Preconfigurando paquetes ...
Seleccionando el paquete libsdl-ttf2.0-0:amd64 previamente no seleccionado.
(Leyendo la base de datos ... 902401 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../libsdl-ttf2.0-0_2.0.11-3_amd64.deb ...
Desempaquetando libsdl-ttf2.0-0:amd64 (2.0.11-3) ...
Seleccionando el paquete virtualbox-5.1 previamente no seleccionado.
Preparando para desempaquetar .../virtualbox-5.1_5.1.2-108956~Ubuntu~trusty_amd64.deb ...
Desempaquetando virtualbox-5.1 (5.1.2-108956~Ubuntu~trusty) ...
Procesando disparadores para ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Procesando disparadores para hicolor-icon-theme (0.13-1) ...
Procesando disparadores para shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Procesando disparadores para gnome-menus (3.10.1-0ubuntu2) ...
Procesando disparadores para desktop-file-utils (0.22-1ubuntu1) ...
Procesando disparadores para bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Procesando disparadores para mime-support (3.54ubuntu1.1) ...
Configurando libsdl-ttf2.0-0:amd64 (2.0.11-3) ...
Configurando virtualbox-5.1 (5.1.2-108956~Ubuntu~trusty) ...
Añadiendo el grupo `vboxusers' (GID 126) ...
Hecho.
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.
Procesando disparadores para libc-bin (2.19-0ubuntu6.9) ...
gari@gari-X550LA:~$ sudo apt-get install dkms
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
dkms ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 9 no actualizados.
gari@gari-X550LA:~$ 
```

---

### Post by MAFoElffen on 2016-08-05
Note to others, this is just a work-around for the current state of the VirtualBox 5.1 package, as it is from upstream. Not to be used for other versions, and might change when upstream changes it's code to correct it's problem. There is a current problem where the install script has a problem installing virtualbox-dms while selinux active and enable.

@OP:

In a Terminal Session, do
```

sudo selinux-config-enforcing disabled
cat /etc/selinux/config

```
The output of the second command should be similar to the following. Verify that the red has been changed to that. If not, then manually edit the /etc/selinux/config file to match. (set SELINUX=disabled). This file controls the state of SELinux on the system. 
```

# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
[COLOR=#ff0000]SELINUX=disabled[/COLOR]
# SELINUXTYPE= can take one of these three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected. 
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted

```
You have to reboot for it to take that change. Then do the recommended 
```

sudo /sbin/vboxconfig

```
If it installs successfully,then 
```

sudo selinux-config-enforcing enforcing
cat /etc/selinux/config

```
Verify that it has been changed back. Manually edit it if needed. Reboot to pick up the change.

---

### Post by gari2 on 2016-08-05
So, do I have to install 5.1? Because as they told me to try downgrading I have another version

---

### Post by MAFoElffen on 2016-08-05
You could try to install 5.1 with that fix, or downgrade to 5.0.28... With that solution to installing, that should get you installed with 5.1. I know ajgreeny had problems with 5.1. That was noted by him, that he had various problems with that version so he downgraded back to 5.0.28 and has been fine with that version.

I can't say that this fix will solve all the problems that he had (I could check with him to see just what problems he had...) Not to say Oracle has not work on some of those upstream problems yet... With evry release, you are bound to have some things to work out. But then again, It  didn't seem like 5.0.28 was out very long, before they released 5.1, so there must have been changes that they did between those, that caused them to rush 5.1 out to correct... Just thinking out loud.

Basically, it all comes down to: "It's your choice. Pick what is best for you."

---

### Post by gari2 on 2016-08-08
What happens with this?

```
root@gari-X550LA:/home/gari# sudo selinux-config-enforcing disabled
sudo: selinux-config-enforcing: command not found
```

Thanks!

---

### Post by MAFoElffen on 2016-08-09
That, if present would have automatically change the option in the selinux conf file, As noted, as an laternative, manually change the option in the conf file to relflect what I posted: Change the enforcing option to disabled.

---

### Post by gari2 on 2016-08-12
The directory doesn't exist.:???:

```
root@gari-X550LA:/home/gari# cat /etc/selinux/config
cat: /etc/selinux/config: No existe el archivo o el directorio
```

Sorry, I couldn't answer before

Thanks!

---

### Post by anandkrishnan411 on 2016-08-14
I think this problem started for me when [FONT=courier new]virtualbox-dkms[/FONT] was updated as part of a bunch of other package updates.
I hadn't noticed that my Virtualbox wasn't working since I rarely need to boot up my Windows VM.

First I tried [post=13525495]**MAFoElffen**'s solution[/post]...which didn't quite work, but was on the right track.

Here is what I did to fix it.

I remembered that during the [FONT=courier new]virtualbox-dkms[/FONT] update I was prompted to create some kind of password to "**Disable Secure Boot**" which struck me as odd. I was wondering how Ubuntu would be able to affect a setting in UEFI like that :confused:
I took a cue from [SIZE=2]this thread: [Secure boot questions/problems]("https://ubuntuforums.org/showthread.php?t=2333372").

And after a little digging online I was lead to [How to Disable or Enable Secure Boot for ASUS Motherboard]("http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility") (since that is my motherboard manufacturer).

I pretty much followed that article, except I just left the 'OS Type' as-is, "Windows UEFI mode", since Ubuntu had been booting just fine for me with that setting.

After disabling secure boot, I then reinstalled the [/SIZE][SIZE=2][FONT=courier new]virtualbox-dkms[/FONT] package and noticed that the kernel driver was installed successfully.
[/SIZE]
```
[SIZE=2]
$ lsmod | grep vbox
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27830  0 
vboxdrv               414452  3 vboxnetadp,vboxnetflt,vboxpci
[/SIZE]
```

---

### Post by MAFoElffen on 2016-08-14
Congrats! So this is good for you now? (As in Solved?)

---

### Post by anandkrishnan411 on 2016-08-14
Yes, that's right. It is solved for me. :)

---

### Post by MAFoElffen on 2016-08-15
Great. If you sould please revisit this thread > Select the link in the upper right of the page marked as "Thread Tools" > Select "Mark thread as Solved"

This helps others (later), to help them find solutions to their own similar problems.

---

### Post by anandkrishnan411 on 2016-08-15
Yes, I understand. I am new here. 
Under "Thread Tools", I only have options: "Show Printable Version", "Email this Page...", and "Unsubscribe from this Thread".
Please let me know if there is something else I need to do in order to see the option, "Mark thread as Solved"... Or maybe someone else can mark it.

---

### Post by MAFoElffen on 2016-08-17
If you were logged in while looking at that menu, the last line should be that option... 2 lines under the "subscribe/unsubscribe" line

---

### Post by anandkrishnan411 on 2016-08-18
As a logged in user, I still only see options: "Show Printable Version", "Email this Page...", and "Unsubscribe from this Thread".
Is there some other setting somewhere that will enable me to "Mark Thread as Solved" ?

---

### Post by &amp;KyT$0P# on 2016-08-18
You have to be the thread starter to be able to mark the thread solved.

---

### Post by gari2 on 2016-08-19
Hi!

First of all, sorry for not answering but I hadn't access to the Internet.

I knew the Secure Boot was one of the problems I had and I tried to disable it following those instructions. However, my BIOS is Aptio Setup Utility whilst my laptop is an ASUS and I don't know how to disable it.

Thank you for all!

---

### Post by anandkrishnan411 on 2016-09-04
gari2, 

Not sure if you've already found this, but here is a youtube clip of an [ASUS BIOS Secure Boot Disable]("https://www.youtube.com/watch?v=s4Un_QpDoRQ") that may help, since it is specifically for the ASUS Aptio Setup Utility.
Here is a separate post on [How to Solve Problems with Aptio Setup Utility]("http://www.tomsguide.com/answers/id-1854127/solve-problem-aptio-setup-utility.html")  at tomsguide.

Also I found this interesting [Secure Boot Overview]("https://technet.microsoft.com/en-us/library/hh824987.aspx") on Microsoft Technet including a general doc on [Disabling Secure Boot]("https://technet.microsoft.com/en-us/library/dn481258.aspx") (yes, it's laced with a bit of FUD, but useful nonetheless.)

---

### Post by gari2 on 2016-09-09
Hi!

I disabled Secure Boot and it is already working! I had installed VMWare and there was an error about the monitor, Therefore I can mark this thread as solves.

Thank you all!

---


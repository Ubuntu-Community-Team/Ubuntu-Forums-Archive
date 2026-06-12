---
title: "problemas dpkg xubuntu 8.10"
date: 2009-05-25
forum: Software
---

### Post by andy_91 on 2009-05-25
```
andy@andy-desktop:~$ sudo dpkg --configure -a
Configurando dash (0.5.4-9ubuntu1.1) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar dash (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando linux-headers-2.6.27-7-generic (2.6.27-7.16) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-7-generic.postinst line 110.
dpkg: error al procesar linux-headers-2.6.27-7-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de libc6-dev:
 libc6-dev depende de libc6 (= 2.8~20080505-0ubuntu9); sin embargo:
  La versión de `libc6' en el sistema es 2.8~20080505-0ubuntu7.
dpkg: error al procesar libc6-dev (--configure):
 problemas de dependencias - se deja sin configurar
Configurando libssl0.9.8 (0.9.8g-10.1ubuntu2.2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar libssl0.9.8 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de openssl:
 openssl depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar openssl (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-core:
 xserver-xorg-core depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar xserver-xorg-core (--configure):
 problemas de dependencias - se deja sin configurar
Configurando tzdata (2009f-0ubuntu0.8.10) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar tzdata (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depende de xserver-xorg-core (>= 2:1.5.1-1ubuntu3); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
dpkg: error al procesar xserver-xorg-video-radeon (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depende de xserver-xorg-core (>= 2:1.5.1-1ubuntu3); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
dpkg: error al procesar xserver-xorg-input-evdev (--configure):
 problemas de dependencias - se deja sin configurar
Configurando linux-headers-2.6.24-02062404-generic (2.6.24-02062404) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.24-02062404-generic.postinst line 110.
dpkg: error al procesar linux-headers-2.6.24-02062404-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de linux-restricted-modules-2.6.27-14-generic:
 linux-restricted-modules-2.6.27-14-generic depende de linux-image-2.6.27-14-generic; sin embargo:
  El paquete `linux-image-2.6.27-14-generic' no está instalado.
dpkg: error al procesar linux-restricted-modules-2.6.27-14-generic (--configure):
 problemas de dependencias - se deja sin configurar
Configurando tasksel (2.73ubuntu11.1) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar tasksel (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando linux-headers-2.6.27-14-generic (2.6.27-14.33) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
dpkg --configure -adebconf: DbDriver "config": could not open /var/cache/debconf/config.dat
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-14-generic.postinst line 110.
dpkg: error al procesar linux-headers-2.6.27-14-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Configurando console-setup (1.25ubuntu4) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar console-setup (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de libsnmp15:
 libsnmp15 depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar libsnmp15 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de bind9-host:
 bind9-host depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar bind9-host (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de transmission-gtk:
 transmission-gtk depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar transmission-gtk (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-image-generic:
 linux-image-generic depende de linux-image-2.6.27-14-generic; sin embargo:
  El paquete `linux-image-2.6.27-14-generic' no está instalado.
dpkg: error al procesar linux-image-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libcurl3:
 libcurl3 depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar libcurl3 (--configure):
 problemas de dependencias - se deja sin configurar
Configurando foomatic-filters (4.0.0-0ubuntu3) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar foomatic-filters (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando flashplugin-nonfree (10.0.22.87ubuntu1~intrepid1) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar flashplugin-nonfree (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando libpam-runtime (1.0.1-4ubuntu5.5) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar libpam-runtime (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando ufw (0.23.3) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar ufw (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando msttcorefonts (2.5) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar msttcorefonts (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de linux-restricted-modules-generic:
 linux-restricted-modules-generic depende de linux-restricted-modules-2.6.27-14-generic; sin embargo:
 El paquete `linux-restricted-modules-2.6.27-14-generic' no está configurado todavía.
dpkg: error al procesar linux-restricted-modules-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libdns43:
 libdns43 depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar libdns43 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-intel:
 xserver-xorg-video-intel depende de xserver-xorg-core (>= 2:1.5.1-1ubuntu3); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
dpkg: error al procesar xserver-xorg-video-intel (--configure):
 problemas de dependencias - se deja sin configurar
Configurando cups-bsd (1.3.9-2ubuntu9.1) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar cups-bsd (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de linux-generic:
 linux-generic depende de linux-image-generic (= 2.6.27.14.18); sin embargo:
 El paquete `linux-image-generic' no está configurado todavía.
 linux-generic depende de linux-restricted-modules-generic (= 2.6.27.14.18); sin embargo:
 El paquete `linux-restricted-modules-generic' no está configurado todavía.
dpkg: error al procesar linux-generic (--configure):
 problemas de dependencias - se deja sin configurar
Configurando nvidia-common (0.2.4.1) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error al procesar nvidia-common (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de linux-headers-generic:
 linux-headers-generic depende de linux-headers-2.6.27-14-generic; sin embargo:
 El paquete `linux-headers-2.6.27-14-generic' no está configurado todavía.
dpkg: error al procesar linux-headers-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ntpdate:
 ntpdate depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
dpkg: error al procesar ntpdate (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libpam-ck-connector:
 libpam-ck-connector depende de libpam-runtime (>= 1.0.1-2ubuntu1); sin embargo:
 El paquete `libpam-runtime' no está configurado todavía.
dpkg: error al procesar libpam-ck-connector (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de avahi-daemon:
 avahi-daemon depende de bind9-host | host; sin embargo:
 El paquete `bind9-host' no está configurado todavía.
  El paquete `host' no está instalado.
  El paquete `bind9-host' que provee `host' aún no está configurado.
dpkg: error al procesar avahi-daemon (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ca-certificates:
 ca-certificates depende de openssl; sin embargo:
 El paquete `openssl' no está configurado todavía.
dpkg: error al procesar ca-certificates (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-video-ati:
 xserver-xorg-video-ati depende de xserver-xorg-core (>= 2:1.5.1-1ubuntu3); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
 xserver-xorg-video-ati depende de xserver-xorg-video-radeon; sin embargo:
 El paquete `xserver-xorg-video-radeon' no está configurado todavía.
dpkg: error al procesar xserver-xorg-video-ati (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depende de xserver-xorg-core (>= 2:1.5.1-1ubuntu3); sin embargo:
 El paquete `xserver-xorg-core' no está configurado todavía.
dpkg: error al procesar xserver-xorg-input-vmmouse (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libcurl3-gnutls:
 libcurl3-gnutls depende de ca-certificates; sin embargo:
 El paquete `ca-certificates' no está configurado todavía.
dpkg: error al procesar libcurl3-gnutls (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de dnsutils:
 dnsutils depende de libdns43 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); sin embargo:
 El paquete `libdns43' no está configurado todavía.
 dnsutils depende de libssl0.9.8 (>= 0.9.8f-5); sin embargo:
 El paquete `libssl0.9.8' no está configurado todavía.
 dnsutils depende de bind9-host | host; sin embargo:
 El paquete `bind9-host' no está configurado todavía.
  El paquete `host' no está instalado.
  El paquete `bind9-host' que provee `host' aún no está configurado.
dpkg: error al procesar dnsutils (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libpam0g:
 libpam0g depende de libpam-runtime; sin embargo:
 El paquete `libpam-runtime' no está configurado todavía.
dpkg: error al procesar libpam0g (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de avahi-utils:
 avahi-utils depende de avahi-daemon; sin embargo:
 El paquete `avahi-daemon' no está configurado todavía.
dpkg: error al procesar avahi-utils (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libpam-modules:
 libpam-modules depende de libpam0g (>= 0.99.7.1); sin embargo:
 El paquete `libpam0g' no está configurado todavía.
dpkg: error al procesar libpam-modules (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de foo2zjs:
 foo2zjs depende de foomatic-filters (>= 4.0.0~bzr156); sin embargo:
 El paquete `foomatic-filters' no está configurado todavía.
dpkg: error al procesar foo2zjs (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de base-files:
 base-files depende de libpam-modules (>= 0.79-3ubuntu3); sin embargo:
 El paquete `libpam-modules' no está configurado todavía.
dpkg: error al procesar base-files (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ppp:
 ppp depende de libpam0g (>= 0.99.7.1); sin embargo:
 El paquete `libpam0g' no está configurado todavía.
 ppp depende de libpam-modules; sin embargo:
 El paquete `libpam-modules' no está configurado todavía.
 ppp depende de libpam-runtime (>= 0.76-13.1); sin embargo:
 El paquete `libpam-runtime' no está configurado todavía.
dpkg: error al procesar ppp (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de samba-common:
 samba-common depende de libpam-modules; sin embargo:
 El paquete `libpam-modules' no está configurado todavía.
dpkg: error al procesar samba-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de smbclient:
 smbclient depende de samba-common (= 2:3.2.3-1ubuntu3.4); sin embargo:
 El paquete `samba-common' no está configurado todavía.
dpkg: error al procesar smbclient (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de passwd:
 passwd depende de libpam0g (>= 0.99.7.1); sin embargo:
 El paquete `libpam0g' no está configurado todavía.
 passwd depende de libpam-modules; sin embargo:
 El paquete `libpam-modules' no está configurado todavía.
dpkg: error al procesar passwd (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libisccfg40:
 libisccfg40 depende de libdns43 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); sin embargo:
 El paquete `libdns43' no está configurado todavía.
dpkg: error al procesar libisccfg40 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libbind9-40:
 libbind9-40 depende de libdns43 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); sin embargo:
 El paquete `libdns43' no está configurado todavía.
 libbind9-40 depende de libisccfg40 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); sin embargo:
 El paquete `libisccfg40' no está configurado todavía.
dpkg: error al procesar libbind9-40 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de cups:
 cups depende de libpam0g (>= 0.99.7.1); sin embargo:
 El paquete `libpam0g' no está configurado todavía.
dpkg: error al procesar cups (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: demasiados errores, parando
dpkg: ../../src/packages.c:265: process_queue: Afirmación `!queue.length' fallida.
Cancelado
```

Alguna idea de como solucionarlo :confused:

---

### Post by Hei Ku on 2009-05-25
Este archivo /var/cache/debconf/config.dat
existe, o paso algo? Que paso que tuviste que correr el --configure -a en primer lugar?

---

### Post by andy_91 on 2009-05-25
si el archivo existe (creo). La razon fue un error al instalar el flash player. Al principio no molestaba, pero despues la plaga se fue expandiendo.
Dal flash paso a java de jaa al msttcorefonts y de ahi a el resto que ves.

como atravez del update manager

---

### Post by Hei Ku on 2009-05-25
"Creo" no sirve. Existe y tiene algun contenido o no?

---

### Post by Hei Ku on 2009-05-25
Proba poniendo:

sudo apt-get --reinstall install debconf

---

### Post by andy_91 on 2009-05-25
```
andy@andy-desktop:~$ sudo apt-get --reinstall install debconf
[sudo] password for andy: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

bueno el archivo existir existe lo que no se es si es el mismo que el principio cuando instale el flash, por que borre algunos archivos, para poder seguir usando el synaptic normalmente. (funciono por un tiempo)

---

### Post by Hei Ku on 2009-05-25
Como prueba, podes probar de hacer un backup de los archivos de la carpeta /var/cache/debconf, borrar todo el contenido de la carpeta y correr el dpkg --configure -a otra vez

Pero venis arrastrando un problema de antes por meter mano, asi que no se que puede pasar sin saber los detalles de lo que borraste.

---

### Post by andy_91 on 2009-05-25
borre los archivos de var/chae/apt y var/cache/app-install

---

### Post by Hei Ku on 2009-05-25
uhh! :D

Probaste borrando el contenido de /var/cache/debconf como te sugeri?

---

### Post by andy_91 on 2009-05-26
si borre la carpeta

---

### Post by Hei Ku on 2009-05-26
y te sigue apareciendo el mismo error?
Ojo que era borrar los contenidos de la carpeta, no la carpeta en sí. Si no, te va a aparecer el mismo error.

---

### Post by andy_91 on 2009-05-26
ahora cree esa carpeta y va masomenos normal pero se cuelga el flash

---

### Post by Hei Ku on 2009-05-26
andy, se mas especifico. pudiste resolver el problema de actualizacion?

el problema con flash cual es? no se instala? se instala pero no corre?

---

### Post by andy_91 on 2009-05-27
el de este tema

> **ambystoma_19 said:**
> hola como estan todos, estoy pidiendo ayuda aqui porque ya estoy cansado.
bueno hace unos dias tuve que reinstalasr el sistema por problemas con un kernel, estoy usando ubuntu 8.10. pero el problemas de ahora no es por eso, es por el flash player.
bueno como yua dije tuve que reinstalar el sistema, terminado esto fui a youtube con mozilla y me pidoio los plugins, y nunca instalo el adobe flash player 10, intente hacerlo desde consola y se queda en la parte de peticion http enviada, esperando repuesta... y luego de multiples intentos llo cierro. lo cual me trajo muchos problemas con el dpkg, que ya estan solucionados. entonces intente descargarlo desde la pagina, pero jamas lo descarga, ni el.deb, ni el tar.gz ni el .rpm.
enconclusion no puedo usar ninguna pagina que necesite flash, alguien me podria ayudar coon este problemita.?
 recuerdo haber comentado ahi tener ese problema

---


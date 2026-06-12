---
title: "Problema instalar programas"
date: 2010-02-28
forum: Software
---

### Post by juanlunix on 2010-02-28
hola! sigo con problemas para instalar programas.
Abro un nuevo post, ya que el que abri hace unas semanas figura como "solved", asi que espero no romper ninguna regla del foro.

El problema que tengo es que instalo programas ( ya sea desde centro de soft ubuntu, gestor de paquetes syp.., como desde el terminal con la opcion sudo) en el medio de la instalacion me saltan errores ( los programas estan dentro de la opcion aplicaciones pero no anda ninguno).
Ya prove con desintalar e intalar, como tambien con la opncion desintalar y eliminar (ese el gestor de paquetes).
cuando saltan los erores le pongo detalles sale u choclo larguisimo, les dejo unas capturas, quice hacer uin pocy paste pero no me deja.
Si son demasiadas fotos y las debo remover  les pido diosculpas,
saludos

---

### Post by juanlunix on 2010-02-28
sigue

---

### Post by juanlunix on 2010-02-28
sigue..

---

### Post by juanlunix on 2010-02-28
sigue...

---

### Post by juanlunix on 2010-02-28
sigue

---

### Post by juanlunix on 2010-02-28
sigue...

---

### Post by juanlunix on 2010-02-28
siguue

---

### Post by juanlunix on 2010-02-28
sigue...........................

---

### Post by juanlunix on 2010-02-28
ufff  el ultimo!

---

### Post by guillermolisi on 2010-02-28
Podrias mostrarnos el contenido de /etc/apt/sources.list y /etc/apt/sources.list.d ademas de indicarnos que version de Ubuntu estas usando ?

---

### Post by juanlunix on 2010-03-03
guillermo:
la version es ubuntu9.10, creo que es la ultima, la baje hace poco menos de un mes.
el sources.list lo abri con gedit  y dice:
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


en la carpeta sources.list.d hay dos archivos:
[B]google-chrome.list
el contenido:
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main


y el }archivo medibuntu.list
contenido:
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"

espero que alla entendido lo que me estas pidiendo,
desd ya muchas gracias!
[/B]

---

### Post by juanlunix on 2010-03-04
si intento instalar desde centro de software ubuntu sucede esto:
installArchives() failed: Seleccionando el paquete libdbi0 previamente no seleccionado. 
(Leyendo la base de datos ...  (Leyendo la base de datos ... 5% (Leyendo la base de datos ... 10% (Leyendo la base de datos ... 15% (Leyendo la base de datos ... 20% (Leyendo la base de datos ... 25% (Leyendo la base de datos ... 30% (Leyendo la base de datos ... 35% (Leyendo la base de datos ... 40% (Leyendo la base de datos ... 45% (Leyendo la base de datos ... 50% (Leyendo la base de datos ... 55% (Leyendo la base de datos ... 60% (Leyendo la base de datos ... 65% (Leyendo la base de datos ... 70% (Leyendo la base de datos ... 75% (Leyendo la base de datos ... 80% (Leyendo la base de datos ... 85% (Leyendo la base de datos ... 90% (Leyendo la base de datos ... 95% (Leyendo la base de datos ... 100% (Leyendo la base de datos ...   
175143 ficheros y directorios instalados actualmente.) 
Desempaquetando libdbi0 (de .../libdbi0_0.8.2-3_i386.deb) ... 
Seleccionando el paquete libgammu-i18n previamente no seleccionado. 
Desempaquetando libgammu-i18n (de .../libgammu-i18n_1.24.0-1ubuntu1_all.deb) ... 
Seleccionando el paquete libusb-1.0-0 previamente no seleccionado. 
Desempaquetando libusb-1.0-0 (de .../libusb-1.0-0_2%3a1.0.1-1_i386.deb) ... 
Seleccionando el paquete libgammu6 previamente no seleccionado. 
Desempaquetando libgammu6 (de .../libgammu6_1.24.0-1ubuntu1_i386.deb) ... 
Seleccionando el paquete libmysqlclient15off previamente no seleccionado. 
Desempaquetando libmysqlclient15off (de .../libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb) ... 
Seleccionando el paquete libgsmsd6 previamente no seleccionado. 
Desempaquetando libgsmsd6 (de .../libgsmsd6_1.24.0-1ubuntu1_i386.deb) ... 
Seleccionando el paquete python-bluez previamente no seleccionado. 
Desempaquetando python-bluez (de .../python-bluez_0.16-1ubuntu1_i386.deb) ... 
Seleccionando el paquete python-gammu previamente no seleccionado. 
Desempaquetando python-gammu (de .../python-gammu_1.24.0-1ubuntu1_i386.deb) ... 
Seleccionando el paquete python-wxversion previamente no seleccionado. 
Desempaquetando python-wxversion (de .../python-wxversion_2.8.10.1-0ubuntu1_all.deb) ... 
Seleccionando el paquete python-wxgtk2.8 previamente no seleccionado. 
Desempaquetando python-wxgtk2.8 (de .../python-wxgtk2.8_2.8.10.1-0ubuntu1_i386.deb) ... 
Seleccionando el paquete timidity previamente no seleccionado. 
Desempaquetando timidity (de .../timidity_2.13.2-36_i386.deb) ... 
Seleccionando el paquete timidity-daemon previamente no seleccionado. 
Desempaquetando timidity-daemon (de .../timidity-daemon_2.13.2-36_all.deb) ... 
Seleccionando el paquete wammu previamente no seleccionado. 
Desempaquetando wammu (de .../wammu_0.30.1-2_all.deb) ... 
Procesando disparadores para man-db ... 
Procesando disparadores para ureadahead ... 
Procesando disparadores para desktop-file-utils ... 
Configurando liblzma0 (4.999.8beta-0ubuntu2) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar liblzma0 (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
Configurando libqtcore4 (4.5.3really4.5.2-0ubuntu1) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar libqtcore4 (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
dpkg: problemas de dependencias impiden la configuración de libqt4-xml: 
 libqt4-xml depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-xml (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-dbus: 
 libqt4-dbus depende de libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 libqt4-dbus depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-dbus (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: pNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
roblemas de dependencias impiden la configuración de libqt4-script: 
 libqt4-script depende de libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 libqt4-script depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-script (--configure): 
 problemas de dependencias - se deja sin configurar 
Configurando libaudio2 (1.9.2-1) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar libaudio2 (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
dpkg: problemas de dependencias impiden la configuración de libqtgui4: 
 libqtgui4 depende de libaudio2; sin embargo: 
 El paquete `libaudio2' no está configurado todavía. 
 libqtgui4 depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' noNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
 está configurado todavía. 
dpkg: error al procesar libqtgui4 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-designer: 
 libqt4-designer depende de libqt4-script (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-script' no está configurado todavía. 
 libqt4-designer depende de libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 libqt4-designer depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libqt4-designer depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libqt4-designer (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-network: 
 libqt4-network depende de libqtcore4 (= 4.5.3really4.5.2No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-network (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-phonon: 
 libqt4-phonon depende de libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 libqt4-phonon depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libqt4-phonon depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libqt4-phonon (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-sql: 
 libqt4-sql depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-sql (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-qt3support: 
 libqt4-qt3support depende de libqt4-designer (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-designer' no está configurado todavía. 
 libqt4-qt3support depende de libqt4-network (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 libqt4-qt3support depende de libqt4-sql (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-sql' no está configurado todavía. 
 libqt4-qt3support depende de libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 libqt4-qt3support depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libqt4-qt3support depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libqt4-qt3support (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-svg: 
 libqt4-svg depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libqt4-svg depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libqt4-svg (--configure): 
 problemas de dependencias - se deja sin configurar 
Configurando libclucene0ldbl (0.9.20-3) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar libclucene0ldbl (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
dpkg: problemas de dependencias impiden la configuración de libsoprano4: 
 libsoprano4 depende de libclucene0ldbl (>= 0.9.20-1); sin embargo: 
 El paquete `libclucene0ldbl' no está configurado todavía. 
 libsoprano4 depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 libsoprano4 depende de libqt4-network (>= 4.5.1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 libsoprano4 depende de libqt4-xml (>= 4.5.1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 libsoprano4 depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libsoprano4 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de soprano-daemon: 
 soprano-daemon depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 soprano-daemon depende de libqt4-network (>= 4.5.1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 soprano-daemon depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 soprano-daemon depende de libsoprano4 (>= 2.3.0); sin embargo: 
 El paquete `libsoprano4' no está configurado todavía. 
dpkg: error al procesar soprano-daemon (--configure): 
 problemas de dependencias - se deja sin configurar 
Configurando libexiv2-5 (0.18.2-1) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar libexiv2-5 (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
Configurando libstreams0 (0.7.0-1) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar libstreams0 (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
dpkg: problemas de dependencias impiden la configuración de libstreamanalyzer0: 
 libstreamanalyzer0 depende de libclucene0ldbl (>= 0.9.20-1); sin embargo: 
 El paquete `libclucene0ldbl' no está configurado todavía. 
 libstreamanalyzer0 depende de libexiv2-5; sin embargo: 
 El paquete `libexiv2-5' no está configurado todavía. 
 libstreamanalyzer0 depende de libstreams0 (= 0.7.0-1); sin embargo: 
 El paquete `libstreams0' no está configurado todavía. 
dpkg: error al procesar libstreamanalyzer0 (--configure): 
 problemas de dependencias - se deja sin configurar 
Configurando kdelibs5-data (4:4.3.2-0ubuntu7.2) ... 
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable 
dpkg: error al procesar kdelibs5-data (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
dpkg: problemas de dependencias impiden la configuración de kdelibs5: 
 kdelibs5 depende de liblzma0 (>= 4.999.7beta); sin embargo: 
 El paquete `liblzma0' no está configurado todavía. 
 kdelibs5 depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 kdelibs5 depende de libqt4-designer (>= 4.5.1); sin embargo: 
 El paquete `libqt4-designer' no está configurado todavía. 
 kdelibs5 depende de libqt4-network (>= 4.5.1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 kdelibs5 depende de libqt4-phonon (>= 4.5.1); sin embargo: 
 El paquete `libqt4-phonon' no está configurado todavía. 
 kdelibs5 depende de libqt4-qt3support (>= 4.5.1); sin embargo: 
 El paquete `libqt4-qt3support' no está configurado todavía. 
 kdelibs5 depende de libqt4-script (>= 4.5.1); sin embargo: 
 El paquete `libqt4-script' no está configurado todavía. 
 kdelibs5 depende de libqt4-svg (>= 4.5.1); sin embargo: 
 El paquete `libqt4-svg' no está configurado todavía. 
 kdelibs5 depende de libqt4-xml (>= 4.5.1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 kdelibs5 depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 kdelibs5 depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
 kdelibs5 depende de libsoprano4 (>= 2.2.69); sin embargo: 
 El paquete `libsoprano4' no está configurado todavía. 
 kdelibs5 depende de libstreamanalyzer0 (>= 0.7.0); sin embargo: 
 El paquete `libstreamanalyzer0' no está configurado todavía. 
 kdelibs5 depende de kdelibs5-data (>= 4:4.3.2-0ubuntu7.2); sin embargo: 
 El paquete `kdelibs5-data' no está configurado todavía. 
dpkg: error al procesar kdelibs5 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de kdelibs-bin: 
 kdelibs-bin depende de kdelibs5 (= 4:4.3.2-0ubuntu7.2); sin embargo: 
 El paquete `kdelibs5' no está configurado todavía. 
 kdelibs-bin depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 kdelibs-bin depende de libqt4-xml (>= 4.5.1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 kdelibs-bin depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 kdelibs-bin depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
 kdelibs-bin depende de libsoprano4 (>= 2.1.67); sin embargo: 
 El paquete `libsoprano4' no está configurado todavía. 
dpkg: error al procesar kdelibs-bin (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-webkit: 
 libqt4-webkit depende de libqt4-network (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 libqt4-webkit depende de libqt4-phonon (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-phonon' no está configurado todavía. 
 libqt4-webkit depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libqt4-webkit depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libqt4-webkit (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de googleearth: 
 googleearth depende de libqt4-network (>= 4.5.1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 googleearth depende de libqt4-webkit (>= 4.5.1); sin embargo: 
 El paquete `libqt4-webkit' no está configurado todavía. 
 googleearth depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 googleearth depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar googleearth (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libknotificationitem1: 
 libknotificationitem1 depende de kdelibs5 (>= 4:4.3.2); sin embargo: 
 El paquete `kdelibs5' no está configurado todavía. 
 libknotificationitem1 depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 libknotificationNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
item1 depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libknotificationitem1 depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libknotificationitem1 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-opengl: 
 libqt4-opengl depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libqt4-opengl depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar libqt4-opengl (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libplasma3: 
 libplasma3 depende de kdelibs5 (>= 4:4.3.2); sin embargo: 
 El paquete `kdelibs5' no está configurado todavía. 
 libplasma3 depende de libqt4-opengl (>= 4.5.1); sin embargo: 
 El paquete `libqt4-opengl' no está configurado todavía. 
 libplasma3 depende de libqt4-phonon (>= 4.5.1); sin embargo: 
 El paquete `libqt4-phonon' no está configurado todavía. 
 libplasma3 depende de libqt4-svg (>= 4.5.1); sin embargo: 
 El paquete `libqt4-svg' no está configurado todavía. 
 libplasma3 depende de libqt4-webkit (>= 4.5.1); sin embargo: 
 El paquete `libqt4-webkit' no está configurado todavía. 
 libplasma3 depende de libqt4-xml (>= 4.5.1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 libplasma3 depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 libplasma3 depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
 libplasma3 depende de kdelibs5-data (= 4:4.3.2-0ubuntu7.2); sin embargo: 
 El paquete `kdelibs5-data' no está configurado todavía. 
dpkg: error al procesar libplasma3 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de phonon-backend-xine: 
 phonon-backend-xine depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 phonon-backend-xine depende de libqt4-phonon (>= 4.5.1); sin embargo: 
 El paquete `libqt4-phonon' no está configurado todavía. 
 phonon-backend-xine depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 phonon-backend-xine depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar phonon-backend-xine (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de kdebase-runtime: 
 kdebase-runtime depende de kdelibs5 (>= 4:4.3.2); sin embargo: 
 El paquete `kdelibs5' no está configurado todavía. 
 kdebase-runtime depende de libclucene0ldbl (>= 0.9.20-1); sin embargo: 
 El paquete `libclucene0ldbl' no está configurado todavía. 
 kdebase-runtime depende de libknotificationitem1; sin embargo: 
 El paquete `libknotificationitem1' no está configurado todavía. 
 kdebase-runtime depende de libplasma3 (>= 4:4.3.2); sin embargo: 
 El paquete `libplasma3' no está configurado todavía. 
 kdebase-runtime depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 kdebase-runtime depende de libqt4-network (>= 4.5.1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 kdebase-runtime depende de libqt4-phonon (>= 4.5.1); sin embargo: 
 El paquete `libqt4-phonon' no está configurado todavía. 
 kdebase-runtime depende de libqt4-qt3support (>= 4.5.1); sin embargo: 
 El paquete `libqt4-qt3support' no está configurado todavía. 
 kdebase-runtime depende de libqt4-svg (>= 4.5.1); sin embargo: 
 El paquete `libqt4-svg' no está configurado todavía. 
 kdebase-runtime depende de libqt4-xml (>= 4.5.1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 kdebase-runtime depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 kdebase-runtime depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
 kdebase-runtime depende de libsoprano4 (>= 2.3.0); sin embargo: 
 El paquete `libsoprano4' no está configurado todavía. 
 kdebase-runtime depende de libstreamanalyzer0 (>= 0.7.0); sin embargo: 
 El paquete `libstreamanalyzer0' no está configurado todavía. 
 kdebase-runtime depende de libstreams0 (>= 0.7.0); sin embargo: 
 El paquete `libstreams0' no está configurado todavía. 
 kdebase-runtime depende de phonon-backend-xine | phonon-backend; sin embargo: 
 El paquete `phonon-backend-xine' no está configurado todavía. 
  El paquete `phonon-backend' no está instalado. 
  El paquete `phonon-backend-xine' que provee `phonon-backend' aún no está configurado. 
dpkg: error al procesar kdebase-runtime (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de kdebase-runtime-bin-kde4: 
 kdebase-runtime-bin-kde4 depende de kdebase-runtime (>= 4:4.3.2); sin embargo: 
 El paquete `kdebase-runtime' no está configurado todavía. 
 kdebase-runtime-bin-kde4 depende de kdelibs5 (>= 4:4.3.2); sin embargo: 
 El paquete `kdelibs5' no está configurado todavía. 
 kdebase-runtime-bin-kde4 depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 kdebase-runtime-bin-kde4 depende de libqt4-svg (>= 4.5.1); sin embargo: 
 El paquete `libqt4-svg' no está configurado todavía. 
 kdebase-runtime-bin-kde4 depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 kdebase-runtime-bin-kde4 depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar kdebase-runtime-bin-kde4 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de kdelibs-data: 
 kdelibs-data depende de kdelibs5-data; sin embargo: 
 El paquete `kdelibs5-data' no está configurado todavía. 
dpkg: error al procesar kdelibs-data (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt3-mt: 
 libqt3-mt depende de libaudio2; sin embargo: 
 El paquete `libaudio2' no está configurado todavía. 
dpkg: error al procesar libqt3-mt (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libavahi-qt3-1: 
 libavahi-qt3-1 depende de libaudio2; sin embargo: 
 El paquete `libaudio2' no está configurado todavía. 
 libavahi-qt3-1 depende de libqt3-mt (>= 3:3.3.8-b); sin embargo: 
 El paquete `libqt3-mt' no está configurado todavía. 
dpkg: error al proceNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
sar libavahi-qt3-1 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de kdelibs4c2a: 
 kdelibs4c2a depende de libavahi-qt3-1 (>= 0.6.16); sin embargo: 
 El paquete `libavahi-qt3-1' no está configurado todavía. 
 kdelibs4c2a depende de libqt3-mt (>= 3:3.3.8-b); sin embargo: 
 El paquete `libqt3-mt' no está configurado todavía. 
 kdelibs4c2a depende de kdelibs-data (>> 4:3.5.10.dfsg.1); sin embargo: 
 El paquete `kdelibs-data' no está configurado todavía. 
 kdelibs4c2a depende de kdelibs-data (<< 4:3.5.10.dfsg.2); sin embargo: 
 El paquete `kdelibs-data' no está configurado todavía. 
dpkg: error al procesar kdelibs4c2a (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de khelpcenter4: 
 khelpcenter4 depende de kdebase-runtime (>= 4:4.3.2); sin embargo: 
 El paquete `kdebase-runtime' no está configurado todavía. 
 khelpcenter4 depende de kdelibs5 (>= No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
4:4.3.2); sin embargo: 
 El paquete `kdelibs5' no está configurado todavía. 
 khelpcenter4 depende de libqt4-dbus (>= 4.5.1); sin embargo: 
 El paquete `libqt4-dbus' no está configurado todavía. 
 khelpcenter4 depende de libqt4-network (>= 4.5.1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 khelpcenter4 depende de libqt4-qt3support (>= 4.5.1); sin embargo: 
 El paquete `libqt4-qt3support' no está configurado todavía. 
 khelpcenter4 depende de libqt4-svg (>= 4.5.1); sin embargo: 
 El paquete `libqt4-svg' no está configurado todavía. 
 khelpcenter4 depende de libqt4-xml (>= 4.5.1); sin embargo: 
 El paquete `libqt4-xml' no está configurado todavía. 
 khelpcenter4 depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 khelpcenter4 depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar khelpcenter4 (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de kmobiletools: 
 kmobiletools depende de kdelibs4c2a (>= 4:3.5.9); sin embargo: 
 El paquete `kdelibs4c2a' no está configurado todavía. 
 kmobiletools depende de libaudio2; sin embargo: 
 El paquete `libaudio2' no está configurado todavía. 
 kmobiletools depende de libqt3-mt (>= 3:3.3.8-b); sin embargo: 
 El paquete `libqt3-mt' no está configurado todavía. 
dpkg: error al procesar kmobiletools (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-assistant: 
 libqt4-assistant depende de libqt4-network (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-network' no está configurado todavía. 
 libqt4-assistant depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-assistant (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-gui: 
 libqt4-gui depende de libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
 libqt4-gui depende de libqt4-svg (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-svg' no está configurado todavía. 
 libqt4-gui depende de libqt4-opengl (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-opengl' no está configurado todavía. 
 libqt4-gui depende de libqt4-designer (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-designer' no está configurado todavía. 
 libqt4-gui depende de libqt4-assistant (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-assistant' no está configurado todavía. 
dpkg: error al procesar libqt4-gui (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-sql-sqlite: 
 libqt4-sql-sqlite depende de libqt4-sql (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqt4-sql' no está configurado todavía. 
 libqt4-sql-sqlite depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-sql-sqlite (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de vlc: 
 vlc depende de libqtcore4 (>= 4.5.1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
 vlc depende de libqtgui4 (>= 4.5.1); sin embargo: 
 El paquete `libqtgui4' no está configurado todavía. 
dpkg: error al procesar vlc (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de mozilla-plugin-vlc: 
 mozilla-plugin-vlc depende de vlc; sin embargo: 
 El paquete `vlc' no está configurado todavía. 
dpkg: error al procesar mozilla-plugin-vlc (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de lsb-desktop: 
 lsb-desktop depende de libqt3-mt (>= 3.3.6); sin embargo: 
 El paquete `libqt3-mt' no está configurado todavía. 
 lsb-desktop depende de libqt4-gui (>= 4.3); sin embargo: 
 El paquete `libqt4-gui' no está configurado todavía. 
 lsb-desktop depende de libqt4-sql-sqlite; sin embargo: 
 El paquete `libqt4-sql-sqlite' no está configurado todavía. 
dpkg: error al procesar lsb-desktop (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de lsb: 
 lsb depende de lsb-desktop; sin embargo: 
 El paquete `lsb-desktop' no está configurado todavía. 
dpkg: error al procesar lsb (--configure): 
 problemas de dependencias - se deja sin configurar 
Configurando libdbi0 (0.8.2-3) ... 
 
Configurando libgammu-i18n (1.24.0-1ubuntu1) ... 
Configurando libusb-1.0-0 (2:1.0.1-1) ... 
 
Configurando libgammu6 (1.24.0-1ubuntu1) ... 
 
Configurando libmysqlclient15off (5.1.30really5.0.83-0ubuntu3) ... 
 
Configurando libgsmsd6 (1.24.0-1ubuntu1) ... 
 
Configurando python-bluez (0.16-1ubuntu1) ... 
 
Configurando python-gammu (1.24.0-1ubuntu1) ... 
 
dpkg: problemas de dependencias impiden la configuración de timidity: 
 timidity depende de libaudio2; sin embargo: 
 El paquete `libaudio2' no está configurado todavía. 
dpkg: error al procesar timidity (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de timidity-daemon: 
 timidity-daemon depende de timidity (>= 2.13.2-36); sin embargo: 
 El paquete `timidity' no está configurado todavía. 
dpkg: error al procesar timidity-daemon (--configure): 
 problemas de dependencias - se deja sin configurar 
Configurando python-wxversion (2.8.10.1-0ubuntu1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
 
Configurando python-wxgtk2.8 (2.8.10.1-0ubuntu1) ... 
update-alternatives: usar /usr/lib/wx/python/wx2.8.pth para proporcionar /usr/lib/python2.5/site-packages/wx.pth (wx2.5.pth) en modo automático 
update-alternatives: usar /usr/lib/wx/python/wx2.8.pth para proporcionar /usr/lib/python2.6/dist-packages/wx.pth (wx2.6.pth) en modo automático 
 
Configurando wammu (0.30.1-2) ... 
 
Procesando disparadores para libc-bin ... 
ldconfig deferred processing now taking place 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDBus.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsopranoclient.so.1.1.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libstreamanalyzer.so.0.7.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtCLucene.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtSvg.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQt3Support.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDBus.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libstreamanalyzer.so.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtNetwork.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtSvg.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libaudio.so.2.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDesignerComponents.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDesignerComponents.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libaudio.so.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtXml.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtSql.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtCLucene.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtScript.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libstreams.so.0.7.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsopranoserver.so.1 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDesigner.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDesignerComponents.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtXml.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtGui.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsoprano.so.4.2.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtCore.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQt3Support.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtSql.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libphonon.so.4.3.1 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtNetwork.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQt3Support.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libphonon.so.4.3 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDesigner.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libclucene.so.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsopranoserver.so.1.0.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsopranoclient.so.1 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libexiv2.so.5.3.1 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtCLucene.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libexiv2.so.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtScript.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libkdeinit4_kded4.so esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtGui.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtXml.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtSvg.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtGui.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libclucene.so.0.0.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsopranoindex.so.1 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/liblzma.so.0.0.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtNetwork.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/liblzma.so.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtScript.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libkdeinit4_kbuildsycoca4.so esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libstreams.so.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtSql.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtCore.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsopranoindex.so.1.1.0 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDesigner.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtDBus.so.4.5 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libQtCore.so.4.5.2 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libphonon.so.4 esta vacio, no fue verificado. 
/sbin/ldconfig.real: El archivo /usr/lib/libsoprano.so.4 esta vacio, no fue verificado. 
Procesando disparadores para python-support ... 
Se encontraron errores al procesar: 
 liblzma0 
 libqtcore4 
 libqt4-xml 
 libqt4-dbus 
 libqt4-script 
 libaudio2 
 libqtgui4 
 libqt4-designer 
 libqt4-network 
 libqt4-phonon 
 libqt4-sql 
 libqt4-qt3support 
 libqt4-svg 
 libclucene0ldbl 
 libsoprano4 
 soprano-daemon 
 libexiv2-5 
 libstreams0 
 libstreamanalyzer0 
 kdelibs5-data 
 kdelibs5 
 kdelibs-bin 
 libqt4-webkit 
 googleearth 
 libknotificationitem1 
 libqt4-opengl 
 libplasma3 
 phonon-backend-xine 
 kdebase-runtime 
 kdebase-runtime-bin-kde4 
 kdelibs-data 
 libqt3-mt 
 libavahi-qt3-1 
 kdelibs4c2a 
 khelpcenter4 
 kmobiletools 
 libqt4-assistant 
 libqt4-gui 
 libqt4-sql-sqlite 
 vlc 
 mozilla-plugin-vlc 
 lsb-desktop 
 lsb 
 timidity 
 timidity-daemon

---

### Post by guillermolisi on 2010-03-04
Por lo que mostraste, los repositorios estan bien. No veo nada raro en como estan y en cuales estan.

Lo que te esta pasando es que estas usando software desarrollado para KDE, en base a la interface Qt, y te estan faltando componentes, por eso este error (por ejemplo):> 
dpkg: error al procesar libqtcore4 (--configure): 
 el subproceso script post-installation instalado devolvió el código de salida de error 2 
dpkg: problemas de dependencias impiden la configuración de libqt4-xml: 
 libqt4-xml depende de libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); sin embargo: 
 El paquete `libqtcore4' no está configurado todavía. 
dpkg: error al procesar libqt4-xml (--configure): 
 problemas de dependencias - se deja sin configurar 
dpkg: problemas de dependencias impiden la configuración de libqt4-dbus: 
Y al faltar componentes el resto de lo que queres instalar/actualizar no finaliza por dependencias no resueltas correctamente.

---

### Post by juanlunix on 2010-03-04
disculpa mi ignorancia pero como pongo los componentes que me faltan? no puedo instalar ni el vlc.....
gracias por tus respuestas

---

### Post by guillermolisi on 2010-03-04
Hay que buscar que paquetes estas queriendo instalar que usen Qt y quitarlos para probar y ver que pasa.
Que escritorio estas usando ? Es Gnome o KDE ?

Que pasa si abris Synaptic ? Te muestra paquetes rotos ? Si es asi, cuales ?

---

### Post by juanlunix on 2010-03-05
en Synaptic no muestra ningun paquete roto.... todo lo que mencionas la verdad que no entiendo mucho....estoy en una situcion que es mejor " format c: " ????  (disculpen mi windowsrismo).
De todas formas me gustaria comprender que hice mal, para no repetir el error.
gracias y disculpas, soy un queso tratando de adaptarse a un nuevo sistema operativo..........

saludos

juan

---


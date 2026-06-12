---
title: "Instalando Audacity"
date: 2009-02-02
forum: Software
---

### Post by NickCis on 2009-02-02
Hola, al intentar instalar audacity me devuelve este error:

```
newpc@ubuntu-newpc:~$ sudo apt-get install audacity
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  audacity: Depende: libasound2 (> 1.0.17) pero 1.0.15-3ubuntu4 va a ser instalado
            Depende: libgtk2.0-0 (>= 2.14.1) pero 2.12.9-3ubuntu5 va a ser instalado
            Depende: libmad0 (>= 0.15.1b-3) pero 0.15.1b-2.1ubuntu1 va a ser instalado
            Depende: libsoundtouch1c2 (>= 1.3.1) pero 1.3.0-2.2ubuntu0.1 va a ser instalado
            Depende: libwxbase2.8-0 (>= 2.8.8.0) pero no va a instalarse
            Depende: libwxgtk2.8-0 (>= 2.8.8.0) pero no va a instalarse
E: Paquetes rotos
newpc@ubuntu-newpc:~$ 

```

No entiendo, bien como es, por lo que lei por internet es un problema relacionado con que me faltan algunos repositorios, puede ser?.

Saludos.

P.D.: antes de ejecutar el comando "sudo apt-get install audacity", hice un "sudo apt-get update".
Añado la info que me da al hacer un "sudo apt-get update"

```
newpc@ubuntu-newpc:~$ sudo apt-get update
Obj http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-es              
Ign http://security.ubuntu.com hardy-security/restricted Translation-es        
Obj http://ar.archive.ubuntu.com hardy Release.gpg                             
Obj http://ar.archive.ubuntu.com hardy/main Translation-es                     
Obj http://ar.archive.ubuntu.com hardy/restricted Translation-es               
Obj http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-es                    
Ign http://security.ubuntu.com hardy-security/universe Translation-es          
Ign http://security.ubuntu.com hardy-security/multiverse Translation-es        
Obj http://security.ubuntu.com hardy-security Release                          
Obj http://ar.archive.ubuntu.com hardy/universe Translation-es                 
Obj http://ar.archive.ubuntu.com hardy/multiverse Translation-es               
Obj http://ar.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://ar.archive.ubuntu.com hardy-updates/main Translation-es             
Ign http://ar.archive.ubuntu.com hardy-updates/restricted Translation-es       
Ign http://ar.archive.ubuntu.com hardy-updates/universe Translation-es         
Ign http://ar.archive.ubuntu.com hardy-updates/multiverse Translation-es       
Obj http://ar.archive.ubuntu.com hardy Release                                 
Ign http://packages.medibuntu.org hardy/non-free Translation-es                
Obj http://packages.medibuntu.org hardy Release                                
Obj http://security.ubuntu.com hardy-security/main Packages                    
Obj http://ar.archive.ubuntu.com hardy-updates Release                         
Obj http://packages.medibuntu.org hardy/free Packages                          
Obj http://security.ubuntu.com hardy-security/restricted Packages              
Obj http://security.ubuntu.com hardy-security/main Sources                     
Obj http://security.ubuntu.com hardy-security/restricted Sources               
Obj http://security.ubuntu.com hardy-security/universe Packages                
Obj http://ar.archive.ubuntu.com hardy/main Packages                           
Obj http://ar.archive.ubuntu.com hardy/restricted Packages                     
Obj http://ar.archive.ubuntu.com hardy/main Sources                            
Obj http://ar.archive.ubuntu.com hardy/restricted Sources                      
Obj http://ar.archive.ubuntu.com hardy/universe Packages                       
Obj http://security.ubuntu.com hardy-security/universe Sources                 
Obj http://security.ubuntu.com hardy-security/multiverse Packages              
Obj http://security.ubuntu.com hardy-security/multiverse Sources               
Obj http://ar.archive.ubuntu.com hardy/universe Sources                        
Obj http://ar.archive.ubuntu.com hardy/multiverse Packages                     
Obj http://packages.medibuntu.org hardy/non-free Packages                      
Obj http://ar.archive.ubuntu.com hardy/multiverse Sources                      
Obj http://ar.archive.ubuntu.com hardy-updates/main Packages                   
Obj http://ar.archive.ubuntu.com hardy-updates/restricted Packages             
Obj http://ar.archive.ubuntu.com hardy-updates/main Sources                    
Obj http://ar.archive.ubuntu.com hardy-updates/restricted Sources              
Obj http://ar.archive.ubuntu.com hardy-updates/universe Packages               
Obj http://ar.archive.ubuntu.com hardy-updates/universe Sources                
Obj http://ar.archive.ubuntu.com hardy-updates/multiverse Packages             
Obj http://ar.archive.ubuntu.com hardy-updates/multiverse Sources              
Ign http://ubuntu.org.ua getdeb/ Release.gpg                                   
Ign http://ubuntu.org.ua getdeb/ Translation-es                      
Ign http://ubuntu.org.ua getdeb/ Release                             
Ign http://ubuntu.org.ua getdeb/ Packages                            
Obj http://wine.budgetdedicated.com hardy Release.gpg                
Ign http://wine.budgetdedicated.com hardy/main Translation-es
Obj http://ubuntu.org.ua getdeb/ Packages              
Obj http://wine.budgetdedicated.com hardy Release
Ign http://wine.budgetdedicated.com hardy/main Packages
Obj http://wine.budgetdedicated.com hardy/main Packages
Leyendo lista de paquetes... Hecho
newpc@ubuntu-newpc:~$
```

---

### Post by Hei Ku on 2009-02-02
Postea el contenido del archivo /etc/apt/sources.list

---

### Post by NickCis on 2009-02-04
Mi /etc/apt/sources.list :
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ar.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ubuntu.org.ua/ getdeb/
```

---

### Post by Hei Ku on 2009-02-04
Parece que esta habilitado todo lo que hace falta.


Poné:

sudo aptitude install audacity

Y a ver qué errores te tira asi.

---

### Post by NickCis on 2009-02-05
Me devuelve esto:
```
newpc@ubuntu-newpc:~$ sudo aptitude install audacity
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes están ROTOS:
  audacity 
Los siguientes paquetes han sido retenidos automáticamente:
  libavcodec1d libavformat1d libavutil1d libpostproc1d linux-libc-dev 
  linux-restricted-modules-common openoffice.org-help-es 
  openoffice.org-l10n-es 
Se instalarán automáticamente los siguientes paquetes NUEVOS:
  libflac++6 
Se han retenido los siguientes paquetes:
  acpi-support acpid app-install-data-commercial avahi-autoipd avahi-daemon 
  base-files bind9-host brasero bsdutils compiz-fusion-plugins-main 
  console-setup cupsys cupsys-bsd cupsys-client cupsys-common dnsutils 
  evolution-data-server evolution-data-server-common firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gimp gimp-data 
  gimp-gnomevfs gimp-python gksu gnome-power-manager grub guidance-backends 
  hal-info initramfs-tools jockey-common jockey-gtk language-pack-en 
  language-pack-en-base language-pack-es language-pack-es-base 
  language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-es 
  language-pack-gnome-es-base libavahi-client3 libavahi-common-data 
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 
  libavahi-ui0 libbind9-30 libcamel1.2-11 libcupsimage2 libcupsys2 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libgadu3 libgdata-google1.2-1 libgdata1.2-1 
  libgimp2.0 libisccc30 libisccfg30 liblcms1 libldap-2.4-2 liblwres30 
  libnm-glib0 libnm-util0 libntfs-3g23 libperl5.8 libpurple0 libsnmp-base 
  libsnmp15 libssl0.9.8 linux-generic linux-headers-generic 
  linux-image-generic linux-restricted-modules-generic login mount 
  myspell-en-gb myspell-en-us myspell-en-za nautilus-share network-manager 
  ntfs-3g ntp ntpdate nvidia-glx-new openoffice.org-help-en-gb 
  openoffice.org-help-en-us openoffice.org-l10n-common 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
  openoffice.org-thesaurus-en-us openssl passwd perl perl-base perl-modules 
  pidgin pidgin-data python-apt python-gobject rdesktop readahead ssl-cert 
  thunderbird tomboy transmission-common transmission-gtk ubuntu-docs ufw 
  util-linux util-linux-locales vim-common vim-tiny vinagre w32codecs wine 
  xserver-xorg-video-amd xserver-xorg-video-ati xserver-xorg-video-geode 
  xserver-xorg-video-intel xterm xulrunner-1.9 xulrunner-1.9-gnome-support 
Se instalarán los siguiente paquetes NUEVOS:
  libflac++6 
0 paquetes actualizados, 2 nuevos instalados, 0 para eliminar y 139 sin actualizar.
Necesito descargar 3573kB de ficheros. Después de desempaquetar se usarán 10,5MB.
No se satisfacen las dependencias de los siguientes paquetes:
  audacity: Depende: libasound2 (> 1.0.17) pero está instalado 1.0.15-3ubuntu4.
            Depende: libgtk2.0-0 (>= 2.14.1) pero está instalado 2.12.9-3ubuntu5.
            Depende: libmad0 (>= 0.15.1b-3) pero está instalado 0.15.1b-2.1ubuntu1.
            Depende: libsoundtouch1c2 (>= 1.3.1) pero está instalado 1.3.0-2.2ubuntu0.1.
            Depende: libwxbase2.8-0 (>= 2.8.8.0) pero no es instalable
            Depende: libwxgtk2.8-0 (>= 2.8.8.0) pero no es instalable
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Mantener los paquetes siguientes en la versión actual:
audacity [Sin instalar]

La puntuación es -9881

¿Acepta esta solución? [Y/n/q/?] Y
Los siguientes paquetes han sido retenidos automáticamente:
  libavcodec1d libavformat1d libavutil1d libpostproc1d linux-libc-dev 
  linux-restricted-modules-common openoffice.org-help-es 
  openoffice.org-l10n-es 
Se han retenido los siguientes paquetes:
  acpi-support acpid app-install-data-commercial avahi-autoipd avahi-daemon 
  base-files bind9-host brasero bsdutils compiz-fusion-plugins-main 
  console-setup cupsys cupsys-bsd cupsys-client cupsys-common dnsutils 
  evolution-data-server evolution-data-server-common firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gimp gimp-data 
  gimp-gnomevfs gimp-python gksu gnome-power-manager grub guidance-backends 
  hal-info initramfs-tools jockey-common jockey-gtk language-pack-en 
  language-pack-en-base language-pack-es language-pack-es-base 
  language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-es 
  language-pack-gnome-es-base libavahi-client3 libavahi-common-data 
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 
  libavahi-ui0 libbind9-30 libcamel1.2-11 libcupsimage2 libcupsys2 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libgadu3 libgdata-google1.2-1 libgdata1.2-1 
  libgimp2.0 libisccc30 libisccfg30 liblcms1 libldap-2.4-2 liblwres30 
  libnm-glib0 libnm-util0 libntfs-3g23 libperl5.8 libpurple0 libsnmp-base 
  libsnmp15 libssl0.9.8 linux-generic linux-headers-generic 
  linux-image-generic linux-restricted-modules-generic login mount 
  myspell-en-gb myspell-en-us myspell-en-za nautilus-share network-manager 
  ntfs-3g ntp ntpdate nvidia-glx-new openoffice.org-help-en-gb 
  openoffice.org-help-en-us openoffice.org-l10n-common 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
  openoffice.org-thesaurus-en-us openssl passwd perl perl-base perl-modules 
  pidgin pidgin-data python-apt python-gobject rdesktop readahead ssl-cert 
  thunderbird tomboy transmission-common transmission-gtk ubuntu-docs ufw 
  util-linux util-linux-locales vim-common vim-tiny vinagre w32codecs wine 
  xserver-xorg-video-amd xserver-xorg-video-ati xserver-xorg-video-geode 
  xserver-xorg-video-intel xterm xulrunner-1.9 xulrunner-1.9-gnome-support 
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 139 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
¿Quiere continuar? [Y/n/?] Y
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
newpc@ubuntu-newpc:~$ 

```

Si dsp hago un "sudo apt-get install audacity" vuelvo a tener el mismo error que antes...

Saludos.

---

### Post by Hei Ku on 2009-02-05
Tenés un problema de dependencias. Por alguna razón la versión de audacity que esta buscando instalar no tiene todas las dependencias en esos repositorios.

Entra a Synaptic, habilita todos los repos de update, back-port y demas, y proba de vuelta.

---

### Post by NickCis on 2009-02-05
> **Hei Ku said:**
> Tenés un problema de dependencias. Por alguna razón la versión de audacity que esta buscando instalar no tiene todas las dependencias en esos repositorios.

Entra a Synaptic, habilita todos los repos de update, back-port y demas, y proba de vuelta.

No se como hacer lo que me estas pidiendo, me podes explicar?

Saludos.

---

### Post by Hei Ku on 2009-02-05
Estuve viendo, y las dependencias del audacity que muestra no son las que muestra en el repositorio de universe de acuerdo a packages.ubuntu.com.

Tenes un solo repositorio que no es standard, asi que vamos a sacarlo temporariamente.

Abri una terminal:

```

sudo gedit /eta/apt/sources.list

```

Andate a la ultima fila, donde dice 
```
deb http://ubuntu.org.ua/ getdeb/
```
Ponele un # adelante.

Guarda y cerralo.

Ahora pone:

```

sudo aptitude update
sudo aptitude install audacity

```

Pone que errores te tira.

Ademas, tenes un monton de paquetes sin actualizar. Es por algo en particular?

---

### Post by NickCis on 2009-02-05
Problema solucionado, con comentar esa linea el audacity se pudo instalar y correr perfectamente.

> **Hei Ku said:**
> Ademas, tenes un monton de paquetes sin actualizar. Es por algo en particular?

No, no hay razon, es que estoy mal acostumbrado de windows a no actualizar las cosas (por haver tenido un SO pirata, que se muere si lo actualizas xD)Que me recomiendan actualizar?, como lo hago?, es conveniente hacerlo?, con que frecuencia?

Lo que si deseo es conservar la vercion 8.04 d ubuntu, no quiero pasar a la 8.10, la probe y tuve muchos problemas con sonido, video y demases, en esta Pc y otra. Por eso prefiero que darme con esta que ademas es LTS :D

Saludos.

---

### Post by Hei Ku on 2009-02-05
Bien! Alguna razon por la cual habias agregado ese repositorio?

En cuanto a las actualizaciones, te recomiendo que lo hagas. No te va a cambiar la version, pero sí te va a meter parches de seguridad y demas que son necesarios.

Ya que te acostumbraste a la terminal:

```

sudo aptitude dist-upgrade

```

Y con eso te va a bajar e instalar. Despues reinicia y listo. Lo de reiniciar es porque hay un cambio de kernel, que es uno de los pocos casos en que se justifica el reinicio.

---

### Post by NickCis on 2009-02-05
Ahi lo estoy haciendo, gracias por dar soluciones tan rapidas :P.

Con que frecuencia debo ejecutar ese comando?, o cada vez que sepa de alguna actualizacion? (como me fijo si hay alguna actualizacion, meparece que desactive ese icono en la bandeja que te decia,,, xD)...

Saludos.

---

### Post by Hei Ku on 2009-02-05
Yo lo hago manualmente cada semana, pero creo que en Synaptic podes ponerle que se fije regularmente si hay actualizaciones y te avise.

---


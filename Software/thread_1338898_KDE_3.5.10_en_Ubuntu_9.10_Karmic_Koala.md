---
title: "KDE 3.5.10 en Ubuntu 9.10 Karmic Koala"
date: 2009-11-26
forum: Software
---

### Post by emiliano_raso on 2009-11-26
Hola muchachos, quisiera saber como instalar KDE 3.5.10 en Ubuntu 9.10 Karmic Koala.
Utilizé el mismo procedimiento que está en el foro para instalarlo en 9.04 pero no funcionó.

Saludos.

---

### Post by emiliano_raso on 2009-11-27
Aca les pongo lo que me dice la consola.

```
emiliano@emiliano-laptop:~$ sudo aptitude install kubuntu-desktop-kde3
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Los siguientes paquetes están ROTOS:
  adept-batch-kde3 adept-installer-kde3 adept-manager-kde3 adept-notifier-kde3 adept-updater-kde3 kcontrol-kde3 kde-guidance-kde3 
  kdegraphics-kfile-plugins-kde3 kdelibs-data-kde3 kdelibs4c2a-kde3 kipi-plugins-kde3 kubuntu-desktop-kde3 libarts1-akode-kde3 libavcodec-extra-52 
Se instalarán los siguiente paquetes NUEVOS:
  adept-common-kde3{a} adept-kde3 akregator-kde3{a} amarok-common-kde3{a} amarok-engine-xine-kde3{a} amarok-kde3 ark-kde3 cryptsetup{a} debtags{a} 
  digikam-kde3 gnupg-agent{a} gpgsm{a} gtk2-engines-qtcurve{a} guidance-backends-kde3{a} gwenview-kde3 k3b-data-kde3{a} k3b-kde3{a} kaddressbook-kde3{a} 
  kaffeine-kde3 kamera-kde3{a} kappfinder-kde3{a} karm-kde3 katapult-kde3 kate-kde3{a} kbstate-kde3 kcron-kde3 kde-guidance-powermanager-kde3 
  kde-style-qtcurve{a} kde-style-qtcurve-kde3 kde-systemsettings-kde3 kdeadmin-kfile-plugins-kde3 kdebase-data-kde3{a} kdebase-kde3{a} 
  kdebase-kde3-bin{a} kdebase-kio-plugins-kde3 kdebase-runtime-data-common-kde3{a} kdemultimedia-kfile-plugins-kde3 kdemultimedia-kio-plugins-kde3{a} 
  kdenetwork-filesharing-kde3 kdenetwork-kfile-plugins-kde3 kdepasswd-kde3 kdepim-kio-plugins-kde3{a} kdepim-kresources-kde3{a} kdepim-wizards-kde3 
  kdeprint-kde3 kdesktop-kde3{a} kdesudo-kde3{a} kdm{a} kdm-kde3 kdnssd-kde3 keep-kde3 kfind-kde3{a} kghostview-kde3 khelpcenter-kde3 kicker-kde3{a} 
  kio-apt-kde3 kio-locate-kde3 kio-umountwrapper-kde3 klipper-kde3{a} kmag-kde3 kmail-kde3{a} kmailcvt-kde3 kmenuedit-kde3 kmilo-kde3 kmix-kde3 
  kmousetool-kde3 kmplayer-base-kde3{a} kmplayer-konq-plugins-kde3 knetworkconf-kde3 knode-kde3{a} knotes-kde3 konq-plugins-kde3 konqueror-kde3{a} 
  konqueror-nsplugins-kde3{a} konsole-kde3 kontact-kde3 konversation-kde3 kooka-kde3{a} kopete-kde3 korganizer-kde3{a} kpager-kde3{a} kpdf-kde3 
  kpersonalizer-kde3{a} kpf-kde3 kpilot-kde3{a} kppp-kde3 krdc-kde3 kregexpeditor-kde3{a} krfb-kde3 kscreensaver-kde3 kscreensaver-xsavers-kde3{a} 
  ksmserver-kde3 ksnapshot-kde3 ksplash-engine-moodin-kde3 ksplash-kde3{a} ksvg-kde3 ksysguard-kde3{a} ksysguardd-kde3{a} ksystemlog-kde3 ktip-kde3{a} 
  ktorrent-kde3 kvkbd-kde3 kwalletmanager-kde3 kwin-kde3{a} kwin-style-crystal-kde3 kwin-style-qtcurve{a} libavcodec52{a} libdbus-1-qt3{a} 
  libdbus-qt-1-1c2{a} libexiv2-4{a} libflac++6{a} libjpeg-progs{a} libk3b3-extracodecs-kde3{a} libk3b3-kde3{a} libkcal2b-kde3{a} libkcddb1-kde3{a} 
  libkdcraw3-kde3{a} libkdecorations4{a} libkdepim1a-kde3{a} libkexiv2-3-kde3{a} libkipi0-kde3{a} libkleopatra1-kde3{a} libkmime2-kde3{a} 
  libkonq4-kde3{a} libkpimexchange1-kde3{a} libkpimidentities1-kde3{a} libksba8{a} libkscan1-kde3{a} libksieve0-kde3{a} libktnef1-kde3{a} 
  libmimelib1c2a-kde3{a} libmpg123-0{a} libpoppler-qt2{a} librsync1{a} mpg123{a} ncompress{a} network-manager-kde-kde3 networkstatus-kde3 ocrad{a} 
  perl-suid{a} pmount{a} poster{a} postfix{a} procmail{a} psutils{a} pykdeextensions-kde3{a} python-kde3-kde3{a} python-pylibacl{a} python-pyxattr{a} 
  python-qt3{a} python2.6-dev{a} rdiff-backup{a} zoo{a} 
0 paquetes actualizados, 166 nuevos instalados, 0 para eliminar y 1 sin actualizar.
Necesito descargar 162MB/174MB de archivos. Después de desempaquetar se usarán 513MB.
No se satisfacen las dependencias de los siguientes paquetes:
  kcontrol-kde3: Depende: libraw1394-8 que es un paquete virtual.
  kde-guidance-kde3: Depende: libpythonize0 (>= 0.4.0-6) que es un paquete virtual.
  libarts1-akode-kde3: Depende: libakode2 (>= 2-rc1-1) que es un paquete virtual.
  adept-batch-kde3: Depende: libapt-pkg-libc6.9-6-4.7 que es un paquete virtual.
  adept-updater-kde3: Depende: libapt-pkg-libc6.9-6-4.7 que es un paquete virtual.
  kipi-plugins-kde3: Depende: libgpod3-nogtk (>= 0.6.0) que es un paquete virtual. o
                              libgpod3 (>= 0.6.0) que es un paquete virtual.
  libavcodec-extra-52: Entra en conflicto: libavcodec52 pero se va a instalar 4:0.5+svn20090706-2ubuntu2.
  adept-notifier-kde3: Depende: libapt-pkg-libc6.9-6-4.7 que es un paquete virtual.
  kdelibs4c2a-kde3: Depende: libkrb53 (>= 1.6.dfsg.2) que es un paquete virtual.
  kubuntu-desktop-kde3: Depende: hotkey-setup que es un paquete virtual.
                        Depende: ttf-bitstream-vera que es un paquete virtual.
  adept-manager-kde3: Depende: libapt-pkg-libc6.9-6-4.7 que es un paquete virtual.
  kdelibs-data-kde3: Entra en conflicto: kdelibs-data (< 4:4.0) pero está instalado 4:3.5.10.dfsg.1-2ubuntu7.
  kdegraphics-kfile-plugins-kde3: Depende: libpoppler4 que es un paquete virtual.
  adept-installer-kde3: Depende: libapt-pkg-libc6.9-6-4.7 que es un paquete virtual.
Las acciones siguientes resolverán estas dependencias

Mantener los paquetes siguientes en la versión actual:
adept-batch-kde3 [Sin instalar]
adept-common-kde3 [Sin instalar]
adept-installer-kde3 [Sin instalar]
adept-kde3 [Sin instalar]
adept-manager-kde3 [Sin instalar]
adept-notifier-kde3 [Sin instalar]
adept-updater-kde3 [Sin instalar]
akregator-kde3 [Sin instalar]
amarok-engine-xine-kde3 [Sin instalar]
amarok-kde3 [Sin instalar]
ark-kde3 [Sin instalar]
digikam-kde3 [Sin instalar]
gwenview-kde3 [Sin instalar]
k3b-kde3 [Sin instalar]
kaddressbook-kde3 [Sin instalar]
kaffeine-kde3 [Sin instalar]
kamera-kde3 [Sin instalar]
kappfinder-kde3 [Sin instalar]
karm-kde3 [Sin instalar]
katapult-kde3 [Sin instalar]
kate-kde3 [Sin instalar]
kbstate-kde3 [Sin instalar]
kcontrol-kde3 [Sin instalar]
kcron-kde3 [Sin instalar]
kde-guidance-kde3 [Sin instalar]
kde-guidance-powermanager-kde3 [Sin instalar]
kde-style-qtcurve-kde3 [Sin instalar]
kde-systemsettings-kde3 [Sin instalar]
kdeadmin-kfile-plugins-kde3 [Sin instalar]
kdebase-kde3 [Sin instalar]
kdebase-kde3-bin [Sin instalar]
kdebase-kio-plugins-kde3 [Sin instalar]
kdebase-runtime-data-common-kde3 [Sin instalar]
kdegraphics-kfile-plugins-kde3 [Sin instalar]
kdelibs-data-kde3 [Sin instalar]
kdelibs4c2a-kde3 [Sin instalar]
kdemultimedia-kfile-plugins-kde3 [Sin instalar]
kdemultimedia-kio-plugins-kde3 [Sin instalar]
kdenetwork-filesharing-kde3 [Sin instalar]
kdenetwork-kfile-plugins-kde3 [Sin instalar]
kdepasswd-kde3 [Sin instalar]
kdepim-kio-plugins-kde3 [Sin instalar]
kdepim-kresources-kde3 [Sin instalar]
kdepim-wizards-kde3 [Sin instalar]
kdeprint-kde3 [Sin instalar]
kdesktop-kde3 [Sin instalar]
kdesudo-kde3 [Sin instalar]
kdm-kde3 [Sin instalar]
kdnssd-kde3 [Sin instalar]
keep-kde3 [Sin instalar]
kfind-kde3 [Sin instalar]
kghostview-kde3 [Sin instalar]
khelpcenter-kde3 [Sin instalar]
kicker-kde3 [Sin instalar]
kio-apt-kde3 [Sin instalar]
kio-locate-kde3 [Sin instalar]
kio-umountwrapper-kde3 [Sin instalar]
kipi-plugins-kde3 [Sin instalar]
klipper-kde3 [Sin instalar]
kmag-kde3 [Sin instalar]
kmail-kde3 [Sin instalar]
kmailcvt-kde3 [Sin instalar]
kmenuedit-kde3 [Sin instalar]
kmilo-kde3 [Sin instalar]
kmix-kde3 [Sin instalar]
kmousetool-kde3 [Sin instalar]
kmplayer-base-kde3 [Sin instalar]
kmplayer-konq-plugins-kde3 [Sin instalar]
knetworkconf-kde3 [Sin instalar]
knode-kde3 [Sin instalar]
knotes-kde3 [Sin instalar]
konq-plugins-kde3 [Sin instalar]
konqueror-kde3 [Sin instalar]
konqueror-nsplugins-kde3 [Sin instalar]
konsole-kde3 [Sin instalar]
kontact-kde3 [Sin instalar]
konversation-kde3 [Sin instalar]
kooka-kde3 [Sin instalar]
kopete-kde3 [Sin instalar]
korganizer-kde3 [Sin instalar]
kpager-kde3 [Sin instalar]
kpdf-kde3 [Sin instalar]
kpersonalizer-kde3 [Sin instalar]
kpf-kde3 [Sin instalar]
kpilot-kde3 [Sin instalar]
kppp-kde3 [Sin instalar]
krdc-kde3 [Sin instalar]
kregexpeditor-kde3 [Sin instalar]
krfb-kde3 [Sin instalar]
kscreensaver-kde3 [Sin instalar]
kscreensaver-xsavers-kde3 [Sin instalar]
ksmserver-kde3 [Sin instalar]
ksnapshot-kde3 [Sin instalar]
ksplash-engine-moodin-kde3 [Sin instalar]
ksplash-kde3 [Sin instalar]
ksvg-kde3 [Sin instalar]
ksysguard-kde3 [Sin instalar]
ksystemlog-kde3 [Sin instalar]
ktip-kde3 [Sin instalar]
ktorrent-kde3 [Sin instalar]
kubuntu-desktop-kde3 [Sin instalar]
kvkbd-kde3 [Sin instalar]
kwalletmanager-kde3 [Sin instalar]
kwin-kde3 [Sin instalar]
kwin-style-crystal-kde3 [Sin instalar]
libarts1-akode-kde3 [Sin instalar]
libavcodec52 [Sin instalar]
libk3b3-extracodecs-kde3 [Sin instalar]
libk3b3-kde3 [Sin instalar]
libkcal2b-kde3 [Sin instalar]
libkcddb1-kde3 [Sin instalar]
libkdcraw3-kde3 [Sin instalar]
libkdepim1a-kde3 [Sin instalar]
libkexiv2-3-kde3 [Sin instalar]
libkipi0-kde3 [Sin instalar]
libkleopatra1-kde3 [Sin instalar]
libkmime2-kde3 [Sin instalar]
libkonq4-kde3 [Sin instalar]
libkpimexchange1-kde3 [Sin instalar]
libkpimidentities1-kde3 [Sin instalar]
libkscan1-kde3 [Sin instalar]
libksieve0-kde3 [Sin instalar]
libktnef1-kde3 [Sin instalar]
network-manager-kde-kde3 [Sin instalar]
networkstatus-kde3 [Sin instalar]
python-kde3-kde3 [Sin instalar]

Dejar las siguientes dependencias sin resolver:
amarok-common-kde3 recomienda amarok-kde3 (>= 2:1.4.10-0ubuntu5)
La puntuación es -5176

¿Acepta esta solución? [Y/n/q/?] y
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 1 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
¿Quiere continuar? [Y/n/?] y
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

emiliano@emiliano-laptop:~$ 

```

---

### Post by emiliano_raso on 2010-01-02
Ya encontré como hacerlo.

1) Ingresamos como root:
```
$ sudo su
```

2) Abrimos la lista de repositorios
```
# gedit /etc/apt/sources.list
```

3) Agregamos estas lineas al final:
```
deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main
```

4) Guardamos el archivo y en consola agregamos la Key:
```
# wget http://apt.pearsoncomputing.net/public.gpg -q -O- | sudo apt-key add -
```

5) Actualizamos completito como a mi me gusta:
```
# apt-get update && aptitude update && aptitude full-upgrade
```

6) Instalamos KDE3:
```
# aptitude install kubuntu-desktop-kde3
```

---

### Post by pol666 on 2010-01-02
Estás loco jajajaja

---

### Post by emiliano_raso on 2010-01-02
> **pol666 said:**
> Estás loco jajajaja

Porque?

---


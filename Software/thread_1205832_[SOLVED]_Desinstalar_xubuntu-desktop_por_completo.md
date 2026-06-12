---
title: "[SOLVED] Desinstalar xubuntu-desktop por completo"
date: 2009-07-06
forum: Software
---

### Post by Mauro22 on 2009-07-06
Hola!!


Hace rato desde hoy, estoy buscando como desinstalar por completo xubuntu-desktop...


Tengo gnome y una vez instalé xubuntu-desktop deste synaptic. Pero tambien instala programas propios de XFCE.

Ahora, al desinstalarlo (con remove o purge) sòlo borra xubuntu-desktop, no asi todo lo que instaló..


Hay alguna forma?? o algo que por lo menos me saqué los programas del menú porque tengo repetidos y mezclados.


):P
Gracia'!

---

### Post by Mauro22 on 2009-07-17
Aca esta:


Ubuntu 9.04 (Jaunty)

Eliminar Xubuntu y dejar 100% GNOME

```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```


Eliminar Kubuntu y dejar 100% GNOME

```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop
```



Sacado de [0]. Ahi tienen para otras versiones de Ubuntu.

**ATENCION: Este comando puede remover paquetes que necesites, si lo ves en la lista borralo de ahi, sino luego lo vas a tener que volver a instalar unicamente, ya que las preferencias estan en tu home.**

[0] [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Applelnx on 2009-07-17
Muy autodidacta ;)

Gracias por la info. Pregunta por curiosidad nomas: tengo Kubuntu, si pongo la segunda linea de comando lo unico que cambia es el entorno grafico? Se mantienen los archivos? Vi por ahi que se eliminan los programas nativos de KDE.

---

### Post by Mauro22 on 2009-07-17
Por lo que entiendo y lei en esa web, estos comandos te sirven para:


. Tener Gnome instalado como escritorio por defecto (Es decir, haber instalado Ubuntu) y luego instalaste KDE o XFCE y lo queres eliminar por completo y que te quede Gnome unicamente...


Porque si tenes Gnome e instalas otro DE, al borrarlo no se lleva los programas, te los deja...

Estos comando hacen esto, vuelven a un Gnome Puro...



Si tenes K o X -ubuntu, no se si es lo mejor, ya que borraria todo y despues instala un DE.



Borra un poco de más, pero queda muy limpio.. Por ejemplo, el K3b, el Vlc, etc eso vuela y hay que volverlo a instalar.







**Resumen: Solo sirve para volver a tener un gnome sin aplicaciones de X o K -ubuntu. NO AL REVES.**

---

### Post by Applelnx on 2009-07-18
Ok, gracias por la info

---


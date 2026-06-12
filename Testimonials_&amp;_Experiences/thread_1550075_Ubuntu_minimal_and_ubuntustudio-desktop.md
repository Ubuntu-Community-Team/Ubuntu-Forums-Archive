---
title: "Ubuntu minimal and ubuntustudio-desktop"
date: 2010-08-10
forum: Testimonials &amp; Experiences
---

### Post by uRock on 2010-08-10
Here is what I got when I installed ubuntustudio-desktop without installing ubuntu-desktop.

In the internet tab the only thing that came with the install was Firefox. I added the rest.

---

### Post by uRock on 2010-08-10
Running sudo apt-get install ubuntu-desktop returns this huge list of stuff that isn't installed with ubuntustudio-desktop.

```
ronnie@ubuntu:~$ sudo apt-get install ubuntu-desktop
[sudo] password for ronnie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adium-theme-ubuntu aisleriot aptdaemon at-spi binfmt-support branding-ubuntu brltty brltty-x11 cli-common couchdb-bin dcraw desktopcouch dnsmasq-base empathy empathy-common erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl espeak espeak-data evolution evolution-common evolution-couchdb evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal example-content f-spot gbrainy gnome-games-common gnome-mag gnome-mahjongg gnome-orca gnome-sudoku gnome-themes-ubuntu gnomine
  gstreamer0.10-gnonlin guile-1.8-libs gvfs-bin gwibber gwibber-service humanity-icon-theme imagemagick indicator-applet-session indicator-me indicator-session kerneloops-daemon libart2.0-cil
  libavahi-gobject0 libbrlapi0.5 libclutter-1.0-0 libclutter-gtk-0.10-0 libcolamd2.7.1 libcouchdb-glib-1.0-2 libcurl3 libdesktopcouch-glib-1.0-2 libdotconf1.0 libespeak1 libevent-1.4-2
  libexchange-storage1.2-3 libflickrnet2.2-cil libgail-common libgail-gnome-module libgconf2.0-cil libgd2-xpm libgdiplus libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime2.4-cil
  libgnome-keyring1.0-cil libgnome-mag2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome2.24-cil libgnomepanel2.24-cil libgoocanvas-common libgoocanvas3 libgpod-common libgpod4 libgraphite3 libgraphviz4
  libgtk-vnc-1.0-0 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libilmbase6 liblaunchpad-integration1.0-cil libloudmouth1-0 liblouis-data liblouis0
  liblpint-bonobo0 libmagickcore2-extra libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libmtp8
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls libnm-glib2 libnm-util1 libnunit2.4-cil libopenexr6 libpisock9 libpisync1 libportaudio2 libprotoc5 libpst4 libraptor1 librasqal2
  librdf0 libsctp1 libsdl1.2debian-pulseaudio libspeechd2 libsqlite0 libstlport4.6ldbl libtelepathy-farsight0 libubuntuone-1.0-1 libwmf0.2-7 libwmf0.2-7-gtk libwpd8c2a libwpg-0.1-1 libwps-0.1-1
  light-themes lksctp-tools lp-solve media-player-info mobile-broadband-provider-info modemmanager mono-2.0-gac mono-gac mono-runtime nautilus-sendto-empathy network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notify-osd notify-osd-icons onboard openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy openoffice.org-style-human
  openoffice.org-writer pitivi plymouth-theme-ubuntu-logo plymouth-x11 pm-utils-powersave-policy policykit-desktop-privileges pptp-linux protobuf-compiler python-aptdaemon python-aptdaemon-gtk
  python-avahi python-brlapi python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight
  python-gnomekeyring python-gtkspell python-indicate python-launchpad-integration python-louis python-mako python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl
  python-pygoocanvas python-pyinotify python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone
  python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python-virtkey python-wnck quadrapassel rdesktop rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screensaver-default-images simple-scan software-center speech-dispatcher syslinux telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle
  telepathy-mission-control-5 telepathy-salut tomboy transmission-common transmission-gtk tsclient ttf-kacst-one ttf-khmeros-core ttf-opensymbol ttf-punjabi-fonts ttf-takao-pgothic ttf-wqy-microhei
  ubuntu-artwork ubuntu-mono ubuntu-sounds ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome uno-libs3 ure usb-creator-common usb-creator-gtk vinagre xdg-user-dirs xdg-user-dirs-gtk
  xfonts-mathml
Suggested packages:
  brltty-speechd couchdb gphoto2 netpbm erlang-tools erlang erlang-manpages erlang-doc-html bug-buddy evolution-dbg evolution-plugins-experimental gnome-pilot-conduits evolution-exchange-dbg
  gwibber-themes imagemagick-doc transfig monodoc-gtk2.0-manual libgd-tools libgtkhtml3.14-dbg libmono-i18n2.0-cil libmono-winforms2.0-cil libnunit-doc monodoc-nunit-manual jpilot pilot-link kpilot
  gnome-pilot claws-mail sylpheed raptor-utils redland-utils librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite openoffice.org-base openoffice.org-style-industrial
  openoffice.org-style-hicontrast openoffice.org-style-tango openoffice.org-style-crystal openoffice.org-style-oxygen openoffice.org-evolution openoffice.org-java-common openoffice.org-gcj
  openoffice.org-filter-binfilter python-crypto-dbg python-egenix-mxdatetime-dbg python-egenix-mxtools-dbg python-egenix-mxtools-doc python-launchpad-integration-dbg python-beaker python-openssl-doc
  python-openssl-dbg python-pam-dbg libcurl4-gnutls-dev python-pycurl-dbg python-pyinotify-doc python-wxgtk2.8 python-wxgtk2.6 python-wxgtk python-twisted-bin-dbg python-tk python-qt3 python-profiler
  python-coherence rhythmbox-plugin-coherence speech-dispatcher-festival speech-dispatcher-doc-cs speech-dispatcher-flite python-libproxy tasque vnc-viewer xnest ttf-kacst cli-uno-bridge otf-stix
  ttf-lyx
The following packages will be REMOVED:
  libgd2-noxpm libsdl1.2debian-alsa
The following NEW packages will be installed:
  adium-theme-ubuntu aisleriot aptdaemon at-spi binfmt-support branding-ubuntu brltty brltty-x11 cli-common couchdb-bin dcraw desktopcouch dnsmasq-base empathy empathy-common erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl espeak espeak-data evolution evolution-common evolution-couchdb evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal example-content f-spot gbrainy gnome-games-common gnome-mag gnome-mahjongg gnome-orca gnome-sudoku gnome-themes-ubuntu gnomine
  gstreamer0.10-gnonlin guile-1.8-libs gvfs-bin gwibber gwibber-service humanity-icon-theme imagemagick indicator-applet-session indicator-me indicator-session kerneloops-daemon libart2.0-cil
  libavahi-gobject0 libbrlapi0.5 libclutter-1.0-0 libclutter-gtk-0.10-0 libcolamd2.7.1 libcouchdb-glib-1.0-2 libcurl3 libdesktopcouch-glib-1.0-2 libdotconf1.0 libespeak1 libevent-1.4-2
  libexchange-storage1.2-3 libflickrnet2.2-cil libgail-common libgail-gnome-module libgconf2.0-cil libgd2-xpm libgdiplus libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime2.4-cil
  libgnome-keyring1.0-cil libgnome-mag2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome2.24-cil libgnomepanel2.24-cil libgoocanvas-common libgoocanvas3 libgpod-common libgpod4 libgraphite3 libgraphviz4
  libgtk-vnc-1.0-0 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libilmbase6 liblaunchpad-integration1.0-cil libloudmouth1-0 liblouis-data liblouis0
  liblpint-bonobo0 libmagickcore2-extra libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libmtp8
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls libnm-glib2 libnm-util1 libnunit2.4-cil libopenexr6 libpisock9 libpisync1 libportaudio2 libprotoc5 libpst4 libraptor1 librasqal2
  librdf0 libsctp1 libsdl1.2debian-pulseaudio libspeechd2 libsqlite0 libstlport4.6ldbl libtelepathy-farsight0 libubuntuone-1.0-1 libwmf0.2-7 libwmf0.2-7-gtk libwpd8c2a libwpg-0.1-1 libwps-0.1-1
  light-themes lksctp-tools lp-solve media-player-info mobile-broadband-provider-info modemmanager mono-2.0-gac mono-gac mono-runtime nautilus-sendto-empathy network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notify-osd notify-osd-icons onboard openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy openoffice.org-style-human
  openoffice.org-writer pitivi plymouth-theme-ubuntu-logo plymouth-x11 pm-utils-powersave-policy policykit-desktop-privileges pptp-linux protobuf-compiler python-aptdaemon python-aptdaemon-gtk
  python-avahi python-brlapi python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight
  python-gnomekeyring python-gtkspell python-indicate python-launchpad-integration python-louis python-mako python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl
  python-pygoocanvas python-pyinotify python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone
  python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python-virtkey python-wnck quadrapassel rdesktop rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screensaver-default-images simple-scan software-center speech-dispatcher syslinux telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle
  telepathy-mission-control-5 telepathy-salut tomboy transmission-common transmission-gtk tsclient ttf-kacst-one ttf-khmeros-core ttf-opensymbol ttf-punjabi-fonts ttf-takao-pgothic ttf-wqy-microhei
  ubuntu-artwork ubuntu-desktop ubuntu-mono ubuntu-sounds ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome uno-libs3 ure usb-creator-common usb-creator-gtk vinagre xdg-user-dirs
  xdg-user-dirs-gtk xfonts-mathml
0 upgraded, 265 newly installed, 2 to remove and 0 not upgraded.
Need to get 157MB of archives.
After this operation, 660MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by snowpine on 2010-08-10
[http://packages.ubuntu.com/lucid/ubuntustudio-desktop](http://packages.ubuntu.com/lucid/ubuntustudio-desktop)
[http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop)

What is your actual question? ;)

---

### Post by uRock on 2010-08-10
> **snowpine said:**
> [http://packages.ubuntu.com/lucid/ubuntustudio-desktop](http://packages.ubuntu.com/lucid/ubuntustudio-desktop)
[http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop)

What is your actual question? ;)
None. Just showing the difference in case someone out there wants to skip the ubuntu-desktop install.

Thanks for offering.

---

### Post by snowpine on 2010-08-10
My bad; I didn't notice this was in Testimonials and Experiences, sorry for trying to turn it into a support thread. ;)

We now return to our regularly scheduled programming.

---

### Post by uRock on 2010-08-10
Lol, no problem. I just installed it to satisfy my boredom. It runs pretty fast when compared to some of my other vbox installs.

---


---
title: "Vmware on Gutsy Gibbon -- dependency problems"
date: 2008-05-24
forum: Virtualisation
---

### Post by amanjain on 2008-05-24
[COLOR="Blue"]Hi All,
 I was trying to install vmware-server on ubuntu gutsy gibbon.
 But after about 2-3 mins, I pressed CTRL+C to abort the process.
 Now whenever I try to install it again, I'm hit with the following dependency problems.[/COLOR]
/**************** LOGS **************************/
aman@ubox:~$ sudo apt-get install vmware-server
[sudo] password for aman:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome2-globalmenu-applet: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
  gtk2-engines-pixbuf: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
  gtk2.0-examples: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
  libgtk2.0-0: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
  libgtk2.0-dev: Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxinerama-dev but it is not going to be installed
                 Depends: libxi-dev but it is not going to be installed
                 Depends: libxrandr-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
                 Depends: libxcomposite-dev but it is not going to be installed
                 Depends: libxdamage-dev but it is not going to be installed
  vmware-server: Depends: xinetd but it is not going to be installed or
                          netkit-inetd or
                          inetd but it is not installable
                 Depends: vmware-server-kernel-modules but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
/**************************************************************/
[COLOR="Blue"]
So when I try apt-get -f install , I get a long list of packages, asking for removal, which I obviously don't want.
Now I am unable to install anything using apt-get[/COLOR]
/********************** apt-get -f install logs ***************/
aman@ubox:~$ sudo apt-get -f install 
[sudo] password for aman:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcommons-collections3-java libsm-dev libofx3 libgsf-gnome-1-114 guile-1.6 liblzo1 libcommons-pool-java libice-dev libgoffice-0-common
  x11proto-xext-dev libdc1394-13 libatk1.0-dev x11proto-kb-dev libglib2.0-dev liblucene-java libcrypt-ssleay-perl libcairo-jni libosp5 mplayer-skins
  libcommons-el-java x11proto-xinerama-dev fftw3 libpango1.0-dev junit x11proto-render-dev libregexp-java libcommons-modeler-java libxi-dev
  liblog4j1.2-java libxrender-dev libfinance-quote-perl mysql-common libcairo2-dev libxdmcp-dev libseda-java libcommons-cli-java libtomcat5.5-java
  libdvbpsi4 libavformat1d libxosd2 libfontconfig1-dev libmysqlclient15off x11proto-composite-dev xtrans-dev libbcel-java slib libcairo-java libvlc0
  libglib-jni x11proto-core-dev libxcursor-dev ant python-qt3 libcommons-launcher-java libcommons-logging-java vlc-nox libggi2 libbcprov-java
  x11proto-randr-dev python-sip4 x11proto-damage-dev libgii1 libhtml-tableextract-perl libwxbase2.6-0 icedax libxext-dev libxdamage-dev
  libcommons-dbcp-java libglib-java libtunepimp5 x11proto-input-dev libifp4 libfreetype6-dev libgii1-target-x x11proto-fixes-dev
  libcommons-collections-java libdate-manip-perl libdvdnav4 libxau-dev libcommons-beanutils-java libiso9660-4 libxcomposite-dev libxrandr-dev libexpat1-dev
  libcommons-digester-java libxft-dev libx11-dev libtar liblucene-java-doc libjsch-java libxfixes-dev libadns1 guile-1.6-slib mplayer-nogui ant-optional
  libxinerama-dev gnucash-common libvcdinfo0 libebml0 libsvncpp0c2a libmx4j-java libmatroska0 libnjb5 libofa0 wireshark-common libsdl-image1.2 libungif4g
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libglib2.0-dev libice-dev libpango1.0-dev libpng12-dev libsm-dev libx11-dev
  libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libglib2.0-doc libpango1.0-doc imagemagick
The following packages will be REMOVED:
  alacarte amarok amarok-xine apport-gtk apturl at-spi audacity azureus bluez-gnome brltty-x11 bug-buddy compiz compiz-gnome compiz-plugins
  contact-lookup-applet deskbar-applet displayconfig-gtk eclipse eclipse-jdt eclipse-pde eclipse-platform eclipse-rcp eclipse-source ekiga eog evince
  evolution evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-gnome-support
  firefox-gnome-support gcalctool gconf-editor gdebi gdesklets gdesklets-data gdm gedit gimp gimp-print gimp-python gksu gmountiso gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets gnome-apt gnome-btdownload gnome-control-center gnome-games gnome-icon-theme gnome-keyring
  gnome-keyring-manager gnome-mag gnome-media gnome-menus gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes
  gnome-user-guide gnome-utils gnome-volume-manager gnome2-globalmenu-applet gnomebaker gnucash gstreamer0.10-plugins-good gthumb gtk-gnutella gtk2-engines
  gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtk2.0-examples gtkhtml3.14 gucharmap hal-cups-utils hal-device-manager human-theme hwdb-client-gnome
  language-selector language-support-en libatspi1.0-0 libbonoboui2-0 libdeskbar-tracker libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-3
  libgail-common libgail-gnome-module libgail18 libgconf2.0-cil libgdl-1-0 libgdl-gnome-1-0 libgimp2.0 libgksu2-0 libgksuui1.0-1 libglade2-0
  libglade2.0-cil libgnome-desktop-2 libgnome-keyring0 libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomekbd1 libgnomekbdui1 libgnomeprintui2.2-0 libgnomeui-0 libgoffice-0-4 libgpod2 libgtk-java libgtk-jni libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtk2.0-dev libgtkhtml2-0 libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmm-2.4-1c2a libgtksourceview1.0-0
  libgtksourceview2.0-0 libgtkspell0 libgucharmap6 libgutenprintui2-1 liblaunchpad-integration0 liblpint-bonobo0 libmetacity0 libnautilus-burn4
  libnautilus-extension1 libnotify1 libpanel-applet2-0 libpoppler-glib2 librsvg2-2 librsvg2-common librsvg2.0-cil libsexy2 libswt3.2-gtk-java
  libswt3.2-gtk-jni libtotem-plparser7 libtracker-gtk0 libvte9 libwmf0.2-7 libwnck22 libwxgtk2.6-0 linuxdcpp metacity mozilla-firefox-locale-en-gb
  mozilla-mplayer multiget nautilus nautilus-cd-burner nautilus-sendto network-manager-gnome notification-daemon onboard openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-thesaurus-en-us openoffice.org-writer pidgin python-at-spi python-glade2 python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gtk2 python-gtkhtml2 python-launchpad-integration python-notify python-pygtksourceview python-sexy
  python-uno python-virtkey python-vte rapidsvn restricted-manager rhythmbox scim scim-gtk2-immodule scim-modules-table scim-tables-additional
  screensaver-default-images serpentine software-properties-gtk sound-juicer ssh-askpass-gnome synaptic system-config-printer tangerine-icon-theme
  thunderbird-locale-en-gb tomboy totem totem-gstreamer totem-mozilla tracker tracker-search-tool tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs
  update-manager update-notifier vim-gnome vino vlc wireshark xdg-user-dirs-gtk xsane xscreensaver-data xscreensaver-gl xulrunner-1.9 yelp zenity
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libglib2.0-dev libice-dev libpango1.0-dev libpng12-dev libsm-dev libx11-dev
  libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 35 newly installed, 251 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 12.5MB of archives.
After unpacking 974MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
/**************************************************************/

[COLOR="Blue"]Any help would be greatly appreciated, as I need to run WinXp inside Ubuntu.

TIA
Aman Jain
India[/COLOR]

---


---
title: "[SOLVED] Linux distributions with 5+ years support"
date: 2016-06-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Rooster2000 on 2016-06-06
I am searching a Linux distribution to replace my current Lubuntu 16.04 LTS. Basically I am happy with it on other aspects, but would like to get at least five-year support instead of three.

In five-year category there are some good alternatives, like Linux Mint (Xfce) and LXLE (LXDE). These would be also based on the *buntu -family that is somewhat familiar to me and would provide a light and simple desktop environment.

The only alternative in 5+ years category I have found so far is CentOS, which would have even 10 years support (7 yrs full + 3 yrs security). I would probably use Gnome desktop with it. That would be more resource hungry than Xfce and LXDE, but I guess I could consider it (and learning how to use Red Hat -based system) as a trade-off with longer update support.

Are there any other distributions that have a full (or security) support longer than five years? These distributions should be relatively easy to use.

---

### Post by QDR06VV9 on 2016-06-06
I do not know how credible this site is but have look here: [https://en.wikipedia.org/wiki/Long-term_support](https://en.wikipedia.org/wiki/Long-term_support)
I tend to stay with ubuntu-mate and Arch (Rolling) and debian now has a few rolling release's found here: [http://fixmynix.com/debian-rolling-release-distribution-list/](http://fixmynix.com/debian-rolling-release-distribution-list/)
Regards

---

### Post by Rooster2000 on 2016-06-06
I would not like to have a distribution with rolling releases, but rather a stabile LTS which will be supported for long time without any major changes.

The list you provided contains three Linux distributions (Ubuntu, Trisquel, Linux Mint), all of which are supported for five years.

---

### Post by QDR06VV9 on 2016-06-06
> The list you provided contains three Linux distributions (Ubuntu,  Trisquel, Linux Mint), all of which are supported for five years.
There may be one or two more that have have LTS support but there is no documentation on them ATM.
Just to inform Rolling release's have been very stable for myself and I have no intention of removing any of them. But I have an adventurous side to me that love's to see whats is always current
Kind Regards

---

### Post by ajgreeny on 2016-06-06
Just thinking aloud here, but does anyone know what the situation is if you install using the minimal install CD, then add, for example, xfce4 to get the xfce4 desktop; would that give you a system with 5 year support or would it be no different to installing Xubuntu, which of course uses the xfce4 desktop, but gives only 3 years support?

---

### Post by QDR06VV9 on 2016-06-06
I have always heard to be that the ubuntu base gets the 5 year support but the XFCE bits are only 3 years.
Trying to find a link to support this though. here it is.
> Let's clarify this. Traditionally Ubuntu proper  has a 5yr LTS and will do again for 16.04. Most other flavours only  apply for a 3yr LTS. 
  16.04 is our first properly official LTS and after some discussion  with members of the Ubuntu Technical Board, we've decided to follow what  most other flavours do which is a 3yr LTS. 
  What does this mean? We will support Ubuntu MATE 16.04 upto the  16.04.5 release. After that, the Ubuntu MATE bits won't get updates and  fixes but the underlying Ubuntu base will. &#65279;



Source [https://ubuntu-mate.community/t/why-can-t-we-get-5-years-support-for-16-04/5098/10](https://ubuntu-mate.community/t/why-can-t-we-get-5-years-support-for-16-04/5098/10)

---

### Post by mikodo on 2016-06-06
> **ajgreeny said:**
> Just thinking aloud here, but does anyone know what the situation is if you install using the minimal install CD, then add, for example, xfce4 to get the xfce4 desktop; would that give you a system with 5 year support or would it be no different to installing Xubuntu, which of course uses the xfce4 desktop, but gives only 3 years support?

I have always thought it would mean the same as personally choosing to run a Xubuntu LTS for five years. One would have the Ubuntu base supported but, would more and more loose Xubuntu library support. A lot of that happens anyways even during the official LTS support time-frame.

Isn't Kubuntu supported for 5 years in LTS. I cant remember.

My Xubuntu 14.01.1 support:


```
mikodo@mikodo:~$ ubuntu-support-status --show-all
Support status summary of 'mikodo':

You have 40 packages (2.3%) supported until February 2015 (9m)
You have 176 packages (10.0%) supported until May 2017 (3y)
You have 1484 packages (84.5%) supported until May 2019 (5y)

You have 0 packages (0.0%) that can not/no longer be downloaded
You have 56 packages (3.2%) that are unsupported

No longer downloadable:


Unsupported: 
backintime-common backintime-qt4 boot-repair boot-sav boot-sav-extra 
clamtk encfs fancontrol glade2script grub2 grub2-splashimages 
gstreamer1.0-plugins-ugly hplip-gui keepassx libdate-calc-perl 
libdate-calc-xs-perl librlog5 libsword-common libsword9 links links2 
linux-headers-3.13.0-85 linux-headers-3.13.0-85-generic 
linux-headers-3.13.0-86 linux-headers-3.13.0-86-generic 
linux-headers-3.13.0-87 linux-headers-3.13.0-87-generic 
linux-image-3.13.0-85-generic linux-image-3.13.0-86-generic 
linux-image-3.13.0-87-generic linux-image-extra-3.13.0-85-generic 
linux-image-extra-3.13.0-86-generic 
linux-image-extra-3.13.0-87-generic lm-sensors lxpolkit mbmon meld 
menu network-manager-openvpn network-manager-openvpn-gnome 
python-gtksourceview2 python3-keyring python3-secretstorage 
rdiff-backup sane smplayer smplayer-themes smplayer-translations 
smtube system-config-lvm xcalib xiphos xiphos-data xmbmon xsane 
xsane-common 

Supported until February 2015 (9m):
fuse-dbg libbasicusageenvironment0 libbit-vector-perl 
libboost-serialization1.54.0 libcarp-clan-perl libchromaprint0 
libcrystalhd3 libdirac-encoder0 libdvbpsi8 libebml4 libfuse-dev 
libgnutls28 libgroupsock1 libhogweed2 liblivemedia23 libmatroska6 
libpcre3-dev libpcrecpp0 libproxy-tools libreoffice-style-galaxy 
libresid-builder0c2a libselinux1-dev libsepol1-dev libsidplay1 
libsidplay2 libssh2-1 libtar0 libtsan0 libusageenvironment1 libvlc5 
libvlccore7 libzvbi-common libzvbi0 thunderbird-locale-en 
thunderbird-locale-en-us vlc vlc-data vlc-nox vlc-plugin-notify 
vlc-plugin-pulse 

Supported until May 2017 (3y):
apt-offline audacious audacious-plugins audacious-plugins-data 
blueman brltty-x11 catfish desktop-base espeak exo-utils gigolo 
gnome-desktop-data gnome-system-tools gnome-themes-standard 
gnome-themes-standard-data gnumeric gnumeric-common gnumeric-doc 
gstreamer1.0-libav gtk-theme-config gtk2-engines-pixbuf liba52-0.7.4 
libaacs0 libass4 libaudclient2 libaudcore1 libavcodec54 
libavresample1 libbinio1ldbl libbluray1 libbs2b0 libcairo-perl 
libcddb2 libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcue1 
libdc1394-22 libdca0 libdigest-crc-perl libdirectfb-1.2-9 libenca0 
libexo-1-0 libexo-common libexo-helpers libfaad2 libgarcon-1-0 
libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libglib-perl 
libgoffice-0.10-10 libgoffice-0.10-10-common libgsf-1-114 
libgsf-1-common libgstreamer-perl libgtk2-notify-perl libgtk2-perl 
libgtk2-trayicon-perl libgtkmathview0c2a libguess1 libintl-perl 
libkate1 libkeybinder0 liblink-grammar4 libmodplug1 libmowgli2 
libmp3lame0 libmpeg2-4 libmpg123-0 libnet-dbus-perl liboobs-1-5 
libots0 libpango-perl libpostproc52 libquvi-scripts libquvi7 
libschroedinger-1.0-0 libsidplayfp libtagc0 libthunarx-2-0 
libts-0.0-0 libtumbler-1-0 libtwolame0 libunique-1.0-0 libva-x11-1 
libva1 libwv-1.2-4 libx264-142 libxcb-xv0 libxfce4ui-1-0 
libxfce4ui-2-0 libxfce4ui-common libxfce4ui-utils libxfce4util-bin 
libxfce4util-common libxfce4util6 libxfcegui4-4 libxfconf-0-2 
libxml-twig-perl libxml-xpathengine-perl libxvidcore4 light-locker 
light-locker-settings lightdm-gtk-greeter 
link-grammar-dictionaries-en lxsession-data menulibre mousepad 
mplayer2 mugshot myspell-en-us orage parole pavucontrol pidgin 
pidgin-data pidgin-libnotify pidgin-otr plymouth-theme-xubuntu-logo 
plymouth-theme-xubuntu-text python-support python3-pexpect 
python3-psutil ristretto shimmer-themes synaptic 
system-tools-backends thunar thunar-archive-plugin thunar-data 
thunar-media-tags-plugin thunar-volman tsconf tumbler tumbler-common 
xbrlapi xchat xchat-common xchat-indicator xfburn xfce4-appfinder 
xfce4-cpugraph-plugin xfce4-dict xfce4-indicator-plugin 
xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes 
xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin 
xfce4-power-manager xfce4-power-manager-data 
xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session 
xfce4-settings xfce4-systemload-plugin xfce4-taskmanager 
xfce4-terminal xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin 
xfce4-whiskermenu-plugin xfce4-xkb-plugin xfconf xfdesktop4 
xfdesktop4-data xfwm4 xubuntu-artwork xubuntu-community-wallpapers 
xubuntu-default-settings xubuntu-desktop xubuntu-docs 
xubuntu-icon-theme xubuntu-wallpapers 

Supported until May 2019 (5y):
accountsservice acl acpi-support acpid adduser alsa-base alsa-utils 
anacron app-install-data app-install-data-partner apparmor apport 
apport-gtk apport-symptoms apt apt-transport-https apt-utils 
aptdaemon aptdaemon-data aspell aspell-en at-spi2-core avahi-autoipd 
avahi-daemon avahi-utils base-files base-passwd bash bash-completion 
bc bind9-host binutils bluez bluez-alsa bluez-cups brltty 
bsdmainutils bsdutils busybox-initramfs busybox-static bzip2 
ca-certificates clamav clamav-base clamav-freshclam colord 
command-not-found command-not-found-data compiz compiz-core 
compiz-gnome compiz-plugins-default console-setup coreutils cpio cpp 
cpp-4.8 cracklib-runtime crda cron cryptsetup cryptsetup-bin cups 
cups-browsed cups-bsd cups-client cups-common cups-core-drivers 
cups-daemon cups-filters cups-filters-core-drivers cups-ppdc 
cups-server-common dash dbus dbus-x11 dc dconf-gsettings-backend 
dconf-service debconf debconf-i18n debianutils desktop-file-utils 
dh-python dialog dictionaries-common diffstat diffutils dmidecode 
dmsetup dmz-cursor-theme dnsmasq-base dnsutils doc-base docbook-xml 
dosfstools dpkg e2fslibs e2fsprogs ecryptfs-utils ed efibootmgr eject 
enchant espeak-data ethtool evince evince-common 
evolution-data-server-common file file-roller findutils firefox 
firefox-locale-en fontconfig fontconfig-config fonts-dejavu-core 
fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one 
fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala 
fonts-lyx fonts-nanum fonts-opensymbol fonts-sil-abyssinica 
fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg 
fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari 
fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa 
fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist 
fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree 
foomatic-db-compressed-ppds friendly-recovery ftp fuse gawk gcc 
gcc-4.8 gcc-4.8-base gcc-4.9-base gcc-4.9-base:i386 gconf-service 
gconf-service-backend gconf2 gconf2-common gcr gdb gdisk genisoimage 
geoip-database gettext gettext-base ghostscript ghostscript-x gimp 
gimp-data gimp-help-common gimp-help-en gir1.2-appindicator3-0.1 
gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-freedesktop 
gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gmenu-3.0 
gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 
gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-notify-0.7 
gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-soup-2.4 
gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gksu 
glib-networking glib-networking-common glib-networking-services 
gnome-accessibility-themes gnome-calculator gnome-disk-utility 
gnome-icon-theme gnome-icon-theme-full gnome-icon-theme-symbolic 
gnome-keyring gnome-menus gnome-mines gnome-settings-daemon-schemas 
gnome-sudoku gnome-system-monitor gnome-user-guide gnomine gnupg 
gparted gpgv grep groff-base grub-common grub-gfxpayload-lists 
grub-pc grub-pc-bin grub2-common gsettings-desktop-schemas 
gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa 
gstreamer0.10-nice gstreamer0.10-plugins-base 
gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good 
gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x 
gstreamer1.0-plugins-base gstreamer1.0-plugins-good 
gstreamer1.0-pulseaudio gstreamer1.0-tools gstreamer1.0-x 
gtk2-engines-murrine gucharmap gvfs gvfs-backends gvfs-bin 
gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gzip hardening-includes 
hdparm hicolor-icon-theme hostname hplip hplip-data 
humanity-icon-theme ifupdown im-config indicator-application 
indicator-messages indicator-power indicator-sound info 
init-system-helpers initramfs-tools initramfs-tools-bin initscripts 
inputattach insserv install-info intltool-debian iproute iproute2 
iptables iputils-arping iputils-ping iputils-tracepath irqbalance 
isc-dhcp-client isc-dhcp-common iso-codes iw kbd kerneloops-daemon 
keyboard-configuration keyutils klibc-utils kmod krb5-locales 
language-pack-en language-pack-en-base language-pack-gnome-en 
language-pack-gnome-en-base language-selector-common 
language-selector-gnome laptop-detect less libaa1 libaccountsservice0 
libacl1 libamd2.3.1 libapparmor-perl libapparmor1 libappindicator1 
libappindicator3-1 libapt-inst1.5 libapt-pkg-perl libapt-pkg4.12 
libarchive-extract-perl libarchive-zip-perl libarchive13 libart-2.0-2 
libasan0 libasn1-8-heimdal libasound2 libasound2-data 
libasound2-plugins libaspell15 libasprintf-dev libasprintf0c2 
libasyncns0 libatasmart4 libatk-bridge2.0-0 libatk-bridge2.0-0:i386 
libatk1.0-0 libatk1.0-0:i386 libatk1.0-data libatkmm-1.6-1 libatomic1 
libatspi2.0-0 libatspi2.0-0:i386 libattr1 libaudio2 libaudit-common 
libaudit1 libauthen-sasl-perl libautodie-perl libavahi-client3 
libavahi-client3:i386 libavahi-common-data libavahi-common-data:i386 
libavahi-common3 libavahi-common3:i386 libavahi-core7 libavahi-glib1 
libavc1394-0 libavformat54 libavutil52 libbabl-0.1-0 libbind9-90 
libblas3 libblkid1 libbluetooth3 libbonobo2-0 libbonobo2-common 
libbonoboui2-0 libbonoboui2-common libboost-date-time1.54.0 
libboost-system1.54.0 libbrlapi0.6 libbsd0 libburn4 libbz2-1.0 
libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libc6:i386 libcaca0 
libcairo-gobject2 libcairo-gobject2:i386 libcairo2 libcairo2:i386 
libcairomm-1.0-1 libcamd2.3.1 libcamel-1.2-45 libcanberra-gtk3-0 
libcanberra-gtk3-module libcanberra0 libcap-ng0 libcap2 libcap2-bin 
libccolamd2.8.0 libcdio-cdda1 libcdio-paranoia1 libcdio13 
libcdparanoia0 libcgmanager0 libcgmanager0:i386 libcholmod2.1.2 
libclamav6 libclass-accessor-perl libclone-perl libcloog-isl4 
libclucene-contribs1 libclucene-core1 libclutter-1.0-0 
libclutter-1.0-common libclutter-gtk-1.0-0 libcmis-0.4-4 
libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord1 
libcolord1:i386 libcolorhug1 libcomerr2 libcomerr2:i386 
libcompizconfig0 libcrack2 libcroco3 libcrypt-passwdmd5-perl 
libcryptsetup4 libcups2 libcups2:i386 libcupscgi1 libcupsfilters1 
libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls 
libdaemon0 libdatrie1 libdatrie1:i386 libdb5.3 libdbus-1-3 
libdbus-1-3:i386 libdbus-glib-1-2 libdbusmenu-glib4 
libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdconf1 libdebconfclient0 
libdecoration0 libdee-1.0-4 libdevmapper-event1.02.1 
libdevmapper1.02.1 libdigest-hmac-perl libdjvulibre-text 
libdjvulibre21 libdns100 libdotconf0 libdpkg-perl libdrm-intel1 
libdrm-nouveau2 libdrm-radeon1 libdrm2 libdv4 libdvdnav4 libdvdread4 
libebook-contacts-1.2-0 libecryptfs0 libedataserver-1.2-18 libedit2 
libegl1-mesa libegl1-mesa-drivers libelf1 libelfg0 
libemail-valid-perl libenchant1c2a libencode-locale-perl libept1.4.12 
libespeak1 libestr0 libevdocument3-4 libevent-2.0-5 libevview3-3 
libexif12 libexpat1 libexpat1:i386 libexttextcat-2.0-0 
libexttextcat-data libfarstream-0.1-0 libffi6 libffi6:i386 
libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl 
libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl 
libfile-mimeinfo-perl libflac8 libfluidsynth1 libfont-afm-perl 
libfontconfig1 libfontconfig1:i386 libfontembed1 libfontenc1 
libframe6 libfreerdp1 libfreetype6 libfreetype6:i386 libfribidi0 
libfs6 libfuse2 libgail-3-0 libgail18 libgbm1 libgcc-4.8-dev libgcc1 
libgcc1:i386 libgck-1-0 libgconf-2-4 libgcr-3-common libgcr-base-3-1 
libgcr-ui-3-1 libgcrypt11 libgcrypt11:i386 libgd3 libgdbm3 
libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-0:i386 libgdk-pixbuf2.0-common 
libgegl-0.2-0 libgeis1 libgeoclue0 libgeoip1 libgettextpo-dev 
libgettextpo0 libgfortran3 libgif4 libgimp2.0 libgirepository-1.0-1 
libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglamor0 
libglapi-mesa libglib2.0-0 libglib2.0-0:i386 libglib2.0-bin 
libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmp10 
libgnome-bluetooth11 libgnome-keyring-common libgnome-keyring0 
libgnome-menu-3-0 libgnome2-0 libgnome2-bin libgnome2-common 
libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 
libgnomeui-common libgnomevfs2-0 libgnomevfs2-common 
libgnutls-openssl27 libgnutls26 libgnutls26:i386 libgomp1 
libgpg-error0 libgpg-error0:i386 libgphoto2-6 libgphoto2-l10n 
libgphoto2-port10 libgpm2 libgrail6 libgraphite2-3 
libgraphite2-3:i386 libgrip0 libgs9 libgs9-common libgsm1 
libgssapi-krb5-2 libgssapi-krb5-2:i386 libgssapi3-heimdal 
libgssdp-1.0-3 libgstreamer-plugins-base0.10-0 
libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 
libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-0:i386 
libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin 
libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common 
libgtkhtml-editor-4.0-0 libgtkmm-2.4-1c2a libgtkmm-3.0-1 
libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 
libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 
libgudev-1.0-0:i386 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2 
libgutenprint2 libgxps2 libharfbuzz-icu0 libharfbuzz0b 
libharfbuzz0b:i386 libhcrypto4-heimdal libheimbase1-heimdal 
libheimntlm0-heimdal libhpmud0 libhtml-form-perl libhtml-format-perl 
libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl 
libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl 
libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0 
libhx509-5-heimdal libhyphen0 libical1 libice6 libicu52 libidl-common 
libidl0 libidn11 libido3-0.1-0 libiec61883-0 libieee1284-3 
libijs-0.35 libilmbase6 libimobiledevice4 libindicator3-7 
libindicator7 libio-html-perl libio-pty-perl libio-socket-inet6-perl 
libio-socket-ssl-perl libio-string-perl libipc-run-perl 
libipc-system-simple-perl libisc95 libisccc90 libisccfg90 libisl10 
libiso9660-8 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 
libjasper1:i386 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 
libjbig0 libjbig0:i386 libjbig2dec0 libjpeg-turbo8 
libjpeg-turbo8:i386 libjpeg62 libjpeg8 libjpeg8:i386 libjs-jquery 
libjs-sphinxdoc libjs-underscore libjson-c2 libjson-glib-1.0-0 
libjson-glib-1.0-common libjson0 libjte1 libk5crypto3 
libk5crypto3:i386 libkeyutils1 libkeyutils1:i386 libklibc libkmod2 
libkpathsea6 libkrb5-26-heimdal libkrb5-3 libkrb5-3:i386 
libkrb5support0 libkrb5support0:i386 liblangtag-common liblangtag1 
liblapack3 liblcms1 liblcms2-2 liblcms2-2:i386 libldap-2.4-2 libldb1 
liblightdm-gobject-1-0 liblircclient0 liblist-moreutils-perl 
libllvm3.4 liblocale-gettext-perl liblockfile-bin liblockfile1 
liblog-message-simple-perl libloudmouth1-0 libltdl7 liblua5.2-0 
liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres90 liblzma5 
liblzma5:i386 liblzo2-2 libmad0 libmagic1 libmailtools-perl 
libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmetacity-private0a 
libmhash2 libminiupnpc8 libmm-glib0 libmms0 libmng2 libmnl0 
libmodule-pluggable-perl libmount1 libmpc3 libmpcdec6 libmpdec2 
libmpfr4 libmtdev1 libmtp-common libmtp-runtime libmtp9 
libmysqlclient18 libmythes-1.2-0 libnatpmp1 libnautilus-extension1a 
libncurses5 libncursesw5 libneon27-gnutls libnet-dns-perl 
libnet-domain-tld-perl libnet-http-perl libnet-ip-perl 
libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl 
libnetfilter-conntrack3 libnettle4 libnewt0.52 libnfnetlink0 
libnice10 libnih-dbus1 libnih-dbus1:i386 libnih1 libnih1:i386 
libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 
libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin 
libnotify4 libnspr4 libnss-mdns libnss3 libnss3-1d libnss3-nssdb 
libntdb1 libnuma1 libogg0 libopencore-amrnb0 libopencore-amrwb0 
libopenexr6 libopenjpeg2 libopenobex1 libopenvg1-mesa libopus0 
liborbit-2-0 liborbit2 liborc-0.4-0 libotr5 libp11-kit-gnome-keyring 
libp11-kit0 libp11-kit0:i386 libpackagekit-glib2-16 libpam-cap 
libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime 
libpam-systemd libpam0g libpango-1.0-0 libpango-1.0-0:i386 
libpango1.0-0 libpangocairo-1.0-0 libpangocairo-1.0-0:i386 
libpangoft2-1.0-0 libpangoft2-1.0-0:i386 libpangomm-1.4-1 
libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 
libparse-debianchangelog-perl libparted0debian1 libpcap0.8 libpci3 
libpciaccess0 libpcre3 libpcre3:i386 libpcsclite1 libperl5.18 
libperlio-gzip-perl libpipeline1 libpixman-1-0 libpixman-1-0:i386 
libpkcs11-helper1 libplist1 libplymouth2 libpng12-0 libpng12-0:i386 
libpod-latex-perl libpolkit-agent-1-0 libpolkit-agent-1-0:i386 
libpolkit-backend-1-0 libpolkit-gobject-1-0 
libpolkit-gobject-1-0:i386 libpoppler-glib8 libpoppler44 libpopt0 
libportaudio2 libprocps3 libprotobuf8 libproxy1 
libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin 
libpurple0 libpwquality-common libpwquality1 libpython-stdlib 
libpython2.7 libpython2.7-minimal libpython2.7-stdlib 
libpython3-stdlib libpython3.4 libpython3.4-minimal 
libpython3.4-stdlib libqmi-glib0 libqpdf13 libqt4-dbus 
libqt4-declarative libqt4-designer libqt4-help libqt4-network 
libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql 
libqt4-sql-mysql libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns 
libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4 
libquadmath0 libraptor2-0 librarian0 librasqal3 libraw1394-11 librdf0 
libreadline5 libreadline6 libreoffice-base-core libreoffice-common 
libreoffice-core libreoffice-help-en-us libreoffice-pdfimport 
libreoffice-writer libroken18-heimdal librsvg2-2 librsvg2-common 
librsync1 librtmp0 libsamplerate0 libsane libsane-common 
libsane-hpaio libsasl2-2 libsasl2-modules libsasl2-modules-db 
libsdl-image1.2 libsdl1.2debian libsecret-1-0 libsecret-1-0:i386 
libsecret-common libselinux1 libselinux1:i386 libsemanage-common 
libsemanage1 libsensors4 libsepol1 libsexy2 libshout3 
libsigc++-2.0-0c2a libsigsegv2 libslang2 libsm6 libsmbclient 
libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0 
libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 
libspeexdsp1 libspice-server1 libsqlite3-0 libss2 libssl1.0.0 
libstartup-notification0 libstdc++6 libsub-identify-perl 
libsub-name-perl libswscale2 libsystemd-daemon0 libsystemd-login0 
libsystemd-login0:i386 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 
libtasn1-6 libtasn1-6:i386 libtcl8.5 libtcl8.6 libtdb1 
libtelepathy-glib0 libterm-ui-perl libtevent0 libtext-charwidth-perl 
libtext-iconv-perl libtext-levenshtein-perl libtext-soundex-perl 
libtext-wrapi18n-perl libthai-data libthai0 libthai0:i386 libtheora0 
libtidy-0.99-0 libtie-ixhash-perl libtiff5 libtiff5:i386 
libtimedate-perl libtinfo5 libtk8.6 libtxc-dxtn-s2tc0 libudev1 
libudev1:i386 libudisks2-0 libudisks2-0:i386 libumfpack5.6.2 
libunistring0 libunity-protocol-private0 
libunity-scopes-json-def-desktop libunity9 libupnp6 libupower-glib1 
liburi-perl liburl-dispatcher1 libusb-0.1-4 libusb-1.0-0 libusbmuxd2 
libustr-1.0-1 libutempter0 libuuid-perl libuuid1 libv4l-0 
libv4lconvert0 libvcdinfo0 libvdpau1 libvisual-0.4-0 
libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 
libvpx1 libvte-2.90-9 libvte-2.90-common libvte-common libvte9 
libwavpack1 libwayland-client0 libwayland-client0:i386 
libwayland-cursor0 libwayland-cursor0:i386 libwayland-egl1-mesa 
libwayland-server0 libwbclient0 libwebkitgtk-1.0-0 
libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common 
libwebp5 libwebpmux1 libwhoopsie0 libwind0-heimdal libwmf0.2-7 
libwnck-3-0 libwnck-3-common libwnck-common libwnck22 libwpd-0.9-9 
libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwww-robotrules-perl 
libx11-6 libx11-6:i386 libx11-data libx11-xcb1 libx86-1 libxapian22 
libxatracker2 libxau6 libxau6:i386 libxaw7 libxcb-composite0 
libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-keysyms1 
libxcb-present0 libxcb-randr0 libxcb-render0 libxcb-render0:i386 
libxcb-shape0 libxcb-shm0 libxcb-shm0:i386 libxcb-sync1 libxcb-util0 
libxcb-xfixes0 libxcb1 libxcb1:i386 libxcomposite1 
libxcomposite1:i386 libxcursor1 libxcursor1:i386 libxdamage1 
libxdamage1:i386 libxdmcp6 libxdmcp6:i386 libxext6 libxext6:i386 
libxfixes3 libxfixes3:i386 libxfont1 libxft2 libxi6 libxi6:i386 
libxinerama1 libxinerama1:i386 libxkbcommon0 libxkbcommon0:i386 
libxkbfile1 libxklavier16 libxml-parser-perl libxml2 libxmu6 libxmuu1 
libxp6 libxpm4 libxrandr2 libxrandr2:i386 libxrender1 
libxrender1:i386 libxres1 libxshmfence1 libxslt1.1 libxss1 libxt6 
libxtables10 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 
libyajl2 libyaml-tiny-perl libyelp0 libzephyr4 lightdm lintian 
linux-firmware linux-generic linux-headers-generic 
linux-image-generic linux-libc-dev linux-sound-base locales 
lockfile-progs login logrotate lp-solve lsb-base lsb-release lshw 
lsof ltrace lvm2 make makedev man-db manpages manpages-dev mawk 
memtest86+ metacity-common mime-support mlocate 
mobile-broadband-provider-info modemmanager module-init-tools mount 
mountall mscompress mtr-tiny multiarch-support mysql-common nano 
nautilus-data ncurses-base ncurses-bin net-tools netbase 
netcat-openbsd network-manager network-manager-gnome 
network-manager-pptp network-manager-pptp-gnome ntfs-3g ntpdate 
obex-data-server onboard onboard-data oneconf oneconf-common 
openprinting-ppds openssh-client openssl openvpn os-prober p11-kit 
p11-kit-modules parted passwd pastebinit patch patchutils pciutils 
pcmciautils perl perl-base perl-modules pkg-config plymouth 
plymouth-label plymouth-theme-ubuntu-text pm-utils policykit-1 
policykit-1-gnome policykit-desktop-privileges poppler-data 
poppler-utils popularity-contest powermgmt-base ppp pppconfig 
pppoeconf pptp-linux printer-driver-c2esp printer-driver-foo2zjs 
printer-driver-foo2zjs-common printer-driver-gutenprint 
printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa 
printer-driver-postscript-hp printer-driver-ptouch 
printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix 
procps psmisc pulseaudio pulseaudio-module-x11 pulseaudio-utils 
python python-apt python-apt-common python-aptdaemon 
python-aptdaemon.gtk3widgets python-cairo python-chardet 
python-commandnotfound python-crypto python-cups python-cupshelpers 
python-dbus python-dbus-dev python-debian python-debtagshw 
python-defer python-dirspec python-gconf python-gdbm python-gi 
python-gi-cairo python-glade2 python-gnome2 python-gnomekeyring 
python-gobject python-gobject-2 python-gtk2 python-httplib2 
python-imaging python-ldb python-libxml2 python-lxml python-minimal 
python-notify python-ntdb python-oauthlib python-oneconf 
python-openssl python-pam python-pexpect python-pil 
python-piston-mini-client python-pkg-resources python-psutil 
python-pycurl python-pylibacl python-pyorbit python-pyxattr 
python-qt4 python-qt4-dbus python-renderpm python-reportlab 
python-reportlab-accel python-requests python-samba python-serial 
python-sip python-six python-smbc python-talloc python-tdb 
python-twisted-bin python-twisted-core python-twisted-web 
python-ubuntu-sso-client python-urllib3 python-xapian python-xdg 
python-zope.interface python2.7 python2.7-minimal python3 
python3-apport python3-apt python3-aptdaemon 
python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat 
python3-cairo python3-commandnotfound python3-crypto python3-dbus 
python3-dbus.mainloop.qt python3-defer python3-distupgrade 
python3-gdbm python3-gi python3-gi-cairo python3-httplib2 
python3-minimal python3-oauthlib python3-oneconf 
python3-piston-mini-client python3-pkg-resources 
python3-problem-report python3-pycurl python3-pyqt4 python3-sip 
python3-software-properties python3-uno python3-update-manager 
python3-xdg python3-xkit python3.4 python3.4-minimal qdbus qpdf 
qtchooser qtcore4-l10n rarian-compat readline-common resolvconf 
rfkill rsync rsyslog rtkit samba-common samba-common-bin samba-libs 
sane-utils sed sensible-utils session-migration sessioninstaller 
sgml-base sgml-data shared-mime-info simple-scan smbclient 
software-center-aptdaemon-plugins software-properties-common 
software-properties-gtk sound-theme-freedesktop speech-dispatcher 
speech-dispatcher-audio-plugins sshfs ssl-cert strace sudo 
syslinux-common system-config-printer-common 
system-config-printer-gnome system-config-printer-udev 
systemd-services systemd-shim sysv-rc sysvinit-utils t1utils tar tcl 
tcl8.5 tcl8.6 tcpd tcpdump telnet thunderbird time tk tk8.6 toshset 
transmission-common transmission-gtk ttf-indic-fonts-core 
ttf-punjabi-fonts ttf-ubuntu-font-family tzdata ubuntu-drivers-common 
ubuntu-extras-keyring ubuntu-keyring ubuntu-minimal 
ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk 
ubuntu-sso-client ubuntu-standard ucf udev udisks2 ufw 
unattended-upgrades uno-libs3 unzip update-inetd update-manager 
update-manager-core update-notifier update-notifier-common upower 
upstart ure ureadahead usb-modeswitch usb-modeswitch-data usbmuxd 
usbutils util-linux uuid-runtime vbetool vim-common vim-tiny 
wamerican watershed wbritish wget whiptail whois whoopsie 
wireless-regdb wireless-tools wpasupplicant x11-apps x11-common 
x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils 
x11-xserver-utils xauth xbitmaps xcursor-themes xdg-user-dirs 
xdg-user-dirs-gtk xdg-utils xfonts-base xfonts-encodings 
xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xkb-data 
xml-core xorg xorg-docs-core xserver-common xserver-xorg 
xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev 
xserver-xorg-input-mouse xserver-xorg-input-synaptics 
xserver-xorg-input-vmmouse xserver-xorg-input-wacom 
xserver-xorg-video-all xserver-xorg-video-ati 
xserver-xorg-video-cirrus xserver-xorg-video-fbdev 
xserver-xorg-video-glamoregl xserver-xorg-video-intel 
xserver-xorg-video-mach64 xserver-xorg-video-mga 
xserver-xorg-video-modesetting xserver-xorg-video-neomagic 
xserver-xorg-video-nouveau xserver-xorg-video-openchrome 
xserver-xorg-video-qxl xserver-xorg-video-r128 
xserver-xorg-video-radeon xserver-xorg-video-s3 
xserver-xorg-video-savage xserver-xorg-video-siliconmotion 
xserver-xorg-video-sis xserver-xorg-video-sisusb 
xserver-xorg-video-tdfx xserver-xorg-video-trident 
xserver-xorg-video-vesa xserver-xorg-video-vmware xterm 
xul-ext-ubufox xz-utils yelp yelp-xsl zenity zenity-common zip zlib1g 
zlib1g:i386 

mikodo@mikodo:~$ 
```

---

### Post by PaulW2U on 2016-06-06
> **mikodo said:**
> My Xubuntu 14.01.1 support:
ubuntu-support-status should no longer be used as it doesn't return accurate results.

See [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html)
and [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670)

---

### Post by mikodo on 2016-06-06
> **PaulW2U said:**
> ubuntu-support-status should no longer be used as it doesn't return accurate results.

See [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html)
and [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670)

Darn. I had read that before and forgot.

Thank you.

---

### Post by mastablasta on 2016-06-07
> **Rooster2000 said:**
> 
Are there any other distributions that have a full (or security) support longer than five years? These distributions should be relatively easy to use.

Scientific Linux (more aimed at desktop user than centos) : [SIZE=2]http://scientificlinuxforum.org/index.php?showtopic=17
[/SIZE]
Debian LTS ([SIZE=2]https://wiki.debian.org/LTS/)

no one says you have to stop using the system after period expires, it's just that there are no more security updates for it.[/SIZE]

---

### Post by buzzingrobot on 2016-06-07
CentOS is a sanctioned rebuild of Red Hat Enterprise Linux with all the Red Hat trademarks and branding replaced.  Scientific is the same without the relationship with Red Hat. It's important to note that these are not derivatives of Red Hat.  They are rebuilds of Red Hat source packages. With a few documented exceptions, RH's code is not modified.

CentOS 6.8 and CentOS 7.2 are currently available. 6.8 support ends in 2020.  It's a Gnome 2.28 desktop from 2010.   7.2 is on Gnome 3.14, and rumors say it will go to 3.18 on the Red Hat's next upgrade.  The initial release was in 2014, so add 10 years to that.

Red Hat does not target mainstream desktop users who want to keep pace with the latest application releases.  Before commiting to either release, decide if the applications available to you now will keep youi happy for the next several years because it's probably not going to be possible to upgrade them.

Red Hat also has a strict free software policy, so it doesn't include proprietary codecs, Flash, etc. Flash is available from Adobe, and some of the others are available from third-party repos.

---

### Post by mörgæs on 2016-06-08
Any operative system will benefit from a reinstall once in a while, especially a desktop. Supported or not I would not keep a system running for more than five years.

---

### Post by Rooster2000 on 2016-06-08
Thanks for the replies so far. I guess it is becoming more clear now. 
Basically there seems to be two groups of alternatives:
 

[LIST=1]
[*]Debian/Ubuntu -related distributions with 5 years support 
[*]RHEL -related distributions with 10 years support. 
[/LIST]

Here is a table of what I have collected of them so far:

[TABLE="class: grid, width: 750"]
[TR]
[TD][B]OS
[/B][/TD]
[TD]**Version**[/TD]
[TD]**Desktop***[/TD]
[TD]**Editions (bit)**[/TD]
[TD]**Support (yrs)****[/TD]
[TD]**Released**[/TD]
[TD]**End-of-life**[/TD]
[/TR]
[TR]
[TD]CentOS[/TD]
[TD]7.0[/TD]
[TD]GNOME[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]7+3[/TD]
[TD="align: center"]07.07.14[/TD]
[TD="align: center"]06-2024[/TD]
[/TR]
[TR]
[TD]Scientific Linux[/TD]
[TD]7[/TD]
[TD]GNOME[/TD]
[TD="align: center"]64[/TD]
[TD="align: center"]5+5[/TD]
[TD="align: center"]13.10.14[/TD]
[TD="align: center"]06-2024[/TD]
[/TR]
[TR]
[TD]Kubuntu[/TD]
[TD]16.04 LTS[/TD]
[TD]KDE[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]21.04.16[/TD]
[TD="align: center"]04-2021[/TD]
[/TR]
[TR]
[TD]Linux Mint[/TD]
[TD]18[/TD]
[TD]Xfce[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]05/07-2016[/TD]
[TD="align: center"]04-2021[/TD]
[/TR]
[TR]
[TD]Ubuntu[/TD]
[TD]16.04 LTS[/TD]
[TD]Unity[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]21.04.16[/TD]
[TD="align: center"]04-2021[/TD]
[/TR]
[TR]
[TD]Debian[/TD]
[TD]8.0[/TD]
[TD]LXDE[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]3+2[/TD]
[TD="align: center"]25.04.15[/TD]
[TD="align: center"]05-2020[/TD]
[/TR]
[TR]
[TD]LXLE[/TD]
[TD]14.04.3 LTS[/TD]
[TD]LXDE[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]30.08.15[/TD]
[TD="align: center"]04-2020[/TD]
[/TR]
[TR]
[TD]Trisquel Mini[/TD]
[TD]7.0 LTS[/TD]
[TD]LXDE[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]03.11.14[/TD]
[TD="align: center"]04-2019[/TD]
[/TR]
[TR]
[TD]Lubuntu[/TD]
[TD]16.04 LTS[/TD]
[TD]LXDE[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]3[/TD]
[TD="align: center"]21.04.16[/TD]
[TD="align: center"]04-2019[/TD]
[/TR]
[TR]
[TD]Ubuntu GNOME[/TD]
[TD]16.04 LTS[/TD]
[TD]GNOME[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]3[/TD]
[TD="align: center"]21.04.16[/TD]
[TD="align: center"]04-2019[/TD]
[/TR]
[TR]
[TD]Xubuntu[/TD]
[TD]16.04 LTS[/TD]
[TD]Xfce[/TD]
[TD="align: center"]32/64[/TD]
[TD="align: center"]3[/TD]
[TD="align: center"]21.04.16[/TD]
[TD="align: center"]04-2019[/TD]
[/TR]
[/TABLE]

[SIZE=1]**Edit 2016-06-09:** Changed LXLE 14.04.3 LTS End-of-life date from 04-2021 to 04-2020.[/SIZE]

*) Lightest desktop available is selected
**) Full support + possible maintenance/security updates

Based on a brief testing, looks like that these Ubuntu -based systems would have more of the applications I use ready as official packages, whereas at least CentOS seems to have less of them.

---

### Post by Rooster2000 on 2016-06-08
> **runrickus said:**
> But I have an adventurous side to me that love's to see whats is always current

I guess this side is very weak in me, or then it is just being repressed by the side that expects everything to remain stable, predictable, familiar and somewhat functional.

> **mikodo said:**
> Isn't Kubuntu supported for 5 years in LTS. I cant remember.

Yes it is.

> **mastablasta said:**
> [SIZE=2]no one says you have to stop using the system after period expires, it's just that there are no more security updates for it.[/SIZE]

True, but I suppose this is not very recommended, at least if one is going to have the system connected to internet and contain any kind of personal data.

---

### Post by mastablasta on 2016-06-09
if there was better backwards compatibility then this support period wouldn't be such an issue. Windows is descent at that and you can easilly install older version of software on new releases. manufacturers usually provide at least some sort of drivers (legacy or something) and they too support their hardware on windows longer. also the other way arround. ther eis no xservers upgrades and such that would mess up the legacy drivers (AMD).

---

### Post by montag dp on 2016-06-09
I don't think there's an official support length, but Slackware 13.0 has been supported since 2009:

[https://en.wikipedia.org/wiki/Slackware#Releases](https://en.wikipedia.org/wiki/Slackware#Releases)

Looking at the release and EOL dates, it seems to be anywhere from 5-10 years for a given release.

---

### Post by QDR06VV9 on 2016-06-09
> **Rooster2000 said:**
> I guess this side is very weak in me, or then it is just being repressed by the side that expects everything to remain stable, predictable, familiar and somewhat functional.

Oh don't get me wrong I am **very picky** with things being Snappy, Crisp, and work like they were Advertised...but once in blue moon I have to fiddle a bit, but not so much that it becomes a nuisance.:)
But the good or GREAT thing about Linux is the Choices we can make or have before us..:D
Kind Regards

---

### Post by Rooster2000 on 2016-06-10
Before making any conclusions considering available applications, is [Linux Packages Search - pkgs.org]("https://pkgs.org/") a reliable source to determine the content of repositories in those distributions included? I haven't been really able to find many distribution -related online package lists, especially not for CentOS or Scientific Linux. I just found a mention from [CentOS Help | Repos]("https://centoshelp.org/resources/repos/") according which:
  
>  You can have a look at the packages here: [http://dev.centos.org/centos/7/](http://dev.centos.org/centos/7/)

But that is just a directory list, and my knowledge lacks to determinate based on it what packages are included in which CentOS repository.

---

### Post by Rooster2000 on 2016-06-10
There seems to be this one third party repository for CentOS called [EPEL]("http://fedoraproject.org/wiki/EPEL") that has many of the applications I am using at the moment, but which are not included on CentOS core repositories. It is warned on the [CentOS Wiki - Repositories]("https://wiki.centos.org/AdditionalResources/Repositories") site that 

>  If you are considering using a 3rd Party Repository, then you should seriously consider how to prevent unintended 'updates' from these side archives from over-writing some core part of CentOS.

EPEL belongs anyway into so-called *Community Approved Repositories*, which are

> frequently recommended by the community, usually well maintained, and provide a substantial number of additional packages to CentOS. They are still not associated with CentOS, but are independent. The above warnings about updates and priorities should still be heeded!

Does anyone have any experience or knowledge about the stability effect of EPEL to CentOS 7 or Scientific Linux 7?

---

### Post by rosswmcgee on 2016-06-12
Five years is an eternity in technology, I would be itching to try something new way before then. I know people who are using linux distros way beyond 5 years and never upgraded. They lose

security updates that way, but who am I to talk I still use my samsung galaxy s3 with an added 7250 amah anker battery.

---

### Post by PaulW2U on 2016-06-12
> **rosswmcgee said:**
> Five years is an eternity in technology, I would be itching to try something new way before then.
Me too. But may be some want or need the full five years even though they may decide to upgrade before then?
> **rosswmcgee said:**
> ...I still use my samsung galaxy s3....
I recycled my S3 last week. I now use an S4  :)

---

### Post by kurt18947 on 2016-06-12
> **mörgæs said:**
> Any operative system will benefit from a reinstall once in a while, especially a desktop. Supported or not I would not keep a system running for more than five years.

Agreed. I don't find re-installing *buntu  onerous. Having a few simple scripts would make it even easier.

---

### Post by buzzingrobot on 2016-06-12
> **kurt18947 said:**
> Agreed. I don't find re-installing *buntu  onerous. Having a few simple scripts would make it even easier.


Enthusiasts and home users may do that, but enterprise customers would never consider it an option. They expect software that gets installed and then just works forever, like the plumbing.

---

### Post by Rooster2000 on 2016-06-14
> **montag dp said:**
> I don't think there's an official support length, but Slackware 13.0 has been supported since 2009:

[https://en.wikipedia.org/wiki/Slackware#Releases](https://en.wikipedia.org/wiki/Slackware#Releases)

Looking at the release and EOL dates, it seems to be anywhere from 5-10 years for a given release.

Slackware seems to have quite long support length indeed, although I slightly dislike the fact that it is not clearly set. But it is said in the [Slackware Wikipedia site]("https://en.wikipedia.org/wiki/Slackware") that

> Slackware is considered to be most suitable for advanced and technically inclined Linux users.

I am not sure if I belong into that category, as I have doubts with CentOS / Scientific Linux already.

---

### Post by buzzingrobot on 2016-06-14
I used Slackware back in the middle ages when dependency resolvers weren't around and neither were package managers. Linux was steam-powered back then.  Just tar archives of source and a compiler. You got to build your software and then identify and chase down and build the dependencies. Pre-interrnet.  On dial-up.  Yay.

Slackware has a package manager of sorts now, but still no dependency resolver. It's been managed and nurtured by one individual, with the assistance of some dedicated helpers, for a very long time.  No release schedule exists. There is, instead, a development branch called slackware-current. At some point when the winds are just right, that's where the next official release will emerge.  The current non-development release dates from 2013.

I'd argue that Slackware is more hands on and old school than anything besides Linux From Scratch. But, getting into it can have a steep learning curve.

---

### Post by yoshii on 2016-06-15
It seems like any of the more popular distros that are fairly old yet still currently maintained and supported are safe bets even if the support isn't officially 5+ years.  
Take a look at [http://distrowatch.org](http://distrowatch.org) to get the details.  Right now the Ubuntu's (which are Debian-derived) and Debian seem like safe bets based upon the stats.  Also maybe Linux Mint (also based upon Ubuntu / Debian).  I would also avoid any of the distros which aren't freeware/opensource.  And any of the distros maintained by only one or two people aren't probably worth it even if they are really sophisticated.  The person could get hit by a car or married :D and that could be the end of the distro.

---

### Post by Rooster2000 on 2016-06-17
> **rosswmcgee said:**
> Five years is an eternity in technology, I would be itching to try something new way before then.
> **PaulW2U said:**
> Me too. But may be some want or need the full  five years even though they may decide to upgrade before then?

After learning that CentOS / Scientific has a support of 10 years, five started to sound like a good beginning :)

It's worth noticing though that in most cases you do not get the full five years for the same release, at least not in a long run. This assuming that you will upgrade into next LTS version of the same distribution. As most Debian / Ubuntu -related distros publish their LTS versions biennially, this will cut in practice one year of it's support either from the beginning or end of using the specific release. So one has to upgrade his system once every four years in a long run.

--

I guess this is getting more clear now after some research and testing.

 Xubuntu, Ubuntu GNOME and Lubuntu have too short support, only three years.
Ubuntu has Unity desktop that is not configurable enough to me.
 Kubuntu has KDE desktop I don't like for some reason. It is also quite resource hungry.
 Debian might be too technically inclined compared to it's competitors in the five-year support group.
 Trisquel Mini is a bit unfamiliar to me, and seems like a small distro.

So the candidates for the final round are CentOS / Scientific, Linux Mint and LXLE.

Basically, what qualifies CentOS / Scientific to the final round, is 10 years support. Other than that I don't like them so much. I dislike the basic setting of GNOME 3.x desktop and it is not easy to configure at all, but requries some tweaking and extensions installed. I have understood that this is part of the ideology in GNOME desktop though. There seem to be reasonably app selection in EPEL repository to cover most of my needs.

Linux Mint has maybe the best desktop (Xfce) to me. It is also relatively light, configurable and simple, and has almost all the apps available from repositories.

LXLE has pretty much the same advantages than Mint, except that I don't like the basic setting of the desktop. Luckily enough LXDE is easy to configure. It has basically all the apps available from repositories, as SeaMonkey is the default browser of it. This is something that is missing basically from all the other distros.

Anyway, I have to postpone for my final decision until the next versions of Mint (18) and LXLE (16.04?) are released later this  year.

---

### Post by kurt18947 on 2016-06-17
> **buzzingrobot said:**
> Enthusiasts and home users may do that, but enterprise customers would never consider it an option. They expect software that gets installed and then just works forever, like the plumbing.

Very true. A great many enterprises would hold that Windows XP was abandoned too soon [COLOR=#ffa500](given their investment in proprietary technology)[/COLOR]

---

### Post by mastablasta on 2016-06-17
> **Rooster2000 said:**
> .

Basically, what qualifies CentOS / Scientific to the final round, is 10 years support. Other than that I don't like them so much. I dislike the basic setting of GNOME 3.x desktop and it is not easy to configure at all, but requries some tweaking and extensions installed. I have understood that this is part of the ideology in GNOME desktop though. 

what's the problem? just install XFCE, KDE or LXDE or whatever desktop/windows manager you like. in one command line.

for example: [https://www.vultr.com/docs/installing-gnome-kde-gui-on-ubuntu-centos](https://www.vultr.com/docs/installing-gnome-kde-gui-on-ubuntu-centos)

---

### Post by buzzingrobot on 2016-06-18
> **mastablasta said:**
> what's the problem? just install XFCE, KDE or LXDE 

MATE and XFCE are installable on RHEL7/CentOS7 if the EPEL repo is added.  Cinnamon, as well. The distros ship with a pared-down version of KDE4.  AFAIK, LXDE is not available.

RHEL7/CentOS7 ship with Gnome 3.14. It defaults to a Gnome2-ish "classic"  look via use of extensions. That can be changed to standard Gnome Shell when you log in via the display manager. 

While the long support life time is nice, weighing against that will be the increasingly limited access to current software and our own personal inclination to keep the same setup around for years.

---

### Post by Rooster2000 on 2016-06-19
> **buzzingrobot said:**
> MATE and XFCE are installable on RHEL7/CentOS7 if the EPEL repo is added.

I kind of noticed this at some point, but didn't fully realize it, so thanks for reminding. I tried it briefly, but it seems that it would require some customizing (or some nice theme for it) and it doesn't include many basic tools as default, on top of minimum CentOS installation.

> **buzzingrobot said:**
>  While the long support life time is nice, weighing against that will be the increasingly limited access to current software and our own personal inclination to keep the same setup around for years.

I suppose I am getting into conclusion that I am not willing to take the effort necessary to get CentOS / Scientific running with Xfce. Despite it is possible, it's not an official desktop for it, but a third-party repository - even if approved by community. This added to limitations in software available, I'll probably stick with more familiar Linux Mint 18 when it is being released.

Thanks everyone for your comments. I noticed just now that as this sub-forum is not officially for support, there is no option to mark this thread as solved. Well, got to do it in old-fashion way :)

---

### Post by rewyllys on 2016-06-19
BTW, beta versions of Linux Mint 18, for both MATE and Cinnamon, were released on June 9.

I've been running the Cinnamon beta for the past week, and it has worked flawlessly for me.

---

### Post by montag dp on 2016-07-01
> **buzzingrobot said:**
> I used Slackware back in the middle ages when dependency resolvers weren't around and neither were package managers. Linux was steam-powered back then.  Just tar archives of source and a compiler. You got to build your software and then identify and chase down and build the dependencies. Pre-interrnet.  On dial-up.  Yay.

Slackware has a package manager of sorts now, but still no dependency resolver. It's been managed and nurtured by one individual, with the assistance of some dedicated helpers, for a very long time.  No release schedule exists. There is, instead, a development branch called slackware-current. At some point when the winds are just right, that's where the next official release will emerge.  The current non-development release dates from 2013.

I'd argue that Slackware is more hands on and old school than anything besides Linux From Scratch. But, getting into it can have a steep learning curve.[http://www.slackware.com/announce/14.2.php](http://www.slackware.com/announce/14.2.php)  :D

I know this thread is a little old and solved, but it's not everyday a new version of Slackware version is released.

About your comments, I agree that it is definitely hands-on and old-school (one of the reasons I like it).  I don't think it has as steep of a learning curve as, say, Arch or Gentoo, though.  The stable release model helps a lot with that, and the fact that you don't have to build everything from source like in Gentoo.

---

### Post by nargaroth_reg on 2016-07-15
> **mastablasta said:**
> what's the problem? just install XFCE, KDE or LXDE or whatever desktop/windows manager you like. in one command line.

for example: [https://www.vultr.com/docs/installing-gnome-kde-gui-on-ubuntu-centos](https://www.vultr.com/docs/installing-gnome-kde-gui-on-ubuntu-centos)
Anybody has tried centos with some or all of the community repositories enabled for a while and could tell us how it was? There's also this repository with desktop applications: [http://li.nux.ro/repos.html](http://li.nux.ro/repos.html)
I haven't tried installing the system, enabling them, installing software and using it for a long period yet.

---


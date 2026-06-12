---
title: "how to disable/uninstall plymouth"
date: 2010-07-08
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-08
On one of my server plymouth is consuming a lot of memory.I want to disable it.
I tried uninstalling but then it gave me a message like this
```

apt-get remove plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsmbclient libpolkit-backend-1-0 libplist1 aspell-en libxcb-aux0 libtalloc2 libcdio10 dnsmasq-base libgsf-1-common libxcb-atom1 python-debian libgail18
  libarchive1 libntfs10 unattended-upgrades libhal-storage1 libcdio-paranoia0 libwebkit-1.0-common libcupsimage2 gamin libgphoto2-port0 aspell usbmuxd libgudev-1.0-0
  libgnomecanvas2-0 hunspell-en-us libwmf0.2-7 libicu42 esound-clients libbonobo2-common libilmbase6 libsgutils2-2 gnome-mime-data libcairo-perl libgtk2-perl libaio1
  libimobiledevice0 seabios libproxy0 libbonobo2-0 libvte-common docbook-xml python-software-properties libx86-1 xauth libwbclient0 libavahi-glib1 apturl-common
  mtools libxmuu1 libsdl1.2debian-alsa libpango-perl libgamin0 librsvg2-common vbetool ethtool libxcb-event1 libindicator0 libaxis2c0 python-glade2 libvirt0 libgp11-0
  libgcr0 launchpad-integration libsdl1.2debian libhal1 python-xapian apt-xapian-index libxen3 libgraphviz4 libdbusmenu-glib1 libesd0 openssh-client libenchant1c2a
  libvpx0 vgabios python-vte libvte9 python-cairo libdbusmenu-gtk1 libopenexr6 libgsf-1-114 libgtop2-common librarian0 libopenobex1 rarian-compat
  libgnome2-canvas-perl vlan libidl0 libdjvulibre21 libglade2-0 libdevmapper-event1.02.1 esound-common libglib-perl xdg-utils libatasmart4 libgs8 libhunspell-1.2-0
  psfontmgr libgtop2-7 ntfsprogs libgstreamer-plugins-base0.10-0 libusbmuxd1 libappindicator0 libpciaccess0 libgnomeui-common synaptic libgnome-keyring0 smartdimmer
  liborbit2 ghostscript librsvg2-2 sgml-data librampart0 libpolkit-agent-1-0 libart-2.0-2 liblaunchpad-integration1 libcdio-cdda0 radeontool libgvfscommon0 hal-info
  dictionaries-common scrollkeeper libexif12 bridge-utils libdjvulibre-text libpaper-utils libbonoboui2-common libgstreamer0.10-0 libxv1 libjson-glib-1.0-0
  libpam-gnome-keyring gnome-icon-theme libusb-1.0-0 indicator-application python-gtk2 libaspell15 libbluetooth3 libgnomecanvas2-common libpaper1 libsoup2.4-1
  libgphoto2-2 qemu-common libaudiofile0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2 apache2-mpm-prefork apache2.2-common apparmor apparmor-utils apport apturl at avahi-daemon avahi-utils chromium-browser chromium-browser-inspector
  chromium-codecs-ffmpeg console-setup consolekit cron dbus dbus-x11 dmsetup e2fsprogs eucalyptus-common eucalyptus-gl eucalyptus-nc firefox firefox-branding fop
  friendly-recovery ftp gconf2 gconf2-common gksu gnome-keyring gsfonts-x11 gvfs gvfs-backends hal hostname ifupdown imagemagick initramfs-tools initscripts
  irqbalance kbd libapache2-mod-axis2c libapache2-mod-php5 libbonoboui2-0 libgconf2-4 libgdu0 libgksu2-0 libgnome2-0 libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libice6 libmagickcore2 libmagickcore2-extra libmagickwand2 libnss-mdns
  libpulse0 librpc-xml-perl libsm6 libsoup-gnome2.4-1 libstartup-notification0 libvirt-bin libwebkit-1.0-2 libwww-perl libxaw7 libxml-parser-perl
  libxml-sax-expat-perl libxmu6 libxss1 libxt6 libxtst6 libxxf86dga1 linux-image-2.6.32-21-server linux-image-2.6.32-23-server linux-image-server linux-server
  logrotate lvm2 module-init-tools mountall mysql-server mysql-server-5.1 netbase ntfs-3g ntpdate obex-data-server openjdk-6-jre openssh-server plymouth
  plymouth-theme-ubuntu-text pm-utils policykit-1 policykit-1-gnome powermgmt-base powernap ppp pppconfig pppoeconf procps python-webkit qemu-kvm rsyslog
  software-properties-gtk sun-java6-plugin telnet ubufox ubuntu-minimal ubuntu-standard udev udisks ufw upstart ureadahead util-linux watershed wireless-crda
  x-ttcidfont-conf x11-common x11-utils x11-xserver-utils xfonts-encodings xfonts-utils
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 128 to remove and 13 not upgraded.
After this operation, 492MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
```
After which I decided not to remove since it is removing apache2 and some other necessary things also.
How can I disable this.

---

### Post by mörgæs on 2010-07-09
I believe that it can not be removed, simply because it is deeply integrated with rest of the system.

---

### Post by garvinrick4 on 2010-07-09
I ran to completely remove and it was same. Went into Synaptics and
will remove same. Best to leave alone I do believe.

---

### Post by krishnandu.sarkar on 2010-07-09
See the 2nd Solution, this may come handy for you [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---


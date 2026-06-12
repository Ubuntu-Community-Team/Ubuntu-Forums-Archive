---
title: "Which CD image?"
date: 2006-10-22
forum: The Cafe
---

### Post by PatrickMay16 on 2006-10-22
Hey guys.
I'm soon getting a laptop which I ordered on ebay, and I'll be installing Ubuntu on it. Though I want to do a server install like you could do with Hoary and Breezy and then install X and then a window manager, etc. This is what I always used to do, but now the default dapper CD can't do this.

So, which one of the dapper CD images should I choose?
[http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/](http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/)

I know it's one of the i386 ones, of course. But is it "server-i386" or "alternate-i386" or what?

Thanks.

---

### Post by PatrickMay16 on 2006-10-22
Oh-ho! I am downloading the alternate image, now, because I found that this is what I need.

Thanks anyway.

---

### Post by dbott67 on 2006-10-22
Actually, you probably want the desktop image (i386).

[http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06.1-desktop-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06.1-desktop-i386.iso)

-Dave

---

### Post by GStubbs43 on 2006-10-22
> **dbott67 said:**
> Actually, you probably want the desktop image (i386).

[http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06.1-desktop-i386.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06.1-desktop-i386.iso)

-Dave

But that's the default Ubuntu with x and everything, he wants to install Ubuntu with nothing on it, then a DE, apps etc.

---

### Post by dbott67 on 2006-10-22
> **GStubbs43 said:**
> But that's the default Ubuntu with x and everything, he wants to install Ubuntu with nothing on it, then a DE, apps etc.

I missed that part about the basic installation... I only caught the part about the 'alternate' image (which contains apps from the repos, I think.  It's not an installation CD).

I think the desktop image gives you the ability to do a custom/advanced/expert install, so he could take that path.  He could also install the desktop CD and then:
```
sudo aptitude remove ubuntu-desktop
```

Or follow this thread:
[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

```
sudo apt-get remove alacarte app-install-data app-install-data-commercial at-spi bicyclerepair bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data contact-lookup-applet deskbar-applet diveintopython ekiga eog esound esound-common evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal fastjar festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gdb gedit gedit-common gij-4.1 gimp-python gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-lighthouseblue gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client java-common java-gcj-compat libadns1 libatspi1.0-0 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1 libavc1394-0 libbeagle0 libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcurl3 libcurl3-gnutls libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libesd-alsa0 libestools1.2 libexchange-storage1.2-1 libflac7 libgail-common libgail-gnome-module libgail17 libgcj-common libgcj7 libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgeoip1 libglew1 libglib-perl libgmp3c2 libgnome-desktop-2 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgphoto2-2 libgphoto2-port0 libgpod0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libhsqldb-java libicu34 libid3-3.8.3c2a libidn11 libieee1284-3 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjline-java liblircclient0 liblpint-bonobo0 libmagick9 libmdbtools libmetacity0 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libneon25 libnetcdf3 libnotify1 liboil0.3 libopal-2.2.0 libopenobex-1.0-0 libpanel-applet2-0 libpisock8 libpisync0 libportaudio0 libpq4 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraptor1 librasqal0 libraw1394-5 librdf0 libsane libsdl1.2debian libsdl1.2debian-alsa libservlet2.3-java libsexy2 libshout3 libsmbclient libsndfile1 libsoup2.2-8 libsqlite0 libsqlite3-0 libstlport4.6c2 libtotem-plparser1 libvorbisenc2 libvorbisfile3 libwnck-common libwnck18 libxalan2-java libxerces2-java libxklavier10 libxml2-utils libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxres1 libxt-java metacity mysql-common nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-writer openssl pkg-config python-adns python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-launchpad-integration python-ldap python-libxml2 python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-soappy python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml python2.4-xmpp rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tcl8.4 tk8.4 totem totem-gstreamer tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs update-notifier vino vnc-common whois xsane xsane-common xsltproc xvncviewer yelp zenity
```



-Dave

---

### Post by maniacmusician on 2006-10-22
or you know, just use the alternate CD and choose "Install Command Line System". a little less work.

---


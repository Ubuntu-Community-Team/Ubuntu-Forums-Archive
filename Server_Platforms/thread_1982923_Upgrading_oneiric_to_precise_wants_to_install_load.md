---
title: "Upgrading oneiric to precise wants to install loads of desktop-packages"
date: 2012-05-19
forum: Server Platforms
---

### Post by isecore on 2012-05-19
As the topic says, I just attempted to upgrade my oneiric-based server to precise. It's completely headless and needs no GUI or anything, yet do-release-upgrade wants to add a long list (400+ packages) of what seems to be desktop-related stuff. I don't want this, nor do I need it on a server.

The packages are: 

```

  ibxcursor1 libxcursor1:i386 libxcb-shm0:i386 dconf-service 
  libxt6 libxt6:i386 libxv1 libxv1:i386 libslang2:i386 libxext6:i386 
  libsasl2-modules:i386 libavahi-common3:i386 libxrandr2 
  libxrandr2:i386 mysql-server-5.5 libgtk-3-common 
  gstreamer0.10-plugins-base:i386 libsndfile1:i386 libsqlite3-0:i386 
  libmng1:i386 libgtk2.0-0 libgtk2.0-0:i386 libjasper1 
  libjasper1:i386 libpng12-0:i386 libvisual-0.4-plugins:i386 
  libgstreamer-plugins-base0.10-0:i386 libpciaccess0:i386 
  libudev0:i386 libgnome-keyring0 libgnome-keyring0:i386 
  libgnome-keyring-common libxtst6 libxtst6:i386 
  gtk2-engines-pixbuf:i386 gsettings-desktop-schemas libuuid1:i386 
  libisccfg82 libcryptsetup4 libqtgui4:i386 liblua5.1-0 
  libtag1c2a:i386 librsvg2-2:i386 libavahi-client3:i386 
  libgail-common:i386 libxrender1:i386 libhcrypto4-heimdal 
  libhcrypto4-heimdal:i386 liborc-0.4-0:i386 libraw1394-11:i386 
  libnspr4:i386 libshout3:i386 libdv4:i386 libatasmart4 
  libhx509-5-heimdal libhx509-5-heimdal:i386 libvorbisenc2:i386 
  libqt4-xml libqt4-xml:i386 zlib1g:i386 libasyncns0:i386 
  gstreamer0.10-x:i386 libgettextpo0:i386 libdconf0 libxss1 
  libxss1:i386 liblvm2app2.2 libgd2-xpm:i386 libheimbase1-heimdal 
  libheimbase1-heimdal:i386 libtiff4 libtiff4:i386 libsdl-net1.2:i386 
  libgdk-pixbuf2.0-common libltdl7:i386 gvfs-daemons mysql-client-5.5 
  libkrb5-26-heimdal libkrb5-26-heimdal:i386 libssl1.0.0:i386 
  libasound2-plugins:i386 glib-networking glib-networking:i386 
  libgpg-error0:i386 gconf-service-backend libllvm3.0 libllvm3.0:i386 
  libsoup2.4-1:i386 libgphoto2-2:i386 libogg0:i386 consolekit 
  libtag1-vanilla:i386 libaudiofile1:i386 libpulsedsp:i386 
  libept1.4.12 libxdamage1 libxdamage1:i386 gvfs gvfs:i386 
  libqt4-sql-mysql:i386 libxcb-render0:i386 libodbc1 libodbc1:i386 
  libexif12:i386 libgtk2.0-bin libqt4-scripttools:i386 
  libglu1-mesa:i386 librtmp0:i386 libgssapi-krb5-2:i386 dbus-x11 
  libxi6 libxi6:i386 libvorbis0a:i386 libisc83 libqtwebkit4:i386 
  glib-networking-services libxcb-shape0 libc6:i386 
  libgstreamer0.10-0:i386 libattr1:i386 libxp6:i386 libaudio2:i386 
  libgcrypt11:i386 libthai0:i386 libdrm-intel1:i386 libxml2:i386 
  libbind9-80 libao4:i386 libkeyutils1:i386 libapt-pkg4.12 
  libdevmapper-event1.02.1 policykit-1-gnome libxmu6 libxmu6:i386 
  libcanberra-gtk0:i386 libgpm2:i386 libvorbisfile3:i386 
  libqt4-sql:i386 libsane-common esound-common libasound2:i386 
  libxpm4:i386 libflac8:i386 libqt4-svg:i386 libusb-0.1-4:i386 
  krb5-locales libssl0.9.8:i386 libmpg123-0:i386 libmad0:i386 
  libpolkit-agent-1-0 libx11-6:i386 fuse libsasl2-2:i386 
  libdb5.1:i386 gtk2-engines-oxygen:i386 libfontconfig1:i386 
  gconf-service libevent-2.0-5 xaw3dg:i386 libpango1.0-0:i386 libsm6 
  libsm6:i386 libpulse0:i386 resolvconf liboil0.3:i386 
  libheimntlm0-heimdal libheimntlm0-heimdal:i386 hicolor-icon-theme 
  libnl-3-200 libbz2-1.0:i386 libxcb-glx0:i386 dovecot-core 
  libxcb-glx0 udisks libgl1-mesa-dri odbcinst1debian2:i386 
  libdbus-glib-1-2:i386 libtdb1:i386 linux-image-3.2.0-24-generic 
  libqt4-dbus:i386 libproxy1 libqt4-network:i386 libqt4-dbus 
  libtinfo5:i386 libdbus-1-3:i386 libxxf86vm1:i386 libaio1:i386 
  libqt4-designer:i386 libproxy1:i386 libxxf86vm1 
  libgl1-mesa-dri:i386 libqt4-script:i386 ibus-gtk:i386 libcap2:i386 
  libsdl-mixer1.2:i386 gcc-4.6-base:i386 libsane:i386 
  libqt4-test:i386 libv4l-0:i386 libunistring0:i386 libgphoto2-l10n 
  libqt4-qt3support:i386 libao-common libcupsimage2:i386 libxxf86dga1 
  libxcomposite1 libgphoto2-port0:i386 liblcms1:i386 
```

Is this normal?

---

### Post by 2F4U on 2012-05-19
Are you sure that you don't have desktop packages installed, even if you don't use them. On my upgrade of Ubuntu Server from 10.04 to 12.04 it didn't want to install any desktop packages. But I had the server version installed, which comes without GUI and there was no GUI installed.

---

### Post by isecore on 2012-05-19
So why would it install these packages? It seems wasteful to me. I literally have only 174 packages installed on the server - only what I need, nothing I don't want. It wants to add 400+ more packages, some of which seem oddly out of place for a GUI-less server, for example - why would I need the GTK-themes package on a server?

Like I said, makes no real sense.

---

### Post by CharlesA on 2012-05-19
> **2F4U said:**
> Are you sure that you don't have desktop packages installed, even if you don't use them. On my upgrade of Ubuntu Server from 10.04 to 12.04 it didn't want to install any desktop packages. But I had the server version installed, which comes without GUI and there was no GUI installed.
That was my experience upgrading from 10.04 to 12.04.

@OP: Do you have any desktop packages installed now?

---

### Post by oldfred on 2012-05-19
Are you running 32 bit or 64 bit?

I have 64 bit desktop, but had an issue and following some post installed a 32bit app that pulled in the 32bit meta package that installed lots of 32 bit apps. I had a heck of time uninstalling, and found that in some cases the 32 bit app uninstalled my 64bit version.

---


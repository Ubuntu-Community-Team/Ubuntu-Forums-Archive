---
title: "Install virtualbox on crouton Toshiba cb35"
date: 2015-05-07
forum: Virtualisation
---

### Post by leotemp on 2015-05-07
I've been trying to get virtualbox to run on crouton for days with no success. Crouton allows you to run ubuntu on chromeos, for more information go here:
[https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)

I am using a Toshiba cb35 chromebook, details on this device can be found here:
[http://www.toshiba.com/us/computers/laptops/chromebook/cb35/CB35-A3120](http://www.toshiba.com/us/computers/laptops/chromebook/cb35/CB35-A3120)

My chromeos version is: 42.0.2311.134 (Official Build) (64-bit)


I don't have any issues installing crouton on my device and it always installs either precise or trusty successfully depending on which release i choose. However, in order to install virtualbox some kernel headers are required that crouton does not use. There is a workaround posted on github here:
[https://github.com/dnschneid/crouton/wiki/Build-kernel-headers-and-install-Virtualbox-%28x86%29](https://github.com/dnschneid/crouton/wiki/Build-kernel-headers-and-install-Virtualbox-%28x86%29)

I have also found this video in which the user is using the same chromebook and successfully using the above hack to get virtualbox working:
[https://www.youtube.com/watch?v=OImoN7frSdg](https://www.youtube.com/watch?v=OImoN7frSdg)


Even with all this I struggle to get virtualbox to even install. I successfully altered my kernel flags and have never received an error when running the setup-headers script from within my ubuntu terminal however when I install virtualbox using the standard dpkg -i path/to/virtualbox.deb i get dependency errors. Output:
 
sudo dpkg -i virtualbox-4.3_4.3.26-98988~Ubuntu~precise_i386.deb 
[sudo] password for leotemp: 
Selecting previously unselected package virtualbox-4.3:i386.
(Reading database ... 81033 files and directories currently installed.)
Unpacking virtualbox-4.3:i386 (from virtualbox-4.3_4.3.26-98988~Ubuntu~precise_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox-4.3:i386:
 virtualbox-4.3:i386 depends on libcurl3 (>= 7.16.2-1).
 virtualbox-4.3:i386 depends on libdevmapper1.02.1 (>= 2:1.02.20).
 virtualbox-4.3:i386 depends on libpng12-0 (>= 1.2.13-4).
 virtualbox-4.3:i386 depends on libpython2.7 (>= 2.7).
 virtualbox-4.3:i386 depends on libqt4-network (>= 4:4.5.3).
 virtualbox-4.3:i386 depends on libqt4-opengl (>= 4:4.7.2).
 virtualbox-4.3:i386 depends on libqtcore4 (>= 4:4.8.0).
 virtualbox-4.3:i386 depends on libqtgui4 (>= 4:4.8.0).
 virtualbox-4.3:i386 depends on libsdl1.2debian (>= 1.2.10-1).
 virtualbox-4.3:i386 depends on libssl1.0.0 (>= 1.0.0).
 virtualbox-4.3:i386 depends on libstdc++6 (>= 4.6).
 virtualbox-4.3:i386 depends on libvpx1 (>= 1.0.0).
 virtualbox-4.3:i386 depends on libx11-6.
 virtualbox-4.3:i386 depends on libxcursor1 (>> 1.1.2).
 virtualbox-4.3:i386 depends on libxext6.
 virtualbox-4.3:i386 depends on libxinerama1.
 virtualbox-4.3:i386 depends on libxml2 (>= 2.7.4).
 virtualbox-4.3:i386 depends on libxmu6.
 virtualbox-4.3:i386 depends on libxt6.
 virtualbox-4.3:i386 depends on zlib1g (>= 1:1.1.4).
 virtualbox-4.3:i386 depends on psmisc.
dpkg: error processing virtualbox-4.3:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 virtualbox-4.3:i386


When I run apt-get install -f it runs for a bit and then presents me with a long list of packages it wants to remove asking me to verify this by typing "Yes, do as I say!". The output:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gtk2-engines-murrine gtk3-engines-unico ubuntu-mono adium-theme-ubuntu
  gir1.2-vte-2.90 libqtcore4:i386 libglib2.0-0:i386 libpcre3:i386
  libx11-6:i386 libstdc++6:i386 zlib1g:i386 libqt4-network:i386
  libqt4-dbus:i386 libdbus-1-3:i386 libqt4-xml:i386 libqtgui4:i386
  libjpeg8:i386 libfreetype6:i386 libjpeg-turbo8:i386 libice6:i386 libsm6:i386
  libuuid1:i386 libqt4-opengl:i386 libxml2:i386 libxext6:i386 libssl1.0.0:i386
  libfontconfig1:i386 libexpat1:i386 libcurl3:i386 libgssapi-krb5-2:i386
  libkrb5-3:i386 libldap-2.4-2:i386 libgnutls26:i386 libgcrypt11:i386
  libcomerr2:i386 libkeyutils1:i386 libxinerama1:i386 libxrender1:i386
  libpng12-0:i386 libselinux1:i386 libcups2:i386 libavahi-common3:i386
  libavahi-client3:i386 libsasl2-2:i386 libdb5.1:i386 libidn11:i386
  libtiff4:i386 libpulse0:i386 libwrap0:i386 libxmu6:i386 libxt6:i386
  libxcursor1:i386 libxfixes3:i386 libmng1:i386 liblcms1:i386 libp11-kit0:i386
  libxi6:i386 libgpg-error0:i386 libffi6:i386 libgssapi3-heimdal:i386
  libkrb5-26-heimdal:i386 libsqlite3-0:i386 libasn1-8-heimdal:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libhx509-5-heimdal:i386
  libwind0-heimdal:i386 libqt4-declarative:i386 libqt4-sql:i386
  libqt4-script:i386 libqt4-sql-mysql:i386 libmysqlclient18:i386
  libqt4-xmlpatterns:i386 libsasl2-modules:i386 libsndfile1:i386 libflac8:i386
  libogg0:i386 libvorbis0a:i386 libvorbisenc2:i386 libk5crypto3:i386
  libaudio2:i386 libxau6:i386 libelf1:i386 libroken18-heimdal:i386
  libasyncns0:i386 libsdl1.2debian:i386 libcaca0:i386 libslang2:i386
  libncursesw5:i386 libtinfo5:i386 libgpm2:i386 libavahi-common-data:i386
  libvpx1:i386 libxcb1:i386 libxdmcp6:i386 librtmp0:i386 libtasn1-3:i386
  libkrb5support0:i386 libheimntlm0-heimdal:i386 libjson0:i386
  libgl1-mesa-glx-lts-trusty:i386 libudev0:i386 libxdamage1:i386
  libxxf86vm1:i386 libdrm2:i386 libx11-xcb1:i386 libxcb-dri2-0:i386
  libxcb-glx0:i386 libgl1-mesa-dri-lts-trusty:i386 libdrm-intel1:i386
  libpciaccess0:i386 libdrm-radeon1:i386 libtxc-dxtn-s2tc0:i386
  libdrm-nouveau2:i386 libglapi-mesa-lts-trusty:i386 libllvm3.4:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  krb5-locales libasn1-8-heimdal:i386 libasyncns0:i386 libaudio2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libcaca0:i386 libcomerr2:i386 libcups2:i386 libcurl3:i386 libdb5.1:i386
  libdbus-1-3:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386
  libdrm2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386
  libglapi-mesa-lts-trusty:i386 libglib2.0-0:i386 libgnutls26:i386
  libgpg-error0:i386 libgpm2:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libice6:i386 libidn11:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm3.4:i386
  libmng1:i386 libmysqlclient18:i386 libncursesw5:i386 libogg0:i386
  libp11-kit0:i386 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386
  libpulse0:i386 libqt4-dbus:i386 libqt4-declarative:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386
  libroken18-heimdal:i386 librtmp0:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsdl1.2debian:i386 libselinux1:i386 libslang2:i386 libsm6:i386
  libsndfile1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-3:i386 libtiff4:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386
  libudev0:i386 libuuid1:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386
  libxrender1:i386 libxt6:i386 libxxf86vm1:i386 python3 python3-minimal
  python3.2 python3.2-minimal uuid-runtime zlib1g:i386
Suggested packages:
  nas:i386 cups-common:i386 rng-tools:i386 libglide3:i386 gnutls-bin:i386
  gpm:i386 krb5-doc:i386 krb5-user:i386 liblcms-utils:i386
  libqt4-declarative-folderlistmodel:i386 libqt4-declarative-gestures:i386
  libqt4-declarative-particles:i386 libqt4-declarative-shaders:i386
  qt4-qmlviewer:i386 libqt4-dev:i386 libthai0:i386 qt4-qtconfig:i386
  libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386 python3-doc python3-tk python3.2-doc
  binfmt-support
Recommended packages:
  krb5-locales:i386 uuid-runtime:i386 xml-core:i386
The following packages will be REMOVED:
  aptdaemon compiz compiz-gnome compiz-plugins-main-default
  compizconfig-backend-gconf evolution-data-server firefox
  foomatic-db-compressed-ppds gconf2 gdebi gdebi-core gir1.2-peas-1.0
  gir1.2-rb-3.0 gksu gnome-control-center gnome-menus gnome-terminal
  gnome-terminal-data indicator-datetime indicator-power launchpad-integration
  libcanberra-gtk-module libcanberra-gtk3-module libcompizconfig0 libgksu2-0
  libgnome2-common libgweather-3-0 libgweather-common libmetacity-private0
  libpeas-1.0-0 libpython2.7 librhythmbox-core5 light-themes lsb-release
  metacity metacity-common python python-apt python-apt-common
  python-aptdaemon python-aptdaemon.pkcompat python-cairo python-chardet
  python-cups python-cupshelpers python-dbus python-debian python-defer
  python-dirspec python-gconf python-gi python-gnomekeyring
  python-gnupginterface python-gobject python-gobject-2 python-gst0.10
  python-gtk2 python-libxml2 python-mako python-markupsafe python-minimal
  python-notify python-packagekit python-pkg-resources python-pycurl
  python-smbc python-software-properties python-xdg python-zeitgeist python2.7
  python2.7-minimal rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev ubuntu-artwork ubuntu-minimal
  ubuntu-system-service unattended-upgrades unity unity-2d unity-common
  unity-lens-applications unity-lens-video unity-scope-musicstores
  unity-scope-video-remote virtualbox-4.3:i386 xul-ext-ubufox zeitgeist
  zeitgeist-core zeitgeist-datahub
The following NEW packages will be installed:
  krb5-locales libasn1-8-heimdal:i386 libasyncns0:i386 libaudio2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libcaca0:i386 libcomerr2:i386 libcups2:i386 libcurl3:i386 libdb5.1:i386
  libdbus-1-3:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386
  libdrm2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386
  libglapi-mesa-lts-trusty:i386 libglib2.0-0:i386 libgnutls26:i386
  libgpg-error0:i386 libgpm2:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libice6:i386 libidn11:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm3.4:i386
  libmng1:i386 libmysqlclient18:i386 libncursesw5:i386 libogg0:i386
  libp11-kit0:i386 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386
  libpulse0:i386 libqt4-dbus:i386 libqt4-declarative:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386
  libroken18-heimdal:i386 librtmp0:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsdl1.2debian:i386 libselinux1:i386 libslang2:i386 libsm6:i386
  libsndfile1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-3:i386 libtiff4:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386
  libudev0:i386 libuuid1:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386
  libxrender1:i386 libxt6:i386 libxxf86vm1:i386 python3 python3-minimal
  python3.2 python3.2-minimal uuid-runtime zlib1g:i386
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  python-minimal python2.7-minimal (due to python-minimal)
0 upgraded, 117 newly installed, 96 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 44.2 MB of archives.
After this operation, 159 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]     



 If i do confirm this it runs for about 10 mins and all seems okay for a moment, then the unity bar vanishes and upon reboot i get only the ubuntu wallpaper. I have no idea if virtualbox even installed and unity is broken at this point.

I have verified that I am using precise and that i am downloading the precise virtualbox deb file. 

If anyone has an idea of what to try next I would really appreciate it. I need photoshop for work and I bought this chromebook based on research that made it appear a VM would be possible. Thanks!

---

### Post by TheFu on 2015-05-09
Chromebook?
Photoshop?

Bad idea. Low end CPU, not enough RAM. You'll need an external disk - that's easy, but you can't fix the other two issues.
I don't have that chromebook - have an Acer C720.  Only has 2G of RAM, so I played with KVM for about 6 hrs and decided that was a bad idea. KVM is lighter than virtualbox.

I would be surprised if running ubuntu in a chroot will let you run virtualbox. I think you'd need a real Ubuntu install to load vbox so the kernel modules required could be used.

I clicked here to suggest you try an LXC container solution instead of full virtualization, but if you need to load Windows, that won't work. Containers only work for Linux-based needs.

---


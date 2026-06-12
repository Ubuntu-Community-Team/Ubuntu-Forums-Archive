---
title: "Distro upgrade"
date: 2012-07-01
forum: Server Platforms
---

### Post by kalosh on 2012-07-01
Hello.
I wanted to upgrade the distro. I have run the command, I have seen packages which were downloaded and installed but I have lost connection to my ssh console (my server resides in the closed without external devices). DHCP server was shut down by the installer. Ok, no problem I assigned IP to my laptop manually, logged in again by ssh. I see in ps that installer process is hang up (probably waits for my reaction on the console):
```
kalosh@solis:~$ ps ax | grep dpkg
18881 pts/2    Ss+    0:03 /usr/bin/dpkg --force-overwrite --status-fd 39 --configure dmsetup libdevmapper1.02.1 gettext-base grub-common grub-pc-bin grub2-common grub-gfxpayload-lists grub-pc libnewt0.52 libpopt0 whiptail friendly-recovry libpixman-1-0 libxcb-render0 libxcb-shm0 libxrender1 libcairo2 libthai-data libdatrie1 libthai0 libxft2 fontconfig libpango1.0-0 bzip2 libswitch-perl libclass-isa-perl perl-modules perl update-inetd libsnmp-base libperl5.14 libsensors libsnmp15 libltdl7 imagemagick-common libgomp1 libjasper1 liblcms1 liblqr-1-0 libtiff4 libxext6 libxml2 libmagickcore4 perlmagick libapparmor1 libapparmor-perl libtext-charwidth-perl libsub-name-perl liburi-perl libhtml-parser-perl liblcale-gettext-perl libnet-ssleay-perl libterm-readkey-perl libtext-iconv-perl openssl ca-certificates libencode-locale-perl libfile-listing-perl libnet-http-perl netbase libwww-perl libxml-parser-perl fuse-utils xkb-data hdparm keyboard-cnfiguration kbd console-setup tzdata-java libkrb5support0 libk5crypto3 libkeyutils1 libkrb5-3 libgssapi-krb5-2 libidn11 wget ssh-import-id libbsd0 libedit2 openssh-client openssh-server liblist-moreutils-perl libparams-validate-perl libdtetime-locale-perl libclass-singleton-perl libparams-util-perl libsub-install-perl libdata-optlist-perl libparams-classify-perl libmodule-runtime-perl libpackage-deprecationmanager-perl libpackage-stash-perl libtry-tiny-perl libclass-loa-perl libdatetime-timezone-perl libmath-round-perl libdatetime-perl libclass-factory-util-perl libdatetime-format-strptime-perl libdatetime-format-builder-perl libdatetime-format-iso8601-perl librpc-xml-perl cron cpio libsqlite3-0 python.7 python python-pkg-resources python-lazr.uri python-wadllib python-simplejson python-wsgi-intercept python-markupsafe python-mako libpython2.7 python-newt iproute ifupdown libgphoto2-l10n libexif12 libgphoto2-port0 libgphoto2-2 libcdt4libgraph4 libpathplan4 libgvc5 libasound2 libcaca0 libflac8 libvorbis0a libvorbisenc2 libsndfile1 libpulse0 libsdl1.2debian bsdmainutils libapt-inst1.4 liblockfile-bin liblockfile1 libssl0.9.8 ntpdate resolvconf libelf1 mawk apparmor bas-completion iso-codes python-apt-common python-apt libdbus-glib-1-2 python-dbus-dev python-dbus dbus libpolkit-gobject-1-0 libaccountsservice0 accountsservice language-selector-common libroken18-heimdal libasn1-8-heimdal libp11-kit0 libtsn1-3 libgpg-error0 libgcrypt11 libgnutls26 libhcrypto4-heimdal libheimbase1-heimdal libwind0-heimdal libhx509-5-heimdal libkrb5-26-heimdal libheimntlm0-heimdal libgssapi3-heimdal libsasl2-2 libsasl2-modules libldap-2.4-2 librtmp0 libcur3-gnutls libparted0debian1 libpcap0.8 libpci3 pciutils libpipeline1 libusb-1.0-0 libxmuu1 ntfs-3g libcolord1 libgudev-1.0-0 liblcms2-2 libsane-common acl libavahi-common-data libavahi-common3 libavahi-client3 libieee1284-3 libv4lconvert0libv4l-0 libsane libpolkit-agent-1-0 libpolkit-backend-1-0 libck-connector0 consolekit policykit-1 colord foomatic-db-compressed-ppds libcups2 libcupsmime1 libcap2 libtalloc2 libtdb1 libwbclient0 samba-common winbind samba-common-bin sama smbclient libpam-smbpass openprinting-ppds libcupscgi1 libcupsimage2 libcupsppdc1 libpaper1 libpoppler19 poppler-utils libijs-0.35 libgs9-common libgs9 ghostscript gs-cjk-resource cups-common cups-client cups-bsd ssl-cert cups-ppdc libupsfilters1 cups-filters cups foomatic-filters locales language-pack-en-base language-pack-en language-pack-pl-base language-pack-pl libgpm2 libaa1 libaccess-bridge-java libaccess-bridge-java-jni libatk1.0-data libatk1.0-0 libgdk-pixbuf20-common libgdk-pixbuf2.0-0 libgtk2.0-common libxcomposite1 libxfixes3 libxcursor1 libxdamage1 libxi6 libxinerama1 libxrandr2 shared-mime-info libgtk2.0-0 openjdk-6-jre-lib java-common default-jre-headless libnspr4 libnss3 libnss3-1d ca-ertificates-java libpcsclite1 openjdk-6-jre-headless icedtea-6-jre-cacao icedtea-6-jre-jamvm libgif4 x11-common libxtst6 libatk-wrapper-java libatk-wrapper-java-jni openjdk-6-jre default-jre libatm1 libavahi-core7 libavutil51 liborc-0.4- libschroedinger-1.0-0 libspeex1 libtheora0 libva1 libvpx1 libavcodec53 libav
26700 pts/2    S+     0:01 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/samba-common.postinst configure 2:3.5.11~dfsg-1ubuntu2.1
26720 pts/2    S+     0:00 /bin/sh /var/lib/dpkg/info/samba-common.postinst configure 2:3.5.11~dfsg-1ubuntu2.1
28329 pts/3    S+     0:00 grep --color=auto dpkg

```Is it possible to get access to the hanging process or I need to kill it and run command again from new ssh session?
Thanks, for the answers:)
Dawid.

---

### Post by kalosh on 2012-07-02
do-release-upgrade creates screen by default so I could reconnect session using the screen command.

---


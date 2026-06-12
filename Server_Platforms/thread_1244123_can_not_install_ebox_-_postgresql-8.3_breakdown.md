---
title: "can not install ebox - postgresql-8.3 breakdown"
date: 2009-08-19
forum: Server Platforms
---

### Post by parvez on 2009-08-19
HI - I am trying to install ebox on my ubuntu-server-9.04 but the installation break down when its trying to install postgresql-8.3, Here is the console output. Hope somebody can give me any suggestion.

sudo apt-get install ebox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common defoma fontconfig fontconfig-config gconf2
  gconf2-common gettext hicolor-icon-theme javascript-common libapache-singleton-perl libapache2-mod-perl2
  libapache2-reload-perl libapr1 libaprutil1 libatk1.0-0 libatk1.0-data libauthen-sasl-perl libbsd-resource-perl
  libcache-cache-perl libcairo2 libchart-perl libclass-container-perl libclass-data-inheritable-perl
  libclass-singleton-perl libclone-perl libcroco3 libcups2 libdatetime-format-mail-perl
  libdatetime-format-w3cdtf-perl libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl libdatrie0
  libdbd-pg-perl libdbi-perl libdevel-stacktrace-perl libdevel-symdump-perl libdigest-sha1-perl libdirectfb-1.0-0
  libebox liberror-perl libexception-class-perl libfile-copy-recursive-perl libfile-mmagic-perl libfile-slurp-perl
  libfile-tail-perl libfilesys-df-perl libfontconfig1 libfontenc1 libfreetype6 libgconf2-4 libgd-gd2-perl
  libgd2-xpm libglib-perl libgnome2-gconf-perl libgomp1 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libhtml-mason-perl libidl0 libintl-perl libio-socket-ssl-perl libipc-shareable-perl libipc-sharelite-perl
  libjasper1 libjpeg62 libjs-prototype libjs-scriptaculous liblog-dispatch-perl liblog-log4perl-perl
  libmail-rfc822-address-perl libmysqlclient15off libnet-daemon-perl libnet-ip-perl libnet-jabber-perl
  libnet-libidn-perl libnet-ssleay-perl libnet-xmpp-perl liborbit2 libpango1.0-0 libpango1.0-common
  libparams-validate-perl libperl5.10 libperl6-junction-perl libpixman-1-0 libplrpc-perl libpng12-0 libpolkit-dbus2
  libpq5 libproc-process-perl libproc-processtable-perl libreadonly-perl libreadonly-xs-perl libsys-cpu-perl
  libsys-cpuload-perl libsysfs2 libthai-data libthai0 libtiff4 libts-0.0-0 libxcb-render-util0 libxcb-render0
  libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxml-rss-perl
  libxml-stream-perl libxpm4 libxrandr2 libxrender1 mysql-common postgresql postgresql-8.3 postgresql-client-8.3
  postgresql-client-common postgresql-common ssl-cert ttf-dejavu ttf-dejavu-core ttf-dejavu-extra wwwconfig-common
  x-ttcidfont-conf xfonts-encodings xfonts-utils
.................................................

 * Starting PostgreSQL 8.3 database server                                                                            * The PostgreSQL server failed to start. Please check the log output:
2009-08-18 16:15:35 BST LOG:  could not bind IPv4 socket: Cannot assign requested address
2009-08-18 16:15:35 BST HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
2009-08-18 16:15:35 BST LOG:  could not bind IPv6 socket: Cannot assign requested address
2009-08-18 16:15:35 BST HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
2009-08-18 16:15:35 BST WARNING:  could not create listen socket for "localhost"
2009-08-18 16:15:35 BST FATAL:  could not create any TCP/IP sockets
                                                                                                              [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on postgresql; however:
  Package postgresql is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                               Errors were encountered while processing:
 postgresql-8.3
 postgresql
 ebox
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Adina on 2009-08-19
I remember trying to install ebox on an ubuntu server 8.10 and the installation crashed halfway through. I later found out that there was some issue with 8.10 that ebox didn't work. I have installed ebox on server 8.04 and it worked fine. I have not tried 9.04 yet but maybe ebox doesn't work on that version. Hopefully someone on the forum will know.

---

### Post by parvez on 2009-08-19
Hi - I have fixed the installation problems. The server does not have loopback scripts in /etc/init.d. So the server can not ping it self ( I am not sure why we need that). I just copy from my PC into the server and restart the network and the installation went smoothly. But I have another problem now I can not login into my server using ebox. I typed on my firefox browser http;//myserver/ebox but its saying that "192.168.1.82 uses an invalid security certificate.". Any idea why? Thansk for your time.

---

### Post by parvez on 2009-08-19
ok - its working now. I just need to click on "I understand the risks" and accepted the certificate. Thanks

---


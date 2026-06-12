---
title: "Sip Express Router"
date: 2006-08-16
forum: Server Platforms
---

### Post by najeer on 2006-08-16
download package, unzipped it to the usr/src/, downloaded build-essentials, flex, and bison.  issued make clean nunca.  issued make install it appears to be installing but I see the following statements:  makefile rules 80 no such file or directory for a bunch of the apps.  

Any suggestions,

najeer

---

### Post by byteslash on 2007-06-05
Hi everyone. im posting this to help anyone pretending to install SER on UBUNTU 7.04.

Steps:

1. download the source from  [http://ftp.iptel.org/pub/ser/LATEST-IS-0.9.6/src/]("http://ftp.iptel.org/pub/ser/LATEST-IS-0.9.6/src/")

2. upgrade your build utils by downloading the following packages needed packages for compiling all the modules:
  Debian:
      - libmysqlclient-dev for libmysqlclient
      - libpq-dev for libpq
      - libexpat1-dev for libexpat
      - libxml2-dev for libxml2
      - libradiusclient-ng-dev for libradiusclient (you can download the 
      package from [http://apt.sip-router.org/debian/dists/unstable/main/binary-i386/libradiusclient-ng-dev_0.5.1-0.5_i386.deb](http://apt.sip-router.org/debian/dists/unstable/main/binary-i386/libradiusclient-ng-dev_0.5.1-0.5_i386.deb) ).
      NOTE: you can get up-to-date ser packages or libradiusclient packages
      from [http://apt.sip-router.org:](http://apt.sip-router.org:) add to your /etc/apt/sources.list the
      following lines:
         deb [http://apt.sip-router.org/debian](http://apt.sip-router.org/debian) testing main contrib non-free
         deb [http://apt.sip-router.org/debian](http://apt.sip-router.org/debian) unstable main contrib non-free
      and then: apt-get update; apt-get install libradiusclient-ng-dev
      (or, if you want to use the pre-built modules:
       apt-get install ser ser-cpl-module ser-jabber-module ser-mysq-module ser-pa-module ser-postgres-module ser-radius-modules )


  Compile example (all the modules and ser in a tar.gz):
     make bin include_modules="mysql jabber cpl-c auth_radius group_radius uri_radius postgres pa"

Since my system was quite updated i have just issued " apt-get install libpq-dev " on shell the as root on ser extracted folder issued make install.  everythings were successfully compiled and installed.

i recommend u to do the following on section 2 of this link [http://ftp.iptel.org/pub/ser/0.9.6/doc/INSTALL]("http://ftp.iptel.org/pub/ser/0.9.6/doc/INSTALL")

3. then follow the installation of the sip User agent (client ) on [http://www.en.voipforo.com/Telephones/sjphone-configuration.php]("http://www.en.voipforo.com/Telephones/sjphone-configuration.php")

:popcorn: enjoy uself

---


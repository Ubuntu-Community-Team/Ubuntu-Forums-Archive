---
title: "apt-get spkg serious warning.   help"
date: 2009-08-18
forum: Server Platforms
---

### Post by joefizz on 2009-08-18
hi

when trying to perform tasks like install with apt-get I continuously get the following errors.  I'm getting to a point where I'm ready to just reinstall but I really don't want to.   ANy help would be much appreciated.

> joe@ubuntuXF:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-image-generic linux-restricted-modules-generic netatalk
The following packages will be upgraded:
  acpid amule amule-common apache2 apache2-mpm-prefork apache2-utils
  apache2.2-common apparmor apparmor-utils apt apt-utils base-files bind9
  bind9-host bsdutils console-setup cpp-4.2 cron cupsys cupsys-bsd
  cupsys-client cupsys-common dash dbus dbus-x11 devscripts dhcp3-client
  dhcp3-common dnsutils fakeroot file foomatic-filters g++-4.2 gcc-4.2
  gcc-4.2-base gksu gnome-power-manager grub hal hal-info initramfs-tools
  initscripts installation-report irb1.8 language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  ldap-utils libapr1 libaprutil1 libavahi-client-dev libavahi-client3
  libavahi-common-data libavahi-common-dev libavahi-common3 libavahi-core5
  libavahi-glib1 libbind9-30 libcupsimage2 libcupsimage2-dev libcupsys2
  libcupsys2-dev libcurl3 libcurl3-gnutls libdbus-1-3 libdbus-1-dev libdns35
  libffi4 libfreetype6 libgcc1 libglib2.0-0 libgnutls-dev libgnutls13
  libgnutlsxx13 libgomp1 libhal-storage1 libhal1 libisc35 libisccc30
  libisccfg30 libldap-2.4-2 liblwres30 libmagic1 libntfs-3g23 libpango1.0-0
  libpango1.0-common libparted1.7-1 libperl5.8 libpq5 libreadline-ruby1.8
  libruby1.8 libsmbclient libssl-dev libssl0.9.8 libstdc++6 libstdc++6-4.2-dev
  libtiff4 libtiff4-dev libtiffxx0c2 libvolume-id0 libxml2 linux-libc-dev
  linux-restricted-modules-common login logrotate lsb-base lsb-release
  module-init-tools mount myspell-en-gb myspell-en-us myspell-en-za nfs-common
  nfs-kernel-server ntfs-3g ntpdate openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-thesaurus-en-us openssl parted passwd perl perl-base
  perl-modules php-pear php5 phpmyadmin pm-utils python-apt python2.5
  python2.5-dev python2.5-minimal rdoc1.8 ruby1.8 samba samba-common samba-doc
  slapd smbclient sudo sysv-rc sysvutils tasksel tasksel-data tzdata udev ufw
  update-manager-core util-linux util-linux-locales vim-common vim-tiny
157 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/105MB of archives.
After this operation, 532kB disk space will be freed.
Do you want to continue [Y/n]?
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `python-minimal' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `psmisc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sysv-rc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sgml-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `aspell-en' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/dash_0.5.4-8ubuntu1.1_i386.deb (--unpack):
 files list file for package `libsnmp-base' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/dash_0.5.4-8ubuntu1.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@ubuntuXF:/$:confused:

---

### Post by SukiSuki on 2009-09-29
I was having a similar problem recently; some of my package listing files had been corrupted in "/var/lib/dpkg/info/" 

Deleting the offending listing files then reinstalling the packages with "serious warnings" fixed things for me.

```

apt-get install <list of package names> --reinstall

```

ref: [http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/]("http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/")

---


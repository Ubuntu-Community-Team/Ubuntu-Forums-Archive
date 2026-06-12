---
title: "Upgrade 10.04 to 12.04.1 failed"
date: 2012-08-23
forum: Server Platforms
---

### Post by frec on 2012-08-23
Hello, I have waited till 12.04.1 to be released today to upgrade from 10.04 LTS server edition, and i have tried to upgrade it just now since the first point release has been released today.
The commands I used are:
sudo apt-get update
sudo apt-get upgrade
> Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo do-release-upgrade
> Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg'
extracting 'precise.tar.gz'
however, I got this error message during upgrade:
 
> Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be
caused by held packages.
This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu
If none of this applies, then please report this bug using the
command 'ubuntu-bug update-manager' in a terminal.
 
Restoring original system state
Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
I have looked into the /var/log/dist-upgrade
 
there is an error
> Log time: 2012-04-27 11:19:00.472574
Log time: 2012-04-27 11:19:03.977565
Log time: 2012-04-27 11:19:09.158573
Installing libssl1.0.0 as Depends of vsftpd
Installing multiarch-support as PreDepends of libssl1.0.0
Installing libtinfo5 as Depends of libedit2
new important dependency: krb5-locales:i386
Installing krb5-locales as Recommends of libkrb5-3
Installing gcc-4.6-base as Depends of libstdc++6
Installing libdb5.1 as Depends of iproute
Installing db-util as Depends of sasl2-bin
Installing db5.1-util as Depends of db-util
Installing mysql-client-5.5 as Depends of mysql-client
Installing mysql-client-core-5.5 as Depends of mysql-client-5.5
Installing libpam-modules-bin as PreDepends of libpam-modules
Installing python2.7 as Depends of update-manager-core
Installing python2.7-minimal as Depends of python2.7
ignore old unsatisfied important dependency on dbus:i386
Installing libgmp10 as Depends of g++-4.4
Installing libmpfr4 as Depends of g++-4.4
Installing libmysqlclient18 as Depends of libdbd-mysql-perl
Installing mysql-client-5.1 as Depends of mysql-server-5.1
Installing libpciaccess0 as Depends of libdrm-intel1
Installing python-apt-common as Depends of python-apt
new important dependency: xz-lzma:i386
Installing xz-lzma as Recommends of python-apt
Installing libnl-3-200 as Depends of quota
Installing libnl-genl-3-200 as Depends of quota
ignore old unsatisfied important dependency on bash-completion:i386
Installing libp11-kit0 as Depends of libgnutls26
Installing g++-4.6 as Depends of g++
Installing gcc-4.6 as Depends of g++-4.6
Installing cpp-4.6 as Depends of gcc-4.6
Installing libmpc2 as Depends of cpp-4.6
Installing libquadmath0 as Depends of gcc-4.6
Installing libstdc++6-4.6-dev as Depends of g++-4.6
Installing librtmp0 as Depends of libcurl3-gnutls
Installing upstart as Depends of udev
new important dependency: php5-dev:i386
Installing php5-dev as Recommends of php-pear
Installing autoconf as Depends of php5-dev
Installing m4 as Depends of autoconf
Installing automake as Recommends of autoconf
Installing libssl-dev as Depends of php5-dev
Installing libssl-doc as Recommends of libssl-dev
Installing shtool as Depends of php5-dev
Installing ubuntu-keyring as Depends of apt
ignore old unsatisfied important dependency on bsdmainutils:i386
Installing mysql-server-5.5 as Depends of mysql-server
Installing mysql-server-core-5.5 as Depends of mysql-server-5.5
Installing upstart as Depends of mysql-server-5.5
new important dependency: ecryptfs-utils:i386
Installing ecryptfs-utils as Recommends of adduser
Installing libecryptfs0 as Depends of ecryptfs-utils
Installing libnss3 as Depends of libecryptfs0
Installing libnspr4 as Depends of libnss3
Installing gettext-base as Depends of ecryptfs-utils
Installing keyutils as Depends of ecryptfs-utils
Installing libnss3-1d as Depends of ecryptfs-utils
Installing cryptsetup as Recommends of ecryptfs-utils
Installing dmsetup as Depends of cryptsetup
Installing libdevmapper1.02.1 as Depends of dmsetup
Installing cryptsetup-bin as Depends of cryptsetup
Installing libcryptsetup4 as Depends of cryptsetup-bin
Installing lsof as Recommends of ecryptfs-utils
Installing rsync as Recommends of ecryptfs-utils
Installing libdpkg-perl as Depends of dpkg-dev
new important dependency: libalgorithm-merge-perl:i386
Installing libalgorithm-merge-perl as Recommends of dpkg-dev
Installing libalgorithm-diff-perl as Depends of libalgorithm-merge-perl
Installing libalgorithm-diff-xs-perl as Recommends of libalgorithm-diff-perl
Installing libjpeg8 as Depends of libgd2-xpm
Installing libjpeg-turbo8 as Depends of libjpeg8
Installing libpython2.7 as Depends of vim
Installing libswitch-perl as Depends of perl-modules
Installing libclass-isa-perl as Depends of perl-modules
Installing liblzma5 as Depends of xz-utils
Installing keyboard-configuration as Depends of console-setup
Installing libgssapi3-heimdal as Depends of libldap-2.4-2
Installing libasn1-8-heimdal as Depends of libgssapi3-heimdal
Installing libroken18-heimdal as Depends of libasn1-8-heimdal
Installing libhcrypto4-heimdal as Depends of libgssapi3-heimdal
Installing libheimntlm0-heimdal as Depends of libgssapi3-heimdal
Installing libkrb5-26-heimdal as Depends of libheimntlm0-heimdal
Installing libheimbase1-heimdal as Depends of libkrb5-26-heimdal
Installing libhx509-5-heimdal as Depends of libkrb5-26-heimdal
Installing libwind0-heimdal as Depends of libhx509-5-heimdal
ignore old unsatisfied important dependency on uuid-runtime:i386
Installing libtinfo-dev as Depends of libreadline6-dev
Installing libelf1 as Depends of libglib2.0-0
Installing libffi6 as Depends of libglib2.0-0
ignore old unsatisfied important dependency on libglib2.0-data:i386
ignore old unsatisfied important dependency on shared-mime-info:i386
Installing libmount1 as PreDepends of mount
new important dependency: ssh-import-id:i386
Installing ssh-import-id as Recommends of openssh-server
Installing mountall as Depends of initscripts
Installing libdrm-nouveau1a as Depends of plymouth
ignore old unsatisfied important dependency on plymouth-theme-ubuntu-text:i386
ignore old unsatisfied important dependency on bash-completion:i386
ignore old unsatisfied important dependency on bsdmainutils:i386
Starting
Starting 2
Investigating (0) udev [ i386 ] < 151-12 -> 175-0ubuntu9 > ( admin )
Broken udev:i386 Depends on upstart [ i386 ] < 0.6.5-6 -> 1.5-0ubuntu5 > ( admin ) (>= 1.4-0ubuntu6)
Considering upstart:i386 10027 as a solution to udev:i386 32
Holding Back udev:i386 rather than change upstart:i386
Investigating (0) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (0) ifupdown [ i386 ] < 0.6.8ubuntu29.2 -> 0.7~beta2ubuntu8 > ( admin )
Broken ifupdown:i386 Depends on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (>= 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to ifupdown:i386 18
Holding Back ifupdown:i386 rather than change initscripts:i386
Investigating (0) mysql-common [ i386 ] < 5.1.62-0ubuntu0.10.04.1 -> 5.5.22-0ubuntu1 > ( database )
Broken mysql-common:i386 Breaks on mysql-client-5.1 [ i386 ] < 5.1.62-0ubuntu0.10.04.1 > ( database )
Considering mysql-client-5.1:i386 2 as a solution to mysql-common:i386 13
Added mysql-client-5.1:i386 to the remove list
Broken mysql-common:i386 Breaks on mysql-client-core-5.1 [ i386 ] < 5.1.62-0ubuntu0.10.04.1 > ( database )
Considering mysql-client-core-5.1:i386 0 as a solution to mysql-common:i386 13
Added mysql-client-core-5.1:i386 to the remove list
Broken mysql-common:i386 Breaks on mysql-server-5.1 [ i386 ] < 5.1.62-0ubuntu0.10.04.1 > ( database )
Considering mysql-server-5.1:i386 -1 as a solution to mysql-common:i386 13
Added mysql-server-5.1:i386 to the remove list
Broken mysql-common:i386 Breaks on mysql-server-core-5.1 [ i386 ] < 5.1.62-0ubuntu0.10.04.1 > ( database )
Considering mysql-server-core-5.1:i386 1 as a solution to mysql-common:i386 13
Added mysql-server-core-5.1:i386 to the remove list
Fixing mysql-common:i386 via remove of mysql-client-5.1:i386
Fixing mysql-common:i386 via remove of mysql-client-core-5.1:i386
Fixing mysql-common:i386 via remove of mysql-server-5.1:i386
Fixing mysql-common:i386 via remove of mysql-server-core-5.1:i386
Investigating (0) console-setup [ i386 ] < 1.34ubuntu15 -> 1.70ubuntu5 > ( utils )
Broken console-setup:i386 Conflicts on console-terminus [ i386 ] < 4.30-2 > ( fonts )
Considering console-terminus:i386 -1 as a solution to console-setup:i386 11
Added console-terminus:i386 to the remove list
Fixing console-setup:i386 via remove of console-terminus:i386
Investigating (0) plymouth [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( x11 )
Broken plymouth:i386 Depends on udev [ i386 ] < 151-12 -> 175-0ubuntu9 > ( admin ) (>= 166-0ubuntu4)
Considering udev:i386 32 as a solution to plymouth:i386 11
Removing plymouth:i386 rather than change udev:i386
Investigating (0) libdrm-nouveau1a [ i386 ] < none -> 2.4.32-1ubuntu1 > ( libs )
Broken libdrm-nouveau1a:i386 Conflicts on libdrm-nouveau1 [ i386 ] < 2.4.18-1ubuntu3 > ( libs )
Considering libdrm-nouveau1:i386 -1 as a solution to libdrm-nouveau1a:i386 8
Added libdrm-nouveau1:i386 to the remove list
Fixing libdrm-nouveau1a:i386 via remove of libdrm-nouveau1:i386
Investigating (0) xz-lzma [ i386 ] < none -> 5.1.1alpha+20110809-3 > ( utils )
Broken xz-lzma:i386 Conflicts on lzma [ i386 ] < 4.43-14ubuntu2 -> 9.22-2ubuntu1 > ( utils )
Considering lzma:i386 0 as a solution to xz-lzma:i386 5
Added lzma:i386 to the remove list
Conflicts//Breaks against version 4.43-14ubuntu2 for lzma but that is not InstVer, ignoring
Fixing xz-lzma:i386 via remove of lzma:i386
Investigating (0) mysql-server-5.5 [ i386 ] < none -> 5.5.22-0ubuntu1 > ( database )
Broken mysql-server-5.5:i386 Depends on upstart [ i386 ] < 0.6.5-6 -> 1.5-0ubuntu5 > ( admin ) (>= 0.6.7-2)
Considering upstart:i386 10027 as a solution to mysql-server-5.5:i386 0
Holding Back mysql-server-5.5:i386 rather than change upstart:i386
Investigating (0) cryptsetup [ i386 ] < none -> 2:1.4.1-2ubuntu4 > ( admin )
Broken cryptsetup:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( x11 )
Considering plymouth:i386 11 as a solution to cryptsetup:i386 0
Holding Back cryptsetup:i386 rather than change plymouth:i386
Investigating (0) mysql-server [ i386 ] < 5.1.62-0ubuntu0.10.04.1 -> 5.5.22-0ubuntu1 > ( database )
Broken mysql-server:i386 Depends on mysql-server-5.5 [ i386 ] < none -> 5.5.22-0ubuntu1 > ( database )
Considering mysql-server-5.5:i386 0 as a solution to mysql-server:i386 0
Removing mysql-server:i386 rather than change mysql-server-5.5:i386
Investigating (1) mountall [ i386 ] < 2.14 -> 2.36 > ( admin )
Broken mountall:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( x11 )
Considering plymouth:i386 11 as a solution to mountall:i386 10025
Added plymouth:i386 to the remove list
Fixing mountall:i386 via keep of plymouth:i386
Investigating (1) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Try to Re-Instate (1) udev:i386
Investigating (1) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Try to Re-Instate (1) ifupdown:i386
Try to Re-Instate (1) plymouth:i386
Investigating (1) plymouth [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( x11 )
Broken plymouth:i386 Depends on libdrm-nouveau1 [ i386 ] < 2.4.18-1ubuntu3 > ( libs ) (>= 2.4.11-1ubuntu1~)
Considering libdrm-nouveau1:i386 -1 as a solution to plymouth:i386 11
Added libdrm-nouveau1:i386 to the remove list
Broken plymouth:i386 Depends on libplymouth2 [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( libs ) (= 0.8.2-2ubuntu2)
Considering libplymouth2:i386 16 as a solution to plymouth:i386 11
Removing plymouth:i386 rather than change libplymouth2:i386
Investigating (2) mountall [ i386 ] < 2.14 -> 2.36 > ( admin )
Broken mountall:i386 Depends on plymouth [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( x11 )
Considering plymouth:i386 11 as a solution to mountall:i386 10025
Added plymouth:i386 to the remove list
Fixing mountall:i386 via keep of plymouth:i386
Investigating (2) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (2) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (2) plymouth [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( x11 )
Broken plymouth:i386 Depends on libdrm-nouveau1 [ i386 ] < 2.4.18-1ubuntu3 > ( libs ) (>= 2.4.11-1ubuntu1~)
Considering libdrm-nouveau1:i386 -1 as a solution to plymouth:i386 10025
Added libdrm-nouveau1:i386 to the remove list
Broken plymouth:i386 Depends on libplymouth2 [ i386 ] < 0.8.2-2ubuntu2 -> 0.8.2-2ubuntu30 > ( libs ) (= 0.8.2-2ubuntu2)
Considering libplymouth2:i386 16 as a solution to plymouth:i386 10025
Added libplymouth2:i386 to the remove list
Fixing plymouth:i386 via keep of libdrm-nouveau1:i386
Fixing plymouth:i386 via keep of libplymouth2:i386
Investigating (2) libdrm-nouveau1a [ i386 ] < none -> 2.4.32-1ubuntu1 > ( libs )
Broken libdrm-nouveau1a:i386 Conflicts on libdrm-nouveau1 [ i386 ] < 2.4.18-1ubuntu3 > ( libs )
Considering libdrm-nouveau1:i386 10025 as a solution to libdrm-nouveau1a:i386 8
Holding Back libdrm-nouveau1a:i386 rather than change libdrm-nouveau1:i386
Investigating (3) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (3) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Try to Re-Instate (3) libplymouth2:i386
Investigating (4) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (4) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (5) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (5) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (6) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (6) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (7) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (7) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (8) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (8) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Investigating (9) base-files [ i386 ] < 5.0.0ubuntu20.10.04.2 -> 6.5ubuntu6 > ( admin )
Broken base-files:i386 Breaks on initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin ) (< 2.88dsf-13.3)
Considering initscripts:i386 31 as a solution to base-files:i386 5212
Upgrading initscripts:i386 due to Breaks field in base-files:i386
Investigating (9) initscripts [ i386 ] < 2.87dsf-4ubuntu17 -> 2.88dsf-13.10ubuntu11 > ( admin )
Broken initscripts:i386 Depends on mountall [ i386 ] < 2.14 -> 2.36 > ( admin ) (>= 2.28)
Considering mountall:i386 10025 as a solution to initscripts:i386 31
Holding Back initscripts:i386 rather than change mountall:i386
Done
ERROR:root:Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
Log time: 2012-04-27 11:19:10.968188
Since then, i have reinstalled the mountall and still got error during upgrade.
 
here is inside of /etc/apt/sources.list
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main


---

### Post by rubylaser on 2012-08-24
To repair this properly, I would back up your important data and do a fresh install of 12.04.

---

### Post by frec on 2012-08-24
I forgot to mention that this is a VPS, and the host doesn't provide ubuntu 12 image as an option in the control panel. Also, The reason I posted a question here is that if possible, I would prefer upgrading because there is a lot of custom configurations for the system, and downtime should be as minimal as possible. Thank you.

---

### Post by darkod on 2012-08-24
Not sure if it can help or mess it up more, but to fix broken packages you usually run:
sudo apt-get install -f

Note that I don't guarantee 100% what will happen and since this is VPS with no physical access, run at your own risk. :)

In that log there do seem to be loads of broken package messages but I am not sure if some of them are 'broken' before the upgrade starts or during. Because it seems like during which doesn't make much sense.

---

### Post by frec on 2012-08-24
This is what I get:
> *sudo apt-get install -f*
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am not sure why/when does the package seems to be broken since when I do sudo apt-get update and also sudo apt-get update, I don't get any messages. I assumed everything has been fixed since then.
Any suggestion/input on how I can proceed with the upgrade smoothly is greatly appreciated. Thank you.

---

### Post by darkod on 2012-08-24
Well, you can try the do-release-upgrade again but if it fails I don't have any other ideas.

---

### Post by arrrghhh on 2012-08-24
> **frec said:**
> Any suggestion/input on how I can proceed with the upgrade smoothly is greatly appreciated. Thank you.

I am looking into upgrading from 10.04 to 12.04.1 myself soon.  It seems with any Linux (or perhaps Ubuntu?) distribution upgrade, the recommendation is always to do a backup and clean install.

For whatever reason, upgrading is NOT advised, because of these types of issues.

Based on the error output, there's a TON of packages that have been held back/broken for one reason or another.  I assume it's this large list of packages that is causing your issue.

I wish I could help more.  I think I'm still going to attempt an upgrade to 12.04.1, but I definitely have backed up all my configs etc in case I do have to reinstall.

As you're running a VPS that doesn't have 12.04 as an option, it might be best for you to wait until they do.  10.04 is going to be supported on the Server platform for a very long time, so you have plenty of time for your VPS to catch up.

---

### Post by cariboo on 2012-08-24
You are missing an important step, you have to make sure your current installation is fully up-to-date, before doing an upgrade to a new version. Run the following commands first before trying to upgrade:

```
sudo apt-get update
```

followed by

```
sudo apt-get dist-upgrade
```

Once the above commands have run, next:

```
sudo apt-get install update-manager-core
```

followed by:

```
sudo do-release-upgrade
```

---

### Post by arrrghhh on 2012-08-24
cariboo907,

Thanks for that post.  I understand the reasoning behind all the commands, except for the install of update-manager-core.

What does this do?  Does it apply to the server platform?  Thanks.

---

### Post by LHammonds on 2012-08-24
The core is a prerequisite to do the release upgrade as noted in the upgrade documentation

---

### Post by arrrghhh on 2012-08-24
> **LHammonds said:**
> The core is a prerequisite to do the release upgrade as noted in the upgrade documentation

Yes, but neither you nor the docs have explained why this step is necessary, or even what it does (other than install update-manager-core...)

---

### Post by frec on 2012-08-24
> **darkod said:**
> Well, you can try the do-release-upgrade again but if it fails I don't have any other ideas.
I have tried sudo do-release-upgrade again, but it still gives me the same error as before.
> **cariboo907 said:**
> You are missing an important step, you have to make sure your current installation is fully up-to-date, before doing an upgrade to a new version. Run the following commands first before trying to upgrade:

```
sudo apt-get update
```followed by

```
sudo apt-get dist-upgrade
```Once the above commands have run, next:

```
sudo apt-get install update-manager-core
```followed by:

```
sudo do-release-upgrade
```
As i stated before, I have updated & upgraded all the packages.
> *sudo apt-get update*
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
Reading package lists... Done
> *sudo apt-get dist-upgrade*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I have already installed update-manager-core beforehand; otherwise, it wouldn't let me sudo do-release-upgrade.> *sudo apt-get install update-manager-core*
Reading package lists... Done
Building dependency tree
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by LHammonds on 2012-08-24
> **arrrghhh said:**
> Yes, but neither you nor the docs have explained why this step is necessary, or even what it does (other than install update-manager-core...)

From my understanding, it helps insure a smooth upgrade when going between major versions.  It is a "core" component (eg required) part of the update manager.  But I have not researched that nor do I care to look through the source code.  Have you done a google search for this particular inquiry?

Here is a list of file contained in the package if you want to investigate further: [http://packages.ubuntu.com/precise-updates/i386/update-manager-core/filelist](http://packages.ubuntu.com/precise-updates/i386/update-manager-core/filelist)

---

### Post by arrrghhh on 2012-08-24
> **LHammonds said:**
> From my understanding, it helps insure a smooth upgrade when going between major versions.  It is a "core" component (eg required) part of the update manager.  But I have not researched that nor do I care to look through the source code.  Have you done a google search for this particular inquiry?

Here is a list of file contained in the package if you want to investigate further: [http://packages.ubuntu.com/precise-updates/i386/update-manager-core/filelist](http://packages.ubuntu.com/precise-updates/i386/update-manager-core/filelist)

Well, I already had the package installed.  Which is why I'm curious that the directions (and others) have stated it's necessary for upgrading.

I don't think I installed this manually, but the server has been up for quite some time - it's entirely possible I installed that package at one point or another.

---

### Post by LHammonds on 2012-08-24
I upgraded a couple of 10.04 servers to 12.04 and each one already had it.  Probably came in through updates which I perform regularly.  I never installed it manually, that I know for sure.  The 2 upgrades I did went smooth.  I also only used apps from the repository on those servers.

The ones where I had custom built/compiled software like Nagios in my sig, I simply created a new server with 12.04 rather than upgrade in place.

LHammonds

---

### Post by OrangeVixen on 2013-04-22
The problem lies within mountall, more generally to the fact, that it is "broken" and is "held" as started in the /var/log/dist-upgrade logs.

Any package at the end of log that is stated as "held" is often the problem.

I have personally tried removing some of them, but mountall and others are "essential" packages and removing them causes Linux fail to boot up properly (major problems like X video drivers not working).

My only solution when faced with that was to just make a clean install from the 12.04 live CD. After making a backup of all your /home and data, of course.

I have to conclude that upgrading from Lucid to Precise is plagued with the problem of "held" packages, and if and only if you have a very "virgin" Lucid (no custom or 3rd party PPA's) then an upgrade might work.

---


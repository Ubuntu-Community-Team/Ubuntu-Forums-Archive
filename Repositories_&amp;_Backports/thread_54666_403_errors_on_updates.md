---
title: "403 errors on updates"
date: 2005-08-05
forum: Repositories &amp; Backports
---

### Post by brorich on 2005-08-05
Just installed Hoary from the installation CD and all seemed to go well. I ran the package updater thing in the system tray and it says there are 35 updats. i click install and I start getting errors like the following (see below). I have used varying sources.list files including the stock one and one from Ubuntu Guide. I also removed the us from us.archive etc to no avail. Nothing I try is working. I really would like to update/install software but I am unable to.  This error came from running apt-get upgrade aget running apt-get update. Same thing.

Any help would be appreciated



richard@richard:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
The following packages will be upgraded:
  binutils bzip2 dpkg dpkg-dev dselect fetchmail file-roller foomatic-db-hpijs
  foomatic-filters-ppds gaim gaim-data gdb gedit gedit-common gimp gimp-data
  gimp-python gnome-btdownload gnome-menus gtk2-engines-clearlooks gzip hpijs
  libbz2-1.0 libgcc1 libgimp2.0 libgnome-menu0 libgnutls11 libldap2 libmagick6
  libnspr4 libnss3 libpq3 libsmbclient libtiff4 linux-image-2.6.10-5-386
  openoffice.org openoffice.org-bin openoffice.org-gtk-gnome
  openoffice.org-l10n-en powernowd python-xdg python2.4-samba samba
  samba-common smbclient sudo synaptic tcpdump totem totem-gstreamer
  ttf-opensymbol unzip vim vim-common wget xchat xchat-common zlib1g
58 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 123MB of archives.
After unpacking 4506kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgcc1 file-roller hpijs foomatic-db-hpijs gaim gaim-data libgnome-menu0
  gimp gimp-data libgimp2.0 gimp-python gnome-btdownload gnome-menus
  gtk2-engines-clearlooks powernowd python-xdg python2.4-samba smbclient samba
  samba-common synaptic totem totem-gstreamer xchat xchat-common
  foomatic-filters-ppds libsmbclient
Install these packages without verification [y/N]? y
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main libgcc1 1:4.0.0-7ubuntu6~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main dpkg 1.10.27ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main file-roller 2.11.1-0ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe hpijs 2.1.2+0.9.2-2ubuntu3~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main gzip 1.3.5-9ubuntu3.4
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main foomatic-db-hpijs 1.5-20050420-1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libbz2-1.0 1.0.2-2ubuntu0.2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gaim 1:1.4.0-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gaim-data 1:1.4.0-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main zlib1g 1:1.2.2-4ubuntu1.2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main libgnome-menu0 2.10.2-0ubuntu1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libtiff4 3.6.1-5ubuntu0.2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gimp 2.2.8-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gimp-data 2.2.8-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libmagick6 6:6.0.6.2-2.1ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main libgimp2.0 2.2.8-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main vim-common 1:6.3-046+1ubuntu7.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gimp-python 2.2.8-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gnome-btdownload 0.0.20-1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main vim 1:6.3-046+1ubuntu7.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gnome-menus 2.10.2-0ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main gtk2-engines-clearlooks 0.6.2-1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main dselect 1.10.27ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main powernowd 0.96-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe python-xdg 0.14-0ubuntu1~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libgnutls11 1.0.16-13ubuntu0.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main python2.4-samba 3.0.14a-3ubuntu3~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main smbclient 3.0.14a-3ubuntu3~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libldap2 2.1.30-3ubuntu3.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main samba 3.0.14a-3ubuntu3~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main samba-common 3.0.14a-3ubuntu3~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main binutils 2.15-5ubuntu2.2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main dpkg-dev 1.10.27ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main synaptic 0.56+revertedto+officialhoary+0.55+cvs20050406-1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main totem 1.1.1-0ubuntu3~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main totem-gstreamer 1.1.1-0ubuntu3~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main gdb 6.3-5ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main sudo 1.6.8p5-1ubuntu2.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main bzip2 1.0.2-2ubuntu0.2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main fetchmail 6.2.5-12ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main gedit 2.10.2-0ubuntu2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main gedit-common 2.10.2-0ubuntu2
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main wget 1.9.1-10ubuntu2.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libnspr4 2:1.7.10-0ubuntu05.04
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libnss3 2:1.7.10-0ubuntu05.04  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main xchat 2.4.3-0.1ubuntu2~5.04ubp2
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main xchat-common 2.4.3-0.1ubuntu2~5.04ubp2
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main libpq3 7.4.7-2ubuntu2.1
  403 Response denied [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main foomatic-filters-ppds 20050430-1ubuntu1~5.04ubp1
  403 Response denied
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main libsmbclient 3.0.14a-3ubuntu3~5.04ubp1
  403 Response denied
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main linux-image-2.6.10-5-386 2.6.10-34.3
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main openoffice.org-bin 1.1.3-8ubuntu2.3
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main openoffice.org-l10n-en 1.1.3-8ubuntu2.3
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main ttf-opensymbol 1.1.3-8ubuntu2.3
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main openoffice.org 1.1.3-8ubuntu2.3
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main openoffice.org-gtk-gnome 1.1.3-8ubuntu2.3
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main tcpdump 3.8.3-3ubuntu0.4
  403 Response denied [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main unzip 5.51-2ubuntu1.1
  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.10.27ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.10.27ubuntu1.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-9ubuntu3.4_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.2-2ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.2-2ubuntu0.2_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g_1.2.2-4ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g_1.2.2-4ubuntu1.2_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.6.1-5ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.6.1-5ubuntu0.2_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.0.6.2-2.1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.0.6.2-2.1ubuntu1.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-common_6.3-046+1ubuntu7.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim-common_6.3-046+1ubuntu7.1_all.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim_6.3-046+1ubuntu7.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vim/vim_6.3-046+1ubuntu7.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.10.27ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.10.27ubuntu1.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls11/libgnutls11_1.0.16-13ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls11/libgnutls11_1.0.16-13ubuntu0.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openldap2/libldap2_2.1.30-3ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openldap2/libldap2_2.1.30-3ubuntu3.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.15-5ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.15-5ubuntu2.2_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.10.27ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.10.27ubuntu1.1_all.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_6.3-5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_6.3-5ubuntu1.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.8p5-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.8p5-1ubuntu2.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.2-2ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.2-2ubuntu0.2_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/fetchmail/fetchmail_6.2.5-12ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/fetchmail/fetchmail_6.2.5-12ubuntu1.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/file-roller_2.11.1-0ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/file-roller_2.11.1-0ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/hpijs_2.1.2+0.9.2-2ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/hpijs_2.1.2+0.9.2-2ubuntu3~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/foomatic-db-hpijs_1.5-20050420-1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/foomatic-db-hpijs_1.5-20050420-1~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gaim_1.4.0-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gaim_1.4.0-1ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gaim-data_1.4.0-1ubuntu1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gaim-data_1.4.0-1ubuntu1~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgnome-menu0_2.10.2-0ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgnome-menu0_2.10.2-0ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.10.2-0ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.10.2-0ubuntu2_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.10.2-0ubuntu2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.10.2-0ubuntu2_all.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.9.1-10ubuntu2.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gimp_2.2.8-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gimp_2.2.8-1ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gimp-data_2.2.8-1ubuntu1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gimp-data_2.2.8-1ubuntu1~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgimp2.0_2.2.8-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgimp2.0_2.2.8-1ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gimp-python_2.2.8-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gimp-python_2.2.8-1ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gnome-btdownload_0.0.20-1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gnome-btdownload_0.0.20-1~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gnome-menus_2.10.2-0ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gnome-menus_2.10.2-0ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gtk2-engines-clearlooks_0.6.2-1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gtk2-engines-clearlooks_0.6.2-1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mozilla/libnspr4_1.7.10-0ubuntu05.04_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mozilla/libnspr4_1.7.10-0ubuntu05.04_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mozilla/libnss3_1.7.10-0ubuntu05.04_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mozilla/libnss3_1.7.10-0ubuntu05.04_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql/libpq3_7.4.7-2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql/libpq3_7.4.7-2ubuntu2.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-bin_1.1.3-8ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-bin_1.1.3-8ubuntu2.3_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-l10n-en_1.1.3-8ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-l10n-en_1.1.3-8ubuntu2.3_all.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_1.1.3-8ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_1.1.3-8ubuntu2.3_all.deb)  403 Response denied [IP: 82.211.81.138 80]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_1.1.3-8ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_1.1.3-8ubuntu2.3_all.deb)  403 Response denied [IP: 82.211.81.138 80]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk-gnome_1.1.3-8ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk-gnome_1.1.3-8ubuntu2.3_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/powernowd_0.96-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/powernowd_0.96-1ubuntu1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/python-xdg_0.14-0ubuntu1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/python-xdg_0.14-0ubuntu1~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/python2.4-samba_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/python2.4-samba_3.0.14a-3ubuntu3~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/smbclient_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/smbclient_3.0.14a-3ubuntu3~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/samba_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/samba_3.0.14a-3ubuntu3~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/samba-common_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/samba-common_3.0.14a-3ubuntu3~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/synaptic_0.56+revertedto+officialhoary+0.55+cvs20050406-1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/synaptic_0.56+revertedto+officialhoary+0.55+cvs20050406-1~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tcpdump/tcpdump_3.8.3-3ubuntu0.4_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/totem_1.1.1-0ubuntu3~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/totem_1.1.1-0ubuntu3~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/totem-gstreamer_1.1.1-0ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/totem-gstreamer_1.1.1-0ubuntu3~5.04ubp1_i386.deb)  403 Response denied
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.51-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.51-2ubuntu1.1_i386.deb)  403 Response denied [IP: 82.211.81.138 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/xchat_2.4.3-0.1ubuntu2~5.04ubp2_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/xchat_2.4.3-0.1ubuntu2~5.04ubp2_i386.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/xchat-common_2.4.3-0.1ubuntu2~5.04ubp2_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/xchat-common_2.4.3-0.1ubuntu2~5.04ubp2_all.deb)  403 Response deniedFailed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/foomatic-filters-ppds_20050430-1ubuntu1~5.04ubp1_all.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/foomatic-filters-ppds_20050430-1ubuntu1~5.04ubp1_all.deb)  403 Response denied
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libsmbclient_3.0.14a-3ubuntu3~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libsmbclient_3.0.14a-3ubuntu3~5.04ubp1_i386.deb)  403 Response denied
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Mapassy on 2005-08-16
Hi, I think I had similar prob :smile: 

In my list I have got GB instead of US, it is not removed

I just removed # where was needed plus the additional lines from the 
''Unofficial Ubuntu Guide''

The first time I ran apt - update it did not work, but later on it was OK.
I am also newbie, but that's the experience i have got
so hopefully it will be usefull for U :grin:

or someoneelse will help?

---

### Post by Kapre on 2005-08-22
[QUOTE=Mapassy]Hi, I think I had similar prob :smile: 

In my list I have got GB instead of US, it is not removed

I just removed # where was needed plus the additional lines from the 
''Unofficial Ubuntu Guide''

The first time I ran apt - update it did not work, but later on it was OK.
I am also newbie, but that's the experience i have got
so hopefully it will be usefull for U :grin:

or someoneelse will help?[/QUOTE]
 Mapassy - I think you're right because it seems like the repo was not edited (removal of the # on the list).

brorich - so should copy and paste the all that is on [www.ubuntuguide.org/#repositories](www.ubuntuguide.org/#repositories)

---


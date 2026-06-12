---
title: "Updates broken since upgrade to 12.04"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lazymanc on 2012-04-15
Hi, since updating to 12.04 I can't get any updates to work.

I have tried various combinations of apt-get upgrade and apt-get -f install but I'm unsure where to go from here.

Here's the log:

```

phil@phil-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gnome-session : Depends: gnome-session-common (= 3.2.1-0ubuntu6) but 3.2.1-0ubuntu7 is installed
 gvfs : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is installed
        Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is installed
 gvfs-backends : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is installed
                 Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is installed
                Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is installed
 ubuntu-sso-client-qt : Depends: python-ubuntu-sso-client (= 2.99.92-0ubuntu2) but 3.0.0-0ubuntu1 is installed
                        Depends: ubuntu-sso-client (= 2.99.92-0ubuntu2) but 3.0.0-0ubuntu1 is installed
 ubuntuone-control-panel-qt : Depends: python-ubuntuone-control-panel (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is installed
                              Depends: ubuntuone-control-panel (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is installed
                              Depends: ubuntuone-control-panel-common (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
phil@phil-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libstdc++6:i386 libxfixes3:i386 libaccess-bridge-java libxcomposite1:i386 libldap-2.4-2:i386 libroken18-heimdal:i386 libidn11:i386 libnss3:i386
  libwrap0:i386 nspluginwrapper libsamplerate0:i386 libjpeg-turbo8:i386 libx264-116 libfile-homedir-perl libjpeg8:i386 libmagickcore3 libmagickwand3 libasn1-8-heimdal:i386 libjack-jackd2-0:i386
  libiso9660-7 libnspr4-0d:i386 libcairo2:i386 libgnutls26:i386 libgssapi3-heimdal:i386 libtasn1-3:i386 libfreetype6:i386 python-encutils libexpat1:i386 libdatrie1:i386 libavahi-common-data:i386
  libjson0:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386 libp11-kit0:i386 libaccess-bridge-java-jni libwind0-heimdal:i386 libxau6:i386 python-clientform libpixman-1-0:i386 libcups2:i386 libcurl3:i386
  libxinerama1:i386 libkrb5support0:i386 nspluginviewer:i386 libxft2:i386 libvpx0 python-django libmatroska4 libice6:i386 libspeexdsp1:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386 libkeyutils1:i386
  libasound2:i386 libflac8:i386 libxrender1:i386 libhcrypto4-heimdal:i386 python-cssutils-doc libnspr4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 python-django-tagging libasyncns0:i386
  libheimbase1-heimdal:i386 libtiff4:i386 libjasper1:i386 libjpeg62:i386 gtk2-engines-pixbuf libattica0 libavahi-client3:i386 libx11-6:i386 libsasl2-2:i386 libid3tag0 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libmusicbrainz4c2a libpulse0:i386 libmagickcore3-extra libheimntlm0-heimdal:i386 libxdamage1:i386 openoffice.org-common libxcb-render0:i386 librtmp0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libvorbis0a:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386 libxext6:i386 libsasl2-modules:i386 libavahi-common3:i386 libxrandr2:i386 libnss3-1d:i386
  libsndfile1:i386 libsqlite3-0:i386 libgtk2.0-0:i386 libkrb5-26-heimdal:i386 libasound2-plugins:i386 libgpg-error0:i386 libogg0:i386 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-session gvfs gvfs-backends gvfs-daemons gvfs-fuse ubuntu-sso-client-qt ubuntuone-control-panel-gtk ubuntuone-control-panel-qt
Suggested packages:
  desktop-base gnome-session-fallback
The following packages will be upgraded:
  gnome-session gvfs gvfs-backends gvfs-daemons gvfs-fuse ubuntu-sso-client-qt ubuntuone-control-panel-gtk ubuntuone-control-panel-qt
8 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
13 not fully installed or removed.
Need to get 0 B/2,695 kB of archives.
After this operation, 23.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gvfs-daemons:
 gvfs-daemons depends on gvfs-libs (= 1.12.0-0ubuntu4); however:
  Version of gvfs-libs on system is 1.12.0-0ubuntu6.
 gvfs-daemons depends on gvfs-common (= 1.12.0-0ubuntu4); however:
  Version of gvfs-common on system is 1.12.0-0ubuntu6.
dpkg: error processing gvfs-daemons (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gvfs:
 gvfs depends on gvfs-daemons (>= 1.12.0-0ubuntu4); however:
  Package gvfs-daemons is not configured yet.
 gvfs depends on gvfs-daemons (<< 1.12.0-0ubuntu4.1~); however:
  Package gvfs-daemons is not configured yet.
 gvfs depends on gvfs-libs (= 1.12.0-0ubuntu4); however:
  Version of gvfs-libs on system is 1.12.0-0ubuntu6.
 gvfs depends on gvfs-common (= 1.12.0-0ubuntu4); however:
  Version of gvfs-common on system is 1.12.0-0ubuntu6.
dpkg: error processing gvfs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on gvfs (= 1.12.0-0ubuntu4); however:
  Package gvfs is not configured yet.
dpkg: error processing gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on gvfs (= 1.12.0-0ubuntu4); however:
  Package gvfs is not configured yet.
 gvfs-backends depends on gvfs-daemons (= 1.12.0-0ubuntu4); however:
  Package gvfs-daemons is not configured yet.
 gvfs-backends depends on gvfs-libs (= 1.12.0-0ubuntu4); however:
  Version of gvfs-libs on system is 1.12.0-0ubuntu6.
 gvfs-backends depends on gvfs-common (= 1.12.0-0ubuntu4); however:
  Version of gvfs-common on system is 1.12.0-0ubuntu6.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gvfs; however:
  Package gvfs is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                        dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs (>= 1.3.2); however:
  Package gvfs is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on nautilus; however:
  Package nautilus is not configured yet.
 gnome-session depends on gnome-session-common (= 3.2.1-0ubuntu6); however:
  Version of gnome-session-common on system is 3.2.1-0ubuntu7.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus (>= 1:2.91); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-sendto; however:
  Package nautilus-sendto is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-sso-client-qt:
 ubuntu-sso-client-qt depends on python-ubuntu-sso-client (= 2.99.92-0ubuntu2); however:
  Version of python-ubuntu-sso-client on system is 3.0.0-0ubuntu1.
 ubuntu-sso-client-qt depends on ubuntu-sso-client (= 2.99.92-0ubuntu2); however:
  Version of ubuntu-sso-client on system is 3.0.0-0ubuntu1.
dpkg: error processing ubuntu-sso-client-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-control-panel-qt:
 ubuntuone-control-panel-qt depends on python-ubuntuone-control-panel (= 2.99.92-0ubuntu1); however:
  Version of python-ubuntuone-control-panel on system is 3.0.0-0ubuntu1.
 ubuntuone-control-panel-qt depends on ubuntu-sso-client-qt (>= 2.99.92); however:
  Package ubuntu-sso-client-qt is not configured yet.
 ubuntuone-control-panel-qt depends on ubuntuone-control-panel (= 2.99.92-0ubuntu1); however:
  Version of ubuntuone-control-panel on system is 3.0.0-0ubuntu1.
 ubuntuone-control-panel-qt depends on ubuntuone-control-panel-common (= 2.99.92-0ubuntu1); however:
  Version of ubuntuone-control-panel-common on system is 3.0.0-0ubuntu1.
dpkg: error processing ubuntuone-control-panel-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntuone-control-panel-gtk:
 ubuntuone-control-panel-gtk depends on ubuntuone-control-panel-qt (= 2.99.92-0ubuntu1); however:
  Package ubuntuone-control-panel-qt is not configured yet.
dpkg: error processing ubuntuone-control-panel-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 gvfs-daemons
 gvfs
 gvfs-fuse
 gvfs-backends
 brasero
 nautilus
 gnome-session
 nautilus-sendto
 nautilus-share
 ubuntu-desktop
 ubuntu-sso-client-qt
 ubuntuone-control-panel-qt
 ubuntuone-control-panel-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It looks like the libs installed are newer than the ones required, but I'm not sure how this could happen as I just ran update-manager -d from 11.10.

This is my sources.list:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
~                                                                                                                                                                                                            

```

Would really appreciate some help with this, cheers.

---

### Post by kc1di on 2012-04-15
Question when you say updated to 12.04 do you mean you did a distro-upgrade from another version or did you do a complete install? 

could you post the contents of the following file ```
/etc/apt/sources.list
```

You might want to do the following from a terminal and see if that frees up things also from a terminal copy and past the following commands one at a time:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

---

### Post by lazymanc on 2012-04-15
Hi kc1di, I updated from 11.10 using the distro upgrade (Alt-F2 then update-manager -d).

I did paste my sources.list in the original post, the only thing I've changed since the update was to remove the 11.10 CD from the list.

I've tried changing the source server I was using to see if it was just a sync issue but whichever one I try it doesn't seem to make a difference. It's currently set to "Main Server".

Output from sudo rm /var/lib/apt/lists/* -vf:
```

phil@phil-desktop:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources'
removed `/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release'
removed `/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

```

Output from sudo apt-get update:
```

phil@phil-desktop:~$ sudo apt-get update
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease                                           
Ign http://archive.ubuntu.com precise-backports InRelease                                          
Ign http://archive.ubuntu.com precise-security InRelease                                           
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                                        
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]        
Get:3 http://archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://dl.google.com stable InRelease                                   
Get:4 http://archive.ubuntu.com precise-security Release.gpg [198 B]
Ign http://extras.ubuntu.com precise InRelease                              
Get:5 http://archive.ubuntu.com precise Release [49.6 kB]
Get:6 http://dl.google.com stable Release.gpg [198 B]                    
Get:7 http://extras.ubuntu.com precise Release.gpg [72 B]                             
Get:8 http://archive.ubuntu.com precise-updates Release [28.9 kB]                     
Get:9 http://archive.ubuntu.com precise-backports Release [28.9 kB]                                    
Get:10 http://dl.google.com stable Release [1,347 B]                                                   
Get:11 http://extras.ubuntu.com precise Release [11.9 kB]                                                     
Get:12 http://archive.ubuntu.com precise-security Release [28.9 kB]                      
Get:13 http://dl.google.com stable/main amd64 Packages [1,233 B]                                                   
Get:14 http://archive.ubuntu.com precise/main Sources [933 kB]                                    
Get:15 http://extras.ubuntu.com precise/main Sources [14 B]                                                             
Get:16 http://extras.ubuntu.com precise/main amd64 Packages [14 B]                                          
Get:17 http://extras.ubuntu.com precise/main i386 Packages [14 B]                                            
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                          
Get:18 http://dl.google.com stable/main i386 Packages [1,240 B]                                              
Get:19 http://archive.ubuntu.com precise/restricted Sources [5,467 B]                
Get:20 http://archive.ubuntu.com precise/universe Sources [5,069 kB]                                      
Ign http://extras.ubuntu.com precise/main Translation-en_GB                                               
Ign http://extras.ubuntu.com precise/main Translation-en                                                  
Get:21 http://archive.ubuntu.com precise/multiverse Sources [157 kB]                    
Get:22 http://archive.ubuntu.com precise/main amd64 Packages [1,289 kB]           
Get:23 http://archive.ubuntu.com precise/restricted amd64 Packages [8,451 B]             
Get:24 http://archive.ubuntu.com precise/universe amd64 Packages [4,833 kB]               
Get:25 http://archive.ubuntu.com precise/multiverse amd64 Packages [120 kB]                                                                                                                                 
Get:26 http://archive.ubuntu.com precise/main i386 Packages [1,292 kB]                                                                                                                                      
Get:27 http://archive.ubuntu.com precise/restricted i386 Packages [8,388 B]                                                                                                                                 
Get:28 http://archive.ubuntu.com precise/universe i386 Packages [4,842 kB]                                                                                                                                  
Get:29 http://archive.ubuntu.com precise/multiverse i386 Packages [122 kB]                                                                                                                                  
Get:30 http://archive.ubuntu.com precise/main TranslationIndex [3,570 B]                                                                                                                                    
Get:31 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,540 B]                                                                                                                              
Get:32 http://archive.ubuntu.com precise/restricted TranslationIndex [2,464 B]                                                                                                                              
Get:33 http://archive.ubuntu.com precise/universe TranslationIndex [2,784 B]                                                                                                                                
Get:34 http://archive.ubuntu.com precise-updates/main Sources [14 B]                                                                                                                                        
Get:35 http://archive.ubuntu.com precise-updates/restricted Sources [14 B]                                                                                                                                  
Get:36 http://archive.ubuntu.com precise-updates/universe Sources [14 B]                                                                                                                                    
Get:37 http://archive.ubuntu.com precise-updates/multiverse Sources [14 B]                                                                                                                                  
Get:38 http://archive.ubuntu.com precise-updates/main amd64 Packages [14 B]                                                                                                                                 
Get:39 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [14 B]                                                                                                                           
Get:40 http://archive.ubuntu.com precise-updates/universe amd64 Packages [14 B]                                                                                                                             
Get:41 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [14 B]                                                                                                                           
Get:42 http://archive.ubuntu.com precise-updates/main i386 Packages [14 B]                                                                                                                                  
Get:43 http://archive.ubuntu.com precise-updates/restricted i386 Packages [14 B]                                                                                                                            
Get:44 http://archive.ubuntu.com precise-updates/universe i386 Packages [14 B]                                                                                                                              
Get:45 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14 B]                                                                                                                            
Get:46 http://archive.ubuntu.com precise-updates/main TranslationIndex [70 B]                                                                                                                               
Get:47 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [70 B]                                                                                                                         
Get:48 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [70 B]                                                                                                                         
Get:49 http://archive.ubuntu.com precise-updates/universe TranslationIndex [70 B]                                                                                                                           
Get:50 http://archive.ubuntu.com precise-backports/main Sources [14 B]                                                                                                                                      
Get:51 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                                                                                
Get:52 http://archive.ubuntu.com precise-backports/universe Sources [14 B]                                                                                                                                  
Get:53 http://archive.ubuntu.com precise-backports/multiverse Sources [14 B]                                                                                                                                
Get:54 http://archive.ubuntu.com precise-backports/main amd64 Packages [14 B]                                                                                                                               
Get:55 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                                                                                                         
Get:56 http://archive.ubuntu.com precise-backports/universe amd64 Packages [14 B]                                                                                                                           
Get:57 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]                                                                                                                         
Get:58 http://archive.ubuntu.com precise-backports/main i386 Packages [14 B]                                                                                                                                
Get:59 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                                                                                          
Get:60 http://archive.ubuntu.com precise-backports/universe i386 Packages [14 B]                                                                                                                            
Get:61 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]                                                                                                                          
Get:62 http://archive.ubuntu.com precise-backports/main TranslationIndex [70 B]                                                                                                                             
Get:63 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [70 B]                                                                                                                       
Get:64 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                                                                                                                       
Get:65 http://archive.ubuntu.com precise-backports/universe TranslationIndex [70 B]                                                                                                                         
Get:66 http://archive.ubuntu.com precise-security/main Sources [14 B]                                                                                                                                       
Get:67 http://archive.ubuntu.com precise-security/restricted Sources [14 B]                                                                                                                                 
Get:68 http://archive.ubuntu.com precise-security/universe Sources [14 B]                                                                                                                                   
Get:69 http://archive.ubuntu.com precise-security/multiverse Sources [14 B]                                                                                                                                 
Get:70 http://archive.ubuntu.com precise-security/main amd64 Packages [14 B]                                                                                                                                
Get:71 http://archive.ubuntu.com precise-security/restricted amd64 Packages [14 B]                                                                                                                          
Get:72 http://archive.ubuntu.com precise-security/universe amd64 Packages [14 B]                                                                                                                            
Get:73 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [14 B]                                                                                                                          
Get:74 http://archive.ubuntu.com precise-security/main i386 Packages [14 B]                                                                                                                                 
Get:75 http://archive.ubuntu.com precise-security/restricted i386 Packages [14 B]                                                                                                                           
Get:76 http://archive.ubuntu.com precise-security/universe i386 Packages [14 B]                                                                                                                             
Get:77 http://archive.ubuntu.com precise-security/multiverse i386 Packages [14 B]                                                                                                                           
Get:78 http://archive.ubuntu.com precise-security/main TranslationIndex [70 B]                                                                                                                              
Get:79 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [70 B]                                                                                                                        
Get:80 http://archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]                                                                                                                        
Get:81 http://archive.ubuntu.com precise-security/universe TranslationIndex [70 B]                                                                                                                          
Get:82 http://archive.ubuntu.com precise/main Translation-en_GB [77.3 kB]                                                                                                                                   
Get:83 http://archive.ubuntu.com precise/main Translation-en [725 kB]                                                                                                                                       
Get:84 http://archive.ubuntu.com precise/multiverse Translation-en_GB [79.9 kB]                                                                                                                             
Get:85 http://archive.ubuntu.com precise/multiverse Translation-en [94.3 kB]                                                                                                                                
Get:86 http://archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]                                                                                                                             
Get:87 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                                                                                                
Get:88 http://archive.ubuntu.com precise/universe Translation-en_GB [5,416 B]                                                                                                                               
Get:89 http://archive.ubuntu.com precise/universe Translation-en [3,371 kB]                                                                                                                                 
Get:90 http://archive.ubuntu.com precise-updates/main Translation-en [14 B]                                                                                                                                 
Get:91 http://archive.ubuntu.com precise-updates/multiverse Translation-en [14 B]                                                                                                                           
Get:92 http://archive.ubuntu.com precise-updates/restricted Translation-en [14 B]                                                                                                                           
Get:93 http://archive.ubuntu.com precise-updates/universe Translation-en [14 B]                                                                                                                             
Get:94 http://archive.ubuntu.com precise-backports/main Translation-en [14 B]                                                                                                                               
Get:95 http://archive.ubuntu.com precise-backports/multiverse Translation-en [14 B]                                                                                                                         
Get:96 http://archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                                                                                                         
Get:97 http://archive.ubuntu.com precise-backports/universe Translation-en [14 B]                                                                                                                           
Get:98 http://archive.ubuntu.com precise-security/main Translation-en [14 B]                                                                                                                                
Get:99 http://archive.ubuntu.com precise-security/multiverse Translation-en [14 B]                                                                                                                          
Get:100 http://archive.ubuntu.com precise-security/restricted Translation-en [14 B]                                                                                                                         
Get:101 http://archive.ubuntu.com precise-security/universe Translation-en [14 B]                                                                                                                           
Ign http://dl.google.com stable/main TranslationIndex                                                                                                                                                       
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en                                                                                                                                                         
Fetched 23.2 MB in 37s (620 kB/s)                                                                                                                                                                           
Reading package lists... Done

```

---

### Post by dino99 on 2012-04-15
so now it should be ok, right ?

open synaptic, install it if you need, then try to install/updrade the packages not all at the same time, one of them is probably conflicting with an other pending one.

but for future: remember that dist-upgrade works when the release is done, not before. (but now you know why) :lolflag:

---

### Post by lazymanc on 2012-04-15
Nope, still the same - if I try and open software centre I get this:
[IMG]http://i.imgur.com/8QSEL.png[/IMG]

If I try and install via CLI I get this:

```

phil@phil-desktop:~$ sudo apt-get install synaptic
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 gnome-session : Depends: gnome-session-common (= 3.2.1-0ubuntu6) but 3.2.1-0ubuntu7 is to be installed
 gvfs : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is to be installed
        Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is to be installed
 gvfs-backends : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is to be installed
                 Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is to be installed
 gvfs-daemons : Depends: gvfs-libs (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is to be installed
                Depends: gvfs-common (= 1.12.0-0ubuntu4) but 1.12.0-0ubuntu6 is to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
 ubuntu-sso-client-qt : Depends: python-ubuntu-sso-client (= 2.99.92-0ubuntu2) but 3.0.0-0ubuntu1 is to be installed
                        Depends: ubuntu-sso-client (= 2.99.92-0ubuntu2) but 3.0.0-0ubuntu1 is to be installed
 ubuntuone-control-panel-qt : Depends: python-ubuntuone-control-panel (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
                              Depends: ubuntuone-control-panel (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
                              Depends: ubuntuone-control-panel-common (= 2.99.92-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by dino99 on 2012-04-15
try:  sudo dpkg-reconfigure -phigh -a

(can take a while, dont stop it)

or simply log out/in or reboot

---

### Post by kc1di on 2012-04-15
you can also try ```
sudo dpkg --configure -a 
``` if you haven't already.
I'd also run ```
sudo apt-get clean && sudo apt-get autoclean
```

if that all fails do a clean install of 12.04 ( I know you didn't want to hear that :)  ) I haven't had very good luck with upgrades.

---


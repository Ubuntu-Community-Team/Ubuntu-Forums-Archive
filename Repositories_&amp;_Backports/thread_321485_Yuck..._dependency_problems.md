---
title: "Yuck... dependency problems"
date: 2006-12-19
forum: Repositories &amp; Backports
---

### Post by crazybrit4967 on 2006-12-19
Here's what happens when I try to install just about any package:
```
ed@ed-desktop:~$ sudo aptitude install mozilla-thunderbird
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager 
  adept-notifier adept-updater akregator apt-index-watcher ark arts 
  bogofilter bogofilter-bdb bogofilter-common debtags digikam 
  gtk2-engines-gtk-qt gwenview hwdb-client-kde k3b kaffeine kaffeine-xine 
  karm katapult kate kaudiocreator kbstate kcron kde-guidance 
  kde-guidance-powermanager kde-icons-mono kde-systemsettings 
  kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins 
  kdemultimedia-kfile-plugins kdenetwork-filesharing 
  kdenetwork-kfile-plugins kdepasswd kdepim-kresources kdepim-wizards 
  kdeprint kdm kdnssd keep kio-apt kio-locate kipi-plugins klipper kmag 
  kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base 
  kmplayer-konq-plugins knetworkconf konq-plugins konqueror-nsplugins 
  konversation kooka kopete kpdf kpf kppp krdc krfb kscd kscreensaver 
  ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard 
  ksysguardd ksystemlog ktorrent kubuntu-default-settings kubuntu-docs 
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal 
  language-selector-qt libavahi-compat-libdnssd1 libcurl3-gnutls 
  libexif-dev libgmp3c2 libgphoto2-2-dev libgsl0 libimlib2 
  libjasper-runtime libjpeg-progs libk3b2 libkexif1 libkipi0 liblockdev1 
  libmagick++9c2a libpoppler1-qt libpythonize0 libqt4-core libqt4-gui 
  libqt4-qt3support libqt4-sql librsync1 libskim0 libsqlite0 libtdb1 
  libungif4g openoffice.org-kde poster psutils pykdeextensions 
  python-elementtree python-kde3 python-qt4 python2.4-dev qca-tls qobex 
  rdiff-backup scim-qtimm skim speedcrunch vorbis-tools wlassistant 
The following NEW packages will be installed:
  mozilla-thunderbird 
0 packages upgraded, 1 newly installed, 126 to remove and 0 not upgraded.
Need to get 10.7MB of archives. After unpacking 247MB will be freed.
Do you want to continue? [Y/n/?] 
```
I'm pretty sure this is because I installed Basket 0.6 from their website (the Ubuntu repos only have 0.5) and it made me upgrade a bunch of kde-related packages.  Anyone know anything I can do about all this - preferably without uninstalling anything?

Edit - never mind, I think I soved the problem - I used Synaptic instead of Aptitude and it installs fine.

---


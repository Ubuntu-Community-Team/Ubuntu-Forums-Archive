---
title: "Howto remove kubuntu-desktop !"
date: 2007-03-02
forum: The Cafe
---

### Post by drfalkor on 2007-03-02
Installed kde with this command ->[COLOR="Sienna"] sudo [COLOR="Sienna"]apt-get install kubuntu-desktop[/COLOR][/COLOR] ?
well, here is how you remove every single kde app, but not the kde-usplash ! 

[COLOR="Red"]**BE SURE THAT YOU HAVE GDM AS DEFAULT BEFORE YOU DO THIS, AND THAT YOU ARE NOT USING KDE WHEN YOU ARE DOING THIS !**[/COLOR]

Open a terminal, then
> sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apt-index-watcher ark arts bogofilter bogofilter-bdb bogofilter-common dcraw debtags digikam enscript gtk2-engines-gtk-qt gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libavahi-compat-libdnssd1 libavahi-qt3-1 libdbus-qt-1-1c2 libexif-dev libflac++5c2 libgmp3c2 libgpgme11 libgphoto2-2-dev libgsl0 libifp4 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmagick++9c2a libmimelib1c2a libmysqlclient15off libnjb5 libnss-mdns libpoppler1-qt libpq4 libpythonize0 libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsqlite0 libtdb1 libtunepimp3 mysql-common openoffice.org-kde openoffice.org-style-crystal perl-suid poster psutils pykdeextensions python-elementtree python-kde3 python-qt3 python-qt4 python-sip4 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch wlassistant
If you failed the first time, try to reboot then log directly into gnome or any terminal- then try it again.
(do this at your own risk)

I am not sure if this will work if you have installed kde in any other ways.

---

### Post by Kobalt on 2007-03-02
This is a copy/paste of an aysiu entry on [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) ...

---

### Post by drfalkor on 2007-03-02
well, no.. are you complaining ? 
Actually i did a sudo apt-get install kubuntu-desktop, copyed the list, and removed the spaces in gedit.. and I dint know such a howto existed

---

### Post by adam.tropics on 2007-03-02
> **drfalkor said:**
> well, no.. are you complaining ? 
Actually i did a sudo apt-get install kubuntu-desktop, copyed the list, and removed the spaces in gedit.. and I dint know such a howto existed

Wouldn't 'aptitude' rather than 'apt-get' be better in the first place, since it would remove it all anyway?

---

### Post by drfalkor on 2007-03-02
> **adam.tropics said:**
> Wouldn't 'aptitude' rather than 'apt-get' be better in the first place, since it would remove it all anyway?

I dont know :)

---

### Post by Niko38752 on 2007-03-02
Yeah, it would. Although it doesn't remove absolutely everything kubuntu-desktop installed, or at least it didn't when I installed and removed ubuntu-desktop with it.

---


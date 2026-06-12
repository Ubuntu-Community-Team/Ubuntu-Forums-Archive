---
title: "Installing kubuntu-desktop on gnome.... (what a mass..)"
date: 2007-08-05
forum: The Cafe
---

### Post by Kosimo on 2007-08-05
Wanted to try KDE...

terminal:  sudo apt-get install kubuntu-desktop....

It installed more than 400 MB to my hard drive.
I give it a try to KDE, but didn't like it.

My boot screen changed to kubuntu, my gnome changed my fonts, now firefox have very strange fonts.. I have lots of kde programs in gnome, like kopete, konkeror...  WOW!... I wanted to uninstall it by typing sudo apt-get remove kubuntu-desktop...    (It only delete 45k's to my hard drive!!!!!!!!!!)

Restart...
Still kubuntu boot screen
Still strange fonts in gnome
Still all this kde programs....

****.....

I don't want to format my hard drive.......

Can I fix this??    
1- I want to recover this 400+ MB used by installing KDE...
2- I want ubuntu boot screen back!
3- I want to have the same fonts I had before in gnome... :(

I am may asking too much???

---

### Post by Kosimo on 2007-08-05
sorry, I post it in the wrong place... Can some admin move to absolute beginner forum? Thanks.

---

### Post by needtolookatascreenshot on 2007-08-05
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by smoker on 2007-08-05
hi, have a look at this link, it uses aptitude to install and remove though. there are links on the page that may help though;
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

best of luck

---

### Post by henrismail on 2007-08-05
Next time you should use aptitude it keeps track of all the dependencies. To uninstall now you will have to 

```
 sudo apt-get remove --purge adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libavahi-compat-libdnssd1 libavahi-qt3-1 libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libifp4 libimlib2 libjasper-runtime libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmtp5 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch  
```

---

### Post by Kosimo on 2007-08-05
Cool!.
Thank you guys. Next time I will use aptitude.

Almost everything is fixed.

Ubuntu Boot screen.
Recovered all my HD space.

But, I'm still having this "new" strange fonts in Firefox. Ugly fonts...  

Any idea guys?

Thank you anyway to everyone.

---

### Post by happy-and-lost on 2007-08-05
I think deleting your ~/.fontconfig folder should force your font cache to reload with Gnome's settings.

---

### Post by Kosimo on 2007-08-05
> **happy-and-lost said:**
> I think deleting your ~/.fontconfig folder should force your font cache to reload with Gnome's settings.

where can I find this folder?
Is not in root directory

---

### Post by happy-and-lost on 2007-08-05
The **~** means your /home/$USER directory. .fontconfig is a hidden folder, press Ctrl+H to unhide it.

---

### Post by dptxp on 2007-08-05
Best way to try kde is to install kde-core, not kubuntu-desktop. I have found both to coexist comfortably in this manner.

---


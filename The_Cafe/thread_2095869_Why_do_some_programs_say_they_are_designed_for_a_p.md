---
title: "Why do some programs say they are designed for a particular desktop enviroment"
date: 2012-12-18
forum: The Cafe
---

### Post by Arielxgbarton on 2012-12-18
Some programs say, on ubuntu software center, that they are designed for a particular desktop enviroment, for example

dolphin       -> KDE
Kdenlive      -> KDE
Gedit         -> Gnome

et cetera

What is the purpose of that? That software all works fine on LXDE and Unity (the desktop enviroments I use, I dont use KDE) So what is the point of saying that it is for KDE or GNOME, et cetera

---

### Post by Jakin on 2012-12-18
Designed for.

For example if you get a KDE based app, you may have to also download alot of KDE libraries and packages just to make that one app work.
Likewise running Gnome apps in KDE.n

---

### Post by vasa1 on 2012-12-18
> **Arielxgbarton said:**
> Some programs say, on ubuntu software center, that they are designed for a particular desktop enviroment, for example

dolphin       -> KDE
Kdenlive      -> KDE
Gedit         -> Gnome

et cetera

What is the purpose of that? That software all works fine on LXDE and Unity (the desktop enviroments I use, I dont use KDE) So what is the point of saying that it is for KDE or GNOME, et cetera
As Jakin pointed out, it's not just dolphin or gedit or whatever other app that will be installed but a whole lot of dependencies will be pulled in.

One way to see the "extras" that will come with dolphin if one wants to install it on a pure Ubuntu, for example, is to start with  a pure Ubuntu installation then run **apt-get install -s dolphin**. No need for sudo since the -s switch indicates a simulation.
On my system, I see
```
The following NEW packages will be installed:
  cryptsetup-bin docbook-xml docbook-xsl dolphin gstreamer0.10-alsa gstreamer0.10-pulseaudio icoutils kate-data katepart kde-runtime kde-runtime-data
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools kubuntu-debug-installer libattica0.4 libcanberra-pulse libclucene0ldbl libcryptsetup4 libdbusmenu-qt2
  libdlrestrictions1 libexiv2-12 libkactivities-bin libkactivities6 libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkonq-common libkonq5-templates libkonq5abi1 libkparts4 libkpty4 libkrosscore4 libktexteditor4 libkxmlrpcclient4 liblvm2app2.2
  libnepomuk4 libnepomukcore4abi1 libnepomukquery4a libnepomuksync4 libnepomukutils4 libntrack-qt4-1 libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1
  libpulsedsp libqapt-runtime libqapt1 libqca2 libqt4-opengl libsgutils2-2 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4
  libvirtodbc0 libxml2-utils mtools nepomuk-core nepomuk-core-data ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript pulseaudio pulseaudio-module-x11 pulseaudio-utils qapt-batch rtkit sgml-data
  shared-desktop-ontologies soprano-daemon udisks virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 upgraded, **100 newly installed**, 0 to remove and 0 not upgraded.

```

(I don't have much of KDE except whatever came along when I installed Retext.)

---

### Post by Arielxgbarton on 2012-12-18
And so, does that mean, for a basic text editor for example, if used on LXDE, Leafpad would be the best one as it is designed for LXDE and no extra packages would be required

---

### Post by Jvdy on 2012-12-18
cause its use a different engine/framework
gnome use gtk+
and kde use qt 
more about gtk [http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)
more about qt [http://en.wikipedia.org/wiki/Qt_%28framework%29](http://en.wikipedia.org/wiki/Qt_%28framework%29)

---

### Post by vasa1 on 2012-12-18
> **Arielxgbarton said:**
> And so, does that mean, for a basic text editor for example, if used on LXDE, Leafpad would be the **best** one as it is designed for LXDE and no extra packages would be required
What is your criterion for "best"? Is it usability? Features? Minimal size of install?

---

### Post by zombifier25 on 2012-12-18
> **Jvdy said:**
> cause its use a different engine/framework
gnome use gtk+
and kde use qt 
more about gtk [http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)
more about qt [http://en.wikipedia.org/wiki/Qt_%28framework%29](http://en.wikipedia.org/wiki/Qt_%28framework%29)

Not a valid reason actually. Ubuntu One control panel uses Qt. Unity 2D uses Qt.

The difference is that KDE apps integrate deeply with KDE, while GNOME apps integrate deeply with GNOME (gconf, gsettings, Seahorse,..).

---

### Post by dannyboy79 on 2012-12-18
> **Arielxgbarton said:**
> And so, does that mean, for a basic text editor for example, if used on LXDE, Leafpad would be the best one as it is designed for LXDE and no extra packages would be required
the "best" app would be the one that does what you need it to do plain and simple. I use xubuntu (switched from ubuntu due to unity) but prefer gedit over mousepad. as long as you have enough space for the extra libraries then just install and use which ever one you enjoy using.

---

### Post by evilsoup on 2012-12-18
The extra libs don't really amount to much, the only way I could see them being an issue is if you are on mobile internet or dialup with a low data cap.

---

### Post by N00b-un-2 on 2012-12-18
This line has blurred over time, especially with the decrease in cost and rise in availability of both high capacity storage space and high speed always-on internet connectivity.  This has led to better desktop integration between KDE and GNOME.   But when I think back just a few years to when I started using Linux in 2007, there was a very clear and distinct difference between the two systems, each one making the other seem like incompatible alien technology.  Integration was poor and the design aesthetics of the two were extremely different from each other.
But at the end of the day, what makes a KDE app a KDE app and a GNOME app a GNOME app is essentially the choice the devs made as to which tool kit is used for the GUI (typically QT for KDE and GTK for GNOME) *AS WELL AS* dependence on the associated libraries for that particular desktop environment.  Then there are "desktop agnostic" apps that don't favor one DE over another.  Such as GIMP, which although being a GTK based app is not dependent on GNOME libs nor is it part of the GNOME desktop, or VLC which is a QT based app but does not rely on the KDE libs, nor is it specifically a KDE app.
Over time, it would be nice to see an end to this type of schism and to see the two toolkits merged somehow, but given the nature of open source software and the schizophrenic tendencies of the community of devs to split/fork/abandon software on a whim, this will likely never happen.

---

### Post by mastablasta on 2012-12-19
> **zombifier25 said:**
> The difference is that KDE apps integrate deeply with KDE, while GNOME apps integrate deeply with GNOME (gconf, gsettings, Seahorse,..).
 
 
exactly.
 
the best way to see this that i noticed is if you use firefox on Kubuntu (KDE) you can see that effort was made to fit into the whole theme and KDE. but if oyu install chromium oyu will see strange out of place things. though th eporgramme works just ifne. it just doesn't looks as good and doesn't fit into the theme propperly.

---


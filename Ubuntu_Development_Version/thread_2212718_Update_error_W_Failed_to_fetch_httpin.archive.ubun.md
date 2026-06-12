---
title: "Update error: W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-bac"
date: 2014-03-22
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2014-03-22
```
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://in.archive.ubuntu.com trusty-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release  

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages  Hash Sum mismatch

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Getting this error for last few days on apt-get update, though system performance is not affected, should something be done for this?

---

### Post by bapoumba on 2014-03-22
Have you tried with the main servers ?

---

### Post by su:bhatta on 2014-03-22
> **bapoumba said:**
> Have you tried with the main servers ?

I have never changed the servers. After installation, I have always used the default servers that are recognized. 

A little help please, Where  & how do I change the servers from, Synaptic ?

---

### Post by bapoumba on 2014-03-22
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Yes, synaptic does it, so does software sources or editing /etc/apt/sources.list and removing the "in" in the repos url.

---

### Post by su:bhatta on 2014-03-22
Thanks a ton bapoumba. 
I've only done that once in my Wheezy install, almost a year back, so i was distraught.

Am going to give that a go. 

another help please : I was reading earlier today in a thread that apt-get dist-upgrade does not bring in kernel upgrades unless linux-generic is installed, if i remember correctly. I cannot trace back that thread anywhere :confused:
I am running low-latency kernel here.
 In Synaptic, I am seeing Linux-image-lowlatency & Linux-lowlatency, which I do i need to install to get the latest kernel updates in 14.04 install?

---

### Post by bapoumba on 2014-03-22
Hmm, I'll have to look about kernel stuff. It is past bedtime here. Others will certainly have the answer by tomorrow. If not, I'll do my homework :)

---

### Post by su:bhatta on 2014-03-22
> **bapoumba said:**
> Hmm, I'll have to look about kernel stuff. It is past bedtime here. Others will certainly have the answer by tomorrow. If not, I'll do my homework :)

Good night Bapoumba,
 Thanks for the pointers.

I got this in sources.list:
> ## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports** WILL NOT** receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


Is it necessary to make any changes to it ?
Also, when I ran ```
sudo kate /etc/apt/sources.list

```

It gave this :

```
sudo kate /etc/apt/sources.list
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-tres-bhatta" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-tres-bhatta" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-tres-bhatta" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-tres-bhatta" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-tres-bhatta" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-tres-bhatta" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-tres-bhatta" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-tres-bhatta" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-tres-bhatta" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-tres-bhatta" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-tres-bhatta" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-tres-bhatta" is owned by uid 1000 instead of uid 0.
QObject::connect: Cannot connect (null)::resourceScoreUpdated(QString, QString, QString, double) to NepomukPlugin::resourceScoreUpdated(QString, QString, QString, double)
QObject::connect: Cannot connect (null)::recentStatsDeleted(QString, int, QString) to NepomukPlugin::deleteRecentStats(QString, int, QString)
QObject::connect: Cannot connect (null)::earlierStatsDeleted(QString, int) to NepomukPlugin::deleteEarlierStats(QString, int)
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.8'

```

What does it all mean?
I guess I am in big time trouble here, Ringi just posted his D-bus thread.

---

### Post by bapoumba on 2014-03-23
Could you please post the complete output to
```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

It is not advised to open graphical applications as root with sudo, but use kdesudo instead : [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by su:bhatta on 2014-03-23
My bad, I forgot kdesudo, my first installation and adventures with KDE SC actually, I opened it the Gnome way.

> cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Studio 14.04 _Trusty Tahr_ - Alpha amd64 (20140211)]/ trusty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as                                                                                                           
## extensively as that contained in the main release, although it includes                                                                                                  
## newer versions of some applications which may provide useful features.                                                                                                   
## Also, please note that software in backports WILL NOT receive any review                                                                                                 
## or updates from the Ubuntu security team.                                                                                                                                
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse                                                                               
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse                                                                           
                                                                                                                                                                            
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted                                                                                                       
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted                                                                                                   
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe                                                                                                              
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe                                                                                                          
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

You want me to post the complete outputs of 

```
sudo apt-get update
sudo apt-get upgrade
```

too ?

---

### Post by bapoumba on 2014-03-23
> **bhattabhishek said:**
> My bad, I forgot kdesudo, my first installation and adventures with KDE SC actually, I opened it the Gnome way.

You want me to post the complete outputs of 

```
sudo apt-get update
sudo apt-get upgrade
```

too ?
In Gnome, the situation is the same, use gksudo and not sudo to open graphical applications as root.
And please yes, post the outputs to the update/upgrade. I see you have not changed to the main repos.

---

### Post by su:bhatta on 2014-03-24
I used kdesudo to open sources.list and Terminal gave following : 

```
~$ kdesudo kate /etc/apt/sources.list
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "k3bsetup.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "plasma-applet-touchpad.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gnome-color-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Actions in "/usr/share/applications/gnome-terminal.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/unity-user-accounts-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/gdebi.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gnome-screen-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/sooperlooper.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/qsynth.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/foo-yc20.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/agave.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/zita-at1.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gnome-user-accounts-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gnome-power-panel.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                                                                                       
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/qasconfig.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                                                                                               
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/unity-screen-panel.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                                                                                      
kbuildsycoca4(4811)/kdecore (services) KServicePrivate::init: The desktop entry file  "/usr/share/applications/evolution-data-server-uoa.desktop"  has Type= "Application"  but no Exec line                                                                                                                                                            
                                                                                                                                                                            
kbuildsycoca4(4811) KBuildServiceFactory::createEntry: Invalid Service :  "/usr/share/applications/evolution-data-server-uoa.desktop"                                       
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/qmidiarp.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                                                                                                  
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/ardour3.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/yoshimi.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/unity-power-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/xjadeo.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/firefox-trunk.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/unity-color-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/unity-region-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/language-selector.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gnome-region-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/qasmixer.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/qashctl.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/calf.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/firefox.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/unity-appearance-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/im-config.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/im-config.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Actions in "/usr/share/applications/gnome-screenshot.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Keywords in "/usr/share/applications/puredata.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4811) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gnome-background-panel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QObject::connect: Cannot connect (null)::resourceScoreUpdated(QString, QString, QString, double) to NepomukPlugin::resourceScoreUpdated(QString, QString, QString, double)
QObject::connect: Cannot connect (null)::recentStatsDeleted(QString, int, QString) to NepomukPlugin::deleteRecentStats(QString, int, QString)
QObject::connect: Cannot connect (null)::earlierStatsDeleted(QString, int) to NepomukPlugin::deleteEarlierStats(QString, int)
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kactivitymanagerd(4891)/nepomuk (library): Could not find virtuoso to connect to. Aborting 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.kde/share/config/activitymanager-pluginsrc


```

I changed the Trussty-backports to this:
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

and ran update:
```
~$ sudo apt-get update
[sudo] password for tres-bhatta: 
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com trusty InRelease                                                                                                       
Ign http://ppa.launchpad.net trusty InRelease                                                                                                           
Hit http://dl.google.com stable Release.gpg                                                                                                             
Ign http://security.ubuntu.com trusty-security InRelease                                                                                                
Ign http://in.archive.ubuntu.com trusty InRelease                                                                                                       
Hit http://archive.canonical.com trusty Release.gpg                                                                                                     
Ign http://archive.ubuntu.com trusty-backports InRelease                                                                                                
Ign http://ppa.launchpad.net trusty InRelease                                                                                                           
Ign http://extras.ubuntu.com trusty InRelease                                                                                                           
Hit http://dl.google.com stable Release                                                                                                                 
Hit http://archive.canonical.com trusty Release                                                                                                         
Hit http://security.ubuntu.com trusty-security Release.gpg                                                                                              
Hit http://extras.ubuntu.com trusty Release.gpg                                                                                                         
Hit http://dl.google.com stable/main amd64 Packages                                                                                                     
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                                         
Ign http://in.archive.ubuntu.com trusty-updates InRelease                                                                                               
Get:1 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]                                                                                    
Hit http://dl.google.com stable/main i386 Packages                                                                                                      
Hit http://archive.canonical.com trusty/partner amd64 Packages                                                                                          
Hit http://extras.ubuntu.com trusty Release                                                                                                             
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                                         
Hit http://security.ubuntu.com trusty-security Release                                                                                                  
Get:2 http://in.archive.ubuntu.com trusty Release.gpg [933 B]                                                                                           
Hit http://archive.canonical.com trusty/partner i386 Packages                                                                                           
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                                                                                 
Get:3 http://archive.ubuntu.com trusty-backports Release [58.6 kB]                                                                                      
Hit http://ppa.launchpad.net trusty Release                                                                                                             
Hit http://security.ubuntu.com trusty-security/main Sources                                                                                             
Hit http://extras.ubuntu.com trusty/main i386 Packages                                                                                                  
Hit http://ppa.launchpad.net trusty Release                                                                                                             
Hit http://in.archive.ubuntu.com trusty-updates Release.gpg                                                                                             
Hit http://security.ubuntu.com trusty-security/restricted Sources                                                                                       
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                                 
Get:4 http://in.archive.ubuntu.com trusty Release [58.5 kB]                                                                                             
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                                  
Hit http://security.ubuntu.com trusty-security/universe Sources                                                                                         
Hit http://security.ubuntu.com trusty-security/multiverse Sources                                                                                       
Hit http://security.ubuntu.com trusty-security/main amd64 Packages                                                                                      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                                 
Hit http://in.archive.ubuntu.com trusty-updates Release                                                                                                 
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages                                                                                
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                                  
Get:5 http://archive.ubuntu.com trusty-backports/main Sources [14 B]                                                                                    
Get:6 http://in.archive.ubuntu.com trusty/main Sources [1,074 kB]                                                                                       
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages                                                                                  
Ign http://archive.canonical.com trusty/partner Translation-en_IN                                                                                       
Get:7 http://archive.ubuntu.com trusty-backports/restricted Sources [14 B]                                                                              
Ign http://extras.ubuntu.com trusty/main Translation-en_IN                                                                                              
Ign http://archive.canonical.com trusty/partner Translation-en                                                                                          
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages                                                                                
Ign http://dl.google.com stable/main Translation-en_IN                                                                                                  
Ign http://extras.ubuntu.com trusty/main Translation-en                                                                                                 
Get:8 http://archive.ubuntu.com trusty-backports/universe Sources [14 B]                                                                                
Ign http://dl.google.com stable/main Translation-en                                                                                                     
Hit http://security.ubuntu.com trusty-security/main i386 Packages                                                                                       
Get:9 http://archive.ubuntu.com trusty-backports/multiverse Sources [14 B]                                                             
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages                                                                
Get:10 http://archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]                                                           
Hit http://security.ubuntu.com trusty-security/universe i386 Packages                                                                  
Get:11 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]                                                     
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages                                                                                 
Get:12 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [14 B]                                                       
Get:13 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [14 B]                                                                      
Hit http://security.ubuntu.com trusty-security/main Translation-en                                                                                      
Ign http://linux.dropbox.com saucy InRelease                                                                               
Get:14 http://archive.ubuntu.com trusty-backports/main i386 Packages [14 B]                                                
Hit http://linux.dropbox.com saucy Release.gpg                                                                             
Hit http://linux.dropbox.com saucy Release                                                                                 
Get:15 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]                                                                       
Hit http://linux.dropbox.com saucy/main amd64 Packages                                                                                                  
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en                                                                                
Get:16 http://archive.ubuntu.com trusty-backports/universe i386 Packages [14 B]                                                                         
Hit http://linux.dropbox.com saucy/main i386 Packages                                                                                                   
Ign http://ppa.launchpad.net trusty/main Translation-en_IN                                                                                              
Get:17 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [14 B]                                                                       
Ign http://ppa.launchpad.net trusty/main Translation-en                                                                                                 
Hit http://security.ubuntu.com trusty-security/restricted Translation-en                                                                                
Ign http://ppa.launchpad.net trusty/main Translation-en_IN                                                                                              
Ign http://ppa.launchpad.net trusty/main Translation-en                                                                                                 
Get:18 http://archive.ubuntu.com trusty-backports/main Translation-en [14 B]                                                                            
Hit http://security.ubuntu.com trusty-security/universe Translation-en                                                                                  
Get:19 http://archive.ubuntu.com trusty-backports/multiverse Translation-en [14 B]                                                                      
Get:20 http://archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]                                                                      
Ign http://linux.dropbox.com saucy/main Translation-en_IN                                                                                               
Ign http://linux.dropbox.com saucy/main Translation-en                                                                                                  
Get:21 http://archive.ubuntu.com trusty-backports/universe Translation-en [14 B]                                                                        
Ign http://security.ubuntu.com trusty-security/main Translation-en_IN                                                                                   
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_IN                                                                             
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_IN                                                                             
Ign http://security.ubuntu.com trusty-security/universe Translation-en_IN                                                                               
Ign http://archive.ubuntu.com trusty-backports/main Translation-en_IN                                                                                   
Ign http://archive.ubuntu.com trusty-backports/multiverse Translation-en_IN                                                                             
Ign http://archive.ubuntu.com trusty-backports/restricted Translation-en_IN                                                                             
Ign http://archive.ubuntu.com trusty-backports/universe Translation-en_IN                                                                               
Get:22 http://in.archive.ubuntu.com trusty/restricted Sources [5,386 B]                                                                                 
Get:23 http://in.archive.ubuntu.com trusty/universe Sources [6,403 kB]                                                                                  
Get:24 http://in.archive.ubuntu.com trusty/multiverse Sources [175 kB]                                                                                  
Get:25 http://in.archive.ubuntu.com trusty/main amd64 Packages [1,362 kB]                                                                               
Get:26 http://in.archive.ubuntu.com trusty/restricted amd64 Packages [13.1 kB]                                                                          
Get:27 http://in.archive.ubuntu.com trusty/universe amd64 Packages [5,867 kB]                                                                           
Get:28 http://in.archive.ubuntu.com trusty/multiverse amd64 Packages [131 kB]                                                                           
Get:29 http://in.archive.ubuntu.com trusty/main i386 Packages [1,357 kB]                                                                                
Get:30 http://in.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]                                                                           
Get:31 http://in.archive.ubuntu.com trusty/universe i386 Packages [5,875 kB]                                                                            
Get:32 http://in.archive.ubuntu.com trusty/multiverse i386 Packages [133 kB]                                                                            
Hit http://in.archive.ubuntu.com trusty/main Translation-en                                                                                             
Hit http://in.archive.ubuntu.com trusty/multiverse Translation-en                                                                                       
Hit http://in.archive.ubuntu.com trusty/restricted Translation-en                                                                                       
Hit http://in.archive.ubuntu.com trusty/universe Translation-en                                                                                         
Hit http://in.archive.ubuntu.com trusty-updates/main Sources                                                                                            
Hit http://in.archive.ubuntu.com trusty-updates/restricted Sources                                                                                      
Hit http://in.archive.ubuntu.com trusty-updates/universe Sources                                                                                        
Hit http://in.archive.ubuntu.com trusty-updates/multiverse Sources                                                                                      
Hit http://in.archive.ubuntu.com trusty-updates/main amd64 Packages                                                                                     
Hit http://in.archive.ubuntu.com trusty-updates/restricted amd64 Packages                                                                               
Hit http://in.archive.ubuntu.com trusty-updates/universe amd64 Packages                                                                                 
Hit http://in.archive.ubuntu.com trusty-updates/multiverse amd64 Packages                                                                               
Hit http://in.archive.ubuntu.com trusty-updates/main i386 Packages                                                                                      
Hit http://in.archive.ubuntu.com trusty-updates/restricted i386 Packages                                                                                
Hit http://in.archive.ubuntu.com trusty-updates/universe i386 Packages                                                                                  
Hit http://in.archive.ubuntu.com trusty-updates/multiverse i386 Packages                                                                                
Hit http://in.archive.ubuntu.com trusty-updates/main Translation-en                                                                                     
Hit http://in.archive.ubuntu.com trusty-updates/multiverse Translation-en                                                                               
Hit http://in.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://in.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://in.archive.ubuntu.com trusty/main Translation-en_IN
Ign http://in.archive.ubuntu.com trusty/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com trusty/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com trusty/universe Translation-en_IN
Ign http://in.archive.ubuntu.com trusty-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com trusty-updates/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com trusty-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com trusty-updates/universe Translation-en_IN
Fetched 22.5 MB in 6min 45s (55.5 kB/s)
Reading package lists... Done
```

So yes, the problem seems to have gone.

Running upgrade:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  akregator ark audiocd-kio baloo blender blender-data blogilo chromium-codecs-ffmpeg-extra compiz-plugins-main-default compizconfig-settings-manager
  cracklib-runtime dolphin firefox-trunk freespacenotifier gnome-shell gnome-shell-common gstreamer1.0-plugins-ugly gwenview kaccessible kamera kate
  kate-data katepart kcalc kde-base-artwork kde-baseapps-bin kde-baseapps-data kde-config-pimactivity kde-runtime kde-runtime-data kde-style-oxygen
  kde-wallpapers kde-wallpapers-default kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin kde-workspace-data
  kde-workspace-kgreet-plugins kdebase-runtime kdegraphics-strigi-analyzer kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins
  kdenetwork-filesharing kdepasswd kdepim-kresources kdepim-runtime kdepimlibs-kio-plugins kdoctools khelpcenter4 kinfocenter kio-audiocd klipper kmag
  kmenuedit kmix kmousetool knotes konsole kontact korganizer krdc ksnapshot ksysguard ksysguardd ksystemlog kwalletmanager libakonadi-calendar4
  libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4 libakonadi-socialutils4 libastro1
  libbaloocore4 libbaloofiles4 libbaloopim4 libbaloowidgets4 libbalooxapian4 libcalendarsupport4 libcomposereditorng4 libcrack2 libeventviews4
  libgnomecanvasmm-2.6-1c2a libgpgme++2 libincidenceeditorsng4 libjemalloc1 libkabc4 libkactivities-bin libkactivities-models1 libkactivities6
  libkalarmcal2 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkcompactdisc4
  libkdcraw-data libkdcraw23 libkde3support4 libkdeclarative5 libkdecorations4abi1 libkdecore5 libkdepim4 libkdepimdbusinterfaces4 libkdesu5 libkdeui5
  libkdewebkit5 libkdgantt2-0 libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-11 libkexiv2-data libkfile4 libkfilemetadata4 libkholidays4 libkhtml5
  libkidletime4 libkimap4 libkio5 libkipi-data libkipi11 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmbox4 libkmediaplayer4 libkmime4
  libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common libkonq5-templates libkonq5abi1 libkontactinterface4 libkparts4 libkpgp4
  libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4 libksane-data libksane0
  libkscreensaver5 libksgrd4 libksignalplotter4 libktexteditor4 libktnef4 libkunitconversion4 libkwineffects1abi4 libkwinglesutils1 libkwinglutils1abi3
  libkworkspace4abi2 libkxmlrpcclient4 libmailcommon4 libmailimporter4 libmailtransport4 libmarblewidget18 libmessagecomposer4 libmessagecore4
  libmessageviewer4 libmicroblog4 libnepomuk4 libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a libnepomukutils4 libnewt0.52 libnoteshared4
  libokularcore3abi1 libpimactivity4 libpimcommon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi4 libplasmagenericshell4
  libprocesscore4abi1 libprocessui4a libpython2.7 libpython2.7-minimal libpython2.7-stdlib libpython3.4 libpython3.4-minimal libpython3.4-stdlib
  libqgpgme1 libqmobipocket1 libsendlater4 libsolid4 libsyndication4 libtaskmanager4abi5 libtemplateparser4 libthreadweaver4 libweather-ion6
  marble-data marble-plugins mencoder mplayer nepomuk-core-data nepomuk-core-ffmpegextractor nepomuk-core-runtime okular okular-extra-backends
  oxygen-icon-theme oxygen-icon-theme-complete plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook
  plasma-scriptengine-javascript plasma-widget-folderview plasma-widget-kimpanel plasma-widgets-addons plasma-widgets-workspace print-manager
  python-apt python-apt-common python-compizconfig python-crypto python-dbus python-dbus-dev python-imaging python-lxml python-numpy python-pil
  python-pycurl python-renderpm python-reportlab python-reportlab-accel python2.7 python2.7-minimal python3-apt python3-crypto python3-dbus
  python3-pycurl python3.4 python3.4-minimal simple-scan systemsettings ubuntu-minimal ubuntu-standard whiptail xfce4-screenshooter
257 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 283 MB of archives.
After this operation, 3,129 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

Thanks so much for giving your time to look into the matter.
Also, thought I would add, I have KDE, Gnome, FVWM-Crystal and Xfce(default) installed in this Ubuntu Studio.

---

### Post by bapoumba on 2014-03-24
Have you accepted the upgrade ?
If not, you need to run sudo **apt-get update** and **sudo apt-get upgrade** again, and say Y at the end of the process.

I'm not sure about the errors you get opening kate with kdesudo. In any case, to edit the sources.list file, you can do it from the terminal.

For a later utilisation, here are the steps you could have done :

```
cat /etc/apt/sources.list
```
Will list what is in the file. You can copy/paste here for info.

```
sudo nano /etc/apt/sources.list
```
Will allow you to edit the file with nano in the terminal (no graphical application, nano is a small text editor). You can edit the file, then save it with ctrl-o (letter o) and exit with ctrl-x.

---

### Post by mc4man on 2014-03-24
The QDBusConnection: ... is said to be harmless - 
[https://bugs.kde.org/show_bug.cgi?id=297020](https://bugs.kde.org/show_bug.cgi?id=297020)
All the messages concerning lines in various .desktops are also of no real importance, if inclined you can edit  in the trailing ;

I would definitely get in habit of using a terminal editor for root files, otherwise do use kdesudo or in gnome gksudo 
(while in past something like sudo gedit was fine that is no longer the case

For nano, after editing it's - 
ctrl+o
**enter**
ctrl+x

---

### Post by su:bhatta on 2014-03-24
I used kdesudo kate /etc/apt/sources.list to open the sources.list with Kate and made the changes ( removing in. from the trusty-backports lines) .

Ran update & upgrade, I did put in a 'y' and press enter, and the upgrade was carried out successfully :)

I didn't paste the entire contents of apt-get upgrade here.

@mc4man

Actually, only time I have had to change sources.list was to add 'contrib & non-free' in Debian, and there I had to use 'su' and then I did 'gedit /etc/apt/sources.list'

I am not a techinal person in computers, and not aware & savvy with in Terminal applications or editors like nano. 
But I guess, I have to get into knowing them now, if I have to really get into it and get my hands dirty. That is fine with me :)

---

### Post by bapoumba on 2014-03-24
Thanks mc4man, I remember similar warnings with gksudo long ago. I did not look for that.
bhattabhishek, do I understand the issue is now solved ?

---

### Post by su:bhatta on 2014-03-24
@mc4man: Thanks to your reply, my mind is at peace. I am simply ignoring them. My system is running with no real problem in usage.

@ bapoumba: Definitely my issue is solved, as using the default repos, there is no problem. Marking the thread as Solved.

Thanks for the help both of you.
Time to read up a little about nano ! :)

---

### Post by Elfy on 2014-03-24
> **mc4man said:**
> The QDBusConnection: ... is said to be harmless - 
[https://bugs.kde.org/show_bug.cgi?id=297020](https://bugs.kde.org/show_bug.cgi?id=297020)
All the messages concerning lines in various .desktops are also of no real importance, if inclined you can edit  in the trailing ;

I would definitely get in habit of using a terminal editor for root files, otherwise do use kdesudo or in gnome gksudo 
(while in past something like sudo gedit was fine that is no longer the case

For nano, after editing it's - 
ctrl+o
**enter**
ctrl+x

Not at all sure about Kubuntu and kdesudo - but gksudo isn't installed by default anymore afaik.

I'm not at all sure what 'they' expect people to do. 

Just fyi - though I'd guess you know anyway :)

---

### Post by bapoumba on 2014-03-24
> **bhattabhishek said:**
> 
@ bapoumba: Definitely my issue is solved, as using the default repos, there is no problem. Marking the thread as Solved.

Thanks for the help both of you.
Time to read up a little about nano ! :)

You may want to check every now and then, the "in" repos may just be out of sync for some reason. Thanks for marking the thread as solved. **man nano** will be helpful :)

---

### Post by johnnyzee on 2014-04-14
I continue to get the same error trying for months to upgrade from 12.04 to 12.10 and have set my system to use the main server several times but still get:

W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Index](http://au.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Index)  
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Do you have any tips for me as to how to get around this?

---

### Post by Elfy on 2014-04-14
> **johnnyzee said:**
> I continue to get the same error trying for months to upgrade from 12.04 to 12.10 and have set my system to use the main server several times but still get:

W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Index](http://au.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Index)  
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Do you have any tips for me as to how to get around this?

You've got backport repos for Natty Narwhal enabled - disable them - they were EOL October 2012.

---

### Post by ibjsb4 on 2014-04-14
Or avoid the rush and install 14.04 now.

```
do-release-upgrade -d
```

---

### Post by su:bhatta on 2014-04-14
> **ibjsb4 said:**
> Or avoid the rush and install 14.04 now.

```
do-release-upgrade -d
```

Can't that break the system? 
I have only tried it once from 13.04 to 13.10 while 13.10 was under development.
The next thing I knew, I had to download the 13.10 ISO for fresh installation !

---

### Post by johnnyzee on 2014-04-20
> **Elfy said:**
> You've got backport repos for Natty Narwhal enabled - disable them - they were EOL October 2012.

Thanks Elfy. Unfortunately I do not know how to disable the backport repos. Can you tell me how to do that?

Thanks

---

### Post by johnnyzee on 2014-04-20
Thanks Coffeecat

I appreciate the advice. Can you tell me how to remove or disable the repos?

Then when I upgrade to 14.04 will I need to download, create an iso image,etc or will the update manager do that for me?

---

### Post by BlinkinCat on 2014-04-20
If I was you, I would post the output suggested by bapoumba in your last thread -

[http://ubuntuforums.org/showthread.php?t=2218294&p=12994727#post12994727](http://ubuntuforums.org/showthread.php?t=2218294&p=12994727#post12994727)

---

### Post by Elfy on 2014-04-20
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you have anymore issues - please start a thread in the main support areas. This forum is not for released version support.

---


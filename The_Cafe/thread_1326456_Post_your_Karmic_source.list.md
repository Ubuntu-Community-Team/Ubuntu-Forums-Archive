---
title: "Post your Karmic source.list"
date: 2009-11-14
forum: The Cafe
---

### Post by Tapas Bose, India on 2009-11-14
Hallo everybody.
I don't think that any one will mind to share his/her  sources list of Karmic!! Lets share our secrecy of source list and enhance the topic. Here is mine:
```

#### Ubuntu Main Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted

#### Ubuntu Update Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted

#### Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic-security partner

#### 3rd Parties Repos

## Themes du ZgegBlog: Project Bisigi
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main

## Cairo-dock
##  wget -q [http://repository.cairo-dock.org/cairo-dock.gpg](http://repository.cairo-dock.org/cairo-dock.gpg) -O- | sudo apt-key add
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7274A4DAE80D6BF5
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main multiverse restricted universe 
deb [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) karmic main multiverse restricted universe 
deb [http://ppa.launchpad.net/cairo-dock-team/update/ubuntu](http://ppa.launchpad.net/cairo-dock-team/update/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/cairo-dock-team/update/ubuntu](http://ppa.launchpad.net/cairo-dock-team/update/ubuntu) karmic main multiverse restricted universe

## Chromium-browser
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main

## Ubuntusatanic
## wget -q [http://ubuntusatanic.org/ubuntu-se-key.gpg](http://ubuntusatanic.org/ubuntu-se-key.gpg) -O- | sudo apt-key add -
deb [http://ubuntusatanic.org/hell](http://ubuntusatanic.org/hell) karmic main

## Openoffice
# deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) karmic main

## Google software repository
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

## Getdeb
## wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

## Opera
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
## wget -q -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) squeeze non-free
deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) squeeze non-free

## Firefox
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main

## Pidgin
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

## GIMP (Testing Version)
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) karmic main multiverse restricted universe
deb-src [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) karmic main multiverse restricted universe

## Compiz-fusion
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) karmic main
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) karmic main multiverse restricted universe
deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) karmic main multiverse restricted universe

## VLC
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) karmic main

## SMPlayer/MPlayer Core Libraries
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A7E13D78E4A4F4F4
deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2C20FEBDE130B2A5
deb [http://ppa.launchpad.net/rvm/testing/ubuntu](http://ppa.launchpad.net/rvm/testing/ubuntu) karmic main multiverse universe restricted
deb-src [http://ppa.launchpad.net/rvm/testing/ubuntu](http://ppa.launchpad.net/rvm/testing/ubuntu) karmic main multiverse universe restricted
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
deb [http://ppa.launchpad.net/rvm/libs/ubuntu](http://ppa.launchpad.net/rvm/libs/ubuntu) karmic main multiverse universe restricted
deb-src [http://ppa.launchpad.net/rvm/libs/ubuntu](http://ppa.launchpad.net/rvm/libs/ubuntu) karmic main multiverse universe restricted
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0893DC134548A28D
deb [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) karmic main multiverse universe restricted
deb-src [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) karmic main multiverse universe restricted
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 015A66E603E02400
deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) karmic main multiverse universe restricted 
deb-src [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) karmic main multiverse universe restricted 

## Medibuntu
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

## Empathy
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main

## Gnome-do
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) karmic main

## Nautilus-dropbox
## gpg --keyserver pgp.mit.edu --recv-keys 3565780E
deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic main

## Gnome-globalmenu
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main

## Gnome-colors theme
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main

## Shutter
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) karmic main

## Terminator
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
deb [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) karmic main

## Azureus
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7A16627C
deb [http://ppa.launchpad.net/smaioli/ppa/ubuntu](http://ppa.launchpad.net/smaioli/ppa/ubuntu) karmic main

## Breathe Icon Set
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb [http://ppa.launchpad.net/breathe-dev/ppa/ubuntu](http://ppa.launchpad.net/breathe-dev/ppa/ubuntu) karmic main

## Conky
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 95628707
deb [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) karmic main

## Esmska
## wget -q -O - [http://repo.palatinus.cz/repo.key](http://repo.palatinus.cz/repo.key) | sudo apt-key add -
deb [http://repo.palatinus.cz/stable](http://repo.palatinus.cz/stable) /

## KDE 3.5
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 44869960
deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main

## Miro HD Video Player
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/

## Playdeb
## wget -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games

## PlayOnLinux
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) karmic main

## Ubuntu Tweak
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main multiverse restricted universe 
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2E183FA1E260F5B0
deb [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) karmic main multiverse restricted universe
deb-src [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) karmic main multiverse restricted universe 

## Wine
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main

## Viewizard Games repository
## wget [http://www.viewizard.com/linux/viewizard-gpg.asc](http://www.viewizard.com/linux/viewizard-gpg.asc)
## sudo apt-key add viewizard-gpg.asc
## sudo apt-get install astromenace
deb [http://viewizard.com/linux](http://viewizard.com/linux) debian/

## Banshee
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main  
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C9DF5F3AFD21FFFE
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main multiverse restricted universe 
deb [http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu](http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu](http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu) karmic main multiverse restricted universe
deb [http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu) karmic main multiverse restricted universe 
deb [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu](http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu) karmic main multiverse restricted universe

## ClamAV
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AB767895ADC2037
deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) karmic main multiverse restricted universe
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) karmic main multiverse restricted universe

## Bigon (empathy, rhythmbox)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F586F9AD744BF4D0
deb [http://ppa.launchpad.net/bigon/ubuntu](http://ppa.launchpad.net/bigon/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bigon/ubuntu](http://ppa.launchpad.net/bigon/ubuntu) karmic main

## Gmusicbrowser (open-source jukebox for large collections of mp3/ogg/flac/mpc/ape files, written in perl)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2FE527580ADD8151
deb [http://squentin.free.fr/gmusicbrowser](http://squentin.free.fr/gmusicbrowser) ./ 

## Audacious
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 729BC20A4FCA60A8
deb [http://ppa.launchpad.net/sebner/ubuntu](http://ppa.launchpad.net/sebner/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/sebner/ubuntu](http://ppa.launchpad.net/sebner/ubuntu) karmic main

## CairoClock
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FF6D1003462167CE
deb [http://ppa.launchpad.net/macslow/ubuntu](http://ppa.launchpad.net/macslow/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/macslow/ubuntu](http://ppa.launchpad.net/macslow/ubuntu) karmic main

## Mozilla Daily Build Team
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9BDB3D89CE49EC21
deb [http://ppa.launchpad.net/mozillateam/ffox35/ubuntu](http://ppa.launchpad.net/mozillateam/ffox35/ubuntu) karmic main multiverse restricted universe
deb-src [http://ppa.launchpad.net/mozillateam/ffox35/ubuntu](http://ppa.launchpad.net/mozillateam/ffox35/ubuntu) karmic main multiverse restricted universe
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A6DCF7707EBC211F
deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) karmic main multiverse restricted universe 
## gpg --keyserver subkeys.pgp.net --recv-key 247510BE && gpg --armor --export  247510BE | sudo apt-key add -
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main universe restricted multiverse 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main universe restricted multiverse 

``` 
Thank you all of you for your participation.

---

### Post by dragos240 on 2009-11-14
> **Tapas Bose, India said:**
> Hallo everybody.



Hello, Dr. Nick!

---

### Post by J-Buntu on 2009-11-14
When i have some time, i'll see if i can add anything to that, but that's a nice long list, here's one i think you missed - but looking at that it made my eyes fuzzy, so i dunno, i might be there  :P

XBMC for Linux (very cool media center)
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) karmic main

- If you can find the "Media Stream" skin for XBMC, it looks exactly like Plex on Mac.
I use XBMC and it's much better than Moovida - which on my lappy was awful.
To get the media stream skin, just download the windows version and move the skin from that 
into the skins folder in Ubuntu. (it's hard to find the media stream skin online i found and it didn't come with the Ubuntu version for me)

---

### Post by coldReactive on 2009-11-14
Here's mine...

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://apt.wakoopa.com all main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/giftwrap/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/giftwrap/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/abhidg/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/abhidg/ppa/ubuntu karmic main
```

---

### Post by Tapas Bose, India on 2009-11-14
Thank you friends. Carry on...

---

### Post by days_of_ruin on 2009-11-15
Since Karmic has ```
add-apt-repository
``` which places a file for each ppa in /etc/apt/source.list.d/ my /et/apt/sources.list is pretty vanilla.

---

### Post by RiceMonster on 2009-11-15
> **dragos240 said:**
> Hello, Dr. Nick!

I lol'd

---

### Post by coldReactive on 2009-11-15
> **RiceMonster said:**
> I lol'd

You changed your avatar! *gasp* I like the new one.

---

### Post by RiceMonster on 2009-11-15
> **coldReactive said:**
> You changed your avatar! *gasp* I like the new one.

Thanks. I got bored of the old one.

---

### Post by Tapas Bose, India on 2009-11-15
Repository for acetoneiso:
link:[https://launchpad.net/~samrog131/+ppa-packages]("https://launchpad.net/%7Esamrog131/+ppa-packages")
Code:
> 
## Sam Rog (acetoneiso etc)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A47958D42B7E03A7
deb [http://ppa.launchpad.net/samrog131/ppa/ubuntu](http://ppa.launchpad.net/samrog131/ppa/ubuntu) karmic main multiverse restricted universe
deb-src [http://ppa.launchpad.net/samrog131/ppa/ubuntu](http://ppa.launchpad.net/samrog131/ppa/ubuntu) karmic main multiverse restricted universe


---

### Post by Dale61 on 2009-11-15
This is mine, and any Aussie with BigPond is free to copy-and-paste as it is mostly unmetered.

```
## BigPond unmetered repositories.
 
deb http://mirror.files.bigpond.com/ubuntu/ karmic main restricted universe
deb http://mirror.files.bigpond.com/ubuntu/ karmic-security main restricted universe
deb http://mirror.files.bigpond.com/ubuntu/ karmic-updates main restricted universe
deb http://mirror.files.bigpond.com/ubuntu/ karmic-backports main restricted universe
deb http://mirror.files.bigpond.com/ubuntu/ karmic-proposed main restricted universe
deb-src http://mirror.files.bigpond.com/ubuntu/ karmic main restricted universe
deb-src http://mirror.files.bigpond.com/ubuntu/ karmic-security main restricted universe
deb-src http://mirror.files.bigpond.com/ubuntu/ karmic-updates main restricted universe
deb-src http://mirror.files.bigpond.com/ubuntu/ karmic-backports main restricted universe
deb-src http://mirror.files.bigpond.com/ubuntu/ karmic-proposed main restricted universe
 
## Ubuntu's Australia repositories (what BigPond doesn't cover).
 
deb http://au.archive.ubuntu.com/ubuntu/ karmic multiverse restricted universe main
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates multiverse restricted universe main
deb http://au.archive.ubuntu.com/ubuntu/ karmic-security multiverse restricted universe main
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic multiverse restricted universe main
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates multiverse restricted universe main
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-security multiverse restricted universe main
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner
```

---

### Post by Flymo on 2009-11-16
Thanks, Dale!

Having just discovered this, and tried it out - it "just worked". Well, after logging in to BigPond (yet) again.  They do log us out pretty soon, eh?

With five+ *****buntu installs here, it will save us a lot of bandwith on their
mean and and over-expensive offerings. 

Have you had any success with their "Unmetered" web offerings?  We can only seem to view pages, with downloads or live news just sitting there mute and unresponsive.  We have the latest Flash and Silverlight from the Ubuntu repos, but no joy.

Thanks again, and all the best, Ben

---

### Post by Dale61 on 2009-11-16
> **Flymo said:**
> Thanks, Dale!

Have you had any success with their "Unmetered" web offerings?  We can only seem to view pages, with downloads or live news just sitting there mute and unresponsive.  We have the latest Flash and Silverlight from the Ubuntu repos, but no joy.

Thanks again, and all the best, Ben

Yeah, I've had no problems with the unmetered offerings I 'need'.  I check all the footy and motor racing news via BigPond, but I have no need to partake any of the other offers.  In the last two weeks, my unmetered downloads add up to 1105 MB's.

However, I do have a lot of the content filtered with Ad Block Plus, so I've only got what I want on display.

In regards to log in, I've never been logged out unless I do it from my end.  That could be a problem with your line, or even your modem.  What plan are you on?  We are on ADSL Liberty* (12GB) 1500/256, having only just upgraded from the slower plan.

---

### Post by earthpigg on 2009-11-16
just because this great tool hasn't already been mentioned in this thread:

[Ubuntu sources.list Generator]("http://repogen.simplylinux.ch/")

example sources.list:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free
```

and, right below that:

> Getting the GPG keys:
```
wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
```



much cleaner.

---

### Post by siimo on 2009-11-16
I use this and recommend it for NZ users:

```

# Main OS 
deb http://debian.ihug.co.nz/ubuntu karmic main restricted universe multiverse 

# Updates
deb http://debian.ihug.co.nz/ubuntu karmic-updates main restricted universe multiverse 

# Security
deb http://debian.ihug.co.nz/ubuntu karmic-security main restricted universe multiverse 

```

Downloads are very fast, especially on the Vodafone network.  Ihug = Vodafone.

---

### Post by Tapas Bose, India on 2009-11-16
I have found some extra repo:
> 
## kde4-extras
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2B397B5E
deb [http://ppa.launchpad.net/kde4-extras/ppa/ubuntu](http://ppa.launchpad.net/kde4-extras/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/kde4-extras/ppa/ubuntu](http://ppa.launchpad.net/kde4-extras/ppa/ubuntu) karmic main multiverse restricted universe 

## kde4-fixes
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9EF1DB6
deb [http://ppa.launchpad.net/kde4-fixes/ppa/ubuntu](http://ppa.launchpad.net/kde4-fixes/ppa/ubuntu) karmic main multiverse restricted universe  
deb-src [http://ppa.launchpad.net/kde4-fixes/ppa/ubuntu](http://ppa.launchpad.net/kde4-fixes/ppa/ubuntu) karmic main multiverse restricted universe  

## Sam Rog (acetoneiso etc)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A47958D42B7E03A7
##deb [http://ppa.launchpad.net/samrog131/ppa/ubuntu](http://ppa.launchpad.net/samrog131/ppa/ubuntu) karmic main multiverse restricted universe 
##deb-src [http://ppa.launchpad.net/samrog131/ppa/ubuntu](http://ppa.launchpad.net/samrog131/ppa/ubuntu) karmic main multiverse restricted universe 

## Joel Goguen (file-roller etc)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 13A1301D
deb [http://ppa.launchpad.net/jgoguen/ppa/ubuntu](http://ppa.launchpad.net/jgoguen/ppa/ubuntu) karmic main multiverse restricted universe 
deb-src [http://ppa.launchpad.net/jgoguen/ppa/ubuntu](http://ppa.launchpad.net/jgoguen/ppa/ubuntu) karmic main multiverse restricted universe 

## Ubuntu Desktop
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1231595
deb [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) karmic main multiverse restricted universe  
deb-src [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) karmic main multiverse restricted universe 

## Ubuntu Audio Dev team 
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72B194E5
deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) karmic main 

## Geany Developers
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B3641232
deb [http://ppa.launchpad.net/geany-dev/ppa/ubuntu](http://ppa.launchpad.net/geany-dev/ppa/ubuntu) karmic main multiverse restricted universe  
deb-src [http://ppa.launchpad.net/geany-dev/ppa/ubuntu](http://ppa.launchpad.net/geany-dev/ppa/ubuntu) karmic main multiverse restricted universe  

## Kubuntu Members
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 39E06C25
deb [http://ppa.launchpad.net/kubuntu-members/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-members/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/kubuntu-members/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-members/ppa/ubuntu) karmic main 

## Swiftfox
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free


---

### Post by Ylon on 2009-11-16
Simply, can't stay without mintmenu... even on karmic!

```
## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------
## +++ Linux Mint 7 Gloria (stable) +++
deb http://packages.linuxmint.com/ helena main upstream import
## +++ Backports (not as stable) +++
deb http://packages.linuxmint.com/ helena backport
## +++ Community (not as stable) +++
deb http://packages.linuxmint.com/ helena community
## +++ Romeo (unstable) +++
deb http://packages.linuxmint.com/ helena romeo

```

---

### Post by Uncle Spellbinder on 2009-12-18
Here's mine. Used a few things from Ubuntu sources.list Generator and added from there...

```
#############################################################
############### OFFICIAL UBUNTU KARMIC REPOS ################
#############################################################

###### Ubuntu Karmic CD ROM
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


###### Ubuntu Karmic Main
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

###### Ubuntu Karmic Update
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

###### Ubuntu Karmic Security
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

###### Ubuntu Karmic Backports
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

###### Ubuntu Partner
deb http://archive.canonical.com/ubuntu karmic partner


##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

#### Medibuntu - http://www.medibuntu.org/ 
## sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ karmic free non-free

#### Miro HD Video Player - http://www.getmiro.com/
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/

#### Ubuntuzilla - http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main


##############################################################
###################### LAUNCHPAD PPA's #######################
##############################################################

#### Abiword 
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
deb http://ppa.launchpad.net/abiword-stable/ubuntu karmic main

#### Aurora Gtk2 Engine 
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0AAFAD78
deb http://ppa.launchpad.net/merlwiz79/aurora/ubuntu karmic main

#### Avant Window Navigator (AWN Testing Team - Trunk Builds)
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com BF810CD5
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main

#### Exaile
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43CBFCC0
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main

#### GCstar Collection Manager
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb http://ppa.launchpad.net/gcstar/ppa/ubuntu karmic main 

#### Nvidia Vdpau Team PPA
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main

#### MediaInfo
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu karmic main

#### Quod Libet, quodlibet-plugins, exfalso and mutagen (Trunk Builds)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5806C7C4
deb http://ppa.launchpad.net/lazka/dumpingplace/ubuntu karmic main

#### Songbird (Daily Builds)
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5719E347
deb http://ppa.launchpad.net/songbird-daily/ppa/ubuntu karmic main

#### Themes for GNOME and Ubuntu
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main 

#### Ubuntu Tweak
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
```

---

### Post by m0o on 2009-12-29
Here is my Kubuntu Karmic repository:

```
## Backports Kubuntu PPA
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) karmic main

## Choqok Experimental PPA
## [https://launchpad.net/~neversfelde/+archive/experimental]("https://launchpad.net/%7Eneversfelde/+archive/experimental")
deb [http://ppa.launchpad.net/neversfelde/experimental/ubuntu](http://ppa.launchpad.net/neversfelde/experimental/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/neversfelde/experimental/ubuntu](http://ppa.launchpad.net/neversfelde/experimental/ubuntu) karmic main 

## Chromium Daily Build PPA
## [https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main

## Fabien Tasin PPA
## [https://launchpad.net/~fta/+archive/ppa]("https://launchpad.net/%7Efta/+archive/ppa")
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main

## ffmpeg - Reinhard Tarler
## [https://launchpad.net/~siretart/+archive/ppa]("https://launchpad.net/%7Esiretart/+archive/ppa")
## deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) karmic main
## deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) karmic main

[COLOR=black]## [COLOR=Red]Firefox KDE integration PPA[/COLOR]
## [https://launchpad.net/~debfx/+archive/firefox-kde]("https://launchpad.net/%7Edebfx/+archive/firefox-kde")
deb [http://ppa.launchpad.net/debfx/firefox-kde/ubuntu](http://ppa.launchpad.net/debfx/firefox-kde/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/debfx/firefox-kde/ubuntu](http://ppa.launchpad.net/debfx/firefox-kde/ubuntu) karmic main [/COLOR]

## getdeb.net repo
##deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

## GIMP svn PPA
deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) karmic main

## Jonathan Riddell PPA Beta
## [https://launchpad.net/~jr/+archive/ppa]("https://launchpad.net/%7Ejr/+archive/ppa")
##deb [http://ppa.launchpad.net/jr/ppa/ubuntu](http://ppa.launchpad.net/jr/ppa/ubuntu) karmic main 
##deb-src [http://ppa.launchpad.net/jr/ppa/ubuntu](http://ppa.launchpad.net/jr/ppa/ubuntu) karmic main 

## Kdenlive PPA
## [https://launchpad.net/~sunab/+archive/ppa]("https://launchpad.net/%7Esunab/+archive/ppa")
##deb [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) karmic main 
##deb-src [http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu) karmic main 

## Kubuntu Updates PPA
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) karmic main

## Kubuntu KDE 4.4 Beta 1
deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) karmic main

## Mozilla Team Daily PPA
## [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
#deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
#deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

## Nvidia Vdpau Team PPA
## [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")
deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main 

## Qwit (Identica/Twitter) PPA
## [https://launchpad.net/~dr-akulavich/+archive/qwit]("https://launchpad.net/%7Edr-akulavich/+archive/qwit")
##deb [http://ppa.launchpad.net/dr-akulavich/qwit/ubuntu](http://ppa.launchpad.net/dr-akulavich/qwit/ubuntu) karmic main
##deb-src [http://ppa.launchpad.net/dr-akulavich/qwit/ubuntu](http://ppa.launchpad.net/dr-akulavich/qwit/ubuntu) karmic main

## Theora Team PPA
# [https://launchpad.net/~theora/+archive/ppa]("https://launchpad.net/%7Etheora/+archive/ppa")
##deb [http://ppa.launchpad.net/theora/ppa/ubuntu](http://ppa.launchpad.net/theora/ppa/ubuntu) karmic main
##deb-src [http://ppa.launchpad.net/theora/ppa/ubuntu](http://ppa.launchpad.net/theora/ppa/ubuntu) karmic main

## WebKit Team PPA
## [https://launchpad.net/~webkit-team/+archive/ppa]("https://launchpad.net/%7Ewebkit-team/+archive/ppa")
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) karmic main

## Wine Team Ubunut PPA
## [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main

```[INDENT]**My favorite is the Firefox KDE 4 Qt integration PPA.*
[/INDENT]I was wondering, is the matthaeus123 PPA the only latest GIMP PPA available?

---


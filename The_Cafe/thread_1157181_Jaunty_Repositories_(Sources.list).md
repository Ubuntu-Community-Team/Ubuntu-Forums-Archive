---
title: "Jaunty Repositories (Sources.list)"
date: 2009-05-12
forum: The Cafe
---

### Post by abhiroopb on 2009-05-12
Thought I would start a thread where we could share our sources.list files!

```

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu/ jaunty-security main universe restricted multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security main universe restricted multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main universe restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main universe restricted multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed main universe restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed main universe restricted multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main universe restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main universe restricted multiverse

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

###################################################################################################################

#Personal Packages

#Gnome-Do
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

#Dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main
deb-src http://linux.getdropbox.com/ubuntu jaunty main

#Medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free

#Amarok 1.4 - prefer it over Amarok 2
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main

#VLC 1.0
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main

#Gm-Notify
deb http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu jaunty main

#Chromium
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

#OpenOffice
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main

#Compiz Fusion
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main

#Free Fonts
deb http://ppa.launchpad.net/corenominal/ubuntu hardy main

#VirtualBox
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

#Liferea
#deb http://ppa.launchpad.net/liferea/ppa/ubuntu jaunty main
#deb-src http://ppa.launchpad.net/liferea/ppa/ubuntu jaunty main
#deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
#deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main

#Mozilla
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

```

Couple of things:

I am not using the Liferea PPA as Liferea 1.6 does not allow [**_this fix_**]("http://ubuntuforums.org/showpost.php?p=7162556&postcount=8") to the fsync bug. So, I still use the older 1.4 version (which is in the ubuntu repo.

The Mozilla PPA is for Prism rather than using the bleeding edge Firefox.

---

### Post by dmizer on 2009-05-13
Since this really isn't a request for support, I've moved this thread to the Community Cafe.

On all 8 of my Ubuntu machines, my sources.list is bone stock with the exception of medibuntu. Not much of a bleeding edge person myself.

---

### Post by abhiroopb on 2009-05-13
Thanks for moving it!

I wouldn't say I'm bleeding edge for the sake of it. There are specific features in certain programs that I want to use, so I need to find newer versions of them!

---

### Post by juancarlospaco on 2009-05-13
*...Without Keys ...?*

---

### Post by abhiroopb on 2009-05-13
after you add all the repositories and do apt-get update, you will get errors with various public keys in those errors.

Just do the following for each of those errors:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <key>

---

### Post by konqueror7 on 2009-05-13
here's mine...
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.mmu.edu.my/ubuntu/ jaunty main restricted universe
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.mmu.edu.my/ubuntu/ jaunty-updates main restricted universe
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty universe
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.mmu.edu.my/ubuntu/ jaunty multiverse
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty multiverse
deb http://archive.mmu.edu.my/ubuntu/ jaunty-updates multiverse
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ph.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.mmu.edu.my/ubuntu/ jaunty-security main restricted universe
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty-security main restricted
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty-security universe
deb http://archive.mmu.edu.my/ubuntu/ jaunty-security multiverse
deb-src http://archive.mmu.edu.my/ubuntu/ jaunty-security multiverse
## Custom Sources
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://dl.google.com/linux/deb/ stable non-free #Google
deb http://packages.medibuntu.org/ jaunty free non-free #Medibuntu
deb http://wine.budgetdedicated.com/apt jaunty main #Wine
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://getswiftfox.com/builds/debian unstable non-free #Swiftfox
deb http://linux.getdropbox.com/ubuntu jaunty main #Dropbox
deb-src http://linux.getdropbox.com/ubuntu jaunty main #Dropbox
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu intrepid/ #MiroTV (Intrepid)
## Custom PPAs
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main #NVIDIA Pre-compiled
deb-src http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main #NVIDIA Pre-compiled
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main #Ubuntu Tweak
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main #Ubuntu Tweak
deb http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main #Firefox
deb-src http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main #Firefox
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main #Compiz
deb-src http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main #Compiz
deb http://ppa.launchpad.net/gilir/ppa/ubuntu jaunty main #Screenlets
deb-src http://ppa.launchpad.net/gilir/ppa/ubuntu jaunty main #Screenlets
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main #Deluge
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main #Deluge
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #OpenOffice
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #OpenOffice
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main #Pidgin IM
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main #Pidgin IM
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main #WebKit
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main #WebKit
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #Chromium
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main #VLC
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main #VLC

```

---

### Post by abhiroopb on 2009-05-13
What does the nVidia pre-compiled PPA do?

---

### Post by ashmew2 on 2009-05-13
Here's my sources.list :
> 
# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to ine the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to ine the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide ineful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## iners.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


it's the same except that i changed all the US servers to Indian servers (in.)

Oh and btw , can you add an older version's repository and download software from it ? i mean if i want some software which was in the hardy main but it isnt in the intrepid main , can i just add another deb [http://URL](http://URL) hardy main line to my sources.list and do apt-get update ? will it break deps ? :)

---

### Post by abhiroopb on 2009-05-13
Not really sure, better let someone else answer that. But generally it is probably better to use ones taht are recommended.

---

### Post by konqueror7 on 2009-05-13
> **abhiroopb said:**
> What does the nVidia pre-compiled PPA do?
oh, its for my video card...its the same *.run you download from the nvdia site...:)

---

### Post by cmost on 2009-05-14
I don't know why you've entitled this post "Jaunty Repositories" when your sources.list clearly points to the upcoming pre pre alpha of Ubuntu 9.10 Karmic Koala.  It's really not smart to recommend newbies use the alpha repositories.

---

### Post by abhiroopb on 2009-05-14
Please read everything before you make unnecessary posts.

Someone happened to post about Karmic packages, (it wasn't me) if you had read my post it listed ONLY jaunty repositories. If you don't like it then there is no need to comment.

---

### Post by dixon on 2009-05-19
Here're my added ppas
```

#pidgin
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
#dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main
deb-src http://linux.getdropbox.com/ubuntu jaunty main
#balzam themes
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
#backintime
deb http://le-web.org/repository stable main
#fatrat
deb http://ppa.launchpad.net/hamrle/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/hamrle/ppa/ubuntu jaunty main
#chromium
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
#bluman
deb http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/blueman/ppa/ubuntu jaunty main
#gnome-do
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

```Does anyone know about ppa with latest alsa release (1.0.20 atm) and pulseaudio release?

---

### Post by kaivalagi on 2009-05-19
Here mine, where no cmd line for adding the key is present in the comments the keys should be available from the relevant ppa pages on launchpad.net. I piped all of this out from individual list files under /etc/apt/sources.list.d/, I leave the main /etc/apt/sources.list file well alone.

```
# awn
deb http://ppa.launchpad.net/awn-core/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-core/ppa/ubuntu jaunty main

# banshee
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main

# cairo dock
# wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock

# deluge
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main

# doctormo
deb http://ppa.launchpad.net/doctormo/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/doctormo/ppa/ubuntu jaunty main

# dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main
deb-src http://linux.getdropbox.com/ubuntu jaunty main

# exaile
deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu jaunty main

# Google software repository
# sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

# kaivalagi's ppa - conky
# sudo wget -q http://www.kaivalagi.com/m-buck-conky-jaunty.list -O /etc/apt/sources.list.d/m-buck-conky-jaunty.list
# wget -q http://www.kaivalagi.com/m-buck-conky-key.gpg -O- | sudo apt-key add -
deb http://ppa.launchpad.net/m-buck/conky/ubuntu jaunty main
deb-src http://ppa.launchpad.net/m-buck/conky/ubuntu jaunty main

# kaivalagi's ppa - gtk-desktop-info
# sudo wget -q http://www.kaivalagi.com/m-buck-gtk-desktop-info-jaunty.list -O /etc/apt/sources.list.d/m-buck-gtk-desktop-info-jaunty.list
# wget -q http://www.kaivalagi.com/m-buck-gtk-desktop-info-key.gpg -O- | sudo apt-key add -
deb http://ppa.launchpad.net/m-buck/gtk-desktop-info/ubuntu jaunty main
deb-src http://ppa.launchpad.net/m-buck/gtk-desktop-info/ubuntu jaunty main

# kaivalagi's ppa - rhythmbox
# sudo wget -q http://www.kaivalagi.com/m-buck-rhythmbox-jaunty.list -O /etc/apt/sources.list.d/m-buck-rhythmbox-jaunty.list
# wget -q http://www.kaivalagi.com/m-buck-rhythmbox-key.gpg -O- | sudo apt-key add -
deb http://ppa.launchpad.net/m-buck/rhythmbox/ubuntu jaunty main
deb-src http://ppa.launchpad.net/m-buck/rhythmbox/ubuntu jaunty main

# mkvmerge
# wget http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb http://www.bunkus.org/ubuntu/jaunty/ ./
deb-src http://www.bunkus.org/ubuntu/jaunty/ ./

# open office
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main

# PlayOnLinux
# wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
deb http://deb.playonlinux.com/ jaunty main

#shutter
deb http://ppa.launchpad.net/shutter/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu jaunty main

#spring
deb http://ppa.launchpad.net/spring/ubuntu jaunty main
deb-src http://ppa.launchpad.net/spring/ubuntu jaunty main

# ssherminator
deb http://ppa.launchpad.net/ssherminator-team/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/ssherminator-team/ppa/ubuntu intrepid main
```

---

### Post by abhiroopb on 2009-05-19
what is the benefit of having your own ppa? and what can you do with it?

---

### Post by kaivalagi on 2009-05-19
> **abhiroopb said:**
> what is the benefit of having your own ppa? and what can you do with it?

You can write your own software, and publish it. Have a look at my sig links for the sort of things I am creating/maintaining (all are python based). All my packages need to be authenticated by a trusted user of the branch which is an added bonus for all.

Also Launchpad is more than just a package repository, it also allows me to manage my source code changes (check-in, branch etc using bazaar). The packages get built on the launchpad servers too, for hardy, intrepid and jaunty (and others if so wanted) from the source packages I upload.

Why don't you have a quick browse through my source code, packages etc on Launchpad, you'll get an idea of what it supports. PPA link below...

---

### Post by 1jackjack on 2009-05-20
@abhiroopb Thanks for the sweet tip for auto-adding public key authentication!

I would add the Gnome-Colours repo (LOADS of amazing icons and themes - really makes Gnome-Do shine!):
deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) jaunty main

Also, I was wondering: do you really need to add the second 'sources.list' item (source)? How does it help?

Cheers

---

### Post by abhiroopb on 2009-05-20
> **1jackjack said:**
> @abhiroopb Thanks for the sweet tip for auto-adding public key authentication!

I would add the Gnome-Colours repo (LOADS of amazing icons and themes - really makes Gnome-Do shine!):
deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) jaunty main

Also, I was wondering: do you really need to add the second 'sources.list' item (source)? How does it help?

Cheers

I don't understand your question?

---

### Post by Tristam Green on 2009-05-20
Custom PPAs - Gnome-Do, Amarok 1.4 via Bogdanb's PPA, WineHQ, medibuntu, chromium PPA

```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main #Bogdan's PPA - Ubuntu 9.04 - Amarok 1.4
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main #Bogdan's PPA - Ubuntu 9.04 - Amarok 1.4
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main #GNOME Do PPA - Ubuntu 9.04
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main #GNOME Do PPA - Ubuntu 9.04
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #Chromium Daily Builds - Ubuntu 9.04
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #Chromium Daily Builds - Ubuntu 9.04
```

---

### Post by 1jackjack on 2009-05-20
> I don't understand your question?
Where ever you find the 'sources.list' entry for a repo, there are always 2 lines e.g.
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main

My question is: what is the purpose of the second line (starting 'deb-src')? I know you don't need to add it (I've stopped bothering), so why is it included? Is it for devs?

Cheers

---

### Post by abhiroopb on 2009-05-20
> **1jackjack said:**
> Where ever you find the 'sources.list' entry for a repo, there are always 2 lines e.g.
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main

My question is: what is the purpose of the second line (starting 'deb-src')? I know you don't need to add it (I've stopped bothering), so why is it included? Is it for devs?

Cheers

Thats exactly it. Its for devs, as it contains the source code of the packages. It definitely is not necessary. But, I figure what difference does it make, may as well have it complete!

---

### Post by rolandixor on 2009-05-27
It's for devs, and for the rare case that you need to compile the package automatically for your system. If I know I won't need it I skip. But when there is the rare case I might need it, I go ahead and add it.

---

### Post by 1jackjack on 2009-05-27
well you learn a new thing every day! thanks.

---

### Post by CylnZ on 2009-05-27
> **dixon said:**
> 
Does anyone know about ppa with latest alsa release (1.0.20 atm) and pulseaudio release?

[https://launchpad.net/~voria/+archive/archive/+build/1027520]("https://launchpad.net/%7Evoria/+archive/archive/+build/1027520")

that work for ya??

---

### Post by rolandixor on 2009-05-28
that doesn't help, seeing as they were deleted. There is another repo that houses the new pulseaudio, but I'm trying to find a way to update the gstreamer pulse plugin, cause it cause problems.

---

### Post by CylnZ on 2009-06-08
> **rolandixor said:**
> that doesn't help, seeing as they were deleted. There is another repo that houses the new pulseaudio, but I'm trying to find a way to update the gstreamer pulse plugin, cause it cause problems.

  ok, I was looking for pulse updates myself and found this.  [https://launchpad.net/ubuntu/intrepid/amd64/libgstreamer-plugins-base0.10-0](https://launchpad.net/ubuntu/intrepid/amd64/libgstreamer-plugins-base0.10-0)

---


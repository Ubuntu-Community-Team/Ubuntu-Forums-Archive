---
title: "[SOLVED] Error installing libgtk2.0-dev"
date: 2008-03-18
forum: Repositories &amp; Backports
---

### Post by unutbu on 2008-03-18
After spending years merrily frying in rpm dependency hell like a piece of low-sodium thin-sliced bacon stuck on the devil's sombrero, I was finally peeled off, kicking and screaming into the enlightened world of apt. Where the birds sing and the sun shines. So bright... so very very bright. Ouch! It's hot down here. No, is it true? I'm in apt-get hell!


```

farmer:~% sudo apt-get install libgtk2.0-dev
[...]
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages

farmer:~% sudo apt-get -f install libpango1.0-dev
[...]
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 is to be installed
E: Broken packages

farmer:~/finance% dpkg --status libpango1.0-0
[...]
Package: libpango1.0-0
Status: install ok installed
Version: 1.18.3-0ubuntu1

```

So a natural question would be, what packages (if any) required libpango1.0-0 version 1.18.3?
A few slices of 'apt-cache rdepends', 'dpkg -l', and 'dpkg --status' wrapped in a perl sandwich tells me:

```

Packages that depend on version >= 1.18.3:
   acroread
   compiz-gnome
   deskbar-applet
   gdm
   gimp
   gimp-python
   gnome-games
   libgimp2.0
   libpoppler-glib2
   mplayer
   nautilus
   sound-juicer

```

What is the best way install libgtk2.0-dev in this situation?

---

### Post by bapoumba on 2008-03-19
Please post your sources.list:
```
cat /etc/apt/sources.list
```

and any error to 
```
sudo apt-get update
```

---

### Post by unutbu on 2008-03-19
```

08:59:17 cyrano@farmer:~% cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted security universe

# deb http://packages.ubuntu.com/ubuntu gutsy security
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse restricted main
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main



##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Backports


## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## Other
deb http://packages.medibuntu.org/ gutsy free non-free
deb http://lug.mtu.edu/ubuntu/ gutsy main
deb http://ppa.launchpad.net/avassalotti/ubuntu gutsy main
deb-src http://ppa.launchpad.net/avassalotti/ubuntu gutsy main

```

```

08:59:28 cyrano@farmer:~% sudo apt-get update
[sudo] password for cyrano:
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Get:2 http://lug.mtu.edu gutsy Release.gpg [191B]
Ign http://lug.mtu.edu gutsy/main Translation-en_US
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:4 http://packages.medibuntu.org gutsy Release.gpg [189B]
Ign http://packages.medibuntu.org gutsy/free Translation-en_US
Get:5 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Ign http://ppa.launchpad.net gutsy Release.gpg
Ign http://ppa.launchpad.net gutsy/main Translation-en_US
Get:6 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Hit http://lug.mtu.edu gutsy Release
Hit http://us.archive.ubuntu.com gutsy Release
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:7 http://security.ubuntu.com gutsy-security Release [51.2kB]
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Hit http://archive.canonical.com gutsy Release
Hit http://ppa.launchpad.net gutsy Release
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Hit http://lug.mtu.edu gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Ign http://packages.medibuntu.org gutsy/free Packages
Hit http://archive.canonical.com gutsy/partner Packages
Ign http://ppa.launchpad.net gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://archive.canonical.com gutsy/partner Sources
Ign http://ppa.launchpad.net gutsy/main Sources
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://ppa.launchpad.net gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://packages.medibuntu.org gutsy/non-free Packages
Hit http://ppa.launchpad.net gutsy/main Sources
Get:8 http://security.ubuntu.com gutsy-security/main Packages [76.9kB]
Get:9 http://security.ubuntu.com gutsy-security/restricted Packages [14B]
Get:10 http://security.ubuntu.com gutsy-security/main Sources [14.2kB]
Get:11 http://security.ubuntu.com gutsy-security/restricted Sources [14B]
Get:12 http://security.ubuntu.com gutsy-security/universe Packages [52.1kB]
Get:13 http://security.ubuntu.com gutsy-security/universe Sources [7303B]
Get:14 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]
Get:15 http://security.ubuntu.com gutsy-security/multiverse Sources [833B]
Fetched 206kB in 3s (54.8kB/s)
Reading package lists... Done

```

---

### Post by bapoumba on 2008-03-19
I have not much time atm to look into each individual repo listed under #other. Please comment them out, **sudo apt-get update** to reload the file and try to install the package with ubuntu-only repos.

---

### Post by unutbu on 2008-03-19
```

09:34:27 cyrano@farmer:~% tail -n 5 /etc/apt/sources.list
## Other
#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
#deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) gutsy main
#deb [http://ppa.launchpad.net/avassalotti/ubuntu](http://ppa.launchpad.net/avassalotti/ubuntu) gutsy main
#deb-src [http://ppa.launchpad.net/avassalotti/ubuntu](http://ppa.launchpad.net/avassalotti/ubuntu) gutsy main

09:34:43 cyrano@farmer:~% sudo apt-get update
[...]

09:35:41 cyrano@farmer:~% sudo apt-get -f install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages

```

---

### Post by bapoumba on 2008-03-19
Hmm.. As there is only emacs in the ppa, I suppose the problem comes from something you installed from lug.mtu.edu. Do you recall which package(s) it was?

If yes, the solution would be to enable the repos again, remove all packages and deps coming from there, comment the repos, update and try to install or -fix broken libgtk2.0-dev.

My guess is there is a version conflict with the package(s) you installed from third party repos.

---

### Post by unutbu on 2008-03-19
Thanks for your reply, bapoumba.
Yes, I have installed some unofficial packages from the other repos (acroread, mplayer, emacs-snapshot-gtk).

I tried to find out what package(s) were causing the problem. I don't know apt/dpkg very well, so I ended up writing a perl script to find all packages that were installed (using dpkg -l), that depended on libpango1.0-0 (using apt-cache rdepends), and which required a version >= 1.18.3 (using dpkg --status).

The complete list of problem packages include gdm, and nautilus, things that I never installed. This machine is a Dell 530N, so it appears Dell shipped the machine with incompatible packages.

I'm reluctant to downgrade all the problem packages (see the original post for the list) because I don't know for what purpose Dell installed their versions.

---

### Post by unutbu on 2008-03-20
Is there a way to install two versions of a package on the same system, and then direct other packages to use the correct version?

In this case, is there a way to install libpango1.0-0 1.18.2-0ubuntu1 in a separate directory so I can have libpango version 1.18.2 and 1.18.3 on the same system? And then is it possible to tell libgtk2.0-dev to use libpango 1.18.2?

---

### Post by bapoumba on 2008-03-20
> **unutbu said:**
> Is there a way to install two versions of a package on the same system, and then direct other packages to use the correct version?

In this case, is there a way to install libpango1.0-0 1.18.2-0ubuntu1 in a separate directory so I can have libpango version 1.18.2 and 1.18.3 on the same system? And then is it possible to tell libgtk2.0-dev to use libpango 1.18.2?
Not that I know of. The distribution is tied up with the dependencies, in particular with the ubuntu-desktop metapackage. This package is just a list of dependencies, ensuring all versions of all packages are homogenous. 

What I would do is remove the extra packages installed from the third party repos for now (the ones you installed after you got the computer), remove the third party repos from the source.list, update, (in that order) and see from there. You can install back the packages later and see which one is giving you trouble.

A basic install should not lead to version conflicts. So remove the conflicting packages and then install the lib.
From my gutsy setup: 
```
~$ aptitude show libgtk2.0-dev
Package: libgtk2.0-dev
State: not installed
Version: 2.12.0-1ubuntu3
Priority: optional
Section: libdevel
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 9351k
Depends: libgtk2.0-0 (= 2.12.0-1ubuntu3), libglib2.0-dev (>= 2.12.0),
         **libpango1.0-dev (>= 1.10.0-2)**, libatk1.0-dev (>= 1.6.1-2),
         libcairo2-dev, libx11-dev (>= 2:1.0.0-6), libxext-dev, libxinerama-dev,
         libxi-dev, libxrandr-dev, libxcursor-dev, libxfixes-dev,
         libxcomposite-dev, libxdamage-dev, pkg-config
Recommends: python (>= 2.4)
Suggests: libgtk2.0-doc
[B]Conflicts: libgtk1.3-dev
Replaces: libgtk1.3-dev, gtk2-engines-pixbuf (< 2.8.18-5)[/B]

```
```
aptitude show libpango1.0-dev
Package: libpango1.0-dev
**State: not installed**
**Version: 1.18.3-0ubuntu1**
Priority: optional
Section: libdevel
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1262k
Depends: libpango1.0-0 (= 1.18.3-0ubuntu1), libglib2.0-dev (>= 2.14.0),
         libfreetype6-dev (>= 2.1.3), libx11-dev, libxrender-dev, pkg-config,
         libxft-dev, libfontconfig1-dev (>= 2.1.91), libcairo2-dev (>= 1.2.6)
Suggests: libpango1.0-doc, imagemagick
Conflicts: libpango-dev, libpango1.0-common (< 1.15.3-0ubuntu1)
Replaces: libpango-dev, libpango1.0-common (< 1.15.3-0ubuntu1)

```

```
~$ aptitude show libpango1.0-0
Package: libpango1.0-0
State: installed
**Automatically installed: yes**
**Version: 1.18.3-0ubuntu1**
Priority: optional
Section: libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 815k
Depends: libpango1.0-common (>= 1.18.3-0ubuntu1), libc6 (>= 2.6-1), libcairo2
         (>= 1.4.0), libdatrie0, libfontconfig1 (>= 2.4.0), libfreetype6 (>=
         2.3.5), libglib2.0-0 (>= 2.14.0), libthai0 (>= 0.1.7), libx11-6,
         libxft2 (> 2.1.1), libxrender1, zlib1g (>= 1:1.2.3.3.dfsg-1)
Conflicts: pango-libthai
Provides: pango1.0-modver-1.6.0

```
For some reason, libpango1.0-0 is 1.18.2-0ubuntu1 on your system. And conflicts with gutsy's standard version.

Am I making sense ?.

---

### Post by unutbu on 2008-03-20
Thank very much for the reply, bapoumba. Not sure if I follow you.

```

10:20:11 cyrano@farmer:~% dpkg --status gdm
Package: gdm
Status: install ok installed
[...]
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.13.2), libattr1 (>= 2.4.4-1), libc6 (>= 2.6-1), libcairo2 (>= 1.4.0), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libdmx1, libfontconfig1 (>= 2.4.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.14.0), libgnomecanvas2-0 (>= 2.11.1), libgtk2.0-0 (>= 2.12.0), libpam0g (>= 0.99.7.1), **libpango1.0-0 (>= 1.18.3)**, librsvg2-2 (>= 2.18.1), libselinux1 (>= 2.0.15), libwrap0, libx11-6, libxau6, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxdmcp6, libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.29), libxrandr2 (>= 2:1.2.0), libxrender1, debconf (>= 0.5) | debconf-2.0, adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1), gnome-session | xterm | x-window-manager | x-terminal-emulator, xbase-clients, alsa-utils, gksu (>= 1.0.7), lsb-base (>= 3.0-10), librsvg2-common, kbd | console-tools

```

Is dpkg telling me that gdm will not work with any version of libpango1.0-0 less than 1.18.3? And meanwhile...

```

10:20:54 cyrano@farmer:~% sudo apt-get -f install libpango1.0-dev
[...]
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (**= 1.18.2-0ubuntu1**) but 1.18.3-0ubuntu1 is to be installed
E: Broken packages

```

Isn't apt-get telling me that libpango1.0-dev will never install until I have libpango1.0-0 ver. 1.18.2-0ubuntu1 (and no higher) installed?

If so, I'm going to have it uninstall a lot more than emacs, acroread and mplayer, and some perl packages. I'll have to uninstall  acroread, compiz-gnome,   deskbar-applet,   gdm,   gimp,   gimp-python,   gnome-games,   libgimp2.0, libpoppler-glib2,   mplayer,   nautilus, and   sound-juicer.

Also, just so we are on the same page, my libpango1.0-0 version is currently 1.18-3-0ubuntu1:

```

10:25:10 cyrano@farmer:~% dpkg --status libpango1.0-0
Package: libpango1.0-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 796
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: pango1.0
Version: 1.18.3-0ubuntu1

```

---

### Post by bapoumba on 2008-03-20
Hmm.. Okay :D

Your libpango1.0-dev Depends: libpango1.0-0 (= 1.18.2-0ubuntu1)
My libpango1.0-dev depends libpango1.0-0 (= 1.18.3-0ubuntu1)

Not sure where this is coming from ..

---

### Post by unutbu on 2008-03-20
I appreciate your help very very much, but I am philosophically stubborn. Although I love learning about the apt/dpkg way, I refuse to take take 15 steps backward to make one small step forward. 

I appreciate linux because of the freedom it affords. I appreciate apt/dpgk/ubuntu for its easy of use and stability, but it seems in this instance the two values are in conflict. At this moment I wish 
apt & co. gave me more freedom.

On rpm based systems you can force rpms to install come hell or high water, let the user beware and take full responsibility if he breaks his system. 

I wish apt didn't try to protect me so much. I'd be willing to try installing libgtk2.0-dev and just seeing what happens. If it doesn't work, then the minor gtk app I was thinking of making would break. I think that is an acceptable cost compared to having to uninstall so many things.

---

### Post by unutbu on 2008-03-20
I currently don't have libpango1.0-dev installed:
I tried installing, but it choked on libpango1.0-0 version 1.18.3. It seems to insist on 1.18.2.

```


10:20:54 cyrano@farmer:~% sudo apt-get -f install libpango1.0-dev
[...]
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 is to be installed
E: Broken packages

11:10:23 cyrano@farmer:~% dpkg --status libpango1.0-dev
Package `libpango1.0-dev' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


```

---

### Post by bapoumba on 2008-03-20
No problem.
As all your third party repos were gutsy, I would say one of them did not package an app correctly. Nothing on your side, or on apt's side, as far as I can tell. I would trust medibuntu.

I do not know the rpm system, as I switched to debian from a mandrake (first linux distro I ever installed), that was some time ago :)
I'd like to help you better, sorry.

---

### Post by bapoumba on 2008-03-20
> **unutbu said:**
> I currently don't have libpango1.0-dev installed:
I tried installing, but it choked on libpango1.0-0 version 1.18.3. It seems to insist on 1.18.2.

```


10:20:54 cyrano@farmer:~% sudo apt-get -f install libpango1.0-dev
[...]
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 is to be installed
E: Broken packages

11:10:23 cyrano@farmer:~% dpkg --status libpango1.0-dev
Package `libpango1.0-dev' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


```

Ah !
Please add the gutsy-update repos:
```
## Updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
```
[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libpango1.0-dev]("http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libpango1.0-dev")

```
sudo apt-get update
sudo apt-get dist-upgrade
```
and try to install it again.

---

### Post by unutbu on 2008-03-20
Il a réussi! J'adore apt, J'adore gutsy-updates, Je t'adore (platoniquement)!
Merci beaucoup.

---

### Post by bapoumba on 2008-03-20
De rien !
Sorry it took me so long to figure it out. My first impression was correct: repo missing. I got distracted by the #Others repos.
Glad you got it to work. Enjoy you apt experience :)

---


---
title: "Does anyone else have dependency problems??"
date: 2005-08-25
forum: Repositories &amp; Backports
---

### Post by André on 2005-08-25
Hi everybody,

i am having some serious problems with my repositories.

This is my sources.list:
```

##
# Dateiname:            /etc/apt/sources.list
# Letzte Änderung:      24.08.05
#
# Beschreibung:         Backport Fix
##

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://de.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://de.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu hoary universe
deb-src http://de.archive.ubuntu.com/ubuntu hoary universe

deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

## Multiverse Pakete
deb http://de.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hoary multiverse

## Multiverse Sicherheitspakete
deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

## Backport Pakete
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Backport Fix
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted

```

Now apt-get update gives me:

root@gremLin:/etc/apt # apt-get update
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary Release.gpg [189B]
Hole:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hole:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Hole:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary Release
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging Release.gpg
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/main Sources
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging Release.gpg
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/restricted Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/universe Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/universe Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hoary/multiverse Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages
OK   [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Sources
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging Release
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging Release
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/universe Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/multiverse Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/restricted Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/universe Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/multiverse Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/restricted Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/restricted Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/restricted Packages
Es wurden 4B in 2s geholt (1B/s)
Paketlisten werden gelesen... Fertig

and serious packages like evolution, cvs and OpenOffice.org appear in the obsolete or local area of Synaptic.

Is anyone experiencing similar problems? Any idea how to solve them?

Greetings
André

---

### Post by André on 2005-08-25
I decided to do a reinstall (it was such a fresh system that it doesn´t really matter) to get a clean system.

I was just starting again with my setup so it doesn´t really matter and i just wanted to stay in this state.

Greetings
André

---

### Post by cyrix on 2005-08-25
There are a mess of packages NOT available. It's getting to the point where I may just start looking towards another flavor of Linux. What choice am I being left with, I'm a newb linux user too.

---

### Post by c0rderr0y on 2005-08-27
i say just go out and try other flavors of linux and come back when the server is fixed....

---


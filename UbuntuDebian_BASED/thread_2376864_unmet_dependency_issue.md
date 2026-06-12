---
title: "unmet dependency issue"
date: 2017-11-06
forum: Ubuntu/Debian BASED
---

### Post by zy_guy on 2017-11-06
/I am trying to install a piece of software and I get this error message. I don't know how to fix this, I've tried to manually install the required dependency, but it just goes in circles. Someone please help.


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

```
The following packages have unmet dependencies:
 libcurl-ocaml : Conflicts: libcurl-ocaml:i386 but 0.5.3-2build5 is to be installed
 libcurl-ocaml:i386 : Depends: ocaml-base-nox-4.02.3:i386
                      Conflicts: libcurl-ocaml but 0.5.3-2build5 is to be installed
 libcurl-ocaml-dev : Conflicts: libcurl-ocaml-dev:i386 but 0.5.3-2build5 is to be installed
 libcurl-ocaml-dev:i386 : Depends: ocaml-nox-4.02.3:i386
                          Depends: libcurl4-gnutls-dev:i386 (>= 7.15.0-2) but it is not going to be installed
                          Depends: ocaml-findlib:i386 (>= 1.2.5) but it is not going to be installed
                          Conflicts: libcurl-ocaml-dev but 0.5.3-2build5 is to be installed
 libcurl4-gnutls-dev : Conflicts: libcurl4-nss-dev but 7.47.0-1ubuntu2.4 is to be installed
                       Conflicts: libcurl4-openssl-dev but 7.47.0-1ubuntu2.4 is to be installed
 libcurl4-nss-dev : Conflicts: libcurl4-gnutls-dev but 7.47.0-1ubuntu2.4 is to be installed
                    Conflicts: libcurl4-openssl-dev but 7.47.0-1ubuntu2.4 is to be installed
 libcurl4-openssl-dev : Conflicts: libcurl4-gnutls-dev but 7.47.0-1ubuntu2.4 is to be installed
                        Conflicts: libcurl4-nss-dev but 7.47.0-1ubuntu2.4 is to be installed
 libvorbis-ocaml : Depends: libogg-ocaml-xh9y0
                   Conflicts: libvorbis-ocaml:i386 but 0.6.1-3build2 is to be installed
 libvorbis-ocaml:i386 : Depends: libogg-ocaml-465c2:i386
                        Depends: ocaml-base-nox-4.02.3:i386
                        Conflicts: libvorbis-ocaml but 0.6.1-3build2 is to be installed
 libvorbis-ocaml-dev : Depends: libogg-ocaml-dev-xh9y0
                       Depends: libogg-ocaml-dev but it is not going to be installed
                       Conflicts: libvorbis-ocaml-dev:i386 but 0.6.1-3build2 is to be installed
 libvorbis-ocaml-dev:i386 : Depends: libogg-ocaml-dev-465c2:i386
                            Depends: ocaml-nox-4.02.3:i386
                            Depends: libogg-ocaml-dev:i386 but it is not going to be installed
                            Conflicts: libvorbis-ocaml-dev but 0.6.1-3build2 is to be installed
E: Unable to correct problems, you have held broken packages.
```


I tried sudo apt purge libcurl* openal* libvorbis* and sudo apt install libcurl* openal* libvorbis*
 but that didn't work either.

Thank you in advance.

---

### Post by ajgreeny on 2017-11-07
We need to know what Ubuntu version you are using and what you were trying to install before we can help you much.

Contrary to what some forum users think, we are not mind readers, and that info will give us much more help so that we can help you.

It may also help us if we can see the output of ```
cat /etc/apt/sources.list
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by vasa1 on 2017-11-07
It's also possible that OP may have added/removed ppas.```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```may provide more information,

---

### Post by zy_guy on 2017-11-07
I'm using peppermint os built on 16.04. i was trying to install voxelands.

```
output of cat /etc/apt/sources.list:

# deb cdrom:[Peppermint 8 _Eight_ - Release amd64 (20170527)]/ xenial main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

out put of grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list.d/minetestdevs-ubuntu-stable-xenial.list:deb [http://ppa.launchpad.net/minetestdevs/stable/ubuntu](http://ppa.launchpad.net/minetestdevs/stable/ubuntu) xenial main
/etc/apt/sources.list.d/peppermint.list:deb [http://ppa.launchpad.net/peppermintos/p8-release/ubuntu](http://ppa.launchpad.net/peppermintos/p8-release/ubuntu) xenial main
/etc/apt/sources.list.d/peppermint.list:deb [http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-3.9/ubuntu](http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-3.9/ubuntu) xenial main
/etc/apt/sources.list.d/peppermint.list:deb [http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-4.0/ubuntu](http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-4.0/ubuntu) xenial main
/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main
```

---

### Post by ajgreeny on 2017-11-08
*Thread moved to **Ubuntu/Debian BASED**.* which is more appropriate and a better fit as this is not a Ubuntu version but a derivitive.

Can you now show us the output of a simplified version of the command shown by vasa1 please; we already have the sources.list file so now need all your "Other software" sources from
```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list.d/*.list
```
I am now wondering if the peppermint repos that are enabled are possibly causing this problem of version conflicts, though I know nothing of peppermint or what is adds(?) to Ubuntu.

---

### Post by zy_guy on 2017-11-08
/etc/apt/sources.list.d/minetestdevs-ubuntu-stable-xenial.list:deb [http://ppa.launchpad.net/minetestdevs/stable/ubuntu](http://ppa.launchpad.net/minetestdevs/stable/ubuntu) xenial main
/etc/apt/sources.list.d/peppermint.list:deb [http://ppa.launchpad.net/peppermintos/p8-release/ubuntu](http://ppa.launchpad.net/peppermintos/p8-release/ubuntu) xenial main
/etc/apt/sources.list.d/peppermint.list:deb [http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-3.9/ubuntu](http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-3.9/ubuntu) xenial main
/etc/apt/sources.list.d/peppermint.list:deb [http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-4.0/ubuntu](http://ppa.launchpad.net/peppermintos/p8-release-llvm-toolchain-4.0/ubuntu) xenial main
/etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main

---

### Post by zy_guy on 2017-11-09
I just reinstalled the os since i didn't have anything important. Thanks for trying to help. I suspect i messed up some librarywhile trying different things to get it to work.

---

### Post by ajgreeny on 2017-11-10
That is good news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---


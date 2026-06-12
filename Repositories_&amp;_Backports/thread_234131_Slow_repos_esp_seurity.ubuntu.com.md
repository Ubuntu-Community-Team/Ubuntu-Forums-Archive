---
title: "Slow repos esp seurity.ubuntu.com"
date: 2006-08-11
forum: Repositories &amp; Backports
---

### Post by dj-toonz on 2006-08-11
Hi all, is anybody having problems with the repos this morning? i've just reinstalled ubuntu after a clean up and having loads of problems trying to download anything i.e updates, stuff like that .all the over repos are ok i.e archive.ubuntu.com, just the secuirty.ubuntu.com seems to be the main problem , i'm on a 24meg ADSL 2+ connection and it's shooting up to like 4060 kb/s to right down to 1 b/ for about 40 secs then starts again (up & down more times then a tarts knickers) in m$ i'm getting perfect speeds around 4.4meg download on average but it never goes below 3800. it's saying right now ,to do 150 updates gonna take 18hrs 20mins & 30secs :-({|= i can walk faster then tha,t download speed 509 b/s. here's my sources list

# Hand-Customized variant of:
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY wit# gpg --keyserver subkeys.pgp.net --recv KEYh the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Backports 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
# deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
# deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
# deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
# deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main
# deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
# deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
# deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Penguin Liberation Front (PLF)

# PLF primary repository HTTP 100mbit/s mirror provided thanks to OVH ([http://ovh.com](http://ovh.com))
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# PLF secondary repo. Use if primary repo is offline. FTP mirror from [http://free.fr](http://free.fr) (french ISP)
# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# PLF Mirrors: Use if primary and secondary are offline

# PLF mirror 1
# deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) dapper free non-free
 
# PLF mirror 2
# deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./

# Wine Official (Non-Ubuntu)
# deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
# deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/

# Wine Bleeding Edge
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Dapper-commercial by canonical
# currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# The Opera browser (packages)
# deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Automatix (packages, GPG key: 521A9C7C)
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

# Repository for Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# Cinelerra: Choose your Architecture
# i686:
# deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
# athlonxp:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
# pentium4:
# deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

# mjpegtools ubuntu backport (for Cinelerra)
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./

Hope it's a temp problem :confused: , hope somebody know's what's going on with the repos at the moment

---

### Post by iml on 2006-08-11
Yes, I'm having the same slowness, around 20kB/s.

---

### Post by iml on 2006-08-11
Seems to have cleared up now.

---


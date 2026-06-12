---
title: "removed /usr/bin/dpkg in ubuntu 15.04"
date: 2015-07-23
forum: Repositories &amp; Backports
---

### Post by mehdi10 on 2015-07-23
hi
i in ubuntu 15.04 removed file /usr/bin/dpkg  , now can't installed application .
hellp me.

---

### Post by slickymaster on 2015-07-23
Hi medhi10, welcome to the forums.

I'm afraid I don't have good news for you. You will have to replace that file in order to get a working system again.

You can try to download a copy of the **dpkg** package appropriate for your distribution from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and then extract it :
```
mkdir x
cd x
ar x ../path/to/where/the/downloaded/file/is/dpkg_version.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
```
Then copy the file into place:
```
sudo cp ./usr/bin/dpkg /usr/bin
```
Now re-install a clean version of dpkg to correct whatever state might be out of sync between the package manager's idea of what's installed and what's actually installed:```
sudo apt-get install --reinstall dpkg
```

But quite frankly my advise for you is to go with a fresh reinstall. Backup all you important data before doing it.

---

### Post by mehdi10 on 2015-07-23
hi, i get error :
```
engmmrj@engmmrj-MS-7592:~/Downloads/x$ ar x ~/Dwonloads/dpkg_1.17.25ubuntu1_amd64.deb
ar: /home/engmmrj/Dwonloads/dpkg_1.17.25ubuntu1_amd64.deb: No such file or directory



```

---

### Post by slickymaster on 2015-07-23
> **mehdi10 said:**
> hi, i get error :
```
engmmrj@engmmrj-MS-7592:~/Downloads/x$ ar x ~/Dwonloads/dpkg_1.17.25ubuntu1_amd64.deb
ar: /home/engmmrj/Dwonloads/dpkg_1.17.25ubuntu1_amd64.deb: No such file or directory



```
If you are already in the **x** directory just extract the archive```
ar x dpkg_version.deb
tar xzf data.tar.gz
```

---

### Post by mehdi10 on 2015-07-23
is it true.

---

### Post by slickymaster on 2015-07-23
> **mehdi10 said:**
> ```
engmmrj@engmmrj-MS-7592:~/Downloads/x$ ar x dpkg_version.deb
ar: dpkg_version.deb: No such file or directory
engmmrj@engmmrj-MS-7592:~/Downloads/x$ ls 
dpkg-1.17.25ubuntu1  dpkg_1.17.25ubuntu1_amd64.deb
engmmrj@engmmrj-MS-7592:~/Downloads/x$

```

dpkg_version.deb is just a made name I typed. Please run```
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
```

---

### Post by mehdi10 on 2015-07-23
> **slickymaster said:**
> dpkg_version.deb is just a made name I typed. Please run```
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
```
thank you, now want install application bzr but i get error :
```

engmmrj@engmmrj-MS-7592:~/Downloads$ sudo apt-get install bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bzr : Depends: python-bzrlib (<= 2.6.0+bzr6595-6ubuntu1.1~) but it is not going to be installed
       Depends: python-bzrlib (>= 2.6.0+bzr6595-6ubuntu1) but it is not going to be installed
       Recommends: python-gpgme but it is not going to be installed
 kerio-control-vpnclient:i386 : Depends: debconf:i386 (>= 0.5) but it is not installable
                                Depends: procps:i386 but it is not installable
 libasound2:i386 : Depends: libasound2-data:i386 (>= 1.0.28-1) but it is not installable
                   PreDepends: multiarch-support:i386 but it is not installable
 libasound2-plugins:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libasyncns0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libaudio2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libavahi-client3:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libavahi-common3:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libcdparanoia0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libcomerr2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libcups2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libdbus-1-3:i386 : PreDepends: multiarch-support:i386 but it is not installable
                    Recommends: dbus:i386 but it is not installable
 libdrm-intel1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libdrm-nouveau2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libdrm-radeon1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libdrm2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libedit2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libelf1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libexpat1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libffi6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libflac8:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.11.1-0ubuntu6) but it is not installable
                       PreDepends: multiarch-support:i386 but it is not installable
 libfreetype6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgcc1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgcrypt20:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgl1-mesa-dri:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgl1-mesa-glx:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libglapi-mesa:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libglib2.0-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
                     Recommends: libglib2.0-data:i386 but it is not installable
                     Recommends: shared-mime-info:i386 but it is not installable
                     Recommends: xdg-user-dirs:i386 but it is not installable
 libglu1-mesa:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgmp10:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgnutls-deb0-28:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgpg-error0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgssapi-krb5-2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libgstreamer-plugins-base1.0-0:i386 : Depends: iso-codes:i386 but it is not installable
                                       PreDepends: multiarch-support:i386 but it is not installable
 libgstreamer1.0-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libhogweed2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libice6:i386 : Depends: x11-common:i386 but it is not installable
                PreDepends: multiarch-support:i386 but it is not installable
 libicu52:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libjack-jackd2-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libjbig0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libjpeg-turbo8:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libjpeg62:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libjson-c2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libk5crypto3:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libkeyutils1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libkrb5-3:i386 : PreDepends: multiarch-support:i386 but it is not installable
                  Recommends: krb5-locales:i386 but it is not installable
 libkrb5support0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 liblcms2-2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libllvm3.6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 liblzma5:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libmng2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libmysqlclient18:i386 : Depends: mysql-common:i386 (>= 5.5) but it is not installable
                         PreDepends: multiarch-support:i386 but it is not installable
 libnettle4:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libogg0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 liborc-0.4-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libp11-kit0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libpciaccess0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libpcre3:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libpng12-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libpulse0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-dbus:i386 : Depends: qdbus:i386 (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1) but it is not installable
 libqt4-declarative:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-network:i386 : PreDepends: multiarch-support:i386 but it is not installable
                       Recommends: ca-certificates:i386 but it is not installable
 libqt4-opengl:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-script:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-sql:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-sql-mysql:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-xml:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqt4-xmlpatterns:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqtcore4:i386 : Depends: qtcore4-l10n:i386 but it is not installable
                   PreDepends: multiarch-support:i386 but it is not installable
 libqtdbus4:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libqtgui4:i386 : Depends: fontconfig:i386 but it is not installable
                  PreDepends: multiarch-support:i386 but it is not installable
 libqtwebkit4:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libsamplerate0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libselinux1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libsm6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libsndfile1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libspeexdsp1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libsqlite3-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libssl1.0.0:i386 : Depends: debconf:i386 (>= 0.5) but it is not installable or
                             debconf-2.0:i386 but it is not installable
                    PreDepends: multiarch-support:i386 but it is not installable
 libstdc++6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libsystemd0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libtasn1-6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libtheora0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libtiff5:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libtinfo5:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libtxc-dxtn-s2tc0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libudev1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libuuid1:i386 : Depends: passwd:i386 but it is not installable
                 PreDepends: multiarch-support:i386 but it is not installable
                 Recommends: uuid-runtime:i386 but it is not installable
 libvisual-0.4-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libvorbis0a:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libvorbisenc2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libwrap0:i386 : PreDepends: multiarch-support:i386 but it is not installable
                 Recommends: tcpd:i386 but it is not installable
 libx11-6:i386 : Depends: libx11-data:i386 but it is not installable
                 PreDepends: multiarch-support:i386 but it is not installable
 libx11-xcb1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxau6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxcb-dri2-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxcb-dri3-0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxcb-glx0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxcb-present0:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxcb-sync1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxcb1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxdamage1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxdmcp6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxext6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxfixes3:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxi6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxinerama1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxml2:i386 : PreDepends: multiarch-support:i386 but it is not installable
                Recommends: xml-core:i386 but it is not installable
 libxrandr2:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxrender1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxshmfence1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxslt1.1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxss1:i386 : Depends: x11-common:i386 but it is not installable
                PreDepends: multiarch-support:i386 but it is not installable
 libxt6:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxtst6:i386 : Depends: x11-common:i386 but it is not installable
                 PreDepends: multiarch-support:i386 but it is not installable
 libxv1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 libxxf86vm1:i386 : PreDepends: multiarch-support:i386 but it is not installable
 zlib1g:i386 : PreDepends: multiarch-support:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

### Post by slickymaster on 2015-07-23
Did you run the last two commands i gave you [here]("http://ubuntuforums.org/showthread.php?t=2287931&p=13326023&viewfull=1#post13326023") ```
sudo cp ./usr/bin/dpkg /usr/bin
sudo apt-get install --reinstall dpkg
```

---

### Post by mehdi10 on 2015-07-23
> **slickymaster said:**
> Did you run the last two commands i gave you [here]("http://ubuntuforums.org/showthread.php?t=2287931&p=13326023&viewfull=1#post13326023") ```
sudo cp ./usr/bin/dpkg /usr/bin
sudo apt-get install --reinstall dpkg
```
i sudo apt-get install f ran, , it's correct

---

### Post by slickymaster on 2015-07-23
> **mehdi10 said:**
> i sudo apt-get install f ran, , it's correct

The correct command is **sudo apt-get -f install**

Please post back here the output you get from```
sudo apt-get -f install
sudo apt-get install bzr
```

---


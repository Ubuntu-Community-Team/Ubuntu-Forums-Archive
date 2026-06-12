---
title: "Mono repository?"
date: 2007-10-09
forum: Repositories &amp; Backports
---

### Post by Charlatat on 2007-10-09
Is there one? If not, couldn't one be created? Its a PITA trying to get all the required libs installed, and packages compiled. I prefer Ubuntu and would like to it for development but with all the troubles I've encountered, I'm considering using OpenSuSe 10.2 (had too many problems with 10.3 so far), which is only "ok".

Even those on Mono's mailing list don't have a lot of suggestions to get all the dependencies worked out on Ubuntu.

Just a thought

---

### Post by Lord Illidan on 2007-10-09
I second this.

---

### Post by foxiness on 2007-10-10
me too to this "I'm third"

to be update with this "monodevelop" like "firefox" we must have a way to  
install it "we can not jest keep watching until second release"

---

### Post by Lord Illidan on 2007-10-11
Mono is pretty important for me, as I am learning c#, and I would like to do it on Linux, not on Windows. However, Ubuntu is not the best distro for it. Apart from the older versions of Mono and Monodevelop, many libraries are not that easy to find if you want it from source.

---

### Post by Charlatat on 2007-10-11
Actually, in a prior post, I did outline the steps I went thru to get the latest Mono/Monodevelop installed from source. Listed all the libraries I had to install to get things working too.

Was thinking maybe converting OpenSuSe's rpms into debs (after figuring out their dependences) from their repository.  Its kind of a stretch, but I'm curious enough to try.

Anyone know how to pipe the output of "rpm -i --test whatever.rpm" into a text file? There's a --pipe switch, but couldn't think of something to pipe it thru.

---

### Post by druhboruch on 2007-10-13
Monodevelop from getdeb works with gutsy...

---

### Post by Charlatat on 2007-10-15
but its not the latest version.

---

### Post by antmangaka on 2007-10-16
I support this thread :)
its very hard to compile it from source. 
like 4 month trying and nada :(

---

### Post by Charlatat on 2007-10-16
I outlined a manual way to install it here:

[http://ubuntuforums.org/showthread.php?t=558214](http://ubuntuforums.org/showthread.php?t=558214)

But I created a couple shell scripts to help out.

getlibs.sh :
```
#!/bin/bash

sudo apt-get update
sudo apt-get upgrade

sudo apt-get build-dep mono --assume-yes 
sudo apt-get build-dep gnome-devel --assume-yes
sudo apt-get build-dep build-essential --assume-yes
sudo apt-get build-dep devscripts --assume-yes
sudo apt-get build-dep dh-buildinfo --assume-yes
sudo apt-get build-dep sbuild --assume-yes
sudo apt-get build-dep pkg-config --assume-yes
sudo apt-get build-dep libextutils-pkgconfig-perl --assume-yes 
sudo apt-get build-dep libgift-dev --assume-yes
sudo apt-get build-dep libpthread-stubs0-dev --assume-yes
sudo apt-get build-dep xserver-xorg-dev --assume-yes
sudo apt-get build-dep bison --assume-yes
sudo apt-get build-dep libcairo2-dev --assume-yes
sudo apt-get build-dep libcairo-directfb2 --assume-yes
sudo apt-get build-dep libcairo-directfb2-dev --assume-yes
sudo apt-get build-dep libglib1.2 --assume-yes
sudo apt-get build-dep libglib1.2-dev --assume-yes
sudo apt-get build-dep libglib2.0-0 --assume-yes
sudo apt-get build-dep libglib2.0-cil --assume-yes
sudo apt-get build-dep libglib2.0-data --assume-yes
sudo apt-get build-dep libglib2.0-dev --assume-yes
sudo apt-get build-dep libungif4-dev --assume-yes
sudo apt-get build-dep libungif-bin --assume-yes
sudo apt-get build-dep libjpeg-progs --assume-yes
sudo apt-get build-dep libtiff4-dev --assume-yes
sudo apt-get build-dep libtiff-opengl --assume-yes
sudo apt-get build-dep libtiff-tools --assume-yes
sudo apt-get build-dep libtiffxx0c2 --assume-yes
sudo apt-get build-dep libgnome-desktop-dev --assume-yes
sudo apt-get build-dep libgtkhtml2-0 --assume-yes
sudo apt-get build-dep libgtkhtml2-dev --assume-yes
sudo apt-get build-dep libgtkhtml3.14-dev --assume-yes
sudo apt-get build-dep libgtkhtml3.8-dev --assume-yes
sudo apt-get build-dep libgtkhtml3.8-15 --assume-yes
sudo apt-get build-dep libgtkhtml3.8-dev --assume-yes
sudo apt-get build-dep libvte2.0-cil --assume-yes
sudo apt-get build-dep libvte-cil --assume-yes
sudo apt-get build-dep libvte-dev --assume-yes
sudo apt-get build-dep librsvg2-bin --assume-yes
sudo apt-get build-dep librsvg2-dev --assume-yes
sudo apt-get build-dep libgail-gnome-dev --assume-yes
sudo apt-get build-dep libgnome-cil --assume-yes
sudo apt-get build-dep libgnomedb2-4 --assume-yes
sudo apt-get build-dep libgnomedb2-bin --assume-yes
sudo apt-get build-dep libgnomedb2-dev --assume-yes
sudo apt-get build-dep libgnome-dev --assume-yes
sudo apt-get build-dep libpanel-applet2-dev --assume-yes
sudo apt-get build-dep gawk --assume-yes
sudo apt-get build-dep exif --assume-yes
sudo apt-get build-dep exiftags --assume-yes
sudo apt-get build-dep exiftran --assume-yes
sudo apt-get build-dep exifprobe --assume-yes
sudo apt-get build-dep libexif-gtk-dev --assume-yes
sudo apt-get build-dep libexif-gtk5 --assume-yes
sudo apt-get build-dep libsdl-pango1 --assume-yes
sudo apt-get build-dep libsdl-pango-dev --assume-yes
sudo apt-get build-dep monodevelop --assume-yes 

sudo aptitude install gnome-devel --with-recommends --assume-yes
sudo aptitude install build-essential --with-recommends --assume-yes
sudo aptitude install devscripts --with-recommends --assume-yes
sudo aptitude install dh-buildinfo --with-recommends --assume-yes
sudo aptitude install sbuild --with-recommends --assume-yes
sudo aptitude install pkg-config --with-recommends --assume-yes
sudo aptitude install libextutils-pkgconfig-perl --with-recommends --assume-yes
sudo aptitude install libgift-dev --with-recommends --assume-yes
sudo aptitude install libpthread-stubs0-dev --with-recommends --assume-yes
sudo aptitude install xserver-xorg-dev bison --with-recommends --assume-yes
sudo aptitude install libcairo2-dev --with-recommends --assume-yes
sudo aptitude install libcairo-directfb2 --with-recommends --assume-yes
sudo aptitude install libcairo-directfb2-dev --with-recommends --assume-yes
sudo aptitude install libglib1.2 --with-recommends --assume-yes
sudo aptitude install libglib1.2-dev --with-recommends --assume-yes
sudo aptitude install libglib2.0-0 --with-recommends --assume-yes
sudo aptitude install libglib2.0-cil --with-recommends --assume-yes
sudo aptitude install libglib2.0-data --with-recommends --assume-yes
sudo aptitude install libglib2.0-dev --with-recommends --assume-yes
sudo aptitude install libungif4-dev --with-recommends --assume-yes
sudo aptitude install libungif-bin --with-recommends --assume-yes
sudo aptitude install libjpeg-progs --with-recommends --assume-yes
sudo aptitude install libtiff4-dev --with-recommends --assume-yes
sudo aptitude install libtiff-opengl --with-recommends --assume-yes
sudo aptitude install libtiff-tools --with-recommends --assume-yes
sudo aptitude install libtiffxx0c2 --with-recommends --assume-yes
sudo aptitude install libgnome-desktop-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml2-0 --with-recommends --assume-yes
sudo aptitude install libgtkhtml2-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.14-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.8-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.8-15 --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.8-dev --with-recommends --assume-yes
sudo aptitude install libvte2.0-cil --with-recommends --assume-yes
sudo aptitude install libvte-cil --with-recommends --assume-yes
sudo aptitude install libvte-dev --with-recommends --assume-yes
sudo aptitude install librsvg2-bin --with-recommends --assume-yes
sudo aptitude install librsvg2-dev --with-recommends --assume-yes
sudo aptitude install libgail-gnome-dev --with-recommends --assume-yes
sudo aptitude install libgnome-cil --with-recommends --assume-yes
sudo aptitude install libgnomedb2-4 --with-recommends --assume-yes
sudo aptitude install libgnomedb2-bin --with-recommends --assume-yes
sudo aptitude install libgnomedb2-dev --with-recommends --assume-yes
sudo aptitude install libgnome-dev --with-recommends --assume-yes
sudo aptitude install libpanel-applet2-dev --with-recommends --assume-yes
sudo aptitude install gawk --with-recommends --assume-yes
sudo aptitude install exif --with-recommends --assume-yes
sudo aptitude install exiftags --with-recommends --assume-yes
sudo aptitude install exiftran --with-recommends --assume-yes
sudo aptitude install exifprobe --with-recommends --assume-yes
sudo aptitude install libexif-gtk-dev --with-recommends --assume-yes
sudo aptitude install libexif-gtk5 --with-recommends --assume-yes
sudo aptitude install libsdl-pango1 --with-recommends --assume-yes
sudo aptitude install libsdl-pango-dev --with-recommends --assume-yes

sudo apt-get autoremove --assume-yes

```

and installmono.sh :
```
#!/bin/bash

mkdir ~/Desktop/src
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/libgdiplus/libgdiplus-1.2.5.tar.bz2
tar xvf libgdiplus-1.2.5.tar.bz2
rm libgdiplus-1.2.5.tar.bz2
cd ~/Desktop/src/libgdiplus-1.2.5
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo sh -c "echo /usr/local >> /etc/ld.so.conf"
sudo sh -c "echo /usr/local/lib >> /etc/ld.so.conf"
sudo ldconfig

wget http://go-mono.com/sources/mono/mono-1.2.5.1.tar.bz2
tar xvf mono-1.2.5.1.tar.bz2
rm mono-1.2.5.1.tar.bz2
cd ~/Desktop/src/mono-1.2.5.1
./configure --prefix=/usr/local -with-preview=yes
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtk-sharp/gtk-sharp-1.0.10.tar.gz
tar xzf gtk-sharp-1.0.10.tar.gz
rm gtk-sharp-1.0.10.tar.gz
cd ~/Desktop/src/gtk-sharp-1.0.10
./configure --prefix=/usr/local -with-preview=yes
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtk-sharp210/gtk-sharp-2.10.2.tar.bz2
tar xvf gtk-sharp-2.10.2.tar.bz2
rm gtk-sharp-2.10.2.tar.bz2
cd ~/Desktop/src/gtk-sharp-2.10.2
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gecko-sharp2/gecko-sharp-2.0-0.12.tar.gz
tar xzf gecko-sharp-2.0-0.12.tar.gz
rm gecko-sharp-2.0-0.12.tar.gz
cd ~/Desktop/src/gecko-sharp-2.0-0.12
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gnome-sharp2/gnome-sharp-2.16.0.tar.gz
tar xzf gnome-sharp-2.16.0.tar.gz
rm gnome-sharp-2.16.0.tar.gz
cd ~/Desktop/src/gnome-sharp-2.16.0
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtksourceview-sharp2/gtksourceview-sharp-2.0-0.11.tar.bz2
tar xvf gtksourceview-sharp-2.0-0.11.tar.bz2
rm gtksourceview-sharp-2.0-0.11.tar.bz2
cd ~/Desktop/src/gtksourceview-sharp-2.0-0.11
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/monodoc/monodoc-1.2.5.zip
unzip monodoc-1.2.5.zip
rm monodoc-1.2.5.zip
cd ~/Desktop/src/monodoc-1.2.5
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/mono-tools/mono-tools-1.2.4.tar.bz2
tar xvf mono-tools-1.2.4.tar.bz2
rm mono-tools-1.2.4.tar.bz2
cd ~/Desktop/src/mono-tools-1.2.4
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/mono-debugger/mono-debugger-0.50.tar.bz2
tar xvf mono-debugger-0.50.tar.bz2
rm mono-debugger-0.50.tar.bz2
cd ~/Desktop/src/mono-debugger-0.50
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://download.gnome.org/sources/glade3/3.4/glade3-3.4.0.tar.bz2
tar xvf glade3-3.4.0.tar.bz2
rm glade3-3.4.0.tar.bz2
cd ~/Desktop/src/glade3-3.4.0
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo aptitude install monodoc-manual --with-recommends --assume-yes
sudo aptitude install monodevelop-boo --with-recommends --assume-yes
sudo aptitude install monodevelop-java --with-recommends --assume-yes
sudo aptitude install monodevelop-nunit --with-recommends --assume-yes
sudo aptitude install monodevelop-versioncontrol --with-recommends --assume-yes
sudo aptitude install monodevelop-query --with-recommends --assume-yes
sudo aptitude install nemerle --with-recommends --assume-yes
sudo aptitude install monodoc-gtk-manual --with-recommends --assume-yes
sudo aptitude install monodoc-gecko-manual --with-recommends --assume-yes
sudo aptitude install monodoc-nunit-manual --with-recommends --assume-yes
sudo aptitude install monodoc-browser --with-recommends --assume-yes
sudo aptitude install monodoc-http --with-recommends --assume-yes
sudo aptitude install monodoc-viewer --with-recommends --assume-yes

wget http://go-mono.com/sources/monodevelop/monodevelop-0.15.tar.bz2
tar xvf monodevelop-0.15.tar.bz2
rm monodevelop-0.15.tar.bz2
cd ~/Desktop/src/monodevelop-0.15
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo ldconfig

```

---

### Post by Alpha_Cluster on 2007-10-21
I'm surprised Novells Build Services have yet to be brought up. They don't yet have 7.10 but I'm guessing will soon but if you search for mono they got all the latest in a repo for Ubuntu 7.04. Link: [http://software.opensuse.org/search](http://software.opensuse.org/search)

---

### Post by RoundSparrow on 2007-11-03
Is Mono 1.2.5 now in Gutsy  repos somewhere or still build from source?

Thanks.

---

### Post by inyoka on 2008-03-28
Its times like this I wish I could build .debs, we definitely need an up to date mono and mono-develop on Ubuntu.  Tried getting OpenSuSE running in VirtualBox but it hung, which again reminded me why I use Ubuntu.

P.S Its mono 1.2.4-6 in Gutsy's repos (released May 15th, 2007),  and monodevelop 0.14.

---

### Post by rivera151 on 2008-03-30
> **Charlatat said:**
> I outlined a manual way to install it here:

[http://ubuntuforums.org/showthread.php?t=558214](http://ubuntuforums.org/showthread.php?t=558214)

But I created a couple shell scripts to help out.

getlibs.sh :
```
#!/bin/bash

sudo apt-get update
sudo apt-get upgrade

sudo apt-get build-dep mono --assume-yes 
sudo apt-get build-dep gnome-devel --assume-yes
sudo apt-get build-dep build-essential --assume-yes
sudo apt-get build-dep devscripts --assume-yes
sudo apt-get build-dep dh-buildinfo --assume-yes
sudo apt-get build-dep sbuild --assume-yes
sudo apt-get build-dep pkg-config --assume-yes
sudo apt-get build-dep libextutils-pkgconfig-perl --assume-yes 
sudo apt-get build-dep libgift-dev --assume-yes
sudo apt-get build-dep libpthread-stubs0-dev --assume-yes
sudo apt-get build-dep xserver-xorg-dev --assume-yes
sudo apt-get build-dep bison --assume-yes
sudo apt-get build-dep libcairo2-dev --assume-yes
sudo apt-get build-dep libcairo-directfb2 --assume-yes
sudo apt-get build-dep libcairo-directfb2-dev --assume-yes
sudo apt-get build-dep libglib1.2 --assume-yes
sudo apt-get build-dep libglib1.2-dev --assume-yes
sudo apt-get build-dep libglib2.0-0 --assume-yes
sudo apt-get build-dep libglib2.0-cil --assume-yes
sudo apt-get build-dep libglib2.0-data --assume-yes
sudo apt-get build-dep libglib2.0-dev --assume-yes
sudo apt-get build-dep libungif4-dev --assume-yes
sudo apt-get build-dep libungif-bin --assume-yes
sudo apt-get build-dep libjpeg-progs --assume-yes
sudo apt-get build-dep libtiff4-dev --assume-yes
sudo apt-get build-dep libtiff-opengl --assume-yes
sudo apt-get build-dep libtiff-tools --assume-yes
sudo apt-get build-dep libtiffxx0c2 --assume-yes
sudo apt-get build-dep libgnome-desktop-dev --assume-yes
sudo apt-get build-dep libgtkhtml2-0 --assume-yes
sudo apt-get build-dep libgtkhtml2-dev --assume-yes
sudo apt-get build-dep libgtkhtml3.14-dev --assume-yes
sudo apt-get build-dep libgtkhtml3.8-dev --assume-yes
sudo apt-get build-dep libgtkhtml3.8-15 --assume-yes
sudo apt-get build-dep libgtkhtml3.8-dev --assume-yes
sudo apt-get build-dep libvte2.0-cil --assume-yes
sudo apt-get build-dep libvte-cil --assume-yes
sudo apt-get build-dep libvte-dev --assume-yes
sudo apt-get build-dep librsvg2-bin --assume-yes
sudo apt-get build-dep librsvg2-dev --assume-yes
sudo apt-get build-dep libgail-gnome-dev --assume-yes
sudo apt-get build-dep libgnome-cil --assume-yes
sudo apt-get build-dep libgnomedb2-4 --assume-yes
sudo apt-get build-dep libgnomedb2-bin --assume-yes
sudo apt-get build-dep libgnomedb2-dev --assume-yes
sudo apt-get build-dep libgnome-dev --assume-yes
sudo apt-get build-dep libpanel-applet2-dev --assume-yes
sudo apt-get build-dep gawk --assume-yes
sudo apt-get build-dep exif --assume-yes
sudo apt-get build-dep exiftags --assume-yes
sudo apt-get build-dep exiftran --assume-yes
sudo apt-get build-dep exifprobe --assume-yes
sudo apt-get build-dep libexif-gtk-dev --assume-yes
sudo apt-get build-dep libexif-gtk5 --assume-yes
sudo apt-get build-dep libsdl-pango1 --assume-yes
sudo apt-get build-dep libsdl-pango-dev --assume-yes
sudo apt-get build-dep monodevelop --assume-yes 

sudo aptitude install gnome-devel --with-recommends --assume-yes
sudo aptitude install build-essential --with-recommends --assume-yes
sudo aptitude install devscripts --with-recommends --assume-yes
sudo aptitude install dh-buildinfo --with-recommends --assume-yes
sudo aptitude install sbuild --with-recommends --assume-yes
sudo aptitude install pkg-config --with-recommends --assume-yes
sudo aptitude install libextutils-pkgconfig-perl --with-recommends --assume-yes
sudo aptitude install libgift-dev --with-recommends --assume-yes
sudo aptitude install libpthread-stubs0-dev --with-recommends --assume-yes
sudo aptitude install xserver-xorg-dev bison --with-recommends --assume-yes
sudo aptitude install libcairo2-dev --with-recommends --assume-yes
sudo aptitude install libcairo-directfb2 --with-recommends --assume-yes
sudo aptitude install libcairo-directfb2-dev --with-recommends --assume-yes
sudo aptitude install libglib1.2 --with-recommends --assume-yes
sudo aptitude install libglib1.2-dev --with-recommends --assume-yes
sudo aptitude install libglib2.0-0 --with-recommends --assume-yes
sudo aptitude install libglib2.0-cil --with-recommends --assume-yes
sudo aptitude install libglib2.0-data --with-recommends --assume-yes
sudo aptitude install libglib2.0-dev --with-recommends --assume-yes
sudo aptitude install libungif4-dev --with-recommends --assume-yes
sudo aptitude install libungif-bin --with-recommends --assume-yes
sudo aptitude install libjpeg-progs --with-recommends --assume-yes
sudo aptitude install libtiff4-dev --with-recommends --assume-yes
sudo aptitude install libtiff-opengl --with-recommends --assume-yes
sudo aptitude install libtiff-tools --with-recommends --assume-yes
sudo aptitude install libtiffxx0c2 --with-recommends --assume-yes
sudo aptitude install libgnome-desktop-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml2-0 --with-recommends --assume-yes
sudo aptitude install libgtkhtml2-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.14-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.8-dev --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.8-15 --with-recommends --assume-yes
sudo aptitude install libgtkhtml3.8-dev --with-recommends --assume-yes
sudo aptitude install libvte2.0-cil --with-recommends --assume-yes
sudo aptitude install libvte-cil --with-recommends --assume-yes
sudo aptitude install libvte-dev --with-recommends --assume-yes
sudo aptitude install librsvg2-bin --with-recommends --assume-yes
sudo aptitude install librsvg2-dev --with-recommends --assume-yes
sudo aptitude install libgail-gnome-dev --with-recommends --assume-yes
sudo aptitude install libgnome-cil --with-recommends --assume-yes
sudo aptitude install libgnomedb2-4 --with-recommends --assume-yes
sudo aptitude install libgnomedb2-bin --with-recommends --assume-yes
sudo aptitude install libgnomedb2-dev --with-recommends --assume-yes
sudo aptitude install libgnome-dev --with-recommends --assume-yes
sudo aptitude install libpanel-applet2-dev --with-recommends --assume-yes
sudo aptitude install gawk --with-recommends --assume-yes
sudo aptitude install exif --with-recommends --assume-yes
sudo aptitude install exiftags --with-recommends --assume-yes
sudo aptitude install exiftran --with-recommends --assume-yes
sudo aptitude install exifprobe --with-recommends --assume-yes
sudo aptitude install libexif-gtk-dev --with-recommends --assume-yes
sudo aptitude install libexif-gtk5 --with-recommends --assume-yes
sudo aptitude install libsdl-pango1 --with-recommends --assume-yes
sudo aptitude install libsdl-pango-dev --with-recommends --assume-yes

sudo apt-get autoremove --assume-yes

```

and installmono.sh :
```
#!/bin/bash

mkdir ~/Desktop/src
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/libgdiplus/libgdiplus-1.2.5.tar.bz2
tar xvf libgdiplus-1.2.5.tar.bz2
rm libgdiplus-1.2.5.tar.bz2
cd ~/Desktop/src/libgdiplus-1.2.5
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo sh -c "echo /usr/local >> /etc/ld.so.conf"
sudo sh -c "echo /usr/local/lib >> /etc/ld.so.conf"
sudo ldconfig

wget http://go-mono.com/sources/mono/mono-1.2.5.1.tar.bz2
tar xvf mono-1.2.5.1.tar.bz2
rm mono-1.2.5.1.tar.bz2
cd ~/Desktop/src/mono-1.2.5.1
./configure --prefix=/usr/local -with-preview=yes
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtk-sharp/gtk-sharp-1.0.10.tar.gz
tar xzf gtk-sharp-1.0.10.tar.gz
rm gtk-sharp-1.0.10.tar.gz
cd ~/Desktop/src/gtk-sharp-1.0.10
./configure --prefix=/usr/local -with-preview=yes
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtk-sharp210/gtk-sharp-2.10.2.tar.bz2
tar xvf gtk-sharp-2.10.2.tar.bz2
rm gtk-sharp-2.10.2.tar.bz2
cd ~/Desktop/src/gtk-sharp-2.10.2
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gecko-sharp2/gecko-sharp-2.0-0.12.tar.gz
tar xzf gecko-sharp-2.0-0.12.tar.gz
rm gecko-sharp-2.0-0.12.tar.gz
cd ~/Desktop/src/gecko-sharp-2.0-0.12
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gnome-sharp2/gnome-sharp-2.16.0.tar.gz
tar xzf gnome-sharp-2.16.0.tar.gz
rm gnome-sharp-2.16.0.tar.gz
cd ~/Desktop/src/gnome-sharp-2.16.0
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtksourceview-sharp2/gtksourceview-sharp-2.0-0.11.tar.bz2
tar xvf gtksourceview-sharp-2.0-0.11.tar.bz2
rm gtksourceview-sharp-2.0-0.11.tar.bz2
cd ~/Desktop/src/gtksourceview-sharp-2.0-0.11
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/monodoc/monodoc-1.2.5.zip
unzip monodoc-1.2.5.zip
rm monodoc-1.2.5.zip
cd ~/Desktop/src/monodoc-1.2.5
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/mono-tools/mono-tools-1.2.4.tar.bz2
tar xvf mono-tools-1.2.4.tar.bz2
rm mono-tools-1.2.4.tar.bz2
cd ~/Desktop/src/mono-tools-1.2.4
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/mono-debugger/mono-debugger-0.50.tar.bz2
tar xvf mono-debugger-0.50.tar.bz2
rm mono-debugger-0.50.tar.bz2
cd ~/Desktop/src/mono-debugger-0.50
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://download.gnome.org/sources/glade3/3.4/glade3-3.4.0.tar.bz2
tar xvf glade3-3.4.0.tar.bz2
rm glade3-3.4.0.tar.bz2
cd ~/Desktop/src/glade3-3.4.0
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo aptitude install monodoc-manual --with-recommends --assume-yes
sudo aptitude install monodevelop-boo --with-recommends --assume-yes
sudo aptitude install monodevelop-java --with-recommends --assume-yes
sudo aptitude install monodevelop-nunit --with-recommends --assume-yes
sudo aptitude install monodevelop-versioncontrol --with-recommends --assume-yes
sudo aptitude install monodevelop-query --with-recommends --assume-yes
sudo aptitude install nemerle --with-recommends --assume-yes
sudo aptitude install monodoc-gtk-manual --with-recommends --assume-yes
sudo aptitude install monodoc-gecko-manual --with-recommends --assume-yes
sudo aptitude install monodoc-nunit-manual --with-recommends --assume-yes
sudo aptitude install monodoc-browser --with-recommends --assume-yes
sudo aptitude install monodoc-http --with-recommends --assume-yes
sudo aptitude install monodoc-viewer --with-recommends --assume-yes

wget http://go-mono.com/sources/monodevelop/monodevelop-0.15.tar.bz2
tar xvf monodevelop-0.15.tar.bz2
rm monodevelop-0.15.tar.bz2
cd ~/Desktop/src/monodevelop-0.15
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo ldconfig

```

Here's an edit that will make it a little easier upgrading.  Great script, by the way.

```

#! /bin/sh

LIBGDI_VER=1.9
MONO_VER=1.9
GTK1_VER=1.0.10
GTK2_VER=2.4.3
GECKO_VER=2.0-0.13
GNOME_VER=2.16.1
SRCVW_VER=2.0-0.12
MONODOC_VER=1.9
MONODEBUG_VER=0.60
GLADE_VER=3.4.0
MONODEVELOP_VER=1.0

mkdir ~/Desktop/src
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/libgdiplus/libgdiplus-$LIBGDI_VER.tar.bz2
tar xvf libgdiplus-$LIBGDI_VER.tar.bz2
rm libgdiplus-$LIBGDI_VER.tar.bz2
cd ~/Desktop/src/libgdiplus-$LIBGDI_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo sh -c "echo /usr/local >> /etc/ld.so.conf"
sudo sh -c "echo /usr/local/lib >> /etc/ld.so.conf"
sudo ldconfig

wget http://go-mono.com/sources/mono/mono-$MONO_VER.tar.bz2
tar xvf mono-$MONO_VER.tar.bz2
rm mono-$MONO_VER.tar.bz2
cd ~/Desktop/src/mono-$MONO_VER
./configure --prefix=/usr/local -with-preview=yes
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtk-sharp/gtk-sharp-$GTK1_VER.tar.gz
tar xzf gtk-sharp-$GTK1_VER.tar.gz
rm gtk-sharp-$GTK1_VER.tar.gz
cd ~/Desktop/src/gtk-sharp-$GTK1_VER
./configure --prefix=/usr/local -with-preview=yes
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtk-sharp210/gtk-sharp-$GTK2_VER.tar.bz2
tar xvf gtk-sharp-$GTK2_VER.tar.bz2
rm gtk-sharp-$GTK2_VER.tar.bz2
cd ~/Desktop/src/gtk-sharp-$GTK2_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gecko-sharp2/gecko-sharp-$GECKO_VER.tar.gz
tar xzf gecko-sharp-$GECKO_VER.tar.gz
rm gecko-sharp-$GECKO_VER.tar.gz
cd ~/Desktop/src/gecko-sharp-$GECKO_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gnome-sharp2/gnome-sharp-$GNOME_VER.tar.gz
tar xzf gnome-sharp-$GNOME_VER.tar.gz
rm gnome-sharp-$GNOME_VER.tar.gz
cd ~/Desktop/src/gnome-sharp-$GNOME_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/gtksourceview-sharp2/gtksourceview-sharp-$SRCVW_VER.tar.bz2
tar xvf gtksourceview-sharp-$SRCVW_VER.tar.bz2
rm gtksourceview-sharp-$SRCVW_VER.tar.bz2
cd ~/Desktop/src/gtksourceview-sharp-$SRCVW_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/monodoc/monodoc-$MONODOC_VER.zip
unzip monodoc-$MONODOC_VER.zip
rm monodoc-$MONODOC_VER.zip
cd ~/Desktop/src/monodoc-$MONODOC_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/mono-tools/mono-tools-$MONOTOOLS_VER.tar.bz2
tar xvf mono-tools-$MONOTOOLS_VER.tar.bz2
rm mono-tools-$MONOTOOLS_VER.tar.bz2
cd ~/Desktop/src/mono-tools-$MONOTOOLS_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://go-mono.com/sources/mono-debugger/mono-debugger-$MONODEBUG_VER.tar.bz2
tar xvf mono-debugger-$MONODEBUG_VER.tar.bz2
rm mono-debugger-$MONODEBUG_VER.tar.bz2
cd ~/Desktop/src/mono-debugger-$MONODEBUG_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

wget http://download.gnome.org/sources/glade3/3.4/glade3-$GLADE_VER.tar.bz2
tar xvf glade3-$GLADE_VER.tar.bz2
rm glade3-$GLADE_VER.tar.bz2
cd ~/Desktop/src/glade3-$GLADE_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo aptitude install monodoc-manual --with-recommends --assume-yes
sudo aptitude install monodevelop-boo --with-recommends --assume-yes
sudo aptitude install monodevelop-java --with-recommends --assume-yes
sudo aptitude install monodevelop-nunit --with-recommends --assume-yes
sudo aptitude install monodevelop-versioncontrol --with-recommends 
--assume-yes
sudo aptitude install monodevelop-query --with-recommends --assume-yes
sudo aptitude install nemerle --with-recommends --assume-yes
sudo aptitude install monodoc-gtk-manual --with-recommends --assume-yes
sudo aptitude install monodoc-gecko-manual --with-recommends 
--assume-yes
sudo aptitude install monodoc-nunit-manual --with-recommends 
--assume-yes
sudo aptitude install monodoc-browser --with-recommends --assume-yes
sudo aptitude install monodoc-http --with-recommends --assume-yes
sudo aptitude install monodoc-viewer --with-recommends --assume-yes

wget http://go-mono.com/sources/monodevelop/monodevelop-$MONO_VER.tar.bz2
tar xvf monodevelop-$MONO_VER.tar.bz2
rm monodevelop-$MONO_VER.tar.bz2
cd ~/Desktop/src/monodevelop-$MONO_VER
./configure --prefix=/usr/local
make
sudo make install
cd ~/Desktop/src
clear

sudo ldconfig

```

---

### Post by randomstuff on 2008-03-31
Please consider voting for mono and monodevelop inclusion in hardy on the brainstorm site:

[[IMG]http://brainstorm.ubuntu.com/idea/6088/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/6088/)
[[IMG]http://brainstorm.ubuntu.com/idea/4846/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4846/)

Also please try to spread the word about this.

---

### Post by prensing on 2008-04-02
I tried compiling mono 1.9 for my machine (7.10 64-bit) using prevu. That worked for me for 1.2.6. However, I cannot find a copy of the original source; specifically, the .dsc file is looking for mono_1.9+dfsg.orig.tar.gz which is the slightly modified file from Debian, but I could not find a copy. If anyone has it, or knows how to generate it, please post.

I definitely think there should be an archive which has the latest Mono for Ubuntu.

---

### Post by o xavi on 2008-04-17
I guys I have been trying to install all the libraries and software it is in your scripts for a couple of days. Now that I have everything installed and running fine I can't get Monodevelop to install in my machine :( In fact, to have Monodevelop up and running so I could use it to start with mono and gtk# was my objective so it is disappointing to be stuck so close to it. 

So, this is what I get when I run the ./configure --prefix=/usr/local command:


----
javi@javi-laptop:~/scripts/monodevelop-1.0$ ./configure --prefix=/usr/local
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for mono... /usr/local/bin/mono
checking for gmcs... /usr/local/bin/gmcs
checking for update-mime-database... /usr/bin/update-mime-database
checking for update-desktop-database... /usr/bin/update-desktop-database
checking for pkg-config... /usr/bin/pkg-config
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking pkg-config is at least version 0.9.0... yes
checking for UNMANAGED_DEPENDENCIES_MONO... yes
checking for mono... /usr/local/bin/mono
checking for gmcs... /usr/local/bin/gmcs
checking for MONO_ADDINS... yes
checking for MONO_ADDINS_SETUP... yes
checking for MONO_ADDINS_GUI... yes
checking for GLIB_SHARP... configure: error: Package requirements (glib-sharp-2.0 >= 2.8.0) were not met:

Requested 'glib-sharp-2.0 >= 2.8.0' but version of GLib is 2.4.3

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_SHARP_CFLAGS
and GLIB_SHARP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

-----
But I have Glib 2.8 installed!!!


I am running Ubuntu 7.10, in an 32 bit Intel station. 

Has anybody had this erro message before?? Some help would be really apreciated.

Thanks in advance.

xavi.

---

### Post by o xavi on 2008-04-22
It´s me again. I have just found the way to fix the error I got yesterday. It was an issue with Glib but specifically from the Gtk-Sharp library. I had just to install a newer version of it and the problem disappeared. I wonder why you didn´t get this message if you installed the same libraries as me.

There is one thing I don´t get, why do we need to install two versions of Gtk-sharp (1.X and 2.X)? I presume it is just a technical issue but it still makes me curious? If I find out the reason I would write a new post :)

see you,

o_xavi.

---

### Post by ihavenoname on 2008-04-22
> **o xavi said:**
> It´s me again. I have just found the way to fix the error I got yesterday. It was an issue with Glib but specifically from the Gtk-Sharp library. I had just to install a newer version of it and the problem disappeared. I wonder why you didn´t get this message if you installed the same libraries as me.

There is one thing I don´t get, why do we need to install two versions of Gtk-sharp (1.X and 2.X)? I presume it is just a technical issue but it still makes me curious? If I find out the reason I would write a new post :)

see you,

o_xavi.

I believe they are different. For a while (I am not sure if this is still true). We had gtk 1 and 2 in the repos as well. By the way I believe the mono vernsions discussed earlier in this thread are now obsolete. If I  correctly mono is at version 1.9 and monodevelop is actually version 1.0 now. There is a mono installer now as well that you can use, I was not successful with it but you may have more luck with it than I. Make sure you have all the dependencies satisfied (you may have to tap into the debian repositores for a few updated version of some libraries, then run the installer and install mono that way while we wait for an update.

---

### Post by trippinnik on 2008-04-23
Why not try using one of the PPAs? [https://launchpad.net/~firerabbit/+archive](https://launchpad.net/~firerabbit/+archive)
this one has a pretty up to date mono, maybe you'll have to look a bit more for monodevelop.

---

### Post by prensing on 2008-05-01
> **trippinnik said:**
> Why not try using one of the PPAs? [https://launchpad.net/~firerabbit/+archive](https://launchpad.net/~firerabbit/+archive)
this one has a pretty up to date mono, maybe you'll have to look a bit more for monodevelop.

Looks promising, but I guess no one is using this because **you can't find it!** I tried to find those packages (after a long hunt for what "PPA" stand for ;-) using the Launchpad search and came up empty handed. If something does not come up when you search, no one is going to know to use it. 

Also, if I understand the interface correctly, the Mono 1.9 packages failed to build correctly, so I don't know that the packages can be used.

---


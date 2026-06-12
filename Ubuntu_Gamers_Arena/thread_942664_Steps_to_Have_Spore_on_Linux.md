---
title: "Steps to Have Spore on Linux"
date: 2008-10-09
forum: Ubuntu Gamers Arena
---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-10-09
:KS Just follow this steps:

Requirements

    * git and various needed libraries for compiling wine-git, the patches required for playing spore are in the current git mainline for wine
    * A Decent System: This guide was tested on an dell xps 1210 3.5GB Ram, Ubuntu 8.04.1 (amd64)
    * Up to date graphics driver (NVIDIA beta 177.67 was tested)
    * NoCD crack (Also known "as DRM is stupid and stops things working properly, and stop trying to pretend games copying takes away from sales, fix")) 

Getting Wine Compiled

On Amd64 systems for distros that do not support multi-lib (Debian based, and others), you need to do some manual symlinking in the wine-git checkouted repository to the location on the 32bit libs.

The winehq guide has a wiki on compiling for amd64, I presume this is not needed for 32bit dists. it can be found here : [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

For the lazy steps:
[edit] Step 1: Create a directory (as normal user) somewhere with space, and move into it.

```
mkdir ~/git
cd ~/git
```

Step 2: Get wine dependancies and, git. ( [http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine) )

```
sudo apt-get build-dep wine
sudo apt-get install git-core
```

Headline text
Step 3: Check out wine-git

git clone git://source.winehq.org/git/wine.git ~/git/wine-git

Step 4: Make lib32 symlinks in wine-git directory (amd64 only, location may be different for dists other than debian/ubuntu)

```
cd ~/git/wine-git
mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
```

 Step 5: Configure and compile wine-git (you don't need the ldflags if you are not on amd64)

```
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v
make depend
make
sudo make install

```
[edit] Step 6: Check that the version of wine in your path is the git one (wine --version should report something like 1.4.asddgf )If not remove wine from package manager to clean any dist versions out, and re-run make install from the wine-git directory
 Step 7: Install Spore (wine <path to spore setup>)
 Step 8: Copy over the NoCD patched .exe over SporeApp.exe

```
cp /path/to/spore/SporeBin/SporeApp.exe /path/to/spore/SporeBin/SporeApp.exe.orginal
cp /path/to/nocd/SporeApp.exe /path/to/spore/SporeBin/SporeApp.exe

```

Step 9: Run spore with the follow (this turns off console logging of error messages which can hinder performance)
```

WINEDEBUG=-all wine /path/to/spore/SporeBin/SporeApp.exe
```

 Step 10: Rejoice

:KS Original Article: [http://spore.wikia.com/wiki/How_to_get_Spore_working_on_Linux]("http://spore.wikia.com/wiki/How_to_get_Spore_working_on_Linux")

---

### Post by Bios Element on 2008-10-20
Erm...It should be noted that you don't need to compile WINE with patches to run spore...It runs just fine without.

---


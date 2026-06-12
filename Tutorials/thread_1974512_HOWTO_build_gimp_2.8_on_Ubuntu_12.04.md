---
title: "HOWTO: build gimp 2.8 on Ubuntu 12.04"
date: 2012-05-06
forum: Tutorials
---

### Post by k999 on 2012-05-06
Install necessary tools and dependencies:

```
sudo apt-get install git build-essential libgtk2.0-dev libpango1.0-dev libgdk-pixbuf2.0-dev libglib2.0-dev libcairo2-dev libfreetype6-dev fontconfig libdbus-glib-1-dev liblcms2-dev libpng12-dev libjpeg-dev libpoppler-dev libpoppler-glib-dev libtiff4-dev libwebkit-dev libmng-dev librsvg2-dev libwmf-dev zlib1g-dev libbz2-dev libgs-dev libaa1-dev libjasper-dev python-dev python-gtk2-dev libtool autoconf automake libexiv2-dev openexr libopenexr-dev exrtools dcraw libopenraw-dev libsdl1.2-dev graphviz libgraphviz-dev libavformat-dev libspiro-dev libumfpack5.4.0 enscript ruby-dev liblua5.2-dev gtk-doc-tools libgudev-1.0-dev libexif-dev libxpm-dev

```

Then fetch the dependencies you need to build:
```
git clone git://git.gnome.org/babl
git clone git://git.gnome.org/gegl
```

and build them:
```
cd babl
./autogen.sh --prefix=$HOME/build
make
make install
cd ..

cd gegl
PKG_CONFIG_PATH=$HOME/build/lib/pkgconfig ./autogen.sh --prefix=$HOME/build
make
make install
cd ..
```

Get the gimp source. CHOOSE ONE:

EITHER, download and unpack the tarball (recommended):
```
wget ftp://ftp.gimp.org/pub/gimp/v2.8/gimp-2.8.0.tar.bz2
tar xvfj gimp-2.8.0.tar.bz2
cd gimp-2.8.0
```

OR clone the git repo and check out 2.8.0:
```
git clone http://git.gnome.org/cgit/gimp
cd gimp
git checkout GIMP_2_8_0
```

Now, build it gimp:
```
PKG_CONFIG_PATH=$HOME/build/lib/pkgconfig ./autogen.sh --prefix=$HOME/build
make
make install
```

That's it. Now you can run gimp-2.8 like this:
```
LD_LIBRARY_PATH=$HOME/build/lib $HOME/build/bin/gimp-2.8
```

Let me know if anything needs fixing. The install list can definitely be trimmed.

---

### Post by BlackMaxPhoto on 2013-02-18
Building from the tarball ...

After:

# PKG_CONFIG_PATH=$HOME/build/lib/pkgconfig ./autogen.sh --prefix=$HOME/build

return is:
bash: ./autogen.sh: No such file or directory


???

:confused:


ls:

acinclude.m4       config.h.win32   INSTALL         NEWS
aclocal.m4         config.sub       install-sh      NEWS.pre-2-0
app                configure        libgimp         NEWS.pre-2-2
AUTHORS            configure.ac     libgimpbase     NEWS.pre-2-4
authors.dtd        COPYING          libgimpcolor    NEWS.pre-2-6
authors.xml        cursors          libgimpconfig   plug-ins
authors.xsl        data             libgimpmath     po
build              depcomp          libgimpmodule   po-libgimp
ChangeLog          desktop          libgimpthumb    po-plug-ins
ChangeLog.pre-1-0  devel-docs       libgimpwidgets  po-python
ChangeLog.pre-1-2  docs             LICENSE         po-script-fu
ChangeLog.pre-2-0  etc              ltmain.sh       po-tips
ChangeLog.pre-2-2  gimp.pc.in       m4macros        py-compile
ChangeLog.pre-2-4  gimpthumb.pc.in  Makefile.am     README
ChangeLog.pre-2-6  gimpui.pc.in     Makefile.in     README.i18n
compile            gimp-zip.in      menus           themes
config.guess       gtk-doc.make     missing         tools
config.h.in        HACKING          modules

---

### Post by BlackMaxPhoto on 2013-02-18
... building from 'git':

"... checking for BABL... yes
checking for GEGL... no
configure: error: Package requirements (gegl-0.2 >= 0.2.0) were not met:

No package 'gegl-0.2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GEGL_CFLAGS
and GEGL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Configure failed or did not finish!"


Not working either way building for Ubuntu 12.04.1 or UBS 12.04.2


:confused:

---

### Post by elpraga on 2013-06-24
Hi guys,
I hit the same problem, and I found the solution. The reason it could not find the gegl was that the new gegl we get from the git is gegl-0.3. For some reason it does not dot work and we have to use the gegl-0.2 version.

We can get it here:

[ftp://ftp.gimp.org/pub/gegl/0.2/](ftp://ftp.gimp.org/pub/gegl/0.2/)

After compiling this version all goes as expected.

Im happily using the 2.8.6 version of GIMP on my Ubuntu 12.04!

Thanks for the great post! It was really simple to use it!

---


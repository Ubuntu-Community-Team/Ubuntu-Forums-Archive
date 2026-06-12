---
title: "How to compile gpac / mp4box from source?"
date: 2009-07-17
forum: Ubuntu Studio
---

### Post by Nixie Pixel on 2009-07-17
Hello, is there a guide out there anywhere that can tell me how to get the latest version of gpac (0.4.5?) and compile it from source?

Thanks!

---

### Post by FakeOutdoorsman on 2009-07-17
Here's a quick run-through to give you a start.  I didn't get to test it like I wanted to and the checkinstall section could use some work:

1. Remove old gpac
```
sudo apt-get purge gpac
```

2. Get dependencies
```
sudo apt-get install build-essential zlib1g-dev checkinstall
```
There are probably more dependencies, but I didn't test this on a clean system.

3. Compile GPAC
```
cd
wget [http://downloads.sourceforge.net/gpac/gpac-0.4.5.tar.gz](http://downloads.sourceforge.net/gpac/gpac-0.4.5.tar.gz)
tar xzvf gpac-0.4.5.tar.gz
cd gpac
chmod +x configure
./configure --mandir=/usr/local/share/man
make
```

4. Install GPAC
```
sudo checkinstall --pkgname=gpac --pkgversion "0.4.5"
```

I was having a few issues possibly related to an unclean test system so I changed some checkinstall settings to:
```
4 -  Release: [ 1 ]
10 - Requires: [  ]
```

On the checkinstall command the *--pkgversion* could probably be improved to prevent apt from being greedy and attempting to down/upgrade your custom version.  Also, you can probably declare the release with *--pkgrelease*, the requirements with *--requires*, and use *--default* to answer those annoying questions automatically.

That should do it.  I didn't get to spend as much time on this as I wanted.  Stupid deadlines.

---

### Post by Nixie Pixel on 2009-07-17
Thanks for the help! Unfortunately, compiling failed, probably because of a missing dependency. Since I am new to this, perhaps you can give me some advice on how to find the dependencies?

Thanks again!

---

### Post by mc4man on 2009-07-17
I'm not going to step to far into this discusion, mainly because I don't use gpac itself, though do use libgpac-dev, so have built 0.4.5 on my hardy install (as a debian package set.

Anyway happened to be on a jaunty live cd atm, so built the set quickly.

The apt-get build-deps is somewhat deficient for 0.4.5 on jaunty (or intrepid, hardy

You could add these (blue is optional I believe, red is just for package building

> sudo apt-get install [COLOR="Red"]devscripts[/COLOR] libwxgtk2.8-dev xulrunner-1.9-dev libpulse-dev libfaad-dev libogg-dev libjack-dev libxv-dev libvorbis-dev libtheora-dev liba52-0.7.4-dev [COLOR="Blue"]libmozjs-dev[/COLOR] libopenjpeg-dev  libxmlrpc-c3-dev [COLOR="Red"]quilt[/COLOR]

libgpac-dev must not be installed prior to building (on jaunty


The main decisions are 
whether to use system libraries or local (on source)
whether to enable MOZILLA_1_8_BRANCH SpiderMonkey macro (enabled if the blue above is installed
whether to include the amr libraries (requires external sources to be added to gpac source plus configuring in
whether to add the few add. options (joystick

In the gpac source you'll see a docs folder, look for the ...gcc file, will provide some info.

./configure --help is also good to look at


Here's the beginning of my build log, may prove informative
> 
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package gpac
dpkg-buildpackage: source version 0.4.5-0.3ubuntu1
dpkg-buildpackage: source changed by Julien Lavergne <julien.lavergne@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
[ ! -f config.mak ] || /usr/bin/make distclean
debian/rules unpatch
make[1]: Entering directory `/home/ubuntu/gpac/gpac-0.4.5'
QUILT_PATCHES=debian/patches quilt --quiltrc /dev/null pop -a -R || test $? = 2 
No patch removed
rm -rf .pc debian/stamp-patched
make[1]: Leaving directory `/home/ubuntu/gpac/gpac-0.4.5'
dh_clean config.h bin/gcc/libgpac*
 dpkg-source -b gpac-0.4.5
dpkg-source: info: using source format `1.0'
dpkg-source: info: building gpac in gpac_0.4.5-0.3ubuntu1.tar.gz
dpkg-source: info: building gpac in gpac_0.4.5-0.3ubuntu1.dsc
 debian/rules build
# quilt exits with 2 as return when there was nothing to do. 
# That's not an error here (but it's useful to break loops in crude scripts)
QUILT_PATCHES=debian/patches quilt --quiltrc /dev/null push -a || test $? = 2
Applying patch 01_soname.patch
patching file src/Makefile

Applying patch 02_amd64.diff
patching file configure

Applying patch 03_memeset-typo.diff
patching file src/isomedia/box_code_base.c

Now at patch 03_memeset-typo.diff
touch debian/stamp-patched
dh_testdir
chmod 755 configure
./configure --build i486-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man \
	--extra-cflags="-fPIC -DPIC -I/usr/include/mozjs -DXP_UNIX -Wall -g" \
	 --enable-joystick
WARNING: Turning on MOZILLA_1_8_BRANCH SpiderMonkey macro
If you have troubles with scripts in GPAC, disable this macro and recompile


** System Configuration
Install prefix: /usr
Source path: /home/ubuntu/gpac/gpac-0.4.5
C compiler: gcc
make: make
CPU: x86
Big Endian: no

** GPAC 0.4.5 Core Configuration **
debug version: no
GProf enabled: no
Memory tracking enabled: no
read-only version: no
fixed-point version: no
IPV6 Support: yes
IsoMedia MovieFragments support: yes
SVG Support disabled: no

** Detected libraries **
zlib: system
OSS Audio: yes
ALSA Audio: yes
Jack Audio: yes
PulseAudio Audio: yes
X11 Shared Memory support: yes (path: /usr/X11R6)
X11 XVideo support: yes
SDL Support: yes
OpenGL support: yes
TinyGL support: no
OpenSSL support: yes
Mozilla XUL/GECKO support: no
Joystick support: yes
Renoir enabled: no
DVB Support: yes
XMLPRC Support: yes
wxWidgets support: Version 289

** Extra Libraries used **
SpiderMonkey: system
FreeType: system
JPEG: system
OpenJPEG: system
PNG: system
MAD: system
FAAD: system
XVID: system
FFMPEG: local
Xiph OGG: system
Xiph Vorbis: system
Xiph Theora: system
A52 (AC3): system


The other reason is I tthink this may be better built as a debian package set rather than other means (gpac, libgpac0, libgpac-dev

note that in this case using the karmic diff, the debian-multimedia diff also works well (used that on hardy

edit: what I meant to mention - for a configure, make, make install or checkinstall a straight ./configure should be fine. Your additions to that would mainly be based on forcing the extra libraries if desired, for the most part they are auto detected and will default to 'system' if the -dev's are installed, local otherwise.or disabled if configured so (the exception is ffmpeg which is local on jaunty, hardy (current libavcodec52, ect. based), can be system on intrepid

tested also on Amd_64 build (intrepid), builds and installs fine (benefits from --extra-cflags="-fPIC -DPIC "

---

### Post by qyot27 on 2009-07-18
This is the sequence I used when compiling GPAC:

```
wget http://superb-east.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.5.tar.gz
wget http://voxel.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.5.tar.gz
tar -zxf gpac-0.4.5.tar.gz
tar -zxf gpac_extra_libs-0.4.5.tar.gz
cd gpac_extra_libs
cp -r * ../gpac/extra_lib
cd ../gpac
chmod +x configure
./configure --disable-opengl --use-js=no --use-ft=no --use-jpeg=no --use-png=no --use-faad=no --use-mad=no --use-xvid=no --use-ffmpeg=no --use-ogg=no --use-vorbis=no --use-theora=no --use-openjpeg=no
make lib
make apps
sudo make install-lib
sudo make install
sudo cp bin/gcc/libgpac.so /usr/lib
```
(yes, those ./configure disables are a bit paranoid, but it works for me - all I needed GPAC for was to enable MP4 output in x264)

If, however, it complains about not having zlib-1.2.3 (and zlib1g-dev from the repositories isn't sufficient - I still haven't tested whether it's fine or not), then do this *before* compiling GPAC:
```
wget http://www.zlib.net/zlib-1.2.3.tar.gz
tar -zxf zlib-1.2.3.tar.gz
cd zlib-1.2.3
./configure
make
sudo make install
```

---

### Post by FakeOutdoorsman on 2009-07-18
> **Nixie Pixel said:**
> Thanks for the help! Unfortunately, compiling failed, probably because of a missing dependency. Since I am new to this, perhaps you can give me some advice on how to find the dependencies?

Thanks again!

I just retested this again on a clean, vanilla Jackalope installation and it went fine.  This only extra dependency I needed was *checkinstall*.  Since it's a clean install I didn't install any third-party libraries, so I don't know how that would limit MP4Box if at all:
```
** Extra Libraries used **
SpiderMonkey: no
FreeType: no
JPEG: no
OpenJPEG: no
PNG: no
MAD: no
FAAD: no
XVID: no
FFMPEG: no
Xiph OGG: no
A52 (AC3): no
```
What Ubuntu version are you using?  What errors did you get when compiling failed?

---

### Post by Nixie Pixel on 2009-07-18
I am actually getting errors regarding missing directories when I try to do the checkinstall. If I try to mkdir the missing directories, it gives me new errors about other missing things. 

The compiler seems to be doing ok, but not the installation. I will try to run through the steps again and copy the output...

I am running this on Ubuntu Server 8.10.

---

### Post by FakeOutdoorsman on 2009-07-19
> **Nixie Pixel said:**
> I am running this on Ubuntu Server 8.10.

Oops...I should have asked that first. I believe 8.10 was kind of picky with checkinstall and needs additional checkinstall options.  You don't need to re-compile.  Just navigate into your gpac directory and try this:
```

sudo checkinstall --fstrans=no --install=yes --pkgname=gpac --pkgversion "0.4.5"
```

This is just a guess and I didn't do a test run. You may have to adjust *Release* and *Requires* as mentioned before.

---

### Post by Nixie Pixel on 2009-07-19
Ok, something I did messed something else up. Now I'm getting an error on compiling the program:

```
/usr/bin/ld: /usr/local/lib/libz.a(gzio.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libgpac.so] Error 1
make[1]: Leaving directory `/home/nixie/gpac/src'
make: *** [lib] Error 2
```

Any ideas?

I tried installing the zlib from qyot27 above, but that didn't help.

---

### Post by mc4man on 2009-07-20
> Any ideas?
Well, your getting a zlib error, considering this
> I tried installing the zlib .............

you should undo what you did.

The repo versions, whether for 8.04, 8.10, 9.04 are perfectly fine for building gpac. (they are all basically the same
What you want installed, whether on a 32 or 64 bit install is zlib1g, zlib1g-dev.

(( if you are on a 64 bit install there are 32 bit libs available (lib32z1, lib32z1-dev and vice-versa on a 32 bit install, you don't want or need them


> am actually getting errors regarding missing **directories** when I try to do the checkinstall



Checkinstall may fail in different ways, the --fstrans=no would take care of an error concerning 1 dir. ( a tmp

It would be useful  posting the actual errors or in many cases checkinstall will offer the view a log.
I'd think you'd need to set a release number, but if you're getting errors concerning directories other than a tmp then it may also be failing to install the deb. (or will when given the chance

I'd also remove any dir.'s you created due to checkinstall errors, and maybe start with a fresh source when zlib is squared away

edit
As per usual I forgot to mention something, there's a slight chance that if you run 
sudo ldconfig
that your zlib install to /urs/local will become useful, though I'd just get rid of it and use the repo packages

---

### Post by Nixie Pixel on 2009-07-20
Ok, I will undo everything and then try again with the repository packages.

But...how do I undo what I have done? There are lots of guides out there to tell you how to compile and install things, but how do I manually remove it?

Thanks!

---

### Post by mc4man on 2009-07-20
> how do I undo what I have done? 
That would depend on what you did. 

Generally speaking the below is how to undo an install from source

In this case though I'd tread very carefully, zlib is core to many things, you may want to post how you configured it first and confirm that zlib1g is presently installed to /usr (check in your package manager), I wouldn't remove your built version unless it is
this 
```
 whereis libz.so
```

should show some entries for /usr/lib


If you only built and installed as static libraries then it should be safe to remove, though if so and you do so as below, run sudo ldconfig before rebooting just to be safe

If you configured as ./configure --shared please post so before procedding



.......................................................................

 cd to the zlip-1.2.3 source folder and run 
```
sudo make uninstall
```

If you had deleted it, (the source folder you built zlib from) then you'd need to remove manually.

Again assuming you did just a ./configure, make, sudo make install these are the installed files 

usr/local/lib/libz.a
usr/local/include/zconf.h
usr/local/include/zlib.h
usr/local/share/man/man3/zlib.3.gz
usr/share/doc/zlib

---

### Post by Nixie Pixel on 2009-07-21
Ok, I followed these steps:
Uninstall zlibg1 (source)
Uninstall gpac (source)
Install dependencies per mc4man's post above.
Download and configure gpac per FakeOutdoorsman's post above.

Attempt to compile...failed, here are the last lines:

```
scenegraph/vrml_smjs.c:3709: error: expected ‘)’ before ‘*’ token
scenegraph/vrml_smjs.c: In function ‘JSScript_NodeModified’:
scenegraph/vrml_smjs.c:3727: error: ‘JSObject’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3727: error: ‘obj’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3742: warning: cast to pointer from integer of different size
scenegraph/vrml_smjs.c: In function ‘gf_sg_handle_dom_event_for_vrml’:
scenegraph/vrml_smjs.c:3757: error: ‘JSBool’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3757: error: expected ‘;’ before ‘ret’
scenegraph/vrml_smjs.c:3760: error: ‘jsval’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3760: error: expected ‘;’ before ‘rval’
scenegraph/vrml_smjs.c:3767: warning: assignment makes pointer from integer without a cast
scenegraph/vrml_smjs.c:3768: warning: assignment makes pointer from integer without a cast
scenegraph/vrml_smjs.c:3779: error: ‘JSObject’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3779: error: ‘evt’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3780: error: expected ‘;’ before ‘argv’
scenegraph/vrml_smjs.c:3783: error: ‘argv’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3786: error: expected ‘;’ before ‘funval’
scenegraph/vrml_smjs.c:3787: error: ‘ret’ undeclared (first use in this function)
scenegraph/vrml_smjs.c:3787: error: expected expression before ‘)’ token
scenegraph/vrml_smjs.c:3789: error: ‘rval’ undeclared (first use in this function)
make[1]: *** [scenegraph/vrml_smjs.opic] Error 1
make[1]: Leaving directory `/home/nixie/gpac/src'
make: *** [lib] Error 2
```

---

### Post by mc4man on 2009-07-22
Sorry your having so much trouble with this. As posted by F.O. it should build quite easily with no extra libraires installed and I found it easy to build with everything installed.

> Attempt to compile...failed,

Remove libmozjs-dev

(I'd had it installed as a dep of something else, didn't cause any problems in building but there is that warning and seems unnecessary anyway.

edit ; run this on your source before re-attempting build
 ```
make distclean 

```
As far as the extra libraries i'm not up on their value, though the website says "GPAC is only fully functionnal when compiled with several third-party libraries (media codecs, ECMAScript, Font engine, ...). Features of GPAC are limited without them."

Are you on a 64 bit install?

If you get a make error about fPIC then add a flag to your configure

```
./configure --extra-cflags="-fPIC -DPIC"
```
or 
```
./configure --extra-cflags="-fPIC "
```

(I need to learn the difference (anybody..?

If you wish to disable some extra libraries either remove the -devs (a poor solution) or configure them out - see
 ./configure --help

In addition if you wish to compare a ./configure ..., make, make install or checkinstall vs building a package set let me know - simple, about 10 - 15 min. start to finish.

---

### Post by PsySc0rpi0n on 2010-05-28
> **qyot27 said:**
> This is the sequence I used when compiling GPAC:

```
wget http://superb-east.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.5.tar.gz
wget http://voxel.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.5.tar.gz
tar -zxf gpac-0.4.5.tar.gz
tar -zxf gpac_extra_libs-0.4.5.tar.gz
cd gpac_extra_libs
cp -r * ../gpac/extra_lib
cd ../gpac
chmod +x configure
./configure --disable-opengl --use-js=no --use-ft=no --use-jpeg=no --use-png=no --use-faad=no --use-mad=no --use-xvid=no --use-ffmpeg=no --use-ogg=no --use-vorbis=no --use-theora=no --use-openjpeg=no
make lib
make apps
sudo make install-lib
sudo make install
sudo cp bin/gcc/libgpac.so /usr/lib
```(yes, those ./configure disables are a bit paranoid, but it works for me - all I needed GPAC for was to enable MP4 output in x264)

If, however, it complains about not having zlib-1.2.3 (and zlib1g-dev from the repositories isn't sufficient - I still haven't tested whether it's fine or not), then do this *before* compiling GPAC:
```
wget http://www.zlib.net/zlib-1.2.3.tar.gz
tar -zxf zlib-1.2.3.tar.gz
cd zlib-1.2.3
./configure
make
sudo make install
```


I got this when performing the

```
make apps
```command

```
psy@****r:~/Desktop/Downloads/gpac$ make apps
...
...
...
...
collect2: ld returned 1 exit status
make[2]: *** [MP4Box] Error 1
make[2]: Leaving directory `/home/psysc0rpi0n/Desktop/Downloads/gpac/applications/mp4box'
make[1]: *** [apps] Error 2
make[1]: Leaving directory `/home/psysc0rpi0n/Desktop/Downloads/gpac/applications'
make: *** [apps] Error 2
psy@*****:~/Desktop/Downloads/gpac$ 
```How do i solve this?

---

### Post by qyot27 on 2010-05-29
I would generally recommend against using what I posted to build the apps, as that was mainly for the libgpac_static.a dependency for x264, and what may have worked on Jaunty (I can't remember) probably no longer does on Karmic or Lucid.  Just skip that step, as any resulting apps would be extremely crippled.

Also, there is very little reason to compile gpac from source now...it's actually in the repositories (sudo apt-get install gpac libgpac-dev).

---

### Post by PsySc0rpi0n on 2010-05-29
> **qyot27 said:**
> I would generally recommend against using what I posted to build the apps, as that was mainly for the libgpac_static.a dependency for x264, and what may have worked on Jaunty (I can't remember) probably no longer does on Karmic or Lucid.  Just skip that step, as any resulting apps would be extremely crippled.

Also, there is very little reason to compile gpac from source now...it's actually in the repositories (sudo apt-get install gpac libgpac-dev).

I'm on Debian and apt-get can't find any gpac... :(

---


---
title: "HOWTO: Install OpenGL/Graphic card Benchmark utility - SVN"
date: 2006-04-09
forum: Tutorials
---

### Post by Perfect Storm on 2006-04-09
**Doesn't work in Ubuntu Breezy 5.10 and below**
**Tested: 6.04 x86, 6.10 x86, 7.04 x86 | 7.10 64-bit, 8.04 64-bit and 8.10 64-bit**


NB: Nvidia 9xxx driver support GL_shadow.

A couple a months ago I found this handy little tool which are build for benchmarking your Graphic card. The name of the tool is GLobs.
Before you start, make sure you have universe enable in your sourcelist. There's plenty of threads and howtos throughout the forum to do so.

---------------------------------------------------------------

[size=4]**Before Installation:**[/size]

Make sure that your sourcelist is properly set up and your 3D driver for your graphic card is working.
Next step is getting you the right compiling tools and depended libs to compile and making Globs working:

**7.04 and previous releases:**
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential subversion scons
sudo apt-get install libsdl-image1.2-dev libsqlite0-dev libsqlite3-0 libsqlite3-dev python-gnome2-dev python-gobject-dev python-gtk2-dev python2.4-opengl x11proto-gl-dev libgtk2.0-dev python2.4-pysqlite2 freeglut3-dev
```

**7.10, 8.04 and 8.10:**
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential subversion scons
sudo apt-get install libsdl-image1.2-dev libsqlite0-dev libsqlite3-0 libsqlite3-dev python-gnome2-dev python-gobject-dev python-gtk2-dev python-opengl x11proto-gl-dev libgtk2.0-dev python2.4-pysqlite2 freeglut3-dev
```



[size=4]**Installation:**[/size]

Now to the compiling and installing;

```
cd ~/Desktop
svn co https://globs.svn.sourceforge.net/svnroot/globs/globs/trunk globs
svn co https://globs.svn.sourceforge.net/svnroot/globs/benchmarks/trunk globs/src/benchmarks
cd globs
scons
sudo scons install prefix=/usr
sudo python patchdir.py prefix=/usr
sudo python setup.py install --prefix=/usr
```


Last step is making an application launcher;

```
sudo rm -f /usr/share/applications/globs.desktop
sudo nano /usr/share/applications/globs.desktop
```


add the following text:

[b][Desktop Entry]
Name=GL O.B.S.
Comment=OpenGL Benchmark Utility
Exec=globs %F
Icon=/usr/share/globs/pixmaps/globs.png
Terminal=false
Type=Application
Categories=Application;System;[/b]


Save and exit.
[ctrl]+[o] | [ctrl]+[x] 

You can now start GLobs in the Application tab ---> System Tools or type globs in the terminal.

---

### Post by pestypest on 2006-04-30
[QUOTE=Artificial Intelligence]A couple a months ago I found this handy little tool which are build for benchmarking your Graphic card. The name of the tool is GLobs.
Before you start, make sure you have universe enable in your sourcelist. There's plenty of threads and howtos throughout the forum to do so.

---------------------------------------------------------------

**1)** Download GLobs to your Desktop. You can download it here: [http://sourceforge.net/project/showfiles.php?group_id=161613](http://sourceforge.net/project/showfiles.php?group_id=161613)

**2)** Next step is getting you the right compiling tools and depended libs to   compile and making Globs working:

```

sudo apt-get install build-essential libsqlite0-dev libsqlite3-0 libsqlite3-dev python-gnome2-dev python-gobject-dev python-gtk2-dev python2.4-opengl scons x11proto-gl-dev libgtk2.0-dev freeglut3-dev

```

**3)** Now to the compiling and installing:

```

cd Desktop
tar zxvf globs-0.1.tar.gz
cd globs-0.1
scons
sudo scons install prefix=/usr
sudo python patchdir.py prefix=/usr
sudo python setup.py install --prefix=/usr

```

**4)** Last step is making an application launcher:

```
sudo rm -f /usr/share/applications/globs.desktop
sudo gedit /usr/share/applications/globs.desktop

```

add:



Save an exit.
You can now start GLobs in the Application tab ---> System Tools
or type **globs** in the terminal.


This howto is also tested on Dapper.[/QUOTE]

[QUOTE=namit]I am gettting this error message
Can anyone help?

Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)[/QUOTE]

got this error

jason@jason:~/Desktop/globs-0.1$ scons
scons: Reading SConscript files ...
sh: sdl-config: command not found
sh: sdl-config: command not found
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... no
Did not find libSDL, exiting!


 and this

scons: Reading SConscript files ...
sh: sdl-config: command not found
sh: sdl-config: command not found
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... no
Did not find libSDL, exiting!

---

### Post by Perfect Storm on 2006-04-30
Try install the devel package of libsdl.

---

### Post by pestypest on 2006-04-30
[QUOTE=Artificial Intelligence]Try install the devel package of libsdl.[/QUOTE]


tried.

jason@jason:~/Desktop/globs-0.1$ scons
scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... no
Did not find libSDL, exiting!

---

### Post by Ramses de Norre on 2006-04-30
python-gobject-dev is not available from breezy repo's.

---

### Post by davygravy on 2006-05-03
Followed all the recommendations/directions here and at the main GL OBS site - still, I got compile errors when I ran scons.

My post/inquiry/plea for help is here [GL OBS on Ubuntu PPC?]("http://ubuntuforums.org/showthread.php?t=169097").  

Anyhelp would be appreciated.  You can pm me.

thanks,

davygravy

---

### Post by davygravy on 2006-05-05
bump...anyone?

---

### Post by Perfect Storm on 2006-05-05
Sorry don't know. It might be PPC related somehow.
But you might take contact with the developer of Globs to straighten out the errors.

---

### Post by fatty_chris on 2006-05-10
When I try to get the globs installed, I get this message:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package python-gobject-dev

I get that after I input this:
 sudo apt-get install build-essential python-gnome2-dev python-gtk2-dev python-gobject-dev libwnck-dev libxres-dev x11proto-resource-dev libgnome-desktop-dev libstartup-notification0-dev automake1.8 python-gobject

How do I get python-gobject-dev installed?

---

### Post by Perfect Storm on 2006-05-10
It might be called something else on breezy, because I've manage to install it on breezy but I've moved to dapper and wrote the howto through there. A mistake of mine.

But you could try and see if the dapper version of the file works or you ran into dependency problems: [http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fp%2Fpygobject%2Fpython-gobject-dev_2.10.1-0ubuntu1_all.deb&md5sum=6bd25f05294a69ae503094cb4a952758&arch=all&type=main](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fp%2Fpygobject%2Fpython-gobject-dev_2.10.1-0ubuntu1_all.deb&md5sum=6bd25f05294a69ae503094cb4a952758&arch=all&type=main)

---

### Post by Omnios on 2006-05-10
Found a dapper deb which may or may not work checking it out now.
[http://packages.ubuntulinux.org/dapper/python/python-gobject-dev]("http://packages.ubuntulinux.org/dapper/python/python-gobject-dev")

edit: already a dependancy problem requires
```
dpkg: dependency problems prevent configuration of python-gobject-dev:
 python-gobject-dev depends on python2.4-gobject (= 2.10.1-0ubuntu1); however:
  Package python2.4-gobject is not installed.
dpkg: error processing python-gobject-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered whil
```

Going to try to get gobobject but have to check my python version first.

Edit 2: K python version is ok and got the gob object deb from 
[http://packages.ubuntulinux.org/dapper/python/python2.4-gobject]("http://packages.ubuntulinux.org/dapper/python/python2.4-gobject")
Got the following dependancy error
```

tom@reboot:~/apt-get$ sudo dpkg -i python2.4-gobject_2.10.1-0ubuntu1_i386.deb
Selecting previously deselected package python2.4-gobject.
dpkg: considering removing python2.4-gtk2 in favour of python2.4-gobject ...
dpkg: no, cannot remove python2.4-gtk2 (--auto-deconfigure will help):
 listen depends on python2.4-gtk2
  python2.4-gtk2 is to be removed.
dpkg: regarding python2.4-gobject_2.10.1-0ubuntu1_i386.deb containing python2.4-gobject:
 python2.4-gobject conflicts with python2.4-gtk2 (<< 2.8.3)
  python2.4-gtk2 (version 2.8.1-0ubuntu2) is installed.
dpkg: error processing python2.4-gobject_2.10.1-0ubuntu1_i386.deb (--install):
 conflicting packages - not installing python2.4-gobject
Errors were encountered while processing:
 python2.4-gobject_2.10.1-0ubuntu1_i386.deb

```

 ANyways tryed the dapper gtk package
[http://packages.ubuntulinux.org/dapper/python/python2.4-gtk2]("http://packages.ubuntulinux.org/dapper/python/python2.4-gtk2")
 and got heavy dependancy hell. Errors as follows
```
tom@reboot:~/apt-get$ sudo dpkg -i python2.4-gtk2_2.8.6-0ubuntu1_i386.deb
(Reading database ... 127259 files and directories currently installed.)
Preparing to replace python2.4-gtk2 2.8.1-0ubuntu2 (using python2.4-gtk2_2.8.6-0ubuntu1_i386.deb) ...
Unpacking replacement python2.4-gtk2 ...
dpkg: dependency problems prevent configuration of python2.4-gtk2:
 python2.4-gtk2 depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.1.
 python2.4-gtk2 depends on libglib2.0-0 (>= 2.10.0); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 python2.4-gtk2 depends on libpango1.0-0 (>= 1.12.1); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 python2.4-gtk2 depends on python2.4-gobject; however:
  Package python2.4-gobject is not installed.
dpkg: error processing python2.4-gtk2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-gtk2

```

 ANyone else want to try this im kind of scared of breaking mys system. Think im going to make a test Multi boot next install lol.

---

### Post by Omnios on 2006-05-10
Fiddling with the above broke my system now im stuck with two broken packages that want to uninstall huge amounts of my python related stuff.

 The broken packages are Python2.4-gtk2 and puthon2.4glade2. Anyways I can not uninstall the broken so im going to have to install the previos version of gtk2  and see if that works. Anyways how do you apt-get a previos version?

  Edit: Got it all fixed up.

---

### Post by Omnios on 2006-05-10
Oh almost forgot, from what I have seen with the dapper python packages this program should work with dapper.

---

### Post by bluevoodoo1 on 2006-05-12
Got it working. Very good guide!

The GL_shadow doesn't seem to work for me. It will popup as if to begin the test, then close, without showing any data. All others work, perhaps my card doesn't handle it?

---

### Post by Perfect Storm on 2006-05-12
Same problem for me in Dapper. Perhaps it's the card driver. Which card do you have? I'm running nvidia dapper default.

---

### Post by bluevoodoo1 on 2006-05-12
[QUOTE=Artificial Intelligence]Same problem for me in Dapper. Perhaps it's the card driver. Which card do you have? I'm running nvidia dapper default.[/QUOTE]

FX 5500 with Dapper driver.


EDIT: One more question. I'm curious, do the save/open features work for you as well?

---

### Post by Perfect Storm on 2006-05-12
Nope. Doesn't work or implemented yet. Though it's a 0.1 release.

I think the GL_shadow issue might be a dapper problem or nvidia problem as when I installed it on Breezy back then, it worked fine.

---

### Post by bluevoodoo1 on 2006-05-12
[QUOTE=Artificial Intelligence]Nope. Doesn't work or implemented yet. Though it's a 0.1 release.

I think the GL_shadow issue might be a dapper problem or nvidia problem as when I installed it on Breezy back then, it worked fine.[/QUOTE]


Ah yes, I forgot that it's a 0.1 release! Either way, it's quite nifty.

---

### Post by Perfect Storm on 2006-06-01
Changed it to only works in Dapper (sorry folks).

---

### Post by Omnios on 2006-06-09
[QUOTE=Artificial Intelligence]Changed it to only works in Dapper (sorry folks).[/QUOTE]


 Works in dapper very well thanks for the how to. :D

---

### Post by deizel on 2006-08-01
same problem as pestypest:
```
deizel@deizel:~/Desktop/globs-0.1$ sudo scons
scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... no
Did not find libSDL, exiting!
```
according to synaptics, the following packages are installed:
```
libsdl1.2debian - Simple DirectMedia Layer
libsdl1.2debian-alsa - Simple DirectMedia Layer (with X11 and ALSA options)
libsdl1.2-dev - Simple DirectMedia Layer development files
libsdl-gfx1.2-4 - drawing and graphical effects extension for SDL
libsdl-gfx1.2-dev - development files for SDL_gfx
libsdl-image1.2 - image loading library for Simple DirectMedia Layer 1.2
libsdl-mixer1.2 - mixer library for Simple DirectMedia Layer 1.2
libsdl-net1.2 - network library for Simple DirectMedia Layer
```
i am running ubuntu 6.06 lts aka dapper drake
```
deizel@deizel:~/Desktop/globs-0.1$ uname -r
2.6.15-26-amd64-xeon
```
any ideas?

---

### Post by sunilsattiraju on 2006-08-29
i had no error compiling the package but ..when i tried to run GLOBS i got the following error ..any help???????

$globs
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in ?
    from Globs import gui
  File "/usr/lib/python2.4/site-packages/Globs/gui.py", line 24, in ?
    import gtk.glade
ImportError: No module named glade

---

### Post by Perfect Storm on 2006-08-29
Follow this guide instead: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63)
I havn't updated this guide for awhile.

---

### Post by NoTiG on 2006-09-01
is this a true benchmark? how come nobody is posting their scores. anyways....

i think im using opensource DRI drivers.  I have 3d acceleration because direct rendering is on according to glxinfo . Im using ATI 9600 mobility (only 64 mb of ram)

GL_points = 23
GL Blit = 687
GL Blit ext = 690
GL smoke = 231.4 

Im going to try the ATI binary drivers next if i can get them to work ><

---

### Post by Perfect Storm on 2006-09-02
> **NoTiG said:**
> is this a true benchmark? how come nobody is posting their scores. anyways....


Because this is a howto section.

---

### Post by wdcrls on 2006-09-23
worked just fine.
ty for the guide

---

### Post by Rob2687 on 2006-09-23
Ran fine except for the first test, GL_shadow.

GL_pointz = 1223.2
GL_blit = 4185.6
Fake = 274090.2
GL_blit_ext = 4177.6
GL_smoke = 655.4

---

### Post by Perfect Storm on 2006-09-23
> **Rob2687 said:**
> Ran fine except for the first test, GL_shadow.

GL_pointz = 1223.2
GL_blit = 4185.6
Fake = 274090.2
GL_blit_ext = 4177.6
GL_smoke = 655.4

It's common problem. On every feedback I've heard and seen experience the same issue.

---

### Post by mips on 2006-10-02
When i follow the gwos guide i get the following error:

The following packages have unmet dependencies.
  libsdl-image1.2-dev: Depends: libsdl1.2-dev (>= 1.2.2-3.3) but it is not going to be installed
E: Broken packages

Also, I assume it would be correct to substitute qt & kde libs for gtk & gnome libs ?

---

### Post by zenrox on 2006-10-02
works 
i think gl shadow ant implemeted
GL_pointz 65.4
GL_blit 89.0
GL_blit_ext 8.2
GL_smoke 40.0
nice for the latest drivers from nvidia
on an fx5500 256mbs card

---

### Post by Perfect Storm on 2006-10-02
Aye, you need the libgtk as the application can't be compiled with QT libs.

> The following packages have unmet dependencies.
libsdl-image1.2-dev: Depends: libsdl1.2-dev (>= 1.2.2-3.3) but it is not going to be installed
E: Broken packages

Often seen when having unofficial sources in the sourcelist.

---

### Post by Omnios on 2006-10-04
Hi I get this error. 

```
tom@miko:~/tarball/globs-0.1$ globs
\
(globs:6485): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/globs", line 31, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
tom@miko:~/tarball/globs-0.1$ \


``` I think my locals was borked when playing around with bleeding edge libs.

 Played around with lang for a bit and it seems that I have
```
LC_ALL = (unset),
```
and have no idea how to set it.

---

### Post by Perfect Storm on 2006-10-18
NEWS!!!


Completly rewritten the howto.
It works in Edgy + beryl + nvidia driver 9xxx

---

### Post by Treviño on 2006-11-23
Debian package...: [http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/globs_0.2+svn20061119-r42-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/globs_0.2+svn20061119-r42-3v1ubuntu0_i386.deb)

Link may change... Look at [this page]("http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/") for updates...

If you need I could post the debian/rules file or the sources (+ diff) I used to make the deb, but it's quite easy...

---

### Post by Perfect Storm on 2007-04-21
Tested in Feisty

---

### Post by slayerboy on 2007-04-23
This is AWESOME!  Thanks man!  Worked like a charm, but the "fake" test seems like the FPS is outta wack.

All of these are @ 1280x960, my monitor's native resolution.  I have a AMD Sempron 2Ghz, 1GB RAM, and 256MB GeForce 6200 graphics card:

> GL_Shadow = 98.2
GL_pointz = 295.4
GL_bit = 272.0
Fake = 3205697.8
GL_bit_ext = 238.4
GL_smoke = 117

---

### Post by codedmin on 2007-05-01
> **Omnios said:**
> Hi I get this error. 

```
tom@miko:~/tarball/globs-0.1$ globs
\
(globs:6485): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/globs", line 31, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
tom@miko:~/tarball/globs-0.1$ \


``` I think my locals was borked when playing around with bleeding edge libs.

 Played around with lang for a bit and it seems that I have
```
LC_ALL = (unset),
```
and have no idea how to set it.

After install the *deb when run globs, get this error

```
globs 
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in <module>
    from Globs import app
ImportError: No module named Globs

```
Can anyone help?

---

### Post by Omnios on 2007-07-09
> **codedmin said:**
> After install the *deb when run globs, get this error

```
globs 
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in <module>
    from Globs import app
ImportError: No module named Globs

```Can anyone help?


 Getting same error here.

---

### Post by sad_iq on 2007-07-10
Ok...my install attempt ended earlyer:
 ```
sadiq@omerta:~/Desktop$ svn co https://svn.sourceforge.net/svnroot/globs/globs/trunk globs
svn: PROPFIND request failed on '/svnroot/globs/globs/trunk'
svn: PROPFIND of '/svnroot/globs/globs/trunk': Could not resolve hostname `svn.sourceforge.net': No address associated with hostname (https://svn.sourceforge.net)
```
What have I done wrong???

---

### Post by azidrane on 2007-08-18
Easiest way:

```

sudo nano /etc/apt/sources.list

```

add this to the bottom of the file

```


deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0


```

ctrl + o
ctrl + x

Then:

```


sudo apt-get update
sudo apt-get install glob2


```

Done!

---

### Post by hriceto on 2007-11-16
Installs fairly easy on Gutsy-server. 

sudo apt-get install python2.4-opengl   - was missing so I went without it.

Needed to add:

> sudo aptitude install python2.4-glade2

> sudo apt-get install gettext

---

### Post by z0mbie on 2007-12-23
globs 0.2-svn is out

New SVN repository locations, so update that when following the tutorial:

```
svn co https://globs.svn.sourceforge.net/svnroot/globs/globs/trunk globs
```
```
svn co https://globs.svn.sourceforge.net/svnroot/globs/benchmarks/trunk globs/src/benchmarks
```


GL Open Benchmark Suite relocation site:
[http://globs.sourceforge.net/index.php](http://globs.sourceforge.net/index.php)


Works on Gutsy, my benchmarks:

[INDENT]**Graphics Card:**   nVidia 8600 GT 256MB

**nVidia Driver:**
[INDENT]Version: 169.07
Operating System: Linux x86
Release Date: December 20, 2007[/INDENT]

**GL_shadow** - [COLOR="Green"]2773.80[/COLOR]  FPS
**GLSL_parallax** - [COLOR="Teal"]2235.20[/COLOR]  FPS
**GL_pointz** - [COLOR="Green"]1541.20[/COLOR]  FPS
**GL_blit** - [COLOR="Teal"]3495.20[/COLOR]  FPS
**GL_blit_ext** - [COLOR="Green"]3500.80[/COLOR]  FPS 
**GL_smoke** - [COLOR="Teal"]1001.20[/COLOR]  FPS[/INDENT]

---

### Post by Perfect Storm on 2007-12-23
Guide updated and tested.

---

### Post by Silvain on 2008-01-13
Hello, Artificial Intelligence.
Have tried to follow this tutorial, Most seems to have gone Ok, but on trying to run the shortcut nothing appears. I saved most of what my cl app gave back , I can post it here, if that is good to help for trouble shooting. Any suggestion on how to trouble shoot this?

TIA
Silv

added: Tried the install part again and got this:
```
scons: done reading SConscript files.
scons: Building targets ...
gcc -o src/benchmarks/GLSL_parallax/glsl_parallax src/benchmarks/GLSL_parallax/main.o src/benchmarks/GLSL_parallax/init.o src/benchmarks/GLSL_parallax/textfile.o src/benchmarks/GLSL_parallax/extra.o src/benchmarks/get_options.o src/benchmarks/check_time.o -L/usr/lib -lSDL -lSDL_image -lGL
src/benchmarks/GLSL_parallax/main.o: In function `main':
main.c:(.text+0x4e4): undefined reference to `glUseProgram'
main.c:(.text+0x4fd): undefined reference to `glUseProgram'
main.c:(.text+0x578): undefined reference to `glDetachShader'
main.c:(.text+0x58d): undefined reference to `glDetachShader'
main.c:(.text+0x59b): undefined reference to `glDeleteShader'
main.c:(.text+0x5a9): undefined reference to `glDeleteShader'
main.c:(.text+0x5b4): undefined reference to `glDeleteProgram'
src/benchmarks/GLSL_parallax/init.o: In function `InitShaders':
init.c:(.text+0x156): undefined reference to `glCreateProgram'
init.c:(.text+0x16a): undefined reference to `glCreateShader'
init.c:(.text+0x1aa): undefined reference to `glShaderSource'
init.c:(.text+0x1c2): undefined reference to `glCompileShader'
init.c:(.text+0x1d9): undefined reference to `glAttachShader'
init.c:(.text+0x1e5): undefined reference to `glCreateShader'
init.c:(.text+0x227): undefined reference to `glShaderSource'
init.c:(.text+0x240): undefined reference to `glCompileShader'
init.c:(.text+0x258): undefined reference to `glAttachShader'
init.c:(.text+0x266): undefined reference to `glLinkProgram'
init.c:(.text+0x29d): undefined reference to `glUseProgram'
init.c:(.text+0x2b3): undefined reference to `glGetUniformLocation'
init.c:(.text+0x2d1): undefined reference to `glGetUniformLocation'
init.c:(.text+0x2ef): undefined reference to `glGetUniformLocation'
init.c:(.text+0x30d): undefined reference to `glUniform1i'
init.c:(.text+0x323): undefined reference to `glUniform1i'
init.c:(.text+0x339): undefined reference to `glUniform1i'
src/benchmarks/GLSL_parallax/extra.o: In function `printObjectInfoLog':
extra.c:(.text+0x507): undefined reference to `glIsShader'
extra.c:(.text+0x526): undefined reference to `glGetShaderiv'
extra.c:(.text+0x542): undefined reference to `glGetProgramiv'
extra.c:(.text+0x567): undefined reference to `glIsShader'
extra.c:(.text+0x58c): undefined reference to `glGetShaderInfoLog'
extra.c:(.text+0x5c1): undefined reference to `glGetProgramInfoLog'
collect2: ld returned 1 exit status
scons: *** [src/benchmarks/GLSL_parallax/glsl_parallax] Error 1
scons: building terminated because of errors.

```

---

### Post by Perfect Storm on 2008-01-13
Just wait a bit, SVN is development version so time to time there's a bug or two.

---

### Post by Perfect Storm on 2008-04-10
Now tested on 8.04 64-bit Ubuntu.

---

### Post by nick09 on 2008-04-30
The program won't load for some reason.

I have 64 bit ubuntu too.

---

### Post by BLTicklemonster on 2008-05-10
> **Treviño said:**
> Debian package...: [http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/globs_0.2+svn20061119-r42-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/globs_0.2+svn20061119-r42-3v1ubuntu0_i386.deb)

Link may change... Look at [this page]("http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/") for updates...

If you need I could post the debian/rules file or the sources (+ diff) I used to make the deb, but it's quite easy...

Got an error when I tried to run it installed the first way, then found this deb, installed it, and got this:

bill@bill-desktop:~$ globs
Benchmarks table exists already
Traceback (most recent call last):
  File "/usr/bin/globs", line 36, in <module>
    app = app.Application(share_dir, bench_dir)
  File "/usr/lib/python2.5/site-packages/Globs/app.py", line 47, in __init__
    self.main_win = main_win.Main_Window(self)
  File "/usr/lib/python2.5/site-packages/Globs/main_win.py", line 95, in __init__
    self.info_textview.set_wrap_mode(gtk.WRAP_WORD)
AttributeError: 'NoneType' object has no attribute 'set_wrap_mode'
bill@bill-desktop:~$ 


:(

Gutsy

---

### Post by Perfect Storm on 2008-10-07
Tested with Ubuntu 8.10 64-bit

---

### Post by Qchan on 2009-01-07
[b][color=darkred]
I click on Execute and nothing happens. The program installs without error. I even tried running in terminal and no errors.

I have Ubuntu Intrepid Ibex at 32bits. 
I'm using an nVidia GeForce 7950GT
[/b][/color]

---

### Post by Perfect Storm on 2009-01-07
execute **globs %F** in the terminal and see what will happen. You might made a mistake somewhere.

---

### Post by Qchan on 2009-01-07
> **Artificial Intelligence said:**
> execute **globs %F** in the terminal and see what will happen. You might made a mistake somewhere.

[b][color=darkred]
This is what I get...
[/b][/color]
> 
Benchmarks table exists already
User table exists already
/usr/lib/python2.5/site-packages/Globs/main_win.py:45: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.xml = gtk.glade.XML(self.glade_file, root="main_win")


---

### Post by Wartender on 2009-04-06
Well, i might be a bit late here, but i wanna try this. i get the error:
```
scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... yes
Checking for IMG_GetError() in C library libSDL_image... no
Did not find libSDL_image, exiting!

```
i am running ubuntu 8.10 32-bit, does anyone know how to solve?

---

### Post by Qchan on 2009-04-06
> **Wartender said:**
> Well, i might be a bit late here, but i wanna try this. i get the error:
```
scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... yes
Checking for IMG_GetError() in C library libSDL_image... no
Did not find libSDL_image, exiting!

```
i am running ubuntu 8.10 32-bit, does anyone know how to solve?

[b][color=darkred]
This program no longer works. You're better off using something else. The developer for this program has abandoned this a long time ago.
[/b][/color]

---

### Post by Wartender on 2009-04-06
oh ok... then can you suggest some other program for benchmarking my system? -.- 
BESIDES glxgears XD

---

### Post by Qchan on 2009-04-06
> **Wartender said:**
> oh ok... then can you suggest some other program for benchmarking my system? -.- 
BESIDES glxgears XD


[http://lbs.sourceforge.net/](http://lbs.sourceforge.net/)

---

### Post by EvilMoose on 2009-05-11
> **Wartender said:**
> Well, i might be a bit late here, but i wanna try this. i get the error:
```
scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... yes
Checking for IMG_GetError() in C library libSDL_image... no
Did not find libSDL_image, exiting!

```
i am running ubuntu 8.10 32-bit, does anyone know how to solve?

sudo apt-get install libsdl-image1.2-dev

---

### Post by Wartender on 2009-05-16
oh yeah thanks i had already found that out XD, but it still doesn't have any plugins so i kinda gave up on globs, i found the phoronix benchmarking suite and i'm trying to use that, however my laptop is currently not working so...

---

### Post by jukzh on 2009-06-06
Hello All!
Help me, what does it means?
```
$ globs %F
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in <module>
    from Globs import app
ImportError: No module named Globs

```

Regards,
JK

---

### Post by Alucard-sama on 2009-06-11
Doesn't start up for me, if I change the Terminal bool to "true" it quickly pops up and disappears, so the launcher works, just the program doesn't want to launch for some reason.

---

### Post by _sluimers_ on 2009-08-05
> **jukzh said:**
> Hello All!
Help me, what does it means?
```
$ globs %F
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in <module>
    from Globs import app
ImportError: No module named Globs

```

Regards,
JK

bump

---

### Post by AbraKdabra on 2009-08-30
I've got the same error:

> mauro@mauroubuntu:~$ globs %F
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in <module>
    from Globs import app
ImportError: No module named Globs

---

### Post by inokungfu on 2009-09-25
```
$ globs %F
Traceback (most recent call last):
  File "/usr/bin/globs", line 28, in <module>
    from Globs import app
ImportError: No module named Globs
```To fix this error all you need to do is add the location of the Globs module to Python's search path. The easiest way of doing that is to set PYTHONHOME env. variable to the path where Globs installation put the module. For example, on my machine the installer said something like:

```
creating /usr/lib/python2.6/site-packages/Globs
copying build/lib.linux-i686-2.6/Globs/local_db.py -> /usr/lib/python2.6/site-packages/Globs
...

```So, to get Globs to work run:

```
$ export PYTHONPATH=/usr/lib/python2.6/site-packages
```After that everything worked great. You could also add the path in /usr/bin/globs by adding this:

```
import sys
sys.path.append('/usr/lib/python2.6/site-packages')
```Replace "/usr/lib/python2.6/site-packages" with the path where Globs is (use 'locate' if necessary)

---

### Post by K1773R on 2011-09-05
Thanks alot inokungfu :) :popcorn:

---


---
title: "Howto compile mono 2.8"
date: 2010-10-09
forum: Tutorials
---

### Post by WitchCraft on 2010-10-09
mono [s]2.8[/s] 2.10.6 stable is out.
Unfortunately, Ubuntu 10.04 still uses 2.4, while Maverick Meerkat will have 2.6.7.

So you'll have to compile it yourselfs.
This tutorial explains how to do this.
Sudo is omitted, you should add it if you don't work as root.

Step 1: Get the build dependencies
```

apt-get update
user@system$> apt-get install build-essential autoconf automake \
bison flex gtk-sharp2-gapi boo gdb valac libfontconfig1-dev \
libcairo2-dev libpango1.0-dev libfreetype6-dev libexif-dev \
libjpeg62-dev libtiff4-dev libgif-dev zlib1g-dev libatk1.0-dev \
libglib2.0-dev libgtk2.0-dev libglade2-dev libart-2.0-dev \
libgnomevfs2-dev libgnome-desktop-dev libgnome2-dev libgnomecanvas2-dev \
libgnomeui-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev \
libpanel-applet2-dev libnautilus-burn-dev librsvg2-dev \
libgtkhtml3.14-dev libgtksourceview2.0-dev libgtksourceview-dev \
libvte-dev libwnck-dev libnspr4-dev libnss3-dev libxul-dev \
libwebkit-dev libvala-dev

```



Step 2: Download the source and setup the environment
Download the stable tarballs from:
[s][http://ftp.novell.com/pub/mono/sources-stable/](http://ftp.novell.com/pub/mono/sources-stable/)[/s]
[http://download.mono-project.com/sources/](http://download.mono-project.com/sources/)

Then, create a bash script in /usr/local/bin, called mono-2.8
with this content
```

#!/bin/bash
MONO_PREFIX=/opt/mono-2.8
GNOME_PREFIX=/opt/gnome-2.8
export DYLD_LIBRARY_PATH=$MONO_PREFIX/lib:$DYLD_LIBRARY_PATH
export LD_LIBRARY_PATH=$MONO_PREFIX/lib:$LD_LIBRARY_PATH
export C_INCLUDE_PATH=$MONO_PREFIX/include:$GNOME_PREFIX/include
export ACLOCAL_PATH=$MONO_PREFIX/share/aclocal
export PKG_CONFIG_PATH=$MONO_PREFIX/lib/pkgconfig:$GNOME_PREFIX/lib/pkgconfig
PATH=$MONO_PREFIX/bin:$PATH

exec "$@"

```

And give it execute permissions
```

chmod +x /usr/local/bin/mono-2.8

```


Then open a console and go to the directory where you extracted the mono source tarballs.


Step 3:
execute this script
```


#!/bin/bash
MONO_PREFIX=/opt/mono-2.8
GNOME_PREFIX=/opt/gnome-2.8
export DYLD_LIBRARY_FALLBACK_PATH=$MONO_PREFIX/lib:$DYLD_LIBRARY_FALLBACK_PATH
export LD_LIBRARY_PATH=$MONO_PREFIX/lib:$LD_LIBRARY_PATH
export C_INCLUDE_PATH=$MONO_PREFIX/include:$GNOME_PREFIX/include
export ACLOCAL_PATH=$MONO_PREFIX/share/aclocal
export PKG_CONFIG_PATH=$MONO_PREFIX/lib/pkgconfig:$GNOME_PREFIX/lib/pkgconfig
export PATH=$MONO_PREFIX/bin:$PATH
PS1="[mono 2.8] \w @ "

```

Now create the directory where you'll install mono 2.8 to:
```

mkdir -p /opt/mono-2.8

```


Step 4: libgdiplus
```

user@system$> cd libgdiplus-2.8
user@system$> ./configure --prefix=/opt/mono-2.8 --with-pango
user@system$> make
user@system$> sudo make install

```


Step 5: mono-2.8
```

user@system$> cd ../mono-2.8
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```
Verify that the mono compilers have been installed:
```

user@system$> which gmcs

```


Step 6: gtk+ and gnome
```

user@system$> cd ../gtk-sharp-2.12.10
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../gnome-sharp-2.24.1
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../gnome-desktop-sharp-2.24.0
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```


Step 7: gluezilla, gecko-sharp, webkit-sharp

Now compile the libraries for embedding the gecko and webkit html rendering engines.

```

user@system$> cd ../gluezilla-2.6
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../gecko-sharp-2.0-0.13
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../webkit-sharp-0.3
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make

```

Step 8: build Mono.Addins
```

user@system$> cd ../mono-addins-0.5
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```


Step 9: build Mono tools
```

user@system$> cd ../mono-tools-2.8
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```



Step 10: Build Mono XSP, the webserver for ASP.NET
```

user@system$> cd ../xsp-2.8
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```



Step 11: build the Mono Debugger
```

user@system$> cd ../mono-debugger-2.8
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```



Step 12: build MonoDevelop 2.0
```

user@system$> cd ../monodevelop-2.4
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../monodevelop-debugger-mdb-2.4
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../monodevelop-debugger-gdb-2.4
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../monodevelop-database-2.4
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../monodevelop-java-2.4
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install
user@system$> cd ../monodevelop-vala-2.4
user@system$> ./configure --prefix=/opt/mono-2.8
user@system$> make
user@system$> sudo make install

```

---

### Post by kids_pro on 2010-11-10
Note: On Meerkat

build gluezilla-2.6 required xulrunner-dev package install

build mono-tools --> error
./PrintManager.cs(28,31): error CS0234: The type or namespace name `PrintJob' does not exist in the namespace `Gnome'. Are you missing an assembly reference?
./PrintManager.cs(29,25): error CS0246: The type or namespace name `PrintDialog' could not be found. Are you missing a using directive or an assembly reference?
./PrintManager.cs(31,29): error CS0234: The type or namespace name `HTML' does not exist in the namespace `Gtk'. Are you missing an assembly reference?
./PrintManager.cs(34,31): error CS0234: The type or namespace name `PrintContext' does not exist in the namespace `Gnome'. Are you missing an assembly reference?
------------------------ look like we need to install libgtkhtml3.14-cil-dev to get pass this problem.

---

### Post by Mrbronz on 2010-11-29
So How do I [B]compile mono 2.8

Is .... 

[/B]apt-get update
user@system$> apt-get install build-essential autoconf automake \
bison flex gtk-sharp2-gapi boo gdb valac libfontconfig1-dev \
libcairo2-dev libpango1.0-dev libfreetype6-dev libexif-dev \
libjpeg62-dev libtiff4-dev libgif-dev zlib1g-dev libatk1.0-dev \
libglib2.0-dev libgtk2.0-dev libglade2-dev libart-2.0-dev \
libgnomevfs2-dev libgnome-desktop-dev libgnome2-dev libgnomecanvas2-dev \
libgnomeui-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev \
libpanel-applet2-dev libnautilus-burn-dev librsvg2-dev \
libgtkhtml3.14-dev libgtksourceview2.0-dev libgtksourceview-dev \
libvte-dev libwnck-dev libnspr4-dev libnss3-dev libxul-dev \
libwebkit-dev libvala-dev


A script?

where do I put Sudo?

Do I run each line individually? 

Very fustrated!!!

---

### Post by WitchCraft on 2010-11-30
> **Mrbronz said:**
> So How do I [B]compile mono 2.8

Is .... 

[/B]apt-get update
user@system$> apt-get install build-essential autoconf automake \
bison flex gtk-sharp2-gapi boo gdb valac libfontconfig1-dev \
libcairo2-dev libpango1.0-dev libfreetype6-dev libexif-dev \
libjpeg62-dev libtiff4-dev libgif-dev zlib1g-dev libatk1.0-dev \
libglib2.0-dev libgtk2.0-dev libglade2-dev libart-2.0-dev \
libgnomevfs2-dev libgnome-desktop-dev libgnome2-dev libgnomecanvas2-dev \
libgnomeui-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev \
libpanel-applet2-dev libnautilus-burn-dev librsvg2-dev \
libgtkhtml3.14-dev libgtksourceview2.0-dev libgtksourceview-dev \
libvte-dev libwnck-dev libnspr4-dev libnss3-dev libxul-dev \
libwebkit-dev libvala-dev


A script?

where do I put Sudo?

Do I run each line individually? 

Very fustrated!!!

apt-get is the package manager for Debian/Ubuntu-based Linux systems. It is used to install programs from the repository (via internet). It's something like windows installer, just an awsome lot more powerful.

sudo is an abbrevation for switch user & do / super-user do.
Which in this context means run the installation as administrator.

You put sudo right before apt-get:
```

sudo apt-get install <packagename>

```

for example:
```

sudo apt-get install lsb-release

```

If you run your system as root (=with administrator account), you can omit all the sudo stuff. But the latter is a dangerous practise, especially for a novice, because you can really screw up your system, if you don't know what you're doing.


If your system doesn't recognize apt-get, then most likely you don't have a Debian/Ubuntu system. For example, Red Hat/Fedora uses yum, while OpenSuse uses Zypper, Arch Linux uses pacman, and Gentoo (the fastest of all Penguins) uses emerge.

In that case, the Pacman Rosetta-Stone might be useful:
[https://wiki.archlinux.org/index.php/Pacman_Rosetta](https://wiki.archlinux.org/index.php/Pacman_Rosetta)

You can check what version of Linux you have by doing:
```

lsb_release -a

```


Which on Ubuntu should answer
> 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


or
> 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid




You can either install one program/library/sdk after another like this:
```

sudo apt-get install package1
sudo apt-get install package2
sudo apt-get install package3
sudo apt-get install package4
....
sudo apt-get install packageN

```


or you can just put the packages one after another, and install them all in one
```

sudo apt-get install package1 package2 package3 package4 ... packageN

```

---

### Post by irondog on 2010-12-09
I got a build error with 'gnome-sharp-2.24.1' 
This occur because Mono.GetOptions.dll is not shipped anymore.

According to this article, an error occur in building sample.
So you should remove it from Makefile..

[http://go-mono.com/forums/#nabble-td2969455]("http://go-mono.com/forums/#nabble-td2969455")
 

Thank you for your nice article.

---

### Post by WitchCraft on 2010-12-11
> **irondog said:**
> I got a build error with 'gnome-sharp-2.24.1' 
This occur because Mono.GetOptions.dll is not shipped anymore.

According to this article, an error occur in building sample.
So you should remove it from Makefile..

[http://go-mono.com/forums/#nabble-td2969455]("http://go-mono.com/forums/#nabble-td2969455")
 

Thank you for your nice article.

I know, I'm the one who wrote that message to the mailinglist (published on Nabble) in the first place.
in gnome-sharp-<version>/sample/gnomevfs/Makefile
Line 449 + 450 of the generated makefile in that folder
Comment out these two lines (by adding # in front)
#TestXfer.exe: $(srcdir)/TestXfer.cs $(assemblies)
#    $(CSC) /out:TestXfer.exe $(references) -r:Mono.GetOptions.dll $(srcdir)/TestXfer.cs
AND
#EXTRA_TARGETS = TestXfer.exe
on line 221.

**[COLOR="Red"](Note: as of now, this still applies to mono 2.10.2, too.)[/COLOR]**

I thought, since I told them - and since it's the stable sources, they would have fixed it by now, but obviously... 
Well, I guess, in the meantime, I wouldn't call 2.8 "stable" anyway, but they probably wait for the first mayor fix for it until they publish 2.8.1 ...

---

### Post by WitchCraft on 2011-03-06
If on compiling Gluezilla-2.6 you get:
> 
checking Mozilla XPCOM > 1.8... not found
checking Mozilla XPCOM 1.8... You need to install the Mozilla XPCOM development package.


You need to do:
```

apt-get install xulrunner-dev

```

As kids_pro already said.

---

### Post by WitchCraft on 2011-03-06
For mono 2.10.1, you'll have difficulties, because MonoDevelop doesn't find gtksharpglue-2
> 
---> System.DllNotFoundException: gtksharpglue-2


If you do 
```

updatedb
locate gtksharpglue-2

```

> 
/usr/lib/cli/gtk-sharp-2.0/libgtksharpglue-2.so

you'll see that it is installed, but that its path is not in the library include directories, so you need to add it.

Create a new file called glib.conf in /etc/ld.so.conf.d/
```

gedit /etc/ld.so.conf.d/glib.conf

```

And fill it with the following content:
```

# Mono needs you
/usr/lib/cli/glib-sharp-2.0

```

Afterwards, you have to update the ld library paths:
```

/sbin/ldconfig

```

---

### Post by WitchCraft on 2011-03-24
To get the latest MonoDevelop, do the following:

Go to:
[http://monodevelop.com/Download](http://monodevelop.com/Download)

Switch to beta, and download the source tarball.
[http://ftp.novell.com/pub/mono/sources/monodevelop/monodevelop-2.5.90.tar.bz2](http://ftp.novell.com/pub/mono/sources/monodevelop/monodevelop-2.5.90.tar.bz2)


Now you still need the latest version of mono-addins (configure will complain when < 0.6)
[http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.6.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.6.tar.bz2)


Then configure and make and make install mono-addins, then the same for MonoDevelop & Co.


[IMG]http://i.imgur.com/x00zhl.jpg[/IMG]

---

### Post by kuh3h3 on 2011-04-24
> **WitchCraft said:**
> If on compiling Gluezilla-2.6 you get:


You need to do:
```

apt-get install xulrunner-dev

```

As kids_pro already said.

your tip is wrong. because monodevelop-database configure scripy looking for xulrunner 1.8 but ubuntu natty now xulrunner 2.0.
so build failed. have to fix configure script

---

### Post by WitchCraft on 2011-04-30
> **kuh3h3 said:**
> your tip is wrong. because monodevelop-database configure scripy looking for xulrunner 1.8 but ubuntu natty now xulrunner 2.0.
so build failed. have to fix configure script

The tip may be wrong now, but it wasn't. 
It worked perfectly fine on Maverick Meerkat. 

It's just that I didn't have time to upgrade to Natty.
But you're of course right, if it wants 1.8 and you got 2.0, you have to fix the configure script. 

Maybe that means that now some bugs that I recently run into with xulrunner + mono are gone.

---

### Post by WitchCraft on 2011-06-03
Update: I just switched to natty.

You needn't fix the configure file for gluezilla.

Just install:
```

apt-get install xulrunner-1.9.2-dev

```


and for mono-tools, you need:
```

apt-get install libgtkhtml3.14-cil-dev 

```

---

### Post by WitchCraft on 2011-06-03
Note:

In order for monodevelop-database to be able to support MySQL, you need to have MySql.Data installed.

```

apt-get install libmysql6.1-cil

```

---

### Post by WitchCraft on 2011-10-25
Find the latest mono source tarballs at:
[http://download.mono-project.com/sources/mono/](http://download.mono-project.com/sources/mono/)


[img]http://i.stack.imgur.com/UHvbZ.png[/img]

---

### Post by WitchCraft on 2012-01-30
To install libgluezilla on 11.10, you first need to download xulrunner 1.9.2:

[https://launchpad.net/ubuntu/oneiric/amd64/xulrunner-1.9.2/1.9.2.17+build3+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/oneiric/amd64/xulrunner-1.9.2/1.9.2.17+build3+nobinonly-0ubuntu1)

Then you can install libgluezilla from here [https://launchpad.net/ubuntu/oneiric/amd64/libgluezilla/2.6-2ubuntu2](https://launchpad.net/ubuntu/oneiric/amd64/libgluezilla/2.6-2ubuntu2)

---

### Post by WitchCraft on 2012-11-18
Tip for mono 3.0:

If you get:
**error: #error "Only <glib.h> can be included directly."**

when compiling GTK-Sharp, you have to alter gtk-sharp-2.12.11/glib/glue/thread.c to:
```

// #include <glib/gthread.h>
#include <glib.h>

```In mono-debugger-2.10/sysdeps/server/breakpoints.c
comment out gthread.h
```

#include <server.h>
#include <breakpoints.h>
//#include <glib/gthread.h>
#include <sys/stat.h>
#include <signal.h>

```These are the dependencies on 12.04:
```

apt-get install build-essential autoconf automake \
bison flex gtk-sharp2-gapi boo gdb valac libfontconfig1-dev \
libcairo2-dev libpango1.0-dev libfreetype6-dev libexif-dev \


apt-get install libtiff4-dev libgif-dev zlib1g-dev libatk1.0-dev libjpeg8-dev libjpeg-turbo8-dev


apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libart-2.0-dev

apt-get install libgnomevfs2-dev libgnome-desktop-dev libgnome2-dev libgnomecanvas2-dev

apt-get install libgnomeui-dev libgnomeprint2.2-dev libgnomeprintui2.2-dev

apt-get install libpanel-applet-4-dev \
libnautilus-extension-dev (replaces libnautilus-burn-dev ???)

apt-get install librsvg2-dev
apt-get install libgtkhtml3.14-dev libgtksourceview2.0-dev libgtksourceview2.0-dev \
apt-get install libvte-dev libwnck-dev libnspr4-dev libnss3-dev 
apt-get install libwebkit-dev libvala-0.18-dev

```Anybody knows what happened to:
[B]libxul-dev  ???



[/B]And the new parallel scripts:[B]
```


#!/bin/bash
MONO_PREFIX=/opt/mono-3.0
GNOME_PREFIX=/opt/gnome-3.0
export DYLD_LIBRARY_PATH=$MONO_PREFIX/lib:$DYLD_LIBRARY_PATH
export LD_LIBRARY_PATH=$MONO_PREFIX/lib:$LD_LIBRARY_PATH
export C_INCLUDE_PATH=$MONO_PREFIX/include:$GNOME_PREFIX/include
export ACLOCAL_PATH=$MONO_PREFIX/share/aclocal
export PKG_CONFIG_PATH=$MONO_PREFIX/lib/pkgconfig:$GNOME_PREFIX/lib/pkgconfig
PATH=$MONO_PREFIX/bin:$PATH











#!/bin/bash
MONO_PREFIX=/opt/mono-3.0
GNOME_PREFIX=/opt/gnome-3.0
export DYLD_LIBRARY_FALLBACK_PATH=$MONO_PREFIX/lib:$DYLD_LIBRARY_FALLBACK_PATH
export LD_LIBRARY_PATH=$MONO_PREFIX/lib:$LD_LIBRARY_PATH
export C_INCLUDE_PATH=$MONO_PREFIX/include:$GNOME_PREFIX/include
export ACLOCAL_PATH=$MONO_PREFIX/share/aclocal
export PKG_CONFIG_PATH=$MONO_PREFIX/lib/pkgconfig:$GNOME_PREFIX/lib/pkgconfig
export PATH=$MONO_PREFIX/bin:$PATH
PS1="[mono 3.0] \w @ "




mkdir -p /opt/mono-3.0

```For Monodevelop:

[/B]Go into directory 
monodevelop-3.0.4.7/tests# 
if you lack the directories
```

UnitTestsUserInterfaceTests
MacPlatform.Tests      
MonoDevelop.MacDev.Tests  

```then download the latest version of the monodevelop sources


If it doesn't run afterwards, it's because /usr/local/lib is not in the ld library paths.
Make sure /etc/ld.so.conf.d contains a file like mono3.conf with the following contents
```

# mono default configuration
/usr/local/lib

```


I figured it should already have this in the library path, because there is a file libc.conf that contains that path.
But obviously, the paths aren't updated, so run
```

sudo ldconfig

```

and there you go.

---

### Post by WitchCraft on 2013-01-13
Here the full dependencies for mono 3.0 in one copy-paste install 

```

apt-get install build-essential autoconf automake \
bison flex gtk-sharp2-gapi boo gdb valac libfontconfig1-dev \
libcairo2-dev libpango1.0-dev libfreetype6-dev libexif-dev \
libtiff4-dev libgif-dev zlib1g-dev libatk1.0-dev libjpeg8-dev \
libjpeg-turbo8-dev libglib2.0-dev libgtk2.0-dev libglade2-dev \
libart-2.0-dev libgnomevfs2-dev libgnome-desktop-dev \
libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomeprint2.2-dev \
libgnomeprintui2.2-dev libpanel-applet-4-dev \
libnautilus-extension-dev librsvg2-dev libgtkhtml3.14-dev \
libgtksourceview2.0-dev libgtksourceview2.0-dev libvte-dev \
libwnck-dev libnspr4-dev libnss3-dev libwebkit-dev libvala-0.18-dev

```

---

### Post by WitchCraft on 2013-01-19
Note:

On mono 3, the install scripts for xsp-2.10.2 is broken. 

You get a HTTP 502 always when executing a website via fastcgi-mono-server4.

With this error message in the logfiles.
```
 [error] 3384#0: *101 upstream sent unexpected FastCGI record: 3 while reading response header from upstream, client: 127.0.0.1, server: localhost, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "localhost:8000" 
```
You need to execute this script (if you don't parallel install, use PREFIX=/usr).
All it does is copy the 3 assemblies from the 4 gac to the 4.5 gac, and adjust the startup scripts in PREFIX/bin to use PREFIX/lib/mono/4.5

```

#!/bin/bash

# Your mono directory
PREFIX=/opt/mono-3.0.3


FILES=('mod-mono-server4'
       'fastcgi-mono-server4'
       'xsp4')

cd $PREFIX/lib/mono/4.0

for file in "${FILES[@]}"
do
   cp "$file.exe" ../4.5
done


cd $PREFIX/bin

for file in "${FILES[@]}"
do
  sed -ie 's|mono/4.0|mono/4.5|g' $file
done

```Additionally, for debugging, it is helpful to start fastcgi-mono-server-4 with debugging enabled.
Use the switches 
```

/loglevels=Debug /printlog=true

```For example:
```

sudo /opt/mono-3.0.3/bin/fastcgi-mono-server4 /loglevels=Debug /printlog=True /applications=/:/var/www/mono/Mvc3Template /socket=tcp:127.0.0.1:9000

```

---


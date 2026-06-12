---
title: "Request? gmpc 0.13"
date: 2006-06-18
forum: Ubuntu Backports
---

### Post by JMO707 on 2006-06-18
I dont know, because of the sub-forum warning, if its right to do a request at this time, but here it goes.

Any chance to hace gmpc 0.13 with us?, it has two new features that are pretty nice: cover art fetching and plugin support.

[cms.qballcow.nl]("cms.qballcow.nl") is the place.

Thanks.

---

### Post by mlind on 2006-06-20
You should probably request this on launchpad.net. I can help you to rebuild this package yourself if you want.

---

### Post by JMO707 on 2006-06-20
Mmm, that would be interesting, if there is no problem =)

---

### Post by mlind on 2006-06-20
No it's not a problem. It wasn't so straightforward task as I expected, but I'll fill you in
later how to build your own out of this. If you could test these two binaries first that
I built, to see if they work for you.

to extract package
```

tar zxvf gmpc_0.13+libmpd0.tar.gz

```

to install
```

sudo dpkg -i gmpc_0.13.0-0ubuntu1_i386.deb libmpd0_0.12.0-0ubuntu1_i386.deb

```

tell me if you encounter any problems.

---

### Post by JMO707 on 2006-06-20
WOW

I dont know how you do it, but thanks, I was looking for a way to get this version for a while.

When you have some time, It would be great to learn what was the process.

---

### Post by mlind on 2006-06-21
Sure thing, I'll try my best to write instructions for you tomorrow.

---

### Post by mlind on 2006-06-21
This will be very brief and probably contains some errors, so you should try it out
yourself and report any problems you experience.

First, we must build new libmpd because current version that's on Dapper
repositories is too old. gmpc build requirement seems to be atleast libmpd-0.12.
This error occurs if you're trying to build gpmc with old library.

I suggest you install **debfoster** before you start. It's useful for tracking
unwanted dependencies, like packages you only need for building. 

```

sudo aptitude install debfoster
sudo debfoster

```

Answer **y** to all questions, so it will know the current state of installed
packages. Next time you run it, only installed build dependencies will be listed and
those can be safely removed too.



[SIZE="4"]Initial setup[/SIZE]
[LIST]
[*]Install tools required for building process
```

sudo aptitude install build-essential cdbs devscripts dh-make fakeroot

```
[/LIST]


[SIZE="4"]libmpd[/SIZE]

Let's install libmpd first,

[LIST]
[*]Add this to /etc/apt/sources.list
```

deb-src http://ftp.fi.debian.org/debian sid main contrib non-free

```

[*]Create necessary build environment 
```

mkdir -p ~/packages/libmpd
cd ~/packages/libmpd

```

[*]Fetch source from debian unstable. Don't use sudo while getting the source.
```

sudo apt-get update && apt-get source **libmpd**

```

[*]Source is automatically extracted, go into that folder
```

cd libmpd-0.12.0

```
[*]Add new changelog entry
```

dch **-i**

```

Insert changelog information
```

libmpd (0.12.0-**2ubuntu1**) unstable; urgency=low

  * Builded against Dapper

 -- Firstname Lastname <yourname@yourhost.com>  Wed, 21 Jun 2006 22:07:21 +0300

```

(Bolded part will be appended to builded .deb package name)

[*]Build libmpd
```

dpkg-buildpackage -rfakeroot -us -uc

```

[*]Install libmpd0 and libmpd-dev packages
```

sudo dpkg -i ../libmpd0_0.12.0-2ubuntu1_i386.deb
sudo dpkg -i ../libmpd-dev_0.12.0-2ubuntu1_i386.deb

```
[/LIST]



[SIZE="4"]gmpc[/SIZE]

This is basically a repeat of libmpd install procedures, but instead we'll do it by
upgrading from current Dapper package. So first, [U]remove the Debian unstable
source repository you added previously for libmpd[/U] from /etc/apt/sources.list.

[LIST]
[*]Create necessary build environment 
```

mkdir -p ~/packages/gmpc
cd ~/packages/gmpc

```

[*]Fetch source from Dapper repositores. Don't use sudo while getting the source.
```

sudo apt-get update && apt-get source

```

(This procedure should have created directory called gmpc-0.12.0 and extraced
source there automatically.)


[*]Download new sources from upstream
```

wget http://download.qballcow.nl/programs/gmpc-0.13/gmpc-0.13.0.tar.gz

```

[*]Apply debian build information from old source
```

cd gmpc-0.12.0
uupdate ../**gmpc-0.13.0.tar.gz**

```

(Now old build infomation have been applied to new source)


[*]Prepare for building gmpc
```

cd ../gmpc-0.13.0
dch

```

Insert changelog information
```

gmpc (0.13.0-**0ubuntu1**) unstable; urgency=low

  * New upstream release

 -- Firstname Lastname <yourname@yourhost.com> Wed, 21 Jun 2006 22:26:25 +0300

```


[*]Check requirements and install them all
```

dpkg-checkbuilddeps

```

Install all packages that were listed by previous command. This should do it
```

sudo aptitude install libgtk2.0-dev libglade2-dev libglib2.0-dev libgnomevfs2-dev zlib1g-dev intltool

```

[*]Build gmpc
```

dpkg-buildpackage -rfakeroot -us -uc

```

[*]Install gmpc
```

sudo dpkg -i ../gmpc_0.13.0-0ubuntu1_i386.deb

```
[/LIST]


[SIZE="4"]Clean unnecessary packages[/SIZE]
Now you can clear all installed packages that building required by running
```

sudo debfoster

```
and answering **p** (as purge) for all questions.

---

### Post by Schroeder on 2006-06-21
Wow! Works like a charm! :D 

Thanks!

One question though: does this work with sources for other programs, too? I.e., can I create packages from every kind of source code?

Chris

Two things I noted: 'dh -i' obviously doesnt work before devscripts are installed. 'uupdate' is missing the name of the archive. Other than that its just follow your instructions step by step.

---

### Post by JMO707 on 2006-06-22
Whe Im trying to download the source to build libmpd it says me that I need a key:

[I]Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  El subproceso gzip devolvió un código de error (1)
Leyendo lista de paquetes... Hecho
W: GPG error: [http://ftp.fi.debian.org](http://ftp.fi.debian.org) sid Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 010908312D230C5F
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/I]

---

### Post by mlind on 2006-06-22
[QUOTE=Schroeder]Wow! Works like a charm! :D 

Thanks!

One question though: does this work with sources for other programs, too? I.e., can I create packages from every kind of source code?

Chris

Two things I noted: 'dh -i' obviously doesnt work before devscripts are installed. 'uupdate' is missing the name of the archive. Other than that its just follow your instructions step by step.[/QUOTE]

In general, yes, these steps work for already debianized packages. You can use
dh_make to package which has not yet been debianized. It's much more complex
task, so always check out first if debian upsteam offers already maintained package.
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

dch is just a wrapper for editing debian/changelog, you can do it manually too.
You are right about devscripts, I'll move build package installs at the beginning

uupdate is supposed to point the new downloaded source, I'll fix that too, thanks.

---

### Post by mlind on 2006-06-22
[QUOTE=JMO707]Whe Im trying to download the source to build libmpd it says me that I need a key:

[I]Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  El subproceso gzip devolvió un código de error (1)
Leyendo lista de paquetes... Hecho
W: GPG error: [http://ftp.fi.debian.org](http://ftp.fi.debian.org) sid Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 010908312D230C5F
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/I][/QUOTE]


Is that error actually from Ubuntu server, and only warning about Debian sid server?
Warnings are not fatal and apt-get source should work afterwards.

If not, try with either apt-get update --allow-unauthenticated
or
```

gpg &#8211;keyserver keyring.debian.org &#8211;recv-keys 010908312D230C5F
gpg &#8211;armor &#8211;export 010908312D230C5F | apt-key add -
apt-get update

```

---

### Post by JMO707 on 2006-06-22
Im trying to build it from the subversion repository. What changes should I do to your steps to make it work?

---

### Post by mlind on 2006-06-23
[QUOTE=JMO707]Im trying to build it from the subversion repository. What changes should I do to your steps to make it work?[/QUOTE]

I guess you have to create .tar.gz or tar.bz2 package out of module you've checked
out for uupdate to work

---

### Post by qball on 2006-06-23
If you build from svn, make sure you grab the latest Libmpd aswel.
2 other remarks:
1. Gmpc will work alot nicer in combination with mpd from svn. (but also works with 0.11.5)
2. SVN is UNSTABLE.  It hasn't crashed for me, but YMMV.

If you don't want to install libsm,  you can pass --disable-sm.
For help and or bug reports go into #mpd on irc.freenode.org.
[http://musicpd.org/mantis/](http://musicpd.org/mantis/) is the bugtracker of mpd/gmpc/libmpd.

Q

---

### Post by JMO707 on 2006-06-23
Well, the package as mlind has stated in his process went fine =)
I tried to build the newest one from the SVN, but got some errors with libmpd that I dont remember right now...
Being some tired, I looked for a way to install the deb's of the SVN version, because before of that I tried and the version of libc6 wasnt correct...
So, I find a version some weeks older than the last one and it worked like charm. I got the combo of libmpd0 (0.13.0~svn+r3931-1), mpd (0.11.5-7) & gmpc (0.14.0~svn+r3985-1). In fact, the only reason why I got those last versions was the covert art support, but that is the only thing that I cant get =P

I need to fill this dependencies when I want to configure the plugin:

[I]checking for gmpccaa... configure: error: Package requirements

        glib-2.0 >= 2.4
        gobject-2.0 >= 2.4
        gtk+-2.0 >= 2.4
        gmodule-2.0
        libxml-2.0
        gthread-2.0
        libmpd >= 0.12.0
        gmpc    >= 0.13.0


[/I]

Bleh, I guess I will get some help in the IRC channel, and well, if that doesnt work, gmpc is great too ^^

Thanks.

---

### Post by mlind on 2006-06-23
[QUOTE=JMO707]
I need to fill this dependencies when I want to configure the plugin:

[I]checking for gmpccaa... configure: error: Package requirements

        glib-2.0 >= 2.4
        gobject-2.0 >= 2.4
        gtk+-2.0 >= 2.4
        gmodule-2.0
        libxml-2.0
        gthread-2.0
        libmpd >= 0.12.0
        gmpc    >= 0.13.0


[/I]
[/QUOTE]

When you're building something from source, you're 'almost' always after 
packages that have **-dev** ending at their name. It's probably easiest
to use apt-get/aptitude/synaptic for searching these packages.

for example, glib-2.0, you need a package that probably has glib and -dev on it's
name.

```

apt-cache search dev | grep glib

```

looking through search results you'll find a matching candidate: libglib2.0-dev.
You can use apt-cache show libglib2.0-dev or apt-cache policy libglib2.0-dev
to get some extra info about it.

About next one I'm not sure, but it must be a -dev package alright
```

apt-cache search gobject | grep dev

```

it's probably libbtctl2-dev (bluetooth library)

Just continue like this, install one library at time and try building again. This way
you also find out if you installed wrong library.

---

### Post by qball on 2006-06-24
[QUOTE=mlind]
About next one I'm not sure, but it must be a -dev package alright
```

apt-cache search gobject | grep dev

```

it's probably libbtctl2-dev (bluetooth library)

Just continue like this, install one library at time and try building again. This way
you also find out if you installed wrong library.[/QUOTE]

gobject has nothing todo with bluetooth.. and it should be part of the glib package.   (apt-file search gobject-2.0.pc to be sure)

make sure gmpc.pc is in the PKG_CONFIG_PATH. 

btw. I _really_ advice mpd from svn, f.e. cover art won't work in all the places without it.

and make sure you install the dev package for libcurl

---

### Post by JMO707 on 2006-06-24
Mmm..., I got a really extrange problem.

I was needing libatk1.0-dev for libgtk2.0-dev, and I get the Debian stable branch.
Now apt-get says me that the half of my system is broken..., but when I installed the packages it didnt say anyting.
Look:

[I][23:37:54](/media/cdrom0)$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Corrigiendo dependencias... Listo
Los siguientes paquetes se ELIMINARÁN:
  alacarte amule at-spi automatix bluez-pin bonfire brltty-x11 bug-buddy bum
  checkgmail compiz-gnome contact-lookup-applet dbus-1-utils deskbar-applet
  devilspie ekiga eog evince evolution-webcal file-roller gaim
  gaim-extendedprefs gaim-themes gcalctool gcompmgr gconf-editor gcursor gdebi
  gdm gedit gimp-python gksu gmpc gnome-about gnome-accessibility-themes
  gnome-applets gnome-art gnome-btdownload gnome-control-center
  gnome-cups-manager gnome-games gnome-humility-icon-theme gnome-icon-theme
  gnome-icon-theme-gartoon gnome-icon-theme-suede gnome-keyring gnome-mag
  gnome-media gnome-netstatus-applet gnome-nettool gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-spell gnome-splashscreen-manager gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-themes gnome-themes-extras
  gnome-utils gnome-volume-manager gnopernicus gok gset-compiz
  gstreamer0.10-plugins-good gthumb gtk2-engines-cleanice
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-geramik
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-magicchicken gtk2-engines-metal
  gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-qtpixmap
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-spherecrystal
  gtk2-engines-thingeramik gtk2-engines-thinice gtk2-engines-ubuntulooks
  gtk2-engines-wonderland gtk2-engines-xfce gtkhtml3.8 gucharmap
  hal-device-manager hwdb-client language-selector libatk1-ruby libatspi1.0-0
  libbonoboui2-0 libedataserverui1.2-6 libeel2-2 libexchange-storage1.2-0
  libexchange-storage1.2-1 libexo-0.3-0 libgail-common libgail-gnome-module
  libgail17 libgdk-pixbuf2-ruby libgdl-1-0 libgdl-1-common libgimp2.0
  libgksuui1.0-1 libglade2-0 libglade2-ruby libglade2.0-cil libgnome-desktop-2
  libgnome-keyring0 libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil
  libgnomecanvas2-0 libgnomecupsui1.0-1c2a libgnomeprintui2.2-0 libgnomeui-0
  libgpod0 libgtk2-gladexml-perl libgtk2-perl libgtk2-ruby
  libgtk2-trayicon-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtkmm-2.4-1c2a
  libgtksourceview1.0-0 libgtkspell0 libgucharmap4 libgutenprintui2-1
  liblaunchpad-integration0 liblpint-bonobo0 libmetacity0 libnautilus-burn3
  libnautilus-extension1 libnotify1 libpanel-applet2-0 libpoppler0c2-glib
  libpoppler1-glib librsvg2-2 librsvg2-common libsexy2 libtotem-plparser0
  libtotem-plparser1 libvte4 libwnck18 libwxgtk2.6-0 libxfcegui4-4 metacity
  mplayer mplayer-386 mplayer-fonts nautilus nautilus-cd-burner
  nautilus-sendto notification-daemon nvidia-glx python-glade2 python-gnome2
  python-gnome2-desktop python-gnome2-extras python-gst python-gst0.10
  python-gtk2 python-launchpad-integration python-vte python2.4-glade2
  python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras
  python2.4-gtk2 scim scim-gtk2-immodule screensaver-default-images
  sound-juicer ssh-askpass-gnome synaptic tangerine-icon-theme
  tango-icon-theme-common totem totem-xine tsclient ubuntu-artwork
  update-manager update-notifier vino xsane xscreensaver xscreensaver-data
  xscreensaver-gl zenity
0 actualizados, 0 se instalarán, 200 para eliminar y 13 no actualizados.
Necesito descargar 0B de archivos.
Se liberarán 389MB después de desempaquetar.
¿Desea continuar [S/n]? n[/I]

=(

I have no luck.

Edit2: ...

---

### Post by JMO707 on 2006-06-26
Solved. Oh, well, partially...
I will give the final report when I get everything working.

---

### Post by mikeym on 2006-06-30
[QUOTE=JMO707]Solved. Oh, well, partially...
I will give the final report when I get everything working.[/QUOTE]

As somone who is not confortable installing development packages and compiling code I'm not sure I want ot go down a path that has problems like the one you mention here. Does anyone have any advice for how I could get the plugins working on my computer? I have installed the deb packages at the begining of this post for gmpc_0.13 and mpd_0.11.5. I don't suppose it is an option for somone to post the builds of the plugins?

The begining of this post is a good how-to but it is really still unresolved for anyone reading it.

---

### Post by mikeym on 2006-06-30
Just to note I did try and compile the package myself but I didn't even get past the first hurdle - having a C compiler.


```
$./configure --prefix=/usr/include/gmpc
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

---

### Post by mlind on 2006-06-30
[QUOTE=mikeym]Just to note I did try and compile the package myself but I didn't even get past the first hurdle - having a C compiler.
[/QUOTE]

You need *build-essential* package installed which provides gcc compiler for you.
Did you try out instructions [posted earlier]("http://www.ubuntuforums.org/showpost.php?p=1166298&postcount=7") or do you need a cvs build?

I could try to write instuctions for you to build a .deb package on a clean-room
environment, so you don't need to install any build dependencies on your actual system.

---

### Post by JMO707 on 2006-06-30
If you want an easy path, you could use the next, that, at least for libc6 2.3.6-0ubuntu20, is the last of the last =p

[libmpd0_0.13.0~svn+r4027-1]("http://musicpd.org/~normalperson/debian/experimental/libmpd/libmpd0_0.13.0~svn+r4027-1_i386.deb")

[mpd_0.12.0~svn+r4016-1]("http://musicpd.org/~normalperson/debian/experimental/mpd/mpd_0.12.0~svn+r4016-1_i386.deb")

[gmpc_0.14.0~svn+r3985-1]("http://musicpd.org/~normalperson/debian/experimental/gmpc/gmpc_0.14.0~svn+r3985-1_i386.deb")

I dont know if there were extra dependencies, but try with that.

---

### Post by mikeym on 2006-07-02
I was just trying to get mpd, gmpd and cover art plugins to work without having to build anything. This was possible for mpd and gmpc but no one has posted a build of the plugins: I was suggesting you should do this.

But anyway, I have followed your post on how to build your own mpd and gmpc and been successfull but I still can only get one plugin to compile and I can't even work out where to but it to get it to run.

These are the problems I had when I was following your instructions (incase anyone is interested):

**Problems with Keys**

I couldn't get the debain package source to work without getting a key. I also had problems following the instructions for getting this.

You had obviously put in two '-' in a row and this had been converted to one character. Also I had to do one step as 'su' - here's what I did:

```

gpg --keyserver keyring.debian.org --recv-keys 010908312D230C5F
gpg --armor --export 010908312D230C5F > key.txt
sudo apt-key add key.txt

```


**Problems installing libmpd**

> **mlind]
[*]Fetch source from debian unstable. Don't use sudo while getting the source.
```

sudo apt-get update && apt-get source

``` [/quote] 
This doesn't work on my machine I found by guessing the following worked:

```

sudo apt-get update
apt-get source libmpd

``` 
[quote=mlind]
Insert changelog information

```

libmpd (0.12.0-**2ubuntu1**) unstable said:**
>  
Don't insert this information as a new entry just edit the top one which it has created for you. The bits to change are the **"2ubuntu1"** and **"* Builded against Dapper"**.


**Problems installing gmpc**

[quote=mlind]
sudo apt-get update && apt-get source
 
- still doesn't work on my machine do the same as I did before but swap libmpd with gmpc.

[quote=mlind]
Insert changelog information
[/quote] 
- do the same as I did before again.


**Problems compiling plugins**

Then before I cleared away all the dependencies I downloaded the **Amazon Cover Art Provider 0.1.0** and the **Music Directory Cover Art Provider 0.1.0** I then extracted them and from the extracted directory I ran:

```
./configure --prefix=/usr/include/gmpc/
make
make install

``` 
for **Music Directory Cover Art Provider 0.1.0** this made 
This made "/usr/include/gmpc/share/gmpc/plugins/gmpcmdcover.so".

The **Amazon Cover Art Provider 0.1.0** encounters an error when I run make.

I tried to use the SVN for this but I don't know how to use SVN so I gave up. (I got as far as installing subversion and trying to install from the link they gave but I don't know how.

P.S I have just coppied the /usr/include/gmpc/share/gmpc/plugins/gmpcmdcover.so file to /usr/share/gmpc/plugins/gmpcmdcover.so and restarted gmpc and this is now working. I still however want the Amazon album art plugin.

---

### Post by mikeym on 2006-07-02
O.k.

To get the SVN files

```

cd ~/packages
mkdir amazon-cover-art-svn
cd amazon-cover-art-svn
sudo apt-get install subversion
svn co https://svn.qballcow.nl/gmpc-coveramazon/trunk/
cd trunk
./autogen.sh

```

But it requires automake 1.6 and ubuntu only apears to be on 1.4

Stuck again...

---

### Post by mlind on 2006-07-02
[QUOTE=mikeym]
But anyway, I have followed your post on how to build your own mpd and gmpc and been successfull but I still can only get one plugin to compile and I can't even work out where to but it to get it to run.
[/QUOTE]

what plugin is this? I'll aid you building it.


[QUOTE=mikeym]
**Problems with Keys**

I couldn't get the debain package source to work without getting a key. I also had problems following the instructions for getting this.
[/QUOTE]

I didn't have to install any debian keys to get the source downloads working. There
are warnings when updating the package list, but those aren't fatal. I didn't
actually test that keyserver thingy, but good you got it working.


[QUOTE=mikeym]
**Problems installing libmpd**
 
This doesn't work on my machine I found by guessing the following worked:

```

sudo apt-get update
apt-get source libmpd

``` 
[/QUOTE]

oops, maybe the most essential part had a typo in it, my fault :mrgreen:
Well spotted!
 

[QUOTE=mikeym]
**Problems compiling plugins**
...
[/QUOTE]

I would install plugins the debian way and build .deb packages, so those are easier
to control and remove.


I know this is going to mix up things even more, but building packages on a
sandboxed environment is preferred, so you don't need to alter your actual
system for satisfying build-time dependencies. Check it out, it has sample for
gmplayer too. [http://www.ubuntuforums.org/showthread.php?t=206382](http://www.ubuntuforums.org/showthread.php?t=206382)

---

### Post by mikeym on 2006-07-02
[QUOTE=mlind]what plugin is this? I'll aid you building it.[/QUOTE]

The album art plugins for gmpc that one of the other posters mentioned and I am trying to get to work with gmpc as they have to be compiled seperately and they are not included in the sources you posted. 


[QUOTE=mlind]
I would install plugins the debian way and build .deb packages, so those are easier
to control and remove.
[/QUOTE]

I don't think it is entirely nessicary in this case as it is only building one file.

And I'm still stuck...

Has anyone else actualy made both the plugins for gmpc 0.13 and got them working? 

Is it possible to post a packaged version of them?

---

### Post by mlind on 2006-07-02
I think the code is broken on svn, I couldn't get it to compile
```

plugin.c:40: error: syntax error before 'cam_cover'
plugin.c:41: warning: initialization makes integer from pointer without a cast
plugin.c:43: warning: excess elements in scalar initializer
plugin.c:43: warning: (near initialization for 'cam_cover')
plugin.c:43: warning: data definition has no type or storage class
plugin.c:49: error: 'GMPC_PLUGIN_META_DATA' undeclared here (not in a function)
.
.

```

and so forth. Here are the packages build-depends that I got resolved
```

autoconf, automake1.7, libtool, libglib2.0-dev (>= 2.4), libgtk2.0-dev (>= 2.4), libxml2-dev, libmpd-dev (>= 0.12.0), gmpc-dev (>= 0.13.0), libcurl3-openssl-dev

```

Install them and try building.

---

### Post by mikeym on 2006-07-04
[QUOTE=mlind]I think the code is broken on svn, I couldn't get it to compile
```

plugin.c:40: error: syntax error before 'cam_cover'
plugin.c:41: warning: initialization makes integer from pointer without a cast
plugin.c:43: warning: excess elements in scalar initializer
plugin.c:43: warning: (near initialization for 'cam_cover')
plugin.c:43: warning: data definition has no type or storage class
plugin.c:49: error: 'GMPC_PLUGIN_META_DATA' undeclared here (not in a function)
.
.

```

and so forth. Here are the packages build-depends that I got resolved
```

autoconf, automake1.7, libtool, libglib2.0-dev (>= 2.4), libgtk2.0-dev (>= 2.4), libxml2-dev, libmpd-dev (>= 0.12.0), gmpc-dev (>= 0.13.0), libcurl3-openssl-dev

```

Install them and try building.[/QUOTE]

I'm sorry I don't know where to begin.

I have downloaded and installed pbuilder as I would like to package the plugins if I can and post them here if possible and I have built the gmpc_0.13.0-0ubuntu1_i386.deb package and libmpd0_0.12.0-2ubuntu2_i386.deb (+dev) package. But I don't realy see how it can be used to build a package for the plugins? 

What is this .dsc file? How does the version information work. Can you only follow this process with files downloaded as source from a debain repository?

Where would I install automake1.7 for example? Would I log on to pbuilder and apt-get it there then run it from inside... doesn't seem right to me.

Could you point me in the right direction?

---

### Post by mlind on 2006-07-04
[QUOTE=mikeym]I'm sorry I don't know where to begin.

I have downloaded and installed pbuilder as I would like to package the plugins if I can and post them here if possible and I have built the gmpc_0.13.0-0ubuntu1_i386.deb package and libmpd0_0.12.0-2ubuntu2_i386.deb (+dev) package. But I don't realy see how it can be used to build a package for the plugins? 
[/QUOTE]

pbuilder is intended to build debian packages on a chroot environment, so that
plugin should be a .deb package too. Then just add libmpd-dev and gmpc-dev
as Build-Depends, libmpd and gmpc as Depens (runtime).



If you want to use pbuilder for testing and building on a safe environment, you can
do like this:

[LIST]
[*]Let's assume that you've built *libmpd* and *gmpc* earlier and their packages are on pbuilder's BUILDRESULT folder (*/var/cache/pbuilder/result* by default)

[*]Plugin you want to build is on ~/packages/fooplugin/fooplugin-0.1
```

sudo pbuilder login --bindmounts ~/packages/fooplugin/fooplugin-0.1

```

[*]Now on chroot environment, install gmpc and libmpd. BUILDRESULT folder is bindmounted, so it's visible here too
```

cd /var/cache/pbuilder/result	#or cd $BUILDRESULT if variable was exported
apt-get install *.deb		#install all libmpd and gmpc .deb files

```

[*]You should see bindmounted fooplugin-0.1 folder on filesystem root
```

cd /fooplugin-0.1

```
[/LIST]

Try to compile the plugin manually first. Install addional editor like nano and all
build depends this plugin requires, even svn client if you want. Just place your stuff
on $BUILDRESULT before you exit the session, so those will be persisted.

To make things easier if you plan to do this often is to make a hook that would
setup this environment for you, or use different pbuilder environment for just
testing by creating one and using --basetgz argument when you login.


[QUOTE=mikeym]
What is this .dsc file? How does the version information work. Can you only follow this process with files downloaded as source from a debain repository?
[/QUOTE]

.dsc is a source package control file. Process is meant for debianized packages,
but you can create debian package out of any application/script you want.

You should read 
[http://www.debian.org/doc/debian-policy/ch-controlfields.html](http://www.debian.org/doc/debian-policy/ch-controlfields.html)
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)



[QUOTE=mikeym]
Where would I install automake1.7 for example? Would I log on to pbuilder and apt-get it there then run it from inside... doesn't seem right to me.
[/QUOTE]

If you plan to build it inside chroot enviroment like in previous example, then
yes, install it there.


This might sound over-complicated, but it's actually not. If this doesn't work for
you then don't use it. I find this method quite nice and use it often.


I hope this helps.

---

### Post by qball on 2006-07-19
GMPC svn needs plugins from svn. (The plugin api has changed, and there is a new metadata system).

Plugins can also be "installed" by placing the .so file inside ~/.gmpc/plugins/
I will try if I can make a "make userspaceinstall" or something for the plugins, so this can be done automagically.

---

### Post by qball on 2006-07-21
[https://launchpad.net/products/dapper-backports/+bug/53614](https://launchpad.net/products/dapper-backports/+bug/53614)

---

### Post by kimara on 2006-08-19
I tried to install new gmpc-svn but errors came.
```
checking for autoconf...
checking for automake 1.6 or later... automake
checking for aclocal 1.6 or later... aclocal
checking for libtool... libtoolize
Generating configuration files for gmpc, please wait....
  aclocal
aclocal:configure.ac:107: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
  autoheader
  libtoolize --automake
  automake --add-missing
  autoconf
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
./configure: line 2183: syntax error near unexpected token `gmpc,0.21'
./configure: line 2183: `AC_PROG_INTLTOOL(gmpc,0.21)'

```

What I do?

---

### Post by mlind on 2006-08-19
> **kimara said:**
> I tried to install new gmpc-svn but errors came.
```
checking for autoconf...
checking for automake 1.6 or later... automake
checking for aclocal 1.6 or later... aclocal
checking for libtool... libtoolize
Generating configuration files for gmpc, please wait....
  aclocal
aclocal:configure.ac:107: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
  autoheader
  libtoolize --automake
  automake --add-missing
  autoconf
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
./configure: line 2183: syntax error near unexpected token `gmpc,0.21'
./configure: line 2183: `AC_PROG_INTLTOOL(gmpc,0.21)'

```

What I do?

You're probably missing glib development headers.
Try installing libglib2.0-dev or libglib1.2-dev.

---

### Post by kimara on 2006-08-19
Does'nt work.

---

### Post by mlind on 2006-08-19
> **kimara said:**
> Does'nt work.

You need to install a package that provides /usr/share/aclocal/glib-gettext.m4 which defines AM_GLIB_GNU_GETTEXT macro.
You can use **apt-file** to search this package.

---

### Post by kimara on 2006-08-19
I meant this problem.

```
/configure: line 2183: syntax error near unexpected token `gmpc,0.21'
./configure: line 2183: `AC_PROG_INTLTOOL(gmpc,0.21)'
```

---

### Post by kimara on 2006-08-19
apt-file does'nt work here. i tried apt-cache but didnt find file.

What about this.

```
/configure: line 2183: syntax error near unexpected token `gmpc,0.21'
./configure: line 2183: `AC_PROG_INTLTOOL(gmpc,0.21)'
```

Thanks

---

### Post by mlind on 2006-08-19
> **kimara said:**
> apt-file does'nt work here. i tried apt-cache but didnt find file.

What about this.

```
/configure: line 2183: syntax error near unexpected token `gmpc,0.21'
./configure: line 2183: `AC_PROG_INTLTOOL(gmpc,0.21)'
```

Thanks

apt-file works, but it's cache needs to be updated like with apt-get
```

sudo apt-file **update**
apt-file search *file*

```

Did you run autogen.sh script again? What's on line 2183 in ./configure file?

---

### Post by kimara on 2006-08-19
```
AC_PROG_INTLTOOL(gmpc,0.21)
```


I did'nt had apt-file but I installed it.

---

### Post by mlind on 2006-08-19
> **kimara said:**
> ```
AC_PROG_INTLTOOL(gmpc,0.21)
```

sudo apt-file update said that "command not found"

Yeah, that package is not installed by default.. But I won't solve your problem here. Try running autogen.sh script again.

---

### Post by kimara on 2006-08-19
I have intltool installed and also gettext.

This has to wait to tomorrow, my brother wanna be at computer.

---

### Post by kimara on 2006-08-20
It don't work and I don't how to make it work and I think I have all files that I need.

Can you get it and make make .deb package.

Thank you.

---

### Post by mlind on 2006-08-20
> **kimara said:**
> It don't work and I don't how to make it work and I think I have all files that I need.

Can you get it and make make .deb package.

Thank you.

Sure, try if this works.

---

### Post by kimara on 2006-08-21
Thanks, it works :)

---

### Post by kanpachi on 2006-11-20
here's the package i built for edgy
try it out :)

---

### Post by finferflu on 2007-03-08
Any idea on how to get the plugins installed? I get a lot of dependencies errors when I try to compile them from source...

---


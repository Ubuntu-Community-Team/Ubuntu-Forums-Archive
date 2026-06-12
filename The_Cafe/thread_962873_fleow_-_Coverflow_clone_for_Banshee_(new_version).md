---
title: "fleow - Coverflow clone for Banshee (new version)"
date: 2008-10-29
forum: The Cafe
---

### Post by jochenh on 2008-10-29
Hi@all!

I want to present you the new fleow plugin for Banshee.

Fleow short description:
```
A Banshee plugin letting you to view, manage & select albums from the library
in the 3D mode.
```

I've done some bug fixing and added new features:
ChangeLog:
* bug fixing
* edit default cover path
* add scroll function
* add play on left-click at current cover
* delete buttons
* default high set to 200

Please download and test it, write a post if theres any problems with installing or something.

Site(with download): [fleow - Coverflow clone for Banshee]("http://jochen.h1326436.stratoserver.net/fleow/fleow.htm")

Screenshot:
[[IMG]http://img88.imageshack.us/img88/3748/fleowbansheepluginpr7.th.jpg[/IMG]](http://img88.imageshack.us/my.php?image=fleowbansheepluginpr7.jpg)


God bless you!

Jochen

---

### Post by jochenh on 2008-10-31
I added a special Tutorial for Ubuntu, so its now very easy to install the plugin.

[fleow - Coverflow clone for Banshee]("http://jochen.h1326436.stratoserver.net/fleow/fleow.htm")

Please test it and write a post!Even if you don't test it, please let me know if it looks good!

Thank you!

---

### Post by yavez on 2008-10-31
At the third stage -- wget [http://colliertech.com/downloads/gtkglarea-sharp/gtkglarea-sharp-current.tbz](http://colliertech.com/downloads/gtkglarea-sharp/gtkglarea-sharp-current.tbz) -- error returned 2 while untarring.  Downloads the file but won't untar.

---

### Post by jochenh on 2008-10-31
Okay, thanks I fixed it in the Tutorial.

Please test and post if there are any problems or post if you like it or if you don't like it!

Thanks!

---

### Post by UbuWu on 2008-10-31
Nice, but it could use some anti-aliasing for the graphics!

---

### Post by dpm_edinburgh on 2008-10-31
I can't seem to get it installed with the latest version of Banshee.  Running autogen in the final stage complains that I don't have a version of banshee later than 0.12.2 (in fact, I have 1.2.1).  What is the problem, here?

---

### Post by jochenh on 2008-11-01
Not working with 1.2.1 right now, sorry.I'll try to fix this.Use 0.13 from universe, if you want to try the plugin.

@UbuWu Yes,you're right,there should be some AA.

Thanks for testing!

---

### Post by cacharreo on 2008-11-01
Ok, in this point I get the next error

[I]jaime@Eliux:~/opt/taoframework-2.1.0/source$ sudo chmod 755 bootstrap;./bootstrap
+ test no = yes
+ aclocal-1.7 -I m4 -I .auto -I .
+ autoconf
+ test no = yes
+ automake-1.7 --foreign --add-missing --copy
configure.ac: installing `.auto/install-sh'
configure.ac: installing `.auto/mkinstalldirs'
configure.ac: installing `.auto/missing'
[B]configure.ac:3: option `tar-ustar' not recognized
[/B]
[/I]

---

### Post by barbedsaber on 2008-11-01
```
checking for Tao.Sdl assembly version... 1.2 (1.2.13.0)
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO_DEPENDENCY... no
checking for csc.exe... no
configure: error: You need to install either mono or .Net
make: *** No targets specified and no makefile found.  Stop.
sudo: unable to resolve host Neo
make: *** No rule to make target `install'.  Stop.
harry@Neo:~/opt/taoframework-2.1.0/source$ 

```
well, I obviously have mono, because I can run banshee fine. hmm.

---

### Post by jochenh on 2008-11-01
@barbedsaber please install it like its done in the [Ubuntu Tutorial]("http://jochen.h1326436.stratoserver.net/fleow/fleow-ubuntu.htm").You'll need to install this:
```
sudo apt-get install banshee mono-1.0-devel mono-2.0-devel libmono-winforms1.0-cil libmono-winforms2.0-cil mono-mcs mono-gmcs libgtk2.0-0 libgtk2.0-dev gtk-sharp2-gapi libgtkgl2.0-1 libdevil1c2
```

@cacharreo Please install newest automake (evt. autoconf).The problem is solved [here]("http://ubuntuforums.org/showthread.php?t=251350&page=7#66").

---

### Post by billgoldberg on 2008-11-01
Nice, but it doesn't really fit into banshee.

---

### Post by jochenh on 2008-11-01
@billgoldberg Because of Style, background color ?

---

### Post by billgoldberg on 2008-11-01
> **jochenh said:**
> @billgoldberg Because of Style, background color ?

Yes, the black background seems out of place.

---

### Post by jochenh on 2008-11-01
Okay,I'll think of a better background color.Maybe some kind of grey.

Thanks!

---

### Post by cacharreo on 2008-11-02
I have install automake 1.9 and I fixed the error. But now I got another compiling error running [I]./configure --prefix=/usr;make;sudo make install
[/I]:

...................

	  [I]monodocer --assembly:$x/$x.dll --path:doc/$x; \
        done
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
/bin/bash: line 1: monodocer: orden no encontrada
make[2]: *** [Tao.zip] Error 127
make[2]: se sale del directorio `/home/jaime/opt/taoframework-2.1.0/source/src'
make[1]: *** [install-recursive] Error 1
make[1]: se sale del directorio `/home/jaime/opt/taoframework-2.1.0/source/src'
make: *** [install-recursive] Error 1[/I]

Thanks

---

### Post by jochenh on 2008-11-02
Sorry, I forgot a package in Tutorial:

Please run:
```
sudo apt-get install monodoc
```

I fixed that in Tutorial now.

---

### Post by barbedsaber on 2008-11-02
> **jochenh said:**
> @barbedsaber please install it like its done in the [Ubuntu Tutorial]("http://jochen.h1326436.stratoserver.net/fleow/fleow-ubuntu.htm").You'll need to install this:
```
sudo apt-get install banshee mono-1.0-devel mono-2.0-devel libmono-winforms1.0-cil libmono-winforms2.0-cil mono-mcs mono-gmcs libgtk2.0-0 libgtk2.0-dev gtk-sharp2-gapi libgtkgl2.0-1 libdevil1c2
```

I ran those commands as the tuturial said (the first time I did it) it said it didn't need to install any more packages, and I still have the problem I was having before.
Is there a way that I can get it to ignore the error, and compile anyway?
(because I have all the packages I need.)

---

### Post by jochenh on 2008-11-03
There are 3 things you may do to fix this:

1.Do this steps again in taoframework-source.
```
sudo chmod 755 bootstrap;./bootstrap
./configure --prefix=/usr;make;sudo make install
```

2.Try the same step with an other prefix:
```
./configure;make;sudo make install or
./configure --prefix=/;make;sudo make install
```

3.I have these mono packages installed,please check if there some you don't have and evt. install them:
```
libmono-0 libmono1.0-cil libmono2.0-cil libmono-accessibility1.0-cil libmono-accessibility2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-dev mono-common
```

---

### Post by directhex on 2008-11-03
Warning: never ever use --prefix=/usr (or, god forbid, --prefix=/), you will get no support or sympathy from any packagers or developers

---

### Post by jochenh on 2008-11-03
Why don't do this?

In this package you have to set the prefix to /usr otherwise you'll get it installed in /usr/local and it doesn't find the mono libs.

---

### Post by twright on 2008-12-07
> **jochenh said:**
> Why don't do this?

In this package you have to set the prefix to /usr otherwise you'll get it installed in /usr/local and it doesn't find the mono libs.
As Ubuntu uses package management all manually compiled software should be placed in either /usr/local or even better (IMO) /opt to prevent conflicts or massive breakages

---

### Post by LuisAugusto on 2008-12-16
I got the following error:

> Unhandled Exception: System.IO.FileNotFoundException: The directory `doc/Tao.OpenAl' does not exist
  at Monodoc.EcmaProvider..ctor (System.String base_directory) [0x00000] 
  at Monodoc.Assembler.Main (System.String[] args) [0x00000] 
make[2]: *** [Tao.zip] Error 1
make[2]: Leaving directory `/home/augusto/opt/taoframework-2.1.0/source/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/augusto/opt/taoframework-2.1.0/source/src'
make: *** [install-recursive] Error 1

The funny thing is that the Tao.OpenAl folder exists XD

---

### Post by jochenh on 2008-12-18
@twright If I place it in /usr/local the other software dont find the mono libs.How should I edit it that I can put it in /usr/local?

@LuisAugusto Have you installed monodoc etc. like its done in the Ubuntu Tutorial?

I added a post on [www.taoframework.com]("http://www.taoframework.com/node/751") but no one is answering...If you know something about aa in taoframework please let me know...

---

### Post by CholericKoala on 2008-12-18
You know CJ Mahaney?

---

### Post by jochenh on 2008-12-19
No,sry dont know him.

---

### Post by brainkilla on 2008-12-29
> **LuisAugusto said:**
> I got the following error:



The funny thing is that the Tao.OpenAl folder exists XD

Same here... Couldn't somebody just post the compiled plugin, if not the appropriate package itself? Thanx...

---

### Post by DeadSuperHero on 2008-12-29
Does this work in the new Banshee?

---

### Post by jochenh on 2009-01-01
@brainkilla/LuisAugusto Try:
> ./configure --prefix=/usr --disable-doc;make;sudo make install
instead of
> ./configure --prefix=/usr;make;sudo make install

@Mr. Psychopath No sry, doesn't work with the new Version of Banshee until now.

---

### Post by jochenh on 2009-06-16
Deleted it from the server. Use Songbird's Mediaflow plugin instead...

If you want to have the file then e-mail me: [email]jochen.hoermann@web.de[/email]

Greets,

Jochen

---


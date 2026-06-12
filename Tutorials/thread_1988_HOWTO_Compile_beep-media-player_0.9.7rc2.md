---
title: "HOWTO Compile beep-media-player 0.9.7rc2"
date: 2004-10-24
forum: Tutorials
---

### Post by flygmaskin on 2004-10-24
**EDIT:** I know that beep-media-player is included in universe, but that is version 0.9.6.1, which is very buggy. You can Tty installing that one first (sudo apt-get install beep-media-player). If you find 0.9.6.1 to be too buggy, you can follow the instructions below instead.

[Beep-media-player](http://beepmp.sf.net) , or bmp, is a GTK+2 media player, forked from xmms.

From the FAQ:
> "Milosz Derezynski started hacking on XMMS in fall last year (2003) alone and eventually made it compile against GTK+2. He went on to release it to the public under the name 'Beep' and stirred up considerable interest among XMMS users who were eager to move their favourite application to GTK+2. From that moment on, the way was clear. :)"

Before you start:
Make sure you have libglade-2.0 installed.

1. Download the 0.9.7rc2 tarball from SourceForge 
[http://prdownloads.sourceforge.net/beepmp/bmp-0.9.7rc2.tar.gz?download](http://prdownloads.sourceforge.net/beepmp/bmp-0.9.7rc2.tar.gz?download)

2. Unpack the tarball
```
tar -xvzf bmp-0.9.7rc2.tar.gz
```

3. Enter the new directory
```
cd bmp-0.9.7rc2.tar.gz/
```

4. Run the configure script
```
./configure
```

5. Compile bmp
```
make
```

6. Install bmp
```
sudo make install
```

7. Run bmp
```
beep-media-player 
```

Please post any problems that you run in to. You probably need to install some packages in order to do this, and I will add them to this howto whenever I figure out what they are :)

---

### Post by oddabe19 on 2004-10-24
if you want alsa/mp3 remember to pass the --with-alsa / --with-mp3 (? iirc) in your ./configure, or even edit the configure file to suit your needs.

---

### Post by flygmaskin on 2004-10-24
[QUOTE=oddabe19]if you want alsa/mp3 remember to pass the --with-alsa / --with-mp3 (? iirc) in your ./configure, or even edit the configure file to suit your needs.[/QUOTE]
 I don't think that is necessary, it wasn't for me at least (the mp3 part).

---

### Post by oddabe19 on 2004-10-25
Make sure you also have the libglade-2.0 libraries installed as well.

---

### Post by flygmaskin on 2004-10-25
[QUOTE=oddabe19]Make sure you also have the libglade-2.0 libraries installed as well.[/QUOTE]
 Thanks, added to the howto

---

### Post by redeye on 2004-11-12
Hi, I got the following error when configuring:

checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.4.0 gtk+-2.0 >= 2.4.0 gthread-2.0 pango... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
configure: error: Cannot find glib2/gtk2/pango
how can i solve this .I have installed gtk2 , glib.

---

### Post by flygmaskin on 2004-11-12
[QUOTE=redeye]Hi, I got the following error when configuring:

checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.4.0 gtk+-2.0 >= 2.4.0 gthread-2.0 pango... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
configure: error: Cannot find glib2/gtk2/pango
how can i solve this .I have installed gtk2 , glib.[/QUOTE]

You have to install the -dev packages
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev libpango-dev libglade-dev
```

I'm not sure if that are all the packages needed, just post again if you get any more problems.

---

### Post by p!=f on 2004-11-13
Just a few suggestions, I'm sure you won't mind. 
 
 (Note that in this guide I won't go much into details. Consult Maintainers Guide for more than a dirty little guide. :))
 
 **I want to have a control over what's installed on my system. How do I create a package instead?**
 
 First, install everything as mentioned by **flygmaskin**, especially -dev packages. For ALSA support install libasound2-dev and for debianizing sources debmake:
 ```

 sudo apt-get install libasound2-dev debmake
 
```
 
 
 Follow **flygmaskin's** steps till number three. Instead of running *./configure, make, make install*, run following:
 ```

 deb-make
 
```
 
 A small dialog will appear asking you for a type of a package you want to create. Answer *s* for a single binary. Take a look at the debmake manpages to see more options.
 This will create debian directory with some files inside bmp sources.
 > 
 [cut]
 -rw-r--r--  1 pef  pef   426 2004-11-13 14:21 control
 -rwxr-xr-x  1 pef  pef  1347 2004-11-13 14:25 rules
 [/cut]
  (There're more files out there but we'll take a look at the two mentioned above).
 
 **control** file:
 > 
  * 14:39:25 * pef @ agonicus *
 [~/src/beep-media-player-0.9.7rc2] > cat debian/control
 Source: beep-media-player
 Section: universe/sound
 Priority: optional
 Maintainer:  <beep@seznam.cz>
 Standards-Version: 3.5.8
 Build-Depends: debmake
 
 Package: beep-media-player
 Architecture: i386
 Depends: ${shlibs:Depends}
 Description: Versatile audio player that supports Winamp skins
   A player that supports Winamp skins, with a customizable interface based on
  GTK2. It has various output plugins and can read various audio formats.
  is used for providing basic but essential information about the package. As you may see, this file controls dependencies as well.
 Because we are creating a single, little package in our example, we will leave it as it is. Just type something meaningful into the description and section field. Feel free to use lines used above, they are taken from the official package anyway.
 
 **rules** file:
 ```

 * 14:41:09 * pef @ agonicus *
 [~/src/beep-media-player-0.9.7rc2] > cat debian/rules
 [cut]
 #!/usr/bin/make -f
 # Made with the aid of debmake, by Christoph Lameter,
 # based on the sample debian/rules file for GNU hello by Ian Jackson.
 
 package=beep-media-player
 
 build:
         $(checkdir)
         ./configure --prefix=/usr 
         $(MAKE) CFLAGS="-O2 -g -Wall"
         touch build
 [/cut]
 
```
 Again, I won't explain much about this file, consult Maintainers Guide for a full info.
 Let's take a look at the build section as seen above. There's is a single parameter given to the ./configure script, --prefix. But we want more options to be included in the package so run ./configure --help to see all.
 ```

  * 14:49:33 * pef @ agonicus *
 [~/src/beep-media-player-0.9.7rc2] > ./configure --help
 `configure' configures bmp 0.9.7rc2 to adapt to many kinds of systems.
 
```
 (This list is quite long so I won't post it here)
 Now go back to your rules file, section build and edit it like this:
 ```

 build:
         $(checkdir)
         ./configure --prefix=/usr --enable-gconf --enable-gnome-vfs --enable-one-plugin-dir
 
```
 (note that some/all options may be used by default, I just added them to be sure it will compile the way I want to)
 
 Save the file and proceed to the final step:
 ```

 sudo dpkg-buildpackage -D -uc
 
```
 As usual, feel free to take a look at the manpages of the dpkg-buildpackage command.
 
 Now you should have the package beep-media-player_0.9.7rc2-1_i386.deb/ bmp_0.9.7rc2-1_i386.deb (depends on how did you unpacked the sources) in .. created. Install using dpkg and pat yourself on the back. Mission accomplished. :)

---

### Post by tUrtleAE86 on 2004-11-17
I get the following error trying to run configure on a clean install of warty:

checking for X... no
configure: error: Cannot find X11 headers/libraries

Any ideas?

---

### Post by p!=f on 2004-11-17
[QUOTE=tUrtleAE86]I get the following error trying to run configure on a clean install of warty:

checking for X... no
configure: error: Cannot find X11 headers/libraries

Any ideas?[/QUOTE]
You don't have X11 dev packages installed.
```

sudo apt-get install x-dev

```

---

### Post by andyjjones on 2012-03-04
Sorry to post more than 7 years later.  But I thought I'd report with my findings.

To get "./configure" to work I had to install the following packages:

sudo apt-get install xorg-dev
sudo apt-get install glade-gtk2
sudo apt-get install libvorbis-dev

But when I tried to run 'make' I got the following errors (it has been truncated):

Perhaps it just won't work/isn't supported anymore?  I'm  not sure because I'm a Linux newbie.

```

...
mainwin.c:152:17: error: static declaration of &#8216;mainwin_menubtn&#8217; follows non-static declaration
mainwin.h:88:17: note: previous declaration of &#8216;mainwin_menubtn&#8217; was here
mainwin.c:152:35: error: static declaration of &#8216;mainwin_minimize&#8217; follows non-static declaration
mainwin.h:88:35: note: previous declaration of &#8216;mainwin_minimize&#8217; was here
mainwin.c:152:54: error: static declaration of &#8216;mainwin_shade&#8217; follows non-static declaration
mainwin.h:88:54: note: previous declaration of &#8216;mainwin_shade&#8217; was here
mainwin.c:153:6: error: static declaration of &#8216;mainwin_close&#8217; follows non-static declaration
mainwin.h:89:17: note: previous declaration of &#8216;mainwin_close&#8217; was here
mainwin.c:163:16: error: static declaration of &#8216;mainwin_minus_num&#8217; follows non-static declaration
mainwin.h:85:16: note: previous declaration of &#8216;mainwin_minus_num&#8217; was here
mainwin.c:163:36: error: static declaration of &#8216;mainwin_10min_num&#8217; follows non-static declaration
mainwin.h:85:36: note: previous declaration of &#8216;mainwin_10min_num&#8217; was here
mainwin.c:163:56: error: static declaration of &#8216;mainwin_min_num&#8217; follows non-static declaration
mainwin.h:85:56: note: previous declaration of &#8216;mainwin_min_num&#8217; was here
mainwin.c:164:16: error: static declaration of &#8216;mainwin_10sec_num&#8217; follows non-static declaration
mainwin.h:86:16: note: previous declaration of &#8216;mainwin_10sec_num&#8217; was here
mainwin.c:164:36: error: static declaration of &#8216;mainwin_sec_num&#8217; follows non-static declaration
mainwin.h:86:36: note: previous declaration of &#8216;mainwin_sec_num&#8217; was here
mainwin.c: In function &#8216;run_no_audiocd_dialog&#8217;:
mainwin.c:2427:44: warning: format not a string literal and no format arguments [-Wformat-security]
mainwin.c: In function &#8216;run_no_output_device_dialog&#8217;:
mainwin.c:2447:44: warning: format not a string literal and no format arguments [-Wformat-security]
make[4]: *** [beep-mainwin.o] Error 1
make[4]: Leaving directory `/home/andrew/Desktop/bmp-0.9.7rc2/beep'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/andrew/Desktop/bmp-0.9.7rc2/beep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/andrew/Desktop/bmp-0.9.7rc2/beep'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andrew/Desktop/bmp-0.9.7rc2'
make: *** [all] Error 2

```

---


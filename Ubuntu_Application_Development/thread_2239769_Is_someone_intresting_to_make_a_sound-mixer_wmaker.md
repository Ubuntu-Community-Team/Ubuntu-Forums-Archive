---
title: "Is someone intresting to make a sound-mixer wmaker dockapp for ALSA"
date: 2014-08-15
forum: Ubuntu Application Development
---

### Post by Andy_Crowd on 2014-08-15
Hi!

I am looking for someone who can create a sound-mixer dockapp that supports ALSA and [COLOR=#ff0000]not[/COLOR] OSS.

Source for [http://ie.archive.ubuntu.com/pld-linux/pool/w/wmmixer-alsa/](http://ie.archive.ubuntu.com/pld-linux/pool/w/wmmixer-alsa/) cannot be compiled in ubuntu.

I have also tested with [COLOR=#800000]*wmmixer-alsa-0.6-1.i686.rpm*[/COLOR]
1) Extracted files with [xarchiver]("http://packages.ubuntu.com/search?keywords=xarchiver&searchon=names").
2) Installed [libxpm-dev]("http://packages.ubuntu.com/trusty/libxpm-dev"), and followed this [guide]("http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system") to make it possible for 32 bit programs to run on a 64 bit Ubuntu.
3) Copied sub-folders from [COLOR=#0000cd]*X11R6*[/COLOR] directory into[COLOR=#0000cd] */usr/*[/COLOR]
4) Created a symlink[COLOR=#006400]* ln -s /usr/lib/x86_64-linux-gnu/libXpm.so.4.11.0*[/COLOR][COLOR=#0000ff]* libXpm.so.4*[/COLOR] in the [COLOR=#0000ff]*/lib/*[/COLOR] directory and got errors like:
./wmmixer-alsa 
./wmmixer-alsa: error while loading shared libraries: libXpm.so.4: wrong ELF class: ELFCLASS64

How make it work? Or how to compile the source code correctly without any problems/erros?

---

### Post by Andy_Crowd on 2014-08-19
At least I found a [alsamixer-dockapp]("http://www.filewatcher.com/p/alsamixer-dockapp-0.1-3.fc17.src.rpm.32513/AlsaMixer.app-0.1.tar.gz.html"). It looks like a [Mixer.app]("http://packages.ubuntu.com/sv/raring/mixer.app") but using [ALSA]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&lang=sv&keywords=alsa-base&searchon=names") instead of [OSS]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&lang=sv&keywords=alsa-OSS&searchon=names"). It is easy to compile, just by using *make* command and then *sudo make install:*
```
install -d  /usr/local/GNUstep/Apps/AlsaMixer.app
install -m 0755 AlsaMixer.app /usr/local/GNUstep/Apps/AlsaMixer.app/AlsaMixer
```
The executable AlsaMixer file is installed in the[I] /usr/local/GNUstep/Apps/AlsaMixer.app
[/I]For an easy access you can create a symlink:
```
cd /usr/local/bin
ln -s /usr/local/GNUstep/Apps/AlsaMixer.app/AlsaMixer AlsaMixer
```

It will work like a charm and has a lot of good configuration options:```
AlsaMixer -h
AlsaMixer.app Copyright (c) 1998-2002 by Per Liden (per@fukt.bth.se), Petr Hlavka (xhlavk00@stud.fit.vutbr.cz)

options:
 -1 <source>     set sound source for control 1 (default is Master)
 -2 <source>     set sound source for control 2 (default is PCM)
 -3 <source>     set sound source for control 3 (default is CD)
 -w 1|2|3        bind a control button to the mouse wheel (default is 1)
 -l <text>       set label text
 -S              save volume settings on exit
 -L              load volume settings on start up
 -f    <file>       use setting <file> instead of ~/GNUstep/Defaults/AlsaMixer
 --card <id>     select card
 --device <dev>  select device, default 'default'
 -e <command>    execute <command> on middle click
 -n <name>       set client instance name
 -d <disp>       set display
 -v              print version and exit
 -h, --help      display this help and exit
``` But leaks one of my favorite feature from *wmmixer* , when clicking somewhere on the bar it jumps there and no need to pull. Unfortunately I could not compile *wmmixer-alsa* and so far got no help with it.

Thanks for me!

---


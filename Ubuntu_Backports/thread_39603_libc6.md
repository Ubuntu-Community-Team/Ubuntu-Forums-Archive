---
title: "libc6"
date: 2005-06-05
forum: Ubuntu Backports
---

### Post by TravisNewman on 2005-06-05
Hey, just wondering if you knew that a lot of the media related backports (specifically mplayer right now) aren't working because libc6 is too old. I'm not sure if there's much you can do about it, just wanted to let you know.

---

### Post by TravisNewman on 2005-06-05
apologies all around.

I had another repo with mplayer in it, and I had no clue it was there!

There are some problems still when trying to install some backports because of dependencies not existing in the repos. I only have the official repos and backports now.

(did a fresh install today because I'd borked some stuff).

---

### Post by oddabe19 on 2005-06-05
[QUOTE=panickedthumb]apologies all around.

I had another repo with mplayer in it, and I had no clue it was there!

There are some problems still when trying to install some backports because of dependencies not existing in the repos. I only have the official repos and backports now.

(did a fresh install today because I'd borked some stuff).[/QUOTE]
 libc6 seems to be broken anyway.... totem-xine xine amarok java amongst many other things (libpthread) die because libc6 is broken (on my pc at least)

---

### Post by oddabe19 on 2005-06-06
[QUOTE=oddabe19]libc6 seems to be broken anyway.... totem-xine xine amarok java amongst many other things (libpthread) die because libc6 is broken (on my pc at least)[/QUOTE]
 bump: is anyone else experienceing that?

---

### Post by jdong on 2005-06-07
Umm, is the libc6 breakage Backports related? Backports provides a newer version of libstdc++6 due to a GCC4 backport, which on my system hasn't caused any issues yet.

---

### Post by oddabe19 on 2005-06-07
[QUOTE=jdong]Umm, is the libc6 breakage Backports related? Backports provides a newer version of libstdc++6 due to a GCC4 backport, which on my system hasn't caused any issues yet.[/QUOTE]
 I don't know, but yeah, i kinda started experiencing the problems with the new libc6 when that upgraded and when gcc4 got installed as well... through backports.

apt-get install --reinstall libc6 doesn't work, and i can't uninstall it fully... without uninstalling nearly EVERYTHING on my system.

---

### Post by jdong on 2005-06-07
Does **apt-get install libc6/hoary** fix your issues?

---

### Post by hostile on 2005-06-07
[QUOTE=jdong]Does **apt-get install libc6/hoary** fix your issues?[/QUOTE]


I too am having issues trying to install from the standard repositories:

[INDENT]Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages[/INDENT]

If I try 'apt-get install libc6/hoary', I get:

[INDENT]
Selected version 2.3.2.ds1-20ubuntu13 (Ubuntu:5.04/hoary) for libc6
libc6 is already the newest version.
[/INDENT]

I am using the standard repositories.

---

### Post by jdong on 2005-06-07
Post your sources.list. Ubuntu only has libc6 version 2.3.2.ds1-20ubuntu13: for Hoary. No other choice.

---

### Post by oddabe19 on 2005-06-08
I get that too, I wish i could just uninstall libc6, but since everything relies on it, it seems like the only way out is by reformatting.
My debug output is here [http://home.comcast.net/~amsilveira/totem.txt](http://home.comcast.net/~amsilveira/totem.txt) which is the same output i get for any program that just crashes on startup (GUI shows, but then dies). This was from Totem-xine, totem-gstreamer works (but i hate it).
problems start at libpthreads, which ldd traces to libc6.

```
#deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

###Hoary Branch###
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted  
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted  

deb http://archive.ubuntu.com/ubuntu/ hoary universe  
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe  

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse  
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

#deb http://backports.ubuntuforums.org/ubp hoary-backports-staging main universe multiverse restricted
#deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
```

---

### Post by Farhad on 2005-06-08
Try removing the debian-marrilat entries except testing (WFM)

---

### Post by jdong on 2005-06-08
debian-marillat entries are causing it. Marillat is compiled against Debian, which recently got new libc6 versions.

So, this has nothing to do with Backports.

---

### Post by oddabe19 on 2005-06-08
so, how would I revert to our libc6? just take them out then apt-get reinstall libc6?

The version installed, is the version on the backports (2.3.2.ds1-ubuntu13).

---

### Post by jdong on 2005-06-08
You're already at your libc6. It's just that you can no longer install packages from Marillat.

---

### Post by oddabe19 on 2005-06-08
[QUOTE=jdong]You're already at your libc6. It's just that you can no longer install packages from Marillat.[/QUOTE]
 i know taking out marillat keeps me from installing packages from them, but that doesnt fix my libc6 problem then....

Did you see my debug output? if so, what are your thoughts?

---

### Post by jdong on 2005-06-08
I'm not understanding... what's your problem?

---

### Post by oddabe19 on 2005-06-08
Programs crash on startup (once gui shows)
Debug output shows problems start at libpthreads (see my totem.txt debug output).
ldd traces libpthreads to libc6.

It seemed to break about the time gcc4 was installed from backports.
Therefor it seemed that the current libc6 was broken for me, i was wondering if anyone else had the same problem essentially. I thought you did (or knew of my problem) that's why i kept the thread going.

but if not, that's ok :-)

---

### Post by jdong on 2005-06-08
Hmm, totem and all java apps on my system work fine. I don't know what's wrong with yours. ;)

---

### Post by mtron on 2005-06-10
i know it's a bit off topic here, but i can you try to backport the libc6 2.3.2.ds1-21 from debian to hoary, or is it impossible?

---

### Post by DarkSilver on 2005-06-11
[QUOTE=mtron]i know it's a bit off topic here, but i can you try to backport the libc6 2.3.2.ds1-21 from debian to hoary, or is it impossible?[/QUOTE]
It'll be cool because a lot of packages of marillat are very useful (last mplayer, w32codecs, etc..)

---

### Post by jdong on 2005-06-11
[QUOTE=mtron]i know it's a bit off topic here, but i can you try to backport the libc6 2.3.2.ds1-21 from debian to hoary, or is it impossible?[/QUOTE]

Every package in Hoary would have to be recompiled against this new libc ;)

---

### Post by mtron on 2005-06-11
ok. i think thats a clear answer, althou wouldn't it be a challange?  ;-)  just kidding.

---

### Post by DarkSilver on 2005-06-11
[QUOTE=jdong]Every package in Hoary would have to be recompiled against this new libc ;)[/QUOTE]

another solution is to recompile ONLY marillat package into backports 
the only thing to change is the libc6 depends of these packages !

Thanks to this, we won't need to add marillat repositry to our sources.list, only the backport one !

---

### Post by verbalshadow on 2005-06-11
[QUOTE=DarkSilver]another solution is to recompile ONLY marillat package into backports 
the only thing to change is the libc6 depends of these packages !

Thanks to this, we won't need to add marillat repositry to our sources.list, only the backport one ![/QUOTE]
 backports only can pull from the current development version of ubuntu

---

### Post by jdong on 2005-06-11
extras does incorporate a good chunk of Marillat. However, for stuff like mplayer in marillat, there's this never ending spiral of dependencies, and they're not all specified in the debian packages. I've tried to import as much of Marillat into hoary-extras as I could.

---


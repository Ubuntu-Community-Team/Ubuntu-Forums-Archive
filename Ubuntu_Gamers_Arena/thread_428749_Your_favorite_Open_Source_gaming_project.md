---
title: "Your favorite Open Source gaming project"
date: 2007-04-30
forum: Ubuntu Gamers Arena
---

### Post by compiledkernel on 2007-04-30
What do you think is going to be the next big up and coming Linux Friendly Game? 

For me , on the retail level - UT3 or Quakewars. 

On the non-retail level - Its Padman's. 

What other games out there should we follow or do you think will turn out from its beginnings to be a big game?

---

### Post by hikaricore on 2007-04-30
[http://funguloids.sourceforge.net/](http://funguloids.sourceforge.net/) <--- this ftw

---

### Post by drbob07 on 2007-04-30
I can't even get Funguloids to work. I wish I could though, it looks like a good game.


WZ2100 (Ressurection) is my favorite
[http://wz2100.net/](http://wz2100.net/)

---

### Post by hikaricore on 2007-05-01
>.<  I'm still working on figuring out how to compile Funguloids myself.  I cheated and played the windows version at work.  lol

I've managed to compile and install all the proper libraries on my edgy system except for Ogre.

I'll post more info on UGA upon success, unless AI  or CK decide to beat me to it.

---

### Post by Matt Yun on 2007-05-01
Just an apt-get install away...

[Vegastrike]("http://vegastrike.sourceforge.net/"): an Elite/Privateer space shooter, moddable

[Nexuiz]("http://www.alientrap.org/nexuiz/")

---

### Post by Xenogis on 2007-05-01
does xbmc count?

---

### Post by Perfect Storm on 2007-05-01
> **hikaricore said:**
> >.<  I'm still working on figuring out how to compile Funguloids myself.  I cheated and played the windows version at work.  lol

I've managed to compile and install all the proper libraries on my edgy system except for Ogre.

I'll post more info on UGA upon success, unless AI  or CK decide to beat me to it.

You need to compile CEGUI, install Nvidia cg Tool, compile the latest Ogre and install fmodEX

---

### Post by Perfect Storm on 2007-05-01
Hika if you want to try, I just put this together;

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall flex bison pkg-config libboost-filesystem-dev autoconf automake1.9 libtool
sudo aptitude install liblua5.1-0-dev libfreetype6-dev libzzip-dev libxt-dev libxaw7-dev libxxf86vm-dev libxrandr-dev libgtk2.0-dev libpng12-dev libdevil-dev libopenexr-dev libpcre3-dev libexpat1-dev libxml-parser-perl libxerces27-dev libgl1-mesa-dev libglu1-mesa-dev libxml2-dev


CG Toolkit
----------
cd ~/Desktop
wget [http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007_x86.tar.gz](http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007_x86.tar.gz)
tar zxfv Cg-1.5_Feb2007_x86.tar.gz
cd usr
sudo cp -r * /usr


CEGUI - 
----------
cd ~/Desktop
wget [http://prdownloads.sourceforge.net/crayzedsgui/CEGUI-0.5.0b.tar.gz?download](http://prdownloads.sourceforge.net/crayzedsgui/CEGUI-0.5.0b.tar.gz?download)
tar zxfv CEGUI-0.5.0b.tar.gz
cd CEGUI-0.5.0
./configure --prefix=/usr --with-gtk2 
make
sudo make install

OIS - [http://downloads.sourceforge.net/wgois/ois-1.0RC1.tar.gz?modtime=1165167684&big_mirror=0](http://downloads.sourceforge.net/wgois/ois-1.0RC1.tar.gz?modtime=1165167684&big_mirror=0)
---------------
cd ~/Desktop
tar zxfv ois-1.0RC1.tar.gz
cd ois-1.0RC1
./bootstrap
./configure --prefix=/usr
make
sudo checkinstall

OGRE
---------
cd ~/Desktop
wget [http://downloads.sourceforge.net/ogre/ogre-linux_osx-v1-4-0.tar.bz2?download](http://downloads.sourceforge.net/ogre/ogre-linux_osx-v1-4-0.tar.bz2?download)
tar jxfv ogre-linux_osx-v1-4-0.tar.bz2
cd ogrenew
./configure --enable-openexr --disable-freeimage
make
sudo make install




Fmod
---------
cd ~/Desktop
wget [http://www.fmod.org/files/fmodapi40616linux.tar.gz](http://www.fmod.org/files/fmodapi40616linux.tar.gz)
tar zxfv fmodapi40616linux.tar.gz
cd fmodapi40616linux
sudo checkinstall
sudo ln -s /usr/local/lib/libfmodex.so /usr/lib/libfmodex.so


Funguloids
-----------
cd ~/Desktop
tar jxfv funguloids-linux-1.05f.tar.bz2 
cd funguloids
make

---

### Post by hikaricore on 2007-05-01
> **Artificial Intelligence said:**
> You need to compile CEGUI, install Nvidia cg Tool, compile the latest Ogre and install fmodEX

retrying now with your instructions >.<

FreeImage was pwning me.

---

### Post by Clay_Banger on 2007-05-01
> **Artificial Intelligence said:**
> I just put this together;I tried, but got stuck at:

> OIS - [http://downloads.sourceforge.net/wgo...4&big_mirror=0](http://downloads.sourceforge.net/wgo...4&big_mirror=0)
---------------
cd ~/Desktop
tar zxfv ois-1.0RC1.tar.gz
cd ois-1.0RC1
./bootstrap
./configure --prefix=/usr
make
sudo checkinstallThis is my output:
```
michaelc@backwards:~/Desktop/ois-1.0RC1$ ./bootstrap
You should update your `aclocal.m4' by running aclocal.
aclocal:configure.ac:15: warning: macro `AM_PROG_LIBTOOL' not found in library
src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:3:
src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:3: to `configure.ac' and run `aclocal' and `autoconf' again.
```I have no idea what that means.:confused: Any ideas?

---

### Post by donkyhotay on 2007-05-01
If your talking straight open-source projects I'm keeping an eye on globulation2 and the mana world.

---

### Post by mh114 on 2007-05-02
A better Linux version (v1.06) of **Those Funny Funguloids** is in the works, with proper autotools build and OpenAL support in addition to FMOD Ex. :) You can follow the development from this thread at Ogre forums: [http://www.ogre3d.org/phpBB2/viewtopic.php?t=29147&start=50](http://www.ogre3d.org/phpBB2/viewtopic.php?t=29147&start=50)

Hopefully somebody'll contribute an Ubuntu deb when we're done. ;)

---

### Post by Perfect Storm on 2007-05-02
*Good news ^_^

---

### Post by phorim on 2007-05-10
Thanks for all the commands, AI.  Between this thread and the Fungaloids thread on the Ogre forums, I managed to compile everything you listed here for Feisty AMD64.  I think it is important that I mention that up until the last couple days or so I was very uncomfortable compiling from source, but all this has given me a major boost in confidence.

Thanks,
Randall

---

### Post by DuneSoldier on 2007-05-11
I've been very impressed with [ UFO: Alien Invasion ]("http://ufo.myexp.de/").

---

### Post by lethu on 2007-05-12
**Those Funny Funguloids** looks pretty awesome ! I never knew about even its existence, same thing with **World of Padman** and even the release of Q3's sourcecode (I lived in a cave named Windows for the last 2 years) this definitely is some really good news : D !
Now one of the other most promising OS games to me is [Planeshift]("http://www.planeshift.it/"), it's an mmorpg and it is using the Crystalspace 3d engine, I regularly played to many of its releases both under Windows and Linux and it is continuously making huge progress.
[Happypenguin]("http://happypenguin.org/") (aka The Linux Game Tome) is one great place to spot promising games.

---

### Post by Perfect Storm on 2007-05-12
> Happypenguin (aka The Linux Game Tome) is one great place to spot promising games.

Most of these games can be found on UGL.

---

### Post by AthlonMDK on 2007-05-12
I like wesnoth, openttd, World of Padman.

Recently linux opensource games are getting better and better...

---

### Post by lethu on 2007-05-13
> **Artificial Intelligence said:**
> Most of these games can be found on UGL.

Great site indeed ! I should have already noticed it in your sig, however unlike in Happypenguin.org there are no user comments nor ranking system in UGL, functions which can prove very informative and useful to users, but I guess the two sites are of different types.

I have some difficulties running Those Funny Funguloids though, I followed your instructions compiling everything successfully (had to install two more libs in my case to get CEGUI compiled, libtiff4-dev and libjpeg62-dev) but the game exits right after showing a black window for a couple seconds vomiting some error messages in the terminal, the most interesting part of which is this : 
```
Cannot find codec for extension png in Codec::getCodec at OgreCodec.cpp (line 62)Segmentation fault (core dumped)
```
From what I have learned, that means Ogre is missing png support, so after many hours reading forum posts and wikis I found out that I was supposed to : A) ./configure Ogre with the -enable-devil=yes (tried --enable-devil=yes and -enable-devil too) flag in order to get png support, or B) compile Ogre with Freeimage. Both ways led me nowhere. With A I still get the same result when launching the game while with B I get errors at Ogre's compile time even with the FreeImage library installed (at least I understand now the why of that --disable-freeimage flag)
All I got now is : a huge headache, many many useless libraries scattered through all the system, one possibly great game that won't run and a delay of one whole night of sleep...
Please can you help me improve my situation ?

Also for those like me who might encounter troubles getting Ogre to find libOgreMain-1.4.0.so even tho it's in /usr/local/lib, here is how you can triumph over this naughty obstacle :-D .
Put this in your terminal :
```
export LD_LIBRARY_PATH=/usr/local/lib
```
then if it works, for a more permanent solution add a new file in /etc/ld.so.conf.d/ with /usr/local/lib as its content and run :
```
sudo ldconfig
```
enjoy :biggrin: !

All this makes me nostalgic though, it makes me recall the days I was sweating over apps to get them compiled under Mandrake (my first distro) most of the time unsuccessfully, hehe.

PS: Sorry for my english, feel free to correct me :-).

---

### Post by Perfect Storm on 2007-05-13
I'm planning to rebuild Ubuntu Game List, with rating system etc. better overview, links etc. but at the moment I'm collectiong ideas from fellow gamers how they ideas of an ultimate list looks like in their eyes.


About Funny Funguloids it's a bit tricky, but the great news is the guy who made it are building a more friendly linux set up for it :KS

---

### Post by el mariachi on 2007-05-13
Fungloids seems very original and the graphics are quite something, too bad there's no deb yet

I played Planeshift and found it to be a little... weird... :lolflag:

Pok3d is a good game too, if you like poker off course

---

### Post by lethu on 2007-05-13
> **Artificial Intelligence said:**
> I'm planning to rebuild Ubuntu Game List, with rating system etc. better overview, links etc. but at the moment I'm collectiong ideas from fellow gamers how they ideas of an ultimate list looks like in their eyes.
Nice, am sure your site will become more popular if you  do that.

Regarding Funny Funguloids, I tried this "./configure --enable-openexr" with Ogre and now I can successfully compile it with the Freeimage library support and run Funguloids but I can't go past the greeting screen, it just exits as soon as I click or hit enter. The log file shows some warning and fail messages :
```
WARNING: material Ogre/Compositor/Blur0 has no supportable Techniques and will be blank. Explanation: 
Pass 0: Vertex program Blur0_vs11 cannot be used - not supported.
Pass 0: Vertex program Blur0_vs_glsl cannot be used - not supported.

funguloids: OgreGpuProgram.cpp:621: void Ogre::GpuProgramParameters::_writeRawConstants(size_t, const float*, size_t): Assertion `physicalIndex + count <= mFloatConstants.size()' failed.
Aborted (core dumped)
```

Sorry for having somewhat hijacked this topic, but I have officially given up now and shall not pull my hair out any longer on this game, I guess I ll just sit and wait for the more linux friendly release.
I have learned one thing though, Ubuntu along with its community aren't much "compile it yourself" friendly, unlike Gentoo for example.

---

### Post by LordFu on 2007-05-13
UFO: Alien Invasion

I've got high hopes for this game. I'm a huge X-Com fan.

---

### Post by mh114 on 2007-05-14
> **lethu said:**
> Regarding Funny Funguloids, I tried this "./configure --enable-openexr" with Ogre and now I can successfully compile it with the Freeimage library support and run Funguloids but I can't go past the greeting screen, it just exits as soon as I click or hit enter. The log file shows some warning and fail messages :
```
WARNING: material Ogre/Compositor/Blur0 has no supportable Techniques and will be blank. Explanation: 
Pass 0: Vertex program Blur0_vs11 cannot be used - not supported.
Pass 0: Vertex program Blur0_vs_glsl cannot be used - not supported.

funguloids: OgreGpuProgram.cpp:621: void Ogre::GpuProgramParameters::_writeRawConstants(size_t, const float*, size_t): Assertion `physicalIndex + count <= mFloatConstants.size()' failed.
Aborted (core dumped)
```
Darn, that problem seems to be quite common.. :P I've had three reports of the same thing so far. Could you post your system specs and Ogre.log here? I'm guessing you're on nVidia card? :)

The v1.06 will improve the Linux build process (it has ./configure and OpenAL support by default), .debs will have to wait until someone contributes the necessary Ogre / etc. debs.. :) Unfortunately this assertion problem is so far unknown.. :( But I'm working on it, although a bit clueless atm..

---

### Post by lethu on 2007-05-14
> **mh114 said:**
> Darn, that problem seems to be quite common.. :P I've had three reports of the same thing so far. Could you post your system specs and Ogre.log here? I'm guessing you're on nVidia card? :)

Of course :D, you will find the log attached to this post (renamed to .txt though since naughty forum doesn't seem to appreciate .log extensions) along with my system specs.
And yeah you were right am on nVidia! A developer trick I guess? hehe :).

Also I noticed two things that may or may not be related to the issue, key repetition gets deactivated each time Funguloids crashes, hitting the Num lock key two times fixes that. The second thing is that some Ogre demos (not all) crash the same way Funguloids do and again key repetition gets deactivated. Hope all of this will help you fix the problem and allow people with similar issues to finally collect those tasty mushrooms :p!
Good luck!

PS: May I say Finnish game-development FTW! Even tho am not Finnish ;).

---

### Post by mh114 on 2007-05-14
> **lethu said:**
> Of course :D, you will find the log attached to this post (renamed to .txt though since naughty forum doesn't seem to appreciate .log extensions) along with my system specs.
And yeah your were right am on nVidia! A developer trick I guess? hehe :).
Thanks a lot. And yup, the very same problem. So far it has been on GF 4 Ti and GF 2. Windows version however worked fine on my old & crappy GF 2 MX, so it must be Linux only. And I thought it'd be on nVidia since all the previous reports have been.. ;)

> Also I noticed two things that may or may not be related to the issue, key repetition gets deactivated each time Funguloids crashes, hitting the Num lock key two times fixes that. The second thing is that some Ogre demos (not all) crash the same way Funguloids do and again key repetition gets deactivated. Hope all of this will help you fix the problem and allow people with similar issues to finally collect those tasty mushrooms :p!
Good luck!
Hmm, this is interesting. I thought that it'd be something I'm doing wrong, but if the Ogre demos crash also it must be Ogre related.. :? I have the key repetition issue as well, since it always crashes on me at exit (due to crappy ATI drivers, I've gathered). Good to know that it can be fixed with Num lock, I've always had to uncheck and check the repetition box from Keyboard properties..

Does for example Ogre demo Dot3Bump work? Also, if you could get CEGUI and rebuild Ogre with it, you get the Compositor demo. It would be helpful if you could test that. As far as I can tell, it should fail exactly the same way as Funguloids. If not, then it's something wrong on my part. Thanks for your help so far. :)

> PS: May I say Finnish game-development FTW! Even tho am not Finnish ;).
Why you certainly may! ;) Thanks!

---

### Post by lethu on 2007-05-14
> **mh114 said:**
> Does for example Ogre demo Dot3Bump work? Also, if you could get CEGUI and rebuild Ogre with it, you get the Compositor demo. It would be helpful if you could test that. As far as I can tell, it should fail exactly the same way as Funguloids. If not, then it's something wrong on my part. Thanks for your help so far. :)

No problem :). I tried launching the Dot3Bump demo and yup like you predicted it did fail the same way as Funguloids, outputting the following message :

```
Dot3Bump: OgreGpuProgram.cpp:621: void Ogre::GpuProgramParameters::_writeRawConstants(size_t, const float*, size_t): Assertion `physicalIndex + count <= mFloatConstants.size()' failed.
Aborted (core dumped)
```

I However had no success running the Compositor demo even though I had CEGUI compiled both before and after Ogre, but I think am doing something wrong as from what I have understood Ogre is complaining about not being able to locate CEGUI (am I missing a flag when compiling Ogre or something?) :

```
An exception has occured: OGRE EXCEPTION(6:FileNotFoundException): Cannot locate resource CEGUIConfig.xsd in resource group General or any other group. in ResourceGroupManager::openResource at OgreResourceGroupManager.cpp (line 603)Unregistering ResourceManager for type BspLevel
*-*-* OGRE Shutdown
```

So can't really tell if the demo is working or not.

Now with the possibility that the problem might be Ogre related in mind, am going to get Ogre's development version from CVS (I was using the stable release so far), compile then cross fingers hoping that the latest release got this problem fixed :D. I will probably do that this evening, I ll keep you informed.

PS: I also tried launching both the demo and Funguloids with different RTT modes as suggested in some forum/wiki, always unsuccessfully.

---

### Post by lethu on 2007-05-14
Sorry for not having been able to do this earlier, I had many things to do in town.
No luck with Ogre's development version, it still spits the same errors ](*,), that was my ultimate attempt, I hope you ll get more luck than me.

PS: Let me know if I can do anything else to help :).

---

### Post by mh114 on 2007-05-15
> **lethu said:**
> Sorry for not having been able to do this earlier, I had many things to do in town.
No luck with Ogre's development version, it still spits the same errors ](*,), that was my ultimate attempt, I hope you ll get more luck than me.
No problem, thanks for the information. :) It indeed seems to be an Ogre bug, so there's not very much I can do right now. I do have my thread on the Ogre forums about this, and I probably will report this as a bug later.

---

### Post by Roberticus on 2007-05-18
Funny, no one mentioned Nosferatu - Carpe Diem 
Vampires with claws and super powers against humans with guns, all open source (Not released yet though).
Based on QFusion engine (based on Q2). 
Some pics
[http://nosferatuthegame.com/media/ingame/nosferatu00020.jpg](http://nosferatuthegame.com/media/ingame/nosferatu00020.jpg)

[http://nosferatuthegame.com/media/ingame/nosferatu00018.jpg](http://nosferatuthegame.com/media/ingame/nosferatu00018.jpg)

Vampire player model:
[http://nosferatuthegame.com/media/players/nos_scare-ws.jpg](http://nosferatuthegame.com/media/players/nos_scare-ws.jpg)

And a video of engine capabilities:
[http://www.nosferatuthegame.com/media/video/nosferatu_engine_divx.avi](http://www.nosferatuthegame.com/media/video/nosferatu_engine_divx.avi)


And of course the website: 
[http://www.nosferatuthegame.com/](http://www.nosferatuthegame.com/)

---

### Post by Perfect Storm on 2007-05-18
Well the reason people havn't mention it could be that it isn't released yet ;)
I always hesitate to say X an Y game is my favorite until I have tried it :guitar:

---

### Post by el mariachi on 2007-05-18
SoulFu seems cool too! Although not released yet (only source code available, care to compile?) it's not GPL'd tho

[http://www.aaronbishopgames.com/](http://www.aaronbishopgames.com/)

---

### Post by mh114 on 2007-05-18
Regarding to the Funguloids assertion problem: The bug is indeed in Ogre ([http://www.ogre3d.org/mantis/view.php?id=170](http://www.ogre3d.org/mantis/view.php?id=170)), hopefully it'll get fixed at some point. :)

EDIT: Fixed the link.

---

### Post by lethu on 2007-05-21
That's great that somebody filled a bug report for this in Ogre's site! I also hope it won't take too long before someone gets it fixed. Thanks for sharing :)

---

### Post by Zyphrexi on 2007-05-21
I really want to see vega strike take off. (no pun intended)

EDIT: 

free source of soul-fu is now available according to [freegamer]("http://freegamer.blogspot.com/")

there's a bin [here]("http://perpetuum-immobile.de/soulfu.bin")

---

### Post by el mariachi on 2007-05-22
how do I install the bin? sh doesn't seem to work (newbie here)

---

### Post by lethu on 2007-05-22
Type ```
./soulfu.bin
``` in your fav terminal, make sure you cd to the bin's dir before.

---

### Post by mh114 on 2007-05-24
[Those Funny Funguloids!](http://funguloids.sourceforge.net) has reached v1.06. :) The assertion problem is still there though, as it is Ogre bug. :(

Changes since v1.05:
[list][*]We have music now! 
[*]A proper Linux version (autotools + OpenAL support) is now available, thanks to Piet! 
[*]More nicely aligned high scores 
[*]Upgraded to Ogre v1.4.1 
[*]Small bug fixes plus more platform independant code.. [/list]

---

### Post by finferflu on 2007-05-30
> **lethu said:**
> Type ```
./soulfu.bin
``` in your fav terminal, make sure you cd to the bin's dir before.
I tried that, but it does nothing...
Actually, all it does, is creating a logfile, which says:

```
INFO:   Log file started
INFO:   ------------------------------------------
INFO:   Allocated 33554432 bytes (32 Meg) for the mainbuffer
INFO:   Trying to open DATAFILE.SDF
ERROR:  DATAFILE.SDF not open
ERROR:  sdf_load() failed
INFO:   Log file closed
```

I was wandering wether I needed the source together with the bin file...

---

### Post by finferflu on 2007-05-30
> **Artificial Intelligence said:**
> Hika if you want to try, I just put this together;

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential checkinstall flex bison pkg-config libboost-filesystem-dev autoconf automake1.9 libtool
sudo aptitude install liblua5.1-0-dev libfreetype6-dev libzzip-dev libxt-dev libxaw7-dev libxxf86vm-dev libxrandr-dev libgtk2.0-dev libpng12-dev libdevil-dev libopenexr-dev libpcre3-dev libexpat1-dev libxml-parser-perl libxerces27-dev libgl1-mesa-dev libglu1-mesa-dev libxml2-dev


CG Toolkit
----------
cd ~/Desktop
wget [http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007_x86.tar.gz](http://developer.download.nvidia.com/cg/Cg_1.5/1.5.0/0019/Cg-1.5_Feb2007_x86.tar.gz)
tar zxfv Cg-1.5_Feb2007_x86.tar.gz
cd usr
sudo cp -r * /usr


CEGUI - 
----------
cd ~/Desktop
wget [http://prdownloads.sourceforge.net/crayzedsgui/CEGUI-0.5.0b.tar.gz?download](http://prdownloads.sourceforge.net/crayzedsgui/CEGUI-0.5.0b.tar.gz?download)
tar zxfv CEGUI-0.5.0b.tar.gz
cd CEGUI-0.5.0
./configure --prefix=/usr --with-gtk2 
make
sudo make install

OIS - [http://downloads.sourceforge.net/wgois/ois-1.0RC1.tar.gz?modtime=1165167684&big_mirror=0](http://downloads.sourceforge.net/wgois/ois-1.0RC1.tar.gz?modtime=1165167684&big_mirror=0)
---------------
cd ~/Desktop
tar zxfv ois-1.0RC1.tar.gz
cd ois-1.0RC1
./bootstrap
./configure --prefix=/usr
make
sudo checkinstall

OGRE
---------
cd ~/Desktop
wget [http://downloads.sourceforge.net/ogre/ogre-linux_osx-v1-4-0.tar.bz2?download](http://downloads.sourceforge.net/ogre/ogre-linux_osx-v1-4-0.tar.bz2?download)
tar jxfv ogre-linux_osx-v1-4-0.tar.bz2
cd ogrenew
./configure --enable-openexr --disable-freeimage
make
sudo make install




Fmod
---------
cd ~/Desktop
wget [http://www.fmod.org/files/fmodapi40616linux.tar.gz](http://www.fmod.org/files/fmodapi40616linux.tar.gz)
tar zxfv fmodapi40616linux.tar.gz
cd fmodapi40616linux
sudo checkinstall
sudo ln -s /usr/local/lib/libfmodex.so /usr/lib/libfmodex.so


Funguloids
-----------
cd ~/Desktop
tar jxfv funguloids-linux-1.05f.tar.bz2 
cd funguloids
make

Sorry for double posting and double-asking, but I was trying to compile Those Funny Funguloids, and I used [this script]("http://qbic.sourceforge.net/node/6") to build OGRE, CEGUI, FreeImage, Cg and OIS from CVS. It is supposed to be for Edgy, but I gave it a go on Feisty to see if it worked anyways, and it seemed to go flawlessly. Now, I passed the ./configure part of Funguloids, but when I run make I get the following error:

```
make[1]: Entering directory `/home/mmanu/Desktop/funguloids/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -I../include/SimpleIni -I/usr/include/lua5.1 -I/usr/include/OIS   -DOGRE_GUI_gtk -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/OGRE    -g -O2 -MT funguloids-ballworm.o -MD -MP -MF ".deps/funguloids-ballworm.Tpo" -c -o funguloids-ballworm.o `test -f 'ballworm.cpp' || echo './'`ballworm.cpp; \
        then mv -f ".deps/funguloids-ballworm.Tpo" ".deps/funguloids-ballworm.Po"; else rm -f ".deps/funguloids-ballworm.Tpo"; exit 1; fi
../include/streamplayer.h:69: error: ISO C++ forbids declaration of &#8216;SoundStream&#8217; with no type
../include/streamplayer.h:69: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../include/streamplayer.h:71: error: ISO C++ forbids declaration of &#8216;SoundStream&#8217; with no type
../include/streamplayer.h:71: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[1]: *** [funguloids-ballworm.o] Error 1
make[1]: Leaving directory `/home/mmanu/Desktop/funguloids/src'
make: *** [all-recursive] Error 1
```

What to do?
By the way, I used OpenAL instead of FMOD, I also tried to install FMOD as indicated above, with no positive results.

Thanks for your time.

---

### Post by mh114 on 2007-06-10
Those Funny Funguloids:
> **mh114 said:**
> The assertion problem is still there though, as it is Ogre bug. :(
I'm happy to report that the assertion bug has been fixed in Ogre 1.4.2. :) I haven't tried it personally though, since it has always worked for me.

---

### Post by el mariachi on 2007-06-29
The funguloids build was updated today! Has anyone tried it? I don't know how to compile that thing:(

---

### Post by el mariachi on 2007-06-29
if anyone does i (or did it) please say it ;)

---

### Post by sad_iq on 2007-07-01
OK...compiled here...finally...works great!!!
 Just had to upgrade Ogre and install libjpeg62-dev and libtiff4-dev. Also it was not a fresh feisty install, and i do compile a lot of stuff usually!!! I'll try on a fresh install as soon as I can!!!

---

### Post by el mariachi on 2007-07-01
> **sad_iq said:**
> OK...compiled here...finally...works great!!!
 Just had to upgrade Ogre and install libjpeg62-dev and libtiff4-dev. Also it was not a fresh feisty install, and i do compile a lot of stuff usually!!! I'll try on a fresh install as soon as I can!!!

Great!! Can't you upload it to somewhere?

---

### Post by sad_iq on 2007-07-02
Ok...bad news...I tried on a fresh install and it (miserably) fails...don't know why :(
 This is the error (more or less) I get when compiling funguloids:
./include/streamplayer.h:69: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../include/streamplayer.h:71: error: ISO C++ prohíbe la declaración de &#8216;SoundStream&#8217; sin tipo
../include/streamplayer.h:71: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[1]: *** [funguloids-ballworm.o] Error 1
make[1]: se sale del directorio `/home/sadiq/test/funguloids/src'
make: *** [all-recursive] Error 1

(sorry for the spanish words...but it was not my system...and it's in spanish)

> **el mariachi said:**
> Great!! Can't you upload it to somewhere?
 Can I do That??? Will all the dependencies be installed on your system(I'm not that guru in compiling stuff)???
 If they will I will compile again using **sudo checkinstall** and upload the deb package somewere or mail it to you..or whatever.
 Also I compiled funguloids without a prefix (./configure --prefix=/usr) and it installed in /usr/local/games so if I did it wrong please correct me for further compiles I do(I really do want to learn this stuff...but I've only started now!!!)

P.S. Also ..sticking to the thread...does **Urban Terror** counts(I think it's open source)????

---

### Post by el mariachi on 2007-07-02
well I haven't done any compiling so I'll just eagerly wait for an answer.
this game sure is hard to get hands on lol

---

### Post by donkyhotay on 2007-07-03
I personally love tremulous, wesnoth & BZflag.

---

### Post by el mariachi on 2007-07-03
what about Warsow? no one plays it?

---

### Post by finferflu on 2007-07-04
I have installed it, but when I try to play, whathever the settings, I get very choppy movements, for example when shooting. It seems my ATI card is not enough for this game. Too bad, since I liked the concept of blending sport with FPS. 
Anyways, I'm *loving* Tremulous, I'm becoming a big fan of this game. It's so simple (in concept, not in gameplay) and so clever.

---

### Post by tretle on 2007-07-10
My current favorites are Warsow and Gridwars 2.

---

### Post by Sindwiller on 2007-07-19
[FreeOrion]("http://freeorion.org/index.php/Main_Page")

[OpenArena]("http://openarena.ws/")

---


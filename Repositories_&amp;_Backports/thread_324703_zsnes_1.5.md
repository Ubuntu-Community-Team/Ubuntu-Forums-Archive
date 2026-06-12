---
title: "zsnes 1.5"
date: 2006-12-24
forum: Repositories &amp; Backports
---

### Post by MadMan2k on 2006-12-24
here you go:
[http://www.madman2k.net/files/zsnes_1.500-0ubuntu1_i386.deb](http://www.madman2k.net/files/zsnes_1.500-0ubuntu1_i386.deb)

---

### Post by adam0509 on 2006-12-25
thank you ! :)

---

### Post by adam0509 on 2006-12-25
seems you compile the file for Edgy, because when I try to install it on dapper I got :

```

$ sudo dpkg -i zsnes_1.500-0ubuntu1_i386.deb
Sélection du paquet zsnes précédemment désélectionné.
(Lecture de la base de données... 73107 fichiers et répertoires déjà installés.)
Dépaquetage de zsnes (à partir de zsnes_1.500-0ubuntu1_i386.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de zsnes :
 zsnes dépend de libc6 (>= 2.4-1) ; cependant :
  La version de libc6 sur le système est 2.3.6-0ubuntu20.
 zsnes dépend de libgcc1 (>= 1:4.1.1-12) ; cependant :
  La version de libgcc1 sur le système est 1:4.0.3-1ubuntu5.
 zsnes dépend de libsdl1.2debian (>= 1.2.10-1) ; cependant :
  La version de libsdl1.2debian sur le système est 1.2.9-0.0ubuntu2.
 zsnes dépend de libstdc++6 (>= 4.1.1-12) ; cependant :
  La version de libstdc++6 sur le système est 4.0.3-1ubuntu5.
dpkg : erreur de traitement de zsnes (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 zsnes
```

How can I co on dapper ? :confused:

---

### Post by MadMan2k on 2006-12-25
yes, its an edgy backport. and since Ive got no dapper system any more I cant backport it for dapper :(

---

### Post by adam0509 on 2006-12-25
**okay, so please if someone here is on a dapper system and making a package for zsnes for dapper drake LTS, please reply thanks**


I think LTS (dapper and future) need to be more considerated in documentation, and normal "stable" version should only be talked when they are out. That's was it annoys me a little when I see hoary, warty, or even breezy (even if still supported) on docs/tutorials...

---

### Post by janfsd on 2006-12-26
> **adam0509 said:**
> **okay, so please if someone here is on a dapper system and making a package for zsnes for dapper drake LTS, please reply thanks**


I think LTS (dapper and future) need to be more considerated in documentation, and normal "stable" version should only be talked when they are out. That's was it annoys me a little when I see hoary, warty, or even breezy (even if still supported) on docs/tutorials...

Well, you can get some binaries at [http://board.zsnes.com/phpBB2/viewtopic.php?t=9179](http://board.zsnes.com/phpBB2/viewtopic.php?t=9179)
I got it from there and it's working great.

---

### Post by jsully1 on 2006-12-26
A lot of us are having sound issues with Edgy - anyone here having any luck?

---

### Post by adam0509 on 2006-12-27
yes, it's a problem on zsnes 1.42 and 1.5 dapper and Edgy as well...


In my opinion, I think it's just some missing packages that Zsnes needs...


EDIT : complain here : [http://board.zsnes.com/phpBB2/viewtopic.php?t=8947](http://board.zsnes.com/phpBB2/viewtopic.php?t=8947)

---

### Post by jsully1 on 2006-12-28
Heh, I'm casualsax3 in that thread - I've been a ZSNES board regular for years, since version .4xx :)

---

### Post by hikaricore on 2006-12-28
thanks of the package :)

---

### Post by adam0509 on 2006-12-30
Zsnes 1.5 for dapper is on french'asher repository :


[http://asher256-repository.tuxfamily.org/](http://asher256-repository.tuxfamily.org/)


Direct link :

[http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/binary-i386/zsnes_1.500-0ubuntu1_i386.deb](http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/binary-i386/zsnes_1.500-0ubuntu1_i386.deb)

:)

---

### Post by Achraf cherti on 2006-12-31
A new release is available in the [repository]("http://asher256-repository.tuxfamily.org") (optimized with --enable-release) :

[zsnes_1.500-0ubuntu2_i386.deb]("http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/binary-i386/zsnes_1.500-0ubuntu2_i386.deb")

---

### Post by adam0509 on 2006-12-31
Ok, for the sound problem, it was in french doc :


"In order not to get crappy sound in zsnes you will need the SDL library with OSS (sorry ^^) &#8594; package "libsdl1.2debian-oss" with synaptic/apt-get. If needeed, kill ESD :

```

$ sudo killall esd

```

You **may** need to go to "System>Preferences>Multimedia outputchooser (or sth like that) and choose OSS"


good game !

---

### Post by msak007 on 2006-12-31
Thanks for the updated package and the link to the ZSNES forums. My problem wasn't that I had crackling sounds, it's that I had no sound at all and kept getting the error (in the terminal) "Sound init failed" whenever launching ZSNES. Everything I found kept indicating that it was due to another app using sound and that I need to kill esd, kill this, kill that, but nothing worked. Finally, based on the recommendation in the forum, I installed **libsdl1.2debian-all** (instead of just libsdl1.2debian-oss) and now sound works perfectly. Interestingly, I already had libsdl1.2debian-alsa installed, but the -all package conflicts with it for some reason and removed it. Oh well, at least it works. Thanks again.

EDIT: I guess the fix *was ***libsdl1.2debian-oss** after all. I thought that the -all package installed all of the SDL packages, but they all conflict with each other. It made the sound in Firefox freeze / loop whenever there was Flash. -alsa fixed this, but then zsnes wouldn't work again. So I installed -oss and now they both work.

---

### Post by nethyun9 on 2007-01-03
Thank you msak007!
Finally I solve sound problem.
Let's enjoy ZSNES. :)

---

### Post by pagefault on 2007-01-10
We will be releasing 1.51 soon with libao support for people with sound issues.

What is holding us back from a true 64-bit release is the lack of an assembler that does what we want and does 64-bit.

---

### Post by msak007 on 2007-01-10
> **pagefault said:**
> We will be releasing 1.51 soon with libao support for people with sound issues.
You mean the sound issues with not having the right version of libsdl installed? I thought I fixed my issue, but I had to install libsdl1.2debian-alsa again and get rid of libsdl1.2debian-oss because Firefox started having the same looping sound issues with Flash again. I installed the newest update to the Flash beta, and that fixed the looping, but sound kept hanging and freezing every couple of seconds then going again. This was very annoying to say the least (all games and videos froze with the sound for approximately a second), but now I don't have sound in zsnes again.

---

### Post by amano on 2007-01-28
[http://www.zsnes.com/index.php?page=news](http://www.zsnes.com/index.php?page=news)

The bug fix release 1.51 is out now ;)

---

### Post by cyberlion on 2007-01-28
> **amano said:**
> [http://www.zsnes.com/index.php?page=news](http://www.zsnes.com/index.php?page=news)

The bug fix release 1.51 is out now ;)

And I'm waiting the debian package.:D

---

### Post by KStorm on 2007-01-28
Thanks for the package - installs and runs flawlessly in Edgy, except you have to create a menu entry (the icon is in the /usr/share/pixmaps folder).  Thanks much!

---

### Post by MadMan2k on 2007-01-28
> **cyberlion said:**
> And I'm waiting the debian package.:D
I can give you the one for feisty. installs the .desktop file too now.

[http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb](http://www.madman2k.net/files/zsnes_1.510-0ubuntu1_i386.deb)

---

### Post by cyberlion on 2007-01-28
Tank's! :D:D
But I use the Dapper version...
And for the Dapper, you have a package?

---

### Post by janfsd on 2007-01-28
> **cyberlion said:**
> Tank's! :D:D
But I use the Dapper version...
And for the Dapper, you have a package?

You can just use the binary, no need for a deb package, btw there is a new version: 1.51, you can find the binaries at [http://board.zsnes.com/phpBB2/viewtopic.php?t=9465](http://board.zsnes.com/phpBB2/viewtopic.php?t=9465)

---

### Post by cyberlion on 2007-01-28
Tank's... but this versions working in my computer (Celeron 2.6) with the CPU in 100%... resulting in crashes in the system...

Any sugestion?!

---

### Post by janfsd on 2007-01-28
Did this happen with the 1.5 version too?

---

### Post by cyberlion on 2007-01-28
Yes! In the version 1.4, 1.5 and 1.51... in all version the CPU work in 100%

---

### Post by amano on 2007-01-28
Well. It works fine for me on edgy though. Sometimes the sound is crackling.

If you want to use the new NTSC filter, you have to use a graphics mode without an "O" mode.
In the new filter tab that is displayed then, you can choose one of 4 profiles to determine "how crappy" the TV shall look ;)

The "most authentic" I got it to look was 512 x 448 DRF and choosing the "S-Video" Profile (on my european PAL TV the TV effects were certainly not so strong like in the "Composite" profile).

---

### Post by janfsd on 2007-01-28
> **amano said:**
> Well. It works fine for me on edgy though. Sometimes the sound is crackling.

With the newest version (1.51) using libao instead of sdl helps with the sound problem. Just run zsnes like this:
```
zsnes -ad oss
``` 
There are more options, but this works for me the best.

---

### Post by amano on 2007-01-28
Hmm. I will give that a try.

I have got an Athlon 1400. And using the NTSC filter is really resource intensive. So this might be the reason as well.


EDIT: Nope. I have got the sound runnung now perfectly with your suggestion. Thanks a lot. Even if I turn the NTSC filter on (which I shouldn't do, since that cranks up the CPU usage from 10 percent to 100 percent. Thnaks ;)

---

### Post by cyberlion on 2007-01-28
And my problem?
The CPU work in 100% all time.
This is problematic... my sistem restart after one hour of game.

---

### Post by amano on 2007-01-28
@cyberlion:

Hmm. What could it be?

What is your graphics card?
Do you try to use other graphics card drivers (eg. the official binary nvidia drivers?
Did you try to use a lower resolution or another graphics mode?
Did you turn off all graphic filters?
Did you try out the Old GFX Engine?
Did you turn off the sound sound filters?
Or try to lower the sound sampling rate?

Does it happen with any game?
Do other SDL programs work?
Did you upgrade your SDL packages manually?

Just some suggestions ;)

I am here on edgy with the official nvidia drivers for a GeForce 4 Ti 4200 but use the sounddrivers that were installed by default (Creative Soundblaster 5.1. My CPU is an Athlon 1400. When using bilinear filtering and basic sound filters, the CPU uses about 10-20 percent of its power.

Just for the comparison.

---

### Post by janfsd on 2007-01-28
@cyberlion:

Try to run it with zsnes -ad oss option, in that way zsnes won't use SDL at all, and tell us if you get the same problem. 
Zsnes just uses SDL for audio by default, but for graphics it uses opengl, (maybe you got an ati card?)

---

### Post by cyberlion on 2007-01-29
> **amano said:**
> @cyberlion:

Hmm. What could it be?

What is your graphics card?
Do you try to use other graphics card drivers (eg. the official binary nvidia drivers?
Did you try to use a lower resolution or another graphics mode?
Did you turn off all graphic filters?
Did you try out the Old GFX Engine?
Did you turn off the sound sound filters?
Or try to lower the sound sampling rate?

Does it happen with any game?
Do other SDL programs work?
Did you upgrade your SDL packages manually?

Just some suggestions ;)

I am here on edgy with the official nvidia drivers for a GeForce 4 Ti 4200 but use the sounddrivers that were installed by default (Creative Soundblaster 5.1. My CPU is an Athlon 1400. When using bilinear filtering and basic sound filters, the CPU uses about 10-20 percent of its power.

Just for the comparison.

- My video card is a "S3 Inc. VT8375 [ProSavage8 KM266/KL266]" (the result of lspci command)

- I try change the vesa driver, but the problem continues.
- I run the zsnes in all resolutions (without opengl), the problem continues.
- I try disable all graphic filter, the problem continue.
- Try disable sound... the problem continue.
- All games appears the problem.

Now that you it spoke, I perceived that the XMAME (that it is SDL) also presents the same problem… I must install the version of the SDL of the site of the developers?

Thank's for the help!

---

### Post by cyberlion on 2007-01-29
> **janfsd said:**
> @cyberlion:

Try to run it with zsnes -ad oss option, in that way zsnes won't use SDL at all, and tell us if you get the same problem. 
Zsnes just uses SDL for audio by default, but for graphics it uses opengl, (maybe you got an ati card?)

I try it, but this command (zsnes -ad) not run. And regarding opengl, I run the zsnes in the other modes (whithout opengl)... tried until compiling without opengl suport, but the problema continues.

---

### Post by janfsd on 2007-01-29
> **cyberlion said:**
> I try it, but this command (zsnes -ad) not run. And regarding opengl, I run the zsnes in the other modes (whithout opengl)... tried until compiling without opengl suport, but the problema continues.

Well this command just works for the 1.51 version, you mean that zsnes doesn't run at all?

---

### Post by cyberlion on 2007-01-29
Debtor to that they had helped, but I decided the problem&#8230; I reinstalled dbus and now zsnes is working the 30, 40%...

	
it remains to see if it continues restarting the system!

THANK's!!

---

### Post by cor2y on 2007-02-11
hi 1.51 compiles and runs but if i enable --enable-libao (which is installed) i have no audio even if  its just run as "zsnes" with no other arguments.
Without --enable-libao the audio is back but it still crackles and of course without --enable-libao the "zsnes -ad oss" argument is useless.

---

### Post by amano on 2007-02-13
Did you try the binary?

---

### Post by Bagboy23 on 2007-02-15
Does anyone have a deb for 1.51 for edgy?

---

### Post by Kosimo on 2007-08-10
I'm also having audio problems... :(

The command -ad sdl doesnt' works for me :(

Any idea?

---


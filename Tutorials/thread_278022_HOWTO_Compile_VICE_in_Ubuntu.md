---
title: "HOWTO: Compile VICE in Ubuntu"
date: 2006-10-15
forum: Tutorials
---

### Post by K.Mandla on 2006-10-15
[CENTER][COLOR="Red"]**CHICKENHEADS UNITE!**[/COLOR]

**If this picture hits a warm spot in your heart, this howto is for you!**

[IMG]http://img290.imageshack.us/img290/5303/screenshotgianadk6.jpg[/IMG]

**If you think this is the way a computer should look when you turn it on, this howto is for you!**

[IMG]http://img290.imageshack.us/img290/9987/screenshotstartupjg6.jpg[/IMG]

**If this was the first program you ever wrote, this howto is for you!**

[IMG]http://img290.imageshack.us/img290/3483/screenshothelloxk7.jpg[/IMG][/center]

That's right, friends and neighbors. It's time to stop *fragging* and start *playing*. This howto will walk you through compiling VICE -- the Versatile Commodore Emulator -- in current Ubuntu releases. An hour from now, you'll be playing all the old classics, just like you used to in the good old days. Best of all, you can cut load times, bump up the speed and add gobs of memory at no cost. It's the dream C64 you always wanted!

If you want more information about VICE, how it works or how to contribute, start [here]("http://vice-emu.sourceforge.net/"). VICE isn't anything new -- C64 emulators on the whole have been around for about a decade or more, in varying forms. VICE is just one of the oldest and well-established.

By the way, you're not limited to the glory days of the C64. VICE includes emulators for the VIC-20, the C128 and a variety of other Commodore-era hardware. It's like having an entire computer museum at your disposal!

This howto has been tested on 
[LIST]
[*]a squeaky-clean Dapper Xubuntu installation on a dual Xeon 2.8Ghz machine, 
[*]a multitude of Ubuntu installations as far back as 6.06., and all the way to the current release, all on a 1Ghz Pentium III Dell Inspiron 8000,
[*]a 32-bit Ubuntu 8.04 installation on a 2.0Ghz AMD64 machine, and
[*]a cluttered Edgy Openbox 3.3.1 install on a 1Ghz Pentium III Dell Optiplex.
[/LIST] 
It worked perfectly each time, and with some luck it might work on other architectures (I don't have the hardware to be sure; reply here if it works for you, or even if it doesn't).

(A side note: I tried compiling this from the Xubuntu 7.04 live CD once, and while it *probably* would have worked fine, I ran out of memory before I could complete *checkinstall*. If you have more than 512Mb in your machine, you might be able to compile and run VICE from a live CD. I don't know why I mention that, except to suggest that it could possibly be done.)

I should note that there are VICE packages in the repositories; click [here]("http://packages.ubuntu.com/vice") for a list of each version available to each release. But for copyright reasons, they're supplied without the kernel ROMs, which means you'll have to find them, download them and install them from elsewhere. Without those ROMs, the VICE emulators don't work. If you decide to try it anyway, take a look at the readme files that are installed in /usr/lib/vice/docs when you install the VICE package. The ROMs are out there, but the legwork and experimentation is up to you. In the end, it might be easier to just compile. ;)

(Note: This howto was originally written for version 1.20, but newer versions have since been released. Where you see 1.20 in this howto, please substitute the new version number.)

**What you'll need**

An Internet connection
The [latest source version]("http://vice-emu.sourceforge.net/#download") of VICE
The *build-essential* and *libxaw7-dev* packages

[COLOR="Red"]**Quick and dirty: For advanced users**[/COLOR]

[LIST]
[*]Update and upgrade, if you want
[*]Download VICE tarball; extract
[*]Install *build-essential* and *libxaw7-dev*
[*]Configure, make, make install (or checkinstall)
[/LIST]
[COLOR="Red"]**Step-by-step: For beginners**[/COLOR]

**1. Download some stuff**

[INDENT]There are three things that you'll need before you can get started: The VICE tarball (which is to say, the VICE source code), the *build-essential* package and the *libxaw7-dev* package.

First things first. Go to the VICE home page and download the most recent version.

[http://vice-emu.sourceforge.net/#download](http://vice-emu.sourceforge.net/#download)

Download the "source distribution" to your computer -- the one at the top of the list. Don't try the other releases; they're for other operating systems and other architectures.

When it's downloaded, open a terminal window. Type this command in the box:

```
sudo aptitude install build-essential libxaw7-dev
```
That will install the packages you need to compile VICE. The download can take a little while; it's about 15Mb or so (I forget exactly). If you don't get all the packages, or if you skip this step, you end up with errors when you try to compile VICE.[/INDENT]

**2. Extract the tarball**

[INDENT]Now navigate to the VICE source package you downloaded. Then type in this command:

```
tar -xvf vice*
```
If you want, you can add *-C directory-where-you-want-to-install-vice*. For example, I like to put all my games into a folder called (of all things) "games" inside my home directory. For me, the command is *tar -xvf vice* -C ~/games*.

You can also open XArchiver and extract it that way. ;)[/INDENT]

**3. Compile**

[INDENT]Next, navigate your terminal window into the VICE folder. The next three steps are short commands that take a long time.

```
./configure
```
Now wait. A bunch of stuff will stream by. This took me about four or five minutes on a 1Ghz machine. 

As a side note, it's worth checking the configure options, because they may or may not be useful to you. Try *.configure --help | less* and see what applies. Some experimentation has given me this, which I find is best for my hardware. If you're new to compiling programs, you should probably stick with the plain *./configure* command.

```
./configure --disable-realdevice --enable-ethernet --disable-ipv6 --enable-fullscreen --without-esd --without-oss --without-resid --with-x
```
The next step is the actual compilation. 

```
make
```
Now wait. More stuff will stream by. This took close to 10 minutes on a 1Ghz machine.

Finally,

```
sudo make install
```
Wait one more time. More stuff will stream by. This took about seven or eight minutes on a 1Ghz machine. We need the *sudo* command here because it's going to put the final VICE commands in /usr/bin and other directories outside your home folder. For that, we need permission.[/INDENT]

**4. Uninstallation**

[INDENT]To remove VICE, return to the directory where you compiled it and give make the uninstall command.
```
sudo make uninstall
```
Again you need *sudo* there, because it will remove things from directories elsewhere on the system.[/INDENT]

**The End**

[COLOR="Red"]**Optional Director's Cut Ending ;) **[/COLOR]

[INDENT]As lukew suggested below, it might be preferable to use *checkinstall* over the final step listed above -- *sudo make install*. The benefit is that checkinstall creates a .deb package, which makes it easier to get rid of VICE if you decide 1980s-era computing wasn't as great as it was cracked up to be, or if something goes wrong and you just want to try it over again.

checkinstall is in the universe repository, so you'll have to make sure you have that repository [enabled]("https://help.ubuntu.com/community/Repositories"). Install it with this command, which you can combine with the installation command listed above, in step 1.

```
sudo aptitude install checkinstall
```
When you reach the last command listed above -- *sudo make install* -- use *checkinstall* instead.

```
sudo checkinstall
```
The first thing checkinstall will want to know is if you want a default set of package docs.

> **checkinstall]The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:[/quote]
 I answer yes. I see no harm in it.

Next, checkinstall will ask for a description of the package. 

[quote=checkinstall]Please write a description for the package.
End your description with an empty line or EOF.
>>[/quote]
You can fill that with whatever you like said:**
> *****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ kmandla@cc99p01 ]
1 -  Summary: [ VICE Versatile Commodore Emulator v1.20 ]
2 -  Name:    [ vice ]
3 -  Version: [ 1.20 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ vice-1.20 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:
You can modify those if you like; I just use the defaults.

The next step takes a while and a lot of messages will spin by. If all goes well (and it should), the next message will be this one, or one like it:

[quote=checkinstall]**********************************************************************

 Done. The new package has been installed and saved to

 /home/kmandla/downloads/vice-1.20/vice_1.20-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r vice

********************************************************************** [/quote]
Checkinstall has finished its work and left you with a .deb file, and installed it for you. If you decide in the future to dump VICE, you can uninstall it with the command you see above -- with a slight addition.

```
sudo dpkg -r vice
```
It's worth noting that if you don't use *checkinstall* with *sudo*, the package creation will continue, but the installation will fail. In that case you can still install VICE with ```
sudo dpkg -i vice*.deb
```or by double-clicking on the .deb file. (I used the splat there in case the version number changes, or you're using a different architecture.)[/INDENT]

**And that's about it.** Unless you ran into compiling errors, you should be able to enter *x64* into a terminal window and the VICE C64 emulator will spring into view, like a ninja!

[CENTER][[IMG]http://img290.imageshack.us/img290/9326/screenshothireskb0.th.jpg[/IMG]](http://img290.imageshack.us/my.php?image=screenshothireskb0.jpg)[/CENTER]

If you're more interested in the other emulators, take a glance back at the [VICE home page]("http://vice-emu.sourceforge.net/") to see which machines are represented, and how to invoke them.

As far as getting games or programs or old disk images, you're on your own. A quick Google search will no doubt turn up hundreds of thousands of pages offering games from 20 and 25 years ago. But since most of that material is still copyrighted, it's not included in this howto.

[COLOR="Red"]**Have fun! **[/COLOR]
[B]
P.S.: [/B]If you really want to wallow in the nostalgia, take a spin past [Bo Zimmerman's fantastic Web pages]("http://zimmers.net/index.html") dedicated to the No. 1 home computer of 25 years ago.

[SIZE="1"]**Thread history:**

[INDENT]Edited, 06/10/15: I double-checked, and both *build-essential* and *libxaw7-dev* are within the main repositories, so I removed the part about enabling multiverse and universe. :D

Edited, 06/12/22: I added the checkinstall method at the suggestion of lukew ... which is really a better way to do it.

Edited, 07/03/17: VICE is at 1.21 now, and Feisty has 1.20 in the repos. Version 1.21 compiles in the same way as the previous version.

Edited, 07/04/13: The VICE source code needs a very easy edit to get it to work under the new libx11 packages. I added a link to [Compyx's post]("http://ubuntuforums.org/showthread.php?p=2427105#post2427105"), which explains the what-where-when-why-how of getting a happy ending.

Edited, 07/08/16: VICE has updated to 1.22, which fixes the aforementioned incompatibility with libx11. I've removed notes in the howto that talk about editing the source code, since that's no longer necessary.

Edited, 07/10/26: The tutorial works for 1.22 under Gutsy, so I've edited it to reflect that.

Edited, 08/01/25: I added notes about uninstalling VICE with *make*.

Edited, 08/04/29: The tutorial works for 1.22 under Hardy now.

Edited, 08/07/29: Version 2.0 of VICE worked for me under 8.04.

Edited, 08/11/03: The instructions work for version 2.0 of VICE in Ubuntu 8.10.

Edited, 08/12/25: Updated to the Sourceforge web site, and for the 2.1 release.

Edited, 09/04/30: The tutorial works fine under Ubuntu 9.04, with or without the Gnome UI.

Edited, 09/12/31: Updated to Ubuntu 9.10 with version 2.2, and all is working as expected.

Edited, 10/05/13: Updated to Ubuntu 10.04 with the short fix described [here]("http://ubuntuforums.org/showthread.php?p=9253413#post9253413"), but otherwise requires nothing different for version 2.2.

Edited, 10/11/04: Updated to Ubuntu 10.10. The fix mentioned for 10.04 is still needed for 10.10. And occasionally, checkinstall will finish with errors. If that is the case, stay with *sudo make install*.[/INDENT][/SIZE]

---

### Post by rcmiv on 2006-10-24
Nicely done.

Thanks!

-rcmiv

---

### Post by dualtone on 2006-10-31
[B]HELP!!!!:--
[/B]
matthew@Bob3:~/Downloads/vice-1.20$ x64
*** VICE Version 1.19 ***
 
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
X11: Found 24bit/TrueColor visual.
X11: Using private colormap.
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...

---

### Post by K.Mandla on 2006-11-01
Do you have the VICE package from the repositories installed? It looks like you're starting up version 1.19 when you give the x64 command.

Try

```
sudo aptitude remove --purge vice
```
to get rid of 1.19, then you'll probably have to recompile 1.20. Let us know how it goes. :-D

---

### Post by dualtone on 2006-11-01
That did it! Thank you!!! :-)

---

### Post by lazyart on 2006-11-02
SWEEEEEEEEET!  I can play those games I wrote for Compute!'s Gazette all over again! :D

---

### Post by BoyOfDestiny on 2006-11-05
Cool. I compiled vice 1.20 a little while ago, turns out it has a gnome ui if you'd rather use that than xaw.

to see the options
./configure --help

for gnome ui
./configure --enable-gnomeui

[[IMG]http://img170.imageshack.us/img170/9527/ubuntuc64zn1.th.png[/IMG]](http://img170.imageshack.us/my.php?image=ubuntuc64zn1.png)

P.S. The double size thing is an option in ~/.vice/vicerc. Also, audacious has a great sid player (ported from xmms.) Just thought I'd plug my favorite player, since it handles more than mp3 and oggs :)

---

### Post by McQuaid on 2006-11-05
Does this emulator have a good fullscreen support yet?  I remember trying it a couple of years back and it had dga and x11 modes, but it was difficult getting to to stretch, they definitely weren't using hardware overlay. 

Has it got any better?  I checked frodo's site and they announced an sdl version but I think development has ceased.

---

### Post by sphere02 on 2006-11-05
how to start with gnome-ui??

---

### Post by K.Mandla on 2006-11-09
> **sphere02 said:**
> how to start with gnome-ui??
You might have to compile it with the gnomeui option to start up with that UI.

I tried it with the --with-xaw3d UI option, and it's kind of clunky when compared to the standard libxaw7-dev interface. You need the xaw3dg-dev package for that, if you want to try it -- not the libxaw7-dev one.

---

### Post by gendel on 2006-12-07
oh my god, thank you! have some unfinished bussiness with turrican ;)

---

### Post by gorkur on 2006-12-11
Nice howto :)

There's just one thing bugging me. Is there no way to get it to work fullscreen?

---

### Post by K.Mandla on 2006-12-13
I'll have to check up on that. I don't believe it will jump to true fullscreen, but I haven't really tried. You might look over the VICE home page and see if it's mentioned in their documentation.

---

### Post by Steve Grace on 2006-12-17
Thank you very much for this information! I compiled and installed VICE 1.20 with no problems. :-D 

I'm using Ubuntu (GNOME), so I used ./configure --enable-gnomeui as listed above.

At first, I had issues with sound -- the sound wasn't keeping up and seemed to be missing voices. I fixed that by changing two settings on the Settings>Sound settings menu:

Sound device name: esd
Suspend time: 1 sec suspend

I left all other sound settings at their default values. These changes seem to have fixed the problem!

---

### Post by K.Mandla on 2006-12-18
Cool! I'm glad you liked it. I have had some problems with sound emulation too, and they seemed linked to the speed of the processor, curiously.

I don't remember enough to say exactly what settings I changed, but I think yours will probably do the trick. Thanks!

---

### Post by lukew on 2006-12-21
May I add that it emulates the whole peripheral of Comodores including the the C16/Plus 4 emulator as well!!!

Going to go back and play Treasure Island and Fire Ant!!

Also ......


```

./configure
make 
checkinstall
```


Also .... initally after installing the deb package i tried to run and got a can not find /user*** (cant quite remember ). I uninstalled. When I tried installing again it worked. Not sure if a reboot / reinstall worked but thought it was worth my two pence.

Also .... I could not get this to compiler with gnonme gui. 

Thanks

Luke

---

### Post by lukew on 2006-12-21
Anyone ran xplus4?

Everything works ok but i have to press the buttons several times to move. For example to move right in have to press the right key tonnes of times. Everything works ok in x64....


Thanks

Luke

---

### Post by lukew on 2006-12-21
> **lukew said:**
> Anyone ran xplus4?

Everything works ok but i have to press the buttons several times to move. For example to move right in have to press the right key tonnes of times. Everything works ok in x64....


Thanks

Luke


Hay if you use the custerom keys everything is ok.
[HTML]
wersdfxcv[/HTML]

---

### Post by K.Mandla on 2006-12-21
> **lukew said:**
> May I add that it emulates the whole peripheral of Comodores including the the C16/Plus 4 emulator as well!!!
You're right! I forgot to mention that. So all you VIC-20 and C-128 fans can join in the fun. :D

> **lukew said:**
> 
Also ......
```

./configure
make 
checkinstall
```

That's actually a really good idea. When I first wrote the howto I thought I should stick to configure-make-sudo make install because it might seem familiar to someone who was new to Linux. But to be honest, I think checkinstall is a better way of doing things. Thanks! :mrgreen:

---

### Post by lukew on 2006-12-22
> **K.Mandla said:**
> You're right! I forgot to mention that. So all you VIC-20 and C-128 fans can join in the fun. :D


That's actually a really good idea. When I first wrote the howto I thought I should stick to configure-make-sudo make install because it might seem familiar to someone who was new to Linux. But to be honest, I think checkinstall is a better way of doing things. Thanks! :mrgreen:

No Probs!!

Trying to find a way to reconfiogure the keys so I can use my X-Arcade Joystics!!

Any ideas anyone? I did the key dump but that did not produce anything intuitive. Think I might have to go and Read The Functional Manual.....

Luke

---

### Post by K.Mandla on 2006-12-22
I've added the checkinstall method, which lukew suggested, and I prefer really. Cheers! :KS

---

### Post by samwyse on 2007-02-04
Any idea how to get it compile with --enable-ffmpeg?

It says:
```
checking ffmpeg/avformat.h usability... no
checking ffmpeg/avformat.h presence... no
checking for ffmpeg/avformat.h... no
```
So I guess I'm missing something.

---

### Post by ice60 on 2007-02-04
wow, that's so cool 8) that was the first program i ever wrote, and i haven't really advanced much since :(  maybe nowadays i'd add an ; at the end of line 10 to make the whole screen fill up lol

i'm going to try it out thanks :lolflag:

---

### Post by K.Mandla on 2007-02-07
> **samwyse said:**
> Any idea how to get it compile with --enable-ffmpeg?

It says:
```
checking ffmpeg/avformat.h usability... no
checking ffmpeg/avformat.h presence... no
checking for ffmpeg/avformat.h... no
```
So I guess I'm missing something.
No guarantees, but I'm thinking maybe there are ffmpeg development packages that you'll need to install before you compile it for ffmpeg support. Strangely enough, the [package search page]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ffmpeg&searchon=names&subword=1&version=edgy&release=all") isn't much help this time.

---

### Post by samwyse on 2007-02-07
There's no ffmpeg-dev package in the repos, I guess I have compile it too.

---

### Post by K.Mandla on 2007-02-07
The Vice page links to this one for Linux ffmpeg support.

[http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)

I'm in uncharted territory with that one, though. Let us know how it goes.

---

### Post by lukew on 2007-02-09
Has anyone managed to get this working in Edgy?

K.Mandla I know changed your post to say it works in Edgy but every time I do the "make" my machine completey locks up!

Has anyone got a deb file they could share? I would much apreciated it.

Thanks.

Luke

---

### Post by K.Mandla on 2007-02-10
Yup, works great in Edgy. Or did you mean Feisty?

---

### Post by lukew on 2007-02-13
Hi,

I can not compile it, mu machine locks up. If I remember rightly i strugled under dapper as well. I stupidly did not keep the deb file. Could someone please post one?

Thanks

Luke

---

### Post by Robin T Cox on 2007-02-13
You can set the emulator window to double size, which is approx (as I recall) the size of a C64 screen.

See:
[http://www.viceteam.org/vice_6.html#SEC45](http://www.viceteam.org/vice_6.html#SEC45)

---

### Post by lukew on 2007-02-15
Hi,

I have managed to compile this on my dads machine. Not sure why mine was locking up! Learnt my lesson and kept the deb file this time!!

Luke

---

### Post by K.Mandla on 2007-02-16
Cool. Strange that it was locking up, though. ...

---

### Post by lukew on 2007-02-17
> **K.Mandla said:**
> Cool. Strange that it was locking up, though. ...

If I remember rightly it locked up doing this under dapper as well.....

I think I might have used:

```
./configure --bindir=/usr/bin

```

Who knows.....

Luke

---

### Post by K.Mandla on 2007-03-17
About a week ago the [VICE]("http://www.viceteam.org/") team released version 1.21, and judging by the [changelog]("http://www.viceteam.org/plain/NEWS") there are a lot of new tweaks, not least of them being "fullscreen mode based on XRandR."

I haven't had a chance to recompile it yet, but I should have time within the next few days.

It's also worth noting that Feisty has [1.20]("http://packages.ubuntu.com/feisty/otherosfs/vice") in the repos, but I don't think 1.21 will make it in time for the full release next month.

Edit, 07/03/20: VICE 1.21 compiles on Edgy in the exact same way as the howto describes. So there haven't been any changes to the instructions. ;)

[CENTER][[img]http://xs413.xs.to/xs413/07123/2007-03-20-215445_388x383_scrot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs413&d=07123&f=2007-03-20-215445_388x383_scrot.png)[/CENTER]

Have fun!

---

### Post by eddie303 on 2007-04-05
I have a huge problem. I managed to compile and install, and tried the stock version before, but I get no screen image, only a black window, and the message: XCreateImage failed. I have an on-board Intel 910GM video card, and I have got this problem with uae too. Somebody can help me?

---

### Post by Compyx on 2007-04-06
I have a similar problem, it looks like yesterdays update of xorg-server borked Vice somehow. I also get the 'XCreateImage failed' message when running x64. Both the binary 1.20 package and 1.19, 1.20 and 1.21 built from source have this problem.
Hopefully another update of xorg-server will fix this...

---

### Post by eddie303 on 2007-04-06
> **Compyx said:**
> I have a similar problem, it looks like yesterdays update of xorg-server borked Vice somehow. I also get the 'XCreateImage failed' message when running x64. Both the binary 1.20 package and 1.19, 1.20 and 1.21 built from source have this problem.
Hopefully another update of xorg-server will fix this...

Nice, maybe if we are more with the problem, the chance is bigger to be solved. Interesting enough, Frodo works, but I don't really like it.

---

### Post by Flutterby on 2007-04-07
I have the same problem as the previous two posters.... help?

---

### Post by Sir Nose on 2007-04-09
Same problem here.

---

### Post by Sir Nose on 2007-04-09
Also, it might be useful to include some optimizations as VICE is one of the more cpu-intensive programs.

CFLAGS="-march=i686 -O5 -DNO_REGPARM" ./configure

---

### Post by K.Mandla on 2007-04-09
Sorry I haven't been able to look at this lately; I'm going to try it in the next few hours and see if I get the same errors.

---

### Post by K.Mandla on 2007-04-09
> **Sir Nose said:**
> Also, it might be useful to include some optimizations as VICE is one of the more cpu-intensive programs.

CFLAGS="-march=i686 -O5 -DNO_REGPARM" ./configure
Good idea. If you're using another architecture than an i686, you might want to look up the CFLAGS that are appropriate for your CPU.

[http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)

If you're not sure what CPU you use, you could try 

```
cat /proc/cpuinfo
```

I believe the "model name" category will give you the processor you're using, and you can use CFLAGS that are specific to your chip.

---

### Post by K.Mandla on 2007-04-09
I'm getting the same errors in Feisty with version 1.21, and in Feisty with a deb built under Edgy.

As best I can tell, libx11 is what causes the VICE package to break.

[http://www.nabble.com/Bug-418295%3A-vice-broken-by-libx11-security-update-p9896114.html](http://www.nabble.com/Bug-418295%3A-vice-broken-by-libx11-security-update-p9896114.html)

It looks like a patch is suggested there, but I won't get a chance to try it for a week or so. If anyone can try it and tell us if it works, it would be greatly appreciated.

---

### Post by Compyx on 2007-04-09
Tried the patch, well, that is, I altered the offending lines in the source of VICE 1.21 and x64 is running a Horizon demo right now :)

What you need to change is this:

In  line 123/124 of src/arch/unix/x11/xaw/uicolor.c:
```
    im = XCreateImage(display, visual, x11ui_get_display_depth(),
                      ZPixmap, 0, (char *)data, 1, 1, 8, **1**);
```
change this to:
```
    im = XCreateImage(display, visual, x11ui_get_display_depth(),
                      ZPixmap, 0, (char *)data, 1, 1, 8, **0**);
```

These same goes for line 167-169 in src/arch/unix/x11/gnome/uicolor.c, when compiling with --enable-gnomeui:
```
    im = XCreateImage(display, GDK_VISUAL_XVISUAL(visual),
                      x11ui_get_display_depth(),
                      ZPixmap, 0, (char *)data, 1, 1, 8, **1**);
```
change to:
```
    im = XCreateImage(display, GDK_VISUAL_XVISUAL(visual),
                      x11ui_get_display_depth(),
                      ZPixmap, 0, (char *)data, 1, 1, 8, **0**);
```


I had already noticed that these lines where causing the error, but didn't know how to deal with it, since I've never used X11 libraries in my code.

Now I can finally watch the Breakpoint 2007 entries, hooray!!
(I considered switching back to Gentoo because of this... I'm a C64-addict, I know :D)

---

### Post by eddie303 on 2007-04-09
> **Compyx said:**
> 
Now I can finally watch the Breakpoint 2007 entries, hooray!!
(I considered switching back to Gentoo because of this... I'm a C64-addict, I know :D)
I'd rather think about getting a real thing. I had some sleepless nights when I was younger playing Int. Karate+. Thanks for the patch, I'll try it right away.

---

### Post by Compyx on 2007-04-09
> **eddie303 said:**
> I'd rather think about getting a real thing. I had some sleepless nights when I was younger playing Int. Karate+. Thanks for the patch, I'll try it right away.

Well, I have 3 C64's, but my floppies and drives are a bit of a mess. And I prefer cross-development over working on the real deal, today's assemblers and editors (vim!) are much better than the old Turbo Assembler ;)

---

### Post by Flutterby on 2007-04-11
Compyx, first of all, thanks for the patch.  It works for me... once.

The first time after using it and running X64, things worked fine.  However now on subsequent starts, I do not get a C64 screen at all; just the menu bar and the bottom line (with the fps info and such) right below it. Not even apt-get remove --purge and a reinstall (from the home-made package ) helps.

The no-screen-at-all thing on subsequent starts also happened before I used Compyx's patch, BTW.

...help please?

---

### Post by Compyx on 2007-04-13
First of all, it's not my patch, the patch was mentioned by K. Mandla., I just showed how to apply the patch with a text-editor or something similar.

Anyway, this no-screen thing happened to me a lot too, I found that compiz was the cause of this, so if you're running compiz, try disabling compiz and then running x64, maybe that'll help. I'll have to investigate further, and then maybe report a bug.

---

### Post by K.Mandla on 2007-04-14
Thanks, people. I tacked on a little warning to the OP, and linked to Compyx's instructions. Cheers.

---

### Post by Christian Johansson on 2007-05-01
I also got the black screen problem after an X11 update. I had installed VICE 1.19 from the repositories and manually downloaded and copied the ROM files to the correct place. Hmmm, it looks a bit complicated to compile yourself. Can't somebody do a compilation and put the .deb file somewhere instead so we can download and install or doesn't it work to do it that easy?

---

### Post by Christian Johansson on 2007-05-01
Does anyone btw know exactly which X11 security updates that caused the problem? I have identified that libx11-6 and libx11-data were updated but I'm a bit uncertain if more was updated as well. I'm asking this because I thought I could perhaps do "Force version" in Synaptic to go back to the previous version. That seems easy to do (but risky perhaps).

---

### Post by Christian Johansson on 2007-05-01
Sorry to spam this thread. I just saw in [https://bugs.launchpad.net/debian/+source/libx11/+bug/107732](https://bugs.launchpad.net/debian/+source/libx11/+bug/107732) that the same X11 security update also causes problems to start Opera and the writer writes there that he has successfully downgraded libx11-6 and then it worked to start Opera. I think I will try that too and hopefully VICE will start correctly as well.

---

### Post by K.Mandla on 2007-05-03
Did you see [Compyx's fix]("http://ubuntuforums.org/showpost.php?p=2427105&postcount=44")? It's a one-letter change and is very easy to do. That might work better than trying to force a downgrade, since this method is for compiling the source anyway.

---

### Post by OU812 on 2007-06-30
Thanks for the how-tos on getting vice to work on debian machines (I always wondered why I couldn't get it to work). However, I am still struggling with the directions in the patch: I cannot find

> In line 123/124 of src/arch/unix/x11/xaw/uicolor.c:

this file. I am runnnig xubuntu and I don't have a search feature. Thanks.

john

EDIT
The directions confused me. The file is in the tar ball and needs to be modified prior to installing. My bad.

---

### Post by gorkur on 2007-07-09
I'm wondering, how can I uninstall vice if I followed these steps while compiling:

```
./configure
make
sudo make install
```

I'm getting pretty nuts here, being unable to play Turrican on my Linux box, and I have to reinstall Vice using Compyx's fix ;)

---

### Post by whitingx on 2007-07-20
Hello,

I've installed VICE through the repos but am getting the following error when running x64

```

*** VICE Version 1.20 ***

 

Welcome to x64, the free portable C64 Emulator.

 

Current VICE team members:

A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,

M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel.

 

This is free software with ABSOLUTELY NO WARRANTY.

See the "About VICE" command for more info.

 

X11: Found 24bit visual.

DGA2: Found mode:  800x600-0.0Hz, 1

DGA2: Found mode:  640x480-0.0Hz, 2

C64MEM: Error - Couldn't load kernal ROM `kernal'.

Machine initialization failed.



Exiting...

```

I have placed the kernal rom in the correct place as specified here [http://www.viceteam.org/vice_4.html#SEC23]("http://www.viceteam.org/vice_4.html#SEC23") but it is still not working.

Any help you could give or any links to good VICE guides would be greatly appreciated.

Thanks in advance.

---

### Post by mocha on 2007-07-29
For the people that are having problems with black screen output, after starting x64 right click on the black screen, go down to "VIC II settings", select "Hardware scaling".  After that the familiar blue C64 BASIC screen should appear.  After that you can increase the size of the window, scan lines, scaling, etc..  Don't forget to go to "Settings" - "Save settings" before you exit.

I tried this on the version from the Feisty repository, don't know if it works on the latest version.

---

### Post by DCMP on 2007-08-04
Thanks a lot! 

I am actually using Fedora core 5 and had the same error ( XCreateImage failed )  when trying to open Vice while it worked perfectly for months.

 I tried compiling vice 1.16 up to 1.21 and none wanted to compile, giving a video error having to do with missing files. This was odd as I had 1.20 up and that was running fine earlier. I followed the advice for the bugfix ( changing the 1 to a 0) and it still did not want to compile. On David (Tao)'s advice I checked if xaw3d and xaw3d dev were installed. They were not and now the newest version compiled fine.

I hope others will be helped with this information. 

greets

---

### Post by K.Mandla on 2007-08-13
I see that the [Vice team has released 1.22]("http://www.viceteam.org/"), and [among the changes]("http://www.viceteam.org/plain/NEWS") are fullscreen emulation that's supposed to work, and a fix to the annoying black screen quirk.

I'm not running Ubuntu right now (I know, it's blasphemous), but I should get a chance to recompile this within the next few days. More news at 11.

---

### Post by K.Mandla on 2007-08-16
I recompiled 1.22 on a fresh installation of Feisty, and everything works without hand-editing the source code. You can breathe a sigh of relief now. ;)

[CENTER][[img]http://xs318.xs.to/xs318/07334/2007-08-16-155515_1600x1200_scrot.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs318&d=07334&f=2007-08-16-155515_1600x1200_scrot.jpg)[/CENTER]

I'll update the howto and remove parts about editing the source files. Cheers, fellow chickenheads! :mrgreen:

---

### Post by z-vap on 2007-08-24
Hi all 

I got mine to work also.  1-22.  I compiled the regular one and the gnome-ui one.  

But the gnome-ui version won't properly stay at a regular window size... it's always shrunk to the size of a pencil.  I can drag the border of the window to resize it bigger, but that's annoying to do all the time.

Any ideas on a fix for that?

---

### Post by K.Mandla on 2007-08-24
Not sure. I haven't compiled the gnome-ui one, so someone might have to experiment and give an idea.

Is there any kind of VICE configuration file that might hold screen size settings? I'm thinking of something like the .leafpad file that's made by Leafpad, and includes a height and width setting, so it returns to its former size when its restarted. Probably a long shot, but I thought I'd suggest it. :-k

---

### Post by z-vap on 2007-08-24
it must have been a setting in my ~/.vice/vicerc file because I deleted it, and re-installed.  

Now it's okay.

edit: and let me say, I love the gnome-ui version much better than the xaw one.

---

### Post by Kernel_Killer on 2007-09-21
Great post. Unfortunately, I'm going to have to reminisce for a few months I'm sure. Already grabbed The Final Cartridge 3, and TASM. Now if only I had a HardSID..... scrolltext anyone? :-#

I wonder if VICE will ever add Kaillera support......

---

### Post by K.Mandla on 2007-10-25
I'm going to make sure this works on Gutsy tomorrow; I can't imagine why it wouldn't, but it's always good to check. Watch this space. ;)

---

### Post by K.Mandla on 2007-10-25
Looks like 1.22 behaves predictably under Gutsy.

[[img]http://xs320.xs.to/xs320/07434/2007-10-25-234304_1600x1200_scrot.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs320&d=07434&f=2007-10-25-234304_1600x1200_scrot.jpg)

I'll update the original post to include Gutsy. Cheers, fellow chickenheads! :KS

---

### Post by K.Mandla on 2007-11-15
Shameless plug: If you care to, you might set up VICE to run as the sole application on an older system, and camouflage it to look something vaguely like the real thing.

[http://kmandla.wordpress.com/2007/11/15/howto-convert-a-k6-2-into-a-c64/](http://kmandla.wordpress.com/2007/11/15/howto-convert-a-k6-2-into-a-c64/)

Better than tossing a computer in the garbage, anyway. ;)

---

### Post by Hopworks on 2007-11-18
I can't say enough how pleased I am to see those screen shots. I owe thanks to the VIC20, C64 and C128 for my interest in computers today.

So I compiled manually, using the awesome instructions in this thread, but I have one little problem. My keyboard doesn't work in the emulation. It works in my GNOME UI, just not in the emulation. What a let down, I really wanted to start playing around with my old CBM machine. :(
I get the starting screen, and the prompt, blinking, and that's as far as I can go.

Is there something simple I might have overlooked?

Also, and not sure how to fix this, but when I type x64, it's looking for it in /usr/bin when in fact it is in /usr/local/bin. I used checkinstall at the end of the building process as recommended.

Thanks!

Hop

EDIT: Vice 1.22 downloaded source from the recommended site.

---

### Post by K.Mandla on 2007-11-18
Interesting. :-k I've not run into that problem before. There are keyboard settings within VICE; is there any chance you have it set to an unusual setting? Is it an international keyboard?

You might also check the *.configure --help* flags to see if there was something that was omitted by accident when you compiled.

---

### Post by Hopworks on 2007-11-18
> **K.Mandla said:**
> Interesting. :-k I've not run into that problem before. There are keyboard settings within VICE; is there any chance you have it set to an unusual setting? Is it an international keyboard?

You might also check the *.configure --help* flags to see if there was something that was omitted by accident when you compiled.

Well, I thought of that, because I did the recommended line (optional, iffy)```
./configure --disable-realdevice --enable-ethernet --disable-ipv6 --enable-fullscreen --without-esd --without-oss --without-resid --with-x
``` for the ./configure. So, I went and did it again without doing that, but maybe I should have removed everything before I compiled again??

I'm real new to this compiling from scratch, so bare with me. I was just pleased that I got as far as seeing that startup UI screen because I didn't use synaptic or other easy way to it. I'm trying to learn all I can about Linux, specifically Ubuntu. Ubuntu Feisty 7.04 Server has been everything I ever wanted from it, and this was a challenge.

So if you haven't seen that issue before, that doesn't surprise me. Chaulk it up to my bad luck on new experiences. LOL! :)

I know... :-({|=  hehehe
Thanks for your time, and others that made this old dream come back alive for me.

Hop

OH, PS. Is there a thread here where people can post their VIC20/C64/C128 experiences? If not, I'd like to start one. I have many a tale to tell about my work as a kid using those wonderful machines.  AND! What was the name of that apache gunship game? Was it "Apache Gunship"?? That game took up so much of my time, it actually hurt my standings in 'Trade Wars' I use to play on local BBS's, using a home-made modem. LOL

EDIT: My god, I just looked and sure enough, there is a 6510 chip still in my device cabinet. WOW! hehehehe

---

### Post by K.Mandla on 2007-11-19
> **Hopworks said:**
> Well, I thought of that, because I did the recommended line (optional, iffy)```
./configure --disable-realdevice --enable-ethernet --disable-ipv6 --enable-fullscreen --without-esd --without-oss --without-resid --with-x
``` for the ./configure.
Hmm. Maybe I should take that out. It has been working perfectly for me, but I wouldn't want that to be the cause of problems.

> **Hopworks said:**
> So, I went and did it again without doing that, but maybe I should have removed everything before I compiled again??
Yes, you should probably delete the entire folder that you decompressed from the tarball, and uncompress it for a clean start. I know you can also 

```
make clean
```
to start fresh, but I sometimes suspect it's not really "cleaning" up as much as I would want. Start with a fresh folder, and try *./configure* with no flags on it.

> **Hopworks said:**
> Thanks for your time, and others that made this old dream come back alive for me.
No problem! I'm sure once this little problem gets ironed out, it's going to be smooth sailing.

> **Hopworks said:**
> PS. Is there a thread here where people can post their VIC20/C64/C128 experiences? If not, I'd like to start one. 
Not that I've seen, but if you wanted, you could probably start one somewhere. Link to it from here, so people know they can share their war stories there. ... :)

> **Hopworks said:**
> EDIT: My god, I just looked and sure enough, there is a 6510 chip still in my device cabinet. WOW! hehehehe
Lucky you! That might be worth a little money these days. ... :mrgreen:

---

### Post by ice60 on 2007-11-24
thanks for the howto. i used to play pitstop 2, i ownd a copy of it, so i just installed VICE and got pitstop2.t64. is there anywhere on the internet that tells you how to run a t64 file?? i can't find it. 

i can't believe every single person that's ever used VICE just knows how to run it so that's why it doesn't say anything about it on the internet :( when i played it i loaded it on a cassette recorder, but i can't do that with a *.t64

---

### Post by ice60 on 2007-11-24
OMG [img]http://planetsmilies.net/shocked-smiley-9456.gif[/img]

---

### Post by K.Mandla on 2007-11-26
Heh, looks like you got it working.

Tape images should be loadable through the click menu ... I think it's "load a tape image" or something like that.

Usually I try to use disk images; I always, *always* hated that tape drive. :evil:

---

### Post by BigSilly on 2007-11-26
Downloaded this off the repository (ver.1.20-2), but when I type x64 into a terminal I get -

```
Set fontpath: `xset fp+ /usr/lib/vice/fonts'.
*** VICE Version 1.20 ***
 
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
X11: Found 24bit visual.
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...
```

What can I do?

---

### Post by K.Mandla on 2007-11-26
Yes, that error means you haven't got the kernels installed. You have to search the Web for them and put them in the proper directories. I can't help you with that.

On the other hand, you could uninstall the repository version and compile it from the source code, which will solve your problem.

---

### Post by naivri on 2007-12-02
hi guys

firstly, thanks for the guide, the closest I have came to linux is compiling eggdrop bots.... :/

as a proud owner of a ps3 with vice installed on it now, has anyone here got the sound to work on it?  I know the sound works in Ubuntu on the PS3 a it make noises all the time, however, I cant get the sound to work in vice.  If anyone drops by here who does get it to work.....help ?

I <3 my SID chip

---

### Post by K.Mandla on 2007-12-03
Have you tried different sound settings from within VICE? It's possible the program is trying to generate sounds that are unusual for that hardware.

Otherwise, I'm at a loss. I don't know enough about PS3s to make a very good suggestion. :???: Sorry.

---

### Post by naivri on 2007-12-22
got it working

there was an alsa library of some kind missing

I made a post on the psubuntu forums explaining what I did if any PS3 owners come across this post

[http://psubuntu.com/forum/viewtopic.php?t=1740](http://psubuntu.com/forum/viewtopic.php?t=1740)

---

### Post by cncox1991 on 2007-12-28
Thank you so much for the instructions on getting VICE up and running  under Ubuntu.  I only have one issue-- where do you go to configure your keyboard set?  I can't seem to find it under the menu (right or left click mouse).

---

### Post by Frankie6502 on 2007-12-29
Thanks for the info. However I did have some issues running vice on my laptop. 

The problem was mainly with the joystick options, it seemed that you couldn't define your own keyset and I couldn't get the other two  keysets to work. As my laptop doesn't have a number pad I could not use that option either.

The solution I found was to run "./configure --enable-gnomeui" after making and installing there is now the option to define your own keys under Settings>Joystick settings>Define keysets

I hope this helps any laptop users like myself with this or similar problems with the joystick options. :)

---

### Post by K.Mandla on 2007-12-29
That is a bit annoying, isn't it? There used to be a version with customizable keypad controls; perhaps that was a Windows version I used a long time ago, but I know I did it. It would be great to be able to modify those keys again (without relying on the Gnome UI), since the number pad is usually an issue for laptop users.

---

### Post by K.Mandla on 2008-04-29
Version 1.22 is compiling fine for me under 32-bit Ubuntu 8.04 on an AMD64 machine. 

[center][[img]http://xs226.xs.to/xs226/08182/vice-shot844.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs226&d=08182&f=vice-shot844.png)[/center]

I've updated the guide for Hardy. Have fun!

---

### Post by K.Mandla on 2008-07-29
It looks like the 2.0 version of VICE will compile and run normally under Hardy.

[CENTER][attach]79318[/attach][/CENTER]

I've updated the howto to show that. Have fun! :D

P.S.: Don't ask me why my screen is at 800x600. It's been a long afternoon. ...

---

### Post by K.Mandla on 2008-11-02
I built the 2.0 version of VICE under Ubuntu 8.10 and it's working fine. Which means this thread is now two years old and still works great! :D

---

### Post by m2.g5ru6y7s on 2008-11-09
Thanks for sharing this info :). I nearly opened a new thread for compiling under 8.10.
:guitar:

---

### Post by billc123 on 2008-11-18
hi - thanks for the instrctions. 
I just installed vice 2.0 on ubuntu 8.10  (which worked great using your instructions)

I just wondered about that full screen thing though. I see a double screen, but not sure about a full screen...

---

### Post by K.Mandla on 2008-12-14
Oh darn, I can't remember off-hand how to get the full screen going. It's an option under one of the display submenus ... I can remember seeing xrandr and another option. ... #-o

Give me a day and I think I can get an answer for you.

---

### Post by kosmo on 2008-12-20
Since VICE 2.1 is released, if you use Ubuntu 8.04 or 8.10 you can check my PPA for 2.1 debs;). I would like to hear some feedback from users, so i could try to make debs better for wide-spread usefullness (if they not good enough already).

 [https://launchpad.net/~smoki00790/+archive](https://launchpad.net/~smoki00790/+archive)

 NOTE: All roms are mangled from original source, so neither .orig source nor debs packages include any of it!

---

### Post by K.Mandla on 2008-12-21
VICE 2.1? The home page still only shows 2.0. :???:

Or did you mean "when" it's released?

Edit: Ah, never mind. I see that it's been released, but the home page is late in being updated.

---

### Post by kosmo on 2008-12-21
Probably you check this on old link [http://www.viceteam.org/](http://www.viceteam.org/) , but new link we should use is [http://vice-emu.sourceforge.net/](http://vice-emu.sourceforge.net/) .

---

### Post by billc123 on 2008-12-22
i noticed the changelog says...

"- XRandR fullscreen implemented"

has anyone been able to get fullscreen with 2.1?

---

### Post by kosmo on 2008-12-22
As i know, xrander is implemented as of 2.0, but now that is official and works better. To go to fullscreen (i can go:)), example for C64: just first checked Settings>VIC-II settings>Hardware Scaling. For this to work, 'gtk2' version must be compiled with gtkglext also and you must have working OpenGL or Mesa driver. If you you use 'xaw' version, also make sure to have Hardware scaling checked. For this older gui you don't need OpenGL, but you need good and working Xv (also must be compiled with) in your DDX driver. In both ways graphics driver must be correct.

 You can try debs from my PPA, if you want to check gtk2 version. (i will add ffmpeg support today, but not for mp3 capture, because liblame0 is not in Ubuntu official repos for Intrepid and for Hardy, ffmpeg is not even compiled with mp3 support for video.).

 P.S. Right now i added ffmpeg support for intrepid and hardy packages (without mp3, sorry:().

---

### Post by billc123 on 2008-12-23
ok, I must be doing something wrong then because I don't see "Hardware scaling" under vic II settings.
screenshot attached.

---

### Post by kosmo on 2008-12-23
As i know, only fglrx drivers have problems with Xv, but maybe that is not case here... Did you tried to delete old ~/.vice/vicerc and start x64 again? Some command output and logs will be more usefull: vice-2.1/config.log, output from console when you actually start 'x64' and:

 ```
ldd /usr/bin/x64 && xvinfo
```

 or ldd /usr/local/bin/x64 if your x64 was installed in local path.

---

### Post by billc123 on 2008-12-23
thanks for the help-
I tried deleting the vicerc file but no luck 
mine is only 2.0 though,not 2.1, but here was the result of the command...

 ldd /usr/local/bin/x64
	linux-gate.so.1 =>  (0xb7fb9000)
	libXaw.so.7 => /usr/lib/libXaw.so.7 (0xb7f30000)
	libXpm.so.4 => /usr/lib/libXpm.so.4 (0xb7f20000)
	libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb7f0a000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb7eb8000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7ea9000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7dba000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb7db1000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7d99000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d80000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7c90000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c6a000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7c5b000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7afd000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7afa000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7af6000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7add000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ad9000)
	/lib/ld-linux.so.2 (0xb7f9f000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7ad4000)

---

### Post by kosmo on 2008-12-23
OK that is usefull, as you can see you miss Xv extensions, probably you don't have dev packages installed. Install the following (i think that is to be enough):

 ```
sudo apt-get libxxf86vm-dev libxv-dev
```

 And then recompile and reinstall new vice again.

---

### Post by billc123 on 2008-12-24
oh- ok. Although when I run that command I also get an error...

sudo apt-get libxxf86vm-dev libxv-dev
E: Invalid operation libxxf86vm-dev

---

### Post by K.Mandla on 2008-12-24
There's a small typo in that. Try:

```
sudo apt-get install libxxf86vm-dev libxv-dev
```

---

### Post by K.Mandla on 2008-12-24
> **kosmo said:**
> Probably you check this on old link [http://www.viceteam.org/](http://www.viceteam.org/) , but new link we should use is [http://vice-emu.sourceforge.net/](http://vice-emu.sourceforge.net/) .
Ah, thank you.

---

### Post by billc123 on 2008-12-28
Thanks K.Mandla.

 That worked. :) I have the full screen option now after doing that command and recompiling with the --enable fullscreen option.

 The only problem I see now is that the fullscreen does not work with my resolution (but at least it is there now). I think it's just not a feature of the program. My normal desktop resolution is 1280 x 800 (16:10), and it looks like the program only supports either 640 x 480 or 800 x 600 at fullscreen.
I tried for testing purposes to change my desktop resolution to 800 x 600 and it looked somewhat ok, but I wouldn't want to leave my desktop like that normally though. oh well - thats ok -at least I found out the answer to why it wasn't there anyway.

---

### Post by kosmo on 2008-12-29
You must have that resolution in vice and any other which 'xrandr' command listed. If you use some
resolution for Desktop, you can use the same in vice... Maybe libxrandr-dev also not installed:

 ```
sudo apt-get install libxrandr-dev
```

 After you recompiled with that also, look for available resolutions in 'XRandR Reslotions' and not in "VidMode".

 > NEWS
 ..... 
 - Vidmode (fullscreen support) is broken and therefore marked as
  deprecated. It will be removed in the next release if no-one takes
  responsibility to fix the broken code and is willing to maintain the
  code.

---

### Post by billc123 on 2009-01-01
i ran that command (sudo apt-get install libxrandr-dev) and it installed ok, then recompiled- but i still don't see an option called "XRandR Reslotions". Do you need to recompile with a certain command to get it? also where should it be found?
thanks...

---

### Post by xc8 on 2009-02-15
Hi,

I got an error : sound fragment. (on alsa)

I think its missing oss sound support. How can I enable this?



> **kosmo said:**
> Since VICE 2.1 is released, if you use Ubuntu 8.04 or 8.10 you can check my PPA for 2.1 debs;). I would like to hear some feedback from users, so i could try to make debs better for wide-spread usefullness (if they not good enough already).

 [https://launchpad.net/~smoki00790/+archive](https://launchpad.net/~smoki00790/+archive)

 NOTE: All roms are mangled from original source, so neither .orig source nor debs packages include any of it!

---

### Post by lukew on 2009-03-25
> **kosmo said:**
> Since VICE 2.1 is released, if you use Ubuntu 8.04 or 8.10 you can check my PPA for 2.1 debs;). I would like to hear some feedback from users, so i could try to make debs better for wide-spread usefullness (if they not good enough already).

 [https://launchpad.net/~smoki00790/+archive](https://launchpad.net/~smoki00790/+archive)

 NOTE: All roms are mangled from original source, so neither .orig source nor debs packages include any of it!

Thank you so much for this. However I can not get the key to verify. I import it into the software repositories and it is listed however when I go to install the software it says it can not be authenticated.

Trying to install the hardy versions.


Thanks
Luke
Luke

---

### Post by lukew on 2009-03-25
> **lukew said:**
> Thank you so much for this. However I can not get the key to verify. I import it into the software repositories and it is listed however when I go to install the software it says it can not be authenticated.

Trying to install the hardy versions.


Thanks
Luke
Luke

Well I went and installed this anyway without getting the gpg key to work. However I get the following error message when trying to open x64 or xplus4


XRandR: XRandR reports current display: 1280x768@60
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Any ideas?

Thanks
Luke

---

### Post by lukew on 2009-03-28
> **lukew said:**
> Well I went and installed this anyway without getting the gpg key to work. However I get the following error message when trying to open x64 or xplus4


XRandR: XRandR reports current display: 1280x768@60
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Any ideas?

Thanks
Luke

I compiled successfully on an intrepid box though I got a recursive error on the checkinstall step. Any one have any ideas?

Thanks 
Luke

---

### Post by lukew on 2009-03-28
Ok. In short I could never compile this on my AMD64. Always hard locks and have to force a reboot with the power switch. Last time someone posted the deb file for gutsy which worked. This does not seem to work for me now on hardy. My laptop runs intrepid. Compiled ok but as you see above I get a recursive error when I run Check Install.

All in all getting no wwhere very slowly.

My actions?

01: Remove all copies of vice ( and repos added to get compiled version of vice.)

02: Install vice from the default ubuntu repositories which do not include the roms required to play.

03. Read the file /usr/share/doc/vice/README/ROMS.

The file contains the following information:

[B][I]Previously, this was handled with the vice-getroms package, which was
a fragile downloader that attempted to download the individual ROM
images and put them in their correct places.  At one point, the
upstream maintainers of VICE put together a tarball of the necessary
images, which can be found at:

[ftp://ftp.zimmers.net/pub/cbm/crossplatform/emulators/VICE/old/vice-1.5-roms.tar.gz](ftp://ftp.zimmers.net/pub/cbm/crossplatform/emulators/VICE/old/vice-1.5-roms.tar.gz)

Download that file, and copy the contents of vice-roms-1.5/data/* into
the matching directories in /usr/lib/vice.  You will probably need to
be root to do this.
[/I][/B]

For me this worked a treat.

Also to to get a rom to work:

01 Left click on running emulator select smart attach disk/rom
02 Navigate to required rom, highlight and select autostart
03. Roms take a while to load.

Hope this helps but. 

Luke

---

### Post by K.Mandla on 2009-03-28
Interesting. I'll have to track down an AMD64 and see if I can get it to build. Thanks for the note.

---

### Post by proevofanatik on 2009-04-18
im using linux mint ant ive installed vice through the package manager. but i dont see it in the game section in the menu button on the bottom left hand of the sceen. do i need to use come kind of command line to load it up all the time? or can i create a shortcut to my desktop?

---

### Post by K.Mandla on 2009-04-19
> **proevofanatik said:**
> im using linux mint ant ive installed vice through the package manager. but i dont see it in the game section in the menu button on the bottom left hand of the sceen. do i need to use come kind of command line to load it up all the time? or can i create a shortcut to my desktop?
Beats me. You should probably ask the 'Mint folks where it is supposed to reside to make sure you're not working around a bug.

---

### Post by K.Mandla on 2009-04-29
I've updated the howto only slightly for the Jaunty release. Ubuntu 9.04 works fine with the tutorial as it is. 

[CENTER][[img]http://omploader.org/tMWxuaA[/img]](http://omploader.org/vMWxuaA) [/CENTER]

(That's with the Gnome user interface enabled; the instructions as they stand only call for the xaw-based interface.)

Enjoy!

---

### Post by RogueClown on 2009-06-09
i'm having trouble saving my programs in VICE c128 mode.

i am running VICE on a HP Pavilion dv4000, running Hardy Heron.  in my ~/.vice/vicerc, i first defined FSDevice8Dir="/home/adalia/bin/vice/c128", a directory i had created.  i tried to save a program by typing DSAVE"programname", and it gave me a device not present error.  

i then went back into the vicerc file and defined FSDevice8Dir=".".  i fired up VICE again, wrote another sample program and ran DSAVE"programname".  the screen output:

SAVING 0: PROGRAMNAME
READY

then, i typed DIRECTORY to see if it saved, and it didn't list any files.  there just printed a blank line, and then READY.  sure enough, i listed the directory that it was supposed to save in, and there were no files in the directory.

i'm wondering...what am i doing wrong?

thank you for your help;

---

### Post by richard270384 on 2009-07-02
> **Frankie6502 said:**
> Thanks for the info. However I did have some issues running vice on my laptop. 

The problem was mainly with the joystick options, it seemed that you couldn't define your own keyset and I couldn't get the other two  keysets to work. As my laptop doesn't have a number pad I could not use that option either.

The solution I found was to run "./configure --enable-gnomeui" after making and installing there is now the option to define your own keys under Settings>Joystick settings>Define keysets

I hope this helps any laptop users like myself with this or similar problems with the joystick options. :)

I'm having this same problem - and most games require a joystick in one way or another.

I tried Frankie's advice to configure with --enable-gnomeui, but I got this error message:

```
checking for GTK... configure: error: Package requirements (gtk+-2.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I tried to find a package named gtk+-2.0 (or something similar) in Synaptic but couldn't find one.

I'm running Ubuntu 9.04... Any thoughts or any other info you need?

---

### Post by K.Mandla on 2009-07-03
> **richard270384 said:**
> I'm having this same problem - and most games require a joystick in one way or another.

I tried Frankie's advice to configure with --enable-gnomeui, but I got this error message:

```
checking for GTK... configure: error: Package requirements (gtk+-2.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I tried to find a package named gtk+-2.0 (or something similar) in Synaptic but couldn't find one.

I'm running Ubuntu 9.04... Any thoughts or any other info you need?
If I recall correctly, you'll need the [libgtk2.0-dev]("http://packages.ubuntu.com/jaunty/libgtk2.0-dev") package in order to get that working under the Gnome UI. To be honest, I would recommend installing [gnome-core-devel]("http://packages.ubuntu.com/jaunty/gnome-core-devel") instead, since it's probably going to require more than just the GTK2.0 development files.

But a +1 to the Gnome-based interface, for ease of adjusting the joystick settings. It's a shame the xaw version doesn't also have that option. ... :(

---

### Post by richard270384 on 2009-07-03
> **K.Mandla said:**
> If I recall correctly, you'll need the [libgtk2.0-dev]("http://packages.ubuntu.com/jaunty/libgtk2.0-dev") package in order to get that working under the Gnome UI. To be honest, I would recommend installing [gnome-core-devel]("http://packages.ubuntu.com/jaunty/gnome-core-devel") instead, since it's probably going to require more than just the GTK2.0 development files.

But a +1 to the Gnome-based interface, for ease of adjusting the joystick settings. It's a shame the xaw version doesn't also have that option. ... :(

I installed gnome-core-devel and it works fine now. Thanks.

---

### Post by whoya on 2009-09-23
K.Mandla you a life saver. i did as you said copyed the code and now im playing all the old c64 games i loved so much.
cheers mate

---

### Post by K.Mandla on 2009-12-30
It's more than 3 years old, but the how-to still works. This is Ubuntu 9.10 and VICE 2.2.

[[img]http://omploader.org/tMzRlZA[/img]](http://omploader.org/vMzRlZA)

Enjoy! :KS

---

### Post by K.Mandla on 2010-05-04
I've tried four or five times now to build VICE 2.2 in Lucid, but I hit the same error each time. Here are the final lines from the *make* command, so you can compare it with yours.
```
x11video.c:268: warning: function declaration isn’t a prototype
x11video.c: In function ‘shmhandler’:
x11video.c:348: error: ‘X_ShmAttach’ undeclared (first use in this function)
x11video.c:348: error: (Each undeclared identifier is reported only once
x11video.c:348: error: for each function it appears in.)
make[7]: *** [x11video.o] Error 1
make[7]: *** Waiting for unfinished jobs....
make[7]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src/arch/unix/x11/xaw'
make[6]: *** [all-recursive] Error 1
make[6]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src/arch/unix/x11/xaw'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src/arch/unix/x11'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src/arch/unix'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src/arch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/kmandla/Downloads/vice-2.2/src'
make: *** [all-recursive] Error 1

real	1m49.583s
user	2m40.754s
sys	0m14.309s
```
I will do a little more research and see if there is a patch or a fix somewhere; more than likely something was updated in a core library that interferes with VICE's compilation, and it will be adjusted on one or the other side. Stay tuned. ... :)

---

### Post by datenraffzahn on 2010-05-07
@K.Mandla

I've a work-arround for this issue. 

1. open vice-2.2/src/arch/unix/x11/xaw/x11video.c

with you favorite editor

2. goto line 348 and replace X_ShmAttach by 1

3. save, close and compile

First I tried to include shmproto.h but this didn't do it. Compliler tells me this file would'nt exist, but it does. So I commented out my own include again.

Just looking out the value for X_ShmAttach in the shmproto.h file and replacing it in x11video.c by 1 (as defined in shmproto.h) does the trick. Vice compiles probably.

regards.

---

### Post by K.Mandla on 2010-05-12
> **datenraffzahn said:**
> I've a work-arround for this issue. ...
Thanks very much, this worked perfectly for me for both the xaw version and the Gnome UI build.

[[IMG]http://img268.imageshack.us/img268/4876/vicexaw.th.png[/IMG]](http://img268.imageshack.us/i/vicexaw.png/) [[IMG]http://img243.imageshack.us/img243/6775/vicejumpman.th.png[/IMG]](http://img243.imageshack.us/i/vicejumpman.png/)

I'll update the original post to link to your fix. Cheers! :mrgreen:

---

### Post by parovelb on 2010-06-25
After the make command nothing happens?
```
parovelb@parovelb-laptop:~/vice-2.2$ make
make: *** No targets specified and no makefile found.  Stop.
parovelb@parovelb-laptop:~/vice-2.2$
```
Now what?

---

### Post by parovelb on 2010-06-26
> **parovelb said:**
> After the make command nothing happens?
```
parovelb@parovelb-laptop:~/vice-2.2$ make
make: *** No targets specified and no makefile found.  Stop.
parovelb@parovelb-laptop:~/vice-2.2$
```Now what?

simple k pasulj. to solve this I have installed the latest g++ and related libs.

---

### Post by WARvault on 2010-08-12
I am having some trouble with the "sudo checkinstall" stage of this on my G3 iMac with lucid.
I am getting this error [http://pastebin.com/4YNJnp92](http://pastebin.com/4YNJnp92)

Thanks for the great howto KMan!

---

### Post by K.Mandla on 2010-11-03
This tutorial is four years old now, and still works. :)

[[img]http://ompldr.org/tNjFjMw[/img]](http://ompldr.org/vNjFjMw)

Unfortunately, the one-line edit that was needed for 10.04 is still required for 10.10. Don't forget that, or VICE won't compile. Probably at some point in the future, that will not need editing.

Additionally, as WARvault mentioned, checkinstall might give errors. If that's the case, stick with *sudo make install*; that has yet to fail me.

Have fun! :KS

---

### Post by rudy.b on 2010-11-04
For some reason I couldn't get sound to work initially when compiling under Maverick, although sound on my Lucid machine worked fine.  When running from the command line, the Maverick machines would give me this error:
```
Did not find any uss device
```
Also, I really wanted to get fullscreen to work and I found a solution to both problems with information in [this thread]("http://ww.ubuntuforums.org/showthread.php?p=8629869").

After I installed the SDL development files:
```
sudo aptitude install libsdl-dev
```

I was able to configure VICE using the following command:
```
./configure --enable-sdlui
```

And then did the 'make' and 'sudo checkinstall' to complete the process.  Now, sound works perfectly well on all my systems with no additional tweaking.

The SDL interface isn't as nice as the Gnome one, but it does the job.  Pressing F12 will give you the command menu and from there you can select your video settings.  I was able to setup a fullscreen option with a custom resolution and OpenGL free scaling for great results on my LCD TV.  Now I can play Jumpman in full widescreen with stereo sound!

---

### Post by DrazenZG on 2011-01-08
Thank you very much for this tutorial, great job :)

---

### Post by beerli on 2011-02-19
dont forget to 
$make clean
prior to your checkinstall! 

thx to the datenraffzahn for the cool workaround. how do you come up with that?! all avaliable thumbs up!

---

### Post by JohnFante on 2011-05-15
Version 2.3 compiled with SDL and work fine on Natty-x64 :-). And it is way better than the 2.2 version in the repo. I did not make any changes to the source, so I do not think the change on page 12 is needed anymore.

I can not get it to make a deb-package with checkinstall but sudo make install does the trick. Sudo checkinstall works fine on the x86 version of Natty I have on a laptop so it is proberbly a x64 thing. No problem thou.

---

### Post by Antirad on 2012-08-30
I need some help it's not letting me run any emulator...it says:

OS compiled for: Linux
GUI compiled for: GTK+
CPU compiled for: Pentium Pro
Compiler used: GCC-4.6.2
Current OS: not yet implemented
Current CPU: Intel Pentium Pro/II/III/Celeron/Core/Core 2/Atom
 
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
D. Lem, A. Matthies, M. Pottendorfer, S. Trikaliotis, M. van den Heuvel,
C. Vogelgsang, F. Gennari, D. Kahlin, A. Lankila, Groepaz, I. Korb,
E. Smith, O. Seibert.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
XRandR: XRandR reports current display: 1366x768@60
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Error - Machine initialization failed.

Exiting...

---


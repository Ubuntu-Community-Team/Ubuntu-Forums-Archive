---
title: "Google Earth beta available for download"
date: 2006-06-12
forum: The Cafe
---

### Post by johanPO on 2006-06-12
I just found that they relesed a beta [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Don't know if this is old news, but anyway I thought I'd post this

Download, and execute sh GoogleEarthLinux.bin and that was it
 
I have it up and running and so far it looks  nice

---

### Post by BWF89 on 2006-06-12
I like how it says "Tested on the following OS's" and Ubuntu is the first one on the list.

---

### Post by MetalMusicAddict on 2006-06-12
I dont care if you are late, Thanx man. I got it going right off the bat. Killer.

---

### Post by Ubunted on 2006-06-12
Woohoo!

The overall interface is a bit different, but it's working beautifully on my X800XL.

---

### Post by 23meg on 2006-06-12
Good to hear this; downloading now.

---

### Post by krye on 2006-06-12
I don't think you are late... why isn't this posted all over news sites on the internet??

Thanks! I'm installing it as soon as I get home.

---

### Post by ubuntu27 on 2006-06-12
[QUOTE=johanPO]I just found that they relesed a beta [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Don't know if this is old news, but anyway I thought I'd post this

Download, and execute sh GoogleEarthLinux.bin and that was it
 
I have it up and running and so far it looks  nice[/QUOTE]

Hey thanks! Tha's NEWS for me :)

---

### Post by _simon_ on 2006-06-12
it's a shame that the windows live one has more detail :(

However.... :D been waiting for this!

---

### Post by grsing on 2006-06-12
It does work pretty well, though on my laptop (just on the edge of the specs, can run the Windows version but it's slow) it doesn't work very well (LOTS of visual artifacts and such, hard to use).  On the desktop, once I realized I had old nvidia drivers installed and put the new ones on, it works great, just as good as the Windows.

---

### Post by MetalMusicAddict on 2006-06-12
Heres a screenshot:

[[IMG]http://img66.imageshack.us/img66/9895/screenshot5at.th.jpg[/IMG]](http://img66.imageshack.us/img66/9895/screenshot5at.jpg)

I have a AMD 2600+ and a nVidia 6800OC.

---

### Post by 23meg on 2006-06-12
15 minute impression: performance isn't any different than the Windows version but it's already crashed twice, beta being beta.

---

### Post by grsing on 2006-06-12
[QUOTE=23meg]15 minute impression: performance isn't any different than the Windows version but it's already crashed twice, beta being beta.[/QUOTE]

Though with Google, it's hard to say what Beta actually means (gmail is still beta, for goodness sakes).  But you're right, this is a pretty early beta, and the first on Linux, so we have to expect some problems.  Still, I love Google more than ever right now (and the news that they're reconsidering the China stuff is all the better).

---

### Post by MetalMusicAddict on 2006-06-12
[QUOTE=grsing](and the news that they're reconsidering the China stuff is all the better).[/QUOTE]
Got a link to that?

---

### Post by imagine on 2006-06-12
Try Google =)

[http://news.google.com/news?hl=en&q=google+china](http://news.google.com/news?hl=en&q=google+china)

But they don't really reconsider anything. Sergey Brin just said that Google may have compromised its principles with their censorship in China.
However IMHO Googles single principle is making as much money as possible, as every other big company. So I don't see what they compromised there.

---

### Post by givré on 2006-06-12
So funny,[http://earth.google.com/](http://earth.google.com/)
"View exotic locales like Maui and **Paris**" :rolleyes: :cool:

---

### Post by Technoviking on 2006-06-12
I can only run Google Earth as root, in via sudo.

Anyone having this problem?

---

### Post by REBELinBLUE on 2006-06-12
[QUOTE=Mike]I can only run Google Earth as root, in via sudo.

Anyone having this problem?[/QUOTE]

Yeah, in fact that is the rest for my visit, to see if anyone else is.

I get "symlink: Permission denied" unless I use sudo

---

### Post by cbudden on 2006-06-12
Did you install as sudo to your home dir?  I didn't need to use sudo to install.

---

### Post by NeoChaosX on 2006-06-12
The simple solution would be not to run the installer as sudo and just install to your home directory.

Personally, I'm having toruble with the graphics. The display area has pretty corrupt and/or messed up graphics. I'm using an ATI card (Mobility Radeon 7500 with 64 MB of RAM), though, so that may explain my problems.

---

### Post by avilella on 2006-06-12
[QUOTE=grsing]It does work pretty well, though on my laptop (just on the edge of the specs, can run the Windows version but it's slow) it doesn't work very well (LOTS of visual artifacts and such, hard to use).  On the desktop, once I realized I had old nvidia drivers installed and put the new ones on, it works great, just as good as the Windows.[/QUOTE]

mine is also misbehaving... the image is broken in pieces like a puzzle. Incidentally, there must be something wrong with my nvidia:

avilella@magneto:~$ dpkg -l nvidia-glx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  nvidia-glx                        1.0.8762+2.6.15.11-1              NVIDIA binary XFree86 4.x/X.Org driver

---

### Post by kashms on 2006-06-12
[QUOTE=REBELinBLUE]
I get "symlink: Permission denied" unless I use sudo[/QUOTE]

when you install with sudo the ~/.googleearth directory is owned by root.

```
sudo chown -R user:user ~/.googleearth
```

exchange "user" with your user name.

---

### Post by K.Mandla on 2006-06-12
Looking at the system requirements, am I to understand it longer needs wine?

---

### Post by grsing on 2006-06-12
[QUOTE=NeoChaosX]The simple solution would be not to run the installer as sudo and just install to your home directory.

Personally, I'm having toruble with the graphics. The display area has pretty corrupt and/or messed up graphics. I'm using an ATI card (Mobility Radeon 7500 with 64 MB of RAM), though, so that may explain my problems.[/QUOTE]

The computer I'm having trouble on is a Mobility Radeon 9000, pretty much the same problem.  I'm going to try to find a fix, I'll let you know if I come up with anything.

---

### Post by grsing on 2006-06-12
[QUOTE=K.Mandla]Looking at the system requirements, am I to understand it longer needs wine?[/QUOTE]

If it runs like Picasa, it uses Wine, but it's part of the install, configured so that you don't even know Wine is running (but that's only if it's like Picasa, they could have just ported it entirely, I don't know).

---

### Post by Rhapsody on 2006-06-12
Working for me, but the program says I'm using OpenGL with software emulation. I know that this means my CPU is doing all the work and my GeForce4 MX (with good OpenGL support) is just sitting there looking pretty. This isn't really an acceptable situation, so does anyone have a tip about what to do? My video card is a Micro-Star International GeForce4 MX4000.

---

### Post by grsing on 2006-06-12
[QUOTE=avilella]mine is also misbehaving... the image is broken in pieces like a puzzle. Incidentally, there must be something wrong with my nvidia:

avilella@magneto:~$ dpkg -l nvidia-glx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  nvidia-glx                        1.0.8762+2.6.15.11-1              NVIDIA binary XFree86 4.x/X.Org driver[/QUOTE]

You might try installing the most recent NVIDIA drivers, that's what worked for me.  The guide here: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1) worked well (used Method 1, it'll automatically install the most recent version).

---

### Post by K.Mandla on 2006-06-12
[QUOTE=grsing]If it runs like Picasa, it uses Wine, but it's part of the install, configured so that you don't even know Wine is running (but that's only if it's like Picasa, they could have just ported it entirely, I don't know).[/QUOTE]
True. I would prefer it didn't rely on wine. Nothing against wine, just a personal quirk of mine. ;)

---

### Post by givré on 2006-06-12
[QUOTE=grsing]If it runs like Picasa, it uses Wine, but it's part of the install, configured so that you don't even know Wine is running (but that's only if it's like Picasa, they could have just ported it entirely, I don't know).[/QUOTE]
I'm not so sure, there is no .dll in their directory but .so files
I think they converted their .dll from the windows version into .so with wine, but i might be wrong.
Anyway, wine is not launch when i use it

---

### Post by futaris on 2006-06-12
[QUOTE=kashms]when you install with sudo the ~/.googleearth directory is owned by root.[/QUOTE]

Thanks for that... It fixed the problem nicely...

---

### Post by Azrael on 2006-06-12
[quote=Rhapsody]Working for me, but the program says I'm using OpenGL with software emulation. I know that this means my CPU is doing all the work and my GeForce4 MX (with good OpenGL support) is just sitting there looking pretty. This isn't really an acceptable situation, so does anyone have a tip about what to do? My video card is a Micro-Star International GeForce4 MX4000.[/quote]
Same for me with an S3 Savage of a Thinkpad T20.

Suggestions be welcome. :o

---

### Post by humansuit on 2006-06-12
Just installed with great anticipation, and it works fine.. except.. all the fonts allover the application are unreadable-small. I've had these problems before with other applications (aMsn recently) but i've worked them out somehow, not quite sure how.. i'm totally new at this linux-thing..:)

---

### Post by antdengineer on 2006-06-12
when I install either as root or as a regular user i get:

```
symlink: Permission denied
```

when running "googleearth"

How are you installing this program so that the command "googleearth" can be used to do this.

---

### Post by REBELinBLUE on 2006-06-12
Perfect, thanks

---

### Post by ArizonaKid on 2006-06-12
[QUOTE=imagine]Try Google =)

[http://news.google.com/news?hl=en&q=google+china](http://news.google.com/news?hl=en&q=google+china)

But they don't really reconsider anything. Sergey Brin just said that Google may have compromised its principles with their censorship in China.
However IMHO Googles single principle is making as much money as possible, as every other big company. So I don't see what they compromised there.[/QUOTE]

They better make money.  I own stock in Google :)  and I sure as heck don't want to build my nest egg on companies that don't want to make money.

This may not be the place to get into politics (oh well), but a Google in China with restrictions is better than no Google at all.  I do believe it is evil to restrict information, but sometimes operating in the gray zone is needed in situations like this.  [B]Remember, only a Sith operates in absolutes.  ;)
[/B]

Although we have principles in America, we can't just force and expect change overnight (that's what WAR is for).  There have been several reports that prove that a restrictive Google in China still provides a wealth of information that would be deemed inappropriate.  It's just a matter of time before China is free.  We just have to keep giving China more and more information, access, a free market, trade, and soon the country will know its just **better business** to allow a free society.  Influence, especially economic, can be a wonderful tool of freedom.

---

### Post by bigken on 2006-06-12
Cheers mate my daughter loves this :D

---

### Post by mstlyevil on 2006-06-12
Works very well and I am impressed. From what I am reading Google Earth for Linux is native and does not use wine. I need to do more research to confirm this.

---

### Post by MetalMusicAddict on 2006-06-12
[QUOTE=mstlyevil]Works very well and I am impressed. From what I am reading Google Earth for Linux is native and does not use wine. **I need to do more research to confirm this.**[/QUOTE]
Im looking into this also. Im looking into the processes and I see no WINE processes. Even if it does it aint runnin' half bad. ;)

---

### Post by ArizonaKid on 2006-06-12
[QUOTE=mstlyevil]Works very well and I am impressed. From what I am reading Google Earth for Linux is native and does not use wine. I need to do more research to confirm this.[/QUOTE]

Not sure how definitive this is, but this link says its native.

[URL="http://blogs.zdnet.com/Burnette/index.php?p=124"]
ZDNET BLOGS[/URL]

The article states:
> If Picasa for Linux is successful, then other Google applications (and future versions of Picasa) may also be ported using Wine.  (Google Earth won't be one of them, though; it will be a native Linux application.)

---

### Post by mwales on 2006-06-12
I've tried installing it both as user and sudo/root.  Either way I install it, it can only be run as sudo/root.  Either way, if I try to run it as a normal user I get:

symlink: Permission denied

Please post up your configuration, how you installed it, and how it's working for you.

As long as I run it as root, it seems to work fine.

my config = Kubuntu 6.06 x86_64, GeForce6800 (with NVidias driver)

---

### Post by dudus on 2006-06-12
I was prepared to see a wine port to GEarth. I'm glad to see they made it native.
Although I find wine apps performance pretty nice.

---

### Post by dudus on 2006-06-12
[QUOTE=mwales]I've tried installing it both as user and sudo/root.  Either way I install it, it can only be run as sudo/root.  Either way, if I try to run it as a normal user I get:

symlink: Permission denied

Please post up your configuration, how you installed it, and how it's working for you.

As long as I run it as root, it seems to work fine.

my config = Kubuntu x86_64, GeForce6800 (with NVidias driver)[/QUOTE]
I just chmoded the bin +x and then executed it sayeng yes to all the preconf. parms. After that a new item was added to my applications menu>Internet. Just click and enjoy.

---

### Post by RAV TUX on 2006-06-12
I will pass on GoogleEarth hated it on windows and I hated Picasa on my Ubuntu.

I would rather not have to do a download of old technology like GoogleEarth and I prefer to use either Windows Live Local(with Birds' eye imagery) right from my Firefox or Opera browser. Much better is A9 maps with Blockview technology. 

Google has a long way to go to impress me, they use technology I was using 10 years before they came out with GoogleEarth so I found it a great disappointment but a worthy endeavor.

I do find it amusing how many people are impressed by such old technology.

GoogleEarth & Picasa both a waste of space on my computer, kinda of like useless kitchen gadgets, fun for a week then you realize their worthless.

My apologies in advance for not having a fanboy-like cult following of Google but I haven't found much use for any of their products, especially their search engine & email(not to mention Picasa & GoogleEarth).

---

### Post by RAV TUX on 2006-06-12
Silly question but do we really need 3 threads on GoogleEarth ?:confused:


[http://www.ubuntuforums.org/showthread.php?t=69581](http://www.ubuntuforums.org/showthread.php?t=69581)
[http://www.ubuntuforums.org/showthread.php?t=195199](http://www.ubuntuforums.org/showthread.php?t=195199)
[http://www.ubuntuforums.org/showthread.php?t=183956](http://www.ubuntuforums.org/showthread.php?t=183956)

---

### Post by grsing on 2006-06-12
[QUOTE=yozef]I will pass on GoogleEarth hated it on windows and I hated Picasa on my Ubuntu.

I would rather not have to do a download of old technology like GoogleEarth and I prefer to use either Windows Live Local(with Birds' eye imagery) right from my Firefox or Opera browser. Much better is A9 maps with Blockview technology. 

Google has a long way to go to impress me, they use technology I was using 10 years before they came out with GoogleEarth so I found it a great disappointment but a worthy endeavor.

I do find it amusing how many people are impressed by such old technology.

GoogleEarth & Picasa both a waste of space on my computer, kinda of like useless kitchen gadgets, fun for a week then you realize their worthless.

My apologies in advance for not having a fanboy-like cult following of Google but I haven't found much use for any of their products, especially their search engine & email(not to mention Picasa & GoogleEarth).[/QUOTE]

Your choice, of course.  I've found Google Earth extremely useful when planning trips and the like, and I know other people have found it useful as more than just a toy, but Windows Live Local and A9 are both good, too.  Picasa I kind of agree with you, and also agree that we'd probably be better off with one thread on Google Earth.

---

### Post by TripleE on 2006-06-12
I just downloaded and installed it.  Easy install.  It is working good for me.  My only complaint is that I do not see GoogleEarth in my Applications bar anywere:(

_____________
TripleE

AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16
Raid0 2x SATA 80gb HDs

---

### Post by disturbed1 on 2006-06-12
[QUOTE=TripleE]I just downloaded and installed it.  Easy install.  It is working good for me.  My only complaint is that I do not see GoogleEarth in my Applications bar anywere:(

_____________
TripleE

AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16
Raid0 2x SATA 80gb HDs[/QUOTE]
It installed under internet in GNOME for me.

Works fine with hardware rendering using an ATI x1600.

---

### Post by mwales on 2006-06-12
**For everyone running into the symlink: Permission Denied error**

Found this info over at the google earth community board.  Check your user's home directory for a .googleearth directory.  Mine was owned by root, causing the user to not be able to run the application.  To fix it:

```

sudo chown -R <username> ~/.googleearth/
sudo chgrp -R <username> ~/.googleearth/

```

---

### Post by mustang on 2006-06-12
Thank you for the link. Video is kind of choppy---probably because I don't have the proper ATI drivers working.

---

### Post by benuski on 2006-06-12
Finally.. .this was one of the things I missed the most from windows

---

### Post by professor_chaos on 2006-06-12
[QUOTE=yozef]I will pass on GoogleEarth hated it on windows and I hated Picasa on my Ubuntu.

I would rather not have to do a download of old technology like GoogleEarth and I prefer to use either Windows Live Local(with Birds' eye imagery) right from my Firefox or Opera browser. Much better is A9 maps with Blockview technology. 

Google has a long way to go to impress me, they use technology I was using 10 years before they came out with GoogleEarth so I found it a great disappointment but a worthy endeavor.

I do find it amusing how many people are impressed by such old technology.

GoogleEarth & Picasa both a waste of space on my computer, kinda of like useless kitchen gadgets, fun for a week then you realize their worthless.

My apologies in advance for not having a fanboy-like cult following of Google but I haven't found much use for any of their products, especially their search engine & email(not to mention Picasa & GoogleEarth).[/QUOTE]

Sorry you dont like GoogleEarth. But, ohh man, I think google earth is freekin awesome. Thanks for the link.

---

### Post by nrayever on 2006-06-13
[QUOTE=mwales]**For everyone running into the symlink: Permission Denied error**

Found this info over at the google earth community board.  Check your user's home directory for a .googleearth directory.  Mine was owned by root, causing the user to not be able to run the application.  To fix it:

```

sudo chown -R <username> ~/.googleearth/
sudo chgrp -R <username> ~/.googleearth/

```[/QUOTE]

thanks mwales, this is the real solution for the symlink problem. now i'm enojying of GEarth at my user!! GEarth rocks!! \\:D/ \\:D/ \\:D/ 

nrayever

---

### Post by benplaut on 2006-06-13
[QUOTE=NeoChaosX]The simple solution would be not to run the installer as sudo and just install to your home directory.

Personally, I'm having toruble with the graphics. The display area has pretty corrupt and/or messed up graphics. I'm using an ATI card (Mobility Radeon 7500 with 64 MB of RAM), though, so that may explain my problems.[/QUOTE]

same card here, same problem.

Actually, after doing something i can't remember, it pretty much hard-froze the comp.  Mouse worked, but couldn't get to a TTY or kill X.

Still cool, tho

---

### Post by PapaWiskas on 2006-06-13
Sweet....thanks alot....

---

### Post by flu on 2006-06-13
The installer can be run in normal user and sudo but which is the better way to run the installer? :confused:

---

### Post by grsing on 2006-06-13
[QUOTE=flu]The installer can be run in normal user and sudo but which is the better way to run the installer? :confused:[/QUOTE]

From what I've done and heard about, better to do it normally, otherwise you have to run the program as sudo, which is a pain, and potentially unsafe (I doubt Google wants to hurt your stuff, but with root permissions, it could, and it still is a beta, after all)

---

### Post by codelad on 2006-06-13
I get the following error when i try running google earth :-(

```

$ googleearth
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x212) [0x804ab32]
  ./googleearth-bin [0x804b133]
  [0xffffe500]
  /usr/lib32/libX11.so.6(XQueryExtension+0x17) [0x5734afc7]
  /usr/lib32/libX11.so.6(XInitExtension+0x3b) [0x5733f54b]
  /usr/lib32/libXext.so.6(XextAddDisplay+0x49) [0x5731951c]
  /usr/lib32/libGL.so.1 [0x57457394]
  /usr/lib32/libGL.so.1(__glXInitialize+0x1f) [0x57457a5b]
  /usr/lib32/libGL.so.1(__glXSetupForCommand+0x47) [0x57458a11]
  /usr/lib32/libGL.so.1(glXSwapIntervalSGI+0x9d) [0x57455f57]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext15setSwapIntervalEi+0x100) [0x56adbf60]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x568) [0x56b17378]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll13VisualContext11openContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xff) [0x59a898bf]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0xdf) [0x59a8b2af]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x3f) [0x59a3be8f]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x4b) [0x56fb87bb]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x8a) [0x56fa06ba]
  ./libgoogleearth.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x7d) [0x55c6180d]
  ./libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0x277) [0x56266db7]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0x561ba731]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xc9) [0x561bb219]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x266) [0x56265d16]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN11QMainWindow4showEv+0x93) [0x56338513]
  ./libqt-mt.so.3(_ZN7QWidget10showNormalEv+0x33) [0x5625f383]
  ./libgoogleearth.so(_ZN10MainWindow18readScreensizeInfoEv+0x621) [0x55c26e61]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEiPPc+0x1569) [0x55c4e2d9]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0x923) [0x55c502c3]
  ./googleearth-bin [0x804c73d]
  /lib32/libc.so.6(__libc_start_main+0xd2) [0x57122ea2]
  ./googleearth-bin(__gxx_personality_v0+0x41) [0x804a961]

```

Any ideas on how to get this fixed? 

I'm running Dapper Drake 6.06 amd64 with 2.6.15-23-amd64-generic #1 SMP PREEMPT

Thanks in advance, 
VJ

---

### Post by _simon_ on 2006-06-13
[QUOTE=mwales]I've tried installing it both as user and sudo/root.  Either way I install it, it can only be run as sudo/root.  Either way, if I try to run it as a normal user I get:

symlink: Permission denied

Please post up your configuration, how you installed it, and how it's working for you.

As long as I run it as root, it seems to work fine.

my config = Kubuntu 6.06 x86_64, GeForce6800 (with NVidias driver)[/QUOTE]

installed via ```
sh GoogleEarthLinux.bin
```

I Let the installer use the default location and symlink.

I run it via the menu entry in Applications -> Internet and a panel icon.

Not had any crashes yet and graphics are problem free, I use the 32bit version of Dapper + k7 kernel and have an nvidia Geforce 6800, driver 1.0-8762

---

### Post by Hanj on 2006-06-13
I also get lots of visual artefacts on my laptop :( It's not even usable. Hope this will get better in newer versions.

---

### Post by Footissimo on 2006-06-13
For those with 'owned by root problems' its worth mentioning that, like all the loki installers, you shouldn't run the program from the button which presents at the end of the installer - as you are currently running as root, the program will create the ~/.googleearth directory as root.

Instead, once the installer has finished, just press 'exit' and then type in 'googleearth' and the ~/.googleearth directory will be created as user.

I wish the loki installer and its look-a-likes would just NOT offer to run the programs, it confuses the hell out of some.

Oh and thankyou Google :)

---

### Post by Brynster on 2006-06-13
Nice app

Shame google had to ruin is reputation. Personally my anti google axe grinding and refusal to use or support google will go on until it stops dealing with China.

---

### Post by DerHesse on 2006-06-13
Same for me (Dapper)
```

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x212) [0x804ab32]
  ./googleearth-bin [0x804b133]
  [0xffffe420]
  ./libbase.so(_ZN5earth12MemoryWindow17ShowMemoryMessageEP7QWidget7QStringbS3_S3_RKS3_S5_+0x462) [0xb7991d92]
  /home/xxx/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl18requireDXOGLSwitchERK7QStringS4_+0x183d) [0xb3ba148d]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0xcc) [0xb658183c]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x8a) [0xb65696ba]
  ./libgoogleearth.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x7d) [0xb791a80d]
  ./libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0x277) [0xb6ff5db7]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6f49731]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xc9) [0xb6f4a219]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x266) [0xb6ff4d16]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6ff4a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6ff4cb7]
  ./libqt-mt.so.3(_ZN11QMainWindow4showEv+0x93) [0xb70c7513]
  ./libqt-mt.so.3(_ZN7QWidget10showNormalEv+0x33) [0xb6fee383]
  ./libgoogleearth.so(_ZN10MainWindow18readScreensizeInfoEv+0x621) [0xb78dfe61]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEiPPc+0x1569) [0xb79072d9]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0x923) [0xb79092c3]
  ./googleearth-bin [0x804c73d]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb62deea2]
  ./googleearth-bin(__gxx_personality_v0+0x41) [0x804a961]


```

i did the uninstall :) and will stay with [http://maps.google.com/](http://maps.google.com/)

I wonder if there are any Daper Drake users with a working googleearth.

---

### Post by phido on 2006-06-13
[quote=DerHesse][]("http://maps.google.com/")
I wonder if there are any Daper Drake users with a working googleearth.[/quote]
Works fine here :D

---

### Post by rippon on 2006-06-13
Works fine for me, but then it randomly locks up. :(

---

### Post by PapaWiskas on 2006-06-13
so ok, i made the mistake as installing with sudo.

How do I uninstall it, so I can start over?

---

### Post by givré on 2006-06-13
the uninstaller is in /usr/local/google-earth

---

### Post by bruce89 on 2006-06-13
[QUOTE=ArizonaKid]Although we have principles in America, we can't just force and expect change overnight (that's what WAR is for).  There have been several reports that prove that a restrictive Google in China still provides a wealth of information that would be deemed inappropriate.  It's just a matter of time before China is free.  We just have to keep giving China more and more information, access, a free market, trade, and soon the country will know its just **better business** to allow a free society.  Influence, especially economic, can be a wonderful tool of freedom.[/QUOTE]
And America is free?  It's one of the more oppressive places I know of.  Also, war doesn't make things any better, contary to what George thinks.

---

### Post by imagine on 2006-06-13
[QUOTE=yozef]I would rather not have to do a download of old technology like GoogleEarth and I prefer to use either Windows Live Local(with Birds' eye imagery) right from my Firefox or Opera browser. Much better is A9 maps with Blockview technology. 

Google has a long way to go to impress me, they use technology I was using 10 years before they came out with GoogleEarth so I found it a great disappointment but a worthy endeavor.[/QUOTE]
I don't know what you used 10 years ago, however here are two shots of the same, randomly chosen place in Germany. One from Windows Live and one from Google Maps, *both with the highest possible resolution*.

[Google Maps](http://img149.imageshack.us/img149/3595/google3qg.png)
[Windows Live](http://img149.imageshack.us/img149/8925/windows7dt.png)

So be careful before calling one of them obsolete.

---

### Post by bruce89 on 2006-06-13
[OpenStreetMap]("http://www.openstreetmap.org") is much better!  Well, not for satellite views anyway.

---

### Post by grsing on 2006-06-13
For those with the weird visual artifacts, try hiding and then showing the sidebar (the square kinda button at the top left of the picture space).  Don't know why it works, but that clears up the problem for me, hopefully for you too.

---

### Post by outdooricon on 2006-06-13
If this is native, then why does the UI look so bad. It's got an ugly windows 95 feel to it especially in the menus, instad of using nice gtk menu's...

---

### Post by NeoChaosX on 2006-06-13
[QUOTE=outdooricon]If this is native, then why does the UI look so bad. It's got an ugly windows 95 feel to it especially in the menus, instad of using nice gtk menu's...[/QUOTE]
That's because it's built with Qt and Google seems to have used the default Qt theme rather than let it use a user's Qt theme. In KDE, it actually looks nice (or the fonts do, at least).

---

### Post by cbudden on 2006-06-13
[QUOTE=outdooricon]If this is native, then why does the UI look so bad. It's got an ugly windows 95 feel to it especially in the menus, instad of using nice gtk menu's...[/QUOTE]

I agree, it does look ugly.

---

### Post by givré on 2006-06-13
It is definitly native, if you still thinking that is not, look at /usr/local/google-earth/, you will see only .so (and in particular the famous libqt4.so) and no .dll, so why would they use wine? to convert linux library into linux library ? that's stupid guys.

---

### Post by cyB3r4rd on 2006-06-13
As I mentioned in the other main GE topic, it would be really nice if GE could use the shared libraries of the present system, including libjpeg, libmng, libpng, libcurl, libcrypto... and libqt-mt and libqui.
But it doesn't at the moment, that's why the GUI looks so ugly.

I'd like to use it with my custom QtCurve, but I can't... quite bad...

---

### Post by richbarna on 2006-06-13
[QUOTE=johanPO]I just found that they relesed a beta [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Don't know if this is old news, but anyway I thought I'd post this

Download, and execute sh GoogleEarthLinux.bin and that was it
 
I have it up and running and so far it looks  nice[/QUOTE]

YAY ! This is the one and only thing I missed on Windows.
Looks good, old news or not, I didn't know about it until I saw this thread !

Thank you :)

---

### Post by lonegranger on 2006-06-13
I'm a real newbie to Linux. Used to run Google Earth before on my XP box until I was converted. How exactly do you install and run it with Ubuntu.

Thanks

---

### Post by _simon_ on 2006-06-13
there's a few ways.

first download the GoogleEarthLinux.bin file

then the way I did it was, open terminal and type:
```

sh /path/to/GoogleEarthLinux.bin

```
obviously replace /path/to/ with the actual location of the bin file!

---

### Post by grsing on 2006-06-13
[QUOTE=lonegranger]I'm a real newbie to Linux. Used to run Google Earth before on my XP box until I was converted. How exactly do you install and run it with Ubuntu.

Thanks[/QUOTE]

Assuming you download it to your home directory, just type:

sh GoogleEarthLinux.bin

and just follow the prompts.  To run it, it should show up in the Internet part of the applications menu; to run from terminal, it's googleearth

---

### Post by bruce89 on 2006-06-13
I just right clicked on it, went to Properties>Permissions and selected Owner executable.  I then just double clicked it.

---

### Post by stenka on 2006-06-14
Hi,

On my laptop with i915 graphic card, it displays well but it so slow that it is not usable.

On the terminal, I get the following messages :

stenka@ubuntu:~$ sudo googleearth
Password:
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.

Do you have any idea ?

Thanks in advance.

---

### Post by givré on 2006-06-14
Are you using xgl/aiglx guy, it seems so.
If it is, unactive compiz and it should be better

---

### Post by stenka on 2006-06-14
Thank you for your answer.

Indeed I installed it, even if I am not using it right now (deactivated with compiz).

But, sorry for my stupidity, I don't know how to disable it.

I tried to uncomment the related line of my xorg.conf :

<<
Section "Module"
        Load   "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        #Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"
EndSection

...

Section "ServerLayout"
        #Option "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

>>

But when I run googleearth it claims that glx extension is missing.

What's the way for deactivating xgl without desinstalling all the stuff ?

---

### Post by stenka on 2006-06-15
anyone tried it with a 915 GM laptop ?

Xgl is not activated at my GDM startup, so I don't think it comes from that...

And 3d games are not slow (I tested penguin racer), while Googleearth take more than 10s to answer to any command.

---

### Post by JimmyDeSotto on 2006-06-15
Hi all, I have a Acer Aspire 5021 with a Radeon mobility X700 card under the hood and Google Earth doesn't seem to want to recognise it, it keeps loading up the Open GL emulation and is very very slow. This is very puzzling as *suprise suprise* it loads up perfectly fine on my old desktop with a crappy Geforce 440MX. If anyone's found a solution to this problem that'd be great

---

### Post by stenka on 2006-06-15
[QUOTE=stenka]anyone tried it with a 915 GM laptop ?

Xgl is not activated at my GDM startup, so I don't think it comes from that...

And 3d games are not slow (I tested penguin racer), while Googleearth take more than 10s to answer to any command.[/QUOTE]

For those who would meet the same problem, a simple "export LIBGL_ALWAYS_INDIRECT=true" resolved my problem.

---

### Post by Bols on 2006-11-02
> **stenka said:**
> For those who would meet the same problem, a simple "export LIBGL_ALWAYS_INDIRECT=true" resolved my problem.
Thank you, it did the trick but it seems more a workaround than a real fix
by using this command you just replace the hardware rendering by the software one.
Maybe it's related to [this xorg bug]("https://bugs.freedesktop.org/show_bug.cgi?id=6814")?

---

### Post by inthepit on 2006-11-03
> **BWF89 said:**
> I like how it says "Tested on the following OS's" and Ubuntu is the first one on the list.

its cause of this [http://en.wikipedia.org/wiki/Goobuntu](http://en.wikipedia.org/wiki/Goobuntu)

---


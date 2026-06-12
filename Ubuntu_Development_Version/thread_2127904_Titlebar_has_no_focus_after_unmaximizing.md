---
title: "Titlebar has no focus after unmaximizing"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by stinkeye on 2013-03-21
After bringing a window out of a maximized state the titlebar has no focus.
Can't move by grabbing or use buttons.
Clicking on the titlebar goes straight through to any application behind it.

---

### Post by grahammechanical on 2013-03-21
I have just noticed that myself. Cannot close the application either. Except by going to the icon in the launcher and selecting Quit.

---

### Post by mc4man on 2013-03-21
Noticed this last week but that was when testing a proposed qt4 bug fix in a compiz test ppa.  Reverting  back to the then current stopped this behavior. (that bug fix has been discarded for a new proposed one.

So ironically the latest compiz   1:0.9.9~daily13.03.20-0ubuntu1 seems to bring this on (possibly the compiz source used by the testing ppa included code that's now in the current compiz & it wasn't the proposed patch that caused.

To further 'muddle' the new proposed patch for a qt4 fix also 'fixes' this though likely should have a new compiz bug specific to this behavior.

---

### Post by stinkeye on 2013-03-21
Found bug report here
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1158264](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1158264)

---

### Post by Hreinsi on 2013-03-23
someone notice prob with firefox when i shrink the window i cant close minimize or close top bar seems dead. Can move the window with mouse right under top bar.but have to close on unity launsher. hope you understand my English

---

### Post by Hreinsi on 2013-03-23
Ok now it seems like ewery window that  i open in min mode after maximixing and shrink back top bar freeze so i cant double click to maximize.

---

### Post by Hreinsi on 2013-03-23
maybe some compiz prob after setsid unity in terminal it works once twice maybe 3 times and freese again

---

### Post by SMOKE14 on 2013-03-23
I actually was just having that problem... I use the Gnome Classic desktop, I had to use the Fallback to get it to move windows.

---

### Post by Hreinsi on 2013-03-23
i can move them by clicking right under top bar but the top bar just dies

---

### Post by SMOKE14 on 2013-03-23
> **Hreinsi said:**
> i can move them by clicking right under top bar but the top bar just dies

That does not work for me. I have to use the Fallback session.

---

### Post by grahammechanical on 2013-03-23
Now we have two threads on this subject.

[http://ubuntuforums.org/showthread.php?t=2127904](http://ubuntuforums.org/showthread.php?t=2127904)

---

### Post by cariboo on 2013-03-23
Merged two similar threads

---

### Post by VinDSL on 2013-03-23
*Had* the same problem(s).

Switched theme (in GS) to "OMG".

Problem went away...  ;)

---

### Post by VinDSL on 2013-03-23
> **mc4man said:**
> So ironically the latest compiz   1:0.9.9~daily13.03.20-0ubuntu1 seems to bring this on [...]
Oh... is this a Unity problem too :confused:

I'll go check it out.  BBL

**EDIT**

Dern it!  [s]Everything is working fine here, in a Unity session[/s]...

```
vindsl@Zuul:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.9~daily13.03.20-0ubuntu1
  Candidate: 1:0.9.9~daily13.03.20-0ubuntu1
  Version table:
 *** 1:0.9.9~daily13.03.20-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1:0.9.8.6-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main i386 Packages
vindsl@Zuul:~$
```

Hrm.  Theme issue, maybe?!?!?

Guess I'll go read the bug...

---

### Post by VinDSL on 2013-03-23
Seems like this is affecting a lot of different setups.

Here's my [s]working[/s] config, for what it's worth...

```
Current Date/Time: Sat Mar 23 15:18:47 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc3-generic
Gnome Release: GNOME Shell 3.7.92
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.84

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.3-0ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

```

**EDIT**

n/m

I just lost focus, on the terminal window, in Unity.

I can still move the window around, but the min/max/close buttons are missing.

I'll add a 'me too' in Launchpad...

---

### Post by mc4man on 2013-03-23
Just to clarify, maybe..
This bug is in compiz, specifically the decor plugin (window deco.) & has been fixed, just not yet released.
Issues the same or similar but Not in a compiz session would be different & unaffected by the fix to come in the next compiz release

---

### Post by monkeybrain2012 on 2013-03-23
> **grahammechanical said:**
> Now we have two threads on this subject.

[http://ubuntuforums.org/showthread.php?t=2127904](http://ubuntuforums.org/showthread.php?t=2127904)

Actually at least three, I started one too.

[http://ubuntuforums.org/showthread.php?t=2128354](http://ubuntuforums.org/showthread.php?t=2128354)

Updating Compiz from [https://launchpad.net/~smspillaz/+archive/compiz-experimental](https://launchpad.net/~smspillaz/+archive/compiz-experimental) appears to fix the problem for now.

---

### Post by VinDSL on 2013-03-23
> **mc4man said:**
> Just to clarify, maybe..
This bug is in compiz, specifically the decor plugin (window deco.) & has been fixed, just not yet released.
Issues the same or similar but Not in a compiz session would be different & unaffected by the fix to come in the next compiz release
Aha!  That makes sense.

The problem I was having in GS was similar, but not the same.  BTW, I'm still in Unity and the only prob I've had is with the terminal window (above).

In GS, depending on which mixture of theme, shell theme, icon theme set , and so forth, and so on -- and depending on the app(s) I had open -- the title bars looked and acted differently.  Anyway, moot point.

Thanks, for the clarification.  ;)

---

### Post by VinDSL on 2013-03-23
> **monkeybrain2012 said:**
> Updating Compiz from [https://launchpad.net/~smspillaz/+archive/compiz-experimental](https://launchpad.net/~smspillaz/+archive/compiz-experimental) appears to fix the problem for now.
WoW!  That's weird!

I *thought* Sam quit maintaining Compiz :confused:

Is this the same 'Sam' mentioned in articles/posts all over the blogisphere?

---

### Post by mc4man on 2013-03-23
> **monkeybrain2012 said:**
> 

Updating Compiz from [https://launchpad.net/~smspillaz/+archive/compiz-experimental](https://launchpad.net/~smspillaz/+archive/compiz-experimental) appears to fix the problem for now.
That ppa can cause some issue at times, particulary if you update unity from it. Last I checked, (a while), DnD with the ppa unity was a no go.

---

### Post by EgoGratis on 2013-03-23
I indeed can't move some widows after latest RR updates (probably after using some minimize/maximize.... operations) by clicking on title bar but it works pressing the ALT button + mouse click and close/minimize/maximize buttons stops working too but i do see them!

---

### Post by mc4man on 2013-03-23
> **VinDSL said:**
> WoW!  That's weird!

I *thought* Sam quit maintaining Compiz :confused:

Is this the same 'Sam' mentioned in articles/posts all over the blogisphere?
Same guy, different 'role'

He's been helping out lately with some bugs & has recent commits to - 
[https://code.launchpad.net/~compiz-team/compiz/0.9.9](https://code.launchpad.net/~compiz-team/compiz/0.9.9)

There is also this which was recently created
[https://code.launchpad.net/~compiz-team/compiz/raring](https://code.launchpad.net/~compiz-team/compiz/raring)

At times I may have understood the diff. between the 2, now I just don't bother...

Edit: about as much as I undertand why this post is RE: Firefox? (Oh, I did figure that out.

---

### Post by VinDSL on 2013-03-23
> **mc4man said:**
> Same guy, different 'role' [...]
Heh!
[QUOTE=Chinese Curse]
"May you live in interesting times"[/QUOTE]
Hard to keep up these days...  ;)

---

### Post by cariboo on 2013-03-23
Sam left Canonical, because basically his job is over, now that UnityNext is on the horizon. With Unity being re-written using QT, and running on Mir, there was no real need for a compiz developer any more.

---

### Post by VinDSL on 2013-03-23
> **cariboo907 said:**
> Sam left Canonical, because basically his job is over, now that UnityNext is on the horizon. With Unity being re-written using QT, and running on Mir, there was no real need for a compiz developer any more.
What?  No more "Cube" :confused:


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-23-mar-2013-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-mar-2013-3.png")[/INDENT]


Sorry!  Still testing Unity and got bored...  LoL!  :D

---

### Post by cariboo on 2013-03-24
> **VinDSL said:**
> What?  No more "Cube" :confused:


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-23-mar-2013-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-mar-2013-3.png")[/INDENT]


Sorry!  Still testing Unity and got bored...  LoL!  :D

That's what it looks like, but looking at your screenie, I'm glad you get bored once in a while. :-D

---

### Post by mc4man on 2013-03-24
> **cariboo907 said:**
> Sam left Canonical, because basically his job is over, now that UnityNext is on the horizon. With Unity being re-written using QT, and running on Mir, there was no real need for a compiz developer any more.
Well yes & no.
13.04/13.04+a little is using compiz & represented a chance for at least one decent compiz/unity release before abandoning at some point in the near future.
So hopefully they'll get some things fixed & refrain from borking it up any further.

---

### Post by stinkeye on 2013-03-26
Issue resolved with compiz update.

---


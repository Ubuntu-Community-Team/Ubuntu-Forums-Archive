---
title: "Randomly smirched characters"
date: 2013-10-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-10-25
I have several different machines on a hardwired KVM so I know it is not just one machine that is acting up. On three workstations I have Trusty. Every once in a while for the past few days I have been noticing 'smirched' or 'squished' characters while reading content through FireFox. When I go to try and take a snapshot of the 'smirched' letter or numeral it restores itself so, when I see it next I will try and get a hard photo of it with my camera.

Anyone else noticing these?

---

### Post by ventrical on 2013-10-25
Here are two photocaps of a smirched "y".  I haven't noticed these anomolies on other sites but I can't say for certain if it is systemic only with ubuntuforums. I'll keep a look out :)  Also other characters will look like they are squashed or smudged, like somebody smudging the screen.

Sounds weird .. I know.

---

### Post by ventrical on 2013-10-25
Graphics..

---

### Post by ventrical on 2013-10-25
Yet another.

---

### Post by xc3RnbFO8P on 2013-10-25
You could check:
> echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

---

### Post by brainwash on 2013-10-25
Probably related to this bug report:

[https://launchpad.net/bugs/1098334](https://launchpad.net/bugs/1098334)

---

### Post by ventrical on 2013-10-25
> **Ringi said:**
> You could check:


Thanks ..

```

ventrical@ventrical-desktop:~$ echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo 

  dimensions:    1440x900 pixels (381x238 millimeters)
  resolution:    96x96 dots per inch

ventrical@ventrical-desktop:~$ 

```

  But I think I nailed it down to a problem with FireFox, smoothscrolling and ubuntuforums.  When I have smooth scrolling enabled (Trusty Tahr) in FF I can notice this sort of raster scan.  Only a trained eye can detect it.  It will not happen on other webpages like the wikis or Nick's page at organebook or other pages for that matter .. only ubuntuforums. When I turn off smooth scrolling the problem seems to disappear but it is awfully chunky ..  This just started to happen with the transition over to 14.04.

  I am not faulting ubuntuforums or firefox for that matter. It may be a problem with my monitor or KVM but  to counter that theory I tried using Xubuntu ... etc.. and this anomoly is not present on the same KVM with the same monitor - so - I am assuming that something came in with some of the pre-updates as we transitioned over to Trusty. I say again .. these are only my assumptions at this point.

Thanks for your help and interest.:)

Regards..

---

### Post by ventrical on 2013-10-25
> **brainwash said:**
> Probably related to this bug report:

[https://launchpad.net/bugs/1098334](https://launchpad.net/bugs/1098334)

I do not think I have SNA enabled. This is a raw install, updated, upgraded of trusty with no PPAs atm.. however... the bug report you eluded to described a very similar case scenario. I did experiement with SNA during  the raring cycle on another machine but did not have any problmes with it.

  Is SNA now enabled by default (do you know ?).

---

### Post by xc3RnbFO8P on 2013-10-25
> It may be a problem with my monitor 
yes if you cant see it in screenshot, maybe you should change the cable

---

### Post by ventrical on 2013-10-25
Apparently gone , with most recent updates. :)

edit ..

The cat came back ! :(

---

### Post by The Cog on 2013-10-25
> **brainwash said:**
> Probably related to this bug report:

[https://launchpad.net/bugs/1098334](https://launchpad.net/bugs/1098334)

I don't think it is that bug. That bug report is for chromuim's tab bar. I have seen it regularly for the last 6 months - an interesting but harmless effect. I could be wrong, (I may have just stopped noticing it) but I don't think I've seen it since I upgraded to 13.10.

This bug with random corrupted font characters, single characters in a line of otherwise perfect text in firefox is new to 13.10. I thought it was only firefox for a while, but I have just once in the last few days seen the same effect in a gnome-terminal session. This is on a laptop with intel mobile 4 graphics, running Xubuntu. Passing another window over the top of the corruption does not clear it, nor does scrolling the page as long as the corrupt text remains on screen. Rolling the window up into the title bar and down again (I use the scroll wheel over the title bar to do this) seems the quickest way to get a repaint that clears it, although another character elsewhere may get damaged in the process.

---

### Post by brainwash on 2013-10-25
> **The Cog said:**
> I don't think it is that bug. That bug report is for chromuim's tab bar.

This indicates that you did not bother to actually read the comments posted in the bug report. On top of that, you should have taken a look at the reports marked as duplicates and the linked upstream report.

---

### Post by The Cog on 2013-10-25
I repeat, the chromium tabs bug has been evident to me for 6 months - since the release of 13.04. So, incidentally, has the occasional problem with images when scrolling firefox though I didn't mention that earlier. The firefox character corruption is new to 13.10.

The problem with firefox and individual characters is new to 13.10. This problem is not described anywhere in the bug report you linked, in any of the 104 posts (to date). There is quite a difference between the two symptoms - I can only guess that you have not seen them both.

I admit to not reading every post marked as duplicate before. I just read the first 2 or 3 and clearly were duplicates. On reading all of them, I see that four other reports describe the new firefox problem (all in 13.10) have been marked as duplicates of this bug, as have two bug reports describing 'Rhythmbox generates warning about podcast' and '"The application "nautilus" has quit unexpectedly"'. I am sceptical about the accuracy of duplicate linking. I still do not think they are the same bug.

EDIT:
I just re-tested, and it seems that the reason I hadn't noticed the twinkling chromium tabs in the last week since I installed 13.10 is that the problem has gone away. I think the firefox image scrolling problem has also gone, but as that was infrequent I can't yet be certain.

---

### Post by ventrical on 2013-11-25
Again ... looks as this one is fixed.  If I do not see it during the rest of the day I'll mark this thread solved.

---

### Post by vasa1 on 2013-11-25
It's a pity, IMO, that discussion is going on here when the "smirched text bug" isn't restricted to Ubuntu +1. It exists in 13.10 as well.

---

### Post by ventrical on 2013-11-26
I have an array of several different machines hooked up to a physical KVM. One of those machines on the KVM is identical to another machine that is not hooked up to the KVM. They are both Intel Core2Duos and this phenomenon is only happening on these two machines with Trusty. I have eliminated the KVM as a source and also any monitor or physical cable problems (they are both running on different monitors .. same results) and other installs of Trusty on different machines are not displaying these 'smirched' characters  so it leads me to conclude that there is something wrong either with the machines themselves or the Intel Graphics  Driver which is currently Intel 965Q. The only other thing I can think of is that there is some wrong setting in the BIOS that is producing this that is not handshaking correctly with the Intel Driver.

  Cannot mark the thread as solved because after update/upgrade and a whole day of any sign of 'smirched characters' they showed up still once again.

Regards.

Edit:

In BIOS I am presented with options:

DVMT MODE    Fixed/DVMT
IGD DVMT MEM 256MB
YGD Aperature   256MB
Primary Video Int Graphics IGD

I was using the FIXED  mode. I switched back to DVMT. I'll see what happens throughout the day.

---

### Post by ventrical on 2013-12-16
Doing a followup reply :

 I had noticed that the 'smiched' character phenom still persisted  on my 2 Core2Duo machines while running Unity and/or gnome-session-flashback with FF browser. I have now installed Xubuntu-Desktop and am going to monitor there for a while for smirched text. So far I have not seen the smirched anomoly on Xubuntu.

---

### Post by ventrical on 2013-12-16
Smirched characters on xubuntu also. I think I nailed it down a bit. I think it has to do when using the Ctrl+ LeftShift + (+or-) to magnifiy the characters in FF. I can't say for certain  but I seen a smirched character disolve as I was try to make the characters smaller.

---

### Post by VinDSL on 2013-12-16
Interesting...

I've been following, e.g. reading, this thread since the beginning.  Couldn't relate to it, because I never had this problem -- until today.

I've been building up a gently used Dell Latitude ATG D630 lappy.  It'll be my new 'road warrior'.

I always run Peppermint OS on my portables, but hear me out. LoL!

This lappy has Intel Crestline graphics, and it was doing the same thing you described above, especially with links on pages.  The links were all over the place -- smirched -- underneath the text in articles, etc.

The whole display -- Conky -- Chromium -- Kingsoft Writer -- everything -- looked rather janky, but the links put me over the top.

Anyway, I just switched from SNA to UXA, and it really made a huge difference in quality.

```
vindsl@Lothgar ~ $ cat /var/log/Xorg.0.log | grep -i sna

vindsl@Lothgar ~ $ cat /var/log/Xorg.0.log | grep -i uxa
[    24.331] (**) intel(0): Option "AccelMethod" "uxa"
[    24.991] (II) UXA(0): Driver registered support for the following operations:

vindsl@Lothgar ~ $ 

```

You might want to try this, if you already haven't.

```
vindsl@Lothgar ~ $ sudo mkdir /etc/X11/xorg.conf.d/
```
```
vindsl@Lothgar ~ $ echo -e 'Section "Device"\n Identifier "Card0"\n Driver "Intel"\n Option "AccelMethod" "uxa"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf
```
Reboot and test.

Hopefully, it will hold...

---

### Post by ventrical on 2013-12-17
@VinDSL

  Honestly .. I had no idea they put that in there by default.!!  I remember using the ppa on Quantal testing but I thought it was optional and not set as default..

```

ventrical@ventrical-desktop:~$ cat /var/log/Xorg.0.log | grep -i sna
[    25.517] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    25.556] (II) intel(0): SNA initialized with Broadwater (gen4) backend
ventrical@ventrical-desktop:~$ 


```

brb  :)

---

### Post by ventrical on 2013-12-17
Tried your method and got this much at least.

```

ventrical@ventrical-desktop:~$ cat /var/log/Xorg.0.log | grep -i uxa
[    25.187] (**) intel(0): Option "AccelMethod" "uxa"
ventrical@ventrical-desktop:~$ 


```

I'll keep a lookout for smirched characters.

Thanks again...:)

Edit:

So far, so good. However .. there appears to be another bug unrelated. Upon magnifiying the characters on the web pages with Ctrl+LShift+ (+or-) the links will not zone into the mouse hover meaning to say that when you hover over a magnified link the mouse icon will not morph to the handy dandy finger pointer :) lol ... Unlrelated bug methinks.. and this goes for SNA  and the UXA modes.

---

### Post by ventrical on 2013-12-17
Nope ! They are still there. :(   lol

---

### Post by VinDSL on 2013-12-17
> **ventrical said:**
> @VinDSL

  Honestly .. I had no idea they put that in there by default.!!  I remember using the ppa on Quantal testing but I thought it was optional and not set as default.

I guess *they* think we're all running Sandy Bridge systems.  LoL!  :D

SNA = Sandybridge's New Acceleration

UXA = Unified Acceleration Architecture

---

### Post by VinDSL on 2013-12-17
> **ventrical said:**
> Nope ! They are still there. :(   lol
Well, here's something else you might try...

I enabled SNA acceleration again, this morning, but disabled 3D acceleration:

```
Section "Device"
 Identifier "Intel Graphics"
 Driver "intel"
 Option "AccelMethod" "sna"
 Option "DRI" "False"
EndSection
```
```
vindsl@Lothgar ~ $ cat /var/log/Xorg.0.log | grep -i sna 
[    25.457] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4.3 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    25.478] (**) intel(0): Option "AccelMethod" "sna"
[    26.131] (II) intel(0): SNA initialized with Broadwater/Crestline backend
vindsl@Lothgar ~ $ 

```

Haven't noticed any smirched characters yet, on this machine -- * fingers crossed *.

---

### Post by ventrical on 2013-12-18
> **VinDSL said:**
> I guess *they* think we're all running Sandy Bridge systems.  LoL!  :D

SNA = Sandybridge's New Acceleration

UXA = Unified Acceleration Architecture

No wonder I don't get smudges and smirches on my SandyBridge set. I thought SNA stood for  SuperNanoAccelerator or SimpleNoobAddons err whatever ! :) lol

jk.. :)

Thanks a million Vin.

---

### Post by ventrical on 2013-12-18
Typo methinks amigo :)

"
$ echo -e 'Section "Device"\n Identifier "Card0"\n Driver "Intel"\n Option 
"AccelMethod" "uxa"\nEndSection' | sudo tee /etc/X11/xorg.conf.d/20-intel.conf"

Should not \nEndSection' be \n EndSection'  ?

:)

or does it matter.

---

### Post by VinDSL on 2013-12-18
Bwahahaha!

That's one of the perils of coding on a 14" laptop.  LoL!  :D

You wouldn't believe how many mistakes I need correct in forums, et cetera.

Anyway, that was a copy n' paste from my bash history -- it created the file correctly on this machine, regardless of the misspelling...

**EDIT**

On second thought, I *think* that wasn't a misspelling.

If you look at the output, I first and last lines of the script were flush with the margin -- the other lines are supposed to be indented by one space.  Heh!

---

### Post by ventrical on 2014-01-10
Looks like smudged characters have been fixed with new kernel.

```

ventrical@ventrical-desktop:~$ uname -a
Linux ventrical-desktop 3.13.0-1-generic #16-Ubuntu SMP Tue Jan 7 19:47:28 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-desktop:~$ 



```

---

### Post by ventrical on 2014-01-11
This PC has been up and running for about 24 hours and no smudged characters with new kernel so I will mark this thread as solved.

Regards..

---

### Post by ventrical on 2014-01-17
Strange.... I  just upgraded the GRub bootloader ONLY from proposed-repo and now I have my 'smirched' characters back. :) lol

---

### Post by VinDSL on 2014-01-18
Only smirched characters I've experienced recently are Korean/Hangul.

Solved that by installing 'UnDotum.ttf' (from the UN Fonts package).  Got me wondering...

Could your situation be font related -- corrupt font file -- janky cache, et cetera?!?!?

---

### Post by ventrical on 2014-01-20
> **VinDSL said:**
> Only smirched characters I've experienced recently are Korean/Hangul.

Solved that by installing 'UnDotum.ttf' (from the UN Fonts package).  Got me wondering...

Could your situation be font related -- corrupt font file -- janky cache, et cetera?!?!?

Hi Vin,

 I'm not totally sure  what it is but I do not think it is fonts .... however .. how would I install the package you that you currently using?

Also .. I had thought about corrupt fonts .. etc.. but the smirchies go away  if I hover over them or scroll the screen etc... they are capricious atm si I have to eliminate the font theory on this particular machine.  They (smirchies) only come up on this one Intel desktop Core2Duo with Intel Graphics.

---


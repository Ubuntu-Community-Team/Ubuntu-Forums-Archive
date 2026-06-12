---
title: "can't run Planescape:torment fullscreen"
date: 2009-01-08
forum: Wine
---

### Post by Adahn on 2009-01-08
This is apparently a common issue per the wineappdb

I got the game sucessfully installed and patched.

I can only get it to run with Fullscreen=0 in torment.ini, and then only in a virtual window.  It runs normally, including sound, just very small...800x600 or 640x480 by the looks of it.

Setting desktop resolution to 8x6 may be my only workaround, but I still lose the in-game movies.

I'm using intrepid, restricted fglrx drivers, and wine 1.1.1
I've tried setting wine to use different windows versions to no avail.

---

### Post by Adahn on 2009-01-18
wineappdb says the last working wine version for PS:T is 0.9.15
I'll look into reverting.

---

### Post by merlyn on 2009-01-18
Are you running Compiz or Compiz/Fusion perchance?

---

### Post by Adahn on 2009-01-21
No.

---

### Post by JoeBob McGee on 2009-01-21
I've spent several days researching this problem myself for Baldur's Gate II.  I'm running Hardy with the fglrx 8.12 drivers.

This issue seems to plague all the Infinity Engine games under Wine.  The only way I've managed to get Baldur's Gate II working in fullscreen mode is via 3D acceleration, which crashes frequently.  I've tried all manner of registry changes within Wine and changes within Baldur's Gate II to no avail.

Since Planescape Torment does not have 3D acceleration, I doubt fullscreen mode is even an option.  As far as I've been able to research, there is no solution to this problem.  If you find anything workable though, I'd definitely like to hear.

I've read that VirtualBox may work to play Infinity Engine games.  I haven't tried it, but I imagine you'd need an extra beefy system to play any game under VirtualBox, but it may be worth a try.  When I get some extra time this weekend, I may try it.

---

### Post by merlyn on 2009-01-22
> **Adahn said:**
> No.

Bugger, that blows my theory to hell then.

---

### Post by aniruddha on 2010-03-08
Has anyone managed to get torment working in wine? I've had no success with wines 1.1.36-40.

---

### Post by Toffeeapple on 2010-03-08
Me!

I have it running, I'm at the moment with wine 1.1.40 but it's been working for a while now since 1.1.27 at least I'm sure.

I have wine emulate a virtual desktop of 1280x800, to run the game at that resolution read [here]("http://www.gibberlings3.net/readmes/readme-widescreen.html"). I don't see why you cant run it at any resolution in a wine emulated virtual desktop and make it fill your entire screen with using this mod.

Incidentaly, that mod can be used for all of the infinity engine Bioware games, there is also a mod on the same site that enables you to play BG1 with the BG2 engine and that in combination with the widescreen mod enables me to play BG1 at 1440x900 with the BG2 engine... rather nice : )

Have a look [here]("http://www.gibberlings3.net/") at the The Gibberlings Three sit, lots of good Infinity engine mods and hacks.

One point of note though is that for some reason Planescape will crash if you drag another screen across or over it, doesn't happen with any of the other infinity games I have running just Planescape.. something to do with colour depth I think, dunno.

---

### Post by aniruddha on 2010-03-08
Thanks a ton toffeeapple. Will check this and see if it works.

---

### Post by Toffeeapple on 2010-03-09
There is also [this]("http://gemrb.sourceforge.net/wiki/doku.php") which is a native linux fronted for infinity engine games, it can be used to play Planescape as well as BG1 and IWD1, I have tried it but prefer the above solution I mentioned with wine and the widescreen mod.

---

### Post by aniruddha on 2010-03-10
Hey toffeeapple,

I tried running the WeiDU mod you had pointed out, and followed their instructions. However, when attempting the "tolower" command, I was told that "baldur.ini" did not exist. However, on reading their forums, I realized that the linux.ini that is to be created just points out the unix directories (/home/user/.wine/drive_c/torment or whatever the directory is). So I changed the torment.ini to this format (I found this post useful, [http://forums.gibberlings3.net/index.php?showtopic=15486](http://forums.gibberlings3.net/index.php?showtopic=15486))

Now, when I run WeInstall for the widescreen it runs fine until this error message shows up:

[/home/user/.winet/drive_c/pst/cd2/ar0100.cbf] decompressed bif file 6584190 bytes
ERROR: BIFF [./cache/AR0100.BIF] cannot be loaded: Unix.Unix_error(20, "stat", "./cache/ar0100.bif")

ERROR locating resource for 'COPY'
Resource [AR0100.WED] not found in KEY file:
	[./chitin.key]

[I have the 2cd version].

what seems to be happening is that on decompressing the .cbf file, an UPPERCASE bif file is created. Which unix systems can't read. When I run tolower in the cache directory, the program repeats the error for the next file (i.e. AR0101.bif). So what needs to happen is that the bif files must be lowercased as well, on their extraction. How does one get around this problem?

Thanks a ton.

---

### Post by Toffeeapple on 2010-03-10
Your torment.ini should be something like this.. just like it was when installed in windows, it's planescapes config file.
```
[Alias]
HD0:=C:\Program Files\Black Isle\Torment
CD1:=C:\Program Files\Black Isle\Torment\cd1\
CD2:=C:\Program Files\Black Isle\Torment\cd2\
CD3:=C:\Program Files\Black Isle\Torment\cd3\
CD4:=C:\Program Files\Black Isle\Torment\cd4\
CD5:=C:\Program Files\Black Isle\Torment\cd5\
[Config]
CacheSize=120
[Movies]
BISLOGO=1
TSRLOGO=1
OPENING=1
SS_MSLAB=1
SIGIL=1
[Game Options]
Footsteps=1
Mouse Scroll Speed=50
GUI Feedback Level=5
Locator Feedback Level=3
Command Sounds Frequency=3
Selection Sounds Frequency=3
Bored Timeout=3000
Always Dither=1
Keyboard Scroll Speed=50
Effect Text Level=62
Attack Sounds=1
Auto Pause State=0
Difficulty Level=3
Quick Item Mapping=1
Always Run=1
Memory Access=100
Memory Level=1
Health Bar Settings=63
Subtitles=0
Environmental Audio=1
Sound Processing=1
Music Processing=1
[Program Options]
Tooltips=0
Sprite Mirror=1
Gamma Correction=0
Brightness Correction=0
Volume Movie=100
Volume Music=100
Volume Voices=100
Volume Ambients=100
Volume SFX=100
Strref On=0
Screen Position X=0
Screen Position Y=0
Full Screen=1
Path Search Nodes=4000
Maximum Frame Rate=30
Translucent Shadows=1
SoftSrcKeyBltFast=0
SoftBltFast=0
SoftSrcKeyBlt=0
SoftBlt=0
SoftMirrorBlt=0

```

I think the chitin.key is generated when the game runs, the fact that you have altered the torment.ini file may be why it hasn't and is being looked for in your home folder ( [./chitin.key] ).. but I don't know, it's just a guess.

You might also what to have a look at [this]("http://www.spellholdstudios.net/ie/ghostdogs-pst-ui") mod, it fixes GUI anomalies when using non standard resolutions.

I can only assume the linux.ini file is of no use in Planescape as I don't have it in my install and it works OK, I may have deleted it I don't remember.But I just loaded the game up to be sure and it all works fine (apart from the fact that I wasted half an hour playing the game when I should really be getting my kids ready for school, damn you planescape!)

Also just in case you don't... I have all the data CD's copied over to my planescape install as is described [here]("http://www.bootstrike.com/Torment/Online/tti2.html").

---

### Post by Toffeeapple on 2010-03-10
Empty the 'cache' folder ? have you tried that ? all that is generated when you play the game anyway I think.

You were editing your post just as I was posting my last reply, sorry missed all the added stuff : )

edit.. maybe you don't have a full install.. as in the last line of my above post?

---

### Post by aniruddha on 2010-03-10
Hmm. Just edited to add the link to the mod site. Sorry!

With respect to the torment.ini file, I followed the instructions on their forums (which say you should have changed directories in the torment.ini to match the unix file system thingy). Will try again with the windows format. 

Yes, I have completed a full install (I used the same bootstrike guide you mentioned). I tried deleting the cache folders as well (doesn't work). Will try using your torment.ini suggestions. Thanks for all your help. 

And I empathize completely with your last half hour. I think I lost a couple of years to this beautiful, cursed game!!!

Nope, even the windows file paths lead to the same error:

[/home/aniruddha/.winet/drive_c/pst/cd2/ar0100.cbf] decompressed bif file 6584190 bytes
ERROR: BIFF [./cache/AR0100.BIF] cannot be loaded: Unix.Unix_error(20, "stat", "./cache/ar0100.bif")

ERROR locating resource for 'COPY'
Resource [AR0100.WED] not found in KEY file:
	[./chitin.key]

D*mn. Will putter around and see if there is anything to be done.

---

### Post by aniruddha on 2010-03-10
Hah! Success!!!

In order to get the widescreen and other mods to work, I just downloaded the windows versions and extracted them into the game directory. Then used "wineconsole cmd" (after alt+f2) to run them. 

Now I gaze upon Sigil in all its 1600x1200 splendour...

---

### Post by Toffeeapple on 2010-03-10
Good : )

Also that crash I mentioned in an earlier post that happened when ever another window was passed over the planescape one seems to have gone now with wine 1.1.40, still crashes if I minimise the wine window though : (

---

### Post by aniruddha on 2010-03-10
Hmm, I managed to get al+tab working. I had compiz running, and the first (prevent directx apps from letting the mouse leave or some such) and the last (virtual desktop) options checked in winecfg. Leaving the window manager options unchecked seems to allow for window switching (strange but true). Best luck, and thanks for all your help...

---


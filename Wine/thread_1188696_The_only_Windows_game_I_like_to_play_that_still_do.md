---
title: "The only Windows game I like to play that still doesn't work..."
date: 2009-06-16
forum: Wine
---

### Post by Cadeyrn on 2009-06-16
Guild Wars. I installed it on WINE 1.0.1 and then upgraded to 1.1.23. Not the exact guidelines, but it should have produced the same result. Guild Wars does work properly, I'll give it that much, except every single time it tries to load an area it immediately closes without an error message. The window, the process, everything just suddenly quits. I'm suspecting being on Jaunty x64 might have something to do with it; this seems like a glitch that any x32 game would do on any x64 system.

---

### Post by Cadeyrn on 2009-06-16
Okay, and now S.T.A.L.K.E.R. Clear Sky doesn't work either. I followed the newest WineHQ AppDB how-to and most is well, except every single time I've launched it, "XrEngine encountered a serious error and needs to close." I'm on STALKER 1.5.07 with the no-dvd patch, and WINE 1.1.23. If I downgraded to 1.1.22, would these nuisances be fixed? Or is it a x64 issue?

---

### Post by themusicalduck on 2009-06-16
The best way to find out what's going wrong with a program in wine is to run it from the terminal and look for any error messages.

```
wine /path/to/file.exe
```

the file path will probably be somewhere along the lines of 
~/.wine/drive_c/Program\ Files/whereyourprogramisinstalled

---

### Post by nmaster on 2009-06-16
You should try using a virtual machine.  You'll need an Windows ISO/CD, but a lot of people already do.  I would never suggest using a torrent or google searching through megaupload.com, but who am I to stop you?

Try out these links.  They're very good.

[http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox](http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox)
[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)
[COLOR=#888888]

If you do this, you could forget all about WINE.  A virtual machine would solve any future problems that you could have with using Windows applications.  You don't need a lot of disk space and if you have sufficient RAM this should be a good option.
[/COLOR]

---

### Post by themusicalduck on 2009-06-16
3D acceleration isn't greatly supported in virtualbox and is only limited to OpenGL.. (for now). Although DirextX is supported experimentally in VMware. Also it would potentially take a massive performance hit trying to run new games in a virtualmachine unless you have a very powerful computer.

I'd have thought wine would be better to use in this case aside from dual-booting.

---

### Post by gunboat on 2009-06-16
Guild Wars did not work for me under Wine 1.1.22, but I dropped down to 1.1.20 (after getting advice here) and it works perfectly. Never crashes, no problems at all.

---

### Post by NightMKoder on 2009-06-16
There were a few bugs related to memory management in wine that appeared in the 1.1.20+ series. Guild wars is affected by one of them, but you can run it fine on 1.1.20. Check the appdb entry.

---

### Post by Cadeyrn on 2009-06-17
Alright. Actually, I was going to try making a partition of x32 Jaunty running WINE 1.1.22 for Gw and STALKER, but why not, eh? I'll download 1.1.20 now.

One more question, though: do Titan Quest Immortal Throne 1.30 and Steam work fine on 1.1.20? Because I'd like to not lose those apps.

EDIT: Guild Wars works now! And so does TQIT as well as Steam. But we still haven't fixed STALKER Clear Sky... On 1.1.20 it acts the same.

Through the Terminal (wine "C:\Program Files\Deep Silver\S.T.A.L.K.E.R. - Clear Sky\bin\xrEngine.exe") we get this:
```
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x113fd8 0
fixme:heap:HeapSetInformation 0x110000 0 0x32f990 4
```
With the -i that I should be using, I get the same Terminal error and the same GUI behavior.

---

### Post by Cadeyrn on 2009-06-17
Read my edit.

---

### Post by gunboat on 2009-06-17
> **Cadeyrn said:**
> Guild Wars works now! And so does TQIT as well as Steam. But we still haven't fixed STALKER Clear Sky... On 1.1.20 it acts the same.
 
Is your Titan Quest:IT installed via CD or Steam? I ask because I have the disks and wonder if it would work.

---

### Post by Cadeyrn on 2009-06-17
It's not, and, false alarm--Guild Wars is still crashing while loadng areas, every time. And I had to upgrade back to 1.1.23 because Steam wouldn't work on 1.1.20. I'll try 1.1.22 now.

---

### Post by Cadeyrn on 2009-06-17
1.1.22 Also is the same.

---

### Post by gunboat on 2009-06-17
> **Cadeyrn said:**
> 1.1.22 Also is the same.

1.1.20 works for me for GW.

---

### Post by Cadeyrn on 2009-06-18
And now Steam is being very weird. Left 4 Dead, Counterstrike: Source, and Garry's Mod (11, that is) aren't working, just like for many people, but mine don't work in a weird way. They will either freeze Steam or be unavailable, no matter what I do. The strangest part is they're the only broken apps. My other Steam apps like Half - Life 2, the episodes, Lost Coast, Portal, etc., work flawlessly on max graphics.

So, we have Guild Wars, STALKER Beer Sky, Left 4 Dead, Counterstrike Source, and Garry's Mod with issues that no one else has had before. The odds seem hard... I'm going to try Guild Wars with Steam, if that's available, because the client should be a free download.

---

### Post by Cadeyrn on 2009-06-18
Well Gw isn't available for Steam, but suddenly things are going very wrong with Steam. Just a few minutes ago I played Half-Life 2 for a few minutes with no problems, then I exited it and tested CS: Source. Steam froze, so I had to end its process. Then I made that last post and relaunched Steam, but the other apps don't still work. Every single app on Steam permanently freezes Steam when I try to launch it now.

---

### Post by Cadeyrn on 2009-06-20
Well, as strangely as the Steam problem started, it's disappeared. Even CS: Source works now. But we still need to fix Guild Wars and STALKER Clear Sky.

To remind everyone of the problems, I'm running 64-bit WINE 1.1.20-23 (depending on what fix I'm trying now, but 20-23 all act the same on my computer) on x64 Jaunty. Guild Wars works in every way possible besides the fact that it crashes when it begins to load any area, rendering it unplayable. STALKER, upon launch, gives me the WINE version of the popular Windows error, "<app name> has encountered a serious problem and needs to close." The only x32 packages I'd need for x64 WINE that I don't have are the build dependencies, which are useless right now because I'm not trying to compile x32 WINE. Plus my computer isn't able to install them for some glitchy unknown reason.

The STALKER Terminal output, from launch to error message, is this:
```
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x113fd8 0
fixme:heap:HeapSetInformation 0x110000 0 0x32f990 4
```

The Guild Wars Terminal output from launch to crash is much longer, so it's an attachment.

And apparently Counter-Strike: Source refuses to work as well. It randomly crashes, but not until I join a server (any server). I know tons of people have this problem, but for me none of the fixes work. I've tried PulseAudio, ALSA, OSS, WINE 1.1.21, everything.

---

### Post by Cadeyrn on 2009-06-20
Come on! I need some help here! Well, since everybody has forgotten this topic, I'm making a new one.

[http://ubuntuforums.org/showthread.php?p=7490728#post7490728](http://ubuntuforums.org/showthread.php?p=7490728#post7490728)

---

### Post by NightMKoder on 2009-06-20
start the games with pasuspend. Pulseaudio just doesn't work well in wine.

pasuspend wine '....exe'

---

### Post by Cadeyrn on 2009-06-20
I have heard of pasuspend before and haven't tried it, but... BASH tells me there is no command called pasuspend. Shouldn't I have it???

---

### Post by NightMKoder on 2009-06-20
I think its in the pulseaudio-utils package. In the worst case its possible to completely remove pulseaudio.

---

### Post by Cadeyrn on 2009-06-20
Well, I already had pulseaudio-utils installed. Plus its description in Synaptic lists every command added, and pasuspend isn't in that list. I refuse to uninstall PulseAudio because it's awesome and I have WINE set to only use ALSA, not PA.

---

### Post by Cadeyrn on 2009-06-21
I would like a moderator to delete this thread, please.

---

### Post by NightMKoder on 2009-06-21
> **Cadeyrn said:**
> Well, I already had pulseaudio-utils installed. Plus its description in Synaptic lists every command added, and pasuspend isn't in that list. I refuse to uninstall PulseAudio because it's awesome and I have WINE set to only use ALSA, not PA.

Pulseaudio doesn't respect what wine says. wine says to use alsa, but pulseaudio takes over all alsa-directed stuff and attempts to emulate it. and fails miserably.

and apparently i mistyped. its "pasuspender" not "pasuspend"

---

### Post by cutterjohn on 2009-06-21
I get dumped out with the same error, but I'm blaming ATI ATM as I have a mobility radeon hd 4850 and a whole bunch of games that worked with nVidia products didn't work well at all with ATI + fglrx.

1.1.24 at least fixed the texture problems for me in X3 Reunion, but now I've got all the other "normal" wine problems that require use of native libraries to "fix", and the mouse still lags like mad(also normal for wine).

GW with 1.1.24 still bombs out for me just like with 1.1.22 & .23.

Do you have an ATI, nVidia, Intel, ... graphics card?

[EDIT]
Oh yeah, .24 still tries to "repair" the archive every startup for me still....
[/EDIT]

[EDIT2]
Using x86-64 9.04 Ubuntu plus pre-built 32b wine from their repos of the above listed versions...
[/EDIT2]

---

### Post by NightMKoder on 2009-06-21
> **cutterjohn said:**
> I get dumped out with the same error, but I'm blaming ATI ATM as I have a mobility radeon hd 4850 and a whole bunch of games that worked with nVidia products didn't work well at all with ATI + fglrx.

1.1.24 at least fixed the texture problems for me in X3 Reunion, but now I've got all the other "normal" wine problems that require use of native libraries to "fix", and the mouse still lags like mad(also normal for wine).

GW with 1.1.24 still bombs out for me just like with 1.1.22 & .23.

Do you have an ATI, nVidia, Intel, ... graphics card?

[EDIT]
Oh yeah, .24 still tries to "repair" the archive every startup for me still....
[/EDIT]

GW has a known problem with the newer wines. (1.1.22+: [http://bugs.winehq.org/show_bug.cgi?id=18675](http://bugs.winehq.org/show_bug.cgi?id=18675)) 

For your mouse, consider the useful registry keys has something about mouse warping, i think.

What "normal" wine problems do you have? There's really not too many of them anymore. As for ATI problems: the best you can do is change offscreenrenderingmode to backbuffer, until ati fixes their drivers (or radeon gallium becomes mesa master :D)

---

### Post by cutterjohn on 2009-06-21
> **NightMKoder said:**
> GW has a known problem with the newer wines. (1.1.22+: [http://bugs.winehq.org/show_bug.cgi?id=18675](http://bugs.winehq.org/show_bug.cgi?id=18675))I'm prettty sure that I checked there already and found nothing applicable, but I'll re-check again tonight to see if anything new turned up.  (Thanks for reminding of that.) [EDIT] hmmm... upon re-reading it would appear that I'm incorrect, so I must've just assumed that they'd fix that bug by now.  Maybe I should start building/patching my own version of wine from git... [/EDIT]

> For your mouse, consider the useful registry keys has something about mouse warping, i think.Maybe, but those would likley be global?  (Which is probably something I'd not want.  Easier to just see if I can get a USB gamepad going, and try re-memorizing the keyboard commands again.)

> What "normal" wine problems do you have? There's really not too many of them anymore. As for ATI problems: the best you can do is change offscreenrenderingmode to backbuffer, until ati fixes their drivers (or radeon gallium becomes mesa master :D)X3R specific, in that videos fail to play w/o amplayer.dll(IIRC), trading in stations fails without other native .dlls, some "registry" tweaks.  Lots of things that I don't really want to do, for general support reason although I suppose that I could run 2 swappable .wine directories(one "broken", and un"broken")

offscreenrendering-> backbuffer, yeah had to do that for .22 & .23.  I just checked .24 and it made no difference setting it to fbo or backbuffer, so I left it at fbo now.  (There was an ATI specific bugfix in .24)

I'm betting that ATI never manages to fix their crap as they'd need to fire their crew and poach all of nVidia's driver crew, but I'm stuck for now with ATI on my notebook until a) warranty runs outs, then b) I find a decently priced recent nVidia mobile MXM GPU, and c) have time/tools to fabricate a new heatsink attachment for it then d) enjoy the lush green nVidia drivers instead of the ATI bloody mess. (New desktop buid is going to be nVidia because of ATI's crappy support.)

---

### Post by NightMKoder on 2009-06-21
> **cutterjohn said:**
> I'm prettty sure that I checked there already and found nothing applicable, but I'll re-check again tonight to see if anything new turned up.  (Thanks for reminding of that.) [EDIT] hmmm... upon re-reading it would appear that I'm incorrect, so I must've just assumed that they'd fix that bug by now.  Maybe I should start building/patching my own version of wine from git... [/EDIT]

The code in question is not apparently wrong so noone has a clue as to why it's happening
> 
Maybe, but those would likley be global?  (Which is probably something I'd not want.  Easier to just see if I can get a USB gamepad going, and try re-memorizing the keyboard commands again.)

separate prefix (down)
> 
X3R specific, in that videos fail to play w/o amplayer.dll(IIRC), trading in stations fails without other native .dlls, some "registry" tweaks.  Lots of things that I don't really want to do, for general support reason although I suppose that I could run 2 swappable .wine directories(one "broken", and un"broken")

You don't need to swap. wine has built-in support for handling multiple .wine folders - ie:
```

WINEPREFIX=/home/mike/.wine_x3c wine x3c.exe
WINEPREFIX=/home/mike/.wine wine experiment.exe

```
would actually be two different installs of wine. You can install a program per prefix (called bottling) and then live happily without fear of accidentally nuking all your programs.
> 
offscreenrendering-> backbuffer, yeah had to do that for .22 & .23.  I just checked .24 and it made no difference setting it to fbo or backbuffer, so I left it at fbo now.  (There was an ATI specific bugfix in .24)

I'm betting that ATI never manages to fix their crap as they'd need to fire their crew and poach all of nVidia's driver crew, but I'm stuck for now with ATI on my notebook until a) warranty runs outs, then b) I find a decently priced recent nVidia mobile MXM GPU, and c) have time/tools to fabricate a new heatsink attachment for it then d) enjoy the lush green nVidia drivers instead of the ATI bloody mess. (New desktop buid is going to be nVidia because of ATI's crappy support.)

I don't know about ATI proprietary support, but OSS radeon modesetting code made it into kernel 2.6.31, so we may see some new developments in the OSS world of graphics :).

---

### Post by cutterjohn on 2009-06-21
> **NightMKoder said:**
> The code in question is not apparently wrong so noone has a clue as to why it's happeningAh, but I noted a second regression test pointing to the same change, then reverting in a new build apparently fixed it for that user.  Maybe it's an odd bug in the GW client...

> You don't need to swap. wine has built-in support for handling multiple .wine folders - ie:
```

WINEPREFIX=/home/mike/.wine_x3c wine x3c.exe
WINEPREFIX=/home/mike/.wine wine experiment.exe

```
would actually be two different installs of wine. You can install a program per prefix (called bottling) and then live happily without fear of accidentally nuking all your programs.I was sort of implying that, presumably that's what some of the playonlinux scripts(part of them anyways as they also apparently install misc. wine versions simultaneously) do although I haven't really looked closely at them.

meh, snipped the rest as this is getting to be a little close to derailing the OP topic... although I still wonder what hw/Ubuntu version he had...

---

### Post by whitetimer on 2010-04-16
> **cutterjohn said:**
> Ah, but I noted a second regression test pointing to the same change, then reverting in a new build apparently fixed it for that user.  Maybe it's an odd bug in the GW client...

I was sort of implying that, presumably that's what some of the playonlinux scripts(part of them anyways as they also apparently install misc. wine versions simultaneously) do although I haven't really looked closely at them.

meh, snipped the rest as this is getting to be a little close to derailing the OP topic... although I still wonder what hw/Ubuntu version he had...


Hi Cutterjohn 

I'm trying to get X3 Reunion working on Wine, but having issues with movies, voice etc ... Have you managed to get all working etc ?

:lolflag:

---


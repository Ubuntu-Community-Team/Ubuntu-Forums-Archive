---
title: "Install and configure World of Warcraft properly?"
date: 2010-05-12
forum: Wine
---

### Post by MarkH01 on 2010-05-12
I'm a half step shy of abandoning Windows to go full Ubuntu 10.04(amd64) on my home desktop.  The only reason I'm still keeping my windows install (and in it most of the time) is World of Warcraft.  I would turn my back on Microsoft completely if I knew for a fact that I could get WoW installed and configured.

I've been dual booting Windows and Ubuntu since 8.04 (in fact I built my desktop specifically for 8.04 in hopes of moving over back then.)  I've had mixed luck getting WoW to run properly.  I've used different wikis, installed PlayOnLinux, WINE Doors, used different tweaks and tricks I've found scattered around the web and I've had a plethora of issues from mildly annoying to down right unusable.  Stuttering animation, no sound, crackling sound, no mic, crashes when stepping outside, crashes only when stepping outside in Dal (that was a weird one), lost frame rates, random crashes, display issues, font issues, you name it and I've seen it broken.

Is there a set of directions that explains how to get a version of WoW running and configured correctly from scratch?

Is this current with 10.04?

Less important, but still wondering, does Vent work?

---

### Post by amohell on 2010-05-12
I have no idea what sort of configurations you are talking about but you can just copy the whole folder of world of warcraft from you windows drive to your linux drive and run the wow.exe with wine.

anyway wowwiki has a whole guide for it check: [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)
I found copying the easiest method although
it is explained in method 3, try working though those steps after changing some stuff in my config I got my wow working perfectly

and about ventrilo I found this at my first google search:
[http://ubuntuforums.org/showthread.php?t=41737](http://ubuntuforums.org/showthread.php?t=41737)
dont know if it works, but you could give it a shot

---

### Post by MarkH01 on 2010-05-12
Thanks for the quick reply.  Copying it over has been the most successful way for me as well.  I've set it to use OpenGL and told WINE it was Windows 7.  This has been my greatest success to date, but I have no audio.  So your mic and sound work with no issues?  I suppose this could be a driver issue, but Counter Strike: Source works great without changing anything...

Please bare with my n00bism, I don't have any issues getting in and mucking around in config files... I just don't know where they all are or what does what unless I can find an explanation on the web.

EDIT:: I found this for Vent.  Sorry for not effing googling it: [http://www.mangler.org/](http://www.mangler.org/)

I have been to that WoW-Wiki page though.  Just no love as of yet.

---

### Post by amohell on 2010-05-12
it might be caused by hardware(driver etc) problems but I wont recall myself an expert when it comes to wine, my wow worked perfectly including the sound(latest patch) when using the config and copying method. I cant remenber a moment when I had problems with it either.

But I gues a check for a new driver at your manufactor(of your video card) wont hurt. I gues it would be best to wait for an 'expert' since I was lucky to get it working in one shot;)[COLOR=#2f3699]
[/COLOR]

---

### Post by cburner on 2010-05-12
This may fix your sound and it may not. Open a terminal and type:```
padsp winecfg
``` Then tick the OSS box in the audio tab. If that does not work, run the same command but uncheck OSS and try ALSA.

Make sure you start WoW with padsp before wine as in:```
padsp wine "path/to/WoW/"
```

Good Luck

---

### Post by MarkH01 on 2010-05-12
That didn't work for the sound.  I had tried it already, but gave it another go just in case something I had done in the mean time had changed something... but it got me thinking...

under Windows Version drop down:

Win7 - stability but no sound
Win2008 - stability, no sound
Vista - stability, no sound
Win2003 - random crashes with no errors reported but sound
WinXP - random crashes with no errors reported but sound

So apparently the recoded drivers for vista and above changed something.  I know it was big jump with major overhauling on the windows side.

The underlying message I think I can take away is that it must be installed, see what breaks, then try and fix it.  That versus I'm just doing it wrong.  I may be, but it just isn't 'there' yet across the board.

---


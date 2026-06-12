---
title: "No sound comes out of jack server"
date: 2008-08-29
forum: Ubuntu Studio
---

### Post by lolzlolz on 2008-08-29
hey, whenever i run jack i don't get sound from any applications not from firefox, my normal desktop sounds, not even rosegarden.... when jack isn't running sound comes through fine... now this wouldn't be a problem if i weren't trying to use rosegarden for some music recording, but rosegarden says when i start it without jack that without jack running i can't play or record audio which ruins the point of rosegarden so anyway how do i get sound when jack is running
thanks

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > lspci

---

### Post by lolzlolz on 2008-08-30
I assume you would mean to run the command lspci from terminal.  If this is what you mean here are the results.
```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```
thanks

---

### Post by thorgal on 2008-08-30
> **lolzlolz said:**
> hey, whenever i run jack i don't get sound from any applications not from firefox, my normal desktop sounds, not even rosegarden.... when jack isn't running sound comes through fine... now this wouldn't be a problem if i weren't trying to use rosegarden for some music recording, but rosegarden says when i start it without jack that without jack running i can't play or record audio which ruins the point of rosegarden so anyway how do i get sound when jack is running
thanks

Firefox: the flash plugin is to blame. It only supports OSS (/dev/dsp), ALSA, esd or pulseaudio. No jack support in it.

Desktop sounds: they probably rely on the desktop manager being able to talk to an audio server (esd for gnome, artsd for KDE, pulseaudio nore recently). When jack is running, the desktop manager has to talk to it as jackd is handling all audio traffic to the lower level layer (ALSA or whatever jack backend you are using). 

Rosegarden is a jack aware app. So it relies on the jackd server for its audio throughput (the MIDI throughput is another story and relies more on the ALSA midi layer). So not running jackd makes RG useless.

There are ways to make all these antagonist entities talk to each other but you won't like the way to achieve this ... I think your safest bet is to get the new generic audio server called pulseaudio up and running and use the pulseaudio jack plugin so you can run jackd concurrently. There are threads about this very topic in this forum, but I don't have pointers.

---

### Post by lolzlolz on 2008-08-30
well i guess the only thing i need sound from is rosegarden when running jack, however jack isn't giving me sound from rg so this is the problem if pulse audio will fix this then i will do that but if not.... then there's no point 
thanks

---

### Post by jocheem67 on 2008-08-30
Way I got rid of most audio#$%^%&%& was by not using pulse:)

Used the "asoundconf list" command in the terminal to list my soundcards and after that "asoundconf set-default-card"  to select the chip I wanna....
Next I select alsa in soundpreferences and let pulse be quiet.

Then I fire up "qjackctl" ( it's in the repo's ) and in preferences there, or setup it's called I think , I just select the one card/chip I wanna use through jack. Somewhere on the right.

This way I keep things versatile, and all my applications work through alsa + jackd, that is ardour, mixxx, totem, rhythmbox....

Hope this helps.

---

### Post by lolzlolz on 2008-09-02
i tried this and it didn't change the situation still no sound :(

---

### Post by lolzlolz on 2008-09-03
i also tried setting up pulse audio, after I set it up is there a way or something i need to do with jack for it to work properly?

---

### Post by lolzlolz on 2008-09-19
bump

---

### Post by lolzlolz on 2008-09-25
bump....

---

### Post by markbuntu on 2008-09-27
You can get all your non-jack applications to play through pulseaudio and pulseaudio  to play through jack by following this guide.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---


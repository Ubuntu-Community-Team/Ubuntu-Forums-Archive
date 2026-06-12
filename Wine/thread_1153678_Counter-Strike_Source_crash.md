---
title: "Counter-Strike Source crash"
date: 2009-05-09
forum: Wine
---

### Post by Smasha on 2009-05-09
Hello everyone,

I'm trying to play counter-strike source on ubuntu but it crashes after 1-2 minutes of gameplay.
I'm using wine 1.1.20 and have installed the ATI 9.4 proprietary drivers. After some mucking around with some wine settings i figured out that CSS only crashes when the alsa driver is enabled in winecfg, so i upgraded alsa to version 1.0.20 to see if it helped, but it didn't.

Changing the driver to OSS makes CSS work without crashing, but there isn't any sound.

System specs: (incase they help)
Ubuntu 9.04 64bit
Intel Q6600
8gb ddr2 800 ram
ati HD 3450

I've also tried running CSS in win98/xp/vista mode but it doesn't help.

Does anybody know of any fixes for this?

Thanks.

---

### Post by cogadh on 2009-05-10
According to the information in the game's [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731"), this is a pretty common bug. You have to use ALSA for the sound (OSS doesn't work anymore), but you also need to disable PulseAudio and make sure the "Steam Community In-Game" features are disabled. If that doesn't help, run the game from the terminal and post Wine's output here, it might explain what is going on:
```
cd ~/.wine/drive_c/Program\ Files/Steam && wine steam -applaunch 240
```

---

### Post by Smasha on 2009-05-11
> **cogadh said:**
> According to the information in the game's [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731"), this is a pretty common bug. You have to use ALSA for the sound (OSS doesn't work anymore), but you also need to disable PulseAudio and make sure the "Steam Community In-Game" features are disabled. If that doesn't help, run the game from the terminal and post Wine's output here, it might explain what is going on:
```
cd ~/.wine/drive_c/Program\ Files/Steam && wine steam -applaunch 240
```

Thank's for the reply, i disabled pulseaudio and the steam community in-game and it still crashes. I can't post the output of the terminal because when it crashes it also locks up the system and i have to do a hard reset :( 

Also i installed OSS 4.1 and now the sound works with OSS, but when i installed OSS 4.1 my alsa drivers got completely disabled. I tried modprobe snd-hda-intel but it gives a bunch of errors, also tried reinstalling alsa but still doesn't work.

Btw, when i use OSS for sound Counter strike eventually freezes up like it did when i was using alsa..so now i think that maybe it wasnt just the sound drivers alone...i might just go and save myself some trouble by going and getting an nvidia card...

---

### Post by u235sentinel on 2009-05-11
> **Smasha said:**
> Thank's for the reply, i disabled pulseaudio and the steam community in-game and it still crashes. I can't post the output of the terminal because when it crashes it also locks up the system and i have to do a hard reset :( 

Also i installed OSS 4.1 and now the sound works with OSS, but when i installed OSS 4.1 my alsa drivers got completely disabled. I tried modprobe snd-hda-intel but it gives a bunch of errors, also tried reinstalling alsa but still doesn't work.

Btw, when i use OSS for sound Counter strike eventually freezes up like it did when i was using alsa..so now i think that maybe it wasnt just the sound drivers alone...i might just go and save myself some trouble by going and getting an nvidia card...

I'm running it under alsa and it works overall.  I've had issues with the mic.  It doesn't work but the game sounds work great. 

I had to drop back to 1.1.18 so other stuff works also (like oblivion is busted in 1.1.20 and 1.1.21).

also I have had bad experiences with ATI cards.  Might want to try running an nvidia and see if that helps.

---

### Post by Duskao on 2009-05-12
How do you disable pulse audio for running CS and HL2 and all those?

---

### Post by Smasha on 2009-05-12
> **Duskao said:**
> How do you disable pulse audio for running CS and HL2 and all those?

open terminal: kill pulseaudio

Also fixed all my problems by using an nvida card!

---

### Post by Duskao on 2009-05-12
desktop:~$ kill pulseaudio
bash: kill: pulseaudio: arguments must be process or job IDs

What does that mean exactly? Is Pulse Audio not running? Because it's still showing in "System Monitor"

I'm still getting the looping sound lockup in all the HL2 and various source games.

Alright guys, tried TF2 in the terminal (cause thats what I wanted to play) applaunch 440. But when it froze up I did the RSEINUB with alt+PrntScrn. But even when I rebooted I had nothing. Doesn't the screenshot usually end up on the desktop? Anyway, I tried all that with no avail, but that isn't saying I won't try it again. I think I just need a bit more information potentially. Maybe I am doing something wrong.

---

### Post by Amof on 2009-05-12
> **Duskao said:**
> desktop:~$ kill pulseaudio
bash: kill: pulseaudio: arguments must be process or job IDs


The kill command require a process ID number try this

```
sudo pkill pulseaudio
```

or

```
ps -A | grep pulseaudio
```

and then enter the Id number

```
sudo kill <ID given>
```

---


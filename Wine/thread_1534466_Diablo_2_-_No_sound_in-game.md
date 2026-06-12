---
title: "Diablo 2 - No sound in-game"
date: 2010-07-19
forum: Wine
---

### Post by ShadowMage on 2010-07-19
Hi everyone,

I am trying to get Diablo II: Lord of Destruction working in Wine and I've almost got it perfect, but I'm experiencing some issues with the sound.

When I run the program, I can hear the sound at first, but once I enter a game there is no more sound. And even if I exit back to the menu, there is still no sound, but if I close the program and re-open it then same like before (sound until I enter a game).

I'm using wine-1.2. If I run the game from terminal, I get the following output
```
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
$ fixme:advapi:SetSecurityInfo stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13c778,0x13c6d8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13c778,0x13c6d8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13c778,0x13c6d8): stub
```but this output happens right away and I don't get additional output when the sound gets "lost".

Has anyone gotten this to work, or anyone have any ideas?

---

### Post by valbaca on 2010-07-19
Once in game, try ESC and go to Options/Settings etc. I haven't played Diablo 2 in a while but there should be settings there for display and sound.
 
I'll try later today, see where it gets me, and post.

---

### Post by ShadowMage on 2010-07-19
Thanks for the reply, valbaca.

Unfortunately, it's not because of the in-game settings. Sound was at max and Music at half. Changing their values also doesn't help. I do appreciate the suggestion tho, it was worth a try.

Any other ideas out there?

---

### Post by valbaca on 2010-07-19
A couple more "shots from the hip" that are crazy enough to work
[LIST]
[*]Try turning up the volume using volume keys or hitting mute
[*]See if there is any sound coming from the headphone jack
[/LIST]Now I'm really eager to get home and pop in those old discs (Skelemancers ftw!)

---

### Post by ShadowMage on 2010-07-19
Thanks, but I still can't get it to work, unfortunately. Tried changing my system's volume, mute/unmute, plugging in headphones, etc. No dice :\

---

### Post by Goveynetcom on 2010-07-20
I can verify that the game does work under Wine with sound. Played it not to long ago. Have any other sound issues? And have you tried playing with Wine's sound settings?

---

### Post by asdfoo on 2010-07-20
pulseaudio may be the problem, try suspending or killing it

---

### Post by ShadowMage on 2010-07-21
Hi, thanks for the replies. With some research and experimentation, I think I've got a solution now.

The sound seems to work ok when only the OSS Driver is selected in winecfg (Audio tab). But then it doesn't let other sources (like firefox, for example) play sound. To fix this, I found [[COLOR="Blue"]this[/COLOR]](http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/) while searching, and by putting padsp in front of the command used to launch Diablo 2 it seems to work. For example, my launcher command is:
```
padsp env WINEPREFIX="/home/???/.wine" wine C:\\windows\\command\\start.exe /Unix /home/???/.wine/dosdevices/c:/users/???/Start\ Menu/Programs/Diablo\ II/Diablo\ II\ -\ Lord\ of\ Destruction.lnk -w
```(username replaced with question-marks for the purpose of posting)

Marking thread as solved.
Cheers :)

---

### Post by rebelrex on 2011-01-16
switching to oss didnt helped me
what did help me was changing Direct sound to "Emulation"
Applications->wine-> wine configuration->audio-> Direct Sound- "Emulation"

---

### Post by sgrin27 on 2011-01-17
Cool, Thanks for the fix. I added that prefix and it didn't work at first so I enabled BOTH ALSA and OSS drivers because my other games need ALSA. Now it works!

---

### Post by Spirit of Yggdrasill on 2011-06-11
Thanks man, adding prefix worked as a charm :):popcorn:

---

### Post by Kreedx on 2011-07-18
> **rebelrex said:**
> switching to oss didnt helped me
what did help me was changing Direct sound to "Emulation"
Applications->wine-> wine configuration->audio-> Direct Sound- "Emulation"

This is what fixed it for me, thanks.

---

### Post by HolgerB on 2011-07-23
> **rebelrex said:**
> switching to oss didnt helped me
what did help me was changing Direct sound to "Emulation"
Applications->wine-> wine configuration->audio-> Direct Sound- "Emulation"
Thanks...this fixed my vanishing sound also after a WINE upgrade. I have no clue what is causing this issue though. Esp. since D2 has always worked perfectly under WINE with different versions.

---

### Post by Supersonic Doom on 2011-08-02
I've actually go the same problem but the prefix didn't help.

padsp: in winecfg audio tests for all combinations fail, prefix for d2 command produces no sound, even in the initial menus

otherwise, alsa with emulation or full, either one, produces sound in initial menus, no sound in-game, and any combination involving OSS, prefixed or otherwise, fails.

the prefixed command produces 

err:oss:AUDDRV_GetEndpointIDs OSS /dev/mixer doesn't seem to exist

which I can only find mentioned in what look like patch notes of some sort.

Any ideas?

---

### Post by 4Orbs on 2011-08-02
In order to get Diablo2 sound working completely in Ubuntu 10.10 and 11.04, I found it necessary to install a Wine version that has been modified to include Pulseaudio support (it adds that option in the wine configuration utility, audio section). It is version 1.3 from the c-korn repository. First, add the repository by entering this in the terminal:
```
sudo add-apt-repository ppa:c-korn/ppa
```
then update your sources by entering:
```
sudo apt-get update
```
then you can either install wine 1.3 by using Synaptic Pkg Mgr or by entering in the terminal:
```
sudo apt-get upgrade
```

---

### Post by Supersonic Doom on 2011-08-02
Success!

I only ran into one hitch though, my wine1.3 was already 1.3.25, but the c-korn version was 1.3.18, and therefore wouldn't let me just upgrade to it. So Just a heads up if anyone ends up reading through this thread in the future, in synaptic package manager, I had to go to the installed package, open 'Package -> Force version', then choose 1.3.18. 
Opened winecfg to a plethora of driver options, pulseaudio among them, and now everything works like a charm ^^ 


Much appreciated all, especially 4Orbs

---

### Post by crimsonmane on 2012-01-24
These solutions did not work for me. After downgrading to the proper Wine version and selecting PulseAudio in the setup, I tested the game. Not only was there still no sound, but the screen was showing the desktop through the opening scenes. Alt-Tab would bring the game back to the foreground. The game would halt at the main menu screen. Upgraded to latest Wine again. I can play the game just without sound.

So this thread should be downgraded to [Un-Solved].

---


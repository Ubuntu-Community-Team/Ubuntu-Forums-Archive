---
title: "[SOLVED] Planescape Torment"
date: 2011-03-24
forum: Wine
---

### Post by Count-T. on 2011-03-24
Hello, I've spent my whole day figuring out how to launch Planescape Torment on Ubuntu through Wine and finally succeeded (it seems).

My setup:
Asus eeePC 1201N; Ubuntu 10.10 x86 Desktop edition; Wine 1.2.2.
Planescape Torment from Good Old Games (gog.com) (although I believe that provided solution should be also relevant for 4-CD version)

Problems encountered:
1) Game doesn't launch. It just changes resolution and then nothing happens.
2) Game launches, but not in fullscreen mode.
3) No sound during the game (background music, speech, etc.)

Solution:
0) Install the game in Wine. It should be pretty basic, so I'm skipping explanations here.

1) Go to Menu->Wine->Configure Wine. On Graphics tab check "Emulate a virtual desktop" and type in your actual screen resolution. And while we're here let's solve our sound-issue:

3) Go to Audio tab, check ALSA driver (or other driver if it doesn't work for you). Apply settings, then change Hardware acceleration mode to "emulation" and save settings.

2) Time to change resolution and apply game fixes and tweaks. We base our actions on a following guide:
[http://www.gog.com/en/news/mod_spotlight_planescape_torment_mods_guide/0/pp/a2e33d344f272e100d4a8efeabc7ae8a60a8ba7a](http://www.gog.com/en/news/mod_spotlight_planescape_torment_mods_guide/0/pp/a2e33d344f272e100d4a8efeabc7ae8a60a8ba7a)
However. I've been unable to install those fixes from terminal or even Wine due to some errors. So, we should apply a different strategy:
You need to login into Windows (separate installation or VirtualBox image - doesn't matter). Then install the game and apply fixes according to the guide. And final step is to copy your whole Planescape directory from Windows and replace your Wine folder with it (in my case it was ~/.wine/drive_c/Program\ Files/GOG.com/Planescape\ Torment/ )

Voila! Now you can enjoy the game in fullscreen and with sound. At least I hope that you can :)

All credits go to developers of Planescape Torment and mods and writers of the guide at gog.com

---


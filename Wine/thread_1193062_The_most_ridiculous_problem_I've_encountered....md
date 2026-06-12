---
title: "The most ridiculous problem I've encountered..."
date: 2009-06-21
forum: Wine
---

### Post by Cadeyrn on 2009-06-21
Steam used to run just fine. Then, while I was preparing Counter Strike Source to run through WINE, I added -alsa to the Steam shortcut to make sure it was using ALSA. When no sound came out of the games, instead of removing the -alsa I stupidly tampered with my audio settings. Steam and its games used to run just fine, but when I clicked on the Audio tab on winecfg and it told me to apply its automatic choosing of the correct sound driver, I clicked apply. Now Steam and its games both have no sound while other WINE apps do, and we all know that no sound causes major problems in Steam. Now every single game suddenly crashes except for Half-Life 2 and the source mods. No games at all have sound.

I've already tried marking the WINE package for complete removal in Synaptic, applying, and marking it for installation and applying, but the audio config is still the way I left it. How do I reset it so I can play my Steam games again? Because OSS, ALSA, JACK, NAS, EsounD, and any combination of them will not let my Steam have sound.

---

### Post by jhoeijao on 2009-06-21
> **Cadeyrn said:**
> Steam used to run just fine. Then, while I was preparing Counter Strike Source to run through WINE, I added -alsa to the Steam shortcut to make sure it was using ALSA. When no sound came out of the games, instead of removing the -alsa I stupidly tampered with my audio settings. Steam and its games used to run just fine, but when I clicked on the Audio tab on winecfg and it told me to apply its automatic choosing of the correct sound driver, I clicked apply. Now Steam and its games both have no sound while other WINE apps do, and we all know that no sound causes major problems in Steam. Now every single game suddenly crashes except for Half-Life 2 and the source mods. No games at all have sound.

I've already tried marking the WINE package for complete removal in Synaptic, applying, and marking it for installation and applying, but the audio config is still the way I left it. How do I reset it so I can play my Steam games again? Because OSS, ALSA, JACK, NAS, EsounD, and any combination of them will not let my Steam have sound.

Uninstall wine using the Synaptic for complete removal or you may use the terminal and type "sudo apt-get remove wine" after this you have to delete the .wine folder in your home folder Ctrl+H to unhidden files and delete .wine folder or you may type "rm -rf ~/.wine"

Note: Make sure that you have no other programs installed using wine or else it maybe affected after the uninstallation.

---

### Post by Cadeyrn on 2009-06-21
Thank you! I was thinking about doing that, but wasn't sure of the repurcussions. Someone else suggesting it gave me the courage to go for it, though, and now it works better than ever.

I think the real problem with all of my Steam games was the installation of random winetricks crap I didn't need, and I think I accidentally installed x32 1.1.23 on top of x64 1.1.20-22. Many times.

---

### Post by NightMKoder on 2009-06-21
Next time if you're messing around with something, consider installing your "working well" programs into a separate prefix:
```

export WINEPREFIX="/home/$USER/.wine_good" wine Setup.exe

```
This way when you want to get something working, you use your normal wine prefix, and once it works you can move it to your bottle.

Also - you don't actually need to remove wine itself. rm -rf ~/.wine is enough to clean everything.

---


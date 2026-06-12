---
title: "Wine sound problems"
date: 2011-05-30
forum: Wine
---

### Post by jakejw93 on 2011-05-30
two problems actually, the mouse jerks randomly a lot..but i sorted that by making the game windowed.

Then on a lot of steam games (half-life 2, day of defeat, counterstrike) there is no sound at all, anyone else experiencing this or have a fix?

latest version of wine!!

---

### Post by Perfect Storm on 2011-05-30
Moved to UF wine section.

---

### Post by bobwyajnr on 2011-05-30
> **jakejw93 said:**
> two problems actually, the mouse jerks randomly a lot..but i sorted that by making the game windowed.

Then on a lot of steam games (half-life 2, day of defeat, counterstrike) there is no sound at all, anyone else experiencing this or have a fix?

latest version of wine!!

Latest version isn't a very helpful way of describing the Wine version you are using! Numbers please! :)
[LIST=1]
[*]The 1.3.19 is one to use if you **don't** have a mouse warping issue.
The 1.3.20 release had a big fix for the (long running) mouse warping problem. It sadly breaks the X-input for the mouse in most games...
The 1.3.21 release (not yet in the Ubuntu PPA) includes further mouse fixes. I have only checked a Git Master (prior to the official release) but there was still unresolved mouse warping issues at that point...

[*] Have you run **winecfg** (usually in your *Gnome/Wine* menu) to see what ALSA audio device Wine will use for playback? You can also run that from the command line.
Have you played about with the **pavucontrol** applet? It allows you to see what audio streams PulseAudio is multiplexing and what device will be used as the default output.
Personally I don't use PulseAudio as it doesn't play nice with SPDIF-optical output pass-through. :)
[/LIST]

If you are not confident compiling from source there are always work arounds - like using a different PPA with an earlier release (e.g. [Wine+PulseAudio support]("https://launchpad.net/~runeks/+archive/winepulse")), etc.

I would pull the 1.3.21 release as soon as it is released! :popcorn:

Bob

---

### Post by jakejw93 on 2011-05-30
> **bobwyajnr said:**
> Latest version isn't a very helpful way of describing the Wine version you are using! Numbers please! :)
[LIST=1]
[*]The 1.3.19 is one to use if you **don't** have a mouse warping issue.
The 1.3.20 release had a big fix for the (long running) mouse warping problem. It sadly breaks the X-input for the mouse in most games...
The 1.3.21 release (not yet in the Ubuntu PPA) includes further mouse fixes. I have only checked a Git Master (prior to the official release) but there was still unresolved mouse warping issues at that point...
[*] Have you run **winecfg** (usually in your *Gnome/Wine* menu) to see what ALSA audio device Wine will use for playback? You can also run that from the command line.
Have you played about with the **pavucontrol** applet? It allows you to see what audio streams PulseAudio is multiplexing and what device will be used as the default output.
Personally I don't use PulseAudio as it doesn't play nice with SPDIF-optical output pass-through. :)
[/LIST]

If you are not confident compiling from source there are always work arounds - like using a different PPA with an earlier release (e.g. [Wine+PulseAudio support]("https://launchpad.net/%7Eruneks/+archive/winepulse")), etc.

I would pull the 1.3.21 release as soon as it is released! :popcorn:

Bob

well i use wine 1.3.20, but i will keep an eye out for the new release like i already have been doing so..and i have use winecfg - i usually go to that instantly with sound problems within wine. i will try a few more things and if the update comes along i will make sure to post my results back on here...

---

### Post by bobwyajnr on 2011-05-30
> **jakejw93 said:**
> well i use wine 1.3.20, but i will keep an eye out for the new release like i already have been doing so..and i have use winecfg - i usually go to that instantly with sound problems within wine. i will try a few more things and if the update comes along i will make sure to post my results back on here...

I am sure you read the subforum stickies :p But just in case you didn't... You can [pull older .debs of Wine]("http://ubuntuforums.org/showthread.php?t=871535"). Just uncheck the Wine PPA in the Synaptic repositories and uninstall your existing (PPA) Wine first. Wine 1.3.19 should fix the mouse issues (like I mentioned before).

Bob

---


---
title: "Diablo 2 LOD black screen"
date: 2010-05-02
forum: Wine
---

### Post by tbiddy on 2010-05-02
Anyone else having this problem?
starts up and goes to a black screen. cant even get to the main menu
quits game when i press spacebar.
taking any advice

edit:using 10.04 version of Xubuntu if helps anything

---

### Post by 3etamax on 2010-05-02
Hi,

Ive just been trying to get D2 working on 10.04 too, I found it only works for me if I run it in windowed mode. Just put -w at the end of the launch command:

env WINEPREFIX="/home/alexander/.wine" wine "C:\Program Files\D2\Diablo II\Diablo II.exe" -w

Also I changed the audio in wine to OSS as I didnt get any sound coming through the game, although you may need to change yours to alsa depending on soundcard.

:)

---

### Post by UnderPantGn0mes on 2010-06-09
ight i found an easy fix to the whole black screen full screen problems :P

winecfg
graphics tab
then uncheck Allow the Window manager to control the windows
----- i also unchecked Allow DirectX to stop the moust leaving their window

i got lag now trying to figure out how to fix that will post when i find that answer aswell :)

---

### Post by Soulcage on 2010-06-10
Try running the game in glide mode with a glide wrapper [http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html"). It worked perfectly the last time I tryied.

---


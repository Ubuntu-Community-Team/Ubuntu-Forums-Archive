---
title: "Morrowind on wine"
date: 2010-03-09
forum: Wine
---

### Post by Z0n3br34k3r on 2010-03-09
Funny i just fresh installed ubuntu updated - installed drivers and so on...got wine down installed morrowind got some errors then installed all again...then i though new wine was problem it isn't problem is with missing direct x files -.- i had to install specific direct x into wine from oblivion cd so that morrowind now runs without problem!even setting controls and all just fine only some minor on npc skin and doors..

---

### Post by NightwishFan on 2010-03-09
Even on Wine 1.01 Morrowind works excellent for me. The only issue is with pulseaudio which glitches. You can fix by opening regedit and adding this key: (Create if does not exist)

```
Software -> Wine -> Alsa Driver -> UseDirectHW
```
Set to: y

This page is a reference:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Z0n3br34k3r on 2010-03-09
Seem that problem with the game isn't always same cause i had sound problem but since installed direct x from oblivion cd now runs without fail

---

### Post by Z0n3br34k3r on 2010-03-09
Here just useful since you don't know what directx you need for which game list of some them

[http://filehippo.com/download_directx/](http://filehippo.com/download_directx/)

---

### Post by NightwishFan on 2010-03-09
I do not recommend installing DirectX in Wine, even though it can rarely fix some issues it will probably cause more.

---

### Post by Progressive on 2010-03-10
Usually the only dll for Morrowind you need is msvcp60.dll which you can just grab from either your windows partition or through a site like dll-files. 

Then you install it into ~/.wine/drive_c/Windows/System32

You do not need anything extra.

---


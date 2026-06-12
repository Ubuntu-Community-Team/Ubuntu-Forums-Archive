---
title: "World of Warcraft scratchy sound"
date: 2010-10-06
forum: Wine
---

### Post by ze3rax on 2010-10-06
Hello,

I finally managed to run WoW in Linux but when I start the game I hear awful scratchy sound, in addition to that when I try to configure the Game Sound Output from Options in logging screen changing "devices" there's that sound also... it's like something is not plugged in right ( I'm using my internal laptop speakers )

Using Wine 1.3.4

The changing the size of SoundBuffer is not helping also:
SET SoundOutputSystem "1"  
SET SoundBufferSize "150"

---

### Post by ze3rax on 2010-10-07
No one knows what causes that sound problem ?!?

---

### Post by Rody on 2010-10-07
no clue, but you could try changing your sound in winecfg from oss to alsa or the other way around.

rody

---

### Post by ze3rax on 2010-10-07
Thanks, tried it already. Now with winetricks installed I have no sound and audio options have only System Default...  Lucky me... what to do ? To uninstall Wine and it's components or what :?

---

### Post by cwwilson721 on 2010-10-07
What windows system are you using? (WinXP, Vista, Win7,2000?) I use XP, works perfect. WoW seems to like it

---

### Post by Aydos on 2010-10-09
I am wondering if I am having the same problem as you. Basically with me after I have been playing a bit the sound goes to like a weird under water/scratchy/sonar sounding noise. If I go under sound in preferences and turn off the sound and back on it fixes the prob temporarily and it comes back. It also makes my mangler sound funny when it happens.

I tried setting wine to OSS and it seemed to work except it made my audio go from my USB headset to my monitor. I need for it to come out of the headset in OSS anyone know what to do?

---

### Post by Rody on 2010-10-11
click on your sound horn in your task bar, select sound preferences, then select the out put tab and select your usb headset there.

---

### Post by Hairy_Palms on 2010-10-12
i had this problem when my win version was set to windows 7, i turned it back to XP and it stopped.

---


---
title: "ncrypt.dll full of unimplemented functions"
date: 2011-01-03
forum: Wine
---

### Post by AngelDE98 on 2011-01-03
Hello everyone . I have one of the NOT-WANTING-TO-GO-AWAY errors . I always get ... ```
wine: Call from 0x7b839192 to unimplemented function ncrypt.dll.BCryptOpenAlgorithmProvider, aborting
err:module:DelayLoadFailureHook failed to delay load ncrypt.dll.BCryptOpenAlgotithmProvider
``` ... when installing WMP10 or .net 3 ... On WMP10 it loops the bottom install bar and the top is stuck at 15% . I am installing .net 3 now . .net 2 installed normally . I have some problems with sound , too but this is another thing ... Ok , I post my error here too ... ```
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014

``` The sound stutters like hell in Wine ( I use ALSA and I use my USB headphones with DMIX / Software Mixing ... ) . Yeah , I have an full Error House ... Error , Error and this is my latest ... 

Oh , I use now Wine 1.3.10 but 1.2.2 gives me the same . I have Vista installed , too if it is important . I tried the Vista dll ncrypt.dll but same error . Please help me ! I am sooo close to play Need for Speed World ( NFSW ) on Ubuntu ( It runs on Windows ) because Windows games are running faster than on Windows ( Compare : 
- UltraHD Game on Windows with Full Graphics : LAAAAGGGG 
- UltraHD Game on Ubuntu , Wine and with PixelShader : SMOOTH 
) 

Thanks for any help .

EDIT : .net 3 got stuck just 4 pixels before the end !!! :mad:

---

### Post by cogadh on 2011-01-03
Check Wine's Application Database, much of what you are trying to install/run does not work in Wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by AngelDE98 on 2011-01-03
Lol ... The .Net Framework 3 ... It is accessible as ```
winetricks dotnet30
``` 
And it is just bronze ... But the error affects other errors , too . 

I installed WMP9 flawlessly , but with 
```
winetricks wmp10
```
it gives me the same ... Even the same as dotnet30

And the sound stuttering ... It was not before 2 weeks ... 

I think this DLL is corrupted or something . Do I need to replace it with an special one ?

---

### Post by cogadh on 2011-01-03
No, that won't help. You are trying to install and run software in Wine that it simply is not capable of running yet. No amount of tweaking or changing of DLLs will change that, the Wine code itself needs to be improved before that will happen.

As for the sound stuttering, that really could be any number of things, but it most likely has something to do with PulseAudio of ALSA, not Wine.

---

### Post by AngelDE98 on 2011-01-03
Umm ... No coding , just reinstalling Wine from scratch ... 

I garbaged my system with my Vista DLLs and DLLs from other sites ... Just reinstalling the WHOLE Wine helped me ...

---


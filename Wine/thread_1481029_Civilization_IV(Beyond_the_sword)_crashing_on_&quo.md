---
title: "Civilization IV(Beyond the sword) crashing on &quot;init engine&quot;"
date: 2010-05-12
forum: Wine
---

### Post by amohell on 2010-05-12
[FONT=Arial]hello,

After installing civilization IV succesfully (Civilization IV works perfectly). I installed beyond to the sword and warlods, after that I updated them with the latest patches but the same error still appears (when the loader comes to the "init engine" it crashes, the crash looks as following:
[http://www.youtube.com/watch?v=6uj0qg2Qx-U](http://www.youtube.com/watch?v=6uj0qg2Qx-U)[/FONT](the crash happens at circa 0:35 sec))[FONT=Arial]

[/FONT][FONT=Arial]
After checking the support websites, like winehq and the ubuntu forums, the solutions sugested there didn't  fix my problem it still crashes when the loader comes to "init engine"[/FONT].
[FONT=Arial] My warlords has the same sort of error as beyond the sword, the weird error once appeared with context and said the following:[/FONT][B][FONT=Arial] Failed to Initialize Renderer - check directx version and  graphics settings

[/FONT][FONT=Arial]thanks,

Amohell
[/FONT][/B]

---

### Post by hseara on 2010-05-12
I have exactly the same problem. My Civ IV was totally operative, but one of the last wine update has broke it. Please help

---

### Post by amohell on 2010-05-13
bump

---

### Post by amohell on 2010-05-17
last bump, does really no one know a sulution to this problem?

---

### Post by 8Kuula on 2010-05-17
Do you have d3dx9 installed from winetricks?

---

### Post by amohell on 2010-05-17
after trying to reinstall directx I came to the conclusion to try to run it with the new kernel of ubuntu released around these days, for some reason it started working now might have been a quick bug fix although I'm a really happy civilization player!.

although thanks alot for the reply,

Sander881

---

### Post by z0wb13 on 2010-08-20
hi. new to ubuntu and the forums, but i solved the installation problem and everything seems to run right under wine. i'm not sure how well or how long, because now i have another problem with my graphics card and drivers (sapphire radeon 3850). it seems like i finally got the 3d acceleration on, but the shading is totally wrong. the playerheads look like liquid metal terminators, and the map is black with floating/colored resources. 

anyway, to install it is easy. you will need:
ubuntu 10.04
civ4- vanilla disc
civ4 bts disc
civpatch1.74_final.exe 
civ4beondtheswordpatch3.19.exe

i didn't bother installing the warlords. if you really want to play the barbarians mod, there is a version for bts.

the absolutely first thing you should do is open system>administration>system_monitor. you will be using this to kill the DRXInstaller.exe. or DXUPDTE something along those lines. i did it last night after many hours of trial and error, so the details are a little fuzzy.  

if you haven't even installed WINE yet:> sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get  update
sudo apt-get  install wine1.3first, install civ4 vanilla by launching setup.exe on your disc using wine program launcher. agree to the terms, do an express install, then wait for the installer to freeze after telling you that you need to update directx. once it's frozen, go to system_monitor, and under the processes menu, kill the directx updater. if you have trouble finding it, list processes by CPU usage and it should be at the top. installation should continue normally. 

step two is to update civ vanilla to the latest version, so the bts installer won't try to do it for you. just launch the updater with wine.

step three is to install bts from disc, by launching setup.exe. agree to the license, and you will have the same problem with it wanting to install directx, just kill it in system monitor again. installation should continue normally. 

step four is to update bts to version. a BIG NOTE: uncheck any extra options that appear during installation. so don't join gamecomrade or the firaxis newsletter either. you can do that later if you really want to. 

alright, it probably took half an hour, but your done! not really! i too had the problem of loading during init engine. to fix this you will need winetricks. lss:
> wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
chmod +x winetricks


now, somebody help me with my graphics issues, so that i can actually play the darn thing.

---


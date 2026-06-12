---
title: "Counter Stike 1.6 ubuntu 9.10 please help"
date: 2009-12-05
forum: Wine
---

### Post by hardfire_avk on 2009-12-05
Ok, this thing has been driving me crazy, i have wine 1.0.1 installed,
installed counter strike 1.6, starts well but freezes after loading the map.

I have a AMD Athlon X2 processor,
2 GB Ram
Nvidia Geforce go 6150 card
graphics card driver is version 185 , as showin in hardware drivers window

this is what the terminal says
```
avinash@avinash-laptop:~$ env WINEPREFIX="/home/avinash/.wine" wine "C:\Program Files\Valve\hl.exe" -nomaster -game czero -heapsize 1024000 &
[1] 22330
avinash@avinash-laptop:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x32f5e8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:shdocvw:ViewObject_SetAdvise (0x153c08)->(1 00000002 0x7c65c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x153c08)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x153c08)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x153c08)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1cfef8)->(1 00000002 0x102ce98)
fixme:shdocvw:PersistStreamInit_InitNew (0x1cfef8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1cfef8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1cfef8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1d0d50)->(1 00000002 0xfcbf08)
fixme:shdocvw:PersistStreamInit_InitNew (0x1d0d50)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1d0d50)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1d0d50)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1cfef8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1cfef8)
fixme:shdocvw:OleObject_Close (0x1cfef8)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x1d1030)->(1 00000002 0x1017eb0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1d1030)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1d1030)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1d1030)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1d0d50)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1d0d50)
fixme:shdocvw:OleObject_Close (0x1d0d50)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1d1030)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1d1030)
fixme:shdocvw:OleObject_Close (0x1d1030)->(1)
^C
[1]+  Terminated              env WINEPREFIX="/home/avinash/.wine" wine "C:\Program Files\Valve\hl.exe" -nomaster -game czero -heapsize 1024000

```

---

### Post by hardfire_avk on 2009-12-05
oh! common someone !!!

---

### Post by beastrace91 on 2009-12-05
[Upgrade your Wine Version](www.winehq.org/download/deb)

Regards,
~Jeff

---

### Post by hardfire_avk on 2009-12-06
still no progress !!

---

### Post by hardfire_avk on 2009-12-06
Ok! here i am , i finally updated wine, have both Valve and counter strike source installed on wine. This is the problem that i am facing
1) IN valve : if i disable all sound, it works awesome. but even OSS freezes the game. so i shud say it works but weithout soung
2) for Counter strike source, the problem is that, it cannot detech a network and on 'slist', i see my ip as 127.sth.sth.sth.

So, how do i solve these problems

---

### Post by hardfire_avk on 2009-12-06
one more thing, with heapsize as -heapsize 300000 , i get errror as cannot allocat 286.sth MB of memory !!why is that so !

---

### Post by hardfire_avk on 2009-12-07
anyone! any idea .. need to solve this !

---

### Post by gradinaruvasile on 2009-12-07
The sound problem is because of pulseaudio. It doesnt work right with wine. Loose PulseAudio if you dont have bluetooth headsets/multiple sound cards. Use ALSA only, it works really well.

Launch the game without heapsize and stuff, only "-game whatever".
I have both CS and CS:Source working well with wine but i use Ubuntu 9.04 (ALSA only) and i wont upgrade soon...

Do not install directx. Just download the dll's (and put them in the windows/system32/ folder) wine asks for.

---

### Post by hardfire_avk on 2009-12-07
removed pulse audio and the heapsize thing. still no success. the game freeze , or better goes very very very slow when ALSA or OSS enabled . !!

---

### Post by gradinaruvasile on 2009-12-07
> **hardfire_avk said:**
> removed pulse audio and the heapsize thing. still no success. the game freeze , or better goes very very very slow when ALSA or OSS enabled . !!

Rename your .wine folder. Its in your home folder.

open a terminal and type

winetricks
select directx9
set alsa to driver in winecfg.

Install Cs (one of them).


Launch the game in a terminal:

cd /path/to/game/
wine game.exe

what output do you have there?

When you talk about sound do you refer to the actual game or the launcher?

---

### Post by hardfire_avk on 2009-12-08
i mean after the game starts. it connects to server , gives the view and freezes . and yah! tried the winwtrick thing ..dindnt work. had to download winetrick. !!

---

### Post by gradinaruvasile on 2009-12-08
Do you have the wine-gecko package installed?

sudo apt-get install wine-gecko

---

### Post by hardfire_avk on 2009-12-08
the gecko package was not installed, installed it bus still see no progress !!

---


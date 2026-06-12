---
title: "Wow Low frame rate?"
date: 2009-05-07
forum: Wine
---

### Post by rob2nd9th on 2009-05-07
Ok iv trawled through god know many threads and im still lost.

 I'm running 9.04
I have an Acer Aspire 5720

wine 1.1.20

my fps is approx 8-9 

Any help most welcome

---

### Post by asdfoo on 2009-05-07
> **rob2nd9th said:**
> Ok iv trawled through god know many threads and im still lost.

 I'm running 9.04
I have an Acer Aspire 5720

wine 1.1.20

my fps is approx 8-9 

Any help most welcome

Which video card and drivers? Looking at google this laptop comes with an intel video card which do not work as well under Linux as Windows, which is the reason for your low framerate.

The only thing I can suggest is trying with the -opengl switch to WoW.

---

### Post by rob2nd9th on 2009-05-08
> **asdfoo said:**
> Which video card and drivers? Looking at google this laptop comes with an intel video card which do not work as well under Linux as Windows, which is the reason for your low framerate.

The only thing I can suggest is trying with the -opengl switch to WoW.

Hows that done?

---

### Post by t.rei on 2009-05-08
append it to the start-link:

```

wine /home/username/.wine/drive_c/Programme/World\ of\ Warcraft/Wow.exe -opengl

```

also you can add this to the config.wtf :
```

SET gxAPI "OpenGL"

```

this is supposed to be redundant, but I think there might be some settings that do not apply one or the other. So setting both is probably the best way.

---

### Post by rob2nd9th on 2009-05-08
The shortcut properties is 
env WINEPREFIX="/home/rob/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"

if i add

env WINEPREFIX="/home/rob/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl

it freezes up when i click it?

---

### Post by asdfoo on 2009-05-08
> **rob2nd9th said:**
> The shortcut properties is 
env WINEPREFIX="/home/rob/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"

if i add

env WINEPREFIX="/home/rob/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl

it freezes up when i click it?

if your machine freezes then that's down to the buggy video drivers, I'm not sure there is much else you can do except better research your hardware requirements in the future

---

### Post by rob2nd9th on 2009-05-09
> **asdfoo said:**
> if your machine freezes then that's down to the buggy video drivers, I'm not sure there is much else you can do except better research your hardware requirements in the future

Yep wise words, the game was bought for me as a prezie. and despite the hassle i enjoy playing - look like a new laptop is on the cards.

---

### Post by asdfoo on 2009-05-09
> **rob2nd9th said:**
> Yep wise words, the game was bought for me as a prezie. and despite the hassle i enjoy playing - look like a new laptop is on the cards.

There's always the option of dual booting, pretty sure people play WoW on intel cards with Windows.  

But if you do get a new laptop, nvidia is the way to go for the moment.  ati is still likely to be some way off from being as reliable as nvidia.

---


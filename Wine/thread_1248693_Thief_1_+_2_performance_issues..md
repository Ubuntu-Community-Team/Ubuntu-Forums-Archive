---
title: "Thief 1 + 2 performance issues."
date: 2009-08-24
forum: Wine
---

### Post by naikon89 on 2009-08-24
Hi, I have been playing Thief 1 + 2 under wine lately, and while
it runs well, performance is kinda bad. I have an 8600GTS with 3gigs of ram and a AMD 4400+

Considering that it is a old directX game, has anyone improved performance 
when using resolutions above 1024x768? Should I contact the crossover people?

Regards.
naikon89

---

### Post by castlefox on 2009-08-24
That weird because I had not problems running Theif 2 on my old Intel inter-graded card.  

What version of WINE are you using?

I did not have any problems with 1.0.1



Is there anyway you can tell how many frames per sec you are getting?

Are you using the non-free drivers or the open source ones?

---

### Post by naikon89 on 2009-08-24
> **castlefox said:**
> That weird because I had not problems running Theif 2 on my old Intel inter-graded card.  

What version of WINE are you using?

I did not have any problems with 1.0.1



Is there anyway you can tell how many frames per sec you are getting?

Are you using the non-free drivers or the open source ones?



I am using 1.1.26

Can't use fraps with wine, but I will try to find a solution.
Even at 1024x768 it feels a bit laggy.

It just feels very laggy at resolutions at 1024x768 and above.
I thought it would run higher than this.

I only use non-free Nvidia drivers on a gaming machine to boot.
Myabe there are dependencies on native dll'&#353; to boost performance?

---

### Post by Brebs on 2009-08-25
Use ddfix, to convert Thief's 16-bit calls to 32-bit. IIRC, that helped me.

[http://forums.nvidia.com/lofiversion/index.php?t30515.html](http://forums.nvidia.com/lofiversion/index.php?t30515.html)
[http://www.ttlg.com/forums/showthread.php?t=117616](http://www.ttlg.com/forums/showthread.php?t=117616)
[http://ttlg.com/forums/showthread.php?t=121449](http://ttlg.com/forums/showthread.php?t=121449)
[http://timeslip.chorrol.com/ddfix.html](http://timeslip.chorrol.com/ddfix.html)

I run Thief 2 with:
```
export WINEPREFIX=$HOME/.wine-thief2
# Turn off the tons of error messages
export WINEDEBUG="fixme-all,err-all"
dir="$WINEPREFIX/drive_c/Program Files/Thief2"
export __GL_SYNC_TO_VBLANK=1
nvidia-settings -a SyncToVBlank=1 -a XVideoTextureSyncToVBlank=1 -a FSAA=5 -a FSAAAppEnhanced=1 -a FSAAAppControlled=0
cd "${dir}" && taskset -c 1 /usr/bin/wine thief2
```
That "taskset" command makes the game run on *ONE* CPU core, because the game is unstable otherwise (it was written in the days before dual-core CPUs).

---

### Post by naikon89 on 2009-08-25
> **Brebs said:**
> Use ddfix, to convert Thief's 16-bit calls to 32-bit. IIRC, that helped me.

[http://forums.nvidia.com/lofiversion/index.php?t30515.html](http://forums.nvidia.com/lofiversion/index.php?t30515.html)
[http://www.ttlg.com/forums/showthread.php?t=117616](http://www.ttlg.com/forums/showthread.php?t=117616)
[http://ttlg.com/forums/showthread.php?t=121449](http://ttlg.com/forums/showthread.php?t=121449)
[http://timeslip.chorrol.com/ddfix.html](http://timeslip.chorrol.com/ddfix.html)

I run Thief 2 with:
```
export WINEPREFIX=$HOME/.wine-thief2
# Turn off the tons of error messages
export WINEDEBUG="fixme-all,err-all"
dir="$WINEPREFIX/drive_c/Program Files/Thief2"
export __GL_SYNC_TO_VBLANK=1
nvidia-settings -a SyncToVBlank=1 -a XVideoTextureSyncToVBlank=1 -a FSAA=5 -a FSAAAppEnhanced=1 -a FSAAAppControlled=0
cd "${dir}" && taskset -c 1 /usr/bin/wine thief2
```That "taskset" command makes the game run on *ONE* CPU core, because the game is unstable otherwise (it was written in the days before dual-core CPUs).

Thanks. Just wondering though, how do you deal with no cd executables?

I can patch the original executable, but the no cd .exe won't patch because 
the string DDRAW.DLL is nowhere to be seen in the hacked executable. 

Cheers,
naikon89

---

### Post by Brebs on 2009-08-25
Here it is [conveniently pre-patched](http://www.johnanthonycurran.com/gamemods.html#thief).

---

### Post by naikon89 on 2009-08-26
Thanks Brebs. Performance and stability seems a bit better now at 1280x1024
after using the pre patched executable with ddfix.

Thanks again for the help.
naikon89

---


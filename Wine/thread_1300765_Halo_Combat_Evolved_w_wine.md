---
title: "Halo: Combat Evolved w/ wine"
date: 2009-10-25
forum: Wine
---

### Post by umby24 on 2009-10-25
Ok, so I've read many different forums on how to get things running, but it doesn't seem to be working right.

theres no solid answers on google, so I am going to post here.

Ubuntu 9.04
 - Intel pentium dual core
 - Intel graphics card (unknown model)
 - 1.5 GB ram

WINE 1.0.1

Halo Combat Evolved 1.08


Ok, so after getting mfc42.dll from my windows partition, and putting it into the system32 folder of wine,

the halo installer ran perfectly fine, no issues at all.

Then I ran halo 

(I have tryed this many different ways, from just the normal file browser, to command line using these 2 commands:

env WINEPREFIX="/home/tommy/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" -vidmode 1024,768,50 -novideo -use14



WINEDEBUG=-all wine explorer /desktop=nose,1024x768 "C:\Program Files\Microsoft Games\Halo\halo.exe" -vidmode 1024,768 -use14 -console 


)


Every single way (the 3 that I have tryed)

I have gotten this:

Halo starts, Intro movies play perfect..

Then the main menu shows up and everything looks horrible, the sound I hear just keeps repeating like a broken record, the first 2-3 seconds of the intro music.

where the Campain.. Multiplayer.. profiles.. settings  should be,

its just white blocks.

I can't see the halo, nor the planet that its orbiting (intro backround)

there is no halo logo at the top, and then after a few seconds, some random colors start showing up, and my normal non-wine cursor shows up.

after clicking the x and nothing happening I had to alt + f4 to make it quit.


Using the termnial commands it had some output, which is:

```

tommy@tommy-laptop:~/.wine/drive_c/Program Files/Microsoft Games/Halo$ WINEDEBUG=-all wine explorer /desktop=nose,1024x768 "C:\Program Files\Microsoft Games\Halo\halo.exe" -vidmode 1024,768 -use14 -console 
get fences failed: -1
param: 6, val: 0
Mesa 7.4 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org

```

and yet halo is getting platinum ratings on wine-hq. :confused:

any help would be greatly appreciated.

---

### Post by edin9 on 2009-10-26
Ugh. To be blunt, if it's a desktop buy a nVIDIA card (if your PC can take one). If it's a laptop stick with Windows.

---

### Post by spoons on 2009-10-26
I'd try with a newer Mesa and see if that helps. The easiest way to do it would be to upgrade to 9.10, but you can probably compile it if you don't want to do that.

---

### Post by umby24 on 2009-10-26
its a laptop, and whats a 'Mesa'

---

### Post by hikaricore on 2009-10-26
That would be a video driver.

---


---
title: "Blender problem"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by martin.burianjr on 2009-11-18
Hello all,
nice to see a support forum! I migrated from windows recently (very annoying system btw), so I'm a sort of new to unix. Anyway, I'm a blender person, so I installed blender from the default repository. When I ran the windowed version, the GUI behaved in a very strange way. It took quite some time to react, some of the controls even didn't work (like windowtype switching or the number selection boxes with the two little arrows on the sides). So I tried fullscreen version. There the GUI worked just fine, but blender thought he was still in a window, so all the mouse reactions were offset by the height of the top panel and at the bottom of the window the taskbar or how do you call it reacted instead of blender.
I have Radeon HD4850 with the drivers offered by ubuntu installed and running. The main 3D window behaved a bit better, so it should'nt  be an OpenGL problem, am I right? I also tried a random 3D openGL game from the repository, something with aliens, and it did work, even though there were some graphics issues when i tried to change some graphics settings of the game.
Sorry for such a long description, but i can't make it any shorter.
So, Is there anybody out there knowing what did I do wrong?

---

### Post by saidinesh5 on 2009-11-18
hey, have you tried running blender after switching desktop effects off? the last time i had a problem with blender on ubuntu , long time ago, it was due to a problem with the desktop effects. so simply 
1)right click on the desktop >
2)change desktop background> visual effects > 
3)select None.

now run blender . if it still doesnt work, we'll look up for an alternate solution :)
good luck :)

---

### Post by cotcot on 2009-11-18
An alternative is to download blender from the blender website for your version of synaptic, extract the file and very simple run the blender executable in the extracted folder without anything to be installed. It could be that sound does not work. (it is known with blender under linux). You can solve this by starting blender as ```
blender -g noaudio
```

---

### Post by xtracool_protik on 2009-11-18
@martin.burianjr
 As saidinesh5 said just right click on fusion icon 
 Select Window Manager --> Metacity and then try running blender
 U may lose all 3D effects and stuff but after u r done with blender u can set it back to compiz.
 I'm not a blender person but this method solved me Blender UI issue for me.

[EDIT]: However Ubuntu 9.10 seems to run it quite good

---

### Post by martin.burianjr on 2009-11-19
Thanks to all,
turning off the fx did the job, and I think I'll stick to the no-fx Ubuntu, I'm not a fan of all the graphical stuff... And some more thanks for such a fast reply!

---


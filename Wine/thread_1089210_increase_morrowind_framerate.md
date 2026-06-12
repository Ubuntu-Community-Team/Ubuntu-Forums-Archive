---
title: "increase morrowind framerate"
date: 2009-03-06
forum: Wine
---

### Post by juanoleso on 2009-03-06
Hi all,

I hate having to dual boot, but my framerate in morrowind with wine wavers between 5-15 fps with 1024x768 while I get between 25-30 in windows.  I am almost certain my drivers are working cuz I can play UrT4 and CoD (original) perfectly (CoD in wine is amazing, works just as well as in windows).

I've followed all the suggestions at [[COLOR="Blue"]Morrowind:Linux - UESPWiki[/COLOR]]("http://www.uesp.net/wiki/Morrowind:Linux").  Does anyone have any suggestions on how to increase my fps?  Am I out of luck?

Specs as follows
```

nvidia 5700LE 512MB
1 GB DDR RAM
Athlon XP 1800 (i believe) single core OC'd to 2 GHz

```

Thanks in advance

---

### Post by juanoleso on 2009-03-09
[OpenMW - Open Source Morrowind reimplementation]("http://openmw.sourceforge.net/jaws/")

I found this site after I posted here.  It looks very promising (although not helpful to my current situation) and I can't wait until they finish.

---

### Post by Progressive on 2009-03-09
Yes, OpenMW is coming along nicely. Their new version landed a few days ago. The menu system is the spitting image of Morrowind's

However, there are some ways to improve Morrowind's framerates without affecting quality.

I was able to run this program: [http://www.bethsoft.com/bgsforums/index.php?showtopic=880625](http://www.bethsoft.com/bgsforums/index.php?showtopic=880625)

It works natively on linux. Although it was built for Oblivion, I just had it optimize my Morrowind meshes in addition to my Oblivion meshes. It works equally well, but the performance boost is less since the meshes are less complex. (It takes a long time for this script to complete. Probably 3 hours or so.)

I was able to get the Morrowind FPS Optimizer to run, but not simultaneously with Morrowind. Yet, some of the optimizations can just be set ahead of time with that program

[http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=22](http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=22)

There are probably other tweaks too. Just search around for different mods. Oblivion has mods which optimize the in-game scripts, remove unneeded polygons, etc. There is bound to be similar things for Morrowind.

Obviously tweak the ini file and turn down the settings when possible.

[http://www.uesp.net/wiki/Morrowind:Ini_Settings](http://www.uesp.net/wiki/Morrowind:Ini_Settings)

Also, make sure your game has the latest official patch as well as the unofficial patch.

[http://www.tesnexus.com/downloads/file.php?id=19510](http://www.tesnexus.com/downloads/file.php?id=19510)

---

### Post by juanoleso on 2009-03-09
Thank you!  I'll be doin' this when I get home.

---


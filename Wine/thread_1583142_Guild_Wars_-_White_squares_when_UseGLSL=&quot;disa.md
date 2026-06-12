---
title: "Guild Wars - White squares when UseGLSL=&quot;disabled&quot;"
date: 2010-09-27
forum: Wine
---

### Post by ShadowMage on 2010-09-27
Hi everyone,

Using wine-1.2, I've finally been able to get Guild Wars to work on my system, with a little bit of tinkering. First, many thanks to the wine dev team for making this possible! There is one small issue, though, and I'm wondering if there is any fix or workaround available.

Let me first briefly describe what I did. With the help of this guide [http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine) and the winehq AppDB entry [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194) I fixed the black UI by editing the registry, OffscreenRenderingMode="backbuffer" in HKEY_CURRENT_USER/Software/Wine/Direct3D. Then, because the game was running terribly slow, I also made UseGLSL="disabled" (in the same registry directory).

Now the game runs nice and smooth and performance is on par with when I run it in Windows. The problem is with UseGLSL="disabled", footprints appear as white squares. This seems to be a known issue as it is mentioned on the [http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine) page. But this is a wiki.guildwars.com page, so I wonder, does the wine dev team know about this issue? And since Guild Wars is on the top 10 platinum games list, are there plans to address this issue?

If anyone knows more details about this issue or has any suggestions, please let me know. I noticed it says the white squares shouldn't appear in some older versions  of wine, but I was never able to get GW to work in previous versions.

Thanks!

---

### Post by ShadowMage on 2011-06-07
The white squares issue that was happening with wine-1.2 seems to be  fixed in newer versions of wine. Currently running Guild Wars with  wine-1.3.21 and the footprints now appear just like they should.

I'm marking this thread as solved. :smile:

---

### Post by -=- Mr. Tux -=- on 2011-07-05
raising the graphics to highest also takes care of many of the texture promblems... however a few things like costumes have a few glitches... any idea of how to get these fixed?

---


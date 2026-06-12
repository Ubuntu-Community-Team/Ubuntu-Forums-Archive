---
title: "Wine with multi-core CPU frame-rate issue in WoW"
date: 2011-02-03
forum: Wine
---

### Post by Frantumn on 2011-02-03
Im using wine to run WOW... and i have to say, whether its my new computer or new versions of wine / ubuntu. it runs great compared to how it used to.

**my question is this... **
When i run wow in wine, it is only using 1 of my 8cpu cores. im running a 64bit OS with an i7-720QM, 4gb of ram and a Nvidia GTS360m. because it's only using one CPU core, my frame rate suffers.

Is there anythign special I have to do to make wine use multicores for WOW?

Thanks!

---

### Post by cascade9 on 2011-02-03
Tried this? 

Open the WTF folder the WoW directory
Open Config.wtf 
At the bottom, add one these lines- 

Dual-cores:
SET processAffinityMask "3"

Tri-cores:
SET processAffinityMask "7"

Quad-cores & I5s:
SET processAffinityMask "15"

I7s:
SET processAffinityMask "255"

[http://www.wowwiki.com/CVar_processAffinityMask](http://www.wowwiki.com/CVar_processAffinityMask)

---

### Post by cwwilson721 on 2011-02-03
Erm....

If you bothered to read about wine, you would already have known that wine is a 32bit program. Since you need a 64bit program to access multiple cores, I'd have to assume you have 64bit wine.

Since you already knew this, [because you were told in the stickies at the top of the forum to search about wine]("http://wiki.winehq.org/WineOn64bit"), I'm assuming your computer is broken, and only allowing a single core to work.

Or do you ask/post first, then research?

---

### Post by cascade9 on 2011-02-04
> **cwwilson721 said:**
> Erm....

If you bothered to read about wine, you would already have known that wine is a 32bit program. Since you need a 64bit program to access multiple cores, I'd have to assume you have 64bit wine.

Since you already knew this, [because you were told in the stickies at the top of the forum to search about wine]("http://wiki.winehq.org/WineOn64bit"), I'm assuming your computer is broken, and only allowing a single core to work.

Or do you ask/post first, then research?

Need a 64bit program to access multipule cores? You've got to be kidding. Back at ya on 'research'.

---

### Post by Frantumn on 2011-02-04
> **cwwilson721 said:**
> Erm....

If you bothered to read about wine, you would already have known that wine is a 32bit program. Since you need a 64bit program to access multiple cores, I'd have to assume you have 64bit wine.

Since you already knew this, [because you were told in the stickies at the top of the forum to search about wine]("http://wiki.winehq.org/WineOn64bit"), I'm assuming your computer is broken, and only allowing a single core to work.

Or do you ask/post first, then research?
If my post bothers you, don't help. I'd rather have no help than have someone sit there and make me feel stupid.

And you are wrong, Wine runs other programs with multiple cores just fine. It's only WoW.

---


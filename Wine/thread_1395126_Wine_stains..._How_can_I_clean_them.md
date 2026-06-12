---
title: "Wine stains... How can I clean them?"
date: 2010-01-31
forum: Wine
---

### Post by -EvilGrin- on 2010-01-31
So.. I've been playing with wine a bit, and I managed to install cs4 after some trouble (and none of tutorials helped). But for some reason cs4 died 2 days after. I made a complete uninstall of wine (which for some reason wasn't complete cos I've found config files in home directory), and I've re-installed it after which Applications menu entry of wine have not appeared. I did same process again few times, but no results. When I gave up, I noticed that on right click I got a lot of duplicated options (open with).
I put a screen shot.

**----The Important Part---**
My questions: 
    Is there any right click manager for ubuntu? 
    How to remove this crappy crap from my right-click menu?

I allso tried installing wine 1.1.17 or somethin, cos I read cs4 works fine on that, but I read later on that It coses problem I courently have.

Thanks for your answers!

---

### Post by mister_playboy on 2010-01-31
I saw that problem when I ran uTorrent.  It seemed to make an new entry for it in the list every single time the program ran.

I don't know how to fix it. :?:

---

### Post by -EvilGrin- on 2010-01-31
Is there no any "registry thing" where I could edit right click options, and possibly delete that properties?

---

### Post by hikaricore on 2010-01-31
You could hunt around in: **regedit**

:p

---

### Post by -EvilGrin- on 2010-02-01
> **hikaricore said:**
> You could hunt around in: **regedit**

:p

That's how I used to do it in windows until I find out that I can do same thing more safely in cpanel. -.-

But apparently this was branded in to linux, so I can't "play" regedit command (mainly becouse I removed wine)

---

### Post by oedipuss on 2010-02-01
I don't think regedit has anything to do with it. 

Look here, under 'Uninstalling' : [http://wiki.winehq.org/FAQ/#head-82f00d009961866727f7e2d46e99d60f82e84cd8](http://wiki.winehq.org/FAQ/#head-82f00d009961866727f7e2d46e99d60f82e84cd8)
It mentions how to remove wine menus and file associations completely. Apparently they're stored as files. The FAQ is about menu items only, but if you look in those folders you'll see many association files. After I deleted them there's no more wine clutter in my open with list. 
Higher up it mentions a way to disable building menus for wine applications. Presumably this will disable file associations as well.

---


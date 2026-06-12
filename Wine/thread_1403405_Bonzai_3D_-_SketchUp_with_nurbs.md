---
title: "Bonzai 3D - SketchUp with nurbs"
date: 2010-02-10
forum: Wine
---

### Post by nikkkko on 2010-02-10
Hi,

As a SketchUp pro user, running under wine, I resent having to run Windows so that I can use a 3D application which does nice curves, being SketchUp's big failing.

Enter [Bonzai3D]("http://www.bonzai3d.com/products/bonzai3d.html"), a new version of which has just been launched and which, judging by the comments made in the SketchUp forums, has the potential to convert a fair amount of users, me amongst them.

The only problem is that Bonzai does not quite run under wine and there's no mention of Bonzai in the wine forums.  Has anyone here given it a go and had better luck than me?

---

### Post by nikkkko on 2010-04-06
I've been playing around with Bonzai under windows and would really like to get this working under Ubuntu.  There's a problem rendering the menu icons - they don't render at all - but apart from that it appears to work OK.

Bonzai uses xrender to draw the menus and from scratching around, this appears to be where the problem lies.  Here's the error :

> fixme: xrender:X11DRV_AlphaBlend not a dibsection

I've posted in [winehq forums]("http://forum.winehq.org/viewtopic.php?t=7650&highlight=bonzai") and filed a bug in [wine bugs]("http://bugs.winehq.org/show_bug.cgi?id=21725"), but the thread has run out of steam.  Anyone got any ideas?

Thanks,

Nick

---


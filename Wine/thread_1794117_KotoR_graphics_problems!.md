---
title: "KotoR graphics problems!"
date: 2011-06-30
forum: Wine
---

### Post by kyletstrand on 2011-06-30
Hello,

i'm trying to run Star Wars: Knights of the Old Republic in Playonlinux.  Everything is running fine other than the fact that the graphics are messed up.  Everything is a shade of blue or white.

[IMG]http://i51.tinypic.com/b8ml3b.png[/IMG]

I have Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (unfortunately I know very little about this, but it can run WoW, so I assume it should work on KotoR.)

Any one have suggestions? I'm at a loss since I'm not terribly familiar with playonlinux or wine.

Thanks!

---

### Post by kyletstrand on 2011-07-01
I found a workaround for this problem.

[HTML]http://bugs.winehq.org/show_bug.cgi?id=14770[/HTML]

I used driconf to force S3TC to be enabled as suggested in this thread.

Works like a dream!

---


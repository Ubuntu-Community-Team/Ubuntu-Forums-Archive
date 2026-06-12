---
title: "Lash Problems"
date: 2009-10-07
forum: Ubuntu Studio
---

### Post by drharence on 2009-10-07
Please refer to this bug report:

[http://codingteam.net/project/livemix/bugs/show/226]("http://codingteam.net/project/livemix/bugs/show/226")

for I found this one, having the same problem, and somehow , the operator got it to work... by launching the app from a commandline konsole .  .

---

### Post by c00kie55 on 2009-10-07
this also happend to me when i installed lash 6.0 rc2 the only solution i cut find was to compile things that relayed on lash myself (like jack-rack)
 
also it seams like that its not god enough to reinstall lashd, lash-bin and liblash2 i have to completly remove and install guess it kind off su*ks as lot of apps relay on liblash2

---

### Post by drharence on 2009-10-08
ok. I see that [LiveMix]("http://packages.ubuntu.com/karmic/livemix") also depends on lash . It definetely was some update, I am experiencing the messages : *cannot connect ... disabling lash*  from launching LiveMix in a commandline. But it **does** execute, as long as I'm not launching from the desktop shortcut.

---

### Post by c00kie55 on 2009-10-08
drharence what have you done ? hehe

if you have compiled lash 6 r2 you also need to compile Livemix and you migth need to enable liblash in the configure option (maybe you also need to remove old lash ??dont realy know) i notised that the old lash_panel didnt connect to localhost with lash 6 rc2 but a workaround was using patchage (build with lash ofcourse)


1) i dont think any apps need lash to run (i Guess it like some sort off project controller scripht) but its cool 

2) that desktop shortcut ! cant you not just make a new one whit the same command as you use in konsole.
and guess it need jack running to dont it havent really used livemix so much


__

---

### Post by Stochastic on 2009-10-09
Moved posts to their own thread as the original thread had no relevance to Lash, was an issue with configuring Jack, was solved, and was a year and a half old.

---


---
title: "Request: bmp-mp4 plugin"
date: 2005-06-30
forum: Ubuntu Backports
---

### Post by ulisse on 2005-06-30
Could it be possible to have [bmp-mp4](http://www.sosdg.org/~larne/w/Plugin_list) plugin for Beep Media Player? (the first from top)
I tried to build it from source, but it seems I'm not skilled enough... :| 

Thanks in advance.

---

### Post by Slo Mo Snail on 2005-07-01
I'll look at it... and when everything works fine I'll try to get it also into breezy

---

### Post by Slo Mo Snail on 2005-07-01
I compiled it and it worked... but there are other problems which prevent a package:
-there seems to be no project homepage and even no email address or other way to contact the author
-the license situation of the plugin is unclear... and without clarification I can't publish a package... and as I can't contact the author.....

sorry

but you can download the 2 .so files from [http://fondriest.frederic.free.fr/fichiers/](http://fondriest.frederic.free.fr/fichiers/) and put them into your bmp plugins directory (e.g. ~/.bmp/Plugins/Input or /usr/lib/bmp/Plugins/Input)

---

### Post by ulisse on 2005-07-01
I tried to download the two files, but the only effect i had was that putting them into ~/.bmp/Plugins/Input makes BMP crash.

In the other directory, under /usr/lib, there is no effect.

Ok, I'll open my m4a files with Totem, then I'll try to contact the author and tell him about Ubuntu...

Thanks anyway ;-)

---

### Post by Slo Mo Snail on 2005-07-02
I've talked to some people and it seems to be ok to package the plugin as it's a rather simple modification to code already under GPL and it's freely available... Maybe you get a package this evening or tomorrow ;)

---

### Post by ulisse on 2005-07-02
Thank you very much!
In the meanwhile, I found the email address of the author and wrote him about this; if he will ever reply I'll make you know.

---

### Post by Slo Mo Snail on 2005-07-02
Can you give me the email address?
I uploaded the package here for review: [http://siretart.tauware.de/revu/index.py](http://siretart.tauware.de/revu/index.py)

when everything goes fine it will probably be in breezy in a few days...

---

### Post by ulisse on 2005-07-02
This is the answer I had from CiberFred:
> It's seems ok. Well you could past this message on the forum (boring to submit to the forum just for one message) Also you could add this email adress on the package description if you want :

The bmp-plugin is just a simple code modification from the xmms plugin. It's just an adaptation to beep. The code is free under GPL (well you could do what you want with it even sending me patchs :p).

Thanks to package it ! don't know if a package already exist for debian
on the rarewares web site.

You could contact me by email or by irc too. (or on the lamip web part site forum).


Note that in the README file there are some nice explanation howto compil the plugin. So it should not too hard to do it.

Thanks for using it.

Ps. you could try lamip if you want !  
I'll send you the email adress in pvt, for privacy reasons.

---


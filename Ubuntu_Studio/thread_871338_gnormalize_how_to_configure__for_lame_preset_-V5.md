---
title: "gnormalize: how to configure  for lame preset -V5?"
date: 2008-07-26
forum: Ubuntu Studio
---

### Post by maddiemax on 2008-07-26
Hi to all of you,

I've got a issue with gnormalize 0.63 I'm not able to solve neither by myself nor asking at other linux forums here and there...

The issue is that: in gnormalize 0.63, tab "Configuration", section "lame settings", there are two options which I do not understand how to set properly: "Encode Quality" and "Variable". To which lame's switches they correspond?

In particular, i would like to pass to lame the preset -V5 (target kb/s=130; bitrate rage kb/s=110..150), how should I configure gnormalize?

Thanks very much,

-----------------------
max biagetti
[email]maddiemax@infinito.it[/email]

---

### Post by pietjanjaap on 2008-07-27
"Encode Quality" and "Variable". To which lame's switches they correspond.
I do not know the program.

Mp3 have these settings
1 
-quality(how good the mp3 sounds/is)
-variable bitrate(wen there is no sound the file gets smaller(bitrate), wen there is sound the file gets bigger(bitrate)).

2
-quality(how good the mp3 sounds/is).
-constant bitrate, the size is the same, bitrate stays the same.

Constant bitrate is the best I think, the file is bigger.
You can also use audacity to normalize.

---


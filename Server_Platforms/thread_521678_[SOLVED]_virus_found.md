---
title: "[SOLVED] virus found"
date: 2007-08-09
forum: Server Platforms
---

### Post by chrisb.40 on 2007-08-09
Have installed F Fawn 7.04 after various try outs, no windows on this system.

Just installed Aegis virus scanner and on first scan has found, in vp31vfw.dll, the W32/Magistr.a@mm virus.  Anyone familiar with this? Is it a known virus or a false positive(?) and if a virus how to remove?

Regards

Chris

---

### Post by jrusso2 on 2007-08-09
I am pretty sure its a false positive.  You could try another online scanner and see if it picks it up, I think Housecall works pretty goodl

---

### Post by bapoumba on 2007-08-09
One more option: something in your email box. Some virus may be, but active on windows only. Just a guess (I have no av myself, but ran into this on a friends comp once).

---

### Post by chrisb.40 on 2007-08-09
Thanks to you both.

Does Housecall work with Ubuntu?

Regards

---

### Post by kayvortex on 2007-08-09
I think the file appears to be a win32 codec file, which means that your system may be using it (so deleting it means that you'll probably want to replace it afterwards). I think it's more likely to be a false positive, but I'd scan with another virus scanner to be sure. I think avast have a linux virus scanner...you could try that.

---

### Post by jrusso2 on 2007-08-09
> **chrisb.40 said:**
> Thanks to you both.

Does Housecall work with Ubuntu?

Regards

As long as you have a working Java.  The reason I figure its a false it seems I looked it up and everyone that reported that file as a virus was using aegis

---

### Post by euler_fan on 2007-08-12
There's a rumor going around that Aegis has a higher rate of false positives than ClamAV.

If you search the forums there are some good howto's on installing it from source (the only way as we don't have a volatile repo).

If ClamAV doesn't find it, then it's probably not there.

EDIT: AEGIS 2.0 uses clamAV as the backend. Ergo, no higher rate of false positive. Which version do you use?

---


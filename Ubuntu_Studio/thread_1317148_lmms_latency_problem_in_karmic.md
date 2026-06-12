---
title: "lmms latency problem in karmic"
date: 2009-11-06
forum: Ubuntu Studio
---

### Post by djzoid on 2009-11-06
hi,

im trying to get lmms to work on karmic. i dont know how to find out whats wrong with lmms but it was working great on hardy and jaunty, now, even having made sure i have all the right kernels including rt installed, the little cpu meter it has, shoots straight into the red and then i have no sound from lmms. everything in the program still functions for a bit but when developing music that is not very helpful.

if anyone could give me any suggestions as to a fix, that would be great.

---

### Post by Settel on 2009-12-02
I've got the same symptoms. Mine seem to be linked to the use of the freeverb version 3 LADSPA plugin. Does your problem vanish if you disable all freeverb FX plugins?

See also my posting on the LMMS devel mailing list ([http://lmms.info/community.php](http://lmms.info/community.php)) on 2009-12-02.

---

### Post by alexfish on 2009-12-06
Hi 

are you using pulse as the server

---

### Post by DerickX on 2009-12-07
Try to use OSS as audio system. If you don't use LMMS via Jack, you don't need a special kernel.

---

### Post by VertexPusher on 2009-12-07
> **DerickX said:**
> Try to use OSS as audio system. If you don't use LMMS via Jack, you don't need a special kernel.
You can use Jack without a special kernel if you disable the realtime option in Jack's setup. Most systems can handle 12ms latency without a realtime kernel.

One benefit of using Jack is that you don't need to worry about PulseAudio any more. By default, PulseAudio will be suspended automatically when you launch Jack. This will release all the occupied ALSA hardware devices and make them available to Jack for low-latency operation.

There really is no reason not to use Jack.

---

### Post by DerickX on 2009-12-07
But there is a reason for not using LMMS with JACK...

---

### Post by VertexPusher on 2009-12-07
> **DerickX said:**
> But there is a reason for not using LMMS with JACK...
Care to explain? I'm curious.

---

### Post by DerickX on 2009-12-07
JACK support in LMMS is not very good... One of the reason why I prefer and advise to learn Qtractor instead, see also

[http://ubuntuforums.org/showthread.php?t=1348391](http://ubuntuforums.org/showthread.php?t=1348391)

---

### Post by AutoStatic on 2009-12-07
> **DerickX said:**
> Try to use OSS as audio system.There are no OSS packages for Karmic. And JACK support in LMMS is indeed poor. From the LMMS mailinglist:

> All audio backends will slightly benefit from the rewrite due to less locking 
and no memory allocations/releases in the FIFO reader thread.

Armin Kazmi is working on improving the JACK backend. However it's mainly a 
scheduling problem. When running LMMS with root permission (so it can set 
realtime priority for itself), there're no xruns even with buffersize of 64 
frames. That's already true for all versions of LMMS out there.

Toby

Toby is one of the main devs of LMMS by the way.

---

### Post by DerickX on 2009-12-07
> **AutoStatic said:**
> There are no OSS packages for Karmic.
I don't think that is true.

---

### Post by VertexPusher on 2009-12-07
Are you talking about OSS4 or the old OSS emulation layer provided by ALSA?

The emulation layer is always available, but since PulseAudio occupies ALSA hardware devices for exclusive access, the emulation layer will be occupied as well unless you temporarily suspend PulseAudio.

---

### Post by AutoStatic on 2009-12-07
> **DerickX said:**
> I don't think that is true.
[http://ubuntuforums.org/showpost.php?p=7496246&postcount=15](http://ubuntuforums.org/showpost.php?p=7496246&postcount=15)

---


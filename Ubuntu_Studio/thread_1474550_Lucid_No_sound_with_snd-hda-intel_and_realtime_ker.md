---
title: "Lucid: No sound with snd-hda-intel and realtime kernel"
date: 2010-05-06
forum: Ubuntu Studio
---

### Post by scotty64 on 2010-05-06
Sound on Samsung NB30 netbook (intel soundchip) works fine with the generic kernel but not with the rt-kernel that comes with Lucid.
I wonder if an old bug made it back into the rt-kernel: [http://ubuntuforums.org/showthread.php?t=514619&highlight=realtime+kernel+sound](http://ubuntuforums.org/showthread.php?t=514619&highlight=realtime+kernel+sound)
Sadly there are no audio backports for the rt-kernel.

---

### Post by AutoStatic on 2010-05-06
Hello scotty64, what does **aplay -l** output in a terminal? And **cat /proc/asound/card*/codec* | grep Codec** ? When booted with both the generic and the realtime kernel if possible. Thanks!

---

### Post by falkTX on 2010-05-06
The same thing happened to me.

But the thing is that audio never worked before (only through phones).
With the new .32 kernel it works fine.

So the problem may not be a regression, but a new feature of new kernel.

The solution for me was this:
[http://ubuntuforums.org/showthread.php?p=7717667](http://ubuntuforums.org/showthread.php?p=7717667)

Yours may be different

---


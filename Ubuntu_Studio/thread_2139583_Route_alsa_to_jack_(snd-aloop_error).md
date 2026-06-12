---
title: "Route alsa to jack (snd-aloop error)"
date: 2013-04-27
forum: Ubuntu Studio
---

### Post by stilllife on 2013-04-27
Hi, I am trying to route all my alsa application to jack following this documentation [http://alsa.opensrc.org/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge](http://alsa.opensrc.org/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge) . I have the module snd-aloop but for some reason I am not able to load the module 

Here some relevant result
```

sudo modprobe snd-aloop
FATAL: Error inserting snd_aloop (/lib/modules/3.2.0-40-lowlatency/kernel/sound/drivers/snd-aloop.ko): No such device


dmesg | tail -n 3
[ 8365.859773] cannot find the slot for index 0 (range 0-2), error: -16
[ 8365.859793] snd_aloop: probe of snd_aloop.0 failed with error -16
[ 8365.859857] aloop: No loopback enabled

```

I also tryed to remove the alsa modules as the document says but some of them (snd-hda...) are in use so they cannot be removed...


Any idea? thanks

---


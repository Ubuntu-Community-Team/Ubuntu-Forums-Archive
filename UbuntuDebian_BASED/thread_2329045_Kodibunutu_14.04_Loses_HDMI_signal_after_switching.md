---
title: "Kodibunutu 14.04 Loses HDMI signal after switching inputs"
date: 2016-06-27
forum: Ubuntu/Debian BASED
---

### Post by doug piston on 2016-06-27
Currently have a HTPC that uses the GeForce GTX 950. New install of Kodibunutu which is 14.04 I can switch between my HDMI ports on the tv normally for a bit but if it's not on the HTPC input for some time and I switch back I get a "No signal" on my tv.

Xorg log -> [http://sprunge.us/HhcG](http://sprunge.us/HhcG)

Driver version 
```

adam@jarvis ~ &#10095;&#10095;&#10095; nvidia-smi
Mon Jun 27 06:33:44 2016
+------------------------------------------------------+
| NVIDIA-SMI 352.63     Driver Version: 352.63         |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 950     Off  | 0000:01:00.0      On |                  N/A |
|  0%   59C    P0    30W / 125W |    149MiB /  2046MiB |     18%      Default |
+-------------------------------+----------------------+----------------------+


+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      1316    G   /usr/bin/X                                     107MiB |
|    0      1478    G   /usr/lib/kodi/kodi.bin                          30MiB |
+-----------------------------------------------------------------------------+

```

Please let me know if there is anymore info I get. Hopefully someone might know something as my googlefu doesn't seem to bring anything back that seems relevant to my case.

Thanks!

---

### Post by howefield on 2016-06-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by doug piston on 2016-06-27
Sorry about that. Thanks for the move.

---


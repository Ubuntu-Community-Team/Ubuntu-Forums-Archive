---
title: "nvidia vram usage on 313.20 driver"
date: 2013-11-13
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-11-13
i just updated the driver today and i noticed my vram usage appears to have gone up alot, i know xfce does not require nearly 400MB of vram to run
it usually sites around 128mb usage
anyone else noticed higher vram usage on xfce?
```
~$ nvidia-smi
Wed Nov 13 16:42:51 2013       
+------------------------------------------------------+                       
| NVIDIA-SMI 331.20     Driver Version: 331.20         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 550 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 30%   36C  N/A     N/A /  N/A |    **407MiB /  1023MiB** |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
```

---

### Post by QDR06VV9 on 2013-11-13
> **pqwoerituytrueiwoq said:**
> i just updated the driver today and i noticed my vram usage appears to have gone up alot, i know xfce does not require nearly 400MB of vram to run
it usually sites around 128mb usage
anyone else noticed higher vram usage on xfce?
```
~$ nvidia-smi
Wed Nov 13 16:42:51 2013       
+------------------------------------------------------+                       
| NVIDIA-SMI 331.20     Driver Version: 331.20         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 550 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 30%   36C  N/A     N/A /  N/A |    **407MiB /  1023MiB** |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
```
 
With a sweet rig like yours I'm wondering why also?
I'm running Gnome-Shell, Cinnamon, KDE With all the bells and whistles, well heres mine.
```
Wed Nov 13 17:50:54 2013       
+------------------------------------------------------+                       
| NVIDIA-SMI 331.20     Driver Version: 331.20         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 520      Off  | 0000:01:00.0     N/A |                  N/A |
| 40%   49C  N/A     N/A /  N/A |    166MiB /  1023MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
me@me-Aspire-M3300:~$ 


```

---

### Post by pqwoerituytrueiwoq on 2013-11-14
seems to be normal now, i think it was something with firefox involving a [certain tab]("http://www.overclock.net/t/1274407/lightbox/post/17562684/id/1127187ROCF-11003"), never noticed anything if ff use much vram
*if anyone is wondering why i am looking at fans when i have such good cooling, just trying to get it quieter*
i had closed everything including ff even my panels and it was still high like that, no idea what made it go down
this is with everything open now
```
~$ nvidia-smi
Thu Nov 14 21:01:24 2013       
+------------------------------------------------------+                       
| NVIDIA-SMI 331.20     Driver Version: 331.20         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 550 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 30%   34C  N/A     N/A /  N/A |    181MiB /  1023MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
```

---

### Post by kevpan8152 on 2013-11-15
Sorry but I no longer have any NVIDIA Graphics Cards anymore to try out, all I have now is a Laptop with Intel 4000 Series Integrated Laptop Graphics. Edit: I should correct myself to say that I also have a Dell Desktop with ATI Graphics but it will no longer run any flavor of Ubuntu/Kubuntu/Lubuntu/Xubuntu due to the fact that I added an After Market 120 GB Crucial M500 Solid State Drive to the Machine.

---


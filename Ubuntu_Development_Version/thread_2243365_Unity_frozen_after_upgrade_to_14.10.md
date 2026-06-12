---
title: "Unity frozen after upgrade to 14.10"
date: 2014-09-08
forum: Ubuntu Development Version
---

### Post by wgarcia on 2014-09-08
I updated today to 14.10 and can't get into Unity.

The system starts OK, lightdm starts fine, but when Unity starts it shows the upper and left panel, and only can move the mouse around. Everything is frozen otherwise. 

This is a Dell Latitude E6530 and has the following graphic cards:

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)

```

If I do 

```

dpkg -l | grep nvidia

```

I get:

```

ii  nvidia-libopencl1-331-updates          331.89-0ubuntu3    amd64        NVIDIA OpenCL Driver and ICD Loader library

```

---

### Post by wgarcia on 2014-09-08
I installed lxde for a while, and moved from nouveau to nvidia-331 as a driver, and now I can login into Unity.

---


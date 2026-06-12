---
title: "WIne 3D not working after 11.04 upgrade"
date: 2011-04-27
forum: Wine
---

### Post by _Pete_ on 2011-04-27
Upgraded system to 11.04 and using PPA wine 1.3.18. 

After update all 3D games refuses to work and gives this error when starting:

err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems

Using these drivers:

$ glxgears -info
GL_RENDERER   = GeForce GT 220/PCI/SSE2
GL_VERSION    = 3.3.0 NVIDIA 270.41.06
GL_VENDOR     = NVIDIA Corporation

Any ideas how to fix this?

---

### Post by cogadh on 2011-04-27
Run this from the terminal:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: No", then there is something wrong with your video card drivers and you should try to reinstall them.

---

### Post by _Pete_ on 2011-04-27
> **cogadh said:**
> Run this from the terminal:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: No", then there is something wrong with your video card drivers and you should try to reinstall them.


```

$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,

```

Seems like that is not the issue...

---

### Post by cogadh on 2011-04-27
Are you running Ubuntu with all the 3D "bells and whistles" tuned on? Try disabling the desktop effects, in the past they would basically break OpenGL from Wine's perspective, maybe 11.04 somehow brought that issue back.

---

### Post by disabledaccount on 2011-04-27
I've had similar problem few versions ago (I don't remember which exactly) and I've solved it by restoring wine configuration in registry. At least I would check/try to set those in Direct3D key.

---

### Post by _Pete_ on 2011-04-28
Got this somehow resolved: 

Removed the nvidia drivers which were installed from repositories.

Then manually installed drivers from nvidia.com/drivers. What was missing I guess was the 32-bit compability libraries, which got installed with manual installation procedure.

The system I am using is 64bit so it needs those 32bit libs...

---

### Post by Arminius on 2011-05-08
I had same problem, turned out to not be wine's fault in my case.
When I set up drivers I went for the experimental prototype one, I set it to the recommended one, reboot, and now steam and all other 3D games under wine is working correctly.

---


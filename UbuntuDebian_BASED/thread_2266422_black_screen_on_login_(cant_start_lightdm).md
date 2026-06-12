---
title: "black screen on login (cant start lightdm)"
date: 2015-02-22
forum: Ubuntu/Debian BASED
---

### Post by hasanaa on 2015-02-22
installed elementary alongside win7 on uefi system. everytings went fine. after upgrade & reboot, i select the os in GRUB, it takes me to a  black screen. tried “service lightdm start” and “startx”, didnt work.  what should i do?

---

### Post by hasanaa on 2015-02-25
```
~$ lspci | egrep "VGA|3D|Display"
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)

~$ glxinfo | grep render
direct rendering: Yes
         GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Gallium 0.4 on NVA0
         GL_MESA_texture_signed_rgba, GL_NV_conditional_render, GL_NV_depth_clamp, 
         GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp,
```

---


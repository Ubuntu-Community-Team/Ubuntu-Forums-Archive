---
title: "Chrome doesnt start with bumblebee nvidia graphics"
date: 2016-04-06
forum: Ubuntu Development Version
---

### Post by startas on 2016-04-06
Chrome doesnt start on laptop with optimus graphics (intel hd4400 + nvidia 840m) using nvidia card. I am using proposed updates for xorg-server 1.18.3, also using nvidia drivers ppa for nvidia-364.12 driver. In general, bumblebee works - i can run unigine heaven benchmark via optirun or primerun commands. Has anyone else managed to run chrome via bumblebee with nvidia graphics ? Is it chrome issue, ubuntu or nvidia drivers ? Error i get :
```

mypc:~$ primusrun google-chrome
[5010:5010:0406/151348:ERROR:browser_main_loop.cc(267)] <unknown>: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Fontconfig warning: FcPattern object size does not accept value 11(i)
Fontconfig warning: FcPattern object size does not accept value 11(i)
primus: warning: reusing initial X connection for display thread
libGL error: failed to open drm device: Operation not permitted
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
[5088:5150:0406/151348:ERROR:x11_util.cc(78)] X error received: serial 32, error_code 169, request_code 154, minor_code 6
primus: fatal: failed to acquire direct rendering context for display thread

```

---


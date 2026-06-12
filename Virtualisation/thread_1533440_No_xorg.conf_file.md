---
title: "No xorg.conf file"
date: 2010-07-18
forum: Virtualisation
---

### Post by wlraider70 on 2010-07-18
I am running a headless ubuntu server, therefore I do not have a xorg.conf file. The only resolution available is600x800

I access through VNC



Can anyone help me with a custom file, something to get me a little better res.

edit:

I have tried numerous xorg.conf settings.

the only settings that will boot for me are.
```


Section "Monitor"
Identifier "Monitor0"
Option "DPMS"
HorizSync 30-85
VertRefresh 48-120
EndSection


```

If i even adding this line will cause failure

Mode		"1024x768"


The file had been blank, but leaving the above code make no difference, it just doesn't crash.

---

### Post by squaregoldfish on 2010-07-18
If you're accessing your server through VNC, the xorg file won't help you - instead, you should be able to set the screen size in the VNC server. For example, I use tightvnc with the following command:
```

tightvncserver -geometry 1024x768 -depth 24 :1
```Steve.

---


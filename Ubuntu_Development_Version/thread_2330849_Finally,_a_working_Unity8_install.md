---
title: "Finally, a working Unity8 install"
date: 2016-07-15
forum: Ubuntu Development Version
---

### Post by cariboo on 2016-07-15
I finally managed to install a working Unity8 environment, now I find I can't install anything. When I first accessed the Software Store I was asked to sign on using SSO, but I'm never asked for a sudo password when trying to install apps.

---

### Post by grahammechanical on 2016-07-15
What video adapter? I am still getting a frozen desktop with Unity part loaded on Nvidia adapter. The user interface is still a phone/tablet interface. That would explain the power of SSO.

---

### Post by ventrical on 2016-07-15
Hey guys ! :) 

no more ppa! :)



[http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)

@ cariboo

but you still might need this.

```

sudo click install --user mhall com.ubuntu.filemanager_0.4.525_multi.click
sudo click install --user mhall com.ubuntu.terminal_0.7.170_multi.click

```

just replace mhall with the user name on your install. 
Try the terminal first and you have to execute those commands in the same directory
you downloaded the click pkgs, link also available at link provided.

Regards..

Edit:
If you accidently execute the above commands with 'mhall' in it (if you overcopy one space then it will run in the terminal after you paste it) it will break you install. touchy indeed :) so you have to use your arrow ket to bring the cusor to the user name area so you can enter your own username. Or you can do it manually:)

---

### Post by cariboo on 2016-07-15
Im running Unity8 on a Toshiba laptop with:

```
inxi -CG
CPU:       Quad core Intel Pentium N3530 (-MCP-) cache: 1024 KB 
           clock speeds: max: 2582 MHz 1: 2255 MHz 2: 2392 MHz 3: 2582 MHz
           4: 2582 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 11.2.1
```

I haven't tried Ctrl-Alt-t yet, as we've been kind of busy getting all the bugs chased down after the Forum breach and subsequent upgrade.

---

### Post by ventrical on 2016-07-15
Sorry..

all ppas not gone . Still need this.

```

sudo add-apt-repository ppa:ci-train-ppa-service/stable-phone-overlay

```

---

### Post by cariboo on 2016-07-15
> **ventrical said:**
> Sorry..

all ppas not gone . Still need this.

```

sudo add-apt-repository ppa:ci-train-ppa-service/stable-phone-overlay

```

That's the one I used.

---


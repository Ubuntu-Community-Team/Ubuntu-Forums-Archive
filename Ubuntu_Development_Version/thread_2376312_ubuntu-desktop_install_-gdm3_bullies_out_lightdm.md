---
title: "ubuntu-desktop install -gdm3 bullies out lightdm"
date: 2017-11-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-11-01
I was trying to test an ISO I built with just unity on it. It was pristine and working fine with lightdm. I was trying to emulate a bug in another thread: [https://ubuntuforums.org/showthread.php?t=2375934](https://ubuntuforums.org/showthread.php?t=2375934)

From terminal the desktop manager program gave me option of gdm3 or lightdm. I chose lightdm and as soon as I chose lightdm it bullied right into gdm. I went to tty, tried to remove gdm3 but it want ubuntu-desktop also so anyways  I now have unity default  with two instances of gnome on xorg and a dead wayland session. 

##I am not worried about this. I do this kind of edge testing so please do not tell me to turn off proposed - because it is not installed on this session :) I'm just saying .. I'm just reporting what happened. the good the bad and the ugly:)

so I'll  try 

```

sudo apt-get install ubuntu-session

```

---

### Post by ventrical on 2017-11-01
So if you look at the screen shot I choose lightdm <highlited> and if I hit enter of choose <ok> it will black-out and boot right into gdm3 which gives me my wayland back. Actually it's kind of a kewl bug in a way.:)

Regards..

---

### Post by Chanath on 2017-11-01
> **ventrical said:**
> So if you look at the screen shot I choose lightdm <highlited> and if I hit enter of choose <ok> it will black-out and boot right into gdm3 which gives me my wayland back. Actually it's kind of a kewl bug in a way.:)

Regards..
Do you have Wayland or not? What do you have in xsessions?

---

### Post by ventrical on 2017-11-01
I just told ya it gives me my wayland back..

---

### Post by ventrical on 2017-11-01
It was there and now it's gone...

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.2.2 Direct Render: Yes

```

---

### Post by ventrical on 2017-11-02
Only boots into wayland under gdm3.

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.2.2 Direct Render: Yes

```

---

### Post by Chanath on 2017-11-02
When you do the next upgrade, check what you have in xsessions/ubuntu.desktop. Ligtdm or gdm doesn't change what's in xsessions. 

(Btw, change the thread heading to ubuntu from ubutnu)

---


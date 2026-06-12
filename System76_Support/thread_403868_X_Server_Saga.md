---
title: "X Server Saga"
date: 2007-04-07
forum: System76 Support
---

### Post by space2k on 2007-04-07
I've been working on this problem for days now - I've searched these forums endlessly and tried dozens of seemingly logical solutions, but can't seem to get anywhere. I'm desperate for help! Any assistance will be deeply appreciated...

First, I have a system76 Ratel desktop that I've owned for about 3-4 months. I cheaped out and went with the VIA onboard graphics. Everything was fine and I was really digging Ubuntu (this is my first linux experience) until last week, when suddenly my system won't load xserver - "Fatal server error: no screens found".

So I search these forums and try dpkg-configure xserver-xorg. No progress.

I edit xorg.conf. In various ways suggested by some threads here. Still the same error. OK - so I decide to completely re-install (I have to use the alternate CD, since X won't load). So I re-install 6.10. X Server failed to start. Damn. I try to install 6.06. Again X Server failed to start.

At this point I think that maybe my on board graphic chip is bad - so I install an Nvidia 6200 AGP card. Same deal. I try to install the invidia drivers - nothing. Just for kicks, I pull the Nvidia card and re-install 6.10 while using the on board graphics again. Same deal.

So - I get the exact same errors every time -
* X Server fails to start.
* No devices found.
* No screens found.
* XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed with 0 events remaining
*WTF?

This seems crazy to me. I know a thing about troubleshooting - but the same issues with multiple hardware configs and after reinstalling different versions of an OS? I'm stymied.

I'll work with anyone who can help me. Please note that I'm posting from a windows laptop and may not be able to post entire log files - I'll do what I can, though...

Thanks...

---

### Post by heimo on 2007-04-07
In xorg.conf, do you have Device section with a line:
```
Driver "via"
```

---

### Post by space2k on 2007-04-07
Yes - I've got this in xorg.conf

```

Section "Device" 
     Identifier "Generic Video Card"
     Driver "via"
EndSection

```

Note the lack of a BUS ID. What seems strange to me is that whenever I reconfig xserver, it never suggests a bus ID for me. Also, when I run lspci I don't see anything that looks like a video card. This applies for when I am trying the VIA onboard graphics or the Nvidia card I had in. Does this seem like a hardware (motherboard) issue to anyone?

---

### Post by Ptero-4 on 2007-04-07
The VIA onboard graphics doesn`t show in LSPCI or ask BUS ID because it`s integrated in the mobo. As for the NVidia card it`s normal that it doesn`t show in LSPCI because it`s not PCI (you said it`s AGP) as for the BUS ID. It might be that AGP doesn`t use it (have not had X f*ck on me yet so don`t know that), or it might also be a burnt AGP slot and a burnt onboard GPU. Better let this in carl`s hands, he knows his stuff.

---

### Post by space2k on 2007-04-07
Thanks for the info. Does Carl watch this board or should I contact system76 support?

---

### Post by Ptero-4 on 2007-04-10
He watches this forum (his nick is crichell).

---


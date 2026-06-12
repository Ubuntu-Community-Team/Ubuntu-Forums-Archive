---
title: "Screen tearing on Bonobo Extreme 7"
date: 2014-07-19
forum: System76 Support
---

### Post by eric_r2 on 2014-07-19
Hello, I'm running a Bonobo Extreme 7 with nvidia driver 331. About 2/3s of the games that I have tried playing suffer from screen tearing. I believe the games that have an option for vertical sync don't have the problem, but not all games have that option. I've tried completely reformatting my computer and the problem persists. Is there some way to force vertical sync, or some other solution?

---

### Post by billdozor on 2014-07-20
What version of Ubuntu are you running? And what Desktop Environment?

Also, an older tutorial, but have you checked out this link for options on disabling compositing and certain features in NVIDIA settings?
[URL="http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu"]http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu
[/URL]

---

### Post by isantop on 2014-07-21
In addition to the above, do you have the system76-driver-nvidia pacakge installed? If you still have the original Ubuntu installation from when the system was new, it should be preinstalled.

---

### Post by eric_r2 on 2014-07-23
It is 14.04 and Unity. Billdozer's guide didn't work unfortunately. None  of those options to adjust the refresh rate exist in the places that  the guide says any more, so I was lost without being able to try the  guide at all.

Yes, I do have the System76 driver installed. 14.04.8.

---

### Post by isantop on 2014-07-24
In addition to the package, there is also the system76-driver-nvidia package that includes the Nvidia Proprietary Driver. That may have a large effect on screen tearing, as the proprietary driver is much better optimized for the hardware.

---

### Post by eric_r2 on 2014-07-27
Hi Isantop, yes, I have that installed and updated to the latest version already, according to apt-get.

---

### Post by silverslimer on 2014-07-30
I've suffered the same kind of problem under Ubuntu 14.04 and Ubuntu GNOME 14.04 so it doesn't look like it's limited to Unity. I've tried a number of solutions but eventually decided to simply play the games in windowed mode. In that mode, the screen tearing doesn't seem to exist. Let me know if you've seen an improvement even though this "solution" might be less than ideal.

---

### Post by eric_r2 on 2014-07-30
Silverslimer, yep, I can confirm that the problem does not happen in windowed mode. But there was to be a better solution.

---

### Post by billdozor on 2014-08-06
I know that in the KDE and XFCE environments, full screen video tears can be fixed by disabling "Compositing". 
This is something that can be turned off with a check box in the settings.

Turn off compositing
KDE: 
[LIST]
[*]Settings > System Settings > Desktop Effects > Advanced > Suspend desktop effects for fullscreen windows.
[LIST]
[*]This is how I fixed screen tearing while using Debian 7 with KDE and NVidia proprietary drivers.
[/LIST]
[/LIST]

XFCE:

[LIST]
[*]Settings > Personal section > Window Manager Tweaks > Compositor > Uncheck "Enable display compositing"
[LIST]
[*]**08/06/14:** I just tested this with my desktop system and it resolves Steam games full screen tearing. (Xubuntu 14.04 64-bit, NVidia 331.38 driver for GeForce GTX285 card)
[/LIST]
[/LIST]

Although, from what I understand with Ubuntu Unity, compositing is pretty integrated because of the 3d desktop environment. (no 2d fallback anymore)

Other things you could try is in the NVidia Settings utility: 


[LIST]
[*]Enable "sync to vblank"
[LIST]
[*]X Screen 0 > OpenGL Settings > Check "Sync to VBlank"
[/LIST]
[/LIST]

[LIST=1]
[*]Set GPU Power Levels to run at Max instead of auto
[/LIST]

[LIST=|INDENT=2]
[*]GPU 0 > PowerMizer > PowerMizer Settings > Preferred Mode: Prefer Maximum Performance
[/LIST]

---

### Post by eric_r2 on 2014-08-26
Thanks Billdozor.. I definitely don't want to give up Unity to resolve this.. I tried your other two suggestions. Sync to VBlank was already checked.. and Prefer Maximum Performance seems to have had no effect.

Any other ideas?

---

### Post by jawilljr2 on 2014-08-27
Eric, try the following command to see if it gets rid of your tearing:

```
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ForceCompositionPipeline = On }"
```

I got the command from [this post,]("https://devtalk.nvidia.com/default/topic/543305/linux/screen-video-tearing-gtx6xx-7xx-titan-kepler-maxwell-in-almost-all-applications-including-desktop/post/4032623/#4032623") in [this thread.]("https://devtalk.nvidia.com/default/topic/543305/?comment=4244809")

Hope it helps.

---


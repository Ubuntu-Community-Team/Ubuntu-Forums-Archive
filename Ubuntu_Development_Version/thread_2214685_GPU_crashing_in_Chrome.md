---
title: "GPU crashing in Chrome"
date: 2014-04-02
forum: Ubuntu Development Version
---

### Post by lasse-r on 2014-04-02
I am running the 14.04 beta on my laptop, and it works great so far, apart from one problem I am having with Google Chrome.
GPU acceleration in Chrome doesn't seem to be working. When I go to about:gpu in Chrome, I see the following in the logs section:

```

GpuProcessHostUIShim: The GPU process crashed!
GpuProcessHostUIShim: The GPU process crashed!
GpuProcessHostUIShim: The GPU process crashed!

```

Obviously, none of the GPU related functions such as WebGL work. Do any of you have the same problem? I think it is related to Ubuntu 14.04 since I do not have those problems with 13.10.
My laptop has Intel integrated graphics by the way (Intel HD 3000 to be exact). I can play games, so the drivers should be working.
WebGL seems to work in Firefox, so I think this is a Chrome problem. I would appreciate any help on solving this problem!

---

### Post by Mateusz Stachowski on 2014-04-02
Check this [article]("http://www.webupd8.org/2014/01/enable-hardware-acceleration-in-chrome.html") from Web Upd8. Basically you need to go to chrome://flags and enable "Override software rendering list" and use the button on the bottom of that page to restart Chrome.

Then when you have Chrome opened again go to chrome://gpu and everything should be hardware accelerated.

Keep in mind that Google developers consider graphics drivers on Linux to be [very problematic]("http://www.phoronix.com/scan.php?page=news_item&px=MTYyMDk") and they aren't looking to enable hardware video acceleration by default anytime soon. I can confirm that I had multiple crashes of whole system while watching a video on Chrome with this acceleration enabled. I use NVIDIA drivers which one would consider as pretty stable and good.

---

### Post by lasse-r on 2014-04-02
> **Mateusz Stachowski said:**
> Check this [article]("http://www.webupd8.org/2014/01/enable-hardware-acceleration-in-chrome.html") from Web Upd8. Basically you need to go to chrome://flags and enable "Override software rendering list" and use the button on the bottom of that page to restart Chrome.

Then when you have Chrome opened again go to chrome://gpu and everything should be hardware accelerated.

Keep in mind that Google developers consider graphics drivers on Linux to be [very problematic]("http://www.phoronix.com/scan.php?page=news_item&px=MTYyMDk") and they aren't looking to enable hardware video acceleration by default anytime soon. I can confirm that I had multiple crashes of whole system while watching a video on Chrome with this acceleration enabled. I use NVIDIA drivers which one would consider as pretty stable and good.

I have tried exactly that, but I still have the same problem. The GPU process simply crashes when I start Chrome. WebGL does not work either.

---

### Post by lasse-r on 2014-04-02
I have not resolved this issue yet, and I have tried almost anything I can think of. Just in case more people want to help, here is the output I get when running Chrome from the terminal:

```
ATTENTION: default value of option force_s3tc_enable overridden by environment.
/chrome/chrome --type=gpu-process --channel=19932.15.1402172566 --supports-dual-gpus=false --gpu-driver-bug-workarounds=0,1,2,9,27 --disable-accelerated-video-decode --gpu-vendor-id=0x8086 --gpu-device-id=0x0046 --gpu-driver-vendor=Mesa --gpu-driver-version=10.1.0: ../../../../../../../src/mesa/drivers/dri/i965/brw_reset.c:43: brw_get_graphics_reset_status: Assertion `brw->hw_ctx != ((void *)0)' failed.

```

This happens 3 times before Chrome stops trying (for stability reasons I assume).

---

### Post by monkeybrain20122 on 2014-04-02
Same in 13.10. So no webgl on Chrome now.

---

### Post by monkeybrain20122 on 2014-04-02
> **Mateusz Stachowski said:**
> Check this [article]("http://www.webupd8.org/2014/01/enable-hardware-acceleration-in-chrome.html") from Web Upd8. Basically you need to go to chrome://flags and enable "Override software rendering list" and use the button on the bottom of that page to restart Chrome.

Then when you have Chrome opened again go to chrome://gpu and everything should be hardware accelerated.

Keep in mind that Google developers consider graphics drivers on Linux to be [very problematic]("http://www.phoronix.com/scan.php?page=news_item&px=MTYyMDk") and they aren't looking to enable hardware video acceleration by default anytime soon. I can confirm that I had multiple crashes of whole system while watching a video on Chrome with this acceleration enabled. I use NVIDIA drivers which one would consider as pretty stable and good.

Doesn't work. I have this setting from the begining but it has stopped working. If you go to about://gpu you can see all the accelerations enabled but as soon as you go to a page like [https://webglsamples.googlecode.com/hg/aquarium/aquarium.html](https://webglsamples.googlecode.com/hg/aquarium/aquarium.html), it crashes and you go to about://gpu again and you will find all the previously enabled accelerations all turn red (disabled)  I don't know how long has it been like that because I use Firefox 99% of the time and haven't launched Chrome for several weeks. But I remember it was definitely working before.

I am sure this has to do with graphic driver. It happens on an intel machine (ironlake ) but works fine on an amd machine with the open radeon driver (HD 6310)  But I am using beta drivers from ppa (for both machines) so I expect some glitches.

---

### Post by Gavin77 on 2014-04-02
This bug is probably relevant.
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1299499](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1299499)

I had crashes in KDE as well as Chrome when the kernel updated to 3.13.0-20.
Booting into the older 3.13.0-19 works fine and I'm currently using the latest Liquorix kernel without any problems.

---

### Post by carl4926 on 2014-04-03
As much as I like Chrome, it seems recently that they just don't give a hoot.
I've had to use Firefox in a number of instances, where Chrome was just failing.

---

### Post by monkeybrain20122 on 2014-04-03
> **Gavin77 said:**
> This bug is probably relevant.
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1299499](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1299499)

I had crashes in KDE as well as Chrome when the kernel updated to 3.13.0-20.
Booting into the older 3.13.0-19 works fine and I'm currently using the latest Liquorix kernel without any problems.

Don't think so. Here on Unity everything works great except for Chrome. I can confirm another poster's experience that Firefox works completely. I think the KDE bug is unrelated.

---

### Post by Gavin77 on 2014-04-03
It's not a KDE bug, it's a Mesa bug which surfaced when the kernel was updated.
Did you try an older kernel?  If you've already tried it and it still doesn't work then it's probably not the same thing I had.

---

### Post by mc4man on 2014-04-03
seems to be hardware specific, intel 4600 (haswell) is fine the chrome gpu hwaccel

---

### Post by monkeybrain20122 on 2014-04-03
> **Gavin77 said:**
> It's not a KDE bug, it's a Mesa bug which surfaced when the kernel was updated.
Did you try an older kernel?  If you've already tried it and it still doesn't work then it's probably not the same thing I had.

You are right. I can confirm that it has to do with kernel and mesa. I have just upgraded to kernel 3.14. when I noticed this problem. Boot into 3.13.6 and all is fine. But it only affects my machine with the intel card. There is no issue with the other one with an Amd card (using open mesa driver)

---

### Post by wd5gnr2 on 2014-10-11
In case anyone finds this via Google. What seems to work is starting Chrome with: [COLOR=#333333][FONT=ClearSans-Light]--ignore-gpu-blacklist --disable-gpu-sandbox

The sandbox is the culprit.[/FONT][/COLOR]

---

### Post by chronos00 on 2015-01-05
> **wd5gnr2 said:**
> In case anyone finds this via Google. What seems to work is starting Chrome with: [COLOR=#333333][FONT=ClearSans-Light]--ignore-gpu-blacklist --disable-gpu-sandbox

The sandbox is the culprit.[/FONT][/COLOR]

I would like to add my 2 cents here:

The solution was for me to run chrome from the terminal in the following way: 
```
LIBGL_DRI3_DISABLE=1 google-chrome
```

As described here: [https://code.google.com/p/chromium/issues/detail?id=418858]("https://code.google.com/p/chromium/issues/detail?id=418858")

---

### Post by cariboo on 2015-01-05
Another 14.04 thread that was woken up. I'll put it back to sleep. Thread Closed.

---


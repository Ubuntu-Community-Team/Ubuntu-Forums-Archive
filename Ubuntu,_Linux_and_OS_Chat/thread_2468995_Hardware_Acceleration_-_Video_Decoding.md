---
title: "Hardware Acceleration - Video Decoding"
date: 2021-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2021-11-16
I am wondering why Linux Distributions (in general) do not have Video Hardware Acceleration available from the Browser.

I know it can be enabled.  Unfortunately, it's fussy, and sometimes does or does not work.  I am also aware of all of the variables included...

Nvidia or AMD drivers support Hardware Accelerated Video Decoding, but the browser doesn't work correctly with the drivers.
YouTube and other online Video Sources tend to use VP9, and some older video cards do not support it.  You can "force enable" H.264 on certain video websites, but again, it's "iffy."

So, what I am wondering, is why this isn't a priority?  Internet Video is no longer a "gimmicky" thing, it's how most people watch television and movies.  YouTube is only second to Netflix in being the biggest slinger of media over the internet.

Chromium, Chrome, Brave, Vivaldi, and even Edge do not support Hardware Acceleration in Linux.
Firefox is in the same basket.
Yeah, they can be enabled (sort of), but as soon as your driver or browser updates, it's all over.

Why is this not a priority in the Linux world?

---

### Post by monkeybrain20122 on 2021-11-16
> **Shibblet said:**
> 
Chromium, Chrome, Brave, Vivaldi, and even Edge do not support Hardware Acceleration in Linux.
Firefox is in the same basket.
Yeah, they can be enabled (sort of), but as soon as your driver or browser updates, it's all over.


Firefox supports VAAPI

All the Chromium based browsers did too, but stopped working when they were built from Chromium 95 because Chromium switched to Ozone platform and can't be disabled, a commit will land on Chromium 96 so it should work again.
[https://github.com/saiarcot895/chromium-ubuntu-build/issues/116](https://github.com/saiarcot895/chromium-ubuntu-build/issues/116) (**Edited:** VAAPI is working on Brave-Browser again after it was updated an hour ago, now it is based off Chromium 96. I think Google-Chrome and Vivaldi  should also work too if based off Chromium 96, though I don't have these installed)

With Nvidia it is a bit more complicated, apparently it works on FF with nouveau but not the Nvidia proprietary driver, the issue is with Nvidia did not DMA-BUF , not really the fault of the Linux world (though Nvidia-470  apparently has added this support, see link below). I don't know the status of Chromium based browsers on Nvidia.
[https://wiki.archlinux.org/title/firefox#Hardware_video_acceleration](https://wiki.archlinux.org/title/firefox#Hardware_video_acceleration)

The mpv addon for Firefox and Chrome works for all browsers, if you have a recent Nvidia card it does hardware decoding for vp9 too.

**P.S.** None of this will work with Firefox snap that is now default since Ubuntu 21.10 (though not the flavors) and the software store also offers Brave-browser snap which has multiple issues aside from hardware decoding (see brave's forum) so as a rule just get rid of all the snap versions and install the browsers properly with deb. For FF the deb is still available since flavors haven't switched to snap, otherwise just get the distro agnostic binary directly from Mozilla.

---

### Post by Shibblet on 2021-11-16
> **monkeybrain20122 said:**
> Firefox supports VAAPI

All the Chromium based browsers did too, but stopped working when they were built from Chromium 95 because Chromium switched to Ozone platform and can't be disabled, a commit will land on Chromium 96 so it should work again.
[https://github.com/saiarcot895/chromium-ubuntu-build/issues/116](https://github.com/saiarcot895/chromium-ubuntu-build/issues/116) (**Edited:** VAAPI is working on Brave-Browser again after it was updated an hour ago, now it is based off Chromium 96. I think Google-Chrome and Vivaldi  should also work too if based off Chromium 96, though I don't have these installed)
And that can be "enabled" to work on any of the browsers.  But none of them actually use VDPAU.  VAAPI seems more like "GPU Assisted" Decoding, and not actual Hardware Decoding.  Which is better than nothing.

> **monkeybrain20122 said:**
> With Nvidia it is a bit more complicated, apparently it works on FF with nouveau but not the Nvidia proprietary driver, the issue is with Nvidia did not DMA-BUF , not really the fault of the Linux world (though Nvidia-470  apparently has added this support, see link below). I don't know the status of Chromium based browsers on Nvidia.
[https://wiki.archlinux.org/title/firefox#Hardware_video_acceleration](https://wiki.archlinux.org/title/firefox#Hardware_video_acceleration)
Yeah, I'm starting to feel like Torvalds when it comes to Nvidia.  My new PC which should be here in a few days is an AMD Ryzen with a Radeon Vega 8 iGPU...  I'm not much of a gamer anymore.  Any games I really want to play will either be Streamed via XBox Live, or Stadia.

See, this is how learning about this all came up.  I wanted to be able to run processes in the background, and then not worry about those processes being slowed down by watching Videos or Playing Games on Stadia.  And because I cannot use Hardware Acceleration via the Browser in Kubuntu, I have to dedicate 20% of my CPU to decoding an incoming H.264 1080p Stream, and about %27-%30 to decoding an incoming 1080p VP9 stream.

> **monkeybrain20122 said:**
> The mpv addon for Firefox and Chrome works for all browsers, if you have a recent Nvidia card it does hardware decoding for vp9 too.
I was doing that for YouTube videos and the like... until this: [https://ubuntuforums.org/showthread.php?t=2468897]("https://ubuntuforums.org/showthread.php?t=2468897")

> **monkeybrain20122 said:**
> **P.S.** None of this will work with Firefox snap that is now default since Ubuntu 21.10 (though not the flavors) and the software store also offers Brave-browser snap which has multiple issues aside from hardware decoding (see brave's forum) so as a rule just get rid of all the snap versions and install the browsers properly with deb. For FF the deb is still available since flavors haven't switched to snap, otherwise just get the distro agnostic binary directly from Mozilla.
And again... we've come full circle.  [https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")

I appreciate the information.

Knowing all of this, why doesn't the Linux Community (i.e. Canonical, Google, Mozilla, Nvidia, AMD, etc.) fix this glaringly gaping open hole?
I can't imagine Linux users would rather not have it.
Does Wayland resolve any of these issues?

---

### Post by monkeybrain20122 on 2021-11-16
> **Shibblet said:**
> 


I was doing that for YouTube videos and the like... until this: [https://ubuntuforums.org/showthread.php?t=2468897](https://ubuntuforums.org/showthread.php?t=2468897)



Well that problem is solved, or at least there is a workaround. ;)

---

### Post by monkeybrain20122 on 2021-11-17
So I just checked. vp9 hardware decoding is working here on all browsers!
 
GTX1070, Nvidia 470.82. vdpau-va-driver-vp9 installed from this [fork]("https://github.com/xuanruiqi/vdpau-va-driver-vp9") which incorporates patches from Arch (development of the original branch appears to be stalled)

Hardware decoding (vp9) on Firefox just works, I don't remember having done anything other than enabling hw acceleration in about:config (layers.acceleration.force-enabled=true)  (check nvidia-smi, or Nvidia-settings > GPU utiliztion) 

Also works on latest Google-Chrome ([COLOR=#5F6368][FONT=Roboto]Version 96.0.4664.45) if start with command

[/FONT][/COLOR]```
LIBVA_DRIVER_NAME=vdpau VDPAU_DRIVER=nvidia /usr/bin/google-chrome-stable --use-gl=desktop --enable-features=VaapiVideoDecode
``` 

(on Youtube, more tools > developer tools > media and see that hardware decoding is enabled) However it seems that with hd decoding enabled more frames are dropped and 360 degree videos stops working (shows blackbox) These don't happen on Firefox

Also works on Chromium (but an older version 93) and vivaldi 4.3.2439.65 (latest) --just change /usr/bin/google-chrome-stable to /usr/bin/vivaldi in command above to start.

Haven't tested brave but I am pretty sure it would work too.


P.S. Now you may want to block av1 (there is an addon called Not yet Av1 for chromium based browsers) since hardware acceleration don't work on those. Some youtube videos will send you av1 stream and they are much worse than vp9 in terms of resource requirement.

---

### Post by marcjohnen on 2021-11-17
I managed to make it work on 21.10 with Nvidia with the following instructions:
Firefox: [https://discourse.ubuntu.com/t/enabling-accelerated-video-decoding-in-firefox-on-ubuntu-21-04/22081](https://discourse.ubuntu.com/t/enabling-accelerated-video-decoding-in-firefox-on-ubuntu-21-04/22081)
Chromium: [https://amigotechnotes.wordpress.com/2021/08/29/enable-video-hardware-acceleration-in-chrome-chromium-firefox-on-ubuntu-20-04/](https://amigotechnotes.wordpress.com/2021/08/29/enable-video-hardware-acceleration-in-chrome-chromium-firefox-on-ubuntu-20-04/)

---

### Post by Shibblet on 2021-11-17
> **marcjohnen said:**
> I managed to make it work on 21.10 with Nvidia with the following instructions:
Firefox: [https://discourse.ubuntu.com/t/enabling-accelerated-video-decoding-in-firefox-on-ubuntu-21-04/22081](https://discourse.ubuntu.com/t/enabling-accelerated-video-decoding-in-firefox-on-ubuntu-21-04/22081)
Chromium: [https://amigotechnotes.wordpress.com/2021/08/29/enable-video-hardware-acceleration-in-chrome-chromium-firefox-on-ubuntu-20-04/](https://amigotechnotes.wordpress.com/2021/08/29/enable-video-hardware-acceleration-in-chrome-chromium-firefox-on-ubuntu-20-04/)

Excellent!

I was able to get it to work in Brave (Chromium) with some similar ideas.  However, it only worked for "YouTube," and that's only if I used the "h264ify" extension.  My GTX 780ti does not do Hardware VP9.

Regardless... I also need it to work with Stadia and GeForce Now.  And it does not.  Even if I force both to use H.264 instead of VP9.

---

### Post by monkeybrain20122 on 2021-11-17
> **Shibblet said:**
> Excellent!

I was able to get it to work in Brave (Chromium) with some similar ideas.  However, it only worked for "YouTube," and that's only if I used the "h264ify" extension.  My GTX 780ti does not do Hardware VP9.

Regardless... I also need it to work with Stadia and GeForce Now.  And it does not.  Even if I force both to use H.264 instead of VP9.

It does vp9. Make sure you update your driver to Nvidia 470 and get the va-vdpau-vp9 driver from git like I posted above. I don't have h264ify installed, only thing is to block out av1.

---

### Post by Shibblet on 2021-11-17
> **monkeybrain20122 said:**
> It does vp9. Make sure you update your driver to Nvidia 470 and get the va-vdpau-vp9 driver from git like I posted above. I don't have h264ify installed, only thing is to block out av1.

The GTX 780ti does not support VP9 via Hardware.

That doesn't really matter though.  "h264ify" only works with YouTube, but it works great in those regards!  I can get Full VDPAU Hardware Acceleration for YouTube in a Browser.

My problem is with Stadia and GeForce Now.  They both send H.264 streams, but the I am not sure how to get the browser to utilize the VDPAU for those services.
I have a stadia extension that allows me to force H.264 streams, but it still doesn't use Hardware Acceleration.

I also have a Chromebook, ASUS C425.  This has built in VP9 decoding, and it works flawlessly with Stadia and GeForce Now using VP9 Streams.  Chromebooks are based off of Linux... and it's in the Chrome Browser... so what gives?

---


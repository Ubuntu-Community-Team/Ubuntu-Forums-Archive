---
title: "Serp6 wecam: only 7 fps??"
date: 2011-02-06
forum: System76 Support
---

### Post by natieo on 2011-02-06
I've been trying to use the webcam on the Serval Pro 6 and the framerates are abysmal: locked in around 7.5 fps.  I've run LUVCview and uvcdynctrl to try to adjust settings, but it seems there are none worth adjusting:

```
./uvcdynctrl/uvcdynctrl -c
Listing available controls for device video0:
  Backlight Compensation
  Sharpness
  Power Line Frequency
  Gamma
  Hue
  Saturation
  Contrast
  Brightness
```

There are many references out there to improved framerates by disabling auto exposure (which seems to be on -- it adjusts dynamically to changing lighting), but the webcam driver doesn't expose this setting??

Anyone able to get a decent framerate out of their webcam?  Or is this like the [touchpad]("http://ibuclaw.ubuntuforums.org/showthread.php?t=1506918&highlight=serp6+touchpad") -- an otherwise great laptop that somehow ships with bad drivers and no recourse?

Nate

PS more info: lsusb shows:

Bus 001 Device 005: ID 5986:0343 Acer, Inc

---

### Post by ajgreeny on 2011-02-06
Like most people, as far as I can make out, I've been totally unable to record any video using cheese using my simple, cheap Logitech webcam, and using wxcam, which will record videos, I get the same fps as you do, ie about 7 - 7.5.

I don't really find it a problem as I only use it for skype, and occasionally for stills, but the fps is rather limiting if you need video, I agree.

---

### Post by isantop on 2011-02-07
I think this has to do with the USB interface, first and foremost. By default, the video resolution should be set up for stills (i.e. high and therefore slow). You have to adjust this in each application, but if you reduce the resolution to something around 480x600 or so, which is decent for video calls and such, then you should be better.

---

### Post by natieo on 2011-02-07
Thanks for the reply.  I've got it set to 640x480 in GUVCVideo and it's still 7.5 fps. It's right around 7 no matter what resolution I pick, even a paltry 160x120! It does get much worse at higher resolutions (1-3 fps at 1024x768 for instance), but I can't coax anything better than 7.5 fps out of it even at super low frequencies.

It occurs to me that scaling might be happening AFTER the capture with the webcam, and therefore moot.  Is there a way (I can't find it) to change the resolution closer to the source?

---

### Post by isantop on 2011-02-08
When I adjust the resolution in Cheese, I see some big performance increases. Can you try it from there?

---

### Post by natieo on 2011-02-09
Nope, it's the same at 640x480 as it as at 160x120: really slow and blurry. Cheese is actually worse than the lower level interfaces I've tried.

I'm on 10.04 LTS with 2.6.32-28-generic kernel, and the webcam is the BisonCam NB Pro. Latest System76 drivers. Are you using similar hardware? It's frustrating because the Serp6 is such a beast in general I can't quite imagine where the bottleneck is that can't keep up with 640x480 video!

---

### Post by mboney on 2011-02-24
I've noticed a similar situation on my Serp6.  The webcam output is like watching a flip book, heh.

---


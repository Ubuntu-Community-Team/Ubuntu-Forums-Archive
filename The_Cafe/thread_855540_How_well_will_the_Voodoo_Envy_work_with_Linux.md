---
title: "How well will the Voodoo Envy work with Linux?"
date: 2008-07-10
forum: The Cafe
---

### Post by 50words on 2008-07-10
Since it has a version of Linux pre-installed on the motherboard, I would think it should work great with Ubuntu.

The [hardware specs]("http://www.voodoopc.com/#/productsenvy") make me optimistic. Intel processor with integrated X3100 graphics and WiFi.

The integrated webcam may not work quite as smoothly, of course.

The touchpad supports multi-touch, which probably will not do much with Linux right off the bat, although I think there are a few multitouch projects.

Will the touchpad proximity sensor work?

All in all, I think the Envy would be a pretty slick ultra-mobile laptop, but not if I have to run Windows.

---

### Post by midtown on 2008-11-12
> **50words said:**
> All in all, I think the Envy would be a pretty slick ultra-mobile laptop, but not if I have to run Windows.

I have been looking around for an answer to this as well. The Envy 133 looks nice but if it can't provide a fairly pleasant Ubuntu experience I am not interested. I hope someone will pop in with an answer!

---

### Post by profmaad on 2009-02-04
I own a Voodoo Envy since October and am using Ubuntu Linux (8.10) on it exclusively.

I works quite nice, most stuff worked out of the box. Altough it worked a bit better with Hardy, I think.

What works is:
 - Sleep
 - Hibernate
 - Brightness buttons
 - Volume buttons
 - Wifi kill button
 - Webcam
 - all Ports
 - ExpressCard/34 slot
 - audio output (both speakes and headphones)
 - most other stuff

What doesn't (yet) work:
 - audio input via internal or external microphone (will probably be fixed with upcoming versions of alsa)
 - Mute button (the light on it is always on, regardless of mute state. Pressing the button also doesn't mute or anything but rather disables the keyboard for some while)
 - Multitouch (this is just not really in linux yet, so it can't work)
 - The LAN2Wifi Connection on the Aura power brick (you could probably get it working though, I just didn't have the time to play with it yet. Got myself a nice ExpressCard Gigabit Ethernat card, that works way better)

Any questions regarding this gorgeous peace of hardware art can be directed to me. ^^

Bye,
Prof. MAD

---

### Post by birdofhades on 2009-03-29
Prof. MAD,

Would you mind telling me if the keyboard proximity detector and ambient light sensor work? Thanks

---

### Post by profmaad on 2009-06-23
Hi birdofhades,

the proximity sensor for the keyboard works without any problems, it also correctly locks the touchpad. Sometimes its a bit oversensitive though.

I guess the ambient light sensor works, but I'm not sure. Settings the display backlight manually works perfect, but I don't know how to tell Ubuntu to use the ambient light sensor so I don't know whether it works. I never missed it, though.

Little general update: By now, audio subsystem works flawless (also the microphone). Mute button hasn't become any better. Getting the Aura PowerConnect Wifi working is possibly, you need to extract your WPA2 key from the original Windows installation on the device though. If you can not get it, try resetting the Aura, that should work as well.

Bye,
Prof. MAAD

---

### Post by hlenz on 2010-08-09
Hello,

I noticed it has been a while, since this threat was active. Howev,er I recently installed Lucid Lynx on my Envy 133 and I must say I love it.

Unfortunately I have to problems. The first one is the constant light of the mute button discribed already earlier. The second problem is that the computer doesn't hibernate. 

it would be nice if  anybody has a solution to these two problems

Thanks in advance for your help!

---

### Post by inverser on 2010-12-26
> **birdofhades said:**
> Prof. MAD,

Would you mind telling me if the keyboard proximity detector and ambient light sensor work? Thanks
Hello, I know it's been a while but I'm running Maverick and both the proximity and ambient sensor function well.

The always-lit mute light is driving me insane, though. Its xev output is strange:

```
FocusOut event, serial 36, synthetic NO, window 0x5400001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 36, synthetic NO, window 0x5400001,
    mode NotifyWhileGrabbed, detail NotifyNonlinear
```

---


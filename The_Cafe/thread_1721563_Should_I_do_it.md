---
title: "Should I do it?"
date: 2011-04-04
forum: The Cafe
---

### Post by Legendary_Bibo on 2011-04-04
For the longest time I could never get my HDMI port to work on my laptop under Maverick, the VGA port works just fine though. I looked into it and it has to do with the fact that I have an ATI card that uses FGLRX drivers apparently. Is this the case? So I'm thinking about backing my /home up and writing out a script that has all my installed programs, as well as all my custom configurations, and I'm going to try getting my HDMI port to work. Here's my question though, does it look better? I have a 1080p monitor, and so I was wondering is if the picture quality will look better or not. If it's insanely better I'll start diving into it (I don't mess with video settings ever, but now that I have more experience with using the terminal, I think I could fix things by the way of the terminal). If there's no difference then I'll just avoid it. I have my PS3 hooked up to it, and I could get an HDMI switch which would mean one less cable (audio) I would have to pull in and out every time I switch between my laptop and my PS3.

---

### Post by sydbat on 2011-04-04
> **Legendary_Bibo said:**
> For the longest time I could never get my HDMI port to work on my laptop under Maverick, the VGA port works just fine though. I looked into it and it has to do with the fact that I have an ATI card that uses FGLRX drivers apparently. Is this the case? So I'm thinking about backing my /home up and writing out a script that has all my installed programs, as well as all my custom configurations, and I'm going to try getting my HDMI port to work. Here's my question though, does it look better? I have a 1080p monitor, and so I was wondering is if the picture quality will look better or not. If it's insanely better I'll start diving into it (I don't mess with video settings ever, but now that I have more experience with using the terminal, I think I could fix things by the way of the terminal). If there's no difference then I'll just avoid it. I have my PS3 hooked up to it, and I could get an HDMI switch which would mean one less cable (audio) I would have to pull in and out every time I switch between my laptop and my PS3.DO IT!!

I have one of my boxen hooked up to our 46" HDTV via HDMI and I find the overall picture quality well worth it. However, I have an NVIDIA card and have had no problems with configuration.

Also, DO IT!!!

---

### Post by Paul820 on 2011-04-04
I have an ATI using fglrx and the HDMI port on my lappy works when connected to a HD tv. If it's not working for you then do what you need to get it working. Good luck! :D

oh yeah, my graphics card is ATI mobility readeon HD 4250.

---

### Post by grahammechanical on 2011-04-04
In theory the picture quality should be better. With VGA you get digital to analogue conversion of the signal on the graphic card. Then you get analogue to digital conversion inside the Monitor. VGA was designed for CRT monitors which are analogue devices. The computer is a digital device so there has to be digital to analogue conversion to use a CRT monitor. Flat screen monitors are digital devices. So, when using VGA there has to be a analogue to digital conversion inside the monitor. It is possible that all this converting may degrade the picture quality.

I saw a post recently where someone could not get HDMI to work. The graphic card had two HDMI connectors. With the cable plugged into one connector it would not work but when he tried it in the other connector it worked.

Regards.

---

### Post by mips on 2011-04-05
> **Legendary_Bibo said:**
> Here's my question though, does it look better?

Yes, you will notice a difference between using hdmi & vga, well at least I do.

Instead of going through this hassle why don't you do a temp install to a flash stick and try getting it to work in there then you can transfer the settings to your standard install. Alternatively just image / try and get the hdmi working and if you bork / you can just restore it from the image.

---

### Post by doorknob60 on 2011-04-06
Check the Catalyst Control Center if you haven't. All I have to do with my ATI card is plug in the cable and enable it in the AMD control center (sudo amdcccle), and it works fine (and Pulseaudio has no problems using it for sound output either. If you want simultaneous output you can enable it in paprefs). If you have the Catalyst driver installed, it should come with that. I assume you tried this, but I'm pointing it out just in case you didn't know about it :)

---


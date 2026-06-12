---
title: "Open Movie Editor Crashes All the Time"
date: 2008-12-01
forum: Ubuntu Studio
---

### Post by MusicallyInspired on 2008-12-01
This is the most unstable program I've ever used. Ever. But I hear a lot of good things about it so obviously something must be wrong on my end.

I'm running Ubuntu Studio Intrepid. I open the program and this is what the terminal spits out while it's running:

```

When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
Libquicktime Version: 1.0.2
Libquicktime API Version: 9
libavcodec Version: Lavc51.50.0
libavformat Version: Lavf52.7.0
/etc/debian_version:
lenny/sid
/etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
----8<-----------------------
Jack Samplerate: 48000
cannot lock down memory for RT thread (Cannot allocate memory)
XRequest.158: BadRequest (invalid request code or no such operation) 0x4c00002
Insufficient GL support

```

It doesn't crash yet, but when I try to add audio and video/pictures to the timeline and press play it seg faults and closes. This also happens while trying to do other random things within the program. Any idea what's causing this?

Also when I add audio it only shows a portion of the wave output and the rest is all black where there should be more.

---

### Post by zettberlin on 2008-12-01
> **MusicallyInspired said:**
> 
cannot lock down memory for RT thread (Cannot allocate memory)

First: get the Ubuntu Studio Control (uscontrol) utility, make and join the group audio using the user-admin tool and set /etc/security/limits.conf so the users in the group audio have sufficient rights to start/use  jackd as needed.

> **MusicallyInspired said:**
> 
XRequest.158: BadRequest (invalid request code or no such operation) 0x4c00002
Insufficient GL support


there might be something wrong with your video-driver also....

---

### Post by MusicallyInspired on 2008-12-01
What exactly do I add to the @audio line in limits.cfg? Right now it says "-     rtprio     99". Also, since I'm running Ubuntu Studio Intrepid that means there is no real-time kernel. Will that affect it? Right now it's still crashing after reboot.

And regarding my video driver. I've had problems since I started using Ubuntu that I've never solved. I have an ATI X1650 Pro AGP card and I've never gotten it to work right. And there's no help online that has ever helped me. I even made a thread about it here and nothing helped. Can I still use it even though it says that? I can watch videos fine with players and such.

**EDIT:** Ok, never mind. It seems the problem was my video driver. I changed it from fglrx to ati and now it works fine and I even get 3D which I never had before with Hardy! Thank you.

---


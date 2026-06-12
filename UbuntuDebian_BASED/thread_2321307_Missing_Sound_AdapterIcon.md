---
title: "Missing Sound Adapter/Icon"
date: 2016-04-21
forum: Ubuntu/Debian BASED
---

### Post by mrl-g on 2016-04-21
Hello, im using a ubuntu's based and I had some problems with my sound now.
Since yesterday, my sound icon is missing from the tray, but it's "invisible" between others. If I open it, cant change the volume bar and uncheck muted box.
The sound is working btw, but I have almost no control over the volume. With some mixed I opened, I can control it (maybe was Alsa?not sure).

Opening my Sound settings, there's no adapter at outputs, nor inputs.
I've installed pulseaudio-dlna before this problem, maybe its related. 
when trying to run pulseaudio-dlna or others pulseaudio's commands, I receive a fail message with "E: [pulseaudio] daemon-conf.c: [/etc/pulse/daemon.conf:82] Invalid number of fragments '0'."

running:  
```
     aplay -L
E: [pulseaudio] daemon-conf.c: [/etc/pulse/daemon.conf:82] Invalid number of fragments '0'.
E: [pulseaudio] daemon-conf.c: [/etc/pulse/daemon.conf:82] Invalid number of fragments '0'.
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, 92HD81B1X5 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, 92HD81B1X5 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD81B1X5 Analog
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions

```

What could I do to fix this? 
thanks

---

### Post by Bucky Ball on 2016-04-21
Welcome. Which 'Ubuntu-based'? The more specific you can be the more chance you have of support. Also, please see the green link in my signature below for how to use code tags for terminal output. Thanks. ;)

---

### Post by mrl-g on 2016-04-22
> **Bucky Ball said:**
> Welcome. Which 'Ubuntu-based'? The more specific you can be the more chance you have of support. Also, please see the green link in my signature below for how to use code tags for terminal output. Thanks. ;)

I'm using Elementary OS 0.3.2 Freya. Sorry about that and thanks for fixing my post.

---

### Post by deadflowr on 2016-04-22
*Thread moved to **Ubuntu/Debian BASED**.*

And added the Elementary prefix for ya

---

### Post by mrl-g on 2016-04-23
I've gived up on elementary, then installed ubuntu 16.04 LTS, that was all good, until I install that pulseaudio-dlna again.

sound was working good, installed pulseaudio-dlna, runned it, it was working propely. 
Then I shutted the terminal and installed alsa-tools-gui, because I need to use that hdajackretask for my laptop w beats audio. Selected the pins, when clicked on "Apply", a message poped up saying that something was busy.

Then I tested my speakers again, no sound at all. Opened the sound settings, there wasn't any adapters there....

Tried to run pulseaudio-dlna again, it open but doenst work as it should.
running pulseaudio:
```

$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.



```

---

### Post by Bucky Ball on 2016-04-23
Sounds like this has changed quite significantly. For starters you're no longer using Elementary and the problem in the title of your thread is fixed. 

For the best chance of support I'd mark this thread as solved and start a new one with the details you've given here. Post a link to this one if you think it's relevant. Good luck.

---


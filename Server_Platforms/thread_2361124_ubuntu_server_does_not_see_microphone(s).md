---
title: "ubuntu server does not see microphone(s)"
date: 2017-05-12
forum: Server Platforms
---

### Post by pruda on 2017-05-12
I'd like to record from webcam microphone on headless server 17.04, but ubuntu does not see audio devices, only some dummy. I have followed [instructions for headless server]("https://askubuntu.com/questions/28176/how-do-i-run-pulseaudio-in-a-headless-server-installation"), but I do not see any microphone, there should be jack mic and webcam mic. What am I missing? Thank you.
```

me@ubuntus:~$ lsusb
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
.
.
me@ubuntus:~$ pacmd list-sources
1 source(s) available.
  * index: 0
        name: <auto_null.monitor>
        driver: <module-null-sink.c>
        flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE
        priority: 1000
        volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
                balance 0.00
        base volume: 65536 / 100% / 0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max rewind: 344 KiB
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 0
        configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
        monitor_of: 0
        module: 10
        properties:
                device.description = "Monitor of Dummy Output"
                device.class = "monitor"
                device.icon_name = "audio-input-microphone"

```

---

### Post by TheFu on 2017-05-12
Is this a physical machine or a VPS?

---

### Post by pruda on 2017-05-14
Hi, it's physical machine, old netbook.

---


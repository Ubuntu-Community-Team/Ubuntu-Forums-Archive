---
title: "segfault with USB Edirol UA-25 ext soundcard playback"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by believekevin on 2008-09-22
when i try to playback sound through an Edirol UA-25, i am seeing segfaults in the kern.log like this:
```

kernel: [  222.573112] gnome-sound-pro[5683]: segfault at b54b0000 eip b6cda8dc esp b6023fd0 error 7
kernel: [  822.957920] gnome-sound-pro[6013]: segfault at b555a000 eip b6d848dc esp b60cdfd0 error 7
```

the soundcard is detected fine:
```

$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 23
 1 [UA25           ]: USB-Audio - UA-25
                      EDIROL UA-25 at usb-0000:00:1d.2-1, full speed
```

but playback crashes like this:
```
$ speaker-test -c2 -D plughw:UA25 -twav

speaker-test 1.0.15

Playback device is plughw:UA25
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 97 to 190217
Period size range from 48 to 95109
Using max buffer size 190216
Periods = 4
was set period_size = 0
was set buffer_size = 190216
 0 - Front Left
Floating point exception

```

anyone know what's up with this?

BTW, i'm on Ubuntu 8.04 - the Hardy Heron

---


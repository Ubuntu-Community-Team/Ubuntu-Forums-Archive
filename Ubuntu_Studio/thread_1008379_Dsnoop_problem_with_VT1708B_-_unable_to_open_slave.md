---
title: "Dsnoop problem with VT1708B - unable to open slave (on second arecord)"
date: 2008-12-11
forum: Ubuntu Studio
---

### Post by hackeron on 2008-12-11
I'm having a problem opening a dsnoop device pointing to VT1708B multiple times:

```

# arecord -c2 -r 44100 -D plug:HDA_Intel test1.wav &
Recording WAVE 'stdin' : Unsigned 8 bit, Rate 44100 Hz, Stereo
#
# arecord -c2 -r 44100 -D plug:HDA_Intel test2.wav
ALSA lib pcm_dsnoop.c:641:(snd_pcm_dsnoop_open) unable to open slave
arecord: main:590: audio open error: Invalid argument

```

This is my asoundrc:

```

pcm.HDA_Intel {
type dsnoop
ipc_key 822256
    slave {
        pcm "hw:1,0"
        rate 44100
        channels 2
    }
}
pcm.Audigy_SE__SB0570 {
type dsnoop
ipc_key 944213
    slave {
        pcm "hw:0,0"
        rate 44100
        channels 2
    }
}

```

I have no problem opening the Audigy device multiple times:

```

# arecord -c2 -r 44100 -D plug:Audigy_SE__SB0570 test3.wav &
Recording WAVE 'stdin' : Unsigned 8 bit, Rate 44100 Hz, Stereo
#
# arecord -c2 -r 44100 -D plug:Audigy_SE__SB0570 test4.wav
Recording WAVE 'stdin' : Unsigned 8 bit, Rate 44100 Hz, Stereo

```

I'm using 1.0.18a driver and 1.0.18 libs downloaded and compiled from the alsa website (the drivers/libs shipped with ubuntu didn't work either)

Any ideas?

---

### Post by hackeron on 2008-12-22
anyone?

---

### Post by hackeron on 2009-01-06
Anyone at all? :( -- This worked fine until I upgraded from gutsy to intrepid.

---

### Post by Stochastic on 2009-01-06
It looks to me like there is nobody with that level of expertise on these forums, try the linux audio users mailing list or IRC channel.

---

### Post by hackeron on 2009-07-03
Still having this issue :( - Anyone have any ideas at all?

---

### Post by hackeron on 2009-07-04
Finally found a solution, adding: defaults.pcm.subdevice 1 to asoundrc (the default is -1 for some reason).

---


---
title: "ALSA loopback, trying to record from multiple subdevices"
date: 2017-05-19
forum: Virtualisation
---

### Post by ravendark2 on 2017-05-19
Hello, 

I am using a VM with Ubuntu 16.04 and what I am trying to do is record multiple sources.
I read about ALSA snd_aloop having 8 subdevices.
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
```

What works so far, I can play for example a network stream (internet radio) with mplayer

```
mplayer hw:0,0,0 -ao alsa -af volume=10:1 -prefer-ipv4 http://someradio1
```

and record it:

```
arecord -D hw:0,1,0 -f S32_LE -c 2 -r 48000 /home/raven/record1.wav
```

Now if I have understood correctly, if I use mplayer and use a different subinterface, eg. **hw:0,0,1 , **I can record using **hw:0,1,1**. Is this correct?
Well this does not work, recording is ok using **hw:0,1,0** , but using **hw:0,1,1** records nothing.

Could you help me please?

Edit:
Problem solved, the mplayer command was wrong... to access a subdevice needs parameter: alsa:device=hw=0.0.0

---

### Post by Autodave on 2017-05-19
Let's simplify this a bit, if you don't mind. Exactly what are you trying to record?

Secondly, have you determined that your sound card is capable of duplexing? Most sound cards are NOT capable of duplexing (playing and recording at the same time).

Lastly, keep in mind that if you are trying to record copyrighted material, you probably will not receive help from this forum since that is illegal.

---

### Post by ravendark2 on 2017-05-19
There is no issues with copyrights, I have a license for that.
There is no soundcard as well, as I said I am just using snd_aloop on a Virtual Machine (VMware).

I am trying to copy some online radio stations (I work in a company that does that)

What I don't know is why if I try to record one stream works ok, but not more than one (if I try 2 for example in different subdevices of the loopback, it does not work, arecord will record the first one just fine and the second one is empty)

---

### Post by howefield on 2017-05-19
Thread moved to the "*Virtualisation*" forum.

---


---
title: "Mixxx cannot access the sound device"
date: 2010-01-14
forum: Ubuntu Studio
---

### Post by jocampo on 2010-01-14
I am trying to use a Bose® SoundLink wireless music system (you connect the system via USB dongle) with mixxx 1.7.0 The Bose system works perfectly with any other audio player, but mixxx refuses to use Bose as "master" and main sound output. Instead, I'm getting this error

[I]Mixxx cannot access the sound device 1 ... Another application is using the sound device or it is not plugged in.
Retry after closing the other application or reconnecting the sound device
Reconfigure Mixxx to use another sound device.[/I] 

It is obvious that the device is busy some way but why and how can I "kill" the other process. 

To explain more in detail why I'm using the Bose or how it works, is simple: the dongle uses the internal audio card and "transports" the sound and information via wireless to the Bose speaker.

Thanks in advance,

PS: I've noticed that on my other partition, with Ubuntu Jaunty, I can use OSS and it works on mixxx, but not with ALSA. On Ubuntu Studio Karmic, does not work at all on mixxx, even with OSS.

---

### Post by thorgal on 2010-01-15
user "fuser":

for hw:1 :

```

fuser -v /dev/snd/pcmC1*

```

it will display the process ID and name of the app that has a grip on your device. You can then kill it.

---

### Post by jocampo on 2010-01-15
> **thorgal said:**
> user "fuser":

for hw:1 :

```

fuser -v /dev/snd/pcmC1*

```

it will display the process ID and name of the app that has a grip on your device. You can then kill it.

I think I tried already? let me check again maybe I killed the wrong process.

Thanks for reply

---

### Post by jocampo on 2010-01-15
Here's fuse output:

```
jocampo@studio:~$ fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  jocampo    2629 F.... pulseaudio
/dev/snd/controlC1:  jocampo    2629 F.... pulseaudio
                     jocampo    3536 F.... jackd
/dev/snd/pcmC1D0p:   jocampo    3536 F...m jackd
/dev/snd/seq:        jocampo    2999 F.... qjackctl.bin
                     jocampo    3536 F.... jackd
                     jocampo    3550 F.... mixxx
jocampo@studio:~$ 
```

It looks (someone correct me if I'm wrong) 2629 or pulseaudio is using that resource too so I can not set master output on mixxx, to start using BOSE output via Jack. 

After killing pulseaudio, stop and restart Jack and Mixxx, the problem persists and now fuse's output changed to:

```
jocampo@studio:~$ fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  jocampo    3903 F.... pulseaudio
/dev/snd/controlC1:  jocampo    3935 F.... jackd
/dev/snd/pcmC1D0p:   jocampo    3935 F...m jackd
/dev/snd/seq:        jocampo    2999 F.... qjackctl.bin
                     jocampo    3935 F.... jackd
                     jocampo    3949 F.... mixxx
jocampo@studio:~$ 
```

Now it looks like C1 is not shared but mixxx continues saying "can not open device"

any other suggestion?

---

### Post by AutoStatic on 2010-01-16
Create a *$HOME/.pulse/client.conf* file with the line *autospawn = no* and try killing Pulseaudio again.

---

### Post by jocampo on 2010-01-16
> **AutoStatic said:**
> Create a *$HOME/.pulse/client.conf* file with the line *autospawn = no* and try killing Pulseaudio again.

Thanks but no luck.

Here's the fuse output just before open mixxx and after I started Jack with the Bose device

```
jocampo@studio:~/.pulse$ fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC1:  jocampo    5747 F.... jackd
/dev/snd/pcmC1D0p:   jocampo    5747 F...m jackd
/dev/snd/seq:        jocampo    4935 F.... qjackctl.bin
                     jocampo    5747 F.... jackd
jocampo@studio:~/.pulse$ 
```

it should work, C1 is used by Jack only, but still gives an error (please see screenshoot). I decided to test with audacious and had no issues at all; it worked! I was able to play the mp3 file with audacious and set output to Jack (via Bose)

---

### Post by thorgal on 2010-01-16
mmmm, looks to me that you did not set up mixxx to use jack ... sounds like a dumb statement but better check the obvious.

---

### Post by jocampo on 2010-01-16
> **thorgal said:**
> mmmm, looks to me that you did not set up mixxx to use jack ... sounds like a dumb statement but better check the obvious.

Yes I did :-) .. it works when I use the laptop's speakers and UCA202 with my headphones.

But I think I fixed the problem ;-) .. although, I do not fully understand why or the technical reason. I decided to open mixxx via console and saw some sample rate errors. I changed to 48000 (on mixxx) and now it works; it opens my Bose audio device and I can use mixxx using Bose as master and the UCA202 for my headphones, both via Jack. 

But why 44100 sample rate does not work on mixxx when choosing Bose as master? hmmm...

---

### Post by scathdesolas on 2010-05-23
I had the same problem. Said it was in use. Couldn't configure anything. This fixed my issue with Mixxx. Just changing to 48000. Weird and strange I tried everything too. I have the Nvidia nForce2. intel8x0m.

Just trying to help :popcorn:

---

### Post by sgx on 2010-05-24
> **scathdesolas said:**
> I had the same problem. Said it was in use. Couldn't configure anything. This fixed my issue with Mixxx. Just changing to 48000. Weird and strange I tried everything too. I have the Nvidia nForce2. intel8x0m.

Just trying to help :popcorn:
Confirmations are important. Computers are good at math,
and don't cut me any slack for my lack of math skills :)

---

### Post by lzap on 2010-07-28
Was because your sound card expect 48000. I know Behringer UCA needs that.

---


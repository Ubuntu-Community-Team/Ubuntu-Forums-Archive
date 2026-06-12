---
title: "How to get M-Audio Mobile Pre Microphone to audio out?"
date: 2012-01-28
forum: Ubuntu Studio
---

### Post by Niels Olson on 2012-01-28
My daughter wants to listen to music any which way (youtube, spotify, performous, whatever) and sing along with it into a microphone, hearing her voice amplified in real time. I got her an m-audio microphone and the m-audio MobilePre for christmas, and installed Ubuntu Studio.

I have not been able to get this to work. I have the jack realtime kernel module running right now. I have tried alsamixer, qjackctl, performous, and pykaraoke, all to no avail. Audacity will record from the microphone, performous is clearly getting input from the mic.

I can get real time midi output with a midi controller via timidity and synthesia, but I can't get mic output. Any suggestions?

---

### Post by jejeman on 2012-01-28
First, you need to think, do you really need jack?
Which programs you plan to use, and do they work with just alsa/pulseaudio?
I will exclude jack because you want to listen to youtube. Yes, you can connect it via pulseaudio jack sink, but, is it gone to be stable?
So, do you need jack?

What is that mic? Is it usb or plain analog? And what is the soundcard?
You can monitor your mic thru alsamixer playback, if there is any fader for it.

---

### Post by sgx on 2012-01-29
> **Niels Olson said:**
> My daughter wants to listen to music any which way (youtube, spotify, performous, whatever) and sing along with it into a microphone, hearing her voice amplified in real time. I got her an m-audio microphone and the m-audio MobilePre for christmas, and installed Ubuntu Studio.

I have not been able to get this to work. I have the jack realtime kernel module running right now. I have tried alsamixer, qjackctl, performous, and pykaraoke, all to no avail. Audacity will record from the microphone, performous is clearly getting input from the mic.

I can get real time midi output with a midi controller via timidity and synthesia, but I can't get mic output. Any suggestions?
Hi, if these are two separate usb devices, study info and screenshots at links 4 and 8 from the qjackctl wiki to configure and connect them, with the mic as input device, and the Mobile Pre as output device.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

A motherboard soundchip may also be chosen as output device. If the mic plugs into Mobile Pre, choose the pre as both the input and output device, if it does not work, choose the pre as input, and motherboard sound as output.

If all fails, try the other mAudio kernel module from a terminal

sudo modprobe snd_ice1724

A blank prompt after the command means success, reboot, and try again. snd_ice1712 is the most used for maudio devices, the Pre may be a bit different inside.   lsmod   lists your kernel modules, and their interactions. 

aqualung is a handy mp3 player that works with jackd. Use opera web browser, empty its cache, view the desired youtube with the cache
folders data folder open in a file manager, with 'sort by size'
chosen. The video will be the one growing in size, probably the largest
in short order.

/home/you/.opera/cache/g_002B/opr004AU.tmp
(g_002B/opr004AU.tmp are typical examples, not exact names)  
  
Rename opr004AU.tmp using .flv extension, save it,

Imogen-Heap Just For Now.flv

then use an flv2mp3 conversion utility to make it a plain mp3.
rakarrack multifx, or calf plugins can be inserted in qjackctl for vocal fx. 

timemachine can record each part routed to it, so
she could start timemachine recording (just make the qjackctl connections, and hit the center record button)
start the song playing in aqualung, and sing along. Press the center
button to stop recording. It can then be imported into audacity, for editing, and exported as an mp3 or standard .wav file. This can be repeated, to record a harmony.

Old cassettes/CDs can be recorded into audacity with the pre line-in, to get a collection of backings started, without spending a fortune
Cheers

---


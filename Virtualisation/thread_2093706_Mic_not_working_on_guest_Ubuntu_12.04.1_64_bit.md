---
title: "Mic not working on guest Ubuntu 12.04.1 64 bit"
date: 2012-12-11
forum: Virtualisation
---

### Post by jlanza on 2012-12-11
Hi,

I'm virtualizing an ubuntu installation using Virtual Box. Sound playing is working correctly, but when I tried to record, nothing happens. As host, I'm using win7.

```
$ lspci| grep audio
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)

```
When clicking on Sound Settings -> Input, I got:
```
Video Built-in Audio
Analog input Built-in Audio
Line In Built-in Audio
Microphone 1 Built-in Audio
Microphone 2 Built-in Audio

```
I've checked both Microphones but the input level is always blank.

I have tried also recording 
arecord -vv -d 4 /tmp/test-mic.wav && aplay /tmp/test-mic.wav

But the output file has no sound in it.

Besides, I've tried with alsamixer, but don't know if I did correct:
1) F4 capture
2) I have LR Caputre in MIC and Capture, but in Mic there is no column with the level. It is only displayed on Capture.

After modifying anything I run alsactl store and then open again the Sound setting to check if micro works, with no luck.

Any idea is more than welcome. 
TA

---

### Post by prkrol on 2013-03-12
Hi

Have you managed to solve this problem?

I have the same :(

---

### Post by jlanza on 2013-03-12
The only solution has been using VmWare instead of Virtual box. This way it works if I plug the headphone before starting the Virtual Machine.

---


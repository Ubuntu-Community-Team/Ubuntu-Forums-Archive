---
title: "I can't record with"
date: 2011-10-01
forum: Ubuntu Studio
---

### Post by joepepp on 2011-10-01
Hello,

I am trying to record my guitar on Ardour, but it seems Ardour can't feel the signal.

How I do connect the guitar to PC: I'm using the effect processor Line 6 Pod X3; its "right output" is connected to the "mic" input of my pc using an adapter 1/4" to 1/8".

Few days ago my OS was Ubuntu 10.04 and I was able to redirect the mic input toward the speakers by using Jack: without Jack running, no sound; on the contrary after connection I could ear the sound. I am not really an expert of Linux systems, but I think this is normal since Ubuntu do not direct automatically the sound in input towards the output and Jack makes the job.

However in this configuration I have been able to open Ardour and record my guitar. No problems yet!

Since "better is the enemy of good enough" I then decided that I wanted to exploit better my Pod; actually the previous configuration had the drawback of a constant "hummmmmmm" that prevented my recording to sound really good.
So I decided to google about "usb+pod+ubuntu" and I found somewhere that the usb connection Pod->Pc could work on Ubuntu 10.10; I decided then to upgrade my OS, and the problems started.

It seems to me that the root of everything is that with Maverik I do not need any more of Jack in order to redirect my audio input (mic) towards the speakers, it works already whenever I plug the Pod to the mic port (still persists the disturbing "hummmmm"). This fact could be even positive, the problem is that, even if I run Jack and set up the connections exactly as previously, Ardour do not "ear" the audio input.

You see that so far the problem is just with analog in/out connection; concerning with USB connection I was not able to figure out how to proceed. Actually I read on this forum that is not possible to use the USB connection since there are no drivers for the Pod X3 :(
nevertheless I have to say that in my audio configuration window (system->Preferences->Audio) I can see Ubuntu recognize the Pod device. But I wasn't able to find somewere if this is enough to think to use the Pod with the USB port.

Finally I upgraded to Ubuntu Studio by following the procedure described [here]("http://wiki.ubuntu-it.org/Multimedia/UbuntuStudio") (sorry it is in italian, essentially I took the package ubuntustudio-desktop), but I have the same problems as before.

Someone has any idea?

P.S. sorry for the lack of technical details, I just moved on linux OS.

---

### Post by jejeman on 2011-10-01
You should use line in instead of mic, if you have one.
In alsamixer you can unmute playback for line in, or mic, for monitoring.
Go in
```
alsamixer
```
and unmute playback channels, adjust levels for monitoring purposses. If you hear the sound, then maybe youre capture settings are wrong.
So, go to capture section (F4), select the input you use and adjust the levels.

---

### Post by sgx on 2011-10-01
[http://www.tanzband-scream.at/line6/driverdocs.pdf](http://www.tanzband-scream.at/line6/driverdocs.pdf)

according to this pdf, the X3 is not supported by native usb connection. But the analog ports will work, headphone and line-out.
You may want to sell it before it is obsolete. edit: I should say,
'while it's value remains high'. Good sound, to me, is never obsolete, but now that the HD 500 group has been out for awhile, buyers will leverage the age factor, when dickering. If it gets a good price, you might make
some linux compatible purchases, and come out ahead on all fronts

I use a fender mustang usb amp, $50-$99,

[http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000](http://www.musiciansfriend.com/guitars/fender-mustang-i-20w-1x8-guitar-combo-amp/h61791000001000)

it requires no driver, the 24 presets you choose or design, are a dial-nudge away. Its usb compliant, so all linux software sees and hears it, when it is the selected input device. Sounds fantastic.
A linux editor called 'plug' has been written:

[http://piorekf.org/plug/](http://piorekf.org/plug/)

for connections info,

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl) 

-start with the bottom link,
and work up, to see pics/tips of connections, and general useful guidance.

Cheers

---

### Post by sgx on 2011-10-01
An maudio 24/96 pci soundcard, in a desktop computer with nVidia graphics, is a very hassle-free linux setup. If your pod has digital i/o, this has inputs to record it, and the line-in sounds excellent too.

[http://www.musiciansfriend.com/pro-audio/m-audio-audiophile-2496-pci-digital-audio-card/701341000000000](http://www.musiciansfriend.com/pro-audio/m-audio-audiophile-2496-pci-digital-audio-card/701341000000000)

found this, not linux specific, but good pod tips

[http://www.benvesco.com/blog/category/pod-x3-live-tips-and-tricks/](http://www.benvesco.com/blog/category/pod-x3-live-tips-and-tricks/)

Cheers

---

### Post by joepepp on 2011-10-05
Thank you guys but you are not answering to my main answer:

with ubuntu 10.04:
1a) I plug the analog output of the Pod to the mic-in: no sound
2a) I tell Jack to connect the mic-in to speakers: I get sound
3a) Ardour can record what I play

on the contrary with ubuntu 10.10:
1b) I plug the analog output of the Pod to the mic-in: already I get sound
2b) I start Jack as step 2a
3b) Ardour can't record. It seems it does not feel the mic-in.

Why there is this difference? Does 1b mean that there is some kind of short-cut and Jack can't any more manage the audio? I am sure the system is working, because I already tried with the previous version of Ubuntu.

Giuseppe

---

### Post by jejeman on 2011-10-05
There are two sets of faders in alsamixer.
1. for playback (F3)
2. for capturing (F4)

For 1a you need to unmute and adjust the level of playback for physical input you are using to here sound.
> Does 1b mean that there is some kind of short-cut and Jack can't any more manage the audio?No. Jack never manages the audio, it just picks what alsa is giving it. It just means that playback for that input is unmuted. Playback is done on driver level (alsa). Playback of input never goes to sound servers (jack, pulseaudio), it goes straight to speakers. Capturing goes to sound servers. So, in a way, you can call it the shortcut, but it does not affect jack or pulseaudio.

For 2b you need to set input source in alsamixer to be the one that you are using. You can also set it in sound preferences if you are using pulseaudio.
For 3b you need to connect capture to ardour track. You should already know that.
> Why there is this difference?Who knows. It is a different version of alsa, pulse...
> I am sure the system is working, because I already tried with the previous version of Ubuntu.That is not the rule.

---

### Post by sgx on 2011-10-06
Hi, Is there no separate line-in on your computer? This would be
stereo, and with an adaptor, receive both L and R outputs from the pod.
If there is only the mic input, check the docs/google to see if it is
a combo mic/line jack, in which case it may have compromised hardware input settings, and possibly a jumper or bios config, to adjust the input level.

With 1//4 inch to 1/8 inch adaptors, it is good to secure the
cable so that there is no pressure on the 1/8 inch jack.
Combo jacks are usually on a laptop (loser sony cheapskates!)
and probably get little attention from linux developers.

This is the Pod Pilot Guide pdf, don't know if that
came with your device.

[http://images.thomann.de/pics/prod/207495_manual_en.pdf](http://images.thomann.de/pics/prod/207495_manual_en.pdf)

-according to 3-5 #17, of the pdf, plugging in headphones switches the pod levels to 'Studio Mode', so misc high-end features might influence the results of your testing.

Cheers

---


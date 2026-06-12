---
title: "Can i record sound playing through realtek alc268 card?"
date: 2009-06-17
forum: Ubuntu Studio
---

### Post by keratos on 2009-06-17
Toshiba A300 satellite pro laptop
Alsa 1.0.18
kernel 2.6.28-3-rt
ubuntu 9.04
Intel HD audio (realtek ALC268 codec using snd-hda-intel module)

Playback is fine but is is possible to record the sound playing through the audio card?

Having googled and seached the forums, I did find it was possible to accomplish this using S/W mixing however, the mixer that is available in my setup only offers the front mic, mic inbuilt into the lid, and headphones as input.

I could link the headphone to the mic using a lead but this is messy and not what I want.

I've tried pulse and jack ... didnt like it, couldnt get it working anyway and dont wont to use this combination that is relatively new so far as its inclusion in linux.

Surely there must be a way?

---

### Post by sedawk on 2009-06-17
You can try to start audacity and see which recording devices
it offers in the preferences dialog ("audio i/o").

---

### Post by keratos on 2009-06-17
Audacity Only provides Alsa or /dev/dsp and as we know, the input and output have to be the same type (i.e. MME, DirectSound etc).

What's more, my soundcard does not offer any mixer input options, only CD, Line or Mic.

---

### Post by keratos on 2009-06-20
BUMP! Please, anyone ??

---

### Post by mirage on 2009-06-20
Not sure if it helps, but i have an alc268 in my acer aspire laptop, too. I had similar problem with it (mic was not working), and the solution was to turn the recording volumes down: digital and capture to ~30%, with mic boost to 100%.
This works only with the external mic, with the internal, i didn't reached any break-through, yet. (And i'm not sure i will...)

---

### Post by jjross on 2009-06-21
You can use arecord to record the output of your sound card.
It is a command line recorder but the learning curve is not to bad, just type man arecord in a terminal and it will give you all the command options and a couple of examples.

Try this in a terminal

arecord -d 10 -f cd  foobar.wav

this will give you 10 seconds of what ever is coming out of your speakers of CD quality in a wav format and it should be in your /home folder.

---

### Post by sgx on 2009-06-21
> **keratos said:**
> BUMP! Please, anyone ??
Hi, I use Cantabile12Lite, and Reaper 2.56 in linux, as they can record vsts output(s) live, or render it, after recording midi tracks. Both are free for non-professional, or testing, and used with wineasio 7.3 and wine 1.01, are quite stable. I use many of the plugins from ComputerMusic magazine dvd, along  with synth1, rez2, oatmeal 37.4/38.x, Adonis Pro, and a few commercial synths. qtractor may work for recording
linux audio live, but I have not read about its options yet, just hoping.
ecasound is a recording app, been around a long time, and there are a couple of jack recording utilities that should work also, check in synaptic.
Cheers :)

---

### Post by keratos on 2009-08-20
Guys - I dont have an output channel (mixer) with which to capture. I really wanted ideas and support with the sound card side drivers et al rather than S/W recommendations. But thanks anyway.

I give up. 

Thanks anyway.

---

### Post by Ralph386 on 2009-10-19
Hey my friend I got the same problem and I solved it!!!!!!. I have a Toshiba satellite A200, Realtek ALC268, UBUNTU 9.04 here is how I did it:

**1. **Install A**LSA driver 1.0.21** following this link (very elegant by the way):

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)


**2. **Edit **alsa-base.conf**

sudo gedit /etc/modprobe.d/alsa-base.conf

at the last line add:

alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 model=toshiba position_fix=1


**3. **Configure **Alsa Mixer** (we are almost there!!)

Open volume control then click on **Preferences**

1.Tick **Capture** and **Input Source**. On the Tab **Options** select **Mic** as **Input Source**. In the Tab **Recording** set ¼ of the full power the **Capture** command
2.Be sure that **Front Mic Boost** and **Mic Boost** are at full power
3.Try a call by Skype or record your voice. Normally if the **Capture** command is too high the sound distortions.
4.ENJOY!!!!!!!!!!!!
[SIZE="5"][B]
UBUNTU ROCKS!!!!!!!!!![/B][/SIZE]:guitar:

---

### Post by Ralph386 on 2009-10-19
Forgot to tell to re-start your computer in steps 1 and 2

ENJOY!!!!!!:guitar:

---

### Post by nickleus on 2009-11-04
i found out what the problem was in karmic:
[http://ubuntuforums.org/showthread.php?p=8238734#post8238734](http://ubuntuforums.org/showthread.php?p=8238734#post8238734)

---


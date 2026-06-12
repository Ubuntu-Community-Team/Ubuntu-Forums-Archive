---
title: "Rezound Playback"
date: 2008-05-01
forum: Ubuntu Studio
---

### Post by haelen on 2008-05-01
Hi,

After despairing at the lack of compatibility between Audacity and Heron, I've decided to give Rezound a try.

It records OK, but the playback is "juddery". The latency in JACK is set to "default". Could the problem be something other than latency?

I see that Rezound has a mailing list, but is there a forum too?

TIA,
Tim

---

### Post by warbread on 2008-05-01
Do you have the real time kernel enabled?  Are you getting any xruns?  Also, what is your sample rate set at in Jack?

---

### Post by haelen on 2008-05-01
> **warbread said:**
> Do you have the real time kernel enabled?  Are you getting any xruns?  Also, what is your sample rate set at in Jack?

Sample rate= 44100

Not sure about the real time kernal or xruns.

TIA (and for your prompt response - I'm back in 2 hrs or so)

Tim

---

### Post by warbread on 2008-05-01
Post the output of the following command: 

```
:-$ uname -r
```

This will tell us what kernel you're using.  Also, check the 'Messages' box on Jackqtl while recording to see if you're getting xruns.  These are buffer over OR under runs, meaning that the buffer is either too full or too empty for the program to do anything with.  This will produce a pop, click or chirp sound in your recording.  If this is a buffer problem, it'll be a simple matter of enabling real time access and rebooting, then clicking another box in the Jack settings window.

---

### Post by haelen on 2008-05-01
Hi,

the kernel is 2.6.24-16-generic

I am getting xruns. Here's a small sample - but I think the highest was around 0.100 msec.

**** alsa_pcm: xrun of at least 0.020 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.033 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.025 msecs
**** alsa_pcm: xrun of at least 0.021 msecs
12:58:54.315 XRUN callback (23 skipped).

Cheers,
Tim

---

### Post by warbread on 2008-05-01
Ah, yeah.  You'll want to download and run the real time kernel (synaptic search), and then put the following into terminal:

(From [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation))
```

:-$ sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
:-$ sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

```

Then reboot the computer.  You'll also need to install the real time kernel restricted modules package (again, synaptic search) if you use the nVidia or ATI graphics card drivers.  Once you have that done, start up qjackctl again, but before hitting that green arrow, go into settings and enable real time mode.  If your DSP can handle it, crank the sampe rate, too.  That will lower latency.  

I believe that should solve your problems.

---

### Post by haelen on 2008-05-01
Hi,

I followed your instructions. This time Rezound froze during recording.

I've posted the results to the Pastebin:

[http://paste.ubuntu.com/9184/](http://paste.ubuntu.com/9184/)

Thanks,
Tim

---

### Post by warbread on 2008-05-01
That's quite a bit of xruns for a low latency set up.  What sound card are you using?

---

### Post by haelen on 2008-05-01
> **warbread said:**
> That's quite a bit of xruns for a low latency set up.  What sound card are you using?

Just onboard sound (Intel HDA?) which I would imagine is not great for low latency work. I got away with using Audacity until Hardy was released - but there are compatibility issues.

Tim

---

### Post by warbread on 2008-05-01
That's true, it's not very good for it at all.  You could try upping the sample rate, which should lower latency, but I don't know anything about rezound's stability.  Your problems in Hardy could be related to Pulseaudio, Jack or Rezound itself.  What I did was buy a $20 Turtlebeach USB soundcard which works very well in Ubuntu.  I can understand why you wouldn't want to buy new hardware just to get one program to work in Hardy, but unfortunately I'm out of ideas at this point.  You could run Rezound from terminal and see what output it gives you when it crashes, but that might not reveal anything useful.

---

### Post by haelen on 2008-05-01
> **warbread said:**
> That's true, it's not very good for it at all.  You could try upping the sample rate, which should lower latency, but I don't know anything about rezound's stability. .

Thanks. I'll try that. Could you tell me the Model number of the USB card you bought?

I appreciate your helping with this problem!

Tim

---

### Post by haelen on 2008-05-01
It was a bit of a long shot, but I had the idea of running the Windows release of Audacity using WINE.

To my amazement, it worked first time!

Best,
Tim

---

### Post by Stochastic on 2008-05-01
Two things with rezound (though I guess audacity under wine is working, I don't really consider that a solution IMHO); first it can run without jack (through alsa, or even oss) - have you tried that? Second, in jack's setup did you turn on the realtime feature (top-left box on the qjackctl settings panel)?  Rezound has always been solid as a rock for me.  From your outputs I'd say your issues are the excessive xruns that are causing the rezound playback issues.  Your inbuilt card should be able to handle a low latency setup, but you need to turn on jack's realtime abilities.

---

### Post by haelen on 2008-05-01
Hi,

Rezound crashes (closes down) as soon as I enter the first window (output channel).

I tried Realtime in Jack and had the same result.

True, using Audacity under WINE is a "hack", but it works,and I needed something urgently for work.

Cheers,
Tim

---

### Post by Stochastic on 2008-05-01
can you run rezound from a terminal and post the output messages after it crashes

---

### Post by warbread on 2008-05-01
Sorry for the wait!  [Here's the soundcard I got for my laptop]("http://www.amazon.com/TURTLE-BEACH-VOYETRA-MICRO-SOUND-AUDIOADVMICRO/dp/B000H5GL4M/ref=sr_1_3?ie=UTF8&s=electronics&qid=1209697998&sr=8-3").  I can't promise that it works in Hardy, but it sure does work in Gutsy.  I've got it to output to Jack, Amarok and Kaffeine.  Haven't tried anything else.

---

### Post by haelen on 2008-05-02
> **Stochastic said:**
> can you run rezound from a terminal and post the output messages after it crashes

Without JACK:

```
haelen@dell:~$ rezound
using path '/usr/share/rezound' for share data directory
Error occurred while initializing audio output method 'oss' -- virtual void COSSSoundPlayer::initialize() -- error opening OSS device '/dev/dsp -- Device or resource busy
Error occurred while initializing audio output method 'jack' -- virtual void CJACKSoundPlayer::initialize() -- error connecting to jack server -- jackd not running?
If rezound dies unexpectedly while seeking with the keyboard, auto-repeat may be disabled.. if this happens run 'rezound --fix-auto-repeat'

```

Running JACK gives xruns (I mean without loading Rezound too)

Tim

---

### Post by haelen on 2008-05-02
Thanks for that, warbread

---

### Post by Stochastic on 2008-05-02
Hmm strange, it looks like it didn't attempt to connect to ALSA first as it should have.  There are two possible reasons for this: 
-ALSA is perma-tied to another application.  Often firefox does this on some systems - particularly flash apps.  Try closing all sound applications running (or even do a reboot if the same error comes up).
-The configure file /home/username/.rezound/registry.dat doesn't have ALSA listed as an option.  Open a text editor and edit "alsa" (with quotes) into the front of the list in the top two settings.

---

### Post by haelen on 2008-05-02
> **Stochastic said:**
> 
-The configure file /home/username/.rezound/registry.dat doesn't have ALSA listed as an option.  Open a text editor and edit "alsa" (with quotes) into the front of the list in the top two settings.

This is what I have there already:

[I]
AudioInputMethods={"oss","alsa","jack","portaudio"};
AudioOutputMethods={"oss","alsa","jack","portaudio"};[/I]

Closed down all apps apart from Rezound and it still crashes.

Tim

---

### Post by Stochastic on 2008-05-02
what do you mean "apart from rezound" is it already running?  I thought it crashed?  since you have crashed apps, let's do a reboot, then go straight to rezound, then try to record, then post any and all results.

---

### Post by haelen on 2008-05-02
Ok. I fired up Rezound straight after booting. It wouldn't load. I killed PulseAudio, and started Rezound.

It crashed as soon as I started to  allocate file name and number of channels.

---


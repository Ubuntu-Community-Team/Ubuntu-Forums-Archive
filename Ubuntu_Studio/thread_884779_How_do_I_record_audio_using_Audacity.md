---
title: "How do I record audio using Audacity?"
date: 2008-08-09
forum: Ubuntu Studio
---

### Post by wersdaluv on 2008-08-09
Audacity is a great app but I use it only for mixing primarily because I can't record with it. I can't record with it with my Mic or a guitar plugged in the mic port. 

I always get the error message ```
Error while opening sound device. Please check the input device settings and the project sample rate.
```. 

Can I really record with Audacity? If so, what do I do?

Thanks in advance :)

---

### Post by onus on 2008-08-09
ive got the same problem.... :(

---

### Post by Spainface on 2008-08-09
I experience the same problem using a USB mic.

When I run the program in terminal, I receive this:  

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback

**** alsa_pcm: xrun of at least 0.041 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.031 msecs

That continues without end.  


when I try to record the terminal response is:

Expression 'parameters->channelCount <= maxChans' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924
Expression 'ValidateParameters( inputParameters, hostApi, StreamDirection_In )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1961

Any thoughts?

Thanks!

---

### Post by eye208 on 2008-08-10
> **Spainface said:**
> when I try to record the terminal response is:

Expression 'parameters->channelCount <= maxChans' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924
Expression 'ValidateParameters( inputParameters, hostApi, StreamDirection_In )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1961
This is a PulseAudio issue (as you can tell by the "pa_" prefix). According to the PulseAudio documentation (see [here](http://www.pulseaudio.org/wiki/PerfectSetup#Audacity)) Audacity does not yet work with PulseAudio. You have to either suspend, kill, or [remove](http://ubuntuforums.org/showpost.php?p=5354773&postcount=6) PulseAudio to make Audacity work.

---

### Post by wersdaluv on 2008-08-10
> **eye208 said:**
> This is a PulseAudio issue (as you can tell by the "pa_" prefix). According to the PulseAudio documentation (see [here](http://www.pulseaudio.org/wiki/PerfectSetup#Audacity)) Audacity does not yet work with PulseAudio. You have to either suspend, kill, or [remove](http://ubuntuforums.org/showpost.php?p=5354773&postcount=6) PulseAudio to make Audacity work.
So what exactly do I do? I killed pulseaudio but I still can't record.

---

### Post by luctor on 2008-08-10
on my pc however it just works ?!?
first check in audacity Edit -> Preferences -> Audio In/Out

Taken from [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

> Audacity doesn't support PulseAudio, nor Esound for the moment. You'll have to kill or suspend pulseaudio before you use this application. Audacity uses the PortAudio cross-platform Audio API which doesnt support pulseaudio. Some work was started on making portaudio support PulseAudio but this does not appear to be under active development currently and does not work in it's current state.

Using pasuspender to momentarily suspend pulseaudio is the most convenient way to use the non-beta versions (1.2.x) of Audacity at present.

pasuspender -- audacity <argument>

You could also run the windows version through wine, to have proper pulseaudio support 

---

### Post by eye208 on 2008-08-10
> **wersdaluv said:**
> So what exactly do I do? I killed pulseaudio but I still can't record.
In Audacity (Edit > Preferences > Audio I/O) select "ALSA: default" for both recording and playback. If Audacity records silence, check your mixer settings. Make all the "capture" sliders visible and set them to maximum gain. Select the desired input source (mic, line-in etc.) for recording.

---

### Post by markbuntu on 2008-08-10
I just use ardour instead.

---

### Post by sharadaprasad on 2008-08-15
Even I am facing the same problem - Unable to record. Initially the device settings were set to OSS. Then, if I click on record button, Audacity wud audaciously hang.

I changed it to ALSA: Default. Now Audacity does not hang but it does not record sound either.

OS: 8.0.4
Audacity Version - 1.3.4 Beta. Installed thru Synaptic Manager.

---

### Post by eye208 on 2008-08-15
> **sharadaprasad said:**
> I changed it to ALSA: Default. Now Audacity does not hang but it does not record sound either.
Have you removed PulseAudio (as shown [here](http://ubuntuforums.org/showthread.php?t=885437))?

---

### Post by markbuntu on 2008-08-15
There is really no need to remove pulseaudio to use audacity. eye208 seems to be obsessed with the idea. All you need to do is edit the audacity launcher.

System/Preferences/Main Menu. Find Audacity in the Menus and double click on it. In the Launcher Properties window that pops up change the Command: from audacity to

pasuspender audacity

close all the windows and start up audacity. If you have changed all the defaults in System/Preferences/Sound to alsa, you should be able to record. If you still cannot record, then your alsa configuration is wrong. You can try changing the System/Preferences/Sound/Audio Conferencing/Sound Capture setting to your sound card if the ALSA setting does not work.

---

### Post by jocheem67 on 2008-08-16
My very elegant solution ( as I may say so :) ) is to use jack.

I installed jackd and qjacktl, made alsa my default backend ( not pulse --- hate that stuff ) and I've got no problem now in playback and recording.
Used the repo audacity.

---

### Post by markbuntu on 2008-08-16
Well yes, but that is a daunting proposition for many so I did not mention it. Since you are now using jack, you can get your other applications to play through it by following my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The jack section is near the bottom.

---

### Post by eye208 on 2008-08-16
> **markbuntu said:**
> There is really no need to remove pulseaudio to use audacity. eye208 seems to be obsessed with the idea.
It's quite ironic to be called obsessed by someone who spent five weeks compiling a 12-pages guide only to avoid removing PulseAudio.

---

### Post by fredfelter on 2008-08-17
I think I've done all the suggested modifications to try to make Audacity record from Pandora. What I'm getting is an overwhelming amount of static and the recording graphic and meters are off the chart so I can't tell if there is music in the background even tho the volume controls are in normal positions. I'm thinking now it has to do with the Vol Control settings; could someone tell me exactly what to check in Preferences. And what are ADC and CDC for?
Thanks in advance.
   By the way I can record from my mic, with Audacity. or at least I was able to before I made all these changes. Thinkpad T22 with Ubuntu 8.04.

---

### Post by audioAl on 2008-08-17
I too have downloaded Audacity, I wish to go Line in to my HT, how do I do that? I am new to Ubuntu, Hardy Heron 8.04:guitar:

---

### Post by markbuntu on 2008-08-17
> **eye208 said:**
> It's quite ironic to be called obsessed by someone who spent five weeks compiling a 12-pages guide only to avoid removing PulseAudio.

That was not my goal at all when I started out. My only goal was to find some way to add a nice deep echo/delay to the internet radio streams I was playing from streamtuner through xmms. You can call that obsessive if you want but for me it was more of a spare time casual troubleshooting exercise.

At more than one point in my exercise I did remove pulseaudio and revert to a purely ALSA setup but that proved itself to be a counterproductive dead end as the alsa application to jack connections proved to be less than reliable for me and left more problems than it solved.

This led me to the conclusion that I needed to get a better handle on the architecture of sound management in Ubuntu and the pulseaudio-alsa-jack interaction scheme since it seemed to be such an inadequate incoherently documented mess. So I did.

I am not some sort of pulseaudio zealot but pulse does solve a number of particular issues that alsa/oss does not while leaving a number of issues that concern me still unsolved by any of the sound servers, OSS, ALSA, or PulseAudio.

---

### Post by fredfelter on 2008-08-17
This is to "markbuntu". 

I am methodically going through your "Multiple Sound Solution" of 27/June to try to get Audacity working. I note that in your list of Alsa packages search you have a "lid=basound2 (aksa libs and plugins) listed but I can't find it in Synaptic Package Manager. Any ideas?

Thanks.

---

### Post by markbuntu on 2008-08-17
> **fredfelter said:**
> This is to "markbuntu". 

I am methodically going through your "Multiple Sound Solution" of 27/June to try to get Audacity working. I note that in your list of Alsa packages search you have a "lid=basound2 (aksa libs and plugins) listed but I can't find it in Synaptic Package Manager. Any ideas?

Thanks.

OOPs, that is a typo, thanks for pointing it out, I have corrected it,It should be 

libasound2 

and it is probably installed already by default.

Anyway, you do not have to go through my entire guide just to get audacity to work. You can just use pasuspender as I explained a few posts ago. 

Personally, I have had nothing but headaches with audacity and switched to ardour which is a real professional recording suite that integrates seamlessly with jack and can be used to control the clock/timing of playback/recording of linked midi programs like rosegarden and hydrogen, so adjusting the drum track can be done in hydrogen and tried out again immediately by just hitting the play button in ardour, etc. I am not sure if audacity can do stuff like that, I have never got it to run properly.

If you are doing serious recording you should be using whatever you use through jack with the real time kernel, the jack section near the bottom of my guide should help you get started with that.

---

### Post by fredfelter on 2008-08-18
Thanks for the reply markbuntu.

Re: your excellent guide I encountered a couple of problems. Hopefully you can help me with them:

1) In Sound Preferences the only sound captures that work are OSS, but it yields no sound, and Test Sound but I doubt that is one to run with.

2) Re: Pulse Audio Manager. Apps > Sound and Video > Pulse Audio Device Chooser > taskbar icon > Manager > "connection refused or failed" so I see no server information.

---

### Post by jocheem67 on 2008-08-18
@ Markbuntu: I love jack, however I've seen your guide and see no need to integrate pulse and jack, or consider the other modifications.
Rosegarden, mixxx, and ardour already work well with jack and alsa, using the rt-kernel offcourse.

Great tutorial by the way...

I'll shut up now, since this quite off-topic.

---

### Post by Cresho on 2008-08-18
well, I tried audacity and it does not work for me as well...but ardour does.

---

### Post by Cresho on 2008-08-18
Like everybody who was having problems.  I decided to install my own audacity and ended up finding a new version available at getdeb.net


This one works fine.  I can record from my mic and line in no problems.  The one in ubuntu repo's sucks major butt!


this is how i did it.  I uninstalled the old one and installed this one.

[http://www.getdeb.net/release/2782](http://www.getdeb.net/release/2782)

---

### Post by wersdaluv on 2008-08-18
> **Cresho said:**
> Like everybody who was having problems.  I decided to install my own audacity and ended up finding a new version available at getdeb.net


This one works fine.  I can record from my mic and line in no problems.  The one in ubuntu repo's sucks major butt!


this is how i did it.  I uninstalled the old one and installed this one.

[http://www.getdeb.net/release/2782](http://www.getdeb.net/release/2782)
I'll try that when I get home.

I wonder why I can record with the Eee PC 701 with the same Hardy and Audacity versions installed.

---

### Post by eye208 on 2008-08-19
> **Cresho said:**
> The one in ubuntu repo's sucks major butt!
BS. It works fine. PulseAudio sucks butt.

---


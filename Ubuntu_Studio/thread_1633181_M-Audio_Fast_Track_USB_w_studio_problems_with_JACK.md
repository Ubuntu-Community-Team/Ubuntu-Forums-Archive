---
title: "M-Audio Fast Track USB w/ studio: problems with JACK"
date: 2010-11-28
forum: Ubuntu Studio
---

### Post by McMillan73 on 2010-11-28
I'm running M-Audio Fast Track USB (guitar|mic recording interface) so I can plug in my guitar and record along with hydrogen drumtracks in ardour, maybe add some vocals or keyboard/synth later. So far the plan.

Without Jack I get sound (a bit distorted) both from video/music files and from hydrogen on the output of the Fast Track. Same with the onboard soundcard when I unplug the Fast Track. 

Using the Fast Track as soon as I try to run hydrogen through Jack I don't hear anything. Linking Hydrogen with ardour I see the main levels move with the Hydrogen drum track but... no output sound.

Here are the JACK settings:
Realtime, 128 Frames/Period, Sample rate 44100, 3 Periods/buffer, Interface default, Input device hw:0, Output device hw:0 which gives me a theoretical latency of 8.71msec. I'll optimize for better latency as soon as I can hear something :(

One more thing I noticed: on the Connection chart I don't see alsa input/output as described in most posts or manuals but "system capture_1 and capture_2" and "system playback_1 and playback_2".

Here's where my cards are at:
$ cat /proc/asound/cards
 0 [Track          ]: USB-Audio - Fast Track
                      M-Audio Fast Track at usb-0000:00:1a.1-1, full speed
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfeaf4000 irq 22


Here's some data on my system:
Ubuntu Studio 10.04 64bit, Kernel 2.6.32-25-generic, gnome 2.30.2
3 GB RAM, 2 Dual Core Pentiums @2.8GHz
 
To be honest, I don't quite understand how to find out where to control the system output/input parameters, I've been fumbling around with the pulse audio controls and with the sound preferences offered in the system/preferences menu of ubuntu studio but I'm not sure which one does what and if they're in paralell with JACK or between both of them or if by using JACK pulse audio becomes meaningless because it's not used.

Could someone try and help me with that rabbit hole? I've been trying for more than five days now and no results...

Thanks a lot in advance!!

---

### Post by cchhrriiss121212 on 2010-11-29
Hi
To answer your questions:
The connection window in qjackctl handles your connections
Your system capture/playback is your fast track ins/outs
Pulse is suspended when jack is started

In order to get to grips with jack you can simplify your audio chain, so for the tine being forget about recording with Ardour, and just try using one jack program. Rakarrack for example.

(The distortion could mean that your levels are set too high, so open alsamixer from a terminal and try lowering your capture levels.)

Try physically connecting your guitar to the fast track, then start jack + rakarrack and open the connection window. Connect your capture port to rakarrack and then connect that to playback. Experiment to find which capture ports relate to your hardware.

---

### Post by transmogrifox on 2010-11-30
alsamixer

That is what you can use to control input/output levels on your sound card.  

Open a terminal and type "alsamixer", then adjust playback levels and capture level and capture ports.

You can set a specific device as a capture device by arrow keys to the channel you want to capture and space bar.

Use 2 periods per buffer unless jack absolutely won't run.  Anything more than 2 periods per buffer is a work-around to either bad hardware or a bad driver.  I'm not sure about the M-Audio card alsa support, but try to avoid using 3 periods if you can make it work with 2.

Causes of audio distortion when using jack are more often related to dropped frames than having to do with input/output levels.  Of course, you should check these levels, but usually your program needs to be running really hot to cause distortion by clipping.

Also, don't rule out your amplifier and speaker system.  Does it work without distortion for playback of regular music from an audio player (not using jack) using the same hardware connections?

---

### Post by McMillan73 on 2010-12-01
Thanks transmogrifox and Chris,

the combination of all tips did the trick! 1st of all alsamixer input was all the way up and the output was all over the place (I had been trying to use Alsa-mixer gui... won't anymore!) and then to connect the specific ports in the JACK patchbay did the rest. After playing around with rakarrack then adding Hydrogen to jam along I connected everything in Ardour and recording worked!

Also changed to 2 periods/buffer and lowered the frames to 64 which gives me quite a good sound result!

Thanks a lot in advance! Now to some recording and then to MIDI integration of the keyboard... there's challenges everywhere!

---


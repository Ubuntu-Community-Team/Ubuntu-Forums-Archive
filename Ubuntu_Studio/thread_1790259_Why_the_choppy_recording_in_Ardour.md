---
title: "Why the choppy recording in Ardour?"
date: 2011-06-24
forum: Ubuntu Studio
---

### Post by treehouse on 2011-06-24
I'm new to recording on a computer.

I have a guitar plugged into the line-in jack. Using Jack and Ardour to record gave me a track that was super choppy. I attempted to export this choppy track as a wav and the resulting file would open but not play. Attempting to record in Audacity works perfectly.

Searching around, most solutions involve the now unsupported low latency or realtime kernels, but as my hardware is pretty up-to-date I can't see that being the issue.

My relevant specs:
CPU: AMD Phenom II X6 1090T 3.2GHz
RAM: 4GB SDRAM DDR3 1600 (PC3 12800)
Sound Card: Onboard Realtek ALC892

What are the potential causes for the choppy audio?

Thanks for reading.

---

### Post by akavir on 2011-06-24
Are you using JACK when recording in Audacity?  If not, my first guess would be to reduce the buffer size.  Open Qjackctl>Setup>Frames/Period.  If it's set to 1024 by default, try reducing to 512, and start JACK again.  See if this makes a difference.  Using a built in soundcard, it should.

---

### Post by treehouse on 2011-06-25
I'm not using Jack with Audacity. If Jack is running when Audacity is, then it won't let me record. Lowering the frames/period didn't help, I went down to 64 before it made Ardour lock up.

---

### Post by luctor on 2011-06-26
are you using qjackctl ?

---

### Post by treehouse on 2011-06-26
yes, qjackctl

---

### Post by Pablo_F on 2011-06-27
Please, paste here the contents of the Messages window, once qjackctl's display says that jackd is started.

---

### Post by treehouse on 2011-06-27
```

0:04:45.393 JACK is starting...
20:04:45.394 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p512 -n2
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
20:04:45.447 JACK was started with PID=4084.
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|512|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe6f4000 irq 16
configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
**** alsa_pcm: xrun of at least 0.049 msecs
**** alsa_pcm: xrun of at least 0.051 msecs
**** alsa_pcm: xrun of at least 0.045 msecs
**** alsa_pcm: xrun of at least 0.046 msecs
**** alsa_pcm: xrun of at least 0.047 msecs
**** alsa_pcm: xrun of at least 0.046 msecs
**** alsa_pcm: xrun of at least 0.049 msecs
**** alsa_pcm: xrun of at least 0.046 msecs
**** alsa_pcm: xrun of at least 0.046 msecs
**** alsa_pcm: xrun of at least 0.046 msecs
**** alsa_pcm: xrun of at least 0.049 msecs
**** alsa_pcm: xrun of at least 0.048 msecs
**** alsa_pcm: xrun of at least 0.047 msecs
**** alsa_pcm: xrun of at least 0.051 msecs
**** alsa_pcm: xrun of at least 0.050 msecs
**** alsa_pcm: xrun of at least 0.050 msecs

```

---

### Post by laquri on 2011-07-27
BUMP

I've got exactly the same problem,almost  same specs exactly same soundcard. I can start qjackctl get this message:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:13:51.177 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:13:51.200 Statistics reset.[/COLOR]
 [COLOR=#cccc99]13:13:51.608 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:13:51.616 JACK is starting...[/COLOR]
 [COLOR=#990099]13:13:51.617 /usr/bin/jackd -m -dalsa -dhw:0 -r44100 -p128 -n3[/COLOR]
 Cannot connect to server socket err = Bestand of map bestaat niet
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = Bestand of map bestaat niet
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]13:13:51.630 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]13:13:51.717 JACK was started with PID=3162.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfbef4000 irq 16
 configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
 [COLOR=#9999cc]13:13:53.858 JACK connection change.[/COLOR]
 [COLOR=#999933]13:13:53.859 Server configuration saved to "/home/ellonisi/.jackdrc".[/COLOR]
 [COLOR=#999999]13:13:53.859 Statistics reset.[/COLOR]
 [COLOR=#999999]13:13:53.865 Client activated.[/COLOR]
 [COLOR=#cc9966]13:13:53.867 JACK connection graph change.[/COLOR]



It looks ok but when I start a application for example zynaddsubfx I've got things like:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999999]JackEngine::XRun: client = ZynAddSubFX was not run: state = 2[/COLOR]
 [COLOR=#999999]JackAudioDriver::ProcessGraphAsync: Process error[/COLOR]
 [COLOR=#999999]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999999]JackEngine::XRun: client = ZynAddSubFX was not run: state = 2[/COLOR]
 [COLOR=#999999]JackAudioDriver::ProcessGraphAsync: Process error[/COLOR]
 [COLOR=#999999]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999999]JackEngine::XRun: client = ZynAddSubFX was not run: state = 2[/COLOR]
 [COLOR=#999999]JackAudioDriver::ProcessGraphAsync: Process error[/COLOR]
 [COLOR=#999999]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999999]JackEngine::XRun: client = ZynAddSubFX was not run: state = 2[/COLOR]
 [COLOR=#999999]JackAudioDriver::ProcessGraphAsync: Process error[/COLOR]
 [COLOR=#999999]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999999]JackEngine::XRun: client = ZynAddSubFX was not run: state = 2[/COLOR]
 [COLOR=#999999]JackPosixMutex::Unlock res = 1[/COLOR]


Same when starting lmms etc.


I tried all kind off options but I am out now, is it the soundcard or what, dunno, anyone?

---

### Post by laquri on 2011-07-27
It is a bit better now, I installed jaaa wich gave:

jaaa -A
playback :
  nchan  : 6
  rate   : 48000
  frsize : 1024
  nfrags : 2
  format : S32_LE
capture  :
  nchan  : 2
  rate   : 48000
  frsize : 1024
  nfrags : 2
  format : S32_LE
synced
Connected to ALSA with 2 inputs and 6 outputs

When using this in qjackctl (rt, hw0, sample rate=48000 and Frames/Period=1024) and also with Periods/Buffer=3 it is less choppy, wheater lower Frames/Period=512 (latency=32ms) doesn't seem possible, guess have to look for another card then?

---

### Post by Pablo_F on 2011-07-27
Hi, 

lmms and zynaddsubfx are not the best jack clients. In any case, increase the frames/period value. You don't want xruns but you don't always need very low latency, which leads to the question:

Do you really need low latency? Are you playing live and monitoring through software? 

More suggestions, 

Put 2 periods/buffer. Also, sometimes sync mode works better in jackd2, so try "/usr/bin/jackd --sync" in the "server path" field.


Cheers, Pablo

---

### Post by laquri on 2011-08-07
> **Pablo_F said:**
> Hi, 

lmms and zynaddsubfx are not the best jack clients. In any case, increase the frames/period value. You don't want xruns but you don't always need very low latency, which leads to the question:

Do you really need low latency? Are you playing live and monitoring through software? 

More suggestions, 

Put 2 periods/buffer. Also, sometimes sync mode works better in jackd2, so try "/usr/bin/jackd --sync" in the "server path" field.


Cheers, Pablo
Sorry for late reply, the jack2d suggest helps very well for latency.
I was just replying on the choppy recording which that user had. I have the same. I am just wondering why it is so hard to configure this sound card, I used a 10 years old soundblaster Live! before wich was easy to use with nice sound on all applications, but with this grand new Realtek ALC892 it just is hard ( things should be improve in 10 years I think?). For example for Skype I have to use pulse and it gives an anoying echo and is in fact unusable for skype. I don't know but it is just crazyness to configure this card properly. It is just strange as soon something works in one application it doesn't work properly in another application anymore. I don't need to play live but it should work properly for the applications I use.

---

### Post by laquri on 2011-08-07
> **laquri said:**
> Sorry for late reply, the jack2d suggest helps very well for latency.
I was just replying on the choppy recording which that user had. I have the same. I am just wondering why it is so hard to configure this sound card, I used a 10 years old soundblaster Live! before wich was easy to use with nice sound on all applications, but with this grand new Realtek ALC892 it just is hard ( things should be improve in 10 years I think?). For example for Skype I have to use pulse and it gives an anoying echo and is in fact unusable for skype. I don't know but it is just crazyness to configure this card properly. It is just strange as soon something works in one application it doesn't work properly in another application anymore. I don't need to play live but it should work properly for the applications I use.

Ok, Skype works ok now, by removing pulseaudio, dunno but with pulseaudio it was impossible to get use skype. So far now it doesn't seem to influence other applications from working. Still recording with the microphone is very noisy in comparing to old soundblaster but it is ok for now.

---


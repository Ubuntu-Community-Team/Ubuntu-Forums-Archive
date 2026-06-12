---
title: "pulse switch to try establisch connection but have faillure"
date: 2012-04-27
forum: Ubuntu Studio
---

### Post by JvdS45 on 2012-04-27
I am using pulse and jack and need pulse for having skype in idjc internnetbroadcasting. It was always working, bus since the 12.04 ubuntustudio the pulse try to establisht the sound, but can't.

I can choose for audio jack-sink and jack-source searching to try do this, but where?

I did everything which i know to help but the sink and source are not working with jack
so meaning only jack is working and cant establish connection with pulse. so every pulse application will not working (hearing the sound and using the mic by pulse)

a flickering pulseserver only tells that it cannot establish the soundserver

what is going wrong?

this is what jack tells see below

08:31:58.386 JACK verbindingen tekening aangepast.
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not run: state = 1[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 1[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Sat Apr 28 08:31:57 2012: Disconnecting 'PulseAudio JACK Sink:front-left' from 'system:playback_1'
Sat Apr 28 08:31:57 2012: Disconnecting 'PulseAudio JACK Sink:front-left' from 'PulseAudio JACK Source:front-left'
Sat Apr 28 08:31:57 2012: Disconnecting 'PulseAudio JACK Sink:front-right' from 'system:playback_2'
Sat Apr 28 08:31:57 2012: Disconnecting 'PulseAudio JACK Sink:front-right' from 'PulseAudio JACK Source:front-right'

Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 1[0m
Sat Apr 28 08:31:57 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m


when i did use this in terminal pacmd load-module module-jack-source channels=2; pacmd load-module module-jack-sink channels=2;

Jack xruns out off hell

Hope someone can help me to find these problem?

---

### Post by shimoda on 2012-04-29
I also have problems with jack in pulseaudio... 
In 10.04 worked very well the pulse-jack bridge of **falkTX**...

I don't know exactly how works jack in pulseaudio by default in 12.04...

**Precipitous** had a similar problem here:
[http://ubuntuforums.org/showthread.php?t=1963309](http://ubuntuforums.org/showthread.php?t=1963309)

Had you tried to start jack with simply "jackd" command?
If I found something else I'll post here...

---


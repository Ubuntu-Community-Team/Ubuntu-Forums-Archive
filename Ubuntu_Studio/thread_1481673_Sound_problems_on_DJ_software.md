---
title: "Sound problems on DJ software"
date: 2010-05-12
forum: Ubuntu Studio
---

### Post by TheLarch on 2010-05-12
Hi.  Like many here, I'm sure, I upgraded to the latest release (10.04). On the surface, it was a nice improvement. Some apps that didn't work as expected or not at all, like kaffeine, rhythmbox and soundird, are now working properly. On the other hand, I'm  having a new problem. DJ software like mixxx, xwax or Ultramixer cannot access the sound devices. Loading UltraMixer, freezes the PC. On mixxx, I get the following errors:    Bus::open: Can not get ibus-daemon's address  Debug: [Main]: Opened PortAudio stream successfully... starting  Debug: [Main]: Dynamically loaded PortAudio library!  Debug: [Main]: PortAudio: Started stream successfully  Debug: [Main]: SoundDevicePortAudio::open() &quot;3, SB Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)&quot;  Debug: [Main]: m_dSampleRate 44100  Debug: [Main]: iLatencyMSec: 64  Debug: [Main]: output channels: 2 | input channels: 0  Debug: [Main]: iFramesPerBuffer 4096  Debug: [Main]: iLatencyMSec: 64  Debug: [Main]: Opening stream with id 3  Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1294 Expression 'PaAlsaStreamComponent_InitialConfigure( &self->playback, outParams, self->primeBuffers, hwParamsPlayback, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1873 Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1994 Debug: [Main]: Error opening stream: Invalid sample rate  Debug: [Main]: FIXME: repaintEverything switches table model and shouldn't do that when viewing the playlist model in  src/wtracktableview.cpp:  227     As for xwax, &quot;You need to give at least one audio device to use as a deck; try -h.&quot;  Can anyone shed some light on the matter?   For everything else, sound seems to be working properly.  Thanks!

---

### Post by psidrum on 2010-05-21
> **TheLarch said:**
> Hi.  Like many here, I'm sure, I upgraded to the latest release (10.04). On the surface, it was a nice improvement. Some apps that didn't work as expected or not at all, like kaffeine, rhythmbox and soundird, are now working properly. On the other hand, I'm  having a new problem. DJ software like mixxx, xwax or Ultramixer cannot access the sound devices. Loading UltraMixer, freezes the PC. On mixxx, I get the following errors:    Bus::open: Can not get ibus-daemon's address  Debug: [Main]: Opened PortAudio stream successfully... starting  Debug: [Main]: Dynamically loaded PortAudio library!  Debug: [Main]: PortAudio: Started stream successfully  Debug: [Main]: SoundDevicePortAudio::open() &quot;3, SB Audigy 2 ZS [SB0350]: Multichannel Playback (hw:0,3)&quot;  Debug: [Main]: m_dSampleRate 44100  Debug: [Main]: iLatencyMSec: 64  Debug: [Main]: output channels: 2 | input channels: 0  Debug: [Main]: iFramesPerBuffer 4096  Debug: [Main]: iLatencyMSec: 64  Debug: [Main]: Opening stream with id 3  Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1294 Expression 'PaAlsaStreamComponent_InitialConfigure( &self->playback, outParams, self->primeBuffers, hwParamsPlayback, &realSr )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1873 Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1994 Debug: [Main]: Error opening stream: Invalid sample rate  Debug: [Main]: FIXME: repaintEverything switches table model and shouldn't do that when viewing the playlist model in  src/wtracktableview.cpp:  227     As for xwax, &quot;You need to give at least one audio device to use as a deck; try -h.&quot;  Can anyone shed some light on the matter?   For everything else, sound seems to be working properly.  Thanks!

i recommend going with Deckadance with Wineasio,
for Dj

works great, and you can use a midi controller with it

i tried UltraMixer and never did get it to run, but Deckadance worked great


you can also try uninstalling them, then reinstall them again, works for me when i do that

---

### Post by OneMixDJ on 2010-06-09
With all due respect, I don't see how paying $100-180 to go with another application over a free open source serves as a solution. 

Instead of doing that, downgrade back to the previous distro that had everything working and keep your wallet in your pocket. You can also check the Mixxx forums for possible solutions, which is also free. ;)

---

### Post by jangal on 2010-06-10
TheLarch - check this thread [http://www.mixxx.org/forums/viewtopic.php?f=3&t=1388](http://www.mixxx.org/forums/viewtopic.php?f=3&t=1388)
 
i've haven't been able to get mixx working with 10.04, the folks on the above thread recommend purging PulseAudio and using ALSA only, I chose not to because I don't fully understand the impacts of purging. So in the meanwhile I using it on my macbook pro.
 
I agree OneMixDJ - its definitely not worth buying a digital-vinyl software after having used trakktor, serato, and mixx - mixx if you can get it going does work well and the dev team has new bells and whistles coming with the next release.

---


---
title: "PulseAudio 2.0 call for testing"
date: 2012-05-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-05-15
I found this in my inbox a little while ago:

> Hey folks,
PulseAudio 2.0 was recently released, and the audio team would like to get this into quantal at some point, but before we do, some testing is required to make sure things don't massively break. We don't believe they will, but its better to be sure.

PulseAudio 2.0 packages are available in the Ubuntu Audio dev PPA, [https://launchpad.net/~ubuntu-audio-dev/+archive](https://launchpad.net/~ubuntu-audio-dev/+archive) for quantal and precise. Precise packages are also available to help get increased testing coverage, as I am sure many of you are not yet running quantal.

If you find any regressions with PulseAudio 2.0, please file a bug against pulseaudio in launchpad, and clearly state in the bug subject that you are testing PulseAudio 2.0. Please also state whether you are running quantal or precise, just in case the bug is reproduceable on one, but not the other.

All being well, PulseAudio 2.0 will be uploaded to Quantal at the end of May, in time for alpha 1.

Thanks in advance.

Luke

---

### Post by ronacc on 2012-05-16
you posted that after I had shut down for the night , added the PPA this AM and installed pulse 2.0  , now to tickle the beast and see if it roars .

---

### Post by Miykel on 2012-05-16
G'Day  Cariboo  Just installed Pulse Audio and played some music with VLC and it worked fine, set the equaliser all over the place and evrything checked out exactly.
  Regards Miykel

---

### Post by pedro.nariyoshi on 2012-05-16
So far so good over here (;

---

### Post by jfernyhough on 2012-05-16
Headline changes from [http://arunraghavan.net/2012/05/pulseaudio-2-0-twice-the-goodness/](http://arunraghavan.net/2012/05/pulseaudio-2-0-twice-the-goodness/) :


[LIST]
[*]Dynamic sample rate switching by Pierre-Louis Bossart: This makes PulseAudio even more power efficient.
[*]Jack detection by David Henningsson: Separate volumes for your laptop speakers and headphones, and more stuff coming soon.
[*]Major echo canceller improvements by me: Based on the WebRTC.org  audio processing library, we now do better echo cancellation, remove  the need to fiddle with the mic volume knob and have fixed AEC between laptop speakers and a USB webcam mic.
[*]A virtual surround module by Niels Ole Salscheider: Try it out for some virtual surround sound shininess!
[*]Support for Xen guests by Giorgos Boutsiouki: Should make audio virtualisation in guests more efficient.
[/LIST]

Announcement: [http://lists.freedesktop.org/archives/pulseaudio-discuss/2012-May/013538.html](http://lists.freedesktop.org/archives/pulseaudio-discuss/2012-May/013538.html)

Release notes: [http://www.freedesktop.org/wiki/Software/PulseAudio/Notes/2.0](http://www.freedesktop.org/wiki/Software/PulseAudio/Notes/2.0)

---

### Post by jfernyhough on 2012-05-17
Well, everything seems to be working fine.

It may just be me but music sounds better. I'm not sure if audio quality could have improved as a byproduct of the dynamic sample rate switching?

---

### Post by bmbaker on 2012-05-18
the sound seems to be better no crashes no distortion :-)

---

### Post by zika on 2012-05-18
Is DynamicSampleRateSwitching switchable?

---

### Post by t1497f35 on 2012-05-18
> **zika said:**
> Is DynamicSampleRateSwitching switchable?
lol it would be funny if it wasn't ..

---

### Post by zika on 2012-05-18
> **t1497f35 said:**
> lol it would be funny if it wasn't ..OK. How? Or should I rtfm... ;)
Update&#8321;: I did not find it...
Question&#8322;: How do I turn "passthrough mode" on? I suppose that "passthrough" mode is for having unaltered stream through PA... Am I wrong?

---

### Post by fjgaude on 2012-05-18
On Precise 12.04, after installing pulseaudio from the PPA music sounds good. Can't say if it is any better than before.

---

### Post by vsteel on 2012-05-28
They way you are supposed to turn passthrough on is :  

[COLOR=Red][http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Passthrough](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Passthrough)[/COLOR]

My testing though I can't get it to work, it seems to resample no matter what I do.  

I also can't find the dynamic switching.  It seems to lock into a sample rate and then I can't get out of it unless I shutdown a program and restart it.  

I am sending my signals from my computer to my stereo through a s/pdif cable.  I have an Asus xonar essence stx card going to a rotel 1069 receiver.  It displays the frequency of the signal I send to it.  If I use the deadbeef player and directly send it to my alsa driver each song will switch to the proper frequency and I am getting bit perfect music.  

When I try and use the pass through it tries to sample everything to 96Khz and it has a hard time sampling things to 88.2Khz (for CD's and such and some music I have at 88.2Khz.)  

Another curious thing is when I am listening to a song it looks like it is trying to force the song to a mono song.  

The following log is from trying to play a 44.1Khz stereo song.  It says though it is making an output of 96Khz and using the resampler peaks.  Which isn't what I have selected. The card is actually outputting 88.2Khz in this case.  It also says it is coming out with mono mapping which I can hear that it isn't mono.   So I am either not understanding the logs or they are giving wrong information.   (logging is set to information.)   

```

May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] resampler.c: Using resampler 'src-sinc-best-quality'
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] resampler.c: Using float32le as working format.
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c: Created input 52 "Playback Stream" on alsa_output.pci-0000_03_04.0.iec958-stereo with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     media.name = "Playback Stream"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.name = "Amarok"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     native-protocol.version = "26"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     media.role = "music"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     phonon.streamid = "{543f888f-65cb-47bc-9293-30cf4e8695b7}"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.process.id = "13554"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.process.user = "vsteel"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.process.host = "chainsaw"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.process.binary = "amarok"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.language = "en_US.UTF-8"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     window.x11.display = ":0"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.process.machine_id = "c19043c01f49e528e76ce2a600000003"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.process.session_id = "c19043c01f49e528e76ce2a600000003-1338240205.367573-1881502279"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     application.icon_name = "amarok"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-media-role:music"
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] protocol-native.c: Requested tlength=200.00 ms, minreq=10.00 ms
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] protocol-native.c: Final latency 200.00 ms = 90.00 ms + 2*10.00 ms + 90.00 ms
May 28 17:02:11 chainsaw pulseaudio[13095]: [pulseaudio] sink.c: Cannot update rate, monitor source is RUNNING
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c: Trying to change sample rate
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c: Resampling enabled to 96000 Hz
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] remap.c: Using generic matrix remapping
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] resampler.c: Using resampler 'peaks'
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] resampler.c: Using float32le as working format.
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c: Created output 22 "Peak detect" on alsa_output.pci-0000_03_04.0.iec958-stereo.monitor with sample spec float32le 1ch 25Hz and channel map mono
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     media.name = "Peak detect"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.name = "PulseAudio Volume Control"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     native-protocol.peer = "UNIX socket client"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     native-protocol.version = "26"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.id = "org.PulseAudio.pavucontrol"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.icon_name = "audio-card"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.version = "0.99.2"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.process.id = "9473"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.process.user = "vsteel"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.process.host = "chainsaw"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.process.binary = "pavucontrol"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.language = "en_US.UTF-8"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     window.x11.display = ":0"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.process.machine_id = "c19043c01f49e528e76ce2a600000003"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     application.process.session_id = "c19043c01f49e528e76ce2a600000003-1338240205.367573-1881502279"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] source-output.c:     module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] protocol-native.c: Final latency 60.00 ms = 40.00 ms + 20.00 ms
May 28 17:02:12 chainsaw pulseaudio[13095]: [pulseaudio] module-stream-restore.c: Storing volume/mute/device for stream sink-input-by-media-role:music.
May 28 17:02:22  pulseaudio[13095]: last message repeated 10 times
May 28 17:02:22 chainsaw pulseaudio[13095]: [pulseaudio] module-stream-restore.c: Synced.
```I also have scoured and scoured the net and I can not find how to turn on the dynamic rate sampling.  Would someone please let me know how to do that so I can try and get perfect sound out of pulseaudio.  Or at the very least better sound.  Currently if I mix my 96Khz, 88.2Khz and 44.1Khz recordings I get terrible sounds out of the speakers once the frequency changes. (playing a 96Khz song at 88.2Khz).

I am running Kubuntu 12.04 with alsa 1.0.25 
uname -a = 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by samwillc on 2012-05-30
How do I go about installing the update to pulse audio?

I installed it already a few days ago and my vlc sound is AWFUL, scratchy and really not good on the ears! I presume I don't have the latest version which *may* also fix my vlc issue.

More than willing to test this if someone could give me the terminal commands to install the ppa.

Thanks.

Sam.

------------------------------------------------------------------------

**edit** solved my issue in vlc by choosing tools > preferences > audio > output module (ALSA audio output) > HDA ATI SB, ALC892 Analog Default Audio Device

Works ok now through my logitech front left/right and sub. Still would like to test the above though. Thanks.

---

### Post by jfernyhough on 2012-05-30
```
$ sudo apt-add-repository ppa:ubuntu-audio-dev/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```(Also, reading first post points to the PPA on Launchpad. PPA page has instructions for adding.)

---

### Post by samwillc on 2012-05-31
> **jfernyhough said:**
> (Also, reading first post points to the PPA on Launchpad. PPA page has instructions for adding.)

Hi,

Thanks, I did read the launchpad page:

"This PPA can be added to your system manually by copying              the lines below and adding them to your system's software              sources."

...and added the sources to the software centre. Then on clicking software update (in the menu under the little cog top right of screen), there were no updates. I don't know how to initiate sudo update/upgrade via the software centre. Seems easier in terminal.

Sam.

---

### Post by cariboo on 2012-05-31
At this point in time it's better to use the software center or synaptic to do updates.  The repositories are in a state of flux, as new packages are being added hourly.

---

### Post by samwillc on 2012-05-31
> **cariboo907 said:**
> At this point in time it's better to use the software center or synaptic to do updates.  The repositories are in a state of flux, as new packages are being added hourly.

Ok, point noted.

Going to remove pulseaudio ppa. It works on everything I want so time to stick for a while, got a good hand going right now!

Thanks.

Sam.

---

### Post by zika on 2012-06-01
Offtopic: Does [http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu) have Quantal branch?
I can see it via http but main page for alsa-daily-ppa does not show Quantal...

---

### Post by cariboo on 2012-06-01
If you click on the dists link, you see there is a quantal directory, I also see a quantal option on the ppa page.

---

### Post by zika on 2012-06-01
> **cariboo907 said:**
> If you click on the dists link, you see there is a quantal directory, I also see a quantal option on the ppa page.I supose we were talking about different PPA's... ;)
Never mind... Mea culpa... (There was once upon a time ubuntu-audio-dev PulseAudio-nightly, and now PA is in Alsa PPA... ;))

---

### Post by shadowwizzard on 2012-06-13
Greetings,

I've a question regarding this 2.0 version.
Why equalizer module and qpaeq is not included in ubuntu build of pulseaudio 2.0 ?

---

### Post by Starks on 2012-06-13
Why does jack detection for HDMI still not work?

Btw, I've built equalizer-enabled PA. It's not worth it. That other unofficial PA equalizer is still miles better.

---

### Post by shadowwizzard on 2012-06-14
I just doesn't understand why it's not built ? In that case users can't even try it to judge it or improve it.
 The other one equalizer mentioned by you have a lot of dependencies (including gnome components) so I don't like it in KDE environment. 
Anyway I don't see a reason to not include it in official build .
 Is there any problem with including it ?

---

### Post by Starks on 2012-06-14
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/932834](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/932834)

Luke seems skeptical it will ever be enabled

---

### Post by shadowwizzard on 2012-06-14
Thank you very much for clarifying the issue :)

---

### Post by mileslane on 2012-07-05
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1020154](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1020154)

Currently, pulseaudio is misconfiguring my system.  It does not enable my ASUS UL50VT internal speakers and microphone.  This machine contains two sound cards:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

When I look at the device list in the Sound Control Panel, only the "Simultaneous output to High Definition Audio Controller Digital Stereo (HDMI)" is shown for output.  Nothing is listed for input.

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by frogotronic on 2012-08-15
Hello,

  This PPA version fixed a problem with sound routing out through the display port on an nVIDIA Quadro2000 card running the XSWAT drivers.  Previously, every time I rebooted I lost sound and would have to manually reselect the correct HDMI output.

Thanks,
CH

---


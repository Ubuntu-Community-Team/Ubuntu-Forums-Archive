---
title: "Problems with JACK"
date: 2011-08-12
forum: Ubuntu Studio
---

### Post by Keith_Beef on 2011-08-12
Good evening, all.

I've a problem with Jack. I recently got an Alesis Q49 midi keyboard, that I connect to my computer running Ubuntu 10.10 with ubuntu studio through a USB cable.

Here's what I'm doing, and what's happening.

Boot, with the Alesis keyboard plugged into a USB hub.

Check that the keyboard is seen:
$ usb-devices 
...
T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=13b2 ProdID=0063 Rev=01.00
S:  Manufacturer=Alesis
S:  Product=Q49
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 2 Cls=01(audio) Sub=03 Prot=00 Driver=snd-usb-audio


Play an OGG file through Totem, works fine.

While Totem is playing, start amsynth; pressing the AUdition button plays a sound, as it should.

Quit Totem, quit amsynth.

Start Jack Control, seems to start up OK.

Start amsynth again; now, pressing the AUdition button just gets a short "tok" sound, instead of the full note.

In the connection panel:
	Audio tab,
		readable client amSynth is connected to writable client system
		readable client PulseAudio JACK Sink is connected to writable client system
		readable client system is connected to writable client PulseAudio JACK Source

	Midi tab is completely empty

	ALSA tab
		readable client 14:Midi Through		writable client 14:Midi Through
		readable client 20:Q49			writable client 20:Q49
		readable client 129:amSynth		writable client 129:amSynth
		(no connections)

Played music through Rhythbox, from NAS.
From time to time, music seems to skip, when this happens, the message in Jack Control is either:
JackAudioDriver::ProcessAsync: read error, skip cycle
or something like:
21:57:30.432 XRUN callback (58).

$ ps -edf | grep -i jack
xxxxxxxx  4123     1  0 21:46 ?        00:00:03 /usr/bin/qjackctl
xxxxxxxx  4135  4123  1 21:46 ?        00:00:06 /usr/bin/jackd -v -dalsa -dhw:0,0 -r48000 -p128 -n2
xxxxxxxx  4147     1  2 21:46 ?        00:00:13 pulseaudio -DnF /home/xxxxxxxx/.pulse/pulsejack.pa
xxxxxxxx  4248  2874  0 21:55 pts/0    00:00:00 grep --color=auto -i jack

Here's the contents of pulsejack.pa, stripped of all comments

.nofail

.fail

load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

load-module module-augment-properties

load-module module-jack-source
load-module module-jack-sink

.ifexists module-udev-detect.so
load-module module-udev-detect
.else

load-module module-detect
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

load-module module-default-device-restore

load-module module-rescue-streams

load-module module-always-sink

load-module module-intended-roles

load-module module-suspend-on-idle

load-module module-console-kit

load-module module-position-event-sounds


I've tried amsynth, genpo, ZynAddSubFX... they show up in Jack Control, but I get no sound (except for the "toc" in amsynth), however Rhythmbox and Totem play find, but don't show up in Jack Control.

This makes me think it is just a Jack Control problem.

I've read a dozen threads and a few web tutorials, but cannot figure this out.

What am I doing wrong?


Second thing I like to know, is how can I test that the keyboard is sending midi commands? I've been trying cat /dev/input/event[0-3] but although that catches mouse and keyboard actions, it does nothing when I press the Q49's keys.

I hope I can get some help here...

---

### Post by sgx on 2011-08-13
doublepost

---

### Post by sgx on 2011-08-13
Hi, some audio players can use jackd, aqualung autoconnects by default, vlc, xine, xmms and others have a back-end in the repositories that you can install for them. But connections must be made for some of them (see link below)

It is best to avoid using a hub with audio devices, some will force
unknown devices to use usb 1.1, which might fail. After plugging the alesis into a regular usb port, reboot, and use this command

ps ux

to look for anything named pulse, and if you find one, use

killall name-of-pulse  to end it for this session.

Now start your soundserver with

jackd -d alsa -r 44100 -p128 -n3

Now start qjackctl, (here is a link with screenshots)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

and follow the guide, using phasex,
zynaddsubfx, or yoshimi (not sure if amsynth is a jackd app)

Once the connections in qjackctl are made, the alesis should be playing the chosen softsynth.

In the qjackctl Setup page, on the right are

Input device >
Output device >

click the > widgets, to see the detected sound hardware, and choose your soundcard for output, and the alesis for input

Cheers

---

### Post by Keith_Beef on 2011-08-13
Thanks, SGX, that's helping me out a bit. I now know that the Q49 is sending midi commands and these are getting to the softsynth. Sadly, I get no sound... so I think the problem is not so much with the Q49 or jack control, but it seems that all sound disappears whenever jackd is running... so it's a problem with jackd.

I started the server as you suggested, but after reading [another page]("https://help.ubuntu.com/community/HowToJACKConfiguration") I tried adding -S too. This doesn seem to change anything, as you'll see later.

jackd -S -d alsa -r 44100 -p128 -n3

Then started jack control and zynaddsubfx. This was a good one to choose, because the level meters show that at least something is happening; when I press a key on the Q49 I see the level meters in zynaddsubfx move.

Now, here's something else I just found, since I began typing this reply...

I stopped jack control and made sure jackd was no longer running, then I started up amsynth and Patchage. This showed me the Q49 (actually two instances of this), QAMix (that I had left open after settin glevels for playing back some music), TiMidity, amSynth and two instances of Midi Through.

I connected one instance of Q49 to the amSynth MIDI IN, and now when I press a key on the Q49 I get sound out of amSynth, but with a delay of what seems like about half a second.

K.

---

### Post by sgx on 2011-08-13
> **Keith_Beef said:**
> Thanks, SGX, that's helping me out a bit. I now know that the Q49 is sending midi commands and these are getting to the softsynth. Sadly, I get no sound... so I think the problem is not so much with the Q49 or jack control, but it seems that all sound disappears whenever jackd is running... so it's a problem with jackd.

I started the server as you suggested, but after reading [another page]("https://help.ubuntu.com/community/HowToJACKConfiguration") I tried adding -S too. This doesn seem to change anything, as you'll see later.

jackd -S -d alsa -r 44100 -p128 -n3

Then started jack control and zynaddsubfx. This was a good one to choose, because the level meters show that at least something is happening; when I press a key on the Q49 I see the level meters in zynaddsubfx move.

Now, here's something else I just found, since I began typing this reply...

I stopped jack control and made sure jackd was no longer running, then I started up amsynth and Patchage. This showed me the Q49 (actually two instances of this), QAMix (that I had left open after settin glevels for playing back some music), TiMidity, amSynth and two instances of Midi Through.

I connected one instance of Q49 to the amSynth MIDI IN, and now when I press a key on the Q49 I get sound out of amSynth, but with a delay of what seems like about half a second.

K.Try -n2 (that should be 3 for usb soundcards, but you
have a usb midi keyboard -my bad advice, sorry!) and -p64

These should reduce latency. patchage is another gui for jackd,
so if it's running and working, it started up another jackd for you.
I would install   alsamixergui, it shows all the soundcard outputs
and make sure nothing you need is muted.

Connection in both the alsa and audio tabs of qjackctl is needed for zynaddsubfx, if the meters are bouncing, either the mixer is muted, or the wrong output device is chosen in qjackctl setup page.

Timidity may have been started from some other app, I would start from
a clean boot, and get things working with zyn, and then most other things will also work. Your system audio for playing music CDs and movies does not require or use jackd.

ps ux

will show what processes are running

timemachine is a good simple jackd recording app, to save your new
performances.
Cheers

---

### Post by Keith_Beef on 2011-08-13
Thanks again for your help.

In the end, I think that the delay I noticed in amSynth is not from jackd but from amSynth itself. I managed to use Patchage to connect the Q49 to both Hydrogen and to amSynth. When I press a key, Hydrogen's drum sound comes on immediately, but amSynth's note comes on about half a second later.

K.

---


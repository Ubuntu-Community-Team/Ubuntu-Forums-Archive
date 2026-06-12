---
title: "Scarlett 2i4 no audio"
date: 2016-11-02
forum: Ubuntu Studio
---

### Post by sanfrd16237 on 2016-11-02
I finally got my new scarlett 2i4 the other day and I've run through a few different how to's on setting jack up and I'm still unable to get any sound from the 2i4.  Just to clarify on my setup, im trying to simply play my electric through the 2i4 and listen on headphones through it.  I've tried playing with the settings in a bunch applications like guitarx, ardour, etc and still nothing.  I've used linux for a while and sort of know my way around but this is my first time trying to do any recording with it.  I feel like I'm missing something simple here.  Also here are the messages from jack when I start it up.  Any help would be greatly appreciated.



```
[COLOR=#999999]20:17:05.135 Statistics reset.[/COLOR][COLOR=#cccc99]20:17:05.139 ALSA connection change.[/COLOR]
[COLOR=#999999]20:17:05.142 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
[COLOR=#66cc99]20:17:05.158 ALSA connection graph change.[/COLOR]
[COLOR=#999999]20:17:33.999 D-BUS: JACK server is starting...[/COLOR]
[COLOR=#999999]20:17:34.009 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
Wed Nov  2 20:17:33 2016: Starting jack server...
Wed Nov  2 20:17:33 2016: JACK server starting in realtime mode with priority 10
Wed Nov  2 20:17:33 2016: self-connect-mode is "Don't restrict self connect requests"
Wed Nov  2 20:17:33 2016: Acquired audio card Audio1
Wed Nov  2 20:17:33 2016: creating alsa driver ... hw:USB|hw:USB|1024|2|44100|0|0|nomon|swmeter|-|32bit
Wed Nov  2 20:17:33 2016: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Wed Nov  2 20:17:33 2016: ALSA: final selected sample format for capture: 32bit integer little-endian
Wed Nov  2 20:17:33 2016: ALSA: use 2 periods for capture
Wed Nov  2 20:17:33 2016: ALSA: final selected sample format for playback: 32bit integer little-endian
Wed Nov  2 20:17:33 2016: ALSA: use 2 periods for playback
Wed Nov  2 20:17:33 2016: graph reorder: new port 'system:capture_1'
Wed Nov  2 20:17:33 2016: New client 'system' with PID 0
Wed Nov  2 20:17:33 2016: graph reorder: new port 'system:capture_2'
Wed Nov  2 20:17:33 2016: graph reorder: new port 'system:playback_1'
Wed Nov  2 20:17:33 2016: graph reorder: new port 'system:playback_2'
Wed Nov  2 20:17:33 2016: graph reorder: new port 'system:playback_3'
Wed Nov  2 20:17:33 2016: graph reorder: new port 'system:playback_4'
Wed Nov  2 20:17:34 2016: New client 'PulseAudio JACK Sink' with PID 1629
Wed Nov  2 20:17:34 2016: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Wed Nov  2 20:17:34 2016: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Wed Nov  2 20:17:34 2016: New client 'PulseAudio JACK Source' with PID 1629
Wed Nov  2 20:17:34 2016: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Wed Nov  2 20:17:34 2016: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
[COLOR=#9999cc]20:17:36.071 JACK connection change.[/COLOR]
[COLOR=#999933]20:17:36.072 Server configuration saved to "/home/daveis/.jackdrc".[/COLOR]
[COLOR=#999999]20:17:36.072 Statistics reset.[/COLOR]
[COLOR=#999999]20:17:36.088 Client activated.[/COLOR]
[COLOR=#999999]20:17:36.088 Patchbay deactivated.[/COLOR]
[COLOR=#cc9966]20:17:36.126 JACK connection graph change.[/COLOR]
Wed Nov  2 20:17:35 2016: Saving settings to "/home/daveis/.config/jack/conf.xml" ...
Wed Nov  2 20:17:36 2016: New client 'qjackctl' with PID 2768
```

---

### Post by CrocoDuck on 2016-11-03
Is it the old or new Scarlett series? Not that it should matter, they both should work. I own the old one and it works as a charm. Give us the output of these commands:

```

aplay -l
arecord -l
amidi -l
cat .jackdrc

```

---

### Post by sanfrd16237 on 2016-11-03
Its the old one.  I kind of wanted the new one but from the comparison tests it looked like the latency differences were negligible.  Plus the old ones can be had new for a pretty good price now.  On a positive note, I did find that Rakarrack would produce audio.  Although it sounded very flat, weak, and diminished.  There was a lot of latency also.  Whatever was working wasn't working right, that was apparent.  Also, CrocoDuck, I've been reading through your blog for the past few months and there's a lot of good info there.  Thanks for keeping that  thing up.  Its helped me out a few times. 


 
aplay -l
```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [Scarlett 2i4 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

arecord -l
```
**** List of CAPTURE Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [Scarlett 2i4 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

amidi -l
```
Dir Device    NameIO  hw:1,0,0  Scarlett 2i4 USB MIDI 1



```

cat  .jackdrc
```
/usr/bin/jackd -dalsa -dhw:USB -r44100 -p1024 -n2


```

---

### Post by CrocoDuck on 2016-11-03
Uhm... apparently your device is correctly recognized and jack has been told to use it. So, the problems is that jack starts but you cannot hear sound through the headphones. Is that correct? Check that you are monitoring the right channels. On the front of the device there is a switch. If your audio programs are connected to, say, system playback_1 and playback_2 make sure you select 1-2 in the front switch. Audio sounds exactly like you mentioned when you are monitoring the wrong channels (there is some crosstalk between the channels).

> **sanfrd16237 said:**
> Also, CrocoDuck, I've been reading through your blog for the past few months and there's a lot of good info there.  Thanks for keeping that  thing up.  Its helped me out a few times. 

Uh, thanks!

---

### Post by sanfrd16237 on 2016-11-03
Well, everything is where it should be on the unit itself.  Switching the cable between the two inputs produces its own oddities.  Channel 2 sounds even worse than 1.  I still dont have any sound from any the programs except for the super poor audio from rakarrack.  The audio there is super quiet and you have to crank up the gain really high just to even hear anything but then its all distorted.  I have been looking at patchage and have noticed that with guitarix nothing is hooked up as opposed to rakarrack some things are linked up.  Im guessing this might be the problem.  Are there any good guides to figuring out this spaghetti mess?

---

### Post by CrocoDuck on 2016-11-04
> **sanfrd16237 said:**
> Well, everything is where it should be on the unit itself.  Switching the cable between the two inputs produces its own oddities.  Channel 2 sounds even worse than 1.  I still dont have any sound from any the programs except for the super poor audio from rakarrack.  The audio there is super quiet and you have to crank up the gain really high just to even hear anything but then its all distorted.

This is weird. Are you sure your unit is not defective? It does not really look as a software problem. If you have a chance, hook up your device to a computer with another os (win or mac) and check how it works. It might be worth to try the audio outputs by connecting them to a stereo or some kind of speakers, so that we can rule out whether the audio streams that come from the computer are bad or there is some kind of circuit issue.

> **sanfrd16237 said:**
> I have been looking at patchage and have noticed that with  guitarix nothing is hooked up as opposed to rakarrack some things are  linked up.  Im guessing this might be the problem.  Are there any good  guides to figuring out this spaghetti mess?

Most of the jack programs do not auto connect to sockets. You have to manually connect them or configure autoconnection yourself. At first it looks indeed messy, but you will find the ability of linking together programs as they were stomp-boxes incredibly powerful. Here a [good reference]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack").

---

### Post by sanfrd16237 on 2016-11-04
Yea, I was kind of worried about that.  I think over the next few days I'll try it with a few other distros and see if I can reproduce the issues.  I have a really weak windows tablet I might be able to test on too.  Thanks again for the help and I'll post the results soon enough.

---


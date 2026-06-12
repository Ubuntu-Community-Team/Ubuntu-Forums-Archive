---
title: "A little recording problem"
date: 2011-06-27
forum: Ubuntu Studio
---

### Post by wheresmything on 2011-06-27
i am currently enjoying all the features of ubuntustudio and have no complaints. ok, i got rosegarden, qsynth to work with vmpk keyboard and all the nice soundfonts i could get. it works with alsa selected in qsynth, not with jack. i cannot for the life of me get jack working at all. well, it does "work" in the sense the program starts and i can start the server, but no sound. not a peep. nothing.
ok, the issue...
now that i have written my little tune and have all the midi inputs instruments or what they are called set up, how do i record that to an mp3 format or something similar? i have read that ardour will do it, and a dirty way of just recording an audio track with rosegarden, but those methods need jack and i have explained my experience with jack. audacity will not do it. i tried just playing it and recording it with sound recorder, nothing doing. 
i guess the really cheap way to do it would be to run a line from my line-out to a line-in on some tape deck or something. i guess. but are there any other ways to do this?

---

### Post by cchhrriiss121212 on 2011-06-27
Jack is a great tool for audio, so I would recommend you take another look at it. If you use patchage to connect everything up it should be pretty straightforward.

OTOH, if you just want a quick solution:
[http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html](http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html)

---

### Post by Pablo_F on 2011-06-27
Hi, 

I think you are confusing things. Jack has "two sides", Audio and MIDI. Depending on the context, "Jack" could refer to MIDI, although it is more common that just refers to the audio side.

If you are able to hear sounds with Rosegarden-qsynth, you are already have jack audio up and running. Only, you are not using jack MIDI but alsa MIDI. Normally, this is not a problem (although jack MIDI has more accurate timing). As Rosegarden has not jack MIDI ports, rosegarden users certainly need to choose alsa MIDI in qsynth (well, there is a bridge called a2jmidid to expose alsa MIDI ports to Jack MIDI, but better use the same MIDI system in both sides, sequencer and synth. There are synths like yoshimi and sequencers like ardour3 that only do jack MIDI so if (for example) you wanted to use Rosegarden with yoshimi you would need a2jmidid).

I suggest you use patchage for a general view of audio and MIDI ports. Blue is jack audio, red is jack MIDI, green is alsa MIDI. You can see the same in qjackctl, connections window.

Ardour2 only needs jack audio. So you can use it. It can't export to mp3 though. You can convert to mp3 later, via Audacity or simple command line tools.

Also, there are simple jack audio recorders. My favourite ones are jack timemachine and jack_capture. The latter can record to mp3 directly and it autoconnects whatever is connected to the "system: playbacks" to their input (recording) ports. Therefore, it records what you are hearing through the speakers or headphones. The sad part is that jack_capture is not in the official repos.

Cheers, Pablo

---

### Post by wheresmything on 2011-06-27
Thank you for the kind replies.  I followed a tutorial on setting qjackctl with zyn and some virtual keyboard (zyn has a keyboard, but i was following directions) and again, nothing. no sound. although in the connections i do not see "alsa_pcm", i see "system" and the midi is backwards than the diagrams shown. i am guessing my soundcard works with alsa (its an onboard ATI radeon something. came with the gigabyte motherboard) since i am making sounds not using qjackctl. i know it is working, i can see the display on qjackctl change and the zyn meters were working fine. but, nothing in the speakers (or headphones).
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

patchage looks nice, but what are "dropouts"? they just kept adding up.

the soundrecorder is the cheap and dirty way, but works (had to go through a few hoops to get it to work, but it works!). i would really like to get ardour to work because it looks really involved way of doing things and i love it complicated!
seriously. 

thank you again for the kind replies.

---

### Post by cchhrriiss121212 on 2011-06-27
Are you seeing xruns in jack message window? If so you will need to change your settings. Please post the results of this in a terminal;
```
aplay -l && cat ~/.jackdrc
```If jack is running happily, then it seems as if you just need to connect the zyn output to the correct system payback port.

---

### Post by wheresmything on 2011-06-27
ok, here goes...

james@Andromeda-II:~$ cat aplay -l && cat ~/.jackdrc
cat: invalid option -- 'l'
Try `cat --help' for more information.
james@Andromeda-II:~$ 

ok, seems that first part is a little off...so i tried help

james@Andromeda-II:~$ cat --help
Usage: cat [OPTION]... [FILE]...
Concatenate FILE(s), or standard input, to standard output.

  -A, --show-all           equivalent to -vET
  -b, --number-nonblank    number nonempty output lines
  -e                       equivalent to -vE
  -E, --show-ends          display $ at end of each line
  -n, --number             number all output lines
  -s, --squeeze-blank      suppress repeated empty output lines
  -t                       equivalent to -vT
  -T, --show-tabs          display TAB characters as ^I
  -u                       (ignored)
  -v, --show-nonprinting   use ^ and M- notation, except for LFD and TAB
      --help     display this help and exit
      --version  output version information and exit

With no FILE, or when FILE is -, read standard input.

Examples:
  cat f - g  Output f's contents, then standard input, then g's contents.
  cat        Copy standard input to standard output.

Report cat bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
For complete documentation, run: info coreutils 'cat invocation'
james@Andromeda-II:~$ 

that did not help, so i tried the part after the &&...

james@Andromeda-II:~$ cat ~/.jackdrc
/usr/bin/jackd -p128 -t5000 -dalsa -r48000 -p64 -n3 -S -Xseq -D -Chw:0 -Phw:0 -zr
james@Andromeda-II:~$ 

thanks for the help, dig that picture by the way

---

### Post by cchhrriiss121212 on 2011-06-28
My bad, that should be:
aplay -l
you don't need the "cat" in there.

But I can see from your settings that you have latency set quite low, could you start jack and post what the message window says?

---

### Post by Pablo_F on 2011-06-28
Yes, you have to increase the frames/period. The default 1024 is good to start with. Also, try 2 periods/buffer. Don't use dither. Also, in most cases (duplex analog devices as I guess it is your case) it is neater if you just select the interface, and leave the input and output devices blank.  

Yes, alsa_pcm is now called "system". It is the audio card that jack is using.

Dropouts are buffer underruns or overruns, i.e., missing audio data. They are also called xruns. You are telling jack to use a buffer much too short for your hardware-software system configuration. Increase the latency. 

Cheers, Pablo

---

### Post by wheresmything on 2011-06-28
the message/status i get when i start qjackctl (with new config, thanks pablo) and zyn
the message side...

[COLOR=#999999]19:08:26.187 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:08:26.209 Statistics reset.[/COLOR]
 [COLOR=#cccc99]19:08:26.352 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]19:08:26.403 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]19:14:14.181 Statistics reset.[/COLOR]
 [COLOR=#999999]19:14:15.008 Statistics reset.[/COLOR]
 [COLOR=#999999]19:14:15.472 Statistics reset.[/COLOR]
 [COLOR=#999999]19:14:15.880 Statistics reset.[/COLOR]
 [COLOR=#66cc99]19:14:35.860 ALSA connection graph change.[/COLOR]
 [COLOR=#66cc99]19:14:36.612 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]19:14:36.778 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:14:44.350 JACK is starting...[/COLOR]
 [COLOR=#990099]19:14:44.351 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r48000 -p1024 -n2 -S -Xseq[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 [COLOR=#999999]19:14:44.386 JACK was started with PID=2150.[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]jackdmp 1.9.7[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]Copyright 2004-2010 Grame.[/COLOR]
 [COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=#999999]control device hw:0[/COLOR]
 [COLOR=#999999]control device hw:0[/COLOR]
 [COLOR=#999999]audio_reservation_init[/COLOR]
 [COLOR=#999999]Acquire audio card Audio0[/COLOR]
 [COLOR=#999999]creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|16bit[/COLOR]
 [COLOR=#999999]control device hw:0[/COLOR]
 [COLOR=#999999]Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe024000 irq 16[/COLOR]
 [COLOR=#999999]configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for capture: 16bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#999999]ALSA: final selected sample format for playback: 16bit little-endian[/COLOR]
 [COLOR=#999999]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#66cc99]19:14:44.699 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]port created: Midi-Through:midi/playback_1[/COLOR]
 [COLOR=#999999]port created: Midi-Through:midi/capture_1[/COLOR]
 [COLOR=#999999]port created: ZynAddSubFX:midi/capture_1[/COLOR]
 [COLOR=#9999cc]19:14:46.452 JACK connection change.[/COLOR]
 [COLOR=#999933]19:14:46.482 Server configuration saved to "/home/james/.jackdrc".[/COLOR]
 [COLOR=#999999]19:14:46.483 Statistics reset.[/COLOR]
 [COLOR=#999999]19:14:46.500 Client activated.[/COLOR]
 [COLOR=#cc9966]19:14:46.531 JACK connection graph change.[/COLOR]
 
a screenshot is a little extreme, so i will describe the connections...
AUDIO
left side, SYSTEM
right side, SYSTEM

MIDI
left side, SYSTEM (with a clock or pin-connector in it)
right side, SYSTEM (with a clock or pin-connector in it)

ALSA
left side, MIDI THROUGH
right side, MIDI THROUGH and ZYN

also...

james@Andromeda-II:~$ aplay -l && cat ~/.jackdrc
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
/usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r48000 -p1024 -n2 -S -Xseq
james@Andromeda-II:~$ 


thats it. thanks for stepping me through this...

---

### Post by Pablo_F on 2011-06-28
Hi, 

This looks so much better. BTW, you really don't need a jack MIDI driver. You are using alsa MIDI so far.

Two more tips: 

1) Run jack in synchronous mode: In the "server path" field, write down:

/usr/bin/jackd --sync (-S instead of --sync does the trick also).

2) Use card names instead of numbers. Numbers can get mixed up in different reboots. Now, your onboard is hw:0, but this could change without you noticing. So, in the interface field write down:

hw:SB

to make sure that jack is always using the onboard card. 

I suggest you also check *arecord -l* to see the capture devices. A card (or "interface" in qjackctl's terminology) can have more than one "device". hw:SB,0 (card SB, device 0) is a duplex device (it can do playback and capture) so you will see it in both *arecord -l* and *aplay -l*. However, some devices could be capture only or playback only, so it is a good idea to check also *arecord -l*


Now, back to the topic. You can record audio from the output ports of any jack client and from the capture ports of the souncard that jack is using (referred to as "system") with any jack-aware recorder, including ardour. But don't use the default sound recorder as it is not jack-aware. 

Cheers, Pablo

---

### Post by wheresmything on 2011-07-01
thanks a lot. i got qjackctl working...at least sound comes out using ZYN and nothing else. i played with the patchbay and it was working. unfortunately i did not take note of what i was doing. 

i tried with ardour, but i could not figure out the connections (there are like 20 of them) and it did not work. do i need to go into the patchbay and redo all my connections? do i need to have the full version of ardour rather than the one that comes with studio? so many questions!

but again i thank you all very much for your time and input.

---

### Post by jejeman on 2011-07-01
> do i need to have the full version of ardour rather than the one that comes with studio?What full version?

---

### Post by wheresmything on 2011-07-01
according to the ardour website, there is a -i am guessing here- full version of the software. or a pro version i may be mistaken.

---

### Post by sgx on 2011-07-02
There is a V3,xxx beta, and various stable versions, depending on
the linux version you have. That's it. Check youtube for ardour/zyn videos.
Cheers

---

### Post by wheresmything on 2011-07-10
ok, back to the main issue at hand...jack seems to be moody. i had it working once. once.
it will not come back on at all. when i start it, if it starts, it won't produce sound. not a peep.  

here is the aplay and arecord:

james@Andromeda-II:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
james@Andromeda-II:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
james@Andromeda-II:~$ 

see the attached screen shots for more details on the setup.

this message will be in two or three installments

---

### Post by wheresmything on 2011-07-10
continued from the last...

---

### Post by wheresmything on 2011-07-10
part three, the final one.
i have a self made 64 bit machine, (amd phenom II, gigabyte mb, onboard realtek -i think or radeon soundcard, 16gb memory) i am running ubuntu studio 11.04 and i know i have a low latency kernel because i installed it and could nto use my computer for 4 hours due to some vid card glitch with the kernel. at least that is what some forum anwer was. 

at any rate, i can use qsynth with alsa and alsa only. in fact all i can use is alsa. but i want to record audio and need jack for that or get down and dirty and just plug a mixer in and do it that way. dont want ot do that if i do not have to.

i have noticed that jack seems to cause a lot of headaches for people, both users and helpers. is there an alternative to jack?

even the vids from youtube dont seem to help with the jack. maybe its karma that i cannot get it to work, i am not sure. :cry:

---

### Post by wheresmything on 2011-07-10
oops, forgot the shots

---

### Post by cchhrriiss121212 on 2011-07-10
Jack is running OK in your screen shots, so the trouble you seem to be having is with the connections. Did you take a look at patchage?

I will put down some simple steps here and you can reply with what works or not:

[LIST=1]
[*]Open jack, press start (forget about the patchbay, as soon as it starts you can ignore it)
[*]Open qsynth and virtual keyboard
[*]Open patchage - connect the green boxes for virtual keyboard and fluid synth together; then connect the blue qsynth boxes to system playback
[*]Select a soundfont in qsynth using the channels window
[*]Play a few notes with the virtual keyboard
[/LIST]
If jack is not starting, please post what the message window says.

---

### Post by wheresmything on 2011-07-10
did as said...no sound, here is what it says...

 p, li { white-space: pre-wrap; }  [COLOR=#999999]23:34:42.486 Patchbay activated.[/COLOR]
 [COLOR=#999999]23:34:42.513 Statistics reset.[/COLOR]
 [COLOR=#cccc99]23:34:42.598 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]23:34:42.629 ALSA connection graph change.[/COLOR]
 [COLOR=#99cc66]23:34:42.802 ALSA active patchbay scan...[/COLOR]
 [COLOR=#999999]23:34:44.832 JACK is starting...[/COLOR]
 [COLOR=#990099]23:34:44.833 /usr/bin/jackd --sync -p128 -t5000 -dalsa -dhw:SB -r48000 -p1024 -n2 -S -Xseq -P[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]23:34:44.857 JACK was started with PID=2099.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:SB|-|1024|2|48000|0|0|nomon|swmeter|-|16bit
 Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe024000 irq 16
 configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 2 periods for playback
 [COLOR=#66cc99]23:34:45.222 ALSA connection graph change.[/COLOR]
 port created: Midi-Through:midi/playback_1
 port created: Midi-Through:midi/capture_1
 [COLOR=#99cc66]23:34:45.405 ALSA active patchbay scan...[/COLOR]
 [COLOR=#9999cc]23:34:47.036 JACK connection change.[/COLOR]
 [COLOR=#999933]23:34:47.111 Server configuration saved to "/home/james/.jackdrc".[/COLOR]
 [COLOR=#999999]23:34:47.112 Statistics reset.[/COLOR]
 [COLOR=#999999]23:34:47.130 Client activated.[/COLOR]
 [COLOR=#6699cc]23:34:47.132 JACK active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:34:47.161 JACK connection graph change.[/COLOR]
 [COLOR=#6699cc]23:34:47.358 JACK active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:34:56.474 JACK connection graph change.[/COLOR]
 [COLOR=#66cc99]23:34:56.507 ALSA connection graph change.[/COLOR]
 port created: FLUID-Synth-(2111):midi/capture_1
 [COLOR=#6699cc]23:34:56.569 JACK active patchbay scan...[/COLOR]
 [COLOR=#99cc66]23:34:56.571 ALSA active patchbay scan...[/COLOR]
 [COLOR=#9999cc]23:34:56.619 JACK connection change.[/COLOR]
 [COLOR=#cccc99]23:34:56.645 ALSA connection change.[/COLOR]
 [COLOR=#cc66cc]23:34:56.646 XRUN callback (1).[/COLOR]
 [COLOR=#cc9966]23:34:56.646 JACK connection graph change.[/COLOR]
 **** alsa_pcm: [COLOR=#cc0000]xrun of at least 78.015 msecs[/COLOR]
 JackPosixMutex::Unlock res = 1
 [COLOR=#6699cc]23:34:56.846 JACK active patchbay scan...[/COLOR]
 [COLOR=#99cc66]23:34:56.847 ALSA active patchbay scan...[/COLOR]
 [COLOR=#66cc99]23:35:04.040 ALSA connection graph change.[/COLOR]
 [COLOR=#99cc66]23:35:04.057 ALSA active patchbay scan...[/COLOR]
 [COLOR=#cccc99]23:35:04.059 ALSA connection change.[/COLOR]
 [COLOR=#cc9966]23:35:04.063 JACK connection graph change.[/COLOR]
 port created: Virtual-Keyboard:midi/playback_1
 [COLOR=#66cc99]23:35:04.065 ALSA connection graph change.[/COLOR]
 [COLOR=#6699cc]23:35:04.260 JACK active patchbay scan...[/COLOR]
 [COLOR=#99cc66]23:35:04.262 ALSA active patchbay scan...[/COLOR]
 [COLOR=#9999cc]23:35:04.263 JACK connection change.[/COLOR]
 [COLOR=#6699cc]23:35:04.465 JACK active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:35:10.868 JACK connection graph change.[/COLOR]
 [COLOR=#6699cc]23:35:10.874 JACK active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:35:10.900 JACK connection graph change.[/COLOR]
 [COLOR=#66cc99]23:35:10.901 ALSA connection graph change.[/COLOR]
 [COLOR=#6699cc]23:35:11.101 JACK active patchbay scan...[/COLOR]
 [COLOR=#99cc66]23:35:11.102 ALSA active patchbay scan...[/COLOR]
 [COLOR=#66cc99]23:36:39.613 ALSA connection graph change.[/COLOR]
 [COLOR=#99cc66]23:36:39.798 ALSA active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:37:11.631 JACK connection graph change.[/COLOR]
 [COLOR=#6699cc]23:37:11.633 JACK active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:37:21.828 JACK connection graph change.[/COLOR]
 [COLOR=#6699cc]23:37:21.845 JACK active patchbay scan...[/COLOR]
 [COLOR=#cc9966]23:37:24.601 JACK connection graph change.[/COLOR]
 [COLOR=#6699CC]23:37:24.651 JACK active patchbay scan...[/COLOR]

[COLOR=#6699CC][/COLOR]
[COLOR=#6699cc]i dont get it...i checked my audio settings on the system (making sound come out at all, and it works)
[/COLOR]

---

### Post by cchhrriiss121212 on 2011-07-10
How about using other programs with jack? Does zynaddsubfx work? Can you play anything with aqualung?

---

### Post by wheresmything on 2011-07-11
ok, i got it to work (had some overruns, but it still played sound!) even got ardour to work with it and later rosegarden. 
thank you so much to you and all who have helped me!

i will now mark this as solved. 

as soon as i figure how.

---


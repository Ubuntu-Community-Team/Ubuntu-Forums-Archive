---
title: "persistent midi connection"
date: 2010-08-18
forum: Ubuntu Studio
---

### Post by spetroff on 2010-08-18
Hello,

I'd like to find out more about how to configure an M-Audio Axiom 49 in Ubuntu Studio 10.04 (SB Live 5.1 in an older single core AMD system if it makes a difference).

The keyboard did not function 'out of the box', but it wasn't too hard to get started. I've played with 3 ways to get it working so far. The first was ZynAddSubFX and the ALSA Connect GUI. This setup worked the best and had the kids up and playing around. However, the connection isn't persistent, and I'd like something that is easier for my son to use. I also succeeded partially with LMMS, but it had an annoying latency, so I didn't spend any time with it. I also had some measure of success with the JACK Control. If I went in via JACK Control's Connect utility and connected the Axiom to TiMidi, it worked, but had horrible latency. If I set up the "same" connection via Patchbay, I got nothing.

What I want to achieve is setting up per/user default instrument and a persistent 'connection' so that my 7yr old can log into his account and just play. I can teach him what to do if he wants to change instruments, but ideally he could just play his 'trash guitar' and his big sister could use her default piano sounds.

To that end, either I need to deal with the latency issues or somehow configure ZynAddSubFX to run in the background on startup/login and on the same event that triggers the Axiom to appear in the ALSA Sequencer, set up the 'connection'. Is that doable? Or is there a better way to set this up? Thanks

---

### Post by Pablo_F on 2010-08-18
Hi, 

Before thinking on automating the connectios, I suggest you should start the jack audio server, for lower audio latency. In this case you would launch qjackctl (Jack Control). In the setup button, enable the realtime option if disabled and then start the jack server (start button). You will need to set the rtprio and memlock limits for the users belonging to the audio group. Check with: 

sudo dpkg-reconfigure -p high jackd

and then add the users to this "audio" group 

If the jack server is running, to get sound you need a "jackified" synth, at least in the audio part. For example, timidity is not jackified by default, but you can use zynaddsubfx or others. I suggest you try qsynth which plays soundfonts. You need to load a soundfont, you can install a decent general midi one through synaptic or apt-get. The package is called "fluid-soundfont-gm" and the sf2 file is installed as "/usr/share/sounds/sf2/FluidR3_GM.sf2".

For a "per user default instrument" you can save a preset. At least in qsynth (channels button), you can make a preset with up to 16 channels, each with a different instrument. Selecting the channels from the midi keyboard should be easy.

As for the midi connection, there is this command "aconnect" which connects alsa midi ports. List the ports with:

aconnect -io

and make the connections with (just an example, choose the client and port numbers for your axiom 49 and your software synth):

aconnect 28:0 131:0

Once you are pleased with whatever combination, you can make a script, for example:

example.sh

#!/bin/bash
sleep 5
qjackctl &
sleep 3
qsynth &
sleep 3
aconnect 28:0 131:0

Or something similar. You will need to setup qjacktl to "start jack audio server on application startup" in the misc tab and the soft sytnh to autoconnect the audio outputs to the system playbacks.

Then you can move the script to /usr/local/sbin and so, "example.sh" is like a new command. You can put this command in System -> Preferences -> Startup Applications or just add a custom launcher for it.

Feel free to ask if something is not clear. I could have missed something but I hope this helps.

Cheers! Pablo

---

### Post by AutoStatic on 2010-08-18
> **Pablo_F said:**
> aconnect 28:0 131:0aconnect also accepts client names so it should be possible to do it like this too:

aconnect Hydrogen:1 phasex-01
aconnect Hydrogen:1 phasex-02

(Bad examples for client names but hopefully you get the idea)

> **Pablo_F said:**
> Then you can move the script to /usr/local/sbinIt's a user specific script so it might be better to stick it in */home/yourusername/bin*. Ubuntu adds this directory to the search path when it exists (check your */home/yourusername/.profile* file).

---

### Post by Pablo_F on 2010-08-18
> aconnect also accepts client names

Better names than numbers :)

> It's a user specific script so it might be better to stick it in /home/yourusername/bin. Ubuntu adds this directory to the search path when it exists (check your /home/yourusername/.profile file)

Thanks for this correction. Much better so! I did not know this and I have moved my scripts to ~/bin. 

For a multiuser computer as it is the case discussed here, please steroff, do as Auto sugests and sorry for my misleading.

Cheers! Pablo

---

### Post by spetroff on 2010-08-18
Thanks guys, it will take me a while to get this done, but I will report back!

---

### Post by spetroff on 2010-08-19
Ack! I've inadvertently done something which kills both Zyn and JACK's connect. That is, now when I connect the Axiom to Zyn via Aconnectgui I get no sound. I can see that the MIDI signals are getting through to Zyn, because the levels respond, but neither the Axiom, nor the virtual keyboard on Zyn's beginner mode make sounds. Also, when I try to use JACK's connect, to link the Axiom with TiMidi, nothing happens there either (latent or otherwise). LMMS still works the way it used to (with an annoying latency). Incidentally, LMMS won't work when the JACK audio server is running. In any case, how can I track down whatever it is I've managed to bugger up? AFAICT, I've reset everything back to it's original state, but I must have missed something... Thanks 

Shane

---

### Post by Pablo_F on 2010-08-19
Hi Shane, 

I am not sure of what you are missing but, for starters, after starting jackd (Start button of Jack Control) and Zynaddsubfx, connect the axiom49 to Zynadd midi input in the alsa tab (these are connections in the alsa sequencer, i.e., alsa midi, and this way is equivalent to making the connections through aconnect or aconnect-gui) AND Zynadd outputs to the system playbacks in the AUDIO tab.

Cheers! Pablo

---

### Post by spetroff on 2010-08-20
Pffft... Something is really borked, when I start JACK Control (not the audio server yet), even simple MP3's won't play. Starting the audio server solves nothing. 

When I reboot, login, start Zyn, start ALSA Seq, select connect, connect the Axiom ch1 to Zyn (ch2 isn't active right now), I still only see the level displays reacting to keyboard notes, no sound. (At this point basic MP3 playback works)

If I open the JACK Control at this point, not only does MP3 playback stop, but the audio server won't start. It fails with "the playback device "hw:0" is already in use". If I shut down Zyn and ASeq, then launch JACK Control again, I can start the audio server. This may be expected behavior, but it isn't obvious (it seems plausible that the previous connections launch some other process, incompatible with JACK's audio server). 

In any case, with the JACK audio server started, the only sounds I can get out are through a microphone connected via an M-Audio Fast Track interface. However, if I now connect the Axiom as usual (start Zyn, start ASeq, connect the Axiom to Zyn), inside the JACK Control's connect display, I see an ALSA connection between the Axiom and Zyn, as well as an Audio connection between Zyn and the system playback (on 2 channels, presumably stereo). The MIDI tab also shows devices, but making connections there has no effect. In short, all of the connections seem correct, but I still can't get to where I was the other day... (yes, the volume is set above zero on the speakers, in both controls on Zyn and in sound preferences - input and output, nothing muted) Incidentally, I get the same behavior connecting the virtual MIDI Keyboard, so it seems not to be a problem with the Axiom itself.

Any help would be greatly appreciated, because now I've successfully turned my new Axiom into a boat anchor (it really is heavy!) Thanks

Shane

---

### Post by Pablo_F on 2010-08-20
I know this can be frustrating, take it easy.

> Pffft... Something is really borked, when I start JACK Control (not the audio server yet), even simple MP3's won't play. Starting the audio server solves nothing. 

Even if you can make midi connections in the alsa tab, launching Jack Control (= qjackctl) without starting the jack server is a very bad decision because in ubuntu qjackctl suspends pulseaudio (try launching qjackctl from a terminal and you will see). Therefore you lose the audio from pulseaudio while you don't have yet the jack server (=jackd) running. 

Starting the jack audio server doesn't solve that you can have audio from an app that does not behave as a jack client (unless you use some pulse-jack bridge). The default multimedia players (rhythmbox, totem...) don't work with jack out of the box. If you want a simple media player that behaves well with jack, I suggest aqualung (to install it, just use synaptic or apt-get). If you prefer rhythmbox, vlc, mplayer... almost all of them have a jack output plugin. It is easy to "jackify" them. Check this topic at linuxmusicians:

[http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

Another possible solution to listening to music while jack is up and running is the pulse-jack plugin. I have not used it but you can search the internet. 

> When I reboot, login, start Zyn, start ALSA Seq, select connect, connect the Axiom ch1 to Zyn (ch2 isn't active right now), I still only see the level displays reacting to keyboard notes, no sound. (At this point basic MP3 playback works)


So it seems that zynaddsubfx does not launch jackd in the background. What says the terminal? (just type "zynaddsubfx", without the quotes)


> If I open the JACK Control at this point, not only does MP3 playback stop, but the audio server won't start. It fails with "the playback device "hw:0" is already in use".

Because some other audio server is using it, I think.

>  If I shut down Zyn and ASeq, then launch JACK Control again, I can start the audio server.

 This is what you have to do, launch Jack Control and start the server before you try to launch any jack client.

> This may be expected behavior, but it isn't obvious (it seems plausible that the previous connections launch some other process, incompatible with JACK's audio server).

Yes it seems. If you are curious about it, check the terminal messages when you launch zynaddsubfx.

> In any case, with the JACK audio server started, the only sounds I can get out are through a microphone connected via an M-Audio Fast Track interface.

You didn't talk about your cards, did you? This is crucial. We need more info, see below.

> However, if I now connect the Axiom as usual (start Zyn, start ASeq, connect the Axiom to Zyn), inside the JACK Control's connect display, I see an ALSA connection between the Axiom and Zyn, as well as an Audio connection between Zyn and the system playback (on 2 channels, presumably stereo).

Connections are right but I doubt about the audio interface that jack is using. Again, see below. By the way, you don't need Aseq, you can make the alsa midi (devs call it alsa sequencer) connection in the alsa tab of qjackctl.

> 
The MIDI tab also shows devices, but making connections there has no effect.

This is jack midi. Some modern synths and sequencers use it. Leave it alone for now. 

> In short, all of the connections seem correct,

Yes
> 
(yes, the volume is set above zero on the speakers, in both controls on Zyn and in sound preferences - input and output, nothing muted) Incidentally, I get the same behavior connecting the virtual MIDI Keyboard, so it seems not to be a problem with the Axiom itself.

You are right.

Jack talks to the alsa driver of the selected audio card (interface field in qjackctl's setup). If not impossible afaik, it is not common using a card for capture and another one for playback.

Jack uses the generic word "system" for any card that is actually using. So you will always see system:captures (inputs) and system:playbacks (outputs. Normally 1 and 2 are the two first analog mono outputs or the first stereo pair, depending on the card). 

However, you have to double check which card is using jack, as you seem to have more than one. 

Please, give the following info:

Which card do you have connected to the speakers? Onboard, m-audio?

What is the output of the following informative command?

aplay -l

Do you need to capture from an external micro or instrument?

Please show the messages window of jack, where we can see the setup and maybe make a proposal for the better.

Cheers! Pablo

---

### Post by spetroff on 2010-08-25
> **Pablo_F said:**
> ...in ubuntu qjackctl suspends pulseaudio

So I gathered, still seems weird, but now that I know about it, I can work around it.


> The default multimedia players (rhythmbox, totem...) don't work with jack out of the box.

OK, I just assumed that they did. I'll look into aqualung since I have no particular desire to keep the defaults.

> So it seems that zynaddsubfx does not launch jackd in the background. What says the terminal? 

The terminal does output an error (isn't there a log somewhere which the gui tool uses?)

    Sound Buffer Size =   256 samples
    Internal latency =    5.8 ms
    ADsynth Oscil.Size =  1024 samples
    ERROR: Cannot make a jack client (possible reasons: 
    JACK server is not running or jackd is launched by root 
    and zynaddsubfx by another user.).
    Using OSS instead.

A quick look at *top* shows that jackd is not started by any user.


> You didn't talk about your cards, did you? ... Connections are right but I doubt about the audio interface that jack is using... Jack talks to the alsa driver of the selected audio card (interface field in qjackctl's setup). If not impossible afaik, it is not common using a card for capture and another one for playback.

OK, well there's one thing that I am doing oddly: I am using 2 'cards'. In my sound preferences, input comes from the M-Audio FastTrack, and output goes to the SB Live 5.1. I looked at the interface combo on JACK Control and it is still set to (default). I wasn't able to interpret the other values in there (hw:0, plughw:0, /dev/audio, /dev/dsp), so for the moment it is still set to (default).


> Which card do you have connected to the speakers? Onboard, m-audio?
What is the output of the following informative command?
aplay -l
Do you need to capture from an external micro or instrument?
Please show the messages window of jack, where we can see the setup and maybe make a proposal for the better.

Technically, there are 3 sound 'cards' in the system. The onboard card is disabled in the bios, so it shouldn't be a factor. The other 2 are: PCI - SB Live 5.1 and the USB M-Audio FastTrack. The speakers are currently connected to the SB and the external mic is connected to the FastTrack (sound pref: input - FastTrack, output - SB).

aplay -l: (seems weird in that there are multiple 'card 2' instances, but no 'card 1')

**** List of PLAYBACK Hardware Devices ****
card 0: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Live [SB Live! 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Live [SB Live! 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Live [SB Live! 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



and Jack Messages after starting: (does hw:0 corresponds to card0 above?)

12:59:25.733 Patchbay deactivated.
12:59:25.747 Statistics reset.
12:59:25.887 ALSA connection graph change.
12:59:26.055 ALSA connection change.
13:58:11.915 Startup script...
13:58:11.916 artsshell -q terminate
sh: artsshell: not found
13:58:12.320 Startup script terminated with exit status=32512.
13:58:12.321 JACK is starting...
13:58:12.321 /usr/bin/jackd -t1000 -m -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
13:58:12.361 JACK was started with PID=13243.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
13:58:14.419 Server configuration saved to "/home/administrator/.jackdrc".
13:58:14.421 Statistics reset.
13:58:14.424 Client activated.
13:58:14.425 JACK connection change.
13:58:14.435 JACK connection graph change.

Thanks for your help / time.

Shane

---


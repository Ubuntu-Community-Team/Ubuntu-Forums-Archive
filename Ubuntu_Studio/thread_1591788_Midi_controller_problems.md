---
title: "Midi controller problems"
date: 2010-10-09
forum: Ubuntu Studio
---

### Post by Jetstreamer on 2010-10-09
Ok so I went out and bought an M-Audio Keyrig 49. Try as I might I could not get it to work with Ubuntu. I got mad at it so then I installed Ubuntu Studio. I managed to get the keyboard to work by making a connection in "jack". I connected my keyboard with timidity, and then I made a noise! I could make noise but it was really delayed! How is this fixed? More importantly how do I use my keyboard with a program that allows different tones and such like LMMS? Any help appreciated!

---

### Post by Pablo_F on 2010-10-10
Hi!

I have the same midi keyboard. It just works, no latency for me. However, take it easy, be patient. I recommend you use the jack audio server which was specially written for low lattency audio and flexible inter-application audio routing.

So your first goal should be to have the jack server up and running. You launch Jack Control. In the setup window you choose (between other things) your audio card, this is, the "Interface". If you happen to have one only audio card, (default) should work.  So for starters, don't change anything in the setup, close the window and start the jack server with the Start button.

If jack starts the first step is done. 

Now, in the connections window you will see three tabs. Both "ALSA" and "MIDI" refer to MIDI. They are two different midi implementations. You see your keyboard in the ALSA tab.

Now you need something that has a midi input and audio outputs. Timidity can do the job but, by default, timidity is not jack-aware, so you will see it has midi inputs but noy jack audio outputs. You can "jackify" timidity or use another softsynth like qsynth.

Qsynth is a frontend for fluidsynth. You should have it in the sound and video menu, if not install it with synaptic for example. In qsynth you need to load a soundfont, configuration button, soundfonts tab. If you have installed the package "fluid-soundfont-gm" you can load FluidR3_GM.sf2 which is located in your system in /usr/share/sounds/sf2/

In the midi tab of qsynth, make sure alsa-seq is selected. In the audio tab make sure jack is selected. It is important that the sample rate in qsynth and in the jack setup is the same.

Restart qsynth and, in qjackctl, connect the keyrik49 to qsynth input in the alsa tab, and make sure that qsynth outputs are connected to system: playbacks in the audio tab.

You can choose different instruments in qsynth, channels button. 

This is just an option. I hope it helps.

Cheers! Pablo

---

### Post by Jetstreamer on 2010-10-10
I connected the keyboard to timidity using jack but jack wont start. Qsynth wont work either! Here are two screen caps to show you what I'm seeing: 
[IMG]http://imgur.com/de3Bj.png[/IMG]
[IMG]http://imgur.com/S08vq.png[/IMG]

---

### Post by Pablo_F on 2010-10-10
Hi, 

Default server already active, which means that you soundcard is being used by another server. 

I suggest the following:

Avoid that pulseaudio autospawns (comes to life after being killed). In a terminal:

**echo "autospawn = no" > ~/.pulse/client.conf**

Kill pulseaudio before starting the jack audio server:

Jack Control, Setup, Options, execute script on start up:

**pulseaudio -k**

(instead of the apparently useless "artshell -q terminate")

Execute script after shutdown:

**pulseaudio -D**

(to launch again the pulseaudio daemon when the jack daemon is stopped)

Cheers! Pablo

---

### Post by Jetstreamer on 2010-10-11
Pablo you're awesome! I t took me a while to realize my laptops speakers  won't work and that I need external speakers or headphones plugged in!

---

### Post by maghoxfr on 2010-10-12
There's also plenty of soft synths, [Yoshimi]("http://yoshimi.sourceforge.net/") and [Phasex]("http://sysex.net/phasex/") for instance, they have plenty of presets. Maybe it's easier to make the connections with patchage which is a bit more visual than Qjackctl connections window.

I remember I got some soundfonts from [HERE]("http://www.hammersound.net/") but the best ones I don't really remember where I got them, that's because I've searched very chaotically and later I lost my bookmarks on my browser. But do some research for soundfonts, sf2 files and you'll find some good ones to load on Qsynth.

[Bristol]("http://bristol.sourceforge.net") ([link]("http://sourceforge.net/projects/bristol/")) is also awesome, somehow I had to struggle a bit to make it work, but it's great.

Cheers

---

### Post by skywriter on 2010-10-20
What about other keyboards from M-Audio (such as "ProKeys" model)? Are they working well with Ubuntu?

---

### Post by AutoStatic on 2010-10-20
> **skywriter said:**
> What about other keyboards from M-Audio (such as "ProKeys" model)? Are they working well with Ubuntu?As long as they're USB 1.1. class compliant devices, yes. And the ProKeys series seem to be class compliant.

---

### Post by Jetstreamer on 2010-10-28
> **Pablo_F said:**
> Hi, 

Default server already active, which means that you soundcard is being used by another server. 

I suggest the following:

Avoid that pulseaudio autospawns (comes to life after being killed). In a terminal:

**echo "autospawn = no" > ~/.pulse/client.conf**

Kill pulseaudio before starting the jack audio server:

Jack Control, Setup, Options, execute script on start up:

**pulseaudio -k**

(instead of the apparently useless "artshell -q terminate")

Execute script after shutdown:

**pulseaudio -D**

(to launch again the pulseaudio daemon when the jack daemon is stopped)

Cheers! Pablo

Ok so I had to try the new distro so I have ended up where I began. This is the message jack gives me:
[IMG]http://imgur.com/NwOdZ.png[/IMG]

---

### Post by Pablo_F on 2010-10-29
Hi, 

What is the terminal output of:

aplay -L

?

(you don't need to attach a screenshot, just select-paste the test with left and middle buttons, respectively)

---


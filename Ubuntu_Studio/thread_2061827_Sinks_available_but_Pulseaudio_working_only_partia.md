---
title: "Sinks available but Pulseaudio working only partially - PulseAudio JACK Sink"
date: 2012-09-23
forum: Ubuntu Studio
---

### Post by jorgealfonso on 2012-09-23
Hello,

I recently made a fresh install of Ubuntu Studio. I am overall positively impressed: this release looks pretty solid (the former one was bad) and almost everything worked out-of-the-box.

One of the few things not working out of the box is Pulseaudio trough Jack. 

I've done this setup before (even by hand, some time ago when the sinks were not very well integrated yet) but this time I'm getting contradictory symptoms and I'm a bit lost... I am using QjackCtl.

Symptoms:
- The sinks are available in the Connection Panel. They connect automatically to the correspondent system playback input ports.
- Most audio applications won't output any sound (ex: VLC, youtube through web browser, xbmc) but at least they don't freeze. As soon as I stop jack, they start sounding again.
- The confusing part is that some DO WORK through the sinks, such as Audacity. If I disconnect the Pulseaudio Jack sinks (front-left and front-right) it DOES disconnect, so I am sure that the sinks and Pulseaudio are somehow working at least partially.

I look at the forums and on the internet but I couldn't find this particular case (in most posts it's just not working at all. The sinks are just not there)

Would appreciate so much if you could put me on the right track for this one!! :D

Thanks a lot!


PS: Probably an obvious note, but I'll still mention it just in case: if I try to start jack with a pulseaudio application running (say, audacity or xbmc) jack won't start and will freeze  ("hw:0 already in use" according to the log... need to kill jackdbus from the terminal). So, before starting qjackctl I have to close all the pulseaudio applications.

---

### Post by jorgealfonso on 2012-10-13
BUMP

Anyone could at least point me towards the good direction? something I could try? Thanks.

---

### Post by CrocoDuck on 2012-10-13
Hi. Basically I don't know how to help you, but try to verify if those programs (i.e. VLC) are configured to use pulsaudio (should be default) instead of directly ALSA. An easy way to do it is open the GUI pulsaudio mixer while an audio program is running and check if that program appears into the pulsaudio mixer. Of course, with JACK off.

---

### Post by jorgealfonso on 2012-12-08
CrocoDuck> You might be sending me on the right direction! All of the programs appear on the Pulseaudio Mixer, but only those that worked with Jack read "Alsa Playback" (ex: Audacious and Audacity on the attached screenshot)

So, this would mean that the pulseaudio sinks are NOT working AT ALL. The fact that some applications worked is now explained: they were simply not using pulseaudio...

Don't have a clue yet why the sinks don't work, but at least the scenario looks less confusing now! ;)

---

### Post by jorgealfonso2 on 2013-10-14
I finally found the solution! (a year later, yeah... but better late than never -_- )

The sink always worked fine, but pulseaudio was still trying to output directly to my sound card. It should output to "Jack Sink" instead.

In "normal" Ubuntu, you can change this using the default volume control application. In Ubuntu Studio, you are using xfce as windows manager, and its default volume control application does NOT allow this.

You just need to install PulseAudio Volume Control (pavucontrol) where you will be able to change the sink from sound-card to "Jack Sink" :D

[ATTACH=CONFIG]246955[/ATTACH]
[http://askubuntu.com/questions/107277/how-do-i-switch-to-another-audio-output-sink-in-xfce](http://askubuntu.com/questions/107277/how-do-i-switch-to-another-audio-output-sink-in-xfce)

---

### Post by argallguitars on 2013-11-10
I have been having a similar issue with pulse audio, jack and alsa. I have been using ubuntu studio 13.10 and have to restart my computer so that i can use my presonus audiobox on youtube for sound. Once I start ardour or hydrogen drums and then back to youtube the sound won't work unless i plug in to my computers sound card. I then tried ubuntu studio 12.04 on virtual machine and it worked without any problems switching back and forth. Maybe I could get some advice as to what to do to get this to work. I like 13.10 but am willing to switch to 12.04 if I can't resolve this. Sometimes it would work to stop jack but most of the time it doesn't. Do I need to start a new post for this?

---


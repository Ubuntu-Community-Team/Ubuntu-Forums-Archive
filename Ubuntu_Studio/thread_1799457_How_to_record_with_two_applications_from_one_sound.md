---
title: "How to record with two applications from one soundcard?"
date: 2011-07-07
forum: Ubuntu Studio
---

### Post by wrybread on 2011-07-07
I'm setting up a broadcasting and podcasting system for a community radio station, and, if possible, I'd like to be able to send our Icecast stream and record it using the same soundcard. I'm using Darkice for the Icecast, and wrote a Python script using PyAudio to record the podcasts, but sometimes (unpredictably) both can't access the soundcard simultaneously. I've been using Alsa.

So I'm wondering how best to share the soundcard?

I installed and started Jack, but I haven't been able to record from it. Here's the command I used to start it:

```
jackd -R -P4 -dalsa -r44100 -p512 -n4 -D -Chw:0 -Phw:0
```

Looking at Pulse Audio's "PulseAudio Preferences" utility I see a folder tab called "Simultaneous Output" with a checkbox to "add virtual output device for simultaneous output on all local sound cards". Would that enable multiple applications to record from my soundcard?

Any other tips?

---

### Post by Pablo_F on 2011-07-07
You can do it with jack and I think it is the most reliable option.

But you need a jack_aware recorder, such as jack_capture (a nice included gui frontend is called jack_capture_gui2) or timemachine.
Note that "man timemachine" does not tell all the options. Use "timemachine --help" instead.

You also need to make the connections between the jack clients. The audio card that jack is using is called "system". To make the connections you can use qjackctl (you can also use qjackctl to set jackd options and parameters) or patchage (more intuitive and nicer). If you need the command line, then you can use jack_connect / jack_disconnect. You want the system: playbacks connected to the recorder input. Jack_capture is cool because connects automatically whatever is connected to the system playbacks, so you literally record what you are hearing through the speakers.

It is crucial that jackd settings is OK. P4 is a too low priority, I think. Leave it default or increase it. Also, increase the timeout value, just in case. If you are using jackd2 (see "jackd --version"), I think sync mode is better. As for the audio card, if you are using the same alsa device for capture and playback, you don't need to specify them separately, but the crucial point is that you have to make sure that jack is using the right audio card.

So you could use something like:

jackd --sync -t5000 -dalsa -dhw:NAMEOFTHECARD

where NAMEOFTHECARD appears between square brackets in the output of "cat /proc/asound/cards". This is assuming that your card has a duplex alsa device, which is not always so. Take a look at the output of "aplay -l && arecord -l". 

For more reliability, kill pulseaudio before starting jackd and avoid pulseaudio autospawn. When pulseaudio is dead and jackd is up and running, the sound preferences are useless.

All of this is not very obvious, so feel free to ask again.

See also jackaudio.org FAQs
Cheers, Pablo

---


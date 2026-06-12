---
title: "Qtractor trouble"
date: 2010-09-04
forum: Ubuntu Studio
---

### Post by cchhrriiss121212 on 2010-09-04
Recently I've tried to make the switch from Ardour to Qtractor(version 0.4.6), but I'm having trouble getting started. First I'd like to know whether [this basic setup]("http://i879.photobucket.com/albums/ab352/cchhrriiss121212/qtractorblues.png") looks sane.
The problem is that nothing can be recorded. The mixer levels are showing and I can monitor OK, but when I record to a track I just get an empty track and a 0MB sound file in my chosen directory.
I've also had it crash on me a few times when attempting to record, jack shows a single xrun and a message saying "qtractor not run".

---

### Post by AutoStatic on 2010-09-04
The track doesn't seem to be armed. Did you arm the track (the little R in the track on the right) and then press the Record button and then Play? And what are you're JACK settings? I've been using 0.4.6 a while now and it's pretty rock solid here.

---

### Post by cchhrriiss121212 on 2010-09-04
Yeah the track was definitely armed, [here]("http://i879.photobucket.com/albums/ab352/cchhrriiss121212/record.png") is another shot showing it in (non recording) action.
My jack settings: /usr/bin/jackd -p128 -t2000 -dalsa -dhw:0 -r48000 -p64 -n2
                                 I'm using jack2, which may be the source of the problems, though everything else (Ardour, Hydrogen, rakarrack etc.) seems to be going fine.

I'd also like to know whether you have this on your version:
[IMG]http://i879.photobucket.com/albums/ab352/cchhrriiss121212/qtarct.png[/IMG]

Specifically the "JACK Session support disabled" part, which seems odd.

---

### Post by AutoStatic on 2010-09-04
> **cchhrriiss121212 said:**
> I'm using jack2, which may be the source of the problems, though everything else (Ardour, Hydrogen, rakarrack etc.) seems to be going fine.Qtractor should work properly with Jack2.

> **cchhrriiss121212 said:**
> I'd also like to know whether you have this on your version:

...

Specifically the "JACK Session support disabled" part, which seems odd.I'm using a SVN version, 0.4.6.4 I think. Did you compile Qtractor yourself or did you get it from a PPA? And JACK Session support being disabled is not that odd, it's just a compiler flag/dependency. If you built it yourself you could build it with JACK Session support.

But judging from your screenshot it should work. And your JACK settings look ok to me. Never tried lowering the maximum number of ports, does it do anything?

---

### Post by cchhrriiss121212 on 2010-09-04
This is all on a Debian Squeeze (posting here as I don't know any better support forums for this) machine and everything is installed from the main repo. I think I will try a newer or older version to see if it makes a difference.

Jack does not start unless the inputs/output ports are set to default. Default for some reason gives me 12 ins/outs despite the fact that a Delta 44 only has four of each (?).

---

### Post by Pablo_F on 2010-09-04
> Jack does not start unless the inputs/output ports are set to default. Default for some reason gives me 12 ins/outs despite the fact that a Delta 44 only has four of each (?). 

I have a m-audio audiophile 2496 and it is the same "no-problem". I have lots of ports even if I only have 2 ins and 2 outs. I always use 1 and 2 for capture and playback. You can use the rest of the ports, or some of them, if you do internal mixing, as TraumFlug points out.

See:

[http://www.linuxmusicians.com/viewtopic.php?f=27&t=2435&p=11278&hilit=2496](http://www.linuxmusicians.com/viewtopic.php?f=27&t=2435&p=11278&hilit=2496)

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-05
This may sound weird but did you check the directory you try to record to? Do you have enough space? Permissions? I ask this because in your first screenshot the file viewer on the left is empty, if you recorded something succesfully it should normally appear in that pane.
And did you try creating a Bass bus with only 1 channel and then record to a stereo track?

---

### Post by cchhrriiss121212 on 2010-09-05
Found the problem: I had set the capture/export file as FLAC which does not function for some reason (I have all the relevant FLAC packages installed). I have switched to WAV now and all is working as it should. Thanks for the help, Jeremy.
> 
I have a m-audio audiophile 2496 and it is the same "no-problem". I have  lots of ports even if I only have 2 ins and 2 outs. I always use 1 and 2  for capture and playback. You can use the rest of the ports, or some of  them, if you do internal mixing, as TraumFlug points out.
Ah, that makes sense, but it would be nice if I could have the option of disabling some of them. If I try and connect some of the phantom ports jack will freeze up.

---

### Post by cchhrriiss121212 on 2010-09-07
Seem to have found another small problem, perhaps some one could try and replicate it on their setup?
When using rakarrack on the Quasi Acoustic setting, the sound becomes badly detuned as soon as recording starts in Qtractor. Before hitting record it is fine, and it does not happen when recording with Ardour, so I'm guessing this is a Qtractor or jack settings problem.

---

### Post by AutoStatic on 2010-09-07
How's it all connected? And you're not using the MIDI settings by any chance in Rakarrack?

---

### Post by cchhrriiss121212 on 2010-09-07
Not using any MIDI settings in either program, my chain looks like this (can post a screenshot or an audio file of the problem if you need):
capture>rakarrack>qtractor>playback

It happened first when in the middle of a project, but I can replicate it on a new one as well. It does not seem to happen on any other rakarrack bank settings, but I have not tried them all.

Edit: the problem seems to be with rakarrack, which is taking the tempo from qtractor and applying it to the chorus effect, changing it from 21 to 122, thus the detuning effect.
But I can't seem to figure out how to turn this off, the solutions shown [here]("http://sourceforge.net/projects/rakarrack/forums/forum/778862/topic/3819378") do not work for me. The tempo is changed regardless whether the Tap Tempo feature is on, or what the input is selected as. By default it is off and has GUI as input, which is what I was using when this started.
Any ideas?

---

### Post by AutoStatic on 2010-09-07
Try setting Qtractor as the JACK slave maybe? By default it is set to Full, so if there's no master Qtractor will act as master which might be causing your issues. But I've tested it myself and I can't reproduce the issue, yeah the tempo does change when I enable MIDI and select Jack Transport there.

---

### Post by cchhrriiss121212 on 2010-09-08
Seems to be a bug for 0.5.8 according to the guy on sourceforge that is fixed in the newer git version. Slave setting had no effect, so I have jack transport set to none now which is good enough for me.

---


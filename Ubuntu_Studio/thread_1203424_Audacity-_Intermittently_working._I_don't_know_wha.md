---
title: "Audacity- Intermittently working. I don't know what I'm doing."
date: 2009-07-03
forum: Ubuntu Studio
---

### Post by Donalb on 2009-07-03
Hey all,

I want to record some Public Domain works for Librivox, which I haven't done before.
I seem to be having problems with Audacity, which I've never used.
I'm using a headset (working) on my Dell e6400 Latitude.
All I want is to record my voice and save, with occasional clipping of the start and end of tracks. 
Record & Playback setup is set to "ALSA:HDA Intel:STAC92xx Analog" which seems fine.
I recorded and saved three paragraphs/tracks ok. Then the 4th just won't record.
When I press the Rec button a new track opesn but isn't recoding anything or seems to be moving the cursor but with no input.
I haven't changed any settings. 
Restarting my laptop though will get it working again.

I had a look at Ardour, suggested elsewhere but, wtf? I couldn't figure out how to just record on it.
I also have Sound Recorder but it seems <too> simple and it also hangs when I try it so I can't use it consistently.

Thoughts?

I'm on Intrepid btw.

---

### Post by igorzwx on 2009-07-03
Perhaps, this may help:
**Getting Audacity to Record (when time stuck at 0)**
[http://ubuntuforums.org/showthread.php?t=936448](http://ubuntuforums.org/showthread.php?t=936448)

I also have a problem with Audacity, but of another sort.
Can you look at it too?

			 			[It seems to be a bug in PulseAudio]("http://ubuntuforums.org/showthread.php?t=1202857")
[http://ubuntuforums.org/showthread.php?t=1202857](http://ubuntuforums.org/showthread.php?t=1202857)

---

### Post by trulan on 2009-07-03
Ardour does require four or five clicks to record, instead of one click in Audacity.  And, you need to have Jack Control running, that's a whole different ballgame.  Audacity can record from Jack too and it might fix your intermittent problems - might be worth a shot.

But to record in Ardour:
1. Right-click the left-hand panel and select 'add track.'
2. Click the 'record' button on the track you have just created.  You should get action on the level meter on your track.  If not, you'll have to open the mixer and set the input of your track.
3. Click the main 'record' button at the top of the screen.
4. Click 'play' and you're on!  Each time you record, an audio file is created and stored in your project's directory.  You can also export part or all of your project.

If you can pretty much get it right the first time, Audacity is the way to go.  But if you need to do multiple takes, punch in, and so on, it will be worth your time learning to use Ardour.

---

### Post by igorzwx on 2009-07-04
Hi Trulan!

It does not seem to be a problem of Audacity.
Just incorrect settings.
You see, he selected "alalog" in Audacity,
but he has, perhaps, "digital" selected in Alsa Mixer.
Just this.
If he has such problems, one can imagine his troubles with Ardour.

I will try now your "howto" with Ardour, jack and OSS4,
to see if it works.

Audacity seems to work well with OSS4.
And you can also record with ossrecord, of course.

I cannot really understand why people do not use command line tools for
recording, especially those who make simple recordings.

---

### Post by igorzwx on 2009-07-04
Ardour seems to work with OSS4 too.

jackd -d oss

then run Ardour and record what you need.

If you want to try OSS4, read this first:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

Better try it on an old box, if you have one for experiments.

Ardour OSS4 howto is here:
[http://www.4front-tech.com/forum/viewtopic.php?t=3198&sid=522d1e67aa383ccb4cc324ae1eaf4914](http://www.4front-tech.com/forum/viewtopic.php?t=3198&sid=522d1e67aa383ccb4cc324ae1eaf4914)

QUOTE:
This means we need to get vmix attached to /dev/dsp.

Add the command "vmixctl attach /dev/dsp_out /dev/dsp_in" to /usr/lib/oss/soundon.user (before "exit 0" line), and run "sudo chmod +x /usr/lib/oss/soundon.user". Then run the file ("sudo /usr/lib/oss/soundon.user"). That file is run everytime OSS is started, and running vmixctl will attach vmix.

You need to either select "OSS" in "Audio setup" tab after starting Ardour, or just run "jackd -d oss" before starting Ardour.

---

### Post by Donalb on 2009-07-05
Thanks guys. Not sure what's going on now. I did 1 more system reset and Audacity seems to be fine now, though I've made no changes.
Thanks for the info on Ardour btw. I'll give it a try again.
I'm trying to do my first public domain audiobook recording and when Audacity is working it's good, though the main control layout is poor (once the Record button is pressed you have to select a different button to pause or stop.) This becomes important because when reading and recording you're not looking at the screen. I'd prefer if the record button acted like a play/pause button.

Edit: Uh...Keyboard shortcuts setup.

---


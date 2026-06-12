---
title: "Problem with Jack and PyFluidSynth"
date: 2012-09-26
forum: Ubuntu Studio
---

### Post by mandroidcoding on 2012-09-26
Hello all, first time poster here.  I've tried searching for a thread which deals with my current problem both here and in Google, but few people seem to need help with PyFluidSynth as compared to Jack, so I am starting a new thread.  If anyone knows of another thread where the answer to my question is posted, please close my thread and link me to it, and I apologize in advance for my insufficient search skills.

I am writing a thesis currently at my undergrad college and my project involves algorithmically generated music created by Python code - the technical details are not relevant to the current question I have (though I would be glad to describe my code scheme if anyone is interested), but it is important that you understand what I am trying to do.

The data structures being composed are melody instances, and each note instance stores information on its duration and frequency.  I am trying to write a piece of code which takes the information stored in these melody instances and generates something which can actually be listened to.  

In an attempt to get this working, I have been messing with PyFluidSynth.  I have not gotten past the initial testing script that they included so users could check that it is indeed working.  The script is supposed to play a chord for one second, but nothing plays when I run the script.  Here is the demo that I am talking about:

```

import sys, time, fluidsynth

try:
    open("/home/johndoe/Desktop/piano.SF2")
except:
    sys.exit("opening failed")

fs = fluidsynth.Synth()
fs.start()

sfid = fs.sfload("/home/johndoe/Desktop/piano.SF2")
fs.program_select(0, sfid, 0, 0)

fs.noteon(0, 60, 30)
fs.noteon(0, 67, 30)
fs.noteon(0, 76, 30)

time.sleep(1.0)

fs.noteoff(0, 60)
fs.noteoff(0, 67)
fs.noteoff(0, 76)

time.sleep(1.0)

fs.delete()

```If you compare this with the test file given by the creators of PyFluidSynth, you will notice that I changed the location of the sf2 file I want to use.  I also put in a check to make sure that I'm actually successfully locating the file, which I am.  The problem appears to be totally on the side of JACK.

Here is the error log which appears when I run the script:

```

Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf4800000 irq 46
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
AcquireSelfRealTime error
Cannot lock down memory area (Cannot allocate memory)
Cannot use real-time scheduling (RR/5)(1: Operation not permitted)
AcquireRealTime error
fluidsynth: Jack sample rate mismatch, adjusting. (synth.sample-rate=44100, jackd=48000)
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
JackEngine::XRun: client = fluidsynth was not run: state = 2
JackAudioDriver::ProcessGraphAsync: Process error
JackActivationCount::Signal value = 0 ref = 2
JackTemporaryException : now quits...
jack main caught signal 2


------------------
(program exited with code: 0)
Press return to continue
control device hw:0
Released audio card Audio0
audio_reservation_finish
control device hw:0

```I am using Ubuntu 11.04 - could this create some problems?  I have been putting off updating it because I'm working on my thesis and I've been worried that the latest distribution of Ubuntu will upgrade my version of Python from 2.7.1 to 3.

Other than that I have no idea what the problem could be - I am going to do more reading on the topic of JACK so that when I return to see if anyone has responded I will possibly be more able to understand what I am doing. 

One last thing which needs to be considered - the ultimate outcome of my script is a chorale instance.  A chorale is a group of four melodies, one for each of the classic voice ranges - Soprano, Alto, Tenor and Bass.  These melodies are meant to be started at the same time and played in conjunction with one another.  So for example, if the chorale is 3 measures then usually each melody is 3 measures and they would start and stop at the same times.  

It is important to note that the notes in each melody may or may not line up in a nice way - that is in the Soprano melody you may have two notes which take up the same duration as a single note in the Alto melody.  Therefore in the end, whichever module I decide to use to convert my data into sound, it needs to be able to handle the entire domain of possible combinations of notes that could be produced.  

Looking at this test file, it appears that would be hard to do, unless there are advanced ways of preparing sounds, like a list of note events that is iterated through.  I am capable of creating a method which outputs the melody's data to text files, then using another language to read those files and create the sounds, so if Python is simply incapable of doing what I need it to I can always take another approach if one exists.

Thank you in advance for any help, and I'm sorry if I'm being tl;dr.

:guitar:

---

### Post by sgx on 2012-09-27
Hi, you might want to pose your thesis at the
mailinglist:

[http://www.spinics.net/lists/linux-audio-users/](http://www.spinics.net/lists/linux-audio-users/)

and ask what would be the best language choices to
implement it. In the meantime, try to launch everything
using sudo, in case permissions are in the way.

Run the groups command, to see if you are in the audio group,

and edit text file /etc/security/limits.conf
to end it with these lines, maintaining the actual spacing in your file
which gets lost in forum output:

@audio          -       rtprio           99
@audio          -       nice             -10
@audio          -       memlock          unlimited
# End of file


Post your soundcard, and the output of commands

aplay -l and
arecord -l
cat /proc/asound/cards

Items shown within brackets, can be used in qjackctl,
on the setup page, 

Input Device >
Output Device >    click the > widget to see a list
of available soundcards. Something should resemble or
equal the text in brackets, so choose or edit that entry.
Supply a constant sound source, when testing connections.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)  Links 4 and 8 at this
wiki walk thru the jackd and qjackctl setup and connections.

The mailing list is a deep braintrust, perhaps someone knows a
csound, PD, or supercollider project aimed at algorithmic output.
Soundfont design can vary, and may effect playback. Using
fonts with multiple wav files inside, may be an extra layer
of problematica. Searching google by eliminating ranges of years,
can help speed up results, for finding old projects, or avoiding
them. 

[http://www.linuxjournal.com/article/8972](http://www.linuxjournal.com/article/8972) mentions an interesting project

[http://lists.linuxaudio.org/pipermail/linux-audio-user/2005-July/025390.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2005-July/025390.html)

[http://common-lisp.net/project/fomus/doc/](http://common-lisp.net/project/fomus/doc/)

Cheers

---


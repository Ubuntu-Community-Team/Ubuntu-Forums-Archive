---
title: "How to sequence MIDI with sfz/gig soundfonts and export a sound file?"
date: 2011-10-10
forum: Ubuntu Studio
---

### Post by hreichgott on 2011-10-10
Hello,

I recently discovered Matthias Westlund's "Sonatina Symphony Orchestra" set of samples, which are available as a sfz sound font.
I figured out how to use the sfz sound font with Linuxsampler and the Fantasia frontend for linuxsampler (using Autostatic's builds for Lucid, thanks Autostatic, if you're reading this!)
The piano sound wouldn't load in Fantasia but I found a perfectly respectable gig-format piano soundfont that works fine. I then got Rosegarden working as the sequencer and all was beautiful.

The only wrinkle is trying to export a sound file from Rosegarden. There's no easy way to do it. The two popular suggestions seem to be "use JACK to record the output of playing a file in Rosegarden" and "use Timidity instead of Rosegarden". 

Timidity is out because it can't use sfz files.

JACK would be a nice solution, but sadly, when my computer is loaded up with Fantasia running in Java, a 16-track orchestra open on the sampler, and Rosegarden cooking away, there are some undesirable pops in the sound output. Nothing I can't put up with while composing, but it isn't great for recording. I was hoping for a way to ask the computer to export a wav or flac at its own pace without pops etc.

So I am here looking for suggestions. Does anyone know either a workaround for my current Timidity and JACK obstacles, or else a suggestion for a MIDI sequencer that will handle sfz and gig soundfonts and export a sound file?

---

### Post by sgx on 2011-10-11
Hi, if rosegarden has outputs in qjackctl, you can install timemachine, start it, and connect the rosegarden outputs to the timemachine inputs that are in the qjackctl. Press the timemachine record button, then play the song in rosegarden.

timemachine default file format is .w64, which can be imported
in audacity, edited as desired, then exported in several common formats. .wav file format can also be chosen in timemachine: 

timemachine -f wav

here is a general flowchart of rosegarden sound:

[http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html](http://rosegarden.sourceforge.net/tutorial/en/chapter-2.html)

Cheers

soundfont is a specific file format, with a .sf2 extension
.gig and .sfz are different file types. Fluidsynth, and its
qsynth gui will load and play soundfonts.

There is a new project called oomidi, specifically created
to work with the Sonatina sfz file, scroll halfway down this page for
pics and info:

[http://planet.linuxaudio.org/](http://planet.linuxaudio.org/)

you will pass qtractor on the way, another popular sequencer.

---

### Post by hreichgott on 2011-10-11
Hello sgx,

Thanks for the suggestions. Oomidi looks very useful! Thanks for the tip! I'll try it out as soon as I successfully wade through compiling it and all its dependencies from source. O.o
(no, really, I am making progress... this makes me appreciate Ubuntu packager volunteers all the more)

Jack timemachine would definitely be an elegant solution, but doesn't it just capture whatever audio the soundcard is playing? I was looking for a way around the occasional pops and clicks that occur in the soundcard audio--it's ok for composing, but for recording, not so much.

Anyway, oomidi looks to be able to export audio files, so that will solve my problem completely provided it works.
thanks again

---

### Post by sgx on 2011-10-11
There is a package or two out there, thanks to the omnipresent and
diligent work of falk, and his several PPAs

[https://launchpad.net/~kxstudio-team/+archive/latest/+packages](https://launchpad.net/~kxstudio-team/+archive/latest/+packages)

KX PPAs:

[https://launchpad.net/~kxstudio-team](https://launchpad.net/~kxstudio-team)

How to add a PPA to synaptic:

[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

I used alien to make an rpm on my non-ubuntu system, you can
add add the KX-studio PPA in synaptic, and do a proper system supported install.

Compiling should work, as oomidi-2011 appears to be based on rosegarden, minus some notation and other features,
which I just discovered. (edit: oomidi is now based on Muse2 code)

For pops and clicks during recording, you can raise the qjackctl
frames/period setting. This would introduce more latency
with each increment, latency of 20, is roughly the same as sitting
20 feet away from your speakers, or guitar amp.
but not an issue on playback.

If you have a recording with a few pops, or human error,
audacity lets you zoom in and redraw the glitch into oblivion,
or just select and delete it. usb devices do best with a
qjackctl periods/buffer setting of 3.

Cheers



Cheers

---

### Post by hreichgott on 2011-10-12
Thanks again sgx for the package suggestions. I've now got oomidi up and running!

Once I successfully get a midi file created and exported to audio file, I'll come back and mark this solved.

---

### Post by sgx on 2011-10-12
:guitar::popcorn:
I wish I was that fast!

---

### Post by jejeman on 2011-10-12
> I was looking for a way around the occasional pops and clicks that occur in the soundcard audio--it's ok for composing, but for recording, not so much.

Anyway, oomidi looks to be able to export audio files, so that will solve my problem completely provided it works.
thanks againOOMidi is based on Muse.
If you have xruns you will get them when you bounce audio to file.
Only if youre jack server is runnig without xruns you will loose pops and clicks.

I use Muse 1.1, not OOMidi. Maybe they did somethnig different to audio engine, but in Muse if you get xrun you will record glitch. Eather while capturing audio or bouncing audio. Bouncing is done in realtime while playbacking the project. So, if jack gets xrun it will be written in audio file.

---

### Post by sgx on 2011-10-12
xruns often have inaudible results. While having a system free
of them is a good thing, if there is no audible effect,
lack of them is more of a status symbol, than a necessity.
I've recorded with linux for years, and never even check for the
little buggers. ;)

oomidi is indeed now based on Muse2, the codebase changed a year ago.
I'll correct my post. Here is a developer announcement:

[http://linuxmusicians.com/viewtopic.php?f=1&p=22448](http://linuxmusicians.com/viewtopic.php?f=1&p=22448)

Cheers

---

### Post by jejeman on 2011-10-12
> xruns often have inaudible results. While having a system free
of them is a good thing, if there is no audible effect,
lack of them is more of a status symbol, than a necessity.I agree with you sgx. But if they are audible, they will be recorded.

---

### Post by sgx on 2011-10-13
> **jejeman said:**
> I agree with you sgx. But if they are audible, they will be recorded.
I'm like a dog chasing its tail. And thats on my GOOD days ;)

---

### Post by hreichgott on 2011-10-15
Well, I can't get sound working on oomidi, but if it is as you say, oomidi's export wouldn't be any different from rosegarden audio recorded with jack. Will keep experimenting with rosegarden/jack. I do appreciate the help!

---

### Post by sgx on 2011-10-16
> **hreichgott said:**
> Well, I can't get sound working on oomidi, but if it is as you say, oomidi's export wouldn't be any different from rosegarden audio recorded with jack. Will keep experimenting with rosegarden/jack. I do appreciate the help!
Maybe report your efforts in this thread where the oomidid dev-team can get the info.

[http://linuxmusicians.com/viewtopic.php?f=1&t=7365](http://linuxmusicians.com/viewtopic.php?f=1&t=7365)

Cheers

---


---
title: "Recommend an audio editor..."
date: 2009-09-14
forum: Ubuntu Studio
---

### Post by bobince on 2009-09-14
...that isn't Audacity.

Yeah, Audacity always seems fine when you start off doing noddy jobs in it. But as soon as you've got anything important it starts crashing, corrupting your samples, going weird on the UI and generally making life difficult and losing work.

I've been using Audacity for years and it's always been unreliable one way or the other. I no longer hold out any hope that it will ever become stable. I've had enough. Can anyone think of a good alternative? I want:

* a simple, single-track recorder-editor like SoundForge was back before Sony had its way with it;
* quick navigation, selection and editing. Mouse wheel zoom is a must;
* non-broken undo
* simple built-in processing and LADSPA for more effects.

I don't want:

* Audacity.

Thanks.

---

### Post by ajgreeny on 2009-09-14
I am amazed that you find audacity unstable, as I've been using it for a long time also.  I use version 1.3.8-1~getdeb1 from getdeb which is a bit better than the one from the repos (1.3.7-2ubuntu1).

I use it for a number of things, but mostly recording from microphone and then editing the sound files produced as sound effects for stage purposes.  I have been able to speed things up, slow them down, lower or raise the pitch, add various echo and reverb effects, and it has never been a problem.  Perhaps your requirements are much more high tech than mine, but it may be worth trying the version I have been using to see if it is any better.
[http://www.getdeb.net/](http://www.getdeb.net/)

Ardour is also available, but I have no experience of that at all, so can't comment on it, but I believe it is a much more detailed in its abilities, and also perhaps more complicated to use.  As I say, I've not seen it in action, but give it a try, perhaps it's just what you need.

---

### Post by bobince on 2009-09-14
Yeah, I'm aware of Ardour; it's more of a big complex multi-track sequencer, where all I want is a simple single sample editor I can use to record, chop up and pre-process WAVs before taking them into the sequencer (if that step is necessary).

(Not that I don't also want a sequencer, but I didn't appreciate Ardour's interface and workflow at all. REAPER remains well ahead of any other sequencer as far as I'm concerned. QTractor was the nearest native Linux app to usable when I last tried, but it wasn't quite there yet.)

I'm not trying any more versions of Audacity. I've tried any number of versions on different platforms and they've all appeared initially good, lulled me into a false sense of security, and then lost a bunch of my work (usually in simple editing, nothing fancy). I want out of this abusive relationship!

---

### Post by kayosiii on 2009-09-15
[http://www.jackaudio.org/applications](http://www.jackaudio.org/applications)
also [http://wiki.linuxaudio.org/apps/categories/general_audio_editors](http://wiki.linuxaudio.org/apps/categories/general_audio_editors)
are probably the first places I would look.

I can't make specific reccomendations beyond that. I use Audacity - but really only for repairing damaged files (gnome wave cleaner is another good tool for doing that). My main tools are Freewheeling, hydrogen & Ardour. From the sounds of it your production requirements are quite diiferent to mine.

edit: I am just giving mhwaveedit a shot -- So far so good ... 
Mousewheel zoom [check]
single track interface [check]
built in processing and Ladspa effects [check]
can't be sure about long term stability though - but it seems like its a mature projet.

---

### Post by bobince on 2009-09-15
Thanks&#8201;—&#8201;mhwaveedit looks quite promising, seems much more pleasant to use!

The only feature I'm missing is Noise Reduction. Don't suppose there's a LADSPA plug-in I can grab for this?

---

### Post by Stochastic on 2009-09-15
I too loathe Audacity - no serious audio software should be utilizing PortAudio in my personal opinion.  Half the time it just doesn't work, and don't get me started on its interface.

When I go to edit audio, I look to Rezound.  Nice interface, with lots of minor options that other editors just don't give you, including fully configurable hotkeys.  I also really like the bright pink display of all clipped samples.

---

### Post by cooper77z on 2009-09-18
Just use openshot and make all of your tracks audio tracks. OpenShot doesn't even discriminate between audio and video. But I think Open Shot plays tracks in a hierachial order, from top to bottom. Can't say for sure, because there aren't any instructions yet. Then export the file to a control track and hooray! it works under a new project. SIMPLE

If the gain is too high, then of course one will have to discover a way to adjust it infinitely, but most of the audio presets on openshot are fine.

By the way, Mplayer doesn't work right anymore since I installed openshot, but I prefer VLC anyway. :)

---

### Post by arthursucks on 2009-09-24
The closest thing I've ever found to SoundForge in the Linux world was reZound.

[http://rezound.sourceforge.net/](http://rezound.sourceforge.net/)

It's very light, fast, and it's NOT Audacity.

:P Cheers!

---

### Post by Lars Noodén on 2009-09-24
Where you able to reproduce the bug consistently in Audacity?  If so, please pose the link to the bug report.

---

### Post by kayosiii on 2009-09-25
> **bobince said:**
> Thanks&#8201;—&#8201;mhwaveedit looks quite promising, seems much more pleasant to use!

The only feature I'm missing is Noise Reduction. Don't suppose there's a LADSPA plug-in I can grab for this?

The only too tools I know that do noise reduction are Audacity and gwc (gnome wave cleaner)...

GWC is geared towards cleanup of files recorded from old tapes or vinyl and is quite good at this sort of thing

---

### Post by bobince on 2009-09-25
> **Lars Noodén said:**
> Where you able to reproduce the bug consistently in Audacity?

No, there was no single consistent bug, just years of drip...drip...drip on both Windows and Linux. The most recent things were (on Karmic, but entirely consistent with my experience elsewhere):

- after recording a mono track from mic, just selecting and deleting a number of small sections to remove ‘erm’s and tame some plosives caused Audacity to get confused and start overwriting parts my sample with silence (zeroes)

- loaded a stereo track in from WAV, made a number of edits similar to the above, Audacity stopped responding (goes grey in Ubuntu) and could not recover the files when quit/reloaded

- UI randomly stopped paying attention to anything I clicked on, making it impossible to save/render the file

I have come to the conclusion that there's just something fundamentally wrong with Audacity. I have given up hope that it will ever be stable. And to be honest I never really liked its mode of operation, being as it is a uncomfortable halfway house between a single sample editor and a full-on sequencer.

> GWC is geared towards cleanup of files recorded from old tapes or vinyl and is quite good at this sort of thing

Thanks... this does have a sample-and-remove-noise mode. Unfortunately it doesn't seem to be nearly as effective against mic noise as Audacity's. If I turn it up enough to remove a significant amount of noise I get some nasty metallic artefacts.

---

### Post by kayosiii on 2009-09-25
I haven't done a direct comparison between GWC and audacity. GWC supports a few different algolrythms but I think the stuff in Audacity is more up to date. I remember that the last large job I used it for I over did the noise removal. then mixed the original and the noise removed version together until I got the best quality balance.

---

### Post by Cool Surfer on 2009-11-02
> **arthursucks said:**
> The closest thing I've ever found to SoundForge in the Linux world was reZound.

[http://rezound.sourceforge.net/](http://rezound.sourceforge.net/)

It's very light, fast, and it's NOT Audacity.

:P Cheers!

Thanks, I couldnt hear anything that i played in audacity, will try this one.

---


---
title: "Sibelius-like software?"
date: 2009-05-09
forum: Ubuntu Studio
---

### Post by phantomjoker on 2009-05-09
Im looking for some software similar to sibelius.

So i can *write* music and hear it back.. rather than *recording* it via midi or microphone.

anyone know of any?

cheers

---

### Post by raboofje on 2009-05-10
A nice list of notation editors is at [http://linux-sound.org/notation.html](http://linux-sound.org/notation.html)

You might like Rosegarden, Canorus or MuseScore.

---

### Post by Stochastic on 2009-05-10
I personally can't give enough praise to Lilypond (though it does have a learning curve).  And am really enjoying it's Fresobaldi editor.

Denemo is also nice.

The above mentioned link does cover most of the options.  I have also heard of people running Sibelius (which is a very robust program) in Wine with varying success.

---

### Post by kayosiii on 2009-05-11
Current state of notation editors from Linux Journal Magazine
[http://www.linuxjournal.com/content/music-notation-software-linux-progress-report-part-1](http://www.linuxjournal.com/content/music-notation-software-linux-progress-report-part-1)
[http://www.linuxjournal.com/content/music-notation-software-linux-progress-report-part-2](http://www.linuxjournal.com/content/music-notation-software-linux-progress-report-part-2)

Finale Vs Lilypond...
[http://www.musicbyandrew.ca/finale-lilypond-1.html](http://www.musicbyandrew.ca/finale-lilypond-1.html)

Hopefully the above links will help

---

### Post by phantomjoker on 2009-05-11
i'll try it out, thanks for the advice!

---

### Post by Cam42 on 2009-05-11
Try MuseScore

---

### Post by phantomjoker on 2009-05-12
can you have audio playback with musescore?

cheers

---

### Post by Musicologynut85 on 2009-05-28
Nothing available on Linux is close to being comparable to Sibelius and Finale, I played with every notation program I could get my hands on for the better part of two months. Rosegarden is close, and should work fine for basic stuff.

I eventually screwed around enough with WINE that I got Sibelius 5 working almost perfectly in it.

Good luck, and if you find something I missed, let me know.
-Jeff

---

### Post by oedipuss on 2009-05-28
> **Musicologynut85 said:**
>  Rosegarden is close, and should work fine for basic stuff.


Does it support multiple voices (or layers) in the same staff ? Last time I checked it did not, and that's kind of important even for basic stuff...

---

### Post by phantomjoker on 2009-05-28
nope, i too have tried virtually all the software and its apsolute rubbish. Wouldn't even bother. Looks like I DO need a windows partition, just for video editing and music composition. Shame really, my **only** fault with linux.

---

### Post by oedipuss on 2009-05-28
> **phantomjoker said:**
> nope, i too have tried virtually all the software and its absolute rubbish. Wouldn't even bother. Looks like I DO need a windows partition, just for video editing and music composition. Shame really, my **only** fault with linux.

Perhaps not a whole partition, just the software.
Sibelius reportedly works with wine, and so does Finale. Midi outputs might be a little cumbersome if you want to say connect finale to a vst or some other software; I find wine to be somewhat erratic with midi, but you can bypass that by using midi through as output in Finale/Sibelius etc, and connecting it to wherever you need with qjackctl. You don't even need to have a running jack server if all you need is midi redirection, just the qjackctl gui.

There's even a way to add more midi through ports, if you need different tracks to go to different software, using "modprobe snd_seq_dummy ports=4" (perhaps you'd need to unload the existing module first with modprobe -r snd_seq_dummy )

---

### Post by kayosiii on 2009-05-28
> **oedipuss said:**
> Does it support multiple voices (or layers) in the same staff ? Last time I checked it did not, and that's kind of important even for basic stuff...

The development version supports multiple voices in the one editor window, Each voice has it's own staff. The matrix editor is however layered. The next version may be a while off from an official release though (they are upgrading from QT3 to QT4).

@PhantomJoker -- Just because a piece of software is not designed to meet your needs does not make it rubbish.

---

### Post by oedipuss on 2009-05-28
> **kayosiii said:**
> The development version supports multiple voices in the one editor window, Each voice has it's own staff. The matrix editor is however layered. The next version may be a while off from an official release though (they are upgrading from QT3 to QT4).

@PhantomJoker -- Just because a piece of software is not designed to meet your needs does not make it rubbish.


That's not quite what I was talking about, unless I misunderstand what you mean. I meant multiple voices in one staff, for instance a whole C4 note and above it eights moving between G4 and C5 in the same staff. It allows for other things too, for example having a chord in which some notes have their stem in a different direction than the others.
Is that possible with the dev version ?

---

### Post by phantomjoker on 2009-05-29
Im sorry, but a lot of the software out there is rubbish. A lot doesn't work, has major faults and lacks basic functions. Unusable software is rubbish.

Most is good, and hence im using ubuntu. But some software is really really bad.

---

### Post by kayosiii on 2009-06-01
@oedipuss -- Rosegarden already sort of does what you ask... While technically correct it renders the result in a very non standard and difficult to read fashion. This is acceptable if you are just trying to produce a musical part for a recording but if you want a usable score to print as well then Rosegarden will disappoint.

I took some time to look at MuseScore (called mscore in apt-get) and it is better than I remember it being. It supports up to 4 voices per staff and comes pre set up with a reasonable soundfond and fluidsynth (less work to get up and running than RoseGarden). The only real disappointment for me at the moment is that it doesn't play back dynamics really at all. Though this seems to be on the near term todo list for the project.

---

### Post by jolx on 2009-06-01
i like musescore, but i've been tending to use sibelius in virtualbox - no need to dual boot!

---

### Post by oedipuss on 2009-06-01
> **kayosiii said:**
> 

I took some time to look at MuseScore (called mscore in apt-get) and it is better than I remember it being. It supports up to 4 voices per staff and comes pre set up with a reasonable soundfond and fluidsynth (less work to get up and running than RoseGarden). The only real disappointment for me at the moment is that it doesn't play back dynamics really at all. Though this seems to be on the near term todo list for the project.

MuseScore looks very promising, but it was very unstable for me. Maybe if it's run in a full kde environment it'd be different, I only tried it on gnome + kde dependencies..

Another one to watch would be frescobaldi, which is basically a frontend to lilypond. At the moment it lacks an easy way to playback your score, apart from converting it to midi and launching it in an external player, but that's understandable as it's something out of lilypond's scope. If they do add that feature however, it might be very useful as a sibelius/finale replacement.

---

### Post by WiDzz on 2009-06-11
[LEFT]Good morning my friends sorry English (google translator) I am a musician I have worked 10 years with musical arrangements by Sibelius with the help of a workstation Yamaha (Tyros) and windows is perfect for realism when playing scores by Sibelius is unique. (hue, expression and realism in Tyros instruments) well ... now my question to install Sibelius WINE Ubuntu 9.04 and almost perfect! but I found two problems that no one is well written document measurement example 2 / 4 appears 2 and four in the same place ... and one can not change the name of the instruments in the score. please help (may be problem of fonts) or configuration ...thaks you [email]williegrizz@hotmail.com[/email]
[/LEFT]

---

### Post by snapback77 on 2009-06-20
Thanks, I have used Finale when I was mostly Windows.  Now, that I am Ubuntu I wondered if there was a good open source.  Saved me a lot of work.

---

### Post by kayosiii on 2009-06-21
> **oedipuss said:**
> MuseScore looks very promising, but it was very unstable for me. Maybe if it's run in a full kde environment it'd be different, I only tried it on gnome + kde dependencies..

I remember the earlier versions being highly unstable as well. I am KDE based - have you tried the 0.94 version?

---

### Post by solracsuii on 2009-06-26
I have used Finale and Sibelius for some time now, i do prefer Sibelius for 1 thing: it's like photoshop u can drag, drop, move anything to almost any place u want.

I think that if u want to make a really good Music notation program u need to merge the 2 things together, take Gimp for example : great program, awesome layout and workspace, u need to put that in the skull of Rosegarden,etc.

I think that what's important here is the "how it looks" and "how much i can do to make it look nice " rather than sound fidelity and stuff, now, i don't know bout u guys but i don't care much how it sounds in the pc, as long as there's someone out there eager to play it..

cheers! :D

---

### Post by oedipuss on 2009-06-27
> **kayosiii said:**
> I remember the earlier versions being highly unstable as well. I am KDE based - have you tried the 0.94 version?

Yes, it's in the jaunty repos. Somewhat better, but it still crashed unpredictably

---

### Post by Stochastic on 2009-06-27
Why is it that people don't seem to be using Lilypond?  It's by far the most elegant notation program I've used (finale and sibelius included).  It just has a learning curve of about two years (depending on your needs).

---

### Post by kayosiii on 2009-06-28
Because people are looking for articulated playback of their scores -- If this is not an issue then I don't see a problem with using lilypond.

---

### Post by raboofje on 2009-06-28
> **kayosiii said:**
> Because people are looking for articulated playback of their scores -- If this is not an issue then I don't see a problem with using lilypond.

In fact, there has been some recent advance in that area, so we might see improvement there in the future: [http://lists.gnu.org/archive/html/lilypond-devel/2009-06/msg00008.html](http://lists.gnu.org/archive/html/lilypond-devel/2009-06/msg00008.html)

Personally, I absolutely love lilypond for engraving an already-composed/arranged piece of music, but it's not much use when still in the process of composing/arranging. For the latter, I'm mostly still sticking to pen and paper.

---

### Post by dave collin on 2009-07-02
Hi, have only recently migrated to Jaunty - one of my main requirements was a notation program or I would stick with Vista.
But - have been using Musescore on Vista for a long time and the version on ubuntu is the same. Yes - it is still a work in progress but the latest prerelease that I've got ( 9.5 revision 1898) works fine - multiple voices etc, etc, etc.
It's a great program.
Dave

---

### Post by Johann-1.0 on 2010-08-22
[[IMG]http://brainstorm.ubuntu.com/idea/25660/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/25660/)

---


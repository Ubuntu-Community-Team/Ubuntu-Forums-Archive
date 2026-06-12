---
title: "Musicians on linux"
date: 2007-03-12
forum: The Cafe
---

### Post by PatrickMay16 on 2007-03-12
I'm interested in asking musicians for their experiences with linux.

Do you use linux alone, or keep windows for some things, or do all your music work on windows and linux for everything else, or use mac and linux, or mac for all music work, or what?

What programs for music do you use on linux?


Myself, I will relate my own experience. I do not call myself a musician, but I do like to try my hand now and then at making a bit of music. 
On linux, I use a bunch of programs for making music: 
Rosegarden4, Audacity, LMMS
Timidity++, fluidsynth
opl3emu

Rosegarden is an excellent program, and I use it very much. Audacity is a good audio editor, I use that a lot. 
LMMS is a little glitchy and strange in some ways, but it's still pretty useful.
Timidity and fluidsynth are both good.

opl3emu is a small program that somebody wrote which emulates the opl2 sound chip that was on some soundblaster cards.
[http://bisqwit.iki.fi/source/opl3emu.html](http://bisqwit.iki.fi/source/opl3emu.html)

So with these programs I have been able to make some music. It's not professional quality music, but then I'm not a professional musician and I have no musical training.

---

### Post by Tomosaur on 2007-03-12
Linux really is under-estimated when it comes to music production. I have a lot more useful apps on my Linux install than I do on my windows install. I can't remember the names of a lot of them though (I have them all set up in a script, since I use them all simultaenously, for the most part), and I'm currently logged in to XP for homework, but I'll post again in a few hours to list them off :)

---

### Post by xyz on 2007-03-12
I must admit I'm still having some problems with this...but working on it!

Like with JACK; sorry if I'm totally off base/ignorant but is it true you have to be connected to internet to use it?

---

### Post by Tomosaur on 2007-03-12
> **xyz said:**
> I must admit I'm still having some problems with this...but working on it!

Like with JACK; sorry if I'm totally off base/ignorant but is it true you have to be connected to internet to use it?

Umm no, I don't think so. I've never actually tried while being offline, but I really don't think it's the case. Jack DOES initiate connections between different software / hardware etc, but I think it simply uses localhost to do this.

---

### Post by beefcurry on 2007-03-12
We dont have anything like GarageBand yet do we?

---

### Post by 23meg on 2007-03-12
> **beefcurry said:**
> We dont have anything like GarageBand yet do we?

Take a look at [Jokosher]("http://www.jokosher.org/").

---

### Post by Matt Nichols on 2007-03-12
I have had the issue with Jokosher that it crashes whenever I try to play what I have recorded...other than that it seems like a great application.

---

### Post by xyz on 2007-03-13
> **Matt Nichols said:**
> I have had the issue with Jokosher that it crashes whenever I try to play what I have recorded...other than that it seems like a great application.
Well tha't kind of a 'funny reply'. If you can't play what you've recorded, then it can't be that great of an application?
What have you been able to do with it if I may ask?

---

### Post by Matt Nichols on 2007-03-13
I was joking...sorry to be unclear. I have really not been able to do anything, and I am rather dissapointed, as it looks like it has potential to be a great app. I will eagerly anticipate the next release, hoping my bug is fixed.

---

### Post by nalmeth on 2007-03-13
LMMS is sort of considered to be a GarageBand equivalent.

As far as I'm concerned, the centerpieces to making music with GNU are JACK (qjackctl) and the JACK tools (like jack-rack, jack-eq), _**Ardour,**_ and lastly JAMin

I find the LADSPA plugins good, if totally unorganized, and lacking GUI's. Of course they aren't on par with VST plugins, but I like my system to consist of Free Software when possible, and I haven't required VST yet.

My focus is with real instruments and vocals though, for MIDI people, the school of thought is a little different. LMMS is really nice looking, and I'm learning a lot about it, but MIDI just isn't my focus. Rosegarden is what I started learning with, and it is a powerful program, but again not central to my priorities.I have had the issue with > Jokosher that it crashes whenever I try to play what I have recorded...other than that it seems like a great application.
Me too :) 
Until its more mature, I think audacity is a better solution for most people.

---

### Post by loell on 2007-03-13
i play a little, with piano .. i just wish there is a simple music notation software , like noteworthy composer.

---

### Post by shareMenaPeace on 2007-03-13
Which is the closest cubase equivalent?

Are there special programs for acid music?

---

### Post by hanzomon4 on 2007-03-14
I'm using linux for audio production after mainly using windows. I do experimental avant-garde, artsy fartsy stuff that exist somewhere between a john cage wannabe/sonic youth fanboy orgy with the kool-aid being served by the various devil musics of past generations.

Currently I'm working on a scholarship project where a lot of the focus is going to be on sound synthesis via csound5 and recorded audio. For audio I'm using Ardour.... I would love to use Joksher but my m-audio delta 66 won't record using gstreamer... only jack works.

Being that I lack mics and have chosen to restrict my use of guitars I've had to turn to sound synthesis for "new sounds". Since the school I want to go to uses csound I figured it was a good choice, although I am a sound synthesis neophyte. 

I'm not sure what pros need but I would say that linux [color=red]_**may**_[/color] be able to satisfy the needs of professionals and certainly give beginners more toys then they could ever justify paying for. However you lose the ease of use that a mac, or xp, setup provides.... The software ain't bad but getting the sound card setup may(depending on hardware) be frustrating or if you [color=orange]**_nEeD_**[/color] a patched kernel...

Ok enough rambling here's my list: 
[list][*]Csound [*]Alsa modular synth(ams)[*]Ardour[*]Hydrogen[/list]

---

### Post by silhouette on 2007-03-14
[quote="shareMenaPeace"]Which is the closest cubase equivalent?[/quote]
According to the [Rosegarden site](http://rosegardenmusic.com), it's the closest to Cubase. In some ways it's actually better -- for instance, it provides a score view, and that's nice sometimes if you want to check what you've recorded and you're accustomed to reading music. Of course last time I checked Cubase seemed to be more of a sequencer; in that case [Muse](http://www.muse-sequencer.org/) would be comparable.

If you want to work exclusively with a score view, you could probably do fine with NoteEdit. However I find note entry to be slow, even if you're using the keyboard.

Speaking of, I've found that MIDI software for Linux in general is still lacking in the area of note entry and note manipulation. It's great that I can record live in Rosegarden -- but what if I want to fade the strings out between measures X and Y? Or what if I want to repeat sustain pedal data over X and Y twice? What if I want to simulate a guitar strum? Maybe Muse can do #1 and #2, but I have to resort to using [Midge](http://www.undef.org.uk/code/midge/) (a simple text-to-MIDI program) to do #3.

And sometimes I wish I could input one note at a time by pressing the note on my keyboard and then hitting a number on the numpad like I used to do in Finale. That is still the fastest way to manually enter notes.

Anyway I suppose I should say what I use: [LilyPond](http://lilypond.org) for score editing, Jack + QSynth + soundfonts + Rosegarden for live MIDI recording, Timidity + soundfonts for rendering the output, Audacity for post-processing. I think I might also experiment with Hydrogen for drums. I haven't experimented with *actual* audio recording under Linux as I have yet to sell my Emu 0404 and get an audio card that's actually compatible, but I'd probably try out Ardour if I had such a one.

---

### Post by tgalati4 on 2007-03-14
Dynebolic works well in recording 2-hour live concerts, converting to MP3 and streaming--all on a PII, 300 MHz box with an M-Audio/envy24 sound card.  I sold 12 CD's from that concert, so I guess I could consider Linux "professional".

For composition:

There are also some nifty Linux-based keyboards.  These are music composition workstations that perform like a Yamaha Motif system at 1/2 the price.

---

### Post by skywalker___ on 2007-03-14
I use Linux to do my music and its different when other musicians see Iam useing Linux and their pc's are all messed up and freezing. ecpt some I see useing ppc..
its  very handy I use windows to look at porn this is all I see what its good for and to show my buddys porn and drink and party :guitar:

---

### Post by Fidelio on 2007-03-14
I think if I could find a way to record music on Linux I would make the switch, although I have invseted quite heavily in windows software. I have cubase, wavlab,  and 10s if not hundreds of gigs if samples in various formats which may or may not be portable. I have loads of VST fx and VSTis. I have dozens of cubase projects at the sketch stage. There's a lot of inertia keeping me on windows at the moment, and from what I've seen of Rosegarden, it doesn't really compare with cubase or sonar on the PC or logic on the mac.
At the moment I'm very new to linux. I'm just trying to set it up on my home pc. But maybe at some stage I'll try a dual boot on my DAW. Stability is obviously an issue, but so far, linux hasn't seemed particularly stable. My windows DAW has never crashed in 2 years, although individual apps occassionaly stop responding. But in my 3 days or so of using Ubuntu on my home PC, this has happened several times.
I'll be keeping an eye on developments though.

---

### Post by dracomordag on 2007-03-22
> **skywalker___ said:**
> I use Linux to do my music and its different when other musicians see Iam useing Linux and their pc's are all messed up and freezing. ecpt some I see useing ppc..
its  very handy I use windows to look at porn this is all I see what its good for and to show my buddys porn and drink and party :guitar:.

---

### Post by christhemonkey on 2007-03-22
Ardour + Jack is about all you need for recording. (and soon when the -midi branch is merged in ardour2 will be all you need for both MIDI and audio!)

There are many different ways of running VSTs under linux, from running them in wine with FST+DSSI to running them natively with something like JOST.

There are many many different and flexible synths under linux as well, from Zyn to Ams.

Hopefully the whole GUI for ladspa thing should be sorted with LV2, the replacement for ladspa (whos specification is still in draft, so is still a little way off).


Linux itself is a very stable music production platform, with several studios using it in a commerciall situation.


Hopefully when LASH becomes more advanced session restoring will be much much easier! (which can be a slight issue due to the modularity of linux audio)

---

### Post by diskotek on 2007-03-22
hydrogena is a nice drum machine
rosegarden is a quite nice squencer also
but i'm still seeking for something lke ableton live! may be i'll use it through wine hq... i'll try it soon.

[http://www.linux-sound.org](http://www.linux-sound.org) for those who are seeking for categorized softwares on linux.

by the way ubuntustudio.org is on the way... wait till april :D

---

### Post by dbbolton on 2007-03-22
every linux-using musician ought at least to play around with GNU Solfege

[http://www.solfege.org/](http://www.solfege.org/)

---

### Post by dracomordag on 2007-03-22
> **christhemonkey said:**
> Ardour + Jack is about all you need for recording. (and soon when the -midi branch is merged in ardour2 will be all you need for both MIDI and audio!)

There are many different ways of running VSTs under linux, from running them in wine with FST+DSSI to running them natively with something like JOST.

There are many many different and flexible synths under linux as well, from Zyn to Ams.

Hopefully the whole GUI for ladspa thing should be sorted with LV2, the replacement for ladspa (whos specification is still in draft, so is still a little way off).


Linux itself is a very stable music production platform, with several studios using it in a commerciall situation.


Hopefully when LASH becomes more advanced session restoring will be much much easier! (which can be a slight issue due to the modularity of linux audio)
but what about a FINALE mockup?

c'mon now... this needs to be done. tho, to be honest, i hadn't heard of rosegarden. I would've installed it over the last coupla hours, but I've spent it repartitioning and upgrading to Feisty (and at a theory/composition class (not at the same time, mind you)).

---

### Post by kenweill on 2007-03-22
My brother use Finale 2006 in Windows to write Musical Notes.
Dont know if theres an equivalent program in Linux.

---

### Post by dbbolton on 2007-03-23
lilypad ? lilypond ?

whatever it's called. ( i personally dislike it, but i think it is used to compose sheet music )

---

### Post by TBOL3 on 2007-03-23
Lillypond, as a program isn't good, but when other programs use lillypond as a library, it's ok.

---

### Post by drf_av on 2007-03-23
We're going to record our album with 64studio (or UbuntuStudio eventually, when it will come out), Ardour2 and Jamin.
And I'm sure it will sound great. If everything will go well, we'll record our album with just 230&#8364; (about 300$) for all the gear.
That's a great reason to choose linux.

---

### Post by xyz on 2007-03-23
> **drf_av said:**
> We're going to record our album with 64studio (or UbuntuStudio eventually, when it will come out), Ardour2 and Jamin.
And I'm sure it will sound great. If everything will go well, we'll record our album with just 230€ (about 300$) for all the gear.
That's a great reason to choose linux.

Wow, I'm impressed! Good luck to you all and maybe we'll even get to listen to bits of it when the time comes! :)

---

### Post by Ozor Mox on 2007-03-23
It'd be great if there was a better choice of music notation applications in Linux. Lilypond produces incredible output but is primarily an engraving tool and is very hard to actually compose in. It's more for if you have the music already written down on paper; it has a very steep learning curve.

I've tried Rosegarden. MIDI doesn't yet work. I thought this would simply be a case of downloading a synthesiser like Timidity to use with it, however it seems it's a bit more complicated than that, am I right?

Haven't tried NoteEdit, is it any good? Better or worse than Rosegarden? Also how about Denemo as a front end for Lilypond? This looks like a decent program but one that still has a lot of development to go.

It's not like it's much better on other platforms of course, unless you're happy with paying ~£500 for a huge do-it-all notation package. Far too much to justify spending on some amateur messing around! I know there are cheaper "lite" options available, but I didn't purchase any of those due to my impending switch to Linux and ending up with useless software!

Any alternatives to good old pencil and paper?

---

### Post by christhemonkey on 2007-03-23
Noteedit as was already mentioned,
[http://noteedit.berlios.de/](http://noteedit.berlios.de/)

or you could use musescore
[http://mscore.sourceforge.net/](http://mscore.sourceforge.net/)

or maybe if you like living on the edge, canorus, which is noteedits replacement.
[http://canorus.berlios.de/](http://canorus.berlios.de/)

Other possibilities also include rosegarden and muse which both can do composing via a score editor though i find the interface somewhat cumbersome.

and there is also denemo and possibly more, but i havent had any experience with them so i cannot comment!

---

### Post by IgnacioMiller on 2007-03-23
I use Windows for composing and arranging with Notepad, I find the UI more intuitive. I don't do that much of it though, I'm mostly a player. So 95% of the time I'm in Linux, listening to music and transposing in my head.:)

---

### Post by loell on 2007-03-24
notepad , do you mean noteworthy?

---

### Post by Chrisj303 on 2007-03-24
> **diskotek said:**
> hydrogena is a nice drum machine
rosegarden is a quite nice squencer also
but i'm still seeking for something lke ableton live! may be i'll use it through wine hq... i'll try it soon.

[http://www.linux-sound.org](http://www.linux-sound.org) for those who are seeking for categorized softwares on linux.

by the way ubuntustudio.org is on the way... wait till april :D

Took the words out of my mouth mate!, I use my mac pretty much only for Music production (acid techno!) Ubuntu, due to it's lack of 'proper' music apps only gets used for word processing and internet - of course i would like this change!

Ableton Live is pretty much where it's at now, it's certainly what me, and everybody i know compare new sequencers against. VST/AU plug-in compatibilty is also a MUST.
At the end of the day, i really feel that more Professional music production applications need to be made available to linux users - even if they aren't free, hell i don't mind paying for QUALITY.

---

### Post by cowlip on 2007-03-24
> **loell said:**
> notepad , do you mean noteworthy?

Noteworthy Composer actually works well in WINE, if that's what you meant.

---

### Post by loell on 2007-03-24
:-k  in older wine versions it does, i'm not sure with the newer versions

---

### Post by diskotek on 2007-04-11
> **Chrisj303 said:**
> Took the words out of my mouth mate!, I use my mac pretty much only for Music production (acid techno!) Ubuntu, due to it's lack of 'proper' music apps only gets used for word processing and internet - of course i would like this change!

Ableton Live is pretty much where it's at now, it's certainly what me, and everybody i know compare new sequencers against. VST/AU plug-in compatibilty is also a MUST.
At the end of the day, i really feel that more Professional music production applications need to be made available to linux users - even if they aren't free, hell i don't mind paying for QUALITY.

yep, i'm also using ableton live! for dj'ing with sampling etc (electro, tech house, minimal techno).. i still couldn't fine app's for it in linux yet.

but i'll try ubuntustudio when it comes up (april?)...

---

### Post by forrestcupp on 2007-04-11
> **christhemonkey said:**
> Ardour + Jack is about all you need for recording. (and soon when the -midi branch is merged in ardour2 will be all you need for both MIDI and audio!)

Sweet!  Ardour is getting midi?

+1 for Ardour.  Other than the lack of midi, it's just as good as any multi-track audio recorder I've used in Windows.  In windows, I used Logic Platinum, n-track Studio, Cubase, and Reaper.  I think Ardour is pretty much as good, especially if they are getting midi support.

+1 for ladspa.  Great audio effects that work with Ardour, Rosegarden ...

+1 for Rosegarden - great for midi.  I think it does notation, too.  to get midi working, try this link:

[http://ubuntuforums.org/showthread.php?t=8736&highlight=soundfont](http://ubuntuforums.org/showthread.php?t=8736&highlight=soundfont)

If your soundcard supports Soundfonts, definitely go that way.  Hardware is always better than software.

+1 for Hydrogen - an excellent drum editor.  It's possible to make an entire song's worth of a realistic sounding drum pattern.  And you aren't limited to their drum samples.  If you can find some you like more, you can use them in Hydrogen.  In Windows, I used a great drum editor called AlgoRhythm.  When I made a long song, it took forever to export it to a wav file.  I was surprised that in Hydrogen when I exported to a wav file it was complete almost instantaneously.

+1 for Audacity - imo, pretty crappy for multi-track - that's what Ardour is for.  But Audacity is an indispensable tool for editing a single audio file.

Then K3b is pretty good for burning the finished product to a CD.

Edit:

I do wish there was something for looping like Acid, though.  I have seen things for looping, but the beautiful thing about Acid is that all of their loop samples are programmed to a certain key, and Acid automatically makes all of the samples you load play in whatever key your song is in.  I have lots of Acid loops that I can't use now.  I've never really tried running Acid in wine, though.

---


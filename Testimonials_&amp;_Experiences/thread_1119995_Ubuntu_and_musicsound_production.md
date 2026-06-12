---
title: "Ubuntu and music/sound production"
date: 2009-04-08
forum: Testimonials &amp; Experiences
---

### Post by pafufta503 on 2009-04-08
I've had an interesting experience changing to Ubuntu.  Since I use my computer 75% of the time for sound and music tasks I thought it might be useful to share my story.  I know alot of people out there are skeptical about changing to Linux, when so many sound hardware and software companies do not supply or support Linux drivers.

Before I installed Ubuntu on my Mac Pro I was running dual-boot XP/OSX. I could restart in either OS to use certain music/sound apps, and with the help of Transmac I could exchange Wave files between OS's.  It was tedious and time consuming to boot into each OS simply to do certain tasks.  I eventually became painfully aware of my limitations and began testing Ubuntu with virtualization in OSX.

This year I switched to an Ubuntu/OSX dual-boot setup. I knew it wouldn't be easy or intuitive (it proved to be easier once I understood how to compile/build Linux software) to set-up my system for my music/sound application needs.  Some programs I used under Windows, and Darwine with OSX, I now run on Ubuntu with Wine.  Apps like MODPlug Tracker (10+ years old, but still the most versatile sequencer I've used), ReBirth 338, Hammerhead.  These programs run semi-stable, I do experience program freezes/crashes when I do certain things within the programs.  Wine has no USB support for windows apps, so Gearbox cannot communicate with my Line6 Toneport, and I cannot use the Korg software for my MicroKorg.  I am however able to output and input MIDI singles to and from my MicroKorg via an M-Audio USB-MIDI interface.

With linux apps like Jack and Patchage I can now route all audio I/O's to and from eachother.  For example, I can route any program that outputs sound through Ingen, via Patchage, to create complex effects and sound generators, recording via Audacity or Ardour.  I can even create synths in Ingen and route them into visualization software like ProjectM, where I can create a simple and constant pulse of sound in order to test ProjectM patches.

I feel like I'm only hitting the tip of the ice-berg in terms of possibilities in sound/music design in Linux. And yet, there are some drawbacks.  With my Mac Pro I face a handful of issues with Ubuntu.  Sound output from the motherboard only works from the back output.  My Line6 Toneport is not supported (which requires me to hold on to OS X for guitar recording purposes), although the new Line6-usb driver makes this very close to being possible.  Technically I could use Jack to route my guitar from a Firewire sound device through Ingen where I could create the effects myself.

I hope this gives some insight into the Linux/multimedia production universe.  If you're interested in the specifics of anything I mentioned, just ask.

- Seth

---

### Post by solwic on 2009-04-09
> **pafufta503 said:**
> I've had an interesting experience changing to Ubuntu.  Since I use my computer 75% of the time for sound and music tasks I thought it might be useful to share my story.  I know alot of people out there are skeptical about changing to Linux, when so many sound hardware and software companies do not supply or support Linux drivers.

Before I installed Ubuntu on my Mac Pro I was running dual-boot XP/OSX. I could restart in either OS to use certain music/sound apps, and with the help of Transmac I could exchange Wave files between OS's.  It was tedious and time consuming to boot into each OS simply to do certain tasks.  I eventually became painfully aware of my limitations and began testing Ubuntu with virtualization in OSX.

This year I switched to an Ubuntu/OSX dual-boot setup. I knew it wouldn't be easy or intuitive (it proved to be easier once I understood how to compile/build Linux software) to set-up my system for my music/sound application needs.  Some programs I used under Windows, and Darwine with OSX, I now run on Ubuntu with Wine.  Apps like MODPlug Tracker (10+ years old, but still the most versatile sequencer I've used), ReBirth 338, Hammerhead.  These programs run semi-stable, I do experience program freezes/crashes when I do certain things within the programs.  Wine has no USB support for windows apps, so Gearbox cannot communicate with my Line6 Toneport, and I cannot use the Korg software for my MicroKorg.  I am however able to output and input MIDI singles to and from my MicroKorg via an M-Audio USB-MIDI interface.

With linux apps like Jack and Patchage I can now route all audio I/O's to and from eachother.  For example, I can route any program that outputs sound through Ingen, via Patchage, to create complex effects and sound generators, recording via Audacity or Ardour.  I can even create synths in Ingen and route them into visualization software like ProjectM, where I can create a simple and constant pulse of sound in order to test ProjectM patches.

I feel like I'm only hitting the tip of the ice-berg in terms of possibilities in sound/music design in Linux. And yet, there are some drawbacks.  With my Mac Pro I face a handful of issues with Ubuntu.  Sound output from the motherboard only works from the back output.  My Line6 Toneport is not supported (which requires me to hold on to OS X for guitar recording purposes), although the new Line6-usb driver makes this very close to being possible.  Technically I could use Jack to route my guitar from a Firewire sound device through Ingen where I could create the effects myself.

I hope this gives some insight into the Linux/multimedia production universe.  If you're interested in the specifics of anything I mentioned, just ask.

- Seth

My only question is why would you install XP or Ubuntu if you're running a Mac?  If I had a Mac, and OS X...I don't think any other OS would be on it.  

Not criticizing, just curious.  :)

---

### Post by wolfen69 on 2009-04-09
> **jrock612 said:**
> If I had a Mac, and OS X...I don't think any other OS would be on it.  


blasphemy!

---

### Post by Tamlynmac on 2009-04-09
> wolfen69
blasphemy! 	

I think we should consider stringing him up. Or staking him to an fire ant hill.
:lolflag:

Beyond that I guess we're just doomed to tolerate him. :p

---

### Post by solwic on 2009-04-09
> **wolfen69 said:**
> blasphemy!

> **Tamlynmac said:**
> I think we should consider stringing him up. Or staking him to an fire ant hill.
:lolflag:

Beyond that I guess we're just doomed to tolerate him. :p

Gee, you all know how to make a guy feel welcome....

:biggrin:

---

### Post by Pkadjipag on 2009-04-10
In fact, I'd be interested to hear how you did it in details because I might have to record and do my music work with Ubuntu. 
I'd like to understand what you did but first, I need to get my built-in mic to work. (Not that I want to use it for professional recording but it might prove useful).

---

### Post by pafufta503 on 2009-04-10
> **Pkadjipag said:**
> In fact, I'd be interested to hear how you did it in details because I might have to record and do my music work with Ubuntu. 
I'd like to understand what you did but first, I need to get my built-in mic to work. (Not that I want to use it for professional recording but it might prove useful).

i find the apps and tools available from [http://drobilla.net/](http://drobilla.net/) (everyone should grab the full repository, especially if you use Jack) to be very useful.  for sound i use jack.  while running jack i can use an app called [U="http://drobilla.net/software/patchage/"]Patchage[/U], where i can see my midi and audio I/O's.  for sequencing i run  [U="http://lpchip.com/modplug/"]Modplug tracker[/U] in Wine.  for effects i use VST from Modplug (semi-unstable but works most of the time).  i can visually connect my sound generating applications to effects and recording applications from Patchages interface.  it's amazingly simple, as easy as connecting instrument cables.  for effects i like to use [U="http://drobilla.net/software/ingen/"]Ingen[/U].

so the whole setup flows something like this:
Sound from Audacious/Modplug/Ingen-->Jack(where i route all audio/MIDI inputs/outputs using Patchage)-->Effects(Ingen, ALSA Modular Synth)-->Recording(Audacity)/Soundcard Output

as far as what i use to compose there's many great linux apps available.  LMMS (which is great for anyone used to fruityloops, not my thing really), Rosegarden.  i just run all my old windows applications, as i've been using ModPlug Tracker for 12 years now and my workflow has become effortless and zenlike.  i can program sequences into that thing faster than i can type this sentence.  once i realized that the tracker was a skeleton of a MIDI programming interface there was no looking back.

there's a few upsides to linux on mac.  i have serious issues with firefox in osx, it crashes constantly, but in linux it runs smooth (and honestly i find faster than XP, not in terms of benchmark tests, the loading time and speed is just faster).  i can install multiple desktop environments in linux very easily, eg. i use XFCE when i'm running my full patchage/jack/ingen/audacity set-up, as GNOME eats up a bit too much CPU making things slight less stable (crashes/freezes).

that aside i've been considering installing Fink in OS X and seeing if i cannot duplicate the set-up i have in linux.  that way i could see which has a more effective workflow and which runs faster.  also using OS X means microkorg and line6 support for my synths/devices that i don't have in linux.

the downside is that i'd have to learn to install gnome/qt4/python/etc into 10.4.  it'd be alot work just trying to compile everything. the size of the OS would grow considerably after i installed enough libraries to compile linux software. it seems like it might take alot of time and research too.

---

### Post by abelbrito on 2009-11-29
> **pafufta503 said:**
> I've had an interesting experience changing to Ubuntu.  Since I use my computer 75% of the time for sound and music tasks I thought it might be useful to share my story.  I know alot of people out there are skeptical about changing to Linux, when so many sound hardware and software companies do not supply or support Linux drivers.

Before I installed Ubuntu on my Mac Pro I was running dual-boot XP/OSX. I could restart in either OS to use certain music/sound apps, and with the help of Transmac I could exchange Wave files between OS's.  It was tedious and time consuming to boot into each OS simply to do certain tasks.  I eventually became painfully aware of my limitations and began testing Ubuntu with virtualization in OSX.

This year I switched to an Ubuntu/OSX dual-boot setup. I knew it wouldn't be easy or intuitive (it proved to be easier once I understood how to compile/build Linux software) to set-up my system for my music/sound application needs.  Some programs I used under Windows, and Darwine with OSX, I now run on Ubuntu with Wine.  Apps like MODPlug Tracker (10+ years old, but still the most versatile sequencer I've used), ReBirth 338, Hammerhead.  These programs run semi-stable, I do experience program freezes/crashes when I do certain things within the programs.  Wine has no USB support for windows apps, so Gearbox cannot communicate with my Line6 Toneport, and I cannot use the Korg software for my MicroKorg.  I am however able to output and input MIDI singles to and from my MicroKorg via an M-Audio USB-MIDI interface.

With linux apps like Jack and Patchage I can now route all audio I/O's to and from eachother.  For example, I can route any program that outputs sound through Ingen, via Patchage, to create complex effects and sound generators, recording via Audacity or Ardour.  I can even create synths in Ingen and route them into visualization software like ProjectM, where I can create a simple and constant pulse of sound in order to test ProjectM patches.

I feel like I'm only hitting the tip of the ice-berg in terms of possibilities in sound/music design in Linux. And yet, there are some drawbacks.  With my Mac Pro I face a handful of issues with Ubuntu.  Sound output from the motherboard only works from the back output.  My Line6 Toneport is not supported (which requires me to hold on to OS X for guitar recording purposes), although the new Line6-usb driver makes this very close to being possible.  Technically I could use Jack to route my guitar from a Firewire sound device through Ingen where I could create the effects myself.

I hope this gives some insight into the Linux/multimedia production universe.  If you're interested in the specifics of anything I mentioned, just ask.

- Seth
so how did you get the Gearbox software to work? or do you not use it at all and go straight with Jack?

---

### Post by solwic on 2009-11-29
> **abelbrito said:**
> so how did you get the Gearbox software to work? or do you not use it at all and go straight with Jack?

Nice resurrection of a dead post.  Not that I'm against that or anything, I just always get a laugh when a mod comes along and squashes them.  :P

---

### Post by abelbrito on 2009-11-30
> **solwic said:**
> Nice resurrection of a dead post.  Not that I'm against that or anything, I just always get a laugh when a mod comes along and squashes them.  :P
ok...so how does this help me?

---

### Post by Tamlynmac on 2009-11-30
> abelbrito
ok...so how does this help me? 	

Perhaps, solwic was just sharing some words of wisdom.

If your seeking help, might I suggest using the Help Sections. As the member your requesting feedback from hasn't shown any activity on their account for 3 weeks. See their profile. I suppose, It may be possible they have another account.

Good Luck

---


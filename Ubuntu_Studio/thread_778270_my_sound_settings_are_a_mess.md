---
title: "my sound settings are a mess"
date: 2008-05-01
forum: Ubuntu Studio
---

### Post by ethanay on 2008-05-01
Hi all,

A half-hour search did not yield any threads about this, so I thought I'd give it a go:

XPS m1330 w/integrated audio running Hardy w/latest

My sound settings are a mess and I have no idea how to cleanly switch between recording w/the built-in mic and recording from internal sounds (whatever is currently playing).

I have no idea why there is an option to switch between OSS, ALSA, Pulse Audio, and my sound hardware: STAC9xxx -- it seems to be three redundant software layers and a hardware layer.  That is messy.

Next, in the mixer, I have again options to select between all these various devices.  In ALSA alone, I have 3 "capture" and 3 "mux" sliders, as well as three "input source" selections with options for "mic" and "front mic."

1) Why this overwhelming array of redundant options?  Can I uninstall OSS and/or ALSA if I have PulseAudio?
2) What is the difference between "capture" and "mux" and why are there three of each for a simple laptop system?
3) I've successfully recorded from my internal digital microphone, but have yet to figure out what is necessary to record from internal sound.

thanks,
Ethan

---

### Post by eye208 on 2008-05-02
When ALSA, which replaced the ancient OSS many years ago, had finally become a mature sound system that just worked, some developers decided they couldn't keep things that way. So they came up with the idea of putting another layer on top of ALSA and its OSS compatibility layer.

The purpose of PulseAudio is to restore the old state of total confusion regarding sound on Linux.

Yes, you can uninstall PulseAudio. All the important applications can talk to ALSA directly. ALSA also does software mixing if there is no hardware mixer available.

But hey, wouldn't that be boring? Where's the excitement when everything just works and is totally transparent? Why use only one set of mixer controls if you can have three of them at no extra charge?

---

### Post by Stochastic on 2008-05-02
Well the simple answer to most of your questions is "variety is the spice of life".


when entering the field of audio recording, there are those who want to talk to their grandson on voip/skype, and those who want to master a CD of their choir/orchestra/rock band recording; oh and EVERYONE in-between.  There CAN'T be a single button solution.


Unix/Linux kinda takes pride in the fact that there are so many versions of the systems available in nearly every aspect of the software ladder (or attempts at such).  The fact that all of these various systems exist, gives the other programmers choice of design and execution method.  Some are more robust, some are faster, some are simpler, and some are dead/dying.  

-ALSA, for example, is Ubuntu's default go-to sound driver.  That makes things do ding when you login, plays movies, etc... for most, this will suffice as their sound.
-OSS is not used by default on many (I'm not really sure about the exact accuracy of this, but I know it's general truth) or any audio apps in Ubuntu, but it's there as a legacy system that ALSA is nearly entirely compatible with (I'm no developer, just a user).  
-Jack is the server best suited for rich and hearty audio WORK with your computer.  Think of this as a really great... (insert excellent hot rod analogy car here) where the one who works with that car(d) can tune it just how they need to make it purr.
-Pulse Audio is the new guy on the block for Ubuntu, which allows communication to the same soundcard from various different other sound servers at any given time.  (i.e. Ardour can still be on, running jack, while you pause to listen to a firefox youtube video.  This wasn't possible prior, as Jack's compexity {/* developers, please read as 'robust' */} was preventing general app developers from adopting it as a output choice in their apps)  Think of it as a really crazy multi-adapter for all your sound plugs in the virtual world.

Effectively, I don't want to tell you to uninstall any apps as I'm not sure what is dependent on what for YOUR particular app list.  Though, any package-manager (software, not a person) should be able to tell you this.



As for your particular soundcard: I don't know much about internal workings of cards, and yours is a model I wouldn't remember if it was in a conversation I had tomorrow outside of this forum, but they generally should "just work" particularly if XPS means Dell.  I'd ask over in the Dell support section of this forum for further help if it doesn't. (I think the STAC9xxx number you gave is your card nuber)

Capture is one AnalogToDigital input of your card and mux would be a Multiplexer on your card (see [http://en.wikipedia.org/wiki/Multiplexer](http://en.wikipedia.org/wiki/Multiplexer)) so it's likely the switcher on your sonundcard between captures (a cost saving measure as wikipedia claims).  But I have no idea which paths your card contains for your "simple laptop system".

There's no such thing as a digital microphone.  (in the sound world anyway)

Microphones turn vibrations into analog electrical currents, a soundcard then changes those analog signals into digital representations of the original sound.  Chances are you're experiencing a low volume level setting in alsa-mixer if you've > successfully recorded from my internal digital microphone, but have yet to figure out what is necessary to record from internal sound

And now I've wasted too much of your time, as I really haven't "fixed" your problems.  But with knowledge comes understanding - and with understanding, comes a working audio chain.

---

### Post by eye208 on 2008-05-02
> **Stochastic said:**
> i.e. Ardour can still be on, running jack, while you pause to listen to a firefox youtube video.  This wasn't possible prior
This was perfectly possible in Ubuntu 7.10 without PulseAudio.

---

### Post by Stochastic on 2008-05-02
> **eye208 said:**
> This was perfectly possible in Ubuntu 7.10 without PulseAudio.

I should have specified "on the same card".  The only solution (the jack alsa plugin) wasn't well implemented or in very heavy development, from what I understood, and took some setup process to get working, just like Pulse Audio.

---

### Post by ethanay on 2008-05-02
haha.  ok, so i'm a musician, but i'm not using this for any professional recording type stuff.  i do basic sound editing via audacity, and sometimes record some music/verbal notes via mic.  i can record from the microphone OK, although i still don't know what all the settings do.  what i want to know is if i can record "what i hear" -- e.g., if i'm playing something from a streaming source, whether i can record whatever it is i'm hearing come out of the computer speakers.  have yet to find a way to do that, or even know if it's possible.

i know there isn't such a thing as a "digital microphone" -- which makes it extra confusing that the hardware and/or software is calling it one!

ok, here's what i've got under alsa mixer (questions about what they are for denoted by "?"):
playback:  master, pcm, front -- no questions there
recording: capture?, capture 1?, capture 2?, digital?, mux, mux 1, mux 2 -- although there are check boxes for all three, i can only remove capture and mux, which always leaves mux and capture 1/2 *even if unchecked* in preferences.  that is confusing.
switches:  headphone as line out, iec958?, iec958 1?, analog loopback?
options: digital input source (digital mic 1 [enables built-in mic] or analog inputs?], input source x 3 (mic or front mic; again, can only remove one)

seems pretty complicated for an integrated laptop soundcard...in fact it seems downright messy.  i've tried all sorts of settings and just am hopelessly confused right now.  there may also be some bugs at play, here...?

---

### Post by joel@parke.ods.org on 2008-05-02
Hi all,

I have just spent the past hour trying to get sound recording going on Ubuntu 8.04.  In general I love Ubuntu, but the sound stuff is such a mess I can't quite imagine.  

First I went to the volume control and found under preferences, 23 (TWENTY THREE) input sources.  Quite a few are redundant.  

Next I tried to simply record some sound using the Gnome sound recorder.  No matter what I did, I never recorded anything.  

Now I know that Skype is working and I can get sound through my mic out to my speakers, but I can't seem to record anything.  

Why is this such a mess?  Any help would be greatly appreciated.

Thanks,
Joel Parke  

PS all this started when I attempted to get some speech recognition going on my XP VirtualBox!

---

### Post by Bastaard on 2008-05-03
I myself got two soundcards - one onboard and one Audigy 2. I got regular sound working through pulseaudio, but (direct) ALSA doesn't work (progs like wine, ardour), I can't get anything to record, can't get the second output on my Audigy (for headphones) to work, can't get the onboard card to play my system sounds, etc.

I'm thinking of removing pulseaudio but I'm kind of afraid that this will mess things up further since this is pretty much the only thing that is just working, albeit just with standard apps.

Makes me kind of sad as a musician and parttime geek that I can't even figure out how to record a simple tune.

---

### Post by eye208 on 2008-05-04
> **Stochastic said:**
> I should have specified "on the same card".  The only solution (the jack alsa plugin) wasn't well implemented or in very heavy development, from what I understood, and took some setup process to get working, just like Pulse Audio.
The Jack ALSA plugin was not required. In fact it was not even included in the plugins package. All you had to do was to specify "default" as Jack's output device (instead of an "hw" hardware address). ALSA's "default" device uses the dmix plugin to implement software mixing unless the soundcard supports mixing in hardware. You can even configure it to use libsamplerate for high quality mixing. PulseAudio's mixing capability is completely redundant. In fact it seems to re-introduce problems that ALSA had solved long ago. Just take a look at the related threads in this forum. Things that worked before are now broken. How anyone can call this an improvement while keeping a straight face is beyond me.

Looking at the history of PulseAudio in Ubuntu 8.04 is like watching a train crash in slowmotion. The developers were well aware of the issues long before the release date, yet decided to ignore them. All this could have been avoided by making PulseAudio an optional component, installable from the repositories. How many users actually need networked audio? One percent?

I can see a lack of direction in the Ubuntu development process. Or maybe it's just a lack of common sense. However, mistakes like these can easily cost Ubuntu its reputation, especially when they happen with a long term support release. Like it or not, in the real world everyone expects Ubuntu LTS to be more stable, more reliable, and less experimental than the average. This is why Ubuntu 6.04 became 6.06 after all.

---

### Post by ethanay on 2008-05-04
my understanding is that pulse audio would combine low-latency audio mixing/streaming for both local and network sources and sinks.  that seems like a reasonable goal, to me.

the problem i have is that it seems we just keep layering one thing on top of another:  PulseAudio ALSA on top of OSS on top of whatever default hardware drivers exist.  It's that part which seems completely unnecessary -- I can't deal with that exponential complexity.

---

### Post by Stochastic on 2008-05-05
> **ethanay said:**
> my understanding is that pulse audio would combine low-latency audio mixing/streaming for both local and network sources and sinks.  that seems like a reasonable goal, to me.

the problem i have is that it seems we just keep layering one thing on top of another:  PulseAudio ALSA on top of OSS on top of whatever default hardware drivers exist.  It's that part which seems completely unnecessary -- I can't deal with that exponential complexity.

The default stack in Hardy should be Soundcard (hardware, no driver) -> ALSA -> PulseAudio -> Program
I'm not even sure if PulseAudio is in the chain as a default for most apps (I think so).  OSS is stuck in between PulseAudio (or ALSA if Pulse isn't there) and the outdated program that's asking to use it.  Two layers of sound server is not redundant if they serve separate purposes (as ALSA and PulseAudio do).  OSS is kinda like KDE to Ubuntu (hehe, my gnome is showing) put there as a compatability thing and for those who would rather utilize that system, for whatever reason.  In most circumstances OSS will not be used on your system unless you tell it to be used.  The hardware driver that you think exists is most likely part of the ALSA driver (they tend to have an excessive amount of detail and options in their drivers, as you've experienced with the mux issue).

Edit: I'd like to (re)state that I'm not a developer, so you can easily become just as/more informed as/than I am by reading the documentation.  Though that kinda goes against Ubuntu's utopian "it just works" ideas.

---

### Post by ethanay on 2008-05-06
where is the alsa/pulse audio documentation?

so i'm understanding that i need to set all default outputs via multimedia systems selector and sound preferences to pulse audio? what about input setup?

via alsa mixer:
i think i understand how to access the internal mic:  set "digital input source" to "digital mic 1"
and the external mic: set "digital input source" to "analog inputs"
however, i don't know how to access and record from the internal source ("what you hear") for recording.  my guess is it has to do with "analog loopback" but haven't had any luck yet.

i'm this confused and i can't believe i will soon be adding a firewire external soundcard and midi to the mix (pardon the pun)

---

### Post by unicynic on 2008-05-06
Sound in Ubuntu is not a mess. It looks like a mess because a lot of people don't use all those level of complexities. I think it would be better that the controls for all sound layers other than the main ALSA is placed in other interfaces, or at least hidden in an "Advanced" mode.

I used to work with sound before and remember that even in a 'simpler' OS you can end up with a worst mess: there's the default mixer, the legacy mixer, the legacy media control, the directx sound layer, the ASIO layer, the VST + directx layer, the MIDI layer + MIDI emulator, the sound fonts, MIDI redirector, PCM redirector/remixer ("software" sound cable), other directx versions layers, proprietary sound driver layer, the AC'97 codecs control, the Intel HDA control, the bluetooth sound control... 

I'm just listing them as I don't really understand them. I just know how to make that ASIO works so I can use some effects with my guitar and then use an audio redirector to get the resulting sound into a recording software that is put under a different effects layer with VST + directx for post processing, use the directx to play other tracks while I record a new track using PCM drivers in a multitrack (directx plays faster but recording is bad), add software drum tracks (mess with sound fonts) and MIDI accompaniments (MIDI redirector + emulator + sound fonts). Pergh.... you think sound in Ubuntu is a mess?
:guitar:

I mean, if you think sound in Ubuntu is a mess, you have never messed with sound in Windows or Mac. The only difference is that in Ubuntu, all the controls are apparent and pre-installed. In other OSes, you only get the mess after you install them yourself (or by some software that needs them). And, they are all over the place. Some have inaccessible settings that you need to mess with in the registry. Some you don't want as they mess up the other layers. It's a total mess unless you really know what you are doing.

I'd prefer a default mess. At least everything has been tested to work together and I don't have to mess with it or know much about it. It's there if someday I need a software that needs one of the layers. I don't have to hunt down a specific layer/ driver/ interface like in Windows and then try to make it work with the other layers.

Maybe Ubuntu sound people can at least put an "Advanced" option on some controls/interfaces and hide away the advanced stuff by default - much cleaner for the rest of us.

This doesn't directly fix your problem, though. But maybe if you realize that it's not a mess, then the mess will go away. :lolflag:

---

### Post by lifestream on 2008-05-09
So no one has been able to help..
I'm having the same problem as OP.
I don't care what that all  means, I already went to school for my degree and do not wish to pursue a multimedia degree. 

Could someone just explain what we need to do to be able to record what we hear? I'm no musician nor do I aspire to be. All I want to do is record my computer plays. Why is that so difficult? My buddies and I would be very happy if I could record our karaoke session.

Grr! :P

---

### Post by Stochastic on 2008-05-09
> **lifestream said:**
> So no one has been able to help..
I'm having the same problem as OP.
I don't care what that all  means, I already went to school for my degree and do not wish to pursue a multimedia degree. 

Could someone just explain what we need to do to be able to record what we hear? I'm no musician nor do I aspire to be. All I want to do is record my computer plays. Why is that so difficult? My buddies and I would be very happy if I could record our karaoke session.

Grr! :P

you're funny.:lolflag:

Not only did the original post not have anything to do with recording the output of another program, you've somehow inferred that a multimedia degree is required in order to complete said task.  Maybe if you tell us what program you'd like to record in a separate post, someone might help; rather than chirping in a rant/poll post more related to the general sound settings of ubuntu.

My first instinct is to tell you to try connecting the output of your karaoke app into the input of a recording program with the JACK server, but seeing as I have no idea of what app you're using I really have no clue if that will work.

good luck with your so-called "problem"

---

### Post by lifestream on 2008-05-09
> **Stochastic said:**
> you're funny.:lolflag:

....

good luck with your so-called "problem"

Hello. Let me refer you  back to the first post:
QUOTE:
My sound settings are a mess and I have no idea how to cleanly switch between recording w/the built-in mic and recording from internal sounds (whatever is currently playing).

QUOTE:
I've successfully recorded from my internal digital microphone, but have yet to figure out what is necessary to record from internal sound.

QUOTE (post #6)
i can record from the microphone OK, although i still don't know what all the settings do. what i want to know is if i can record "what i hear" -- e.g., if i'm playing something from a streaming source, whether i can record whatever it is i'm hearing come out of the computer speakers. have yet to find a way to do that, or even know if it's possible.

Those are exactly my questions, which haven't been answered in the thread. I'm not complaining, but I'm asking that if you or  someone  else knows what to do, to let us know, because we're obviously having problems getting this to work.

I too have spent hours trying every possible mix settings that I can think of, but I cannot record What I Hear.

Any ideas? 

~ Thanks in advance.

Edit: I think all 3 of us (the ones who asked for help) have said we are using Sound Recorder. I myself read the Help file for sound recorder, but the info is only 2 pages long (me thinks) and is very outdated.
It's indeed a problem for me and for the other 2 persons who have posted here. I was not ranting, I think!

Edit2: obviously, you (plural) don't have to help, but if you know of a solution, trust me, you're very much welcome to share it, and it's apreciated.

....
PS: The multimedia degree thing is a [joke]("http://www.answers.com/joke&r=67") (follow link and read point 4.a. )

---

### Post by lifestream on 2008-05-09
"My first instinct is to tell you to try connecting the output of your karaoke app into the input of a recording program with the JACK server, but seeing as I have no idea of what app you're using I really have no clue if that will work."

Well  for karaoke we usually go on msn or skype.
So it's not possible to record What You Hear with Alsa? Ok, atleast now I know that I can stop fiddling with the mixer bars :P

The point however, is I'd like to record any sound that's going on my desktop. Do I have to  try something very specific depending on what that is? I thought I could just have the program monitor the .... speaker sounds, and record them. 

Is that not possible? (Note, I'm not attacking anyone, I'm just asking questions, because I don't know everything :rollseyes: )

---

### Post by Stochastic on 2008-05-10
lifestream: you're right, the original poster did speak of recording internal sounds; I missed that because they were dealing with a few different issues.  I had mistakenly thought I addressed all of the OP's issues in my first response, but upon review I didn't talk about internal recording.

Essentially the only method I've ever used is through Jack's patchbay.  If you're not worried about quality, a simple analog hack of a cord from your headphone out to your mic input or line input would do the trick for anything else.  If you take a look at Pulse Audio, that may now be a solution, though I've yet to fully tinker with it so I can't guarantee anything.

---

### Post by thirdspace on 2008-05-10
I don't have a simple answer either but I have some great excuses for why it's hard to give a simple answer to your question...

It starts with the sound hardware. There are lots of different sound I/O hardware devices in use, with all sorts of differences in features, and odd limitations and quirks. The manufacturers release either no information or incomplete information about how the hardware works, only Windows and maybe Mac driver software. Somebody figures out a "driver" to let Linux use the sound hardware. If you are lucky you have sound hardware for which there is a driver that works. These days, most working drivers for current hardware are written for the ALSA framework and are considered part of ALSA. ALSA has a complex scheme (the mixer interface) by which it exposes all the control settings and features of the sound hardware that the driver writer thought someone might find useful. Alas, the driver writers never seem to write down why they thought the settings they expose might be useful, and generally no one else figures it out either. This is the source of a lot of the cryptic stuff that shows up in Linux mixers and other sound configuration user interfaces. A smart mixer GUI would hide this stuff behind a "here be Dragons" button.

ALSA also has some higher layers that have gradually evolved from being completely horrible, to a point where today as long as all you want to do is output sound through the default output path of your default device, it will probably "just work". If you try to do anything else with ALSA, your blood pressure will rise and rise until you either give up, or your head explodes. That's why JACK and PulseAudio exist, to replace the high-level parts of ALSA with something that won't make your head explode. JACK is for people who want maximum control over timing, sound quality, and routing, and are willing to put up with a little complexity in return. It works well if your (ALSA) sound card driver works well and your applications are JACK-aware. PulseAudio is supposed to make everything easy, but it's new. It's not clear yet how many of the audio problems with Ubuntu 8.04 are because of PulseAudio, and how many are because Ubuntu built their Linux kernel with the wrong scheduler option (the fix for this should be released soon).

OSS used to be a collection of sound hardware drivers, now it's just a compatibility layer that allows applications written to use the OSS drivers to work some of the time. Some people are still bitter about this.

---

### Post by ethanay on 2008-05-11
this last post is useful for understanding why it might not be possible or extremely difficult to figure out how to do something that is a simple function in a windows/mac environment.  i don't know where the bitterness and sarcasm have come from.

but i also believe that there are some bugs involved.  for instance, in alsa mixer, when i choose to hide instances of "capture" and "mux" and "input source" even if i uncheck all three, only one will disappear.  I SHOULD be able to hide all of them from the interface display.  further, it seems that some of them are completely non-functional.  i have not found any documentation to define what each function does and why there are x instances of it.  but the hardware driver issues highlighted in the above post might explain that.

---

### Post by havchr on 2008-05-11
I've installed ubuntu 8.04 , and I have no idea where I set if it should use pulseaudio or not. However, I'm wondering about this; I'm playing a song in Amarok, and if I then open up a synth program called ZynAddSubFX , the synth does not make any sound. In the synth's setting it uses "OSS wave out device" /dev/dsp  etc. Is PulseAudio ment to fix the problem I've always had where something hogs up my sound card and refuses other to use it, and should PulseAudio make every sound software mixed, so that the synth program should mix fine with music played from Amarok?

I have intel HDA laptop card.

---

### Post by ethanay on 2008-05-12
that is my understanding of one of PulseAudio's main features.

---

### Post by havchr on 2008-05-12
> **ethanay said:**
> that is my understanding of one of PulseAudio's main features.

Cool!
(except it's not working on my laptop, but the concept makes sense)

---

### Post by thirdspace on 2008-05-15
PulseAudio is the latest in a long line of "solutions" for this problem, in particular it is supposed to be a drop-in replacement for ESD, the Enlightened Sound Daemon (I'm not making this up). I'm still on Ubuntu 7.10 here, so can't comment on how well PulseAudio works in 8.04. ALSA has its own solution for this problem, called "dmix", which in recent versions just automatically works for writing audio to the default ALSA output place. But it doesn't work for other cases, like writing to an OSS compatibility pseudo-device, as in your example. I think of that as a bug in ALSA. In theory, ALSA can be configured to solve all sound device sharing and audio routing problems, but in practice, I've wasted several chunks of time trying and failing to get ALSA to do it.

I've used ZynAddSubFX myself a little, but only with JACK. It uses JACK automatically if the JACK daemon is running when ZynAddSubFX is started. I think this is the way most use ZynAddSubFX. There are other software synths that might be more suitable for your purposes, depending on what those purposes are; for example, Timidity.
:guitar:

> **havchr said:**
> I've installed ubuntu 8.04 , and I have no idea where I set if it should use pulseaudio or not. However, I'm wondering about this; I'm playing a song in Amarok, and if I then open up a synth program called ZynAddSubFX , the synth does not make any sound. In the synth's setting it uses "OSS wave out device" /dev/dsp  etc. Is PulseAudio ment to fix the problem I've always had where something hogs up my sound card and refuses other to use it, and should PulseAudio make every sound software mixed, so that the synth program should mix fine with music played from Amarok?

I have intel HDA laptop card.

---

### Post by ethanay on 2008-05-31
Just as an update, I can capture sound "what I hear" by manually routing a jackd audio single via qjackctl to JACK Time Machine (if supported).  In theory, as long as a program produces an audio data stream that supports or can be recognized by JACK, then it's possible to reproduce it.  This is still limiting, though, and I wonder what I would do in other cases (e.g., recording a web streaming interview/lecture).

The reason why my "sound settings are a mess" is there shouldn't be five billion duplicates of functions in alsa mixer that are in themselves non-functional and/or especially not working properly.

---

### Post by Stochastic on 2008-05-31
I recently started playing around more with Pulse Audio and found that Gnome Sound Recorder will record from the "mix" option, allowing for me to record the output of all Pulse Audio streams - such as a youtube video.

---

### Post by thorgal on 2008-05-31
on my PC which I use for music production with jackd running ALL the time, I sometimes had to play around with audio coming from flash videos. The solution that I find quite satisfactory in practice (but not in its design) is oss2jack. It will create a /dev/dsp which links to devices created by a daemon called fusd. Actually, it is more a kernel module (kfusd) than a daemon. It is a road that I would not advise a newbie to take as it requires compiling kernel modules, tweaking udev rules so that /dev/fusd/control and /dev/fusd/status become writable for the audio group, having the kernel module to load at boot time, not having the ALSA oss emulation on by default, and compiling oss2jack by hand. It is super tedious for non advanced users. But the result is quite practical. All OSS aware apps are fooled and jackd makes it possible to fire up ardour and dump audio from youtube videos to wav files :) You can do that with PA as well (which I did successfully) but PA was a bit unstable with jackd (made jackd crash randomly) so I gave it up.

---

### Post by ethanay on 2008-06-01
Stochastic -- hmmm, the only option i have in gnome-sound-recorder is "master" 

furthermore, it will record from my laptop internal mic quite well.  however, i can't for the life of me get Audacity to record from my internal mic!  I have two input settings: alsa: stack92xx hw:0,0 and oss: /dev/dsp

no matter what, it results in a "flatline" when I tried to record through my internal mic

pulse audio record volume meter shows sound coming through my mic, also

the "capture" slider is what controls my internal microphone, which is listed as "digital mic 1" under options

so it seems there is something wrong with audacity's access to my sound card...

---

### Post by markbuntu on 2008-06-01
I can record anything playing in my speakers with sound recorder. And play it back over it like a Fripp/Eno show. If I have the mic on in the mixer I can record that along with it or the line in.

I have got a few extra items that are not included in the distro but easily available in the repos that, after a few weeks of fooling around, have made my life a lot easier.

I have the ALSA default sound card chooser. I have sound recorder. I have the GnomeALSA mixer. It lives in the apps menu ans so is readily available and it has a mix option. I also have the alsa plugins for pulseaudio and xmms and OSS and jack. These items make my life easier.

I have set every option for sound to alsa and all the inputs and outputs of all my programs to alsa where possible.

I made a choice. I decided one thing would control the hardware and everybody would go through that to get to the hardware. I suppose you could do this with pulseaudio or xmms or oss but alsa seemed to provide the most flexibility and control and plugin wrappers for the others. Even flash plays through it while something else is also already playing. The pcm streams get mixed somehow.

Pulseaudio is a work in progress. I suppose it was included in the latest distro for the same reason that the buggy firefox 3beta was included rather than firefox2. To provide and easier path to the future for the devs.

I am sure that eventually pulseaudio will superceed alsa as it seems to have much to offer for the future but for now....

---

### Post by fcorourke on 2008-06-01
I still so no reason why anyone would think that a newer version is gong to work -- once they come out with the NEXT major update [this is after 6 months of repairing -- patching Hardy] then if you upgrade YOU CAN START OVER AGAIN to get your system working as well as it was before the update. The system is designed for people that want to spend a few hours every 3 or 4 days getting the NEW version working as well as the old version already did. No other IMPROVEMENTS in Hardy noticed --- AW I am wrong I certainly love being able to mount a couple of fixed disk in my computer without a password for each one. Sorry it took 6 months and broke everything else. Not everything -- just Fire Fox 3 [svboojonvsn] runs worse than Opera & sound & video& mouse in Fire Fox-- almost fixed except only ONE program has ANY volumne. Of course it did work out the box almost with 7.10 & simple links available to fix --- Now just discussions ON HOW NICE IT WOULD BE IF  -- if it ran out the box????

---

### Post by nothinghappens on 2009-03-07
I'm with the people saying that all these many layers and many settings are more trouble than anything.  When all you know is that it's "not working", all you can do is try different settings until something happens.  When there's 14,000 settings to try, this is an impractical feat.

I've heard so many explanations about why this isn't a "simple" problem and why there's supposedly a need for all this complexity, but all one needs to do is point out that certain *ahem* "other" operating systems, dealing with the exact same hardware, have succeeded in making audio i/o usable /long/ ago.  So it's obviously possible.

---

### Post by ethanay on 2009-12-03
I am now running 9.10 which has done a wonderful job of cleaning up the sound settings and auto-detecting audio hardware!  There is no confusing array of buttons/sliders that do not work or go away when I ask them to.  As such, I am marking this thread as "solved":cool:

---


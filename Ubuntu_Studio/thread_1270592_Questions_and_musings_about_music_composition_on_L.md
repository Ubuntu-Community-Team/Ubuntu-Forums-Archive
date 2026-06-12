---
title: "Questions and musings about music composition on Linux and Windows"
date: 2009-09-19
forum: Ubuntu Studio
---

### Post by delsydebothom on 2009-09-19
Hey all!

After a recent, failed, attempt to get Ubuntu to do everything I need it to do in terms of music production, my interest in learning about the inner workings of PC audio has peaked. While I really don't know where to begin, I hope to help improve this aspect of Linux. The amount of time it will take me to develop the ability to do so makes me suspect that someone will get to before me. After all, I don't know how to program a single line of code in any language. Regardless, if I know where to begin learning, I will apply myself to it.

I hope that among those peeking at this thread, someone will know the answer to the questions I have about the way different operating systems handle audio.

First off, how does ASIO in Windows work? The nearest I can tell, ASIO is what gives Windows the audio advantage it has over Linux with samplers, like Kontakt. That piece of software will not work with WINE--a fact that painfully prevents me from dropping Windows altogether. I'd hate to think that problems like these will remain an obstacle to Windows musicians who want to migrate to Linux. An equivalent program would be nice. LinuxSampler comes to mind.  

Yes, LinuxSampler, though it is more like GigaStudio than Kontakt, would be a helpful drop-in replacement if I could get it to work. I know that it isn't the fault of the developers that I can't. Regardless of whether or not I will eventually get it work, though, the fact is that I can install Kontakt in Windows and have it work perfectly with no modification to my system's settings. I can't do that with LinuxSampler. If I could learn to understand how software like this works, I could help fix it.

On the other hand, getting something like LinuxSampler to work in tandem with something like, say Rosegarden, would still not be the best solution. Rosegarden depends upon JACK, which has its own separate interface, and which also depends upon a great deal of configuration (on my system) to get it to run even *some* of the time. As much as I want to like and use this software, the difficulty it took to even get Rosegarden to produce a note from a Soundfont was frustrating. I want to use my computer to write music, not spend all day configuring it. I'm sure that other musicians are the same way.

The trouble I've had with Ubuntu means that, for the time being, I'm stuck with Windows. But there is an as-yet nonexistent piece of software that would make me dump Windows and never look back. This application would use an open source sample format (preferably with FLAC) that would support all the bells and whistles--multiple velocity layers, key-switching, round-robin samples, cross-faders for articulations, etc. You could insert a track, assign it a channel, select your sample from a folder, and be ready insert notes Finale-style. A piano-roll view would allow for more subtle variations. And, of course, you could record midi data directly from your external controller. 

Once you finished the part for one track, you could bounce the output to an audio track--of which you could have an unlimited number. This would allow you to delete your synth/midi track, along with the loaded sample, and save RAM in the process. You could give this audio "location" in a 7.1 surround system with simple graphical tool. All of this would be integrated into a single, seamless UI.

I could go on naming the dream features in this fantasy program, but I'd rather create it, so that I, and others, can use it. Since I can't do squat right now, I'd like some advice; drawing on what I've said here, could someone direct me towards the first step I need to take in the journey of learning *how* to do squat? Pax!

---

### Post by PrivateSNAFU on 2009-09-19
What you are proposing reminds me of LMMS [http://en.wikipedia.org/wiki/LMMS](http://en.wikipedia.org/wiki/LMMS)

By the sounds of it, you have been put off because ubuntu is not the best audio distro.  I would recommend installing ubuntu studio which has a lot of the settings already in place.
Which should mean less fiddling about with the OS.

Good luck, keep us informed of your discoveries.

Cheers 

Dan:guitar:

---

### Post by cooper77z on 2009-09-20
I don't understand, are you saying linux is limiting your creativity? Because you can do anything in linux, you can cut, splice, mix, control gain, synthesize... ad infinitum, you can even program your own distinct sound. So, I don't understand your problem at all. :guitar:

---

### Post by raboofje on 2009-09-20
> **delsydebothom said:**
> While I really don't know where to begin, I hope to help improve this aspect of Linux. I don't know how to program a single line of code in any language. Regardless, if I know where to begin learning, I will apply myself to it.

Welcome! As you say, you've got quite the journey ahead of you - but it should be a fun one :).

> First off, how does ASIO in Windows work? The nearest I can tell, ASIO is what gives Windows the audio advantage it has over Linux

Afaik ASIO is just a workaround because the default sound driver infrastructure on Windows doesn't provide sufficiently low latencies etc. for audio work. On Linux and Mac this is not needed because ALSA and CoreAudio are up to the task.

> with samplers, like Kontakt. That piece of software will not work with WINE--a fact that painfully prevents me from dropping Windows altogether. I'd hate to think that problems like these will remain an obstacle to Windows musicians who want to migrate to Linux. An equivalent program would be nice. LinuxSampler comes to mind.

Yes, LinuxSampler, though it is more like GigaStudio than Kontakt, would be a helpful drop-in replacement if I could get it to work. I know that it isn't the fault of the developers that I can't. Regardless of whether or not I will eventually get it work, though, the fact is that I can install Kontakt in Windows and have it work perfectly with no modification to my system's settings. I can't do that with LinuxSampler. If I could learn to understand how software like this works, I could help fix it.

Indeed, it would be useful to see which hurdles you encountered when trying to use LinuxSampler (or others such as Specimen), and see if anything can be done to take away these hurdles.

> Getting something like LinuxSampler to work in tandem with something like, say Rosegarden, would still not be the best solution. Rosegarden depends upon JACK, which has its own separate interface, and which also depends upon a great deal of configuration (on my system) to get it to run even *some* of the time.

Personally, I really feel that decoupling audio applications from each other and the 'connections' infrastructure is the way to go. Reducing the amount of configuration needed, of course, would be useful. Part of this would be a matter of making sure your distribution comes with better defaults (the Ubuntu Studio defaults aren't that great iirc), part of it is in better feedback about what needs to change when you run into trouble.

> there is an as-yet nonexistent piece of software that would make me dump Windows and never look back. This application would use an open source sample format (preferably with FLAC) that would support all the bells and whistles--multiple velocity layers, key-switching, round-robin samples, cross-faders for articulations, etc. You could insert a track, assign it a channel, select your sample from a folder, and be ready insert notes Finale-style. A piano-roll view would allow for more subtle variations. And, of course, you could record midi data directly from your external controller.

Once you finished the part for one track, you could bounce the output to an audio track--of which you could have an unlimited number. This would allow you to delete your synth/midi track, along with the loaded sample, and save RAM in the process. You could give this audio "location" in a 7.1 surround system with simple graphical tool. All of this would be integrated into a single, seamless UI.

Though a 'seamless UI' sounds great, as mentioned above, I'm a big believer in decoupling. This would mean you could work at one aspect of your 'dream setup' at a time, instead of having to write everything at once. If your application isn't useful until everything is finished, chances are you'll give up somewhere along the way, and the result won't be useful in its unfinished state.

So let's see which components you described:
- a component for punching in notes Finale-style
- a component for tweaking the notes pianoroll-style
- a sampler
- a component for recording the sampled output, allowing for multitracking
- a component for mixing the tracks into a 7.1 surround mix

Now let's see which applications you could use as a starting point:
- notes: denemo, rosegarden
- tweaking notes: rosegarden, seq24?
- sampler: linuxsampler, specimen
- multi-track recording: ardour, rosegarden?
- mixing the tracks into a 7.1 mix: ?

I'd recommend first getting a 'somewhat usable' setup this way. Then, you can start chipping away, taking small steps in the direction of your 'dream setup': pick a component that needs work, and replace or improve it.

You might want to check out the OpenOctave project, [www.openoctave.org](www.openoctave.org) - they're also trying to improve the composition and orchestration workflow/toolchain.

---

### Post by bobince on 2009-09-20
> **delsydebothom said:**
> The nearest I can tell, ASIO is what gives Windows the audio advantage it has over Linux with samplers, like Kontakt.

Not really, ASIO is a hack to get around the poor performance of the default Windows kernel audio mixer. Linux doesn't really need this as the normal sound subsystem is fine.

For low-latency apps you get JACK, which has is way ahead of anything available elsewhere. (The only way I could route audio between applications like I needed for my radio show on Windows was by adding extra sound cards and physically cabling them together, which is a bit sad. You can do it with VirtualAudioCable, but the latency of copying the sound streams around is terrible.)

> That piece of software will not work with WINE

Have you tried [wineasio](http://sourceforge.net/projects/wineasio/)?

> JACK, which has its own separate interface, and which also depends upon a great deal of configuration (on my system) to get it to run even *some* of the time.

It shouldn't be that hard. Run in through qjackctl, and turn off the ‘realtime’ option unless you've installed an rt kernel. (Given that the default kernel isn't rt, really having ‘realtime’ on is a really poor default IMO. You can certainly still get low latency times without the rt kernel on modern hardware.)

> I want to use my computer to write music, not spend all day configuring it. I'm sure that other musicians are the same way.

Yeah. The problem with Linux audio isn't capability, it's more than capable enough. The problem is:

1. Usability. There are too many layers to configure, it's not obvious what does what, and the defaults are often not useful for the average user. We really need *one* audio IO standard, not twenty. For this to happen, either:

a. PulseAudio needs to grow onto JACK territory, allowing arbitrary applications to be plugged together and providing a decent interface for this and other audio config jobs that are currently a pain. And also it needs to stop breaking. Or

b. JACK needs to grow onto Pulse territory, supporting multiple audio devices and providing a push-and-buffer model like (preferably the same as) ALSA.

2. lack of quality user-facing applications.

This is slowly improving, but the larger applications (eg. ardour, cinelerra) tend to bring along an annoying ecosystem and workflow with them.

---

### Post by delsydebothom on 2009-09-22
> **PrivateSNAFU said:**
> What you are proposing reminds me of LMMS [http://en.wikipedia.org/wiki/LMMS](http://en.wikipedia.org/wiki/LMMS)

By the sounds of it, you have been put off because ubuntu is not the best audio distro.  I would recommend installing ubuntu studio which has a lot of the settings already in place.
Which should mean less fiddling about with the OS.

Good luck, keep us informed of your discoveries.

Cheers 

Dan:guitar:

Hey, thanks for the reply! I'm happy to say that I've not been "put off" by Ubuntu; I love this OS! I did actually try Ubuntu Studio. Even though I got a little bit further with it, the rt kernel kept making my computer freeze. At least, I think that was the culprit. When I installed the standard variant, the freezing stopped. It wasn't a big deal, since I couldn't find any way to use my all of my .nki samples in Ubuntu Studio (which collectively I would say represent an investment of $10,000+). I depend entirely upon these libraries. It pains me that I have to use Windows to take advantage of them :(

---

### Post by delsydebothom on 2009-09-22
> **cooper77z said:**
> I don't understand, are you saying linux is limiting your creativity? Because you can do anything in linux, you can cut, splice, mix, control gain, synthesize... ad infinitum, you can even program your own distinct sound. So, I don't understand your problem at all. :guitar:

The problem isn't the capabilities of "Linux qua Linux". The problem is that I have vast libraries of sampled instruments that I cannot use in Linux. E.g., I own a license for this: [http://www.soniccouture.com/en/products/p4-the-skiddaw-stones/](http://www.soniccouture.com/en/products/p4-the-skiddaw-stones/) The license does not say I can't use the samples in Linux, nor does Linux prevent me from using them. The problem is the lack of a Linux software solution. Without a way to use this instrument, and others, in Linux, my music studio will have to remain a Windows (or Mac) machine. I love Linux, and Open Source, and the spirit of fraternal generosity that gives them life--the "ubuntu" of it all. I want to use Linux for everything. It distresses me that in this case, I can't.

---

### Post by delsydebothom on 2009-09-22
I've just downloaded the source for Rosegarden. I'm sure if I poke around the documentation long enough, I'll find out which language I need to learn in order to understand the code...then maybe I can find some classes around here!

---

### Post by raboofje on 2009-09-23
> **delsydebothom said:**
> I own a license for this: [http://www.soniccouture.com/en/products/p4-the-skiddaw-stones/](http://www.soniccouture.com/en/products/p4-the-skiddaw-stones/) The license does not say I can't use the samples in Linux, nor does Linux prevent me from using them. The problem is the lack of a Linux software solution.

In what file format is this sample library provided?

Afaik Linux can play .sf2 (though fluidsynth/qsynth) and .gig (though linuxsampler, version 2 and partially version 3).

The linuxsampler feature page ([http://www.linuxsampler.org/features.html](http://www.linuxsampler.org/features.html)) also mentions it can load, but not play, some DLS and Akai formats.

Rosegarden was written in C++, but I'm not sure whether you'll find what you're looking for there: it sounds like you're looking for a sampler (such as linuxsampler, fluidsynth, specimen), not a sequencer.

---

### Post by delsydebothom on 2009-09-23
> **raboofje said:**
> In what file format is this sample library provided?

Afaik Linux can play .sf2 (though fluidsynth/qsynth) and .gig (though linuxsampler, version 2 and partially version 3).

The linuxsampler feature page ([http://www.linuxsampler.org/features.html](http://www.linuxsampler.org/features.html)) also mentions it can load, but not play, some DLS and Akai formats.

Rosegarden was written in C++, but I'm not sure whether you'll find what you're looking for there: it sounds like you're looking for a sampler (such as linuxsampler, fluidsynth, specimen), not a sequencer.

Actually, what I would really like--and what I would think attract many musicians to Linux--is a sequencer with one or more *integrated* samplers and/or synths. Were it possible to have all the functionality of Reason *and* Rosegarden in a single Linux package, it would, for me, make Linux the only option for music production.

---

### Post by kayosiii on 2009-09-26
> **bobince said:**
> Not really, ASIO is a hack to get around the poor performance of the default Windows kernel audio mixer. Linux doesn't really need this as the normal sound subsystem is fine.

For low-latency apps you get JACK, which has is way ahead of anything available elsewhere. (The only way I could route audio between applications like I needed for my radio show on Windows was by adding extra sound cards and physically cabling them together, which is a bit sad. You can do it with VirtualAudioCable, but the latency of copying the sound streams around is terrible.)

that is partly true - though Linux's normal sound system has it's own share of troubles. Rewire is a fairly close analog for jack on windows.
You can see how jack compares to other sound systems here...
[http://www.jackaudio.org/faq](http://www.jackaudio.org/faq)

> **bobince said:**
> It shouldn't be that hard. Run in through qjackctl, and turn off the ‘realtime’ option unless you've installed an rt kernel. (Given that the default kernel isn't rt, really having ‘realtime’ on is a really poor default IMO. You can certainly still get low latency times without the rt kernel on modern hardware.)

Actually the realtime option has nothing to with having a realtime kernel. This is a common misconception and I give you quite confusing. What the realtime option does is allow jack and other audio applications to use more resources than is usually deemed safe. It requires you to configure an exception to the system security to allow audio programs to get first priority for resources. Basically Jack Control (qjackctl) ships broken on Ubuntu systems and this really shouldn't happen.

> 
1. Usability. There are too many layers to configure, it's not obvious what does what, and the defaults are often not useful for the average user. We really need *one* audio IO standard, not twenty. For this to happen, either:

a. PulseAudio needs to grow onto JACK territory, allowing arbitrary applications to be plugged together and providing a decent interface for this and other audio config jobs that are currently a pain. And also it needs to stop breaking. Or

b. JACK needs to grow onto Pulse territory, supporting multiple audio devices and providing a push-and-buffer model like (preferably the same as) ALSA. 

If you are doing Pro audio on linux the answer at the moment is quite simple. Use Jack and piss everything else off. At the moment I am forced to do this since I have a firewire based card but truth is it makes everything a lot simpler.... Since Xine supports jack really well (another thing that is broken out of the box on Ubuntu)... and KDE can run on top of xine.. there really isn't a lot I am missing out on (other than in browser flash - which gets free run on my onboard soundcard.
Jack2 - (which hasn't yet made it into distro land)... supports multiple souncards but I think that the push/pull model would not work overly well with chaining applications together. 

2. lack of quality user-facing applications.
> 
This is slowly improving, but the larger applications (eg. ardour, cinelerra) tend to bring along an annoying ecosystem and workflow with them.

I sort of agree with this and I sort of do not. I admit it took me years to "get" Audio on Linux and I don't think it is there yet.
But the basic premise is that instead of working in one big monolithic app you work in lots of smaller specialised tools audio midi and control data can be routed between them. It is hard to recommend this workflow over what people from other platforms are used to until all the infrastructure is in place and currently this is not the case. There are a lot of improvements in the works which I am eager to test.

---

### Post by bobince on 2009-09-27
> **kayosiii said:**
> Rewire is a fairly close analog for jack on windows.

Ah yeah, I'd forgotten about that. App support is very poor though! I certainly wouldn't be able to connect the range of things I need with it. (DJ app, browser audio, VoIP...)

> What the realtime option does is allow jack and other audio applications to use more resources than is usually deemed safe.

Thanks for the clarification. I think it's the jack defaults in general that are wrong rather than just qjackctl isn't it? Certainly before I configured realtime off in qjackctl starting any other JACK application (that tried to start jackd) would fail.

> If you are doing Pro audio on linux the answer at the moment is quite simple. Use Jack and piss everything else off.

Sure. I'd love to be able to do that, but for everyday desktop use (normal browsers, media players and other things that make noises) it's not quite there yet. You can hack around it with the alsa jack plugin, but it's not so easy to get working (esp under Ubuntu who deliberately exclude it, bah).

>  Jack2 - (which hasn't yet made it into distro land)... supports multiple souncards but I think that the push/pull model would not work overly well with chaining applications together.

I look forward to that then. Hopefully it will work better than using alsa_in/out to route soundcards, which seems quite broken at the moment.

I think the push+mix+resample model is necessary to get buy-in from applications, as rewriting to support JACK-style pull isn't very attractive. For applications that don't greatly care about having the best possible latency it should be fine. Realistically, like Pulse, it would have to support the ALSA interface to get broad support.

However&#8201;—&#8201;realistically&#8201;—&#8201;I don't think distros are very keen to migrate to another sound server after all the pain we've already gone through with Pulse. Which is a shame, because if we're going to have a sound server running all the time it might as well be one that provides something really useful. (Oh woohoo Pulse, ‘network transparency’, great. For the two people in the world that use it.)

> But the basic premise is that instead of working in one big monolithic app you work in lots of smaller specialised tools audio midi and control data can be routed between them.

Yes, I would love to work like that. The problem is that IMO this isn't here yet. Cinelerra, Ardour and Blender are all of the ‘huge monolithic app that controls your workflow’ variety.

---

### Post by kayosiii on 2009-09-27
> **bobince said:**
> Ah yeah, I'd forgotten about that. App support is very poor though! I certainly wouldn't be able to connect the range of things I need with it. (DJ app, browser audio, VoIP...)
 

You need to pay the makers a big fat licensing fee... there may be other stupid restrictions as well.


> **bobince said:**
> Thanks for the clarification. I think it's the jack defaults in general that are wrong rather than just qjackctl isn't it? Certainly before I configured realtime off in qjackctl starting any other JACK application (that tried to start jackd) would fail.

the default for jack (that is if you start it from the command line is to start it without realtime privileges.... What happens is that jack control writes out a configuration file that other applications use for starting jack (this is quite good most of the time). What it seems like to me is that none of the packaging team actually use jack and so it isn't tested - or perhaps it is configured for ubuntu studio and broken out of the box for regular ubuntu.

> **bobince said:**
> Sure. I'd love to be able to do that, but for everyday desktop use (normal browsers, media players and other things that make noises) it's not quite there yet. You can hack around it with the alsa jack plugin, but it's not so easy to get working (esp under Ubuntu who deliberately exclude it, bah).

The problem here largely I hate to say it is Ubuntu... They have a policy of not compiling applications in their main repository to require libraries in the universe repository which is fair enough. However jack is in the universe repository and though some of us have been asking for years now - [I just checked in launchpad - and there looks like it finally might happen]. 

Currently I have to recompile libxine with jack support. Once this is done amarok (which I use for listening to music) xine which I use for watching movies (or any xine based movie player) or any kde application that produces sound will just use jack. The only problem I have is with in browser sound - with that I either download the file or (say if I want to look at something on youtube. play the flv file directly from /tmp in xine or similar movie player (this also gets around the performance issues that flash generally has).


> **bobince said:**
> I think the push+mix+resample model is necessary to get buy-in from applications, as rewriting to support JACK-style pull isn't very attractive. For applications that don't greatly care about having the best possible latency it should be fine. Realistically, like Pulse, it would have to support the ALSA interface to get broad support.


Basically KDE already has 100% buy in on jack thanks to the magic of phonon and libxine. I can even set which soundcards or sound server a particular class of application will use. So I can have communications apps use onboard soundcard and my music apps use the external soundard.
If I happen to not have my external soundcard plugged in my music app will look for the next best option.
I don't know what the situation is like in the gnome world except they seem to be a lot more forced into PA and gstreamer. 

> However&#8201;—&#8201;realistically&#8201;—&#8201;I don't think distros are very keen to migrate to another sound server after all the pain we've already gone through with Pulse. Which is a shame, because if we're going to have a sound server running all the time it might as well be one that provides something really useful. (Oh woohoo Pulse, ‘network transparency’, great. For the two people in the world that use it.)
I don't think the distro's need to migrate as such. In KDE to run on Jack all I need to do is open up the sound configuration panel choose the class of app and then move jackd to the top of the list of prefered sound devices. I need to configure xine seperately - since I prefer it to any of the other xine based players.

> Yes, I would love to work like that. The problem is that IMO this isn't here yet. 
I agree that it isn't there yet. But the linux audio developer community is much more focused on producing a better working modular sound system then large monolithic apps that don't suck.

There are a couple of developments currently in the works that have me particularly interested. jack2 is on the way (which should eventually support multiple soundcards, netjacks functionality...  There will be an option to run jackd via dbus so applications can start it transparently should they need it).
Also the next generation of LASH called LADI is under early testing this will give some audio session management capabilities to applications that don't explicitly support it. So being able to save the state of several apps then recall it at a later date should be something that will actully work. 

> Cinelerra, Ardour and Blender are all of the ‘huge monolithic app that controls your workflow’ variety.

Cinelerra definitely - we do need something like jack for video, Its not too bad if you are familiar with 3 point video editing. Most people don't seem to be. Import/Export also sucks..

Blender yes, Well not huge...

Ardour no - Ardour is at the centre of a software ecosystem... jack was conceived by the creators of Ardour. 

Want to use meters that are not in Ardour, Simple load up a jack based meter and attach it to the input or output you are interested in measuring. Want to use Ardour with a drum machine, load up a jack based drum machine and set the two to synchronise playback. Want to syncrhonise ardour to a video source, load up a jack based video player and synchronise playback. [interestingly Blender is just getting the beginnnings of jack support].  None of the effects are built in - they are all reusable in other applications.

Ardour was designed from the beginning to be part of a modular system of sound applications that can all work together.

---

### Post by jago25_98 on 2009-09-30
It's easy to compare a Windows setup with linux and feel disheartened, however, if you compare freely available linux with a fully warez Windows studio we're not comparing like with like. 

I believe the vast majority of musicians use copied software on Windows, only later upgrading to ligitimate software if they become successful. Since most muscians don't do it professionally most musicians, I believe, are using copied software. All of this software for Windows cost thousands and thousands of pounds to buy. There is so much software available, in fact, that I don't think there is a studio in the world that can afford it all. Just think of all those VSTi running at upto a grand each. 

This setup is of course, vastly better *to use* than linux, but it's not legal, and it's easy to forget this. And, of course, because we don't have the source code you can pay for all this software and then find it's incompatible with hardware in 30 years time and all those other problems that come with this situation. (I have linux games here that don't work with the glibc I'm now using...)

I'm blown away by the music software now available on linux. I can remember being impressed simply with freebirth a few years ago and that looks very dated now. Sections of UbuntuStudio are very useable for what they are already. I've just tried LMMS and understood it straight away. Same with Hydrogen. Of course, the VST licensing lock out from Steinberg is a pain in the neck but that doesn't always have to be a problem. 
By all means have a separate computer for linux and a separate computer for Windows. 

I already see great applications on linux to be used standalone:
Sooperlooper for example (search sooperlooper youtube, freewheeling is nice too), or the various effects and instruments available. 

Many of the problems should be fixed with UbuntuStudio. By all means dual boot it. I hope this will soon be ready to use staight after install, with great big arrows and easy usability. 
Certainly UbuntuStudio combined with having a separate computer for Windows you can overcome any of the problems we currently have. 

With music I started off on the Amiga with trackers. I then learnt guitar and found that easier to make music with then trackers back then. Since then I've played with Windows software and discovered linux. Right now it's been a while since I've used computers for music and I've lost all my music software. When I think back do I really want to install all those ASIO drivers and bloat my Windows install (which I like to keep clean for work) with music software? 
 This time I'm going with linux, even if it takes more work to begin with. It's the same with everything; takes a bit more work to learn but ulimately much more rewarding.

---

### Post by JC Cheloven on 2009-09-30
I'm an amateur musician and composer, and a firm advocate of free software, but I didn't manage to do my music stuff in musix, ubuntu studio or mandriva. I'm tied to windows because of this. I would eagerly switch to 100% ubuntu if I could get the functionality of an app half as usable as sibelius, and another app half as usable as audition. I could even afford to lack a half-a-replacement for sonar. But I've been unable to find either of these.

That said, there are some promising apps. Some of them have not been mentioned in this thread, and the OP may be interested:

- Musescore is a software notation program. It could be (barely) enough for me if everything worked. But it hangs too often, at least in my boxes. Worth to check out.
- Lilypond may be used as standalone for music notation, but with no easy sound included. Nted is more stable than musescore, but less featured.
- Traverso is a nice digital audio worstation (DAW) software. I'm in love with its user interface, which mixes gestures of mouse and keyboard. Could be very handy, specialy for on-the-field recordings with a laptop. 
[INDENT]---> But there are major problems. The main one is sound in linux itself. It may become really hard to simply get the micro of your laptop (or soundcard) working. Let alone to do multitrack live recording. So doesn't matter how much I like traverso, or whatever.[/INDENT]
- Nobody mentioned the new Open Sound System (OSS). It looked promising, but nobody seems to be taking it for serious at this time. I think it could be a sort of solution though.

EDIT: and there's of course the hardware support. I can't get working my firewire tascam 1804, which can't afford to throw away.

Greetings.

---

### Post by kayosiii on 2009-10-01
Oss 4 at best would perhaps solve the problem of soundcards that don't support hardware mixing trying to be used by multiple incompatible applications at the same time. At worst though it is just another piece in the pile of mess.

Recently Paul Davis - Lead Developer of Ardour has partisipated in two podcasts listening to them should provide quite a bit of insight into where professional audio is on linux and where it is going.

[http://ardour.org/node/3005](http://ardour.org/node/3005)

---

### Post by VertexPusher on 2009-10-01
> **kayosiii said:**
> Oss 4 at best would perhaps solve the problem of soundcards that don't support hardware mixing trying to be used by multiple incompatible applications at the same time.
Didn't ALSA solve that problem 4 years ago?

---

### Post by markbuntu on 2009-10-09
Once you get it set up it is hard to beat linux for audio production. I prefer tihe modular approach, rosegarden for midi, hydrogen for drums, qsynth and zynaddsubfx for synths, jackrack for effects etc etc, ardour for mixing, patchage to connect everything up just the way you want and change everything around at will, and jack to make them all play nice together.

It is so much easier to fix the drums in hydrogen or the midi in rosegarden and just hit play to hear the whole shebang and then just push the record button in ardour.

Having everything open and visible spread out across three monitors (that only took 1 1/2 years waiting for drivers).just makes life so much easier now.... if only there was an easier way to set up my tiny little korg controllers, nanopad for hydrogen (???), nanokey for roesegarden (check) and nanocontrol for ardour (sort of). I hear the new versions work better.

I am still using UbuntuStudio 8.04 because of troubles with the rt kernel and my particular hardware.... I am hoping Karmic will work better, jack2, new ardour with midi, hydrogen, rosegarden....

---


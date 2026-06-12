---
title: "MIDI diagnostics?"
date: 2009-11-23
forum: Ubuntu Studio
---

### Post by DejitaruJin on 2009-11-23
I'm trying to get a MIDI keyboard working, and so far it's a technician's worst nightmare - dozens of different steps all over the place, with no way of testing them individually, and no way of determining where the problem is when it invariably goes awry.

Somewhere, I have a problem. My keyboard is good, and I believe the MIDISport has been configured properly. But on the software side... who knows? I don't. And that's what I want to find out. Thing is, all the sequencers or DAWs I see require some amount of configuration before they'll recognize a MIDI controller, and the only way to know when it's right is for it to work - which makes for a really, really lousy troubleshooting tool.

I need a very, very simple program. Something with no necessary configuration or options. Something that, immediately upon startup, will react to any and all MIDI controllers, and output a noise when a button is pushed. Doesn't even have to be a pleasant noise. Heck, a shell message would be fine - just as long as it can be absolutely guaranteed that, if the movement of MIDI data is functioning up to that point (that is, the point at which a user program would receive the data), it will let me know. In this fashion, the complexities of overall MIDI setup can be completely separated from the complexities of the programs that use it.

Anyone got a lead on such a thing?

---

### Post by mango42 on 2009-11-23
Assuming that you have alsa-utils loaded, amidi -h from the terminal should give you the basics.

It's quite a 'learning curve', huh? ;-)

---

### Post by DejitaruJin on 2009-11-23
Aha! It's beautiful! Could be simpler, but it's easy enough ;)

Okay, that confirms MIDI is being received. That means the issue is somewhere with the applications. Or this "JACK" thing.

Thanks for the info!

---

### Post by AutoStatic on 2009-11-23
The MIDIsport is a USB device right? You can check with **lsusb** if it's properly recognized. But what version of Ubuntu are you using? And what kind of soundcard is supposed to make the noise?
And with amidi you can indeed diagnose MIDI stuff but you will need something like aconnect, aconnectgui or qjackctl to make the actual connections. So maybe you should try aconnectgui. Install it with Synaptic, install ZynAddSubFX also and start aconnectgui. Then start ZynAddSubFX in the terminal to "fool" PulseAudio with the following command:
**pasuspender -- zynaddsubfx -A**
What this does is suspending PulseAudio (the default soundserver for Ubuntu) and then start up ZynAddSubFX. ZASFX can't do PulseAudio, that's why we need to suspend it. I've attached a screenshot so that you might get a clue. I don't have a MIDI keyboard at hand so I used a virtual keyboard.

---

### Post by DejitaruJin on 2009-11-23
Well, the actual MIDISport is fully functional, and it is listed in Rosegarden as an available MIDI interface. However, because I have no idea how Rosegarden works, I have no way of testing whether it actually gets the MIDI signals I have confirmed are entering the system.

It seems rather odd that it would need an additional layer - if amidi can directly receive and interperet the information, it stands to reason that any other program should be able to do the same. It is likely somewhere in this very complicated interface layer that things have gone wrong.

I've got Ubuntu 9.10, and an internal soundcard. The end goal is to strictly use audio samples controlled by the keyboard, not pure MIDI.

---

### Post by bluesscream on 2009-11-23
Next step might be downloading some free sf2-files. Then start qsynth and load them. A little more advanced would be to find matching linuxsampler/gigedit/Q(J)sampler debs or compiling them from sources, make and run gig files. But I recommend to learn this jackd/qjackctl stuff too.

---

### Post by raboofje on 2009-11-24
> **bluesscream said:**
> Next step might be downloading some free sf2-files. Then start qsynth and load them. A little more advanced would be to find matching linuxsampler/gigedit/Q(J)sampler debs or compiling them from sources, make and run gig files. But I recommend to learn this jackd/qjackctl stuff too.

Software synthesis options are explained at [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo) . Perhaps someone should add a section on the other samplers there.

---

### Post by mango42 on 2009-11-24
Glad to see you're moving forwards, DejitaruJin ;-)

AutoStatic, that very helpful image you so kindly provided is a revelation to me as it's my first sight of the elusive 'ALSA Sequencer' panel. I've (very briefly!) seen Patchage (it just folds if nothing external attached?) and JACK's non-standard Control panels but until your post no amount of trying to connect the VKbd to Zyn has worked for me.

All hail '**pasuspender**' - has to be my next attempt at pulling myself up by my boot strings! Pardon my extreme ignorance (also I'm not in Studio mode at present) but does your bit of Terminal magic call up the Alsa Sequencer panel? Up until now I have been expecting a new 'MIDI | internal routing' sort of tab to appear in the standard volume control | ALSA mixer applet.

Small steps but a great adventure... ;)

and thanks, raboofje, for your clear tutorial.

[Ubuntu 9.04 with Studio extensions]

---

### Post by trulan on 2009-11-24
Here's how I do it - I'm a noob at midi but I'm getting pretty comfortable with Jack.

1. Start Jack, via qjackctl
2. Open Qsynth and start it.  (You have to load a soundfont in setup the first time)
3. Connect Midi input to fluidsynth. (via patchage, or the 'connect' window, alsa tab, in qjackctl)

And it works.  The hardest part for me was finding where the soundfonts were stored (two soundfonts come with the Ubuntu Studio audio package). They're in /usr/share/sounds/sf2/.  Here's a screenshot with all the relevant windows open:

---

### Post by DejitaruJin on 2009-11-25
Okay, it's sort of working. I set up QSynth to use alsa_raw for MIDI in and alsa for audio out. It's jittery and static-y and generally sounds terrible, but the only thing I was looking for was response to MIDI signals - which it does properly. (I've heard running fluidsynth directly will fix the sound issues, but it won't recognize MIDI without the GUI settings and I don't care enough to fix it.)

Jack won't run. At all. QJackCtl gives an error that it can't connect to the server. But that's okay - Jack is an overcomplicated mess that seems to work exactly opposite of how I want my workflow to be, and now I know that it is not necessary for the system to recognize MIDI signals. So, I'm willing to put a fair amount of effort into avoiding Jack entirely.

Now, I just need a DAW that is aware I want MIDI input and audio output to be as separate as possible, and everything should go smoothly.

Edit: Okay, Jack *will* work if I run "jackd -d alsa" from the command line and *then* hit Start in QJackCtl. It seems to have the exact inverse problem as QSynth and fluidsynth. But it's still a program I would like to avoid if at all possible by any means.

---

### Post by dawiba on 2009-11-25
DejitaruJin - try this

Download QTractor from the repos.

Open Jack and make your settings are as per the attached screenshots. If you're using RT, then use that screenshot's settings and if you're not using RT, then....;).

Start Jack. Open QTractor.

You should have something like this (see QTractor screenshot)

Open the connections window in Jack and make connections as per the screenshot (Alsa Connections).

In QTractor, add a track. Track -> Add Track. You'll now get a Track window appear. Set it like the attached screenshot (Track - QTractor).

Back in the main QTractor window, click the 'R' button in track 1. The record enable button will now change from greyed out to red. Click the record enable button. You'll now get a pop up window with your choices for where to save your track. Once you've done this, click okay.

Now you're ready to go. Click the play button (or press the spacebar) and you should start recording midi into QTractor.

Now open Hexter (it was the first one I clicked on - you could choose any one you want). Now go back to Jack's Alsa connections tab and connect Hexter up like the attached screenshot (Hexter Connections). Hexter should automatically connect itself under the Audio tab.

Now go back to QTractor, disable record and press play. You should hear your midi playing back to you.

Hope this helps.

---

### Post by dawiba on 2009-11-25
Had to make this post to add the last screenshot.

I also forgot to say, where it shows Mackie XD-2, substitute your own midi interface.

---

### Post by DejitaruJin on 2009-11-25
I've already got JACK working, but those settings don't do it. The server won't start, and then it gives an error that it can't connect to the server. What *will* work is:

Open QJackCtl, and just let it sit.

Through CLI or Alt+F2, run: ```
jackd -d alsa
``` No more, no less.

Back in QJackCtl, click Start. Then it will work.

The problem is, there is a difference in how the GUI calls the underlying program, and how the user typically would. It's the same as with QSynth (which, if I understand correctly, is made by the same person), but QSynth makes the underlying program work when it normally won't while QJackCtrl makes the underlying program *not* work when it normally will.

But, it's already been shown that a program can grab MIDI directly from alsa_raw, with nothing in between. JACK is only necessary if a program has been foolishly built to rely on it - and I intend to stay away from those kinds of programs. The fact that JACK disables Rhythmbox and all other sounds doesn't help its case, either.

I'm also not looking for MIDI output. The programs I normally use can't even save to MIDI format - a MIDI controller is strictly a way to control aspects of the program. It just happens to be that one of those aspects is placement of notes.

On Windows, I can open Reason, click through two menus to tell it to receive MIDI input (assuming it doesn't figure that out automatically), make a new track, assign it to a synthesizer or sampler, and that's it - pressing keys will make noise, in realtime, recording or not. That's all that is needed to make MIDI work. There is no bouncing around through programs, there is no sound server that disables all other noises. *That* is what I require from Linux, which means I need a program that interfaces directly with MIDI input in the same way amidi and QSynth do. Only, scaled up an order of magnitude or two.

---

### Post by dawiba on 2009-11-25
Only trying to help!

If you are looking for a replacement for Reason, then you're out of luck. I used it on a Mac and I share your frustration about Midi in Linux. FWIW, what you describe as the way you operate Reason, which does need a bit of setup, is basically the same as I went through in my other post, just that most of it is hidden from view in Windows or Mac. The same basic things are happening. Midi goes to interface, gets sent to soft synth, triggers samples and/or events, audio comes out (I was showing you how to do audio out, not midi out ;)), gets sent to audio card, then to speakers, hey presto! Once you've set it up, Reason will hook things up for you, but if it's not the way you want, then you have to hit tab, turn it around and start playing with all the virtual cables (albeit very pretty ones :)).

Nothing new in any of that. What's new is you have to do it yourself in Linux.

I used QTractor as an example because you could open that, open some soft synths, route things and assign channels/controllers where you want and have some fun (pretty much like in Reason)! I guess I used the wrong example.

Anyway, Jack doesn't work for you and you don't like it. To my knowledge, there is no program (on any platform) you can just load and start to play sounds using your keyboard without *some* setup. However, you could try LMMS if all you want is to trigger samples on the computer using your keyboard. It doesn't like Jack (on my computer) and works without it.

Hopefully that'll give you what you need.

---

### Post by DejitaruJin on 2009-11-25
But Linux is doing it very, very differently. For one, JACK is totally unnecessary. A program can interface with MIDI input without JACK, no problem (amidi, QSynth). And a program can send audio signals without JACK, no problem (Rhythmbox, built-in sounds). The problem seems to be that other programs have evolved to rely on JACK to do these things, instead of being self-contained.

Reason does have "wires", but they're still within Reason. There's no excuse to have audio or MIDI signals bouncing around whatsoever. It only serves to increase complications and decrease efficiency.

I used Reason as my example because there is essentially no setup. And I imagine other Windows programs would be the same, because this level of configuration can't even be done on a Windows system, let alone required.

I think this may call for a Windows virtual machine. Or making an appropriate program myself, but I'm not much of a GUI programmer.

---

### Post by AutoStatic on 2009-11-25
> **mango42 said:**
> AutoStatic, that very helpful image you so kindly provided is a revelation to me as it's my first sight of the elusive 'ALSA Sequencer' panel. I've (very briefly!) seen Patchage (it just folds if nothing external attached?) and JACK's non-standard Control panels but until your post no amount of trying to connect the VKbd to Zyn has worked for me.Qjackctl shows the same connections in the Alsa tab, Qjackctl and aconnectgui are just different frontends for the same backend (Alsa).

> **mango42 said:**
> All hail '**pasuspender**' - has to be my next attempt at pulling myself up by my boot strings! Pardon my extreme ignorance (also I'm not in Studio mode at present) but does your bit of Terminal magic call up the Alsa Sequencer panel?No, Alsa Sequencer panel = aconnectgui.

---

### Post by AutoStatic on 2009-11-25
DejitaruJin, if you don't like JACK then you could try LMMS. It runs fine on PulseAudio too, only setback then is that when you press a key on your midi keyboard you will hear the keystroke like 10 minutes later or something ;) LMMS works with Alsa too, but then you have to disable PulseAudio.

---

### Post by DejitaruJin on 2009-11-25
It took me about 10 minutes to figure out how to get LMMS to work, as opposed to... well, JACK still isn't really working ;)

This is beautiful. It probably follows the trend of being less full-featured than Windows equivalents, but hell, it *works*. And if I need something it doesn't have, I can likely implement it myself, much easier than I could make a DAW from scratch.

Also, as best I can tell, Ubuntu 9.10 doesn't do anything with PulseAudio by default. I know QSynth complained about it not existing when I tried to set that as the output, and I didn't need any additional configuration to make LMMS use Alsa.

Plug-n-Play, baby ;)

Edit: And it even allows connecting knobs to physical controllers! This program is a whole lot like Reason. I like it. I like it a lot.

---

### Post by dawiba on 2009-11-25
> **DejitaruJin said:**
> But Linux is doing it very, very differently. I agree it's a different approach.

> For one, JACK is totally unnecessary. It might be unnecessary for your needs, but I use it all the time. Again it's a different way of working.

> 
The problem seems to be that other programs have evolved to rely on JACK to do these things, instead of being self-contained. Some programs have and this can be a good thing. If something crashes in the piece you're doing, then only that part should be affected.

> 
Reason does have "wires", but they're still within Reason. There's no excuse to have audio or MIDI signals bouncing around whatsoever. It only serves to increase complications and decrease efficiency Audio and midi will always be 'bouncing around'. Jack lets us control this. Again, I think this is to do with the Linux methodology rather than being a fault of a specific program.

> I used Reason as my example because there is essentially no setup. And I imagine other Windows programs would be the same, because this level of configuration can't even be done on a Windows system, let alone required I'd be happy to be proved wrong, but this level of configuration must apply in Windows for things to work. It's just it's not in plain sight.

I'm not trying to be picky, but simply making the point as you did at the start that it's different in Linux. I struggled with the concept of Jack at first myself and it did take me a bit of time to settle to a different way of doing things.

Why don't you try LMMS, see how you get on and post here if you need any help

---

### Post by DejitaruJin on 2009-11-25
I do appreciate your help, dawiba. JACK is just rather bass-ackwards as far as I'm concerned, and I felt the need to rant ;)

While I'm here, I may as well ask, is there some kind of advanced sampler plugin for LMMS, like Reason's _[NN-19]("http://www.propellerheads.se/products/reason/index.cfm?fuseaction=get_article&article=devices_nn19")_ or _[NN-XT]("http://www.propellerheads.se/products/reason/index.cfm?fuseaction=get_article&article=devices_nnxt")_? Heck, is there even a standardized way of distributing samples? I'm sure Reason Refills aren't the norm :P

Edit: Also, I've just noticed that, like JACK, LMMS makes it so no other programs can produce any sound. Fortunately, closing the program fixes that (as opposed to the reboot required with JACK), but a fix for that would be nifty :)

---

### Post by AutoStatic on 2009-11-26
> **DejitaruJin said:**
> While I'm here, I may as well ask, is there some kind of advanced sampler plugin for LMMS, like Reason's _[NN-19]("http://www.propellerheads.se/products/reason/index.cfm?fuseaction=get_article&article=devices_nn19")_ or _[NN-XT]("http://www.propellerheads.se/products/reason/index.cfm?fuseaction=get_article&article=devices_nnxt")_? Heck, is there even a standardized way of distributing samples? I'm sure Reason Refills aren't the norm :PNo. You can use VST's though within LMMS.

> **DejitaruJin said:**
> Edit: Also, I've just noticed that, like JACK, LMMS makes it so no other programs can produce any sound. Fortunately, closing the program fixes that (as opposed to the reboot required with JACK), but a fix for that would be nifty :)That's because you probably use Alsa as the sound backend in LMMS. If you set it to PulseAudio you won't have this issue. And rebooting with JACK? That shouldn't be necessary. Does JACK lock your PC?

---

### Post by bluesscream on 2009-11-26
@AutoStatic: mine was locked indeed. Priority was set to high in jackd, it came to freezes and zombifying. In systemmonitor-panel-applet I could identify the zombies and choke them off, so no reboot or x restart was necessary. 
Do you think we could ensnare DejitaruJin to give jack a second chance? Might be if he tries jamming and enrich his sounds live by running hydrogen drums and other applications simultaneously? :p
maybe something like this :bg:
[ATTACH]137687[/ATTACH] [ATTACH]137688[/ATTACH] [ATTACH]137689[/ATTACH]
These snapshots were made running 2.6.31-15-generic, not -rt

---

### Post by AutoStatic on 2009-11-26
=P~
Looks good!
Hydrogen 0.9.5 svn 1447, where did you get that from? And good to see that even with a generic kernel one can get such low latencies :)
And when JACK zombifies and everything is locked then an Alt+SysRQ+K should still kill the whole session.

---

### Post by bluesscream on 2009-11-26
> **AutoStatic said:**
> 
Hydrogen 0.9.5 svn 1447, where did you get that from? 
compiled it from svn. But be careful, it's pattern editor is buggy. Only benefit i see is online updating known drumsets. In my real audio workspace i still use 0.9.3

Meanwhile there is Hydrogen 0.9.5 svn 1482. These bugs are fixed and it's working fine.

---

### Post by DejitaruJin on 2009-11-27
> **AutoStatic said:**
> No. You can use VST's though within LMMS.

Well, VST's in LMMS seem to lack the ability to control virtual knobs with real ones (and they're a bit unstable to boot), so I think I'm better off just making a LADSPA plugin - assuming that, amongst the hundreds or maybe thousands of those that already exist, no one has yet gone beyond the basic sampler that comes with LMMS.

> **AutoStatic said:**
>  That's because you probably use Alsa as the sound backend in LMMS. If you set it to PulseAudio you won't have this issue. And rebooting with JACK? That shouldn't be necessary. Does JACK lock your PC?

ALSA is supposed to have its own mixer, but I can't get it to activate. Latency is unacceptable, so PulseAudio is out. It *can* work with ALSA, I just need to get the settings right.

As for JACK, it completely takes over audio processing. So, when it closes, there is no more audio processing. Rhythmbox won't even try to play, and programs that give warnings will state that there's basically no sound capabilities.

---

### Post by AutoStatic on 2009-11-28
> **DejitaruJin said:**
> ALSA is supposed to have its own mixer, but I can't get it to activate. Latency is unacceptable, so PulseAudio is out. It *can* work with ALSA, I just need to get the settings right.That is because PulseAudio locks the Alsa backend. Only one frontend at a time can use Alsa.

> **DejitaruJin said:**
> As for JACK, it completely takes over audio processing. So, when it closes, there is no more audio processing. Rhythmbox won't even try to play, and programs that give warnings will state that there's basically no sound capabilities.Normally when you run JACK PulseAudio gets suspended, just do a **less /usr/bin/qjacktctl**, that's just a wrapper that checks if PA is running and if so, it suspends PA. When JACK locks up jackd keeps running. A **killall -9 jackd** in a terminal should kill the jackd instance and reinstate PulseAudio. When you close JACK normally PulseAudio should take over again.

---

### Post by DejitaruJin on 2009-12-01
I already checked that. Once jackd has been run on the system, no audio will work at all after it has been completely closed. Rhythmbox also uses ALSA; as far as I'm aware, nothing on my system is set to use PulseAudio at all.

---

### Post by kayosiii on 2009-12-04
Ok I am a little late here but...

The jack situation is a mess but I would I think that ubuntu shoulders the majority of the blame here.

The reason that jack does not start for you from Jack control is the same reason it doesn't start for anybody. Jack Control is set to realtime mode by default and Ubuntu is not configured to let audio programs have realtime access, you have to do this by hand. (even Debian gets this right by now - when you install jack it asks you if you want to set up the system for realtime access).

The second thing is due to an internal policy many applications which can quite happily use jack for their output are compiled without this support Meaning that if you want jack support you have to recompile the application for yourself. (I believe that this situation my be changing for Lucid - I hope it is) 

Simply put setting up jack on Ubuntu is a *lot* more hassle than it needs to be.(I own a firepod, which means that jack is the only means by which I can hear anything).

Jack is the only sound system on linux that puts low latency as first priority (it does this best if you give it realtime access) and although you say you can't see the need for it I can safely say after a few years of using jack that the ability to route audio data between different applications is the main reason I continue to use Linux for sound. As it stands jack is "Too hard" to set up and the best way of using it is not immediately obvious. I think these are issues that need to be addressed.

If you are reasonably code literate and you are looking for something all in one... I might suggest taking a look at puredata.

---


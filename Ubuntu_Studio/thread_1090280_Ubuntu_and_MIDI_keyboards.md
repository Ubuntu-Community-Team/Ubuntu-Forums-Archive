---
title: "Ubuntu and MIDI keyboards"
date: 2009-03-08
forum: Ubuntu Studio
---

### Post by Steve H on 2009-03-08
I'm trying to get my external midi keyboard working with Jack.

I'm using an M-audio Audiophile 2496, which shows up nicely in Jack GUI, but when I connect its midi in ports (16:0 M-audio 2496) to any of the softsynths then no signal seems to arrive from the keyboard when any key is pressed.

I've set up a virtual midi keyboard and routed that to the soft synth and that works fine.

Has anyone got any experience of getting an external midi keyboard to route to a softsynth for triggering?

:(

EDIT: I've booted into windows and tried my keyboard in there (in case of an actual hardware failure, which i was dreading), loaded up a soft synth, let ASIO do it thing and bingo! my keyboard sends signals and triggers just fine. Which means it must be the way that linux/ubuntu is handling the MIDI signals. I'm scratching my head and thinking it must be something to do with the JACK & Audiophile combo.

---

### Post by simtaalo on 2009-03-08
have you tried a program that does midi through alsa and not jack?

---

### Post by Steve H on 2009-03-08
Any ideas which synths can be used like that?

---

### Post by raboofje on 2009-03-09
> **Steve H said:**
> when I connect its midi in ports to any of the softsynths then no signal seems to arrive from the keyboard when any key is pressed.

perhaps check with kmidimon whether messages are sent at all?

---

### Post by Steve H on 2009-03-10
> **raboofje said:**
> perhaps check with kmidimon whether messages are sent at all?

I have already done that, but good suggestion. :P

kimidmon is showing two midi ports (one through, one in) but when I monitor them both and press a key on the controller, nothing!!

It's just very weird that it works flawlessly in windows but not in ubuntu.

Is there something about the ICE1712 (Audiophile 2496) driver that could be causing this?

---

### Post by thorgal on 2009-03-10
just to clarify a few things:

when you mentioned qjackctl (Jack GUI), I presume you are talking about the ALSA tab where you see the MIDI ports. This tab shows the ALSA MIDI layer and has nothing to do with jack. It was a matter of convenience, the app author wanted to have a MIDI connection window at a time when jack was not handling MIDI (qjackctl is that old :) ). 

So, I suggest you still use the ALSA tab in qjackctl but don't start the audio handling of the jack server (the big start button in the main window). This will prevent jackd (the jack daemon) from running in the background so you will still use ALSA for the audio as well (default audio layer I presume, unless you have pulseaudio running, which I hope not). 

Anyway, having the Jack GUI opened, the ALSA tab showing MIDI ports and the audio server (jackd) off, you can use a few soft synths outputting their audio to the ALSA layer, for example qsynth.

You can start qsynth from the terminal with the -a switch to indicate ALSA as the audio layer it shall use:

```

qsynth -a alsa

```

then you load a soundfont (sf2 file) in it (Setup window) and restart the driver as it asks you. You may want to set a medium to large buffer size (Setup window) for a glitch-free experience.

However, if kmidimon does not report any input event when it listens to your MIDI input port, I can only think that something is wrong at a low level (alsa-seq driver). Check for system messages at boot time (dmesg).

---

### Post by Steve H on 2009-03-10
Thorgal, thanks for the reply. I will try and have a go at all that when I get home from work. However I do have a question.

Yes I do have pulseaudio running. I know it's not the best audio server in the world but it is essential for gaming and comms (i.e. running Eve Online with a teamspeak client). It did take me ages to sort out, no surprise there, but why would that effect jack and midi?

I do use the ALSA tab in Jack GUI as my card appears in MIDI tab but doesn't seem to connect to anything. Although there is a midi playback on the client side, connecting does not seem to do anything.

I just don't understand why audio servers are having anything to do with the MIDI signals, given that MIDI is just triggering info and not actual sounds.

---

### Post by thorgal on 2009-03-10
hey Steve,

you're right that the soft synth is triggered by MIDI events, but it maps the incoming MIDI notes to its internal sounds and output those to something, as a matter of fact the audio layer. If pulseaudio is running and the soft synth is configured to output to ALSA or jack, you may have an issue here, unless you configured pulseaudio to provide an ALSA or jack source/sink for apps that only understand ALSA or jack. I played little with pulseaudio and did not bother with it more than a day or two, so I cannot help you on that.

What bothers me in your description is the absence of data in kmidimon. This looks suspicious ...

maybe you can tell which version of ALSA you are using ?

---

### Post by Steve H on 2009-03-10
Houston, we have MIDI!!!

:D

I did what you suggested, Thorgal, I started qjackctl but didn't press start on the audio engine, started the synth connected to the keyboard and hey presto!! The MIDI keyboard sent a signal and triggered the synth.

This has taught me a little something about the differences in architecture between OS's. In the old windows all the services are running at once, so you can record MIDI and audio at same time (should you want to), but jack is much more either/or.

I'm pleased to say that pulseaudio didn't seem to interfere, which is a relief, I thought that would be the next headache!!

Thanks for all your help, now I can start on my masterpiece musical opus....maybe...

;)

---

### Post by thorgal on 2009-03-10
great :)

but you are a little mistaken on one thing: you can use the ALSA MIDI layer with jackd running for audio at the same time. I do that all the time :D

The problem may come from your soft synth: it cannot output its audio to jack ;) Which soft synth are you using ?

In fact, forget a sec about MIDI and soft synth. Have you tried using jack for audio only ? I mean, does your sound card work nicely with jack for audio ? if not, then you'll be a little limited for music production. Not totally impossible but jack is really nice to use for music production.

---

### Post by Steve H on 2009-03-14
Thanks for all your help, I have a better understanding of it now. I've been messing about with Qsynth, which didn't work at first, but once I configured it to use a different sound server (ALSA) it all worked perfectly. I get it now how the MIDI and audio are being handled.Using the audio for a sound source and the MIDI as a trigger.

I had a play with just the audio last night. Played a little bit of guitar, using jack to pipe from my inputs to my outputs. It all seemed fine, I managed to record the sounds. The only problem I had was using Creox C, (guitar effect app), nothing I did seemed to make any difference in terms of the sound of the guitar. And I couldn't find any way of connecting the inputs through the app to the outputs. I'm sure I'm missing something obvious but I can't figure it out....yet!!

;)

So what sort of music do you make?

---

### Post by thorgal on 2009-03-14
creox ? last time I heard, it had not been updated for ages. If you want jack aware realtime guitar effects, try :

guitarix : [http://sourceforge.net/projects/guitarix/](http://sourceforge.net/projects/guitarix/)

rakarrack : [http://rakarrack.sourceforge.net/](http://rakarrack.sourceforge.net/)

They both understand MIDI events from a MIDI foot pedal so you can freak out with say a cry-baby FX or others in realtime.

So as a rule of thumb, until you know better about jack-MIDI, use jackd for audio (audio connection graph in the jack-GUI) and ALSA-MIDI for MIDI connections (ALSA tab in the jack-GUI). They both work simulateanously so don't worry. When the jack MIDI handling is supported by many more apps, the ALSA layer will become superfluous. In fact, you can already use the jack-MIDI layer but it is not as straightforward.


Anyway, I am into rock (or post-rock) music, I have not published anything yet on the internet because I still have to finish my current projects + my job is taking me a lot of time these weeks. I was on a sabbatical leave for a year, time I spent building my linux studio and composing, but that came to an end in August 2008 (money resources as well). It's hard to be a full-time solo composer-musician that is not interested in the music-business in a money-freak society ... but things will change slowly ...

---

### Post by rayj on 2009-03-16
First suggestion: listen to Thorgal. He knows what he's talking about. Check out his studio...

Experimental suggestion: I've had a lot of fun using AlsaModularSynth. It's easy to use, completely modular/flexible, and mapping controllers to LADSPA plugins gives you access to an incredible array of wild sounds, all in one app. I've managed to get a simple setup rolling on an old IBM Thinkpad T30 with 256 megs of ram running AlsaModularSynth for audio processing/tweaking and Rosegarden running sequencer duty, piping external hardware synths back into a few effects plugins, all with tweakable parameters (you have to watch and adjust the parameter scaling for usable sounds, but that's easy with the GUI). Qsynth, Qsampler, and Specimen all have worked very well, although there are the extra soundfont/etc. conversion steps to deal with. Hydrogen can function very well as a sample sequencer with any supported audio files (.wav, etc.) Using Alsaseq as the Jack Midi driver (?) has always worked for me. I've only been using Linux for about a year.

Seriously, the flexibility of linux audio (JACK!) is amazing, even on modest hardware.

---

### Post by Steve H on 2009-03-17
Thanks to both of you for your support. I'm slowly dipping my toe in the pool of Ubuntu's production capabilities. I'm enjoying the modular nature of it all, even if it is a bit daunting. It's obviously a bit of a shift, moving over from winxp. I've been using Ubuntu for quite a while but always dual-booted for the music production side of things, but that is now grating my nerves so I thought I'd attempt using Ubuntu. I'm not disappointed.

I'm really only experimenting at the minute, getting an overview of the way the audio/MIDI system works. I always need to know what something can do before I know what I want to do with it.

I'll report back as I try more and more.

Thanks again

:D

---

### Post by markbuntu on 2009-03-18
I use patchage to connect midi and rosegarden and hydrogen softsynths to ardour controls etc. You should check it out. It is point and click and shows absolutely everything in one box. All the jack apps can be set up to be controlled from the jack transport controls so syncing playback/rewind/recording is a snap. There is a bunch of links about getting ubuntuStudio and jack set up near the bottom of this post

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by dirkmitt on 2009-04-19
I hope that you guys don't crucify me for my earlier error, which was to start yet another thread on this subject, because an even earlier thread had migrated into the READ ONLY Archive, yet without checking to see that your thread also existed.

I'd also like to admit that I'm not an audiophile, more of a computer geek who likes to dabble in different uses for his computer.

But I did read Steve H.'s problem eventually, and found myself wondering whether my observation also applies to it, and to the use of QSynth. This is where I had made my own posting:

[http://ubuntuforums.org/showthread.php?t=1129540&highlight=MIDI+keyboards](http://ubuntuforums.org/showthread.php?t=1129540&highlight=MIDI+keyboards)

You see, I would also see QSynth as a program which allows the user to set up which instrument he wants to be playing, as well as the SoundFont, which defines an instrument bank.

Edit: What I just did, was to explore Alsa Modular Synth for the first time. And at first, I started it in pure ALSA mode, that is without Jack. It seems to run fine, but I get a crackling sound at any volume level. Thus, to try to fix that problem, I did install jackd. And I also install qjackctl, which on my system is not an ALSA mixer tab, but a real control window for Jack. And I was able to route the MIDI as well as the audio, so that Alsa Modular Synth works again under Jack, and such that it plays MIDI sent by my Oxygen 61.

And so I've answered my own question: No, This is a completely different type of issue. Also, I should remind people that I don't use Ubuntu myself, but am only trying to expand my knowledge base. I use Kanotix Thorhammer, kernel version 2.6.24 .

Anyhow running 'ams --jack' eventually works, but does not solve the crackling problem. So I deactivated jackd, and launched my Control Center, from where I tested (and restarted) my sound system under pure ALSA, which still works fine.

Do you guys know anything about the crackling that Alsa Modular Synth can cause on some systems? BTW under ALSA, doing such logical things as increasing the sampling period, had no effect. Nor did switching from 44100kHz to 48000kHz.

Dirk

---

### Post by dirkmitt on 2009-04-20
I'm sorry to bump my own post, but thought that as long as I had posted a problem and found the explanation, I should also post the explanation (separately).

Also, Ubuntu users are going to be thrilled to hear that they do have a long-term advantage over Kanotix. Evidently, the reason for which I've been hearing gaps in the playback of Alsa Modular Synth etc., is the fact that it cannot start up into real-time mode. For that, we need a real-time kernel. And the Kanotix forum is exactly the place where their users can find instructions on how to build your own kernel from source code. But one reason I've been dipping my fingers in here, is the fact that Kanotix developers know more about their form of computer-auto-mechanics than they would about music.

And I'm *not* prepared to build a new, real-time Kanotix kernel, where the one I presently have has high stability on its side. I guess that is one really basic advantage which Ubuntu ships with. And also, my motherboard's timing pulses run at only 250Hz, which Rosegarden complains about. Evidently it also helps to have faster timing pulses, or even "tickless time".

And one might not think that it matters running AMS in ALSA mode. But AMS still uses the Jack library for sound output, even if we're not using a Jack server, so it does matter.

Edit:

What I discovered is, that even though I cannot get the Jack server to
run in real-time mode, and even though it was giving me trouble using
its own ALSA driver, which happens to be the default which my system
uses, there was a way to get it running satisfactorily: I needed to
select the OSS driver, not the ALSA driver, from within the Jack server
settings, which I control using the 'qjackctl' GUI package.

But this means for me, since that crackling problem has stopped, that
now I can use "Alsa Modular Synth" as long as I require it to connect to
a running Jack server, and thus not to use ALSA at all. With which
settings it's now producing all its effects without any malfunctions or
'crackling sounds'. It also means that the DAW software "Rosegarden"
should now work for me as well.

But this is a kind of experimenting, which also risks to screw up
somebody's sound setup if anything, but which I happened to luck out with.

When I was configuring SDL ("Simple DirectMedia Layer") in connection
with other software, I got the reverse results, which were also the more
logical results, because until now ALSA has been my default, not OSS. So
I guess that "Kanotix" has as one feature, the fact that its sound is
not fully set up, and that users can ~set it up~ with (mixed) drivers in
an ad-hoc way. And with Jack not running in RT priority.

Dirk

---


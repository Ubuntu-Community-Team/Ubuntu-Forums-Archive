---
title: "Can't get decent audio synthesis"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by violinist2009 on 2008-12-02
I'm running Ubuntu 8.04 Hardy with the rt kernel, and I'm having problems with synth applications. LMMS works for exporting, but realtime sound absolutely sucks. Rosegarden and any other realtime synthesis stuff I've tried does the same thing. ZynAddSubFX works without stuttering only if I'm not trying to get it to pipe meaningful sound to anything. About the only success I've had is with Hydrogen. LMMS is working for me on the same system under Windows. Anyone have any ideas?

---

### Post by Stochastic on 2008-12-03
Do you have the realtime kernel installed?  That fixes major issues in the audio timing chain.  To check, do ```
uname -r
``` and if it doesn't end in "-rt" then do ```
sudo apt-get install linux-rt
```  Then, when you're starting Jack, go into qjackctl's settings panel and tick off the realtime option.

---

### Post by violinist2009 on 2008-12-03
I have the realtime kernel installed, but I'm not sure if I've encountered the realtime option in qjackctrl. When I get back to my computer I'll check that out.

I'll post the results later.

---

### Post by violinist2009 on 2008-12-09
I've checked my qjackctl settings, and I didn't have realtime enabled; however enabling realtime made little to no percievable difference in lmms's synthesis system.

I still am at a loss as to why my laptop, which has 2GB of RAM, and a decent intel dual-core processor should be doing this. My Vista OS shouldn't be outdoing Ubuntu, but it is in this regard.

I haven't really spent lots of time learning the configuration options, but I can get around them quite well if someone would tell me what they are.

Please help. This is extremely frustrating.

---

### Post by warbread on 2008-12-09
Can you describe in greater detail what you're trying to go for?

---

### Post by violinist2009 on 2008-12-14
What I'm trying to get is really a working instance of LMMS. I really wouldn't mind getting the various MIDI synths I have installed working with Rosegarden or Muse (through Jack, of course), but none of them seem to want to work for me. I don't really know what technical details I should be giving or where to look for them. Any guidance will be appreciated.

On a related note, I really like what I see with the Bristol synths, but I can't really get them to work. Without Jack started, they won't start at all, and with Jack started I get an error that the ```
bristolengine
``` is already active and the buffer system is empty.

I have great respect for the way the Linux audio creation and editing software is designed to (mostly) work together, but I have not yet managed to find anything on the content creation side that wasn't endlessly frustrating.

Thanks in advance for any and all advice you can give me. I really want to solve this.

---

### Post by thundercles on 2008-12-15
what exactly are you trying to do with lmms, I was drawn to it at first way back when too and quickly figured out that it wasn´t really powerful enough for what I was trying to do, not to mention I seem to remember having odd issues with it creep out back then too, unless you have a very specific need that only lmms can fulfill I´d suggest trying to branch into Rosegarden, it still accomplishes the all-in-one kinda interface that you are more accostomed to with the Reason/cakewalk/pro tools/acid and all the other windows programs people use to do the same stuff, but still allows you to fully connect all the i/os from jack for your MIDI or sound to other stuff if a specific part of rosegarden isn´t doing the trick (I pretty much always link the midi sequencer up to external softsynths and linuxsampler or qsynth rather then use the soundfonts loading tools in rosegarden, yet I find that its multitrack recording is often fine for my purposes and don´t bother firing up ardour half the time I would have used to anymore since I started recording more stuff right into rosegarden and managing the looping as audio instead of midi sequences to save memory (trying to run rosegarden, qjackctl, zynaddsubfx, amSynth, Qsampler, Qsynth, Hydrogen, and sometimes ardour all at once across two screens was getting ridiculous on my half gig of memory) and I even had all the mapping set up for the sliders on my Oxygen keyboard to the audio mixer in rosegarden for a while (and the transport buttons too now that I think about it, that was wonderful but more recently I can´t for the life of me figure out how to do that again, setting up all the buttons and knobs and such through midi has been my one major constant issue with music stuff in linux) rosegarden does excellent midi routing too, but more recently I´ve been enjoying the more lightweight seq24 for midi sequencing and use ardour for recording again, just mess around with all the different stuff and you might be surprised with what floats your boat.

A little more specific description of what exactly is going haywire and we might be a little more service to you, a copy from a log or two in pastebin might help us figure out what´s going on a little easier too, but the good news is your problems are NOT realtime, the purpose of using a realtime kernel is that realtime allows certain programs ran by a non-root user to take complete precedence over your system´s resources, which is pretty much for latency reduction, most of the time when realtime isn´t working right you know because of the very noticeable delay between a midi device and hearing something from your speakers or problems with recorded instruments or vocals syncing up in the multi-track when recording in full-duplex, it only has to do with signal delay, nothing really to do with quality. From what you have said your culprit is more then likely your audio system or buggyness in the binary of a program or two you are using (as I said above, lmms was always particularly finicky with me), so first off make sure that stuff sounds right normally, use xmms and vlc just over alsa to make sure the kernel modules for your sound card are even working the way they should, if that sounds crystal clear, then try just an audio player over jack (xmms has a jack plugin, which is a must have if you are ever trying to make a midi-sequence based off a recording you already have anyways) make sure that it works just as well through jack as it did straight through alsa, to make sure jack is working right. If it passed both of those tests then your sound system is working perfectly fine and it´s crappy binaries that are to blame, the best way to deal with those is to try just compiling the source for the offending program, reading the front page in the news section of the project may give you some insight as to if there might have been a bug in the code for the version you have and compiling this new code will fix it outright (the fix might only be in the unstable source) or if you should stick to the stable code which will have the highest chances of working perfectly (as long as a specific fix you need is still being tested). When I first started using planetCCRMA I got really hooked on using amSynth for doing monophonic bass lines, but later when I installed it again the repository didn´t even tell yum it was available anymore, so I hollered at one of the maintainers and it was obvious that there just wasn´t enough interest in that program with the maintainers to really mess with it, so I just grabbed the source and had the latest version lickety split and sent the dude the compiled binary, with 2 gigs of ram I can almost guarantee that your proc can probably compile circles around my P4 2.0A ghz one from like 5 years ago, I don´t think that I´ve talked to anyone who has used lmms in a very long time so there is a pretty good chance it´s just not being actively maintained in the repo as well.

So try that stuff, if it turns out to be an alsa problem go right into xterm and copy the output from:
lspci
lsmod
ps -e
and go to [http://pastebin.com/](http://pastebin.com/) and paste all that in the window make sure it´s set to retain for 30 days and then post the link(s) generated from doing this
as well as a screenshot kinda like this:
*edit: oops forgot to include the screenshot, it will now be at the bottom of the page.... :oops:

basically I just need to see the stuff where that cursor is, you can take the shot in the audio setups for KDE or gnome, but chances are qjackctl is already open and it´s the same either way if you just take the shot in qjackctl.
I can´t really think of anything else for figuring out what´s wrong with alsa, but I´m not all the way used to tools like alsaconf just disappearing in ubuntu either...

If it is a jack problem pastebin everything that came up in the ¨messages¨ window and include a screenshot just like the one above, and hell pastebin a ps -e too, that might help.


If xmms plays through both alsa and jack fine, then start figuring out what program is the culprit by trying out many different ones and report back if you still have issues.

I´ll go ahead and subscribe to the thread so if no one else beats me to figuring out what´s wrong, I´ll pop in and give it a whirl, with all that info it shouldn´t be too hard.

---

### Post by warbread on 2008-12-16
> **violinist2009 said:**
> What I'm trying to get is really a working instance of LMMS. I really wouldn't mind getting the various MIDI synths I have installed working with Rosegarden or Muse (through Jack, of course), but none of them seem to want to work for me. I don't really know what technical details I should be giving or where to look for them. Any guidance will be appreciated.

On a related note, I really like what I see with the Bristol synths, but I can't really get them to work. Without Jack started, they won't start at all, and with Jack started I get an error that the ```
bristolengine
``` is already active and the buffer system is empty.

I have great respect for the way the Linux audio creation and editing software is designed to (mostly) work together, but I have not yet managed to find anything on the content creation side that wasn't endlessly frustrating.

Thanks in advance for any and all advice you can give me. I really want to solve this.

Ok, one program at a time.  Let's go back to LMMS.  First, I'm a little confused as to whether the problems you're experiencing are technical - audible pops, crashes, fires, etc. - or if you just don't like the sound quality offered.

---

### Post by thundercles on 2008-12-16
> **warbread said:**
> Ok, one program at a time.  Let's go back to LMMS.  First, I'm a little confused as to whether the problems you're experiencing are technical - audible pops, crashes, fires, etc. - or if you just don't like the sound quality offered.

ya, that's why I asked for the lspci, lsmod and ps -e, the lspci will let us know what sound card he's running and what else, as well as what slot it's in (I always put my sound cards in the closest spot to the controller/proc, but I have a lot of onboard crap that can get in the way, the crappy via onboard soundcard likes to hijack alsa from my SB Live quite often.) So as I was saying if he has a bunch of onboard crap like I do, then the sound card might be getting interrupted by the onboard lan card, or worse yet if the soundcard he's using is onboard he could be getting noise from off the board. It is more then likely something like that since reading the original post again it sounds like he is indeed getting sound it is just crappy, hell the sound card may even just suck (I seem to remember him saying it sounded great in windows, but then again my onboard via card actually has a pretty decent amp for low end so I don't really mind (sometimes prefer) playing music off it, but the SB Live card does 24 bit DAC and ADC and the onboard via does not (not to mention its ADC has picked up noise off the board when the mic or linein is on and cranked up from time to time.)

Also if the crappy sound is only happening when he's using jack, well jack is pretty darn persnickety about being set up right and the system being set up right for it, seems like a pain in the *** now, but it's quite worth it for a completely modular production environment where you can pipe around the audio signals on the PCM however you choose. 

I'm still a little confused about why you would need jack for lmms since (it's been a while since I used it) lmms seems to be the only audio production program for linux that is really geared towards being a jack of all trades, but then again it would depend on what you are doing in lmms, lots of audio recording and midi sequencing and I can see the latency getting outta control.

---

### Post by eye208 on 2008-12-16
> **violinist2009 said:**
> Anyone have any ideas?
Let's tweak your Jack settings.

[img]http://img61.imageshack.us/img61/8493/screenshot1mv6.png[/img]

Does this work for you? If it doesn't, double the "Frames/Period" value until it does.

---

### Post by Zannax on 2008-12-16
I had similar problems (audio stuttering when playing "complex" songs, with rt-kernel and all the stuff).

Since it seemed that the CPU wasn't powerful enough, I've increased the priority (I set nice to -18 in system monitor) to the following processes:
- timidity 
- rosegarden sequencer
- jackd (jack daemon).

It works fine for me, so try lowering the nice value of whatever sinthetizer/sequencer you use...

---

### Post by babarosa on 2008-12-17
Hello violinist,

try the following to solve your performance problems:
Read my advices I gave in this thread "http://ubuntuforums.org/showthread.php?t=965611&highlight=babarosa"

Set the jack-rt priorities as described and stick to the screenshot. Do not set priority in qjackctl but set it in the limits.conf-file as described!

Regards, Michael

---

### Post by kayosiii on 2008-12-19
I don't think LMMS works well with Jack at all - I do wish somebody would get portaudio to work well with Jack.

With Zynaddsubfx - make sure that it is set to the same sample rate as jack this will help things a bit. be warned though that some zyn patches can get stupidly processor intensive.

Increase Jacks buffer size - this will increase latency but will give you more cpu for dsp without getting sound issues.

you can also try DSSI + host (rosegarden does this)- of these whysynth is probably most interesting but I don't know if it is in the repos.

I also don't mind amsynth for some sounds.

Finally make sure that /etc/security/limits.conf is configured correctly the easiest way to do this is with the tools provided for ubuntu studio.

---

### Post by neu2buntu on 2008-12-23
another thing to try...in qjackctl is to tick unlock memory as lmms runs through wine ,and perhaps increase the audio buffers in lmms itself in sound settings

---

### Post by violinist2009 on 2009-03-09
I'm sorry that I haven't posted in a while, but I upgraded to Intrepid and have been going to a intense Bible college without much free time. I made changes to my security.conf and my qjackctrl settings as recommended, and lmms works, though since the upgrade, jack doesn't want to run in realtime mode - even when I boot an rt kernel. I don't really need to solve this, since it would be just a tweak to a working setup anyway.

Thanks for the help!

---

### Post by kayosiii on 2009-03-09
Could you try starting Jack from the terminal in realtime mode 

jackd -R -d alsa 

(assuming that alsa is the driver you use). and post the output here?

---


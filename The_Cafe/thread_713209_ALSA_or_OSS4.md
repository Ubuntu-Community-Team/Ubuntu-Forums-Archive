---
title: "ALSA or OSS4"
date: 2008-03-02
forum: The Cafe
---

### Post by malfist on 2008-03-02
I was wondering what the ubuntu's community thinks about ALSA and OSS4. I've had lots of issues with ALSA and it was suggested that I switch to OSS4 but the information I was given about OSS4 was nazish fanboy stuff that was horribly biased (what else are geeks good for? :P)

Anyways, what do you use?
Which do you think is easier?

**Note: OSS4, not the old depreciated one!**
OSS4 has software mixing.

---

### Post by ~LoKe on 2008-03-02
I'd choose Alsa over OSS, but PulseAudio over both.  They're all lacking somewhere, for ALSA, it's playing multiple sounds at once, for PulseAudio, it's digital passthrough.

I think a healthy mix of PA and ALSA would be the best choice.

---

### Post by malfist on 2008-03-02
OSS4 has software mixing and can play multiple sounds at once. Currently my ALSA can only play one stream though :(

---

### Post by terry_gardener on 2008-03-02
oss4 because alsa doesn't support my x-fi card oss4 does. simple as that. 

alsa is easier to work with though

---

### Post by nerdy_girlscout on 2008-03-03
I vote for OSS4! I've had problems with both ALSA and even Pulseaudio wich is so praised right now. I was first amazed that Pulseaudio supported software mixing, and also switching volume for all streams seperately.. however, this is all supported in OSS4 already! And PA seems slower, and all apps need to be modified to use it correctly. OSS4 works as it is, the only thing we need to change is the new ALSA-only apps.

All apps that I could use OSS in worked as they should with full software mixing. I could even have WINE running at the same time as Kaffeine with sound from both. Now when we're switching to PA, WINE also needs to be modified in order to get PA support..

---

### Post by DancemasterGlenn on 2008-03-05
OSS4 has a lot of things going for it that most newer/inexperienced users may fail to see, since it is not provided as an easy alternative in Ubuntu (but I hope it might be added into the Hardy repos, since it is open source and GPL!). There's an article that I read a while ago that talked about some of the difficulties ALSA has that OSS4 is in some cases able to overcome... although it may sound biased, it is a very good read (and I hope some Ubuntu devs will make a note of it)

[The sorry state of sound in linux](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

Please don't be turned off by the title, it's a very good read.

Honestly, OSS4 is well-kept, well-updated, free (again)... the only problem I have with it at this point is that hardware MIDI sequencing was ripped out, due to it being mostly old code. Once that gets reimplemented (hopefully soon...), sky's the limit for OSS. That's my two cents, anyway :)

---

### Post by derekr44 on 2008-03-05
Alsa here, but mainly because I don't know the difference.

Begs the question from me... what's the difference?  I'm mostly concerned with using a Logitech USB headphone with microphone (has a sound card integrated) in addition to WoW on Crossover.

What would be the best in that situation? :confused:

---

### Post by zekica on 2008-03-05
I personally use ALSA, because I have no problems using it on both an integrated card in my Laptop, and a ens1371 (SB PCI 128 ) on my Desktop.

ALSA may be a mess: it has user space libraries, and kernel space drivers, software mixing in user mode, and if you use it's OSS emulation, it goes from kernel mode to user mode to perform software mixing and then back to kernel mode to send that to device driver, but this is not something necessarily bad.

For example one can set a default sound card using one configuration file, pass all data to userspace program (via plugins), for example to pulseaudio, setup a software volume control, mix channels and remap them... With pulseaudio you can even create 5.1 surround system from three stereo outputs... you can divert sound to another system on a network (even for OSS applications) etc. This is what ALSA can do.

OSS can do software mixing with much less processor time spent (everything is in kernel mode), requires no setup and supports newer hardware, but can't do all things ALSA can.

Maybe one day I'll be able to setup pulseaudio server on my system (for local applications and via network for applications on my laptop), set it to output sounds to OSS (with it's software mixing, if it is possibile), and tell all applications to use pulseaudio (via it's ALSA plugin, or native, and via ALSA's OSS emulation if possible), and make a perfect setup :-({|=

---

### Post by DancemasterGlenn on 2008-03-05
Some people on the OSS4 team are working on SALSA (implemented, but still in development), which will hopefully be able to handle ALSA processes preoperly in the future, which would be the best of both world for me. I can get a similar thing happening with the alsa-oss packages, but that uses oss3, which isn't nearly as awesome. Also, since I'd rather use OSS4 for the majority of my work, leaving ALSA for the things that I absolutely have to, that would be a more preferable choice for me.

derekr44, oss4 is sort of a pain to install (sort of, it may have gotten easier, but I believe you at least need to still install the deb running in a purely terminal session, so that alsa is not running and won't flip out at you), but it wasn't an extreme hassle to try once I figured that out. Also, since the alsa repositories are all in synaptic, it's easy to reinstall them if you have second thoughts. My advice is to try it! There's no harm in trying, and your programs will likely work fine with the change. You can get the deb [here](http://www.opensound.com/download.cgi). Just remember, if you decide to switch back, be sure to uninstall oss before reinstalling alsa. They don't play nice (and probably won't until Ubuntu starts offering them both in the repos).

Hope that's helpful, good luck.

---

### Post by derekr44 on 2008-03-05
> **DancemasterGlenn said:**
> derekr44, oss4 is sort of a pain to install (sort of, it may have gotten easier, but I believe you at least need to still install the deb running in a purely terminal session, so that alsa is not running and won't flip out at you), but it wasn't an extreme hassle to try once I figured that out. Also, since the alsa repositories are all in synaptic, it's easy to reinstall them if you have second thoughts. My advice is to try it! There's no harm in trying, and your programs will likely work fine with the change. You can get the deb [here](http://www.opensound.com/download.cgi). Just remember, if you decide to switch back, be sure to uninstall oss before reinstalling alsa. They don't play nice (and probably won't until Ubuntu starts offering them both in the repos).

Hope that's helpful, good luck.

Thanks for the tip!  I suppose I shall try it out and see...

---

### Post by Methuselah on 2008-03-05
OSS for me.
It has the critical advnatage of not being linux specific.

---

### Post by Zorael on 2008-05-12
If the pulse and OSS crews can get the incompatibilities worked out - OSS4 isn't completely backwards-compatible and pulse calls some now-deprecated function - I'd go pulse and OSS. I've had my share of driver issues with ALSA.

Pulse or no pulse is the dealbreaker for me though, so I'm sticking with Pulse and ALSA for the time being.

---

### Post by OpposingForce on 2008-05-24
OSS4, I have a Creative X-fi so I don't have a choice.  Well my only choice is use OSS4 or not use linux at all (no sound isn't really gonna work for me).  And it actually sounds good and works with pretty much everything (except hl1 engine games in wine 1.0-rc2, I get no sound in game, not sure if its an OSS issue or what)

---

### Post by LightB on 2008-05-24
OSS4 is great, much better than ALSA on many things. Still missing a few things like any hardware midi on emu10kx cards. Also, not so great because distros assume ALSA, installing OSS will break some things. I think linux devs will shy away from OSS4 due to the politics. But 4.0 has been made GPL, right? Legally, it's a one way street. 4.1 is still commercial only.

---

### Post by hanzomon4 on 2008-05-24
I would love to try oss4, I did try it on PC-BSD but it only the pay version supported my Delta 66. I now have a laptop but I'm not sure if PC-BSD can be installed on an apple notebook as easily as Ubuntu. I'm to nervous about breaking an almost perfect Ubuntu setup by installing OSS4 but it sounds so nice.

---

### Post by Rhapsody on 2008-06-12
OSS4 for me, simply because ALSA won't work with my X-Fi. I'm left wondering why we use ALSA. Does anyone have any idea what the position of the kernel developers is now that OSS is GPLed again? Are we going to persevere with ALSA or what?

---

### Post by bruce89 on 2008-06-12
I haven't a clue about all the audio APIs, all I care about is that they work.

---

### Post by cardinals_fan on 2008-06-12
```
#!/usr/bin/ruby

alsa = "easy"
puts alsa
```

---

### Post by F-3582 on 2008-07-06
I use OSS4, because it is everything ALSA and Pulse offers (okay, except for streaming) plus small latency minus overhead. Also, ask some Emulator devs which architecture they like better. Everyone will answer OSS and call ALSA a hackjob.

---

### Post by coolen on 2008-07-20
I must use OSS for my hardware, but I prefer PA running on ALSA. OSS doesn't seem as refined (for example, when I plug my headphones in, it doesn't mute the speakers).

---

### Post by alroger on 2009-02-03
I tried OSS4 as soon as I found this thread.
Thank you for the idea!

OSS4 was the solution to my problems. Pulse is always breaking up, locking up. With Pulse, ALSA or just OSS I've never been able to get Voice (VoIP) inside Second Life.
I've been running OSS4 for a couple of weeks now with any glitches.. superb... 100%. Faster and lighter than pulse, it made possible to use Voice in Second Life (usually won't work without hardware mixing in the audio chip/board) and I can run VLC, Firefox, Amarok, Second Life (and streaming and Voice inside SL) all at the same time with impecable quality.

Perfect! ossxmix is much nicer and easier to use than the strangely undocumented PA utilities.

BTW, super simple to install and remove. Just need devel packages to compile modules... I use the latest updated Ubuntu 8.10 32 bits.

---

### Post by billgoldberg on 2009-02-03
Alsa seems to work for me, I don't really care what it is as long as it stays out of my way (aka works).

---

### Post by Stoneface on 2009-07-18
ALSA + PA don't work well with Skype nor do they function very well in general on my Acer Aspire. I am considering trying OSS4. I am only  worried about long term support for it.

---

### Post by khelben1979 on 2009-07-18
I always prefer ALSA to any version of OSS. I'm not sure which is the best since I've never tried OSS 4.

---

### Post by doorknob60 on 2009-07-18
I use ALSA because it's annoying to find workarounds for all my apps to use OSS4. It works, but ALSA works just as well most of the time.

---

### Post by quazi on 2009-07-19
For me OSS4 seemed to work perfectly and provided better support for my sound card than ALSA was able to.  However, I'm lazy and ALSA+PA is already installed on Ubuntu so it's what I go with.  It would be nice if distros started supporting OSS4 though.

---

### Post by Exershio on 2009-07-19
I just installed OSS4 for the first time on a fresh install of Arch Linux, and I have to say, it's amazing. I can finally get sound in both TuxGuitar and MPD, sound is definitely louder without a reduction in quality, and overall, I like it better.

Thanks for this tip.:popcorn:

---

### Post by martinbaselier on 2009-07-24
Both alsa and ossv4 worked on my machine as they primarily should, play sound. I can also play multiple sources with both at the same time.  I switched to oss recently and found the sound quality much better. I now hear details in the music I could not hear before. That is my primary reason to stay with oss.

---

### Post by Arup on 2009-07-28
I recently made the switch to OSS4 after Alsa would keep loosing sound settings on reboot, also mic would get too low. I do notice that OSS4 has better sound quality with my Yamaha Waveforce soundcard. If you are using Skype, make sure to remove it and install SkypeOSS for proper functioning. Also in programs like Stardict which use the play command for pronouncing words, replace ossplay instead of aplay to make it functional.

---

### Post by MaxIBoy on 2009-07-28
ALSA would be easier to set up, since it's included right with the kernel, and most programs default to it. OSS4 is less of a hassle to deal with once its up and working. So what do you mean by "easier?"

---

### Post by themusicalduck on 2009-07-29
Installed OSS4 to give it a go. Amarok and flash ceased to produce sound even though I told Amarok to use OSS and even though OSS4 worked on the test in sound preferences.

Seems like a hassle to setup properly. Although bit of a shame, if OSS4 does produce better quality and louder sound, to keep using ALSA.

---

### Post by Arup on 2009-07-29
> **themusicalduck said:**
> Installed OSS4 to give it a go. Amarok and flash ceased to produce sound even though I told Amarok to use OSS and even though OSS4 worked on the test in sound preferences.

Seems like a hassle to setup properly. Although bit of a shame, if OSS4 does produce better quality and louder sound, to keep using ALSA.

Did you install gstreamer plugin bad? In my case it works fine here with Banshee and Rhythmbox.

---

### Post by themusicalduck on 2009-07-29
Rhytmbox works, but just about nothing else does like Amarok, VLC or flash. It does appear to play though, there isn't any error from Amarok. Perhaps I need to change a mixer setting somewhere?

I seem to have all gstreamer plugins installed. I think I've installed all the plugins and codecs from medibuntu. While installing the .deb it did come up with a list of errors that it looped a few times, something about disabling driver modules. I can't copy and paste it since it's from the virtual terminal.

OSS4 seems to load fine after a reboot though so don't know if that's the problem.

---

### Post by Arup on 2009-07-29
Make sure to select Unix OSS out in audio options of VLC as it defaults to Alsa.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Please follow all the steps listed here to a T and you won't have any issues with OSS4 upgrade.

---

### Post by themusicalduck on 2009-07-29
Thanks, I'll give that a go :)

---

### Post by cbilljones on 2009-08-03
I end up having to install alot of stuff from source with oss4, but i find its worth it in the end, ubuntu needs to make it an option in 9.10 in my opinion

---

### Post by coldReactive on 2009-08-03
ALSA with ESD.

---

### Post by MasterNetra on 2009-08-04
ALSA and Pulse Audio work fine for me. Though I usually let what Ubuntu decide be it. Which usually is ALSA. Though Mandriva One 2009.1 (KDE) uses pulse audio which seems to work fine thus far.

---

### Post by stevethefiddle on 2009-10-25
I really don't understand these comments about OSS4 sounding louder. The maximum digital signal is 0dB, and it does not matter what sound system you use, if you exceed 0dB almost all sound cards will clip (distort).

The only way that OSS4 could be louder is either to clip the audio, or to compress the dynamics, but in either case this is undesirable for anyone working with music. For any serious music work the digital data should be accurately converted to the analogue waveform.

Personally I doubt that OSS4 does such undesirable things to the sound.

Regarding sound quality, if one is better than the other, then there MUST be distortion in the lower quality sound. This is easily measurable, but to date I have seen no published evidence to support this. If anyone else wants to make the claim that OSS4 has "better sound quality", please please please give us the numbers and take this discussion out of the realms of "my computer sounds better than your computer". My own tests show no difference in sound quality.

Alsa provides open source support for a vast range of audio hardware. OSS on the other hand was open source, then closed source, now partially open source ([http://www.4front-tech.com/license.html](http://www.4front-tech.com/license.html) ). For long term deployment in an open source environment OSS4 does not currently offer a viable alternative.

---

### Post by Xbehave on 2009-10-25
Complex mixing? not in my kernel! even with floating point exception handeling

Those that argue for OSS4 inevitably and invariably don't understand pulseadudio.
ALSA = simple hardware drivers (no complex mixing in kernelspace)
OSS4 = hardware drivers + complex mixing in the kernel
PULSEAUDIO = per user complex audio mixing.

OSS4 can do most of the things that PA+ALSA aims for (powersaving, multiple outputs, piping audio between various inputs/outputs, etc, bass boost for headphones), however it has to do it all in kernel code which is a bad idea. Doing this microkernel style (daemons doing as little as possible in the kernel) does incur a slight overhead, however this is minimal on a desktop (and in other situations complex audio mixing isn't required).

I get that the implementation of PA is not great, but the design is much better than OSS4

---

### Post by SuperSonic4 on 2009-10-25
Phonon (Y)

---

### Post by SomeGuyDude on 2009-10-25
I'm going to quote myself from the Hardy 8.04 & OSS thread.

> **SomeGuyDude said:**
> By the way, what moron decided that OSS shouldn't have jack sensitivity? Who doesn't use their headphone jack?!?

---

### Post by infestor on 2009-10-31
alsa comes default and have been using, no problems so far

---

### Post by dragos240 on 2009-10-31
I like oss. It's nice and direct. Works with old software, works with everything. No issues.

---

### Post by togo59 on 2010-01-02
+1 for OSS4

---

### Post by nrs on 2010-01-02
Old thread, but I wasn't the one to revive it so w/e.

There are some people who say pulseaudio instead of oss/alsa, which doesn't make much sense. Pulse doesn't supplant them, it's layered on top of them. It's a sound server, nothing more.

---

### Post by KayakJim on 2010-01-07
> **nrs said:**
> Old thread, but I wasn't the one to revive it so w/e.

There are some people who say pulseaudio instead of oss/alsa, which doesn't make much sense. Pulse doesn't supplant them, it's layered on top of them. It's a sound server, nothing more.

ALSA replaces OSS.  PulseAudio sits on top of ALSA to provide multiple streams. While PulseAudio can work with OSS it is not needed as OSS4 supports multiple streams by default.

In regards to the original question OSS4 without question.

---

### Post by TalonzX on 2010-03-25
I used alsa for a long time when i used ubuntu, and had a horrible time with studio cards and even my old audigy 2 value card had difficulties under alsa + pa.  

I've since switched to archlinux and decided to give oss4 a try, and ive have had no problems with oss4 at all, with studio sound cards the sound is of professional standards and even my old audigy 2 value has never sound better. 

OSS will never die for the fact that its highly portable across nearly all systems while alsa is not.  while alsa has grabbed a strong foothold in the linux market, OSS still holds a strong user base and is the sound api of choice for BSD users.

---

### Post by purgatori on 2010-03-25
OSS4. I've given Pulse a chance on different releases/distros, and of different machines, and it NEVER works properly. Pulse + 9.10 on my current machine = no sound through external speakers (internal was fine), so it wasn't long before I switched to OSS4, which always 'just works'. and works well.

---

### Post by Nuckinfuts on 2010-03-31
Anyone have OSS4 working in 10.04 Lucid? the deb from 4front seems to crash my system when logging in.

---

### Post by KayakJim on 2010-03-31
> **Nuckinfuts said:**
> Anyone have OSS4 working in 10.04 Lucid? the deb from 4front seems to crash my system when logging in.

You would be best off building from source than using the .deb.

---

### Post by Psumi on 2010-03-31
I've tried OSS4 on various hardware, as well as ALSA and pulse.

ALSA beats the competition handsdown.

---

### Post by Nuckinfuts on 2010-03-31
> **KayakJim said:**
> You would be best off building from source than using the .deb.

Is that really the only issue?  I tried the deb on 9.10 and to the same result and I'm making this post from the Live-USB while the system is reinstalling... again.

I'll try the source route on this new install... fingers crossed

---

### Post by themarker0 on 2010-03-31
I use both. On my laptop, i cannot get ALSA working (Won't touch PA) So i use OSS. On my desktop, ALSA works best.

---

### Post by KayakJim on 2010-04-01
> **Nuckinfuts said:**
> Is that really the only issue?  I tried the deb on 9.10 and to the same result and I'm making this post from the Live-USB while the system is reinstalling... again.

I'll try the source route on this new install... fingers crossed

You should not need to reinstall Ubuntu due to something not working in OSS.

---

### Post by GepettoBR on 2010-04-01
ALSA works for me, so I use ALSA. Never needed OSS. Maybe it's better, but if it ain't broke don't fix it.

---

### Post by Nuckinfuts on 2010-04-01
> **KayakJim said:**
> You should not need to reinstall Ubuntu due to something not working in OSS.

Recovery console doesn't work because it will hang when trying to remove to deb file, it's a pretty bad fail, and the compiled from source route came to the same end.

So all in all, I voted alsa because it only doesn't give me sound, it doesn't lock up my computer too...


I miss the good old days when both were installed and when some program crashed and had the alsa lock out, I would just switch to OSS until I fealt like rebooting... ah the days

---

### Post by KayakJim on 2010-04-01
> **Nuckinfuts said:**
> Recovery console doesn't work because it will hang when trying to remove to deb file, it's a pretty bad fail, and the compiled from source route came to the same end.

So all in all, I voted alsa because it only doesn't give me sound, it doesn't lock up my computer too...


I miss the good old days when both were installed and when some program crashed and had the alsa lock out, I would just switch to OSS until I fealt like rebooting... ah the days

You are following the steps listed on the [OpenSound]("https://help.ubuntu.com/community/OpenSound") page right? I had no problems except for getting my internal mic to work but otherwise everything worked perfectly.

---

### Post by Nuckinfuts on 2010-04-02
> **KayakJim said:**
> You are following the steps listed on the [OpenSound]("https://help.ubuntu.com/community/OpenSound") page right? I had no problems except for getting my internal mic to work but otherwise everything worked perfectly.

followed the page to the letter on 9.10 and 10.04 beta, fresh installs, nothing changed to the point of same desktop background.  hangs still

---

### Post by phaddeus on 2010-04-28
> **Nuckinfuts said:**
> Anyone have OSS4 working in 10.04 Lucid? the deb from 4front seems to crash my system when logging in.

Yes, 

OSS4 drivers from 4front deb, Pulseaudio, Gstreamer, phonon, xine, Libcanberra.
Everything work's so far, Youtube, Amarok, system sounds.

Followed the instructions, except comment out module-hal-detect is in /etc/pulse/system.pa rest in default.pa.

I work with high power audio equipment all day IMHO I do think OSS4 sounds better, It has better clarity and position, maybe down to better signal path / less resampling.  I would like to remove pulseaudio but gnome seems hardwired to set system sounds.

---

### Post by Bachstelze on 2010-04-28
I have used ALSA in the early days, it worked very well, even for my modem! Now I don't use either. :)

---

### Post by mgol on 2010-05-16
I'm still unable to configure OSS4 properly. I removed ALSA completely, installed oss4-gtk and oss4-dkms from this PPA:
[https://launchpad.net/~sevenmachines/+archive/release+1](https://launchpad.net/~sevenmachines/+archive/release+1)
upgraded packages from this PPA:
[https://launchpad.net/~dtl131/+archive/ppa/](https://launchpad.net/~dtl131/+archive/ppa/)
and:
1) external speakers doesn't work; even if connected, sound goes out of internal speakers,
2) the only way I could actually hear anything was via:
```
osstest -lV
```
mplayer with -ao oss doesn't work either.

How to make it work at all?

I use Intel HD Audio:
```

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```
oss modules seems loaded:
```

$ lsmod | grep -i oss
oss_usb               110747  4 
oss_hdaudio           146671  8 
osscore               571433  6 oss_usb,oss_hdaudio

```

---

### Post by themarker0 on 2010-05-16
ALSA for the laptop. OSS for the Tower

---

### Post by dtfinch on 2010-05-16
ALSA (and that extra unnecessary layer Pulse that's the new default) never played smoothly until I got a Phenom II X6. Still, I hate to dedicate an entire cpu core to a buggy unoptimized audio library, but nowadays there's no getting around it.

OSS just worked, from the beginning, perfectly, on the oldest computers, and then it suicided by going proprietary for many years.

I haven't tried OSS4. It may be too late for a comeback.

---

### Post by Frogs Hair on 2010-05-16
I use  Nvidia HDA ( on-board chip)   the Alsa Mixer ( terminal )  and the Pulse Audio equalizer from the PPA.

---


---
title: "Does Pulse Audio work for you?"
date: 2009-04-08
forum: The Cafe
---

### Post by Mehall on 2009-04-08
[http://twtpoll.com/o9w78w](http://twtpoll.com/o9w78w)

Conducting a poll to see if PulseAudio is working for people, because I wanted a global EQ, and was told "already in pulseaudio", when pulseaudio doesn't work for a large number of people.

original brainstorm:

[http://brainstorm.ubuntu.com/idea/19103/](http://brainstorm.ubuntu.com/idea/19103/)

---

### Post by Tibuda on 2009-04-08
Yes, without any tweaking.

---

### Post by damis648 on 2009-04-08
Yes. :popcorn:

Some applications don't like it (Audacity, XBMC :mad:), but it works fine.

---

### Post by swoll1980 on 2009-04-08
Never had a problem with it.

---

### Post by jespdj on 2009-04-08
Works good enough on 8.04 and 8.10. I applied [these fixes](http://ubuntuforums.org/showthread.php?t=789578) but I don't know if they were really necessary or not.

---

### Post by vikigal on 2009-04-08
Never worked for me. I worked through all the solutions many times. I spent a solid week trying to fix my sound issues after an upgrade. Ended up going with alsamixer before I could get any sound. Tried everything. I am now sticking with alsamixer. It works with everything I do.

---

### Post by Methuselah on 2009-04-08
I have relatives that use skype and I find I'll have to take it off default devices if I want playback and capture to work.
Otherwise PA has been working well for me after hardy. I had to tweak my hardy installation.

---

### Post by Ascenti0n on 2009-04-08
I cant record in Audacity. I followed some howto's within these forums, but to no avail. Some of these were even suggesting that you had to close all applications that might use sound to prevent  Pulse audio from getting it's knickers in a twist, WTF?

Audio - playing and recording, you'd think it would be a basic thing to get right in a modern OS wouldn't you?

---

### Post by SomeGuyDude on 2009-04-08
Pulse was wonky for me. Back on ALSA.

---

### Post by Bölvaður on 2009-04-08
depends on hardware. some audio cards I got pulse is not the way... like my rusting (yes it is that old) sound blaster live! 5.1 (the ! is part of the name), that does definetly not work with pulse.

---

### Post by spcwingo on 2009-04-08
After much tweaking, yes.

---

### Post by gn2 on 2009-04-08
Got rid of it almost a year ago and have never been inclined to try it again.

---

### Post by FuturePilot on 2009-04-08
Had problems with it in Hardy, had to do some tweaking but that was because Ubuntu failed at getting good default settings on it. They fixed that since then. I haven't had a single issue with it since Hardy. Works perfectly without tweaking anything in Intrepid and Jaunty. And this is on 4 different computes all with different sound cards. From a Sound Blaster Audigy to Intel cards, all works perfectly.

---

### Post by NightwishFan on 2009-04-08
Pulseaudio causes applications in Wine to lose sound sometimes, even with high priority. (I am pretty sure pulse is at fault anyway, since they work fine with alsa). Other than that I like it, and even the name sounds cool. Better than "core audio" at least. It seems like it has great potential for improvement.

---

### Post by Nevon on 2009-04-08
In Hardy I was having all kinds of problems with it, but in Intrepid it works well - except for capturing audio, which doesn't work at all.

---

### Post by gnomeuser on 2009-04-08
I use PulseAudio every day and I like it very much. I can switch between my external USB sound card and my internal one. These days I find that without PulseAudio my computer just doesn't work as I expect anymore, I have grow to like how it makes audio better for me and easier.

There is a slight problem which currently causes it to crash quite often but it is a bug in the ALSA driver so I hardly think it is fair to blame PA for other peoples suckage. 

It is the same thing with Network Manager, it got a lot of flak for a long time because they refused to turn their codebase into a massive hack to work around other peoples problems. Today after Network Manager helped expose all of these bugs they are largely all gone and Linux is better for it and NM hardly ever causes problems for people anymore. I think PulseAudio will be much the same, issues will be found and fixed, issues that exist already but aren't hit since we are not using these advanced features PA allows us to. 

Linux will be better for this kind of software to be uncompromising with regards to bugs in the stack it depends on. Even if there is a period of pain involved for some users.

---

### Post by PreviousN on 2009-04-08
I hate pulse. It prevents me from listening to music and playing a game at the same time. And, I've had to jump through hoops to get it running on one of my computers. 

I hate it.

---

### Post by billgoldberg on 2009-04-08
> **Mehall said:**
> [http://twtpoll.com/o9w78w](http://twtpoll.com/o9w78w)

Conducting a poll to see if PulseAudio is working for people, because I wanted a global EQ, and was told "already in pulseaudio", when pulseaudio doesn't work for a large number of people.

original brainstorm:

[http://brainstorm.ubuntu.com/idea/19103/](http://brainstorm.ubuntu.com/idea/19103/)

Yes, but poorly (skipping of sound when switching desktops, scrolling websites, ...).

Switched to ALSA.

---

### Post by |Mitch| on 2009-04-08
Pulse Audio was the only way I could get my USB Headphones/Mic working with everything.

---

### Post by Delever on 2009-04-08
At this moment - perfectly. But there are new incoming updates, so... MUST UPDATE... CANT RESIST...

Well, i am on jaunty since last alpha, so it varies.

---

### Post by Bungo Pony on 2009-04-08
It works, but it's a bit of a mess. I can't find what I need, ever. I have two sound cards in my PC which complicates things greatly.

> I cant record in Audacity. 

Use JACK audio control. Better yet, use a Windows program running in WINE. That's what I do. I only use Audacity for editing because getting it to record is a pain in the bum.

---

### Post by timzak on 2009-04-08
I'm still using Soundblaster Live! PCI cards in all my computers (I have them and they sound better than an onboard solutions on my systems, so might as well use them).  The main problem I have with Pulse is that on one of my systems I have 4 channels and a subwoofer, and Pulse does not recognize 4 channels out of the box.  There is tweaking involved to enable more than 2 channels.  Of course, the howto that explains how to fix this tells me to edit a config file that does not exist on my system.  Perhaps it is because the howto is for Ubuntu and my system is Xubuntu.  Regardless, I am stuck with two channels that do not work.  Otherwise, my other systems all use 2 channels and work fine with Pulse.

---

### Post by gnomeuser on 2009-04-08
> **timzak said:**
> I'm still using Soundblaster Live! PCI cards in all my computers (I have them and they sound better than an onboard solutions on my systems, so might as well use them).  The main problem I have with Pulse is that on one of my systems I have 4 channels and a subwoofer, and Pulse does not recognize 4 channels out of the box.  There is tweaking involved to enable more than 2 channels.  Of course, the howto that explains how to fix this tells me to edit a config file that does not exist on my system.  Perhaps it is because the howto is for Ubuntu and my system is Xubuntu.  Regardless, I am stuck with two channels that do not work.  Otherwise, my other systems all use 2 channels and work fine with Pulse.

PulseAudio 0.9.15 supports an easy way of enabling more than stereo. I have my external SB Live! 5.1 running right now with this working and set using just the volume selection gui (there's a tab there now for this).

---

### Post by DMcA on 2009-04-08
It only works properly after a few hacks and a lot of time spent trying to figure these out. It also annoys me that pulse seems to want to be tied to X. I want my sound system to be entirely non-dependent on X thank you very much. 

That said, you can do some very cool stuff with pulseaudio. Streaming over a network is absolutely trivial for example

---

### Post by gnomeuser on 2009-04-08
> **DMcA said:**
> It only works properly after a few hacks and a lot of time spent trying to figure these out. It also annoys me that pulse seems to want to be tied to X. I want my sound system to be entirely non-dependent on X thank you very much. 

That said, you can do some very cool stuff with pulseaudio. Streaming over a network is absolutely trivial for example

PulseAudio is NOT tied to X. It can run systemwide or sessionwide, but it does not tie into the X protocol or libraries at all. I have no idea where you got that idea from.

---

### Post by NightwishFan on 2009-04-09
Ah yeah! I remember opening the Pulse Volume Control, and it had support for mixing all 6 channels when I played a DVD in Totem.

Slightly off topic, but does Jaunty include the new pulseaudio mixer applet? (I have not tested yet I am waiting to buy the DVD after release.)

---

### Post by boteeka on 2009-04-09
As much as I like the concept behind PulseAudio, and aknowledge it that there is a need for it, I must say that it isn't there yet. Whether it is poorly implemented, buggy, or whatever else problem, it just doesn't cut it right now.

I can't use Skype at all (I tried every possible setting and configuration variations), sometimes even music playback produces crackling noises, small pauses, etc. When I mute the main volume, there is a crackling noise again. There are bugs that simply prevent it to be a usable sound server. But I did not gave up hope yet! I really want it to succeed and be a usable, perfectly good sound server. Although, for this to happen, bugs must be exterminated, and overall quality must be raised.

It is part of the truth that I'm running Jaunty, which is not yet stable, but still... wouldn't it be nice if It Just Worked?

---

### Post by timzak on 2009-04-09
> **gnomeuser said:**
> PulseAudio 0.9.15 supports an easy way of enabling more than stereo. I have my external SB Live! 5.1 running right now with this working and set using just the volume selection gui (there's a tab there now for this).

How do I go about getting this working on a Hardy machine?  I don't have the version numbers handy--is 0.9.15 available in the repos?

---

### Post by PurposeOfReason on 2009-04-09
I tried it once, got it working, didn't see a big enough reason for the trouble it caused. I can play multiple sources with alsa. I don't need a sound server. And a software eq will always get killed by a good sound system.

---

### Post by speedwell68 on 2009-04-09
> **billgoldberg said:**
> Yes, but poorly (skipping of sound when switching desktops, scrolling websites, ...).

Switched to ALSA.

That sums up my experiences with it too.

---

### Post by ghindo on 2009-04-09
I'm not sure if I have PulseAudio enabled.  I know it wasn't working for me in 8.04, but I'm now running 9.04 and want to give it another shot.  How do I make sure I have Pulse enabled?

---

### Post by zenithdave on 2009-04-09
Its starting to get good now :guitar: even the sounds from weapons is synced  in Nexuiz (might have been the 2.5  upgrade)
As i mainly have a PC for music i loved the low Latency i have enjoyed for years on a Delta44 card in windows (2ms) 

Im hanging on for pulseaudio to let me connect with ASIO speed in a few fave music apps and VST's in XP virtualbox but im also installing Studio on another partition ext4 ):P

Feeling good Winthorpe :lolflag:

---

### Post by Pkadjipag on 2009-04-10
It does but I can't seem to have my built-in mic to work (I'm on HP pavilion 9700) and I can see on the forums that i'm not the only one with that problem. I hope i can resolve it soon. Apart from that, it works great. Except that I don't get any sound from ePSXe but I don't think Pulseaudio is the problem.

---

### Post by TheIdiotThatIsMe on 2009-04-10
> **zenithdave said:**
> Feeling good Winthorpe :lolflag:

But but.... you didn't wait for someone to say the first part...

Looking good Billy Ray!

---

### Post by DMcA on 2009-04-10
> **gnomeuser said:**
> PulseAudio is NOT tied to X. It can run systemwide or sessionwide, but it does not tie into the X protocol or libraries at all. I have no idea where you got that idea from.

I know it's not actually tied to X, I said it seems to want to be. Trying to run it as a system session is not entirely straightforward. In ubuntu, at least, logging in starts a user session that takes over from the system one. And all the tools like padevchooser aren't exactly command-line friendly. I mean, if you know a good way to control pulse from the command line (without just editing the config files) I'd like to know. I haven't looked into it too thoroughly

---

### Post by 3rdalbum on 2009-04-10
Before Pulseaudio, people were complaining that the audio situation on Linux was fragmented, that some programs would lock other programs out of audio. This is true.

Now that we have Pulseaudio, people are complaining that Pulseaudio is causing some programs to be locked out of audio output.

Pulseaudio has not caused a problem for me, and in fact it gives us some nice features. I used to have programs being locked out of audio; but now with Pulseaudio I'm not getting that at all.

---

### Post by zenithdave on 2009-04-10
> **TheIdiotThatIsMe said:**
> But but.... you didn't wait for someone to say the first part...

Looking good Billy Ray!

Next time Eh ! ;)

Pulseaudio has handled everything i have thrown at it without a glitch, a vast improvement :guitar:

64 jaunty ext4

---

### Post by hyperdude111 on 2009-04-10
Worked on 8.04 and 8.10 but has a few problems on 9.04 beta (occasional crackling) hopefully it will be fixed by the final release.

---

### Post by Solrac924 on 2009-08-12
i mostly use ALSA, but i do use PulseAudio when i use VirtualBox. when i do, it works great.

---

### Post by mamamia88 on 2009-08-12
haven't had a problem since jaunty

---

### Post by pt123 on 2009-08-12
big problem since Jaunty

---

### Post by Kingsley on 2009-08-12
I can't remember if the guys at Ubuntu implemented this in 9.04 or not, but in Fedora there's a default "feature" called flat volume. It basically allows the volume applet to control all the programs using sound at once. I disabled this ASAP because it usually made my applications have max volume by default when I opened them. Other than that, PulseAudio has been a charm.

---

### Post by starcannon on 2009-08-13
I need to answer "kind of"; sometimes its fine, other times it's not.

---

### Post by Alejandro Nova on 2009-08-13
I moved 2 weeks ago to Sabayon Linux with KDE. I had to configure manually PulseAudio (because it's a KDE distro, and they don't have the heavy dependences on Pulse that Ubuntu has), but, when all pieces got together, it was a charm. CPU usage always under 3% of 200% (two cores). This, with some caveats: I'm using here a prerelease 0.9.16 that Sabayon (really) is shipping as DEFAULT (Sabayon 5).

After some configuration hell (as expected in a Gentoo-based distro) I did the "perfect setup" described in PulseAudio homepage... and what a difference!. I have two sound cards and three sound devices. This is always a nightmare to setup with vanilla ALSA, for all my programs. But with PulseAudio, no more nightmare. I use my on-board sound chip to feed headphones, and my cs46xx sound card to feed speakers, and I can freely switch on the fly between them. And I don't know what Sabayon really did, but "glitch free" here IS GLITCH FREE (with both sound devices). Amazing.

---

### Post by Warpnow on 2009-08-13
Pulseaudio is way too much of a headache for me. Alsa worked much better. Pulse does work, but I have problems with some applications and I randomly lose sound on my system until I reboot.

---

### Post by RiceMonster on 2009-08-13
No problems with Pulse in Fedora. Last I used with Ubuntu was 8.04. I experienced minor problems here and there.

---

### Post by NightwishFan on 2009-08-13
Interrupt based scheduling is fine on Ubuntu 8.04.1 and onward. Timer seems to work, but I did not test much.

On Fedora Pulseaudio has minor problems when using timer based scheduling. It chirps and stutters at odd times.

Pulseaudio does not function well at all on OpenSUSE 11.0 and 11.1. I cannot remove it, as it is a dependency of YAST2. It stutters and crackles with OpenAL and Wine. I cannot play more than one ALSA stream at one time. I cannot play an ALSA stream with a Pulse stream running. I can fix by removing alsa-plugin-pulse, but that is only possible on KDE based systems. GNOME requires it. In the end I tried to disable pulseaudio from autospwawning, but it still is used by default in all gstreamer applications.

---

### Post by harry2006 on 2009-08-13
i don't have any issues..i'm on dell and it works out of the obx....no probs at all

---


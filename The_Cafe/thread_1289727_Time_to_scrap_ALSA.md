---
title: "Time to scrap ALSA?"
date: 2009-10-12
forum: The Cafe
---

### Post by Rhapsody on 2009-10-12
I'm increasingly wondering what is actually the point of Linux using ALSA these days. Nothing else uses ALSA, nothing else uses anything *like* ALSA, all of the software developers I've talked to prefer OSS over ALSA, lots of other operating systems use OSS, OSS seems to have better hardware support than ALSA, OSS is available under exactly the same licence as ALSA, and the OSS deb packages available from 4Front work perfectly on Ubuntu.

So why is ALSA still the default in Ubuntu, why is OSS not even available as an option, why can 4Front not find funding for the development of the promising [OSSv5](http://4front-tech.com/hannublog/?p=36), and why is ALSA even still being developed when OSS seems to be better in just about every way?

I ask this in the hope that I will either get told why I am wrong and ALSA should stay, or that no one will be able to answer and we can finally get some movement in the direction of sanity.

---

### Post by SomeGuyDude on 2009-10-12
Forever ago, I think before Hardy came out, Pulse was supposed to be the wave of the future. Somehow didn't happen.

FOSS is pretty democratic. If OSS or Pulse or whatever isn't winning the battle, then chances are someone's doing something wrong somewhere.

---

### Post by Xbehave on 2009-10-12
[LIST]
[*]All modern linux programs use ALSA, OSS is kept for legacy only and poorly supported.
[*]Pulseaudio uses whatever is avalible but is far more tested/stable with alsa
[*]OSS pulled a switcherroo which left kernel devs maintaining code they didn't want to so will not be accepted back into the kernel anytime soon
[*]OSS does complex mixing at the kernel level so kernel devs will not accept it
[*]Alsa while far from perfect is far more advanced and os actively maintained in the kernel
[*]Alsa plays nice with other kernel subsystems if OSS does is unknown
[/LIST]
To my knowledge reiser3 is the only development that made it into widespread use on technical merit after objections about the developer, so the siwtcherroo will really hold OSS back.

Linux audio is finally pretty unified behind pulseaudio+alsa, so why go changing things and breaking apps?

---

### Post by Xbehave on 2009-10-12
> **SomeGuyDude said:**
> Forever ago, I think before Hardy came out, Pulse was supposed to be the wave of the future. Somehow didn't happen.

FOSS is pretty democratic. If OSS or Pulse or whatever isn't winning the battle, then chances are someone's doing something wrong somewhere.
FOSS is not at all democratic its a meritocracy, some people's opinions (e.g linus's) count for a lot more than other (e.g yours and mine)

From my understanding [PA]("http://upload.wikimedia.org/wikipedia/commons/0/00/Pulseaudio-diagram.svg") does not compete directly with OSS/ALSA it builds on top of them.

For the record I'm really not a fan of PA and would rather it was replaced by OSS or ALSA+nice plugins, however it does have some merits that have not been implemented elsewhere yet (e.g powersaving, networked audio) and the chances of this happening are slim. In particular a lot of frameworks are built upon ALSA (which PA emulates, while fixing deficiencies) and the kernel opposition makes OSS a no go (unless a distro has the balls to maintain OSS)

---

### Post by hoppipolla on 2009-10-12
> **Xbehave said:**
> To my knowledge reiser3 is the only development that made it into widespread use on technical merit after objections about the developer, so the siwtcherroo will really hold OSS back.

Woah that's mad man I just read about Hans Reiser... that's insane.

I used to like Reiser4!!! O.O

---

### Post by Jimleko211 on 2009-10-12
> **Xbehave said:**
> FOSS is not at all democratic its a meritocracy, some people's opinions (e.g linus's) count for a lot more than other (e.g yours and mine)

It is a democracy, but it's a type of Florentine democracy.  For those unaware, only people who were part of the guilds in Florence could vote.  For this, I'm ignoring the fact that the de Medici's ruled anyway, and only kept voting around to appease the common people and did what they wanted.

If you have the skills to influence things, you get a "vote".  A normal person is usually ignored because the projects are made to satisfy developers, not for end users.

---

### Post by hoppipolla on 2009-10-12
> **Xbehave said:**
> FOSS is not at all democratic its a meritocracy, some people's opinions (e.g linus's) count for a lot more than other (e.g yours and mine)

Woo Linus! ^_^

Thing is, at least we have good "leaders" or whatever you wanna call them, like Linus Torvalds and Mark Shuttleworth :)

---

### Post by t0p on 2009-10-12
Pulseaudio seems to fritz everything on my systems.  ALSA poots along nicely.  So I love ALSA longtime!

> **hoppipolla said:**
> Woah that's mad man I just read about Hans Reiser... that's insane.

I used to like Reiser4!!! O.O

No matter how murderous a dev may be, if he designs a nice file system, it's a nice file system.

Anyway, if you say bad things about reiserfs, he may escape from prison and come after you! :evil:

---

### Post by dragos240 on 2009-10-12
I use alsa for my arch boxes. I don't see what's wrong with it. No problems so far.

---

### Post by NoaHall on 2009-10-12
I can't remember which one didn't work for me before. Probably Alsa. Didn't let me have sound in more than one application at a time. Works fine now though.

---

### Post by Xbehave on 2009-10-12
> **dragos240 said:**
> I use alsa for my arch boxes. I don't see what's wrong with it. No problems so far.
Lack of per program mixing (it can be done with soft-mix but no distros maintain this as a supported setup)
Lack of power saving (the ironically named glitch free audio)
Inability to do complex mixing

[why pulseaudio was developed]("http://0pointer.de/blog/projects/jeffrey-stedfast.html"), [where i found the link]("http://ubuntuforums.org/showthread.php?t=1206428&highlight=pulseaudio&page=6"). That should explain what pulseaudio can do that alsa cannot (although im still not convinced that alsa couldn't match PA with plugins)

---

### Post by gradinaruvasile on 2009-10-12
I use ALSA only on all Ubuntu running comps... PA is not mature enough... Yet.

---

### Post by dragos240 on 2009-10-12
Do you mean I couldn't run 2 streams at once? Meaning a youtube video and audio from a game? I can do that.

---

### Post by NoaHall on 2009-10-12
No, **_*I*_** couldn't do that before. But now **_*I*_** can ;)

---

### Post by hoppipolla on 2009-10-12
> **t0p said:**
> Pulseaudio seems to fritz everything on my systems.  ALSA poots along nicely.  So I love ALSA longtime!



No matter how murderous a dev may be, if he designs a nice file system, it's a nice file system.

Anyway, if you say bad things about reiserfs, he may escape from prison and come after you! :evil:

rofl oh noes!

> **NoaHall said:**
> I can't remember which one didn't work for me before. Probably Alsa. Didn't let me have sound in more than one application at a time. Works fine now though.

Yeah I had that problem too! It's been much better recently though.

---

### Post by Xbehave on 2009-10-12
> **dragos240 said:**
> Do you mean I couldn't run 2 streams at once? Meaning a youtube video and audio from a game? I can do that.
No that was an old OSS limitation (***might*** still be around when an app uses the OSS api to call alsa directly (e.g not through PA)), what i meant was the lack of vista style per-application volumes, more useful than it shounds.

I believe this can/should be doable in alsa but the route distros have gone is PA and i'm too lazy/unkowledgeable about alsa* to do anything about it.

*I **think** lack of developers knowedgeable with alsa is a problem alsa faces (even though plenty of people implement new drivers for it:S)

---

### Post by hoppipolla on 2009-10-12
> **Xbehave said:**
> No that was an old OSS limitation (***might*** still be around when an app uses the OSS api to call alsa directly (e.g not through PA)), what i meant was the lack of vista style per-application volumes, more useful than it shounds.

I think the Gnome sound tools allow this in Karmic :)

---

### Post by Rhapsody on 2009-10-12
> **Xbehave said:**
> [LIST]
[*]All modern linux programs use ALSA, OSS is kept for legacy only and poorly supported.[/LIST]
With precisely zero support from Canonical, I've installed OSSv4 and made it work with almost all of my applications (the only ones that refuse to work are closed source applications only made for ALSA). The vast majority of Linux programs are open source and either work with OSS already, use sound servers that support OSS already, or can be easily modified to work with OSS.

> **Xbehave said:**
> [LIST]
[*]Pulseaudio uses whatever is avalible but is far more tested/stable with alsa[/LIST]
PulseAudio refuses to work at all on this system (the daemon won't even start, and gives no error messages other than that it failed to start), so I don't know about this. But with OSS unsupported by most distros, it never will be tested because no one's using it, and people won't start using it until my suggestion to add it as a supported option is implemented.

> **Xbehave said:**
> [LIST]
[*]OSS pulled a switcherroo which left kernel devs maintaining code they didn't want to so will not be accepted back into the kernel anytime soon
[*]OSS does complex mixing at the kernel level so kernel devs will not accept it[/LIST]
These may well be valid, though the first is just the kernel developers going with an inferior option because of a grudge in my opinion.

> **Xbehave said:**
> [LIST]
[*]Alsa while far from perfect is far more advanced and os actively maintained in the kernel[/LIST]
The first part of this is just untrue, OSSv4 is every bit as advanced as ALSA, possibly more so. The second part can hardly be considered a fault in OSS.

> **Xbehave said:**
> [LIST]
[*]Alsa plays nice with other kernel subsystems if OSS does is unknown
[/LIST]
This I cannot comment on.

> **Xbehave said:**
> Linux audio is finally pretty unified behind pulseaudio+alsa, so why go changing things and breaking apps?
PulseAudio seems to be as much of a solution to the confusion of sound on Linux as 'unified distros' are to the problem of numerous distros. It just adds one more option into an already crowded mix.

I would also say that unification behind PulseAudio doesn't even impact on this debate, since PulseAudio is made to be a generic sound server that can work with ALSA or OSS. If most of your applications use PulseAudio, then the sound subsystem beneath is immaterial, meaning a switch from ALSA to OSS wouldn't break anything.

---

### Post by Xbehave on 2009-10-12
> **Rhapsody said:**
> The vast majority of Linux programs are open source and either work with OSS already, use sound servers that support OSS already, or can be easily modified to work with OSS.
support for OSS is secondary in most projects and while it may work for you how much software do you use? Do you audio edit? play games? use wine? Much of the linux community has not actively maintained OSS audio, this will affect less maintained apps much more than actively developed apps but. I believe OSSv4 has ALSA emulation to work-around this (like alsa has old-OSS emulation), however if people are coding to ALSA APIs switching to OSS+alsa emulation seams a bit silly (then again pulseaudio+alsa emulation is just as dumb)


> These may well be valid, though the first is just the kernel developers going with an inferior option because of a grudge in my opinion.
That is only true if you don't consider active maintenance of a tool to be a criteria. While I'm not saying i fully agree with the decision, it is much more than a simple grudge! Code that goes into the kernel has to be maintained by somebody and that is much better done if the people writing the code can be trusted to do it.
In addition to the the kernel guys do not want complex software mixing to take place in kernelland (hence they "support" OSS by *FUSE*)

> But with OSS unsupported by most distros, it never will be tested because no one's using it, and people won't start using it until my suggestion to add it as a supported option is implemented.
The problem is that OSS support means that a distro has to maintain its own kernel code, this produced incompatible kernels (BAD), reduces security and general testing of the kernel (all distros try and stick close to mainline so they don't need to do as much testing), it also requires a lot of developer time. How much major ubuntu only stuff is ubuntu add to the kernel? AFAIK none it's not worth the effort, even apparmor is shared with novell.

> The second part can hardly be considered a fault in OSS.
Erm going closed source and not maintaining the implementation in the kernel is ONLY OSS's fault

> PulseAudio seems to be as much of a solution to the confusion of sound on Linux as 'unified distros' are to the problem of numerous distros. It just adds one more option into an already crowded mix.
Only if you do not understand sound servers would you say that, pulseaudio is a generic sound server it runs atop of alsa/oss, it "competes" with jack not alsa/oss. I say competes because jack has a different target market. If you read the linux i provided earlier there are also other features that AFAIK are not in OSSv4 such as
[LIST]
[*]moving streams between devices during playback
[*]positional event sounds 
[*]secure session-switching support, 
[*]monitoring of sound playback levels, 
[*]rescuing playback streams to other audio devices on hot unplug,
[*]automatic hotplug configuration,
[*]high-quality resampling, 
[*]network transparency, 
[*]sound effects, 
[*]simultaneous output to multiple sound devices
[*]volume-follows-focus
[*]automatic attenuation of music on signal on VoIP stream
[*]UPnP media renderer support
[*]Apple RAOP support
[*]mixing/volume adjustments with dynamic range compression
[*]adaptive volume of event sounds based on the volume of music streams, jack sensing, 
[*]switching between stereo/surround/spdif during runtime 
[*]powersaving by precise buffer control 
[/LIST]
Many/most of these features are meant to be implement at the sound server level not at the low level of alsa/oss

> **hoppipolla said:**
> I think the Gnome sound tools allow this in Karmic :)
It does that using pulseaudio

The arguments for replacing a well known and tested stack (alsa) with an unkown/untested stack (OSSv4) are simply not there. ALSA works (within reason) and pulseaudio can add the complex mixing desktop's need in userspace. What are your compelling arguments for OSS over ALSA? (other than it works for you)

Yes the road to pulseaudio was rocky, I for one did not welcome it, but it is pretty much here now and if you read my previous link you'll see why it was worth it.

---

### Post by K.Mandla on 2009-10-13
> **dragos240 said:**
> I use alsa for my arch boxes. I don't see what's wrong with it. No problems so far.
+1. Same here, I use it in Arch and in Crux, and have no problems. I didn't realize it was so problematic for people.

---

### Post by Dimitriid on 2009-10-13
Sound comes out of it, good quality. Haven't tested 5.1 or recording environments ( like 24bit 96000hz audio )

---

### Post by markbuntu on 2009-10-14
Pulseaudio strictly enforces the new sound driver security protocols which prevents user-space applications from directly accessing the harware drivers which were moved to kernel space. This is a big reason why pulseaudio was adopted even though it was not quite ready for prime time. Nothing else would do the job at the time. Since then the KDE devs have introduced the Phonon sound server for KDE4 which accomplishes the same objective.

Pulseaudio has been much improved as anyone who uses karmic can testify though there are still a few issues with pulseaudio implementation in Ubuntu but that is due to choices made by Ubuntu. And of course, ALSA driver development is lagging due to lack of resources.

Much of the old ALSA api has been deprecated and is in the process of being removed. The only thing left of ALSA these days is the hardware drivers. All other functionality has been supreceded by the new sound servers.

OSS is not really an option because it does not follow linux standard kernel security protocols. It may be OK on BSD, but not on linux.

---

### Post by malrost on 2009-10-14
I believe that the ALSA/jack approach remains superior to OSS when it comes to audio recording and multitrack mixing.

The thing that I have always loved about ALSA is the granular level of hardware access, and I believe this is why the ALSA drivers remain. I understand the gist of the security risks that forced the move to PA. But PA brought with it a level of abstraction that neglected the requirements of multitrack recording and serious audio processing.

PA It's a great approach for getting sound out of the box, but I want to get sound into the box. It appears that some of the needs for audio recording simply conflict with a robust security model.

This appears in BSD as well at an even more rudimentary level; Linux has a real time kernel option, whereas last time I checked BSD only provides real time kernel access to root.

---

### Post by FuturePilot on 2009-10-15
> **markbuntu said:**
> Since then the KDE devs have introduced the Phonon sound server for KDE4 which accomplishes the same objective.



Phonon is **not** a sound server and it does not have the same objectives as PulseAudio. It's more of an API. [http://en.opensuse.org/Phonon#Phonon_overview]("http://en.opensuse.org/Phonon#Phonon_overview")

---

### Post by markbuntu on 2009-10-15
> 
In KDE 4 developers are using a new multimedia API, known as Phonon. Phonon is intended to provide a common interface on top of other systems, such as GStreamer. [http://en.wikipedia.org/wiki/Phonon_(KDE](http://en.wikipedia.org/wiki/Phonon_(KDE))

Phonon is a new KDE technology that offers a consistent API to use audio or video within multimedia applications. The API is designed to be Qt-like, and as such, it offers KDE developers a familiar style of functionality. Firstly, it is important to state what Phonon is not: it is not a new sound server, and will not compete with xine, GStreamer, ESD, aRts, etc. Rather, due to the ever-shifting nature of multimedia programming, it offers a consistent API that wraps around these other multimedia technologies. Then, for example, if GStreamer decided to alter its API, only Phonon needs to be adjusted, instead of each KDE application individually. 

By that definition pulseaudio is also not a sound server. 

Phonon has already replaced the aRTs/ESD sound server in KDE4 and provides much the same services and functionality as pulseaudio would.

Xine Gstreamer FFMPEG etc are not and have never been sound servers, they are media frameworks/libs.

Both Phonon and Pulseaudio have simplified APIs for audio and multimedia application developers though Phonon does plan to take the multimedia part further than pulseaudio.

If you want the real facts:

[http://phonon.kde.org/cms/1005](http://phonon.kde.org/cms/1005)

If it walks like a duck and talks like a duck......

---


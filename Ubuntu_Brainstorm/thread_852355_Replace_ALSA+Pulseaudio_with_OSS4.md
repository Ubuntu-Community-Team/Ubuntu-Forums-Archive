---
title: "Replace ALSA+Pulseaudio with OSS4?"
date: 2008-07-07
forum: Ubuntu Brainstorm
---

### Post by F-3582 on 2008-07-07
Let's face it: OSS is really popular, because it's

- Strongly supported by most game/multimedia/emulator developers (easy-to-program-for interface)
- Strongly supported by major sound card manufacturers (Creative, M-Audio etc.)
- Fast with low latency
- Light-weight
- Multi-Platform

The only thing OSS (the one that ships with Linux) wasn't capable of was software mixing which led to frustration and drew many people to ALSA+Pulseaudio. I have to admit that I've liked Pulseaudio a lot, too, but I never got over the overhead it produced.

However, OSS has gone a long way since milestone 3 and could now be considered a serious threat to ALSA and Pulseaudio. Main reasons:

- Software mixing support
- Individual volume control for every single application
- easy-to-use, yet powerful control interface
- No need for a sound server, hence no additional overhead
- Now once again free software

So, how about replacing ALSA and Pulseaudio once and for all? It would be about time. Alternatively users should be provided with a quick and easy way to switch between those two without having to do [this]("http://ubuntuforums.org/showpost.php?p=4874981&postcount=2") manually.

What do you think?

---

### Post by olskar on 2008-07-07
I do not think this will be done since they have already kind of made the decision to replace ALSA and OSS with PulseAudio "once and for all" to clean up the audiomess in Linux. At least that is how I understand it.

---

### Post by zekopeko on 2008-07-07
isn't pulseaudio only a sound server? as i understood it , it only directs sound "traffic" to devices/apps

---

### Post by BlueSkyNIS on 2008-07-07
From [http://www.opensound.com/oss.html:](http://www.opensound.com/oss.html:)

> 
Open Sound System is now free for personal and non-commercial use and comes with a license key that will allow you to run OSS. The license key is valid for up to 6 months at a time after which you will need to download and install OSS again. There are no time limitations or restricted functionality during the licensing period. A permanant license key that will entitle you to free support and upgrades can be ordered here.

Maybe OSS license is not compatible with Ubuntu GPL?

---

### Post by F-3582 on 2008-07-07
This text only applies on the binary packages, as far as I know. The source is released under GPLv2. However, having installed the binaries already without inputting any sort of license key, it appears to me that this text might just be horribly outdated.

---

### Post by olskar on 2008-07-07
> **zekopeko said:**
> isn't pulseaudio only a sound server? as i understood it , it only directs sound "traffic" to devices/apps

Hm that is right, well the answer I gave was the answer I was given when I asked the very same question. I apologize! The reson I wanted OSS back then was that it supported my Creative card and ALSA did not :)

---

### Post by F-3582 on 2008-07-07
The problem I see with such sound servers is that they produce overhead. Last time I measured Pulseaudio generated twelve percent CPU usage while just having one application output sound. OSS4 does all this internally allowing up to four application to output sound at the same time (this can be expanded for sure). As already mentioned the OSS API is ridiculously easy to program for.

---

### Post by Megatog615 on 2008-07-07
Is OSS4 audio mixing on-par with DMIX/DSNOOP?

---

### Post by F-3582 on 2008-07-08
As I said, it supports up to four streams being played simultaneously with individual volume levels. Also, you can adjust the mixing quality. I guess, it is well on par.

---

### Post by rockin_goliath on 2008-07-08
Oh please God no.

We just spend so much work on implementing PulseAudio, which is far superior to ALSA and OSS. PulseAudio is not just a sound server; it has a native audio API for developers to use, which I have heard is much easier to use than anything ALSA or OSS offers. PulseAudio allows for 128 streams, can transmit audio over the network with very low latency, can create virtual sound devices, and is compatible with both ALSA and OSS. I have not noticed any significant overhead when playing audio. 

I hated the days when I had to restart X every time I plugged in my USB Headset and futz around with my sound settings just to listen to music. Thanks to PulseAudio by default in Ubuntu, I plug in my headset, and music comes out immediately. PULSEAUDIO SHOULD BE HERE TO STAY!

---

### Post by Roasted on 2008-07-11
I'm trying to learn more about PulseAudio. Granted, as I just stated, my knowledge on the subject isn't that great... but I'm trying to find a guide, something that's relatively simple and to the punchline of how to install Pulse.

All I keep seeing are pages among pages of ridiculously complex commands. And each and every single time there's a ton of warnings from the poster, which basically contradict the working state of where PulseAudio may be after the installation guide is finished.

To me, I wonder why people bother with the hassle. I installed Ubuntu. I selected Alsa. I'm done. Bam. Done. I hear music. It sounds fine. Right now, I'm listening. Yet I see all of these threads about simplifying the installation process, yet, all I see are people responding like "Hey, thanks, but it didn't work for me."

How is it so far superior if it's the biggest effin headache ever to get running? What's the purpose? The point? Am I missing something to the equation?

---

### Post by F-3582 on 2008-07-11
That's what I asked myself, as well. The I started to wonder why projects like Audacity still use OSS or JACK, but not ALSA. I figured that there had to be some advantage OSS had over ALSA. This plus the many comments out of the emulation community that OSS is the best option available.

---

### Post by rockin_goliath on 2008-07-14
Watch this presentation by Lennart Poettering, the core developer of PulseAudio, to find out what PulseAudio is all about and why we should all adopt it.

[http://mirror.linux.org.au/pub/linux.conf.au/2007/video/talks/211.ogg]("http://mirror.linux.org.au/pub/linux.conf.au/2007/video/talks/211.ogg")

---

### Post by F-3582 on 2008-07-14
I got something for you guys, too. It's written by a person who has no connection to either project (It's actually Nach, a leading developer of ZSNES). This should debunk some myths. Remember, this was over one year ago, but not much has changed, actually. Except for the fact that OSS is now truly "open".

[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

Putting an extra sound server on top of a flawed framework won't fix the framework. It just creates overhead. I'm sure all these fancy features PulseAudio offers can be added to OSS in no time. And remember, OSS has the strongest application support out there.

---

### Post by lithorus on 2008-07-15
> **F-3582 said:**
> I got something for you guys, too. It's written by a person who has no connection to either project (It's actually Nach, a leading developer of ZSNES). This should debunk some myths. Remember, this was over one year ago, but not much has changed, actually. Except for the fact that OSS is now truly "open".

[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

Putting an extra sound server on top of a flawed framework won't fix the framework. It just creates overhead. I'm sure all these fancy features PulseAudio offers can be added to OSS in no time. And remember, OSS has the strongest application support out there.
But then why only settle with OSS? Pulseaudio is by design made to support several backends. This way you only need to support 1 API compared to supporting eg. ALSA and OSS. Also the article you linked to was from May 2007 which is before Pulseaudio got really started. The article doesn't even mention Pulseaudio. Personally I've never seen any problems with Pulseaudio compared to a pure ALSA setup. Quite the opposite, with Pulseaudio I don't get any problems with applications locking the sound system.

You should really see that presentation of Pulseaudio

---

### Post by F-3582 on 2008-07-15
I wouldn't mind running PulseAudio on top of OSS, if it had some good latency (which it apparently has). At the moment I have ESD running on top of OSS handling the system sounds. If PulseAudio replaced ESD, I'd be fine with it.

I'm gonna watch this presentation, but at this very moment I don't see any advantages PulseAudio could give me over OSS.

Anyway, just a few things I noticed while playing around with PulseAudio under ALSA:

- Emulators usually create sound on-the-fly. ePSXe (CPU-heavy) didn't manage to create decent sound with neither SDL nor OSS (emulated) under PulseAudio (ALSA alone was at least bearable). OSS4, however, runs it perfectly. Other emulators, too, by the way.

- Sounds being sent suddenly to PulseAudio (the notification sounds of Pidgin, for example) usually crackle at least once while being played. Now that I think about it... this happens at the beginning of any stream that gets sent to PulseAudio. It got to the point that I really got used to it - and after switching to OSS4 I was really irritated that this glitch had vanished.

- Playing audio under heavy CPU/HDD load (compressing a video, for example), can lead to PulseAudio stuttering. I haven't met a case where OSS4 did this, yet.


Wasn't the Ubuntu philosophy "It just works"? Judging by the amount of people having problems with ALSA (not just X-Fi owners) we should really ask ourselves if there aren't any better options.

OSS4 is something that is widely supported by POSIX apps, because it is cross-platform and easy-to-develop for (Poettering honors that fact, too, by the way, but he seems to have missed that OSS now supports software mixing and individual memorizable volumes for each application).

I think more people should actually be made aware that there is a good alternative to ALSA, again. Ubuntu should have enough influence to do this first step. considering Mark Shuttleworth just suggested that Gnome should start using Qt ;)

---

### Post by NightCrawler03X on 2008-07-16
I voted "Yes, but make ALSA optional."

EDIT:
And for the record, I use OSS4 on my machine (running Archlinux).

---

### Post by weltall2 on 2008-07-16
I agree with F-3582 pulse audio gives too many problems than those it should fix. right now I've setup gnome to use alsa and everything including mixing works fine, personally i don't really care about separate volume levels, i just care about working things and pulse audio is "just not working"

starting with emulators being unusable with it (2 second of delay are you making fun of me?) or being full of crackles either with pulseaudio output functions and pulseaudio wrappers to oss (as most emulators doesn't support alsa entirely, at least internally); then we have the series of applications which doesn't run at all trough pulseaudio or it's wrapper (i have a game which just segfaults if ran trough pulseaudio wrappers). I've never understand the need to switch to pulse when it doesn't fix the alsa bug about oss emulation which disables dmix and makes dmix completely unusable when pulseaudio is in control (what's the reason i can't use pulseaudio applications and alsa applications together? why pulseaudio has to lock the alsa device entirely?).
Network audio? all the problems pulseaudio gives, starting from lag, high cpu usage (10% on a 2ghz core2duo? are you making fun of me? just to mix some streams... oh wait i'm running only one application so it's not even mixing anything 10% of additional cpu for nothing WOOOW even better than vista), missing support on a great array of applications and cracking/crashing on wrappers; just doesn't justify that thing. it should be optional just like in gutsy if you really need it for network audio install it else do nothing.

if you look at oss4 features it's actually better than alsa, pulse audio and alsa+pulseaudio for the desktop user...

---

### Post by mc4100 on 2008-07-16
> **weltall2 said:**
> 
personally i don't really care about separate volume levels, i just care about working things and pulse audio is "just not working"

I agree, it's not really been working: there are tons of bugs, and I think it was put in far too early. However, that said, it provides many features which are needed to compete with *other* modern desktops. I'm a fan of PulseAudio and it's features, yes it has its issues, but moving to a whole 'nother implementation which does essentially the same thing isn't, IMO, the way to go. Just fix Pulseaudio. 

> **weltall2 said:**
> 
2 second of delay are you making fun of me?) or being full of crackles
Have you tried the fix-guide that was floating about one the fora (It involves upgrading to newer packages), it fixed most of my issues, like the delay and stuttering; I'll post a link when I find it.
> **weltall2 said:**
> 
high cpu usage (10% on a 2ghz core2duo? are you making fun of me? just to mix some streams... oh wait I'm running only one application so it's not even mixing anything ...
I don't see this - I definitely agree that it's more than if you used Alsa exclusively - but on my 1.6 Ghz Core Duo, it uses 4% with one app (Rhythmbox) and both cores are scaled to 50%
(EDIT: It has nice -11, which I changed via that guide, don't know if that might be why.)

EDIT, again: Here's the link,
[http://ubuntuforums.org/showthread.php?t=789578&highlight=fix+pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=fix+pulseaudio)

---

### Post by weltall2 on 2008-07-17
> **mc4100 said:**
> I agree, it's not really been working: there are tons of bugs, and I think it was put in far too early. However, that said, it provides many features which are needed to compete with *other* modern desktops. I'm a fan of PulseAudio and it's features, yes it has its issues, but moving to a whole 'nother implementation which does essentially the same thing isn't, IMO, the way to go. Just fix Pulseaudio. 


Have you tried the fix-guide that was floating about one the fora (It involves upgrading to newer packages), it fixed most of my issues, like the delay and stuttering; I'll post a link when I find it.

I don't see this - I definitely agree that it's more than if you used Alsa exclusively - but on my 1.6 Ghz Core Duo, it uses 4% with one app (Rhythmbox) and both cores are scaled to 50%
(EDIT: It has nice -11, which I changed via that guide, don't know if that might be why.)

EDIT, again: Here's the link,
[http://ubuntuforums.org/showthread.php?t=789578&highlight=fix+pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=fix+pulseaudio)

Thanks.
I've tried following the parts i might have needed from that guide.
While it fixed some problems (no more lag and stuttering in emulators (except the fact that sdl in zsnes is broken pratically as it stutters when moving the mouse and it's not kernel fault...) (other applications were fine even before) and some alsa applications can output from pulseaudio). But there are still issues for example: 
some applications in this case i've tried planeshift which is a crystal space based game gives no output at all trough the alsa device (trough oss it was working, trough padsp it was segfaulting) also skype worked for a bit and then stopped outputting audio and is likely to crash upon closing it (the pulse connection seems to stay stuck or whatever), also some windows applications under wine worked while other didn't... for example oblivion is one of these so you have to switch from padsp + oss (or better pure oss trough emulation as else it will crash upon going in game and be mute in main menu with some assertions... but then dmix will stop working for another bug... yes i call it so... of alsa) and alsa continually. This means that the situation is still too annoying for a daily use... i can't change options and use the terminal casually after 10 tries of song output not working

IMHO even 4% of cpu usage is too much for doing no mixing... and 2% for doing completely nothing...

Personally i still prefer an oss4 implementation with no additional layers as from what you can read from the official wiki it has these functions, making it so at the level of other modern os (also because to be at the level of a modern os you must also provide seamless audio playback without changing configuration system/application wise continually and manually):
>     *  Supported audio formats
          o Supports 8/16/24/32 bits/sample audio formats
          o Supports sampling rates from 8KHz up to 192KHz
          o Supports mono, stereo, quad, 5.1, 7.1 and multichannel audio devices 
    * Transparent Software based Audio Mixer
          o Allows applications to share the same "real" audio device regardless of what format is requested by the application.
          o Supports recording and full duplex in addition to playback.
          o Ability to mix stereo and multichannel audio streams up to 7.1/192Khz/32bit.
          o Supports full 24 bit range without loss of precision during internal computations.
          o Each application has its own independant volume controls.
          o Supports loop back recording. This enables you to "record-what-you-hear". Typically this is useful for recording streaming audio or trapping audio from applications 
    * 64bit internal processing guarantees audio fidelity and precision if the audio data needs to be converted.
    * New device enumeration and mixer API makes it very easy to manage devices programatically. 

---

### Post by F-3582 on 2008-07-17
> **mc4100 said:**
> I agree, it's not really been working: there are tons of bugs, and I think it was put in far too early. However, that said, it provides many features which are needed to compete with *other* modern desktops. I'm a fan of PulseAudio and it's features, yes it has its issues, but moving to a whole 'nother implementation which does essentially the same thing isn't, IMO, the way to go. Just fix Pulseaudio.

The thing is: What would you call "other" impleentation? OSS has been around for the longest time, even longer than ALSA. As already mentioned, OSS support had been dropped because of some liensing issues, but it has recently gone open-source again (one year ago). As you can see, many performance-critical applications - mostly games - are using it while most developers call ALSA a crufty, undocumented mess of an API. Also, OSS is officially supported by most sound card vendors and porting ALSA drivers to OSS (those which actually work) should be a lot easier than trying to convince your local sound card vendor to develop ALSA drivers with this discussion going.

Basically, the title of this thread should be: Please replace ALSA with OSS4, because ALSA is crap. PulseAudio can run on OSS4 just fine and can be sit there idly until the end-user decides to let an application make use of it. But please make it optional, because your normal end-user won't need all those fancy capabilities, anyway.

How many people do you know who have their own home entertainment system sending audio streams over the network synchronizing them to a video signal that is still running on that system? Sounds a bit like AirTunes, by the way ;) Or do you know anyone operating thin clients who need constant audio streaming from the terminal server? For these appliances you can install PulseAudio, if you like, but the normal end user won't need these features.

The normal end user wants an audio API that just works and why should we neglect the API with the widest adoption across all Unixes and GNUs? Every game, every emulator uses OSS by default, every media player has an OSS output, Skype uses OSS. Why not switch back, now that OSS is finally a reasonable choice, again?

---

### Post by F-3582 on 2008-07-18
Me be bumpin'

[This]("http://blog.rastageeks.org/spip.php?article7") is just in:

There will be an official Debian package, probably only containing the GPL'd version of OSS4 (not containing any closed source drivers - Creative users, anyone?). However, as far as I know you can use ossupdate to "fix" this. Maybe Debian-Multimedia will release the full version.

---

### Post by feld on 2008-07-18
I was just about to make a poll regarding this.

Here's the deal guys:

Linux audio is a mess. We have a million APIs and a billion more sound servers. This is just totally unreasonable. Let's look at Pulseaudio and ALSA as that's our main discussion point:

ALSA: Undocumented mess of an sound system and 100% incompatible with other unices. Who wants to write professional audio applications specifically for Linux? Why target one platform when you can get other Unix systems working at the same time when you can target OSS and have it working everywhere? I've even talked to developers who run into broken/lying sound drivers for ALSA on a regular basis. It's not just commercial applications -- people these days generally care about having their audio work on both BSD and Linux. Some extend it as far to work on Solaris and others.

You have to remember guys, Linux isn't alone in this world. We rely a lot on developments of other Unix operating systems. By choosing to go the route of ALSA we're breaking compatibility and creating more issues. Reinventing the wheel isn't exactly something we should be doing at this point. Taking the current  wheel and perfecting it is what 4Front's OSS implementation does, and is what we need to be focusing on.

Look at Pulseaudio. It has an amazing resume, but fails to deliver. Ever tried Hardy with Quake3(including ioquake3)? Quake4? ETQW? Those are specific applications I've found to completely and utterly fail under Pulseaudio. The sound is crackly. ETQW the sound is delayed by like 2 seconds. What happened to this "low latency" sound server? How are we to get low latency by adding MORE abstraction layers? It simply doesn't make sense.

I talked to Timothy Bessett, Linux programmer of ID software regarding ETQW and gave him some debugging output -- Pulseaudio is lying about what frequency it's using when it pretends to be a direct ALSA implementation. It's 100% on the Pulseaudio side. I tried contacting the main Pulseaudio developer and he gets all defensive saying his implementation is perfect, when clearly it is not.

There are constant reports of issues with Pulseaudio -- crackling audio, poor audio quality, latency issues, and things just not working anymore. Skype doesn't work very well, nor does Teamspeak. They might not be Open Source, but that's their decision. They're still applications people use every day. (Don't offer me alternatives, I know them all and also use them!)

Now let's try this with 4Front OSS.
Quake3, Quake4, ioquake3, Teamspeak, Skype (static/oss version), and more all work 100% perfect. No audio crackling, no latency issues. In fact, I can actually use Skype, Teamspeak, and Mumble at the same time for mic input! If I try to use Teamspeak and Skype the same time with ALSA, Skype crashes!


No audio quality issues? Check
Low latency? Check
All applications on my system working perfect? Check
Not breaking legacy support & compatible with other Unices? Check
Per application audio controls? Check
Open source? Check


It is completely irresponsible as a community to continue to use ALSA as our sound system. For those people who need it, Pulseaudio can be installed. Those people are going to be few and far between, because its only real feature now is network audio.


Please, Ubuntu devs, take this seriously. If you choose to do the next release with Opensound OSS you're doing the open source community a HUGE favor. Opensound OSS is growing every day in users and developers. They offer sound drivers (Xfi) that ALSA doesn't. Okay, so they have a driver (only one that I know of) they couldn't open source -- big deal. We'll work around it. It's what we always do.

Do the right thing and let's fix this stupid Linux audio catastrophe.

---

### Post by Roasted on 2008-07-18
This is kind of ironic.

Alsa is the only thing that has ever worked for me without a month's headache of troubleshooting.

Then again, I never really gave OSS a real chance, but Alsa does everything I need it to.

I'm curious, though. Perhaps I'll try OSS on Hardy later tonight and see what happens.

---

### Post by F-3582 on 2008-07-18
[This guide]("http://ge.ubuntuforums.com/showpost.php?p=4874981&postcount=2") helped me a lot. You might have to remove libflashsupport and install the package manually with dpkg, if GDebi refuses to open it (I had to).

---

### Post by Megatog615 on 2008-07-19
I'm confused.

Is OSS4 *really* open-source(GPL)? There's a disclaimer about me having to redownload and install the package every so often, and no commercial usage.

One question:
Does OSS4 have a mixer like alsamixer?

---

### Post by F-3582 on 2008-07-19
There's actually two releases. One is binary-only and contains all the closed-source drivers, too. And yes, you have to reinstall the .deb all six months, unless you type ossupdate in the terminal which "activates" OSS4 for free for ever. And I don't have a clue why it does that.

The other one is source-only (licensed under GPL) and won't contain those closed source drivers. I hope that whoever is is going to package it for Debian (there is a guy) might release the GPL version in Main and the other one in Non-Free.

---

### Post by ramenite on 2008-07-19
Yeah, I have to get onboard with OSS here.

If this ALSA/Pulseaudio setup actually worked, maybe this discussion isn't taking place. But some applications haven't worked, what does work with me with the default setup crackles. Just doesn't work well.

All went away with using OSS. It's easy to install, and works better. A couple issues that I have had, were solved by this thread and their wiki. And these issues were more do to Ubuntu. Like gstreamer plugins being behind and not having the OSS4 support in the new versions. And libflash being alsa only.

And I'm not even saying that ALSA/Pulseaudio should just be dropped. Just take the handcuffs off the people that want to use OSS. Keep the gstreamer plugins up to date. Package the OSS support for applications that do have it. That isn't too much to ask.

---

### Post by Roasted on 2008-07-19
Little something I want to throw out there with the crackling with Alsa...

I am currently running Alsa, and I understand the crackling you are speaking about. If I sound like I am talking down to anybody and you already know this, I apologize.

But sound on a computer is a very similar to car audio... and I had a few years in car audio so I remember a couple settings on car amps and what they did and how they functioned. 

PCM, which is an option under alsamixer, controls the decibel gain. The higher the gain, the louder things get. Same way on an amp. However, there's a point on the gain where you have to watch it. If I cranked my gain on a car amp to 100%, the sub would start to, what we car audio enthhusists called, "farting". The sub would receive a clipped signal and sound like ****. If you backed off the gain, less distortion, clearer sound, bam, done.

PCM is the same way. Notice in alsamixer (terminal - type 'alsamixer') when you adjust the PCM, it tells you the db gain for each setting? 

I adjusted mine so it's 0.00 db gain, however, I've noticed I can take it considerably higher in most cases before it starts to crackle out. But, by default, PCM seems to kick itself to 100% on certain applications, such as Audacious. Audacious can handle 100% PCM and sound clear, however, the default volume level with Audacious is quieter than say, Amarok. So, they sort of compensate one another, whereas with Amarok, you want your PCM to stick around 75%, then you can put your volume 100% and it should still be clear. My PCM stays at 75%, and I adjust the volume accordingly to what I want. If I open another music program and it's crackling, I immediately check alsamixer, due to the fact (as I mentioned earlier) sometimes other apps cause the PCM to kick to 100% when you open them. 

Which, btw, if anybody can tell me how to permanently lock in my PCM level across all applications, that'd be great!

But, at least in my experience, this is what I've found. I welcome anybody to correct me... this is simply speculation from my car audio experience that I've noticed on my Ubuntu Hardy machine. :)

---

### Post by mriedel on 2008-07-23
Hell no.

ALSA/Pulse needs some serious fixing, but OSS is a mess no less.

X-fi support is marketing only. The card can produce sound but there's no mixing at all so it might as well not work at all for me.

ossxmix is a joke. The interface is messy as hell.

Then there's the never-ending licensing struggle with OSS. Some drivers are not completely open-source and the oss binary setup clearly shows relics of closed-sourcedness (ossupdate etc).

Furthermore, I feel like I'm getting reduced sound quality with OSS. I have yet to find _any_ advantage that OSS has over ALSA/Pulse.

Edit: Also, Pulse is becoming amazing, as it seems.

---

### Post by F-3582 on 2008-07-23
Well, OSS4 still has an advantage in latency. However, once Pulseaudio gets its glitch-free extension in version 0.9.11, this advantage will be lost, as well. I'm pretty excited at the moment (could be caused by the amount of coffee I just drank ;)).

---

### Post by Megatog615 on 2008-07-24
Could you post some more details on that please?

---

### Post by F-3582 on 2008-07-24
It might be a little hard for me to explain, so I'll let Lennart Poettering [do it]("http://0pointer.de/blog/projects/pulse-glitch-free.html").

---

### Post by Slug71 on 2008-08-03
This is probably a really stupid question as im a noob, but isnt PulseAudio required  whether you have Alsa or OSS? If thats the case then they should just both be made available and let the user decide which he prefers on their system. I think the biggest thing id like to see regardless of what we get is that the versions of all of the above can be updated through the update manager as newer versions are released.

---

### Post by F-3582 on 2008-08-03
Not required, but it can make things a lot easier for developers, in case you have ALSA. At the moment the Pulseaudio implementation Ubuntu ships with lacks a few crucial things, like good latency and efficient CPU usage. I hope that version 0.9.11 will arrive soon.

---

### Post by otchie1 on 2008-08-03
Accept it or not, and I'm telling you not asking, both ALSA & PulseAudio are pieces of junk with compatibility minefields just waiting to snare you.

Here, have a 'for instance'.
A simple SBLive (one of millions).
Simple front & back speakers.
Simple browser multimedia streaming whislt playing background music from RhythmBox.

Pulse CAN'T do it (no rear audio and only allows one stream at a time).
ALSA CAN'T do it (no rear audio and only allows one stream at a time).

OSS, just turn it on and it works perfectly. No configuration, no gedit, JUST FREAKING WORKING.

Whoever is leftover from the days when Linux devs threw a hissy fit and debarred OSS needs to wake up - it is now, always was and will always be better than any PoS cooked up to beat it.

---

### Post by otchie1 on 2008-08-03
> **Roasted said:**
> This is kind of ironic.

Alsa is the only thing that has ever worked for me without a month's headache of troubleshooting.

Then again, I never really gave OSS a real chance, but Alsa does everything I need it to.

I'm curious, though. Perhaps I'll try OSS on Hardy later tonight and see what happens.

I've been recommending the installation of OSS to cure ALSA headaches for years - works EVERY SINGLE TIME.

---

### Post by smartboyathome on 2008-08-03
Well, the cons to it, as expressed [here]("http://wiki.archlinux.org/index.php/OSS"), are basically that a few features implimented in Alsa/Pulseaudio (software-emulated 3D enhancement, reverb effect, and equalizer) have not been implimented in it yet. If these go into it (especially 3D enhancement and equalizer), then it is a sure in for Ubuntu, imo. :)

---

### Post by nerdy_girlscout on 2008-08-05
I just voted "Yes, OSS4 is here to stay!". I tried to live with ALSA for a month or so, but I got really frustrated, and then I installed OSS again. Once again I got problems specific to the bad support in Ubuntu (portaudio needing a recompile, System Settings crashing in KDE), but apart from that it works as it should.

I immediately simply switched driver used in winecfg and SMPlayer and sound is good again. Multiple streams at once! Ohh I wish this was default in Ubuntu. But it probably won't happen.. It seems like it's easier to remove ALSA now than it was before though.

---

### Post by mailmaldi on 2008-08-05
I am not an expert on either alsa or oss or pulse, I have not even been a regular linux user till a few months ago, due to varied reasons, one  of the issues being it seemed that sound quality in linux always seemed to be much poorer as compared to windows (despite trying all kinds of stuff with alsa...).
But just last week, i installed OSS4, and i can definitely say that audio quality has really improved sound quality.
Sure some things have broken, like volume applet and shortcut keys, but theyre gnome specific I think and well worth the sacrifice.

I dont want to diss alsa , but it would be quite nice to atleast have the option of installing OSS with everything working fine on ubuntu, after all freedom of choice innit?

---

### Post by billenbois on 2008-08-08
not all OSS drivers are open source. that's why it wont be accepted.

change that and none will care if you replace ALSA.
until then, we're better off fixing ALSA.

---

### Post by weltall2 on 2008-08-12
if they are in alsa you can use them as reference for doing new ones, if they aren't even there it won't change much if they are there or not ... just don't ship them (they could always be provided by mediubuntu for example for people with those devices which have no audio support already now and could get it with closed oss4 drivers)

---

### Post by Roasted on 2008-08-12
> **otchie1 said:**
> I've been recommending the installation of OSS to cure ALSA headaches for years - works EVERY SINGLE TIME.

Oh?

I have alsa.

I have no headaches.

I installed OSS due to individuals like you pushing it.

I got a headache.

:lolflag:

---

### Post by coolen on 2008-08-29
Hell no.

The reason? ALSA is standard on Linux. PulseAudio is increasingly popular, and will probably be the de facto standard in a year or two.

PulseAudio supports more advanced features, such as network transparency.

OSS's configuration utility is far from simple. It took me ten minutes just to figure out how to mute my internal speaker.

OSS does not have jack sensitivity (plug in headphones, internal speakers remain on).

I fully support easier setup (putting it in Universe, for example), but it will not be default in the foreseeable future, nor should it be, in my opinion.

Also, PulseAudio is cross-platform. This includes Windows, while I'm pretty sure OSS works on Unix variants.

---

### Post by Slug71 on 2008-08-29
Yeh i must say, Alsa seems to be working great for me at the moment!

---

### Post by weltall2 on 2008-08-30
> **coolen said:**
> 
The reason? ALSA is standard on Linux. PulseAudio is increasingly popular, and will probably be the de facto standard in a year or two.

PulseAudio supports more advanced features, such as network transparency.


you have missed the continued problems with applications, skips etc (no these "fixes" doesn't work for everything, games are the ones being ruined mostly by pulse) caused by it and the nice cpu uber usage feature to do no mixing

> 
OSS does not have jack sensitivity (plug in headphones, internal speakers remain on).

neither alsa does for hda devices of one year ago and personally i prefer this way so i can output from both and change the values directly from the mixer. Personally i hate the windows drivers which forcily disable the speaker when i use the headphone. it only seems an artificial limitation.
oh i was forgetting one thing on the 2.6.27 kernel my audio device has become unusable as the separate mixer levels for speaker and headphone  have disappeared and i can output to the headphone only with the speaker enabled... and it must be enabled with a checkbox with a strange name... yeah jack sensitivity :P

> 
Also, PulseAudio is cross-platform. This includes Windows, while I'm pretty sure OSS works on Unix variants.

and then? do you think windows application will support pulseaudio? there is no reason to do that as the windows audio system is actually something working... and windows has even his network audio solutions with terminal server which are also working...


if oss support on alsa would be fixed (support for mixing) i'd be perfectly fine with it ... but pulseaudio isn't a solution and personally "network audio" isn't something valuable enough to explain the presence of something barely working for daily usage which won't do "network audio" in the 90% of desktop systems (comeon not everyone uses x export functionalities... there is a big bug which i'm looking forward to be fixed since gutsy on ubuntu about xdcmp why it's still unfixed? there must be a large amount of people requiring it eh...). neither usb hearphones are so frequently used and for sure you don't detach them continually to explain the usage of pulseaudio. 

I've recently removed everything using pulseaudio and setup everything for alsa now all works better except applications using oss because of the mixing problem of alsa with the oss emulation...

oh i forgot one thing ... something I've never understand if someone could explain this to me i'd be grateful to him:
1) why pulseaudio locks alsa when used? and why if alsa is being used pulseaudio can't go with dmix? if these problems wheren't present i'd not have problems with pulseaudio, it would be a nice addition to workaround alsa oss emulation problem.
2) why if pulseaudio can't get to use the alsa device the applications using it will pratically "freeze" in a certain way? gsstreamer, flash, audacious (this was entirely frozen requiring a kill) and a lot others have this problem. shouldn't pulseaudio be able to just silently drop the audio to null if the first problem isn't resolvable?

---

### Post by coolen on 2008-08-30
So, you prefer no jack sensitivity, despite the fact that most people expect it, so clearly this is the way to go?

Sorry, but that alone makes it unsuitable for the average user. It's expected behaviour. The average user can't be expected to know how to bind a key to mute the internal speakers.

Deficiencies in ALSA/PA should be addressed there, and likely are. I'll admit that the implementation of PA in Ubuntu was not great, and could have been held back until it stabilised, but abandoning it for OSS which, as I mentioned, does not behave as expected and doesn't have a decent GUI, is not the answer, not to mention the work involved in shifting the entire platform to OSS.

I use OSS, and I too kind of like the fact that my speakers don't magically mute when I plug in headphones (or unmute when they fall out). I voted to have OSS as an option. I'd like a good implementation of OSS4 available from the repos with minimal fuss, and a level of ease in switching between the two, but making the change default would be a lot of work, would confuse users, and would alienate Ubuntu from the rest of the Linux community (who largely use ALSA, and increasingly use PA).

Oh, and I can't answer your questions technically. I assume PA blocks ALSA because PA is meant to be a total solution. However, there are still a number of programs which don't work with it, and blocking ALSA altogether might be a bad idea until this is sorted.

---

### Post by weltall2 on 2008-09-03
> **coolen said:**
> So, you prefer no jack sensitivity, despite the fact that most people expect it, so clearly this is the way to go?

Sorry, but that alone makes it unsuitable for the average user. It's expected behaviour. The average user can't be expected to know how to bind a key to mute the internal speakers.
I'm saying that it doesn't work correctly on hda devices of one year ago and if it did it should be selectable, you are actually removing a feature by not letting you also select the volume of both or allowing both to run at the same time.
additionally I've lost a good amount of mixers from alsamixer

> 
Deficiencies in ALSA/PA should be addressed there, and likely are. I'll admit that the implementation of PA in Ubuntu was not great, and could have been held back until it stabilised, but abandoning it for OSS which, as I mentioned, does not behave as expected and doesn't have a decent GUI, is not the answer, not to mention the work involved in shifting the entire platform to OSS.

I use OSS, and I too kind of like the fact that my speakers don't magically mute when I plug in headphones (or unmute when they fall out). I voted to have OSS as an option. I'd like a good implementation of OSS4 available from the repos with minimal fuss, and a level of ease in switching between the two, but making the change default would be a lot of work, would confuse users, and would alienate Ubuntu from the rest of the Linux community (who largely use ALSA, and increasingly use PA).

well then no one is going to adress alsa deficiencies with oss how are we going to fix this?
Also ALSA doesn't actually *have a GUI* it has a cryptic configuration system based on text files which seems more an application than a configuration file and bad documentation... but at least it's not the only thing with bad documentation look at gtk... you have to go for trial and error for most things or reading the sorce itself.... quite time taking as something like gtk is supposed to make developer life easier by abstracting some things, just like a sound api should after all...

Well as for alienating the linux community is alienating from the entire *nix community. That's why i think the correct way of doing this is merging back oss in the vanilla kernel

another thing PA has been the direction of only the distributions with gnome as it has been officially suggested by the gnome developers (or at least who writes in the official site). already kubuntu is missing it and they are living sound better

> 
Oh, and I can't answer your questions technically. I assume PA blocks ALSA because PA is meant to be a total solution. However, there are still a number of programs which don't work with it, and blocking ALSA altogether might be a bad idea until this is sorted.

it is a bad idea always even if everything worked correctly with PA.

---

### Post by feld on 2008-09-21
OSS4 does have jack sensitivity in the newly rewritten driver that's in the mercurial repository.

Perhaps you guys should do some research.

---

### Post by markbuntu on 2008-10-16
Well, we will see. If I can ever get Intrepid to boot on my machine I will give OSS4 a whirl and see what it can do. I have a bunch of audio devices that I have working on ALSA-Pulse. We will see if OSS4 is so lucky.

---

### Post by lowlymarine on 2008-10-17
> **mriedel said:**
> X-fi support is marketing only. The card can produce sound but there's no mixing at all so it might as well not work at all for me.

As someone with an X-Fi, I strongly disagree with you.  The fact that it can produce sound is leaps and bounds better than ALSA, which *can't*. You're right that ALSA isn't a case of "might as well not be working" - it's instead simply "it *isn't working at all*."  And actually there is perfect software mixing in the 4.1 RC build from source.


> **coolen said:**
> OSS does not have jack sensitivity (plug in headphones, internal speakers remain on).
Also not true, though again I'm using the mercurial version, not the older .deb.

---

### Post by weltall2 on 2008-11-23
intrepid seems to have an even worse pulseaudio implementation than hardy. Not only the situation didn't improve but now it's taking as hostage alsa from bootup till shutdown with no way to output to alsa without killing pulseaudio. way to go! now I've to rename the pulseaudio binary if i don't want to remove packages and working audio with something different than the media player (as chmod -x doesn't block it from being executed)

---

### Post by loomsen on 2008-11-23
Just zip it, you won't run into trouble then.

gzip /path/to/pulseaudio, most likely

```
sudo gzip /usr/bin/pulseaudio
```

chmod +x actually makes it eXecutable ^^

However, mine started working recently...

---

### Post by Zorael on 2008-12-03
Well, as already said, it's not a fair matchup. Pulse is just the sound server and still plays its stuff via ALSA libraries and drivers, like a man-in-the-middle attack. If Pulse could play nice with OSS4, people could still write stuff for Pulse, and us with major ALSA driver issues (Intel HDA) could use our OSS drivers while enjoying Pulse goodness.

So, I'd very much like to see OSS4+Pulse, please.


[*"Using non portable APIs is what is deprecated."*](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

---

### Post by Twitch6000 on 2008-12-03
My laptop does like OSS alot better then Pluseaudio....

So I wouldn't mind :).

---

### Post by Roasted on 2008-12-03
In Hardy, I can see this being a valid discussion.

With Intrepid, I haven't had a SINGLE issue on ANY computer I installed Ubuntu on. And I work in IT support!

I wouldn't mind OSS being an option... but standard? Haa...

---

### Post by Progressive on 2008-12-19
OSS screwed themselves by going temporarily insane...err... proprietary.

It is very unfortunate. If it is true what they say about ALSA being hard to code for, then that is a shame. Luckily, PulseAudio and KDE's Phonon framework should make coding easier, if I understand correctly.

Granted, I sincerely hope the OSS people keep improving their code, since it helps everyone. If it becomes good enough eventually it will be impossible to ignore, but as it stands now, whatever features it has are likely in the works now or made irrelevant by these other abstraction layers.

I'm amazed at how quickly the statements on here from October became irrelevant. My X-Fi is working just fine without OSS thanks to the GPL'ed driver. :)

---

### Post by gfxfreak on 2008-12-20
Here are my two cents:
Certainly I'm new to linux at all but I've tried almost every audio API combination mentioned here (ALSA alone, ALSA+Pulse, OSSv3, OSSv4) and on diferent hardware: onboard and hardware-mixing capable cards (SBLive!).
I think OSSv4 should stay because let's face it, end-users won't care about fancy options that Pulseaudio has, they just want their sound WORKING, that means: per-application volume control, clean and fast software mixing (kernel level). Remember that the majority of end-users also doesn't care about sound cards, they just use onboard solutions expecting them to work and eventually OSSv4 is the best choice for onboard solutions.

Personally I stay with ALSA on my main machine, why? because I'm a performance freak, I have a SBLive! and love ALSA's hardware mixing paired with good multi-channel support (which OSSv4 doesn't have, hardware mixing only works on stereo, and multichannel only with software mixing).

And regarding Pulseaudio...it is truly a mess, I had to figure out how to make openal games output to pulse, I mean, is this a joke? every single user wants their favorite video game to actually works! and don't forget Pulse's CPU usage, getting choppy audio while using audacious and compiz-fusion on a dual-core machine(Radeon X1650XT + 1 GB RAM by the way)? give me a break, removed pulseaudio - stick with alsa/hardware mixing and choppy audio disappeared for all.

Oh yeah, OSSv4 works and every single game and app out there, face it guys, OSSv4 is awesome.

---

### Post by markbuntu on 2008-12-21
Ok then, tell me how to get my two sound cards and usb headest and usb webcam all working at the same time with OSS4?
And how to stream my music over my local network?

Anyway, if you have an X-FI card, the latest alsa driver from creative seems to be working?

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

---

### Post by gfxfreak on 2008-12-24
> **markbuntu said:**
> Ok then, tell me how to get my two sound cards and usb headest and usb webcam all working at the same time with OSS4?
And how to stream my music over my local network?

Ok, you got me with Pulse's nice and unique features, but since this is Linux you can choose whatever option you prefer, I mean, many (if not most) of the general and mainstream users use just one soundcard , so don't you think the best choice for them is OSSv4?
Look, I've voted "Yes, but make ALSA optional" oh yeah, and excuse my rant about Pulse's CPU usage, I don't like it, sincerely. 

Maybe if ALSA had a kernel-level software mixer just like OSSv4's vmix...what a dream :lolflag:

---

### Post by smartboyathome on 2008-12-24
By the way, getting your music over the network should just be the same. For example, using shoutcast (which many programs support), just output the audio to a stream, which you can access in other places.

---

### Post by saulgoode on 2008-12-25
In its current form, OSS4 is not an acceptable replacement for ALSA owing to OSS4's development process. Though it is GPLed, all development seems to be controlled by a single company. There is no public CVS/SVN/GIT repository, no bugtracking system, and little transparency in how decisions are made in its development. 

Should 4Front Technologies choose to withdraw their support of the Free version of OSS4 (in order to focus on their commercial version or other interests), the Linux community would be presented with the prospect of instituting a completely new development infrastructure to replace OSS4's current obscure model. This is basically what occurred with the previous OSS, and ALSA was spawned as a result. Why go through this again?

Projects which are to be included as a major system component of GNU/Linux, that contain significantly complex code, and upon which developers are expected to rely, need to be managed openly and transparently. It may be acceptable for small standalone apps such as a desktop clock to be privately developed and the code "thrown over the fence" to the GNU/Linux community, but it is not a reasonable approach for something as important and non-trivial as the core sound architecture of the system, regardless of any potential technological benefits.

---

### Post by super carrot on 2009-03-16
Replace ALSA+Pulseaudio with OSS4? 

Absolutely! I couldn't agree more, and lets do it as soon as possible. PLEASE.

We now have access to the source, we can send patches if we want to, if it all goes wrong, it can be forked.
There is a bug tracker, there is absolutely nothing getting in our way. AND it is simple to write to! This will always be a big thing for people writing applications. It is good quality. I say, lets move over, is anyone from Canonical reading this?

---

### Post by Flag on 2009-03-19
Anything as long as it works

---

### Post by markbuntu on 2009-04-08
OSS was the sound server but then they took it private. Now they are back with OSS4. We don't need to and will not go through that again.

---

### Post by simtaalo on 2009-04-08
i wish i had the money to pay for everybody involved in alsa/PA/OSS etc... to be locked in a room and told to standardise audio on linux. i'm not bothered which solution is picked but audio is the one area where having lots of different projects is counter-productive and hurts the community as a whole.

lots of people seem to have problems with pulseAudio, wierdly on my system if it isn't running then things go wrong. having said that the other day pulse started demanding a stupid amount of cpu capacity, which i'd never had before.

something needs to be done, if OSS4 makes life easier for everyone then that should be the one.

---

### Post by soltanis on 2009-04-09
This thread is exploding pretty quickly.

My 2 cents:

OSS sucks. When I used OSS, only 1 application could play sound at a time and it was slow as hell. Volume controls didn't work at all. Input was 100% broken, got nothing on the mic.

Pulseaudio sucks. Really, don't fix something that isn't broken and especially don't do it with something like pa whose server doesn't seem to understand the concept of accepting a connection or playing a sound.

Alsa sucks, but at least it freaking works. After the mess I've been through, I'd rather have a working, bad sound system that hiccups versus a broken sound system that dies when I ask it to do something.

---

### Post by KhaaL on 2009-04-18
> **soltanis said:**
> This thread is exploding pretty quickly.

My 2 cents:

OSS sucks. When I used OSS, only 1 application could play sound at a time and it was slow as hell. Volume controls didn't work at all. Input was 100% broken, got nothing on the mic.

Pulseaudio sucks. Really, don't fix something that isn't broken and especially don't do it with something like pa whose server doesn't seem to understand the concept of accepting a connection or playing a sound.

Alsa sucks, but at least it freaking works. After the mess I've been through, I'd rather have a working, bad sound system that hiccups versus a broken sound system that dies when I ask it to do something.

i agree. the thing with ossv4 id that it supports x-fi series, the ONLY way to get any sign of life from it under linux

---


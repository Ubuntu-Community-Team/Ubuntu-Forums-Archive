---
title: "Linux Audio - Back to the drawing board?"
date: 2008-11-20
forum: The Cafe
---

### Post by Tom Mann on 2008-11-20
First we had OSS - a fairly capable sound system but with a lack of hardware support - so ALSA was draughted in.

ALSA gave OSS support, near zero latency but regrettably lacked any kind of sound server. So some individuals came up with PulseAudio...


Don't get me wrong, I know GNU/Linux usually has one program do one job and do it well, but surely the above should be contained in one service? Add JACK to the mix for audio professionals and you spend more time messing around setting up an Audio environment than using it.

(This is just my opinion)

Is it not time to either:

a) Consolidate these technologies into one overall sound system, where low latency and multiple audio streams can be handled?

or

b) Go back to the drawing board, and redesign the sound system to handle all of these from the start?

As a musician, being slightly spoilt by one sound system, as supplied by Windows or OS X, it seems a backwards step in starting one sound system for multiple streams (pulse) then shutting down to start up another for audio (JACK)

I admit the above has some merits - and certain features (ie connection graphs in JACK, multiple application volume sliders) are fantastic. But why three systems?

---

### Post by kevin11951 on 2008-11-20
> **Tom Mann said:**
> why three systems?

Because of exactly what you said, the first wasn't good, so they made another, and so on...  One day, even pulse will be surpassed.

---

### Post by Simian Man on 2008-11-20
> **Tom Mann said:**
> 
b) Go back to the drawing board, and redesign the sound system to handle all of these from the start?


So you want to add a fourth?

---

### Post by Tom Mann on 2008-11-20
Not to add a forth - but to (somehow) consolidate the 1 we have into one entity, where it can be optimized to work without the need for several APIs, and ultimately several groups of applications to support them all.

---

### Post by mentallaxative on 2008-11-20
This post reminds me of [this.]("http://blogs.adobe.com/penguin.swf/linuxaudio.png")

---

### Post by stmiller on 2008-11-20
Jack != ALSA. You actually need jack AND alsa. Alsa is the driver (midi and audio), jack is just a connection kit as the name says.

All major audio apps in Linux work great with jack. The key is finding a good sound card to run jack and a realtime kernel. Trying with on-board sound often leaves tons of hangs, crashes, etc. But with a good sound card it all works. This was my experience going to an audiophile 2496.

---

### Post by Tom Mann on 2008-11-20
> **stmiller said:**
> Jack != ALSA. You actually need jack AND alsa. Alsa is the driver (midi and audio), jack is just a connection kit as the name says.

All major audio apps in Linux work great with jack. The key is finding a good sound card to run jack and a realtime kernel. Trying with on-board sound often leaves tons of hangs, crashes, etc. But with a good sound card it all works. This was my experience going to an audiophile 2496.

Exactly - therefore JACK should be part of ALSA. As should Pulse.

---

### Post by Polygon on 2008-11-20
why pulseaudio is better is that it can manage all the other sound servers, so apps like flash and stuff that still use alsa, you can still hear it through pulseaudio

also, my microphone works with pulseaudio. this has NEVER EVER worked before with alsa or whatever we had before

---

### Post by simtaalo on 2008-11-20
they do need consolidation, in other area's of the o/s having multiple systems is beneficial, but sound is not one of these area's, the sound driver's need to be standardised across linux, which would then make JACK easier to setup. when JACK is setup properly it gives oppurtunity for some inventive things that you couldn't do on windows, or at least not in a simple and easy way like you can in JACK.

it has taken me a long time to start making music in linux, and music production is one of the area's where we are lacking. the improvements are coming, LMMS is shaping up to become a very good program,hydrogen is the best drum sequencer i've used on win/linux/mac, but overall more work is needed in this area.

---

### Post by Tom Mann on 2008-11-20
Just to add to this:

We also have very little (ie no) support for Firewire devices outside of JACK and FFADO/FreeBob. It means we need further consolidation in this area too.

---

### Post by mihai.ile on 2008-11-20
> **mentallaxative said:**
> This post reminds me of [this.]("http://blogs.adobe.com/penguin.swf/linuxaudio.png")

Now this... just wow! We really need someone to consolidate all those technologies. The hard work I think is all done, all we need is a little re factoring so that all will eventually work flawlessly.

---

### Post by eragon100 on 2008-11-20
That picture speaks books -- this needs improvement! :)

---

### Post by simtaalo on 2008-11-20
definitely, that picture really shows we've got a mess at the moment.

this is mainly because the linux approach tends to be people developing independently of each other so we have several different options for everything. for other area's of the o/s this approach works well and has benefitted growth, but we can see for audio we need to have a linux-wide consolidated program.

i think it would be worth posting this thread on some of the other major distro forums and see if a unification project can be started.

---

### Post by FuturePilot on 2008-11-20
I wouldn't say it needs to be reworked from scratch, but it definitely isn't perfect. However PulseAudio was definitely a step in the right direction.

---

### Post by jespdj on 2008-11-20
"Go back to the drawing board" means design yet another sound system for Linux - that will not help, to the contrary, it will make things worse (there are already too many sound systems for Linux).

PulseAudio is great, and in my opinion as much software as possible should be modified to work well with PulseAudio, if it doesn't already.

Ubuntu now has PulseAudio, there's work to do to integrate it better.

---

### Post by ericesque on 2008-11-20
So I suppose all of you are busy reading through documentation right now and clearing your calendars to start 'consolidating' these unwieldy systems, eh?

Contributing ideas about how to improve OSS is great, but blindly
saying "hey, this is broke!" without any real constructive input simply
leaves you looking whiny and is in no way respectful of the time and effort 
the devs have already put in.

> "Linux Audio -Back to the drawing board?"  -- pretentious much?

---

### Post by jerrylamos on 2008-11-20
Well, what did I expect, early Jaunty has broken sound.  Alpha 1 isn't even out yet so that will wait.

Now I've read Pulse Audio takes lots of CPU, like 10%.  Anyone have any data on that or how to get it?  

I don't need any more main line code - shades of Windoze where every developer assumes every user wants to run every developer's code all the time and the system slows to a crawl.  And of course keep it a secret.

As an ordinary user all I want to hear is the audio on BBC News, You Tube, etc.  Nothing exotic.  If someone wants lots of CPU for their high end audio, let them do it, just don't splash over on me.

Back to the drawing board....

Jerry

---

### Post by jespdj on 2008-11-20
The problem with "back to the drawing board" is that you can't undo the past. You can't throw it all away and start from scratch. Designing a completely new sound system means you only add another box to the mess.

---

### Post by simtaalo on 2008-11-20
> **ericesque said:**
> So I suppose all of you are busy reading through documentation right now and clearing your calendars to start 'consolidating' these unwieldy systems, eh?

Contributing ideas about how to improve OSS is great, but blindly
saying "hey, this is broke!" without any real constructive input simply
leaves you looking whiny and is in no way respectful of the time and effort 
the devs have already put in.

  -- pretentious much?

yeah it does sound a bit whiny, this is why i suggested posting this thread on the other major distro forums so we can collect together a team of people that are capable the work. personally i'm not :(

---

### Post by pt123 on 2008-11-20
Is there a simple guide to Pulse Audio on Ubuntu? as to where it stands.

I have seen how-tos in the tutorials section but they were old and made Pulse Audio to have primitive configuration tools.

---

### Post by simtaalo on 2008-11-20
[http://www.pulseaudio.org/wiki/](http://www.pulseaudio.org/wiki/)

---

### Post by Tom Mann on 2008-11-20
Ericesque:
Pretencious? Maybe starting again is not a good idea, but consolidation is definitely a logical step. As soon as I get my Delta 66 Rev E working correctly under ALSA (yes I'm looking at sources!) I'll start the process of learning ALSA, pulse, JACK and FFADO and see if I can help and where it's best placed. I have a plan - it's just not ready yet!

Jespdj:
It's not adding another block - it's combining four seperate blocks into one functioning system.

JerryLamos:
You should find pulseaudio is generally disliked by the pro-audio users as it interferes with latency. If anything JACK in my experience uses less, but it too clunky for the average user. (I've noted that pulse is now looking at this)

I should add: I think all of the developers for these projects have done a magnificent job for their target audience.

---

### Post by pt123 on 2008-11-20
> **simtaalo said:**
> [http://www.pulseaudio.org/wiki/](http://www.pulseaudio.org/wiki/)

If that was a reply to my earlier post, that is not helpful. It is all over the place.

---

### Post by Tom Mann on 2008-11-20
(removed wrong link)

---

### Post by simtaalo on 2008-11-20
> **pt123 said:**
> If that was a reply to my earlier post, that is not helpful. It is all over the place.

sorry if thats not a helpful link, but don't blame me because pulseaudio haven't got their wiki well-ordered. 

i'm sure if you looked round properly you would find the answer to your questions, even if it is "all over the place"

---

### Post by mrgnash on 2008-11-20
Your poll is missing a fourth option: Sound in Linux is great, so long as it's OSS4, and not Alsa/Pulse.

I gave up on Alsa/Pulse, ripped it out, and replaced it with OSS4, and haven't had a problem since (except with Adobe Flash, but that was easily resolved). To be fair, the implementation of Pulse in Ubuntu, is pretty bad compared to a distro like Fedora, but still, there are plenty of inherent problems in Alsa/Pulse that you can read about [here](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html).

OSS was **not** replaced due to a lack of hardware support -- at least, this was not the primary reason; but rather, due to licensing issues. Here is the actual history:

[quote=Hannu]Once upon a time in Linux there was a tiny sound subsystem called VoxWare (formerly known as the Linux Sound Diver). It was maintained by me and released under GPL for Linux (and under the BSD license for FreeBSD and some other Unix variants). That piece of code was included in the Linux kernel source tree. I was working on the code “just for fun”. However it become too difficult to work on the sound stuff in my spare time at the same time when working on some Windows projects for my living. I was contacted by 4Front Technologies and we desided to make our living with a commercial version of OSS.

Unfortunately it took too long time to find the proper procedure to support the GPL/BSD version and the commercial one from the same source tree. So a well known Linux distribution vendor got irritated and hired another person to create another version of OSS for them (without even asking me to do that). The result was rather different than my plans for the future so I had to quit as the maintainer of sound for Linux.

Since that moment the kernel (OSS/Free) and the commercial OSS versions have been maintained by different teams. Unfortunately the Linux kernel version of the API got frozen to the OSS 3.8 version while we continued the development of the official API. In addition the OSS/Free version was (unfortunately) restructured so that most of the common (device independent) code was duplicated in the individual low level drivers. This made it impossible to keep the kernel drivers up to date with the development made to the official OSS version. The result was that the kernel drivers got frozen to the 3.8 version forever, unfortunately.

Then couple of years later a group of fearless programmers had created an entirely different, incompatible and Linux-only sound API called ALSA. They pushed it to the Linux kernel tree and the old OSS/Free version was declared as “deprecated”. It was supposed to become more advanced that OSS/Free 3.8. It was released under GPL (only) so it seemed to be the right thing. However application programmers didn’t like the ASA API and continued to use OSS instead. It was necessary to declare OSS as “deprecated” to push application developers to support ALSA instead of OSS.[/quote] -- [Link to full blog post](http://4front-tech.com/hannublog/?p=5)

In fact, Alsa has not even fully replaced OSS:

[quote=Hannu]The latest Linux 2.6.20 kernel still has the old and obsolete 10+ years old OSS version included. It’s being killed (for a very good reason). However it looks like we are getting a very long funeral. ALSA too has OSS emulation. In fact there are two redundant versions of it: one in the kernel and another implemented in library level. Both of them emulate only the now obsolete 3.8 API version. This is the dead and deprecated OSS.

However this is not the only OSS. We at 4Front have continued working on Open Sound System for all the past years. It has become the real Common Unix and Linux Sound Solution (CULSS). In addtion to Linux it’s now the official sound subsystem for all the Unix variants (other than MacOS).[/quote]

In my humble opinion, the best thing that Ubuntu and other distributions could do would be to stop pouring time and effort into getting Alsa/Pulse to work even half-decently for the majority of users, and switch to the much simpler and much more stable OSS4. Given that OSS4 has been released under both GPL and BSD licenses (it's already the default sound server for the BSD system, as indicated above), there's really no good reason that I can see to stick with Alsa/Pulse.

---

### Post by simtaalo on 2008-11-20
how does OSS4 work with JACK?

interesting information mrgnash, good post

---

### Post by mrgnash on 2008-11-20
> **simtaalo said:**
> how does OSS4 work with JACK?

interesting information mrgnash, good post

Thanks :)

There is an experimental OSS back-end in JACK; I don't know anything beyond that though, sorry.

---

### Post by tvtech on 2008-11-20
you've hit on the fundamental of what linux is,  it's a grouping of open source software brought together by many developers to create an end product because no one developer has the resources to create a fully functional OS on their own.  I think nix audio is fine, but it could still use some improvements here and there.

---

### Post by alwayshere on 2008-11-20
Hey i would be happy happy to have sound that works with no fuss seems to be to much to ask at the mo , i think sound was better/working allaround in 7.04 .}  8.04 and 8.10 is a sound wild goose chase ](*,)

---

### Post by cardinals_fan on 2008-11-20
I like ALSA.  It does what I want.

---

### Post by handy on 2008-11-21
I have always found the sound quality of any Linux setup (different distro's & different hardware) that I have used to be inferior to that of windows or OS X.

It is particularly noticeable when watching DVD movies.

I agree that sound needs to be sorted out, & when it does get sorted it will give us a greatly simplified sound setup & control system I'm sure.

The other thing that also needs to be sorted out is theme-ing.  There are too many ways available, & mostly they have tedious solutions. It should not be harder than selecting the thus far non-existent GUI that allows you to choose the element you want to adjust & offers you a few sliders so you can make your eyes happy.

Anyway, in time both of these problems won't exist any more.

---

### Post by simtaalo on 2008-11-21
just talking to someone on a different forum who uses KDE4 which apparently uses a soundserver called 'phonon' which he says works really well.

so is this something else which needs consolidating? or should we like the earlier suggestion goto OSS4?

---

### Post by mrgnash on 2008-11-21
> **simtaalo said:**
> just talking to someone on a different forum who uses KDE4 which apparently uses a soundserver called 'phonon' which he says works really well.

so is this something else which needs consolidating? or should we like the earlier suggestion goto OSS4?

Phonon is not a soundserver, it is a high-level multimedia API which provides basic universal functions (play, pause, seek, etc.) across various backends such as Gstreamer, Xine, Mplayer, etc.

So yeah, I think the OSS4 solution is still the way to go ;)

---

### Post by Tom Mann on 2008-11-21
Sadly with OSS: [http://4front-tech.com/hannublog/?p=14]("http://4front-tech.com/hannublog/?p=14")

Unless people take it on, it's no more.


On another note - does anyone know any other Linux forums I can link this to? Looking at the current poll it seems to be something most people have a gripe with...

---

### Post by saulgoode on 2008-11-21
I consider OSS4 unacceptable to be considered a viable candidate for Linux 's sound architecture. Though it is GPLed, all development seems to be controlled by a single company. There is no CVS/SVN repository, no bugtracking system, and little transparency in the decision-making process.  Should 4Front Technologies choose (yet again) to withdraw their support in order to focus on other interests then we would be stuck (yet again) with the prospect of instituting a completely new development infrastructure to replace OSS4's current development model. I doubt too many GNU/Linux developers would be willing to follow that path. 

ALSA is, and should remain, the Linux audio architecture at the kernel/driver level. Early ALSA development was crippled not by technical limitations of the system, but a dearth of documentation. The main focus at that time seemed to be writing drivers and the assumption was made that programmers would be able to intuit how to write applications using ALSA. Over the past couple of years things have improved greatly on that front and, of course, the structure of ALSA's development is as open and organized as that of the Linux kernel itself.

I am admittedly stodgy when it comes to adopting new technologies, but I do think PulseAudio has at its core a good approach to providing an interface between ALSA and sound applications. I am a little concerned that some of the features being touted for PulseAudio aren't particularly worthwhile, but this should only be a factor to the extent that their development detracts from the implementation of the core capabilities.

PulseAudio is not quite ready for adoption on my machines yet, and I think that Ubuntu was a little bit premature including it in 8.04, but its development seems to be headed in a generally good direction. More importantly, when contrasted with OSS4, it provides a more Free-friendly development infrastructure.

---

### Post by mrgnash on 2008-11-21
> **Tom Mann said:**
> Sadly with OSS: [http://4front-tech.com/hannublog/?p=14]("http://4front-tech.com/hannublog/?p=14")

Unless people take it on, it's no more.


On another note - does anyone know any other Linux forums I can link this to? Looking at the current poll it seems to be something most people have a gripe with...

I read that, but Hannu is not the only one who develops OSS4 -- and he doesn't say that he won't be developing it in the future, only that he has to seek employment elsewhere in order to generate revenue, and this means **less** time for OSS4. 

It is very sad news, but even in its current state, OSS4 is light-years ahead of ALSA, so until ALSA catches up (if it ever does), I am quite content to keep using OSS4 as my sound server.

That said, the best of all possible worlds would be if OSS4 was to be adopted by more Linux distributions, and more people join in and hack the code. This would avert saulgoode's doomsday scenario, and would keep the pace of development nice and brisk.

There are no ideal solutions here, as far as I can see, but I don't consider ALSA to even be a viable one; it's just too much of an impenetrable, flakey, kludge -- and that's just from an admins perspective, I can't even begin to imagine what it must be like to develop for.

---

### Post by Tom Mann on 2008-11-21
mrgnash - I may have misinterpreted that OSS is ending, but it just creates another split in the Linux audio architecture.

---

### Post by Mr. Picklesworth on 2008-11-21
I feel that PulseAudio is doing well as an in between piece that integrates everything. Can't say I know much about the inner workings, but it reminds me a bit of X which was a good idea.

It's all working quite well for me. Just recently I did a stress test with about 6 different videos / music tracks open at once in 4 different programs, and I heard not a crackle. I could individually adjust each audio track and got half of them going to one speaker, half to the other. I wish I'd had a surround sound setup to play with; I was suddenly stricken by the potential awesomeness of giving splitting five speakers evenly between five streams.

Here's a nice little overview of the big APIs:
[http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)

In one sense, having so many means that there's an API suited to every task :P

The Ubuntu community seems the most pessimistic about the future of Linux audio APIs, largely because this distro didn't do very well configuring it all at first. Seems to be sorted out somewhat with Intrepid. I know the folks over at Fedora are committed to really improving the front end to it all, such as audio preferences for GNOME, in their version 11 release. For example they are generating a lot of discussion about replacing the volume control applet with something that more directly speaks of PulseAudio with separate streams and the like, putting ALSA in the background where it should be. This will be good. (Maybe think of it like the X input / output stuff versus the window manager?)

I have had some issues with recording audio, but again it seems like there are some good ideas coming up within our existing technologies. Besides, I never have much luck with microphones in Windows, either. It never seems to guess correctly when I want them muted or unmuted, and which I want to record from. The only advantage on its end is that there is just the one place I need to go to. Repeatedly. To make things work right.
I was actually quite impressed a while ago by Realtech's Windows driver for one of their sound cards. When the user inserted a device into any of the ports, it would ask what kind of device it was -- whether it was a rear, left or right speaker, for example. A similar trick could be applied in the desktop environment to make the audio jungle less jungle-like for the user. Right now he has to directly go somewhere to flip the right switch to make something work. Ideally - and this applies to everything - that switch should *come to him* at just the right moment.

What some people (not our OP, thankfully!) seem to  forget is that you don't *need* to create a new API and fragment things every time one misbehaves. Because this free software, you can draw a picture of how these should all inter-operate -- preferably without breaking existing software or at least with a migration path -- and apply the necessary patches in each API to fit them with the world today.

Of course, I don't do much with audio, so consider me a casual, non audio-phile end user. Now I know what I care about here is more superficial stuff like user interface, but I think the situation with sound will get a lot clearer when it looks tidier on the desktop, and a fair number of people will be happier with it.

Oh, and thanks for the link about OSS. Really interesting! :)

---

### Post by mrgnash on 2008-11-22
> **Tom Mann said:**
> mrgnash - I may have misinterpreted that OSS is ending, but it just creates another split in the Linux audio architecture.

How? :confused:

Also, nice post Mr. Picklesworth. I don't agree that the the problems with Ubuntu's audio configuration "[seem] to be sorted out with Intrepid." My own experience simply doesn't match with that... there were oodles of problems out of the box for me, and in the end, I couldn't be bothered trying to get everything to play nice with such a confusing infrastructure. That's when I tore it out of my system and installed OSS4 instead.

That said, I didn't have nearly so many problems on Fedora 8, so perhaps it is the implementation more than anything else. How much time to wasted on working on a proper implementation of ALSA and Pulse could be saved by using OSS4 though, I wonder?

---

### Post by wersdaluv on 2008-11-22
Linux Audio really is complicated. I have to kill pulseaudio sometimes, run Jack, etc

---

### Post by Tom Mann on 2008-11-22
> **mrgnash said:**
> How? :confused:

We'd still need JACK to attach to OSS4 for audio, Pulse is the de-facto in most Gnome distributions now (like Phonon for KDE4, though Phonon connects to Pulse too... Confused yet?)

---

### Post by DrRockso on 2008-11-22
Definitely back to the drawing board.

When I upgraded to Intrepid Ibex, PulseAudio gave me serious headaches. Just to be able to capture any sound in any way, I had to go into Sessions and stop it from starting up and set it to kill pulseaudio if it does start up. Then I had to set everything to work with Alsa only. Now I have sound and can record properly. Many, many many users have had the same problems with PulseAudio, for those of us who work with multimedia whether for business or pleasure, this kind of tinkering he have to do now when we didn't have to before is a major step backwards.

If the issues with sound in Ubuntu persist, I will have to go elsewhere, which I don't want to do, but I'll have no choice.

While I'm at it, whoever borked ffmpeg for 8.10 should be treated in an unpleasant manner until they feel deep regret. ;)

Ubuntu is great, but I really believe they are so obsessed with staying on the bleeding edge and insisting on releasing something new every 6 months that they often leave a huge number of users in the lurch. PulseAudio is a prime example.

---

### Post by mrgnash on 2008-11-22
> **Tom Mann said:**
> We'd still need JACK to attach to OSS4 for audio, Pulse is the de-facto in most Gnome distributions now (like Phonon for KDE4, though Phonon connects to Pulse too... Confused yet?)

Very :lolflag:

Alls I know is that I'm sticking with OSS4... at least until I am satisfied that ALSA/Pulse can behave themselves on my system.

[quote=DrRockso]
Ubuntu is great, but I really believe they are so obsessed with staying on the bleeding edge and insisting on releasing something new every 6 months that they often leave a huge number of users in the lurch. PulseAudio is a prime example.[/quote]

Ubuntu isn't really "on the bleeding edge", at least, not compared to a distro like Arch.

---

### Post by Tom Mann on 2008-11-23
As a thought on this - it'd be interesting to find out how Jono Bacon managed with the Linux sound system when he created [**Denied by Reign**]("http://www.severedfifth.com/").

---

### Post by simtaalo on 2008-11-23
> **Tom Mann said:**
> 
On another note - does anyone know any other Linux forums I can link this to? Looking at the current poll it seems to be something most people have a gripe with...

[http://fedoraforum.org/](http://fedoraforum.org/)
[http://www.linuxforums.org/](http://www.linuxforums.org/)
[http://forums.gentoo.org/](http://forums.gentoo.org/)
[http://bbs.archlinux.org/](http://bbs.archlinux.org/)
[http://forum.mandriva.com/](http://forum.mandriva.com/)
[http://forums.opensuse.org/](http://forums.opensuse.org/)

i definitely think this is one area where a universal standard will make a massive difference.

---

### Post by oiper on 2008-11-25
Back to the drawing board, but with everyone in the same room, held at gun point until they work this out in a collaborative way.

Just stopping by to check on the current state of sound systems. I had to join the Mac community this past spring as a workaround to the sound problems I was having. I try to check in on this topic every so often to see if it's become safe to come back again. :guitar:

---

### Post by Tom Mann on 2008-11-25
I've just dropped a question into Pulse's bug tracker asking about the possibility of merging their code with ALSA's.

Don't get me wrong - I realise this is a laborious task, and also that Pulse needs to be stable before this happens.

But I think if ALSA had Pulse's abilities built-in we'd be taking a massive step in the right direction with audio. Instead of Pulse dealing with ALSA's API, they would have direct access (and a certain degree of influence) over the ALSA code directly.

This can only lead to speed and feature improvements!

EDIT: Found these...
[https://wiki.ubuntu.com/DesktopTeam/Specs/CleanupAudioJumble]("https://wiki.ubuntu.com/DesktopTeam/Specs/CleanupAudioJumble")
[http://lwn.net/Articles/299211/]("http://lwn.net/Articles/299211/")

Looks like people already know are already looking for a solution.

---

### Post by mrgnash on 2008-11-25
> **oiper said:**
> Back to the drawing board, but with everyone in the same room, held at gun point until they work this out in a collaborative way.

Just stopping by to check on the current state of sound systems. I had to join the Mac community this past spring as a workaround to the sound problems I was having. I try to check in on this topic every so often to see if it's become safe to come back again. :guitar:

I have considered going to FreeBSD for much the same reasons. But even if every other OS (yes, including Windows) only made "bork bork bork" sounds emit from the speakers, I would still never even contemplate the purchase of a Mac, for Mac is whack.

---


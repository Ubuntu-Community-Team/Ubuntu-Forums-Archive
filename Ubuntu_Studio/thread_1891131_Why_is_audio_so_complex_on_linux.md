---
title: "Why is audio so complex on linux?"
date: 2011-12-04
forum: Ubuntu Studio
---

### Post by mwray on 2011-12-04
I have a MacBook (2,1) w/ Ubuntu Studio on it, Sno Leopard, and XP.

On XP and Leopard, all I have to do to record is plug in a recording device to the line in, launch audacity, and hit record.

In Ubuntu, and other linux variants, after every patch, I have to go fix the audio subsystem so my Intel audio drivers will load. Then I have to tell Pulse Audio how to talk with an Alsa driver. Then I have to tell Pulse audio which hardware to use. Then I have to tell Audacity which place to record from. Once that's all done, the recording sounds terrible, compared w/ XP and Mac.  Why so many hoops for such a simple task?

I found the same issue w/ my AsusTek Whitebox pc that has a SoundBlaster Live card. The only step removed was dinking w/ the actual sound driver itself.  

I still have to go into Alsa's mixer to change settings at each boot. (APparently storing and restoring the mixer settings even w/ sudo is broke.)  Then I have to tell Pulse how to use Alsa. Then I have to tell audacity how to use Pulse. EVERY Time. Nothing retians any settings across a reboot.  (Reloading hasn't helped, upgrading hasn't helped, different versions of Linux haven't helped.)  In fact I find many of my Audio problems would probably go away, if I could find a way to do away with Pulse audio. Except every time I install a MultiMedia app, it gets reinstalled, and if I remove Pulse, then alot of times, my entire Xubuntu desktop environment gets yanked. (Even though there is no real requirement for pulse to be present to use Xubuntu)

These issues are preventing me from builing a cost effective digital studio for my church. I want something I can setup once,  and then train other people how to use it. But the audio breaks at almost every boot on 9 out of 10 systems I have here at the house. 

The one it doesn't break on only runs MacOS, not ubuntu. (Wife's PC).

If I could afford to donate a Mac, I probably would. I refuse to donate a PC w/ Windows on it, because I don't want all the support calls caused by viruses/spyware, inability of windows to recover properly from a power outage, etc.

Any suggestions, aside from a distro that requires you build everything from scratch?

---

### Post by jejeman on 2011-12-05
Well, on my systems setup does not change after reboot.
If you think pulseaudio is trouble, just turn it off. No need for uninstall.
Put  in ~/.pulse/client.conf line

autospawn=no

And then kill it ```
pulseaudio --kill
```It will stay dead forever.

---

### Post by click4851 on 2011-12-05
In my opinion this is one of my biggest complaints about linux and particularly Ubuntu. I'm not sure if its too much "choice" among desktop environments or what. If as much effort went into sound as has gone into Unity/Gnome3 maybe we would be closer to a "it just works" distro. Probably audio and unity/Gnome3 will push me into a MAC. I've had the best luck, when the default won't work, and i'm reach my limit of support threads, of just using ALSA, sad to say.

you might also try:

[http://ubuntuforums.org/showthread.php?t=1885240&highlight=ALSA](http://ubuntuforums.org/showthread.php?t=1885240&highlight=ALSA)

---

### Post by fallenshadow on 2011-12-05
I dunno but it seems to be a big fail with extra fail sauce on top. I tried to try out Ardour. I got as far as installing it and still haven't managed to successfully launch it.

Jack isn't started it says but I try launching Jack with QjackCtl and that fails too! If Ardour was really any good it should do all this stuff for you, so you don't have to deal with this crap!!!

Maybe Ubuntu devs should have tried a very simple usecase to find out about this and sort it:

User wants to try audio production, reads that Ardour is the best for the task, installs Ardour... Ardour fails to start. Conclusion: needs fixing!

---

### Post by boast on 2011-12-05
> **mwray said:**
> 
I still have to go into Alsa's mixer to change settings at each boot. (APparently storing and restoring the mixer settings even w/ sudo is broke.)

doing this doesn't work? 

[https://wiki.archlinux.org/index.php/PulseAudio#Pulse_overwrites_ALSA_settings](https://wiki.archlinux.org/index.php/PulseAudio#Pulse_overwrites_ALSA_settings)

---

### Post by ratcheer on 2011-12-05
@mwray, I have no idea what the answer is, but this is a great question.

It seems to me that there are at least three layers of audio systems on Ubuntu (and most Linux systems) and they all have to work perfectly with each other in order for sound to be played, properly. If it all ends up configured correctly, it can be great, but if something is wrong, it is difficult to be sure which subsystem to mess with to try to fix it. This results in the problems often becoming worse than they were when you started.

Tim

---

### Post by mwray on 2011-12-05
> **click4851 said:**
> In my opinion this is one of my biggest complaints about linux and particularly Ubuntu. I'm not sure if its too much "choice" among desktop environments or what. If as much effort went into sound as has gone into Unity/Gnome3 maybe we would be closer to a "it just works" distro. Probably audio and unity/Gnome3 will push me into a MAC. I've had the best luck, when the default won't work, and i'm reach my limit of support threads, of just using ALSA, sad to say.

you might also try:

[http://ubuntuforums.org/showthread.php?t=1885240&highlight=ALSA](http://ubuntuforums.org/showthread.php?t=1885240&highlight=ALSA)

It works until one of the plethora of automatic updates that I keep trying to turn off applies an update (so less than a day.) At install time I say I want to manually run updates, but no matter what there's always a 3rd, 4th, or 5th auto-updater waiting to kick off after I get rid of another.

So far, I have come across 6 different subsystems that think they know better than I do about updates. 3 are from ubuntu, and 3 are from gnome. (Very aggravating since I am using xfce not gnome.) 

If ubuntu is about choice, then let me make my choice and leave it alone!

---

### Post by ratcheer on 2011-12-05
> **mwray said:**
> 

If ubuntu is about choice, then let me make my choice and leave it alone!

That is one of the main goals of Arch Linux. Unfortunately, what you gain in simplicity, you have to pay back in complexity. ;-)

Tim

---

### Post by jejeman on 2011-12-05
> **mwray said:**
> It works until one of the plethora of automatic updates that I keep trying to turn off applies an update (so less than a day.) At install time I say I want to manually run updates, but no matter what there's always a 3rd, 4th, or 5th auto-updater waiting to kick off after I get rid of another.

So far, I have come across 6 different subsystems that think they know better than I do about updates. 3 are from ubuntu, and 3 are from gnome. (Very aggravating since I am using xfce not gnome.) 

If ubuntu is about choice, then let me make my choice and leave it alone!If you think update is toruble, just turn it off. Open software sources and disable updates.

---

### Post by sgx on 2011-12-05
> **mwray said:**
> I have a MacBook (2,1) w/ Ubuntu Studio on it, Sno Leopard, and XP.

Any suggestions, aside from a distro that requires you build everything from scratch?

Get an maudio pci soundcard. They have the easiest configuration,
and excellent sound quality. Study the articles/screenshots from the links at the qjackctl wiki. Turn off updates and kill pulseaudio as already mentioned, and utilize youtube and google for ardour videos and tutorials.

You must set up qjackctl for your sound device, set up ardour preferences, create an ardour project, create a track, arm the track, press record, then press play. (hazy memory)

What specific tasks would you like to use linux for, in the church setting?

If you disable/remove modems/internet apps, and do your backups, xp will not be a huge problem. I've had my xp install for nearly 5 years,
(prays/knocks on wood) dual booting with every 'easy' linux under the sun 
Cheers

---

### Post by sgx on 2011-12-06
> **mwray said:**
> I have a MacBook (2,1) w/ Ubuntu Studio on it, Sno Leopard, and XP.

Any suggestions, aside from a distro that requires you build everything from scratch?
I would get a cheap P4 and maudio pci soundcard, to use for linux.
This will give you stability, as you learn the OS. Bodhi linux is
an Ubuntu minimal distro (400 meg .iso) using E17 by default.
So an 8gig usb-stick is fine to install on. The audio apps can
be added using synaptic and ubuntu repos, and manually installed
.deb files from debian unstable using

dpkg -i name.deb

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

If it lists a herd of related dependencies, like 6 qt items,
using synaptic to install them may save time.

---

### Post by ussndmac on 2011-12-06
I have had very good luck with AVLinux.

I use 24 channels of firewire (dual AF12').

Basically I installed it and it just worked.

I use Ardour all the time. Beats Protools IMO and it's free!

---

### Post by mwray on 2011-12-07
Ok. Ardour. I will check out. (Someone mentioned using ~/.pulseaudio, which wasn't working for me due to having other apps in the audio group that auto login and I'm in those groups too. So I put it in /etc/pulseaudio/someconfig file and that seems to work.

I haven't figured out what apps, I just know when I do a who, audio is logged in. (I think I installed an audio db app that uses a private copy of postgres running on an odd port.) I have looked at so many apps my eyes are spinning.


I will also have to check out AVLinux and Bhodi. 

The AF12 firewire card? (Um anyone know of a cheep mixer that supports firewire?) 

Basically I would like to come up with an inexpensive digital mixer, using my laptop as a test platform. (In otherwords, I'd like to know how the software works before I go spending time on a building a machine for it.)

Firewire would probably be a good choice since the cameras I have in mind if we add video later will support firewire. 

I am assuming firewire 800 not 4.

I like audacity because it's easy to start recording and apply effects, unfortunately, you can't apply effects straight to the live feed, and the problems I've had w/ Jack is that there is about a 6 second delay between the in and the out. (Even with Realtime processing enabled.) Might be that I'm just hitting the limits of a 2GB, 2.08Ghz intel Core 2 duo macbook. Or maybe I need to upgrade the HD again. It's certainly not as fast as the 8GB 1.68Ghz IntelCore2Duo. (Main performance boost is obviously RAM and 6GBs Sata vs 3.


Right now, just trying to record the Sunday sermon to post on the internet as an mp3. Sometimes it works, and sometimes it doesn't. I've ruled out cabling. So I'm down to issues w/ internals on the laptop, and the soundboard. If I am using the same setup on the soundboard for other line out apps, I never have a problem, so it leads me to believe that the issue is more to do w/ the internals on the macbook. 

(ON the mac side, sometimes I can't shut off the built-in mic, which then ruins the recording w/ ambient noise). The windows side often Bsods because it keeps trying to load the firmware for the camera.

The linux side, I am still fighting pulse, and now my wifi and bluetooth suddenly disappeared after a set of security updates for the kernel. Since I use the laptop to do coding for clients, I can't afford not to have security up to date. Very frustrating that things that aren't supposed to be modifying sound or network always seem to affect sound and network.

I think pulse would be easier to use if it had its' own drivers instead of relying on OSS and Alsa which are outdated anyways.


Thanks for all the replies!

---

### Post by mwray on 2011-12-07
Also, thanks for the newbie input, although I personally don't need that. I'm just used to maintaining servers, not desktops. (You know, install the pieces of linux you need, setup manual updates, and let it run, since servers use wired nics, and don't need Gui's or audio, no problems).

---

### Post by sgx on 2011-12-07
> **mwray said:**
> Also, thanks for the newbie input, although I personally don't need that. I'm just used to maintaining servers, not desktops. (You know, install the pieces of linux you need, setup manual updates, and let it run, since servers use wired nics, and don't need Gui's or audio, no problems).
Bodhi is a 370 meg .iso, based on ubuntu, with an active forum, it's easy to add just what you need, and avoid complexity.

Timemachine is great for very high quality yet very simple recording, which audacity can import, edit, and export as mp3.

Rakarrack is a great stereo multi-fx app, and with an maudio pci card,
that 6 second latency will vanish. 

Calf, invada, and mda LV2 fx also have some jewels. The Calf Reverb is one such.

There are some Focusrite firewire
interfaces that also could be used, but 3 times the price of an
maudio 24/96, and a lot more possible configuration niggles. Trulan
is a name to google with firewire ubuntu. The text file .jackdrc
would be handy to post, in case some settings need a twist. There is
a jackd manpage on the net, that itemizes the options, so it appears
less like squirrel tracks. qjackctl saves that file each time your settings are saved, and it can be the command string, to launch jackd
prior to the gui, if desired.

jackd -d alsa -r 44100

is the basic command that almost always works.
Cheers

---

### Post by sheehanje on 2011-12-07
On the original question of Linux having complicated audio systems.

You are absolutely right.  I'm always torn between trying to get stuff to work in Linux and paying big bucks for audio processing tools in Windows.  I'm not a professional, and just a hobbyist when it comes to audio recording.  It seems every time I want to upgrade my Studio distribution I run into a lot of configuration, especially seeing I run 2 firewire interfaces.

Right now with the state of Ubuntu Studio in flux, it just adds to the confusion. Do I stick with Ubuntu Studio, or do I start looking at other distributions.  While I appreciate the efforts of the Ubuntu Studio distro, I wonder why Canonical doesn't provide more backing.  It's obvious that the Default Ubuntu distro's aren't setup for recording.  And while there is a learning curve to the applications that make up a modern recording system (DAW, Sequencer, etc.), that with Linux there is even more of a learning curve to setup RT Kernels, JackD tuning, and Pulse/Jack passthrough.  

I've seen other distributions that are starting to come close, but wouldn't it be a boon to be able to get a general purpose Distro that can also do audio out of the box, then allow the power users to tweak from there if they want.  To me, things like Ardour, Guitarix, Qsynth, and Jackd/Patchage are killer applications.  It just seems getting them running is a whole other subset of learning...  Why can't I have a distro that just runs these applications along with all the other general purpose stuff I do each day?

Don't get me wrong.  I have had success getting all the aforementioned running.  But it's a lot of time and energy between updates.  I've also tried some other distro's, like AVLinux, and running off of PPA's like KXStudio.  They are pretty good, but still geared for the dedicated studio engineer in my opinion rather than giving the average joe a shot at production over what Audacity offers.  Maybe I'm expecting too much, but I think if any of the major distributions threw around some weight to finally solve the Linux audio problem, it would get done for the better of everyone doing any kind of audio work in Linux.  

John

---

### Post by sgx on 2011-12-07
Almost any linux can include the common audio tools. There is some complexity, but that is the gateway to freedom. 'Seek and ye shall find' Basic multi-track multi-instrument recording, whether done on computer, or using room full of hardware, will always baffle someone somewhere. Dozens of cables and knobs and buttons being what they are :popcorn:

---

### Post by mjhouska on 2011-12-07
at least you can "grab" a cable and see where it goes.

---

### Post by sheehanje on 2011-12-08
> **sgx said:**
> Almost any linux can include the common audio tools. There is some complexity, but that is the gateway to freedom. 'Seek and ye shall find' Basic multi-track multi-instrument recording, whether done on computer, or using room full of hardware, will always baffle someone somewhere. Dozens of cables and knobs and buttons being what they are :popcorn:

SGX,  I don't think Complexity necessarily equals freedom.  Or in this case, it has to.  This is what would be nice:  You see Ardour in the Ubuntu Software Center.  You download it and it configures jackd for the hardware you have, and you can use it with relatively good latency.  Then if you want to go into the underpinnings of jackd, IRQ priorities, etc to get ultra low latency, then you can.

That's what started me on the path with Linux recording.  I first looked in about 2003, and there wasn't much there then.  I was surprised how far linux recording came when I looked again in 2008 and saw Ardour in the repositories.  I was excited, downloaded it, then got into days of configuration and tweaking before I was stable.  I'm just saying it would be nice to have been able to download that package, use it right away for recording, then worry about fine tuning if I wanted to.

I'm a network engineer, and used to be a systems analyst.  I know complexity.  And for those making a living dealing with complexities it's fine.  However for the regular user, complexity is a barrier, and I think it would be a good idea on focusing on those barriers.

Canonical did a lot right with Ubuntu, but there are still some serious "barriers" they seem not to work on that would benefit the whole community as a whole.  Audio is one of them.  I guess I'm biased, but I would rather have seen Canonical work on a fully functioning audio system rather than a desktop interface overhaul.   It shows that Audio has taking a backseat in this distribution.  

Please don't get me wrong, I think what the Ubuntu Studio community and the open source community in general did is outstanding, and I'm using (albeit an older version) it to record my band.  Something I couldn't do a decade ago.  I've been using Linux since Slackware was the big distribution.  It's been nice seeing how far things have come, and I've tried to lend a hand when I can.  I just hate to see people settle.  I think it can be better and hope projects like Ubuntu Studio get more backing.  I think in the end it will benefit Canonical's flag ship products.

The last thing I want to note, and it's kind of going off on tangets, but I don't think Unity should be totally dismissed as an interface for audio based recording.  I know it's clunky, especially on a desktop.  But I see Ubuntu in general moving towards tablets with the Unity interface.  Wouldn't it be cool to be able to use all the linux audio tools to great effect on something like a Motorola Xoom, or Samsung Galaxy tab?  That would be freedom.

---

### Post by sgx on 2011-12-08
> **sheehanje said:**
> SGX,  I don't think Complexity necessarily equals freedom.  Or in this case, it has to. 

However for the regular user, complexity is a barrier, and I think it would be a good idea on focusing on those barriers.

I don't think Unity should be totally dismissed as an interface for audio based recording. I know it's clunky, especially on a desktop.


As a musician, there are several things I am free to do, due to the complex routings and creative command lines that are available to me, that are not there for windows musicians.

I don't agree that musicians are regular users. Whether hobbyist or
professional, they require specific hardware, oddlot software, and unique configurations. I see qjackctl and a few text files as easier and more powerful than windoze Control Panel gizmos.

Linux musicians, not being normal users, will eventually choose
a gui of their liking. If Unity is unpopular with the masses,
they will go elsewhere, or install and learn a different gui. Dumb-down versions of linux distros should be available, but making them the default only insults the userbase, and won't likely impress
refugees. 'Feed the horse that brung ya.' 

If Unity is clunky on state of the art monitors with
blazing speed GPUs, just wait til its crammed on expensive 9" X 6"
inch tablet screens...
(but I would be a liar if i claimed never to have researched
homebrew mounting hardware, to put a tablet near middle C, or
mounted on a commodity electric guitar :) )
Cheers

---

### Post by sgx on 2011-12-08
> **mjhouska said:**
> at least you can "grab" a cable and see where it goes.
First you have to unbox everything, them learn where both ends
of all cables go. The unboxed contents need a physical location
and furniture to be at hand.
Location is crucial, since some cables need to
be moved occassionally, and not every button is on the front.
So lighting, and access space are also considerations.

etc etc etc

Which all helped inspire

V irtual
S tudio
T echnology

:popcorn:

---

### Post by manmath on 2012-08-02
Ok.. Ok... let me answer the basic question of the thread - Why is audio so complex on linux?

#1 - I admit - Audio subsystem is very very complex in linux, no doubt, just look at esd, pulse, alsa, oss, gstreamer, xine, jack, arts kernel drivers, audio production/playback applications and around 100 tools and utilities to setup, configure and tweak them. In windows and mac world the average joe is concerned with just the driver and the application software, the rest are hard locked inside the system, and it generally never throws any ugly surprise. 
#2 - Why - Simple answer - perhaps nobody is serious about making it simple. KLANK is coming as a rescue, but my apprehension is that it might be another layer on top of the existing audio subsystem.
#3 - Solution - Can't see it happen soon.

---

### Post by sgx on 2012-08-04
there are about 7 settings to get correct in qjackctl,
just as there are asio, soundcard, latency and bitrate
settings in windows.

As for "100 tools and utilities to setup", that all depends on
what you are doing. The same sounds and tasks done in
mac, linux, or windows, will require the same type of software.

No shortcuts or miracles.
:guitar:

---

### Post by manmath on 2012-08-13
> **sgx said:**
> No shortcuts or miracles.


Do you find the audio subsystem comprising "esd, pulse, alsa, oss, gstreamer, xine, jack, arts kernel drivers" simple?

---

### Post by sgx on 2012-08-13
If they were all needed, it would indeed be a task, but only
jackd, alsa, and a few GUIs are needed to utilize the best
linux audio apps, and a Reaper/wineasio setup.

My /usr/bin folder is under 400 meg, and 100 meg of that is
graphics apps I have yet to use. Most people having
consistent audio difficulties, just have to plod
up the same type of learning curve that mac/win users do.
Same steps, with some varied labeling.

Some musicians are unwittingly burdened by
linux bloatware. Since linux is most often delivered
with a wide array of apps, the beta-testing needed to iron out
the kinks and incompatibilities prior to release, doesn't happen.
It would stagger even a billionaire commercial OS developer,
so they let just let the customers do it for them.
It is high tribute to linux app coders, that things work together
as well as they do.

There are both giant, and tiny customized linux versions for
audio production, and barebones distros waiting to be configured
with a users choice of apps. Bodhi is Ubuntu based, and a 400 meg
iso, so a small uncluttered studio is just a Synaptic/dpkg session
away from the average user.
:guitar:

---

### Post by sgx on 2012-08-13
And while discussing difficulties, after all these years, there should be a sticky topic here for audio/video hardware devices that worked out of the box, or worked with certain steps taken, including the specs of the computer each device worked in. The alsa matrix is fine,
but not centered around any certain distro, and the sometimes unique issues that are presented.
Cheers
:popcorn:

---

### Post by tnob on 2012-09-24
If this discussion is still ongoing, I'd like to contribute to it.

I think that audio in Linux is indeed too complex. What I want, basically, is to plug one of my four electric string instruments, hit a button on my computer and play/record, for I'm a musician - and the chances of ever becoming an it wizzard like gsx, for instance, are extremely remote, at my age.

Yes, audio IS mindbogglingly complicated in Linux, if you don't happen to have a grade in IT (like me). But I also suffered loads of misery, for years on end, when I started out on the very idea of playing and recording my instruments on a PC in the first place: That was on Windows XP - and I can't think of any other system in the world more patronizing and pettily tyrranical than that one. Besides, for every problem sorted, 2 or 3 fresh ones would be on my plate, time and anon!

Some 8 years on (having switched to Linux in the meanwhile), there's still no sound in Ardour. I'll be trying my luck with Audacity and Rakarrack now. But give me Linux any time, since I find it eminently reliable. 

Except in the sound department perhaps...

tnob

---


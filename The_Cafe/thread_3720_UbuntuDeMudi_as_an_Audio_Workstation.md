---
title: "Ubuntu/DeMudi as an Audio Workstation?"
date: 2004-11-08
forum: The Cafe
---

### Post by chaotic on 2004-11-08
Hi,
I haven't switched to Linux yet.  But I will switch.  
There is a mass of information to trawl through before choosing a distro and I only know the little i've picked up in the process.
I primarily want to use my computer for Audio work, and the best option I;ve heard of so far is the **DeMudi distro** put out by [the AGNULA Project](http://www.agnula.org) This is Debian and has a tuned kernel and applications which optimise the computer for audio work.  However I'm no computer expert, I'm switching from windows and i'd like the interface and the desktop functionality of Ubuntu or Mandrake Linux.

Is there some simple way to combine Ubuntu with the DeMudi distro?

I haven't played with Linux yet but from what i gather Debian can be quite a learning curve.

If DeMudi and Ubuntu could be combined it may be a boon for Musicians and other creatives who wish to switch to linux and increase the Ubuntu user community

Any advice/feedback is appreciated

peace

---

### Post by TravisNewman on 2004-11-09
I'd suggest finding out the packages in DeMuDi and seeing if they're available for Ubuntu. Or maybe find out what the repositories for apt are and put them in your sources.list. It may be completely compatible. I'd like to get some audio editing going on my system too!

---

### Post by chaotic on 2004-11-19
[DeMudi is the Debian distro of Agnula](http://www.agnula.org/) , they also have RehMudi - a distro based on Red Hat.

DeMudi is not just a package of audio applications, it's also a Linux Kernel especially tuned for _low-latency audio production_.  That's the important part.

The audio apps in DeMudi are:
 Alsa Modular Synth
 Cecilia
 Jack
 jMax
 LADCCA
 Nyquist
 TkECA 
which will support high-end native linux apps
like Rosegarden, Ardour etc...

For Mandrake there is a patch available to make the kernel low-latency,
but apparently this compromises network security.  [(according to this site)](http://groundstate.ca/mdkaw) 
But this may not be the case with Demudi/Ubuntu.

**If the Ubuntu could run on the tuned Agnula kernel, with the same apps, it could be the basis for a Ubuntu/Agnula distro.**

Using Linux as a Digital Audio Workstation is now only now becoming a truely viable alternative to Windows/Mac platforms.  Applications like  [Ardour](http://www.ardour.org/), [Rosegarden](http://www.rosegardenmusic.com/) , and [Hydrogen](http://hydrogen.sourceforge.net/) in their own right, are approaching the functionality of successful proprietary applications.  

here are some good articles on the _Linux as a digital Audio Workstation_>>>>

[Using Linux for Recording and Mastering](http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm) 
An established studio in the USA is planning to rely on software
that can be freely downloaded from the Internet. Are they crazy, or do
Linux-based recording applications offer a real alternative to the
established Windows and Mac packages?

[Digital Audio Workstations on the Revolutionary Edge](http://www.devx.com/Intel/Article/15702) 
Intel's Richard Winterton explains why Digital Audio Workstations
(DAWs) are changing the way music is being created, both by
professionals and by audio enthusiasts. Yet you can get a powerful DAW
computer for less money than you think. In this paper, Winterton
discusses a few things to look for in the hardware when choosing a
computer on which to base your DAW, and gives you tips on how to choose
the right software. He also explains why he thinks you should take a
serious look at Linux as the ideal platform base. 

[>>>>An Introduction to Linux Audio ](http://www.linuxmusician.com/index.php?option=articles&amp;task=viewarticle&amp;artid=11) 

[Build it: Digital Audio Workstation](http://www.extremetech.com/article2/0,1558,1150193,00.asp) 

peace

---

### Post by chaotic on 2004-11-20
This is what Agnula has going for it so far, could this be combined with Ubuntu?

[from [http://www.agnula.org/documentation/dp_tutorials/](http://www.agnula.org/documentation/dp_tutorials/)]

_Underneath It All_

At the kernel level only the soundcore object is retained. AGNULA's audio driver system is the latest package from ALSA (the Advanced Linux Sound Architecture), a project designed to replace the ageing OSS/Free kernel sound driver modules. ALSA provides users with support for a modern sound system and provides developers with a modern audio applications programming interface (API). The project supports a wide variety of consumer-grade soundcards and audio chipsets, but it also includes support for some excellent professional and semi-pro audio interfaces. ISA, Plug-and-Play, PCI, USB, and serial port devices are all supported under ALSA. For developers the ALSA API has resulted in a high degree of interoperability between applications, giving the user the ability to freely connect ALSA-aware applications in creative and productive configurations.

AGNULA's Linux kernel has been optimized for low-latency. The patches that have been applied can dramatically reduce latency in multimedia systems to well within professionally acceptable ranges, demonstrating another powerful aspect of the GNU/Linux system. In addition to the low-latency patches we have applied the preemptive kernel patch to ensure low-latency over extended periods of time (e.g., more than 24 hours continuous performance). The realtime clock driver has been compiled into the kernel to provide high-accuracy timing for RTC-aware applications. Finally, kernel support for optimized hard-disk usage has been enabled and the hdparm utility is invoked during system start-up to ensure peak [U]disk I/O.

The Middle Ground[/U]

AGNULA's middle tier software includes the various ALSA utilities (such as the alsamixer and aconnect programs) and the JACK audio connection kit, a low-latency sound server for a network of JACK-aware clients. We have included as many such clients as could be found, and we have encouraged all GNU/Linux audio developers to provide JACK support in future versions of their software. AGNULA also includes support for the LADSPA plugins from Richard Furse's Computer Music Toolkit (CMT) and Steve Harris's collection. LADSPA is the GNU/Linux Audio Developers' Simple Plugin Architecture, an API that has engendered some excellent plugins that are available for use by any LADSPA-aware application.

The distribution strives to make the low- and middle-level software layers as transparent as possible to the new user. Utilities such as alsamixer or aconnect are always available from the master menu or the command line. We have also provided versions of those (and other) utilities with GUIs for users working in the X window system, such as the alsamixergui, ALSA MIDI Patch Bay, and QJackConnect software. Sox is another such piece of middle level utility software. SoX has been called "an audio Swiss Army knife" in recognition of its variety of uses. SoX is best known for its file format conversion utility, but it also provides a simple player and recorder along with a respectable selection of special effects such as reverb and chorus. AGNULA includes the standard-issue command-line version of Sox and a version with GUI for X.

_At The Top_

At last we arrive at the level of most interest to the normal user: applications ! GNU/Linux has long enjoyed a large number of useful audio and MIDI applications, and AGNULA has combed such listings as Freshmeat and the Linux Sound & Music Applications sites for the best of free audio software. So what will you actually find here ? Well, let's take a quick look at the kinds of software included with AGNULA :

    * soundfile editors (software for editing audio files in various formats)
    * MIDI sequencers (MIDI data recording systems)
    * hard-disk recording systems (multichannel/multitrack record-to-disk systems)
    * MOD trackers (module composition programs)
    * OGG encoders/decoders (file compression/decompression utilities)
    * sound synthesis software (programs and environments for creating and modifying audio data; includes the subcategory of realtime sound synthesizers, i.e., softsynths)
    * music notation apps (software for preparing and printing sheet music)
    * network audio apps (software for serving audio over a network)
    * media players (players for sound and video files in various formats such as OGG, MIDI, WAV, DVD, etc.)

Thanks to the power of the lower and middle layers many of these application types can work together in an integrated environment with very low latency and excellent realtime performance, all running under the exceptionally stable and secure GNU/Linux operating system. This is AGNULA: an environment rich in powerful applications for the creation, modification, storage, transmission, recording and playback of sound and music, an environment built entirely from truly free software and freely available for composers, musicians, and everyone everywhere.

---

### Post by TravisNewman on 2004-11-20
You could add the DeMudi repositories to your sources.list file and try to install the important packages through apt/synaptic but that's iffy. It sounds great though, and I'd DEFINITELY like to have audio apps on my install (setting up a pseudo-studio for the band) and I'd like to install this in a chroot environment if that's possible, but these are GREAT great apps for linux. I wish they had more specifics, I'd like to try installing some of these (or hell, maybe all of them) and seeing if I can get it running myself. It's late and I'm kinda rambling here...

---

### Post by chaotic on 2004-11-20
Hey 
There's a wealth of information here if you're not signed up already, 

[The Linux Audio User Archives](http://music.columbia.edu/pipermail/linux-audio-user/) 

and with the Agnula apps, these people should be able to help

[The AGNULA Mailing Lists](http://www.agnula.org/lists/) 

I hope it works, could be the basis for a Ubuntu/Agnula Multimedia Distro.

At present I'm weighing up Mandrake, (have learnt the security concerns don't apply to the 2.6 kernel), the Agnula Demudi distro or a Ubuntu/Agnula combination.

peace

---

### Post by halus on 2004-11-25
Hi forum

Going to to install Ubuntu Linux myself and try to put some Demudi on top of it. Have Demudi now, and it is really great, exsept I can not mount my firewire drive.I have tried really hard to get it up, and even with a lot of help I've had no luck. That is the main reason, and, ofcourse, Ubuntu got the better name :-)

Best regards

---

### Post by halus on 2004-11-25
I know Demudi is compatible with Debian Sarge (testing). Anyone knows if Ubuntu is compatible with Debian Sarge?


Halusa

---

### Post by ubuntu_demon on 2004-11-25
Isn't low latency only required by audio pro's ?

I mean if you're making music on consumer/amateur equipment would you notice the difference between a low latency OS and ubuntu ?

Maybe you can install some of agnula's app's on ubuntu and be happy with it. If you don't like it you could switch to agnula.

---

### Post by chaotic on 2004-11-25
Low-latency is important for anyone making music.
Even 10ms can be the difference between something sound right or sounding wrong.  It's essential.  I've read you can get sub 5ms latency with Demudi, depending on your system.  

Halus let us know how it goes.

Peace

---

### Post by halus on 2004-11-26
Have installed Ubuntu, but now I have to get some sleep (the clock is eight in the morning here), and then I am going away for the weekend. I will start to try some sound applications next week, and see if I need the Demudi-kernel and such.

Like Ubuntu so far. My firewire disk is working just fine with Ubuntu. Pjuh


Cheers

---

### Post by TravisNewman on 2004-11-30
Heyo, I found this massive list of sources.list entries. Definitely worth a look:
[http://www.inf.ufsc.br/~nardin/linux/debian/sources.list](http://www.inf.ufsc.br/~nardin/linux/debian/sources.list)
The DeMuDi section is as follows:
```

deb http://http.demudi.org/debian woody local main contrib non-free
deb-src http://http.demudi.org/debian woody local main contrib non-free

```
You can try sid, stable, and unstable in place of woody if you want more bleeding-edge stuff, but that's the ticket. The Demudi-Kernel should be in there.

I couldn't get these entries to work though, I'll do some tweaking later and see what I can do.

---

### Post by halus on 2004-12-01
Here is some entries, Demudi and Debian Sarge:
```
deb http://apt.agnula.org/demudi/ testing local
deb http://ftp.skolelinux.no/debian testing main non-free contrib
deb http://ftp.skolelinux.no/debian-non-US testing/non-US main contrib non-free

```

- I have removed all Ubuntu sources.

There is a Demudi metapackage, which is "used for upgrade purpoises", but I'm not sure what that really means. I will try it, and upgrade all packages from the sources above(36 to install 656 to upgrade, 2 will be removed). I will come back with a report.

---

### Post by TravisNewman on 2004-12-01
Excellent, yes that works better than mine :) I don't get it though, the server setup was basically the same for both of those. Ah well, what can you do? I didn't remove all ubuntu repos, but I did install the metapackage and nothing is broken, but I also don't see anything new really.

---

### Post by halus on 2004-12-01
I got one new thing over here; the JACK Audio Connection Kit(qjackctl) starts when I log in. But the stupid thing is that the Jack system will not load. First it complains of the lack of alsa sequenser,  which I think is fixed with "/usr/share/alsa-base/snddevices", but then it (qjackctl) complains:
```
jack_create_thread: error 1 setting scheduler parameters after thread creation: Operation not permitted
cannot start watchdog thread
cannot load driver module alsa
```

Anyone knows what this is about?



Edit: found that I had typed jackctl over, I meant qjackctl

---

### Post by halus on 2004-12-01
[QUOTE=panickedthumb], but I also don't see anything new really.[/QUOTE]

But you can install sound tools from the Demudi source?

---

### Post by halus on 2004-12-15
Anyone got Ubuntu to co-operate well with the Agnula-sources yet?

My attemt was a failure, softly said. I hate to admit I'm back at the MS/Warez wagon, and planning to stay here atleast till the next Demudi release, or till I get hit by a new (or old) and fancy virus/spyware/somethingelse. The paranoia is implied in every click in this shiny rotten warez existence.

Hope the next Ubuntu Linux release will be suitible for audio-production, and hope it will co-exist well with the Agnula sources for apt-get.
Any chanse?

---

### Post by chaotic on 2004-12-15
Thanks for your efforts Halus,
Myself, i'd like to go with Demudi, but it looks like Mandrake will offer me better hardware support/for non-music related things.
I read recently on [Turn Key Linux Audio](http://tkla.sourceforge.net/)  that  they are working on downloads for more Linux versions, so perhaps Ubuntu is one of them.

I'm stoked that Linux audio is viable, all these developers out there making good software for the love of it, it's how it should be really, The least I can do is use the linux applications to try and make great music.  $1000us for Logic Audio is criminal.  Charging commercial rates for individual users is obscene.  As well the better choice linux is the legitimate choice,  I can foresee the day when software companies start cracking down on warez users, like the music and film industries are doing now.  

You don't need to go back to MS.  Try a Demudi partition to learn the applications, or Mandrake + Thac's RPMs.  Have you thought of getting the firewire harddisk driver from Ubuntu or elsewhere and adding it to Demudi?  then your problem would be solved.

Peace

---

### Post by halus on 2004-12-19
Thanks for the pointer to Turn Key Linux Audio, chaotic.  Interesting indeed.

I could not stay two weeks at windows only, even if I got payed to do so. Going for the Demudi 1.2.1-RC1. The download got finished while I wrote this text. So good luck to me, and everybody else :-)

Please give a tell if you get any good or bad experiences with Mandrake, or other sollutions you may try out for audio works.

Happy winter-celebration (or whatever you may celebrate these days)
Happy new year.

---

### Post by geppy on 2005-02-11
[QUOTE=halus]I got one new thing over here; the JACK Audio Connection Kit(qjackctl) starts when I log in. But the stupid thing is that the Jack system will not load. First it complains of the lack of alsa sequenser,  which I think is fixed with "/usr/share/alsa-base/snddevices", but then it (qjackctl) complains:
```
jack_create_thread: error 1 setting scheduler parameters after thread creation: Operation not permitted
cannot start watchdog thread
cannot load driver module alsa
```

Anyone knows what this is about?[/QUOTE]

I'm not sure if you're still looking into this, but for the sake of other people finding this thread:

The problem was that you didn't have the realtime-lsm module installed.  The easiest way to install it is probably by using 'module-assistant', available in 'universe'.  Once you've installed it, you'll need to run 'modprobe realtime gid=29', which loads the realtime Linux security module with the group ID of 29 (the Debian audio group).

---

### Post by halus on 2005-04-12
[QUOTE=geppy]
The problem was that you didn't have the realtime-lsm module installed.  The easiest way to install it is probably by using 'module-assistant', available in 'universe'.  Once you've installed it, you'll need to run 'modprobe realtime gid=29', which loads the realtime Linux security module with the group ID of 29 (the Debian audio group).[/QUOTE]


Hi, I am back with Ubuntu, and have same error when starting qjackctl. After creating the module with module-assistent I get:
$ sudo modprobe realtime gid=29
Password:
FATAL: Error inserting realtime (/lib/modules/2.6.10-5-686/kernel/security/realtime.ko): Invalid argument

?

---

### Post by halus on 2005-04-12
Ok, did a reboot and the module loaded, and then qjackctl loaded fine, and then jack loaded too. So big thanks Geppy.

---

### Post by karoliina on 2005-06-27
Hi,

I just installed agnula/demudi stuff on my Ubuntu (Hoary). I haven't however tried
to install the kernel patch yet. I installed some 2.6.12-multimedia -kernel
in the belief that would be the solution, but apparently that wasn't - result
was just lockup. I will propably try to patch some functioning kernel soon as
with longer latencies, music making is not possible. I used to have the patch
working on old Redhat 9, but after that I switched to Suse and the audio
applications never really worked as they should and now I am trying things
with Ubuntu. I haven't done music for a while because my audio recording
computer haven't worked, however, I am feeling quite optimistic now...
At least now the audio works and we got Hydrogen running
successfully yesterday evening with the ST-Audio DSP-2000 C-port
(jack etc. works).

Best Regards,
Karoliina Salminen
[http://www.ampcast.com/karoliina](http://www.ampcast.com/karoliina)
P.S. Ubuntu is great, I am using it (Ubuntu Breezy) at work too.

---

### Post by soccerfiend76 on 2005-09-07
I am currently using Demudi on one machine and Ubuntu (actually I moved to KDE) Hoary on another.  The Demudi box for the most part worked out of the box.  The hoary machine took a little massaging to get going, but seems to be working fine.  

The only major change was that I built my own kernel based on the morph sources patches.  Currently this is a 2.6.11 based kernel (the linux audio mailling lists have a lot info on kernels and patches that are suitable for audio production).

Brief summary of issues

modprobe snd-seq-oss

this was needed to get midi working.  I just added snd-seq-oss to /etc/modules

realtime-lsm (handled in this thread)

I am also using the ubuntu backports as well as universe, multiverse and restricted.  I have found that ubuntu does not tend to play nice with regular debian sources, and so I try to stay within the ubuntu world.

Cheers

---

### Post by yaaarrrgg on 2005-12-20
oh... don't know if you've seen this thread ...

[http://www.ubuntuforums.org/showthread.php?t=97453](http://www.ubuntuforums.org/showthread.php?t=97453)

also, posted a howto on using set_rtlimits... works with the default breezy kernel ( see post 18 ).   realtime-lsm, it seems, is deprecated and probably more prone to problems.

---

### Post by drucer on 2005-12-21
[QUOTE=karoliina]Hi,

I just installed agnula/demudi stuff on my Ubuntu (Hoary). I haven't however tried
to install the kernel patch yet. I installed some 2.6.12-multimedia -kernel
in the belief that would be the solution, but apparently that wasn't - result
was just lockup. I will propably try to patch some functioning kernel soon as
with longer latencies, music making is not possible. I used to have the patch
working on old Redhat 9, but after that I switched to Suse and the audio
applications never really worked as they should and now I am trying things
with Ubuntu. I haven't done music for a while because my audio recording
computer haven't worked, however, I am feeling quite optimistic now...
At least now the audio works and we got Hydrogen running
successfully yesterday evening with the ST-Audio DSP-2000 C-port
(jack etc. works).[/QUOTE]

Hi!

And welcome to Ubuntu forums! It's always nice to see fellow Finns on Linux forums. Were you running 'planet CCRMA' audio software package on Redhat 9 before? It is indeed quite nicely "bundled", but unfortunately runs only on top of RH/FC.

However, hope is not lost. There has been discussion about starting a project to create something similar to Ubuntu Linux. Hopefully something will come out of it. It would certainly attract many musicians who are currently using Windows to create music.

I'm currently building my digital audio workstation on top of LFS (Linux From Scratch). It's because I never really found a totally satisfying audio distribution and I figured 'what the heck, I'll do it myself'. It's a lot of work, but I'm sure it will be very pleasing when it's done.

Good luck with trying to get the essential audio apps to work on Ubuntu! Please let me know if I can help you with something. I may not be able to help, but who knows, maybe I can.

---


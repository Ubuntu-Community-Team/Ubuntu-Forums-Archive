---
title: "qsynth segmentation fault"
date: 2009-04-28
forum: Ubuntu Studio
---

### Post by angelsneverdie on 2009-04-28
Hello, this is a continuation in a way of these posts:

[http://ubuntuforums.org/showthread.php?t=1068913](http://ubuntuforums.org/showthread.php?t=1068913)
[http://ubuntuforums.org/showthread.php?t=1072504](http://ubuntuforums.org/showthread.php?t=1072504)

but it also stands alone in a way.  Here is the situation:

I've got a midi controller (m-audio prokeys 88sx) and I am (or was) using it to teach myself how to play the piano.  I was using it with my laptop which was running ubuntu studio.  I had to ditch studio because while it let me play piano (was a bit slow, never worked great) it sucked at pretty much everything else.  So right now both my desktop and my laptop are running 9.04 desktop edition.

I want to start using it with my desktop (haven't tried with my laptop since i changed OS).  Here are the steps I took:

1. turned on the midi controller and plugged it in via usb.
2.  opened terminal
3.  qsynth -a alsa
4.  opened jack control and connected the midi controller to the fluidsynth
5.  realized i probably hadn't set up qsynth with a soundfont.
6.  set up qsynth with a soundfont.
7.  pressed a piano key and it sounded really distorted.
8.  went back to qsynth and tried to raise the buffer size to 512
9.  pressed okay and qsynth said it needed to restart the engine  - hit okay and it closed.
10.  qsynth -a alsa
11.  tried to set up the soundfont again, and it closed upon restarting the engine.  this is what it does all the time now.

here's the output:

> mitchell@mitchell-desktop:~$ qsynth -a alsa
Warning: no locale found: /usr/share/locale/qsynth_en_US.UTF-8.qm
Segmentation fault

anyone have any idea what is going on here?

Last time some really nice people tried helping me out and I got it working on my laptop, sort of - but i'd really like to find a solution.  again, all I want to do is play the piano!

Thanks in advance for your help!

p.s. here is some system info:
Processor	AMD Sempron(tm
Memory	2061MB (388MB used)
Operating System	Ubuntu 9.04
Audio Adapter	NFORCE - NVidia nForce2
Kernel	Linux 2.6.28-11-generic (i686)
Compiled	#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
C Library	GNU C Library version 2.9 (stable)
Distribution	Ubuntu 9.04

---

### Post by angelsneverdie on 2009-05-01
Update:  I tried uninstalling qsynth (sudo apt-get remove qsynth) and reinstalling it (sudo apt-get install qsynth) and am expieriencing the same problem.  Does anyone have any suggestions?

I don't really care if it is qsynth - I just want to use my midi controller to play the piano - are there any other options for ubuntu?

---

### Post by thorgal on 2009-05-02
hello,

qsynth is teasing you, isn't it! :lol:
which version are you using ? in a terminal:
```

dpkg -l qsynth* | grep ii

```

and also
```

dpkg -l *fluidsynth* | grep ii

```

I can think of other means for you to play the piano but it will be a bit more complicated as you would need to set up jack for audio as well. I believe the linuxsampler has a nice grand piano sound but you will need jack up and running well for a glitch-free experience. 

Otherwise, if you are patient enough, a big surprise is coming out soon for piano lovers ... but I cannot say more at the moment ... ;)

---

### Post by angelsneverdie on 2009-05-02
> mitchell@mitchell-desktop:~$ dpkg -l qsynth* | grep ii
ii  qsynth                                     0.2.5-2.2                                            fluidsynth MIDI sound synthesiser front-end
mitchell@mitchell-desktop:~$ dpkg -l *fluidsynth* | grep ii
ii  libfluidsynth1                             1.0.8-1.1build1                                      Real-time MIDI software synthesizer (runtime library)


That is the output i get from the commands you gave me . . . and it's mean to mention a big suprise and then not tell me!  bah

---

### Post by angelsneverdie on 2009-05-05
bumpy bumpy

---

### Post by angelsneverdie on 2009-05-09
Hello?  anyone out there?  my new year's resolution was to learn to play piano - and it not working is proving my wife right that I wouldn't actually do it!  I need to be right at least once!

---

### Post by angelsneverdie on 2009-05-10
update:

So i tried again tonight, hoping for a miracle.  I have changed nothing about it since the last time (save for the fact that i am using a new soundfont).  This time qsynth doesn't crash, but i get no sound.  when i press a key on the midi controller the little light in the bottom left corner of qsynth lights up as if it is registering that a key has been pressed,just no sound.

I don't know if this means i'm one step closer - or why the other problem mysteriously disapeared, but anyone have any ideas what is going on now?

yes, the speakers are on and the volume is up.

thanks!

---

### Post by angelsneverdie on 2009-05-10
i just noticed that the blank after "audio device" in the "audio" tab is blank.  I don't know what to put there though - i tried /dev/audio  but no go

---

### Post by rayj on 2009-05-10
Dumb hunches here:

sudo apt-get purge qsynth maybe? There might be a configuration file that's causing your new install to adapt the same old problem...then re-reinstall qsynth?

---

### Post by thorgal on 2009-05-11
I saw on the LAD mailing list that qsynth 0.3.4 was out. You can maybe find a deb package with that version ? Your version is 0.2.5, could be too buggy ... I know that some early versions are buggy (CPU hog, etc). The 0.3.4 version should have many of those bugs fixed.

If you cannot find a deb package for your ubuntu flavor, you might want to try to compile it. Have you ever done that ? it is not big deal if you understand the process.

---

### Post by angelsneverdie on 2009-05-11
I purged qsynth and installed .3.4  (got the deb file from this link:  [http://www.kde-apps.org/content/show.php/Qsynth?content=14131](http://www.kde-apps.org/content/show.php/Qsynth?content=14131)

qsynth isn't crashing but i'm still not getting any sound when i press a key on the midi controller.  qsynth does flash the light when i press a key but no sound. . .

maybe i'm having an alsa problem?  is there a way to test that?  i tried looking around but a lot of things seem like they depend on my being more advanced at using linux than I am.

thanks for your suggestions guys, i appreciate the help!

---

### Post by thorgal on 2009-05-11
... maybe a channel number issue ?

try kmidimon to snif the MIDI stream from your MIDI controller. It will display a realtime output of what your MIDI controller is sending if you connect kmidimon to it. I am sure you can figure out how to use it, it is rather trivial.

Then you have to ask yourself what qsynth is expecting in terms of channel  for this SF2 font. I have hardly used qsynth but it maybe easy to set it up to listen to specific channels. I vaguely remember someone saying that it was 1-based while ALSA-seq is 0-based but this is probably not true (?)

By the way, can you provide a link to the soundfont you are trying to use ? thanks.

---

### Post by angelsneverdie on 2009-05-11
the soundfont i'm attempting to use is:

[http://www.hammersound.com/cgi-bin/soundlink_download2.pl/Download%20USA;RolandNicePiano.rar;639](http://www.hammersound.com/cgi-bin/soundlink_download2.pl/Download%20USA;RolandNicePiano.rar;639)

i have no attachment to that font or any reason to use it other than the fact that it is free, so if you know of a better one by all means please let me know.

i used kmidimon and it said that when i pressed a note it was using channel one - so i went into qsynth channel control and made sure the sound font was set on that channel.  lo and behold - success!

Thank you thorgal - king of the danes!

---

### Post by angelsneverdie on 2009-05-11
ok, when i say success, i guess i need to qualify that.  It makes noise.  the noise it does make however is only vaguely that of a piano.  It sounds like someone recorded a piano on a handheld voice recorder (the old fashioned cassette kind) and then listend to the tape 8000 times, and then played it.  

I don't know if i don't have the settings right or if my soundcard just isn't capable of this or what - anyone have any idea what could be wrong?  or what I should check?

thanks!

---

### Post by thorgal on 2009-05-12
OK, you're making progress :)
I will try your SF2 file later today, when I get back home. 

About the surprise I quickly mentioned the other day, you still have to be a little patient ;)

---

### Post by thorgal on 2009-05-15
angelsneverdie,

the thing I was expecting just happened. I know the following costs money and is not open-source, but Pianoteq, the excellent piano modelling software (that I use for my ~ daily practice and production) has just launched a linux native version :D

you can try the free demo. Well, yeah, I am promoting some commercial soft here but I was so amazed by the windows version that I talked with one of the devs and convinced him to come up with a linux native version. I have been testing it  for them (I already had a user licence from the windows version which I ran via wine and wineasio with great success) and it beats the windows version! 

the linux version is JACK and ALSA aware. It is using the JUCE framework for the GUI so it is quite platform "independent" at that level. All the dev had to do was to write a jack and ALSA backend. I tested it against jack1 and jack2, at all latencies, tried to make it crash, etc. It works really really nice.

You should give the free demo a try. It is fully functional except for a few notes. If you're not convinced after that, that's fine too :)  

[www.pianoteq.com](www.pianoteq.com)

Note: the user licence is not exactly cheap (249 euros) but what you bug is more than a piano, it's an infinite number of piano. It is not sample based. They have studied the physics of grand pianos and modelled the whole thing. They could reduce equations and parameter space so that you could get a true grand piano sound in realtime. OK, I stop here ...

---

### Post by ethanay on 2009-05-16
I can vouch for Pianoteq, too :)  Thorgal helped me set up my system to use the Windows version in 64studio, and I am extremely excited that there is a Linux version now!  I want to help advertise it to the Linux community!

After all that hard work with Wine, dssi-vst, and WineASIO...I at least have the ability to run other windows audio programs if I need to :)

---

### Post by heldal on 2009-05-22
The Roland piano sounds fine here. Suspect you're caught up in the "usual" alsa/pulseaudio issues. I've had all kinds of problems with latency and noise with the default ubuntu 8.04 pulseaudio setup and have resorted to use the Jack audioserver for any serious sound processing. I use Ardour for multitrack-recording which pulls in most of the other necessary packages during installation. In the multiverse repo there is also a couple soundfont packages, one of which is huge and contains quite a few decent sounds (found in /usr/share/sounds/sf2/).

On top of that I've compiled and installed fluidsynth from [source]("http://fluidsynth.resonance.org/trac/wiki/Download") to get all the new features, as well as qsynth-0.3.4. You can also install [vmpk]("http://vmpk.sourceforge.net/") to have a virtual keyboard to test with which may be useful to eliminate external problems. 

The downside to using Jack is that it suppresses the pulseaudio-server while it is running. Desktop application will thus not have sound while the sound-editing applications are running.

---

### Post by angelsneverdie on 2009-05-27
pianoteq sounds great but unfortunatly $346.83 is just out of the question.  

I'll look into your suggestions heldal, but I've got to wait until i get my new video card in the mail as i fried the one that was in there. . .

thanks guys and I'll get back to ya.

---

### Post by angelsneverdie on 2009-07-25
Okay, my classes are over for the time being so I am ready to start working on this again.  I want to try to compile qsynth from source as suggested but have no idea how to do that or even where to begin.  any suggestions?

thanks!

---

### Post by angelsneverdie on 2009-07-25
By the way, i just downloaded and tried the trial version of pianoteq and love it.  i started it and it just worked, sounded great with no latency.  anyone have a few hundred dollars they're willing to part with?  

oh well.  I'll keep working on this qsynth problem.

---

### Post by turnback on 2011-09-27
Hi All

I'm having a related issue, I think... 

MY qsynth will not work. I've had Hydrogen up and running fine with Jack. (QJackctl). Audacity works fine too, have made some nice recordings from Hydrogen and ZynSubFX.  

I'm thinking it's a Midi Issue cos I can't seem to get QSynth running at all. I try changing the Audio to Jack and Midi to Alsa but both times when I restart QSynth with the new settings it crashes. Jack is up and running at the time. 

I'm running QSynth 0.3.5-1rebuild1, and these are the fluid synth settings: 

ii  fluidsynth                            1.1.3-3                                    Real-time MIDI software synthesizer
ii  libfluidsynth1                        1.1.3-3                                    Real-time MIDI software synthesizer (runtime library)

Is this a simple Midi issue? Or something else?


In the meantime will try d/ling Kmidimon and see if that helps. Not holding out much hope though. Rosegarden and Ardour don't seem to be giving out any Midi sounds either. I think the Midi is just not connecting to the synths. No idea why.

Thanks, I can provide any other info you need.

:)

PS I'm using all soft synths, no hardware...

---

### Post by jejeman on 2011-09-28
You need to mannualy make midi connections in Qjackctl in alsa tab.

---


---
title: "Give Studio a chance?: Audacity Latency vs. Rosegarden instability"
date: 2011-02-11
forum: Ubuntu Studio
---

### Post by crazy ivan on 2011-02-11
Hi,
I'm using the normal ubuntu and stick to audacity to capture ideas for multi-voice compositions with my piano.. 

This did not work from the start however:
1) Software-playthrough+recording does not work with my laptop-on-board sound-card, hence i had to use two different headphones- one piano, one soundcard- to record multi-track.. To change this situation I purchased an external soundcard:
[http://www.artproaudio.com/products.asp?type=90&cat=13&id=132](http://www.artproaudio.com/products.asp?type=90&cat=13&id=132). Which i can really recommend since its plug+play in both windows + linux and also performs well as a simple DI box / Preamp.

2) So now I hooked the monitors to the external soundcard and have nice multitrack recording environment in Audacity, except for terrible latency. I found out that the latency is almost perfectly minimized, when setting Edit>Preferences>Recording>Audio-to-Buffer to 60 (smallest value my soundcard handles smoothely) and Latency correction to -60. The result is no latency most times, and sometimes also really strong latency which has to be fiddled around with with the time shift tool. All in all its not unnerving enough to completely ruin my creativity, so I keep on using this setup.

3) Still I found this unsatisfactory and tried to upgrade my system to ubuntu studio following these [instructions]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu"). I figured out how to run the realtime kernel and started some recordings with rosegarden.. I did not notice any big latency, but did not get down to relly checking it since it crashed every five minutes and kept messing up my audio files. Since at that time I was mainly interested in using rosegardens MIDI and musical score features I did not venture too far into ardour and gave up on the Ubuntu Studio project, since it was killing my creativity. 

But now I got a new PC, and updated to 10.10 so I would like to know if its worth giving it a try again.. I mean, has somebody got rosegarden really working smoothely in a MIDI + Audio recording environment with 10.10? Is anyone using Ubuntu Stuido 10.10 to do multitrack recordings? Are there other tools than rosegarden worth the hassle of running an alternative kernel?

I would be thankful for some advice.. :guitar:

---

### Post by Pablo_F on 2011-02-11
Hi, 

For multitrack audio recording and low latency, there are better tools than Rosegarden and Audacity. Afaik, the most used are qtractor, and ardour. 

ardour has not midi tracks (ardour3 will have) but it is very good at multitrack audio recording. qtractor supports midi and audio tracks although its gui is rather different than Rosegarden's. 

As for the distro, as someone said, ubuntustudio is more ubuntu than studio. Actually, 10.10 has not a realtime kernel or a low-latency kernel available in the official repos. Ubuntustudio has not a separate repository and the "studio" of ubuntustudio does not imply realtime kernel. 

That said, the generic kernel is not that bad although a low-latency kernel is much better. A realtime kernel can help sometimes, depending on your hardware, but it is far from being a must-have nowadays.

There are distros based on ubuntu which are better tweaked than ubuntustudio for the audio studio, for example, [tango studio]("http://tangostudio.tuxfamily.org/en/tangostudio"). It runs a low-latency kernel and jackd1 in realtime mode out of the box (which is not hard to achieve in ubuntu without the need of a realtime kernel but anyway this is a bonus for TS). It does not install pulseaudio, which sometimes is a nightmare for linux audio beginners.

Make sure you choose your usb audio card in the interface field of Jack Control's Setup window, start the server, start ardour, and happy recording. 

For your reference:

[http://www.ardour.org/forum/9](http://www.ardour.org/forum/9)

Cheers, Pablo

---

### Post by crazy ivan on 2011-02-15
Thanks for the complete post Pablo, now I'm starting to catch up. I used to follow jacklab development, but that was back in Suse days... Let me comment on some of your answers:

> ardour has not midi tracks (ardour3 will have) but it is very good at multitrack audio recording.
Yeah its good and latencyfree. Effects (reeeeeverb ;) and mp3 (most of my fellow musicians don't have linux) export are missing though. Anyhow, most likely I'll switch to ardour for my personal rehearsal recordings / loops etc..

> qtractor supports midi and audio tracks although its gui is rather different than Rosegarden's.
Actually I like the GUI better.. And it seems to be doing the stuff it is capable of in a pretty clean way. I checked audio/midi (play along with metronome) latency in both programs and in qtractor it was barely hearable while in rosegarden I was a beat off! Thanks for the hint, I'll try to see if I can get more out of it.
Both tools seems to lack an "audio mixdown" option to quickly create audio files. And both do not come with a configured metronome :rolleyes:

> As for the distro, as someone said, ubuntustudio is more ubuntu than studio. Actually, 10.10 has not a realtime kernel or a low-latency kernel available in the official repos. Ubuntustudio has not a separate repository and the "studio" of ubuntustudio does not imply realtime kernel.

That said, the generic kernel is not that bad although a low-latency kernel is much better. A realtime kernel can help sometimes, depending on your hardware, but it is far from being a must-have nowadays.

Thanks for the information.. Thats really a big change here. With ubuntu 10.10 I was able to install rosegarden from repo and run it on my onboard soundcard, ardour showed 42ms latency. Didn't manage that in early 9.10 and had to mess with realtimekernel. Might be related to jack asking me about "change kernel to high audio priority" at install. > RT kernel definitely not worth it for my humble needs.

> There are distros based on ubuntu which are better tweaked than ubuntustudio for the audio studio, for example, tango studio. It runs a low-latency kernel and jackd1 in realtime mode out of the box (which is not hard to achieve in ubuntu without the need of a realtime kernel but anyway this is a bonus for TS). It does not install pulseaudio, which sometimes is a nightmare for linux audio beginners.

I'll see how far I get without rt, actually whats bugging me is not latency, but the missing functionalities of the programs to correct for it (and in general).

> Make sure you choose your usb audio card in the interface field of Jack Control's Setup window, start the server, start ardour, and happy recording.


Thanks man, at least now I know, that the MIDI sector looks pretty raw, while audio-recording is quickly set up. A bit sad, since I'm thinking about writing a DSSI plugin..

---

### Post by AutoStatic on 2011-02-16
> **crazy ivan said:**
> Both tools seems to lack an "audio mixdown" option to quickly create audio files.With Qtractor you can export your session, no MIDI though and no export to mp3.

> **crazy ivan said:**
> And both do not come with a configured metronome :rolleyes:Qtractor has a metronome, you only need to assign samples for the bar and beat ticks.

Qtractor has excellent DSSI support by the way.

Best,

Jeremy

---

### Post by Pablo_F on 2011-02-16
Hi, 

You can add effects in ardour, in the Mixer window. There are several reverbs available, including convolution reverb as a LV2 plugin, called IR. More on plugins here: 

[http://www.linux-sound.org/plugins.html](http://www.linux-sound.org/plugins.html)

qtractor hosts ladspa and lv2 plugins too, as well as dssi ones.

Indeed, ardour can't export to mp3. You can use audacity or other editors for the final cuts and mp3 exporting of the mix. Or use lame. For example:

lame -h -b 320 mysong.wav mysong.mp3


As for the latency, you set the latency in jack settings. Then, it doesn't matter much if you use ardour, rosegarden or qtractor. You can measure the real round trip latency with jack_delay (aka jdelay).


Ardour is the most advanced multitrack audio recording software you can find in Linux nowadays. You can supply the lack of midi tracks in ardour2 if you sync ardour with a midi sequencer like qtractor, and use the so-called jack transport. 

Cheers Pablo

---

### Post by AutoStatic on 2011-02-16
> **Pablo_F said:**
> qtractor hosts ladspa and lv2 plugins too, as well as dssi ones.You can add native Linux VST's to this list and Windows VST's with the help of DSSI-VST.

Best,

Jeremy

---

### Post by mango42 on 2011-02-16
Re: Qtractor and Ardour:
> Both tools seems to lack an "audio mixdown" option to quickly create audio files. 

Not sure about Ardour but you can run a second instance of Qtractor to mixdown into, or easier (IMO) is to use [JACK Timemachine]("http://plugin.org.uk/timemachine") for virtually distortion-proof mixdown.

---

### Post by crazy ivan on 2011-02-19
Thanks for the many useful responses. 

Concerning mixdown:
Ardour export to wav > lame convert to mp3 is definetely no problem.
Redirecting qtractor midi+audio output via jackctrl > ardrour > lame is not really convenient.. Apart from the time: blocking ouf sound for duration of track + fiddling with ardour, jacktctrl + conversion... I use linux because I want to evade repetetive tasks *sigh*. Maybe jack-timemachine is a bit less of a hassle, I'll check it out.

Concerning DSSI, Midi:
> You can add native Linux VST's to this list and Windows VST's with the help of DSSI-VST.

Thanks for the hint. I think I'll start my synthesizer in Windows-VST within a virtual box and try to keep it DSSI-VST convertible.

> Ardour is the most advanced multitrack audio recording software you can find in Linux nowadays. You can supply the lack of midi tracks in ardour2 if you sync ardour with a midi sequencer like qtractor, and use the so-called jack transport. 

Ok. I already tried this out. Works fine for input, but its kinda hard to fiddle things back together if you want to make changes in the midi-clip / overdub.

Concerning Effects:
Thanks Pablo, I didn't find this option even though I searched for it.. I already thought it has got to be there. I think they managed effect integration quite nicely in qtractor.

Concerning Latency:
> 
As for the latency, you set the latency in jack settings. Then, it doesn't matter much if you use ardour, rosegarden or qtractor. You can measure the real round trip latency with jack_delay (aka jdelay).

Hmm.. That really contradicts my experience: I set up ardour, qtractor and rosegarden and tried to record audio on click.. Ardour managed as the only one without latency (maybe auto-timeshifting for the buffer, which was set to 512ms).. In rosegarden it was really as if I heard the 512 ms.

Concerning metronomes:
I know the procedure, bu I don't WANT to pick my own click ):P . Ardour has a nice one, whats so bad about them being pre-configured?

---

### Post by Pablo_F on 2011-02-19
> Hmm.. That really contradicts my experience: I set up ardour, qtractor and rosegarden and tried to record audio on click.. Ardour managed as the only one without latency (maybe auto-timeshifting for the buffer, which was set to 512ms).. In rosegarden it was really as if I heard the 512 ms.

Ahm, you meant automatic latency compensation. OK. I meant software monitoring latency. Anyway, I realise now that you don't need a low latency in qjackctl's setup, as you are monitoring directly from the piano, aren't you. 

BTW, 512 are frames, not ms. 

> I know the procedure, but I don't WANT to pick my own click . Ardour has a nice one, whats so bad about them being pre-configured? 

I don't understand you, sorry. Do you want to set a tempo map in ardour and the click following this tempo map?

Cheers! Pablo

---

### Post by Jestermusic on 2011-02-22
Just a general reply regarding Audacity, Ardour and Rosegarden along with all of the other "sub-par" Digitial Audio Workstation programs in Ubuntu.
First; unless you are using a AISO compatable driver, you won't be able to access playback in any of the aforementioned workstations. Secondly, if you want to use VST or MIDI devices, you can't. 
 
Most of us (even those of us with several years of DAW experience) deal with frustrations related to audio recording and mastering in the majority of major brand DAWS. Sadly, the Linux offerings are even worse. This in an honest review of my experience with the aforementioned items as a semi-professional studio musician and sound engineer.
 
Audacity has some decent wave file editing features. Rosegarden is far too much work than it is worth. You will spend hours upon hours connecting your sound card and audio recording equipment only to find that there is no real VST support in that system. Hence, you will need to go back to a Windows based DAW if you want those things. Ardour is absolutely useless on many levels. You can record basic audio but cannot record midi or use any midi playback. You also cannot finalize a mix or save it as a true MP3. 
 
The most positive aspect of all of these systems is the latency. Linux, via the AISO driver support, has found a way to limit all of the latency in most applications when you use the JACK adudio plugin and device manager. Unfortunately, as mentioned before, it is pretty useless if you cannot use the programs as a complete DAW.  
 
I downloaded all of the systems and found myself switching back and forth between the programs in order to create one decent mix (without Midi). 
 
I am not complaining based on the fact that these are considered "open source" (even with the guilt trips that the founder of Ardour posts on his website), what I am suggesting is that Linux consider staying out of the Audio recording environment until they have a product worth offering. Audacity is by far the best of them but, lacks a considerable amount overall. 
 
Seriously, by putting out software that is laced with hype and expectations only to find that it is really nothing more than a pretty package with no substance is doing nothing but ruining the Linux reputation.
 
Finally, I tested these systems on Ubuntu 10.10 only to find that this operating system while touted as the most stable of the Linux systems, is anything but stable. After a few days you recognize that many of the drivers for audio, video and flash animation are compromised. You can get them working again at each boot however if type in "help" at the command prompt when Ubuntu is loading. Lastly, Firefox and the "chrome" browser constantly disabled network settings and require daily maintenance and monitoring. And the very last frustration is that in order to install third party software, such as cakewalk, pro-tools, reason, IL FL 9, you need to open a new terminal and give it a command path like you would have done in the old DOS programs. This meas that your drivers and other key functions are compromised at install and you really won't know it until you have examined the program under its preference tabs when you open it.
 
As much as I like the Open Source idea and do like the Linux phillosephy I cannot recommend programs and applications for this OS.
 
I am sticking with Windows until someone develops a better OS that does not require a high degree of maintenance to operate.:confused:

---

### Post by Pablo_F on 2011-02-23
> 
Just a general reply regarding Audacity, Ardour and Rosegarden along with all of the other "sub-par" Digitial Audio Workstation programs in Ubuntu.
First; unless you are using a AISO compatable driver, you won't be able to access playback in any of the aforementioned workstations.
 
ASIO? What is needed is a PCI or USB soundcard supported by ALSA or a firewire device supported by FFADO. And, on top of them, JACK. 

It is crucial that you get a soundcard that is compatible with ALSA or FFADO.

>  Secondly, if you want to use VST..., you can't.
This is not true. Many people are using VST effects and instruments in Linux. It is true that some VST won't work, but there are good plugins in native formats aswell (LADSPA, LV2, Linux VST). 

> ...or MIDI devices, you can't
Hardware support is far from ideal but if the MIDI device is class compliant, it will work. Some others do work. 


The whole post is completely OT. You are in a ubuntustudio forum. You should have come here before, when you were struggling. We would have helped you.

---

### Post by youWho on 2012-01-25
Frankly Jestermusic your comments are misleading. I was tempted to say something harsh, but I won't. Your comments are of the sort one gets from people who try using something new for a few minutes (or hours, or days), probably all the while bitching about how it's not up to par, then give up and gleefully report that they gave it a real "professional" test run. But in all honesty I don't get the impression that you've done so much work professionally in audio; I say this based on some of the clues that are in your post.

If it means anything to say this---I mean to newcomers who might read this---I've worked in audio for quite a number of years (indeed if I had a penny for every cut I made with a razor blade...) I recently switched from OSX to Ubuntu Studio and for me it's all good. It takes some getting used to, but when you do get used to the differences there are some excellent apps. I think most of the time when people are complaining about something being not "professional" enough what they're really saying is that they aren't familiar with it, or that they aren't as familiar with it as they are with what they know well.

For me the only thing new is gnu/linux itself, and because of that I  very much appreciate the amazing generosity of people in these forums.  I've received help when I was stuck, and as Pablo_F pointed out, you  would have too Jestermusic, if only you had asked.

---


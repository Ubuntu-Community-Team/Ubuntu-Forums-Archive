---
title: "Audio Interface - solve my problem and get $5"
date: 2009-04-18
forum: Ubuntu Studio
---

### Post by vaughnm on 2009-04-18
Ha!
just jokin about the $5

but down to business...
I have an Edirol ua-25. I have roland v-drums (td-6)
how do I make this work with audacity or ardour?

OR - 

If you know a good program to use with this interface let me know.

Thanks in advance for the help...maybe I'll send that 5 bucks after all....

---

### Post by Aurora on 2009-04-18
Hi,

Do you have JACK installed?  I believe the UA-25 is well supported in Linux through JACK and ALSA.  I don't know about the drum kit.  Dan Worth, host of the Open Source Musician Podcast, uses some kind of electronic drum to trigger samples in Linux, so it can be done, I just don't know how. [http://opensourcemusician.libsyn.com/](http://opensourcemusician.libsyn.com/)

JACK is essential for audio production in Linux.  It lets your hardware talk to ALSA and your apps, and lets all your JACK-aware software apps (like Ardour) talk to each other.  You can install it through Synaptic or apt-get.  Rather than pick individual software packages, you might want to install the Ubuntu Studio meta-packages--search for Ubuntu Studio in Synaptic.  If you choose the ubuntustusio-audio meta-package, it will install a whole suite of useful audio software, including JACK.

If you want to do some good with your $5, consider going to [www.ardour.org](www.ardour.org) and donating to the project.  Now that the project has no corporate sponsor,  it's completely community-supported.

---

### Post by Abu_Dayya on 2009-04-18
Also, Ubuntu studio 9.04 release candidate has just been released. It features the 2.6.28.rt kernel, which is necessary for realtime processing and low latency. Or you can wait another week for the official release of ubuntu studio

---

### Post by vaughnm on 2009-04-18
I have JACK... I can record with my interface just fine when it is guitar or bass. But when it comes to the drums I can't get it to work. 
It might be because I am going to my Edirol from my drums with a patch cord. 
Do I need to get a midi cable. They both support this.

I'm new with recording on Linux but am intrigued. 

Can someone explain real-time and the reason I want low latency?

---

### Post by poundjd on 2009-04-18
> **vaughnm said:**
> Can someone explain real-time and the reason I want low latency?

Almost all modern Operating systems us a multitasking kernel. What does that mean? Well the impact is that there is no knowing how fast a request to your computer is answered, Now understand that because the computers are very fast, in most things this does not cause any problems.  But for some things that really require true "Real Time" response this is not acceptable. 

   In the early days of computers this was much more of an issue. I ran a VAX 11-780, we often had a variance of 100 ms (1 tenth of a second) or more in the response times. For terminal users this was not noticeable, but for control of some machinery in the laboratory this was totally unacceptable.  So we used a different VAX 11-780 with a special Operating System, that was advertised as "Real Time" what this really meant was that when the laboratory machinery asked for service ( Interrupt ) the OS starting processing that request in less than 25 ms.

Now Low Latency has a similar meaning, It refers to how fast you get through doing something.  As as an example in networking low latency refers to how fast a packet can get to the destination and it's answering packet is received, back at the starting location.  This has a huge impact on network through put.

basically Latency is how long you wait for something to complete.

Sorry if this is too long, Just got a little carried away. 
-jeff

---

### Post by Abu_Dayya on 2009-04-19
> **vaughnm said:**
> 
Can someone explain real-time and the reason I want low latency?

Say you recorded your drums in ardour, and now you want to record your guitar tracks. What will happen if you don't have low latency and real-time processing? You'll start listening to the drums track through your speakers and start recording the guitar over them, and everything sound fine and in beat. Now you're done with that particular track and want to playback your recorded drums and guitar, and you will hear the guitar being late and not in beat or in sync with the drums track. Although you are sure you played the track exactly as it should be, it  still turned out to be a little bit late.

That is what will happen if you don't have low latency

---

### Post by thorgal on 2009-04-19
ardour is smarter than that: every recorded material is latency-compensated. Whatever latency jackd is set up to, ardour will know it and realign the wave form at the right time.

latency is an issue if you use SOFTWARE-monitoring (inconvenience when applying e.g. guitar effects via plugins to the incoming signal feed), or record from an app or a device that have a lot of latency and does not publish it to jack. If you use e.g. hardware inserts and you had measured (in frames) the latency of this hardware chain, you can use a special LADSPA plugin on the track where this insert point is located to correct for the latency when you have recorded something. This plugin is configured with the number of frames you have estimated above.

If you have many tracks in ardour, with various plugins in each of them, etc, you never wondered how you can hear the whole thing at the right time ? each plugin introduces a different latency due to its processing. And the LADSPA or LV2 spec requires that the plugin publishes its latency. So ardour will know it and when it starts the transport, will make the necessary calculation during its buffering so that you hear all tracks at the right time.

There are some apps that do not publish their latency, like a VSTi hosted by dssi-vst. The recorded material will be off by a few frames, due to the internal VSTi processing. A bit annoying but it is already cool that one can use win32 VSTis in linux ;)

---

### Post by vaughnm on 2009-04-19
Great, thanks for the explanations. My next question is how do I get Ardour to recognize my audio interface?
I changed my sound properties in >System>Preferences>Sound to Edirol USB interface
When I want to record I open JACK, press start and then open Ardour.
I have ardour connected to JACK but when I go to record the mic in my laptop records the sound, not my Edirol.

It works great in Audacity and I get great sound but I like ARdour and want to keep using it but this is preventing me from moving forward. How do I set Ardour up to recogize my usb interface?

---

### Post by thorgal on 2009-04-19
you need to know how ALSA has indexed your USB sound card.

From a terminal, type

```

cat /proc/asound/cards

```

spot the USB card index.

Then, in qjackctl (the jack control GUI), open the setup window, and look for a device option. You should see a list with hw:0 and hw:1. Pick the one corresponding to your USB card index.

This option in the jack control GUI is a bit hidden so you'll have to look for it carefully ;) 
Once you picked the right card, you can start jack.  

Good luck :)

---

### Post by vaughnm on 2009-04-19
Great, thanks a lot! That worked. 
NOW, will I need to update my kernel to keep my latency low?
AND...my drums still arn't working. Will getting a midi cable solve the problem?

---

### Post by thorgal on 2009-04-19
is your drumset an e-drum that outputs MIDI events ?

as to the latency: get a 2.6.29 kernel patched for realtime (complete preemption patch by the RT kernel guys).
This kernel serie will do wonder :)

I don't know about packaged kernels as I compile mine. The latest RT kernel is amazing! I am currently using 2.6.29.1-rt8.

---

### Post by vaughnm on 2009-04-19
I have no idea how to update my kernel. This is all new stuff to me so some info on that would be great.

Also, my drums are V-drums, Roland td-6
They have a MIDI Out and 2 1/4 inch outs. One for left and one for right.

A question though...Am I losing sound quality going with midi?

---

### Post by vaughnm on 2009-04-19
Ok, so I've been able to get my drums connected bia patch cord and the sound quality is good. Although, there is one issue. When I record every 5 seconds or so the sounds cuts out. It just makes like a click sound and continues on. Anyone know what this might be and would updating my Kernel to 2.6.29.1-rt8 fix it?

---

### Post by thorgal on 2009-04-19
vaughnm, I see you are not familiar with MIDI. Let me explain briefly:

MIDI is not about sound, so you cannot wonder about sound quality through MIDI. MIDI is "information". In your case, each time you hit a drumkit piece, the brain of your e-drum will produce a MIDI event, it's a bunch of info containing all sorts of data: note, velocity, duration, etc (you can always google the MIDI data specification if you're curious).

Your e-drum must have an internal sound bank. Each sound sample corresponds to a particular MIDI event. So when the MIDI event is produced, your e-drum will trigger the corresponding sound sample, and that's what you hear. Depending on the quality of the sound bank, your drumming will sound more or less realistic.

While patching the audio output of your e-drum to your PC is one option (if you like the sound of it), it is much more flexible to record the MIDI events in your PC. Why ? because you can replay the MIDI sequence and output the MIDI events played back to a sound sampler of your choice. This means that you can completely change the way your sequence sounds by choosing another sound bank. Software synth are made precisely for this: being triggered by MIDI notes and output the sound samples they contain. So you can replay your drum sequence not through a drum sample bank but e.g. piano samples. That would sound weird as there is a MIDI note-to-sound sample mapping in the piano software synth that would not make sense for a drum MIDI sequence.  

So, concretely, if you go the MIDI route instead, you plug a MIDI cable from the e-drum to your PC MIDI input port )could be USB, ALSA can handle that well through USB). The MIDI cable will transport the notes information (which is digital, you have to understand this, there's no analog audio signal involved at all, this is a bunch of data formatted in "bits and bytes") to your PC. 

Fine, what do you do from there ? open up a MIDI sequencer like qtractor, rosegarden or muse for example, and record your drum line in MIDI into a MIDI track. You can of course use your e-drum audio output as realtime monitoring, but what counts is that your record your crazy drumming session in MIDI.

Later on, you can either replay the MIDI track back to the e-drum (PC to e-drum MIDI cable) and thereby trigger the e-drum sound samples, OR, and that's where the fun is, trigger other sound samples located in your PC inside a software synth simulating a drumset. 

Hydrogen is such an app, you can get it from your package repos. It can receive MIDI input events from either a sofwtare sequencer or from a hardware plugged to your PC like your e-drum. There's of course a note mapping to respect, i.e. if you hit your hihat, you want the software app to play its internal hihat, not floor tom :lol:

OK, I guess you see the picture.

I do my drumming like this: I do not have an e-drum so I program my MIDI sequences directly in a software sequencer (rosegarden). I use a VSTi (virtual instrument) simulating a drumset and output the MIDI notes from rosegarden to the VSTi MIDI input port. The VSTi will then produce a realistically  sounding drum sequence. I even made a very lame video showing that. It's super lame, I say nothing, I just fire up the softwares, plug things together inside the jack connection window, and that's all. But it should show you what one can do.

If you are able not to fall asleep through it, try to understand what I am doing :lol:

[http://www.youtube.com/watch?v=Ys1s3Dk5sGo](http://www.youtube.com/watch?v=Ys1s3Dk5sGo)

PS: I forgot to add: if you open a terminal and type 
```

uname -r

```

you get your current kernel version.

---

### Post by vaughnm on 2009-04-19
Cool cool. I checked out the video. It was complicated but I'm intrigued to learn more about Linux recording. 
So basically what you are saying is that if I want to record usind MIDI I need to get a midi sequencer? Is that right? 
Right now I'm just using Ardour for all my recording needs. 
I've tried hooking my drums up to my interface and when I record in Ardour it becomes kinda crackily but only every like 5 seconds. 
Would it be better to record the drums seperately with a midi software? 
I'm really bad with JACK. I don't really know how to use it properly but I'm getting use to it. 
Everything works fine except the cracking drum issue. Will upgrading help this problem?
Sorry about being so unfamiliar with all of this. It's new to me but I am excited to learn about it. 
I havn't used VST's before and don't really know how to go about it. 
I appreciate your patience and any help would be great.

---

### Post by vaughnm on 2009-04-20
anyone?

---

### Post by markbuntu on 2009-04-23
Read and learn

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---


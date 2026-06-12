---
title: "My experiences with U/S 14 LTS, and JACK... A Learning Curve."
date: 2014-06-30
forum: Ubuntu Studio
---

### Post by weaseldb83 on 2014-06-30
I've always loved the release concept for Ububtu Studio; However, JACK has always been the reason I never kept it around. This time I'm gonna work my hardest and learn how to use this suite before I wreck my install with lines of patch fixes until I just give up again.

I managed to install the clean 14 LTS release. Guess what, JACK, well I couldnt get anything tu function. I ended up removing and re-installing PulseAudio. That did the trick and jack is finally running at least with few errors. It even auto locates some of the modules in the _*Connections Bay*_ segment.

So now that I've got basic funtionality; How does somebody work it and use it? Simple statement enough, but seriously. I've tried reading about it. But sometimes the logic of it all is just, well, [FONT=microsoft sans serif]*weird*[/FONT]...

Thats good enough for an opening post. I'll begin to update with pictures, specs, hardware and what I have gotten working.

---

### Post by slonk on 2014-06-30
What exactly are you trying to do? Jack is just a demon. It doesn't do anything for you as such.

---

### Post by weaseldb83 on 2014-06-30
WOW, quick reply; For Instance...

Well really understanding how it works in the connections and patchbays.

I also want to learn how to, under the UbuntuStudio suite, to best acomplish a multi track recording of a single event.
Say like having three to four inputs recording at once. I've been advised to run something like that through JACK routing. Or how about an alternative to Audiacity; which is great for recording single input tracks to mix together, but damn near imposible for multi input scenarios.

---

### Post by slonk on 2014-06-30
What you need is an audio workstation, e.g. Ardour.

---

### Post by jejeman on 2014-06-30
Never uninstall pulseaudio, just turn it off.

---

### Post by weaseldb83 on 2014-06-30
> **slonk said:**
> What you need is an audio workstation, e.g. Ardour.

Ardour comes installed but I have never been able to assign an input to any track. I know I'm missing something obvious.

---

### Post by slonk on 2014-06-30
> **weaseldb83 said:**
> Ardour comes installed but I have never been able to assign an input to any track. I know I'm missing something obvious.

No, the UI leaves much to be desired.

There are a couple of other workstation pieces for Linux. The field changes constantly.

---

### Post by QIII on 2014-06-30
I would like to remind everyone that this is a family-friendly forum.

---

### Post by weaseldb83 on 2014-06-30
Say I wanted to do this in one take:

#1 ) USB - guitar input
#2 ) Front Hardware Mic - Vocal Mic
#3 ) Rear Board Hardware Mic - Room mic

What recording workstation environment would be best suited and how to connect and assign tracks for mixing?

---

### Post by jejeman on 2014-07-01
Are you suggesting to use two different sound cards, of which one is on board and can use just font or back Mic at one time?

---

### Post by weaseldb83 on 2014-07-01
One Motherboard; 3.5mm multiplex & remote duplex via connect pins

Selected Output From Hardinfo:

Processor - 4x AMD A8-6500 APU with Radeon(tm) HD Graphics
Audio Adapter - HDA-Intel - HDA ATI HDMI
Audio Adapter - USB-Audio - Logitech USB Microphone
Audio Adapter - HDA-Intel - HD-Audio Generic 7.1 
  - Duplex 3.5 mm
[TABLE]
[TR]
[TD="class: field"]HD-Audio Generic Front Headphone
[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Line Out Side[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Line Out CLFE[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Line Out Surround[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Line Out Front[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Line[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Rear Mic[/TD]
[TD="class: value"][/TD]
[/TR]
 [TR]
[TD="class: field"] HD-Audio Generic Front Mic

Audio device - Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
[/TD]
[TD="class: value"][/TD]
[/TR]
[/TABLE]
 Audio device - Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)

---

### Post by jejeman on 2014-07-01
1. Use just one card. Using two cards is bad.
2. Onboard cards cannot record from two diffrent mic inputs at the same time, only form one.

---

### Post by luctor on 2014-07-02
what you are trying to do is called el-cheapo
and without hacking hardware it won't work
If you really need multi-track simultaneous recording better buy a multi-track soundcard

[http://quicktoots.linux-audio.com/toots/el-cheapo/](http://quicktoots.linux-audio.com/toots/el-cheapo/)
[http://alsa.opensrc.org/TwoCardsAsOne](http://alsa.opensrc.org/TwoCardsAsOne)

---

### Post by peethagoras on 2014-07-02
Greetings weaseldb83.

The name Jack is a good clue: jackplugs are used to make audio connections between different bits of hardware kit. Associate with the 'AUDIO' tab in the Jack connections box.
DIN plugs are a bit like Jack plugs in that they plug in and connect stuff. MIDI was connected with DIN plugs. Associate with the 'ALSA' tab in the Jack connections box. Depending on your set-up, the MIDI tab might display connected modules and ports.

You don't have to start Jack to connect stuff automatically: some apps will register in ALSA or MIDI tabs, but to connect audio Jack must be started. 

'Starting' refers to using the tape recorder-like 'play' button in the upper left side of the main Jack box, this is not a Jack control: refer to the 'tape recorder' symbols under the display. These are used for MIDI syncing etc.

I am not a great fan of Jack control, but it has shown some useful benefits. 

Hope this helps a little.

---

### Post by brianmc on 2014-07-11
Using JACK takes a little getting used to. It is best thought-of as an alternative to PulseAudio. One designed to cope with near-realtime audio work and have sound signals routed with - if not minimal - at least fixed and known latencies.

Because of that, you simply can't mix-and-match audio devices and expect it to perform magic. If you want multiple inputs, you need to have a single card which has those multiple inputs. Otherwise, your input audio signals will take longer to get from the plug to the recording software, drift out-of-sync, and ... it just isn't worth the grief. Linking multiple cards is a black art, and you can't borrow my witchdoctor kit. ;)

From what you've posted, your built-in audio is the near-standard Intel HDA. It **is** possible to retask some of the jacks on that, but I would neither recommend it, nor expect you to be able to get above the two listed (line in and mic in). In short, your built-in sound card is designed for playback, not recording. You can't use it and the USB input at the same time with Jack because the two drivers would never deliver the samples to JACK at the same time (if they'll even deliver them at the same bitrate).

If there's an old-fashioned PCI socket in your machine, then a lot of fairly good well-supported multichannel cards can be picked up cheaply on Ebay. I've one machine with a Delta-66 card, another with 2xEdirol DA2496 cards, and a 'floating' Akai EIE I/O USB interface. The first gives me 4 line ins and S/PDIF; the second 8 in, 8 out per-card (plus S/PDIF and the option to sync the pair of cards; I've had to patch the kernel to make that work, so don't think what you hoped to do is at-all easy). The Akai, although not capable of as-high-quality as the Delta 66, gives me 4 inputs and outputs with decent mic/line/DI inputs.

With any of those cards, I don't need to use JACK to chuck all the inputs into something like Audacity and get in-sync recording; but, playback at the same time is out of the question *unless you're using JACK and driving the latency as-low as your hardware can cope with.*

As I say, check Ebay. I'm in the UK; and, were I in the market for another card, I see a nice TerraTec DMX 6Fire going for £10 (albeit missing a cable). PCI is a good way to go when trying to keep costs down on Linux because drivers for newer versions of Windows simply aren't being written.

---

### Post by jmarra on 2014-07-11
I suggest using "Patchage" to map devices (midi trigger, analog, synth, etc).  It does what Jack does but it doesn't require you to know how to adjust settings like a Jack controller does.  For instance with Ardour (and Patch running) you can open a virtual synth and a synth plugin...     ...pull your patchage window up and see a physical representation of the devices as if it was a physical patch bay with wires...     ...you can click on the output of one thing (like the synth plugin) and then click on the input of a track you created in Ardour.  the two are now linked and whatever you play on the synth will be "heard" by the track you mapped it to.   Patchage comes with Studio 14.04 and is so simple.  Takes about 20 minutes of playing with before you understand all it can do with your various devices/virtual devices.  In most cases this eliminates needing to use Jack Control.  Use can save sessions in it as well...   ...like if you are always going to use Ardour, a virtual keyboard, a certain plugin, and an analog audio connection, you can have patchage open with that configuration.

---

### Post by brianmc on 2014-07-12
> **jmarra said:**
> I suggest using "Patchage" to map devices (midi trigger, analog, synth, etc).  It does what Jack does but it doesn't require you to know how to adjust settings like a Jack controller does.

With what the original poster requested, and cited as their listed sound devices, that isn't going to help much. Using Patchage to start up Jack will default to the first sound card, their built-in Intel HDA. Nor, I suspect, would it set the Periods/Buffer to 3 as-required for using a USB sound device.

That being said, it'll probably help getting to grips with the absolute basics of using something like Ardour. I'm just finishing up the cleanup of the last track of a live recording and will snag a bunch of screencaps on the basis of how many words pictures are worth...

---

### Post by brianmc on 2014-07-12
As-promised, here are some screencaps. These are from work on a real session, so it is a little messy looking.

First, **Patchage**.[ATTACH=CONFIG]254665[/ATTACH]

What you're looking at is me partway through cleaning up a recording session. Every line is the equivalent of a patch lead, you can simply click and drag from one point to another to make further connections.

I'll point out you won't initially get Ardour showing as two items in Patchage. To get that view, you have to right-click on the top of the box and select "Split".

As should be relatively easy to work out, blue is audio, and red is MIDI. I'm using a Behringer BCF2000 as my controller to do the mixing and record all the automation. How much fine-tuning you might want to do on something like that is entirely up to you.

If you're wondering why I've got 12 in, 10 out on system? I'm using an Edirol DA2496 card.

The rest of the wiring complexity will become more-obvious when we move onto the Ardour screencaps. They're a good-deal more interesting to look at; this is just the Ubuntu Studio equivalent of the "rat's nest" of wiring every engineer and musician should be well-used to.




[HR][/HR]

Now, **Ardour**; with several screenshots. The mixer window (subsequent screencaps) isn't usually displayed by default, but can be pulled up from the Window drop-down menu shown in this first screencap. The same applies for the Meterbridge window seen here on the right. [ATTACH=CONFIG]254666[/ATTACH]

What you're looking at is three recorded tracks, three busses, three processed tracks, plus one I'm using for noise removal.

The following two Ardour screencaps are of the mixer window. The second is annotated because you don't have to keep flipping back to Patchage to wire things up. There are points at the top and bottom of each mixer strip where you can access the signal routing to/from a strip.

I've got the noise gate on the third track opened up, and you can access any f/x you have on a strip simply by double-clicking on it.

[ATTACH=CONFIG]254667[/ATTACH]
This last screencap should help clear up some more of how to work with Ardour ...
[ATTACH=CONFIG]254668[/ATTACH]
I've highlighted where the noise gate is on the mixer, as well as showing the inputs and outputs on a couple of mixer strips. If you go all the way back to the Patchage screencap, you'll see that the highlighted details match up with the graphical representation of the studio arrangement. You can connect/disconnect in either Ardour or Patchage; the latter gives you that helpful 'trace the signal' overview.

---

### Post by weaseldb83 on 2014-07-13
> **brianmc said:**
> Using JACK takes a little getting used to. It is best thought-of as an alternative to PulseAudio. One designed to cope with near-realtime audio work and have sound signals routed with - if not minimal - at least fixed and known latencies.

Because of that, you simply can't mix-and-match audio devices and expect it to perform magic. If you want multiple inputs, you need to have a single card which has those multiple inputs. Otherwise, your input audio signals will take longer to get from the plug to the recording software, drift out-of-sync, and ... it just isn't worth the grief. Linking multiple cards is a black art, and you can't borrow my witchdoctor kit. ;)

From what you've posted, your built-in audio is the near-standard Intel HDA. It **is** possible to retask some of the jacks on that, but I would neither recommend it, nor expect you to be able to get above the two listed (line in and mic in). In short, your built-in sound card is designed for playback, not recording. You can't use it and the USB input at the same time with Jack because the two drivers would never deliver the samples to JACK at the same time (if they'll even deliver them at the same bitrate)...

Great info. Thanks. Thats the direction of advice i like. Not just a simple no, but why too.

Really opens my eyes about what I should be using my setup for. I should be viewing my setup as just an advanced R-R recorder with some neat post effects. I think I'm gonna just buy a 4-Track mixer to do what i"m looking for; and group my sessions that way.

So far Audiacity is my go to program to lay something. It is intuitive and simple. That being said, I'm wondering about Ardour. It looks pretty, but I've tried several tutorials with only partial success. I can sometimes see inputs active. but have never been able to use it to capture & record. Is it even worth fixing and running? Or is it honestly worth learning compared to the simplicity and reliability of Audiacity?

---

### Post by brianmc on 2014-07-13
> **weaseldb83 said:**
> Great info. Thanks. Thats the direction of advice i like. Not just a simple no, but why too.
Thanks!

A wise hacker (called Gandalf) repeatedly told me "there are only pros and cons". He's spot-on; you can't tell people what to do, but you can warn them off the dead-ends, and help them pick a path which they can follow for a while.
> Really opens my eyes about what I should be using my setup for. I should be viewing my setup as just an advanced R-R recorder with some neat post effects. I think I'm gonna just buy a 4-Track mixer to do what i"m looking for; and group my sessions that way.
The screencaps I provided are from mixing/cleaning/mastering a charity gig I recorded. The venue had a ZED-10 mixer plugged into their PA. I'd planned to use that, plus my Akai EIE I/O for recording; but, when I hooked the two up, there was a horrific mains hum due to appalling mains wiring in the venue. For that, I need to make myself a little ground-lift box. What I was left doing was using three 'spare' mics, scattered across the stage, to capture what I could.

Something like the ZED-10 might-well suit your purposes. However, as-soon as you mix down you lose the ability to do overdubs, punch in, etc, etc.

> So far Audiacity is my go to program to lay something. It is intuitive and simple. That being said, I'm wondering about Ardour. It looks pretty, but I've tried several tutorials with only partial success. I can sometimes see inputs active. but have never been able to use it to capture & record. Is it even worth fixing and running? Or is it honestly worth learning compared to the simplicity and reliability of Audiacity?
Audacity is, sorry to say, '*a toy*'. If you can lay something down in one take? Great. If not? It ain't the tool to use.

Ardour is well-worth getting to grips with. I chuckled at an earlier poster getting their comment edited for profanity. Powerful and sophisticated software enables you to do amazing things, as well as becoming so frustrated that you break things and swear profusely. The way to learn is to aim low, exceed your expectations, and know you can make it work when more-complex efforts go a little wrong.

Here's a suggested route for getting to grips with Ardour:[INDENT]You've got a USB doohickey; check the manual/documentation for it. What sample rates does it support? (44.1kHz? 48kHz? 96kHz?)
Pick the highest sample rate, and set up QJackCTL with that. If it's giving you problems, brain-dump what you find here, and folks will try and help you get it working reliably.
When you get it starting, running with as-low a latency as-possible, just wire the inputs straight to the outputs using Patchage. Once you're happy you can play through it, then you're ready to record with it. This is where you'll want to bring Ardour into the equation.
Disconnect absolutely everything in Patchage when you first start Ardour. Then, add a mono audio track.
Connect your USB input to the new mono track; connect the mono track to the master L/R, and connect the master outputs to playback.
'Arm' record on the track you've created (you'll hear nothing until you do!)
Tweak levels until you're happy with the output sound, and arm the master record.
Start recording, and play.
Disarm the track's record, and disconnect it from the input.
Check you can play back what you've recorded.
Add another mono track, wire it to the master, and connect your inputs to it.
Arm that mono track, and the master, then play along with yourself.
[/INDENT]

There are more-than-a-few professional recording studios actually use Ardour, so your efforts will not be wasted here. As-said earlier, this ain't a toy; I first played with this stuff about four or five years ago; most of what I've figured out has been on my own, and I'm not a musician. I'm a Systems Analyst (25 years of that s**t); the musician friends whose crap sound made me first attack a mixing desk all swore by Mac and Windows software. I've spent a few grand playing in 'real' recording studios; what you *can* get in Linux would make 'Abbey Road'-era George Martin drool. So, persist.

---


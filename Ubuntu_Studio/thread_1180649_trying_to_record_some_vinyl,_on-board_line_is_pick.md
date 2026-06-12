---
title: "trying to record some vinyl, on-board line is picking up better than audigy 2 zs"
date: 2009-06-07
forum: Ubuntu Studio
---

### Post by scarf on 2009-06-07
hi all,

i am trying to record some vinyl records in 24-bit, 96 kHz using audacity 1.3.5, and it appears that my on-board line is picking up way more of the spectrum than the audigy 2 zs line... 

i know the audigy 2 zs is an old card, and my on-board audio is about 6 months old, but i would expect the audigy to at least do as well.  look at these spectrums.

first, from the audigy 2 zs line,

[[img]http://img245.imageshack.us/img245/9030/68214472.th.png[/img]](http://img245.imageshack.us/img245/9030/68214472.png)

and then, from the on-board line,

[[img]http://img40.imageshack.us/img40/9505/fooj.th.png[/img]](http://img40.imageshack.us/img40/9505/fooj.png)

(two different records but i tried the same record from the first screen-shot and it looked just as much better).

it appears the audigy is picking up tiny bits of samples that go past 22k, but the on-board picks up way more.  i've verified in the audigy's manual that it can capture 24-bit, 96khz on the line input.... so i am just confused here at the staggering difference.

the devices i'm recording from in audacity have (Alsa) next to them, so could it be some ALSA setting that is preventing the audigy from picking up more?  a mixer setting or something?  kernel module?

both recordings come out just as loud and both sound great.

or, is the audigy just incapable of handling that much frequency at once....?

ok here is some hardware details:

```

$ sudo lspci -vvnn

[...]

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8288]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at fe6f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

[...]

05:06.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
	Subsystem: Creative Labs Device [1102:2004]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at e800 [size=64]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

```

thank you

---

### Post by igorzwx on 2009-06-07
[http://ubuntuforums.org/showthread.php?t=1145822](http://ubuntuforums.org/showthread.php?t=1145822)
[http://n2.nabble.com/user/UserNodes.jtp?user=126956](http://n2.nabble.com/user/UserNodes.jtp?user=126956)
[http://n2.nabble.com/Audacity-f238276.html](http://n2.nabble.com/Audacity-f238276.html)

-> Audacity forum
Ask them!
They tend to believe that Audacity is usable on Ubuntu

---

### Post by kayosiii on 2009-06-07
Most indidivuals can't hear past 20k
Most Microphones don't go much past 20k...
Most Rock and Pop music doesn't do anything interesting above 18k...

Some Sound Cards will filter above a certain frequency. The audigy is possibly one such card. If you are convinced that the original recording was made with equimpent that recorded higher frequencies and the music actually has interesting things going on above 22k then the onboard recording may be useful. otherwise I wouldn't particularly worry about it.

---

### Post by scarf on 2009-06-07
why would the audigy filter any frequencies, when it says it is capable of 96 khz capture?

---

### Post by igorzwx on 2009-06-07
To make things clear try to record from OSS with ffmpeg, or brec, or else.
Then do the same offline
on battery (!!!)
everything on battery

---

### Post by scarf on 2009-06-07
i'll try oss.

i can hear things clearly tho, i don't hear any noise, in either recording.  as kayosiii indicated, the human ear can't hear much past 20k.  however, there is clearly (in my view) something up with the audigy.... either it is faulty somehow, or there is a mixer setting somewhere that is preventing it from fully capturing the analog line.

---

### Post by scarf on 2009-06-08
oss produces a weird looking spectrum also,

[[img]http://img36.imageshack.us/img36/6382/audigyoss.th.png[/img]](http://img36.imageshack.us/img36/6382/audigyoss.png)

what is happening there between 30k-40k?

also, it appears to be levelled off around 47k.

i think i found the problem with ALSA, though.  the kernel module snd-emu10k1 doesn't support 96khz yet, as described on the [emu10k1 module page](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1) (see under "General driver status" "what is not yet supported")

the on-board ATI HDA doesn't get levelled around 47k, and doesn't look strange between 30k-40k.... but i doubt it is a suitable line for high-quality capturing.  for example, the signal to noise ratio probably sucks.  but, i don't have any technical specs for it.....

---

### Post by igorzwx on 2009-06-08
Quote: 
      The Olympus LS-10 Linear PCM Recorder is ideal for any musician or nature enthusiast looking to record audio in the highest possible quality. The recorder is also great for journalists who need to interview and report news on the spot. Folder Messages 5 folders, 200 messages per folder, plus MUSIC folder Speaker 2 16mm round dynamic speakers, 8 ohms, and 200 mW output MIC Jack 3.5mm stereo mini-jack, impedance 2 kohms LINE IN Jack 3.5mm stereo mini-jack, impedance 2 kohms EAR Jack 3.5mm stereo mini-jack, impedance 8 ohms Maximum Headphone Output 3 mW per channel at a load of 16 ohms Batteries 2 AA Alkaline, Lithium, or NiMH batteries

---

### Post by kayosiii on 2009-06-08
Well I am glad I was wrong about the use of filters....

Higher sample rates are still useful for getting better results with some filters - since noise generated by the filters can be shifted outside the audible range for humans.

I have heard of rare individuals who can hear up into the high 20k spectrum but never above 30k most people are 20k or less.

There are studies to suggest that the human brain reacts to higher frequencies, however to really take advantage of this you need microphones specifically designed for this task. For example my most sensitive Microphone can record up 23k... Sounds frequencies significantly above this are not going to factor into my recordings no matter what sample rate I use. It would be interesting to find out what the maximum usable frequencies are on older popular studio microphones.

Anyways if you want to figure out which interface to use. I suggest finding a few people you know have good ears and do a blind (preferably double blind) A,B test and figure out which one sounds better. The amount and type of colouration that the AD Converters add will have a much bigger impact on the sound than what is happening above 30k... (I personally don't like the sound characteristics of the sound blaster cards but YMMV)

---

### Post by v.stiff on 2009-06-08
> **scarf said:**
> oss produces a weird looking spectrum also,

[[img]http://img36.imageshack.us/img36/6382/audigyoss.th.png[/img]](http://img36.imageshack.us/img36/6382/audigyoss.png)

what is happening there between 30k-40k?
This is the evidence for the fact, that ADC is working at 48khz, but then no digital filter is applied (or it is applied above 48khz, since you use 96khz sample rate). Man, relax, encode with audigy and do not care about the spectrum above 20khz anymore :)

If you want better sound quality - you need to use a better card, not more khz. ;)

If you really want to get into this the read about nyquist frequency, digital filter and the ADC at wikipedia.

---

### Post by Darktrax on 2009-06-08
I am lurking your post because I also want to recover and maybe clean up some old vinyl.
So.. It leads to a question.

The high frequency losses involved in using wavy bumps in a vinyl groove, and in recovering the signal with a pickup were somewhat compensated for by using pre-emphasis during recording (boosting the higher frequencies), and then adopting a standardized filter (RIAA equalization) in record deck amplifier playback paths.

Do Audigy cards and applications like Audacity include this correction?
It just occurred to me that not using a RIAA curve equalizer might just possibly contribute to strange spectrums with exaggerated high frequencies.

I don't think most folk can directly hear sounds much above 12 kHz, but the contribution presence of harmonic frequencies up to 20kHz make in altering the waveform character of the lower frequency notes can be heard.

BUT.. I now have the new toy, and I will soon be playing :p

---

### Post by scarf on 2009-06-09
thanks to all who have contributed.  but, i am really not interested in hearing a difference in the recordings.  what i am interested in is digitally reproducing the analog media in the best possible way, using a reasonable budget.  right now, the m-audio 2496 card is looking like a good replacement.

darktrax, i have a pre-amp that takes care of the riaa equalization, and i would also recommend one.  grado produces a top-notch one for the price, but there are certainly less- and more-expensive solutions.

the audigy does not have any riaa equalization that i'm aware of.  audacity does have a riaa equalization filter, though.  however, i would recommend as little software post-processing as possible.  but it's all up to you.

---

### Post by v.stiff on 2009-06-09
> **scarf said:**
> thanks to all who have contributed.  but, i am really not interested in hearing a difference in the recordings.  what i am interested in is digitally reproducing the analog media in the best possible way, using a reasonable budget. right now, the m-audio 2496 card is looking like a good replacement.
Then you should ask people, who do digital recordings of vynil, for example on [http://www.hydrogenaudio.org/forums/](http://www.hydrogenaudio.org/forums/) . I've listened to some recordings done with 2496, sounds pretty good, but heard opinions there cards from e-mu sound better (and bought one)

---

### Post by scarf on 2009-06-09
yes, the e-mu 1212m.  however, this appears to not be fully supported by ALSA yet, so i would stay away.

i am looking at the asus xonar cards, like the d1.

---

### Post by lukeiamyourfather on 2009-06-09
> **scarf said:**
> why would the audigy filter any frequencies, when it says it is capable of 96 khz capture?

That's the sampling rate (how often the card samples the incoming analog audio signal), not related to the audible frequency of the recording. Higher sampling rate means that each "frame" of the sound is not as long. Low sampling rates are useful for things like telephones and heavily compressed recordings.

I would not worry about the motherboard audio chipset picking up more stuff above 20 KHz compared to another audio card because its probably just noise anyway. The human ear can't hear those, and even if they could your speaks can't reproduce that frequency anyway. De facto range of frequencies for recording is 20 Hz to 20 KHz which seems to be covered with either audio chipset. Also most recordings are 44.1 KHz sampling rate so you probably won't get anything more with a 96 KHz sampling rate other than larger files. Cheers!

---


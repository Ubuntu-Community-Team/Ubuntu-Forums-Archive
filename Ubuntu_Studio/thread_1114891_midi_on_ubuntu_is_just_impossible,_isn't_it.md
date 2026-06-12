---
title: "midi on ubuntu is just impossible, isn't it?"
date: 2009-04-03
forum: Ubuntu Studio
---

### Post by adamgram on 2009-04-03
I've been using ubuntu for a while now, but only really at the user level for web browsing and word processing.  I'm no expert for sure.  I still use windows on my desktop because I have a lot of software for recording music on that computer.  I'd like to get into some of the Ubuntu programs for music on my laptop, which has Ubuntu 8.04 on it, but I'm having trouble getting midi to work.

All I really want to be able to do for now is write out music in rosegarden and hear sound when I hit play.  

I downloaded Jack and QSynth, but I'm a little confused as to what exactly these things are supposed to do.  From what I understand Jack is what routes your sounds from various programs to your soundcard?  Am I right about that?  What about QSynth though?  Does this provide sounds from MIDI signals it imports from another program, or should this be able to make sounds by itself?  

I followed a how-to I found here [http://ubuntuforums.org/showthread.php?t=8736](http://ubuntuforums.org/showthread.php?t=8736) and ran into some problems.  I copied and pasted the whole thing below, things with an 'x' beside it worked, and things with a *** beside it are the error messages I got while trying to get it to work.  Any help is appreciated, thanks. 

HOWTO: Getting MIDI to work fully in Ubuntu
MIDI: Getting to Create, Play, Anything with Ubuntu!

Intro
MIDI support has been asked for mostly musically involved people who use Linux, and it hasn't come easily. Most of the HOW-TOs for setting up MIDIs don't even work, and I'd know. So, today, after almost a month of working towards it, I've finally been able to listen, play, and create MIDIs with ease. It's actually not very difficult; you just need the right packages and a loaded GM Soundfont.

Prerequisites
- A MIDI enabled sound card (most people have a SoundBlaster Audigy or Live! card-- if you have onboard sound, meaning the motherboard does the MIDI work, you'll need to use FluidSynth, which I'll talk about later).
*** I have ATI IXP AC97 onboard sound

- A fully working ALSA sound system.
*** ALSA shows up under system--> preferences--> sound and the test sound plays for everything EXCEPT sound capture

- A fully working OSS sound system. (in case the upper doesn't work, you can use this and then do a sudo modprobe snd-seq-oss)
*** OSS shows up under system--> preferences--> sound but I get an error message when I hit the 'test' button:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

- The following ALSA packages installed (get these through apt-get/synaptic/aptitude):
x alsa-base,
libasound,
*** E: Couldn't find package libasound, I do have libasound2
alsa-headers,
***
heather@heather-laptop:~$ sudo apt-get install alsa-headers
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package alsa-headers is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libasound2-dev
E: Package alsa-headers has no installation candidate

x libasound-dev,
alsa-modules-2.4.26-1-686 (replace the 686 with 586, 386, k6, k7, etc. according to your system),
*** E: Couldn't find package alsa-modules-2.4.26-1-686

x alsa-oss,
x alsa-source.

- A program that plays MIDI files. (KMid is a nice one)
*** E: Couldn't find package KMid

x The awesfx package if you are not using FluidSynth. (get this through apt-get)

Blood, Sweat, and Tears time (not really)
You've gotten past most of the work which took me the most time. Some of the packages you install may seem like overkill, but for people who use FluidSynth and have to compile it and other things, those packages are good to have just in case.

Do an lsmod in the terminal. It should return something like this

Quote:
snd_seq_midi 8096 1
snd_emu10k1_synth 6784 4
snd_emux_synth 33408 5 snd_emu10k1_synth
snd_seq_virmidi 7296 1 snd_emux_synth
snd_seq_midi_emul 7680 1 snd_emux_synth
snd_seq_oss 29440 0
snd_seq_midi_event 7552 3 snd_seq_midi,snd_seq_virmidi,snd_seq_oss
snd_seq 46608 19 snd_seq_midi,snd_emux_synth,snd_seq_virmidi,snd_se q_midi_emul,snd_seq_oss,snd_seq_midi_event
nls_iso8859_1 4352 2
nls_cp437 6016 2
vfat 13312 2
fat 41792 1 vfat
i830 68644 6
proc_intf 3968 0
freq_table 4356 0
cpufreq_userspace 5336 0
cpufreq_powersave 2048 0
button 6936 0
ac 5132 0
battery 9740 0
ipv6 230020 8
af_packet 20872 2
8139too 23936 0
8139cp 19072 0
mii 4864 2 8139too,8139cp
crc32 4608 2 8139too,8139cp
emu10k1_gp 3840 0
gameport 4736 1 emu10k1_gp
snd_emu10k1 80776 11 snd_emu10k1_synth
snd_rawmidi 23232 3 snd_seq_midi,snd_seq_virmidi,snd_emu10k1
snd_pcm_oss 48168 0
snd_mixer_oss 16640 3 snd_pcm_oss
snd_pcm 85540 3 snd_emu10k1,snd_pcm_oss
snd_timer 23172 2 snd_seq,snd_pcm
snd_seq_device 7944 7 snd_seq_midi,snd_emu10k1_synth,snd_emux_synth,snd_ seq_oss,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec 59268 1 snd_emu10k1
snd_page_alloc 11144 2 snd_emu10k1,snd_pcm
snd_util_mem 4608 2 snd_emux_synth,snd_emu10k1
snd_hwdep 9120 2 snd_emux_synth,snd_emu10k1
snd 50660 27 snd_seq_midi,snd_emux_synth,snd_seq_virmidi,snd_se q_oss,snd_seq_midi_event,snd_seq,snd_emu10k1,snd_r awmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer ,snd_seq_device,snd_ac97_codec,snd_util_mem,snd_hw dep
soundcore 9824 3 snd
pci_hotplug 30640 0
ehci_hcd 27780 0
uhci_hcd 29328 0
usbcore 104292 4 ehci_hcd,uhci_hcd
intel_agp 20512 1
agpgart 31784 3 intel_agp
pcspkr 3816 0
rtc 12216 0
floppy 54996 0
md 44744 0
dm_mod 51068 1
capability 4872 0
commoncap 7168 1 capability
parport_pc 32064 1
lp 10436 0
parport 37320 2 parport_pc,lp
tsdev 7168 0
ide_cd 38276 0
cdrom 35872 1 ide_cd
evdev 9088 0
mousedev 10124 1
psmouse 17800 0
ext3 109544 1
jbd 54552 1 ext3
ide_generic 1664 0
piix 12576 1
ide_disk 16768 5
ide_core 125272 4 ide_cd,ide_generic,piix,ide_disk
unix 25904 762
fan 4236 0
thermal 13200 0
processor 17712 1 thermal
font 8576 0
vesafb 6688 0
cfbcopyarea 3968 1 vesafb
cfbimgblt 3200 1 vesafb
cfbfillrect 3712 1 vesafb
If you don't see any MIDI related modules (the important ones are
x snd_seq_midi,
snd_emu10k1_synth,
*** E: Couldn't find package snd_emu10k1_synth
snd_emux_synth,
*** E: Couldn't find package snd_emux_synth
x snd_ seq_oss,
x snd_seq,
snd_emu10k1,
*** E: Couldn't find package snd_emu10k1

x snd_rawmidi
),
then that means ALSA hasn't been configured properly. Try sudo modprobe for these modules, and see what results.

Now, that you have MIDI devices working, go over to [http://www.hammersound.net](http://www.hammersound.net), go to Sounds -> Soundfont Library -> Collections (this is over at the bottom). Now, find a GM library which you think will sound good, etc. I am using the Ultimate GM/GS Soundfont collection, which can be downloaded through [http://www.hammersound.net/cgi-bin/s...d=Ultimate.zip](http://www.hammersound.net/cgi-bin/s...d=Ultimate.zip)

Now, download it to your home directory. This one should be in a ZIP file (note: if it is in sfArk form, continue reading), so simply unzip it and there should be a sf2 file inside it. Go to the terminal and do a sfxload thenameofthefile.sf2. It should return to a new $ line, and that is good. Go into KMid and open up a MIDI and it should work. You can use Rosegarden 4 (apt-get install rosegarden4) to create MIDIs with ease and a bit of musical knowledge.

FLUIDSYNTH
FluidSynth is a software synthesizer, meaning there is no hardware involved since your card doesn't support SoundFont synthesis (otherwise, you shouldn't be doing this, hehe). It obviously doesn't relay as much quality as hardware does, but that's a small price to pay. You can find their homepage at [http://www.fluidsynth.org/](http://www.fluidsynth.org/).

It can also be easily installed through apt-get. Once it is installed, open up your terminal and do this: fluidsynth -m alsa_seq ./thenameofthefilehere.sf2. This will load the soundfont into your computer's memory.

Now, that wasn't difficult was it? Open up whatever MIDI program and you should be able to listen to your MIDIs.

SFARK
sfArk is a common compression method composers use to zip up their SoundFonts, and luckily, the company behind it has a Linux version of their utility. Download it at [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). It is a command-line based utility, but again, easy to use. Just do this: sfarkxtc ./thenameofthefilehere.sfArk

That should decompress the sfArk and give you a .sf2 file. If it gives you any other kind (such as an EXE), that means you'll have to move onto another soundfont since this one won't be usable.

CONCLUSION
This hasn't been 100% tested, but it worked just fine for me and I hope it does for you as well. Post all of your errors, suggestions, comments, and I'll be happy to edit them into this. May your musical talent flourish with Ubuntu
Last edited by Quest-Master; December 20th, 2004 at 02:41 PM..

---

### Post by saunders on 2009-04-06
I've been playing with MIDI on and off for the past few weeks. It's quite frustrating at first but I'm actually getting the hang of it. I've just reached the point where I'm recording MIDI output from Rosegarden into Ardour.

Unfortunately I'm not at my Ubuntu box now so most of this is from memory...hopefully there're enough pointers to get you started.

Yes, you need to start by installing Jack control. Always fire this up first. You're right, it's an audio server which routes sounds through programs and soundcards. You may need to alter the latency if you begin having problems with xruns/clipping audio etc. This can be done through Jack, there are several tutorials in the Forums. You may also want to install the -rt kernel (which is realtime, and optimised for audio production). You can select it at the Grub menu when you boot. It's available through synaptic.

If you just want a basic synth, try installing Zynaddsubfx. You can play this from your computer keyboard. It has a bank of sounds, or an advanced mode if you want to create your own.

So, fire up Jack-control, zynaddsubfx and rosegarden. Jack *should* connect both up. You can check by clicking on the connection button in Jack, and looking there. You may also want to check the system outputs in there too, to make sure they're ok.

In rosegarden, use the pencil tool to draw a number of bars you want to step-program your notes into. In the top right of Rosegarden there'll be a button saying "Manage MIDI connections". There'll be a number of pulldown menus on this screen. Change the General MIDI device to Zynaddsubfx. Close this screen, and right click on the bars you drew in. Select "matrix editor 'M'". You'll now see a keyboard and a grid. You can fill in the notes and durations here. Clicking on the keyboard should produce whatever sound you have dialled up in Zynaddsubfx. Once you've programmed the melody, you should be able to hear it by clicking play.

Qsynth acts similarly to zynaddsubfx in this example. It provides a bank of sounds that Rosegarden can use to play the notes. If you use Qsynth, you'll need to alter the MIDI connection in Rosegarden. On my setup, it doesn't come up as Qsynth, instead it's "130:0" or something similar. Your mileage may vary.

Hope this is of some help!

ps. You may want to look into installing the ubuntu studio packages from the repositories, especially the audio one. It should install all the stuff you need.

---

### Post by 0per4t0r on 2009-04-06
Try downloading VLC Media Player. It works with midi.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by Monona on 2009-04-07
While I don't know how to troubleshoot your specific issues, I found this tutorial to be really helpful:

[https://help.ubuntu.com/community/HowToSeq24Introduction](https://help.ubuntu.com/community/HowToSeq24Introduction)

This tells you how to use JACK to link up Seq24 (sequencer), Hydrogen (drum machine), and zynaddsubfx (software synthesizer) to drive Hydrogen and zynaddsubfx with Seq24's midi output.  I'm new to midi, and I had no trouble getting it working.

---

### Post by Califord2008 on 2009-04-07
Delay with midi sounds Multimedia & Video. ... But when vmpk or 
tuxguitar is trying to play a note, there's always a slight delay, 0.5-1 sec, 
which isn't very nice. .... EDIT: This maybe linked to something else, because I 
just noticed ... For Banshee there's almost impossible to hear it, ...

---

### Post by kayosiii on 2009-04-10
ok first of all...
1) Get jack up and running - this is needed for rosegarden's audio support.
2) Rosegarden supports dssi synths this is the easiest way to get sound out or rosegarden. First search for dssi in your package management program (eg synaptic). One I can think of off the top of my head is called Hexter. Start Rosegarden
Right click next the track where it says untitled and select Synth Plugin from the list... The bottom section of the left hand panel will change you can select your synth here, it's parameters and even add effects to it from this panel.
3) Should you want to work with an external synthesizer then you can do so with general midi (the default setting). You should install an application called patchage - this application gives you easy control over all your midi and jackaudio connections. Zynaddsubfx is not a bad external Synth to start with just drag from rosegardens general midi out port (midi ports are green)  Zynaddsubfx's midi in port (if there is not already a line connecting the two)...
4) qsynth is a synthesizer that plays Soundfont 2 files... Without one of these it does precisely nothing. There should be some of these floating around the web.

The howto you are looking at is more for connecting physical hardware (like a keyboard) into linux... so don't worry about it for the moment. 

Hope that helps

---

### Post by bcschmerker on 2010-02-20
I have a variation on this problem:  At present, I have no hardware synthesizer on my Creative Laboratories® SB0350 (CA0102 chipset, uses E-mu 10K1/10K2 drivers)---no response to an external Windows box with [Cakewalk®/Roland® Music Connector]("http://www.cakewalk.com/") feeding the MIDI IN at an Audigy 2 Drive, despite running the JACK daemon and patchbay application.  No plans to retrofit an E-mu® 20K2-based audio card due to lack of communication between the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) and Creative Technology Ltd., a prerequisite for either the [Creative Laboratories® X-Fi® Titanium Fatality Professional](http://us.store.creative.com/) or [Auzen® X-Fi® Home Theatre 7.1](http://www.auzentech.com/).  What need I look at in terms of getting the hardware synth up?

---

### Post by AutoStatic on 2010-02-21
Get yourself a USB midi interface. Those devices are cheap and the majority works out of the box.
And doesn't the SB0305 have MIDI out?

---

### Post by bcschmerker on 2010-02-21
In fact, I attempted to feed a MIDIfile on the Everex, via the Audigy 2 Drive's MIDI Out, to the Windows box via the Cakewalk/Roland Music Connector and I had no transmission---not even flashes on the Music Connector to indicate a functional MIDI out on the Audigy 2 Drive.  JACK doesn't detect the no-send condition.  What need I look at in order to get MIDI up on the SB0350?

---

### Post by AutoStatic on 2010-02-22
Could you post the outcome of **amidi -l** ?
And a screenshot of the ALSA tab of the QjackCtl Connections window?

---

### Post by bcschmerker on 2010-02-22
> **AutoStatic said:**
> Could you post the outcome of **amidi -l** ?
And a screenshot of the ALSA tab of the QjackCtl Connections window?The following StdOut came up for amidi -l:
```
Dir Device    Name
IO  hw:2,0    Audigy MPU-401 (UART)
IO  hw:2,1    Audigy MPU-401 #2
IO  hw:2,2    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:2,3    Emu10k1 Synth MIDI (16 subdevices)

```And JACKd has the following Devices available for QJackCtl, from the Connections page (no software package for PNG'ing a Print Screen on my system as of this post):
```
[AUDIO]
Outputs, System
-Capture1
-Capture2
Inputs, System
-Playback1
-Playback2
[MIDI]
Outputs, MIDI
-Audigy-2-ZS--SB0350-/midi_capture_1
-Audigy-2-ZS--SB0350-/midi_capture_33
-Midi-Through/midi_capture_1
Inputs, MIDI
-Audigy-2-ZS--SB0350-/midi_playback_1
-Audigy-2-ZS--SB0350-/midi_playback_33
-Emu10K1-WaveTable/midi-playback-1
-Emu10K1-WaveTable/midi-playback-2
-Emu10K1-WaveTable/midi-playback-3
-Emu10K1-WaveTable/midi-playback-4-
-Midi-Through/midi-playback-1.
[ALSA]
Outputs, ALSA
-14:Midi-Through
--0-Midi Through Port-0
-24:Audigy 2 ZS [SB0350]
--0-Audigy MPU401 [UART]
--32-Audigy MPU401 #2
Inuts, ALSA
-14:Midi-Through
--0-Midi Through Port-0
-24:Audigy 2 ZS [SB0350]
--0:Audigy MPU401 [UART]
--32:Audigy MPU401 #2
-25:Emu10K1 WaveTable
--0:Emu10K1 Port0
--1:Emu10K1 Port1
--2:Emu10K1 Port2
--3:Emu10K1 Port3

```

---

### Post by AutoStatic on 2010-02-23
Thanks! There are MIDI ports available. What is it that you're trying to do exactly? Do you want to send MIDI out from the Ubuntu PC? From which application? Or do you want to receive MIDI on the Ubuntu PC? For which application?

---

### Post by bcschmerker on 2010-02-23
On my Everex, I am attempting to get the SB0350's hardware synthesizer and Audigy 2 Drive to the point where they will receive and execute incoming MIDI commands from an external system; I am using some project arrangements in [Cakewalk/Roland Music Creator 5.0 and Music Connector](http://www.cakewalk.com/) on a known functional [eMachines/Acer EL1210-09](http://www.emachines.com/) (running Microsoft Windows 6.0.6001) for the purpose.  To date, the hardware synth on the SB0350 has been silent with both local and remote sequencers.

For starters, what is needed to get the hardware synth up?

---

### Post by bcschmerker on 2010-03-09
> **bcschmerker said:**
> On my Everex, I am attempting to get the SB0350's hardware synthesizer and Audigy 2 Drive to the point where they will receive and execute incoming MIDI commands from an external system; I am using some project arrangements in [Cakewalk/Roland Music Creator 5.0 and Music Connector](http://www.cakewalk.com/) on a known functional [eMachines/Acer EL1210-09](http://www.emachines.com/) (running Microsoft Windows 6.0.6001) for the purpose.  To date, the hardware synth on the SB0350 has been silent with both local and remote sequencers....
Update:  I found a hardware Bug referred to at ALSA-Project.org for the Creative Laboratories Audigy 2 Drive:
[QUOTE=]There is an issue with the Audigy 2 Platinum Ex soundcard and the Audigy 4 pro (and probably some other Audigy 2 cards as well), whereas the IR sensor, MIDI and the buttons on the LiveDrive do NOT work at all until the LiveDrive is initialized by sending the sequence of '0xf0, 0x00, 0x20, 0x21, 0x61, 0x0, 0x00, 0x00, 0x7f, 0x0, 0xf7' to the MIDI port. Before doing this, even the LED on the LiveDrive won't blink, as it usually does when a button on the remote is pressed. As far as I know, this behaviour is different than with most LiveDrives manufactured by Creative.

Retrieved from [/Main/Index.php/Matrix:Module-emu10k1](http://alsa-project.org/main/index.php/Matrix:Module-emu10k1) at ALSA-Project.org 09 March 2010.[/quote]The official ALSA wiki uses /dev/snd/midiC0D1; on my Everex, that probably translates to /dev/snd/midiC2D1, given the following return from ls /dev/snd:
```
controlC0
controlC1
controlC2
hwC0D0
hwC2D0
hwC2D2
midiC2D0
midiC2D1
midiC2D2
midiC2D3
pcmC0D3p
pcmC1D0c
pcmC2D0c
pcmC2D0p
pcmC2D1c
pcmC2D2c
pcmC2D2p
pcmC2D3p
pcmC2D4c
pcmC2D4p
seq
timer
```

---

### Post by AutoStatic on 2010-03-09
Hello bcschmerker, can't help you on getting the hardware synth going, I have no experience with that, neither with Audigy cards. So maybe someone else could be of assistance.

---

### Post by stew2222 on 2010-03-17
> **AutoStatic said:**
> Get yourself a USB midi interface. Those devices are cheap and the majority works out of the box.


Yep, thats what I would recommend too (I'm using an Edirol UM-1 USB interface if you decide to have a try with a usb one).  Muse was able to play through it with no problems, and no setup by me

---


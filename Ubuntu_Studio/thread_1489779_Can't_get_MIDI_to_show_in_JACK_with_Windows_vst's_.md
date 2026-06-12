---
title: "Can't get MIDI to show in JACK with Windows vst's via fst"
date: 2010-05-21
forum: Ubuntu Studio
---

### Post by indstr on 2010-05-21
Any help would be appreciated. I am running Xubuntu studio 9.10. Have JACK & fst installed. I am wanting to run some windows vst's through fst. Currently I have a vsti called addictive drums running just fine, including MIDI input which shows up in JACK. I am able to route MIDI to it and trigger it just fine. 
 
But I also need to run some vst's, including a drum triggering program. I get the program to work in fst (KTdrumtrigger), but no MIDI outputs show up in the JACK connections, patchage, or the JP1 control panel. (I also have a2jmidid installed). So I also tried running several Windows hosts in Wine - including Renoise and EnergyXT (Running Wineasio), and they are not having any MIDI in/out showing up in JACK... And of course in their setup menus, there are no options to select for MIDI.
 
I made sure I selected "seq" in the MIDI driver in qjackctl.. (Even tried raw).
 
Seems like it must be something obvious... Is there something special I need to do to get MIDI working properly with Wine? (But the weird thing is, Addictive drums has MIDI inputs just fine)
 
Any help would be appreciated.
 
Thanks

---

### Post by sgx on 2010-05-21
Hi, first, I always choose 'none' in qjackctl, and .dlls started with fst do show correctly in qjackctl. Truly counter-intuitive, the linux way :) 

Second, Reaper is by far the easiest and best wineasio vst solution in linux, a 4.5 meg download, updated often, easy to maintain etc. A how-to is in another recent topic started by beowulf.

I like linux hydrogen for creating unique percussions, rather than windows apps, but for using canned beats, or midi drum parts, EZ Drummer and Addictive drums are both excellent.

Cheers

---

### Post by psidrum on 2010-05-21
hi, you dont have to connect to anything, it should automatically read it

then all you have to do is go to your windows VST or Host and set your midi,

and then for each instrument, set a Channel for it, so whenever you need to use an instrument, you need to use your midi to switch the channel

to control a Windows VST using a sequencer like Seq24 you need to use Midi Through for both software then again use channel to switch to different instruments

this is how i run mine, the MIDI inputs dont show up in Jack but they still work using WineAsio, 

i dont use FST, i just run the standalone, 

or you can use VSThost

[IMG]http://img339.imageshack.us/img339/3798/snapshotmidi.png[/IMG]

---

### Post by indstr on 2010-05-23
I downloaded Reaper. It looks like a nice little program to use as a host... However, it has the same problems that Renoise and EnergyXT had....  No midi is showing up in the config menus (and of course no plugs show up in JACK)

Here is what I am wanting to do:

Use several instances of KTdrumtrigger to send MIDI messages to Addictive drums (I have piezo pickups connected to drum pads so I need to trigger addictive drums with them). So I need to get the MIDI out of Ktdrumtrigger somehow

Interestingly, I did notice that Reaper has its own drum trigger plugin. So I guess if I could get Addictive drums working inside it as a vsti, then it could all work internally with no MIDI routing required. Which would work fine for now... Although it would be nice to get the MIDI routing working eventually.

Here is a screenshot of what is currently going on :

[IMG]http://www.loopproject.com/filebase/sdcompo/organic_io/nomidi.jpg[/IMG]

So...  Anyway. I will keep messing with it, and either see if I can get addictive drums working inside Reaper (and fast enough), or use a different Linux host like JOST or Rosegarden and run ktdrumtrigger via the DSSI-vst route and see if **that** works with MIDI.

Edit: I did try using Reaper's built in trigger --> MIDI plugin set to MIDI channel 10 , with Addictive Drums open, but it didn't receive anything. Addictive Drums doesn't have any settings to listen on a certain channel as far as I know. I think it needs to be plugged straight in. Anyway..

We'll see what happens. Thanks for the help so far

---

### Post by sgx on 2010-05-23
Hi, run the lsmod and lspci commands and post the output.

below are two lines from my lsmod, you'll hope to see similar

snd_mpu401_uart         9856  1 snd_your-soundcard-kernel-module
snd_rawmidi            25632  1 snd_mpu401_uart
snd_seq

cheers

You may just have kernel modules that are not yet loaded, and the
modprobe command can do that

modprobe snd-your-sound-chip
modprobe snd_seq_midi
modprobe snd_rawmidi
modprobe snd_seq_midi_event
modprobe snd_seq

---

### Post by indstr on 2010-05-23
Just wasted 2 hours messing about with lots of various programs, with no success.

I did notice one thing though... One of the plugins I tried to load through DSSI_VST gave me an error when I tried to assign MIDI out of it through the Wine MIDI wrapper... It said there was an error with the MIDIMAP.CFG and to copy the original into the Windows/system directory. I downloaded one online and put it in Wine's windows/system and system32 directories, but it didn't seem to help anything.

Alas

---

### Post by sgx on 2010-05-23
> **indstr said:**
> Just wasted 2 hours messing about with lots of various programs, with no success.

I did notice one thing though... One of the plugins I tried to load through DSSI_VST gave me an error when I tried to assign MIDI out of it through the Wine MIDI wrapper... It said there was an error with the MIDIMAP.CFG and to copy the original into the Windows/system directory. I downloaded one online and put it in Wine's windows/system and system32 directories, but it didn't seem to help anything.

Alas
You MUST have midi kernel modules, or you waste your efforts configuring phantoms. 

lsmod lists the modules
lspci list your hardware, needed to help identify the needed
kernel modules. :)

---

### Post by indstr on 2010-05-24
After another hour and a half last night, I got it figured out! I realized that in my winecfg, I only had JACK selected as the sound driver (to try to decrease latency)... Which I noticed didn't have any options for MIDI. When I selected ALSA and OSS, the ports are now showing up in the vst hosts, and I am able to route it to Addictive Drums. (Although the vst host still doesn't show in the JACK panel as someone said above)
 
And there's no latency! Go Linux!
 
sgx, thanks for the tips. I'll run lsmod and lspci tonight just out of curiosity.
 
:)

---

### Post by indstr on 2010-05-24
Yeh, I had all the stuff I needed listed in lsmod... It was all about the drivers selection in winecfg.

---

### Post by sgx on 2010-05-25
> **indstr said:**
> Yeh, I had all the stuff I needed listed in lsmod... It was all about the drivers selection in winecfg.
I'm curious what appears in your qjackctl, I have midiport icons
from my soundcard in the alsa tab, and when I start a vst,

fst occam.dll

the name occam appears by a new midi icon.

In the Audio tab, occam also appears on the left side of
the pane, above the system icon.

When I start Reaper, Asio_Reaper appears with icons in both sides
of the audio tab, both sides automatically connected.

Cheers

---

### Post by indstr on 2010-05-25
> **sgx said:**
> I'm curious what appears in your qjackctl, I have midiport icons
from my soundcard in the alsa tab, and when I start a vst,
 
fst occam.dll
 
the name occam appears by a new midi icon.
 
In the Audio tab, occam also appears on the left side of
the pane, above the system icon.
 
When I start Reaper, Asio_Reaper appears with icons in both sides
of the audio tab, both sides automatically connected.
 
Cheers
 
It's strange... Some things show up, and some things don't. Addictive drums through fst shows up in the audio tab with inputs and outputs. It shows up in the ALSA tab with MIDI inputs (but no outputs.. I am not sure if it has MIDI out support anyway). But if I start, for example, ktdrumtrigger through fst, it has stuff in the audio tab, but not the ALSA. If I start a Windows host with wineasio (Whether it is Renoise, Reaper, or EnergyXT), it does not show up in qjackctrl connections at all under audio or ALSA... But it still works.
 
Not the most elegant solution, it would be nice to figure out how to get them to all show up in qjackctrl or some kind of patchbay, but as long as it works I won't complain too much   :)

---

### Post by sgx on 2010-05-25
In case you missed it, a nice chap posts anew AD preset each week, available at his blog for just that week, this is week 13. Scroll down
a bit to the preset

[http://thebuddharats.wordpress.com/](http://thebuddharats.wordpress.com/)

There are many oddities around qjackctl. Just last night, I had a terminal window opened by Reaper and qjackctl, and noticed that when the mouse went over the terminal, the reaper connector lines in qjackctl
vanished, and re-appeared as the mouse left the terminal. I think  this
is an xorg vs Qt vs wine issue, but its weird. :)

---


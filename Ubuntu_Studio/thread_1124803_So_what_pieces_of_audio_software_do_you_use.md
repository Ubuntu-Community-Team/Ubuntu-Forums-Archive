---
title: "So: what pieces of audio software do you use?"
date: 2009-04-13
forum: Ubuntu Studio
---

### Post by bolex100 on 2009-04-13
And what do you use them for?

---

### Post by kayosiii on 2009-04-14
My most recent experiment involved

Rosegarden(midi)--->ZynaddsubFX(synth)--->Rakarrack(fx)--->Ardour(DAW)
                                                        /
                                                     Hydrogen (Drum Machine)

I also use Freewheeling a lot...

---

### Post by bolex100 on 2009-04-14
how do you integrate Hydrogen with Ardour?  In windows I use FL studio as a VSTi within cubase.  I'd like to use something like that as a writing tool.
i.e. start with a beat, feed it into Ardour, record something over the top, and be free to change the beat.
OR/
Start with a sampled beat and recreate it in a drum package.

---

### Post by thorgal on 2009-04-14
hydrogen provides jack output ports. Instead of being a plugin, it is a "parallel" app that is visible in the jack graph. So you connect ardour's track input ports to hydrogen's output ports (either master ports or track ports, that's something you can set up in hydrogen). Then, to run them in in sync and control the transport from one app or the other (or from qjackctl's transport buttons), you switch both hydrogen and ardour to jack transport slave mode. You can find find the switch button on both apps main window. Chances are ardour is using "internal" by default. Same for hydrogen. Then you can decide if ardour should be the time master (another big button). If so, you can add tempo and time signature markers along the time line in ardour, and hydrogen will respond to them (at least version 0.9.4beta, not sure about 0.9.3).
Only thing is : tempo ramping is not in the menu. For that, you should switch to rosegarden, set up a tempo map with ramping up and down if you wish and let rosegarden be the time master.

---

### Post by bolex100 on 2009-04-15
I can't make Hydrogen share the same tempo as Ardour.  I set Ardour to use Jack as the time master, but I can't find the same control on Hydrogen.

---

### Post by thorgal on 2009-04-15
which version of HG do you have ?

Look at this screenshot: [http://hydrogen-music.org/images/screenshots/hydrogen-0.9.2.png](http://hydrogen-music.org/images/screenshots/hydrogen-0.9.2.png)
in the bottom, main transport bar, you have a button to make HG a jack transport slave (right end of the bar).

you can also find lots of tips from Brian's bedroom blog :
[http://briansbedroom.org](http://briansbedroom.org)

but to have HG align with another time master, you have to get version 0.9.4

---

### Post by bolex100 on 2009-04-15
The vertion of Hydrogen that comes with Ubuntustudio is 9.3.  I supose that 9.4 will be on the next release of Ubuntustudio.  Its only a few days away so I'll wait.
Its a shame.  I'm just off to a writing session.  These are the basic tools I'd like to have.  The studio is literally across the road from Digital Village.  Its tempting to just rebuild a vista/cubase machine ...... at the same time as subscribing to Ardour.

Meanwhile the thread question still stands:-  

**Anyone else using this stuff?**

---

### Post by thorgal on 2009-04-15
oh yeah, so you wanted to know what sofwares ppl use:

System:
-------
- debian sid + customized system config
- kernel 2.6.29-rt1 (will upgrade to 2.6.29.1-rt7) heavily customized for my needs (h/w and system "tuning", I've only been using home-compiled kernels since I built up my linux DAW)
- openbox + KDE integration for windows manager
- jack2 (aka jackmp) compiled myself, latest svn version

Audio Apps
----------
- for ALL my recordings, mixing, etc: ardour latest 2.8 svn code, compiled myself
- jamin for mastering: CVS version compiled myself
- for my MIDI sequencing : rosegarden 1.7.3 (compiled myself as well, will switch to the QT4 port when it is ready)
- wine 1.1.18 fetched from winehq.org for my VSTis
- dssi-vst (v0.8 compiled from source), fst (latest git code compiled from source) or savihost.exe (win32 app that runs in wine) for VST hosts
- wineasio for win32 standalone apps (svn trunk version compiled myself against wine-dev 1.1.18 ).
- VSTi Addictive Drums by XLN Audio for my drumming (bought a user licence, installed from DVD and upgraded from online updates). I sequence it in rosegarden, sync'ed with ardour and all this plays really nicely along. never had a crash with AD, a really well designed app in many ways
- Pianoteq 3.0 for my piano playing, another extremely well designed windows app that performs really good at ALL latencies (went down to sub millisec, no glitch!). Bought a user licence, and have excellent customer support (talking with dev about bringing a linux version to life!)  

- some LADSPA plugins but only when needed (some band pass filters, parametric EQ, SC4 compressor, GVerb for weird reverb effects). But I tend to minimize their use whenever I can.

---

### Post by bolex100 on 2009-04-15
What is the best WAV file editor (if its not Audacity)?

---

### Post by thorgal on 2009-04-15
best wave file editor ?
don't know, I guess it's up to your being able to handle the tool ?
audacity is not bad, it's kinda simple to use. I only used it for a few editing tasks on single wave files, not at all for multitracking, even less for recording anything. Since it plays back fine along jack, that's all I needed it for, I have no need to connect it to anything jack except my speakers when it plays back, so I avoid all possible headaches with this app :lol:

---

### Post by kayosiii on 2009-04-17
Audacity works best for doing surgery on damaged waveforms and things you where you want to actually change the waveform permanently... I have lately been using the repair function a lot and the level function is quite handy too.

---

### Post by Stochastic on 2009-04-17
I really like rezound as a wave editor.
SND is very powerful for pro users.

---

### Post by triplesquarednine on 2009-07-14
in linux, i pretty much use the same stuff i use in OSX, or 
that i would use in windows (but i don't windows)...

i use *Native Instruments :

*FM8 - fm synthesis 
*Battery3 - best drummachine
*Massive - wicked synth

all using *wine and *wineasio thru *jack 1.9.3 (compiled myself).

i control them using....

 *Seq24 - Akai MPC-style midi sequencer, and also use
and external midi keyboard....i run multiple instances of each plugin, some for live play, some for sequences.

*Patchage and *Ingen - for patching...

*LinuxDSP(mainly compressers but also JP1 - to save my routings, i prefer patchage's GUI but saving setups is better in JP1), 

*LV2/*Zynjacku

i route whatever plugin(s) that i am playing on the keyboard
throoouuuugh....! 

*sooperlooper 1.6.13 - an "alien-ated" RPM from SUSE - compiling src - myself kept producing errors and the end result was a buggy, half functioning version. and the version in the ubuntu repo is outdated - but the RPM works great.
----i can do livelooping of synths and sampling - pure awesomeness!!!

i sync them all using midi and jack...

and they work glitch free, although sooperlooper can sound a bit grainy at times(but that is the nature of pitch-shifting/time-stretching/adjusting loop speeds in realtime...
(when i use those parameters)

this is all geared for interactive live performance...not unlike ableton live, but i didn't enjoy using ableton at all. however, i really like using my linux setup for the same purpose. better GUI, and i use to own an MPC2000. ableton is too cluttered my liking!

when i record, naturally i use *Ardour(3.0) - no vst support, as i run standalone apps
that use wineasio(they run way better then the VST versions). and VST is buggy in ardour....

***I also am currently beta-testing and using *Glitch-sequencer(google it). it uses cellular automation and can do some neat things, especially when plugged into a drum machine. i can't use it with my live setup, as there are some issues with alsa's virmidi, the fact it uses the "java-midibus" library? and while "user" may only use 20% of my CPU, the "System" sky rockets to 99% and it is only good for sampling purposes at this point.(in osx i can use it though).

it needs to be tested by people in linux, it was written using "processing"(processing.org) in winxp...it works great in both OS's, just not Linux yet. i am one of 2 people
beta-testing it(lasttime i chatted with the developer anyway!)

and that's it. my linux audio experience!

cheers!

---

### Post by dawiba on 2009-07-15
When I record it's mainly just guitar/bass, so for audio, I just stick with Ardour. I also mainly just use the LADSPA plugins that came pre-installed with UbuntuStudio. Since it's just me messing around at home, this is more than good enough. I tried the linuxDSP plugins and intend to come back to them.

For drums and keyboards, things are slightly different. On my Mac, I normally play/build up drum and percussion parts on my keyboard and record these as midi events. This is the same (although to a lesser extent) for keyboard parts. I haven't found a way of doing this that I like to use on UbuntuStudio yet, so I'm tending to use loops for drums and tend to record keyboards directly into Ardour nowadays (at least my keyboard playing will (slowly) improve :)). I'm going to take a look at Open Octave for midi as this looks like something I'll enjoy using.

I don't use vst's, preferring just to use sounds directly from my keyboard and generally just try to find a few things that I like and that work for me and stick to them, so my list of software that I use is probably pretty boring compared to some others :oops:

As a small aside, if I can find a midi app that I like, or when Ardour has midi (and this is available through UbuntuStudio), then the Mac will be retired and I will make the switch with a new computer running UbuntuStudio.

---

### Post by Vigh on 2009-11-01
wine
ableton live 8
audacity
NI massive
NI battery 3
arturia moog modular
NI pro-53
NI absynth
NI Guitar Rig
JACK
patchage
horgand
NI B4 II
D-lusion RD
NI FM8
hexter
LMMS
rosegarden
ardour
JAMMIN
ZynADDSUBFX Synth
AMSynth
Mixxx
DJ Play

you really get the best of both worlds with ubuntu and wine, free synths plus your good ole windows apps

---

### Post by AutoStatic on 2009-11-01
For the moment I use GNU/Linux and FOSS only, haven't touched wine for a long, long time. I think it's a big and rewarding challenge.
The software I use:
- Qtractor for recording. Somehow I haven't managed to install and try Ardour yet, I fear that it's too complicated for me ;)
- LMMS for beats and basslines.
- ZynAddSubFX and CALF Organ. I also like to pipe Aeolus through LADSPA effects like overdrives or compressors. Sounds huge.
- Audacity for editing. How's 1.3.9 BTW? JACK support with 1.3.7 is really buggy, they should ditch PortAudio.
- Rackarrak and Guitarix for the guitar parts, though I prefer to record them with a mic'ed amp and if it's getting late I sometimes use a Line6 Pocket Pod.

In the future I hope to unravel JAMin's mysteries and get my band to switch to FOSS too so we can use Ardour in our rehearsal space.

---

### Post by fedexnman on 2009-11-01
im mainly using ardour and the plugins that show up in the ardour plugins menu..  reverb,eq,compression/limiting.  one day im gonna try to learn hydrogen n sync the 2apps.

---

### Post by danflash on 2010-03-14
Reaper (through WINE)
Ardour
EnergyXT2 (bought a license since it's native to Linux)
Audacity
Baudline
Renoise (hardly ever, only demo-mode for farting about)
LASH
MuseScore
NoteEdit
LinuxDSP
Jamin (sometimes)
MDA Plugins
Zynaddsubfx
Qsynth
Hydrogen 


Maybe missed some out, but you get the jist.
On the to-do list - guitarix.

---

### Post by kazakore on 2010-03-14
Renoise!

Not free though, but fully cross-platform and well supported.

Have to admit I haven't had a chance to try and see what of the Linux bits work for me. What I do know is I have tried many free wave editors in the past and never managed to find one i really like so may well continue using my copy of SoundForce (budget version) through Wine (if I can get it to work.)

---

### Post by KoRnholio on 2010-03-15
> **AutoStatic said:**
> For the moment I use GNU/Linux and FOSS only, haven't touched wine for a long, long time. I think it's a big and rewarding challenge.
The software I use:
- Qtractor for recording. Somehow I haven't managed to install and try Ardour yet, I fear that it's too complicated for me ;)
- LMMS for beats and basslines.
- ZynAddSubFX and CALF Organ. I also like to pipe Aeolus through LADSPA effects like overdrives or compressors. Sounds huge.
- Audacity for editing. How's 1.3.9 BTW? JACK support with 1.3.7 is really buggy, they should ditch PortAudio.
- Rackarrak and Guitarix for the guitar parts, though I prefer to record them with a mic'ed amp and if it's getting late I sometimes use a Line6 Pocket Pod.

In the future I hope to unravel JAMin's mysteries and get my band to switch to FOSS too so we can use Ardour in our rehearsal space.

Ardour isn't actually complicated at all. Maybe its just me, but Ardour's interface 'clicked' for me immediately, while I thought QTractor was kind of clunky.

---

### Post by AutoStatic on 2010-03-15
I have to try it out one of these days. I just like Qtractor, it works perfectly for me, also because I work a lot with MIDI.

---


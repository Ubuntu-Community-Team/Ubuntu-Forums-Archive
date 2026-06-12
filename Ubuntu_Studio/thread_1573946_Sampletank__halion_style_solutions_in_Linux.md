---
title: "Sampletank  halion style solutions in Linux"
date: 2010-09-13
forum: Ubuntu Studio
---

### Post by noodletaboo on 2010-09-13
Hi,

I´m a sampletank/philarmonic user very satisfied migrating to Linux and I would like to know which are the options with sample libraries presets in Linux. 

Basically I want pro sample sounds to use as presets as virtual instruments...or something approximated =)

Thanks for any help!

ps: In case there´s nothing similar. I would appreciate oppinions about how to use Vsts in Linux. Is Reaper really the best solution?

---

### Post by cchhrriiss121212 on 2010-09-13
The best thing I have seen for this would be Qsynth, which you can use to load soundfonts (.sf2 files). It does not come with any soundfonts, so you will have to look around for your own, there are plenty free and non-free ones out there.

---

### Post by sgx on 2010-09-14
The linuxsampler can load .gig files, so scour ebay craigslist and forum marketplace sections for Tascam giga format sound collections. Lots are out there. In addition, Sampletank and most IKM products can be used in linux with wineasio, and reaper, and possible with festige, though I have not tested that. Most any plugins without dongles, pace, or ilok copy protection, will work.
There is also a thread about FLS v9 working now, after lots of effort to sort things. In addition, Hydrogen will play back samples in patterns, and sequences of patterns, with 32 samples per kit. So quite a powerful band can be assembled if you are clever with designing and placing your multiple patterns in a
linear grid. Some good youtube on hydrogen and ardour, also cover
setup of the jackd sound server for your audio connections. 

The Fluid R3 soundfont is a good GM collection, and googling for orchestral soundfonts will lead to a few large ones with good samples inside.
Cheers
I use reaper nearly every day, typically with 6 or fewer plugins, and it can run alongside native linux apps, I usually use rakarrack for multi fx (bye bye Amplitube) zynaddsubfx for incredible synth sounds, phasex synth for more incredible sound, hydrogen for sample playback, and drum machine. I also use Drumcore, and EZDrummer, which sound great, but lack the creative space hydrogen provides. I'll double up on the percussion sometimes. Guitarix and Calf plugins are also excellent for fx, and ardour excels at audio recording. qtractor is a sequencer that is probabaly great, I have yet to try it myself. I use windows to record very rarely, for a few synthedit synths that sometimes fail compatibility with a new version of wine. I always have a separate partition for /home, as reinstalling a linux does not require repartioning everything, sparing tedious reinstall/reconfigure sessions, and the need for a drive imaging degree.
 
Using qjackctl, its easy to connect everything to one recording app, I usually use the simple Timemachine, but ardour is a worldclass multi-track signal catcher, under continual developement. Audacity has a linux version that is a workhorse for polishing files, and jamin is a setup for mastering. So the options are quite nice for a small studio. There are people at the reaper forum
who claim to do huge reaper projects in linux, and they seem credible to me.
I install reaper in /home/username
When you install wineasio, the user, (not sudo or root) runs the commands

winecfg

regsvr32 wineasio.dll

The first one opens a config panel, choose alsa for sound, nothing else.

the second one will reply the .dll is registered, and it will show up in most windows
vst host apps as the only asio option. 

I have a dual boot with XP, and copied all the registered Native Instruments apps and Service Center, to their linux/wine counterparts. Sampletank writes in the registry, so you'll probably
have to do a separate install, using a simple command like

wine /home/user/InstallAmplitubeFender.exe

IKM will usually hand out extra authorizations to good customers, if you need one.
Cheers

---


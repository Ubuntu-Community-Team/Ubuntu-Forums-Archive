---
title: "No sound in Rosegarden"
date: 2009-01-02
forum: Ubuntu Studio
---

### Post by perito77 on 2009-01-02
Dear all,

_**[FONT="Arial Black"][SIZE="6"]First of all happy New Year 2009 for everybody[/SIZE][/FONT]**_  :P

[I]Little introduction about my project for this year.\\:D/
Together with some friends we are going to make a world trip giving some workshop (Latin dancing) and DJ-ing. For this project we wanted to make free samples of our music available for download using only open-source systems. This to promote the open source culture even more...
Due to incompatibilities with other software (Skype, Yuguu, Firefox and Audacity) we decided to use Ubuntu Hardy LTS edition.......[/I]

Since 3 weeks ago I was struggling to get Rosegarden work with no luck...:x

Before upgrading it was working fine. I have tried everything I could find on Google to get this fix:

[U]-posting on launchpad (2x) 
-attempt with Tmidity (not working)
-attempt with FluidSynth & Qsynt (no luck)
-attempt in installing Intrepid versions of Rosegarden with its dependencies (no audio, no luck)
-rebuilding the kernel, configuring alsa plugings (nada)[/U]

You name it.... I was really upset that I could not find a decent sequencer to work with Ardour, Jamin, Hydrogen and Jack.

I have tried Muse and LMMS but it was not quite good and easy to learn/work with.But still I do not want to use in my Windows system; Reason, FL Studio and Samplitude to make free samples because it was agains our policy.

When finishing this message I said to myself to Google for something else to see what we can find for the last time. I came across the website:
**[Making Music Blog]("http://making-music.blogspot.com")**

Here they had a whole list of open source software for music productions. There I saw **[energyXT2]("http://www.energy-xt.com")**

*I just could not believe what I was seeing... A real topnotch Music production system that had everything we needed. Only 1 problem... it was not really open source.*:shock:

At that point me with our crew deliberated about this and since we are very tight on schedule already we decided to give it a Go! Even tho you have to pay (a very small amount) for it, you still are working in Linux.[-o<

*I guess it's is true that for some applications you have to give money to have something decent to work with.*:lolflag:

Still I would like to see this Rosegarden issue solved but as I have seen in many other forum messages, blogs and mailinglists this will not be the case till the newest version of Ubuntu gets out.:-\"

Here I will put some references of misguided solution I found.
Thanks for the input and for those who did make a effort in fixing this.


[SIZE="4"]References:[/SIZE]](*,)

[https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?action=show&redirect=MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?action=show&redirect=MidiSoftwareSynthesisHowTo)

[https://launchpad.net/ubuntu/+source/rosegarden](https://launchpad.net/ubuntu/+source/rosegarden)

[https://launchpad.net/ubuntu/hardy/+source/rosegarden/+questions](https://launchpad.net/ubuntu/hardy/+source/rosegarden/+questions)

[http://osdir.com/ml/linux.ubuntu.user.ubuntu-studio/2008-03/msg00175.html](http://osdir.com/ml/linux.ubuntu.user.ubuntu-studio/2008-03/msg00175.html)

[http://osdir.com/ml/linux.ubuntu.user.ubuntu-studio/2008-03/msg00176.html](http://osdir.com/ml/linux.ubuntu.user.ubuntu-studio/2008-03/msg00176.html)

[http://osdir.com/ml/linux.ubuntu.user.ubuntu-studio/2008-03/msg00177.html](http://osdir.com/ml/linux.ubuntu.user.ubuntu-studio/2008-03/msg00177.html)

[http://www.linuxforums.org/forum/suse-linux-help/120591-solved-no-sound-rosegarden.html](http://www.linuxforums.org/forum/suse-linux-help/120591-solved-no-sound-rosegarden.html)

[https://answers.launchpad.net/ubuntu/+source/rosegarden/+question/54605](https://answers.launchpad.net/ubuntu/+source/rosegarden/+question/54605)

[http://www.getdeb.net/search.php?keywords=rosegarden](http://www.getdeb.net/search.php?keywords=rosegarden)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[http://www.rosegardenmusic.com/tutorials/en/chapter-2.html](http://www.rosegardenmusic.com/tutorials/en/chapter-2.html)

---

### Post by barisurum on 2009-01-03
Can you include the output messages of rosegarden that appears when you run it? Also run rosegarden from a terminal and include the outputs that appear there. Is jack audio server working properly? Can you work with other jack software as ardour or rezound? If you can then the problem is rosegarden related. Add more info please.

---

### Post by perito77 on 2009-01-03
Thanks for the reply but no worries. I am no longer interested in solving this issue because it's been going on way too long. But I will put the output for you before I de-install it.
Take care

```

$ rosegarden
kbuildsycoca running...
Reusing existing ksycoca
PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/user/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
junior@COMQNC:~$ Rosegarden 1.6.1 - AlsaDriver [ALSA library version 1.0.15, module version 1.0.16, kernel version 2.6.24-22-generic]

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 1024
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem
LADSPAPluginFactory::discoverPlugins - done
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/user/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    129,0 - (FLUID Synth (6980), Synth input port (6980:0))		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 129:0 on initialisation
done
Creating device 0 in Play mode for connection 129:0 Synth input port (6980:0) (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI output system device for device 1
done
Creating device 1 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 2 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 16, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.16 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 24, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.24-22-generic at least 2.6.20? yes
    Current timer set to "RTC timer" with timer checks
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

LADSPAPluginFactory::discoverPlugins - done
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.6.1/src/base/Composition.cpp:1455
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 130:3 to General MIDI Device
CompositionModelImpl::slotInstrumentParametersChanged()

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    129,0 - (FLUID Synth (6980), Synth input port (6980:0))		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]

kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
Renaming device 0 to General MIDI Device
Disconnecting my port 3 from 129:0 on reconnection
Connecting my port 3 to 14:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 20:0 Midisport 2x2 MIDI 1 (duplex) requested for device 0
AlsaDriver::setPlausibleConnection: fuzzy match 14:0 Midi Through Port-0 (duplex) available with fitness 3
Renamed 130:3 to General MIDI Device
Renaming device 1 to MIDI external device 2
Connecting my port 4 to 14:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 20:1 Midisport 2x2 MIDI 2 (duplex) requested for device 1
AlsaDriver::setPlausibleConnection: fuzzy match 14:0 Midi Through Port-0 (duplex) available with fitness 1
Renamed 130:4 to MIDI external device 2
CREATED OUTPUT PORT 5:out 3 for device 5
Creating device 5 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 1
Renaming device 5 to MIDI external device 3
Connecting my port 5 to 14:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 24:0 UM-2 MIDI 1 (duplex) requested for device 5
AlsaDriver::setPlausibleConnection: fuzzy match 14:0 Midi Through Port-0 (duplex) available with fitness 1
Renamed 130:5 to MIDI external device 3
CREATED OUTPUT PORT 6:out 4 for device 6
Creating device 6 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 2
Renaming device 6 to MIDI external device 4
Connecting my port 6 to 14:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 24:1 UM-2 MIDI 2 (duplex) requested for device 6
AlsaDriver::setPlausibleConnection: fuzzy match 14:0 Midi Through Port-0 (duplex) available with fitness 1
Renamed 130:6 to MIDI external device 4
CREATED OUTPUT PORT 7:out 5 for device 7
Creating device 7 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 3
Renaming device 7 to MIDI external device 5
Connecting my port 7 to 14:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 32:0 VirMIDI 4-0 (duplex) requested for device 7
AlsaDriver::setPlausibleConnection: fuzzy match 14:0 Midi Through Port-0 (duplex) available with fitness 1
Renamed 130:7 to MIDI external device 5
CREATED OUTPUT PORT 8:out 6 for device 8
Creating device 8 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 4
Renaming device 8 to MIDI external device 6
Connecting my port 8 to 14:0 on reconnection
AlsaDriver::setPlausibleConnection: connection like 33:0 VirMIDI 4-1 (duplex) requested for device 8
AlsaDriver::setPlausibleConnection: fuzzy match 14:0 Midi Through Port-0 (duplex) available with fitness 1
Renamed 130:8 to MIDI external device 6
CREATED OUTPUT PORT 9:out 7 for device 9
Creating device 9 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 5
Renaming device 9 to MIDI output system device
Renamed 130:9 to MIDI output system device

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    129,0 - (FLUID Synth (6980), Synth input port (6980:0))		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]

DataBlockRepository::clear()
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.6.1/src/base/Composition.cpp:1455
Available track ids are: 
1
2
3
4
5
6
7
8
10
11
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.6.1/src/base/Composition.cpp:1455
Available track ids are: 
1
2
3
4
5
6
7
8
10
11
Warning: Composition::~Composition() with 2 observers still extant
Observers are: 0x898d8c4 [N10Rosegarden19SegmentParameterBoxE] 0xb518e020 [N10Rosegarden20CompositionModelImplE]
SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()
JackDriver::stopTransport: resetting m_haveAsyncAudioEvent
SoundDriver::clearAudioQueue
RosegardenSequencerApp::quit()
AudioInstrumentMixer::destroyAllPlugins
done
AudioInstrumentMixer::~AudioInstrumentMixer
AudioInstrumentMixer::removeAllPlugins
AudioInstrumentMixer::~AudioInstrumentMixer exiting
DataBlockRepository::clear()
SoundDriver::~SoundDriver (exiting)
AudioPlayQueue::~AudioPlayQueue()
Toodle-pip.
Warning: Composition::~Composition() with 1 observers still extant
Observers are: 0x897a3f0 [N10Rosegarden20CompositionModelImplE]

```

---

### Post by babarosa on 2009-01-04
Hi perito77,

although rosegarden seems to be the most prominent sequencer software these days, I never could get it working properly _on my machine_, it always suffers from crashing using repository's and [www.getdeb.net](www.getdeb.net) versions.

I prefer working with _muse_ (it looks a bit like the old cakewalk v9), but you have to compile the latest svn-version or get a ready made package from [https://launchpad.net/~weboide/+archive](https://launchpad.net/~weboide/+archive), because the repo's version is much too old.
Muse works very well on my machines. Complement it with the newest version of musescore from [https://launchpad.net/~mscore-ubuntu/+archive](https://launchpad.net/~mscore-ubuntu/+archive), and you equal the functions of rosegarden.

To set up (x)ubuntu as an audio work station, you need to install and use the rt-kernel, make some settings for real time priority and maybe give rights to the audio group. then (x)ubuntu works very fine with the audio applications, which are improving rapidly.

Regards, Michael

---

### Post by perito77 on 2009-01-23
Thanks for the replies guys but one thing I learned in the Linux scene is that if you are not willing to waste your time searching for the right fix then just drop it.

About Muse; it's a very good sequencer but not to my linking. I found just 3 other applications that were even better then Rosegarden:

1. Traverso ([http://traverso-daw.org](http://traverso-daw.org)) - Multitrack audio recording & editing
2. Qtractor ([http://qtractor.sourceforge.net/qtractor-index.html](http://qtractor.sourceforge.net/qtractor-index.html)) - Audio/MIDI multi-track sequencer
3. Renoise ([http://www.renoise.com/](http://www.renoise.com/)) - music production environment

Both "Traverso" and "Qtractor" can be installed from the repository. Renoise is a paid software (only $53.24) but I have to say that this one if by FAR my favorite. I am just waiting for version 2 that will be out on the 25th of January:D

After founding these I really don't miss Rosegarden at all.

This thread is for me closed:popcorn:

---


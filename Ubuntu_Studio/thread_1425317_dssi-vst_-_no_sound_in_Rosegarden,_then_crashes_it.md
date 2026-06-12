---
title: "dssi-vst - no sound in Rosegarden, then crashes it"
date: 2010-03-08
forum: Ubuntu Studio
---

### Post by KoRnholio on 2010-03-08
Running Karmic, I started using a demo for a VST, Magnus Choir, which actually advertises Linux compatibility. 

I first tried getting it to work using the command 'vsthost'.  This actually works fine.  I am able to run it from the commandline, and route midi input to it from any app that outputs midi commands. I hear the choir, great.

To better integrate it with my workflow, though, I'd like to get it working through Rosegarden. So I install dssi-vst from the repos, and follow the instructions from various posts. After some work (apparently dssi-vst-scanner doesn't recurse...I had to plop the dll straight in the main directory to get it to see it), I was able to load the VST into Rosegarden as a Synth plugin.

It immediately jumps to 30% processor usage. Its also very prone to segfaulting at this point. Clicking the editor results in a segfault. The main problem is that Rosegarden now produces no sound, even from the channels that aren't using the VST. Then, after about twenty seconds, it gives me the message 'Out of processor power for realtime audio processing'.

I've pasted the terminal output of Rosegarden.
```

crockett@crockett-laptop:~$ sudo rosegarden
Setting graphics system for Qt 4.5+ to: raster
Thorn - 1
System Locale: en_US
Qt translations path: /usr/share/qt4/translations
Qt translations not loaded.
RG Translation: trying to load :locale/en_US
RG Translations loaded successfully.
Loaded application icon "rg-rwb-rose3-16x16"
Loaded application icon "rg-rwb-rose3-32x32"
Loaded application icon "rg-rwb-rose3-48x48"
Loaded application icon "rg-rwb-rose3-64x64"
Loaded application icon "rg-rwb-rose3-128x128"
NOTE: Found stylesheet at ":/rosegarden.qss", applying it
QSettings::endGroup: No matching beginGroup()
AlsaDriver::AlsaDriver [begin]
Rosegarden 10.02.1 - AlsaDriver [ALSA library version 1.0.20, module version 1.0.20, kernel version 2.6.31-20-generic]
PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/crockett/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 1024
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]

AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-20-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-20-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 250Hz resolution!
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG src/base/Composition.cpp:1560
Available track ids are: 
AlsaDriver::addDevice(0,0)
CREATED OUTPUT PORT 3:out 1 - unnamed for device 0
Renamed 129:3 to General MIDI Device
AlsaDriver::addDevice(0,1)
AlsaDriver::setRecordDevice: device 1, action 1
WARNING: AlsaDriver::renameDevice: Cannot find device 1 in port map
audio file manager emitting fake setValue(100)
RosegardenDocument::openDocument: Successfully opened document "/home/crockett/.local/share/rosegarden/autoload/autoload.rg"
VST_PATH not set, defaulting to /home/crockett/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
LADSPAPluginFactory::discoverPlugins - done
Object::connect: No such slot Rosegarden::AudioInstrumentParameterPanel::updateAllBoxes() in src/gui/editors/parameters/AudioInstrumentParameterPanel.cpp:81
Object::connect:  (receiver name: 'Audio Instrument Parameter Panel')
VST_PATH not set, defaulting to /home/crockett/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/crockett/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]

VST_PATH not set, defaulting to /home/crockett/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
LADSPAPluginFactory::discoverPlugins - done
Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:58
Object::disconnect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:65
Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentPencil.cpp:61
DataBlockRepository::clear()
Studio::getMetronomeFromDevice: Having a look at device 1000
Studio::getMetronomeFromDevice: Having a look at device 10000
Studio::getMetronomeFromDevice: Having a look at device 0
Studio::getMetronomeFromDevice(0): device is a MIDI device
rosegarden: could not connect to socket
rosegarden: No such file or directory
Rosegarden: WARNING: No accurate sequencer timer available (and kernel is new enough for RTC addendum)
MAIN WINDOW DISPLAY WARNING:  type 2 text<h3>System timer resolution is too low!</h3>
Rosegarden: WARNING: No accurate sequencer timer available (and kernel is new enough for RTC addendum)
SystemFont::loadSystemFont[Qt]: wanted family LilyPond-feta-rosegarden at size 12, got family LilyPond-feta-rosegarden (exactMatch 1)
SystemFont::loadSystemFont[Qt]: wanted family LilyPond-feta-nummer-rosegarden at size 12, got family LilyPond-feta-nummer-rosegarden (exactMatch 1)
Comparing current version "10.02.1" with latest version "10.02"
SystemFont::loadSystemFont[Qt]: wanted family LilyPond-parmesan-rosegarden at size 12, got family LilyPond-parmesan-rosegarden (exactMatch 1)
SystemFont::loadSystemFont[Qt]: wanted family bitstream vera serif at size 12, got family DejaVu Serif (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family luxi serif at size 12, got family DejaVu Serif (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family times new roman at size 12, got family Times New Roman (exactMatch 1)
SystemFont::loadSystemFont[Qt]: wanted family fughetta at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "fughetta"
SystemFont::loadSystemFont[Qt]: wanted family georgia at size 12, got family Georgia (exactMatch 1)
SystemFont::loadSystemFont[Qt]: wanted family inkpen2 at size 12, got family DejaVu Sans (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family inkpen at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "inkpen2,inkpen"
SystemFont::loadSystemFont[Qt]: wanted family inkpen2 text at size 12, got family DejaVu Sans (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family inkpen text at size 12, got family DejaVu Sans (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family comic sans ms at size 12, got family Comic Sans MS (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family maestro at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "maestro"
SystemFont::loadSystemFont[Qt]: wanted family opus at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "opus"
SystemFont::loadSystemFont[Qt]: wanted family opus text at size 12, got family DejaVu Sans (exactMatch 0)
SystemFont::loadSystemFont[Qt]: wanted family petrucci at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "petrucci"
I am here!
Object::connect: No such signal Rosegarden::ProgressReporter::setProgress(int) in src/document/RosegardenDocument.cpp:1630
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
Composition::notifySegmentAdded
SystemFont::loadSystemFont[Qt]: wanted family sonata at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "sonata"
Plugin identifier ladspa:/usr/lib/ladspa/tap_eq.so:tap_equalizer -> plugin 0xb502f218
set identifier to plugin at position 0 of container 10000
Plugin identifier dssi:/usr/lib/dssi/fluidsynth-dssi.so:FluidSynth-DSSI -> plugin 0xb50d5e78
set identifier to plugin at position 999 of container 10000
Plugin identifier dssi:/usr/lib/dssi/fluidsynth-dssi.so:FluidSynth-DSSI -> plugin 0xb50d5e78
set identifier to plugin at position 999 of container 10001
Plugin identifier ladspa:/usr/lib/ladspa/caps.so:AmpVTS -> plugin 0xb502e598
set identifier to plugin at position 0 of container 10002
Plugin identifier dssi:/usr/lib/dssi/fluidsynth-dssi.so:FluidSynth-DSSI -> plugin 0xb50d5e78
set identifier to plugin at position 999 of container 10002
AlsaDriver::addDevice(0,0)
CREATED OUTPUT PORT 3:out 1 - unnamed for device 0
Renamed 129:3 to General MIDI Device
AlsaDriver::addDevice(0,1)
AlsaDriver::setRecordDevice: device 1, action 1
WARNING: AlsaDriver::renameDevice: Cannot find device 1 in port map

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]

audio file manager emitting fake setValue(100)
AudioInstrumentMixer::setPlugin(10000, 0, ladspa:/usr/lib/ladspa/tap_eq.so:tap_equalizer)
AudioInstrumentMixer::setPlugin(10000, 999, dssi:/usr/lib/dssi/fluidsynth-dssi.so:FluidSynth-DSSI)
SystemFont::loadSystemFont[Qt]: wanted family steinberg notation at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "steinberg notation"
SystemFont::loadSystemFont[Qt]: wanted family xinfonia at size 12, got family DejaVu Sans (exactMatch 0)
Warning: Unable to load any of the fonts in "xinfonia"
AudioInstrumentMixer::setPlugin(10001, 999, dssi:/usr/lib/dssi/fluidsynth-dssi.so:FluidSynth-DSSI)
AudioInstrumentMixer::setPlugin(10002, 0, ladspa:/usr/lib/ladspa/caps.so:AmpVTS)
AudioInstrumentMixer::setPlugin(10002, 999, dssi:/usr/lib/dssi/fluidsynth-dssi.so:FluidSynth-DSSI)
RosegardenDocument::openDocument: Successfully opened document "/home/crockett/Music/dudebro/broaphim.rg"
DataBlockRepository::clear()
Studio::getMetronomeFromDevice: Having a look at device 1000
Studio::getMetronomeFromDevice: Having a look at device 10000
Studio::getMetronomeFromDevice: Having a look at device 0
Studio::getMetronomeFromDevice(0): device is a MIDI device
Warning: Composition::~Composition() with 3 observers still extant
Observers are: 0xae0a130 [N10Rosegarden19SegmentParameterBoxE] 0xae7c708 [N10Rosegarden17TrackParameterBoxE] 0xae9df50 [N10Rosegarden20CompositionModelImplE]
RosegardenSequencer::isTransportSyncComplete: token 0, current token 2
Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentSelector.cpp:73
Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:58
Object::disconnect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:65
Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentSelector.cpp:73
RosegardenSequencer::transportChange: 0
RosegardenSequencer::isTransportSyncComplete: token 2, current token 3
RosegardenSequencer::transportChange: 0
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1000
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1001
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1002
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1003
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1004
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1005
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1006
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1007
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1008
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1009
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1010
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1011
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1012
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1013
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1014
SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1015
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10000
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10001
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10002
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10003
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10004
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10005
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10006
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10007
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10008
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10009
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10010
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10011
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10012
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10013
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10014
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10015
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10016
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10017
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10018
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10019
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10020
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10021
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10022
SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10023
SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()
RosegardenSequencer::isTransportSyncComplete: token 3, current token 3
RosegardenSequencer::isTransportSyncComplete: token 3, current token 4
RosegardenSequencer::isTransportSyncComplete: token 3, current token 4
JackDriver::stopTransport: resetting m_haveAsyncAudioEvent
RosegardenSequencer::isTransportSyncComplete: token 3, current token 4
SoundDriver::clearAudioQueue
RosegardenSequencer::isTransportSyncComplete: token 3, current token 6
RosegardenSequencer::transportChange: 0
AudioInstrumentMixer::removePlugin(10000, 999)
VST_PATH not set, defaulting to /home/crockett/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
AudioInstrumentMixer::setPlugin(10000, 999, dssi:/usr/lib/dssi/dssi-vst.so:Magnus*Choir*demo.dll)
DSSIVSTPlugin::instantiate(Magnus*Choir*demo.dll)
DSSIVSTPluginInstance::DSSIVSTPluginInstance(Magnus*Choir*demo.dll)
Returning file identifiers: JPERKfKx6odpCNQWFycxRu8H
DSSI_PATH not set, defaulting to /home/crockett/.dssi:/usr/local/lib/dssi:/usr/lib/dssi
RemoteVSTClient: executing /usr/lib/dssi/dssi-vst/dssi-vst-server Magnus*Choir*demo.dll,JPERKfKx6odpCNQWFycxRu8H
wine: /home/crockett/.wine is not owned by you
DSSIVSTPluginInstance::DSSIVSTPluginInstance(Magnus*Choir*demo.dll): startup failed: Plugin server timed out on startup
DSSIVSTPluginInstance::DSSIVSTPluginInstance(Magnus*Choir*demo.dll) construction complete
JackDriver::jackProcess: no instrument mixer lock available
DSSIVSTPlugin::configure(DSSI:PROJECT_DIRECTORY,/home/crockett/rosegarden/)
DSSIVSTPluginInstance::configure(DSSI:PROJECT_DIRECTORY,/home/crockett/rosegarden/)
RosegardenSequencer::isTransportSyncComplete: token 6, current token 7
RosegardenSequencer::transportChange: 0
SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()
RosegardenSequencer::isTransportSyncComplete: token 7, current token 7
RosegardenSequencer::isTransportSyncComplete: token 7, current token 8
RosegardenSequencer::isTransportSyncComplete: token 7, current token 8
JackDriver::stopTransport: resetting m_haveAsyncAudioEvent
RosegardenSequencer::isTransportSyncComplete: token 7, current token 8
SoundDriver::clearAudioQueue
RosegardenSequencer::isTransportSyncComplete: token 7, current token 10
RosegardenSequencer::transportChange: 0
Temporary file name is: "/home/crockett/.local/share/rosegarden/autosave/1a012fb299edf7bb77c82a621da8b959ecf68fee..hX2894": is this a full path?  We hope so
```

---

### Post by babarosa on 2010-03-09
Here you find the latest versions of dssi and dssi-vst:
[https://launchpad.net/~philip5/+archive/extra?field.series_filter=karmic](https://launchpad.net/~philip5/+archive/extra?field.series_filter=karmic)

As far as I know, vst-dll's have to be placed in /usr/local/lib/vst. Being sudo, set the dll's read and write rules accessible for all users.

I am using "muse", dssi and dssi-vst with only two vsts (one of them is a must) and also from time to time have to deal with some weired behaviour.

---

### Post by sgx on 2010-03-09
Install Reaper, wine and wineasio if you are serious about using vsts.
The alternatives will kill or limit your creativity just fixing the plumbing. The Reaper output will ultimately be a just an extravagant rompler, that you can record with, or to, other linux apps.
Cheers

---

### Post by KoRnholio on 2010-03-14
Well, I decided to use fst instead.  There is a ppa available ( [http://ppa.launchpad.net/falk-t-j/festige/ubuntu](http://ppa.launchpad.net/falk-t-j/festige/ubuntu) ) that has the new fst, built from reverse engineered Steinberg headers. So you don't have to get the Steinberg headers yourself. It actually installs festige, which is a simple GUI on top of FST.

To get midi input, however, I'm using MuseScore. The MuseScore ppa supports Jack MIDI output, and its been working flawlessly.

---


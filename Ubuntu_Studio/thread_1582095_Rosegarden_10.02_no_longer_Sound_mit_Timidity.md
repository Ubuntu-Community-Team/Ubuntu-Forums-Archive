---
title: "Rosegarden 10.02 no longer Sound mit Timidity"
date: 2010-09-26
forum: Ubuntu Studio
---

### Post by taifunorkan on 2010-09-26
Hello

I don't get any sound on rosegarden, although I have installed timitidy and run Jack.

I asked for help, but didn't get any reply. mybe the wrong forum for my special request. But htis thread is in German.

[http://forum.ubuntuusers.de/topic/rosegarden-10-02-kein-sound-mit-timidity/#post-2632554](http://forum.ubuntuusers.de/topic/rosegarden-10-02-kein-sound-mit-timidity/#post-2632554)

Any help would be wonderfull. I need rosegarden for music production.

Bernd

Here is the translation:

[user:taifunorkan:] wrote:

I don't know how many hours I spent to get rosegarden working. Eventually it did with timidity. Bu now, the sound has gone again. A software update?

Is there anybody who please can give me advice?
 
A normal midi-file I can listen :-)
 
I start rosegarden this way:

> $  /usr/bin/qjackctl
Fine. Jack is running.

Next I start timidity for Jack:
> $ timidity -B2,8  -Oj -s 44100 -iA
okay!
 
> $ rosegarden "/home/oslt/Musik/dritte Quellen/BWV245 27b.mid"
opens rosegarden and the corret file
After start there is no sound and the "common midi-device" echos no Connection (to Timidity).


Console:
> 
> {{{
> Enhanced3DNow! detected
> SSE2 detected
> TiMidity starting in ALSA server mode
> Opening sequencer port: 130:0 130:1 130:2 130:3
> }}}
> 
> {{{
> Setting graphics system for Qt 4.5+ to: raster
> Thorn - 1
> System Locale: de_DE
> Qt translations path: /usr/share/qt4/translations
> Qt translations loaded successfully.
> RG Translation: trying to load :locale/de_DE
> RG Translations loaded successfully.
> Loaded application icon "rg-rwb-rose3-16x16"
> Loaded application icon "rg-rwb-rose3-32x32"
> Loaded application icon "rg-rwb-rose3-48x48"
> Loaded application icon "rg-rwb-rose3-64x64"
> Loaded application icon "rg-rwb-rose3-128x128"
> NOTE: Found stylesheet at ":/rosegarden.qss", applying it
> QSettings::endGroup: No matching beginGroup()
> AlsaDriver::AlsaDriver [begin]
> Rosegarden 10.02 - AlsaDriver [ALSA library version 1.0.22, module version 1.0.21, kernel version 2.6.32-24-preempt]
> PluginFactory::instance(dssi): creating new DSSIPluginFactory
> LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/oslt/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
> Enhanced3DNow! detected
> SSE2 detected
> 
> JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 1024
> JackDriver::initialiseAudio - creating disk thread
> JackDriver::initialiseAudio - found 2 JACK physical outputs
> JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
> JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
> JackDriver::initialiseAudio - found 2 JACK physical inputs
> JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
> JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
> JackDriver::initialiseAudio - initialised JACK audio subsystem
> 
>   ALSA Client information:
> 
>     14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
>     128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
> 
> AlsaDriver::setCurrentTimer((auto))
>     Current timer set to "system timer" with timer checks
> AlsaDriver::initialiseMidi -  initialised MIDI subsystem
> 
> AlsaDriver::setCurrentTimer((auto))
>     Current timer set to "system timer" with timer checks
> Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG src/base/Composition.cpp:1560
> Available track ids are: 
> AlsaDriver::addDevice(0,0)
> CREATED OUTPUT PORT 3:out 1 - unnamed for device 0
> Renamed 131:3 to General MIDI Device
> LADSPAPluginFactory::discoverPlugins - done
> PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
> LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/oslt/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
> AlsaDriver::addDevice(0,1)
> AlsaDriver::setRecordDevice: device 1, action 1
> WARNING: AlsaDriver::renameDevice: Cannot find device 1 in port map
> audio file manager emitting fake setValue(100)
> RosegardenDocument::openDocument: Successfully opened document "/home/oslt/.local/share/rosegarden/autoload/autoload.rg"
> Object::connect: No such slot Rosegarden::AudioInstrumentParameterPanel::updateAllBoxes() in src/gui/editors/parameters/AudioInstrumentParameterPanel.cpp:81
> Object::connect:  (receiver name: 'Audio Instrument Parameter Panel')
> LADSPAPluginFactory::discoverPlugins - done
> Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:58
> Object::disconnect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:65
> Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentPencil.cpp:61
> Connecting my port 3 to 128:0 on reconnection
> AlsaDriver::setPlausibleConnection: connection like "" requested for device 0
> AlsaDriver::setPlausibleConnection: fuzzy match 128:0 TiMidity port 0 (write) available with fitness 1
> AlsaDriver::setPlausibleConnection: connection like "" requested for device 1
> AlsaDriver::setPlausibleConnection: nothing suitable available
> DataBlockRepository::clear()
> Studio::getMetronomeFromDevice: Having a look at device 1000
> Studio::getMetronomeFromDevice: Having a look at device 10000
> Studio::getMetronomeFromDevice: Having a look at device 0
> Studio::getMetronomeFromDevice(0): device is a MIDI device
> rosegarden: could not connect to socket
> rosegarden: No such file or directory
> Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG src/base/Composition.cpp:1560
> Available track ids are: 
> AlsaDriver::addDevice(0,0)
> CREATED OUTPUT PORT 3:out 1 - unnamed for device 0
> Renamed 131:3 to General MIDI Device
> AlsaDriver::addDevice(0,1)
> AlsaDriver::setRecordDevice: device 1, action 1
> WARNING: AlsaDriver::renameDevice: Cannot find device 1 in port map
> audio file manager emitting fake setValue(100)
> RosegardenDocument::openDocument: Successfully opened document "/home/oslt/.local/share/rosegarden/autoload/autoload.rg"
> midiBytesToLong(0,0,0,6) -> 6
> Parsing Track 0
> midiBytesToLong(0,0,0,71) -> 71
> Parse track: last track number is 0
> Parsing Track 1
> midiBytesToLong(0,0,16,4) -> 4100
> Parse track: last track number is 1
> MidiFile: new channel map entry: channel 0 -> track 1
> MidiFile: track number for channel 0 is 1
> Program change or channel aftertouch: time 0, code 192, data 71 going to track 1
> Parsing Track 2
> midiBytesToLong(0,0,16,203) -> 4299
> Parse track: last track number is 2
> MidiFile: new channel map entry: channel 1 -> track 2
> MidiFile: track number for channel 1 is 2
> Program change or channel aftertouch: time 0, code 193, data 68 going to track 2
> Parsing Track 3
> midiBytesToLong(0,0,17,64) -> 4416
> Parse track: last track number is 3
> MidiFile: new channel map entry: channel 2 -> track 3
> MidiFile: track number for channel 2 is 3
> Program change or channel aftertouch: time 0, code 194, data 41 going to track 3
> Parsing Track 4
> midiBytesToLong(0,0,15,76) -> 3916
> Parse track: last track number is 4
> MidiFile: new channel map entry: channel 3 -> track 4
> MidiFile: track number for channel 3 is 4
> Program change or channel aftertouch: time 0, code 195, data 42 going to track 4
> Parsing Track 5
> midiBytesToLong(0,0,15,19) -> 3859
> Parse track: last track number is 5
> MidiFile: new channel map entry: channel 4 -> track 5
> MidiFile: track number for channel 4 is 5
> Program change or channel aftertouch: time 0, code 196, data 0 going to track 5
> Parsing Track 6
> midiBytesToLong(0,0,11,69) -> 2885
> Parse track: last track number is 6
> MidiFile: new channel map entry: channel 4 -> track 6
> MidiFile: track number for channel 4 is 6
> Program change or channel aftertouch: time 0, code 196, data 0 going to track 6
> Parsing Track 7
> midiBytesToLong(0,0,0,32) -> 32
> Parse track: last track number is 7
> MidiFile: new channel map entry: channel 0 -> track 7
> MidiFile: track number for channel 0 is 7
> New Rosegarden track: id = 0, instrument = 2000, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 1, instrument = 2000, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 2, instrument = 2001, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 3, instrument = 2002, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 4, instrument = 2003, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 5, instrument = 2004, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 6, instrument = 2004, name = Imported MIDI
> Composition::notifySegmentAdded
> New Rosegarden track: id = 7, instrument = 2000, name = Imported MIDI
> Composition::notifySegmentAdded
> DataBlockRepository::clear()
> Studio::getMetronomeFromDevice: Having a look at device 1000
> Studio::getMetronomeFromDevice: Having a look at device 10000
> Studio::getMetronomeFromDevice: Having a look at device 0
> Studio::getMetronomeFromDevice(0): device is a MIDI device
> Warning: Composition::~Composition() with 3 observers still extant
> Observers are: 0x7fefec00eb00 [N10Rosegarden19SegmentParameterBoxE] 0x2806040 [N10Rosegarden17TrackParameterBoxE] 0x2c03a20 [N10Rosegarden20CompositionModelImplE]
> RosegardenSequencer::isTransportSyncComplete: token 0, current token 2
> CompositionModelImpl::slotInstrumentParametersChanged()
> CompositionModelImpl::slotInstrumentParametersChanged()
> Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentSelector.cpp:73
> Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:58
> Object::disconnect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentMover.cpp:65
> Object::connect: No such signal Rosegarden::CompositionView::contentsMoving (int, int) in src/gui/editors/segment/compositionview/SegmentSelector.cpp:73
> RosegardenSequencer::transportChange: 0
> Connecting my port 3 to 128:0 on reconnection
> AlsaDriver::setPlausibleConnection: connection like "" requested for device 0
> AlsaDriver::setPlausibleConnection: fuzzy match 128:0 TiMidity port 0 (write) available with fitness 1
> AlsaDriver::setPlausibleConnection: connection like "" requested for device 1
> AlsaDriver::setPlausibleConnection: nothing suitable available
> SystemFont::loadSystemFont[Qt]: wanted family LilyPond-feta-rosegarden at size 12, got family LilyPond-feta-rosegarden (exactMatch 1)
> SystemFont::loadSystemFont[Qt]: wanted family LilyPond-feta-nummer-rosegarden at size 12, got family LilyPond-feta-nummer-rosegarden (exactMatch 1)
> SystemFont::loadSystemFont[Qt]: wanted family LilyPond-parmesan-rosegarden at size 12, got family LilyPond-parmesan-rosegarden (exactMatch 1)
> SystemFont::loadSystemFont[Qt]: wanted family bitstream vera serif at size 12, got family DejaVu Serif (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family luxi serif at size 12, got family DejaVu Serif (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family times new roman at size 12, got family Times New Roman (exactMatch 1)
> SystemFont::loadSystemFont[Qt]: wanted family fughetta at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "fughetta"
> SystemFont::loadSystemFont[Qt]: wanted family georgia at size 12, got family Georgia (exactMatch 1)
> SystemFont::loadSystemFont[Qt]: wanted family inkpen2 at size 12, got family DejaVu Sans (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family inkpen at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "inkpen2,inkpen"
> SystemFont::loadSystemFont[Qt]: wanted family inkpen2 text at size 12, got family DejaVu Sans (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family inkpen text at size 12, got family DejaVu Sans (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family comic sans ms at size 12, got family Comic Sans MS (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family maestro at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "maestro"
> Comparing current version "10.02" with latest version "10.04.2"
> MAIN WINDOW DISPLAY WARNING:  type 4 text<h3>Neuere Version verfügbar</h3>
> SystemFont::loadSystemFont[Qt]: wanted family opus at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "opus"
> SystemFont::loadSystemFont[Qt]: wanted family opus text at size 12, got family DejaVu Sans (exactMatch 0)
> SystemFont::loadSystemFont[Qt]: wanted family petrucci at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "petrucci"
> SystemFont::loadSystemFont[Qt]: wanted family sonata at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "sonata"
> SystemFont::loadSystemFont[Qt]: wanted family steinberg notation at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "steinberg notation"
> SystemFont::loadSystemFont[Qt]: wanted family xinfonia at size 12, got family DejaVu Sans (exactMatch 0)
> Warning: Unable to load any of the fonts in "xinfonia"
> 
>   ALSA Client information:
> 
>     14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
>     128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
>     130,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
> }}}
> 

After I hit on Play:
> 
> {{{
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1000
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1001
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1002
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1003
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1004
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1005
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1006
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1007
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1008
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1009
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1010
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1011
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1012
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1013
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1014
> SoundDriver: setMappedInstrument() : type = 1 : channel = 2 : id = 1015
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10000
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10001
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10002
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10003
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10004
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10005
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10006
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10007
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10008
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10009
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10010
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10011
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10012
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10013
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10014
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10015
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10016
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10017
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10018
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10019
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10020
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10021
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10022
> SoundDriver: setMappedInstrument() : type = 2 : channel = 2 : id = 10023
> SoundDriver::initialiseAudioQueue -- new queue has 0 files
> AudioPlayQueue::~AudioPlayQueue()
> RosegardenSequencer::isTransportSyncComplete: token 2, current token 2
> RosegardenSequencer::isTransportSyncComplete: token 2, current token 3
> RosegardenSequencer::isTransportSyncComplete: token 2, current token 3
> JackDriver::stopTransport: resetting m_haveAsyncAudioEvent
> RosegardenSequencer::isTransportSyncComplete: token 2, current token 3
> SoundDriver::clearAudioQueue
> }}}
> 
> 
> 
>

---

### Post by Pablo_F on 2010-09-26
Hi,

In  Rosegarden, go to Studio -> Manage MIDI devices. 

In the MIDI playback window, select the playback device. In this case, "common MIDI device". You can rename it if you wish. Now, choose the midi input (write) port on the right window. Timidity presents 4 MIDI ports, "timidity port 0" should be OK.

Make sure the timidity audio outputs are connected to the system playbacks in the audio tab of qjackctl.

Cheers! Pablo

---

### Post by mstreibe on 2011-01-12
I tried to get Rosegarden (also 10.02) running with timidity, and only once did it produce sound, It was quiet ever after. I have no idea why it worked back then, and what was different afterwards. Definitely no version change, as it was on the same day, and I had no internet connection :)

I never again managed to get sound out of rosegarden via timidity. Meanwhile I found a different combination of tools that works reliably for me:

- Install fluid-soundfonts-gs, fluid-soundfonts-gm, jackd, JACK Control, Qsynth
- Run the programs in the following order (from the K Menu if you're using KDE -> Applications -> Multimedia:
  Jack Control
  QSynth
  Rosegarden

In Qsynth, select the 2 installed sound fonts via the "Configuration" Button and the Sound fonts tab in the window that opens.

In Rosegarden, select qsynth as the midi output device. Then you should be able to hear sound from rosegarden.

I only have some other rosegarden problem now. When I load a midi file (a very simple one with one track and a few notes), I can play it, but when I resize the track in order to add notes, then I hear no more sound until I save it and open it again.

Any help for that?

---

### Post by mstreibe on 2011-01-12
I'm new to rosegarden, so maybe I'm doing it completely wrong...

---

### Post by Pablo_F on 2011-01-12
Hi, 

> I only have some other rosegarden problem now. When I load a midi file (a very simple one with one track and a few notes), I can play it, but when I resize the track in order to add notes, then I hear no more sound until I save it and open it again.

It was a bug in Rosegarden: [http://sourceforge.net/tracker/?func=detail&aid=3014769&group_id=4932&atid=104932](http://sourceforge.net/tracker/?func=detail&aid=3014769&group_id=4932&atid=104932)

It is solved in the current official version. You will have to compile from the sources, or get a precompiled binary (a deb package) from somewhere. (Or live with it). What ubuntu(studio) version are you running?

Cheers! Pablo

---

### Post by mstreibe on 2011-01-13
Yes meanwhile I got the same info via the rosegarden-users mailing list. I installed the latest version from the deb package which is available for debian experimental. It installed smoothly on my kubuntu 10.10, after removing the original rosegarden and rosegarden-data ubuntu packages.

---


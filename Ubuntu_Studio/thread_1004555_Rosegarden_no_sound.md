---
title: "Rosegarden no sound"
date: 2008-12-07
forum: Ubuntu Studio
---

### Post by korgman on 2008-12-07
I can't get any audio out of Rosegarden.

TiMiditty can open and play mid files just fine.  Jack is up and running.  kinfocenter says that Synth devices : NOT ENABLED IN CONFIG
and Midi devices : NOT ENABLED IN CONFIG
Kernel is 2.6.27.7-generic
Hydrogen plays audio fine.

**Starting rosegarden from the cmd line i get:**
kbuildsycoca running...
Enhanced3DNow! detected
SSE2 detected
PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/matt/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
matt@Mega-Linux:~/Desktop$ LADSPAPluginFactory::discoverPlugins - done
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/matt/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
Rosegarden 1.7.0 - AlsaDriver [ALSA library version 1.0.17a, module version 1.0.17, kernel version 2.6.27-7-generic]
Enhanced3DNow! detected
SSE2 detected

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 1024
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 6 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 128:0 on initialisation
done
Creating device 0 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI software device 2 for device 1
Connecting my port 4 to 128:1 on initialisation
done
Creating device 1 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
CREATED OUTPUT PORT 5:out 3 - MIDI software device 3 for device 2
Connecting my port 5 to 128:2 on initialisation
done
Creating device 2 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
CREATED OUTPUT PORT 6:out 4 - MIDI software device 4 for device 3
Connecting my port 6 to 128:3 on initialisation
done
Creating device 3 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
CREATED OUTPUT PORT 7:out 5 - MIDI output system device for device 4
done
Creating device 4 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 5 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 17, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.17 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 27, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.27-7-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.0/src/base/Composition.cpp:1539
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 130:3 to General MIDI Device
LADSPAPluginFactory::discoverPlugins - done
CompositionModelImpl::slotInstrumentParametersChanged()
TrackButtons::slotUpdateTracks
Rosegarden: WARNING: No accurate sequencer timer available
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
Launched ok, pid = 10713
Comparing current version "1.7.0" with latest version "1.7.2"
RosegardenGUIApp::awaitDialogClearance: entering

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]

RosegardenGUIApp::awaitDialogClearance: exiting


**When I try to play something, I see this and get no sound:**

SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()
JackDriver::stopTransport: resetting m_haveAsyncAudioEvent
SoundDriver::clearAudioQueue

---

### Post by chongzi889 on 2008-12-08
Mud Valve is one of api 6a **[gate valve](http://www.valvesupplier.net/index.htm)**,operated by double actuated thread, and featuring tight structure. The series [gate valve]("http://www.valvesupplier.net/index.htm") had been widely used in oil field, crude exploitation

---

### Post by Jaapie on 2009-09-16
Same here (jaunty). timidity plays midi's but rosegarden doesn't. Timidity is running daemonized in the background.

---


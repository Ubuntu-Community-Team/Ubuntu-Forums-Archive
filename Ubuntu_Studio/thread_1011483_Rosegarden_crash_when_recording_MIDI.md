---
title: "Rosegarden crash when recording MIDI"
date: 2008-12-14
forum: Ubuntu Studio
---

### Post by RedfishBluefish on 2008-12-14
Rosegarden crashes when I try to record from my USB midi interface.The midi device doesn't have any description in lsusb, it just identifies as "1a86:752d". It's a bit strange because rosegarden actually starts recording fine, but if I press a key on the piano/keyboard (a CTK-691) it instantly dies, with these messages:

> $ rosegarden
PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/neil/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
LADSPAPluginFactory::discoverPlugins - done
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/neil/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
LADSPAPluginFactory::discoverPlugins - done
Rosegarden 1.7.0 - AlsaDriver [ALSA library version 1.0.17a, module version 1.0.17, kernel version 2.6.27-9-generic]

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    20,0 - (USB2.0-MIDI, USB2.0-MIDI MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    20,1 - (USB2.0-MIDI, USB2.0-MIDI MIDI 2)		(WRITE ONLY) [ctype 2, ptype 589826, cap 74]

CREATED OUTPUT PORT 3:out 1 - MIDI external device for device 0
Connecting my port 3 to 20:1 on initialisation
done
Creating device 0 in Play mode for connection 20:1 USB2.0-MIDI MIDI 2 (write)
Default device name for this device is MIDI external device
CREATED OUTPUT PORT 4:out 2 - MIDI external device 2 for device 1
Connecting my port 4 to 20:0 on initialisation
done
Creating device 1 in Play mode for connection 20:0 USB2.0-MIDI MIDI 1 (duplex)
Default device name for this device is MIDI external device 2
Creating device 2 in Record mode for connection 20:0 USB2.0-MIDI MIDI 1 (duplex)
Default device name for this device is MIDI hardware input device
CREATED OUTPUT PORT 5:out 3 - MIDI output system device for device 3
done
Creating device 3 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 4 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 17, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.17 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 27, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.27-9-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

AlsaDriver::setCurrentTimer(RTC timer)
Renaming device 0 to General MIDI Device
Renamed 128:3 to General MIDI Device
Renaming device 1 to out 2 - MIDI output system device
Renamed 128:4 to out 2 - MIDI output system device
CompositionModelImpl::slotInstrumentParametersChanged()
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
TrackButtons::slotUpdateTracks

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    20,0 - (USB2.0-MIDI, USB2.0-MIDI MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    20,1 - (USB2.0-MIDI, USB2.0-MIDI MIDI 2)		(WRITE ONLY) [ctype 2, ptype 589826, cap 74]

AlsaDriver::setRecordDevice - successfully subscribed device 2 as record port

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    20,0 - (USB2.0-MIDI, USB2.0-MIDI MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    20,1 - (USB2.0-MIDI, USB2.0-MIDI MIDI 2)		(WRITE ONLY) [ctype 2, ptype 589826, cap 74]

CompositionModelImpl::segmentAdded: segment 0x3196d10 on track 63: calling setTrackHeights
TrackButtons::slotUpdateTracks

 Jump using MMC LOCATE to 0.000000000R
	 which is 0:0:0.0.0
SoundDriver::initialiseAudioQueue -- new queue has 0 files
AudioPlayQueue::~AudioPlayQueue()

(This is when I press a note)

> Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.0/src/base/Composition.cpp:1539
Available track ids are: 
63
KCrash: Application 'rosegarden' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

I'll have a look at the rosegarden source where it suggests but I don't expect I'll be able to figure anything out.

---


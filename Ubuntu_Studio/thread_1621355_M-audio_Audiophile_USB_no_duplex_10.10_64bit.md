---
title: "M-audio Audiophile USB no duplex 10.10 64bit"
date: 2010-11-14
forum: Ubuntu Studio
---

### Post by sliwowitz on 2010-11-14
I have an m-audio audiophile usb soundcard. I want to use it in duplex mode with jack, but it gives me an ALSA error about "broken pipe". Verbose log here: 
```

14:43:05.314 Patchbay deactivated.
14:43:05.441 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
14:43:05.660 ALSA connection graph change.
14:43:05.999 ALSA connection change.
14:43:06.003 ALSA connection graph change.
14:43:26.078 Startup script...
14:43:26.079 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
14:43:26.480 Startup script terminated with exit status=32512.
14:43:26.480 JACK is starting...
14:43:26.480 /usr/bin/jackd -v -dalsa -r48000 -p512 -n2 -D -Chw:1,1 -Phw:1
14:43:26.525 JACK was started with PID=2135.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0
Jack: apparent rate = 48000
Jack: frames per period = 512
Jack: capture device hw:1,1
Jack: playback device hw:1
Jack: JackDriver::Open capture_driver_name = hw:1,1
Jack: JackDriver::Open playback_driver_name = hw:1
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 512
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1,1|512|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 1 - M-Audio Audiophile USB (tm) at usb-0000:00:1d.0-1.2, full speed
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit big-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit big-endian
ALSA: use 2 periods for playback
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_freewheel val = 0
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackGraphManager::SetBufferSize size = 512
Jack: JackAudioDriver::Attach fBufferSize 512 fSampleRate 48000
Jack: JackGraphManager::AllocatePortAux port_index = 1 name = system:capture_1 type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 1
Jack: JackAudioDriver::Attach fCapturePortList[i] 1 
Jack: JackGraphManager::AllocatePortAux port_index = 2 name = system:capture_2 type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 2
Jack: JackAudioDriver::Attach fCapturePortList[i] 2 
Jack: JackGraphManager::AllocatePortAux port_index = 3 name = system:playback_1 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 3
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 3 
Jack: JackGraphManager::AllocatePortAux port_index = 4 name = system:playback_2 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 4
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 4 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
ALSA: could not start playback (Broken pipe)
Cannot start driver
JackServer::Start() failed with -1
Jack: Jack
14:43:27.050 JACK was stopped with exit status=255.
14:43:27.050 Post-shutdown script...
14:43:27.051 killall jackd
Server::Close
Jack: JackServerSocket::Close /dev/shm/jack_default_1000_0
Jack: JackAudioDriver::Detach
Jack: JackGraphManager::DisconnectAllOutput port_index = 1 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 1 
Jack: JackGraphManager::DisconnectAllOutput port_index = 2 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 2 
Jack: JackGraphManager::DisconnectAllInput port_index = 3
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 3 
Jack: JackGraphManager::DisconnectAllInput port_index = 4
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 4 
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackEngine::ClientCloseAux ref = 0
Jack: JackGraphManager::RemoveAllPorts ref = 0
Jack: JackPosixSemaphore::Destroy
Released audio card Audio1
audio_reservation_finish
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 1 ref2 = 1
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackEngine::ClientCloseAux ref = 1
Jack: JackGraphManager::RemoveAllPorts ref = 1
Jack: JackPosixSemaphore::Destroy
Jack: JackEngine::Close
Jack: JackClientSocket::Close
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: ThreadHandler: exit
Jack: Succeeded in unlocking 82208666 byte memory area
Jack: JackShmMem::delete size = 0 index = 0
Jack: ~JackDriver
Jack: ~JackDriver
Jack: JackEngine::~JackEngine
Jack: Succeeded in unlocking 994 byte memory area
Jack: JackShmMem::delete size = 0 index = 1
Jack: cleaning up shared memory
Jack: cleaning up files
Jack: unregistering server `default'
Failed to start server
jackd: no process found
14:43:27.474 Post-shutdown script terminated with exit status=256.

```

If I switch to playback/capture only mode, it works (but I need duplex mode, so this is not an option).

This is on an lenovo X201s laptop, no restricted drivers, fresh install.
Weird thing is, that on my old Pentium-M 32bit laptop, the very same soundcard works in duplex mode using the exact same settings I use on the new one. 

EDIT: 64bit doesn't seem to be a problem. I just tried 32liveCD on the X201 and it shows the same error - no duplex mode, but capture/playback only works. The old 32bit laptop has 10.10 as well, but gradually updated since 8.04, so I really have no idea what additional packages/configurations I might have added over the years.

---


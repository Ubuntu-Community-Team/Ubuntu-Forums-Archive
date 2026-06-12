---
title: "Cannot get jack to start!!"
date: 2015-03-28
forum: Ubuntu Studio
---

### Post by mina2 on 2015-03-28
...so jack doesn't want to start and it's driving me crazy.  Been googling around for a while.

So far all I did was to add myself to the audio group and raise the max memory lock to unlimited (I think?) This was what I did:

```
sudo dpkg-reconfigure -p high jackd2
```

```
sudo adduser *MyUserName* audio
```

And here are Qjackctl's errors so far:

```
[COLOR=#999999]20:42:36.088 JACK is starting...[/COLOR][COLOR=#990099]20:42:36.089 /usr/bin/jackd -v -dalsa -dhw:CA0106 -r48000 -p256 -n2 -P -o1[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
no message buffer overruns
no message buffer overruns
[COLOR=#999999]20:42:36.109 JACK was started with PID=30574.[/COLOR]
no message buffer overruns
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Jack: JackPosixThread::StartImp : create non RT thread
Jack: JackPosixThread::ThreadHandler : start
Jack: playback device hw:CA0106
Jack: capture device hw:CA0106
Jack: apparent rate = 48000
Jack: frames per period = 256
Jack: JackDriver::Open capture_driver_name = hw:CA0106
Jack: JackDriver::Open playback_driver_name = hw:CA0106
Jack: Check protocol client = 8 server = 8
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 256
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:CA0106|-|256|2|48000|0|1|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 256 frames (5.3 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: cannot set channel count to 1 for playback
ALSA: cannot configure playback channel
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackEngine::ClientInternalClose ref = 0
Jack: JackEngine::ClientCloseAux ref = 0
Jack: JackGraphManager::RemoveAllPorts ref = 0
Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_system
Jack: ~JackDriver
Cannot initialize driver
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: JackPosixThread::ThreadHandler : exit
JackServer::Open failed with -1
Jack: Succeeded in unlocking 82274202 byte memory area
Jack: JackShmMem::delete size = 0 index = 0
Jack: ~JackDriver
Jack: Succeeded in unlocking 1186 byte memory area
Jack: JackShmMem::delete size = 0 index = 1
Jack: Cleaning up shared memory
Jack: Cleaning up files
Jack: Unregistering server `default'
Failed to open server
[COLOR=#999999]20:42:36.220 JACK was stopped with exit status=255.[/COLOR]
[COLOR=#ff0000]20:42:38.303 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

aaaaah I want to use ardour and stuff but jack's in the way. I had jack working on my older computer but now I want it to work here. plz help plz help plz help plz help. :-({|=

What other info do you need? My sound card is a "Creative SoundBlaster 5.1 VX" and there's an onboard audio card, a "Core3D" .. inputs doesn't work (no mics work) but I only need the audio output for now. I chose "Playback only". ...What other info do you need? ...aaaaaaaaaand thanks in advance!

---

### Post by mina2 on 2015-10-06
[COLOR=#333333][FONT=Lucida Grande]Okay so my problem got solved with the command `pasuspender`! To use it with qjackctl one types[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]pasuspender qjackctl[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]It "pauses" pulseaudio to allow qjackctl to takeover. .. till qjackctl is terminated and pulseaudio just pops back in! Apparently pulseaudio wasn't allowing jack to take over my audio. .. This quite solves most of my life's audio problems with jack X'D[/FONT][/COLOR]

---


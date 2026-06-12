---
title: "using Behringer audio mixer as input to jack not working"
date: 2014-06-17
forum: Ubuntu Studio
---

### Post by smaring on 2014-06-17
I have a Behringer Xenyx X1204USB audio mixer that shows up as:

```
$ lsusb | grep Audio
Bus 005 Device 005: ID 08bb:2902 Texas Instruments PCM2902 Audio Codec

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT2020 Alt Analog [VT2020 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

it shows up in qjackctl as input sourc hw:CODEC

However, when I select that, jack won't start and I get ...

```
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Jack: JackPosixThread::StartImp : create non RT thread
Jack: JackPosixThread::ThreadHandler : start
Jack: playback device hw:0
Jack: capture device hw:0
Jack: capture device hw:CODEC
Jack: apparent rate = 44100
Jack: frames per period = 2048
Jack: JackDriver::Open capture_driver_name = hw:CODEC
Jack: JackDriver::Open playback_driver_name = hw:0
Jack: Check protocol client = 8 server = 8
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 2048
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio2
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:CODEC|2048|2|44100|0|0|nomon|swmeter|-|16bit
configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
05:35:04.051 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Jack: jack_client_open qjackctl
Jack: JackLibGlobals Init 0
Jack: JackLibGlobals
Jack: JackPosixThread::StartImp : create non RT thread
Jack: JackPosixThread::ThreadHandler : start
Jack: JackGenericClientChannel::ServerCheck = default
Jack: JackClientSocket::Connect : addr.sun_path /dev/shm/jack_default_1000_0
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Jack: JackClientSocket::Close
jack server is not running or cannot be started
Jack: JackLibGlobals Destroy fc7150
Jack: ~JackLibGlobals
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: JackPosixThread::ThreadHandler : exit
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
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
05:35:07.085 JACK was stopped with exit status=255.
```

the things that stick out to me here are:

```
ALSA: cannot set hardware parameters for capture
Cannot initialize driver
```

I've tried setting values that would seem to be compatible with the specs
[http://www.ti.com/product/pcm2902]("http://www.ti.com/product/pcm2902"), but nothing is working.

The frustrating thing is that I had this working before installing some other multimedia apps and running some updates.  So, I'm suspicious that the config options have nothing to do with the problem.

Selecting the other input devices, including default, allows jack to start.  However, with default, the inputs from the audio mixer don't show up as ports.

-Steve
Orlando, FL

---

### Post by CrocoDuck on 2014-06-18
Hi! When I use an USB interfece I always select "USB Audio" in Qjacktlt:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=252912&d=1399375381[/IMG]

Have a try!

---

### Post by jejeman on 2014-06-19
Use samplerate 48000, and 3 periods.

---


---
title: "jackd doesn't start"
date: 2010-10-16
forum: Ubuntu Studio
---

### Post by breek on 2010-10-16
every time i try to start jack control in ubuntustudio 10.10 64 bit i get an error window saying

```

could not connect to jack server as client.
- overall operation failed.
- unable to connect as server.
please check the messages window for more info

```

and in the messages window i get this

```

03:44:35.968 Patchbay deactivated.
03:44:35.969 Statistics reset.
JackSocketClientChannel read fail
Cannot open qjackctl client
03:44:40.983 ALSA connection graph change.
03:44:41.189 ALSA connection change.
03:44:41.190 ALSA connection graph change.
03:45:25.300 Startup script...
03:45:25.300 artsshell -q terminate
JackSocketClientChannel read fail
Cannot open qjackctl client
sh: artsshell: not found
03:45:25.702 Startup script terminated with exit status=32512.
03:45:25.702 JACK is starting...
03:45:25.702 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2
03:45:25.704 JACK was started with PID=2204.
no message buffer overruns
no message buffer overruns
`default' server already active
Failed to start server
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
03:45:25.751 JACK was stopped with exit status=255.
03:45:25.751 Post-shutdown script...
03:45:25.752 killall jackd
03:45:26.167 Post-shutdown script terminated successfully.
03:45:27.716 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = Nessun file o directory
Cannot connect to server socket
jack server is not running or cannot be started

```

if i remove the realtime feature in the jack options i get the same error window but in the messages window i get lots and lots of this

```

Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
alsa_driver_xrun_recovery
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
alsa_driver_xrun_recovery
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
alsa_driver_xrun_recovery

```

any idea?

moreover if i should get jack to run, a latency of 46.4 msec is the best i can get from a generic kernel and an i5 750???

---

### Post by AutoStatic on 2010-10-17
> **breek said:**
> ```
`default' server already active
Failed to start server
```JACK was already started so that's why it doesn't come up.

What soundcard are you using? And could you provide the output of **cat /proc/interrupts** ? And did you disable CPU frequency scaling?

---

### Post by breek on 2010-10-17
i don't think it's a hardware problem as a couple of days ago it used to work on 10.04.
anyway here they are:

```

reek@maialinux:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:         28          0          0          0   IO-APIC-edge      timer
  1:          2          0          0          0   IO-APIC-edge      i8042
  8:          1          0          0          0   IO-APIC-edge      rtc0
  9:         73          0          0          0   IO-APIC-fasteoi   acpi
 12:          4          0          0          0   IO-APIC-edge      i8042
 16:       6022          0          0      45328   IO-APIC-fasteoi   ehci_hcd:usb1, hda_intel, nvidia
 17:          1          0          0          0   IO-APIC-fasteoi   xhci_hcd:usb3
 18:          1          0          0          0   IO-APIC-fasteoi   ahci, firewire_ohci
 19:         97          0       3959          0   IO-APIC-fasteoi   pata_jmicron
 21:       4888      19381          0          0   IO-APIC-fasteoi   ata_piix, ata_piix
 23:         69          0      11817          0   IO-APIC-fasteoi   ehci_hcd:usb2
 40:      43595          0          0          0  HPET_MSI-edge      hpet2
 41:          0      33594          0          0  HPET_MSI-edge      hpet3
 42:          0          0      26055          0  HPET_MSI-edge      hpet4
 43:          0          0          0      12395  HPET_MSI-edge      hpet5
 56:     110536          0          0          0   PCI-MSI-edge      eth0
 58:       1515          0          0         21   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:         70         55         38         21   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:        236        482        307        269   Rescheduling interrupts
CAL:        220        285        279        152   Function call interrupts
TLB:       1104       1149       1150        862   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          4          4          4          4   Machine check polls
ERR:          3
MIS:          0
reek@maialinux:~$ 

```

about cpu frequency scaling i can say i5 has turboboost, a technology that overclock the cpu in case of eccessive load, but i don't know if the kernel support this.

the audio card is VIA VT2020, the one integrated on p7p55d-e deluxe motherboard.
on pulseaudio preferences i see 2 devices: "analog stereo duplex" and "digital stereo (hdmi) output"
```

reek@maialinux:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: VT2020 Analog [VT2020 Analog]
  Sottoperiferiche: 2/2
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
scheda 0: Intel [HDA Intel], dispositivo 1: VT2020 Digital [VT2020 Digital]
  Sottoperiferiche: 2/2
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
scheda 1: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 7: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 8: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 9: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
reek@maialinux:~$

```


on a fresh booted system "ps -e" shows no jack or jackd.
when starting jack control, messages window says:

```

12:39:02.976 Patchbay deactivated.
12:39:02.982 Statistics reset.
Cannot connect to server socket err = Nessun file o directory
Cannot connect to server socket
jack server is not running or cannot be started
12:39:03.014 ALSA connection graph change.
12:39:03.225 ALSA connection change.
12:39:03.226 ALSA connection graph change.

```

---

### Post by RaumTrug on 2010-10-17
last time i've seen that error (server already active), jack had crashed at the first startup after booting up, and remained as kind of zombie in the background, disfunctional, and keeping jack from starting up again.

either do a fresh reboot, or try something like "killall jackd" (can't tell if that'd work), and then try to start up jack, having "verbose messages" mode enabled, and paste messages output here.

and yah, disable cpu-scaling (easiest way: there's an applet for the gnome-tray/panel, don't know what it's called in english - create one for each core & set them all to "performance", or any other level that doesn't change speeds). I think every modern cpu does scaling (since pentium III), and it's not really got something to do with the "turboboost" (let's just hope setting "performance" doesn't overclock to max, making your cores too hot...), but with lowering cpu speeds when cpu isn't loaded fully to save energy. jack doesn't like it, but normally it won't crash jack, but just give nasty x-runs...

oh and the rate...try 48k instead of 44.1k, maybe your soundcard doesn't like 44.1 in realtime....

---

### Post by breek on 2010-10-18
as i said before i've tried on a fresh booted system and now i've tried to killall jackd but the system told me that there was nothing like that to be killed.

verbose message was already active.

setting the sample rate to 48k made no change.

i've installed an applet called "cpu scaling" that only shows the clock for every core and indeed it tells 1.20 or 2.67 ghz (depending on the load) but i don't think this makes jack unable to start; as i said before, on the same machine it used to work on ubuntustudio 10.04.

any other ideas? :(

---

### Post by AutoStatic on 2010-10-18
> **breek said:**
> as i said before i've tried on a fresh booted system and now i've tried to killall jackd but the system told me that there was nothing like that to be killed.And what does **ps -aux | grep jack** output in that case?

> **breek said:**
> on the same machine it used to work on ubuntustudio 10.04.That's probably because 10.04 uses Jack1 and 10.10 uses Jack2. Did you do a fresh install or an upgrade?

---

### Post by breek on 2010-10-18
```

reek@maialinux:~$ ps -aux | grep jack
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
reek      2138  0.0  0.0   8976   876 pts/0    S+   09:13   0:00 grep --color=auto jack
reek@maialinux:~$

```

i always do fresh install, i have other partitions for my data

---

### Post by AutoStatic on 2010-10-18
Thanks! And what if you run JACK from the commandline?
**/usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2**

And you don't have a home on a separate partition? Or you didn't re-use any JACK related config files?

---

### Post by breek on 2010-10-18
/home is on a separate partition; when i install the new ubuntu i first boot using a live distro, so i rename the user folder, then install, then i copy a couple of config folder like .gimp , .mozilla, etc from old user to new one.
i don't re-use config files for gnome, jack, etc

here is the output of /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2 (but i had to hit ctrl-c because it was goin on forever)

```

reek@maialinux:~$ /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0
Jack: playback device hw:0
Jack: capture device hw:0
Jack: apparent rate = 44100
Jack: frames per period = 1024
Jack: JackDriver::Open capture_driver_name = hw:0
Jack: JackDriver::Open playback_driver_name = hw:0
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 1024
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf5ff8000 irq 58
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_freewheel val = 0
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackGraphManager::SetBufferSize size = 1024
Jack: JackAudioDriver::Attach fBufferSize 1024 fSampleRate 44100
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
Jack: JackGraphManager::AllocatePortAux port_index = 5 name = system:playback_3 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 5
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 5 
Jack: JackGraphManager::AllocatePortAux port_index = 6 name = system:playback_4 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 6
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 6 
Jack: JackGraphManager::AllocatePortAux port_index = 7 name = system:playback_5 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 7
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 7 
Jack: JackGraphManager::AllocatePortAux port_index = 8 name = system:playback_6 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 8
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 8 
Jack: JackGraphManager::AllocatePortAux port_index = 9 name = system:playback_7 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 9
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 9 
Jack: JackGraphManager::AllocatePortAux port_index = 10 name = system:playback_8 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 10
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 10 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackThreadedDriver::Init IsRealTime
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 2
Jack: fSocketTable i = 1 fd = 7
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
^Cjack main caught signal 2
Jack: JackServer::Stop
Jack: JackThreadedDriver::Stop
Jack: JackPosixThread::Stop
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: ThreadHandler: exit
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackServer::Close
Jack: JackPosixThread::Stop
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackRequest::Notification kQUIT
Jack: JackMachServerChannel::Execute JackQuitException
Jack: ThreadHandler: exit
Jack: JackServerSocket::Close /dev/shm/jack_default_1000_0
Jack: JackClientSocket::Close
Jack: JackAudioDriver::Detach
Jack: JackGraphManager::DisconnectAllOutput port_index = 1 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 1 
Jack: JackGraphManager::DisconnectAllOutput port_index = 2 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 2 
Jack: JackGraphManager::DisconnectAllInput port_index = 3
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 3 
Jack: JackGraphManager::DisconnectAllInput port_index = 4
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 4 
Jack: JackGraphManager::DisconnectAllInput port_index = 5
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 5 
Jack: JackGraphManager::DisconnectAllInput port_index = 6
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 6 
Jack: JackGraphManager::DisconnectAllInput port_index = 7
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 7 
Jack: JackGraphManager::DisconnectAllInput port_index = 8
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 8 
Jack: JackGraphManager::DisconnectAllInput port_index = 9
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 9 
Jack: JackGraphManager::DisconnectAllInput port_index = 10
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 10 
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackEngine::ClientCloseAux ref = 0
Jack: JackGraphManager::RemoveAllPorts ref = 0
Jack: JackPosixSemaphore::Destroy
Released audio card Audio0
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
reek@maialinux:~$ 

```

---

### Post by AutoStatic on 2010-10-18
So that works, no message about another 'default' instance of JACK running. A lot of xruns though. I think in your case it's the CPU scaling. I always disable it myself before doing any audio/music related things. Did you make any other optimisations to your system?

---

### Post by breek on 2010-10-18
well, why jack control doesn't work? isn't that the very same command?

no optimisations up till now... could you suggest an easy way to temporary disable cpu scaling?

edit: from motherboard manual:Intel(R) SpeedStep(TM) Tech [Enabled]
When set to [Disabled], the CPU runs at its default speed. When set to [Enabled], the CPU
speed is controlled by the operating system. Configuration options: [Disabled] [Enabled]

i'll do some tests in the afternoon... now i have to go to sleep... still awake after a night shift...

---

### Post by AutoStatic on 2010-10-18
> **breek said:**
> well, why jack control doesn't work? isn't that the very same command?I have no idea really. Could you post the contents of your $HOME/.config/rncbc.org/QjackCtl.conf file?

> **breek said:**
> no optimisations up till now... could you suggest an easy way to temporary disable cpu scaling?Haven't got a script at hand, the fastest way though is to add a CPU frequency scaling applet per core and set them all to a fixed frequency. You could also disable the ondemand service, but that requires you to install sysv-rc-conf or another tool to configure system services.

> **breek said:**
> edit: from motherboard manual:Intel(R) SpeedStep(TM) Tech [Enabled]
When set to [Disabled], the CPU runs at its default speed. When set to [Enabled], the CPU
speed is controlled by the operating system. Configuration options: [Disabled] [Enabled]SpeedStep = CPU frequency scaling. So disabling it in the BIOS should work too.

---

### Post by breek on 2010-10-18
i've disabled speedstep from bios but xruns remain

```

jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0
Jack: playback device hw:0
Jack: capture device hw:0
Jack: apparent rate = 44100
Jack: frames per period = 1024
Jack: JackDriver::Open capture_driver_name = hw:0
Jack: JackDriver::Open playback_driver_name = hw:0
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 1024
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf5ff8000 irq 58
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_freewheel val = 0
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackGraphManager::SetBufferSize size = 1024
Jack: JackAudioDriver::Attach fBufferSize 1024 fSampleRate 44100
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
Jack: JackGraphManager::AllocatePortAux port_index = 5 name = system:playback_3 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 5
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 5 
Jack: JackGraphManager::AllocatePortAux port_index = 6 name = system:playback_4 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 6
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 6 
Jack: JackGraphManager::AllocatePortAux port_index = 7 name = system:playback_5 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 7
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 7 
Jack: JackGraphManager::AllocatePortAux port_index = 8 name = system:playback_6 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 8
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 8 
Jack: JackGraphManager::AllocatePortAux port_index = 9 name = system:playback_7 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 9
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 9 
Jack: JackGraphManager::AllocatePortAux port_index = 10 name = system:playback_8 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 10
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 10 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackThreadedDriver::Init IsRealTime
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 2
Jack: fSocketTable i = 1 fd = 7
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
Jack: fPollTable i = 1 fd = 7
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: ALSA XRun wait_status = 0
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery

```

here is QjackCtl.conf

```

[Splitter]
AudioConnectView\sizes=266, 88, 266
MidiConnectView\sizes=34, 20, 34
AlsaConnectView\sizes=34, 20, 34
PatchbayView\sizes=34, 20, 34

[Settings]
Server=/usr/bin/jackd
Realtime=false
SoftMode=false
Monitor=false
Shorts=false
NoMemLock=false
UnlockMem=false
HWMon=false
HWMeter=false
IgnoreHW=false
Priority=0
Frames=1024
SampleRate=44100
Periods=2
WordLength=16
Wait=21333
Chan=0
Driver=alsa
Interface=
Audio=0
Dither=0
Timeout=500
InDevice=
OutDevice=
InChannels=0
OutChannels=0
InLatency=0
OutLatency=0
StartDelay=2
Verbose=true
PortMax=256
MidiDriver=none

[History]
ServerComboBox\Item1=/usr/bin/jackd
ServerComboBox\Item2=jackd
ServerComboBox\Item3=jackdmp
ServerComboBox\Item4=jackstart
InterfaceComboBox\Item1=(default)
InterfaceComboBox\Item2=hw:0
InterfaceComboBox\Item3=plughw:0
InterfaceComboBox\Item4=/dev/audio
InterfaceComboBox\Item5=/dev/dsp
InDeviceComboBox\Item1=(default)
InDeviceComboBox\Item2=hw:0
InDeviceComboBox\Item3=plughw:0
InDeviceComboBox\Item4=/dev/audio
InDeviceComboBox\Item5=/dev/dsp
OutDeviceComboBox\Item1=(default)
OutDeviceComboBox\Item2=hw:0
OutDeviceComboBox\Item3=plughw:0
OutDeviceComboBox\Item4=/dev/audio
OutDeviceComboBox\Item5=/dev/dsp
StartupScriptShellComboBox\Item1=artsshell -q terminate
PostShutdownScriptShellComboBox\Item1=killall jackd
XrunRegexComboBox\Item1=xrun of at least ([0-9|\\.]+) msecs
MessagesLogPathComboBox\Item1=qjackctl.log
ServerConfigNameComboBox\Item1=.jackdrc

[Program]
Version=0.3.6

[Presets]
DefPreset=(default)

[Options]
Singleton=true
StartJack=false
StartupScript=true
StartupScriptShell=artsshell -q terminate
PostStartupScript=false
PostStartupScriptShell=
ShutdownScript=false
ShutdownScriptShell=
PostShutdownScript=true
PostShutdownScriptShell=killall jackd
StdoutCapture=true
XrunRegex=xrun of at least ([0-9|\\.]+) msecs
XrunIgnoreFirst=false
ActivePatchbay=false
ActivePatchbayPath=
MessagesLog=false
MessagesLogPath=qjackctl.log
BezierLines=false
TimeDisplay=0
TimeFormat=0
MessagesFont="DejaVu Sans,8,-1,5,50,0,0,0,0,0"
MessagesLimit=true
MessagesLimitLines=1000
DisplayFont1="DejaVu Sans,12,-1,5,75,0,0,0,0,0"
DisplayFont2="DejaVu Sans,8,-1,5,50,0,0,0,0,0"
DisplayEffect=true
DisplayBlink=true
JackClientPortAlias=0
ConnectionsIconSize=0
ConnectionsFont="DejaVu Sans,8,-1,5,50,0,0,0,0,0"
QueryClose=true
KeepOnTop=false
SystemTray=false
StartMinimized=false
DelayedSetup=false
ServerConfig=true
ServerConfigName=.jackdrc
ServerConfigTemp=false
QueryShutdown=true
AlsaSeqEnabled=true
DBusEnabled=false
AliasesEnabled=false
AliasesEditing=false
LeftButtons=true
RightButtons=true
TransportButtons=true
TextLabels=true
BaseFontSize=0

[Defaults]
PatchbayPath=

[Geometry]
qjackctlMessagesForm\x=4
qjackctlMessagesForm\y=22
qjackctlMessagesForm\width=593
qjackctlMessagesForm\height=479
qjackctlMessagesForm\visible=false
qjackctlStatusForm\x=0
qjackctlStatusForm\y=0
qjackctlStatusForm\width=378
qjackctlStatusForm\height=234
qjackctlStatusForm\visible=false
qjackctlConnectionsForm\x=0
qjackctlConnectionsForm\y=0
qjackctlConnectionsForm\width=532
qjackctlConnectionsForm\height=280
qjackctlConnectionsForm\visible=false
qjackctlPatchbayForm\x=0
qjackctlPatchbayForm\y=0
qjackctlPatchbayForm\width=708
qjackctlPatchbayForm\height=353
qjackctlPatchbayForm\visible=false
qjackctlMainForm\x=797
qjackctlMainForm\y=138
qjackctlMainForm\width=450
qjackctlMainForm\height=100
qjackctlMainForm\visible=true

```

---

### Post by AutoStatic on 2010-10-18
Hmmm, that doesn't reveal anything that could cause issues. You could try installing the alsa backports package **linux-backports-modules-alsa-maverick-generic**, but that only works with the generic kernel. Which kernel are you using?

---

### Post by breek on 2010-10-18
yep i'm using the generic kernel but after installing that package (and rebooting) nothing changed :(

---

### Post by AutoStatic on 2010-10-18
Running out of options... Your soundcard does share an IRQ with your nvidia card. Are you using the closed source drivers? Did you try disabling the desktop effects?

---

### Post by breek on 2010-10-18
nvidia closed source driver (nvidia-current) but no desktop effects (never use them).
what could i try?

---

### Post by AutoStatic on 2010-10-18
You could try disabling the closed source nvidia drivers and try the nouveau drivers that come with kernels >= 2.6.32
Those drivers should load automatically when the closed source drivers are deactivated iirc.

---

### Post by trulan on 2010-10-18
This might be a long shot, but I've had the same issues with an HDA Intel (huge numbers of x-runs, older Ubuntu's) when the input was muted.  If I selected 'playback only' in Jack control, it would start just fine.  I fixed it by simply un-muting the input using gnome-alsamixer. (simple after I finally figured it out - 6 months later!)

---

### Post by breek on 2010-10-19
i've removed nvidia closed source driver and used nouveau but nothing changed for jack control.
i've tried to remove QjackCtl.conf but nothing changed.
i've installed gnome-alsamixer and unmuted one mic and line in (pretty strange as on pulseaudio control panel nothing was muted) but same issue.

now i'm reinstalling nvidia driver bacause on boot dispcalgui tells that can't load monitor profile; but what else can i do to make jack control working?

edit:
i think there's a BIG audio problem: after some seconds i use hydrogen (alsa driver... the only one i can use) long sounds like a crash or a splash are stopped and continued (audio glitches?) at least a couple of time! never heard this on hidrogen and alsa driver on 10.04

---

### Post by Naiki Muliaina on 2010-10-19
2 more paws up for this problem. Guess its time to hit Launchpad bug time? Both me and my partner need Jack as we both use IDJC a lot. We are both having the same problem.

---

### Post by breek on 2010-10-19
i think that it could be a matter of EXTREME latency in the kernel (or alsa driver?): that could be an answer for lots of xruns in jack and the gaps in hydrogen.
mp3 streams for example is something predictable (or at least buffered); if i random click on splash, tom, kick, etc in hydrogen, the system should be very resposnsive but it behaves like a system with very busy cpu (but it's not).
at this condition 10.10 can't stay on my main pc so i'm going back to 10.04 (even thou i know i'll have to solve a couple of problems); i'll install 10.10 on my secondary pc (p4, so 32 bit) and do some test.

---

### Post by breek on 2010-10-20
damn it's a nasty bug!

i've downgraded to 10.04 and added falkTX ppa to upgrade some packages.
jack, hydrogen... everything was working like a charm (not even a single xrun, even with speedstep enabled!). but to solve a mic issue (no mic selector shown in pulseaudio control pannel) i had to inslall linux-backports-modules-alsa-lucid-preempt... boom! again the same problems with jack!

i'm taking a look [here]("https://bugs.launchpad.net/ubuntu") but i can't find anything like that... should i open a new bug report?


edit: open a bug report is a real mess... anyway [here it is]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/663724")

---

### Post by breek on 2010-10-21
i've tried a clean (without any ppa) ubuntustudio 10.04 + linux-backports-modules-alsa-lucid-preempt but still no success :(

using realtime feature jack totally freeze;

without realtime jack gives lots and lots of
```

client event poll on 15 for qjackctl starts at 1360171238
back from client event poll after 121 usecs
client event poll on 15 for qjackctl starts at 1360231243
back from client event poll after 127 usecs

```
and then exits
```

20:42:07.471 Client deactivated.
20:42:07.472 JACK is stopping...
server thread back from poll
+++ deactivate qjackctl
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
start poll on 4 fd's
server thread back from poll
marking client qjackctl with SOCKET error state = Not triggered errors = 0
trying to lock graph to remove 1 problems
we have problem clients (problems = 1
++ Removing failed clients ...
client alsa_pcm error status 0
client qjackctl error status 10000000
removing failed client qjackctl state = Not triggered errors = 10000000
removing client "qjackctl"
removing client "qjackctl" from the processing chain
+++ deactivate qjackctl
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_sort_graph
-- Removing failed clients ...
after removing clients, problems = 0
start poll on 3 fd's
jack main caught signal 15
starting server engine shutdown
stopping driver
server thread back from poll
unloading driver
freeing shared port segments
stopping server thread
last xrun delay: 31.000 usecs
max delay reported by backend: 166.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
WARNING: 1 message buffer overruns!
cleaning up shared memory
cleaning up files
unregistering server `default'
20:42:07.544 JACK was stopped successfully.
20:42:07.545 Post-shutdown script...
20:42:07.545 killall jackd
jackd: nessun processo trovato
20:42:07.987 Post-shutdown script terminated with exit status=256.

```

starting from a terminal
```

reek@maialinux:~$ /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    6143934
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_dummy.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
new client: alsa_pcm, id = 1 type 1 @ 0x10ddd10 fd = -1
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
new buffer size 1024
registered port system:capture_1, offset = 4096
registered port system:capture_2, offset = 8192
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
registered port system:playback_5, offset = 0
registered port system:playback_6, offset = 0
registered port system:playback_7, offset = 0
registered port system:playback_8, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
2301 waiting for signals
jackd watchdog: timeout - killing jackd
reek@maialinux:~$ 

```

without linux-backports-modules-alsa-lucid-preempt jack runs fine
i've updated the info on my bug report on launchpad but it seems to be ignored...

---

### Post by Dangerouge on 2010-10-28
I have the same problem in Desktop 10.10, I've tried to start with almost every possible configuration, but I keep getting

```
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf7ff8000 irq 56
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
^Cjack main caught signal 2
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
Released audio card Audio0
audio_reservation_finish
```

---

### Post by night_fox on 2010-10-29
I thing I have the same problem, but I noticed this:

```

pacmd load-module module-jack-source channels=2; pacmd load-module module-jack-sink channels=2;
Welcome to PulseAudio! Use "help" for usage information.
>>> Module load failed.
>>> Welcome to PulseAudio! Use "help" for usage information.
>>> Module load failed.
```

where pulseaudio-module-jack is installed.

---

### Post by AutoStatic on 2010-10-29
Dangerouge: try disabling CPY frequency scaling.

night_fox: the fact that some PulseAudio module can't be loaded shouldn't cause xruns.

---

### Post by lpc921 on 2010-11-09
> **trulan said:**
> This might be a long shot, but I've had the same issues with an HDA Intel (huge numbers of x-runs, older Ubuntu's) when the input was muted.  If I selected 'playback only' in Jack control, it would start just fine.  I fixed it by simply un-muting the input using gnome-alsamixer. (simple after I finally figured it out - 6 months later!)

That works for me. I manually specified input device to my mic on the webcam and it works without any problems now. I didn't have a mic connected to the sound card

---


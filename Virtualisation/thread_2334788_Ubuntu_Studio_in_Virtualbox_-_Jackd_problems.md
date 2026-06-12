---
title: "Ubuntu Studio in Virtualbox - Jackd problems"
date: 2016-08-22
forum: Virtualisation
---

### Post by Tristan_Williams on 2016-08-22
Host: Windows 10 Home (10.0.14393)
Guest: Ubuntu Studio 16.04 64-bit
Virtualbox version 5.1.2 r108956

Host machine specs:
MSI X99S SLI PLUS Motherboard
Intel Xeon E5-1620v3 @ 3.5GHz
48GB (6x8GB) DDR4 Corsair
Samsung 512GB M.2 NVMe SSD
[DON'T KNOW MANUFACTURER] 400GB HDD (this is what the .vdi file is stored on)
NVidia Geforce GT640
NVidia Quadro 4000

----------------------------------------------------------------------------------------------------------

I have tried installing Ubuntu Studio 16.04 in virtualbox many dozens of times, and can't figure out what I'm doing wrong.
I've tried every combination of:
[LIST]
[*]2 host machines 
[*]5 HDD's and one NVMe M.2 SSD 
[*]2 Versions of Virtualbox 
[*]3 installation methods:
[LIST]
[*]Ubuntu Studio installation ISO 
[*]Xubuntu installation ISO, install ubuntustudio packages after setup 
[*]Ubuntu Minimal ISO, install ubuntustudio packages after setup. 
[/LIST]
  
[/LIST]
Yes, I tried all of those, to no avail (something like 60 installation attempts... I would've posted on here sooner, but I couldn't remember my login details)
I also tried a few times of installing on the physical machine. Can't remember what went wrong there. Couldn't do it though.

[SIZE=3]**Anyways. Here's the current situation:**[/SIZE]

I've installed Ubuntu Minimal 16.04, the installed all of the ubuntustudio packages (I don't feel like reinstalling anymore)
I've installed the guest additions stuff, done all my normal personal-preference modifications (themes and icons)

I am trying to use this to record music. Therefore, Jack and all the audio stuff needs to work. 
Trying to start jack fails, and gives the following error output:
```

13:27:03.759 Statistics reset.
 13:27:03.805 ALSA connection change.
 13:27:04.217 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 13:27:04.280 ALSA connection graph change.
 13:27:30.617 D-BUS: JACK server could not be started. Sorry
 Mon Aug 22 13:27:05 2016: Starting jack server...
 Mon Aug 22 13:27:05 2016: JACK server starting in realtime mode with priority 10
 Mon Aug 22 13:27:05 2016: self-connect-mode is "Don't restrict self connect requests"
 Mon Aug 22 13:27:05 2016: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
 Mon Aug 22 13:27:05 2016: Acquired audio card Audio0
 Mon Aug 22 13:27:05 2016: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Mon Aug 22 13:27:05 2016: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Mon Aug 22 13:27:05 2016: ALSA: final selected sample format for capture: 16bit little-endian
 Mon Aug 22 13:27:05 2016: ALSA: use 2 periods for capture
 Mon Aug 22 13:27:05 2016: ALSA: final selected sample format for playback: 16bit little-endian
 Mon Aug 22 13:27:05 2016: ALSA: use 2 periods for playback
 Mon Aug 22 13:27:05 2016: ERROR: Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
 Mon Aug 22 13:27:05 2016: ERROR: AcquireSelfRealTime error
 Mon Aug 22 13:27:10 2016: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Mon Aug 22 13:27:10 2016: ERROR: Driver is not running
 Mon Aug 22 13:27:10 2016: ERROR: Cannot open client name = dbusapi
 Mon Aug 22 13:27:10 2016: ERROR: failed to create dbusapi jack client
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 13:27:41.570 Could not connect to JACK server as  client. - Overall operation failed. - Server communication error. Please  check the messages window for more info.
 Cannot open qjackctl client
 JackShmReadWritePtr1::~JackShmReadWritePtr1 - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 Mon Aug 22 13:27:41 2016: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Mon Aug 22 13:27:41 2016: ERROR: Driver is not running
 Mon Aug 22 13:27:41 2016: ERROR: Cannot create new client

```

Any help is greatly appreciated.
Let me know if you have any other questions for me.

---

### Post by MAFoElffen on 2016-08-23
On one side, I thought it was a challenge to find a way to check jack states in a VM Guest isolated from the host's hardware. A jack is not a common item to check the state of... There were many who add recommendation to Oracle to add this as a feature to VirtualBox. 
[https://www.virtualbox.org/ticket/6049](https://www.virtualbox.org/ticket/6049)

But then I found this, which just happened to be for doing that with Ubuntu Studio:
[https://forums.virtualbox.org/viewtopic.php?f=1&t=63809](https://forums.virtualbox.org/viewtopic.php?f=1&t=63809)

---

### Post by Tristan_Williams on 2016-08-23
> **MAFoElffen said:**
> On one side, I thought it was a challenge to find a way to check jack states in a VM Guest isolated from the host's hardware. A jack is not a common item to check the state of... There were many who add recommendation to Oracle to add this as a feature to VirtualBox. 
[https://www.virtualbox.org/ticket/6049](https://www.virtualbox.org/ticket/6049)

But then I found this, which just happened to be for doing that with Ubuntu Studio:
[https://forums.virtualbox.org/viewtopic.php?f=1&t=63809](https://forums.virtualbox.org/viewtopic.php?f=1&t=63809)

That guide is meant for a Linux-based host machine.
I'm running Windows 10 as a host, so none of that works unfortunately.

Any other ideas?

---


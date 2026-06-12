---
title: "WineASIO problem"
date: 2011-01-05
forum: Ubuntu Studio
---

### Post by wkcchampion on 2011-01-05
Hi, I have Ubuntu 10.10 and i'm attempting to run Cockos Reaper (on WineASIO).:confused:
 I've tried to read otherp osts and do my best before creating this thread.

I downloaded the Deb of WineAsio 0.7.5 found in a thread over here. it installed fine with the Software Center.
I couldn't get the Steinberg SDK - page gives 404 error.

I installed reaper on both wine and Crossover (trial version). I enabled both ALSA and JACK audio drivers in Wine config. WineASIO is not shown in Reaper audio settings :(

Thanks for the help ):P

Marco

---

### Post by rusty377 on 2011-04-13
marco,

Did you select ASIO as your audio system and then select Wine asio under asio driver? I just did this in the same scenario and it works fine. I downloaded the .deb, right clicked and selected install - no fancy stuff at all :0)

---

### Post by Pablo_F on 2011-04-13
Did you remember to register wineasio.dll after installation? You need this command in a terminal window:

regsvr32 wineasio.dll

---

### Post by rusty377 on 2011-04-13
Pablo,

Oops! Did forget to mention that :0)

---

### Post by sgx on 2011-04-14
> **wkcchampion said:**
> Hi, I have Ubuntu 10.10 and i'm attempting to run Cockos Reaper (on WineASIO).:confused:
 I've tried to read otherp osts and do my best before creating this thread.

I downloaded the Deb of WineAsio 0.7.5 found in a thread over here. it installed fine with the Software Center.
I couldn't get the Steinberg SDK - page gives 404 error.

I installed reaper on both wine and Crossover (trial version). I enabled both ALSA and JACK audio drivers in Wine config. WineASIO is not shown in Reaper audio settings :(

Thanks for the help ):P

MarcoHi,
I install reaper in /home/username to save typing cumbersome commands
in future sessions. Blanks in wine command lines need to be filled with *

wine /home/user/.wine/drive_c/Program*Files/Native*Instruments/Absynth*5/Absynth*5.exe

wine reaper375-install.exe

sudo dpkg -i wineasio_0.8.1_32bit.deb

regsvr32 wineasio.dll


In the Reaper menu choose Options -->Preferences

In the panel that opens,  choose
Audio = asio
Device = wineasio

In the winecfg panel, choose alsa, but not jackd

Reaper will autoconnect to jackd, and appear in qjackctl if that is open.

You can redirect the Reaper output to any jackd input connection,
for further fx, recording, or layering with linux sound apps.

Cheers

---


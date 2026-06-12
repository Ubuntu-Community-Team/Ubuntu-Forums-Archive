---
title: "LMMS Crashing"
date: 2010-05-18
forum: Ubuntu Studio
---

### Post by Tahakki on 2010-05-18
I've installed the linux-rt package, and booted into that kernel, but LMMS still crashes giving 'Segmentation Fault'. What's going on?

Thanks.

---

### Post by sgx on 2010-05-18
I try lmms twice a year, buts its always crashed within minutes, but I have never installed it by compiling it from source, and never followed up on the causes of crashes. Hopefully people using it successfully can advise, its an ambitious project. If nothing changes, wine and wineasio
make using Reaper in linux a very solid option.

If you start lmms from a commandline, maybe some of the terminal output will provide a clue. Are the rest of the studio apps running OK?

Cheers

---

### Post by sgx on 2010-05-19
Since I had not tried LMMS v 0.4.4, I installed it in my hybrid rpm distro, and happily, with this version, I chose jackd as the audio interface, and alsa sequencer as the midi device, and was able to load 2 instances of zynaddsubfx, with 2 sounds each, and record the output with timemachine.The lmms record button itself failed to respond.  I was then able to reload the saved project. So things are looking much better.
Audibly better. 8)

I should mention I had real-time turned off when testing.

Cheers

---

### Post by Tahakki on 2010-05-20
Got realtime running and working, but LMMS *still* crashes, even with Jack. Help?

---

### Post by sgx on 2010-05-20
> **Tahakki said:**
> Got realtime running and working, but LMMS *still* crashes, even with Jack. Help?
Hi, the more details you can provide, the better hope you'll have. 
People need to know your computer details, and hardware and software, version numbers of the software involved, the terminal output after the crash, (start it from a terminal, to see this) Does it behave differently in non-RT jackd session? Was the lmms screen displayed before it crashed? Whats the output of commands lspci and lsmod,
Do other audio apps run OK? 
Cheers

---

### Post by Tahakki on 2010-05-20
Other audio apps all run fine.

Whether using Jack or ALSA, the output is the same - 'Segmentation Fault'. That's it.

I'm running 10.04, and I think I have some kind of Intel HD Audio chip. My LMMS version is the latest one from their website, but this also happened in the version in the ubuntu repos.

---

### Post by sgx on 2010-05-21
> **Tahakki said:**
> Other audio apps all run fine.

Whether using Jack or ALSA, the output is the same - 'Segmentation Fault'. That's it.

I'm running 10.04, and I think I have some kind of Intel HD Audio chip. My LMMS version is the latest one from their website, but this also happened in the version in the ubuntu repos.
Bummer. There are quite a number of lmms youtube videos, maybe one shows some configuration stepsthat will help. 

In the meantime, I put a list of things needed for vsts using reaper, in wine and wineasio, here:

[http://ubuntuforums.org/showthread.php?t=1488670](http://ubuntuforums.org/showthread.php?t=1488670)

click the vst button here, for several free synths:

[http://www.ugoaudio.com/](http://www.ugoaudio.com/)

Cheers

---

### Post by sgx on 2010-05-21
I found a ppa with an lmms:

[https://launchpad.net/~tobydox/+archive/ppa/+build/992267](https://launchpad.net/~tobydox/+archive/ppa/+build/992267)

Maybe someone else has one too?

---

### Post by Tahakki on 2010-05-21
What exactly is wineasio?

---

### Post by sgx on 2010-05-21
> **Tahakki said:**
> What exactly is wineasio?

Hi, it is asio driver code to allow ASynchronus Input Output.

Wine is a very basic implementation of windows, so the two
together enable using a few windows audio apps that require
the speed of asio drivers, to achieve  professional recording and playback
quality. wineasio will be detected when you start a windows app
like reaper or cantabile, using the wine command,

wine /home/tahakki/reaper/reaper.exe   for example

In the setup process of reaper, you select wineasio as your asio device, or driver, the exact wording varies between windows apps.

Cheers

---

### Post by Tahakki on 2010-05-22
D'you think Ableton Live would work then?

---

### Post by sgx on 2010-05-22
> **Tahakki said:**
> D'you think Ableton Live would work then?
I doubt any of the big commercial windows DAWs will work. But they all have demos you can try.
Its mainly Reaper, the windows EnergyXT2, and Cantabile for recording. 
I have tested MULAB and Podium briefly just to insure they loaded plugins,
which they did. 

There is another topic here about FL Studio, and it looks promising.
I installed the Reason demo, and it loaded and played its demo song, and responded to mouse and keyboard, but I did not yet attempt a new project.

Cheers

---


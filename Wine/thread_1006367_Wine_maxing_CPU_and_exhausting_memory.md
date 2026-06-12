---
title: "Wine maxing CPU and exhausting memory"
date: 2008-12-09
forum: Wine
---

### Post by eguy on 2008-12-09
Hi,

Are there settings to govern the amount of CPU and memory used by wine?

I am running ubuntu 8.04 Hardy Heron on an IBM thinkpad T23 with 1Gb of RAM.
I need to access a website that requires Internet Explorer 6.  Yesterday I installed wine for Hardy Heron and IEs4Linux.  It all works, but after a while, my computer became unresponsive.  I brought up the System Monitor, and noticed that wineserver and iexplore.exe were maxing the CPU and had gone beyond 1GB and were accessing the swap file.  Also, the fan was running at full blast.  I killed the wineserver process and the CPU returned to the 7 - 25% range, memory returned to about 300Mb, and the fan stepped down to low speed.  I restarted the computer, opened the System Monitor and then started IE 6.  Both wineserver and iexplore.exe begin with a small memory footprint (about 7Mb and 18Mb, respectively), but almost immediately max the CPU and the fan kicks on high.  Without even performing any actions in IE 6, both processes begin to consume memory at the rate of about 1Mb per second, eventually exhausting physical memory and engaging the swap file.  If I quit IE 6, both processes remain in the process list, but iexplore.exe stops consuming additional memory (it doesn't release what it has though) and drops to 0% CPU.  wineserver continues to max the CPU, but consumes memory at a much slower rate, about 0.1 Mb every 5 seconds or so.

Any insights are greatly appreciated.

---

### Post by asdfoo on 2008-12-10
> **eguy said:**
> Hi,

Are there settings to govern the amount of CPU and memory used by wine?

I am running ubuntu 8.04 Hardy Heron on an IBM thinkpad T23 with 1Gb of RAM.
I need to access a website that requires Internet Explorer 6.  Yesterday I installed wine for Hardy Heron and IEs4Linux.  It all works, but after a while, my computer became unresponsive.  I brought up the System Monitor, and noticed that wineserver and iexplore.exe were maxing the CPU and had gone beyond 1GB and were accessing the swap file.  Also, the fan was running at full blast.  I killed the wineserver process and the CPU returned to the 7 - 25% range, memory returned to about 300Mb, and the fan stepped down to low speed.  I restarted the computer, opened the System Monitor and then started IE 6.  Both wineserver and iexplore.exe begin with a small memory footprint (about 7Mb and 18Mb, respectively), but almost immediately max the CPU and the fan kicks on high.  Without even performing any actions in IE 6, both processes begin to consume memory at the rate of about 1Mb per second, eventually exhausting physical memory and engaging the swap file.  If I quit IE 6, both processes remain in the process list, but iexplore.exe stops consuming additional memory (it doesn't release what it has though) and drops to 0% CPU.  wineserver continues to max the CPU, but consumes memory at a much slower rate, about 0.1 Mb every 5 seconds or so.

Any insights are greatly appreciated.

It sounds like you've hit a bug in Wine, the only way to fix it is for a developer to find and fix the bug.

Some things you might try: 

1. using the latest version of Wine (1.1.10) if you haven't yet, it might be fixed in the latest release
2. trying an older release by compiling from source to see if the bug was introduced recently, if it is then you might be able to help find and report it by doing a Regression Test

---

### Post by eguy on 2008-12-10
> **asdfoo said:**
> It sounds like you've hit a bug in Wine, the only way to fix it is for a developer to find and fix the bug.

Some things you might try: 

1. using the latest version of Wine (1.1.10) if you haven't yet, it might be fixed in the latest release
2. trying an older release by compiling from source to see if the bug was introduced recently, if it is then you might be able to help find and report it by doing a Regression Test

Thanks for the reply.  I am using Wine 1.1.10, so I'll try the stable 1.0,1 version.  I don't have any development tools on this computer (it's a temporary until my desktop returns from repairs), so I won't be able to compile from source.

---

### Post by eguy on 2008-12-10
I uninstalled Wine 1.1.10.  I couldn't figure out how to install 1.0.1, so I used the Synaptic Package Manager, which installed version 1.0.  No change in the behavior, though I did notice that if I only run Notepad from Wine's Programs>Accessories>Notepad menu option, wineserver only consumes 1.5 Mb and doesn't grow its memory usage, so I'm thinking the bug is triggered by something in IEs4Linux

---

### Post by asdfoo on 2008-12-10
> **eguy said:**
> I uninstalled Wine 1.1.10.  I couldn't figure out how to install 1.0.1, so I used the Synaptic Package Manager, which installed version 1.0.  No change in the behavior, though I did notice that if I only run Notepad from Wine's Programs>Accessories>Notepad menu option, wineserver only consumes 1.5 Mb and doesn't grow its memory usage, so I'm thinking the bug is triggered by something in IEs4Linux

is it possible to use firefox for the website, but use an addon to fake ie6?

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---


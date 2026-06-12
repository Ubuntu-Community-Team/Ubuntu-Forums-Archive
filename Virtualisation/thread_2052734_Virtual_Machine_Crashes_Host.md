---
title: "Virtual Machine Crashes Host"
date: 2012-09-03
forum: Virtualisation
---

### Post by cactusgal on 2012-09-03
I'm currently running 64 bit Ubuntu Studio 11.04 (don't like the huge dash icons in the newer versions), with a 3 ghz. Pentium Core2 Duo CPU and 4 gbs. of ram. I've installed two different virtualization programs, the version of Virtual Box for my specific OS and VMWare Player. I'm trying to run Windows 7, 64 bit and/or 32 bit as my Windows PC is down right now and I have a job to do using specific Windows programs. Both programs run fine to create the virtual hard disc but, in both, when I try to run it to install the operating system everything freezes and all I can do is turn off the computer. I've Googled this problem and haven't come up with anything useful so I'm hoping someone here can help me.

---

### Post by Dedoimedo on 2012-09-04
Did you try to collect a kernel crash dump to figure out what might be causing the problem?
Dedoimedo

---

### Post by cactusgal on 2012-09-05
> **Dedoimedo said:**
> Did you try to collect a kernel crash dump to figure out what might be causing the problem?
Dedoimedo

Being not the most experienced Ubuntu user, what you said makes sense so I looked it up, followed the instructions here: [https://help.ubuntu.com/12.04/serverguide/kernel-crash-dump.html](https://help.ubuntu.com/12.04/serverguide/kernel-crash-dump.html) including the test, then caused the real crash. Problem is, being that I am rather a newbie (most of the software I need to use requires Windows), I haven't been able to figure out how to access the crash dump file (in Text Editor) as it's locked. I hate to bother busy people but I've Googled it to death and can't seem to find the proper Terminal lines or whatever to open, read and copy/paste it. I realize that a knowledgeable person reading it will likely be able to see right away what the problem is.

I thought perhaps it might be a driver conflict as I have on-board audio but built this computer for my husband for recording and mixing music tracks and installed a special sound card that connects to an external multi-instrument dock (for Windows, but thought it would be a neat challenge to get it working in Ubuntu, on a second hard drive). So I un-installed the default Alsa audio drivers and it still crashed trying to run a virtual machine. Obviously not it.

---

### Post by Dedoimedo on 2012-09-06
You need the crash tool for that.
And kernel debuginfo installed.

Not for the newbies. 

But the fact there is a crash dump indicates a driver conflict of some sort. In the machine settings, there are options to check vt-x, check apic and other settings. Can you try marking them on/off one by one and see what gives.

Dedoimedo

---


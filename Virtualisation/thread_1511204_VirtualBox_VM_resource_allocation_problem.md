---
title: "VirtualBox VM resource allocation problem"
date: 2010-06-16
forum: Virtualisation
---

### Post by Morphaeus on 2010-06-16
VM Details:

```
&#65532;
General Name: XP Pro
OS Type: Windows XP
&#65532;
System

Base Memory: 2500 MB
Processor(s): 2
Boot Order: Hard Disk
VT-x/AMD-V: Enabled
Nested Paging: Enabled&#65532;

Display

Video Memory: 128 MB
3D Acceleration: Enabled
2D Video Acceleration: Enabled

Storage

IDE Controller
IDE Secondary Master (CD/DVD): Host Drive HL-DT-ST DVDRAM GT20L (sr0)
  IDE Primary Master: EVE.vdi (Normal, 20.00 GB)

Floppy Controller

Floppy Device 0: Empty

Audio

Host Driver: PulseAudio
Controller: ICH AC97
&#65532;
Network

Adapter 1: PCnet-FAST III (NAT)&#65532;

Serial Ports

Disabled&#65532;

Shared Folders

Shared Folders: 1
 

```

This setup gives me this error message (see attachment Error.png)

The VM works fine whenever I allocate only 1 processor, but anything more than that and it blows up.

Running 10.04 on an HP laptop with quad core processor. Any idea why I can only use 1 processor?

---

### Post by bodhi.zazen on 2010-06-16
Always nice if you give us details such as what hypervisor you are using, VirtualBox I believe.

As this is a problem with a Windows XP guest using a third party application, I suggest you ask on a Windows forum or on the Virtualbox forum.

"Unknown error" does not mean much.

You could also try to google search that error message.

---


---
title: "3D acceleration"
date: 2015-01-23
forum: Virtualisation
---

### Post by teemu2 on 2015-01-23
Hello!

I am having difficulties getting 3D acceleration to work in Ubuntu. I have tried all possible fixes I found online - and everything is updated (running Ubuntu 14.04 on VirtualBox 4.3.20 with latest GA installed). It seems my GPU is detected as a VGA card, and therefore not allowed the use of 3D acceleration. I think it may be related to the fact that I am running this on a setup with Intel HD Graphics 4500, because another user has a similar issue to me according to [https://01.org/linuxgraphics/node/133](https://01.org/linuxgraphics/node/133)

After all changes I have made and fixes/workarounds, it still looks like this: 


```
h3l1um@h3l1um-VirtualBox:~$ sudo lspci -vvv -nn
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef] (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at <unassigned> [disabled]

```



```
h3l1um@h3l1um-VirtualBox:~$ /usr/lib/nux/unity_support_test -p
libGL error: failed to authenticate magic 5
libGL error: failed to load driver: vboxvideo
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.3


Not software rendered:   d no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       no



```

Does anyone know how to approach this problem? I feel that the ten hours I have spent on this so far has not been worth it, and appreciate any feedback.

Kind regards,
Teemu

---

### Post by teemu2 on 2015-01-27
Hi again

After doing some more research I have found out that this problem remains in all Linux operating systems through VirutalBox. Does the virtual machine also need graphic drivers to be installed perhaps? Once again, I'm open to guesses.
Since it's confirmed this is more relatable to VirtualBox than Ubuntu I understand the thread may be in the wrong section and I can't find an appropriate place for it. If a moderator could move it I'd be thankful.

Kindly,
Teemu

---

### Post by ajgreeny on 2015-01-28
Your particular problem is one reason why using Windows in VB is no use at all for any extreme graphics programs, eg games that normally play fine on Windows will probably not work in VB.

You will probably have noticed in the VM settings that the maximum graphics memory you can set is only 128MB, and the default, if I remember correctly, is only 4MB until you move the slide setting fully right to 128.

I have no idea if other virtualization applications, eg Vmware-player is any better in this respect; I have used only VB.

---

### Post by redger on 2015-02-26
KVM is your best bet for Windows VMs with accelerated graphics 
[http://ubuntuforums.org/showthread.php?t=2266916&p=13235295#post13235295]("http://ubuntuforums.org/showthread.php?t=2266916&p=13235295#post13235295")
[https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")

---

### Post by TheFu on 2015-02-28
> **redger said:**
> KVM is your best bet for Windows VMs with accelerated graphics 
[http://ubuntuforums.org/showthread.php?t=2266916&p=13235295#post13235295]("http://ubuntuforums.org/showthread.php?t=2266916&p=13235295#post13235295")
[https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")

It is unclear to me if the OP installed the guest additions properly or not OR
if the video RAM for the VM has been maxed out in the virtual machine settings OR
if the video settings for 3D have been checked in the virtual machine settings.

All three are needed and all are for the guest, not the hostOS.  The lspci isn't important - after showing there is a GPU installed.

Running a stock system with virtualbox compared to all the hoops needed to get VGA passthru working with KVM or XEN is a big difference.  Rebuilding a kernel isn't something everyone wants to do, lots of systems don't support IOMMU or have 2 graphics cards.  Those are big caveats worth mentioning when suggesting VGA passthru.

---


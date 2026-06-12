---
title: "Boot ubuntu from VHD - any ideas how to set it up?"
date: 2013-09-12
forum: Virtualisation
---

### Post by michel-moalem on 2013-09-12
Hi there all - have bought a new laptop with windows 8 on - planning to dual boot with ubuntu on a new ssd drive - after a bit of reading on the net it seems that a better solution will be to have both OSs as VHDs and boot from them directly - the flexibility it offers me is that i can always mount one OS within another using virtualbox or vmlite if i need quick access without rebooting...
it looks like its possible to do it but while there are a lot of howtos on windows cant find a good guide on installinga dn booting ubuntu on a vhd...
can anyone here help?
cheers
michel

---

### Post by lukeiamyourfather on 2013-09-12
It goes the other way around typically, you use physical disks for the operating systems and boot the virtual machines or native from the physical disks. If you want to boot both Windows and Linux from virtual disks you need a hypervisor so any operating system running is always a virtual machine, but you might lose a lot of functionality by doing that (for example 3D accelerated graphics).

---

### Post by michel-moalem on 2013-09-12
Thanks for the reply but i think what i am looking for is possible without loosing performance (3d performance is not too important to me)
what i figured till now is that you can boot win7 or win 8 from vhd without a host operating system - ie have the vhd on a bare drive and boot from the vhd as if it is a physical disk
 (see links:
[http://www.nextofwindows.com/windows-7-vhd-native-boot-without-any-hosting-operation-system/](http://www.nextofwindows.com/windows-7-vhd-native-boot-without-any-hosting-operation-system/)
[http://www.johnpapa.net/bootoffmetal/](http://www.johnpapa.net/bootoffmetal/))
and a bootable ubuntu vhd was made back in 2010: [http://www.sevenforums.com/virtualization/77618-linux-vhd-boot-made-possible.html](http://www.sevenforums.com/virtualization/77618-linux-vhd-boot-made-possible.html) but the only image i found was ubuntu 10.04 so need help creatin a bootable 13.04 vhd...

---

### Post by lukeiamyourfather on 2013-09-12
That sounds like a terrible idea to me. It would be writing *everything* to a huge file with a virtual file system on an actual file system. At the very least it's going to affect disk performance and it might come back to bite you down the road if you're trying to recover files or troubleshoot. Good luck with it if that's the route you take, let us know how it works in the long run.

---

### Post by Kevin_Arnold on 2013-09-12
The best bet really would be something similar to what I have on my Mac. I have OS X and Windows both installed directly on the drive. When I'm in OS X, though, I can just open up VMWare and boot windows as a VM directly from the disk. Best of both worlds!

---

### Post by michel-moalem on 2013-09-13
Ok - been looking more into this now and it doesnt look good - the idea is sound and been endorsed by many for running multiply windows installations -  google 'windows boot from vhd' - multiply windows run directly from vhd with no performence hit... the problem is that it seems like a microsoft technology by the look of it - the reference to ubuntu i have seen was using a bios emulator from vmlite - vboot - but this was not as efficient and seems to be a dead project...
so unless anyone can correct me on this than we will have to wait for linux to catch up...

---

### Post by lukeiamyourfather on 2013-09-16
You're expecting Linux to be like Windows so do yourself and everyone else a favor by erasing that from your brain forever because they are different (and that's a good thing!). This is why Microsoft created the feature for Windows.
 
> Enterprise environments already managing and using .vhd files for virtual machine deployment will get the most benefit from the native-boot VHD capabilities.

[http://technet.microsoft.com/en-us/library/hh825689.aspx](http://technet.microsoft.com/en-us/library/hh825689.aspx)

So unless you're deploying it on hundreds/thousands of machines there's no point in using a VHD or the baggage it comes with for that convenience. Linux already has ways to easily deploy on hundreds/thousands of machines so booting from a VHD is kind of a moot point. The feature might make it to Linux eventually but right now it seems like a solution in search of a problem.

Based on what you've written here my guess is you've never used Linux before and you shouldn't let this stop you. Just make multiple partitions to dual boot and try it out. If you don't like Linux then you can remove the partition from the disk manager in Windows and expand the partition to the rest of the drive to get back to where you started.

---

### Post by Orsogg on 2014-06-09
No! No! No! and again No!
<snip>

The idea of michel-Moalem is really good :-)
It's easy to manage different VHDx's with a multi-boot-manager.

The entire hard drive (or partition) is thereby managed almost without any loss in speed of a single file. These files can also be copied or backedup easily.

The questions of michel-moalem be only as follows: First, how does Ubuntu (by the way, the best Linux distribution for me ) to be installed on a VHDx-partition.
And secondly, can I then boot directly from the boot menu?

With Windows 7, Windows 8, MS Server 2008 and MS Server 2012 this works flawlessly. I have already successfully installed Ubuntu on various devices. And I think there's also a possible solution for this question.

Let's see what can be achieved there.

PS: Sorry for my bad english but I usually speak German :-)

---

### Post by TheFu on 2014-06-09
VHD files are a microsoft technology.  I vaguely recall it being possible only on Enterprise and Ultimate releases of Windows - not Pro or Home.  Anyway - it is a cool idea and limited to MS-centric situations - at least that is my understanding.

There are vHDDs in Linux too - .vdi, .raw, .qcow, .qcow2, and vmdk files.  These can all be booted inside a hypervisor, but not directly from the BIOS ... er ... since BIOS doesn't know what to do with it.  

If you want to run multiple Linux systems quickly, there are many options.
* jails
* containers (openvz, lxc, UML, ....)
* paravirtual VMs - Xen
* Whole machine VMs (virtualbox, VMware, Xen, KVM, QEMU, ... )
Some of these support vHDDs, direct partition passthru and/or direct hardware passthru - like passing the PCIe controller hardware thru to the guest OS.  Specific hardware support (usually VT-d, BIOS and kernel) is required to make this work.  It is extremely fast AND very flexible.

IMHO - and it is just an opinion - running 1 OS at a time on hardware is a home-user thing.  Enterprise servers almost always run 5-30 VMs per physical machine these days.

Different OS with different philosophies and different design points.  That doesn't make 1 idea any less valid than some other idea, just less used. There are times when having a VHD may have been useful to me, but it wasn't an easy-to-deploy option on my systems, so other alternatives were used.

There are some people running Windows inside Xen VMs with GPU passthru claiming native GPU performance for high-end games.  The requirements to make that work are extremely specific, however.  BIOS, CPU, specific video cards. The Virtualization forum here has more details.

---

### Post by Pnin on 2015-04-13
> **Orsogg said:**
> The idea of michel-Moalem is really good :-)

It's easy to manage different VHDx's with a multi-boot-manager.

The entire hard drive (or partition) is thereby managed almost without any loss in speed of a single file. These files can also be copied or backedup easily.
Sorry to revive an old thread, but I mostly concur with **Orsogg** on this, plus I wanted to add some info here -- I re-registered expressly for that. :idea:

I've been following this path for quite sometime, but up to now results have been pretty unsatisfactory from the Linux side. This has nothing to do with Linux shortcomings, as it was booting from file from back in the day (e.g., check this 2004 article from the *Linux Gazette*: [http://linuxgazette.net/109/chirico.html](http://linuxgazette.net/109/chirico.html)).

Prior discussions here at Ubuntuforums reveal there was once a ready-made appliance from *VMLite* (see [http://ubuntuforums.org/showthread.php?t=1452018](http://ubuntuforums.org/showthread.php?t=1452018); sadly it's severely obsolete by now), and a *non sequitur* question about a "*vmlinuz for booting from vhd*" ([http://ubuntuforums.org/showthread.php?t=2069515](http://ubuntuforums.org/showthread.php?t=2069515)).

Let's be clear about what we're trying to achieve here: it's fairly easy to achieve a working installation of Windows (v7 and up) to a VHD file, even from so called "bare metal" (the most popular tutorial for this being the one found at [http://www.johnpapa.net/bootoffmetal/](http://www.johnpapa.net/bootoffmetal/)); while an easy and straightforward solution for doing this to any flavor of Linux is unknown to date.

Let's be clear: **[COLOR="#B22222"]we're not trying to run Linux in a virtual machine under Windows[/COLOR]** -- the goal here is to multiboot Windows and Linux, without having to physically partition the hard drive they'll be residing in, and getting the extra benefit of an extremely simplified system disk backup and restoration.

To do that, VHD looks like it would be the easiest way; unfortunately, the only (and barely qualifying) route seems to involve the fading **WUBI** utility (as detailed in this *Superuser.com* answer: [http://superuser.com/questions/33535/can-i-boot-linux-from-a-vhd#306928](http://superuser.com/questions/33535/can-i-boot-linux-from-a-vhd#306928))...

The main objection I have seen raised time and again is that this is a feature of the Windows bootloader, so it isn't available for booting Linux -- but for that to hold any water, it should be proven that it can't be done by chaining bootloaders as usual in many other setups, **GRUB** and **GRUB4DOS** being the prime targets for it.

Sadly, my Linux skills are pretty limited, especially in what concerns the boot up process, so I can't offer further help other than making available whatever research I have on the topic and the general conviction this is possible (dang, *VMLite* did it, right?). Any further help/pointers/clues would be more than welcome...

---


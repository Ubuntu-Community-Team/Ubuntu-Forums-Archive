---
title: "using an installed Windows 8 on a dual boot set up to also run in a virtual machine"
date: 2013-03-28
forum: Virtualisation
---

### Post by gtippitt on 2013-03-28
I just bought an HP 2000 laptop with an AMD E-300 APU and 4GB RAM.  It had Win8 pre-installed.  I installed Ubuntu 12.10 along side for dual boot setup.  I've had some minor problems with GRUB and Win8's UEFI disk format, but have it working okay now.  GRUB configured everything fine, but the first time Win8 downloaded updates, it took over the UEFI boot setup again.  I can swap it temporarily by changing BIOS boot selection during POST.  I must hit F9 and select Ubuntu otherwise WIN8 starts (minor nuisance).

I have a couple of apps that must have real windows because of DRM on materials I download from my local library.  I would like to config Ubuntu to run Win8 as a virtual guest.  I've read where people have gotten Win7 without UEFI to work with Ubuntu 12.04.  They set up a fake virtual drive that points to the real Win7 disk partition and Win7 will work as either a virtual guest or dual boot using the same Win7 partition.  I've tried to follow the same idea with Win8 and Ubuntu 12.10, but have not been able to get it to work.

I don't know if the reason I can't get it to work is the Win8 UEFI, something else in Win8, or something else in Ubuntu 12.10, or I'm stupid and set it up wrong.

I'm fairly experienced with Ubuntu but have not used virtual machines.   I've not used Windows much since Win2K.  Can anyone tell me if they have this set up working or not, so I don't waste time if it simply won't work.  If it will work and you can point me in the direction of some good instruction, I don't mind reading the F(ine) manuals, but don't know where to start looking.  The sticky "Virtualization Mega thread" has a short bit about using a windows partition, and it looks easy with QEMU-KVM without UEFI.  I've read the stuff about now mounting anything double to avoid cache FUBARs.

I started trying VirtualBox first because others had gotten the dual boot and virtual combined thing to work with it on the prior versions of both OSs.  I'm willing to try  VMWare, VirtualBox, Xen, QEMU, or other.  I don't need it to run streaming video, just ebooks and audio books with DRM, so high performance isn't a big deal as long as the virtual client doesn't clobber my Ubuntu system.

My BIOS settings have an option to turn on virtual machine support, which I have done.  I run BOINC under Ubuntu, and it recognizes that the virtual machine support is turned on in the BIOS settings.

Thank you for any help or warnings of pitfalls to avoid.
Greg

---

### Post by oldfred on 2013-03-28
Post #11 discusses virtual install.

[http://ubuntuforums.org/showthread.php?t=2130132](http://ubuntuforums.org/showthread.php?t=2130132)

---

### Post by gtippitt on 2013-03-28
Okay .... ? I'm not sure what that has to do with my question much other than his Desktop machine was an HP and Laptop was an HP and we both use Windows and Ubuntu.  He has a Win8 Dual Booting with Ubuntu 12.04lts and separate copy of Win7 running in a VirtualBox.  

I am asking about having a single copy of Win8 which was pre-installed and is dual booting with Ubuntu 12.10.  I want to run a Virtual guest under Ubuntu 12.10 that will run the copy of Win8 that is already in the /dev/sda4 partition.

Thanks,
Greg

---


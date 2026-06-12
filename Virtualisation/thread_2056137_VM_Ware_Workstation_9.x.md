---
title: "VM Ware Workstation 9.x"
date: 2012-09-10
forum: Virtualisation
---

### Post by Welly Wu on 2012-09-10
I have a System76 Lemur Ultra Thin (lemu4) and I use Ubuntu 12.04.1 64 bit Long Term Service as my primary operating system of choice. I purchased and installed VM Ware Workstation 8.0.4 64 bit, but I find it very annoying that I will have to download and run a third-party unofficial patch every time VM Ware updates Workstation 8.x 64 bit for GNU/Linux platforms periodically. I have a Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 guest virtual machine installed in Oracle VM Virtualbox 4.1.22 64 bit currently.

VM Ware recently released Workstation 9 for Microsoft Windows XP, Vista, and 7 along with GNU/Linux. According to the release announcements and the requirements, it offers support for Ubuntu 12.04.x 32 and 64 bit as both the host and guest operating system. I am thinking about upgrading to Workstation 9 which will cost me $119.99 USD, but I have some questions before making that purchasing decision.

1. Does anyone here use VM Ware Workstation 9 with Ubuntu 12.04.1 64 bit Long Term Service as the host operating system? If so, then will it install and function properly right out of the box without requiring any user intervention such as resorting to third-party unofficial patches to compile the Linux kernel 3.2.0.x to get the VMNet module to install properly or other issues?

2. If you had VM Ware Workstation 8.x 64 bit, then what are the differences that you noticed with VM Ware Workstation 9.x 64 bit with Ubuntu 12.04.1 64 bit Long Term Service as the host operating system? Is it fully compatible? Is it faster? Does it support Microsoft Windows 7 64 bit Aero with all of the special effects such as Aero Snap, Aero Peek, and Jump Lists?

3. What other things do you note about VM Ware Workstation 9.x 64 bit that I should consider as a part of my decision making process?

4. Are there any known problems for my given usage scenario that I should be aware of?

Thank you.

---

### Post by Welly Wu on 2012-09-10
Here is a brief and official VM Ware YouTube video describing the new features in Workstation 9.0.0 64 bit:

[https://www.youtube.com/watch?v=PQ5Z5sG2wZ4](https://www.youtube.com/watch?v=PQ5Z5sG2wZ4)

I just downloaded and I installed VM Ware Workstation 9.0.0 64 bit for Ubuntu 12.04.1 64 bit Long Term Service GNU/Linux. I had absolutely no problems whatsoever with anything. I am following a guide to convert my Oracle VM Virtualbox .VDI disk image into a VMWare Workstation .VMDK disk image:

[http://scottlinux.com/2011/06/24/convert-vdi-to-vmdk-virtualbox-to-vmware/](http://scottlinux.com/2011/06/24/convert-vdi-to-vmdk-virtualbox-to-vmware/)

It should work properly. If so, then I will post another follow up reply to my own thread to let people know about VM Ware Workstation 9.0.0 64 bit and how I like it compared to version 8.0.4 64 bit later tonight.

Fingers crossed!

---

### Post by Welly Wu on 2012-09-10
The ScottLinux guide is not working properly.

I decided to launch Oracle VM Virtualbox and I decided to make a copy of my Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 guest virtual machine, but I specified that the target disk image would be a .VMDK file on my Western Digital My Passport 2.0 TB USB 3.0 Portable hard disk drive. It is a 54 GB 64 bit guest virtual machine. It is taking a long time to copy the .VDI to a .VMDK file right now. I think that I am going to have to stay up late tonight to see how it goes.

I hope that this approach will work. I will find out soon enough later tonight.

---

### Post by Welly Wu on 2012-09-11
This helped me a lot:

[http://blog.laksha.net/2009/10/how-to-create-virtual-machine-using.html](http://blog.laksha.net/2009/10/how-to-create-virtual-machine-using.html)

---

### Post by Welly Wu on 2012-09-11
To summarize:

1. I used Oracle VM Virtualbox to make a duplicate copy of my Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 guest virtual machine and I specified that it should convert the .VDI to a .VMDK file onto my Western Digital My Passport 2.0 TB USB 3.0 hard disk drive.

2. I made a duplicate copy of my Virtualbox VMs folder onto my Western Digital My Passport 2.0 TB USB 2.0 Portable hard disk drive

3. I copied the .VMDK files back onto a VMs folder on my Crucial M4 2.5" SATA-III 6 GB/s MLC NAND FLASH 128 GB Solid State Drive

4. I followed the Laksha.Net guide to create a custom Microsoft Windows 7 64 bit guest virtual machine within VM Ware Workstation 9.0.0 64 bit

It works!

Now, I have to play with VM Ware Workstation 9.0.0 64 bit to enable 3D graphics hardware acceleration and some other stuff.

---

### Post by Welly Wu on 2012-09-11
Things are coming along better and more smoothly for me now. I enabled  VT-x hardware acceleration and set it to automatic mode. I also install  VMWare Tools.

I still keep getting an error message stating that  3D graphics hardware acceleration is not enabled because VM Ware  Workstation 9 is having a problem with my OpenGL 2.1. I am not sure what  this means, but I am not getting 3D graphics hardware acceleration  right now. I did install driconf and I enabled S3T textures, but that did not solve my problem thus far. I know that it is still early so I will have to be patient before I learn how to enable my Intel 3rd Generation "Ivy Bridge" Core i5-3210M with the Intel HD Graphics 4000 for 3D graphics hardware acceleration using OpenGL 2.1 at a future date and time.

VM Ware Workstation 9.0.0 64 bit is extremely fast especially on current generation PC hardware and software. I am going to stick with Ubuntu 12.04.x 64 bit Long Term Service so that nothing breaks in the next 1.5 years from today. I will also upgrade to a future VM Ware Workstation version when Canonical releases Ubuntu 14.04.1 64 bit Long Term Service sometime in August 2014. I will also purchase a brand new System76 high end notebook PC and I plan to spend up to $2,500.00 USD for it. It will have everything that I want in terms of PC hardware and operating system and software applications.

In the meantime, I am enthusiastic about VM Ware Workstation 9.0.0 64 bit. It is fully compatible with Ubuntu 12.0.4.1 64 bit Long Term Service and it is extremely fast. The speed and performance is blistering fast. It is much much faster than Oracle VM Virtualbox 4.1.22 64 bit by several orders of magnitudes higher.

---

### Post by Welly Wu on 2012-09-17
I was having a problem with Ubuntu 12.04.1 64 bit LTS and Linux kernel 3.2.0-30 generic so I contacted System76 and they told me to upgrade to Linux kernel 3.3.6-030300 generic. Previously, I was having random system freezes and lock ups whenever I ran more than 4 software applications at the same time. After I upgraded, this problem disappeared entirely. I also learned to disable the Cocoon add-on for Mozilla Firefox Aurora 17.0a2 as this caused my web browser to crash randomly and repeatedly every 15 minutes or so. This solved the problem entirely too.

VM Ware Workstation 9.0.0 64 bit is features rich. I haven't turned on encryption yet, but I am thinking about doing that tonight so that I can try out the new restrictions features to qualify who can change what configuration settings for my guest virtual machines. As it stands right now, I have enabled ecryptfs to encrypt my /home and /swap partitions with the default Ubuntu 12.04 LTS installation and all of my external storage devices and mediums use LUKS encryption. I don't want to ruin performance too drastically and I want the convenience of being able to launch my guest virtual machines without having to enter a password to unlock it, but I tend to focus on security more than convenience so I may just as well encrypt my guest virtual machine anyway.

VM Ware Workstation 9.x 64 bit is fully compatible and it fully supports Microsoft Windows 8 Pro 64 bit. I plan to pay Microsoft Corporation $39.99 USD to upgrade on October 26th, 2012. As I have a new System76 Lemur Ultra Thin (lemu4) with an Intel 3rd Generation "Ivy Bridge" Core i5-3210M CPU with VT-x and AES-NI, VM Ware Workstation 9.x 64 bit supports these hardware technologies along with my Crucial M4 2.5" SATA-III 6 GB/s MLC NAND FLASH 128 GB Solid State Drive too. The performance penalty should not be too noticeable to encrypt my guest virtual machine.

I have not tried the Unity feature yet, but I may do so tomorrow afternoon to see how it works. As it stands right now, I am extremely happy with VM Ware Workstation 9.x 64 bit and it is heads and shoulders above Oracle VM Virtualbox 4.2 64 bit.

If you have a choice and you can afford it, then I highly recommend VM Ware Workstation 9.x 64 bit for Ubuntu 12.04.x 64 bit LTS. Everything will work right out of the box with little to no user intervention. There is no need to apply an unofficial third-party patch to compile the Linux kernel 3.5.x to make the VMNet module work. It is a great combination.

---

### Post by Welly Wu on 2012-10-04
[http://askubuntu.com/questions/181829/how-to-fix-3d-acceleration-for-vmware-workstation-9/](http://askubuntu.com/questions/181829/how-to-fix-3d-acceleration-for-vmware-workstation-9/)

This is how to enable 3D graphics hardware acceleration in VM Ware Workstation 9 64 bit on Ubuntu 12.04.1 64 bit LTS.

---

### Post by sonnet on 2012-10-06
Interesting thread.
I'm conducting some testing myself, to see the loss in performance when running games within vmplayer 5.0 (which uses the same engine and drivers than workstation 9).

So far I'm positevily impressed.

I'm currently testing with windows 8 as host and windows 7 as guest (***but i think guest performance shouldn't be different whether you run the machine on a windows or linux host.. or am I wrong?***).

Testing machine is:
cpu i5-2550
gpu nvidia gt 520
Both Host and guest reside on the same SSD.

So far I have done those test:

Devil May Cry 4
Native (windows 8 host) : 43.7 (average of the 4 scenes)
Windows 7 guest: 37

Street Fighter IV

Native (windows 8 host) : 52.9
Windows 7 guest: 47.2

Unigine 1.2 Tropic:
Native (windows 8 host) : 17.8/449
Windows 7 guest: 17/429


I'm not been able to run Resident Evil 5 benchmark: screen becomes black.
It would be nice if others might report their test/experience/benchmarks.
So it seems that as long as the game can be run, it's realistic to expect between 80%-95% of native performances.

---

### Post by Welly Wu on 2012-10-07
If you use Ubuntu 12.04.x 64 bit LTS as the host, then 3D graphics hardware acceleration will not be supported unless you have a PC with a discrete GPU and the appropriate graphics drivers installed. So far, I have not been able to get it to work properly on any guest virtual machine be it Windows 7 64 bit or GNU/Linux or BSD.

The thing about VM Ware Workstation 9.0.0 64 bit is the fact that it only supports Linux kernel 3.4.0-1. If you install a GNU/Linux distribution with Linux kernel 3.5.x or higher, then it will stop working properly.

Oracle VM Virtualbox does not have these sorts of problems insofar as my testing has indicated thus far. Direct3D support does not work with Windows 7 64 bit guest virtual machines properly though.

---


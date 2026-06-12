---
title: "Windows server 2008 64 bit"
date: 2008-07-23
forum: Virtualisation
---

### Post by silentbob1978 on 2008-07-23
Hi

I have installed the latest version of ubuntu server 64bit and also vmware server 2.0. They are both working fine. THe problem comes when I try to virtualise windows server 2008 64 bit.

My settings are correct when I create the virtual machine (i think) but when it begins the setup I get the error message - attempting to load a 64 bit application, however this CPU is not compatible with 64 bit mode.

My PC is compatible with 64bit as even the unbuntu software is 64bit. Plus I have instaleld server 2k8 on it before with no issues

Help

---

### Post by sversteeg on 2008-10-14
Hi,

Did you find a solution to this problem?  I am having the exact same issue as you describe.

Cheers.

> **silentbob1978 said:**
> Hi

I have installed the latest version of ubuntu server 64bit and also vmware server 2.0. They are both working fine. THe problem comes when I try to virtualise windows server 2008 64 bit.

My settings are correct when I create the virtual machine (i think) but when it begins the setup I get the error message - attempting to load a 64 bit application, however this CPU is not compatible with 64 bit mode.

My PC is compatible with 64bit as even the unbuntu software is 64bit. Plus I have instaleld server 2k8 on it before with no issues

Help

---

### Post by lazyart on 2008-10-14
Check your settings for the VM itself and be sure you specified a 64 bit OS.

---

### Post by cynthia387 on 2008-10-14
Microsoft Web Deployment Tool 64 can be used on Windows Server 2008 and Internet Information Services 7.0 as well as Windows Server 2003 and Internet Information Services 6.0. Please note that this is a Beta 1 release of the tool. As with any pre-release tools or software, you should always backup your system before using it.
---------------
cynthia jacquline

[promoters]("http://www.drivenwide.com")

---

### Post by sversteeg on 2008-10-14
Hi Lazyart,

Thanks for the reply.  Yes, I've specified 64-bit Windows 2008 as the OS for the VM.  I've tried two ways.  One is to copy a Windows 2008 VM from my Mac OS X box (where it runs on VMWare Fusion and it works) to VMWare Server 2 on the Ubuntu machine.  The other way was to create a new VM from scratch on the Ubuntu machine, again specifiying 64-bit Windows 2008 as the OS.  In both cases this message appears when I try to start the VM:

> File: \windows\system32\boot\winload.exe

Status: 0xc000035a

Info: Attempting to load a 64-bit application, however this CPU is not compatible with 64-bit mode.


From the console on Ubuntu:
> > uname -a
Linux alligator 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux

---

### Post by sversteeg on 2008-10-14
Found the answer on this forum:
[http://communities.vmware.com/thread/140515](http://communities.vmware.com/thread/140515)

Needed to shut down the host machine and explicitly enable virtualisation in BIOS.  This is apparently necessary for 64-bit VMs to work but apparently not for 32-bit VMs (which were working before.)

---


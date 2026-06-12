---
title: "64bit as guest in Virtualbox"
date: 2008-03-21
forum: Virtualisation
---

### Post by caver1 on 2008-03-21
I have 64bit Gutsy installed on an Amd64 x2 dual core with the 64bit version of Virtualbox. Running 32bit guests with no problem. I have tried to load both 64 bit win xp and 64 bit Hardy Heron beta as guests with no luck. I keep getting the error message that no 64 bit system detected so cannot load 64 bit guest get i386 version. 
Is it that you cannot run a 64 bit os guest or is there something I am missing?[/I]
caver1

---

### Post by dacorr on 2008-03-21
virtual box and VMware do not support 64bit guests as of yet just 64bit hosts

Dac

---

### Post by fjgaude on 2008-03-21
> **dacorr said:**
> virtual box and VMware do not support 64bit guests as of yet just 64bit hosts

Dac

This is simply not true; **VMware serve**r handles both Linux and Windows 64-bit guests quite well.

---

### Post by caver1 on 2008-03-22
Thanks. I just wanted to make sure I wasn't missing something.
caver1

---

### Post by vniksic on 2008-10-13
I'd like to bump this thread again.

Where are we standing on this? I'm using a 64bit Hardy Heron. I can't run the 64 bit version of intrepid ibex. It keeps complaining that it requires a 64 bit cpu to run. 64 bit guest OS-es are still unsupported?

---

### Post by darco on 2008-10-14
Try VM Workstation, it handles 64bit fine..My host is Mint x32 and one of my guest is Mint x64.
VM WS also supports USB 2.0, full screen w/o pulling your hair out,has 3D support for Windows, excellent file sharing between Host/Guest.
Unity is just awesome.....
Its a great app!

darco

---

### Post by Valok on 2008-10-14
Are there any free to use alternatives that allow a 64 bit guest?  The only windows disc I have is a 64 bit and I would really like to get rid of the partition.  But I need to have the backup just in case.

---

### Post by reader4 on 2008-10-28
vniksic et al.: You probably need to enable hardware virtualization through your BIOS.  If that is not an option, you are out of luck (like me), since VirtualBox only supports a 64-bit guest OS if the CPU offers hardware virtualization.  Most newer processors do, but my 3-yr-old Xeons do not, so it's not a given.

---

### Post by colinlr on 2008-10-29
There is a free download (iso) to boot off that will tell you if your box can run 64 bit vm's

[http://download3.vmware.com/software/wkst/VMware-guest64check-5.5.0-18463](http://download3.vmware.com/software/wkst/VMware-guest64check-5.5.0-18463)

---

### Post by jurgen32 on 2008-11-20
In yhe newest Virtualbox [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads") your able to install a 64bit guest.
But only if your cpu allow this.
Firts you have to start VB and than you'r gonna make a virtual disk for the guest os.
Before you start installing go to the setting of the virtual hd.
Go to **general/advanced** en check **enable _VT_-x/AMD-V**
After this your able to install a 64bit os.... that what I'm doing on this moment... installin openSUSE 11 64bit.

Regards 
Jurgen

[apologeet]("http://www.apologeet.nl")

---

### Post by bodhi.zazen on 2008-11-20
VBox is built on qemu, and what jurgen32 is talking about is using the same technology as KVM 

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

To test your CPU , enter this command in a terminal :

```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
```If you see any output, with either "vmx" or "svm" (in red) in the output you should be good to go.

_Note_: You may need to enable this technology in your BIOS.

---

### Post by mobee on 2009-07-28
I am trying to install VMWare esxi 64 bit as a guest inside virtual box.
Needless to say that VMWare do not like to be installed as guests.
I used Generic Linux machine with 2.6 kernel, it seems like the installation freeze at some point.
Any idea ?


It seems to be a bug in virtualbox but they have an assertion failure while trying to install VMWare esx 3.5

---

### Post by bodhi.zazen on 2009-07-28
As far as I know you can not run VMWare within Virtualbox.

---


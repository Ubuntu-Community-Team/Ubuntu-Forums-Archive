---
title: "VM unable to login"
date: 2019-11-22
forum: Virtualisation
---

### Post by satimis on 2019-11-22
Host - Ubuntu 18.04
VM - Ubuntu 18.04
VirtualBox

VM (newly installed) - unable to login.  It freezes.

```

User
not listed 
```

This happens after installing virtualbox-guest-x11 because copy/paste not working between host and vm. 

Advanced
Shared Clipboard: [Bidirectional]     # already selected
Drag'n'Drop:  [Bidirectional]      # already selected

I have reinstalled VM twice with same result.

Please help.  Thanks

Regards
satimis

---

### Post by ajgreeny on 2019-11-22
What version of virtualbox are you using?

I have never used the ***virtualbox-guest-x11*** package in a guest so I can't comment on that; I have always added the extension-pack to the virtualbox package which I install from the Oracle repos as shown in the ***Debian-based Linux distributions*** section at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads), currently on VBox-6.0.14.

What resources does you host have and what have you allocated to the guest?
What graphics-controller have you set in the VM's display settings?  All Linux guests should use VMSVGA if using the latest VBox version, but not sure about that if you're still on VBox-5.2.32.

---

### Post by satimis on 2019-11-22
> **ajgreeny said:**
> What version of virtualbox are you using?

I have never used the ***virtualbox-guest-x11*** package in a guest so I can't comment on that; I have always added the extension-pack to the virtualbox package which I install from the Oracle repos as shown in the ***Debian-based Linux distributions*** section at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads), currently on VBox-6.0.14.

What resources does you host have and what have you allocated to the guest?
What graphics-controller have you set in the VM's display settings?  All Linux guests should use VMSVGA if using the latest VBox version, but not sure about that if you're still on VBox-5.2.32.
Motherboard - Ausu PRIME X570-P
CPU - AMD Ryzen 5 3400G

VirtualBox 6.0

Graphic comes from CPU

Have tried VBoxVGA/VMSVGA

Quit difficult to set resolution if selecting VMSVGA.  The screen is very small.  Haven't tried VBoxSVGA.  Screen resolution 1920x1080.  

I followed "Why doesn't clipboard sharing work with Ubuntu 18.04 LTS inside VirtualBox 5.1.26?"
[https://superuser.com/questions/1318231/why-doesnt-clipboard-sharing-work-with-ubuntu-18-04-lts-inside-virtualbox-5-1-2](https://superuser.com/questions/1318231/why-doesnt-clipboard-sharing-work-with-ubuntu-18-04-lts-inside-virtualbox-5-1-2)
to install virtualbox-guest-x11.

extension-pack already installed on host

According to my recollect I came across similar problem before, unable to copy/paste between host/VM

I have another Ubuntu 18.043 VM running without problem.  But its storage size is only 10G unable to install Anaconda, complaint not sufficient storage space.

Regards
satimis

---

### Post by satimis on 2019-11-23
Hi all,

Problem solved as follow;

Created a new Ubuntu 18.04 VM. (copy/paste not working)

On Terminal run;

$ sudo apt update
$ sudo apt install linux-headers-$(uname -r) build-essential dkms

-> Devices -> Insert Guest Additions CD Image ......

Then following window popup;
```

VBox_GAs_6.0.14" contains software intended to be automatically started.  Would you like to run it?
if you don't trust this location or aren't sure, press Cancel.
[Cancel]    [Run] 
```
-> Run

After installation finished rebooted VM.  That is all.  Now copy/paste between Host and VM is working.

One thing I couldn't resolve I have no CD inserted but the Guest Addition ISO was there.  Why ?????

Then I installed Anaconda and it took sometime to finish.  The installation was not so straight forwards.

I'll install IBM Qiskit later for learning Quantum Computing.

Thanks

Regards
satimis

---


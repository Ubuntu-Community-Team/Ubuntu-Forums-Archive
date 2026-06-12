---
title: "Virtualbox and USB Drive"
date: 2011-12-17
forum: Virtualisation
---

### Post by ClinkerMC on 2011-12-17
Hi there,

I'm a brand new, wide eyed, naive Ubuntu user so please be patient with any lack of technical details.

I'm looking for some help getting my usb thumb drive to work with a virtual machine in Virtualbox. I'm running Ubuntu 11.10. I've added my username to vboxusers as directed by the virtualbox manager when I went into settings. I've checked this by running 'id' command in terminal and I can see my vboxusers listed as one of the groups.

The problem that I'm having is when I click on the usb icon at the bottom of virtual machines window and tick the pendrive I get the following error message:
[I]
[SIZE=2]Could not find "/media/PENDRIVE" 
The location is not a folder.[/SIZE][/I]

Is adding my username to vboxusers group the only step involved in making this work? Any help greatly appreciated!

---

### Post by haqking on 2011-12-17
> **ClinkerMC said:**
> Hi there,

I'm a brand new, wide eyed, naive Ubuntu user so please be patient with any lack of technical details.

I'm looking for some help getting my usb thumb drive to work with a virtual machine in Virtualbox. I'm running Ubuntu 11.10. I've added my username to vboxusers as directed by the virtualbox manager when I went into settings. I've checked this by running 'id' command in terminal and I can see my vboxusers listed as one of the groups.

The problem that I'm having is when I click on the usb icon at the bottom of virtual machines window and tick the pendrive I get the following error message:
[I]
[SIZE=2]Could not find "/media/PENDRIVE" 
The location is not a folder.[/SIZE][/I]

Is adding my username to vboxusers group the only step involved in making this work? Any help greatly appreciated!

you need virtual box version not in the repos, you need the extensions pack and your username in the vboxusers group.

then just choose it from devices menu of the bottom

you can also add a filter if you have major issues


cheers

---

### Post by howefield on 2011-12-17
> **haqking said:**
> you need virtual box version not in the repos,...

This used to be the case, but no longer as I understand.

There used to be two versions of VirtualBox, an OSE (Open Source Edition) which could be downloaded via the Ubuntu Software Centre or Synaptic Package Manager ect, which didn't include closed source options such as being able to use USB.

To get USB functionality, you needed to get the PUEL (Personal Use & Evaluation Licence) version from the virtualbox website. This edition included the closed source code giving you several features not available to the OSE version.

For some time now, there has been only one edition (akin to the OSE version) to which you add the extension pack downloaded from the virtualbox website to make it akin to the what was previously the PUEL version.

Basically, it no longer matters how you got virtualbox, just install the extension pack ect ect.

---

### Post by haqking on 2011-12-17
> **howefield said:**
> This used to be the case, but no longer as I understand.

There used to be two versions of VirtualBox, an OSE (Open Source Edition) which could be downloaded via the Ubuntu Software Centre or Synaptic Package Manager ect, which didn't include closed source options such as being able to use USB.

To get USB functionality, you needed to get the PUEL (Personal Use & Evaluation Licence) version from the virtualbox website. This edition included the closed source code giving you several features not available to the OSE version.

For some time now, there has been only one edition (akin to the OSE version) to which you add the extension pack downloaded from the virtualbox website to make it akin to the what was previously the PUEL version.

Basically, it no longer matters how you got virtualbox, just install the extension pack ect ect.


ahh ok gotcha.  good to know its changed.

Cheers

---

### Post by ClinkerMC on 2011-12-17
Still having problems but in actual fact the drive is appearing in device manager on virtual machine (Windows Server 2008 ) with yellow exclamation. Doesn't seem to pick up drivers for it. I've definitely physically connected it to Server 2008 machines with no problems.

Any other suggestions?

---

### Post by haqking on 2011-12-17
> **ClinkerMC said:**
> Still having problems but in actual fact the drive is appearing in device manager on virtual machine (Windows Server 2008 ) with yellow exclamation. Doesn't seem to pick up drivers for it. I've definitely physically connected it to Server 2008 machines with no problems.

Any other suggestions?

Well thats a Windows driver issue and not VM then, if its seen in the VM then the rest is down to Windows

Yellow exclamation in Windows is a driver problem, download the driver for your device

---

### Post by Rebelli0us on 2011-12-22
I think you need to install the "virtual box extension pack" for usb to work. When guest is using USB host can't see it, and vice versa (or so it seems). Also guest USB access (MB/sec) is very slow in my experience.

---

### Post by haqking on 2011-12-22
> **Rebelli0us said:**
> I think you need to install the "virtual box extension pack" for usb to work. When guest is using USB host can't see it, and vice versa (or so it seems). Also guest USB access (MB/sec) is very slow in my experience.

That was already mentioned in post 2, and the OP posted after that saying still having issues.

If it is seen in Windows which it is then the extensions pack is working, a yellow exclamation mark is a driver issue in Windows itself

---


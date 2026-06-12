---
title: "VirtualBox: XP Guest doesn't shutdown"
date: 2011-11-23
forum: Virtualisation
---

### Post by mikegior on 2011-11-23
Hello all,

I'm experiencing an issue with my Windows XP Pro guest in VirtualBox (version 4.1.2_Ubuntu r38459) where if I attempt to shutdown the XP guest, it will proceed to say "Windows is shutting down" but seems to hang there forever to which I'll need to give VBox a little push my invoking a reset (which isn't healthy). I do have the guest additions installed on the guest OS. The host OS is Ubuntu 11.10 64-bit (up to date), and if it matters the hardware is a HP Compaq 6910p.

My question is, has anyone experienced this? And if so is there a solution?

**UPDATE:** Also, I have a Windows 7 Pro 64-bit guest and this issue does not occur on it. Maybe it was the XP installation?

---

### Post by haqking on 2011-11-23
> **mikegior said:**
> Hello all,

I'm experiencing an issue with my Windows XP Pro guest in VirtualBox (version 4.1.2_Ubuntu r38459) where if I attempt to shutdown the XP guest, it will proceed to say "Windows is shutting down" but seems to hang there forever to which I'll need to give VBox a little push my invoking a reset (which isn't healthy). I do have the guest additions installed on the guest OS. The host OS is Ubuntu 11.10 64-bit (up to date), and if it matters the hardware is a HP Compaq 6910p.

My question is, has anyone experienced this? And if so is there a solution?

**UPDATE:** Also, I have a Windows 7 Pro 64-bit guest and this issue does not occur on it. Maybe it was the XP installation?

Check the logs in XP and the virtual box logs for more information.

Does it do the same with a ACPI shutdown from the machine menu ?

Anyways chcek the logs first.

---

### Post by mikegior on 2011-11-23
ACPI shutdown appears to have worked; what is the difference between shutting down in XP or telling VBox to invoke an ACPI shutdown? Also, what should I be looking for specifically in either logs?

---

### Post by ubupirate on 2011-11-23
I also experienced this issue, and it was only present with an XP guest.

Can't tell if it is XP, Virtualbox or the Guest additions.

For you, does it only do it once and then shutdown fine from then on? The first shutdown/restart I did on XP guest invoking from within the OS hanged, but every shutdown/restart after that worked like it should.

---

### Post by mikegior on 2011-11-23
> **ubupirate said:**
> For you, does it only do it once and then shutdown fine from then on? The first shutdown/restart I did on XP guest invoking from within the OS hanged, but every shutdown/restart after that worked like it should.

Any time I invoked a shutdown from within Windows XP, it would hang. I tried doing the ACPI shutdown as someone mentioned and that worked. 

I just tried shutting down from within Windows XP and it worked on its own. Up until I did the ACPI shutdown, it would always hang; odd.

I supposed this is deemed solved.

---

### Post by Perryg on 2011-11-23
There was an issue with the absolute pointer device being active in the guest settings that would cause this issue.  You can disable that if you have the guest additions installed (in the guest) and do not need the tablet drivers or upgrade to the latest version of VirtualBox where this has been fixed. Or at least version 4.1.4

---

### Post by JKyleOKC on 2011-11-26
I have a number of XP Pro VMs installed on this machine, which stay in the "saved" state most of the time. I only start one when I need to use it, and then save it via the "X" box's dialog to "save state" when I'm done.

When I do a Windows update that requires a restart, most of them do the restart automatically with no intervention. One of them, however, experiences the infinite hang at "Windows is shutting down" and I have to use Reset to force it to restart.

At first I was quite nervous about doing this, since aborting in the middle of a write-to-disk of the VDI file could destroy the virtual disk. I have had that happen on another system and full recovery was not possible.

However after watching the action closely, I've found that the disk activity indicator at the bottom of the VBox screen stops flashing red after about 90 seconds, indicating no more disk writes. In addition, my mouse pointer changes from the XP one back to the Linux pointer (I have them configured totally differently) indicating that the VBox software is no longer active although the screen has not changed and the "Machine" menu still works. I can then use "Reset" and all seems well.

I suspect a race condition is responsible for this. I'm still running version 3.2.12 here; Version 4 didn't seem to offer anything but more eye candy so I've not changed my production systems.

---

### Post by Perryg on 2011-11-27
The only other issue I can remember that caused XP to hang at shutdown was the audio driver.  Older versions (like the one you have) were helped by switching to sound blaster or disabling the sound if not required.

---


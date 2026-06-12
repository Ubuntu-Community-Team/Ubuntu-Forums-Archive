---
title: "Virtualbox."
date: 2018-03-13
forum: Virtualisation
---

### Post by timpl on 2018-03-13
This thread sounds very similar to the problem I am experiencing:

This is a Mac host running Virtual box running a Ubuntu guest.  The following error is produced after the first log-in after a fresh startup:

"**Network Service Discovery Disabled**"

"Your current network has a local domain which is not recommended and incompatible with the Avahi network discovery.  The Service has been disabled."

**The configs are**:

Mac OS 10.13.3
VirtualBox Version 5.2.8 r121009 (Qt5.6.3)
Ubuntu LTS 16.04
Memory:	1.9 GigaB
Processor: Intel® Xeon® CPU ES-1620 v2 @ 3.70GHz x 2
Graphics:	llvmpipe (LLVM 5.0, 256 bits)
OS type:	64-bit
Disk:	       18.9 GB

I have tried reinstalling both VirtualBox and Ubuntu but the same error persists.  My guess is that the error is from Ubuntu but in response to an oddity in the VirtualBox environment.

Tim Powys-Lybbe

---

### Post by howefield on 2018-03-13
Post moved to its own thre3ad to avoid hijacking another members thread.

---

### Post by hrsetrdr on 2018-03-13
Re-installing and hoping doesn't solve the problem, it only repeats it.     

Question:  Eventhough the Ubuntu VM is throwing a "Network Service Discovery Disabled" message, have you tried to hit the Internet in a web browser?

Take a look at this thread: [https://ubuntuforums.org/showthread.php?t=2353783](https://ubuntuforums.org/showthread.php?t=2353783)


You mentioned running virtualbox on a Mac, perhaps this article pertains to your situation:  [https://raselkhan.me/2015/08/how-can-i-fix-network-service-discovery-disabled/](https://raselkhan.me/2015/08/how-can-i-fix-network-service-discovery-disabled/)

---

### Post by cruzer001 on 2018-03-13
Try different virtualbox network settings, bridged may work.

[ATTACH=CONFIG]278932[/ATTACH]

---

### Post by timpl on 2018-03-13
Excellent.  Solved.  Many thanks.

Tim

---


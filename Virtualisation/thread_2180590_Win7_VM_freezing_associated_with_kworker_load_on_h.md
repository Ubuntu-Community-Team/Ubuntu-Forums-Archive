---
title: "Win7 VM freezing associated with kworker load on host ubuntu 12.04"
date: 2013-10-13
forum: Virtualisation
---

### Post by Lachele on 2013-10-13
I originally posted about this to the VirtualBox forums and then as a VirtualBox bug ticket.  But, it occurs to me that it might be an Ubuntu and/or kernel thing.  So, I'm copying the post here. 

Original, detailed, post to VirtualBox forums:   [https://forums.virtualbox.org/viewtopic.php?f=7&t=57477](https://forums.virtualbox.org/viewtopic.php?f=7&t=57477)

VirtualBox bug ticket:  [https://www.virtualbox.org/ticket/12175](https://www.virtualbox.org/ticket/12175)

The following is most of the bug ticket text, repeated here for convenience.

64-bit Windows 7 VM hosted on 64-bit Ubuntu 12.04.


The VM freezes up within a few minutes of boot (5 minutes to 20 or so). I can usually re-size the display (e.g., to/from full-screen) with varying success, but the display stops changing, and input from the keyboard and mouse is not registered. Once, after a freeze, audio streaming from the internet continued to work. I haven't been able to test the latter for reproducibility.


It has frozen at least once when the VM was running very limited graphics, during a hard drive check pre-boot.


Not only does the VM freeze, but VirtualBox also becomes unresponsive. It must be killed from within the host operating system. Just after freezing, I can choose from the VirtualBox menu to power off the machine, but it doesn't work. After that, VirtualBox no longer responds to anything at all.


At the moment it freezes, two kworker processes in the host, specficially kworker/u:3 and kworker/u:2, also begin to occupy 100% and 50% CPU, respectively (1.5 procs of a quad-core). The increased kworker load persists until the host machine is rebooted, even if all VirtualBox processes have been killed.


This behavior first appeared associated with a Windows update. Specifically, it seemed to be associated with "Update for Windows7 for x64-based Systems (KB2868116)". However, the relationship might be coincidental because the VM worked for a while after that update was finally applied. But, it has started freezing again. I tried reverting the VM to before the most recent update, but it still freezes.


I attached the log to the VirtualBox ticket.


Please let me know anything else I can do to help fix this.

---


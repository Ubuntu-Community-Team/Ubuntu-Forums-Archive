---
title: "Virtualbox - 100% usage on 1 core (core2duo) - Ubuntu 8.10 host, Clarkconnect 4.3"
date: 2009-02-26
forum: Virtualisation
---

### Post by AndyBBB on 2009-02-26
'm experiencing 100% utilisation on one of my CPU cores (2nd) when the guest OS is idle. This is reported by htop.

Host OS: Ubuntu 8.10
Guest OS: Clarkconnect 4.3
Virtualbox: 2.1
CPU: Core 2 Duo 4400 (2ghz)

It seems to be a reported issue across a few platforms based on some googling. I've been over this thread [http://forums.virtualbox.org/viewtopic.php?t=5511](http://forums.virtualbox.org/viewtopic.php?t=5511) and tried setting the affinity for the Virtualbox process, but this simply transfers the 100% CPU load from the 2nd core to the 1st core.

I've installed htop on the Clarkconnect guest and confirmed that its idling and not using allocated RAM (no swap being used).

I've seen this bug ticket logged [http://www.virtualbox.org/ticket/1233](http://www.virtualbox.org/ticket/1233) which is a similar issue however I'm experiencing 100% load on one core, rather than just higher than expected 20-30%.

Yet to try ACPI/Vt-x settings as ive seen suggested elsewhere - will try these when I get home.

Looking for some help/ideas to sort this one?

---

### Post by lairdre on 2009-11-02
I have almost the same problem with Virtualbox going to 100% utilzation on Ubuntu 9.10. I was on the previous version of Ubuntu for months and did not have this problem. I just upgraded to Virtualbox 3.0.10, and have the same problem. I assume it is an Ubuntu kernel issue? 

Sorry, Ubuntu 9.10 is the guest, the host is XP

Ron

---

### Post by xxicrimsonixx on 2009-11-02
Make sure that you have virtualization enabled in BIOS if your CPU supports it, because if your CPU does not support virtualization, then it ends up taking a huge amount of processor power.

---


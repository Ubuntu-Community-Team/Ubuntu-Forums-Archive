---
title: "VirtualBox prevents host OS from hibernating"
date: 2013-03-10
forum: Virtualisation
---

### Post by Rebelli0us on 2013-03-10
My host is Linux OS, guest is Windows 2000, XP or 7. Suspend works fine, but hibernation fails and session is returned to the login prompt. I noticed that bug was filed 2+ years ago. Is there a workaround?

---

### Post by meteorrock on 2013-03-11
Hibernation works fine for me on my Windows 7 64 bit Host. Using virtualbox 4.2.8 inside the ubuntu 13.04 GUEST and on the Windows 7 host. Might want to upgrade your virtualbox to the newest if you haven't. I get the Windows login screen after walking away for a few minutes. Check the settings in the Windows 7 host for the standby time in the display. Or upgrade your ubuntu build, you did not give specifics on your builds.

---

### Post by Rebelli0us on 2013-03-13
Thank you. Switching the network adapter form "Bridged" to "NAT" and back again fixed the problem. 

Aslo, I noticed that running one or more VMs slows down hibernation/resume time, otherwise it's about 15 sec. to login, impressive for a laptop.

---


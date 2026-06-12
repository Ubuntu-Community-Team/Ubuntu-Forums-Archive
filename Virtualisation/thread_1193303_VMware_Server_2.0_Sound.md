---
title: "VMware Server 2.0 Sound"
date: 2009-06-21
forum: Virtualisation
---

### Post by mastermindg on 2009-06-21
I'm running Jaunty - 9.04 x86-64.

Guest - Windows XP - VMware Server 2.0 Build 128374.

I'm able to get sound fine from /dev/dsp on startup but the sound gets disconnected mid-session:

***Failed to open sound device /dev/dsp: Device or resource busy Sound will be disconnected.***

How can I release /dev/dsp and reestablish connectivity with the VmWare console without restarting the guest?

---

### Post by mastermindg on 2009-06-21
Nevermind. I just logged into web access, clicked on audio and then choose Connect.

---


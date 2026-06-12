---
title: "Sound stops working in Ubuntu in VM Workstation after remote-desktop to windows host"
date: 2013-06-21
forum: Virtualisation
---

### Post by doesntcount on 2013-06-21
I'm running Ubuntu 12.04 in VMWare Workstation 7.0. Everything works great except that, consistently, when I remote desktop to the Windows host, sound stops working in the Ubuntu guest. It immediately begins working as soon as I logout of my session. Ie. as soon as I see the login screen, I hear the ubuntu drum roll.

I'm interested in either a fix or a work-around where I can perhaps reload the driver or something after I find that sound isn't working.

I'm also willing to help debug the issue and get to root cause if someone would like to provide me with some debugging suggestions.

Thanks.

---

### Post by TheFu on 2013-06-21
Seems that "Workstation" is providing an exclusive lock on the audio resources.  I haven't used Workstation in years, so I don't know if this is tunable.  I would ask this question on the VMware Workstation forums and be extremely specific about which OS is the host and which is the client and what virtual audio device your hostOS is presenting to the clientOS.

Sorry that I don't know the answer.

---


---
title: "Virtualbox causing x-server crash and booted back to login screen"
date: 2010-10-24
forum: Virtualisation
---

### Post by Nick Payne on 2010-10-24
I've just today upgraded Ubuntu 10.04 amd64 to 10.10, then re-enabled the VB repository ```
http://download.virtualbox.org/virtualbox/debian maverick
``` and upgraded Virtualbox to 3.2.10. When I start Virtualbox, and before I get a chance to start any VM, a second or two after the VB window appears the entire screen goes black, then the X-server restarts and I'm back at the logon screen.

Via Synaptic, I uninstalled virtualbox-3.2 and installed virtualbox-ose, but virtualbox-ose had exactly the same problem, so I uninstalled that and reinstalled virtualbox-3.2, but the problem still persists. Any ideas on a fix? Uninstall/reinstall hasn't fixed it and the problem is still the same after a reboot. No other applications that I've used since the upgrade to 10.10 have shown any problem.

---

### Post by Nick Payne on 2010-10-24
Well I've found the problem is Xinerama, or some interaction between Xinerama and something else. I'm running dual monitors as separate X screens with Xinerama. If I disable Xinerama the crash doesn't happen. 

However, that's not a viable solution because I then can't drag app windows between monitors, and I can't run Twinview because one of the monitors is rotated 90 degrees to portrait mode and AFAIK I can't rotate one monitor except by having it as a separate X screen.

---

### Post by zackboll on 2010-11-27
Bump, any solutions on this problem?  BTW, it is not only VirtBox that crashes xserver in Ubuntu 10.10, Quanta Plus does the same thing with Xinerma enabled.

Thanks,
Zack

---

### Post by Nick Payne on 2010-11-27
A fix is apparently now in the Maverick proposed repository. See [https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed") on how to enable this.

---


---
title: "Wierd APM issue? on new Serval system.."
date: 2008-09-08
forum: System76 Support
---

### Post by 0x69 on 2008-09-08
A friend of mine recently purchased a Serval Performance laptop (Ubuntu 8.04). I suggested System76 to him as an alternative to purchasing a laptop with Vista, or Windows for that matter..

Anyway.. The problem appears to be an APM issue, though Im not sure, the computer seems to stall and the drive stops after about 30 seconds to a minute of inactivity and doesn't start again until activity on the touchpad/mouse. This happens both during boot and during regular usage while logged in.

I've experimented and the boot screen will sit there basically indefinitely until I move the mouse. I tried updating all the packages via apt-get and during the process the computer would stall as described, the ETA countdown would freeze, after activity on the touchpad/mouse it starts again and the ETA counter starts climbing to hours (though quickly counted down as the download continues).

I'm an experienced ubuntu user and I've definitely never seen anything like this on any system laptop/desktop/server..

---

### Post by 0x69 on 2008-09-08
After investigating dmesg I found the following errors. First the mouse error and then the wireless error, both would repeat..

psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away

iwl4965: Microcode SW error detected.  Restarting 0x2000000.

Installing linux-backports-modules-hardy-generic seems to have fixed the problem.. ([http://ubuntuforums.org/showthread.php?p=4691359](http://ubuntuforums.org/showthread.php?p=4691359)) However I'm still experimenting.

---


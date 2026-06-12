---
title: "VirtualBox - How to fix?"
date: 2010-02-02
forum: Virtualisation
---

### Post by Kvothe on 2010-02-02
I installed VirtualBox for the second time, and this time it asked for virtualbox-ose-modules, so I install that. It asks me to reboot, done. XServer is screwed up. Start in recovery mode, use xfix, problem solved. Start up Ubuntu, drivers gone, music won't play, things like that. Restart, go to grub boot screen. Two Ubuntu boot options. This one has my internet driver, but not my graphics card. Can someone please explain these peculiarities, why they happened, and how to get rid of them? I've removed virtualbox-ose and virtualbox-ose-modules.

---

### Post by Kvothe on 2010-02-02
I may have downloaded the wrong kernel number for virtualbox-ose-modules, would that be it? I have 2.6.24-19-generic and I chose virtualbox-ose-modules-2.6.24-26-generic when installing. But how do I fix what damage has been done?

---

### Post by tripolitan on 2010-02-02
boot into the version with internet driver, apt-get update, apt-get remove virtualbox-ose-modules-2.6.24-26-generic and any other modules that you've installed. Reboot. If you have a functioning system, start over installing the proper modules. Keep in mind, there is a small chance that xfix may have changed your original (working) video setup.

Update virtualbox to the latest version, install the matching kernel module (I think I had to run a command that automatically compiles the modules)

---


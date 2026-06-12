---
title: "Upgraded to ubuntu 18.04 from 17.10, gnome-shell crashes on startup"
date: 2018-04-25
forum: Ubuntu Development Version
---

### Post by dankegel on 2018-04-25
Filed [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1766938](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1766938)

I have a fleet of Dell T7500's, a few Dell 3620's, a Skull Canyon, and a Hades Canyon, and a few other odds and ends, running a mix of ubuntu 16.04 and 17.10.

On one of the T7500 ubuntu 17.10 boxes (nvidia 340 package, Quadro K5000 card),
I did sudo "do-release-upgrade -d".  Went fine, but on reboot, the desktop would
come up for about ten seconds, then the system would shut down.
Doing
  while ! ssh badbox sudo systemctl set-default multi-user.target; do echo foo; done
until it succeeded at least got the machine stable.

Removing the proprietary driver with
  sudo apt remove --purge nvidia-340 nvidia-opencl-icd-340 nvidia-settings nvidia-384 nvidia-opencl-icd-384 nvidia-prime  libcuda1-340
and updating the system didn't help.

startx from multi-user.target is a nicer way to trigger the problem, as then the system remains up.
Installing lwm, and a .xinitrc that started an xterm, let startx succeed, and
the system was stable running firefox, so it's not an obvious graphics problem.

---

### Post by monkeybrain20122 on 2018-04-25
Why don't you just backup your data and do a fresh install? A lot faster and even if problem persists you can rule out cuffs from old settings as the culprit? "Upgrade" is not reliable esp if you have third party software or have some non trivial customization. The only reason I could think of to "upgrade" instead of clean install is you want to keep your non trivial customization but then upgrade is most likely fail, therefore upgrade is completely useless.

---

### Post by dankegel on 2018-04-25
I am preparing to do a fresh install on a different machine to rule out the upgrade path as the problem.

I tested the upgrade path intentionally despite that being riskier precisely to look for problems in upgrading.  Users do expect it to work.

---

### Post by zika on 2018-04-26
> **monkeybrain20122 said:**
> therefore upgrade is completely useless.Beg to differ. Just have done several upgrades on "complicated machines" and it worked much better than before. There is stuff to do after it (due to specific use of those machines) but it is well thought and delivered in 18.04. 

> **dankegel said:**
> Users do expect it to work.And it does... ;) Great work Ubuntu...

---


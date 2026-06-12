---
title: "HOWTO: Reduce VirtualBox CPU Load on Idle"
date: 2008-10-04
forum: Virtualisation
---

### Post by edmondt on 2008-10-04
Running on VirtualBox 1.6 and 2.0 Gave me the same problem: Even when the VM (XP Pro) is idle it still consumes 20%~30% CPU.

It has been bugging me for some time until I found that if you disable **Intel 82801FB/FMB USB2 Enhanced Host Controller -265C** under Universal Serial Bus Controller solves the CPU problem.

Also Disabled CDROM For the sake of it :)

Hope it works for you too!

---


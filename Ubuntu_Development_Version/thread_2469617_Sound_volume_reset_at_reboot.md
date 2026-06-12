---
title: "Sound volume reset at reboot"
date: 2021-12-03
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-12-03
After reboot sound volume is always the same (about 70%) also if at previous boot was manually set at different level. 
I set sound volume to ZERO with settings > sound or status menu (top right)
reboot: now sound volume is about 70%
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1953052](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1953052)

---

### Post by pqwoerituytrueiwoq on 2021-12-04
Not a issue in kubuntu

Operating System: Kubuntu 22.04
KDE Plasma Version: 5.23.4
KDE Frameworks Version: 5.88.0
Qt Version: 5.15.2
Kernel Version: 5.16.0-051600rc3-generic (64-bit)
Graphics Platform: X11
Processors: 12 × AMD Ryzen 5 3600 6-Core Processor
Memory: 15.6 GiB of RAM
Graphics Processor: Radeon RX 580 Series

---

### Post by pqwoerituytrueiwoq on 2021-12-05
It looks like if i restart sddm this happens, but not on reboot, odd

---

### Post by corradoventu on 2021-12-06
qddm?

---

### Post by pqwoerituytrueiwoq on 2021-12-06
wait did i forget the name and type it wrong.. yep, still getting used to some of the names with this DE gdm and lightdm i am familiar with
** sddm

---

### Post by sgage on 2022-01-01
For what it's worth, I have the same issue (running with MATE). It always boots to 74% volume.

Perhaps related... I have a command in rc.local to turn off  'auto power save' on my sound card, because that feature cause annoying loud 'pops' as it times out or whatever. This is no longer 'sticking'. I can confirm that rc.local is running, but by the time I get to the desktop, auto power save is back on. So it seems the whole sound system is being reinitialized/reset fairly late in the boot process.

[edited to add: The auto power save feature is also turned back on upon return from sleep/suspend. But the volume is not reset to 74%.]

---

### Post by sgage on 2022-01-28
It seems like this has been fixed? I hadn't used Jammy in nearly a week, booted up and sound was 74%. Picked up a load of updates today, including a new kernel, so I rebooted. Sound was at 14%, right where I'd left it. I looked through the apt log and didn't see anything upgraded that was obvious (to me). Anyway, try getting all updated and see if the problem is solved for you.

---

### Post by corradoventu on 2022-01-29
I still have the problem, volume is reset at about 70% also when i insert headset.

---

### Post by sgage on 2022-01-29
> **corradoventu said:**
> I still have the problem, volume is reset at about 70% also when i insert headset.

Strange. Definitely working properly here - I've been through several reboots. Again, for the record, I am using MATE.

---


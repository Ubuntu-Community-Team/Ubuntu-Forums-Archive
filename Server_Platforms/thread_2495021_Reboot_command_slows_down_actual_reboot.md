---
title: "Reboot command slows down actual reboot"
date: 2024-02-04
forum: Server Platforms
---

### Post by Heeter on 2024-02-04
Hi all,

I am putting into service and new headless KVM server, to replace my current headless KVM old hardware.

I finished installing Ubuntu 22 LTS onto the server (Dell720, RAID10, EUFI)

I am beginning my initial configurations and I noticed that when I type in the reboot command, the actual reboot is very slow, the 720 BIOS progress bar moves incredibly slow.

If I am to shutdown, and boot from power button, it boots normal speed.

Is there something that I did incorrectly? Maybe non-eufi install instead?

Regards

---

### Post by The Cog on 2024-02-04
Try "shutdown now". Just "shutdown" sends a one minute warning to all users and waits for a minute.

---

### Post by Heeter on 2024-02-04
> **The Cog said:**
> Try "shutdown now". Just "shutdown" sends a one minute warning to all users and waits for a minute.

Hi

'shutdown" "shutdown now" "reboot" all exhibits the same behavior. The bootup is extremely slow. During this really slow Dell progress bar reboot, I press the power button to shutdown immediately, then press the power button again and it boots at a normal speed.


Regards

---

### Post by LHammonds on 2024-02-04
Take the guesswork out of it.

Run these commands to see what is taking up most of the time when booting up.

```
systemd-analyze blame
systemd-analyze critical-chain
```

Once you identify the ones with the longest boot time, drill into their logs and find out what the issue is...which will help you determine the exact solution to fix it.

When I setup Ubuntu Server 22.04, I noticed a slightly longer boot time than I wanted and kept removing the things that were slowing it down until the boot time was somewhere around 8 seconds or so.  The biggest slowdown for me was cloud-init and snapd...both of which I was not going to use.   [Reference post](https://ubuntuforums.org/showthread.php?t=2475667).

LHammonds

---

### Post by Heeter on 2024-02-05
> **LHammonds said:**
> Take the guesswork out of it.

Run these commands to see what is taking up most of the time when booting up.

```
systemd-analyze blame
systemd-analyze critical-chain
```

Once you identify the ones with the longest boot time, drill into their logs and find out what the issue is...which will help you determine the exact solution to fix it.

When I setup Ubuntu Server 22.04, I noticed a slightly longer boot time than I wanted and kept removing the things that were slowing it down until the boot time was somewhere around 8 seconds or so.  The biggest slowdown for me was cloud-init and snapd...both of which I was not going to use.   [Reference post](https://ubuntuforums.org/showthread.php?t=2475667).

LHammonds


Thank you for this heads up and much thank you's for the great reference post.

Since this is just a KVM holding server, I too will be removing the cloud-init and the snap crap. Optional:true will be added to netplan as well.

Thank you for  the great help.

---

### Post by Heeter on 2024-02-08
I figured out what was happening, it was eufi that was the culprit, I disabled eufi and reinstalled 22LTS, and it now reboots and boots at a normal speed.

---


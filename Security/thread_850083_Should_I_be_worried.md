---
title: "Should I be worried?"
date: 2008-07-05
forum: Security
---

### Post by cjv8888 on 2008-07-05
I ran a rkhunter on the system and found this.
What should I do?

> [20:59:33] Performing filesystem checks
[20:59:33] Info: Starting test name 'filesystem'
[20:59:33] Info: SCAN_MODE_DEV set to 'THOROUGH'
[21:00:00]   Checking /dev for suspicious file types         [ Warning ]
[21:00:00] Warning: Suspicious files found in /dev:
[21:00:00]          /dev/shm/pulse-shm-3905468554: data
[21:00:01]   Checking for hidden files and directories       [ Warning ]
[21:00:01] Warning: Hidden directory found: /dev/.static
[21:00:01] Warning: Hidden directory found: /dev/.udev
[21:00:01] Warning: Hidden directory found: /dev/.initramfs

---

### Post by brian_p on 2008-07-05
> **cjv8888 said:**
> I ran a rkhunter on the system and found this.
What should I do?

Ignore it. Read the rkhunter documentation. Do a search on 'rkhunter' in this  forum.

Edit: Just spotted this. It looks informative.

[http://ubuntuforums.org/showthread.php?t=774783](http://ubuntuforums.org/showthread.php?t=774783)

---


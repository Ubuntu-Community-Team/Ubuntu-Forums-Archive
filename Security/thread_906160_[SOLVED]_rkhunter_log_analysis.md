---
title: "[SOLVED] rkhunter log analysis"
date: 2008-08-31
forum: Security
---

### Post by lovinglinux on 2008-08-31
Could someone tell me if this is something I should worry about and why?

[05:11:39] Performing filesystem checks
[05:11:39] Info: Starting test name 'filesystem'
[05:11:39] Info: SCAN_MODE_DEV set to 'THOROUGH'
[05:11:53]   Checking /dev for suspicious file types         [ Warning ]
[05:11:53] Warning: Suspicious files found in /dev:
[05:11:53]          /dev/shm/pulse-shm-1089702965: data
[05:11:54]   Checking for hidden files and directories       [ Warning ]
[05:11:54] Warning: Hidden directory found: /etc/.java
[05:11:54] Warning: Hidden directory found: /dev/.static
[05:11:54] Warning: Hidden directory found: /dev/.udev
[05:11:54] Warning: Hidden directory found: /dev/.initramfs

Any info will much appreciated.

---

### Post by rogeriopvl on 2008-08-31
That's false positives. Nothing to worry about ;)

---

### Post by lovinglinux on 2008-08-31
Thank you

---


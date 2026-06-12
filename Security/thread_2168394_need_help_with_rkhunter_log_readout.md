---
title: "need help with rkhunter log readout"
date: 2013-08-17
forum: Security
---

### Post by nazaroo2 on 2013-08-17
I ran rkhunter after following the install and setup from the rkhunter page.

Only got some warnings about files, and this is what the end of the .log file looks like:
```

[15:28:29] Performing filesystem checks
[15:28:29] Info: Starting test name 'filesystem'
[15:28:29] Info: SCAN_MODE_DEV set to 'THOROUGH'
[15:28:29]   Checking /dev for suspicious file types         [ Warning ]
[15:28:29] Warning: Suspicious file types found in /dev:
[15:28:29]          /dev/shm/pulse-shm-1122854912: data
[15:28:30]   Checking for hidden files and directories       [ Warning ]
[15:28:30] Warning: Hidden directory found: /etc/.java
[15:28:30] Warning: Hidden directory found: /dev/.udev
[15:28:30] Warning: Hidden directory found: /dev/.initramfs
[15:28:30] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[15:28:30] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text
[15:28:59]
[15:28:59] Info: Test 'apps' disabled at users request.
[15:28:59]
[15:28:59] System checks summary
[15:28:59] =====================
[15:28:59]
[15:28:59] File properties checks...
[15:28:59] Files checked: 136
[15:28:59] Suspect files: 0
[15:28:59]
[15:28:59] Rootkit checks...
[15:28:59] Rootkits checked : 242
[15:28:59] Possible rootkits: 0
[15:28:59]
[15:28:59] Applications checks...
[15:28:59] All checks skipped
[15:28:59]
[15:28:59] The system checks took: 2 minutes and 32 seconds
[15:28:59]
[15:28:59] Info: End date is Sat Aug 17 15:28:59 EDT 2013
```

Is that normal?  And if not, should I check those files, and what am I to look for?

thanks in advance
Nazaroo2

---

### Post by Soul-Sing on 2013-08-18
please take a look here: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

---


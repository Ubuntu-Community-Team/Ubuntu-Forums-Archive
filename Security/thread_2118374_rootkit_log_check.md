---
title: "rootkit log check"
date: 2013-02-21
forum: Security
---

### Post by Blindandtoothless on 2013-02-21
Does anything look here suspicious?..
```
 
[22:19:29] Info: Starting test name 'filesystem'
[22:19:29] Performing filesystem checks
[22:19:29] Info: SCAN_MODE_DEV set to 'THOROUGH'
[22:19:29]   Checking /dev for suspicious file types         [ Warning ]
[22:19:29] Warning: Suspicious file types found in /dev:
[22:19:29]          /dev/.udev/rules.d/root.rules: ASCII text
[22:19:29]   Checking for hidden files and directories       [ Warning ]
[22:19:29] Warning: Hidden directory found: '/etc/.java'
[22:19:29] Warning: Hidden directory found: '/dev/.udev'
[22:19:29] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[22:19:34]
```
Thank you. :-0
There are a couple of skipped checks like:
```
[22:19:21] Info: Test 'hidden_procs' disabled at users request.
[22:19:21]
[22:19:21] Info: Test 'suspscan' disabled at users request.
```
And,
```
[22:19:27] Info: Test 'packet_cap_apps' disabled at users request.
[22:19:34] Info: Test 'apps' disabled at users request.
```

---

### Post by Soul-Sing on 2013-02-21
Is it a rkhunter scan? Try this information first: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

---


---
title: "Do I need to be concerned?"
date: 2010-02-09
forum: Security
---

### Post by Morimando on 2010-02-09
I just let rkhunter and chkrootkit scan my system and there were some warnings:
```
[19:04:29] Performing filesystem checks
[19:04:29] Info: Starting test name 'filesystem'
[19:04:29] Info: SCAN_MODE_DEV set to 'THOROUGH'
[19:04:29]   Checking /dev for suspicious file types         [ Warning ]
[19:04:29] Warning: Suspicious file types found in /dev:
[19:04:29]          /dev/shm/pulse-shm-1362868244: data
[19:04:29]          /dev/shm/pulse-shm-56710735: data
[19:04:29]          /dev/shm/pulse-shm-3965609604: data
[19:04:29]          /dev/shm/pulse-shm-3831638392: data
[19:04:29]          /dev/shm/pulse-shm-4188378302: AmigaOS bitmap font
[19:04:29]          /dev/shm/ecryptfs-morimando-Private: ASCII text
[19:04:29]          /dev/shm/pulse-shm-2105635657: data
[19:04:29]   Checking for hidden files and directories       [ Warning ]
[19:04:29] Warning: Hidden directory found: /etc/.java
[19:04:29] Warning: Hidden directory found: /dev/.udev
[19:04:29] Warning: Hidden directory found: /dev/.initramfs
```

Whereas chkrootkit informs me of the following:

```

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.1.7/.autoreg /usr/lib/firefox-3.5.7/.autoreg /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path /usr/lib/jvm/java-6-sun-1.6.0.15/.systemPrefs /usr/lib/jvm/.java-6-sun.jinfo
```

So is there a real problem or is that normal?

---

### Post by tripolitan on 2010-02-09
Looks normal to me.

---


---
title: "Rkhunter help! ***"
date: 2010-09-17
forum: Security
---

### Post by bacon_user on 2010-09-17
I just did a scan with Rkhunter and it spat out this, I'm very concerned! What does this mean? And what can I do to fix this security problem?

```

[00:17:12] Performing filesystem checks
[00:17:12] Info: Starting test name 'filesystem'
[00:17:12] Info: SCAN_MODE_DEV set to 'THOROUGH'
[00:17:13]   Checking /dev for suspicious file types         [ Warning ]
[00:17:13] Warning: Suspicious file types found in /dev:
[00:17:13]          /dev/shm/pulse-shm-4181005934: data
[00:17:13]          /dev/shm/pulse-shm-654856575: data
[00:17:13]          /dev/shm/pulse-shm-2650854220: data
[00:17:13]          /dev/shm/pulse-shm-1522401767: AmigaOS bitmap font
[00:17:13]          /dev/shm/pulse-shm-1814475783: data
[00:17:13]          /dev/shm/ecryptfs-house-Private: ASCII text
[00:17:13]          /dev/shm/pulse-shm-1777687512: data
[00:17:13]   Checking for hidden files and directories       [ Warning ]
[00:17:13] Warning: Hidden directory found: /dev/.udev
[00:17:13] Warning: Hidden directory found: /dev/.initramfs


```

---

### Post by sisco311 on 2010-09-17
They are most likely false positives, but google is your friend:
[http://www.google.ro/search?hl=en&safe=off&client=opera&hs=YTQ&rls=en&q=rkhunter+%2Fdev%2Fshm%2Fpulse-shm&aq=0&aqi=g10&aql=&oq=rkhunter+&gs_rfai=](http://www.google.ro/search?hl=en&safe=off&client=opera&hs=YTQ&rls=en&q=rkhunter+%2Fdev%2Fshm%2Fpulse-shm&aq=0&aqi=g10&aql=&oq=rkhunter+&gs_rfai=)
[http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

Also check out
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
and
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

---

### Post by bodhi.zazen on 2010-09-17
> **sisco311 said:**
> They are most likely false positives, but google is your friend:
[http://www.google.ro/search?hl=en&safe=off&client=opera&hs=YTQ&rls=en&q=rkhunter+%2Fdev%2Fshm%2Fpulse-shm&aq=0&aqi=g10&aql=&oq=rkhunter+&gs_rfai=](http://www.google.ro/search?hl=en&safe=off&client=opera&hs=YTQ&rls=en&q=rkhunter+%2Fdev%2Fshm%2Fpulse-shm&aq=0&aqi=g10&aql=&oq=rkhunter+&gs_rfai=)
[http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

Also check out
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
and
[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

This ^^

---


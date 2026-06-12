---
title: "RKHunter gives warnings of suspicious file types and hidden directories. Rootkit?"
date: 2010-10-11
forum: Security
---

### Post by martini1179 on 2010-10-11
After running RKHunter, I got the following warnings: 

[11:14:48] Performing filesystem checks
[11:14:48] Info: Starting test name 'filesystem'
[11:14:48] Info: SCAN_MODE_DEV set to 'THOROUGH'
[11:14:48]   Checking /dev for suspicious file types         [ Warning ]
[11:14:48] Warning: Suspicious file types found in /dev:
[11:14:48]          /dev/shm/pulse-shm-868281670: data
[11:14:48]          /dev/shm/pulse-shm-2066401558: data
[11:14:48]          /dev/shm/pulse-shm-254060246: data
[11:14:48]          /dev/shm/pulse-shm-2723448528: data
[11:14:48]          /dev/shm/mono.32277: data
[11:14:48]          /dev/shm/pulse-shm-2902466516: data
[11:14:48]          /dev/shm/pulse-shm-3973026706: data
[11:14:48]          /dev/shm/mono-shared-1000-shared_fileshare-marty-desktop-Linux-x86_64-40-12-0: DBase 3 index file
[11:14:48]          /dev/shm/mono-shared-1000-shared_data-marty-desktop-Linux-x86_64-328-12-0: data
[11:14:48]          /dev/shm/mono.2012: data
[11:14:48]          /dev/shm/mono.1998: data
[11:14:48]          /dev/shm/mono.1995: data
[11:14:48]          /dev/shm/pulse-shm-2239269480: data
[11:14:48]          /dev/shm/pulse-shm-658415412: data
[11:14:48]          /dev/shm/pulse-shm-4051081905: data
[11:14:49]   Checking for hidden files and directories       [ Warning ]
[11:14:49] Warning: Hidden directory found: /etc/.java
[11:14:49] Warning: Hidden directory found: /dev/.udev
[11:14:49] Warning: Hidden directory found: /dev/.initramfs

---

### Post by bodhi.zazen on 2010-10-11
This question gets asked almost daily.

See :

[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

I am not trying to be rude, but honestly if you are unwilling to read the documentation and follow though with a google search and investigation on your findings, rkhunter is of little or no use to you.

---


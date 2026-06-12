---
title: "RkHunter Help. Hidden filesystem"
date: 2010-08-29
forum: Security
---

### Post by KlearStatik on 2010-08-29
Sorry brand new to ubuntu. Just wanted a little guidance. I did check the FAQ for rkhunter however im not proficient with linux. YET. Any advice is appreciated and valued.

Is there any problem here? 
[12:49:19] Performing filesystem checks
[12:49:19] Info: Starting test name 'filesystem'
[12:49:19] Info: SCAN_MODE_DEV set to 'THOROUGH'
[12:49:20]   Checking /dev for suspicious file types         [ Warning ]
[12:49:20] Warning: Suspicious file types found in /dev:
[12:49:20]          /dev/shm/pulse-shm-3507992022: data
[12:49:20]          /dev/shm/pulse-shm-349173384: data
[12:49:20]          /dev/shm/pulse-shm-2663416452: data
[12:49:20]          /dev/shm/mono-shared-1000-shared_fileshare-not-laptop-Linux-i686-36-12-0: data
[12:49:20]          /dev/shm/mono-shared-1000-shared_data-not-laptop-Linux-i686-312-12-0: data
[12:49:20]          /dev/shm/mono.5621: data
[12:49:20]          /dev/shm/pulse-shm-546369180: data
[12:49:20]          /dev/shm/pulse-shm-1653964233: data
[12:49:20]          /dev/shm/pulse-shm-1041778540: data
[12:49:20]          /dev/shm/pulse-shm-1437170254: data
[12:49:20]          /dev/shm/ecryptfs-not-Private: ASCII text
[12:49:20]          /dev/shm/pulse-shm-319578103: data
[12:49:20]   Checking for hidden files and directories       [ Warning ]
[12:49:20] Warning: Hidden directory found: /dev/.udev
[12:49:20] Warning: Hidden directory found: /dev/.initramfs

Ubuntu 10.04

Also can someone direct me to a thorough nuts and bolts guide to ubuntu and linux that they themselves would read. Recent transition from windows and I do not want to annoy others with frequent questions. Thankyou

---

### Post by Dies on 2010-08-29
You can start here [https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)


Also, I would suggest that you try to learn the basics before you go worrying about rootkits or malware. 

I wouldn't worry about those warnings.

---

### Post by Rubi1200 on 2010-08-29
> **Dies said:**
> Also, I would suggest that you try to learn the basics before you go worrying about rootkits or malware. 

I wouldn't worry about those warnings.
+1 
First read the security stickies on the forum:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Also, here:
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

For documentation start here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

---


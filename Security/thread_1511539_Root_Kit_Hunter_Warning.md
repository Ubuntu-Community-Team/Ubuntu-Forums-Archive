---
title: "Root Kit Hunter Warning"
date: 2010-06-16
forum: Security
---

### Post by dyous87 on 2010-06-16
I recently installed rkhunter and ran it using the following command:
```
sudo rkhunter --update && sudo rkhunter -c -sk
```The following warnings were in my '/var/log/rkhunter.log' after the scan completed:

```
[23:46:15] Info: Starting test name 'filesystem'
[23:46:15] Info: SCAN_MODE_DEV set to 'THOROUGH'
[23:46:15]   Checking /dev for suspicious file types         [ Warning ]
[23:46:15] Warning: Suspicious file types found in /dev:
[23:46:15]          /dev/shm/pulse-shm-1229992884: data
[23:46:15]          /dev/shm/pulse-shm-4126066074: data
[23:46:15]          /dev/shm/pulse-shm-755244333: data
[23:46:15]          /dev/shm/pulse-shm-1094128980: AmigaOS bitmap font
[23:46:15]          /dev/shm/pulse-shm-1330212131: data
[23:46:15]          /dev/shm/pulse-shm-1990182769: data
[23:46:16]   Checking for hidden files and directories       [ Warning ]
[23:46:16] Warning: Hidden directory found: /etc/.java
[23:46:16] Warning: Hidden directory found: /dev/.udev
[23:46:16] Warning: Hidden directory found: /dev/.initramfs
[23:46:16]
[23:46:16] Info: Test 'apps' disabled at users request.
[23:46:16]
[23:46:16] System checks summary
[23:46:16] =====================
[23:46:16]
[23:46:16] File properties checks...
[23:46:16] Files checked: 132
[23:46:16] Suspect files: 0
[23:46:16]
[23:46:16] Rootkit checks...
[23:46:16] Rootkits checked : 242
[23:46:16] Possible rootkits: 0
[23:46:16]
[23:46:16] Applications checks...
[23:46:16] All checks skipped
[23:46:16]
[23:46:16] The system checks took: 1 minute and 16 seconds
[23:46:16]
[23:46:16] Info: End date is Wed Jun 16 23:46:16 EDT 2010
```Does anyone know if I should be concerned about this at all?

Thanks in advance!

David

---

### Post by Rubi1200 on 2010-06-17
With all due respect:

[http://ubuntuforums.org/showpost.php?p=9265649&postcount=8](http://ubuntuforums.org/showpost.php?p=9265649&postcount=8)

Searching on Google would have given you pretty much the same results as I got back.

By the way, why do you think you need to run rkhunter?

If you follow the advice given here:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

and here:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

then you should be fine.

---

### Post by Vimmander on 2010-07-20
Actually, some of these appear on a fresh install of 10.04 before any updates or drivers are downloaded.  The .java thing comes from the restricted-extras-package that lets you use java, flash, and Windows filetypes like mp3.  There is a way to make rkhunter ignore them:

[http://ubuntuforums.org/showthread.php?t=881404](http://ubuntuforums.org/showthread.php?t=881404)

The /dev/shm stuff is a new concept for me, but it's supposedly a mounted virtual file system.  Read all about it, and how to ignore it in future rkhunter scans, at:

[http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

---

### Post by Vimmander on 2010-07-21
I'd like to point out that many other forums ask users to check this site

[http://www.cert.org/tech_tips/intruder_detection_checklist.html](http://www.cert.org/tech_tips/intruder_detection_checklist.html)

for a list of false-positives.  This link is dead.  Is there a new link for rkhunter false-positives that's regularly updated/maintained?  How about one for chkrootkit?  Going through forum after forum is rather time consuming, considering the few warnings rkhunter tosses my way.

---

### Post by OpSecShellshock on 2010-07-21
Use of rootkit detection software is not (and is not intended to be) a passive process. To me, it seems just as easy to run once after a fresh install, keep a file with everything it finds and note that it's normal (or do so mentally) and then every time there's an update, repeat the process with the dates included. I'm sure such a thing could be automated if someone wanted to do so. I don't personally think that checking regularly for rootkits is even necessary to begin with, but I understand that it sort of nags at people's minds sometimes. But if that's the case, it's important to understand that rootkits are not generic and that detection methods require human discretion as a critical component.

---


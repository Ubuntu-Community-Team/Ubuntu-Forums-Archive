---
title: "aircrack problem"
date: 2009-11-30
forum: Security
---

### Post by nertil on 2009-11-30
heyyy 
/aircrack-ng$ aireplay-ng -9 wlan0
For information, no action required: Using gettimeofday() instead of /dev/rtc
socket(PF_PACKET) failed: Operation not permitted
This program requires root privileges.
nertil@ubuntu:~/aircrack-ng$ sudo airodump-ng-oui-update
[*] Downloading IEEE OUI file...
[*] Parsing OUI file...
[*] Airodump-ng OUI file successfully updated
nertil@ubuntu:~/aircrack-ng$ aireplay-ng -9 wlan0
For information, no action required: Using gettimeofday() instead of /dev/rtc
socket(PF_PACKET) failed: Operation not permitted
This program requires root privileges.
help me plz

---

### Post by __p1n__ on 2009-11-30
What's not clear?  Aireplay-ng is telling you exactly what the problem is.

---

### Post by nertil on 2009-11-30
i suposed to work with root terminal

---

### Post by Logan1985 on 2009-11-30
no...you just need to use Sudo. You did for  airodump-ng but not aireplay-ng.

No offense intended but maybe you should get to grips with linux more before turning to security tools like aircrack...if you aren't careful and blindly follow tutorials, you could end up executing a command that ruins your system. 

Take a look at this thread: [http://ubuntuforums.org/announcement.php?f=333](http://ubuntuforums.org/announcement.php?f=333)

---

### Post by EJeanmaire on 2009-11-30
> **nertil said:**
> i suposed to work with root terminal

Leave your neighbor's wireless network alone.  You won't get help performing illegal activities here.

---

### Post by nertil on 2009-12-02
thanks logan 1985

---


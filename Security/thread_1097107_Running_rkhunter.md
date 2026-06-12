---
title: "Running rkhunter"
date: 2009-03-15
forum: Security
---

### Post by bradthewanderer on 2009-03-15
I ran rkhunter and got these results that concern me:

 /usr/sbin/unhide                                         [ Warning ]

 /usr/sbin/unhide-linux26                                 [ Warning ]

Are these of concern or just false positives?

I run Ubuntu 8.10 on a PowerSpec P4 system.

Thank you for any help.

---

### Post by bradthewanderer on 2009-03-15
I now know those 2 are false positives thanks to someone else's post, but I got one more warning and wondered if anyone can tell me what it means:

Checking /dev for suspicious file types                  [ Warning ]

Thanks for any help

---

### Post by bradthewanderer on 2009-03-16
bump

---

### Post by slowth5 on 2009-03-16
[http://ubuntuforums.org/showthread.php?t=1006870](http://ubuntuforums.org/showthread.php?t=1006870)

If the /dev warning is related to pulse, it's most likely a false positive.

---

### Post by bradthewanderer on 2009-03-16
Thanks but the Checking /dev for suspicious file types [ Warning ] was the only thing that came up, no file was listed after that. That is why I am confused slightly.

---

### Post by slowth5 on 2009-03-16
The log at /var/log/rkhunter.log should list the suspicious files.

---

### Post by bradthewanderer on 2009-03-17
Thanks for the help. :)

---


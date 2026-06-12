---
title: "Roots permissions changed"
date: 2009-11-24
forum: Security
---

### Post by raucous on 2009-11-24
The root permissions on my system have been changed and, as I just got 9.10 in the mail (thank you), I'd rather not upgrade until I have everything back under my control. My roommate had stolen all of my passwords and somehow changed the root permissions. I first noticed this when I went to inspect my lost and found folder and found these nice messages. 


Also I read this post - [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Snort is something I would be interested in, but as the root has been compromised I won't be able to utilize it. 

So basiclly, how can I reclaim the root and make sure the the 9.10 upgrade will take place flawlessly?

---

### Post by bodhi.zazen on 2009-11-24
> **raucous said:**
> The root permissions on my system have been changed and, as I just got 9.10 in the mail (thank you), I'd rather not upgrade until I have everything back under my control. My roommate had stolen all of my passwords and somehow changed the root permissions. I first noticed this when I went to inspect my lost and found folder and found these nice messages. 


Also I read this post - [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Snort is something I would be interested in, but as the root has been compromised I won't be able to utilize it. 

So basiclly, how can I reclaim the root and make sure the the 9.10 upgrade will take place flawlessly?

Well if your system has been compromised you will need to re-install and choose a stronger password.

Since your roommate has physical access it is more difficult. Your best option is to encrypt your entire installation and keep your /boot partition on a removable usb.

Take care as encryption will not protect you from key loggers, some of which are physically connected to your box.

---

### Post by cariboo on 2009-11-25
As a normal user, you don't have access to lost+found.

---


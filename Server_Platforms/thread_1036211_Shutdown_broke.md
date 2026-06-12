---
title: "Shutdown broke"
date: 2009-01-10
forum: Server Platforms
---

### Post by dpeters on 2009-01-10
I was doing two things 1) turning on the boot log function: command bootlogd. Which said I needed to install sysvinit. So I did that. 2) There was also a critical error in the syslog: libpolkit error. So I looked it up online and was informed that I need to install policykit. So I did that. Now rebooting would verify both items fixed. Shutdown is now broken giving this error: "shutdown: timeout opening/writing control channel /dev/initctl". Is there an elegant solution?

---

### Post by dadozgb on 2009-01-10
ls -l /dev/initctl is...?

---

### Post by dpeters on 2009-01-10
ls -l /dev/initctl yields: 
prw------- 1 root root 0 2009-01-08 22:56 /dev/initctl

---


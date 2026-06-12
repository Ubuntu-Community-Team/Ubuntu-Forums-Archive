---
title: "unity/xorg seems to freeze upon wake up"
date: 2012-09-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Nosferax on 2012-09-08
Sometimes when I come back from sleep, the windows are unresponsive, whole desktop is frozen apart from mouse. Mouse moves fine, and I can switch to different viewports using ctrl+alt+#, but that's it. What is at issue?

---

### Post by 2F4U on 2012-09-09
What are your hardware specs? What graphics card and what graphics driver do you have? Did you look into /var/log/pm-suspend.log for further debugging?

---

### Post by Nosferax on 2012-09-09
> **2F4U said:**
> What are your hardware specs? What graphics card and what graphics driver do you have? Did you look into /var/log/pm-suspend.log for further debugging?

Computer is an ASUS UX31, with intelHD 4000 graphics card. I'm using the default driver  (i915?)

I didn't know which file to look in for status messages, didn't find anything weird in /var/log/syslog.

Just did a quick check of /var/log/pm-suspend.log - also nothing apparently wrong but I don't remember exactly the time it happened. Will check again.

---

### Post by Nosferax on 2012-09-11
Just happened again, nothing weird in the logs. Network-manager failed resuming, but it seems unrelated. 

It looks a lot like this bug : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744)

---


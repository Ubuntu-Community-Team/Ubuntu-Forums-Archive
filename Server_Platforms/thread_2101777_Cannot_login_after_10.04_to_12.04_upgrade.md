---
title: "Cannot login after 10.04 to 12.04 upgrade"
date: 2013-01-05
forum: Server Platforms
---

### Post by sentinelace on 2013-01-05
I get the login but when I try to type in my username, it just blinks and goes back to login.  I've tried root and a regular username with no luck.

---

### Post by lykwydchykyn on 2013-01-05
This is often caused by the HDD being out of space.  Often happens after a big upgrade due to the APT cache being huge.

Boot to recovery mode, drop to a root console, and try this:

```

mount -o remount,rw /
apt-get clean
reboot

```

See if that does it.

---

### Post by sentinelace on 2013-01-06
booted into recovery and ran those commands, but still same thing.  I type in my username and it just blinks and goes back to blank

---

### Post by Wim Sturkenboom on 2013-01-06
Assuming we're talking graphical login, I'm a bit confused. In 12.04 you select the username and only have to type the password. Am I missing something?

---

### Post by sentinelace on 2013-01-06
no this is at the terminal login when I hit alt f2.  This is server not desktop.  I uninstalled gnome

---

### Post by lykwydchykyn on 2013-01-07
In that case, you'll want to boot back into that root shell prompt and get some information.  Check out /var/log/syslog, dmesg, and /var/log/kern.log.  Somewhere there's got to be an error telling you why login is failing.

---


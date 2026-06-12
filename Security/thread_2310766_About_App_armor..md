---
title: "About App armor."
date: 2016-01-21
forum: Security
---

### Post by juan53 on 2016-01-21
Hi again.
I'm triying to configure apparmor. My problem is related with Firefox profile activation. I tried to activate it by using:
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox

But the result is:

sudo: aa-enforce:command not found.
I checked the status of aa, and it's loaded, with the basic profiles mounted.
Rightnow I'm running Ubuntu mate 14.03 LTS. Please, colud you help me?
Thanks a lot.

---

### Post by maglin2 on 2016-01-21
The simplest approach is to move the disable symlink for firefox apparmor profile. From memory

```
sudo mv /etc/apparmor.d/disable/usr.bin.firefox ~
```

Then reboot.

The other approach is to install apparmor-utils, then redo what you already tried.

---

### Post by juan53 on 2016-01-21
I tried the first way, but the result was:
'stat' can't be executed over /etc/apparmor.d/disable/usr.bin.firefox
I installed profiles and I updated them, but the result is negative too. I guess that the profile is not loaded. I saw in the installation of the profiles that firefox profile was "skipped".
Thanks for answering

---

### Post by juan53 on 2016-01-21
Sorry, I tried all the process again. I made a mistake. :)

---


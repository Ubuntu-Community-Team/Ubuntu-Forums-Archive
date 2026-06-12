---
title: "[SOLVED] Stops after splash loading screen"
date: 2008-11-26
forum: Server Platforms
---

### Post by CyberCowboy on 2008-11-26
I've had a Hardy server running with a xubuntu gui for a couple of months now.  Yesterday via SSH I did an apt-get dist-upgrade and the system required a reboot.  Now after loading the Xubuntu splash screen the system does a complete lock (caps lock light doesn't even come on on the keyboard)

When I reboot and go via grub into the recovery mode I can start the various services (mail, web etc) and have the system running, but I don't like running a live system in recovery.

I'm fairly well versed in CLI usage but really have no idea where to begin trouble shooting this or the best way to bring it back up.  Any ideas?

---

### Post by cariboo on 2008-11-26
If you disable xdm does it boot to the  command line?

To disable xdm when you are in recovery mode type:

```
update-rc.d -f xdm remove
```

I suspect it is a video driver problem that won't allow the system to boot up.

Jim

---

### Post by CyberCowboy on 2008-11-26
yep that did it, many thanks, I forgot that I had run envynq to get the ATI driver working for another project, forgot to roll back

---


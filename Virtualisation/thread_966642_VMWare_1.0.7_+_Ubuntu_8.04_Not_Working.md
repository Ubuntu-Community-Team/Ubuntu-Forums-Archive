---
title: "VMWare 1.0.7 + Ubuntu 8.04 Not Working"
date: 2008-11-01
forum: Virtualisation
---

### Post by CntdwnToExtn on 2008-11-01
Console is no longer launching and when i attempt to start the vm from a command line is says "a file not found".


i'm rarely on this machine and last time i was on was the 27th of October, when i downloaded 60meg of updates from the update manager.

i have no idea where to begin for this as i am a noob for troubleshooting linux.

if there is a way to do a system restore, that is perfectly fine because this is basically a host machine.

---

### Post by fjgaude on 2008-11-01
Well, I'm sure the update put a new kernel version on your machine and vmware has to be re-configured:

```
sudo /usr/bin/vmware-config.pl
```

That should get you going again.

---

### Post by CntdwnToExtn on 2008-11-01
yes, that did the trick.
thank you

---


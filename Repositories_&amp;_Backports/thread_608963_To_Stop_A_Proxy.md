---
title: "To Stop A Proxy"
date: 2007-11-10
forum: Repositories &amp; Backports
---

### Post by flaugher on 2007-11-10
Does anyone know how to STOP the proxy for automatic updates? I recently configured for downloading at work (behind a proxy) but now I'm home again (no proxy). I'm fine with Firefox, and the System > Administration > Network thing, but all my updates still want to use the proxy. I'm starting to get really backed up, like 85 downloads that fail every time because I can't get the proxy turned off.

---

### Post by trak87 on 2007-11-10
The question is a bit confusing. Synaptic has a proxy option you can adjust at Settings, Prefs, Network. Or do you want to stop Ubuntu from reminding you of available software updates? Or do you want Firefox to stop checking for updates or turn off its proxy?

---

### Post by bapoumba on 2007-11-11
Please paste the output to:
```
cat /etc/apt/apt.conf
```

If this file does not exist, please look in:
```
~/.bashrc
/etc/bash.bashrc
/etc/environment
```
if you have any remaining proxy declared.

---


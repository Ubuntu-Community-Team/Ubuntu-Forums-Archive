---
title: "Local network behind router"
date: 2016-11-21
forum: Security
---

### Post by bearlake on 2016-11-21
Hi good folks, running a local network behind a router and using scp to transfer files. ( Newbie learning Servers )

Should I have any firewall settings?

I do use my laptop to transfer files to the local server using scp but other wise the laptop is mostly on-line.

Laptop is using wireless, server is Ethernet.

Many Thanks

---

### Post by cariboo on 2016-11-21
I've benn running a local network behind a router for about 10 years, nothing is forwarded. I haven't run into any problems so far without running firewalls on local systems.

---

### Post by bearlake on 2016-11-22
Many thanks.

Testing a new field makes you wonder.

I do have incoming set to deny but added:

```
sudo ufw allow from 192.168.xxx.xx
```

All is good, time to install to a VM and learn more new task.

---


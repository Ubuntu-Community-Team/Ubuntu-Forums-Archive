---
title: "How to disable timeout Ubuntu server 20.04"
date: 2021-03-20
forum: Server Platforms
---

### Post by deepakdeshp on 2021-03-20
The timeout of Ubuntu server goes to sleep mode after some time. How do I disable the server going to sleep please?

---

### Post by wildmanne39 on 2021-03-20
Moved to server sub-forum as this appears to be a support request for Ubuntu server and not an issue with a forum account, if this is not the case please clarify.

---

### Post by Doug S on 2021-03-21
You will have to give us some more details about your server, because Ubuntu Server 20.04, or any server version, doesn't go to sleep on its own.

---

### Post by ameinild on 2021-03-21
Agree with Doug - servers do not normally go to "sleep mode". Please describe what is happening, what's working and what's not. Also think about if there is any way you can troubleshoot the problem, to narrow down the possibilities. For instance, can you SSH to your server, does it respond to ping etc.

---

### Post by LHammonds on 2021-03-22
My guess is that it is actually Ubuntu Desktop installed onto a laptop?

```
lsb_release -a
```

```
uname -a
```

---

### Post by TheFu on 2021-03-22
> **deepakdeshp said:**
> The timeout of Ubuntu server goes to sleep mode after some time. How do I disable the server going to sleep please?

Install Ubuntu Server, not any Ubuntu Desktop. Server doesn't go to sleep and doesn't have a GUI.
If you have a desktop install, look in the power settings. Closing a laptop screen can place desktops into standby.  logind.conf has settings to disable that and other similar features.
/etc/systemd/logind.conf

---

### Post by deepakdeshp on 2021-03-26
Thanks, it is a VM and I found that the host was going to keep mode not the server.

---


---
title: "cannot login with ssh after reboot"
date: 2010-12-09
forum: Server Platforms
---

### Post by RocketRanger on 2010-12-09
I doubt I am the first with this problem but I have been unsuccessful in finding a solution for it.

A couple of times now I have rebooted my ubuntu 10.10 server using 
```
 
$ sudo reboot

```

with the result that when the server comes back up ssh is closed. I can ping it, and using nmap I get the following:

```

$ sudo nmap -sT -p22 supert

Starting Nmap 5.21 ( http://nmap.org ) at 2010-12-09 11:05 CET
Nmap scan report for supert (93.176.84.125)
Host is up (0.011s latency).
PORT   STATE  SERVICE
22/tcp closed ssh

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds

```

If I get the administrator to power cycle the server where it is hosted it comes back up fine. But that is quite an annoyance for him and for me as well, so is there a way to prevent this from happening?

---


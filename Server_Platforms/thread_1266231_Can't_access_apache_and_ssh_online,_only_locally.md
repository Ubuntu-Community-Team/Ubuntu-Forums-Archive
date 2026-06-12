---
title: "Can't access apache and ssh online, only locally"
date: 2009-09-14
forum: Server Platforms
---

### Post by tprzepiorka on 2009-09-14
Hi,
I just installed Ubunutu Server on a computer and have it set up with ssh and apache. On my local computer I can type in 192.168.1.81 to get the "It Works!" page, or use an ssh client to access the computer. On my router I have forwarded the ports 80 and 2121 for the local ip address of the Ubuntu server. However it neither the html or ssh work over the internet. (I have dyndns for my IP to go: tprzepiorka.homelinux.com). Any ideas on how to get it up and working? This is my first experience with Ubuntu Server, so I'm not too sure where else to look for help
Thanks in advance :)
Tprzepiorka

---

### Post by Bachstelze on 2009-09-14
Are you trying from a machine inside or outside your LAN?

---

### Post by tprzepiorka on 2009-09-14
I'm testing from inside my LAN.

---

### Post by Bachstelze on 2009-09-14
> **tprzepiorka said:**
> I'm testing from inside my LAN.

Well, that's your problem. ;) Some routers don't let you connect to your public IP from inside your LAN, and that seems to be your case. From outside, it works fine:

```
firas@itsuki ~ % telnet tprzepiorka.homelinux.com 80
Trying 77.254.227.57...
Connected to tprzepiorka.homelinux.com.
Escape character is '^]'.
GET /index.html
<html><body><h1>It works!</h1></body></html>
Connection closed by foreign host.

```

---

### Post by tprzepiorka on 2009-09-14
Thank you, it works :)

---


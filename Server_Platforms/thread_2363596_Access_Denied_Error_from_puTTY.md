---
title: "Access Denied Error from puTTY"
date: 2017-06-12
forum: Server Platforms
---

### Post by bpatel111 on 2017-06-12
Hi All

I am having this issue, tried everything and not having much joy. I created a new user in Ubuntu 16.04 Server. Assigned password etc. I can login with that user locally. But, when I try log this user using puTTY or WinSCP, I get Access Denied error. Please help.

---

### Post by ajgreeny on 2017-06-12
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by steeldriver on 2017-06-12
Have you installed openssh-server on the server? if so, did you modify the configuration at all?

Can you ping the server from the host from which you are trying to connect? Are you trying to connect by hostname? IPv4 address? IPv6 address?

Are you trying to connect from a machine in the same LAN, or from outside? if from outside, have you set up appropriate port forwarding on your router?

Are you running a firewall on the server?

---

### Post by LHammonds on 2017-06-14
> **steeldriver said:**
> Have you installed openssh-server on the server? if so, did you modify the configuration at all?

Can you ping the server from the host from which you are trying to connect? Are you trying to connect by hostname? IPv4 address? IPv6 address?

Are you trying to connect from a machine in the same LAN, or from outside? if from outside, have you set up appropriate port forwarding on your router?

Are you running a firewall on the server?The exact same questions I was going to reply with.  However, I am 99% sure he did not install OpenSSH-Server.

LHammonds

---


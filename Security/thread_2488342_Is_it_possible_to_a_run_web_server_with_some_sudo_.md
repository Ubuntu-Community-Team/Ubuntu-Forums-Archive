---
title: "Is it possible to a run web server with some sudo ability in a secured way?"
date: 2023-07-03
forum: Security
---

### Post by 4-null-nan on 2023-07-03
I have a server with very low usage.  I was actively managing it, using iptables to block IPs (using some list on the net).
However, it was hacked after a few years running.

However, is it possible to have some configuration that makes this possible?  Maybe having the web server talks to another local server that has sudo access, and lock down the communication more to keep it very narrow to improve security?

---

### Post by aljames2 on 2023-07-03
Are you trying to use a web server to gain access to you LAN remotely?  A little confused what you mean.
If this is what you mean, then no.  Web servers are internet facing, and allowing access to your LAN via an internet facing web server is a bad idea.
It is possible to use a SSH tunnel remotely, but I prefer using a self hosted remote access VPN to access home computers.

Perhaps my thinking of what you are asking is not correct, I hope so.

---

### Post by 4-null-nan on 2023-07-04
This server runs on a cloud.  I was only using Sudo to manage the server.  I will have to look for other solution because sudo and web server is just too much risk.

> **aljames2 said:**
> Are you trying to use a web server to gain access to you LAN remotely?  A little confused what you mean.
If this is what you mean, then no.  Web servers are internet facing, and allowing access to your LAN via an internet facing web server is a bad idea.
It is possible to use a SSH tunnel remotely, but I prefer using a self hosted remote access VPN to access home computers.

Perhaps my thinking of what you are asking is not correct, I hope so.

---

### Post by SeijiSensei on 2023-07-04
Why do you think that? My servers are in the cloud (at Linode), and I communicate directly with them via SSH and use sudo when necessary. 

How do you manage the server? With SSH? If so, I don't see the risk. In fact, you cannot manage a server without root privileges.

Are you worried about being hacked again? How did it happen the first time?

---


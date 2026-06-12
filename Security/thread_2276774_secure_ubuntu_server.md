---
title: "secure ubuntu server"
date: 2015-05-04
forum: Security
---

### Post by sajil2 on 2015-05-04
hello everyone
i  use ubuntu server how can i secure it.root and password cant access.and no one can scan open ports,

---

### Post by papibe on 2015-05-04
Hi sajil2.
> **sajil2 said:**
> how can i secure it.root and password cant access.
Start here: [Initial server setup with Ubuntu 14.04]("https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04"), and then here: [7 security measures to protect your servers]("https://www.digitalocean.com/community/tutorials/7-security-measures-to-protect-your-servers").
> **sajil2 said:**
> and no one can scan open ports,
That's not the way things work.

What you do is to open only the necessary ports, close all the rest, and then block failed attempts to the open ones. Most of us use iptables to do that: [How to set up a firewall using iptables on ubuntu 14-04]("https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-iptables-on-ubuntu-14-04").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sajil2 on 2015-05-05
thanks guys i wil try that

---


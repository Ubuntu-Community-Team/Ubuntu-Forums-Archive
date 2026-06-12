---
title: "Which programs/files are needed to set up and configure firewall rules?"
date: 2013-03-17
forum: Security
---

### Post by regency on 2013-03-17
I am new to Linux and Ubuntu.

Besides iptables and netfilter, what other programs and files that I need to use in order to set up and configure firewall rules. My purpose is to force all outbound traffic through a certain software.

---

### Post by kevdog on 2013-03-17
I'm not sure iptables can do this. Iptables deals with port filtering, and packet redirection.  I don't think it can direct packets to a specific software

---

### Post by Ms. Daisy on 2013-03-17
Are you trying to set up a proxy?

---

### Post by regency on 2013-03-18
I plan on installing OpenVPN and route all network traffic through the VPN tunnel. When the VPN connection drops, all network traffic to and from my computer will be instantly terminated.

---


---
title: "SSH/SOCKS vs. VPN"
date: 2007-02-18
forum: Server Platforms
---

### Post by tomallen4 on 2007-02-18
I have a home desktop (Dapper) and laptop (Edgy). When traveling, I am often limited to unsecured wireless networks. What I want is a secure connection from the laptop to the desktop. 

For some time, I have been using OpenSSH secured with a passphrase-protected key. I use ssh (sometimes with X) and sshfs to access files and resources on the desktop from the laptop. I have also been trying to set up an SSH tunnel/SOCKS proxy forwarding arrangement for convenience and security when using email and browsing the web. Unfortunately, I have run into some technical difficulties with ssh -D (which I will post under a separate thread in this forum). 

A friend, however, suggested that I consider OpenVPN as an alternative. I have no experience with VPN, and this seems a little overkill, but I suppose it would be fairly simple to install and configure--surely a static key arrangement would work just fine. But there is still a learning curve. 

Given my needs, which is the better arrangement? What are the trade-offs (security and the time to set everything up correctly)?

---

### Post by galeron on 2007-02-19
Just note that SSH/SOCKS is pretty flexible and can be used with Dynamic DNS. VPNs on the other hand, require a static IP. There are configurations for dynamic IPs, but none seemed to work for me. YMMV. Additionally, key and certificate distribution is a problem in VPNs, but SSH is more flexible with regards to authentication.

Your call.

---

